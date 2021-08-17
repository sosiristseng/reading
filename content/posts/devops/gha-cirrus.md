---
title: "Interoperativity between Github Action and Cirrus CI"
subtitle: ""
date: 2021-08-17T23:29:01+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: ["devops", "github", "cirrus"]
categories: ["DevOps"]

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

Run Github actions after successful Cirrus CI runs with the [`check_suite`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#check_suite) trigger.

<!--more-->

`.github/workflows/cirrus,yml`

```yml
on:
  check_suite:
    type: ['completed']

name: Continue after Cirrus CI Complets Successfully
jobs:
  continue:
    name: After Cirrus CI
    if: github.event.check_suite.app.name == 'Cirrus CI' &&  github.event.check_suite.conclusion == 'success'
    runs-on: ubuntu-latest
    steps:
    - name: Continue
      run: echo "Hello after Cirrus CI Completed"
```
