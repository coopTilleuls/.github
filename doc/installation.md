# Installation

## Software installs

### Linux

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

- todo: oh-my-zsh (+plugins)

### Mac

- iTerm
- [Brew](https://brew.sh/)

## dotfiles

(to update) [Sample dotfiles here](https://github.com/eliseduverdier/dotfiles)

## Git

### basic config

```bash
git config --global user.name "name"
git config --global user.email "name@les-tilleuls.coop"
git config --global core.editor "vim"

git config --global alias.pull "pull --rebase"
git config --global alias.merge "merge --no-ff"
```

### Add SSH key [docs](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification)

```bash
sudo apt-get install xclip
ssh-keygen -t ed25519 -C "name@les-tilleuls.coop"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

Copy the key on github [here](https://github.com/settings/ssh/new)

### Add GPG key [docs](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)

```bash
gpg --gen-key
gpg --list-secret-keys --keyid-format=long
			/home/elise/.gnupg/pubring.kbx
			------------------------------
			sec   rsa3072/ABCD000-THE-KEY-00000 2021-09-06 [SC] [expires: 2023-09-06]
			      ABCD000000000ABCD000-THE-KEY-00000
			uid                 [ultimate] MName  <name@les-tilleuls.coop>
			ssb   rsa3072/6E045DB94B4CB3BE 2021-09-06 [E] [expires: 2023-09-06]
git config --global user.signingkey ABCD000-THE-KEY-00000
gpg --armor --export ABCD000-THE-KEY-00000 xclip -selection clipboard
```

Then copy the key on github [here](https://github.com/settings/gpg/new)

### gitignore

```bash
wget https://gist.githubusercontent.com/octocat/9257657/raw/3f9569e65df83a7b328b39a091f0ce9c6efc6429/.gitignore -O ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

Ajouter les `.idea`, `*.workspace`, etc

## plugins

### phpstorm

symfony / ideavim ...

### vscode

eslint / intelephense / ...
