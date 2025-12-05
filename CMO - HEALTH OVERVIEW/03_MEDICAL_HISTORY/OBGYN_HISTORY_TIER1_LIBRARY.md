# OBGYN History Tier 1 Library
## Comprehensive Obstetric & Gynecologic History for Patient Intake

**Document Version:** 1.0
**Last Updated:** 2025-12-04
**Purpose:** Standardized OBGYN history library for female patient intake with smart expansion logic
**Display Condition:** Only shown when `biological_sex = 'female'` in Section 1

---

## Document Overview

This library defines OBGYN-specific intake questions for female patients, organized into:

1. **Menstrual History** - Current menstrual status and patterns
2. **Pregnancy History** - Obstetric history (gravida/para)
3. **Gynecologic Conditions** - Current and past GYN diagnoses
4. **Gynecologic Surgeries** - GYN-specific surgical procedures
5. **Menopause & Hormone Therapy** - Menopausal status and HRT
6. **Screening History** - Preventive care dates (Pap, mammogram)

**Integration:** This section appears as **Section 3B** (between Medical History and Family History) when patient selects "Female" in Basic Information.

---

## Section Display Logic

```javascript
// Only display OBGYN section for female patients
if (patient.biological_sex === 'female') {
  showSection('section-3b-obgyn');
  updateProgressBar({ total_sections: 8 }); // Add 1 section
} else {
  hideSection('section-3b-obgyn');
  updateProgressBar({ total_sections: 7 }); // Standard 7 sections
}
```

---

# PART 1: MENSTRUAL HISTORY

---

## MENS-001: Current Menstrual Status

**Patient-Friendly Label:** What best describes your current menstrual status?
**Intake Priority:** 1 (Always visible for female patients)
**Field Type:** Radio (single select)
**Required:** Yes

**Options:**
| Option | Value | Clinical Meaning |
|--------|-------|------------------|
| I still have regular periods | `regular_periods` | Premenopausal, cycling normally |
| I still have periods but they're irregular | `irregular_periods` | May indicate PCOS, perimenopause, thyroid issues |
| I'm going through menopause (periods stopping) | `perimenopause` | Perimenopause transition |
| I no longer have periods (menopause complete) | `postmenopausal_natural` | Natural menopause |
| I had surgery that stopped my periods | `surgical_menopause` | Surgical menopause (hysterectomy/oophorectomy) |
| I'm currently pregnant | `pregnant` | Active pregnancy |
| I'm currently breastfeeding | `breastfeeding` | Lactational amenorrhea |

**Smart Expansion by Answer:**

### If `regular_periods` or `irregular_periods`:

```
┌──────────────────────────────────────────────────────────────┐
│ A few more questions about your periods:                     │
│                                                              │
│ 1. How old were you when you got your first period?          │
│    ○ Under 10  ○ 10-11  ○ 12-13  ○ 14-15  ○ 16 or older     │
│                                                              │
│ 2. How many days is your typical cycle (first day of one     │
│    period to first day of next)?                             │
│    ○ Less than 21 days                                       │
│    ○ 21-35 days (normal)                                     │
│    ○ 36-45 days                                              │
│    ○ More than 45 days or unpredictable                      │
│                                                              │
│ 3. Are your periods:                                         │
│    ○ Light  ○ Normal  ○ Heavy  ○ Very heavy (changing        │
│      pad/tampon every 1-2 hours)                             │
│                                                              │
│ 4. Do you have significant pain with your periods?           │
│    ○ No pain  ○ Mild (OTC meds help)  ○ Moderate             │
│    ○ Severe (miss work/school)                               │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### If `postmenopausal_natural`:

```
┌──────────────────────────────────────────────────────────────┐
│ 1. How old were you when your periods completely stopped?    │
│    ○ Under 40  ○ 40-44  ○ 45-50  ○ 51-55  ○ Over 55         │
│                                                              │
│ 2. Have you had any vaginal bleeding since menopause?        │
│    ○ No  ○ Yes (please describe below)                       │
│    [_________________________________________________]       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### If `surgical_menopause`:

```
┌──────────────────────────────────────────────────────────────┐
│ 1. What surgery caused your periods to stop?                 │
│    □ Hysterectomy (uterus removed)                           │
│    □ Oophorectomy (ovaries removed)                          │
│    □ Both uterus and ovaries removed                         │
│    □ Ablation (uterine lining destroyed)                     │
│    □ Not sure                                                │
│                                                              │
│ 2. How old were you when you had this surgery?               │
│    ○ Under 40  ○ 40-45  ○ 46-50  ○ Over 50                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### If `pregnant`:

```
┌──────────────────────────────────────────────────────────────┐
│ Congratulations! A few questions about your pregnancy:       │
│                                                              │
│ 1. How far along are you?                                    │
│    ○ First trimester (1-12 weeks)                            │
│    ○ Second trimester (13-26 weeks)                          │
│    ○ Third trimester (27+ weeks)                             │
│    ○ Not sure                                                │
│                                                              │
│ 2. Are you receiving prenatal care?                          │
│    ○ Yes, regularly  ○ Yes, started recently  ○ Not yet     │
│                                                              │
│ 3. Any complications so far?                                 │
│    □ None                                                    │
│    □ Gestational diabetes                                    │
│    □ High blood pressure/Preeclampsia                        │
│    □ Bleeding                                                │
│    □ Other: [_______________]                                │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Clinical Significance:**

