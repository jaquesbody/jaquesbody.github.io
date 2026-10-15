---
title: Sorted
layout: about
description: Easily check and track your spending, saving and bills — a local-first finance tracker for desktop, browser and Android.
---

# Sorted

A local-first finance tracker — spending, bills and savings in one dark, tidy app. **No backend, no cloud, no login**: everything lives in your device's local storage (IndexedDB) and leaves it only when you export it yourself.

[**Launch Sorted →**](/sorted) · [Source on GitHub](https://github.com/jaquesbody/sorted)

## What you get

- **Dashboard** — total money, what went where, bills due and savings progress for the month, plus a 6-month trend chart
- **Spend** — itemised list with month navigation and status filters (all / confirmed / pending); the tick is what says the money has actually gone
- **Bills Due** — due dates with overdue highlighting; mark one as paid and it stays in the list with the date you paid it, recurring bills rolling forward a month
- **Savings** — accounts with balances, income, and goals with progress against target
- **Reports** — spending, bills and savings by category, a forecast, and who spent what, scoped to all time, this month or this year
- **Receipt OCR** — snap or upload a receipt (image or PDF) on the Spend or Bills form and the app pre-fills the title, amount and date for you to confirm
- **People** — tag spend, bills and goals as somebody's and switch who's using the app; attribution on a shared device, not a login
- **Export / import** — your whole dataset as JSON, CSV, text or a PDF
- Runs in the browser, on the desktop as an Electron app, and on Android — where the six destinations sit in a bottom bar instead of a side rail

## Screenshots

![Sorted dashboard with total money, what went where, this month's bills and savings, and the monthly trend chart](/projects/sorted/dashboard.png)

![Bills — paid and upcoming, each counting down to its date](/projects/sorted/bills.png)

![Spend list with month navigation, filter chips, and the tick that says the money has gone](/projects/sorted/spend.png)

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

[Download the Android APK →](https://github.com/jaquesbody/sorted/releases/latest) and sideload it — the same app in a WebView, fully offline, data on your phone. A new install starts empty and says what it does with your data, once, on the first screen. Rebuild with `npx cap sync android && cd android && ./gradlew assembleDebug` (needs JDK 21 and the Android SDK).

## Tech

Vanilla HTML, CSS and JavaScript with an Electron shell, Capacitor for Android and IndexedDB for storage — no runtime dependencies.

## Repo

[View the source on GitHub →](https://github.com/jaquesbody/sorted) — MIT licensed.
