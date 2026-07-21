<h1 align="center"><img src="https://github.com/danialafjeh/Run-My-Projects-Locally/blob/main/RunLocally.gif?raw=true" width="60%" alt="Intro"></h1>
<h1 align="center">
  <img src="https://img.shields.io/badge/Windows-0078D4?logo=None&logoColor=white" width="7.5%" height="7.5%">
  <img src="https://img.shields.io/badge/Linux-FCC624?logo=None&logoColor=black" width="5%" height="5%">
  <img src="https://img.shields.io/badge/macOS-555555?logo=None&logoColor=white" width="6.5%" height="6.5%">
</h1>
<br>
<h3 align="left">
This repository provides a complete step-by-step guide for running my projects on your local machine. You'll find detailed instructions to help you set everything up correctly.
<br>
  
The guide covers the entire setup process, from cloning a repository and creating a virtual environment to installing dependencies, configuring the database, running migrations, and starting the development server.
<br>
  
Instructions are provided for all major desktop operating systems, including **Windows**, **Linux**, and **macOS**. Where commands or procedures differ between operating systems, each platform is explained separately to ensure a smooth setup experience.
</h3>
<hr>
<h2>📑 Table of Contents</h2>

- [Windows](#windows-setup-guide)
- [Linux](#linux-setup-guide)
- [macOS](#macos-setup-guide)
  
<hr>

# Windows Setup Guide

This guide explains how to run my projects locally on **Windows using Command Prompt (CMD)**.

Follow the steps below carefully to set up the project, install required dependencies, configure the database, and run the development server on your computer.

> All commands in this section are written and tested for **Windows Command Prompt (CMD)**.

---

# 1. Open Command Prompt (CMD)

First, open **Command Prompt**:

1. Press `Win + R`
2. Type:

```text
cmd
```

3. Press `Enter`

A Command Prompt window will open.

---

# 2. Check Required Tools

Before starting, make sure Python and Git are installed.

## Check Python

Run:

```cmd
python --version
```

Example output:

```text
Python 3.x.x
```

If Python is installed correctly, the version will be displayed.

---

## Check pip

Run:

```cmd
pip --version
```

Example output:

```text
pip 25.x.x
```

---

## Check Git

Run:

```cmd
git --version
```

Example output:

```text
git version x.x.x
```

---

# 3. Clone the Project Repository

Navigate to the location where you want to save the project.

Example:

```cmd
cd Desktop
```

Clone the repository:

```cmd
git clone Repository_URL
```

Replace:

```text
Repository_URL
```

with the project's GitHub repository URL.

After cloning, enter the project folder:

```cmd
cd Project_Name
```

---

# 4. Create a Virtual Environment

A virtual environment keeps the project's packages separate from your system Python installation.

Create a virtual environment:

```cmd
pip install virtualenv
```
then:
```cmd
virtualenv denv
```

A new folder named `denv` will be created.

Example project structure:

```text
Project_Name
│
├── denv
├── manage.py
├── requirements.txt
├── project_folder
└── apps
```

> The virtual environment folder is not included in the GitHub repository. Each user must create their own environment.

---

# 5. Activate the Virtual Environment

Activate the virtual environment:

```cmd
denv\Scripts\activate
```

After successful activation, your command line should look like:

```text
(denv) C:\Users\User\Desktop\Project_Name>
```

The `(denv)` text means the virtual environment is active.

---

# 6. Install Project Dependencies

Make sure the virtual environment is active.

Install all required packages:

```cmd
pip install -r requirements.txt
```

This command installs every dependency required by the project.

The exact package versions are already specified inside:

```text
requirements.txt
```

---

# 7. Configure Project Settings

Before running the project, check the configuration files.

Common Django structure:

```text
Project_Name
│
├── manage.py
│
├── project_folder
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
└── applications
    ├── models.py
    ├── views.py
    └── admin.py
```

Depending on the project, you may need to configure:

* Database settings
* Environment variables
* Secret keys
* External services

---

# 8. Configure Database

## SQLite Projects

If the project uses SQLite, no additional database installation is required.

You can continue to the migration step.

---

## PostgreSQL Projects

If the project uses PostgreSQL, you need to configure your own local database.

Open:

```text
settings.py
```

Find the database configuration:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "database_name",
        "USER": "postgres_user",
        "PASSWORD": "your_password",
        "HOST": "localhost",
        "PORT": "5432",
    }
}
```

Replace the values with your PostgreSQL information:

* `NAME` → Database name
* `USER` → PostgreSQL username
* `PASSWORD` → PostgreSQL password
* `HOST` → Usually `localhost`
* `PORT` → Usually `5432`

---

# 9. Apply Django Migrations

Migrations create the required database tables.

Run:

```cmd
python manage.py makemigrations
```

Then:

```cmd
python manage.py migrate
```

If successful, Django will create all required tables.

---

# 10. Create Django Admin Account

Create a superuser:

```cmd
python manage.py createsuperuser
```

Enter:

```text
Username:
Email address:
Password:
```

After creating the account, you can access the admin panel:

```text
http://127.0.0.1:8000/admin/
```

---

# 11. Run the Development Server

Start the Django development server:

```cmd
python manage.py runserver
```

Successful output:

```text
Starting development server at http://127.0.0.1:8000/
```

Open your browser:

```text
http://127.0.0.1:8000/
```

The project is now running locally on your Windows computer.

---

# 12. Stop the Server

To stop the development server:

Press:

```text
CTRL + C
```

inside Command Prompt.

---

# 13. Deactivate Virtual Environment

When you finish working:

```cmd
deactivate
```

The `(denv)` label will disappear from the command line.

---

# Common Windows CMD Errors

## Python is not recognized

Error:

```text
'python' is not recognized as an internal or external command
```

Solution:

* Install Python again
* Enable "Add Python to PATH"
* Restart Command Prompt

---

## ModuleNotFoundError

Example:

```text
ModuleNotFoundError: No module named 'xxx'
```

Solution:

Activate the virtual environment:

```cmd
denv\Scripts\activate
```

Install requirements again:

```cmd
pip install -r requirements.txt
```

---

## Database Connection Error

Check:

* PostgreSQL service is running
* Database name is correct
* Username and password are correct
* Database configuration matches Django settings

---

## Port Already in Use

Run the project on another port:

```cmd
python manage.py runserver 8080
```

Then open:

```text
http://127.0.0.1:8080/
```

---

# ✅ Completed
<hr>
# Linux Setup Guide

This guide explains how to run my projects locally on **Linux using the Terminal**.

Follow each step carefully to prepare your environment, install dependencies, configure the project, and run the development server.

> All commands in this section are written for the Linux Terminal.

---

# 1. Open Terminal

Open your Linux Terminal.

You can usually open it by:

* Pressing `Ctrl + Alt + T`
* Searching for **Terminal** from the applications menu

---

# 2. Update System Packages

Before installing required tools, update your system packages:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade
```

> Note: Commands in this guide are based on Debian/Ubuntu-based distributions.

---

# 3. Install Required Tools

## Install Python

Check if Python is installed:

```bash
python3 --version
```

If Python is not installed:

```bash
sudo apt install python3
```

---

## Install pip

Check pip:

```bash
pip3 --version
```

If pip is not installed:

```bash
sudo apt install python3-pip
```

---

## Install Git

Check Git:

```bash
git --version
```

Install Git:

```bash
sudo apt install git
```

---

# 4. Install virtualenv

Install virtualenv globally:

```bash
pip3 install virtualenv
```

Check installation:

```bash
virtualenv --version
```

---

# 5. Clone the Project Repository

Navigate to the location where you want to store the project:

Example:

```bash
cd Desktop
```

Clone the repository:

```bash
git clone Repository_URL
```

Move into the project directory:

```bash
cd Project_Name
```

---

# 6. Create a Virtual Environment

Create a virtual environment using virtualenv:

```bash
virtualenv denv
```

A new folder named `denv` will be created.

Example:

```text
Project_Name
│
├── denv
├── manage.py
├── requirements.txt
└── project_folder
```

> The virtual environment folder is not included in the GitHub repository. Each user must create their own environment locally.

---

# 7. Activate the Virtual Environment

Activate the environment:

```bash
source denv/bin/activate
```

After successful activation:

```text
(denv) user@computer:~/Project_Name$
```

The `(denv)` label means the virtual environment is active.

---

# 8. Install Project Dependencies

Install required packages:

```bash
pip install -r requirements.txt
```

All required package versions are defined inside:

```text
requirements.txt
```

---

# 9. Configure Project Settings

Check the Django project configuration.

Typical structure:

```text
Project_Name
│
├── manage.py
│
├── project_folder
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
└── apps
    ├── models.py
    ├── views.py
    └── admin.py
```

Depending on the project, configure:

* Database settings
* Environment variables
* Secret keys
* External services

---

# 10. Configure Database

## SQLite Projects

No additional installation is required.

Continue to the migration step.

---

## PostgreSQL Projects

Install PostgreSQL:

```bash
sudo apt install postgresql postgresql-contrib
```

Check PostgreSQL status:

```bash
sudo systemctl status postgresql
```

Create a database:

```bash
sudo -u postgres createdb database_name
```

Update Django database settings with your local PostgreSQL credentials.

Example:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "database_name",
        "USER": "postgres",
        "PASSWORD": "your_password",
        "HOST": "localhost",
        "PORT": "5432",
    }
}
```

---

# 11. Apply Django Migrations

Create migrations:

```bash
python3 manage.py makemigrations
```

Apply migrations:

```bash
python3 manage.py migrate
```

---

# 12. Create Django Admin Account

Create a superuser:

```bash
python3 manage.py createsuperuser
```

Enter:

```text
Username:
Email address:
Password:
```

Admin panel:

```text
http://127.0.0.1:8000/admin/
```

---

# 13. Run the Development Server

Start Django:

```bash
python3 manage.py runserver
```

Successful output:

```text
Starting development server at http://127.0.0.1:8000/
```

Open:

```text
http://127.0.0.1:8000/
```

Your project is now running locally.

---

# 14. Stop the Server

Press:

```text
CTRL + C
```

inside the Terminal.

---

# 15. Deactivate Virtual Environment

When finished:

```bash
deactivate
```

---

# Common Linux Issues

## Permission Error

If you receive a permission error:

```bash
sudo command
```

may be required.

---

## Package Installation Error

Make sure the virtual environment is active:

```bash
source denv/bin/activate
```

Then reinstall requirements:

```bash
pip install -r requirements.txt
```

---

## Database Connection Error

Check:

* PostgreSQL service is running
* Database credentials are correct
* Database exists
* Django settings match your local database

---

# ✅ Completed
<hr>
# macOS Setup Guide

This guide explains how to run my projects locally on **macOS using the Terminal**.

Follow each step carefully to prepare your environment, install dependencies, configure the project, and run the development server.

> All commands in this section are written for the macOS Terminal.

---

# 1. Open Terminal

Open the Terminal application:

1. Press `Command (⌘) + Space`
2. Search for:

```text
Terminal
```

3. Press `Enter`

---

# 2. Install Homebrew

Homebrew is a package manager for macOS that makes installing development tools easier.

Check if Homebrew is installed:

```bash
brew --version
```

If Homebrew is not installed, install it from the official website:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, restart Terminal.

---

# 3. Install Required Tools

## Install Python

Check Python:

```bash
python3 --version
```

If Python is not installed:

```bash
brew install python
```

---

## Check pip

Run:

```bash
pip3 --version
```

---

## Install Git

Check Git:

```bash
git --version
```

Git is usually installed by default on macOS.

If Git is not available:

```bash
brew install git
```

---

# 4. Install virtualenv

Install virtualenv:

```bash
pip3 install virtualenv
```

Check installation:

```bash
virtualenv --version
```

---

# 5. Clone the Project Repository

Navigate to the location where you want to save the project.

Example:

```bash
cd Desktop
```

Clone the repository:

```bash
git clone Repository_URL
```

Move into the project folder:

```bash
cd Project_Name
```

---

# 6. Create a Virtual Environment

Create the virtual environment:

```bash
virtualenv denv
```

A new folder named `denv` will be created.

Example:

```text
Project_Name
│
├── denv
├── manage.py
├── requirements.txt
└── project_folder
```

> The virtual environment folder is not included in the GitHub repository. Each user must create their own environment locally.

---

# 7. Activate the Virtual Environment

Activate the environment:

```bash
source denv/bin/activate
```

After activation:

```text
(denv) user@MacBook Project_Name %
```

The `(denv)` label means the environment is active.

---

# 8. Install Project Dependencies

Install required packages:

```bash
pip install -r requirements.txt
```

All package versions are already defined in:

```text
requirements.txt
```

---

# 9. Configure Project Settings

Check the Django project structure:

```text
Project_Name
│
├── manage.py
│
├── project_folder
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
└── apps
    ├── models.py
    ├── views.py
    └── admin.py