| Finding | Score Modifier | Clinical Action |
|---------|----------------|-----------------|
| Irregular periods + age <40 | -5 Reproductive-Function | Screen for PCOS, thyroid |
| Early menopause (<40) | -8 Cardiovascular-Risk, -10 Musculoskeletal-Risk | Bone density screening, CVD prevention |
| Early menarche (<10) | -3 Reproductive-Risk | Slightly increased breast cancer risk |
| Very heavy periods | -6 Metabolic-Function | Check hemoglobin, iron, thyroid |
| Severe dysmenorrhea | -5 Reproductive-Function | Evaluate for endometriosis |
| Postmenopausal bleeding | **RED ALERT** | Immediate GYN referral (rule out cancer) |
| Currently pregnant | **PREGNANCY CONTEXT** | All medications reviewed for pregnancy safety |

**Database Schema:**

```sql
-- Table: intake_menstrual_history
CREATE TABLE intake_menstrual_history (
  form_id UUID REFERENCES patient_intake_forms(form_id) PRIMARY KEY,
  menstrual_status ENUM('regular_periods', 'irregular_periods', 'perimenopause',
                        'postmenopausal_natural', 'surgical_menopause',
                        'pregnant', 'breastfeeding') NOT NULL,
  age_menarche ENUM('under_10', '10-11', '12-13', '14-15', '16_plus') NULL,
  cycle_length ENUM('less_than_21', '21-35', '36-45', 'over_45') NULL,
  flow_amount ENUM('light', 'normal', 'heavy', 'very_heavy') NULL,
  dysmenorrhea_severity ENUM('none', 'mild', 'moderate', 'severe') NULL,
  age_menopause ENUM('under_40', '40-44', '45-50', '51-55', 'over_55') NULL,
  postmenopausal_bleeding BOOLEAN NULL,
  postmenopausal_bleeding_notes TEXT NULL,
  surgical_menopause_type VARCHAR(100)[] NULL,
  surgical_menopause_age ENUM('under_40', '40-45', '46-50', 'over_50') NULL,
  currently_pregnant BOOLEAN NULL,
  pregnancy_trimester ENUM('first', 'second', 'third', 'unknown') NULL,
  prenatal_care_status ENUM('regular', 'started_recently', 'not_yet') NULL,
  current_pregnancy_complications VARCHAR(100)[] NULL,
  expansion_data JSONB NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

---

# PART 2: PREGNANCY HISTORY (OBSTETRIC)

---

## OB-001: Pregnancy History Overview

**Patient-Friendly Label:** Have you ever been pregnant?
**Intake Priority:** 1
**Field Type:** Radio
**Required:** Yes

**Options:**
- Yes
- No
- Prefer not to answer

**Smart Expansion if "Yes":**

```
┌──────────────────────────────────────────────────────────────┐
│ Please tell us about your pregnancy history:                 │
│                                                              │
│ 1. How many times have you been pregnant (including          │
│    miscarriages, abortions, and current pregnancy)?          │
│    [__] total pregnancies                                    │
│                                                              │
│ 2. How many live births have you had?                        │
│    [__] live births                                          │
│                                                              │
│ 3. Have you had any:                                         │
│    Miscarriages: [__]                                        │
│    Ectopic pregnancies: [__]                                 │
│    Stillbirths: [__]                                         │
│    Abortions/terminations: [__]                              │
│                                                              │
│ 4. For your live births, how were they delivered?            │
│    Vaginal deliveries: [__]                                  │
│    C-sections: [__]                                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Clinical Notation (Gravida/Para):**

```
G = Gravida (total pregnancies)
P = Para (deliveries after 20 weeks) = Term + Preterm + Abortions + Living

GTPAL notation calculated automatically:
- G: Total pregnancies
- T: Term births (≥37 weeks)
- P: Preterm births (20-36 weeks)
- A: Abortions/losses (<20 weeks)
- L: Living children
```

**Database Schema:**

