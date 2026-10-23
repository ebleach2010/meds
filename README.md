# Pill Tracker

A single-page web app for tracking doses against a daily mg allotment. No build step, no server, no dependencies: open `index.html` in any browser.

## What it shows

Your total for the period is the allotted mg/day × the calendar days from "Counting from" to your appointment. Days run midnight to midnight.

The top of the screen shows three numbers:
- **mg left today:** today's allowance minus today's doses. It resets at midnight and turns into "mg over today" if you go past it.
- **Balance (past days):** finished days only. Unused allowance is `+` ("mg extra"), anything over is `−` ("mg deficit").
- **mg/day to target:** what to average from today on to land exactly on the total by the appointment.

Doses logged with a future time don't count until that time arrives.

- **Red line:** what's left of the total if you take exactly the daily allowance. It steps down once a day.
- **Yellow line:** what you've actually got left, dropping at each logged dose.
- **Balance bar:** a short bar on today's midnight line, between the red and yellow lines, labeled with the balance (e.g. "−75 mg"). Its length is the balance.

The look is dark and neon whatever the phone's light/dark setting.

The chart shows the last few days through now. Each dose is a yellow dot on the yellow line. A second scale on the right (0–5) carries **agitation** (purple dots joined by a line, 1 = calm, 5 = very agitated; the latest one carries a small note with the time since the dose before it, that dose's mg and the day's running total at that dose), **sleep** (green dots joined by a line, hours ÷ 2 so 10 hours sits at 5) and **naps** (light-blue dots, no line, just above the axis). Under the chart: time since the last dose and today's running total with a progress bar, e.g. "Today: 45 mg of 60 mg".

Logging is one card: pick Dose, Agitation, Sleep or Nap at the top, choose the value (15/30 mg, 1–5, or hours with − / +; naps have no value), set the date & time (or tap Now), then tap the Log button.

History is one list of every dose, agitation, sleep and nap entry with its date and time, newest first; each dose also shows that day's running total. The yellow line under the chart shows the time since the last logged dose.

The page ends with a line like "Build 6 · Home Screen app · 12 doses saved on this device". The Safari tab and the Home Screen app each keep their own saved doses; use Export/Import backup to move them.

Settings: counting-from date, allotted mg/day, appointment. "Export CSV" under History downloads every dose, agitation, sleep and nap entry with its date and time, plus each refill and target end date. Changing "Counting from" counts as a refill and keeps the previous period in that history.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
