# Command Line Prompt


Tools to enhance the command-line experience.

<!--more-->

## Bashit

[Bash-it][] is the community's collection of useful bash scripts, inspired by the [oh-my-zsh][] project.

There are autocompletion, themes, aliases, custom functions, etc for bash prompt.

```bash
git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it

bash ~/.bash_it/install.sh
```

[Bash-it]: https://github.com/Bash-it/bash-it
[oh-my-zsh]: https://ohmyz.sh/

## zsh improved framework (zimfw)

Zsh improved framework, aka [`zimfw`](https://github.com/zimfw/zimfw), is a blazing fast zsh plugin framework, about 30x faster loading speed than [oh-my-zsh][].

Install `zsh` first and run the script

```bash
wget -nv -O - https://raw.githubusercontent.com/zimfw/install/master/install.zsh | zsh
```

**Powerlevel10k (p10k) prompt**

[Source](https://github.com/romkatv/powerlevel10k#zim)

1. In `~/.zimrc`, replace `zmodule asciiship` with `zmodule romkatv/powerlevel10k`
2. Run `zimfw install` in zsh.
3. Install [powerline fonts](https://github.com/romkatv/powerlevel10k#manual) for proper font rendering.
4. Restart zsh and go through p10k's interactive setup.

**Node version manager (nvm)**

[Source](https://github.com/lukechilds/zsh-nvm)

Add this line in `~/.zimrc`: `zmodule lukechilds/zsh-nvm`, and then run `zimfw install` in zsh.

To save loading time of zsh (about 70x), you can enable lazy loading by adding the following line to `~/.zshrc`, before loading zmodules:

```bash
export NVM_LAZY_LOAD=true
```

## Starship: corss-shell command prompt

[🚀 Starship](https://starship.rs/) is an enhancement for command prompt in a multitude of shells, powered by Rust. Available for bash, zsh, fish, powershell, etc.

### Instalation

- standalone binary
  ```bash
  sudo -v && curl -fsSL https://starship.rs/install.sh | bash
  ```
- AUR
  ```bash
  paru -S starship-bin   # or "starship" if you want to compile the code
  ```

### RC files setup

Append this line in your `*.rc` files of your shell and restart your shell to load starship.

- Bash: `~/.bashrc`
  ```bash
  eval "$(starship init bash)"
  ```
- Zsh: `~/.zshrc`
  ```bash
  eval "$(starship init zsh)"
  ```
- Windows Powershell: `~\Documents\PowerShell\Microsoft.PowerShell_profile.ps1`
  ```powershell
  Invoke-Expression (&starship init powershell)
  ```

Install [nerd fonts](https://www.nerdfonts.com/font-downloads) to show special characters correctly.

