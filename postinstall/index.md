# Windows Postinstall


Things to do after Windows installation via [Chocolatey 🍫](https://chocolatey.org/) package manager.

<!--more-->

## Nvcleaninstall

Install nvidia GPU driver without bloat. Use [nvcleaninstall][] to choose the driver components you need.

[Youtube link](https://youtu.be/LR1XkjtylCM)

**Uninstall current GPU drivers**

Start your Windows to [safe mode][] and run [display driver uninstaller][].

**Clean install NV driver**

Use [nvcleaninstall] to install Nvidia driver.

[safe mode]: https://support.microsoft.com/en-us/windows/start-your-pc-in-safe-mode-in-windows-10-92c27cff-db89-8644-1ce4-b3e5e56fe234
[display driver uninstaller]: https://www.guru3d.com/files-details/display-driver-uninstaller-download.html
[nvcleaninstall]: https://www.techpowerup.com/download/techpowerup-nvcleanstall/

## Debloat scripts

[Debloat scripts @ Chris Titus](https://christitus.com/windows-10-scripts/)

```powershell
powershell -nop -c "iex(New-Object Net.WebClient).DownloadString('https://git.io/JJ8R4')"
```

- Installs [Chocolatey 🍫](https://chocolatey.org/), a command-line interface (CLI) [package](https://chocolatey.org/packages) manager for Windows.
- Removes OneDrive, Indexing, Defender, and more bloatware.

## Install packages

```powershell
choco install -y vscode git gitkraken mingw powershell-core microsoft-windows-terminal nodejs qbittorrent firefox vivaldi brave anydesk telegram microsoft-teams 7zip bandizip honeyview potplayer youtube-dl ffmpeg lavfilters crystaldiskinfo directx vcredist-all okular typora marktext miktex pandoc pandoc-crossref hugo-extended
```

## See also

[Awesome Windows](https://github.com/Awesome-Windows/Awesome)

