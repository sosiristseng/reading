# Apt package manager


**Source**
- [itsfoss | apt](https://itsfoss.com/apt-vs-apt-get-difference/)
- [itsfoss | apt commands](https://itsfoss.com/apt-command-guide/)

<!--more-->

## apt vs apt-get

- `apt` command is more suited towards interactive use, including commonly-used commands from `apt-get` and `apt-cache`. And it comes with a nice progress bar.
- `apt-get` is geared towards scripting use due to its stable interface.

## apt-fast for faster downloads

[`apt-fast`](https://github.com/ilikenwf/apt-fast) is shellscript wrapper for `apt-get` and `aptitude` that can drastically improve `apt` download times by downloading packages in parallel, with multiple connections per package.

`apt-fast` is a drop-in replacement of `apt-get`. e.g. you can use `sudo apt-fast update`, `sudo apt-fast dist-upgrade`. Should your download stall for any reasons, you'll need to run `apt-fast clean`.


```bash
# Set up apt-fast
sudo add-apt-repository -y ppa:apt-fast/stable
echo debconf apt-fast/maxdownloads string 16 | sudo debconf-set-selections
echo debconf apt-fast/dlflag boolean true | sudo debconf-set-selections
echo debconf apt-fast/aptmanager string apt-get | sudo debconf-set-selections
sudo apt update && sudo apt install apt-fast -y
```

## Synaptic the GUI package manager

`apt-xapian-index` offers quick filter search box in `synaptic` [@UbuntuHandBook](http://ubuntuhandbook.org/index.php/2019/01/enable-quick-filter-search-box-synaptic-package-manager/)

```bash
sudo apt install synaptic apt-xapian-index
```

## Fix apt package manager

Try these commands to fix borked apt package registry. Taken from [System76 docs](https://support.system76.com/articles/package-manager-pop/).

```bash
sudo apt clean
sudo apt update -m
sudo dpkg --configure -a
sudo apt install -f
sudo apt dist-upgrade
sudo apt autoremove --purge
```

## Deprecation of `apt-key` command

> Use of apt-key is deprecated. [Debian manpage](https://manpages.debian.org/testing/apt/apt-key.8.en.html)

One may receive a `apt-key add is deprecated` message from Ubuntu 20.10 and newer when adding keys from 3rd party repos.

It is recommended to put keys directly into `/etc/apt/trusted.gpg.d/`.
- `.asc` for text public keys
- `.gpg` for binary public keys

For example, instead of this

```bash
wget -qO- https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo apt-key add -
```

Do this

```bash
curl -fsSL https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/vivaldi-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/vivaldi-keyring.gpg] https://repo.vivaldi.com/archive/deb/ stable main" | sudo tee /etc/apt/sources.list.d/vivaldi.list > /dev/null
```

