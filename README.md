# Jupyter book template for Julia Jupyter notebooks

## Jupyter Book

[Jupyter book](https://jupyterbook.org/index.html) builds a website from Markdown and Jupyter Notebook files.

## CI/CD

GitHub actions and GitLab CI/CD are setup to build and publish the website whenever changes are committed.

- Execution results are executed on the fly so you can push notebooks with empty output cells and received the results once the pipeline is completed.
- Execution results are cached so only the edited notebooks will be executed, saving CI time.
- Docker images with Julia and `jupyter-book` are automatically built and pushed to GitHub and/or Gitlab container registries. Those docker images serve as self-sufficient Julia + `jupyter-book` environments so the CI service don't have to call `Pkg.instantiate()` and run precompile every time.

## Auto update
Periodically updating Julia dependencies and make a PR if notebooks are executed successfully.

- For GitHub: you need a `PAT` [secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets), which is a personal access token with `repo` access.
- For GitLab: you need a `GIT_PUSH_TOKEN` [CI/CD variable](https://docs.gitlab.com/ee/ci/variables/index.html), which is a PAT with `write_repo` access.
