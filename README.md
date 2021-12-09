# Detecting Fake News with Python and Machine Learning

1. Install Python 3, copy paste the command
```
sudo apt update
sudo apt install python3.8
```
Allow the process to complete and verify the Python version was installed sucessfully, copy paste the command:
```
pip3 --version
```
Create virtual environment

The main purpose of Python virtual environments is to create an isolated environment for Python projects. This means that each project can have its own dependencies, regardless of what dependencies every other project has.
```
 virtualenv <INSERT_FILENAME_3.8> --python=python3.8
```
 To check if the file has been created, copy paste the command
```
 ls
```
 To activate the file you just created, copy paste the command:
```
 source fake_news_3.8/bin/activate
```
Project Prerequisites

You’ll need to install the following libraries with pip:
 ```
 pip install numpy
 ```
 ```
  pip install wheel
  ```
  ```
   pip install pandas
   ```
   ```
   pip install -U scikit-learn
   ```
To start working, install jupyter using the command:
```
pip install jupyter
```   
Copy paste the url into the browswer and lets start detecting!


   Make necessary imports:
```
import numpy as np
import pandas as pd
import itertools
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import PassiveAggressiveClassifier
from sklearn.metrics import accuracy_score, confusion_matrix
```
Now, let’s read the data into a DataFrame, and get the shape of the data and the first 5 records.
download the dataset beforehand.
```
#Read the data
df=pd.read_csv('paste the location of the dataset')
#Get shape and head
df.shape
df.head()
```
And get the labels from the DataFrame.
```
#DataFlair - Get the labels
labels=df.label
labels.head()
```
Split the dataset into training and testing sets.
```
#DataFlair - Split the dataset
x_train,x_test,y_train,y_test=train_test_split(df['text'], labels, test_size=0.2, random_state=7)
```

Let’s initialize a TfidfVectorizer with stop words from the English language and a maximum document frequency of 0.7 (terms with a higher document frequency will be discarded).

fit and transform the vectorizer on the train set, and transform the vectorizer on the test set.
```
#DataFlair - Initialize a TfidfVectorizer
tfidf_vectorizer=TfidfVectorizer(stop_words='english', max_df=0.7)
#DataFlair - Fit and transform train set, transform test set
tfidf_train=tfidf_vectorizer.fit_transform(x_train) 
tfidf_test=tfidf_vectorizer.transform(x_test)
```
 Next, we’ll initialize a PassiveAggressiveClassifier. This is. We’ll fit this on tfidf_train and y_train.

Then, we’ll predict on the test set from the TfidfVectorizer and calculate the accuracy with accuracy_score() from sklearn.metrics.
```
#DataFlair - Initialize a PassiveAggressiveClassifier
pac=PassiveAggressiveClassifier(max_iter=50)
pac.fit(tfidf_train,y_train)
#DataFlair - Predict on the test set and calculate accuracy
y_pred=pac.predict(tfidf_test)
score=accuracy_score(y_test,y_pred)
print(f'Accuracy: {round(score*100,2)}%')
```
 We got an accuracy of 92.82% with this model. Finally, let’s print out a confusion matrix to gain insight into the number of false and true negatives and positives.
```
#DataFlair - Build confusion matrix
confusion_matrix(y_test,y_pred, labels=['FAKE','REAL'])
```
So with this model, we have 589 true positives, 587 true negatives, 42 false positives, and 49 false negatives.

# Summary

Today, we learned to detect fake news with Python. We took a political dataset, implemented a TfidfVectorizer, initialized a PassiveAggressiveClassifier, and fit our model. We ended up obtaining an accuracy of 92.82% in magnitude.
