---
title: "Github Workflows/Actions"
category: YAML files
author: J.B.
date: 01/09/2025
tags: ["yaml", "workflows", "githubactions"]
---
# GitHub Actions/Workflows: 

### - ***Notes***
```markdown
  - You can use multiple GitHub Actions workflows in a single repository. 
  • Here's a brief explanation of each type:`
   
- CI/CD (Continuous Integration/Continuous Deployment): Automates process of building, testing, & deploying your code. 
    - Example: running tests on each push or pull request.
- **Linting**: Analyzes your code for potential errors, code style issues, & best practices. 
    - Example: using ESLint for JavaScript.
- **YAML Linting**: Specifically checks YAML files for syntax errors & formatting issues. 
    - Example: using yamllint.

** You can combine all these workflows in a single repository to maintain code quality and automate deployments.
```

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/fire.png)

## Action for Markdown Format : 

- _Create the file,_ `.github/workflows/markdown-lint.yml`

```yaml
name: Markdown Lint

on: [push, pull_request]

jobs:
  markdown-lint:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Install markdownlint
      run: sudo npm install -g markdownlint-cli
    - name: Run markdownlint
      run: markdownlint '**/*.md'
```


## Action for Python Code Formatting:

```yaml
name: Python Lint

on: [push, pull_request]

jobs:
  python-lint:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.x'
    - name: Install flake8
      run: pip install flake8
    - name: Run flake8
      run: flake8 .
```

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/aqua.png)

# **Some more YAML Files**

### Continuous Integration (CI)

```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'
    - run: npm install
    - run: npm test
```

### Linting 

```yaml
name: Lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Install ESLint
      run: npm install eslint
    - name: Run ESLint
      run: npx eslint .
```      


### YAML Linting

```yaml
name: YAML Lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Install yamllint
      run: sudo apt-get install -y yamllint
    - name: Run yamllint
      run: yamllint .
```     
