---
title: "VS Code"
subtitle: ""
date: 2021-08-21T23:40:34+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: [linux, apps]
categories: [Linux, Applications]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
---

[Visual Studio Code](https://code.visualstudio.com) is a lightweight but powerful source code editor which runs on your desktop and is available for Linux, macOS and Windows.

<!--more-->

## Installation

- [Offical binaries](https://code.visualstudio.com)

### snap

[snap](https://snapcraft.io/code)

```bash
sudo snap install code --classic
```

## Windows

[chocoLlatey: VS code](https://community.chocolatey.org/packages/vscode)

```bash
choco install vscode
```

## Ubuntu-base

Setup its deb repository.

```bash
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/packages.microsoft.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list > /dev/null

sudo apt update && sudo apt install code
```

## Arch-based

[AUR](https://aur.archlinux.org/packages/visual-studio-code-bin/)

```bash
paru -S visual-studio-code-bin
```
