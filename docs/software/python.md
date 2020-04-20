# Python

## Virtual Environment

```bash
# install virtualenv
$ pip install --upgrade pip
$ pip install --user virtualenv

# Create a new virtual environment
$ python -m venv env

# Activate the virtual environment
$ source env/Scripts/activate

# Deactivate the virtual environment
$ deactivate

# Save installed packages to requirements.txt
$ pip freeze > requirements.txt

# Install packages from requirements.txt
$ pip install -r requirements.txt
```
