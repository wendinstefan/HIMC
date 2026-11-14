# Horizon prototype 0.3 — what the screens show

A description of the clickable prototype used in the Kingsmere shadow trial and the usability tests. The example is the forecast issued on **Monday 19 October 2026**, the week used in the usability tests. Numbers come from `backtest_site_level.csv`.

The prototype is a desktop web page in English. There is no phone layout.

---

## Screen 1 — Home: seven-day forecast

```
 HORIZON                                    Kingsmere Royal Infirmary      [Menu ≡]
 ───────────────────────────────────────────────────────────────────────────────────
  Adult beds needed — next 7 days

   Tue 20     Wed 21     Thu 22     Fri 23     Sat 24     Sun 25     Mon 26
  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐
  │  436  │  │  434  │  │  435  │  │  441  │  │  425  │  │  431  │  │  433  │
  │ AMBER │  │ AMBER │  │ AMBER │  │ AMBER │  │ GREEN │  │ AMBER │  │ AMBER │
  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘
  428–444    426–443    426–444    431–450    416–434    422–440    424–442

  [ line chart: central forecast with shaded band; last 14 days of actuals ]

  What does the range mean?                                   Ward groups ▼

                                                Issued 19 Oct 2026 06:30 · v0.3
 ───────────────────────────────────────────────────────────────────────────────────
```

- **Title:** "Adult beds needed". The numbers are forecasts of adult beds *occupied* at 08:00.
- **Colour:** forecast as a share of adult beds open when the forecast was issued. Green below 94%, amber 94% to 97%, red 97% or more. The thresholds were chosen by the designer. They are not shown on the screen.
- **Range:** labelled "80% range" on hover.
- **Issue date:** small grey text, bottom right.

## Screen 2 — Ward groups

Reached by scrolling below the chart or from the "Ward groups" link.

A table of forecast patients at midnight for five groups — medicine, surgery, paediatrics, critical care, maternity and neonatal — for each of the seven days, with ranges. A second table shows forecast adult emergency admissions per day.

There is no forecast for an individual ward.

## Screen 3 — What does the range mean?

A text page:

> "The shaded band is an 80% prediction interval. We expect the actual number to fall inside the band on about four days out of five. On about one day in five it will be outside."

## Screen 4 — Accuracy history

Menu → About → Accuracy.

A table of mean absolute error over the last 28 days, by days ahead, for occupied adult beds. No comparison with any other method. No record of individual days.

## Screen 5 — "I disagree with this forecast"

Menu → Feedback → Disagree.

A form: which day; "too high" or "too low"; free-text reason. On submission: "Thank you. Your feedback has been logged." The forecast does not change.

## Screen 6 — Export

Downloads the current forecast as a spreadsheet.

---

## What is not in the prototype

- Any way to tell it that beds will open or close, that a ward is shut, or that something unusual is happening.
- Any warning that the data is late or the forecast is out of date.
- Patients waiting for a bed, patients in corridors, or any measure of unmet demand.
- Staffing.
- Discharge delays or anything about community capacity.
- Yesterday's forecast next to what happened.
- Individual wards, rooms or bed classes.
- Languages other than English.
- A phone layout, offline use, or delivery by message.
- A log of who decided what on the basis of a forecast.
