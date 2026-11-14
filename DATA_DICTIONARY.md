# Data dictionary

Every table in the data room, column by column.

**Conventions**

- Dates are `YYYY-MM-DD` and times are 24-hour local time, unless a column name ends `_as_written` or the note says otherwise.
- A blank cell means the value is missing or does not apply.
- UK financial years run 1 April – 31 March. Money is in pounds unless the column name says otherwise.
- The files are as the organisations supplied them. They have not been cleaned.

---

## 01_company_wardline

### financials_monthly.csv
One row per month, November 2024 – December 2027.

| Column | Meaning |
|---|---|
| `month` | `YYYY-MM` |
| `type` | `Actual`, or `Plan (board-approved base case, Oct 2026)` |
| `recurring_revenue` | Subscription income recognised in the month |
| `services_revenue` | One-off implementation and training income |
| `grant_income` | Innovation grant |
| `total_income` | Sum of the three above |
| `payroll` … `regulatory_security_clinical_safety` | Cost lines |
| `total_costs` | Sum of cost lines |
| `capital_expenditure` | Equipment |
| `net_cash_flow` | `total_income − total_costs − capital_expenditure` |
| `opening_cash`, `closing_cash` | Bank balance at start and end of month |
| `headcount_end_of_month` | Employees |

### closed_deals_history.csv
One row per sales opportunity closed since 2021 (all for Wardline Live).

| Column | Meaning |
|---|---|
| `opportunity_id`, `account`, `country`, `product` | Identity |
| `first_meeting_date`, `close_date` | Start and end of the sales process |
| `outcome` | `Won`, `Lost`, or `No decision` |
| `annual_contract_value_gbp` | Annual value if won; 0 otherwise |
| `procurement_route` | How the buyer bought, or would have |
| `pilot_first` | `Y` if a pilot preceded the decision |
| `pilot_length_months`, `pilot_paid` | Pilot details (`Y`/`N`) |
| `loss_reason` | Sales team's note |
| `sales_cycle_days` | Days from first meeting to close |

### sales_pipeline.csv
One row per open opportunity at 31 October 2026.

| Column | Meaning |
|---|---|
| `stage` | `Lead` → `Discovery` → `Demo done` → `Proposal` |
| `created_date`, `last_activity_date`, `stage_entered_date`, `expected_close_date` | Dates |
| `annual_contract_value_gbp` | Sales team's estimate |
| `rep_probability_pct` | Sales team's own estimate of the chance of winning |
| `economic_buyer_role` | Who holds the budget |
| `champion_role` | Who inside the organisation is pushing for it |
| `procurement_route`, `competitor_present`, `main_blocker` | Sales notes |
| `days_in_current_stage`, `days_since_last_activity` | At 31 October 2026 |
| `weighted_value_gbp` | `annual_contract_value_gbp × rep_probability_pct ÷ 100` |

### pricing_discovery_calls.csv
22 conversations with potential buyers about price.

| Column | Meaning |
|---|---|
| `holds_budget` | `Y` if the person could approve the spend |
| `current_annual_spend_on_similar_tools_local` | What they say they spend now, local currency |
| `stated_wtp_low_local`, `stated_wtp_high_local` | Stated willingness to pay per year, local currency |
| `currency`, `fx_rate_to_gbp_used` | Currency and the conversion rate applied |
| `stated_wtp_low_gbp`, `stated_wtp_high_gbp` | Converted to pounds |
| `key_quote` | Verbatim |

### competitor_landscape.csv, partner_map.csv
Descriptive tables; column names are self-explanatory. `typical_annual_price_gbp` is our estimate of what a hospital pays.

### horizon_cost_assumptions.csv
| Column | Meaning |
|---|---|
| `scope` | What the cost attaches to: the product, each UK hospital, evaluation, EU expansion, Kenya, Indonesia |
| `unit` | Pounds one-off, pounds per year, FTE-months (one person for one month), or per cent |
| `low`, `base`, `high` | Three cases |
| `source_of_estimate` | Who estimated it, and from what |

