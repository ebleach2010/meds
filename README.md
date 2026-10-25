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

## Taper plan tab

The **Taper plan** tab works out exactly when to take each remaining 15 mg pill so you land on your target by the end point:

- **mg to plan:** the target total minus everything taken so far, in whole doses.
- **Hours:** "Around the clock" (default) spaces doses over the full 24 h, so at 75 mg/day there are up to 5 dose times a day, every 4h 48m. "Waking hours" fits the same number between Awake from and Asleep at.
- **Taper shape:** a slider. Fully left (smoothest) is a straight line down from what you've been taking lately (the last 3 finished days' average), started just below it so the step into the plan is the same size as each step after it: the smallest day-to-day drops that still land on target. Fully right (most aggressive) holds your recent level, capped at 90 mg/day, as long as the total allows, then drops hard over the last days, down to nothing if that's what the numbers say. Anywhere in between blends the two. A bar per day under the slider shows the shape (orange = over your daily allowance, dashed red line = the allowance), with the biggest one-day drop and any days left with nothing spelled out under it. Whole days never go back up, and no day is planned above 90 mg (or your allowance, if that's higher); today's doses so far count towards that.
- **Pills I have:** 15 mg and 30 mg, both on by default, so the plan mixes them. Each dose time is one pill: 15s wherever the slots allow, with 30s spread among them on days that need more (e.g. 90 mg = four 15s and one 30). Tap one off when you run out: with 15s only a day tops out at 75 mg; with 30s only, days come in 30 mg steps.
- **Finish with extra:** a dropdown (0, 15, 30 … mg, in 15 mg steps up to everything left) holds that much back from the plan, so you finish with it left over.
- **Never faster than your allowance pace:** today's first dose is at least one full gap after your last dose, and today's last dose is at least one gap before tomorrow's first. If that means the target can't be reached, the plan says how many mg don't fit (you'd finish under target) rather than squeezing them in.
- **Clock change:** on the night clocks go back, a time in the repeated 1 AM hour is marked †, meaning take it at the second 1:30 after the change.
- **Past days:** a list above the upcoming days shows every finished day's total mg against the daily allowance ("on target", "+60 over", "60 under"), newest first, with the running total in the header.
- **Re-plans as you go:** every logged dose, from either tab, updates the plan. "Log 15 mg now" (or 30) logs the next planned dose.

It's a scheduling aid, not medical advice; check any change in how you take your medication with your prescriber.

## Using it on an iPhone

Host it with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), open the URL in Safari, then Share → **Add to Home Screen**.

Data lives in the browser's `localStorage` on that device only. Safari can clear storage for sites you haven't opened in a while, so use **Export backup** now and then.
