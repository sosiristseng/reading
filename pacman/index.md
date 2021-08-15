# Pacman package manager


Managing `pacman` packages in Arch Linux and its derivatives (Manjaro, enOS).

<!--more-->

## Generating a list of packages

List non-AUR, explicitly installed packages:

```bash
pacman -Qnqe > pkgs.txt
```

List AUR packages:

```bash
pacman -Qqem > aurpkgs.txt
```

List all explicitly installed packages:

```bash
pacman -Qqe > allpkgs.txt
```

## Install packages from a list

```bash
paru  # Full upgrade the system first
paru -S --needed - < pkgs.txt
```

## Compilation options for AUR packages

To customize compilation options, a good starting point is to copy from the system-wide config file:

```bash
cp /etc/makepkg.conf ~/.makepkg.conf
```

to you own `~/.makepkg.conf` [makepkg@ArchWiki](https://wiki.archlinux.org/index.php/Makepkg). However,  `PKGBUILD` settings still have higher priority.

### CPU target for building optimized binaries

```txt
CFLAGS="-march=native -O2 -pipe -fstack-protector-strong -fno-plt"
CXXFLAGS="${CFLAGS}"
RUSTFLAGS="-C opt-level=2 -C target-cpu=native"
```

### Parallel compilation

```txt
MAKEFLAGS="-j$(nproc)"
```

### Compressing packages

```txt
# multiple cores on compression of xz archives
COMPRESSXZ=(xz -c -z - --threads=0)

# multiple cores on compression of zstd archives
COMPRESSZST=(zstd -c -z -q - --threads=0)

# multiple cores on compression of gz archives (requires pigz package)
COMPRESSGZ=(pigz -c -f -n)
```

And you can choose the preferred method for package compression

e.g.
```bash
PKGEXT='.pkg.tar.zst'
```

Or turn off compression completely (fastest)
x
```bash
PKGEXT='.pkg.tar'
```

## Arch User Repository (AUR)

The [Arch User Repository (AUR)](https://aur.archlinux.org) hosts community-contributed `PKGBUILD`s, instructions to download and build a packages.

While you could clone the `PKGBUILD` files and run `makepkg -si ` manually, [AUR helpers](https://wiki.archlinux.org/index.php/AUR_helpers) automate these process, giving a similar experience for installing regular packages in `pacman`.

### pikaur

[`pikaur`](https://github.com/actionless/pikaur) reviews PKGBUILDs all in once and asks all questions before installing/building, using systemd dynamic users to spawn build processes.

You can install `pikaur` by another AUR helper, for example:

```bash
paru -S pikaur
```

or install `pikaur` manually,

```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/pikaur.git
cd pikaur
makepkg -fsri
```

Afterwards, you can install AUR packages as if installing regular ones

```bash
sudo pikaur -S google-chrome
```

To update all packages

```bash
sudo pikaur -Syu
```

### paru

[`paru`](https://github.com/Morganamilo/paru) is an AUR helper written in Rust, based on [`yay`](https://github.com/Jguer/yay), an AUR helper written in Go.


```bash
yay -S paru-bin # If you don't want to compile the Rust code
# yay -S paru   # Compile paru from source
```

Or install `paru` manually,

```bash
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

Afterwards, you can install AUR packages as if installing regular ones

```bash
paru -S google-chrome
```

To update all packages

```bash
paru
```

### yay

The AUR helper, [yay](https://github.com/Jguer/yay), is directly available in Manjaro / enOS.

```bash
sudo pacman -S yay
```

Afterwards, you can install AUR packages as if installing regular ones

```bash
yay -S google-chrome
```

To update all packages

```bash
yay
```

Default options for yay could be saved using `yay --save <options>`, for example:

```bash
yay --answerclean All --answerdiff None --answerupgrade None --cleanafter --batchinstall --combinedupgrade --sudoloop --save
```

> - `--cleanafter`: clean untracked files after build.
> - `--combinedupgrade`: resolve dependency and then install both the repo and the AUR packages in one go.
> - `--sudoloop`: Loop sudo calls in the background to prevent sudo from timing out during long builds.
> - `--batchinstall`: Build all AUR packages and install them at once.

