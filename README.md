# Pill Tracker

A single-page web app for tracking doses against a daily mg allotment. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

Your total for the period is the allotted mg/day × the days from "Counting from" to your appointment.

- **Red line:** what's left of that total if you take exactly the daily allotment. Each calendar day's full allotment counts as soon as the day starts, so the line steps down once a day.
- **Yellow line:** what you've actually got left, dropping at each logged dose.
- At "now", the gap is labeled in mg: `+` means allowance left through today, `−` means over it. With 15 mg doses it moves in 15 mg steps.

Settings: counting-from date, allotted mg/day, appointment. Doses are logged with 15 mg / 30 mg buttons.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
