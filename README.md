# AI-powered patient flow: the data room

Synthetic data and documents for the Hyper Island module *Intelligent Machines* group activity, "AI-powered patient flow: a technology leadership challenge".

> **Everything here is fictional.** Wardline Health, Kingsmere Royal Infirmary, Kisima County Referral Hospital, RSUD Sukamaju, every other organisation and every person named in these files were invented for teaching. No real patient, staff or company data was used. Any resemblance to real people or organisations is coincidental.
>
> **What is real:** the laws, regulators, standards, national strike dates, public holidays and country indicators referred to. They were checked in November 2026, but treat them as a starting point and verify anything you rely on.

## The situation

It is **Friday 6 November 2026**. You are the leadership group of **Wardline Health**, a UK health-technology company with 36 staff. The company wants to launch **Horizon**: a system that forecasts hospital bed demand over the next seven days, so hospitals can plan admissions, discharges, staffing and capacity.

- The plan is to pilot in the UK or EU first, then explore Kenya and Indonesia.
- A prototype exists. It has been trialled in "shadow" mode at one NHS hospital.
- The board meets on **15 December 2026** and wants your recommendation: **proceed, pilot, redesign, defer or reject**.
- Time, money and information are all short. Start with `01_company_wardline/company_profile.md`.
- Things will happen while you work. When you are ready, open the cards in `08_inject_cards/` one at a time, as its README explains.

## What is in the data room

| Folder | Contents |
|---|---|
| `01_company_wardline/` | The company: finances, sales history, pipeline, pricing conversations, competitors, partners, cost estimates, and four weeks of emails, minutes and drafts |
| `02_hospital_uk_kingsmere/` | A 536-bed NHS hospital: three and a half years of patient-level stays, daily situation reports, ward census, planned admissions, nurse staffing, temporary staffing, incidents and operational decisions |
| `03_hospital_kenya_kisima/` | A county referral hospital in Kenya: monthly reports, nine months of hand-kept bed-state books, three months of ward registers |
| `04_hospital_indonesia_sukamaju/` | A regional public hospital in Indonesia: two years of daily census, admissions, emergency department and staffing data |
| `05_users_and_workflows/` | How bed management works today; interviews at all three hospitals; a staff survey; usability tests; the trial usage log |
| `06_responsible_innovation/` | Draft risk register, hazard log and impact assessment; regulatory watchlist; patient and staff feedback; data-sharing correspondence; trial incident notes |
| `07_prototype_v0_3/` | The prototype: draft model card, screen descriptions, a twelve-month back-test and the latest forecast |
| `08_inject_cards/` | Ten messages that arrive between 9 and 24 November. Open them one at a time, when the folder's README says to |

`DATA_DICTIONARY.md` explains every column.

## Where each role might start

| Role | Start with | Then |
|---|---|---|
| **VP Strategy & Commercial** | `01_company_wardline/` | Temporary staffing, cancellations and the operational log in `02_…`; the hospital profiles in `03_…` and `04_…` |
| **Director of Data & AI** | `07_prototype_v0_3/` and `02_hospital_uk_kingsmere/data_notes_from_information_team.md` | All the hospital data; `06_…/compute_footprint_estimates.csv` |
| **Head of Responsible Innovation & Clinical Trust** | `06_responsible_innovation/` | The incident log, stays and planned-admissions list in `02_…`; the interviews in `05_…` |
| **VP Product & Customer Experience** | `05_users_and_workflows/` | `07_…/prototype_screens.md`; the emails in `01_…/comms/` |

No role can answer its questions from its own folder alone.

## Questions the files can help with

- What exactly does the prototype forecast, and is that the thing a hospital needs to know?
- How good is it, compared with what a hospital can already do without it?
- Which decisions could a seven-day forecast change? Who makes them, and how far ahead?
- What would a hospital pay for, from which budget, and how long does it take them to buy?
- When the forecast is wrong in each direction, who pays the price? Is it the same people each time?
- What is different in Kenya and Indonesia: the data, the constraint, the buyer, the law, the device in someone's hand?
- What can the company afford, and by when?

