# New (or formatted) Mac setup
Steps I usually follow to setup a new or formatted Mac focused on front-end development as a designer

Inspired by [Tania Rascia's article](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/).

# Steps
1. [Getting started](#getting-started)
2. [Homebrew](#homebrew)
3. [Programs](#programs)
4. [Shell](#shell)

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
