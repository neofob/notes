Setting `iTerm2` with `powerlevel9k` on Mac
===========================================
*A simple guide to setup stuff without too much of googling to save time for doodling*

  1. install `git`, `vim-nox`, `mc`, `iTerm2`
  2. install Adobe `Source Code Pro` font
  3. install `oh-my-zsh`
  4. install `powerlevel9k`

##1. Install a few good packages
```
brew install git vim-nox mc iTerm2
```

##2. Install Adobe `Source Code Pro` font
  * download the font from github
  * install the fonts at the directory `source-code-pro/OTF` (Use `Finder` to
  open `*.otf` files with `Font Book`, think differently in Mac)
  * set your terminal font setting to this flashy font; preferably `iTerm2` by now
```
mkdir ~/src
cd ~/src
git clone -b release https://github.com/adobe-fonts/source-code-pro
```

##3. Install `oh-my-zsh`
*What could go wrong? --famous last words*
  * install `oh-my-zsh`
  * edit `.zshrc`
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
**Add this line to `~/.zshrc`**
```
export ZSH=/Users/YOURNAME/.oh-my-zsh
```

##4. Install `powerlevel9k`
  * clone `powerlevel9k`
  * make symlink to powerlevel9k in `oh-my-zsh/custom`
  * update your `~/.zshrc`
```
cd ~/src
git clone https://github.com/bhillburn/powerlevel9k
ln -s ~/src/powerlevel9k ~/.oh-my-zsh/custom/
```
**Replace the line `ZSH_THEME=` with this**
```
ZSH_THEME="powerlevel9k/powerlevel9k"
```

Open a new `iTerm2` terminal, tab or not, you should see a fancy prompt.

_written by: tuan t. pham_
