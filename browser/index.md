# Web Browsers


Browsing the web.

<!--more-->

## Brave

[Brave](https://brave.com/), a web browser focused on speed, privacy, (and crypto).

- DEB repo
  ```bash
  sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
  echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
  sudo apt update &&  sudo apt install brave-browser
  ```
- [AUR](https://aur.archlinux.org/packages/brave-bin/)
  ```bash
  paru -S brave-bin
  ```
- [choco](https://community.chocolatey.org/packages/brave)
  ```bash
  choco install brave
  ```

## Vivaldi

[Vivaldi Browser](https://vivaldi.com/) is a fast, private, customizable, and secure browser that blocks ads and trackers.

- Download and install the installer from the [official website](https://vivaldi.com/).
- Deb repo
  ```bash
  curl -fsSL https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/vivaldi.gpg
  echo "deb [signed-by=/usr/share/keyrings/vivaldi.gpg] https://repo.vivaldi.com/archive/deb/ stable main" | sudo tee /etc/apt/sources.list.d/vivaldi.list > /dev/null
  sudo apt update && sudo apt install vivaldi-stable
  ```
- `pacman`
  ```bash
  sudo pacman -S vivaldi vivaldi-ffmpeg-codecs
  ```
- `choco`
  ```bash
  choco install vivaldi
  ```

