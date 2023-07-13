## WSL

https://docs.microsoft.com/en-us/windows/wsl/install

```
$ wsl --set-default-version 2
$ wsl --install -d ubuntu
```

## ArchWSL

https://github.com/yuk7/ArchWSL

```
$ sudo pacman-key --init
$ sudo pacman-key --populate
$ sudo pacman -Syy archlinux-keyring
$ sudo pacman -Syyuu
$ sudo pacman -Sy wget openssh
```

## Yay

https://github.com/Jguer/yay

```
$ sudo pacman -Sy --needed git base-devel
$ git clone https://aur.archlinux.org/yay.git
$ cd yay
$ makepkg -si
```

## ZSH

https://github.com/romkatv/powerlevel10k

```
$ yay -Sy zsh
$ yay -S --noconfirm zsh-theme-powerlevel10k-git
$ echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
$ chsh -s /usr/bin/zsh
```

### zsh-autosuggestions

https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#manual-git-clone

```
$ git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
$ echo 'source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh' >>~/.zshrc
```

### zsh-syntax-highlighting

https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md#in-your-zshrc

```
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
$ echo 'source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh' >>~/.zshrc
```

### zsh-history-substring-search

https://github.com/zsh-users/zsh-history-substring-search

```
$ git clone https://github.com/zsh-users/zsh-history-substring-search ~/.zsh/zsh-history-substring-search
$ echo 'source ~/.zsh/zsh-history-substring-search/zsh-history-substring-search.zsh' >> ~/.zshrc
```

## Shell RUST

https://zaiste.net/posts/shell-commands-rust/


```
$ nano ~/.alias
```

```
# Git
alias g='git'
alias gck='git checkout'
alias gst='git status'
alias gps='git push'
alias gpl='git pull'
alias gcm='git commit'

# Shell
alias ls='exa --icons'
alias cat='bat'
alias find='fd'
alias grep='rg'
alias ps='procs'
```

```
$ yay -Sy bat exa fd ripgrep procs grex
$ echo 'source ~/.alias' >> ~/.zshrc
```
## ASDF

- https://asdf-vm.com/
- https://github.com/asdf-vm/asdf-plugins

### Node js

https://github.com/asdf-vm/asdf-nodejs

```
$ yay -Sy asdf-vm
$ echo 'source /opt/asdf-vm/asdf.sh' >> ~/.zshrc

$ asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
$ asdf list-all nodejs
$ asdf install nodejs 18.1.0
$ asdf global nodejs 18.1.0
$ node -v
$ npm i yarn -g
```

### Ruby

https://github.com/asdf-vm/asdf-ruby

```
$ asdf plugin add ruby https://github.com/asdf-vm/asdf-ruby.git
$ asdf list-all ruby
$ asdf install ruby 3.1.2
$ asdf global ruby 3.1.2
$ ruby -v
$ echo 'gem: --no-document' >> ~/.gemrc
$ gem install bundler rails
$ yay -Sy postgresql-libs
```

### Python

https://github.com/danhper/asdf-python

```
$ asdf plugin-add python
$ asdf list-all python
$ asdf install python 2.7.18
$ asdf install python 3.10.4
$ asdf global python 2.7.18
$ python --version
```

### PHP

https://github.com/asdf-community/asdf-php

```
$ asdf plugin-add php https://github.com/asdf-community/asdf-php.git
$ asdf list-all php
$ yay -Sy re2c gd postgresql-libs libzip
$ asdf install php 8.1.6
$ asdf global php 8.1.6
$ php -v
$ composer -v
$ php -m
$ php -m | grep mysql
$ php -m | grep imagick
$ yay -Sy imagemagick
$ pecl install imagick
$ echo "extension=imagick.so" >> $(asdf where php)/conf.d/php.ini
```

### Java

https://github.com/halcyon/asdf-java

```
$ asdf plugin-add java https://github.com/halcyon/asdf-java.git
$ asdf list-all java
$ asdf install java openjdk-18.0.1.1
$ asdf global java openjdk-18.0.1.1
$ java -version
$ echo 'source ~/.asdf/plugins/java/set-java-home.zsh' >> ~/.zshrc
```

## `.zshrc` final (Linux)

```sh
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# Initialize autocompletion
autoload -U compinit && compinit

# History setup
setopt APPEND_HISTORY
setopt SHARE_HISTORY
HISTFILE=$HOME/.zhistory
SAVEHIST=1000
HISTSIZE=999
setopt HIST_EXPIRE_DUPS_FIRST
setopt EXTENDED_HISTORY

# Autocompletion using arrow keys (based on history)
bindkey '\e[A' history-search-backward
bindkey '\e[B' history-search-forward

# Home, End, Insert and Delete keys
bindkey  "^[[H"  beginning-of-line
bindkey  "^[[F"  end-of-line
bindkey  "^[[3~" delete-char
bindkey  "^H"    backward-delete-word

# No beep
setopt NO_BEEP

source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source ~/.zsh/zsh-history-substring-search/zsh-history-substring-search.zsh

source /opt/asdf-vm/asdf.sh

source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

# Aliases
# Git
alias g='git'
alias gck='git checkout'
alias gst='git status'
alias gps='git push'
alias gpl='git pull'
alias gcm='git commit'

# Shell
alias ls='exa --icons'
alias cat='bat'
alias find='fd'
alias grep='rg'
alias ps='procs'
```