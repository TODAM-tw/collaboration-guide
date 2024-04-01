# ToDAM - Collaboration Guide   <!-- omit in toc -->

Some following to collaborate at ToDammm.

**Table of Contents**
- [Coding Style](#coding-style)
  - [Naming](#naming)
    - [General](#general)
    - [Classes, Exceptions](#classes-exceptions)
    - [Variables, Functions, and Methods](#variables-functions-and-methods)
    - [Constants](#constants)
    - [Testing](#testing)
  - [Format](#format)
  - [Logging](#logging)
- [Contribute to the Repository](#contribute-to-the-repository)
  - [The Example of the workflow](#the-example-of-the-workflow)
- [Commit Message](#commit-message)
  - [Type of Commit Message](#type-of-commit-message)
  - [Example](#example)
    - [Add a new feature](#add-a-new-feature)
    - [Documentation](#documentation)
    - [Add the test](#add-the-test)
- [Issue](#issue)
- [Pull Request](#pull-request)
- [Development Environment](#development-environment)
- [License](#license)

## Coding Style

> [!NOTE]
> We 

### Naming

#### General
- Please adhere to the [**PEP 8 – Style Guide for Python Code**](https://peps.python.org/pep-0008/) for the fundamental Python coding style.
    - It is recommended to install the VSCode Extension - [Pylint](https://marketplace.visualstudio.com/items?itemName=ms-python.pylint)

- CRUDL
    - C: Create
    - R: Get
    - U: Update
    - D: Delete
    - L: List
    - Exmaple: `update_order_name.py`
#### Classes, Exceptions
Use of **CapWords** convention (PascalCase) for class names and exceptions.

#### Variables, Functions, and Methods
Use of **lowercase with underscores** (snake_case) for variable names, function and method names.

#### Constants
Use of all **uppercase** letters with underscores separating words for constants.

#### Testing
Begin with **test_** followed by a description of the function's behavior or condition being tested, using underscores to separate words.
Example: `test_calculate_total_with_negative_numbers`, `test_process_data_invalid_format`

### Format

We will use **Black** for formatting.

Please use the following tools, assuming all team members are using VSCode for writing code. If you are using another IDE or editor, please find the equivalent and compatible plugins for your IDE.

- **Black Formatter**
  - **Description:** Automatic code formatting tool.
  - **Download URL:** [https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter)
  - **Note:** [Trial from VS Code Python extension split Black, isort package](https://blog.kyomind.tw/black-and-isort/)

- **Isort**
  - **Description:** Automatic code formatting tool, but only for import statements to comply with PEP 8 standards.
  - **Download URL:** [https://marketplace.visualstudio.com/items?itemName=ms-python.isort](https://marketplace.visualstudio.com/items?itemName=ms-python.isort)
  - **Note:** Keyboard Shortcut: `Shift + Alt + O` <br> [VS Code: Python isort extension introduction and simple settings tutorial](https://blog.kyomind.tw/isort/)

### Logging

**General Guidelines**
The following are mainly based on the PEP 8 guidelines:

1. Do not use bare `print()` statements. Always use `logging` for outputting log messages.
2. Set up a logger for each module: `logger = logging.getLogger(__name__)`.
3. Use appropriate log levels (such as `debug`, `info`, `warning`, `error`, `critical`) for outputting messages.
4. For formatting strings, use the '%' formatting style instead of `.format()` or f-strings.

Example:
```python
import logging

# Configure logging
logging.basicConfig(level=logging.INFO,
                    format='%(asctime)s [%(levelname)s] - %(message)s')

# Create logger
logger = logging.getLogger(__name__)

def add(a, b):
    logger.info("Adding %s and %s", a, b)
    return a + b
```


## Contribute to the Repository

- **No one** is allowed to directly push to the main branch. All changes must be made through pull requests for merging (with or without code review).
- When merging a pull request, it is necessary to link related **TASK** or **USER STORY** and include `#issue_number` in the commit message to provide context. It is also recommended to communicate the purpose of the pull request to the **Product Owner (PO) and Tech Lead** for faster merging of the code.
- Each person should work on their own branch and before starting any development, they should pull the latest code from the main branch to keep their branch up to date.

The following is the workflow:

1. Fork the `TODAM/XXX` repository.
2. Clone your forked repository.
3. Add the `TODAM/XXX` repository as the upstream remote.
4. Create a new branch for your feature.
5. Push your code to the branch you created in your forked repository.
6. If no issues are found, create a pull request to the ``TODAM/XXX`` repository's `main` branch or your Destination Branch.
7. Once the PO or Tech Lead approves, merge the pull request.
8. Fetch the latest code from the `TODAM/XXX` repository and merge it into your forked repository's main branch or your development branch.

> [!IMPORTANT]
> If the PO's repository has been updated, you need to fetch the latest code from the PO's repository and merge it into your forked repository's main branch.

> [!TIP]  
> #### Make sure to synchronize and update your repository before initiating a pull request:
> 1. Run `git stash save` to temporarily stash your local changes.
> 2. Run `git fetch upstream` to sync the source project with your local copy.
> 3. Run `git checkout main` to switch to the main branch.
> 4. Run `git merge upstream/main` to merge the updated remote version into your local copy. If there are no conflicts, the update process is complete.
> 5. Run `git stash pop` to apply your temporarily stashed changes back to your working directory. Resolve any conflicts if necessary.

### The Example of the workflow

- Repository in ToDAM: `TODAM/test-repo`
  - Main Branch: `main`
- Forked Repository: `YourName/test-repo`
  - Main Branch: `main`
  - Feature Branch: `feature/your-feature` <- Add your feature here
  - Upstream Remote: `TODAM/test-repo`
  - Upstream Branch: `main`
- Pull Request: `TODAM/test-repo:main <- YourName/test-repo:feature/your-feature`
- Merge: `TODAM/test-repo:main <- YourName/test-repo:feature/your-feature`
- Fetch: `YourName/test-repo:main <- TODAM/test-repo:main`
- Merged: `YourName/test-repo:feature/your-feature <- YourName/test-repo:main` or Create a new branch from `YourName/test-repo:main`

## Commit Message

We only required the `Header` and `Footer` in the commit message. Header is described as Topic, and Fotter is linked to the issue or task number.

```
Header: <TYPE>(<SCOPE>): <SUBJECT>
    - TYPE: Represents the category of the commit.
    - SCOPE: Represents the scope of the commit.
    - (Required) SUBJECT: Represents a brief description of the commit, (limited to 50 characters and should not end with a period)

Body: 72-character wrapped. This should answer:
    - Provide a detailed description of the commit. (Can be split into multiple lines, with each line limited to 72 characters.)
    - Explain the changes made in the code, and Why to do?

Footer:
    - (if applicable) Include the task number.
    - (optional) BREAKING CHANGE: Record incompatible changes. It should start with "BREAKING CHANGE:" followed by a description of the change, the reason for the change, and migration instructions.
```

### Type of Commit Message

The `Type` field represents the category of the commit and indicates the action performed. Here are some conventions we follow:

- feat: Adding or modifying features.
- fix: Fixing functionality or bugs.
- docs: Writing documentation.
- style: Making formatting changes that do not affect the code's functionality (e.g., white-space, formatting, missing semi colons, etc.).
- refactor: Restructuring code without adding new features or fixing bugs.
- perf: Improving performance.
- test: Adding missing tests.
- chore: Making changes to build processes or auxiliary tools.
- revert: Reverting a previous commit (e.g., revert: type(scope): subject (revert version: xxxx)).

> [!IMPORTANT]
> You must choice the `Type` of the commit message from the above list.

### Example

#### Add a new feature
```
feat: email validation

Issue: #123
```

#### Documentation
```
docs: email validation

Issue: #124
```

#### Add the test
```
test: email validation

Issue: #125
```


## Issue

## Pull Request

## Development Environment

## License
Released under [Apache License 2.0](./LICENSE) by [TODAM-tw](https://github.com/TODAM-tw).

This software can be modified and reused without restriction.
The original license must be included with any copies of this software.
If a significant portion of the source code is used, please provide a link back to this repository.
