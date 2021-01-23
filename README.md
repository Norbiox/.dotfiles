# .dotfiles
My dotfiles and other configuration stuff. Use as git bare repository

## Installation
To clone this repository and use its all goodies in your linux installation use this script:
```
#!/bin/sh
echo ".cfg" >> .gitignore
git clone --bare <git-repo-url> $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
mkdir -p .config-backup && \
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
config checkout
config config --local status.showUntrackedFiles no
```
Above script will download this repo into your home directory, store your current dotfiles in .config-backup directory and install all scripts and configs from this repository.