```

Configure required settings depending on the project:

* Database settings
* Environment variables
* Secret keys
* External services

---

# 10. Configure Database

## SQLite Projects

No additional setup is required.

Continue to migrations.

---

## PostgreSQL Projects

Install PostgreSQL using Homebrew:

```bash
brew install postgresql
```

Start PostgreSQL:

```bash
brew services start postgresql
```

Check PostgreSQL:

```bash
brew services list
```

Create a database:

```bash
createdb database_name
```

Update Django database settings:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "database_name",
        "USER": "your_username",
        "PASSWORD": "your_password",
        "HOST": "localhost",
        "PORT": "5432",
    }
}
```

Use your local PostgreSQL username and password.

---

# 11. Apply Django Migrations

Create migrations:

```bash
python3 manage.py makemigrations
```

Apply migrations:

```bash
python3 manage.py migrate
```

---

# 12. Create Django Admin Account

Create a superuser:

```bash
python3 manage.py createsuperuser
```

Enter:

```text
Username:
Email address:
Password:
```

Admin panel:

```text
http://127.0.0.1:8000/admin/
```

---

# 13. Run the Development Server

Start Django:

```bash
python3 manage.py runserver
```

Successful output:

```text
Starting development server at http://127.0.0.1:8000/
```

Open your browser:

```text
http://127.0.0.1:8000/
```

Your project is now running locally on macOS.

---

# 14. Stop the Server

Press:

```text
CTRL + C
```

inside Terminal.

---

# 15. Deactivate Virtual Environment

When finished:

```bash
deactivate
```

---

# Common macOS Issues

## Command Not Found

If a command is not recognized:

* Check that the required tool is installed.
* Restart Terminal after installation.

---

## Package Installation Error

Make sure the virtual environment is active:

```bash
source denv/bin/activate
```

Then:

```bash
pip install -r requirements.txt
```

---

## PostgreSQL Connection Error

Check:

* PostgreSQL service is running
* Database exists
* Username and password are correct
* Django settings match your local database

---

# ✅ Completed
<hr>
