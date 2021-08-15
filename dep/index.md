# Automatic dependency updates


Automatic dependecy update for GitHub projects
- Git submodules
- GitHub actions
- Node JS packages
- And more

<!--more-->

## Renovate Bot

[Renovate bot](https://www.whitesourcesoftware.com/free-developer-tools/renovate) can manage both dependecy update checking and automated pull request merging.

It supports a variety of platforms:
- GitHub (.com and Enterprise)
- GitLab (.com and CE/EE)
- Bitbucket Cloud / Servee
- Azure DevOps
- Gitea.

And a variety of programming languages
- Git submodules
- GitHub actions
- Node JS packages
- Docker
- Javascript (and node JS)
- Java
- And more

Checkout [Renovate GitHub APP](https://github.com/marketplace/renovate) to get started. After the bot is enabled in GitHub projects, it will open an pull request to ask for an interactive setup.

The setting file `renovate.json` in this project to check GH action updates

```json
{
  "extends": [
    "config:base"
  ],
  "packageRules": [
        {
            "matchUpdateTypes": [
                "minor",
                "patch",
                "pin",
                "digest"
            ],
            "automerge": true,
            "automergeType": "branch"
        }
  ],
  "git-submodules": {
      "enabled": true
  }
}
```

## Dependabot + Kodiak

[Dependabot](https://github.com/dependabot) creates a pull request once there is an update for the dependencies. And the pull request could be tested by continuous integration (CI).

However, [dependabot does not support automerging on its own](https://github.blog/changelog/2021-02-19-github-actions-workflows-triggered-by-dependabot-prs-will-run-with-read-only-permissions/) due to security concerns. We can use [Kodiak](https://kodiakhq.com/) to automate the process. See it's [quickstart](https://kodiakhq.com/#quickstart) to get started.

The example setup file `.github/dependabot.yml`

```yml
version: 2

updates:
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"
    labels:
    - "automerge"
  - package-ecosystem: "gitsubmodule"
    directory: "/"
    schedule:
      interval: "daily"
    labels:
    - "automerge"
  - package-ecosystem: 'npm'
    directory: '/'
    schedule:
      interval: 'daily'
    labels:
    - "automerge"
```

The example setup file `.github/.kodiak.toml`

```toml
version = 1

[merge]
method = "squash"
```


