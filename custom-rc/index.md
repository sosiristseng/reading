# Envrionment variables


Setup of environment variables for bash, zsh, fish, as well as Windows. See  also [Arch Wiki | env variables](https://wiki.archlinux.org/index.php/environment_variables).

<!--more-->

## For all users

- `/etc/profile` is sourced by all POSIX-compatible shells upon login.

## Bash

- `~/.profile` or `~/.bash_profile` for login bash shells.
- `~/.bashrc` for every bash instance.

## Zsh

- `~/.zshenv` for environment variables in zsh.
- `~/.zprofile` for login zsh shells.
- `~/.zshrc` for every zsh instance.


⚠️ zsh [does not read](https://superuser.com/questions/187639/zsh-not-hitting-profile) `~/.profile` by default due to syntax difference. You can do this instead in `~/.zprofile`

```bash
[[ -e ~/.profile ]] && emulate sh -c 'source ~/.profile'
```

## PAM module

- `~/.pam_environment` : only supports `KEY=VALUE`, `KEY DEFAULT=VALUE`, `${HOME}`, `${SHELL}`.

⚠️ Sourcing from `~/.pam_environment` [is being deprecated](https://github.com/linux-pam/linux-pam/commit/ecd526743a27157c5210b0ce9867c43a2fa27784).

## systemd

- `~/.config/environment.d/*.conf` : files are read by systemd in the WayLand session.

## Graphical environment

- `~/.xinitrc` is sourced by `startx`.
- `~/.xprofile` is sourced by display managers (e.g. GDM, SDDM)

## Windows

- [Wikipedia](https://docs.microsoft.com/zh-tw/windows-server/administration/windows-commands/setx)
- Microsoft docs for [set](https://docs.microsoft.com/zh-tw/windows-server/administration/windows-commands/set_1) and [setx](https://docs.microsoft.com/zh-tw/windows-server/administration/windows-commands/setx)

### Shell variables

Using `set`. They will vanish once the shell is closed.

```powershell
set x=123
echo %x%  # You need to wrap the var between % to show the value
```

### Persistent variables

- Set `Environment Variables` in the `Advanced` system settings GUI in the control panel.
- `setx`. See `setx /?` for the complete options

## Organizing custom rc files

Organize your custom `rc` entries (e.g. `.bashrc`, `zshrc`) into a bunch of files inside a directory. [Source](https://medium.com/@waxzce/use-bashrc-d-directory-instead-of-bloated-bashrc-50204d5389ff)

Create a folder for `*.bashrc` files.

```bash
mkdir -p -m 770 ~/.bashrc.d
```

Then add the following line to `~/.bashrc`.

```bash
for f in ~/.bashrc.d/*.bashrc; do . "${f}" done
```

Then put your custom `.bashrc` files into `~/.bashrc.d` folder. From now on the interactive bash shell will read those files in that folder *in alphabetical order* . If you want a particular loading order, prepend numbers like `01-abc.bashrc`, `02-def.bashrc`, ....

