# Model card — Horizon prototype 0.3

**DRAFT. Not reviewed. Not for external use.**
**Authors:** Mateus Oliveira (Senior Data Scientist); headline box added by Dev Ramanathan (CTO) for the October board pack
**Last edited:** 23 October 2026
**Owner from 2 November:** Director of Data & AI

---

> ## Headline (board pack version)
>
> - **97 – 98% accurate** forecasts of occupied adult beds, one to seven days ahead.
> - Trained on **three and a half years** of real hospital data.
> - Gives an **80% prediction range** with every forecast.
> - Hospital-agnostic method: expected to transfer to other acute hospitals with minimal retraining.

---

## 1. What the model does

Each morning at 06:30 it produces forecasts for the next seven days for seven quantities at Kingsmere Royal Infirmary:

| Target | Level |
|---|---|
| `adult_ga_beds_occupied_0800` | Whole site: adult general and acute beds occupied at 08:00 |
| `emergency_admissions_adult` | Whole site: adult emergency admissions in the day |
| `medicine_patients_midnight` | Ward group |
| `surgery_patients_midnight` | Ward group |
| `paediatrics_patients_midnight` | Ward group |
| `critical_care_patients_midnight` | Ward group |
| `maternity_neonatal_patients_midnight` | Ward group |

**Timing.** The forecast issued on day *D* uses the nightly file, which contains data up to midnight at the end of day *D* − 1. The most recent 08:00 bed state the model has seen is therefore yesterday's. "Horizon 1" means day *D* + 1.

## 2. How it works

- One gradient-boosted tree model per target per horizon: 49 models (scikit-learn `HistGradientBoostingRegressor`, 220 iterations, learning rate 0.05, depth 4).
- Refitted on the first of each month using all data to date.
- **Inputs:**
  - the target's own recent history (values 1, 2, 3, 7 and 14 days back; 7- and 28-day averages);
  - yesterday's emergency admissions, discharges, patients waiting in the emergency department for a bed, patients medically ready but not discharged, patients in hospital over 21 days, escalation beds open, and minimum temperature;
  - the most recently *published* regional flu positivity figure;
  - for the day being forecast: day of week, time of year, bank holiday, school holiday, announced strike, and the number of planned admissions booked.
- **Range.** Forecast ± 1.28 × the standard deviation of the model's errors on its training data.

## 3. Training data

- Daily series for Kingsmere from 1 April 2023, built by the data team from the trust's extracts after cleaning.
- The data is anonymous. *(Copied from the impact assessment. To be confirmed.)*
- One hospital. One country.

## 4. Performance

Back-test: forecasts issued every day from 1 November 2025 to 31 October 2026, each using only data available at the time. Full results are in `backtest_site_level.csv` and `backtest_by_ward_group.csv`.

**Occupied adult beds at 08:00**

| Days ahead | Mean absolute error (beds) | Mean absolute percentage error |
|---|---|---|
| 1 | 8.5 | 1.9% |
| 2 | 9.8 | 2.2% |
| 3 | 10.8 | 2.5% |
| 4 | 11.3 | 2.6% |
| 5 | 11.6 | 2.6% |
| 6 | 11.5 | 2.6% |
| 7 | 12.0 | 2.7% |

**Other targets (range across horizons 1 – 7)**

| Target | Mean absolute error | Mean absolute percentage error |
|---|---|---|
| Adult emergency admissions | 5.9 – 6.3 | 10 – 11% |
| Medicine | 7.5 – 9.0 | 2.4 – 2.9% |
| Surgery | 5.2 – 6.6 | 4.1 – 5.2% |
| Paediatrics | 3.5 – 3.8 | 23 – 24% |
| Critical care | 2.2 – 2.6 | 20 – 23% |
| Maternity and neonatal | 4.9 – 5.4 | 15 – 17% |

| Check | Status |
|---|---|
| Comparison with simple baselines ("same as last known value"; "same weekday last week") | **TODO.** The columns are in the back-test files. Not yet summarised |
| How often the actual value falls inside the 80% range | **TODO** |
| Bias (does it run high or low?) | **TODO** |
| Performance on the worst days (OPEL 3 and 4) | **TODO** |
| Performance by season | **TODO** |
| Performance after a change at the hospital (ward reconfiguration, system change) | **TODO** |
| Performance at any other hospital | Not possible. No data |

## 5. Intended use

To support operational decisions including staffing, opening and closing escalation beds, scheduling planned surgery and **discharge planning**.

Out-of-scope uses: *none identified.*

## 6. Fairness

Not applicable. The model uses no patient characteristics.

## 7. Human oversight

- Users can submit an "override" with a free-text reason. Overrides are stored. They do not change the forecast.
- Nobody is currently assigned to read overrides.
- There is no alert when the nightly file is late or the forecast is stale.
- There is no procedure for withdrawing the forecast.

## 8. Known limitations *(MO's list; incomplete)*

1. The target is beds **occupied**, because that is what is recorded.
2. The model does not know how many beds will be open on the day it is forecasting.
3. It knows nothing about ward closures for infection, care home or community capacity, or events at other hospitals.
4. Small units have large percentage errors.
5. The back-test year includes one unusual winter.
6. We have not tested what happens when an input is missing or wrong.

## 9. Version history

| Version | Date | Change |
|---|---|---|
| 0.1 | July 2026 | Same-weekday average |
| 0.2 | August 2026 | Gradient boosting on recent history |
| 0.3 | September 2026 | Added planned admissions, strikes and flu |

## 10. Open comments

- **MO, 23 Oct:** "I would not put '97 – 98% accurate' on anything until section 4's TODO rows are filled in. I suspect I know what they will show."
- **DR, 23 Oct:** "It's 100 minus the percentage error. It's arithmetic. Claros say 94."
- **MO, 23 Oct:** "A hospital with 440 beds occupied today will have about 440 occupied tomorrow whether or not we exist."
