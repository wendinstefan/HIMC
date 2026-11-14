# Data protection impact assessment — Horizon

**Version 0.2 — DRAFT — not reviewed, not signed**
**Author:** Laszlo Varga (Regulatory & QA), with sections completed by engineering
**Last edited:** 18 September 2026

> *Note from LV to the Head of Responsible Innovation, 2 November:* "This is where it stood when I was moved on to the Live recertification. Sections 3 to 7 were filled in by engineering from the Wardline Live template. I have not checked them. Kingsmere's information governance lead has already objected to at least one statement in it. I would not send this to anyone."

---

## 1. What is the project?

Horizon forecasts hospital bed demand for the next seven days. It uses historical hospital data to train a statistical model and shows the forecast to operational staff.

## 2. Why is a DPIA needed?

- Health data (special category).
- New technology (machine learning).
- Large scale: about 150,000 hospital stays from one trust.

## 3. What data is processed?

| Data | Source | Fields |
|---|---|---|
| Inpatient stays | Kingsmere | Stay identifier, pseudonymous patient identifier, admission and discharge dates and times, ward, specialty, diagnosis group, age, sex, ethnic category, deprivation decile, postcode district, comorbidity count, frailty score, discharge destination |
| Daily operational counts | Kingsmere | Counts only |
| Planned admissions list | Kingsmere | As inpatient stays, plus procedure and cancellation history |
| Staffing | Kingsmere | Hours by ward and shift. No staff identifiers |
| Trial usage log | Wardline | User identifier, role, time, page viewed, comments |
| Kenya and Indonesia files | Kisima; Sukamaju | *Not yet assessed* |

**Is the data identifiable?** No. The data is **anonymous**: names, NHS numbers, dates of birth and full postcodes are removed before it reaches us.

## 4. Roles

| | |
|---|---|
| Controller | *TBC — Kingsmere? Wardline? Joint?* |
| Processor | *TBC* |
| Sub-processors | Cloud hosting provider (UK South region) |

## 5. Lawful basis

- Article 6: **consent** *(copied from template — check)*
- Article 9 condition: *TBC*
- Common law duty of confidentiality: not applicable because the data is anonymous.
- National data opt-out: not applicable because the data is anonymous.

## 6. Necessity and proportionality

- **Is all the data needed?** Yes. More data makes a better model.
- **Could the purpose be achieved with less?** Not assessed.
- **Retention:** indefinitely, for model improvement.
- **Who has access?** The data science team (4), engineering (14), and contractors as needed. Engineers in the Utrecht office have the same access as those in the UK.
- **International transfers:** none.

## 7. Automated decision-making

Not applicable. Horizon does not make decisions about individuals.

## 8. Consultation

| Who | Consulted? |
|---|---|
| Trust Data Protection Officer | Informed |
| Caldicott Guardian | No |
| Patients or the public | Not required |
| Staff whose usage is logged | No |
| Staff representatives | No |

## 9. Risks

| Risk | Likelihood | Severity | Mitigation |
|---|---|---|---|
| Data breach | Low | High | ISO/IEC 27001 controls; encryption at rest and in transit |
| *(no other risks recorded)* | | | |

## 10. Sign-off

| | Name | Date |
|---|---|---|
| Wardline Data Protection Officer | | |
| Trust Data Protection Officer | | |
| Trust Caldicott Guardian | | |
| Senior Information Risk Owner | | |

---

### Open comments in the document

- **Ruth Castellanos (Kingsmere), 30 Sep:** "Section 3. A keyed hash with age, sex, ethnic category, postcode district and exact admission times is pseudonymised personal data. It is not anonymous. Everything in section 5 that follows from 'anonymous' is therefore wrong."
- **Mateus Oliveira, 2 Oct:** "For the record, the current model is trained on daily counts. It does not use any patient-level field. We asked for patient-level data because we thought we might need it."
- **Laszlo Varga, 2 Oct:** "Then why do we hold it?"
- **Aisha Rahman, 5 Oct:** "Section 6: there are three copies of the Kingsmere extract. Production bucket, the data science shared drive, and at least one laptop."
- **Head of Responsible Innovation:** *(no comments yet)*
