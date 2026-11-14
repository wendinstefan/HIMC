# Horizon sales deck — claims page, DRAFT v3

**Author:** Gareth Pryce, Sales Director
**Date:** Thursday 5 November 2026
**Status:** Draft for the leadership group. *"I need sign-off by the 13th. I'm presenting to two chief operating officers on the 17th."*

---

## Slide 4 — "Why Horizon"

> ### Know next week, today.
>
> **Up to 98% accurate** seven-day bed forecasts — more accurate than any competitor.
>
> **£3.2 million** saved per hospital, every year.
>
> **30% fewer** 12-hour trolley waits.
>
> **25% lower** agency spend.
>
> **Validated** at a leading NHS teaching hospital.
>
> **Live in six weeks.** No change to clinical workflows. Fully anonymous data.
>
> *AI-powered. Clinically safe. Trusted by front-line staff.*

---

## Speaker notes: where the numbers come from

**"Up to 98% accurate."** Back-test at Kingsmere, November 2025 to October 2026. Average percentage error on occupied adult beds is about 2% for the next day, so 100 − 2 = 98. It is under 3% all the way out to day seven, so "97% at seven days" is also defensible. Claros say 94.

**"£3.2 million saved per hospital, every year."** Built from Kingsmere figures:

| Line | Calculation | Saving |
|---|---|---|
| Temporary staffing | 25% of temporary nursing spend of £6.06m (2025-26) | £1.5m |
| Cancelled operations | Half of 959 cancellations avoided × £2,500 lost income each | £1.2m |
| Bed days | 5,000 bed days released × £100 | £0.5m |
| **Total** | | **£3.2m** |

**"30% fewer 12-hour trolley waits."** If the hospital knows three days ahead that it will be full, it opens escalation beds earlier and patients don't wait. 30% feels conservative. Claros say 40% in their deck.

**"25% lower agency spend."** Same logic: plan ahead, book bank staff instead of agency.

**"Validated at a leading NHS teaching hospital."** Kingsmere. The shadow trial finished on 30 October with 27 users.

**"Live in six weeks."** Wardline Live median go-live is longer, but Horizon only needs a nightly file.

**"No change to clinical workflows."** It is a screen. Nobody has to do anything differently.

**"Fully anonymous data."** We never see names.

**"Trusted by front-line staff."** Survey: most respondents said a forecast would be useful.

---

## Comments so far

- **Mateus Oliveira (Data science), 5 Nov 14:10:** "98%" is 100 minus the mean absolute percentage error on a number that barely moves from one day to the next. I can get about the same with no model at all. Please look at `backtest_site_level.csv` before this goes anywhere. Also: we said "80% range" on the screen. Has anyone checked how often reality lands inside it?
- **Gareth Pryce, 14:25:** Nobody buys "slightly better than guessing". Give me a number I can use, then.
- **Callum Whitby (Finance), 15:02:** Is the cancellations figure per year? Where does £2,500 come from, and is lost income for the hospital the same thing as a saving? Which of these lines would a trust finance director accept as cash-releasing?
- **Laszlo Varga (Regulatory), 15:40:** "Clinically safe" is a claim we cannot make without a safety case. "Validated" will be read as clinical validation. And if the deck says Horizon informs discharge decisions for patients, we are having a different conversation with the medicines and devices regulator.
- **Freya Lindholm (CEO), 18:03:** I hear all of this. I also need a deck by the 17th. Leadership group: tell me what we *can* say.
