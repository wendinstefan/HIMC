# RSUD Sukamaju — hospital profile

*Fictional hospital in a fictional regency in Central Java, Indonesia. Prepared by Wardline from four video calls with an interpreter (June – October 2026). The laws, institutions and holidays mentioned are real. Data files keep their original Bahasa Indonesia column names; translations are in `DATA_DICTIONARY.md`.*

## The organisation

RSUD Sukamaju (*Rumah Sakit Umum Daerah*, regional public hospital) is a Type B hospital owned by the regency government. It operates as a semi-autonomous public service agency (BLUD), which means it keeps its own income and has some freedom over spending. It is the main referral hospital for about 1.3 million people.

| | |
|---|---|
| Inpatient admissions | About 58 a day |
| Emergency department (IGD) visits | About 125 a day |
| Average length of stay | 4.3 days |
| Beds | 338 until June 2025; **304** since 1 July 2025 |

## The bed reduction (KRIS)

Indonesia's national health insurance (JKN, run by BPJS Kesehatan) is replacing its three classes of inpatient room with a single standard, *Kelas Rawat Inap Standar* (KRIS). A KRIS room may hold no more than four beds, with minimum spacing, its own bathroom and other requirements.

To comply, RSUD Sukamaju took beds out of its six- and eight-bed rooms. From 1 July 2025 it has 34 fewer beds. Demand did not fall.

| | Before (November 2024 – June 2025) | After (July 2025 – October 2026) |
|---|---|---|
| Bed occupancy rate (BOR) | 70.8% | 82.9% |
| Patients waiting in the emergency department for a room at 07:00 | 0.7 | 12.8 |
| Patients referred elsewhere because the hospital was full | about 1 every ten months | about 13 a month |

Since July 2025 the main internal medicine ward (Mawar) has averaged 97% occupancy.

## Rooms, classes and "titip"

Wards (*ruangan*) are named after flowers. Each patient has an entitlement class (*kelas hak*) set by their insurance: Class 3, 2 or 1. When no bed is free in the right class, the patient is placed in a different class "on deposit" (*titip kelas*). This creates extra administration and disputes with the insurer about who pays the difference.

A bed is not interchangeable. Whether a patient can be placed depends on ward specialty, class, sex (rooms are single-sex) and infection status. A hospital can be at 83% occupancy and still have no bed for the next patient.

## What drives demand

- **Dengue** (*demam berdarah*, DBD) in the rainy season, roughly January to April. The district health office declared an outbreak (KLB) in February 2026.
- **Ramadan and Lebaran (Eid al-Fitr).** Planned admissions fall during the fasting month. In the week of Lebaran many staff are on leave and many people travel home (*mudik*). Road injuries rise.
- **Referral rules.** JKN patients are meant to arrive with a referral letter from a primary care clinic. A regional change in January 2026 sent more patients directly to Type B hospitals.

## How information works

- The hospital information system (SIMRS) is supplied and hosted by **PT Nusa Medika Digital**. It records admissions, room moves, discharges and billing.
- The hospital's own IT officers can export files. An automated interface needs the vendor.
- The daily census (*sensus harian*) is produced from SIMRS, except when the server is down.
- Electronic medical records are mandatory in Indonesia and must connect to the national platform, SATUSEHAT.
- Staff communicate by WhatsApp. The morning report (*laporan pagi*) to the directors is a WhatsApp message with a photo of a spreadsheet.

## Money

- About 87% of inpatients are covered by JKN. JKN pays a fixed tariff per case (INA-CBG), not per day. A longer stay earns nothing extra.
- The median claim value is about IDR 4.0 million (roughly £190) per admission.
- The hospital buys through the government e-catalogue. Foreign suppliers normally sell through a locally registered company.

## Who wants what

- **dr. Sri Wahyuni, Wakil Direktur Pelayanan (deputy director, services):** wants tomorrow's and next week's bed position by room and class in the morning report, and warning of dengue surges.
- **dr. Bambang Hartono, Direktur:** asks whether a forecast would help defend the hospital's accreditation and its case to the regency for a new building.
- **PT Nusa Medika Digital:** wants to sell the forecast as its own SIMRS module. Its terms are in `01_company_wardline/partner_map.csv`.

## Glossary

| Bahasa Indonesia | English |
|---|---|
| APS (*atas permintaan sendiri*) | Discharge at the patient's own request, against advice |
| BOR | Bed occupancy rate |
| BPJS Kesehatan / JKN | The national health insurer / the national health insurance scheme |
| Dirujuk | Referred to another hospital |
| IGD (*instalasi gawat darurat*) | Emergency department |
| Kelas hak / kelas rawat | Class the patient is entitled to / class the patient is actually in |
| Kepala ruangan | Head nurse of a ward |
| KLB (*kejadian luar biasa*) | Officially declared outbreak |
| PBI / Non-PBI | JKN members whose contributions are paid by government (poorer households) / members who pay their own |
| PNS / PPPK / BLUD kontrak | Permanent civil servant / government contract employee / hospital-contract employee |
| Rawat inap | Inpatient care |
| Ruangan | Ward |
| SIMRS | Hospital management information system |
| SMF | Clinical department (specialty) |
| Titip kelas | Placed in a class other than the one the patient is entitled to |
| TT (*tempat tidur*) | Bed |
| Umum | Self-paying |
