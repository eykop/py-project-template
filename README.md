# py project template
A template place for starting a new python project:
1. [pyproject.toml](https://www.python.org/dev/peps/pep-0518/) to manage all tools, configurations and dependencies in one
place.
2. [poetry](https://python-poetry.org/): python packaging and dependency management made easy.
   - to get started with poetry it is best to follow documentation from [here](https://python-poetry.org/docs/).
   - or just install poetry and create a virtual env in project directory:
     ```shell
        curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
        poetry config virtualenvs.create true \
        && poetry config virtualenvs.in-project true \
        && poetry install --no-interaction --no-ansi
     ```
   - to activate the virtual env with poetry just type: `poetry shell`
   - to deactivate the virtual env `shell` type `exit` or `Ctrl-D`
3. git's [pre-commit](https://pre-commit.com/hooks) hooks for code format and linting
4. default python [.gitignore](https://github.com/github/gitignore/blob/main/Python.gitignore) file.
5. [editorconfig](https://editorconfig.org/) - instructs code editors for some files format conventions.


## Note about python version in template files:

default is python3.8

There are some places that need to pay attention to, when using a different python version:
I think the only place that matters is the poetry (No.1.ii below), but feel free to try.

1. pyproject.toml
    1. Black
        ```toml
            [tool.black]
            target-version = ['py3']
        ```
    2. Poetry
        ```toml
            [tool.poetry.dependencies]
            python = "^3.8"
        ```
2. .pre-commit-config.yaml
   1. flake8
       ```yaml
            - id: flake8
              additional_dependencies:
            - flake8-black>=0.1.1
              language_version: python3
       ```
