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
<ul>
  <li><a href="#-windows">🪟 Windows</a></li>
  <li><a href="#-linux">🐧 Linux</a></li>
  <li><a href="#-macos">🍎 macOS</a></li>
</ul>
<hr>
# 🪟 Windows Setup Guide

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
python -m venv denv
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

