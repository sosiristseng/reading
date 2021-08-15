# Zotero reference manager


[Zotero](https://www.zotero.org/download/) is an open source reference manager.

<!--more-->


## Installation

### Ubuntu / PoPOS

For Ubuntu / PopOS users, zotero can be installed in [zotero-deb](https://github.com/retorquere/zotero-deb)

```bash
wget -qO- https://github.com/retorquere/zotero-deb/releases/download/apt-get/install.sh | sudo bash
sudo apt update
sudo apt install zotero
```

### Manjaro / endeavour OS

Zotero can be installed in [AUR](https://aur.archlinux.org/packages/zotero/)

```bash
paru -S zotero
```

### Windows

Either [download](https://www.zotero.org/download/) and run the installer, or use chocolatey package manager

```powershell
choco install zotero
```

## ZotFile for more Storage space

[Storage space is limited](https://www.zotero.org/storage) (300MB) for the free plan.

If you want to attach more pdf files or dataset you could set up a custom folder using [ZotFile](http://zotfile.com/) attachment manager.[^1] Often this folder will sync with the cloud storage.

The steps are:

- Download the `.xpi` file for ZotFile and install it via the Zotero interface. Restart Zotero.
- In the zotero main program preference
  - Sync -> settings -> untick `Sync attachments in my library`
  - Advanced -> Set `Linked attachment base directory` to your library folder.
- In the ZotFile settings
  - Set Location of Files to `Custom Location` and point it to your library folder.
  - (Optionally) Set `Source folder` to your download folder.

[^1]: <https://www.nrel.colostate.edu/set-up-best-reference-manager>

## Other plugins

See [Plugins for Zotero](https://www.zotero.org/support/plugins) page for details.

