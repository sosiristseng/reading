---
title: "Install Vialdi browsers"
subtitle: ""
date: 2021-06-19T00:04:16+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: [web, vivaldi]
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

[Vivaldi Browser](https://vivaldi.com/) is a fast, private, customizable, and secure browser that blocks ads and trackers.

<!--more-->

## Official executable

Download and run the installer from the [official website](https://vivaldi.com/).

## Ubuntu / PoPOS

```bash
curl -fsSL https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/vivaldi.gpg
echo "deb [signed-by=/usr/share/keyrings/vivaldi.gpg] https://repo.vivaldi.com/archive/deb/ stable main" | sudo tee /etc/apt/sources.list.d/vivaldi.list > /dev/null
sudo apt update && sudo apt install vivaldi-stable
```

## Arch-based

```bash
sudo pacman -S vivaldi vivaldi-ffmpeg-codecs
```

## Windows

Via `chocolatey`

```bash
choco install vivaldi
```
