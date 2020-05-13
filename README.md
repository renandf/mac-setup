# New (or formatted) Mac setup
Steps I usually follow to setup a new or formatted Mac focused on front-end development as a designer

Inspired by [Tania Rascia's article](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/).

# Steps
1. [Getting started](#getting-started)
2. [Homebrew](#homebrew)
3. [Programs](#programs)
4. [Shell](#shell)
5. [Node](#node)

# Getting started
Go through the setup assistant to define your language, time zone, Apple ID, and so on. Once done, update your macOS to get the latest security updates and patches.

# Homebrew
Install the [Homebrew](https://brew.sh/) package manager. Homebrew helps you install almost any package or app from the command line.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
After installation, update it:
```
brew update
```

# Programs
Below is a list of useful programs you might want to install and you can use Homebrew to do it.
`brew cask` installs macOS apps, fonts, plugins, and other non-open source software. Remove the lines you don't want from the command and run it in your Terminal.
Other _Core_: make, travis
Other _Cask_: opera, docker, vlc, slack, keybase, spotify, postgres, postico, postman

```
# Core
brew install \
  git \
  yarn

# Cask
brew cask install \
  visual-studio-code \
  google-chrome \
  firefox \
  rectangle \
  iterm2
```

# Shell
Catalina comes with **[zsh](http://zsh.sourceforge.net/)** as the default _shell_. Install **[Oh My Zsh](https://ohmyz.sh/)** for sensible defaults and themes.
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

# Node
Use [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm/blob/master/README.md) to install Node.js. This allows you to easily switch between Node versions.
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
Restart the terminal and install Node's latest version.
```
nvm install node
```
After installation, you can confirm versions by running the commands `node -v` and `npm -v`.

## Usage (for later)
If you want to install a new version of Node.js and migrate npm packages from a previous version.
```
nvm install node --reinstall-packages-from=node
```
* List installed versions of node (via nvm): `nvm ls`
* List available remote versions of node: `nvm ls-remote`
* Install specific version of node (example): `nvm install X.X.X`
* Set default version of node: `nvm alias default X.X.X`
* Switch version of node: `nvm use X.X.X`
