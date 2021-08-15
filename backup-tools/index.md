# Backup Tools


Back up important files in Linux.

<!--more-->

## Timeshift

[Timeshift](https://github.com/teejee2008/timeshift) is a system backup and restore manager using `rsync` or `btrfs` snapshots.

- Via `apt`
  ```bash
  sudo apt install timeshift
  ```
- Via [AUR](https://aur.archlinux.org/packages/timeshift/)
  ```bash
  paru -S timeshift cronie
  # You may need this step to enable scheduled backup
  sudo systemctl enable --now cronie.service
  ```

