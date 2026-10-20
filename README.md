# Pill Tracker

A single-page web app for tracking pill doses against a tapering prescription. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

- **Red line:** the average pace from the dispensed count down to 0 ("day 0"). It's a straight line using total pills ÷ total days across the whole schedule, so it doesn't jump when the dose steps down.
- **Yellow line:** pills actually left, dropping at each logged dose.
- At "now", the gap between the two is labeled: `+` means more pills left than the average pace, `−` means fewer.

Default prescription: 70 × 15 mg pills dispensed Oct 19, 2026; 60 mg/day for 7 days, then 45 mg/day for 14 days (70 pills over 21 days ≈ 3.33 pills/day, day 0 = Nov 9). All of this is editable under **Prescription & settings**.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
