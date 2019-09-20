# Python

## Virtual Environment

### Install virtualenv

```bash
# Upgrade pip
$ pip install --upgrade pip

# Install virtualenv
$ pip install --user virtualenv
```

### Create a New Virtual Environment

```bash
# Create a new virtual environment
$ python -m venv env

# Activate the virtual environment
$ source env/Scripts/activate

# Deactivate the virtual environment
$ deactivate
```

### Installing Packages

```bash
# Install packages from requirements.txt
$ pip install -r requirements.txt

# Save installed packages to requirements.txt
$ pip freeze > requirements.txt
```