## Health warnings

1. **The data is messy on purpose.** It has gaps, duplicates, typing errors, coding changes, a system migration and a week on paper. Some of this is documented in the files. Some is not.
2. **Things changed during the period.** Wards were reconfigured, services expanded, a supplier failed. A pattern that holds in 2023 may not hold in 2026.
3. **People in these files disagree, and some are wrong.** A number in an email is a claim, not a fact. Where you can, check it against the data.
4. **A recorded number is not always the thing you care about.** Ask how each figure is produced and what it cannot show.
5. **The drafts are drafts.** The model card, impact assessment, risk register and sales deck are unfinished and contain errors. Finding them is part of the work.
6. **You do not have everything.** Some of what you would want does not exist, or belongs to someone who has not been asked.

## Practical notes

- All tables are UTF-8 CSV. The four stay files are 5 – 12 MB each; everything else is small. Total size is about 62 MB.
- Open them with any spreadsheet, statistics package or notebook. In Python:

```python
import pandas as pd, glob
stays = pd.concat(pd.read_csv(f, dtype=str) for f in sorted(glob.glob("02_hospital_uk_kingsmere/inpatient_spells_*.csv")))
sitrep = pd.read_csv("02_hospital_uk_kingsmere/site_daily_sitrep.csv", parse_dates=["date"])
```

- Read identifiers and codes as text (`dtype=str`): some codes look like numbers.
- You may use AI tools to explore the files. Check what they tell you against the data.

## File inventory

