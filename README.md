# Kris Recomp Board

One HTML file that replaces the strength tracker workbook, the Hevy analysis and the meal prep page. No server, no account. Open it in any browser on your phone or laptop.

## Files

- `index.html`: the whole app. It holds the plan, exercise list and meal plan, but **no** Hevy history, weights or goals. On first open, use **Data** to import your Hevy CSV or a backup JSON.

Never commit your Hevy CSV, backup JSON or the personal copy with data built in: anything in this repository is public on GitHub Pages.

## Import a new Hevy export

1. In Hevy: Profile, Settings, Export & Import Data, Export Workouts. Save the CSV.
2. In the dashboard: **Data**, then **Import Hevy CSV**, and pick the file.
3. The new file replaces the old Hevy history. Your Form, Fatigue, RPE, tempo entries, weigh-ins, measurements, prices and stock are kept.
4. If the file is not a Hevy export (missing columns) or empty, nothing changes and the message says why. Rows with an unreadable date or text in a number column are skipped and counted.

Write Form, Fatigue and tempo in each Hevy exercise note as `F5 Ft3 T3-1-1` (order and commas do not matter). The dashboard reads them on import; anything missing shows as "not logged". You can also enter them on the Today tab, which overrides the note.

For Farmer's Walk, log duration in seconds (a timed exercise in Hevy, or the Duration field on Today). Distance cannot show time progress.

## Back up and restore

- **Data, Export backup JSON** downloads a file. If the browser blocks the download (for example inside a claude.ai preview), use **Copy backup JSON** and paste it into a note.
- **Data, Import backup JSON** restores everything from that file.

## Edit prices and foods

Meals tab, **Food database**:
- Price is for the quantity in "For qty": chicken 598 for 1519 g, rice 60 for 1000 g uncooked, mixed veg 59.75 for 500 g.
- "Usable %" covers skin and bone (chicken 92). "Cooked ratio" is cooked grams per bought gram (rice 2.8, dry mung beans 2.5).
- Leave a price blank and every cost that needs it shows "needs price". No price is ever guessed.
- Macros per 100 g are blank unless your files give them. Fill all five (kcal, P, C, F, fiber) for every food in a meal and that meal switches from the meal_prep.html estimate to the database.
- Change portions in the **Meal builder**; **Reset meals to meal_prep.html** undoes that.
- Stock (chicken bought, veg, weighed cooked rice, beans, cook date, meals to cover) is in **Stock and how long it lasts**.

## Update the plan

The plan lives at the top of the script in the HTML file, in plain lists:
- `PLAN`: each weekday (1 = Monday, 0 = Sunday) with exercise id, sets, reps (or `secs`), prescribed weight `w` and the coach note.
- `TEMPO`: the four-week tempo ladder for ceiling lifts.
- `EXERCISES`: name, Hevy title(s), Compound or Isolation, load type (Pair, Single, BW), ceiling, technique-week end date, and the muscle mapping (`d` direct, `i` indirect).
- `HOLDS`, `MUSCLES` (targets and planned sets), `PAIR` and `SINGLE` (the Equipment sheet).

Edit with any text editor, save, reload. If you add a new lift in Hevy, add its exact Hevy title to an `EXERCISES` entry, or it shows up in the Audit tab as "not mapped". For the public copy, push the edited file to GitHub as usual.

## GitHub Pages

Settings, Pages, Source: Deploy from a branch, Branch: main, folder / (root). The site appears at https://kddaclan.github.io/fitness-dashboard/. To update, replace `index.html` and push.
