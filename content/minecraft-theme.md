---
title: Omarchy Minecraft Theme
layout: about
description: A switchable Minecraft theme for Omarchy with hotbar HUD, inventory, Steve companion and more — all original art, code and audio.
---

# Omarchy Minecraft Theme

A switchable [Omarchy](https://omarchy.org) theme plus a suite of Minecraft-style Quickshell overlays — all original art, code, and audio. Not affiliated with Mojang or Microsoft.

<video controls preload="metadata">
  <source src="/projects/minecraft/omarchy-minecraft-theme.mp4" type="video/mp4">
  Your browser does not support the video tag — <a href="/projects/minecraft/omarchy-minecraft-theme.mp4">download the demo</a>.
</video>

## What you get

- **Theme `minecraft`** — obsidian palette, XP-green accents, stone GUI greys, Monocraft font, pixel cursor, transparent bar
- **Bar cube** — grass-block button beside the Omarchy menu; click to toggle the theme on and off (same as SUPER+M)
- **HUD** — hotbar, hearts, hunger, XP bar, status icons and the `[E] inventory` chip
- **Inventory** — classic GUI with app launchers and category-matched craft-row suggestions
- **Steve** — blocky companion, top-left; blinks and bobs; click to open the inventory
- **Death power menu** — a "You Died!" screen with respawn, title screen, log out and shut down actions
- **Toasts & splash** — advancement-style notifications and yellow diagonal splash text
- **Sounds** — original procedural click, open, close, toast and death WAVs
- **Screensaver** — alternating block art while the theme is on

## Screenshots

![HUD over a sunset village with hotbar, hearts, XP bar and Steve](/projects/minecraft/screenshot-hud.png)

![Inventory open over the game world](/projects/minecraft/screenshot-inventory.png)

![Hotbar close-up with hearts, XP bar and the Wi-Fi battery widget](/projects/minecraft/screenshot-hotbar.png)

![Inventory detail with craft row, app suggestions and Obsidian tooltip](/projects/minecraft/screenshot-inventory-detail.png)

![Inventory Apps tab with pixel icons](/projects/minecraft/screenshot-inventory-apps.png)

## Keybinds

- **SUPER+M** — toggle the theme (HUD preloads with splash, toast and screensaver)
- **SUPER+H** — toggle the HUD / hotbar
- **SUPER+E** — toggle the inventory
- **SUPER+SHIFT+S** — toggle Steve
- **SUPER+SHIFT+D** — death-screen power menu
- **SUPER+SHIFT+X** — show splash text

## Install

```bash
git clone https://github.com/jaquesbody/omarchy-minecraft-theme.git
cd omarchy-minecraft-theme
./scripts/install.sh
omarchy theme set minecraft
```

Idempotent and safe to re-run — `./scripts/uninstall.sh` reverts everything it touches. Requires Omarchy 4.0.x, Quickshell and the Monocraft Nerd Font (`yay -S ttf-monocraft-nerd`).

## Repo

[View the source on GitHub →](https://github.com/jaquesbody/omarchy-minecraft-theme)

Code and original art under MIT, pixel art and sounds under CC0 — see the repo's `LICENSE` and `CREDITS.md`.