```sql
-- Table: intake_pregnancy_history
CREATE TABLE intake_pregnancy_history (
  form_id UUID REFERENCES patient_intake_forms(form_id) PRIMARY KEY,
  ever_pregnant BOOLEAN,
  total_pregnancies INT NULL CHECK (total_pregnancies >= 0 AND total_pregnancies <= 20),
  live_births INT NULL CHECK (live_births >= 0),
  miscarriages INT NULL CHECK (miscarriages >= 0),
  ectopic_pregnancies INT NULL CHECK (ectopic_pregnancies >= 0),
  stillbirths INT NULL CHECK (stillbirths >= 0),
  terminations INT NULL CHECK (terminations >= 0),
  vaginal_deliveries INT NULL CHECK (vaginal_deliveries >= 0),
  cesarean_sections INT NULL CHECK (cesarean_sections >= 0),
  -- Calculated fields
  gravida INT GENERATED ALWAYS AS (total_pregnancies) STORED,
  para INT GENERATED ALWAYS AS (live_births + stillbirths) STORED,
  expansion_data JSONB NULL
);
```

---

## OB-002: Pregnancy Complications History

**Patient-Friendly Label:** During any of your pregnancies, did you have any of these complications?
**Intake Priority:** 1 (Only shown if ever_pregnant = true)
**Field Type:** Checkbox (multi-select)
**Required:** No

**Options:**

```
───────────────────────────────────────────────────────────────
🤰 PREGNANCY COMPLICATIONS
───────────────────────────────────────────────────────────────

□ Gestational diabetes (diabetes during pregnancy)
□ Preeclampsia or high blood pressure during pregnancy
□ Preterm labor (before 37 weeks)
□ Placenta previa or placental abruption
□ Severe morning sickness (hyperemesis gravidarum)
□ Blood clots during pregnancy
□ Postpartum depression
□ Postpartum hemorrhage (heavy bleeding after delivery)
□ Emergency C-section
□ Stillbirth or late pregnancy loss
□ Baby with birth defects
□ Baby was very small (under 5.5 lbs) or very large (over 9 lbs)

☑️ None of these complications

□ Other pregnancy complications: [_________________________]
```

**Smart Expansion Examples:**

### If "Gestational diabetes" checked:

```
┌──────────────────────────────────────────────────────────────┐
│ About your gestational diabetes:                             │
│                                                              │
│ 1. How was it treated?                                       │
│    ○ Diet and exercise only                                  │
│    ○ Oral medication                                         │
│    ○ Insulin injections                                      │
│                                                              │
│ 2. Did you develop diabetes after the pregnancy?             │
│    ○ Yes, I now have Type 2 diabetes                         │
│    ○ No, my blood sugar returned to normal                   │
│    ○ Not sure / haven't been tested                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### If "Preeclampsia" checked:

```
┌──────────────────────────────────────────────────────────────┐
│ About your preeclampsia:                                     │
│                                                              │
│ 1. How severe was it?                                        │
│    ○ Mild (elevated BP, some protein in urine)               │
│    ○ Severe (very high BP, hospitalized)                     │
│    ○ HELLP syndrome or eclampsia (seizures)                  │
│    ○ Not sure                                                │
│                                                              │
│ 2. How early in pregnancy did it start?                      │
│    ○ After 34 weeks                                          │
│    ○ Before 34 weeks (early-onset)                           │
│    ○ Don't remember                                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Clinical Significance:**

| Complication | Future Risk | Score Modifier | Clinical Action |
|--------------|-------------|----------------|-----------------|
| **Gestational diabetes** | 7x Type 2 diabetes risk | -8 Metabolic-Risk | Screen for diabetes every 1-3 years |
| **Preeclampsia** | 2x CVD risk, 4x hypertension risk | -10 Cardiovascular-Risk | Annual BP monitoring, aspirin in future pregnancies |
| **Early preeclampsia (<34 wks)** | Higher CVD risk | -15 Cardiovascular-Risk | Cardiology consult, aggressive prevention |
| **Preterm delivery** | 2x CVD risk | -6 Cardiovascular-Risk | CVD risk factor modification |
| **Recurrent miscarriage (≥3)** | Screen for clotting disorders | -5 Reproductive-Function | Hematology workup |
| **Postpartum depression** | 50% recurrence risk | -8 Neurological-Function | Mental health screening |

**ICD-10 Codes for History:**
- Z87.59 - Personal history of complications of pregnancy, childbirth and the puerperium
- Z86.32 - Personal history of gestational diabetes
- O16.5 - Unspecified maternal hypertension, complicating the puerperium

---

# PART 3: GYNECOLOGIC CONDITIONS

---

## GYN-001: Current Gynecologic Conditions

**Patient-Friendly Label:** Do you have any of these gynecologic conditions?
**Intake Priority:** 1
**Field Type:** Checkbox (multi-select)

**Display Structure:**

