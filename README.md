# ToDAM - Collaboration Guide   <!-- omit in toc -->

Some following to collaborate at ToDammm.

**Table of Contents**
- [Coding Style](#coding-style)
- [Contribute to the Repository](#contribute-to-the-repository)
  - [The Example of the workflow](#the-example-of-the-workflow)
- [Issue](#issue)
- [Pull Request](#pull-request)
- [Development Environment](#development-environment)
- [License](#license)

## Coding Style


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

- PO's Repository: `PO/test-repo`
  - Main Branch: `main`
- Forked Repository: `YourName/test-repo`
  - Main Branch: `main`
  - Feature Branch: `feature/your-feature` <- Add your feature here
  - Upstream Remote: `PO/test-repo`
  - Upstream Branch: `main`
- Pull Request: `PO/test-repo:main <- YourName/test-repo:feature/your-feature`
- Merge: `PO/test-repo:main <- YourName/test-repo:feature/your-feature`
- Fetch: `YourName/test-repo:main <- PO/test-repo:main`
- Merged: `YourName/test-repo:feature/your-feature <- YourName/test-repo:main` or Create a new branch from `YourName/test-repo:main`

## Issue

## Pull Request

## Development Environment

## License
Released under [Apache License 2.0](./LICENSE) by [TODAM-tw](https://github.com/TODAM-tw).

This software can be modified and reused without restriction.
The original license must be included with any copies of this software.
If a significant portion of the source code is used, please provide a link back to this repository.
