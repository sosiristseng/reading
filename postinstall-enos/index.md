# Endeavour OS Postinstall


Thing to do after installing [endeavour OS](https://endeavouros.com/).

<!--more-->

💡 You can [add your own additional packages during install](https://discovery.endeavouros.com/installation/add-packages-to-be-installed-in-addition-to-desktop-chosen/2021/04/) by adding `user_pkglist.txt` in the home directory of the enOS live environment.

```txt
akm
pigz
lzop
zstd
base-devel
python-pip
cmake
git
git-lfs
yay
texlive-core
pandoc
pandoc-citeproc
pandoc-crossref
libreoffice-fresh
zotero
vivaldi
vivaldi-ffmpeg-codecs
cifs-utils
gufw
telegram-desktop
htop
bpytop
zsh
timeshift
cronie
docker
appimagelauncher
parallel
trash-cli
ibus
ibus-chewing
ttf-roboto
ttf-fira-sans
noto-fonts
noto-fonts-cjk
noto-fonts-emoji
wqy-microhei
wqy-zenhei
ttf-opensans
smplayer
smplayer-skins
smplayer-themes
ffmpeg
youtube-dl
plasma-browser-integration
```

## Find fastest repository server

Click `select mirror` in the welcome APP and save the mirror list.

## Update kernel

Run `akm` in the terminal.

## Install pikaur

Instatuctions from [its Github repo](https://github.com/actionless/pikaur).

```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/pikaur.git
cd pikaur
makepkg -fsri
```

## Postinstall script

Save the content below as `pkgs.txt`

```txt
# Development
pikaur
pamac-aur
pigz
lzop
zstd
base-devel
python-pip
cmake
git
git-lfs
gitkraken
visual-studio-code-bin

# Text editing
texlive-core
tectonic-bin
pandoc
pandoc-citeproc
pandoc-crossref
typora
libreoffice-fresh
zotero

# Network
vivaldi
vivaldi-ffmpeg-codecs
brave-bin
cifs-utils
gufw
telegram-desktop
anydesk

# System
htop
bpytop
zsh
timeshift
cronie
docker
appimagelauncher
parallel
trash-cli

# Input methods
ibus
ibus-chewing

# Fonts
ttf-roboto
ttf-fira-sans
noto-fonts
noto-fonts-cjk
noto-fonts-emoji
wqy-microhei
wqy-zenhei
ttf-opensans
nerd-fonts-hack

# Multimedia
smplayer
smplayer-skins
smplayer-themes
ffmpeg
youtube-dl

# Themes for KDE
plasma-browser-integration
kvantum-qt5
kvantum-theme-materia
papirus-icon-theme
materia-gtk-theme
materia-kde
qogir-icon-theme-git
qogir-gtk-theme-git
qogir-kde-theme-git
```

Run this script:

```bash
# First phase system setup with services
sudo pikaur -S --noconfirm --needed docker timeshift cronie
sudo systemctl enable --now cronie.service
sudo systemctl enable --now fstrim.timer
sudo systemctl enable --now docker.service
sudo systemctl disable org.cups.cupsd.service || echo "CUPS not installed!"
sudo systemctl enable --now org.cups.cupsd.socket || echo "CUPS not installed!"

# Install the rest
# Check pkgs.txt before running the line below
sed 's/#.*$//' pkgs.txt | xargs sudo pikaur -S --noconfirm --needed
```

## Ibus config
Paste the contents to `~/.xprofile`

```bash
# ~/.xprofile
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
ibus-daemon -drx
```

## Environment variables

Paste the contents to `~/.profile`

```bash
[[ -d "${HOME}/.local/bin" ]] && PATH="${HOME}/.local/bin:${PATH}"
[[ -d "${HOME}/.cargo/bin" ]] && PATH="${HOME}/.cargo/bin:${PATH}"
[[ -d "${HOME}/.go/bin" ]] && PATH="${HOME}/.go/bin:${PATH}"

export BROWSER=$(command -v xdg-open)
export EDITOR=$(command -v nano)
export JULIA_NUM_THREADS=$(nproc)
export JULIA_PROJECT=@.
export ELECTRON_TRASH=trash-cli
```

## NVIDIA GPU drivers and CUDA runtime

Install Nvidia DKMS driver for all kernels and CUDA runtime:

```bash
sudo pacman -S nvidia-dkms cuda cudnn
```

## Theme settings

### KDE

- Kvantum theme: Qogir Dark
- Global theme: Qogir Dark
- Plasma style: Qogir Dark
- Application style: kvantum
- GTK style: Qogir Dark
- Window decorations: Qogir Dark
- Colors: Qogir Dark
- Fonts
  - General: Roboto medium 10.5pts
  - Monospace: Hack Nerd Font 10.5pt
- Icons: Qogir Dark
- Cursors: Qogir Dark

## Additional packages

Use `pikaur -S <pkgname>`

- [PyCharm](https://www.jetbrains.com/pycharm/): `pycharm-community-jre`
- [Anydesk](https://anydesk.com/en/downloads/linux): `anydesk-bin`
- Java runtime: `jre-openjdk`
- Flatpak: `flatpak`
- Snap: `snapd`
- Google drive client: `google-drive-ocamlfuse-opam`
- Onedrive client: `onedrive-abraunegg`
- FreeFileSync: `freefilesync-bin`
- Bottom: `bottom-bin`

### VirtualBox

Install the packages and add your username to the `vbox` group.

```bash
sudo pikaur -S virtualbox virtualbox-guest-iso net-tools virtualbox-ext-oracle

sudo gpasswd -a username vboxusers
```

