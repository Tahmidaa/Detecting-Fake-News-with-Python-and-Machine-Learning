# fake_news

1. Install Python 3
```
sudo apt update
sudo apt install python3.8
```
Allow the process to complete and verify the Python version was installed sucessfully::
```
pip3 --version
```
Create virtual environment

The main purpose of Python virtual environments is to create an isolated environment for Python projects. This means that each project can have its own dependencies, regardless of what dependencies every other project has.
```
 virtualenv <INSERT_FILENAME_3.8> --python=python3.8
```
 To check if the file has been created
```
 ls
```
 To activate the file you just created
```
 source fake_news_3.8/bin/activate
```
 
