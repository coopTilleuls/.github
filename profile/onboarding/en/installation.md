# Installation

## Software installs

### Linux

Install

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt install curl make \
    wmdocker docker-compose \
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

### Mac

Install [Brew](https://brew.sh/) then (select only the tools of interest to you, according to the languages you use):

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

Install [oh-my-zsh](https://ohmyz.sh/) and configure iTerm to use a Nerd Font (optionally, activate ligatures).

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

### Add SSH key ([docs](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification))

```bash
ssh-keygen -t ed25519 -C "name@les-tilleuls.coop"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

[Copy the key on GitHub](https://github.com/settings/ssh/new)

### Add GPG key ([docs](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification))

```bash
gpg --gen-key
gpg --list-secret-keys --keyid-format=long
			/home/elise/.gnupg/pubring.kbx
			------------------------------
			sec   rsa3072/ABCD000-THE-KEY-00000 2021-09-06 [SC] [expires: 2023-09-06]
			      ABCD000000000ABCD000-THE-KEY-00000
			uid                 [ultimate] Name  <name@les-tilleuls.coop>
			ssb   rsa3072/6E045DB94B4CB3BE 2021-09-06 [E] [expires: 2023-09-06]
git config --global user.signingkey ABCD000-THE-KEY-00000
gpg --armor --export ABCD000-THE-KEY-00000 | xclip -selection clipboard
```

[Then copy the key on GitHub](https://github.com/settings/gpg/new)

### .gitignore global

```bash
wget https://raw.githubusercontent.com/coopTilleuls/.github/main/profile/public/dotfiles/.gitignore_global -O ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

---

## Configurations code editors

> complete according to your preferences

- Plugins for PHPStorm : Symfony / PHP Toolbox / PHP Inspections / IdeaVim
- Plugins for VS Code : eslint / intelephense
