#+TITLE: Readme

#+STARTUP: indent
#+TITLE: macOS Setup Guide

* Table of contents :toc:
  - [[#prerequisites][Prerequisites]]
- [[#install][Install]]
  - [[#brew][Brew]]
  - [[#emacs][Emacs]]
  - [[#nvm][NVM]]
  - [[#zsh][Zsh]]
  - [[#github-cli][GitHub CLI]]
  - [[#miscellaneous][Miscellaneous]]

** Prerequisites
*** You need to copy your ssh-keys to the new maschine and correct the file mode.

#+BEGIN_SRC shell
chmod 600 ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_rsa.pub
chmod 644 ~/.ssh/known_hosts
chmod 755 ~/.ssh
#+END_SRC

*** Installing brew

#+BEGIN_SRC shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#+END_SRC

*** Install chezmoi

#+BEGIN_SRC shell
brew install chezmoi
#+END_SRC

*** Cloning the dotfiles

#+BEGIN_SRC shell
chezmoi init git@github.com:Jason-Kennemer/dotfiles.git
#+END_SRC

* Install
** Brew
*** Install packages wiht brew bundle

#+BEGIN_SRC shell
brew bundle
#+END_SRC

** Emacs
*** Install doom-emacs with my configuration

#+BEGIN_SRC shell
git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
cp --recursive ~/Projects/dotfiles/.doom.d ~/.doom.d
~/.emacs.d/bin/doom install
~/.emacs.d/bin/doom sync
#+END_SRC

** NVM

#+BEGIN_SRC
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
source .zshrc
nvm install node
#+END_SRC

** Zsh

Install oh my zsh
#+BEGIN_SRC shell
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
#+END_SRC

** GitHub CLI

#+BEGIN_SRC shell
gh auth login --web
#+END_SRC

** Miscellaneous
*** macOS
**** Alfred/Spotlight

Replace spotlight with alfred. Uncheck all spotlight indexes in the system preferences and deactivate the shortcuts for it.

**** Enable repeating key presses
#+BEGIN_SRC shell
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false
#+END_SRC

**** Change default screenshot folder

#+BEGIN_SRC shell
defaults write com.apple.screencapture location /Users/jkennemer/Downloads/ && killall SystemUIServer
#+END_SRC