### country_context.csv
Real published indicators for six countries, with the source and reference year of each row.

---

## 02_hospital_uk_kingsmere

### wards.csv
| Column | Meaning |
|---|---|
| `ward_code` | Reporting code used in the census, staffing and incident files |
| `ward_type` | Assessment unit, inpatient ward, escalation, ambulatory, or virtual location |
| `specialty_group` | `medical`, `surgical`, `escalation`, `critical`, `paediatric`, `maternity`, `neonatal` |
| `beds_established` | Funded beds |
| `counts_as_adult_general_and_acute` | 1 if the ward's beds count towards adult general and acute beds |
| `legacy_pas_code` | Code used in spell files before 12 October 2024 |
| `epr_location_code` | Code used in spell files from 12 October 2024 |

### inpatient_spells_2023-24.csv … inpatient_spells_2026-27_to_31Oct.csv
One row per hospital stay ("spell"). Includes every stay in hospital at any time from 1 April 2023 to 31 October 2026. Split by financial year of admission.

| Column | Meaning |
|---|---|
| `spell_id` | Stay identifier. Starts `L` (legacy PAS) or `E` (EPR) |
| `patient_pseudo_id` | Keyed hash of the patient's identity. The same patient has the same value in every stay and in the planned-admissions list |
| `source_system` | `LegacyPAS` or `CoreliaEPR` |
| `admission_type` | `Emergency`, `Elective`, `Maternity`, `Birth / neonatal` |
| `same_day_emergency_care` | `Y` if treated in the Same Day Emergency Care unit without an overnight bed |
| `admission_method` | Free text in the legacy system. National code in the EPR (see below) |
| `admission_source` | Where the patient came from |
| `ed_arrival_datetime` | Arrival in the emergency department. Blank if not admitted through it |
| `decision_to_admit_datetime` | When an emergency department clinician decided to admit |
| `admission_datetime` | When the patient reached an inpatient bed (or the Same Day Emergency Care unit) |
| `admission_ward`, `discharge_ward` | First and last ward, in the source system's own codes |
| `specialty` | Treating specialty |
| `primary_diagnosis_group` | Grouped main diagnosis, assigned by clinical coders after discharge |
| `age_at_admission`, `sex` | `sex`: `F`, `M`, `U` (unknown) |
| `ethnic_category` | As recorded |
| `imd_decile` | Index of Multiple Deprivation decile of the patient's home neighbourhood: 1 = most deprived tenth in England, 10 = least |
| `postcode_district` | First part of home postcode (`KM1` – `KM14`), `Out of area`, or `ZZ99` (no fixed abode or not known) |
| `charlson_comorbidity_count` | Number of long-term condition groups from the Charlson index. Adults only |
| `frailty_score_cfs` | Clinical Frailty Scale, 1 (very fit) to 9 (terminally ill). Recorded for some patients aged 65 and over |
| `critical_care_nights` | Nights spent in critical care |
| `ward_moves` | Moves between wards after the first |
| `nights_as_outlier` | Nights in a ward of the wrong specialty group |
| `discharge_ready_date` | Date the patient was first recorded as medically ready to leave ("no criteria to reside"). Adults only |
| `discharge_datetime` | Blank if still in hospital at the cut-off |
| `discharge_destination` | Where the patient went, or `Died` |
| `discharge_pathway` | `Pathway 0` – `Pathway 3` (see hospital profile). Adults only |
| `los_nights` | Midnights in hospital |
| `tci_id` | Link to `elective_tci_list.csv` for planned admissions |

**Admission method codes (NHS Data Model and Dictionary), used from 12 October 2024**

| Code | Meaning |
|---|---|
| 11 | Elective: waiting list |
| 21 | Emergency: via the emergency department |
| 22 | Emergency: via a general practitioner |
| 24 | Emergency: via a consultant clinic |
| 2B | Emergency: transfer of an admitted patient from another hospital |
| 31 | Maternity: admitted before delivery |
| 82 | Birth of a baby in this hospital |

