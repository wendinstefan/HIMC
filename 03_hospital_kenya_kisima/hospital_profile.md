# Kisima County Referral Hospital — hospital profile

*Fictional hospital in a fictional county in western Kenya. Prepared by Wardline from three video calls and one two-day visit (August 2026). The laws, institutions and national events mentioned are real.*

## The organisation

Kisima County Referral Hospital is a public hospital run by the County Government of Kisima. It is the referral hospital for a county of about 1.1 million people, most of them rural. Twelve wards have **420 official beds**. On an ordinary night in 2026 the hospital held between 420 and 500 inpatients; in the June malaria peak it held about 500.

| | |
|---|---|
| Admissions | About 3,050 a month in 2025 |
| Deliveries | About 840 a month |
| Outpatient attendances | About 15,200 a month |
| Nurses in post / approved posts | 218 / 412 (September 2026) |
| Medical officers / clinical officers | 33 / 46 |
| Working computers on the wards | 5 to 8, depending on the month |

## What "full" means here

In the UK a hospital is full when every bed has a patient. Kisima does not turn patients away for lack of a bed. When a ward is full, patients share beds or lie on mattresses on the floor.

- In the monthly reports for 2025, the two medical wards averaged 123% and 127% occupancy, the paediatric ward 121% and the newborn unit 138%.
- The amenity (private) wing averaged 42% and the gynaecology ward 56%.
- On the paediatric ward the typical night shift in 2026 had two nurses for the whole ward: about 28 children per nurse.

The limits that matter, according to the Medical Superintendent, are **nurses, oxygen, blood and money**, in that order. Beds come fifth.

## What drives demand

- **Malaria.** Admissions rise about two months after heavy rain. The long rains fall from March to May; the peak in the wards comes in June and July.
- **Road traffic injuries**, especially motorcycle taxis (*boda boda*).
- **Maternity.** The hospital takes complicated deliveries from the whole county.
- **Strikes.** Health workers in Kenya have been on strike repeatedly since 2017, usually over pay and unpaid allowances. During a strike the hospital empties: the wards went from about 450 patients to under 120 in August 2026. Patients go to private and faith-based hospitals, or stay at home.

## How information works

| Source | What it is | Condition |
|---|---|---|
| Ward admission register | A paper book on each ward. One line per patient | Handwritten. Complete for admissions; discharge details often filled in late or not at all |
| Bed-state book | A paper book. Each night the nurse in charge writes the midnight count | Kept on most wards most nights. Arithmetic done by hand at the end of a twelve-hour shift |
| Monthly ward summary (form MOH 717 and others) | Tallied from the registers by the Health Records & Information Officer and entered into the national health information system (KHIS) | Due by the 15th of the following month. Usually on time. Sometimes not submitted |
| Hospital management system | Billing and pharmacy only, on a handful of computers in the accounts office | Wards do not use it |

There is no patient-level electronic record of who is in which bed.

For this project the hospital's records officer and two students photographed and typed up:

- nine months of bed-state books (`ward_bed_state_daily_transcribed.csv`);
- three months of ward registers (`inpatient_register_sample_apr_jun_2026.csv`). Names, inpatient numbers and telephone numbers were removed before sharing. Read the note in `06_responsible_innovation/data_sharing_correspondence.md` about how these files reached us.

## Infrastructure

- Grid power fails for about 32 hours in a typical month. A generator covers theatres, the newborn unit and the intensive care unit when there is fuel.
- The hospital's internet connection is down for about 70 hours a month. Staff use their own phones and buy their own data bundles.
- The oxygen plant broke down for a week in May 2026.

## Money

- Patients are covered by the Social Health Authority (SHA), which replaced the National Hospital Insurance Fund (NHIF) in October 2024, or pay cash. Some bills are waived for patients who cannot pay.
- The insurer pays slowly. `staffing_infrastructure_financing_monthly.csv` shows claims submitted, claims paid and the unpaid balance.
- The county has no budget line for software. The Medical Superintendent can approve spending up to about KES 100,000 (roughly £600) without the county's sign-off.

## Who wants what

- **Dr Achieng Odhiambo, Medical Superintendent:** "Tell me in May how bad June will be, so I can ask the county for nurses on locum and order oxygen and blood before I need them. A week ahead is too short for me. A month would change things."
- **County Department of Health:** wants a dashboard to show the Governor.
- **Afya Bora Foundation:** offers USD 150,000 over two years. Its conditions are in `01_company_wardline/partner_map.csv`.

## Glossary

| Term | Meaning |
|---|---|
| Absconded | Patient left without being discharged, often to avoid a bill they cannot pay |
| Amenity wing | Fee-paying private ward within the public hospital |
| Casualty | Emergency department |
| Clinical officer | A non-physician clinician with three to four years' training, who does much of the front-line medical work |
| KHIS | Kenya Health Information System, the national reporting platform |
| Locum | Temporary worker paid by the shift |
| NHIF / SHA | The former and current national health insurers |
| Referred out | Sent to another hospital, usually the national or regional teaching hospital |
| Waiver | Bill written off for a patient who cannot pay |
