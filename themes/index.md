# Themes


[Best GTK themes @ Its FOSS](https://itsfoss.com/best-gtk-themes/)

<!--more-->

## Papirus icon theme and Kvantum SVG engine

- [Papirus icon theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)
- [Kvantum SVG-based theme engine](https://github.com/tsujan/Kvantum)

Via `apt`:

```bash
sudo add-apt-repository -y ppa:papirus/papirus           # Papirus icon theme
sudo apt update && sudo apt install papirus-icon-theme qt5-style-kvantum qt5ct
```

Via `pacman`:

```bash
sudo pacman -S papirus-icon-theme kvantum-qt5
```

## Materia theme

Clean theme on both KDE and Gnome.

- [Materia KDE](https://github.com/PapirusDevelopmentTeam/materia-kde)
- [Materia GTK](https://github.com/nana-4/materia-theme)

Via `apt`

```bash
sudo add-apt-repository -y ppa:papirus/papirus
sudo apt update && sudo apt install materia-gtk-theme materia-kde
```

Via `pacman`

```bash
sudo pacman -S materia-gtk-theme materia-kde kvantum-theme-materia
```

Setup fonts for materia theme:

- To properly display the theme, use a font family including Medium weight (e.g. `Roboto` or M+).
- Set the font size to 9.75 (= 13px at 96dpi) or 10.5 (= 14px at 96dpi).

