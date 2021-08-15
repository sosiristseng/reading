# Neon Postinstall


Things to do after installing KDE neon 20.04.

<!--more-->

## Post install script

Save this list in `pkgs.txt`

```txt
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
muon
apt-xapian-index
neofetch
appimagelauncher
linux-xanmod
kubuntu-driver-manager
kio-extras
gnome-keyring

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
fonts-wqy-microhei
fonts-wqy-zenhei
fonts-open-sans

# Editors
typora
zotero
libreoffice
kate
```

Run the following scripts

### Change package server to NCHC (Taiwan server)

```bash
# Setup NCHC mirror
sudo -v
sudo sed -i 's/us.archive.ubuntu.com/free.nchc.org.tw/g' /etc/apt/sources.list
sudo sed -i 's/archive.ubuntu.com/free.nchc.org.tw/g' /etc/apt/sources.list
sudo sed -i 's/security.ubuntu.com/free.nchc.org.tw/g' /etc/apt/sources.list
```

### Setup 3rd party repos

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

sudo add-apt-repository -y ppa:git-core/ppa                 # Latest Git (stable)
sudo add-apt-repository -y ppa:alessandro-strada/ppa        # Google drive client
sudo add-apt-repository -y ppa:libreoffice/ppa              # Latest Libreoffice
sudo add-apt-repository -y ppa:papirus/papirus              # Papirus icon theme
sudo add-apt-repository -y ppa:yann1ck/onedrive              # OneDrive client
sudo add-apt-repository -y ppa:kisak/kisak-mesa              # Mesa driver
sudo add-apt-repository -y ppa:qbittorrent-team/qbittorrent-stable # Qbittorrent
```

### Install packages

```bash
sudo apt update && sudo apt full-upgrade -y && sed 's/#.*$//' pkgs.txt | xargs sudo apt install -y

[[ -x "$(command -v pip3)" ]] && pip3 install -U --user glances bpytop jill youtube-dl
```

## Nvidia GPU

Nvidia CUDA 11 runtime and compatible [GPU driver](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=2004&target_type=debnetwork).

```bash
NVREPO=https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64

# Pin the repo to higher priority
wget -qO- "${NVREPO}/cuda-ubuntu2004.pin" | sudo tee /etc/apt/preferences.d/cuda-repository-pin-600 > /dev/null

# Add keys
wget -qO- "${NVREPO}/7fa2af80.pub" | sudo tee /etc/apt/trusted.gpg.d/nvidia-cuda.asc > /dev/null

# Add repo entry
echo "deb ${NVREPO} /" | sudo tee /etc/apt/sources.list.d/cuda.list > /dev/null
sudo apt update && sudo apt full-upgrade -y && sudo apt -y install cuda
```

## System Settings

- Double click instead of single `Workspace behavior` -> `General behavior` -> `click behavior`
- You may disable the KDE `wallet` subsystem.
- Start with an empty session in `Desktop session`
- Disable also index file content in `File search`
- Reduce swap use: `echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf`
- Add `ibus-daemon -drx` in autostart

## Download binaries if needed

- [Telegram](https://telegram.org/)
- [MarkText (AppImage)](https://github.com/marktext/marktext)
- [FreeFileSync](https://freefilesync.org/)
- [Starship](https://starship.rs/)
- [Hugo](https://github.com/gohugoio/hugo/releases/)
- [Pandoc](https://github.com/jgm/pandoc/releases/)
- [Virtualbox](https://www.virtualbox.org/)

