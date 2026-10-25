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
- **Baseline:** what your last 3 finished days averaged, but never more than 90 mg a day (or your allowance, if that's higher). The cut needed to land exactly on target comes out of that baseline as a dip, and away from the dip the plan goes back up towards the baseline. No day is planned above the 90 mg cap; today's doses so far count towards it.
- **How hard the drops are:** a slider for how concentrated the dip is. Fully left (smoothest) spreads the cut over about half the period in gentle 15 mg steps. Fully right (most aggressive) packs it into as few days as it can, down to nothing on those days if that's what the numbers need.
- **When the biggest drops happen:** a second slider, in its own box below the first, for when the dip is, from right away (the default) to the end. In the middle, the plan holds near the baseline, dips around the date shown, then goes back up. At the end it holds and then drops, the classic taper. Whole days only fall towards the lowest day and only rise after it, so rounding never zig-zags.
- **Day-to-day pattern:** Steady (the default) keeps each day close to the next. Alternate swings high and low days back and forth; Random does it in a shuffled order (Reshuffle for a new one). Swing sets how far, ±15, ±30 or ±45 mg. Days are paired by date, each high day with the low day next to it, so the total never changes, no day goes over the cap or below 0, and a date keeps its high or low as the days go by.
- **Bars:** one per day under the sliders shows the shape (orange = over your daily allowance, dashed red line = the allowance), with the low point, the biggest one-day drop and any days left with nothing spelled out under it.
- **Move a day:** press and hold a day's bar for about half a second, then drag it to another day and let go. That day's amount moves there and the days in between shift over by one, so the total stays the same. "Undo moves" under the bars puts them back. Today can't be moved.
- **Lock it in:** saves each day's total as shown. While locked, the Tracker tab's "mg left today", "Today: X mg of Y mg" and progress bar use the locked amount for that day instead of the flat allowance (marked "locked plan"), and the taper controls are hidden. If what you take drifts from the locked plan, the summary says how far over or under what's left it now is; "Unlock to change" and lock it in again to rebalance. Changing the period in Settings unlocks it.
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
