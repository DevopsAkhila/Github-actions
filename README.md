python-github-actions-demo/
├── .github/
│   └── workflows/
│       └── python-ci.yml
├── app/
│   ├── __init__.py
│   └── calculator.py
├── tests/
│   ├── __init__.py
│   └── test_calculator.py
├── requirements.txt
├── .gitignore
└── README.md


# Python GitHub Actions Demo

Simple Python application built and tested using GitHub Actions.

## Pipeline Steps
- Checkout code
- Setup Python
- Install dependencies
- Lint with flake8
- Test with pytest
