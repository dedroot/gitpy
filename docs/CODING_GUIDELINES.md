<a name="readme-top"></a>

# GitPy Codebase Structure

> *Theses are the guidelines for the GitPy codebase structure. It is important to follow these guidelines in order to have a clean and maintainable codebase.*

<details>
    <summary>Table of Contents</summary>
    <ol>
        <li>
            <a href="#Arborescence">Arborescence</a>
            <li><a href="#source-style-and-other-conventions">Source style and other conventions</a></li>
                <ul>
                    <li><a href="#code-style">Code style</a></li>
                    <li><a href="#branch-naming">Branch naming</a></li>
                    <li><a href="#commit-message-format">Commit Message Format</a></li>
                    <ul>
                        <li><a href="#type">Type</a></li>
                    </ul>
                    <li><a href="#versioning">Versioning</a></li>
                </ul>
        </li>
    </ol>
</details>

## Arborescence

These are the directories that we actively using in the development:

| Directory | Description |
| --------: | :---------- |
| [gitpy/](gitpy/) | Contains the \_\_main\_\_ file of GitPy |
| [gitpy/commands](gitpy/commands/) | Contains the operations of all CLI commands of the tool |
| [gitpy/configs](gitpy/configs/) | Contains the configuration files of the tool. The languages used for the configuration files is Python3 and Yaml |
| [gitpy/core](gitpy/core/) | Contains the core files of the tool. Like the CLI arguments and parsing file |
| [gitpy/manuals](gitpy/manuals/) | Contains manpage of the tool (page that you can have by running `man gitpy`) |
| [gitpy/tools](gitpy/tools/) | Contains third party utilities to improve GitPy. If you have a new feature that require a specific third party package/tool version, you can add it here |
| [gitpy/utils](gitpy/utils/) | Contains utilities of the tool (home made, not third party) |

> [!NOTE]  
> If your changes require a new directory, you have to inform us in the issue you opened and we will tell you if it's okay or not.

## Source style and other conventions

### Code style

For this project, we actually using the [Black][black_url] and the [Isort][isort_url] Python3 formatter together. These two tools are very useful to keep the code clean and readable. If you use [VScode][vscode_url] or [VScode Insider][vscode-insider_url], you can install the Isort and Black extensions with the following commands:

1. First you need to install Black and Isort on you machine. To do that, you can using [pipx][pipx_url]:

    ```shell
    pipx install isort black
    ```

2. If you don't have [pipx][pipx_url], then run the following command:

    - If you are on a Debian based distro:

        ```shell
        sudo apt update && sudo apt install pipx
        ```

    - If you are on a Arch based distro:

        ```shell
        sudo pacman -Syy python-pipx
        ```

3. Next, open your VScode IDE (stable or Insider) and open the Quick Open dialog with <kbd>CTRL</kbd> + <kbd>p</kbd> and paste the following commands one by one:

    ```vscode
    ext install ms-python.isort
    ext install ms-python.black-formatter
    ```

4. Now create a folder called **.vscode** in the project folder. After, create a file called **settings.json** in it. Open it an paste the following:

    ```jsonc
    {
    // PYTHON
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter",
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.organizeImports": "explicit"
        },
    },
    "black-formatter.args": ["--line-length", "120"],
    "isort.args":["--profile", "black"],
    // END PYTHON
    }
    ```

> [!NOTE]  
> You can add more settings in it if you want. For more information, visit the [settings.json][settings.json-doc] section in the official documentation.

That's it! Now you can code with the Black and Isort formatter! Every time you save a python file (.py) in this project, the formatters will automatically format the code for you!

> [!NOTE]  
> The auto formatting will only do the job in the project folder (Workspace). If you want to auto format globally, you need to add the same content in the user settings.json. You can open it by open it the command palette with <kbd>CTRL</kbd> +  <kbd>SHIFT</kbd> + <kbd>p</kbd> and enter **settings.json**. While typing it, you will see the **Preferences: Open Settings (JSON)** option. Select it and only paste the content between the two curly brackets in the file (those in the begin and the end of the file).

### Branch naming