<!-- INVENTORY:START -->
| File | Rows | Columns | What it is |
|---|---:|---:|---|
| `DATA_DICTIONARY.md` | | | Every table, column by column |
| `README.md` | | | This file |
| `01_company_wardline/closed_deals_history.csv` | 34 | 14 | Every sales opportunity closed since 2021 |
| `01_company_wardline/comms/2026-10-14_competitor_press_release_claros_flow.md` | | | A competitor announces a pilot |
| `01_company_wardline/comms/2026-10-27_board_minutes_extract.md` | | | What the board asked for |
| `01_company_wardline/comms/2026-10-30_email_kingsmere_cio.md` | | | The hospital's Chief Information Officer on a pilot |
| `01_company_wardline/comms/2026-11-03_email_ceo_pilot_this_quarter.md` | | | The Chief Executive's request to the leadership group |
| `01_company_wardline/comms/2026-11-05_sales_deck_claims_draft.md` | | | Draft sales claims, with comments |
| `01_company_wardline/comms/2026-q3_investor_update.md` | | | What investors were told in October |
| `01_company_wardline/company_profile.md` | | | Who Wardline is, what it sells, its money and its people |
| `01_company_wardline/competitor_landscape.csv` | 7 | 13 | Alternatives a hospital could choose |
| `01_company_wardline/country_context.csv` | 4 | 10 | Real published indicators for six countries |
| `01_company_wardline/financials_monthly.csv` | 38 | 19 | Income, costs and cash by month: actuals and the board's plan |
| `01_company_wardline/horizon_cost_assumptions.csv` | 24 | 8 | Cost estimates: low, base and high |
| `01_company_wardline/partner_map.csv` | 12 | 7 | Who the company depends on, and on what terms |
| `01_company_wardline/pricing_discovery_calls.csv` | 22 | 14 | What buyers said they would pay |
| `01_company_wardline/sales_pipeline.csv` | 28 | 20 | Open opportunities at 31 October 2026 |
| `02_hospital_uk_kingsmere/calendar_events.csv` | 60 | 6 | Strikes, holidays, service changes and other events |
| `02_hospital_uk_kingsmere/data_notes_from_information_team.md` | | | The hospital's own notes on the extracts |
| `02_hospital_uk_kingsmere/elective_tci_list.csv` | 14,187 | 19 | Planned inpatient admissions, including cancellations and rebookings |
| `02_hospital_uk_kingsmere/external_signals_daily.csv` | 1,310 | 14 | Weather, holidays and infection surveillance |
| `02_hospital_uk_kingsmere/flow_incident_log.csv` | 92 | 11 | Incident reports related to patient flow |
| `02_hospital_uk_kingsmere/hospital_profile.md` | | | The hospital, its beds, its pressures, and a glossary |
| `02_hospital_uk_kingsmere/inpatient_spells_2023-24.csv` | 47,232 | 30 | Hospital stays, one row each |
| `02_hospital_uk_kingsmere/inpatient_spells_2024-25.csv` | 46,460 | 30 | Hospital stays, one row each |
| `02_hospital_uk_kingsmere/inpatient_spells_2025-26.csv` | 37,075 | 30 | Hospital stays, one row each |
| `02_hospital_uk_kingsmere/inpatient_spells_2026-27_to_31Oct.csv` | 20,776 | 30 | Hospital stays, one row each |
| `02_hospital_uk_kingsmere/nurse_staffing_ward_shift.csv` | 56,806 | 16 | Planned and actual nursing hours by ward and shift |
| `02_hospital_uk_kingsmere/ops_actions_log.csv` | 1,045 | 5 | Decisions recorded by the site office |
| `02_hospital_uk_kingsmere/site_daily_sitrep.csv` | 1,311 | 37 | Daily situation report for the whole hospital |
| `02_hospital_uk_kingsmere/temporary_staffing_requests.csv` | 35,277 | 12 | Bank and agency shift requests, with lead time, outcome and cost |
| `02_hospital_uk_kingsmere/ward_daily_census.csv` | 28,820 | 14 | Midnight bed state by ward |
| `02_hospital_uk_kingsmere/wards.csv` | 24 | 10 | Ward list with both systems' codes |
| `03_hospital_kenya_kisima/context_events.csv` | 9 | 4 | Strikes, floods, outbreaks and policy changes |
| `03_hospital_kenya_kisima/hospital_profile.md` | | | The hospital, what 'full' means there, and a glossary |
| `03_hospital_kenya_kisima/inpatient_register_sample_apr_jun_2026.csv` | 4,601 | 13 | Ward admission registers typed up as written |
| `03_hospital_kenya_kisima/khis_monthly_hospital_indicators.csv` | 58 | 9 | Monthly rainfall, malaria, deliveries and attendances |
| `03_hospital_kenya_kisima/khis_monthly_inpatient_summary.csv` | 696 | 12 | Monthly ward reports to the national information system |
| `03_hospital_kenya_kisima/staffing_infrastructure_financing_monthly.csv` | 34 | 15 | Staff, power, internet, oxygen and insurance payments by month |
| `03_hospital_kenya_kisima/ward_bed_state_daily_transcribed.csv` | 2,945 | 13 | Nightly counts typed up from paper bed-state books |
| `03_hospital_kenya_kisima/wards.csv` | 12 | 3 | Ward list with official beds |
| `04_hospital_indonesia_sukamaju/hospital_profile.md` | | | The hospital, the bed reduction, and a Bahasa Indonesia glossary |
| `04_hospital_indonesia_sukamaju/igd_harian.csv` | 730 | 9 | Emergency department, daily |
| `04_hospital_indonesia_sukamaju/kalender_dan_kejadian.csv` | 59 | 5 | Holidays, outbreaks and system and policy changes |
| `04_hospital_indonesia_sukamaju/ketenagaan_perawat.csv` | 24 | 10 | Nurse staffing snapshots by ward |
| `04_hospital_indonesia_sukamaju/kunjungan_rawat_inap.csv` | 42,532 | 22 | Inpatient admissions, one row each |
| `04_hospital_indonesia_sukamaju/ruangan.csv` | 12 | 5 | Ward list with beds before and after the room standard |
| `04_hospital_indonesia_sukamaju/sensus_harian_rawat_inap.csv` | 8,760 | 15 | Daily inpatient census by ward |
| `05_users_and_workflows/decision_lead_times.csv` | 15 | 8 | Which decisions are made how far ahead, and by whom |
| `05_users_and_workflows/how_bed_management_works_today.md` | | | The daily routine at each hospital |
| `05_users_and_workflows/interviews_kingsmere_uk.md` | | | Nine interviews |
| `05_users_and_workflows/interviews_kisima_kenya.md` | | | Four interviews |
| `05_users_and_workflows/interviews_sukamaju_indonesia.md` | | | Four interviews |
| `05_users_and_workflows/prototype_trial_usage_log.csv` | 888 | 10 | Who looked at the prototype, when, and what they did |
| `05_users_and_workflows/staff_survey_questionnaire.md` | | | Survey questions and method |
| `05_users_and_workflows/staff_survey_responses.csv` | 412 | 22 | Survey responses from three hospitals |
| `05_users_and_workflows/usability_test_participants.csv` | 14 | 9 | Usability test participants |
| `05_users_and_workflows/usability_test_protocol_and_notes.md` | | | Usability test tasks and observer notes |
| `05_users_and_workflows/usability_test_results.csv` | 84 | 11 | Usability test results by task |
| `06_responsible_innovation/clinical_safety_hazard_log_draft.csv` | 9 | 12 | Draft clinical safety hazard log |
| `06_responsible_innovation/compute_footprint_estimates.csv` | 5 | 12 | Energy and carbon estimates for five technical options |
| `06_responsible_innovation/data_sharing_correspondence.md` | | | Three threads about how data was shared |
| `06_responsible_innovation/dpia_draft_v0.2.md` | | | Draft data protection impact assessment |
| `06_responsible_innovation/patient_public_panel_feedback.csv` | 32 | 6 | What patients, carers and staff said |
| `06_responsible_innovation/prototype_trial_incident_notes.md` | | | What went wrong during the shadow trial |
| `06_responsible_innovation/regulatory_watchlist.csv` | 25 | 9 | Laws, standards and policies that may apply |
| `06_responsible_innovation/risk_register_draft.csv` | 28 | 12 | Draft risk register |
| `07_prototype_v0_3/backtest_by_ward_group.csv` | 12,635 | 11 | Twelve months of daily forecasts against actuals: five ward groups |
| `07_prototype_v0_3/backtest_site_level.csv` | 5,054 | 11 | Twelve months of daily forecasts against actuals: whole site |
| `07_prototype_v0_3/forecast_issued_2026-10-31.csv` | 14 | 8 | The latest forecast, for 1 - 7 November 2026 |
| `07_prototype_v0_3/model_card_draft.md` | | | Draft description of the model and its performance |
| `07_prototype_v0_3/prototype_screens.md` | | | What the prototype shows, and what it does not |
| `08_inject_cards/README.md` | | | How and when to open the inject cards, with a log to fill in |
| `08_inject_cards/inject_01.md` | | | Inject card 1. Open only when the README says to |
| `08_inject_cards/inject_02.md` | | | Inject card 2. Open only when the README says to |
| `08_inject_cards/inject_03.md` | | | Inject card 3. Open only when the README says to |
| `08_inject_cards/inject_04.md` | | | Inject card 4. Open only when the README says to |
| `08_inject_cards/inject_05.md` | | | Inject card 5. Open only when the README says to |
| `08_inject_cards/inject_06.md` | | | Inject card 6. Open only when the README says to |
| `08_inject_cards/inject_07.md` | | | Inject card 7. Open only when the README says to |
| `08_inject_cards/inject_08.md` | | | Inject card 8. Open only when the README says to |
| `08_inject_cards/inject_09.md` | | | Inject card 9. Open only when the README says to |
| `08_inject_cards/inject_10.md` | | | Inject card 10. Open only when the README says to |
<!-- INVENTORY:END -->

## Using and sharing

Created for teaching at Hyper Island. The data is synthetic and may be reused for education with this notice attached. It must not be presented as real, used to train or validate a real clinical or operational system, or cited as evidence about any real hospital, company or country.
