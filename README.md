# Pill Tracker

A single-page web app for tracking pill doses against a tapering prescription. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

- **Red line:** where you should be at your allotted mg/day, ending at 0 on "day 0". Each refill or dose change starts a new segment: the line jumps up by the pills added and slopes at the new allotment.
- **Yellow line:** pills actually left, dropping at each logged dose and rising at each refill.
- At "now", the gap between the two is labeled: `+` means more pills left than the allotment says, `−` means fewer.

Current setup: 70 × 15 mg pills dispensed Oct 19, 2026 at 60 mg/day (4 pills/day, day 0 = Nov 5). Add refills and dose changes under **Prescription & settings**.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
