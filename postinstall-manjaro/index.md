# Manjaro Postinstall


Things to do after installing [Manjaro](https://manjaro.org/).

<!--more-->

You can also try [the monthly release installation medium](https://github.com/manjaro/release-review).

## Find fastest repository server

Set mirror in `pamac` settings.

## Install pikaur

Enable AUR in `pamac` and install `pikaur`.

## Update kernel and / or drivers

Use manjaro settings.

## Install packages

Save the content below as `pkgs.txt`

```md
# Development
pikaur
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

Run the following script:

```bash

# First phase system setup with services
sudo pikaur -S --noconfirm --needed docker
sudo systemctl enable --now fstrim.timer
sudo systemctl enable --now docker.service

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
export ELECTRON_TRASH=kioclient5
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