### site_daily_sitrep.csv
One row per day: the hospital's daily situation report.

| Column | Meaning |
|---|---|
| `opel_level` | Alert level set that morning, 1 – 4 |
| `ed_attendances` | Emergency department attendances in the day |
| `ed_4hr_performance_pct` | Share of attendances admitted, transferred or discharged within 4 hours |
| `ed_decisions_to_admit` | Decisions to admit made in the emergency department |
| `trolley_waits_4_to_12hr`, `trolley_waits_over_12hr` | Patients admitted that day who had waited that long between the decision to admit and reaching a bed |
| `patients_awaiting_bed_0800` | Adults in the emergency department at 08:00 with a decision to admit and no bed |
| `ambulance_arrivals`, `ambulance_handovers_over_60min` | Ambulances arriving; those that waited over an hour to hand over |
| `adult_ga_beds_open` | Adult general and acute beds open at 08:00: core beds, plus escalation beds open, minus beds closed |
| `adult_ga_beds_occupied` | Of those beds, the number with a patient in at 08:00 |
| `escalation_beds_open` | Beds open on Ward 20 |
| `beds_closed_infection_estates` | Beds closed for infection control or building problems |
| `patients_in_temporary_escalation_spaces` | Admitted adults at 08:00 being cared for in a corridor or other space that is not a bed |
| `paediatric_beds_open`, `paediatric_beds_occupied` | Children's ward |
| `ga_occupancy_pct` | (Adult + paediatric beds occupied) ÷ (adult + paediatric beds open) |
| `critical_care_beds_occupied`, `maternity_beds_occupied`, `neonatal_cots_occupied` | At midnight |
| `emergency_admissions_adult`, `emergency_admissions_paediatric` | Emergency admissions to an inpatient bed |
| `sdec_attendances` | Same Day Emergency Care attendances (from the unit's own log) |
| `elective_inpatient_admissions`, `elective_daycases` | Planned admissions with and without an overnight stay |
| `discharges`, `discharges_before_noon`, `deaths` | Inpatients leaving alive in the day; of those, before 12:00; deaths |
| `nctr_patients_0800` | Adults medically ready to leave at 08:00 |
| `nctr_not_discharged` | Of those, still in hospital at midnight |
| `long_stay_7plus_days`, `long_stay_21plus_days` | Adults in hospital that long |
| `medical_outliers` | Medical patients in beds on non-medical wards |
| `elective_cancellations_on_day_nonclinical` | Planned operations cancelled by the hospital on the day for non-clinical reasons |
| `nursing_sickness_absence_pct` | Nursing sickness absence rate |

### ward_daily_census.csv
One row per ward per day.

| Column | Meaning |
|---|---|
| `beds_established`, `beds_open` | Funded beds; beds open that day |
| `patients_at_midnight` | Patients in the ward at the midnight ending this date |
| `admissions` | Patients arriving from outside the ward system (emergency department, home) |
| `transfers_in`, `transfers_out` | Moves from and to other wards |
| `discharges`, `deaths` | Leaving alive; deaths |
| `outlier_patients` | Patients of the wrong specialty group |
| `nctr_patients` | Medically ready to leave, at midnight |
| `closed_to_admissions` | 1 if the whole ward was closed to admissions |
| `beds_closed` | Beds closed |

A ward can hold more patients than it has beds open. Under the hospital's full-capacity protocol each adult ward takes an extra patient in a space that is not a bed; the SitRep counts these under temporary escalation spaces. Maternity, neonatal and children's wards have no hard limit.

### elective_tci_list.csv
One row per date offered to a patient for planned inpatient admission. A patient whose date is cancelled and rebooked has more than one row.

| Column | Meaning |
|---|---|
| `tci_id` | Booking identifier |
| `priority` | National clinical priority: `P2` within a month, `P3` within three months, `P4` routine |
| `planned_ward` | Reporting ward code |
| `date_added_to_waiting_list`, `date_booked`, `tci_date` | When the patient joined the list; when this date was offered; the planned admission date |
| `outcome` | `Admitted`, `Scheduled` (future), or a cancellation type |
| `cancellation_datetime`, `cancellation_reason` | For cancelled bookings |
| `rebooked_from_tci_id` | The cancelled booking this one replaces. It may be a booking from before 1 April 2023, which is not in the file |
| `times_previously_cancelled` | Earlier hospital cancellations for the same patient and procedure |
| `spell_id` | The resulting stay, if admitted. A few stays are missing from the stay files (see the information team's notes) |

### nurse_staffing_ward_shift.csv
One row per ward per shift. Day and night shifts are each 11.5 paid hours.

| Column | Meaning |
|---|---|
| `patients_at_shift_start` | Patients in the ward |
| `rn_planned_hours` | Registered nurse hours the roster called for |
| `rn_substantive_hours`, `rn_bank_hours`, `rn_agency_hours` | Hours worked by the ward's own staff, the trust's bank, and agency staff |
| `rn_unfilled_hours` | Planned hours nobody worked. Planned = substantive + bank + agency + unfilled |
| `rn_redeployed_hours` | Positive: hours worked here by nurses moved in from another ward. Negative: hours lost because this ward's nurses were moved out. Not included in the sum above |
| `hca_*` | The same for healthcare assistants |
| `red_flag_raised` | 1 if a nurse staffing red flag was raised (for example, a shortfall of more than a quarter of registered nurse time) |

### temporary_staffing_requests.csv
One row per request for a bank or agency shift, from 1 April 2025.

| Column | Meaning |
|---|---|
| `staff_group` | Registered nurse / midwife, or healthcare assistant |
| `reason` | Why the shift was needed |
| `requested_datetime`, `lead_time_hours` | When requested; hours between request and shift start |
| `outcome` | Filled by bank, framework agency or off-framework agency; unfilled; or cancelled |
| `hours`, `hourly_cost_gbp`, `total_cost_gbp` | Cost to the trust. Zero if unfilled or cancelled |

### flow_incident_log.csv
Incident reports in categories related to patient flow.

| Column | Meaning |
|---|---|
| `degree_of_harm` | As graded by the reporter: no harm, low, moderate, death |
| `opel_level_on_day` | Alert level on the incident date |
| `linked_spell_id` | The stay concerned, where recorded |

### ops_actions_log.csv
Decisions recorded by the site office: escalation beds opened and closed, extra discharge rounds, cancellations, requests for help, ward closures. `decided_at` is the meeting at which the decision was taken; `opel_level_that_morning` is the alert level set at 08:30 that day.

### external_signals_daily.csv
| Column | Meaning |
|---|---|
| `temp_max_c`, `temp_min_c`, `rain_mm`, `ice_or_snow_on_ground` | Local weather observations |
| `bank_holiday`, `school_holiday`, `industrial_action` | Calendar flags |
| `surveillance_week_ending`, `surveillance_published_date` | The week a surveillance figure describes, and the date it was published |
| `flu_positivity_pct`, `rsv_positivity_pct`, `covid_positivity_pct` | Share of regional laboratory samples testing positive that week |
| `norovirus_reports_index` | Regional laboratory reports of norovirus, indexed |

### calendar_events.csv
| Column | Meaning |
|---|---|
| `end_date` | Blank for a permanent change |
| `scope` | National, local, or local system |
| `known_in_advance` | Whether the hospital could have known before the start date |

---

## 03_hospital_kenya_kisima

### khis_monthly_inpatient_summary.csv
One row per ward per month, January 2022 – October 2026, as entered in the national health information system.

| Column | Meaning |
|---|---|
| `official_beds` | Beds on the ward's establishment |
| `admissions`, `discharges`, `deaths`, `absconded`, `referred_out` | Monthly counts |
| `inpatient_days` | Sum of the midnight counts for the month |
| `bed_occupancy_pct` | Inpatient days ÷ (official beds × days in month) |
| `average_length_of_stay_days` | Inpatient days ÷ (discharges + deaths) |
| `report_status` | `Submitted on time`, `Submitted late`, or `Not submitted` |

### khis_monthly_hospital_indicators.csv
Monthly hospital-wide figures: `rainfall_mm` (county weather station), `malaria_test_positivity_pct`, `confirmed_malaria_admissions`, `deliveries`, `caesarean_sections`, `outpatient_attendances`, `casualty_attendances`, `industrial_action`.

### ward_bed_state_daily_transcribed.csv
One row per ward per night, February – October 2026, typed up from photographs of the paper bed-state books.

| Column | Meaning |
|---|---|
| `patients_brought_forward` | Patients at the start of the day, as written |
| `admissions`, `discharges`, `deaths`, `absconded`, `referred_out` | As written |
| `patients_remaining_midnight` | As written |
| `patients_sharing_or_on_floor` | As written. Often blank |
| `nurses_on_night_duty` | Nurses on the night shift |
| `transcription_note` | Typist's comment on legibility |

### inpatient_register_sample_apr_jun_2026.csv
One row per line of the ward admission registers, April – June 2026, typed as written.

| Column | Meaning |
|---|---|
| `register_page_line` | Ward and line number in the book |
| `patient_name`, `ip_number`, `next_of_kin_phone` | Replaced with `[removed before sharing]` |
| `date_of_admission_as_written`, `date_of_discharge_as_written` | Free text; several date formats |
| `age_as_written`, `sex_as_written` | Free text; ages may be in years, months or days |
| `residence_as_written` | Village or estate, as the patient gave it |
| `diagnosis_as_written` | Free text, with ward abbreviations |
| `payment_as_written` | Cash, insurer or waiver |
| `outcome_as_written` | Discharged, died, referred, absconded; many spellings; sometimes blank |

### staffing_infrastructure_financing_monthly.csv
Monthly, from January 2024.

| Column | Meaning |
|---|---|
| `nurses_in_post`, `nurses_approved_establishment` | Nurses employed; posts the county has approved |
| `medical_officers_in_post`, `clinical_officers_in_post` | Doctors; clinical officers |
| `grid_power_outage_hours`, `generator_fuel_stockout_days` | Hours without mains electricity; days the generator had no fuel |
| `internet_downtime_hours`, `working_computers_on_wards` | Connectivity and equipment |
| `oxygen_plant_downtime_days` | Days the hospital's oxygen plant was not working |
| `insurance_claims_submitted_kes_m`, `insurance_claims_paid_kes_m` | Claims sent to, and paid by, the national insurer, in millions of Kenyan shillings |
| `cumulative_unpaid_claims_kes_m` | Running balance the insurer owes the hospital |
| `insurer`, `industrial_action` | Which insurer; any strike that month |

### wards.csv, context_events.csv
Ward list with official beds; dated events.

---

## 04_hospital_indonesia_sukamaju

Column names are in Bahasa Indonesia, as exported.

### ruangan.csv (wards)
| Column | English |
|---|---|
| `kode_ruangan`, `nama_ruangan` | Ward code and name |
| `pelayanan` | Service |
| `tt_sebelum_kris`, `tt_sesudah_kris_1jul2025` | Beds before the room standard was applied; beds from 1 July 2025 |

### sensus_harian_rawat_inap.csv (daily inpatient census)
One row per ward per day, 1 November 2024 – 31 October 2026.

| Column | English |
|---|---|
| `tanggal` | Date |
| `tt_tersedia` | Beds available |
| `pasien_awal` | Patients at start of day |
| `pasien_masuk` | Admitted |
| `pasien_pindahan`, `pasien_dipindahkan` | Transferred in from, and out to, another ward |
| `keluar_hidup` | Discharged alive |
| `meninggal_kurang_48_jam`, `meninggal_48_jam_atau_lebih` | Died within 48 hours of admission; died later |
| `pasien_akhir` | Patients at end of day |
| `hari_perawatan` | Patient-days |
| `tt_tambahan_dipakai` | Extra (temporary) beds in use |
| `keterangan` | Remarks |

### kunjungan_rawat_inap.csv (inpatient visits)
One row per admission. Dates are `DD/MM/YYYY`.

| Column | English |
|---|---|
| `no_kunjungan` | Visit number |
| `no_rm_hash` | Hashed medical record number |
| `tgl_masuk`, `jam_masuk` | Admission date and time |
| `cara_masuk` | Route in: `IGD` emergency department; `Poliklinik` outpatient clinic; `VK (kamar bersalin)` delivery room; `Lahir di RS` born in hospital; `Rujukan` referral |
| `asal_rujukan` | Referral source: `Datang sendiri` self; `Puskesmas` public health centre; `Klinik pratama` primary clinic; `Dokter praktik mandiri` private doctor; `RS lain` another hospital |
| `smf` | Department: `Penyakit Dalam` internal medicine; `Bedah` surgery; `Anak` paediatrics; `Kebidanan & Kandungan` obstetrics and gynaecology; `Saraf` neurology; `Jantung` cardiology; `Paru` pulmonology; `Perinatologi` newborn care; `Intensif` intensive care |
| `kode_ruangan` | Ward. `IGD` means the patient was admitted but never reached a ward |
| `kelas_hak`, `kelas_rawat` | Class entitled to; class actually placed in |
| `titip_kelas` | `Y` (ya, yes) if placed outside the entitled class; `T` (tidak, no) |
| `cara_bayar` | Payer |
| `kode_icd10`, `diagnosa_utama` | Main diagnosis code and name |
| `umur_tahun`, `jenis_kelamin` | Age in years; sex (`L` laki-laki, male; `P` perempuan, female) |
| `kecamatan` | Sub-district of residence |
| `tgl_keluar`, `jam_keluar` | Discharge date and time |
| `cara_keluar` | How the stay ended: `Atas persetujuan dokter` with the doctor's agreement; `Pulang atas permintaan sendiri (APS)` at own request; `Dirujuk` referred; `Dirujuk (kamar penuh)` referred because no room; `Meninggal` died, under or over 48 hours |
| `lama_rawat_hari` | Length of stay in days |
| `nilai_klaim_idr` | Claim value in rupiah |

### igd_harian.csv (emergency department, daily)
| Column | English |
|---|---|
| `kunjungan_igd` | Visits |
| `triase_merah`, `triase_kuning`, `triase_hijau` | Triage red, yellow, green |
| `dirawat_inap_dari_igd` | Admitted from the emergency department |
| `pasien_menunggu_kamar_0700` | Patients waiting for a room at 07:00 |
| `dirujuk_karena_kamar_penuh` | Referred elsewhere because the hospital was full |
| `meninggal_di_igd` | Died in the emergency department |

### ketenagaan_perawat.csv (nurse staffing)
Snapshots by ward on `tanggal_data` (date of the data): `jumlah_perawat_bidan` nurses and midwives; `status_pns`, `status_pppk`, `status_blud_kontrak` by employment type; `dinas_pagi_0700_1400`, `dinas_siang_1400_2100`, `dinas_malam_2100_0700` nurses on the morning, afternoon and night shifts; `tt_tersedia` beds.

### kalender_dan_kejadian.csv (calendar and events)
`tanggal_mulai`, `tanggal_selesai` start and end; `jenis` type (`Libur nasional` national holiday; `Cuti bersama` collective leave; `Kejadian penyakit` disease event; `Bulan Ramadan`; `Sistem informasi` information system; `Kebijakan` policy); `keterangan` description; `description_en` English translation.

---

## 05_users_and_workflows

### staff_survey_responses.csv
One row per response. The wording of each question is in `staff_survey_questionnaire.md`.

| Column | Meaning |
|---|---|
| `q1_confidence_predicting_24h`, `q2_confidence_predicting_7days` | 1 (not at all) to 5 (very) |
| `q3_hours_per_shift_on_bed_management` | Hours |
| `q4_tools_used_now`, `q10_concerns` | Several answers separated by a vertical bar |
| `q5_forecast_would_be_useful`, `q6_would_trust_algorithm_as_much_as_experienced_colleague` | 1 (strongly disagree) to 5 (strongly agree) |
| `q7_if_forecast_and_my_judgement_disagree_i_follow`, `q8_preferred_display`, `q9_decision_it_would_help_most`, `q11_device_at_work` | One choice from a list |
| `q12_dashboards_or_reports_already_looked_at_regularly` | Number |
| `q13_comment_original`, `q13_comment_english` | Free text as written, and its English translation |

### usability_test_participants.csv, usability_test_results.csv
One row per participant; one row per participant per task. `result` is `Completed`, `Completed with help` or `Not completed`. `sus_score` is the System Usability Scale, 0 – 100.

### prototype_trial_usage_log.csv
One row per page view or action in the Kingsmere shadow trial.

| Column | Meaning |
|---|---|
| `session_id`, `user_id`, `role`, `device` | Who and how |
| `page` | Screen viewed |
| `action` | `view`, `override_submitted`, `feedback_thumbs_up`, `feedback_thumbs_down` |
| `forecast_horizon_viewed_days` | Which day ahead the user selected on the home screen |
| `comment` | Free text entered by the user |

### decision_lead_times.csv
One row per type of decision at Kingsmere: who decides, where, how far ahead, and what the decision uses today.

---

## 06_responsible_innovation

| File | Rows are | Notes |
|---|---|---|
| `risk_register_draft.csv` | Risks raised internally | `likelihood_1to5` and `impact_1to5` are blank where nobody has scored them |
| `clinical_safety_hazard_log_draft.csv` | Hazards in the format of the NHS clinical risk management standard | Several rows unfinished |
| `regulatory_watchlist.csv` | Laws, standards and policies that may apply | `our_confidence_in_this_row` is the team's own view of how well it understands the item. Verify before relying on any row |
| `patient_public_panel_feedback.csv` | Comments from a patient and carer panel at Kingsmere and a community health volunteers' meeting in Kisima | `theme_assigned_by_note_taker` is one person's reading |
| `compute_footprint_estimates.csv` | Five technical options | `training_kwh_per_hospital_per_year`, `inference_kwh_per_hospital_per_year`, `hosting_kwh_per_hospital_per_year` and `total_kwh_per_hospital_per_year` are electricity in kilowatt-hours. `kgco2e_per_year_if_hosted_on_uk_grid`, `kgco2e_per_year_if_hosted_on_kenya_grid` and `kgco2e_per_year_if_hosted_on_indonesia_grid` convert the total to carbon using `assumed_grid_intensity_gco2e_per_kwh`, which holds the team's working assumptions |

---

## 07_prototype_v0_3

### backtest_site_level.csv, backtest_by_ward_group.csv
One row per target, issue date and horizon.

| Column | Meaning |
|---|---|
| `target` | What is being forecast (see the model card) |
| `forecast_issue_date` | The morning the forecast was produced, using data up to the previous midnight |
| `target_date`, `horizon_days` | The day forecast; days between issue and target |
| `forecast`, `lower_80`, `upper_80` | Central forecast and the range shown to users |
| `actual` | What happened |
| `naive_last_known_value` | The most recent value of the target available when the forecast was issued |
| `naive_same_weekday_last_week` | The value on the most recent same weekday available when the forecast was issued |

### forecast_issued_2026-10-31.csv
The forecast produced on the last day of data, for 1 – 7 November 2026. No actuals.
