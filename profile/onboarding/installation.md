# Installation

## Software installs

### Linux

Installer

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

sudo usermod -aG docker $USER  # il faudra redémarrer la session
```

- [oh-my-zsh](https://ohmyz.sh/) ou alternatives

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

- [liste pratique d'alias](/profile/public/dotfiles/.aliases) à ajouter à `.bashrc` ou `.zshrc`

## Git

### config basique

```bash
git config --global user.name "name"
git config --global user.email "name@les-tilleuls.coop"
git config --global core.editor "vim"

git config --global alias.pull "pull --rebase"
git config --global alias.merge "merge --no-ff"
```

### S'authentifier à Github et signer ses commits avec une clé SSH

Générer une clé SSH

```bash
ssh-keygen -t ed25519 -C "name@les-tilleuls.coop"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

[Copier la clé sur GitHub](https://github.com/settings/ssh/new), le faire deux fois :
- une fois pour la clé de type "Authentification Key"
- une fois pour la clé de type "Signing commits"

```bash
git config --global commit.gpgsign true
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
```

Pour vérifier que tout fonctionne, créer un nouveau repository git sur un dossier vide :
```bash
git init
git commit --allow-empty --message="Testing SSH signing"
# Si tout va bien, l'output devrait ressembler à:
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
