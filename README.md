# Pill Tracker

A single-page web app for tracking pill doses against a daily allotment. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

- **Red line:** the allotted pace, running straight from the bottle count to what should be left at your appointment (the end point).
- **Yellow line:** pills actually left, dropping at each logged dose.
- At "now", the gap between the two is labeled: `+` means more pills left than the allotment says, `−` means fewer.
- The summary says how many more pills you can take, and the average mg/day that works out to, to land on the target count at the appointment, however unevenly you've taken them so far.

Settings: pills in bottle, mg per pill, counting-from date, allotted mg/day, appointment. On a refill, set "Counting from" to now and enter what's in the bottle; earlier doses stay in the history but stop counting.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