For the branch naming, we using the [GitFlow workflow][gitflow_url] branch naming rules. Here is the branch naming convention:

| Branch name | Description |
| ----------: | :---------- |
| `master` | The main branch. It's the branch that's MUST BE ALWAY STABLE. This branch should also always contain the latest stable release of the project |
| `develop` | For working in progress for future releases. It will also have `-dev`, `-alpha` tags in it for release a beta version of the program |
| `feat/<scope>` | For new features are created and will be merged into the `develop` branch |
| `bugfix/<scope>` | For fixing a small bug that are not critical to fix it and will be merged into the `develop` branch |
| `hotfix/<scope>` | For quickly fixing critical issues in production code usually with a temporary solution and will be merged into the `master` and `develop` branches |
| `release/<version>` | For preparing a new production release (not a dev or other, **a stable one**) and will be merged into the `master` and `develop` branches |
| `docs/<scope>` | For documentation changes and will be merged into the `develop` branch |
| `perf/<scope>` | For performance improvements and will be merged into the `develop` branch |
| `refactor/<scope>` | For refactoring the code and will be merged into the `develop` branch |
| `ci/<scope>` | For changes to the CI configuration and will be merged into the `develop` branch |

> [!NOTE]
> If you want to use a different prefix, you just have to tell us in the issue you opened and we will tell you if it's okay or not.

### Commit Message Format

Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **description**. With others words, we using the [Conventional Commits][conventional_commits_url] convention.

Here is the commit message convention format:

```txt
<type>[(optional scope)]: <description>
<BLANK LINE>
[optional body]
<BLANK LINE>
[optional footer(s)]
```

- The **optional scope** is a phrase describing a section of the codebase enclosed in parenthesis, e.g., "docs(CONTRIBUTING)".

- The **description** is a short summary of the code changes, e.g., "docs(CONTRIBUTING): Add commit message format section".

- The **optional body** is a longer description of the code changes. It can be several sentences long.

- The **optional footer** is a place to reference GitHub issues or other PRs that this commit closes.

#### Type

The type must be one of the following:

| Type | Description |
| ---: | :---------- |
| `feat` | A new feature |
| `fix` | A bug Fix |
| `chore` | Used for changes that don't affect the codebase or the user-facing part of the application. This can include changes to the build process, or auxiliary tools and libraries such as documentation generation |
| `docs` | Documentation only changes |
| `style` | Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) |
| `refactor` | A code change that neither fixes a bug nor adds a feature. It's used to clean up the code and make it more readable or easier to maintain |
| `perf` | A code change that improves performance |
| `test` | Adding missing tests or correcting existing tests |
| `ci` | Changes to our CI configuration files and scripts |
| `revert` | Reverts a previous commit |
| `nic` | For "Not In Changelog", used when the commit doesn't have to be in the changelog (because it generated based on the commit type of this list). Can be used when, for example, you already push something and you see after that you forgot to remove some bad typo |

> [!NOTE]
> And also here, if you want to use a different type, you just have to tell us in the issue you opened and we will tell you if it's okay or not.

### Versioning

For the versioning, we using the same principe of the [Semantic Versioning][semantic_versioning_url] convention. Here is the versioning convention:

```txt
<MAJOR>.<MINOR>.<PATCH>
```

- The **MAJOR** version when you make incompatible API changes or significant changes in the codebase
- The **MINOR** version when you add a new functionality
- The **PATCH** version when you fix a bug

<!-- In this versioning scheme, the <major> component typically indicates major releases with significant changes, <minor> is used for important feature additions or substantial updates, and <patch> signifies bug fixes and/or minor updates. -->

[black_url]: https://pypi.org/project/black/
[conventional_commits_url]: https://www.conventionalcommits.org/en/v1.0.0/
[gitflow_url]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[isort_url]: https://pypi.org/project/isort/
[semantic_versioning_url]: https://semver.org/
[vscode_url]: https://code.visualstudio.com/
[vscode-insider_url]: https://code.visualstudio.com/insiders/
[pipx_url]: https://pypa.github.io/pipx/
[settings.json-doc]: https://code.visualstudio.com/docs/getstarted/settings#_settingsjson
