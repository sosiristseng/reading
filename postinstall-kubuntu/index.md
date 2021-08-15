# Kubuntu Postinstall


Thing to do after installing Kubuntu 21.04.

<!--more-->

## Traditional Chinese in language support

Default locale in Ubuntu for traditional Chinese (Taiwan) is `lzh_TW` rather than `zh_TW`.

Setup the locale by editing the file `sudo nano /etc/locale.gen`, comment the `lzh_TW` line and uncomment the `zh_TW` line.

And then run

```bash
sudo locale-gen
```

Install the Traditional Chinese locale in `Language Support` and then set locale to `Taiwan` to solve this problem.

## Add 3rd party sources and fully upgrade

```bash
#!/usr/bin/env bash

# Add 3rd party sources and fully upgrade

sudo apt install -y apt-transport-https ca-certificates curl git gnupg-agent software-properties-common python3-pip

# Run this line if you need Wine and games
# sudo dpkg --add-architecture i386

# Brave
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list > /dev/null

# Vivaldi
curl -fsSL https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/vivaldi-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/vivaldi-keyring.gpg] https://repo.vivaldi.com/archive/deb/ stable main" | sudo tee /etc/apt/sources.list.d/vivaldi.list > /dev/null

# Anydesk
curl -fsSL https://keys.anydesk.com/repos/DEB-GPG-KEY | sudo gpg --dearmor -o /usr/share/keyrings/anydesk-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/anydesk-keyring.gpg] http://deb.anydesk.com/ all main" | sudo tee /etc/apt/sources.list.d/anydesk-stable.list > /dev/null

# Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Zotero
curl -fsSL https://github.com/retorquere/zotero-deb/releases/download/apt-get/install.sh | sudo bash

# Typora
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
echo "deb [signed-by=/usr/share/keyrings/typora-keyring.gpg] https://typora.io/ ./" | sudo tee /etc/apt/sources.list.d/typora.list > /dev/null

# Xanmod linux kernel
curl -fsSL https://dl.xanmod.org/gpg.key | sudo gpg --dearmor -o /usr/share/keyrings/xanmod-keyring.gpg
echo 'deb [signed-by=/usr/share/keyrings/xanmod-keyring.gpg] http://deb.xanmod.org releases main' | sudo tee /etc/apt/sources.list.d/xanmod-kernel.list > /dev/null

# VS Code
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/packages.microsoft.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list > /dev/null

sudo add-apt-repository -y ppa:git-core/ppa # Latest Git (stable)
sudo add-apt-repository -y ppa:alessandro-strada/ppa # Google drive client
sudo add-apt-repository -y ppa:libreoffice/ppa # Latest Libreoffice
sudo add-apt-repository -y ppa:papirus/papirus # Papirus icon theme
sudo add-apt-repository -y ppa:qbittorrent-team/qbittorrent-stable # Qbittorrent
sudo add-apt-repository -y ppa:kubuntu-ppa/backports # Kubuntu backport
sudo apt update && sudo apt full-upgrade -y
```

## Install packages

Review and save this list in `pkgs.txt`

```bash
# Developement
cmake
build-essential
git
git-lfs
python3-pip
docker-ce
docker-ce-cli
containerd.io
code

# Network
cifs-utils
vivaldi-stable
brave-browser
qbittorrent

# System
parallel
pv
zsh
progress
htop
neofetch
linux-xanmod
kio-extras
gnome-keyring
gvfs

# Locale
ibus
ibus-chewing

# Media
ffmpeg
smplayer

# Themes
papirus-icon-theme
qt5-style-kvantum-themes
qt5-style-kvantum

# Fonts
fonts-noto
fonts-open-sans

# Editors
typora
zotero
```

Then run

```bash
sed 's/#.*$//' pkgs.txt | xargs sudo apt install -y
```

## Python packages

```bash
pip install -U --user glances bpytop jill youtube-dl
```

## System Settings

- You may want to disable the KDE `wallet` subsystem.
- Start with an empty session in `Desktop session`
- Reduce swap use:
  ```bash
  echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf
  ```
- Add `ibus-daemon -drx` to `Autostart`.

## Download and install binaries if needed

- [Telegram](https://telegram.org/)
- [MarkText](https://github.com/marktext/marktext)
- [FreeFileSync](https://freefilesync.org/)
- [Starship](https://starship.rs/)
- [Hugo](https://github.com/gohugoio/hugo/releases/)
- [Pandoc](https://github.com/jgm/pandoc/releases/)
- [Virtualbox](https://www.virtualbox.org/)

