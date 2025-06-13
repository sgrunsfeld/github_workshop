# Git in the terminal

**Note:** This tutorial is only for if you want to use GitHub through the command line interface. If you are using the GitHub web interface or an editor (i.e., VS Code), skip this tutorial.

---
### Installation

**Windows Installation**
* Download [Git for Windows installer](https://gitforwindows.org/)
* Run the installer:
  * On the page "Adjusting the name of the initial branch in new repositories" --> Select "Override the default branch name for new repositories" --> Select `main`
  * Select "Git from the command line and also from 3rd-party software"
  * Choosing the OpenSSH executable --> "Use bundled OpenSSH"
  * Select "Use the native Windows Secure Channel Library"
  * Select "Checkout Windows-style, commit Unix-style line endings"
  * Select "Use Windows' default console window"
  * Select "Default (fast-forward or merge)"
  * Select "Git Credential Manager", or, if "Core" is an option under this menu, select that instead
  * Select "Enable file system caching"
  * Do not select either prompt for configuring experimental options
* If your "HOME" environment variable is not set:
  * Open command prompt
  * Enter `setx HOME "%USERPROFILE%"`
  * Should see `SUCCESS: Specified value was saved.` after entering
* You should now be able to launch Git Bash from the start menu

**macOS Installation**
* Check if Git is already installed by running `git --version` in the terminal
* If Git is not installed, download and run the most recent "mavericks" installer from [here](https://sourceforge.net/projects/git-osx-installer/files/)
* Command are exectue in the terminal

**SSH or HTTPS connection to GitHub from terminal**

See [SSH or HTTPS connection to GitHub from terminal](https://coderefinery.github.io/installation/ssh/) for instructions.

---
### Configuration

Configuration settings are saved in your home directory in a `.gitconfig` file. To display configuration settings:

```
$ git config --list --show-origin
```

**Step 1: Setting commit metadata**

Commits contain metadata about the author, namely the user name and user email (recommended to use the email associated with your GitHub account), that are publically available when you make contributions on GitHub.

The following commands will set your user name and email: 

```
$ git config --global user.name "Your Name"
```

```
$ git config --global user.email name@example.com
```

**Step 2: Setting an editor**

This will set the default text editor used by Git for commit messages. There are many options (VS Code, vim, nano, etc.), so this will change depending on your preferred editor. 

Example for setting the editor to VS Code:

```
$ git config --global core.editor vscode
```

**Step 3: Set default branch**

Generally, the default branch name, or the name for the branch generated when a new repository is created, is `main` (or `master`). To ensure the default branch is set to `main` for new local repositories: 

```
$ git config --global init.defaultbranch main
```

**Step 4: Settings for Windows users only**

These setting prevent warnings and/or seeing no output with certain commands on Windows.

```
$ git config --global core.autocrlf false
```
```
$ git config --global core.pager cat
```

---
### Verification 

**Step 1: Check Git version**

```
$git --version
```

**Step 2: Initialize a repository in a new folder**

Create a new folder called "example" and navigate to it: 

```
$ mkdir example
$ cd example
```

Initialize a repository (make sure you are not in your home directory!):
```
$ git init -b main
```

**Step 3: Make a new file**

Create a new file in your text editor (using VS Code as an example here):

```
$ vscode example.txt
```

Write some text in this file, then save and exit.

**Step 4: Stage the change**

Stage the new `example.txt` file before committing the change and record in Git: 

```
$ git add example.txt
```

**Step 5: Commit the change with a message**

Committing the change should open the configured text editor where you can then add a message describing the changes.

```
$ git commit
```

**Step 6: See the change log**

The change log will display the unique record identifier associated with the commit, author information, the date, and the commit message.

```
$ git log
```

---
An **alias** is basically a shortcut for a longer command in Git. The following alias allows us to visualize the branch structure of a given repository in the terminal:

```
$ git config --global alias.graph "log --all --graph --decorate --oneline
```
