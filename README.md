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

