---
title: "Biblography in Hexo-generated sites"
subtitle: ""
date: 2021-08-17T22:40:37+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: [web, hexo, pandoc, bibtex, research]
categories: [WebDev]

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

Using `citeproc` in `pandoc` to generate citation (biblography) entries in Hexo static site generator.

<!--more-->

## Setup a hexo blog site

Please see the [user guide](https://theme-next.js.org) for details.

## Switch markdown renderer to pandoc

A [pandoc](https://pandoc.org/) installation is required.

```bash
npm un hexo-renderer-marked
npm i hexo-renderer-pandoc
```

## Pandoc renderer config

In `_config.yml`

```yml
# markdown-renderer-pandoc config: https://github.com/wzpan/hexo-renderer-pandoc
pandoc:
  extra:
  - citeproc:
  - bibliography: "xxx.bib"
  - csl: "xxx.csl"
  template:
  meta:
  mathEngine:
```
