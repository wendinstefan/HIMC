# Notes on the Kingsmere extracts

**From:** Owen Maddox, Head of Information, Kingsmere University Hospitals NHS Foundation Trust
**To:** Wardline data team
**Date:** 4 November 2026

These are the things we know about. There will be others. We are four analysts and this was done around the day job.

## What you have

| File | Source | Period |
|---|---|---|
| `inpatient_spells_*.csv` | Legacy PAS until 11 October 2024; Corelia EPR after | Every stay in hospital at any time between 1 April 2023 and 31 October 2026. Files are split by the financial year of *admission*; the first file also holds patients admitted earlier who were still in hospital on 1 April 2023 |
| `site_daily_sitrep.csv` | The daily return compiled by the site team | Same |
| `ward_daily_census.csv` | Midnight bed state by ward | Same |
| `elective_tci_list.csv` | Planned inpatient admissions (not day cases) | TCI dates to end of November 2026 |
| `nurse_staffing_ward_shift.csv` | E-rostering system | Same |
| `temporary_staffing_requests.csv` | Bank and agency booking system | From 1 April 2025 (the booking system was replaced then; earlier requests were not migrated) |
| `flow_incident_log.csv` | Incident reporting system, flow-related categories only | Same as spells |
| `ops_actions_log.csv` | Site office decision log | Same |
| `external_signals_daily.csv` | Weather service; regional public health surveillance | Same |

All extracts were taken on 2 November 2026 with a cut-off of midnight on 31 October.

## Known issues

1. **Two systems.** `spell_id` starts with `L` for the legacy PAS and `E` for the EPR. Ward codes differ between the two. The spell files carry each system's own codes; `wards.csv` maps both to the reporting codes used in every other file. Admission method was free text in the PAS and is a national code in the EPR. The lookup is in the data dictionary. The PAS text was typed by hand and is not consistent.

2. **Patients still in hospital at the cut-off** have no discharge date.

3. **Clinical coding runs six to eight weeks behind.** Recent discharges have no diagnosis group yet.

4. **Ethnicity** was poorly recorded in the PAS. It is better in the EPR but not complete.

5. **Discharge times in the PAS.** Where the ward clerk entered a date but no time, the PAS stored a default. Treat PAS discharge *times* with care. Dates are reliable.

6. **Discharge-ready date** was not a mandatory field before the EPR. It is blank for about a third of adult patients before go-live.

7. **May 2026 downtime (12 – 16 May).** Wards recorded admissions on paper. Back-entry was done by temporary staff over the following fortnight. We do not believe it was complete. We have not quantified the gap.

8. **Migration.** Patients who were in hospital on the night of go-live (11/12 October 2024) were migrated from PAS to EPR. Some may appear under both systems.

9. **The SitRep is a manual return.** It is typed into a spreadsheet by the site team, at weekends often by one person covering the whole hospital. Expect the occasional typing error and gap.

10. **IMD decile** comes from the patient's postcode. It is blank where the postcode was missing, invalid or outside England.

11. **Same Day Emergency Care.** Recording of SDEC activity changed in March 2025 when the unit expanded. You would need to ask the SDEC team for the detail. The SitRep count of SDEC attendances comes from the unit's own log and is unaffected.

12. **Small numbers.** We have not suppressed small counts. Please do not publish anything that could identify a patient.

## Things people get wrong with our data

- **Beds occupied cannot be higher than beds open.** That is how the bed state works. When we are full, the patients we cannot place are in ED or in temporary escalation spaces, and they are counted there.
- **Spell-level data and the SitRep will not agree exactly.** Different systems, different clocks, different people.
- **"Occupancy" has several denominators** (funded beds, beds open today, beds open and staffed). The SitRep uses beds open that morning, including any escalation beds.

## What we did not send

- Anything from the local authority or community trust about care packages, community beds or care home places. We do not hold it.
- Patient names, NHS numbers, full postcodes and dates of birth. `patient_pseudo_id` is a keyed hash. We hold the key.
- Outpatient, community and mental health activity.
- Free-text clinical notes.

Owen
