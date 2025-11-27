---
title: How to install Chinese input method on  Steam Deck
category: computer
tags: steam-deck
published: true
---

1. Install Fcitx 5 flatpak version
2. Install Chinese Addons flatpak version
3. Start Fcitx 5
4. Configure -> Add a Chinese input method (e.g.  双拼) -> Confirm
5. Add the following to `/etc/environment`

GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
