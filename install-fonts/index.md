# Fonts installation and setup


Install custom fonts and make the system recognize it using `fc-cache`.

<!--more-->

## Install fonts per user

Copy the font files to  `~/.local/share/fonts/`. Then, run `fc-cache` to rebuild the font cache.

```bash
fc-cache -fv
```

## Install fonts System-wide

Copy the font files to  `/usr/share/fonts/`. Then, run `fc-cache` to rebuild the font cache.

```bash
sudo fc-cache -fv /usr/share/fonts/
```

## Improve font rendering

[Font rendering @ Manjaro wiki](https://wiki.manjaro.org/index.php/Improve_Font_Rendering)

Add these lines to `/etc/fonts/local.conf`

```xml
<match target="font">
  <edit name="autohint" mode="assign">
    <bool>true</bool>
  </edit>
  <edit name="hinting" mode="assign">
    <bool>true</bool>
  </edit>
  <edit mode="assign" name="hintstyle">
    <const>hintslight</const>
  </edit>
  <edit mode="assign" name="lcdfilter">
   <const>lcddefault</const>
 </edit>
</match>
```

Add these lines to `~/.Xresources`

```
Xft.dpi: 96
Xft.antialias: true
Xft.hinting: true
Xft.rgba: rgb
Xft.autohint: false
Xft.hintstyle: hintslight
Xft.lcdfilter: lcddefault
```

And then run

```bash
xrdb -merge ~/.Xresources
```

