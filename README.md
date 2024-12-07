# Github-Notes

### Step 1: Create a Project Directory
Navigate to the location where you want to create your project and make a new directory:

- mkdir my_project
- cd my_project

### Step 2: Initialize a Virtual Environment
a) Create a Virtual Environment:

- python3 -m venv venv

b) Activate the Virtual Environment:

- source venv/bin/activate  # On macOS/Linux

c) Upgrade pip:

- pip install --upgrade pip

### Step 3: Install Required Packages
a) Install the necessary packages (e.g., pandas, numpy):

- pip install pandas numpy

b) Save Installed Packages: Create a requirements.txt file to document the installed dependencies:

- pip freeze > requirements.txt

c) To uninstall all Python packages from your environment via the terminal, you can use the following methods based on your setup:

- pip freeze | xargs pip uninstall -y

Explanation:

pip freeze lists all installed packages. xargs pip uninstall -y takes that list and uninstalls each package without asking for confirmation.

### Step 4: Initialize a Git Repository
a) Initialize Git:

- git init

b) Create a .gitignore File: Add venv/ to .gitignore to prevent the virtual environment from being pushed to GitHub:

- echo "venv/" > .gitignore

c) Add Files to Staging Area:

- git add .

d) Commit Changes:

- git commit -m "Initial commit"

### Step 5: Link to GitHub
a) Create a Repository on GitHub:

- Go to GitHub, log in, and create a new repository.
- Do not initialize it with a README or .gitignore (since you've already done this locally).
- Add Remote Repository: Replace <your-username> and <repository-name> with your GitHub username and the repository name: git remote add origin https://github.com/<your-username>/<repository-name>.git

b) Push to GitHub:

- git branch -M main
- git push -u origin main

### Step 6: Start Writing Your Project Code
a) Create a main.py File:

- touch main.py

Example Content for main.py:

import pandas as pd

import numpy as np

b) Run Your Code:

- python main.py

### Step 7: Document Your Project
a) Create a README.md:

- touch README.md

Example Content:

# My Project

This project demonstrates how to set up a Python project with virtual environments and GitHub integration.

## Setup Instructions
1. Clone the repository.
2. Activate the virtual environment:
source venv/bin/activate
3. Install dependencies:
pip install -r requirements.txt

b) Add and Push Changes:

- git add README.md
- git commit -m "Add README.md"
- git push

### Step 8: Collaborate or Share
a) Clone the Repository (for collaborators):

- git clone https://github.com/<your-username>/<repository-name>.git
- cd <repository-name>

b) Set Up the Environment Locally:

- python3 -m venv venv
- source venv/bin/activate
- pip install -r requirements.txt

c) To deactivate a virtual environment, follow these steps based on your operating system:

Simply type the following command in your terminal or command prompt:
- deactivate
This command will deactivate the virtual environment and return you to the global Python environment.

### Optional: Use GitHub Actions for CI/CD
Add a .github/workflows/python.yml File:

- mkdir -p .github/workflows
- touch .github/workflows/python.yml

Example Content:

yaml
Copy code
name: Python CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.8'
    - name: Install dependencies
      run: |
        python -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt
    - name: Run tests
      run: |
        source venv/bin/activate
        pytest
