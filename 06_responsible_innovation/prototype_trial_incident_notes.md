# Shadow trial at Kingsmere — incident notes

**Trial:** 7 September – 30 October 2026. 27 invited staff could view the Horizon forecast each day. The agreed rule: *the forecast is for information only and must not be used to make or justify a decision.*

Notes kept by the VP Product's team. Figures can be checked against `07_prototype_v0_3/backtest_site_level.csv`, `02_hospital_uk_kingsmere/site_daily_sitrep.csv` and `05_users_and_workflows/prototype_trial_usage_log.csv`.

The home screen colours each day by forecast occupied adult beds as a share of beds open when the forecast is issued: **green** below 94%, **amber** 94% to 97%, **red** 97% or more.

---

## TN-01 — Thursday 10 September: under-forecast in the first week

- Forecast for 08:00 Thursday, issued Wednesday: **435** occupied adult beds (range 427 – 443). Shown as amber.
- Actual: **454**.
- What happened: the hospital was at OPEL 3 from Tuesday. The escalation ward went from 6 to 18 beds over two days. More beds open meant more beds occupied.
- 18 of the 27 trial users looked at Horizon that day. Six submitted an override.
- Site manager's comment in the log: the forecast does not know about the medically fit patients waiting for care packages.

*Question raised at the weekly review:* is a forecast of occupied beds a forecast of anything, when the number of beds open is a decision the hospital takes in response to pressure?

## TN-02 — Thursday 1 October to Saturday 3 October: over-forecast, and a nurse moved

- On Wednesday 30 September the forecast for Saturday 3 October was **443** (range 434 – 452). With 450 beds open, that showed as **red**.
- At the 09:15 staffing huddle on Thursday 1 October a matron showed a screenshot of the red Saturday as the reason to roster a registered nurse from a medical ward onto the escalation ward for Saturday's day shift.
- Actual on Saturday: **415**. The forecast was 28 beds too high. The next day's forecast for Saturday (issued Friday) was 440, still 25 too high.
- The nurse's own ward ran one registered nurse short on Saturday. She raised it with her union representative on Monday.
- This was a breach of the trial rule. Nobody on our side knew until the staff-side chair mentioned it in an interview on 6 October.

*Question:* we told people not to act on it. They acted on it. What did we expect?

## TN-03 — Tuesday 29 September: stale forecast

- The nightly file from the trust, normally received at about 02:00, arrived at 11:40.
- From 06:30 to 11:52 the home screen showed Monday's forecast. The issue date was displayed in small grey text at the foot of the page.
- Six users viewed the forecast that morning, including at the 08:30 bed meeting. None reported noticing.
- The information analyst spotted it at 11:50 and telephoned us.
- There is no alert when a file is late and no banner when a forecast is out of date.

## TN-04 — Tuesday 6 October: green on a bad day

- Forecast for 08:00 Tuesday, issued Monday: **427** (range 419 – 435). Shown as **green**.
- Actual: **452**, 25 above the forecast and 17 above the top of the range.
- On Monday morning 23 patients were waiting in the emergency department for a bed and three planned operations were cancelled on the day. The last six escalation beds were opened on Tuesday morning.
- Six overrides were submitted on Tuesday and four on Monday.
- ED nurse in charge, by email to the Deputy Chief Operating Officer: "If that is green I do not want to see amber."

*Question:* the same model was 25 beds too high on Saturday and 25 too low on Tuesday. The screen said "80% range" both times.

## TN-05 — pattern across the trial: who stopped looking

- Week 1: all 27 invited users opened Horizon at least once. Week 8: 10.
- Eight ward managers used it in week 1, four in week 2, none after that.
- Two-thirds of forecast views were of the next one or two days. About one view in twenty was of day seven.
- Under 5% of activity was at weekends.
- The page that explains the range was opened 24 times in eight weeks.

*Not an incident. Recorded here because it may be the most important thing we learned.*
