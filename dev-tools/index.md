# Development tools


> Compilers, IDEs

<!--more-->

## GCC compiler set

> `gcc` and friends.

- `apt`
  ```bash
  sudo apt install build-essential
  ```
- `pacman`
  ```bash
  sudo pacman -S base-devel
  ```
- `choco` (Windows)
  ```bash
  choco install mingw
  ```

## Docker

> with optional CUDA support

Installation:
- Ubuntu: Setup deb repository
  ```bash
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

  echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

  sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io

  # CUDA runtime support (optional)
  distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
  curl -fsSL "https://nvidia.github.io/nvidia-docker/gpgkey" | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-docker-keyring.gpg
  curl -fsSL "https://nvidia.github.io/nvidia-docker/${distribution}/nvidia-docker.list" | sudo tee /etc/apt/sources.list.d/nvidia-docker.list > /dev/null
  sudo apt update && sudo apt install nvidia-container-toolkit
  sudo systemctl restart docker
  ```
- Arch and derivatives: install docker and [activate](https://wiki.archlinux.org/title/Docker) it.
  ```bash
  sudo pacman -S docker
  sudo systemctl enable --now docker.service

  # CUDA runtime support
  paru -S nvidia-container-toolkit
  sudo systemctl restart docker
  ```

Test your installation

```bash
sudo docker docker run hello-world

sudo docker run --gpus all nvidia/cuda:11.0-base nvidia-smi
```

## Gitkraken

Free Git GUI for Windows, Mac, Linux. But requires Login.

To install:
- [offical binaries](https://www.gitkraken.com/)
- [snap](https://snapcraft.io/gitkraken)
  ```bash
  sudo snap install gitkraken --classic
  ```
- [AUR](https://aur.archlinux.org/packages/gitkraken/)
  ```bash
  paru -S gitkraken
  ```
- [choco](https://community.chocolatey.org/packages/gitkraken)
  ```bash
  choco install gitkraken
  ```

## NodeJS

[NodeJS](https://nodejs.org/) is a JavaScript runtime built on Chrome's V8 JavaScript engine.

**Installation**

- [Node Version Manager (nvm)]()
- [snap](https://snapcraft.io/node)
  ```bash
  sudo snap install node --classic
  ```
- [choco](https://community.chocolatey.org/packages/nodejs)
  ```bash
  choco install nodejs
  ```

## VS Code

[Visual Studio Code](https://code.visualstudio.com) is a lightweight but powerful source code editor which runs on your desktop and is available for Linux, macOS and Windows.

**Installation**

- [Offical binaries](https://code.visualstudio.com)
- [snap](https://snapcraft.io/code)
  ```bash
  sudo snap install code --classic
  ```
- [choco](https://community.chocolatey.org/packages/vscode)
  ```bash
  choco install vscode
  ```
- Setup deb repository (in Ubuntu)
  ```bash
  curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/packages.microsoft.gpg

  echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list > /dev/null

  sudo apt update && sudo apt install code
  ```
- [AUR](https://aur.archlinux.org/packages/visual-studio-code-bin/)
  ```bash
  paru -S visual-studio-code-bin
  ```

