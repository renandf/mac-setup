# New (or formatted) Mac setup
Steps I usually follow to setup a new or formatted Mac focused on front-end development as a designer

Inspired by [Tania Rascia's article](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/).

## Steps
1. [Getting started](#getting-started)
2. [Homebrew](#homebrew)
3. [Programs](#programs)
4. [Git](#git)
5. [Shell](#shell)
6. [Node](#node)
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
Open your `.zshrc` (If using VS Code, `code ~/.zshrc`) and set `ZSH_THEME="spaceship"` in there. With still open, add the following (optional) settings at the end:
```
SPACESHIP_PROMPT_ORDER=(
  user          # Username section
  dir           # Current directory section
  host          # Hostname section
  git           # Git section (git_branch + git_status)
  hg            # Mercurial section (hg_branch  + hg_status)
  exec_time     # Execution time
  line_sep      # Line break
  vi_mode       # Vi-mode indicator
  jobs          # Background jobs indicator
  exit_code     # Exit code section
  char          # Prompt character
)
SPACESHIP_USER_SHOW=always
SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_CHAR_SYMBOL="❯"
SPACESHIP_CHAR_SUFFIX=" "
```

### Fira Code Font
Spaceship requires the font **[FiraCode](https://github.com/tonsky/FiraCode/releases)** to display some nice icons. Download the latest `.zip` file from their [releases page](https://github.com/tonsky/FiraCode/releases) and [install](https://support.apple.com/en-us/HT201749) the `.ttf` files into your Mac.

Then go to *iTerm2 > Preferences > Profiles > Text* tab and change the font to `Fira Coda`. Optionally, increase the font size (**14** looks good).

### Dracula Theme
**[Dracula](https://draculatheme.com/iterm)** is a nice dark theme available for iTerm (and [many others](https://draculatheme.com/)).
Clone the repo locally into a folder of your choice:
```
git clone https://github.com/dracula/iterm.git
```
1. Go to *iTerm2 > Preferences > Profiles > Colors* tab
2. Open the *Color Presets...* drop-down in the bottom right corner
3. Select *Import...* from the list
4. Select the `Dracula.itermcolors` file
5. Select the *Dracula* from Color Presets...

### ZSH Plugins
[Zinit](https://github.com/zdharma/zinit#zinit) is a flexible and fast Zshell plugin manager. To install it, use:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/zdharma/zinit/master/doc/install.sh)"
```
Open `.zshrc` again and go to the very end, after the `### End of Zinit's installer chunk` line just added by Zinit. Add the following lines:
```
zinit light zdharma/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
```

What those plugins do?
* `zdharma/fast-syntax-highlighting`: Adds syntax highlighting while typing
* `zsh-users/zsh-autosuggestions`: Suggests commands based on your prompt's history as you type
* `zsh-users/zsh-completions`: Adds *completions* to popular tools (e.g. Yarn, Homebrew, NVM, Node) so you just need to press TAB

### ZSH inside VS Code
If you're using [Settings Sync](https://github.com/renandf/mac-setup/blob/master/README.md#visual-studio-code) and already set this in the past, skip this step.

To use *Oh My Zsh* with the font *Fira Code* inside VS Code's integrated terminal, open `settings.json` and set (search and update since these settings are already there):
```
"terminal.integrated.shell.osx": "/bin/zsh",
"editor.fontFamily": "Fira Code",
"editor.fontLigatures": true,
```

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
