# Contributing Guide

> *Contributing to the GitPy project is fairly easy. This document shows you how to get started.*

## Prerequisites

First of all, thank you for taking the time to contribute for this project! :heart:

But before you begin, verify that your environment meets the following prerequisites:

- You have a code editor, a GitHub account, and experience using command-line programs, including `git` commands and command line options (CLI). You should also be familiar with the [GitFlow workflow][gitflow_url] and Linux environment.

- You must read, agree and follow the [Code of Conduct](CODE_OF_CONDUCT.md) in order to contribute to this project.

- There are a few guidelines that you must follow in order to ease the process of getting your contribution merged. See [DEVELOPING.md](DEVELOPING.md) for more information.

- We use [OpenPGP][gpg_url] keys to sign our commits. If you don't know how to sign your commits, please read the [GPG Signing][gpg_signing_url] page. It's important to sign your commits because it's a way to verify that the commit is from you and not from someone else.

## Getting stared

  1. Open a new [**Contributing request issue template**](https://github.com/dedroot/gitpy/issues/new?assignees=dedroot&labels=contributing%2Frequest&projects=dedroot%2Fgitpy&template=3-contributing_request.yml&title=%5BCONTRIBUTING+REQUEST%5D%3A+) and fill it with the necessary information  \
  Now you have to wait until the maintainer review your request and approve your proposed features/bugfix/etc

  2. If your request is approved, you can fork the project by going on the [GitPy fork][fork_repo_url] page, and <ins>**untick**</ins> the *Copy the master branch only* option. Then, click on the *Create fork* green button

  3. In your forked repo, create a new branch based <ins>**`develop`**</ins>

> [!IMPORTANT]  
> For the branch name, see the [Branch Naming](CODING_GUIDELINES.md#branch-naming) for more information.

  4. Make a Pull Request from your fork and your branch to the <ins>**`develop`**</ins> branch on the <ins>**main**</ins> repository, and after the PR's open you can start your changes. You create must open a PR before starting your changes, so we know that your working on it and we can help you if needed.

  5. After you finish your changes and <ins>**you tested it and it works properly**</ins>, you can ping dedroot on the PR and wait for the review. Do not spam him please, he will review your PR as soon as possible and give you feedback.

  6. If your PR is approved, it will be merged into the `develop` branch and will be available in the next release.

[fork_repo_url]: https://github.com/dedroot/gitpy/fork
[gitflow_url]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[issues_repo_url]: https://github.com/dedroot/gitpy/issues
[gpg_signing_url]: https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification
[gpg_url]: https://gnupg.org/
