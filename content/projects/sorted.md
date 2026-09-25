---
title: Sorted
layout: about
description: Easily check and track your spending, saving and bills — a local-first finance tracker for desktop, browser and Android.
---

# Sorted

A local-first finance tracker — spending, bills and savings in one dark, tidy app. **No backend, no cloud, no login**: everything lives in your device's local storage (IndexedDB) and leaves it only when you export it yourself.

[**Launch Sorted →**](/sorted) · [Source on GitHub](https://github.com/jaquesbody/sorted)

## What you get

- **Dashboard** — spent this month, bills due, savings progress and a 6-month trend chart, all at a glance
- **Spend** — itemised list with month navigation, status filters (all / confirmed / pending / recurring) and one-tap confirm
- **Bills Due** — due dates with overdue highlighting; mark one as paid and it moves into spend
- **Savings** — goals with progress against target
- **Reports** — spending and bills broken down by category
- **Receipt OCR** — snap or upload a receipt (image or PDF) on the Spend or Bills form and the app pre-fills the title and amount for you to confirm
- **Export / import** — your whole dataset as JSON (desktop and browser)
- Sample data seeds on first run so the app isn't empty

## Screenshots

![Sorted dashboard with this month's spend, bills due, savings progress and the monthly trend chart](/projects/sorted/dashboard.png)

![Spend list for August 2026 with month navigation, filter chips and confirmed items](/projects/sorted/spend.png)

## Run it

### Desktop (Electron)

```bash
git clone https://github.com/jaquesbody/sorted.git
cd sorted
npm install
npm start
```

### Browser

```bash
python3 -m http.server --directory docs
```

### Android

[Download the debug APK →](https://github.com/jaquesbody/sorted/raw/main/sorted-v2-2.0.1-debug.apk) and sideload it — the same app in a WebView, fully offline, data on your phone. Rebuild with `npx cap sync android && cd android && ./gradlew assembleDebug` (needs JDK 21 and the Android SDK).

## Tech

Vanilla HTML, CSS and JavaScript with an Electron shell, Capacitor for Android and IndexedDB for storage — no runtime dependencies.

## Repo

[View the source on GitHub →](https://github.com/jaquesbody/sorted) — MIT licensed.
