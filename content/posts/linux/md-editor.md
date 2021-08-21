---
title: "Markdown editors"
subtitle: ""
date: 2021-06-18T23:54:36+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: [linux, markdown]
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

Markdown is the email-style writing for the web by John Gruber and Aaron Swartz. This post introduces what-you-see-is-what-you-get Markdown editors.

See also

- [awesome Markdown](https://github.com/mundimark/awesome-markdown#markdown).
- [Markdown bookmarks]({{< ref "posts/research/markdown.md" >}})

<!--more-->

## Marktext

[Marktext](https://marktext.app/), a full-featured open-source what-you-see-is-what-you-get Markdown editor.

To install:
- [Official binary](https://marktext.app/)
- [AUR](https://aur.archlinux.org/packages/marktext-bin/)
  ```bash
  paru -S marktext-bin
  ```
- [choco](https://community.chocolatey.org/packages/marktext.install)
  ```bash
  choco install marktext.install
  ```

## Typora

[Typora](https://typora.io/) is a full-featured what-you-see-is-what-you-get Markdown editor.

- Add deb repository
  ```bash
  curl -fsSL https://typora.io/linux/public-key.asc | sudo gpg --dearmor -o /usr/share/keyrings/typora-keyring.gpg

  echo "deb [signed-by=/usr/share/keyrings/typora-keyring.gpg] https://typora.io/ ./" | sudo tee /etc/apt/sources.list.d/typora.list > /dev/nul
  sudo apt update && sudo apt install typora
  ```
- [AUR](https://aur.archlinux.org/packages/typora/))
  ```bash
  paru -S typora
  ```
- [choco](https://community.chocolatey.org/packages/typora)
  ```bash
  choco install typora
  ```

You can [install pandoc](https://pandoc.org/installing.html) to export Markdown files to `docx` files.
