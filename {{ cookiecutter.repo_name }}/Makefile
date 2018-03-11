# Project Makefile
# This makefile automates the operations for the project.
# It should be extended to include all automatic operations.

.PHONY: clean data lint requirements

PROJECT_DIR := $(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))
PROJECT_NAME = {{ cookiecutter.repo_name }}
PYTHON_INTERPRETER = {{ cookiecutter.python_interpreter }}

requirements:
	pip install -U pip setuptools wheel
	pip install -r requirements.txt

data: requirements
	$(PYTHON_INTERPRETER) src/data/make_dataset.py

visualizations: data requirements
	$(PYTHON_INTERPRETER) src/visualization/make_visualization.py

clean:
	find . -type f -name "*.py[co]" -delete
	find . -type d -name "__pycache__" -delete

lint:
	flake8 src