```
───────────────────────────────────────────────────────────────
👩‍⚕️ GYNECOLOGIC CONDITIONS
───────────────────────────────────────────────────────────────

COMMON CONDITIONS (Always Visible - Priority 1):

□ Uterine fibroids (benign growths in the uterus)
□ Endometriosis
□ PCOS (polycystic ovary syndrome)
□ Ovarian cysts
□ Abnormal Pap smear or cervical dysplasia
□ Pelvic inflammatory disease (PID)
□ Chronic pelvic pain
□ Vulvodynia or vaginal pain
□ Urinary incontinence (leaking urine)
□ Pelvic organ prolapse (bladder, uterus, or rectum dropping)
□ Infertility (tried to get pregnant for over 1 year)

          [▼ Click here to see other gynecologic conditions]

───────────────────────────────────────────────────────────────

EXPANDED SECTION (Priority 2):

□ Adenomyosis
□ Ovarian insufficiency (early menopause before age 40)
□ Bartholin's cyst
□ Lichen sclerosus
□ Vaginismus
□ Interstitial cystitis / painful bladder syndrome
□ Vulvar or vaginal cancer history
□ Cervical cancer history
□ Uterine/endometrial cancer history
□ Ovarian cancer history

───────────────────────────────────────────────────────────────

☑️ I do not have any gynecologic conditions

□ Other gynecologic condition: [_________________________]
```

**Smart Expansion Examples:**

### GYN-FIBROID: Uterine Fibroids

**Expansion when checked:**

```
┌──────────────────────────────────────────────────────────────┐
│ About your uterine fibroids:                                 │
│                                                              │
│ 1. Are you having symptoms from your fibroids?               │
│    □ Heavy bleeding                                          │
│    □ Pelvic pain or pressure                                 │
│    □ Frequent urination                                      │
│    □ Constipation                                            │
│    □ No symptoms (found on imaging)                          │
│                                                              │
│ 2. Have you had any treatment for fibroids?                  │
│    □ No treatment / watching                                 │
│    □ Medication (birth control, GnRH agonists)               │
│    □ Myomectomy (surgical fibroid removal)                   │
│    □ Uterine artery embolization                             │
│    □ Hysterectomy                                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Score Modifiers:**
- Symptomatic fibroids: -8 Reproductive-Function
- Asymptomatic (incidental): -2 Reproductive-Function

**ICD-10:** D25.9 - Leiomyoma of uterus, unspecified

---

### GYN-ENDO: Endometriosis

**Expansion when checked:**

```
┌──────────────────────────────────────────────────────────────┐
│ About your endometriosis:                                    │
│                                                              │
│ 1. How was it diagnosed?                                     │
│    ○ Laparoscopy (surgery)                                   │
│    ○ Imaging (ultrasound/MRI)                                │
│    ○ Clinical diagnosis based on symptoms                    │
│    ○ Not sure                                                │
│                                                              │
│ 2. What are your main symptoms?                              │
│    □ Severe period pain                                      │
│    □ Pain during sex                                         │
│    □ Chronic pelvic pain (not just during period)            │
│    □ Bowel or bladder symptoms with periods                  │
│    □ Infertility                                             │
│    □ Minimal symptoms now                                    │
│                                                              │
│ 3. Current treatment:                                        │
│    □ None                                                    │
│    □ Birth control (pills, IUD, etc.)                        │
│    □ GnRH agonists (Lupron, Orilissa)                        │
│    □ Had surgery for endometriosis                           │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Score Modifiers:**
- Endometriosis: -10 Reproductive-Function
- With chronic pelvic pain: -8 Neurological-Function (pain)
- With infertility: -5 Reproductive-Function additional

**ICD-10:** N80.9 - Endometriosis, unspecified

---

### GYN-PCOS: Polycystic Ovary Syndrome

**Expansion when checked:**

```
┌──────────────────────────────────────────────────────────────┐
│ About your PCOS:                                             │
│                                                              │
│ 1. Which symptoms do you experience?                         │
│    □ Irregular or absent periods                             │
│    □ Excess hair growth (face, chest, back)                  │
│    □ Acne                                                    │
│    □ Weight gain / difficulty losing weight                  │
│    □ Thinning hair on scalp                                  │
│    □ Difficulty getting pregnant                             │
│                                                              │
│ 2. Have you been told you have:                              │
│    □ Insulin resistance or prediabetes                       │
│    □ High cholesterol                                        │
│    □ Neither / not tested                                    │
│                                                              │
│ 3. Current treatment:                                        │
│    □ None                                                    │
│    □ Birth control pills                                     │
│    □ Metformin                                               │
│    □ Spironolactone (for hair/acne)                          │
│    □ Fertility medications                                   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Score Modifiers:**
- PCOS: -10 Endocrine-Function
- PCOS + insulin resistance: -8 Metabolic-Risk, -6 Cardiovascular-Risk
- PCOS + infertility: -5 Reproductive-Function

**ICD-10:** E28.2 - Polycystic ovarian syndrome

---

### GYN-ABNPAP: Abnormal Pap Smear / Cervical Dysplasia

**Expansion when checked:**

```
┌──────────────────────────────────────────────────────────────┐
│ About your abnormal Pap smear:                               │
│                                                              │
│ 1. What were you told about the abnormal result?             │
│    ○ Mild changes (LSIL, CIN 1)                              │
│    ○ Moderate/severe changes (HSIL, CIN 2/3)                 │
│    ○ HPV positive but Pap normal                             │
│    ○ Cervical cancer                                         │
│    ○ Don't remember / not sure                               │
│                                                              │
│ 2. What treatment did you have?                              │
│    □ Watchful waiting (repeat Paps)                          │
│    □ Colposcopy (biopsy during exam)                         │
│    □ LEEP or cone biopsy (removed abnormal cells)            │
│    □ Hysterectomy                                            │
│    □ Other treatment                                         │
│                                                              │
│ 3. When was your last Pap smear?                             │
│    ○ Within the last year                                    │
│    ○ 1-3 years ago                                           │
│    ○ More than 3 years ago                                   │
│    ○ Don't remember                                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Score Modifiers:**
- History of CIN 2/3: -5 Reproductive-Risk
- Overdue Pap (>3 years): **CARE GAP ALERT**

