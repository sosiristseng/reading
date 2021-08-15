# Input methods


Input methods enable multilingual inputs including CJK (Chinese, Japanese, Korean).

<!--more-->

## Fcitx5

[Fcitx](https://wiki.archlinux.org/index.php/Fcitx) is a lightweight input method framework aimed at providing environment independent language support for Linux. The development energy is mainly focused on the new [version 5](https://wiki.archlinux.org/index.php/Fcitx5) release.

- `pacman` (Arch, Manjaro, enOS, ...)
  ```bash
  sudo pacman -S fcitx5-im fcitx5-chewing fcitx5-material-color
  ```
- `apt` (Ubuntu 21.04+)
  ```bash
  sudo apt install fcitx5 fcitx5-chewing  citx5-material-color
  ```

Attach these lines to `~/.xprofile` or `~/.profile`.

```bash
export INPUT_METHOD=fcitx5
export GTK_IM_MODULE=fcitx5
export QT_IM_MODULE=fcitx5
export XMODIFIERS=\@im=fcitx5
```

## ibus

[ibus](https://github.com/ibus/ibus) is an input method framework using DBUS, integrating better with the GNOME desktop environment.

- `apt` (Ubuntu)
  ```bash
  sudo apt install ibus ibus-chewing
  ```
- `pacman` (Arch, Manjaro, enOS, ...)
  ```bash
  sudo pacman -S ibus ibus-chewing
  ```

If `ibus` is not loaded at login, attach the following lines to `~/.xprofile` or `~/.profile`.

```bash
# ~/.xprofile
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
ibus-daemon -drx
```

