---
title: "Use Conda in GitHub Actions"
subtitle: ""
date: 2021-08-17T23:47:16+08:00
draft: false
author: ""
authorLink: ""
description: ""

tags: ["devops", "github", "python", "conda"]
categories: [Python, DevOps]

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

The following example uses [setup miniconda](https://github.com/conda-incubator/setup-miniconda) GitHub action and the [mamba](https://github.com/mamba-org/mamba) package manager.

<!--more-->

The workflow file `.github/workflows/conda.yml` with the `jobs` section only.

- enable `mamba` by specifying `mamba-version: "*"`.

```yml
jobs:
  example-6:
    name: Ex6 Mamba
    runs-on: "ubuntu-latest"
    steps:
      - uses: actions/checkout@v2
      - uses: conda-incubator/setup-miniconda@v2
        with:
          python-version: 3.6
          mamba-version: "*"
          channels: conda-forge,defaults
          channel-priority: true
          activate-environment: anaconda-client-env
          environment-file: etc/example-environment.yml
      - shell: bash -l {0}
        run: |
          conda info
          conda list
          conda config --show-sources
          conda config --show
          printenv | sort
      - shell: bash -l {0}
        run: mamba install jupyterlab
```