**ICD-10:**
- R87.619 - Unspecified abnormal cytological findings in Pap smear of cervix
- N87.9 - Dysplasia of cervix uteri, unspecified

---

### GYN-INCONT: Urinary Incontinence

**Expansion when checked:**

```
┌──────────────────────────────────────────────────────────────┐
│ About your urinary incontinence:                             │
│                                                              │
│ 1. What type of leaking do you experience?                   │
│    □ Leaking when you cough, sneeze, or exercise (stress)    │
│    □ Sudden strong urge and can't make it to bathroom (urge) │
│    □ Both types                                              │
│                                                              │
│ 2. How often does this happen?                               │
│    ○ Rarely (a few times a month)                            │
│    ○ Weekly                                                  │
│    ○ Daily                                                   │
│    ○ Multiple times daily                                    │
│                                                              │
│ 3. Have you had treatment?                                   │
│    □ No treatment                                            │
│    □ Pelvic floor exercises / physical therapy               │
│    □ Medication                                              │
│    □ Surgery                                                 │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Score Modifiers:**
- Urinary incontinence: -8 Reproductive-Function (pelvic floor)
- Daily or worse: -10 Reproductive-Function

**ICD-10:**
- N39.3 - Stress incontinence
- N39.41 - Urge incontinence
- N39.46 - Mixed incontinence

---

## GYN Conditions Database Schema

```sql
-- Table: intake_gyn_conditions
CREATE TABLE intake_gyn_conditions (
  id SERIAL PRIMARY KEY,
  form_id UUID REFERENCES patient_intake_forms(form_id) NOT NULL,
  condition_code VARCHAR(20) NOT NULL, -- e.g., 'GYN-FIBROID'
  expansion_data JSONB NULL,
  severity ENUM('mild', 'moderate', 'severe') NULL,
  treatment_status ENUM('none', 'medical', 'surgical', 'resolved') NULL,
  is_free_text BOOLEAN DEFAULT FALSE,
  free_text_description TEXT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_gyn_conditions_form ON intake_gyn_conditions(form_id);
```

---

# PART 4: GYNECOLOGIC SURGERIES

---

## GYNSURG: Gynecologic Surgical History

**Patient-Friendly Label:** Have you had any of these gynecologic surgeries or procedures?
**Intake Priority:** 1
**Field Type:** Checkbox (multi-select)

**Display Structure:**

```
───────────────────────────────────────────────────────────────
🏥 GYNECOLOGIC SURGERIES & PROCEDURES
───────────────────────────────────────────────────────────────

MAJOR SURGERIES:

□ Hysterectomy (uterus removal)
□ Oophorectomy (ovary removal - one or both)
□ Myomectomy (fibroid removal)
□ Cesarean section (C-section)
□ Tubal ligation (tubes tied)

MINOR PROCEDURES:

□ D&C (dilation and curettage)
□ LEEP or cone biopsy (cervical procedure)
□ Laparoscopy (diagnostic or for endometriosis)
□ Hysteroscopy
□ Ovarian cyst removal
□ Bartholin's cyst drainage
□ Colposcopy with biopsy
□ IUD placement or removal

BREAST PROCEDURES:

□ Breast biopsy
□ Lumpectomy
□ Mastectomy
□ Breast reduction or lift
□ Breast augmentation

───────────────────────────────────────────────────────────────

☑️ I have not had any gynecologic surgeries

□ Other GYN surgery: [_________________________]
```

**Smart Expansion for Key Surgeries:**

### GYNSURG-HYST: Hysterectomy

```
┌──────────────────────────────────────────────────────────────┐
│ About your hysterectomy:                                     │
│                                                              │
│ 1. What type of hysterectomy?                                │
│    ○ Total (uterus and cervix removed)                       │
│    ○ Partial/subtotal (uterus only, cervix left)             │
│    ○ Radical (for cancer - uterus, cervix, upper vagina)     │
│    ○ Not sure                                                │
│                                                              │
│ 2. Were your ovaries removed too?                            │
│    ○ Both ovaries removed                                    │
│    ○ One ovary removed                                       │
│    ○ Ovaries were left in                                    │
│    ○ Not sure                                                │
│                                                              │
│ 3. Why did you need the hysterectomy?                        │
│    □ Fibroids                                                │
│    □ Heavy bleeding                                          │
│    □ Endometriosis                                           │
│    □ Prolapse                                                │
│    □ Cancer or precancer                                     │
│    □ Other / don't remember                                  │
│                                                              │
│ 4. When was the surgery?                                     │
│    ○ Less than 1 year ago                                    │
│    ○ 1-5 years ago                                           │
│    ○ 5-10 years ago                                          │
│    ○ More than 10 years ago                                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Clinical Implications:**

| Finding | Clinical Impact |
|---------|-----------------|
| Hysterectomy with ovaries intact | Cervix status determines Pap need |
| Hysterectomy with BSO (both ovaries) before 45 | Surgical menopause, CVD risk, bone loss |
| Cervix removed (total hysterectomy) | No Pap smears needed (unless cancer history) |
| Cervix present (subtotal) | Still needs Pap smears |

**Auto-Update Medical History:**
- If ovaries removed → Auto-add "Surgical menopause" to menstrual status
- If for cancer → Auto-add to cancer history

---

## GYN Surgeries Database Schema

```sql
-- Table: intake_gyn_surgeries
CREATE TABLE intake_gyn_surgeries (
  id SERIAL PRIMARY KEY,
  form_id UUID REFERENCES patient_intake_forms(form_id) NOT NULL,
  procedure_code VARCHAR(20) NOT NULL, -- e.g., 'GYNSURG-HYST'
  expansion_data JSONB NULL,
  when_performed ENUM('<1_year', '1-5_years', '5-10_years', '10+_years') NULL,
  is_free_text BOOLEAN DEFAULT FALSE,
  free_text_description TEXT NULL,
  linked_diagnoses VARCHAR(20)[] NULL, -- Auto-linked conditions
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_gyn_surgeries_form ON intake_gyn_surgeries(form_id);
```

---

# PART 5: MENOPAUSE & HORMONE THERAPY

---

## MENO-001: Menopausal Status & Symptoms

**Only shown if:** `menstrual_status IN ('perimenopause', 'postmenopausal_natural', 'surgical_menopause')`

**Questions:**

```
───────────────────────────────────────────────────────────────
🌸 MENOPAUSE SYMPTOMS & HORMONE THERAPY
───────────────────────────────────────────────────────────────

1. Are you experiencing any menopausal symptoms?
   (Check all that apply)

   □ Hot flashes or night sweats
   □ Vaginal dryness
   □ Difficulty sleeping
   □ Mood changes (irritability, depression, anxiety)
   □ Memory or concentration problems
   □ Joint or muscle aches
   □ Decreased sex drive
   □ Weight gain
   □ None of these

2. Are you using hormone replacement therapy (HRT)?

   ○ Yes, currently taking hormones
   ○ No, never tried
   ○ Tried in the past but stopped
   ○ Interested in discussing HRT

   [IF YES, CURRENTLY TAKING:]
   ┌────────────────────────────────────────────────────────┐
   │ What type of hormone therapy?                          │
   │   □ Estrogen only (pill, patch, gel, or spray)        │
   │   □ Estrogen + progesterone combination               │
   │   □ Vaginal estrogen only (cream, ring, or tablet)    │
   │   □ Bioidentical/compounded hormones                  │
   │   □ Not sure of the type                              │
   │                                                        │
   │ How long have you been on HRT?                         │
   │   ○ Less than 1 year                                  │
   │   ○ 1-5 years                                         │
   │   ○ More than 5 years                                 │
   └────────────────────────────────────────────────────────┘

3. Have you been told you have osteoporosis or low bone density?
   ○ Yes, osteoporosis
   ○ Yes, osteopenia (low bone density)
   ○ No
   ○ Never been tested
```

**Score Modifiers:**

| Finding | Score Modifier |
|---------|----------------|
| Significant menopausal symptoms (3+) | -6 Neurological-Function (quality of life) |
| Early menopause (<40) + no HRT | -10 Cardiovascular-Risk, -12 Musculoskeletal-Risk |
| On HRT for >5 years after menopause | Increased monitoring for breast/CVD |
| Osteoporosis | -12 Musculoskeletal-Structure (link to MSK library) |

**Database Schema:**

```sql
-- Table: intake_menopause
CREATE TABLE intake_menopause (
  form_id UUID REFERENCES patient_intake_forms(form_id) PRIMARY KEY,
  menopause_symptoms VARCHAR(100)[] NULL,
  hrt_status ENUM('current', 'never', 'past', 'interested') NULL,
  hrt_type VARCHAR(100)[] NULL,
  hrt_duration ENUM('<1_year', '1-5_years', '5+_years') NULL,
  osteoporosis_status ENUM('osteoporosis', 'osteopenia', 'no', 'not_tested') NULL,
  expansion_data JSONB NULL
);
```

---

# PART 6: SCREENING HISTORY

---

## SCREEN-001: Preventive Screening Dates

**Purpose:** Track when patient last had key screenings to identify care gaps

```
───────────────────────────────────────────────────────────────
📋 PREVENTIVE SCREENING HISTORY
───────────────────────────────────────────────────────────────

Help us keep your preventive care up to date.

1. When was your last Pap smear (cervical cancer screening)?
   ○ Within the last year
   ○ 1-3 years ago
   ○ More than 3 years ago
   ○ Never had one
   ○ Don't need one (had hysterectomy with cervix removed)
   ○ Don't remember

2. When was your last mammogram (breast cancer screening)?
   [ONLY SHOWN IF AGE ≥40]
   ○ Within the last year
   ○ 1-2 years ago
   ○ More than 2 years ago
   ○ Never had one
   ○ Don't remember

3. When was your last bone density scan (DEXA)?
   [ONLY SHOWN IF AGE ≥65 OR POSTMENOPAUSAL]
   ○ Within the last 2 years
   ○ 2-5 years ago
   ○ More than 5 years ago
   ○ Never had one
   ○ Don't remember

4. Are you up to date on HPV vaccination?
   [ONLY SHOWN IF AGE ≤45]
   ○ Yes, completed the series
   ○ Yes, partially vaccinated
   ○ No
   ○ Not sure
```

**Care Gap Alerts:**

| Finding | Alert Level | Action |
|---------|-------------|--------|
| Pap >3 years (age 21-65) | ⚠️ CARE GAP | Schedule Pap smear |
| Pap >5 years (age 30-65 with HPV co-test) | ⚠️ CARE GAP | Schedule Pap + HPV |
| Mammogram >2 years (age 40-74) | ⚠️ CARE GAP | Schedule mammogram |
| No bone density (age 65+) | ⚠️ CARE GAP | Order DEXA |
| HPV vaccine incomplete (age <45) | ℹ️ INFO | Discuss vaccination |

**Database Schema:**

```sql
-- Table: intake_screening_history
CREATE TABLE intake_screening_history (
  form_id UUID REFERENCES patient_intake_forms(form_id) PRIMARY KEY,
  last_pap ENUM('<1_year', '1-3_years', '>3_years', 'never', 'not_needed', 'unknown') NULL,
  last_mammogram ENUM('<1_year', '1-2_years', '>2_years', 'never', 'unknown') NULL,
  last_dexa ENUM('<2_years', '2-5_years', '>5_years', 'never', 'unknown') NULL,
  hpv_vaccine_status ENUM('complete', 'partial', 'no', 'unknown') NULL,
  care_gaps_identified VARCHAR(100)[] NULL, -- Auto-calculated
  created_at TIMESTAMP DEFAULT NOW()
);
```

---

# COMPLETE OBGYN LIBRARY SUMMARY

---

## Condition Code Reference

| Code | Condition | Priority | Smart Expansion | Score Impact |
|------|-----------|----------|-----------------|--------------|
| **MENSTRUAL** |
| MENS-001 | Current Menstrual Status | 1 | Yes | Variable |
| **OBSTETRIC** |
| OB-001 | Pregnancy History | 1 | Yes | - |
| OB-GDM | Gestational Diabetes History | 1 | Yes | -8 Metabolic-Risk |
| OB-PREEC | Preeclampsia History | 1 | Yes | -10 to -15 Cardio-Risk |
| OB-PREM | Preterm Delivery History | 2 | No | -6 Cardio-Risk |
| OB-PPD | Postpartum Depression History | 2 | No | -8 Neuro-Function |
| **GYNECOLOGIC CONDITIONS** |
| GYN-FIBROID | Uterine Fibroids | 1 | Yes | -2 to -8 Repro-Function |
| GYN-ENDO | Endometriosis | 1 | Yes | -10 Repro-Function |
| GYN-PCOS | PCOS | 1 | Yes | -10 Endo-Function |
| GYN-OVCYST | Ovarian Cysts | 1 | No | -3 Repro-Function |
| GYN-ABNPAP | Abnormal Pap/Cervical Dysplasia | 1 | Yes | -5 Repro-Risk |
| GYN-PID | Pelvic Inflammatory Disease | 1 | No | -8 Repro-Risk |
| GYN-PELVPAIN | Chronic Pelvic Pain | 1 | Yes | -8 Neuro-Function |
| GYN-INCONT | Urinary Incontinence | 1 | Yes | -8 to -10 Repro-Function |
| GYN-PROLAPSE | Pelvic Organ Prolapse | 1 | Yes | -10 Repro-Function |
| GYN-INFERT | Infertility | 1 | No | -5 Repro-Function |
| **GYNECOLOGIC SURGERIES** |
| GYNSURG-HYST | Hysterectomy | 1 | Yes | Variable |
| GYNSURG-OOPH | Oophorectomy | 1 | Yes | Surgical menopause |
| GYNSURG-MYOM | Myomectomy | 1 | No | Links to fibroids |
| GYNSURG-CSEC | C-Section | 1 | No | - |
| GYNSURG-TUBAL | Tubal Ligation | 1 | No | - |
| GYNSURG-LEEP | LEEP/Cone Biopsy | 1 | No | Links to dysplasia |
| GYNSURG-LAP | Laparoscopy | 2 | No | - |
| **MENOPAUSE** |
| MENO-001 | Menopausal Symptoms | 1 | Yes | -6 Neuro-Function |
| MENO-HRT | Hormone Replacement Therapy | 1 | Yes | Monitoring flag |
| **SCREENING** |
| SCREEN-PAP | Pap Smear Status | 1 | No | Care gap alert |
| SCREEN-MAMMO | Mammogram Status | 1 | No | Care gap alert |
| SCREEN-DEXA | Bone Density Status | 1 | No | Care gap alert |
| SCREEN-HPV | HPV Vaccination | 1 | No | Care gap alert |

---

## Integration Points

### 1. Conditional Display Based on Sex

```javascript
// In form initialization:
if (patient.biological_sex === 'female') {
  sections.splice(3, 0, 'section-3b-obgyn'); // Insert after Medical History
  total_sections = 8;
  progress_weights = recalculate_with_obgyn();
}
```

### 2. Age-Based Question Display

```javascript
// Mammogram question only for age 40+
if (patient.age >= 40) {
  showQuestion('screen-mammogram');
}

// DEXA question only for age 65+ or postmenopausal
if (patient.age >= 65 || patient.menstrual_status.includes('menopause')) {
  showQuestion('screen-dexa');
}

// HPV vaccine question only for age ≤45
if (patient.age <= 45) {
  showQuestion('screen-hpv');
}
```

### 3. Auto-Link to Medical History Library

```javascript
// When GYN condition is checked, also add to medical_conditions if matching code exists
const gyn_to_medical_links = {
  'GYN-PCOS': 'REPRO-001', // PCOS in reproductive system
  'GYN-ENDO': 'REPRO-002', // Endometriosis
  'OB-GDM': 'METAB-002',   // May lead to Type 2 diabetes
};
```

### 4. Dashboard Score Integration

All OBGYN conditions feed into the 24-cell scoring matrix:

- **Reproductive-Function:** Fibroids, endometriosis, infertility, prolapse
- **Reproductive-Structure:** Hysterectomy, oophorectomy
- **Reproductive-Risk:** Cervical dysplasia, PID, cancer screening gaps
- **Cardiovascular-Risk:** Preeclampsia history, early menopause
- **Metabolic-Risk:** Gestational diabetes, PCOS with insulin resistance
- **Musculoskeletal-Risk:** Early surgical menopause (bone loss)
- **Neurological-Function:** PPD, menopausal cognitive symptoms

---

## Vietnamese Translation Keys

```json
{
  "obgyn_section_title": "LỊch sử sản phụ khoa",
  "menstrual_status_question": "Tình trạng kinh nguyệt hiện tại của bạn là gì?",
  "regular_periods": "Tôi vẫn có kinh đều",
  "irregular_periods": "Tôi vẫn có kinh nhưng không đều",
  "perimenopause": "Tôi đang trong giai đoạn tiền mãn kinh",
  "postmenopausal": "Tôi đã mãn kinh",
  "surgical_menopause": "Tôi đã phẫu thuật khiến kinh nguyệt dừng",
  "pregnant": "Tôi đang mang thai",
  "breastfeeding": "Tôi đang cho con bú",
  "pregnancy_history": "Bạn đã từng mang thai chưa?",
  "fibroids": "U xơ tử cung",
  "endometriosis": "Lạc nội mạc tử cung",
  "pcos": "Hội chứng buồng trứng đa nang (PCOS)",
  "hysterectomy": "Cắt bỏ tử cung",
  "last_pap_smear": "Lần xét nghiệm Pap gần nhất của bạn là khi nào?",
  "last_mammogram": "Lần chụp nhũ ảnh gần nhất của bạn là khi nào?"
}
```

---

## Document Status

**Status:** ✅ READY FOR INTEGRATION

**Next Steps:**
1. Update PATIENT_INTAKE_FORM_MOCKUP.md to include Section 3B: OBGYN History
2. Update PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md with database schemas
3. Add OBGYN section to SOURCE_DOCUMENT_REGISTRY.md
4. Create Vietnamese translation file for OBGYN section

---

**Document Created:** 2025-12-04
**Author:** Clinical Design Team
**Related Documents:**
- MEDICAL_HISTORY_TIER1_LIBRARY_v1.1_INTAKE_READY.md
- PATIENT_INTAKE_FORM_MOCKUP.md
- PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md

---

*This library provides comprehensive OBGYN history capture for female patients, enabling accurate reproductive health scoring and care gap identification in the Health Overview Dashboard.*
