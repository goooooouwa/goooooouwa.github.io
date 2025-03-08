---
title: Hyprland Installation Steps
category: computer
tags: hyprland
published: true
---

## Install

`$ sudo pacman -S hyprland`

## Setup

Install kitty (default terminal emulator):

`$ sudo pacman -S kitty`

### Launching Hyprland
Systemd users can also start Hyprland, using `uwsm`. This is the recommended method of launching Hyprland on systemd-based distros.

Install uwsm:

`$ sudo pacman -S uwsm`

### Using a display manager 

Login managers are not officially supported, but here’s a short compatibility list:

`SDDM` → Works flawlessly. Install sddm ⩾ 0.20.0 or the latest git version (or sddm-git from AUR) to prevent SDDM bug 1476 (90s shutdowns).

If you use a display manager, choose hyprland (uwsm-managed) entry in a display manager selection menu.