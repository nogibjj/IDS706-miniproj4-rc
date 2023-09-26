# IDS706 Mini Project 4: Matrix Testing

### Description: 
The matrix testing was executed through the `python_matrix.yml` YAML file located in the `.github/workflows` directory. Below, you can find a glimpse of the YAML configuration. This matrix testing was established as a building strategy, incorporating both Python versions and operating system options within the "matrix" section of the "strategy." Python versions 3.8, 3.9, and 3.11 were all subjected to thorough validation.


### Github Actions:
[![Python Version: 3.8, 3.9, 3.11](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/python_matrix.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/python_matrix.yml)   [![Install](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/install.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/install.yml)   [![Format](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/format.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/format.yml)   [![Linting](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/lint.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/lint.yml)   [![Unit Tests](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/unitTests.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/unitTests.yml)
***


### Overview of the files in the project:

In a file located at `.github/workflows/.ymlFiles`, development environments are configured with various Python versions to be used in subsequent actions. These actions are initiated when changes are pushed or pulled into the main branch. Once the environment is established, a sequence of actions, including package installation, linting, testing, and formatting, is executed in the order specified within the Makefile. Here is an example code block demonstrating the setup of Python versions in a file.


```python
name: "Python Version: 3.8, 3.9, 3.11  "

jobs:
  build:
    strategy:
      matrix:
        python-version: [3.8, 3.9, 3.11]
        os: [ubuntu-latest]
    runs-on: ${{matrix.os}}
    steps:
      - uses: actions/checkout@v3
      - name: venv activation
        run: |
          make venv
      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v1
        with:
          python-version: ${{ matrix.python-version }}

```
