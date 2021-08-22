# Hugo Setup


How to set up a Hugo blog site.

<!--more-->

## Simple way: Using my template

Copy [My template site](https://github.com/sosiristseng/template-hugo-doit) for a quick start.

- Beautiful [DoIt](https://github.com/HEIGE-PCloud/DoIt) theme installed as a Git submodule.
- DevOps routines for both GitHub actions and GitLab CI/CD.
  - It automatically fetches update s from the DoIt theme by dependabot (For Github only)
  - The website will be built and deploy automatically upon pushing the changes.

{{< admonition type=note open=true >}}

You need to modify the following files to set base URL.

`config.toml`

```toml
baseURL = "www.yourexample.com/" # With the trailing slash
```

`.gitlab-ci.yml`

```yml
variables:
    HUGO_BASE_URL: 'www.yourexample.com/'
```

{{< /admonition >}}

{{< admonition type=example title="Do-it-yourself" open=true >}}

If you prefer a do-it-yourself way to set up your Hugo blog, please follow the [theme documentation](https://codeit.suntprogramator.dev/theme-documentation-basics/) instead.

{{< /admonition >}}


## Hosting on GitHub pages

Click the `Use the template` button at [my template repository](https://github.com/sosiristseng/template-hugo-codeit).

The website will be deployed on the `gh-pages` branch. You need to activate GitHub pages in the repository settings, pointing to root folder in the `gh-pages` branch.

The example workflow file `.github/workflows/gh-pages.yml`

```yml
name: github pages

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: checkout master
      uses: actions/checkout@v2
      with:
        submodules: true  # Fetch Hugo themes (true OR recursive)
        fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod
    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: 'latest'
        extended: true
    - name: Build
      run: hugo --minify
    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./public
```

## Hosting on GitLab pages

Click [import project](https://gitlab.com/projects/new#import_project) and select `Repo by URL`, paste the git url from [my template](https://github.com/sosiristseng/template-hugo-codeit).

The example workflow file `.gitlab-ci.yml`.


```yaml
image: klakegg/hugo:ext-alpine-ci

variables:
  GIT_SUBMODULE_STRATEGY: recursive
  HUGO_BASE_URL: 'https://sosiristseng.gitlab.io/'

test:
  script:
  - hugo
  except:
  - main

pages:
  script:
  - hugo --minify
  - apk add --update --no-cache brotli
  - find public -type f -regex '.*\.\(htm\|html\|txt\|text\|js\|css\|svg\|xml\)$' -exec gzip   -f -k {} \; || echo 'Gzip failed. Skipping...'
  - find public -type f -regex '.*\.\(htm\|html\|txt\|text\|js\|css\|svg\|xml\)$' -exec brotli -f -k {} \; || echo 'Brotli failed. Skipping...'
  artifacts:
    paths:
    - public
  only:
  - main
```

