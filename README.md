# Pill Tracker

A single-page web app for tracking doses against a daily mg allotment. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

Your total for the period is the allotted mg/day × the days from "Counting from" to your appointment.

- **Red line:** what's left of that total if you take exactly the daily allotment. Each calendar day's full allotment counts as soon as the day starts, so the line steps down once a day.
- **Yellow line:** what you've actually got left, dropping at each logged dose.
- At "now", the gap is labeled in mg: `+30` means 30 mg of allowance still left through today ("mg extra"), `−15` means 15 mg over ("mg deficit").

The chart shows the last few days through now. Each dose is a yellow dot on the yellow line. A second scale on the right (0–5) carries **agitation** (purple dots joined by a line, 1 = calm, 5 = very agitated) and **sleep** (green dots joined by a line, hours ÷ 2 so 10 hours sits at 5). Under the chart: time since the last dose and today's running total, e.g. "Today: 45 mg of 60 mg".

Log agitation (pick 1–5, then "Log agitation") and last night's sleep (hours, then "Log sleep") in the Log card; both use the same date & time field as doses.

History is one list of every dose, agitation and sleep entry with its date and time, newest first; each dose also shows that day's running total. The yellow line under the chart shows the time since the last logged dose.

The page ends with a line like "Build 6 · Home Screen app · 12 doses saved on this device". The Safari tab and the Home Screen app each keep their own saved doses; use Export/Import backup to move them.

Settings: counting-from date, allotted mg/day, appointment. To log a dose, set the date and time (or tap Now), pick 15 mg or 30 mg, then tap Log dose. "Export CSV" under History downloads every dose, agitation and sleep entry with its date and time, plus each refill and target end date. Changing "Counting from" counts as a refill and keeps the previous period in that history.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
