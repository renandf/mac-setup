# New (or formatted) Mac setup
Steps I usually follow to setup a new or formatted Mac focused on front-end development as a designer

Inspired by [Tania Rascia's article](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/).

## Steps
1. [Getting started](#getting-started)
2. [Homebrew](#homebrew)
3. [Programs](#programs)
4. [Shell](#shell)
5. [Node](#node)
6. [Git](#git)
7. [Settings](#settings)
8. [Application settings](#application-settings)

## Getting started
Go through the setup assistant to define your language, time zone, Apple ID, and so on. Once done, update your macOS to get the latest security updates and patches.

## Homebrew
Install the [Homebrew](https://brew.sh/) package manager. Homebrew helps you install almost any package or app from the command line.

* To check if Homebrew is installed and what version: `brew --version`
* To install it:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
* To update it: `brew update`

From time to time (maybe at the start of a new project), run this command to update Homebrew and everything you have installed with it.
```
brew update && brew upgrade && brew cleanup && brew doctor
```

## Programs
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

## Shell - Oh My Zsh
Catalina comes with **[zsh](http://zsh.sourceforge.net/)** as the default _shell_. Install **[Oh My Zsh](https://ohmyz.sh/)** for sensible defaults and themes.
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Spaceship Prompt
**[Spaceship](https://github.com/denysdovhan/spaceship-prompt)** is a minimalistic, powerful and extremely customizable Zsh prompt.

Clone the repo:
```
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
```
Symlink `spaceship.zsh-theme` to your oh-my-zsh custom themes directory:
```
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```
Open your `.zshrc` (If using VS Code, `code ~/.zshrc`) and set `ZSH_THEME="spaceship"` in there.

### Dracula Theme
**[Dracula](https://draculatheme.com/iterm)** is a nice dark theme available for iTerm (and [many others](https://draculatheme.com/)).
Clone the repo locally into a folder of your choice:
```
git clone https://github.com/dracula/iterm.git
```
1. Go to *iTerm2 > Preferences > Profiles > Colors Tab*
2. Open the *Color Presets...* drop-down in the bottom right corner
3. Select *Import...* from the list
4. Select the `Dracula.itermcolors` file
5. Select the *Dracula* from Color Presets...

## Node
Use [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm/blob/master/README.md) to install Node.js. This allows you to easily switch between Node versions.
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
Restart the terminal and install Node's latest version.
```
nvm install node
```
After installation, you can confirm versions by running the commands `node -v` and `npm -v`.

### Usage (for later)
If you want to install a new version of Node.js and migrate npm packages from a previous version.
```
nvm install node --reinstall-packages-from=node
```
* List installed versions of node (via nvm): `nvm ls`
* List available remote versions of node: `nvm ls-remote`
* Install specific version of node (example): `nvm install X.X.X`
* Set default version of node: `nvm alias default X.X.X`
* Switch version of node: `nvm use X.X.X`

## Git
Create your `.gitconfig` file to set your [global configuration](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).
```
vi ~/.gitconfig
```
* Insert mode using `vi` = `i`
* Leave insert mode = `esc`
* Quit and save = `:wq`

Insert your details and create some aliases (e.g. run `git s` instead of `git status`).
```
[user]
  name   = Firstname Lastname
  email  = you@example.com
[github]
  user   = username
[alias]
  a      = add
  cm     = commit -m
  s      = status
  cob    = checkout -b
  co     = checkout
  pu     = push -u origin
  lg     = log --graph --decorate --pretty=format:'%C(yellow)%h%Creset%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)%an%Creset'
```

## Settings
* To get the Home folder in the finder, press `CMD + SHIFT + H` and drag the home folder to the sidebar
* Go to `Finder » Preferences » Advanced` and check `Show all filename extensions`
* Make Google Chrome default browser

### Dock
* Automatically hide and show Dock
* Show indicators for open applications

### Keyboard
* Key Repeat » Fast
* Delay Until Repeat » Short
* Turn keyboard backlight off after 10s of inactivity
* Disable "Correct spelling automatically"
* Disable "Capitalize words automatically"
* Disable "Add period with double-space"
* Disable "Use smart quotes and dashes"

### Security & Privacy
* Allow apps downloaded from App Store and identified developers
* Turn FileVault On (makes sure SSD is securely encrypted)
* Turn Firewall On (extra security measure)

### Sharing
* Change computer's name
* Make sure all file sharing is disabled

### Users & Groups
* Add "Rectangle" to Login items
* Remove Chrome from the Login items

### Modify defaults
```
# Show Library folder
chflags nohidden ~/Library

# Show hidden files
defaults write com.apple.finder AppleShowAllFiles YES

# Show path bar
defaults write com.apple.finder ShowPathbar -bool true

# Show status bar
defaults write com.apple.finder ShowStatusBar -bool true

# Prevent left and right swipe through history in Chrome
defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool false
```
Restart Finder with `killall Finder`

## Application settings
### Visual Studio Code
Use [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) to keep VS Code updated accross diferente machines.
* Upload shortcut: `Shift + Option + U`
* Download shortcut: `Shift + Option + D`
