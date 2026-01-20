# Installation

## Software installs

### Linux

Install

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt install curl make \
    docker docker-compose \
    software-properties-common \
    php8.0 libapache2-mod-php8.0 \
    xclip clipit \
    zsh
sudo snap install --classic phpstorm \
    code \
    node

sudo usermod -aG docker $USER  # you will need to restart your session
```

- [oh-my-zsh](https://ohmyz.sh/) or alternatives

#### Chiffrer son répertoire home avec ecryptfs (Ubuntu, Debian, etc.)

Cela protégera vos données et les données des projets en cas de perte ou vol de votre ordinateur.

1. `sudo apt install ecryptfs-utils`
2. Suivre ce guide : https://doc.ubuntu-fr.org/ecryptfs#chiffrer_sonhome

### Mac

Installer [Brew](https://brew.sh/) puis (sélectionnez uniquement les outils qui vous intéressent suivant le(s) langage(s) que vous utilisez):

    brew tap homebrew/cask-fonts
    brew install git zsh curl node neovim \
    	php composer php-cs-fixer \
    	minikube helm doctl \
    	go golangci-lint goreleaser
    	brew install --cask \
    	firefox google-chrome iterm2 font-fira-code-nerd-font docker jetbrains-toolbox gpg-suite \
    	visual-studio-code \
    	lens \
    	zoom microsoft-teams slack discord

Installer [oh-my-zsh](https://ohmyz.sh/) et configurer iTerm pour utiliser une Nerd Font (optionnellement, activer les ligatures).

## dotfiles

- [handy lists of aliases](/profile/public/dotfiles/.aliases) to add to `.bashrc` or `.zshrc`

## Git

### basic config

```bash
git config --global user.name "name"
git config --global user.email "name@les-tilleuls.coop"
git config --global core.editor "vim"

git config --global alias.pull "pull --rebase"
git config --global alias.merge "merge --no-ff"
```

### Authentificate to Github and signing commits using SSH Key

Generate SSH key

```bash
ssh-keygen -t ed25519 -C "name@les-tilleuls.coop"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

[Copy the key on GitHub](https://github.com/settings/ssh/new), do it twice :
- once for Key type "Authentification Key"
- once for Key type "Signing commits"

```bash
git config --global commit.gpgsign true
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
```

To check if it's working, create a new git repository on any empty dir :
```bash
git init
git commit --allow-empty --message="Testing SSH signing"
# If working properly, output will be:
[main 9xxx104] Testing SSH signing
```

### `.gitignore` global

```bash
wget https://raw.githubusercontent.com/coopTilleuls/.github/main/profile/public/dotfiles/.gitignore_global -O ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

Ajouter les `.idea`, `*.workspace`, etc

---

## Configurations code editors

> à compléter en fonction de vos préférences

- Plugins pour PHPStorm : Symfony / PHP Toolbox / PHP Inspections / IdeaVim
- Plugins pour VS Code : eslint / intelephense
