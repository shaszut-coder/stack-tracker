# Stack Tracker — Changelog

## v2.1.0 — current

### Fixed
- Overall Maxing Score was badly diluted. Simply viewing a month's
  calendar (Tracker, Stats Year view, Journal calendar) silently created
  a blank record for every day in that month, even days never touched.
  This made "since your first entry" drift back to January 1st any time
  a month was browsed, making the all-time score look far lower than
  reality. Fixed so the start date is based only on days with real logged
  activity. The same fix was applied to streak and best-weekday math.

### Changed
- Overall Maxing Score is now a colorful stacked-rainbow badge (same
  colors/order as the app logo) with the percentage in bold black text
  centered on top, instead of a plain dark card.
- About panel and the Journal entry modal both got an explicit close (X)
  button in the top corner, in addition to the existing Close button and
  tap-outside-to-close.
- About panel's "How it works" tiles updated to describe the current
  Tracker (journal box built into each tile), Journal (search + calendar
  + focused edit modal), and Stats (Overall Maxing Score, Maxed Stacks
  counts) — previous tiles described an older version of each.

## v2.0.0

A major update — new activity categories, a rebuilt Journal, a new Stats
tab, a real on-device database, and a visual refresh.

### Storage
- Moved from localStorage to IndexedDB for a much larger storage quota
  and to support journal entries more robustly. Existing localStorage
  data is migrated automatically on first load.

### Tracker (renamed from "Daily Tracker")
- Three new daily categories: Hydration (oz), Nutrition (cal), and Sleep
  (hr) — each with a configurable goal in Setup.
- Personal Training only appears on days marked as a PT day in Setup.
- Daily goal = Steps + Hydration + Nutrition + Sleep, plus Strength +
  Cardio on Workout Days, plus Personal Training on PT Days.
- The month calendar shows each day's completed activities stacked
  top-to-bottom, gold-ringed on any day where everything available was
  completed.
- A journal text box was added to the bottom of every day's tile,
  auto-saving as you type.

### Journal — redesigned twice this version
- First pass: one text entry per day, explicit Save/Edit.
- Final design: a search box (plain text or activity keywords like
  "maxed," "PT," "sleep"), a month calendar, and a Recent Entries list —
  tapping any day or entry opens a large, focused modal for reading and
  editing, auto-saving as you type.
- A small stack indicator next to each day mirrors that day's actual
  Tracker activity, gold-ringed when fully "maxed" — correctly scoped to
  only the activities actually available that day (6 on a normal day, 7
  on a PT day).

### Stats — new tab
- Header: "How are you stacking up?"
- Overall Maxing Score: a single percentage covering every available
  activity since your very first logged day.
- All-time highlights: current/longest streak, total goal days, best
  weekday.
- Maxed Stacks counts for This Week / This Month / This Year.
- Week / Month / Year toggle with its own navigation, goal-days tally,
  and per-activity breakdown. Year view includes a 12-month bar chart.

### Setup
- Daily Goals expanded to include Hydration, Nutrition, and Sleep.
- Weekly Schedule: choose Workout Days and Personal Training Days.
- Export/Import for full backups; Clear All Activity with confirmation.

### Branding & design
- Renamed to Stack Tracker — "A personal fitness and lifestyle journal."
- New logo: a stacked-color square between "Stack" and "Tracker."
- New About panel with a full "How it works" guide.
- Brighter, more modern color palette throughout.

## v1.0.0 — Initial Release

Daily Tracker (Steps, Strength, Cardio, Personal Training), Weekly Review
notes, Setup (goals, schedule, export/import, clear activity). Stored in
localStorage. Earthy color palette, no Stats tab, no logo, no About panel.
