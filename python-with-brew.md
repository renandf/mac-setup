# Python 3 with Homebrew
Follow these steps to set up Python 3 using Homebrew

## Steps
1. [Homebrew](#homebrew)
2. [Python 3](#python-3)
3. [Troubleshooting](#troubleshooting)

## Homebrew
Install the [Homebrew](https://brew.sh/) package manager. Homebrew helps you install almost any package or app from the command line.

* To check if Homebrew is installed and what version: `brew --version`
* To install it:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
* To update it: `brew update`

From time to time (maybe at the start of a new project), run this command to update Homebrew and everything you have installed with it.
```
brew update && brew upgrade && brew cleanup && brew doctor
```

## Python 3
Install Python 3 using Homebrew by running this command:

```
brew install python
```

In theory, brew should have installed both Python 3 and Pip 3 and already put them under python and pip aliases. Verify if that's the case with these commands:

```
python -V
pip -V
```

If you see Python `3.x` and `pip` relative to that Python version, it's all done! Otherwise, troubleshoot below.

## Troubleshooting
### Python & pip are still on version 2 or pip command is missing
If running `python -V` or `pip -V` returns version 2 or pip alias is missing altogether, we'll need to add those aliases.

**If using oh-my-zsh:**
1. Go to folder `cd ~/.oh-my-zsh/custom`
2. If you don't have one yet, create a new .zsh file to add custom aliases/commands = `touch custom.zsh`
3. Add the aliases to the file:
```
alias python='python3'
alias pip='pip3'
```
4. Save the file and restart your terminal or run `source ~/.zshrc`

**If using Bash**, open your bash_profile `vi ~/.bash_profile` and add the following lines:

```
alias python='python3'
alias pip='pip3'
```
Restart your terminal or run `source ~/.bash_profile`

### Homebrew error
If Homebrew throw this error while installing Python:

```
Error: An unexpected error occurred during the `brew link` step
The formula built, but is not symlinked into /usr/local
Permission denied @ dir_s_mkdir - /usr/local/Frameworks
Error: Permission denied @ dir_s_mkdir - /usr/local/Frameworks
```

The computer is missing Frameworks directory. Fix it by running the commands:

```
sudo mkdir /usr/local/Frameworks
sudo chown $USER /usr/local/Frameworks
brew link python
```

### Other issues
For troubleshooting, the following command might help:

```
brew info python
```
