# Kingsmere Royal Infirmary — hospital profile

*Fictional hospital. Prepared by Wardline's customer team from public documents and conversations with the trust, October 2026.*

## The organisation

Kingsmere Royal Infirmary is the main site of **Kingsmere University Hospitals NHS Foundation Trust**, in the north of England. It serves about 430,000 people in the city of Kingsmere and the surrounding rural districts (postcode districts KM1 to KM14). The trust employs about 5,200 people.

The hospital has the only emergency department (ED) in its area. The nearest alternative, Ashby Vale District Hospital, is 19 miles away. A separate elective orthopaedic hub opened off-site in September 2025.

## Beds

| Bed type | Beds | Wards |
|---|---|---|
| Adult general and acute (core) | 444 | AMU, W01–W12, W14–W16, SAU |
| Adult escalation (flexible) | up to 24 | W20, opened in blocks of 6 |
| Critical care | 16 | ICU |
| Children | 26 | CHW |
| Maternity (antenatal and postnatal) | 34 | MAT |
| Neonatal cots | 16 | NNU |
| **Total excluding escalation** | **536** | |

`wards.csv` lists every ward. Two things to know:

- **Assessment units.** Most emergency medical patients are admitted to the Acute Medical Unit (AMU) and move to a specialty ward within a day or two. Surgical emergencies go to the Surgical Assessment Unit (SAU).
- **The escalation ward (W20)** has no permanent staff. Opening it means finding nurses from somewhere else.

## Activity and pressure

Financial years run from 1 April to 31 March.

| | 2023-24 | 2024-25 | 2025-26 | 2026-27 (April – October) |
|---|---|---|---|---|
| ED attendances | 113,991 | 114,710 | 117,364 | 69,937 |
| Seen within 4 hours | 61.9% | 61.0% | 59.6% | 63.2% |
| Adult emergency admissions | 21,697 | 21,663 | 21,408 | 12,610 |
| Same Day Emergency Care attendances | 10,817 | 11,150 | 13,973 | 7,974 |
| Planned inpatient admissions | 3,636 | 3,731 | 3,147 | 1,727 |
| Day cases | 22,116 | 23,707 | 24,171 | 14,512 |
| Adult beds occupied at 08:00, share of beds open | 95.0% | 95.8% | 96.4% | 95.4% |
| Patients waiting over 12 hours in ED for a bed | 1,890 | 2,161 | 2,476 | 346 |
| Days at the highest alert level (OPEL 4) | 8.2% | 8.2% | 19.2% | 1.9% |

Source: the trust's validated figures. `site_daily_sitrep.csv` is the unvalidated daily return behind them; its totals will not match exactly until it has been cleaned. The 2026-27 column covers spring, summer and early autumn only.

## How pressure is described: OPEL

The NHS uses a four-level scale, the Operational Pressures Escalation Levels (OPEL):

| Level | Meaning in practice at Kingsmere |
|---|---|
| OPEL 1 | Normal working. Patients flow. |
| OPEL 2 | Starting to struggle. Extra discharge rounds. |
| OPEL 3 | Major pressure. Escalation beds opened. Planned operations for tomorrow reviewed and some cancelled. |
| OPEL 4 | Unable to deliver comprehensive care. Patients nursed in corridors and other "temporary escalation spaces". Help requested from neighbouring hospitals. |

The trust sets its own level each morning from occupancy, the number of patients in ED waiting for a bed, long waits, and the number of patients who are ready to leave but cannot.

## Things that have changed

| Date | Change |
|---|---|
| 12 October 2024 | New electronic patient record (Corelia EPR) replaced the old patient administration system (PAS). Codes changed. |
| 3 March 2025 | Same Day Emergency Care unit expanded: longer hours, more conditions. |
| 21 June 2025 | Major incident (motorway collision). |
| 1 September 2025 | Planned orthopaedic surgery moved to the off-site hub. Ward 15 became a general and elderly medicine ward. |
| 10 November 2025 | A large local care home provider went into administration. |
| 12 – 16 May 2026 | Cyber incident at a supplier. The EPR was unavailable and wards worked on paper. |

`calendar_events.csv` has these and more, including strikes, bank holidays and ward closures.

## People who are ready to leave

On a typical day about one adult patient in eight is medically ready to go home but still in a bed. Staff call this "no criteria to reside" (NCTR). Most are waiting for something outside the hospital: a care package at home, a community rehabilitation bed, or a care home place. Discharge routes are described as pathways:

| Pathway | Where the patient goes | Who arranges it |
|---|---|---|
| 0 | Home, no new support | Ward |
| 1 | Home with new care or therapy | Local authority and community services |
| 2 | Short-term rehabilitation bed | Community trust |
| 3 | Care home (new, long-term) | Local authority; family choice |

## Money

- The trust spent **£6.06m on temporary nursing staff** in 2025-26, of which £1.91m was agency (`temporary_staffing_requests.csv`, which starts on 1 April 2025).
- "Bank" staff are the trust's own pool of temporary workers and cost less than agency staff.
- The trust has a savings target of 5% this year. Any new spending needs a business case that shows cash-releasing savings or is funded from a specific pot (for example, winter funding).

## Glossary

| Term | Meaning |
|---|---|
| Admission (spell) | One continuous stay in hospital, from admission to discharge |
| AMU / SAU | Acute Medical Unit / Surgical Assessment Unit |
| Bank / agency | Temporary staff from the trust's own pool / from an external supplier |
| Boarding | A patient who needs a bed waiting in ED because none is free |
| Decision to admit (DTA) | The moment an ED clinician decides the patient needs a bed. The "12-hour trolley wait" clock starts here |
| EPR / PAS | Electronic patient record / patient administration system |
| Escalation bed | An extra bed opened under pressure, outside the funded bed base |
| IMD decile | Index of Multiple Deprivation: 1 = most deprived tenth of neighbourhoods in England, 10 = least |
| NCTR | "No criteria to reside": medically ready for discharge |
| Outlier | A patient in a ward that is not the right specialty (for example, a medical patient in a surgical bed) |
| SDEC | Same Day Emergency Care: patients assessed and treated without an overnight stay |
| SitRep | Situation report: the daily return of operational numbers |
| TCI | "To come in": a date given to a patient for planned admission |
| Temporary escalation space | A corridor or other area not designed for inpatient care, used when the hospital is full |
