# Mini Project 4: Matrix Testing

### Description: 
The matrix testing was executed through the `python_matrix.yml` YAML file located in the `.github/workflows` directory. Below, you can find a glimpse of the YAML configuration. This matrix testing was established as a building strategy, incorporating both Python versions and operating system options within the "matrix" section of the "strategy." Python versions 3.8, 3.9, and 3.11 were all subjected to thorough validation.


### Github Actions:
[![Python Version: 3.8, 3.9, 3.11](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/python_matrix.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/python_matrix.yml)   [![Install](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/install.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/install.yml)   [![Format](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/format.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/format.yml)   [![Linting](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/lint.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/lint.yml)   [![Unit Tests](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/unitTests.yml/badge.svg)](https://github.com/nogibjj/mjh140-MiniProject4/actions/workflows/unitTests.yml)
***


```python
name: "Python Version: 3.8, 3.9, 3.11  "
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ] 
  workflow_dispatch:
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
      - name: Install
        run: |
          make install
      - name: Format
        run: |
          make format
      - name: Pylint
        run: |
          make lint
      - name: Unit Tests
        run: |
          make test
```