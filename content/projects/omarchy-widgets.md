---
title: Omarchy widgets
layout: about
description: Home-screen widgets for omarchy-proot, written in OWL — the widget store for Omalauncher.
---

# Omarchy widgets

[Omarchy widgets](https://github.com/jaquesbody/omarchy-widgets) is my fork of [Simon Schubert's omarchy-widgets](https://github.com/SimonSchubert/omarchy-widgets) — the widget store for [Omalauncher](https://github.com/SimonSchubert/omalauncher), the Android launcher that runs Arch Linux and draws home-screen widgets written in **OWL**, a small declarative widget language. It also holds OWL faces, whole home pages, and OWL apps: full-screen views that open from the app drawer instead of sitting on a page.

Omalauncher is "a personal OS that criticises ideas, suggests new directions and dynamically organises all your loose ends into a logical todo list."

## What I've contributed

<!-- Add your widgets here as they land, e.g.:
- **widget-name** — short description. [PR #N](https://github.com/SimonSchubert/omarchy-widgets/pull/N)
-->

- _Widget list coming soon — drop names + PR links here as they merge._

## How the store works

Everything in `widgets/`, `faces/` and `apps/` is reviewed. When a pull request is merged, CI builds `index.json` (widgets), `faces.json` (faces) and `apps.json` (apps) and publishes the store to GitHub Pages, where the launcher's **store** reads them. Before installing, it shows you every command a widget or app runs and every package it installs, and it checks the download against the reviewed file's SHA-256.

## Links

- [My fork →](https://github.com/jaquesbody/omarchy-widgets)
- [Upstream store →](https://github.com/SimonSchubert/omarchy-widgets) (by [@SimonSchubert](https://github.com/SimonSchubert))
- [Omalauncher →](https://github.com/SimonSchubert/omalauncher)
- [My pull requests →](https://github.com/SimonSchubert/omarchy-widgets/pulls?q=is%3Apr+author%3Ajaquesbody)
- [My GitHub profile →](https://github.com/jaquesbody)

## Repo

Contributions are MIT-licensed in line with the upstream project. My own widget code lives in the pull requests linked above.
