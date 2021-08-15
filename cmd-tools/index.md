# Command Line Tools


> Command-line prompt, Terminal emulators. See also [Awesome CLI Apps](https://github.com/agarrharr/awesome-cli-apps)

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

Install via:
- standalone binary
  ```bash
  sudo -v && curl -fsSL https://starship.rs/install.sh | bash
  ```
- AUR
  ```bash
  paru -S starship-bin   # or "starship" if you want to compile the code
  ```

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

## TLDR: command cheatsheets

> [TLDR](https://github.com/tldr-pages/tldr) are collaborative cheatsheets for console commands, a complement to `man` pages.

Also see: [the pdf version](https://tldr.sh/assets/tldr-book.pdf) of TLDR.

**Usage**

For instance, to see the example of the `tar` command, type:

```bash
tldr tar
```

## bat : replacement for cat

> [bat](https://github.com/sharkdp/bat): A cat(1) clone with syntax highlighting and Git integration.

## exa : alternative to ls

> [exa](https://the.exa.website) is an improved file lister with more features and better defaults. It uses colours to distinguish file types and metadata. It knows about symlinks, extended attributes, and Git. And it’s small, fast, and just one single binary.

## fd : alternative to find

> [fd](https://github.com/sharkdp/fd) is a simple, fast and user-friendly alternative to 'find'

## Tilix

[Tilix](https://gnunn1.github.io/tilix-web/) is an advanced GTK3 tiling terminal emulator.

**Installation**

- apt
  ```bash
  sudo apt install tilix
  [[ -x $(command -v nautilus) ]] && sudo apt install python-nautilus
  ```
- pacman
  ```bash
  sudo pacman -S tilix
  [[ -x $(command -v nautilus) ]] && sudo pacman -S python-nautilus
  ```

**Set `tilix` as the default GUI terminal emulator**

- Ubuntu: `sudo update-alternatives --config x-terminal-emulator`
- Arch and derivatives:  Select `tilix` in `Prefered applications`.

