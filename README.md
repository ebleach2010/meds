# Pill Tracker

A single-page web app for tracking doses against a daily mg allotment. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

Your total for the period is the allotted mg/day × the days from "Counting from" to your appointment.

- **Red line:** that total spent evenly, reaching 0 at the appointment.
- **Yellow line:** what you've actually got left, dropping at each logged dose.
- At "now", the gap between the two is labeled in mg: `+` means you've taken less than the allotment so far, `−` means more.
- The summary says how many mg are left before the appointment and the mg/day average that works out to, however unevenly you've taken doses so far.

Settings: counting-from date, allotted mg/day, appointment. Doses are logged with 15 mg / 30 mg buttons.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
