---
title: "Docker with CUDA support"
subtitle: ""
date: 2021-06-18T23:48:23+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: [linux, GPU]
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

Setup docker with GPU (CUDA) containers.

<!--more-->

## Ubuntu-based

Setup the deb repository **for the LTS versions**

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

## Arch-based

install docker and [activate](https://wiki.archlinux.org/title/Docker) it.


```bash
sudo pacman -S docker
sudo systemctl enable --now docker.service

# CUDA runtime support
paru -S nvidia-container-toolkit
sudo systemctl restart docker
```

## Test your installation

```bash
sudo docker docker run hello-world

sudo docker run --gpus all nvidia/cuda:11.0-base nvidia-smi
```
