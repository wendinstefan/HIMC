# Wardline Health — company profile

*Internal briefing for the Horizon leadership group. Prepared by the Chief of Staff, 2 November 2026. Fictional company; see the README.*

## Who we are

Wardline Health Ltd is a health-technology company founded in 2019, with its head office in London, an engineering team in Leeds and a Dutch subsidiary (Wardline Health B.V., Utrecht, set up in 2025 for EU sales). We have 36 employees.

| Function | People |
|---|---|
| Engineering | 14 |
| Data science | 4 |
| Product and design | 4 |
| Customer success and support | 6 |
| Sales and marketing | 4 |
| Clinical, regulatory and quality | 2 (plus a contract Clinical Safety Officer, 2 days a week) |
| Finance and operations | 2 |

## What we sell today: Wardline Live

Wardline Live is an electronic bed board. It shows, in real time, which beds are occupied, which patients are ready to leave and what each discharge is waiting for. It replaces whiteboards, phone calls and spreadsheets in the hospital's site office and on the wards.

- Live in **8 hospital organisations**: seven NHS acute trusts in England and one public hospital in Ireland. Nine contracts have been won since 2023; one customer (Aire & Wharfe Hospitals NHS Trust) did not renew in April 2026 after its new electronic patient record (EPR) system shipped a bed board of its own.
- Annual recurring revenue (ARR) at 31 October 2026: **£1,485,240**.
- Wardline Live describes the present. It does not predict anything. It is not a medical device.
- Assurance in place for Live: ISO/IEC 27001, Cyber Essentials Plus, NHS Data Security and Protection Toolkit ("Standards Met", 2025-26), a completed Digital Technology Assessment Criteria (DTAC) pack and a clinical safety case under DCB0129.

## What we want to sell next: Horizon

Horizon is a proposed product that forecasts hospital bed demand for the next seven days: admissions, discharges, occupancy, and what that means for staffing and capacity. The current state is a prototype (`horizon-proto-0.3`) built on historical data from one hospital.

| Date | What happened |
|---|---|
| March 2026 | Data-sharing agreement signed with Kingsmere University Hospitals NHS Foundation Trust, for "discovery and product research" only |
| April 2025 – September 2026 | An innovation grant of £419,400 part-funded the prototype. It has now ended |
| June – August 2026 | Historical extracts received from Kingsmere; prototype built |
| 7 September – 30 October 2026 | "Shadow" trial: 27 Kingsmere staff could look at the forecast each day. It was not to be used for decisions |
| 20 – 28 October 2026 | Usability tests with 14 people in the UK, Kenya and Indonesia |
| 27 October 2026 | Board meeting (see `comms/`) |
| **15 December 2026** | **Board decision on Horizon. The leadership group's recommendation is due before this** |

Horizon has no customers, no price list, no clinical safety case and no regulatory classification.

## Money

| | |
|---|---|
| Cash at 31 October 2026 | £2,142,079 |
| Net cash outflow, October 2026 | £245,927 |
| Average net outflow, August – October 2026 | £213,723 a month |
| Last funding round | Series A, £9.0m, March 2024, led by Northlight Ventures |

The board approved a base-case plan in October 2026 (`financials_monthly.csv`, rows marked "Plan"). It assumes four hires for Horizon in early 2027 and Horizon revenue starting in February 2027. On that plan, cash runs out in **June 2027**.

## Markets under discussion

1. **UK and EU first.** NHS acute trusts in England; then Ireland, the Netherlands, Germany and Sweden, where we have had first conversations.
2. **Kenya and Indonesia later.** Two hospitals have talked to us and shared data: Kisima County Referral Hospital (Kenya) and RSUD Sukamaju (Indonesia). The board's instruction is to pilot in the UK or EU first and *explore* these two. Nobody has yet said what "explore" should cost.

## The Horizon leadership group

Four people own the recommendation. Each has a red line.

| Role | Lens | Red line |
|---|---|---|
| VP Strategy & Commercial | Business | "I won't commit the company to a plan it can't pay for or deliver." |
| Director of Data & AI | Technology | "I won't claim performance that we haven't validated." |
| Head of Responsible Innovation & Clinical Trust | Society | "I won't support a release without human oversight and a plan for when the tool is wrong." |
| VP Product & Customer Experience | Bridge | "I won't ship something the people on the ward won't use or trust." |

## Other people you will meet in these files

**Wardline:** Freya Lindholm (Chief Executive and co-founder), Dev Ramanathan (Chief Technology Officer and co-founder), Callum Whitby (Chief Financial Officer), Gareth Pryce (Sales Director), Aisha Rahman (Engineering Lead), Mateus Oliveira (Senior Data Scientist), Laszlo Varga (Regulatory & QA Analyst), Dr Niamh Brennan (contract Clinical Safety Officer), Margaret Oyelaran (Chair of the board), Tobias Kern (Northlight Ventures, investor director).

**Kingsmere (UK):** Adaeze Nwosu (Chief Operating Officer), Tom Hallworth (Deputy Chief Operating Officer and our sponsor), Priya Venkataraman (Chief Information Officer), Ruth Castellanos (Head of Information Governance and Data Protection Officer), Sandra Ellery (Chief Nurse), Owen Maddox (Head of Information), Dr Imran Sheikh (Caldicott Guardian, the senior clinician responsible for protecting patient confidentiality).

**Kisima (Kenya):** Dr Achieng Odhiambo (Medical Superintendent), Sr Mercy Wanjiru (Nursing Officer in Charge, paediatrics), Peter Kiplagat (Health Records & Information Officer), Daniel Mwangi (Afya Bora Foundation).

**Sukamaju (Indonesia):** dr. Bambang Hartono (Direktur), dr. Sri Wahyuni (Wakil Direktur Pelayanan), Ns. Dewi Lestari (Kepala Ruangan, Mawar), Agus Setiawan (SIMRS officer), Rudy Tanoto (PT Nusa Medika Digital).

## Files in this folder

| File | What it is |
|---|---|
| `financials_monthly.csv` | Monthly income, costs and cash: actuals from November 2024, board plan to December 2027 |
| `closed_deals_history.csv` | Every sales opportunity closed since 2021, won or lost |
| `sales_pipeline.csv` | Open opportunities at 31 October 2026 |
| `pricing_discovery_calls.csv` | What 22 buyers said they would pay |
| `competitor_landscape.csv` | Seven alternatives, including doing nothing new |
| `partner_map.csv` | Who we depend on and on what terms |
| `horizon_cost_assumptions.csv` | Cost estimates with low, base and high cases |
| `country_context.csv` | Real published indicators for six countries |
| `comms/` | Emails, minutes and drafts from the last four weeks |
