# Installation

## Software installs

### Linux

Install

#### Ubuntu

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

#### Debian

Debian propose des paquets moins à jour qu’Ubuntu, mais ne force pas l’utilisation de snap, ce qui évite des problèmes de lenteur au lancement de certaines applications snap. Le fait de ne pas avoir la dernière version de PHP n’est pas handicapant avec les projets dockerisés qui ont leur propre version de PHP.  

Note : testé avec Debian 13, ça installe PHP 8.4.

```bash
sudo apt install curl make \
    docker.io docker-compose \
    php-cli php-curl php-xml \
    xclip

sudo usermod -aG docker $USER  # you will need to restart your session
```

PhpStorm : télécharger l’archive https://www.jetbrains.com/phpstorm/download/?section=linux la décompresser puis lancer le fichier `PhpStorm/bin/phpstorm`.
Une fois dans PHPStorm, ouvrir le menu « Tools » et cliquer sur « Create Desktop Entry… ». On peut ensuite lancer PHPStorm depuis son environnement de bureau.

Firefox : par défaut Debian fournit la version ESR (support étendu), pour avoir la dernière version on peut [utiliser les dépôts APT de Mozilla](https://support.mozilla.org/fr/kb/installer-firefox-linux#w_installation-par-paquet-deb-pour-les-distributions-basees-sur-debian-recommande) ou [lancer à partir de l’archive](https://support.mozilla.org/fr/kb/installer-firefox-linux#w_installation-locale-de-firefox-dans-un-compte-utilisateur).

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
