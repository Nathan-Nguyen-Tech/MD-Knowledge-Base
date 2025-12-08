# CARD GENERATION SPECIFICATION

> **Purpose**: Ensure deterministic, consistent card generation across all 12 card types.
> **Principle**: Same input → Same output. Every time.

**Version**: 1.0
**Created**: December 2025
**Status**: CANONICAL - All card generation MUST follow this specification

---

## TABLE OF CONTENTS

1. [Core Principles](#1-core-principles)
2. [Architecture Overview](#2-architecture-overview)
3. [Canonical Data Sources](#3-canonical-data-sources)
4. [Seed Input Schema](#4-seed-input-schema)
5. [Deterministic Generation Rules](#5-deterministic-generation-rules)
6. [Terminology Standards](#6-terminology-standards)
7. [Phrase Libraries](#7-phrase-libraries)
8. [Type-Specific Generation Rules](#8-type-specific-generation-rules)
9. [Validation & Quality Checks](#9-validation--quality-checks)
10. [Version Control & Updates](#10-version-control--updates)

---

## 1. CORE PRINCIPLES

### 1.1 The Consistency Guarantee

**If two cards are generated with identical seed inputs, they MUST produce identical master card content.**

This means:
- Same drug + dose + route + frequency → Identical medication card
- Same test name + type → Identical diagnostic card
- Same exercise + modality + intensity → Identical movement card

### 1.2 Separation of Concerns

```
┌─────────────────────────────────────────────────────────────┐
│                    MASTER CARD (Canonical)                  │
│  - ONE per intervention                                     │
│  - Stored in smart_cards table                              │
│  - Generated deterministically from seed input              │
│  - Versioned and reviewed periodically                      │
│  - NEVER contains patient-specific data                     │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│               PATIENT INSTANCE (Personalized)               │
│  - ONE per patient per card assignment                      │
│  - Stored in patient_active_cards table                     │
│  - Contains personalized_target, custom_instructions        │
│  - Links to master card via card_id                         │
│  - Patient's adherence and measurement data                 │
└─────────────────────────────────────────────────────────────┘
```

### 1.3 Generation Flow

```
SEED INPUT (structured JSON/YAML)
        │
        ▼
┌───────────────────┐
│ VALIDATION LAYER  │ ← Reject invalid/incomplete inputs
└───────────────────┘
        │
        ▼
┌───────────────────┐
│ DATA ENRICHMENT   │ ← Pull from canonical sources (FDA, guidelines)
└───────────────────┘
        │
        ▼
┌───────────────────┐
│ TEMPLATE ENGINE   │ ← Apply type-specific template
└───────────────────┘
        │
        ▼
┌───────────────────┐
│ PHRASE LIBRARY    │ ← Apply standardized terminology
└───────────────────┘
        │
        ▼
┌───────────────────┐
│ QUALITY CHECKS    │ ← Validate output consistency
└───────────────────┘
        │
        ▼
    MASTER CARD
```

---

## 2. ARCHITECTURE OVERVIEW

### 2.1 Components

| Component | Purpose | Location |
|-----------|---------|----------|
| **Seed Input Schema** | Defines required/optional fields per card type | This document, Section 4 |
| **Canonical Data Sources** | Authoritative sources for clinical data | This document, Section 3 |
| **Template Engine** | Applies structured template to enriched data | AI_CARD_GENERATION_TEMPLATES.md |
| **Phrase Library** | Standardized terminology and phrasing | This document, Section 7 |
| **Validation Rules** | Ensures output consistency | This document, Section 9 |

### 2.2 What Makes Generation Deterministic

1. **Structured Input**: No free-text interpretation; all inputs are enumerated values or constrained strings
2. **Canonical Sources**: Clinical data pulled from versioned, authoritative sources
3. **Template Rules**: No creative variation; templates specify exact structure
4. **Phrase Library**: Pre-approved phrases for common concepts
5. **Validation**: Output checked against expected patterns

---

## 3. CANONICAL DATA SOURCES

### 3.1 Source Registry

Every piece of clinical information MUST come from a canonical source.

| Data Type | Canonical Source | Update Frequency | Version Reference |
|-----------|------------------|------------------|-------------------|
| **Drug Information** | FDA Label (DailyMed) | Real-time lookup | NDC + Label version |
| **Drug Interactions** | Lexicomp / Micromedex | Quarterly sync | Database version date |
| **Dosing Guidelines** | FDA Label + Clinical Guidelines | Per guideline update | Guideline citation |
| **Side Effects** | FDA Label (Adverse Reactions) | Real-time lookup | Label section 6 |
| **Contraindications** | FDA Label (Contraindications) | Real-time lookup | Label section 4 |
| **Lab Reference Ranges** | Laboratory-specific + AACC | Annual review | Lab name + date |
| **CPT Codes** | AMA CPT Codebook | Annual (January) | CPT year edition |
| **ICD-10 Codes** | CMS ICD-10-CM | Annual (October) | Fiscal year |
| **Clinical Guidelines** | Specific society (ACC/AHA, ADA, etc.) | Per publication | Guideline + year |
| **Evidence Grades** | Source guideline | Per publication | Guideline + year |
| **Reading Level** | Flesch-Kincaid calculation | Per card generation | Calculated |

### 3.2 Source Citation Format

Every card MUST include source citations in the following format:

```
Evidence:
- Source: [SOCIETY] [GUIDELINE NAME] [YEAR]
- Grade: [A/B/C] per [GRADING SYSTEM]
- Key Finding: [ONE SENTENCE SUMMARY]
- Last Verified: [DATE]
```

**Example:**
```
Evidence:
- Source: ACC/AHA Hypertension Guidelines 2017 (Updated 2023)
- Grade: A per ACC/AHA Evidence Grading
- Key Finding: ACE inhibitors reduce cardiovascular events by 20-25%
- Last Verified: 2025-12-01
```

### 3.3 Data Freshness Requirements

| Data Type | Maximum Age | Action if Stale |
|-----------|-------------|-----------------|
| Drug safety (Black Box) | 30 days | Block generation, flag for review |
| Drug interactions | 90 days | Warning flag, allow generation |
| Clinical guidelines | Until superseded | Use current, note version |
| Reference ranges | 1 year | Allow, note verification date |
| CPT/ICD codes | Until annual update | Use current fiscal year |

---

## 4. SEED INPUT SCHEMA

### 4.1 Universal Fields (All Card Types)

```yaml
# REQUIRED FOR ALL CARDS
card_type: enum  # One of 12 Tier 2 types
tier_path:
  tier_1: enum   # "Medical" | "Behavioral"
  tier_3: string # Category file name
  tier_4: string # Subcategory name

# OPTIONAL FOR ALL CARDS
tags: array[string]
notes: string
```

### 4.2 Type-Specific Seed Schemas

#### TYPE 1: MEDICATIONS

```yaml
medication:
  # REQUIRED
  generic_name: string          # Must match FDA label
  dose_value: number            # Numeric dose
  dose_unit: enum               # mg | mcg | g | mL | units | %
  route: enum                   # PO | IV | IM | SC | topical | inhalation | sublingual | rectal | ophthalmic | otic | nasal | transdermal
  frequency: enum               # QD | BID | TID | QID | Q4H | Q6H | Q8H | Q12H | weekly | biweekly | monthly | PRN
  indication_icd10: string      # Primary indication ICD-10 code

  # OPTIONAL (will be auto-populated if not provided)
  brand_names: array[string]
  formulation: enum             # tablet | capsule | liquid | injection | cream | ointment | patch | inhaler | drops | spray
  duration: enum                # days | weeks | months | ongoing
  duration_value: number        # If not ongoing

  # TITRATION (if applicable)
  titration_tiers: array
    - tier: number
      dose_value: number
      criteria_to_advance: string
```

#### TYPE 2: DIAGNOSTIC TESTING

```yaml
diagnostic_test:
  # REQUIRED
  test_name: string             # Standard test name
  test_type: enum               # laboratory | home_monitoring

  # REQUIRED FOR LABORATORY
  cpt_code: string              # If laboratory
  specimen_type: enum           # blood | urine | stool | swab | saliva | other

  # REQUIRED FOR HOME MONITORING
  vital_type: enum              # BP | HR | weight | glucose | O2sat | temperature | peak_flow
  device_category: string       # Device type

  # OPTIONAL
  loinc_code: string
  fasting_required: boolean
  fasting_hours: number
  components: array[string]     # If panel test
```

#### TYPE 3: IMAGING STUDIES

```yaml
imaging_study:
  # REQUIRED
  study_name: string            # Standard study name
  modality: enum                # xray | ct | mri | ultrasound | nuclear | mammography | fluoroscopy | pet
  body_region: string           # Anatomical region

  # OPTIONAL
  cpt_code: string
  contrast: enum                # none | oral | IV | both
  contrast_type: string         # If contrast used
```

#### TYPE 4: PROCEDURES

```yaml
procedure:
  # REQUIRED
  procedure_name: string        # Standard procedure name
  procedure_type: enum          # diagnostic | therapeutic | surgical | preventive
  setting: enum                 # office | outpatient | hospital | bedside

  # OPTIONAL
  cpt_code: string
  anesthesia: enum              # none | local | sedation | general
  duration_minutes: number
```

#### TYPE 5: DURABLE MEDICAL EQUIPMENT

```yaml
dme:
  # REQUIRED
  device_name: string           # Specific device
  device_category: enum         # respiratory | mobility | sensory | chronic_disease

  # OPTIONAL
  hcpcs_code: string
  settings: object              # Device-specific settings
  usage_frequency: string
  usage_duration: string
```

#### TYPE 6: REFERRALS

```yaml
referral:
  # REQUIRED
  specialty: string             # Specialty name
  referral_reason: string       # Clinical question
  urgency: enum                 # routine | urgent | emergent

  # OPTIONAL
  referral_type: enum           # one_time | series | ongoing
  expected_visits: number
```

#### TYPE 7: NUTRITION

```yaml
nutrition:
  # REQUIRED
  intervention_name: string     # Diet/intervention name
  intervention_type: enum       # pattern | food_focus | behavior
  target_condition_icd10: string # Primary condition addressed

  # OPTIONAL
  calorie_target: number
  macro_targets: object
  foods_to_include: array[string]
  foods_to_limit: array[string]
```

#### TYPE 8: MOVEMENT/EXERCISE

```yaml
movement:
  # REQUIRED
  exercise_name: string         # Exercise name
  modality: enum                # aerobic | strength | flexibility | balance
  intensity: enum               # light | moderate | vigorous

  # OPTIONAL
  equipment: enum               # none | minimal | gym
  duration_minutes: number
  frequency_per_week: number
  progression_tiers: array
```

#### TYPE 9: RECOVERY

```yaml
recovery:
  # REQUIRED
  intervention_name: string     # Intervention name
  recovery_type: enum           # sleep | stress | breathing_relaxation

  # OPTIONAL
  duration_minutes: number
  frequency: string
  technique_steps: array[string]
```

#### TYPE 10: MIND-BODY PRACTICES

```yaml
mind_body:
  # REQUIRED
  practice_name: string         # Practice name
  practice_category: enum       # meditation | yoga | tai_chi | qigong | other
  level: enum                   # beginner | intermediate | advanced

  # OPTIONAL
  duration_minutes: number
  frequency_per_week: number
  guidance_type: enum           # app | audio | video | in_person | self_directed
```

#### TYPE 11: ENVIRONMENTAL & SOCIAL HEALTH

```yaml
environmental_social:
  # REQUIRED
  intervention_name: string     # Intervention name
  intervention_area: enum       # social | environmental | occupational | substance | financial

  # OPTIONAL
  target_outcome: string
  resources: array[string]
  first_step: string
```

#### TYPE 12: MICRO-LEARNING

```yaml
micro_learning:
  # REQUIRED
  topic_name: string            # Topic title
  related_condition_icd10: string
  unlocks_card_id: string       # Next card in sequence

  # REQUIRED CONTENT
  learning_objective: string
  key_points: array[string]     # 3-5 points

  # OPTIONAL
  misconceptions: array
    - myth: string
      truth: string
  knowledge_check: array
    - question: string
      answer: string
```

---

## 5. DETERMINISTIC GENERATION RULES

### 5.1 Field Derivation Rules

For each card type, certain fields are DERIVED (not provided) based on canonical sources.

#### MEDICATION DERIVATION RULES

| Derived Field | Source | Derivation Logic |
|--------------|--------|------------------|
| `drug_class` | FDA Label Section 11 | Extract from "Clinical Pharmacology" |
| `mechanism_of_action` | FDA Label Section 12.1 | Summarize in ≤50 words, 8th grade level |
| `brand_names` | FDA Label | All listed brand names |
| `common_side_effects` | FDA Label Section 6 | Top 5 by frequency (≥5% incidence) |
| `serious_side_effects` | FDA Label Section 5 | All boxed warnings + serious warnings |
| `contraindications` | FDA Label Section 4 | All absolute contraindications |
| `drug_interactions` | FDA Label Section 7 | Major interactions only (adjust/avoid) |
| `pregnancy_category` | FDA Label Section 8.1 | Category + brief guidance |
| `renal_adjustment` | FDA Label Section 8.6 | If CrCl thresholds specified |
| `hepatic_adjustment` | FDA Label Section 8.7 | If Child-Pugh guidance specified |
| `monitoring_requirements` | FDA Label + Guidelines | Labs and frequency |
| `evidence_grade` | Clinical Guideline | Grade + source citation |
| `cost_tier` | Formulary lookup | $ / $$ / $$$ / $$$$ |
| `generic_available` | FDA Orange Book | Yes/No + date if applicable |

#### DERIVATION EXAMPLE: Metformin 500mg BID

```yaml
# SEED INPUT
medication:
  generic_name: "metformin"
  dose_value: 500
  dose_unit: "mg"
  route: "PO"
  frequency: "BID"
  indication_icd10: "E11.9"  # Type 2 diabetes

# DERIVED FROM FDA LABEL (DailyMed NDC lookup)
derived:
  drug_class: "Biguanide"
  mechanism_of_action: "Decreases liver glucose production and improves insulin sensitivity in muscle tissue."
  brand_names: ["Glucophage", "Glumetza", "Fortamet", "Riomet"]
  formulation: "tablet"

  common_side_effects:
    - name: "Diarrhea"
      frequency: "53%"
    - name: "Nausea/Vomiting"
      frequency: "26%"
    - name: "Flatulence"
      frequency: "12%"
    - name: "Asthenia"
      frequency: "9%"
    - name: "Headache"
      frequency: "6%"

  serious_side_effects:
    - name: "Lactic Acidosis"
      type: "boxed_warning"
      description: "Rare but serious; risk increases with renal impairment, dehydration, excess alcohol"

  contraindications:
    absolute:
      - "Severe renal impairment (eGFR <30 mL/min/1.73m²)"
      - "Metabolic acidosis, including diabetic ketoacidosis"
      - "History of lactic acidosis on metformin"
    relative:
      - "eGFR 30-45 mL/min/1.73m² (dose reduction)"
      - "Hepatic impairment"
      - "Excessive alcohol use"

  drug_interactions:
    major:
      - drug: "Iodinated contrast"
        action: "Hold metformin before and 48h after"
      - drug: "Carbonic anhydrase inhibitors"
        action: "Increased lactic acidosis risk"

  renal_adjustment:
    - eGFR_min: 45
      eGFR_max: 59
      action: "Monitor renal function more frequently"
    - eGFR_min: 30
      eGFR_max: 44
      action: "Reduce dose; max 1000mg/day; do not initiate"
    - eGFR_min: 0
      eGFR_max: 29
      action: "Contraindicated"

  monitoring_requirements:
    - test: "Renal function (eGFR)"
      frequency: "Baseline, then annually; more frequent if eGFR <60"
    - test: "Vitamin B12"
      frequency: "Consider periodic monitoring with long-term use"
    - test: "HbA1c"
      frequency: "Every 3 months until stable, then every 6 months"

  evidence_grade:
    grade: "A"
    source: "ADA Standards of Care in Diabetes 2024"
    finding: "First-line pharmacotherapy for type 2 diabetes"

  cost_tier: "$"
  generic_available: true
```

### 5.2 Content Generation Rules

#### PATIENT-FACING CONTENT RULES

| Rule ID | Rule | Validation |
|---------|------|------------|
| PF-01 | Reading level: 6th-8th grade (Flesch-Kincaid) | Automated check |
| PF-02 | No medical jargon without plain-language definition | Term list check |
| PF-03 | No abbreviations in patient text (write out fully) | Regex check |
| PF-04 | Active voice only | Grammar check |
| PF-05 | Sentences ≤25 words | Automated check |
| PF-06 | Use "you/your" not "patient/the patient" | Regex check |
| PF-07 | Positive framing when possible | Manual review |
| PF-08 | Numbers: spell out 1-10, numerals for 11+ | Regex check |

#### CLINICAL CONTENT RULES

| Rule ID | Rule | Validation |
|---------|------|------------|
| CL-01 | Use standard medical terminology | Term list check |
| CL-02 | Include units for all measurements | Regex check |
| CL-03 | Cite source for all clinical statements | Citation check |
| CL-04 | Evidence grade required for recommendations | Field presence check |
| CL-05 | ICD-10 codes must be valid current codes | Code validation |
| CL-06 | CPT codes must be valid current codes | Code validation |
| CL-07 | Drug names use generic (brand in parentheses) | Format check |

### 5.3 Section-by-Section Generation

Each template section has specific generation rules:

#### WHAT YOU'RE DOING (Patient-Facing)

**Formula:**
```
[ACTION_VERB] [INTERVENTION] [FREQUENCY_PLAIN] to [SIMPLE_BENEFIT].
```

**Action Verb Library (by card type):**
| Card Type | Action Verbs |
|-----------|-------------|
| Medications | Take, Use, Apply, Inhale, Inject |
| Diagnostic Testing (Lab) | Get, Have |
| Diagnostic Testing (Home) | Check, Monitor, Measure, Track |
| Imaging | Get, Have |
| Procedures | Have, Get, Undergo |
| DME | Use, Wear |
| Referrals | See, Visit, Meet with |
| Nutrition | Eat, Choose, Limit, Add, Try |
| Movement | Do, Walk, Swim, Bike, Stretch, Lift |
| Recovery | Practice, Try, Do |
| Mind-Body | Practice, Do, Try |
| Environmental/Social | Connect with, Join, Reduce, Quit, Call |
| Micro-Learning | Learn about, Understand |

**Frequency Plain English Conversion:**
| Medical Frequency | Plain English |
|-------------------|---------------|
| QD | once a day / every day / daily |
| BID | twice a day / two times a day |
| TID | three times a day |
| QID | four times a day |
| Q4H | every four hours |
| Q6H | every six hours |
| Q8H | every eight hours |
| Q12H | every twelve hours |
| PRN | as needed / when needed |
| Weekly | once a week |
| Biweekly | every two weeks |
| Monthly | once a month |

**Simple Benefit Conversion:**
| Clinical Goal | Simple Benefit |
|--------------|----------------|
| Reduce blood pressure | lower your blood pressure |
| Glycemic control | control your blood sugar |
| Lipid management | lower your cholesterol |
| Pain management | reduce your pain |
| Infection treatment | fight the infection |
| Mood stabilization | help balance your mood |
| Sleep improvement | help you sleep better |
| Weight management | help you reach a healthy weight |

#### WHY THIS MATTERS TO YOU (Patient-Facing)

**Formula:**
```
[PATIENT_GOAL_PLACEHOLDER] — [MECHANISM_SIMPLE]. [BENEFIT_STATEMENT].
```

**Mechanism Simplification Rules:**
- Maximum 20 words
- No medical terms without immediate definition
- Focus on outcome, not biology

**Example Transformations:**
| Technical Mechanism | Simple Mechanism |
|--------------------|------------------|
| "Inhibits angiotensin-converting enzyme, reducing angiotensin II formation" | "Helps blood vessels relax and widen" |
| "Enhances insulin sensitivity in peripheral tissues" | "Helps your body use insulin better" |
| "Reduces hepatic glucose production" | "Reduces sugar made by your liver" |

#### SAFETY SECTION

**Color-Coded Severity (MANDATORY):**

| Color | Meaning | Criteria | Patient Action |
|-------|---------|----------|----------------|
| 🟡 YELLOW | Common, usually manageable | ≥5% incidence, non-serious | Monitor, usually continue |
| 🟠 ORANGE | Concerning, contact care team | <5% but clinically significant | Stop, call within 24h |
| 🔴 RED | Emergency | Life-threatening | Call 911 immediately |

**Safety Statement Templates:**

```
🟡 YELLOW - Common Side Effects (usually manageable):
- [SIDE_EFFECT_1] ([PERCENTAGE]%) - [WHAT_TO_DO]
- [SIDE_EFFECT_2] ([PERCENTAGE]%) - [WHAT_TO_DO]

🟠 ORANGE - Stop and Contact Your Care Team If:
- [SYSTEM]: [WARNING_SIGN]
- [SYSTEM]: [WARNING_SIGN]

🔴 RED - Call 911 Immediately:
- [EMERGENCY_SYMPTOM_1]
- [EMERGENCY_SYMPTOM_2]
```

---

## 6. TERMINOLOGY STANDARDS

### 6.1 Forbidden Terms (Patient-Facing)

These terms MUST be replaced with plain-language equivalents:

| Forbidden Term | Required Replacement |
|----------------|---------------------|
| Administer | Take / Use / Apply |
| Contraindicated | Should not take / Cannot use |
| Discontinue | Stop |
| Etiology | Cause |
| Exacerbation | Flare-up / Worsening |
| Indication | Reason / Purpose |
| Initiate | Start |
| Manifestation | Symptom / Sign |
| Prognosis | Outlook |
| Prophylaxis | Prevention |
| Regimen | Plan / Schedule |
| Titrate | Adjust the dose |
| Utilize | Use |

### 6.2 Required Definitions

If these terms MUST be used, provide immediate parenthetical definition:

| Term | Required Definition |
|------|---------------------|
| ACE inhibitor | (a type of blood pressure medication) |
| Angioedema | (severe swelling of face, lips, tongue, or throat) |
| Arrhythmia | (irregular heartbeat) |
| Beta blocker | (a type of heart and blood pressure medication) |
| Creatinine | (a blood test that measures kidney function) |
| eGFR | (a measure of how well your kidneys are working) |
| HbA1c | (a blood test showing your average blood sugar over 3 months) |
| Hypoglycemia | (low blood sugar) |
| Hyperkalemia | (high potassium levels) |
| Statin | (a type of cholesterol medication) |

### 6.3 Number Formatting

| Context | Format | Example |
|---------|--------|---------|
| Patient-facing, 1-10 | Spelled out | "Take one pill" |
| Patient-facing, 11+ | Numeral | "Take 12 pills" |
| Clinical, all numbers | Numeral | "10 mg" |
| Percentages | Numeral + % | "5%" |
| Ranges | Numeral-Numeral | "5-10 mg" |
| Time | Numeral + unit | "30 minutes" |
| Dates | Month Day, Year | "January 15, 2025" |

---

## 7. PHRASE LIBRARIES

### 7.1 Standard Phrases by Section

Pre-approved phrases that MUST be used (no creative variation):

#### TIMING PHRASES

| Concept | Standard Phrase |
|---------|-----------------|
| Take in morning | "Take in the morning" |
| Take at bedtime | "Take at bedtime" |
| Take with food | "Take with food" |
| Take on empty stomach | "Take on an empty stomach (1 hour before or 2 hours after eating)" |
| Take with full glass of water | "Take with a full glass of water" |
| Take at same time daily | "Take at the same time each day" |
| Can take with or without food | "You can take this with or without food" |

#### MISSED DOSE PHRASES

| Situation | Standard Phrase |
|-----------|-----------------|
| QD medication, remembered same day | "If you miss a dose, take it as soon as you remember. If it's almost time for your next dose, skip the missed dose. Do not take two doses at once." |
| BID medication | "If you miss a dose, take it as soon as you remember unless it's within [X] hours of your next dose. Never double up." |
| Critical timing medication | "This medication must be taken at specific times. If you miss a dose, call your care team for instructions." |

#### STORAGE PHRASES

| Storage Type | Standard Phrase |
|--------------|-----------------|
| Room temperature | "Store at room temperature (68-77°F / 20-25°C), away from moisture and heat." |
| Refrigerated | "Store in the refrigerator (36-46°F / 2-8°C). Do not freeze." |
| Light-sensitive | "Store in original container. Keep away from light." |
| Controlled substance | "Store in a secure location away from children and others." |

#### BENEFIT TIMELINE PHRASES

| Timeline | Standard Phrase |
|----------|-----------------|
| Days | "You may notice [BENEFIT] within a few days." |
| 1-2 weeks | "You may notice [BENEFIT] in one to two weeks." |
| 4-6 weeks | "It may take four to six weeks to see the full benefit." |
| 3 months | "Full effects may take up to three months." |
| Ongoing | "This medication works best when taken consistently over time." |

#### EMERGENCY PHRASES

| Situation | Standard Phrase |
|-----------|-----------------|
| Call 911 | "Call 911 immediately or go to the nearest emergency room." |
| Call care team urgently | "Stop taking this medication and call your care team right away." |
| Contact within 24h | "Contact your care team within 24 hours." |
| Mention at next visit | "Mention this at your next appointment." |

### 7.2 Section Headers (LOCKED)

These section headers MUST be used exactly as written:

**Patient-Facing:**
- WHAT YOU'RE DOING
- WHY THIS MATTERS TO YOU
- HOW TO DO IT
- WHEN TO DO IT
- WHAT TO WATCH FOR

**Clinical View:**
- WHAT
- WHO
- WHEN
- WHERE
- WHY
- HOW
- MEASURE
- TARGET
- SAFETY
- FOLLOW-UP
- NOTES

---

## 8. TYPE-SPECIFIC GENERATION RULES

### 8.1 MEDICATIONS (Type 1)

#### Required Derivations
- Drug class from FDA label
- All black box warnings (verbatim, then simplified)
- Top 5 side effects with percentages
- Major drug interactions
- Renal/hepatic adjustments if applicable
- Pregnancy/lactation guidance
- Generic availability and cost tier

#### Titration Tier Rules
If medication has titration:
- Define starting dose (Tier 1)
- Define target dose (Tier 2-4)
- Define maximum dose
- Define criteria to advance (time-based + tolerance-based)
- Define criteria to hold/reduce

#### Monitoring Schedule Template
```
Monitoring:
- Baseline: [TESTS_BEFORE_STARTING]
- Week 2-4: [EARLY_SAFETY_CHECKS]
- Month 3: [EFFICACY_CHECK]
- Ongoing: [MAINTENANCE_SCHEDULE]
```

### 8.2 DIAGNOSTIC TESTING (Type 2)

#### Laboratory Tests
- CPT and LOINC codes required
- Reference ranges with units
- Critical values (high and low)
- Preparation requirements
- Turnaround time

#### Home Monitoring
- Device specifications (validated devices)
- Proper technique (step-by-step)
- Recording method
- Alert thresholds (when to call)
- Calibration requirements

### 8.3 IMAGING STUDIES (Type 3)

#### Required Fields
- Radiation dose (mSv) for ionizing modalities
- Contrast requirements and screening
- Pregnancy screening protocol (if radiation)
- Claustrophobia options (MRI)
- Metal screening (MRI)
- ACR Appropriateness criteria reference

### 8.4 PROCEDURES (Type 4)

#### Pre-Procedure Checklist
- Labs required (with timing)
- Medications to hold (with timing)
- Fasting requirements
- Transportation arrangements
- Consent requirements

#### Post-Procedure Instructions
- Activity restrictions (type and duration)
- Diet progression
- Wound care (if applicable)
- Pain management expectations
- Warning signs

### 8.5 DME (Type 5)

#### Required Elements
- HCPCS code
- Prescription details (settings, parameters)
- Training requirements
- Compliance tracking method
- Troubleshooting guide
- Supply reorder schedule
- Insurance/prior auth requirements

### 8.6 REFERRALS (Type 6)

#### Required Elements
- Specific clinical question
- Urgency timeline
- Records to send
- What patient should bring
- Questions to prepare
- Expected outcome

### 8.7 NUTRITION (Type 7)

#### Required Elements
- Specific dietary changes (not vague)
- Foods to include (with portions)
- Foods to limit (with alternatives)
- Sample meals
- Cultural adaptations
- Budget-friendly options
- Evidence with effect size

### 8.8 MOVEMENT/EXERCISE (Type 8)

#### Required Elements
- RPE or HR zone targets
- Warm-up routine
- Cool-down routine
- Progression tiers with advancement criteria
- Modifications (easier, harder, joint-friendly)
- Safety precautions by condition

### 8.9 RECOVERY (Type 9)

#### Required Elements
- Step-by-step technique
- Timing (when to practice)
- Duration per session
- Environment setup
- Integration into routine
- Signs of sleep disorder/anxiety (escalation criteria)

### 8.10 MIND-BODY (Type 10)

#### Required Elements
- Complete technique instructions
- Progression path (beginner → advanced)
- Guidance resources (apps, videos)
- Physical requirements
- Trauma-informed considerations
- Crisis resources (988, etc.)

### 8.11 ENVIRONMENTAL/SOCIAL (Type 11)

#### Required Elements
- Specific first step
- Resources with contact info
- Support network engagement
- Barrier plan
- Crisis resources
- SDOH screening integration

### 8.12 MICRO-LEARNING (Type 12)

#### Required Elements
- Single learning objective
- 5 key points maximum
- 5-minute maximum length
- 6th-8th grade reading level
- Common misconceptions addressed
- Next action card specified

---

## 9. VALIDATION & QUALITY CHECKS

### 9.1 Automated Validation Rules

| Check ID | Check Name | Applies To | Validation Logic | Failure Action |
|----------|------------|------------|------------------|----------------|
| VAL-01 | Reading Level | Patient-facing text | Flesch-Kincaid ≤ 8th grade | Block generation |
| VAL-02 | Forbidden Terms | Patient-facing text | No terms from forbidden list | Block generation |
| VAL-03 | Sentence Length | Patient-facing text | All sentences ≤ 25 words | Warning |
| VAL-04 | Abbreviation Check | Patient-facing text | No unexpanded abbreviations | Block generation |
| VAL-05 | Evidence Citation | All clinical claims | Source + grade present | Block generation |
| VAL-06 | ICD-10 Validity | All ICD codes | Valid in current CMS codeset | Block generation |
| VAL-07 | CPT Validity | All CPT codes | Valid in current AMA codeset | Block generation |
| VAL-08 | Drug Name Match | Medications | Generic name matches FDA | Block generation |
| VAL-09 | Safety Colors | Safety section | All 3 tiers present | Warning |
| VAL-10 | Required Sections | All cards | All template sections present | Block generation |

### 9.2 Consistency Checks

| Check ID | Check Name | Logic |
|----------|------------|-------|
| CON-01 | Duplicate Detection | Hash of seed input; reject if card already exists |
| CON-02 | Cross-Reference | Links to other cards must reference valid card IDs |
| CON-03 | Dose Consistency | Dose in WHAT section = dose in clinical WHAT section |
| CON-04 | Frequency Consistency | Frequency appears same in all sections |
| CON-05 | Evidence Consistency | Grade in WHY = grade in NOTES |

### 9.3 Determinism Verification

**Test Protocol:**
1. Generate card with specific seed input
2. Store output hash
3. Re-generate card with identical seed input
4. Compare output hash
5. MUST match exactly (excluding timestamps)

```
DETERMINISM TEST:
  Input: seed_input_hash_A
  Output 1: card_content_hash_X
  Output 2: card_content_hash_X
  Result: PASS (hashes match)
```

### 9.4 Human Review Requirements

Despite automation, these require human review:

| Element | Review Requirement |
|---------|-------------------|
| Black box warnings | Clinician must verify accuracy |
| Drug interactions | Pharmacist review recommended |
| Evidence grades | Must match source document |
| Cultural adaptations | Cultural competency review |
| New drug entries | Full clinical review before publish |

---

## 10. VERSION CONTROL & UPDATES

### 10.1 Card Versioning

```
Card Version Format: [MAJOR].[MINOR]

MAJOR increment when:
- Dose change
- Route change
- Indication change
- Safety information change (new warning)
- Evidence grade change

MINOR increment when:
- Wording clarification
- Additional tips added
- Reference update (same guidance)
- Formatting change
```

### 10.2 Source Update Protocol

When canonical sources update:

1. **Identify affected cards** - Query all cards referencing updated source
2. **Generate diff** - Compare old vs new source data
3. **Classify change** - Safety-critical vs informational
4. **Queue for regeneration** - Safety-critical = immediate; informational = batch
5. **Regenerate cards** - Using updated canonical data
6. **Validate** - Run all automated checks
7. **Review** - Human review for safety-critical changes
8. **Publish** - Update card version, archive old version

### 10.3 Audit Trail

Every card generation MUST log:

```yaml
generation_log:
  card_id: string
  version: string
  generated_at: timestamp
  generated_by: string          # System or user ID
  seed_input_hash: string       # SHA-256 of seed input
  output_hash: string           # SHA-256 of generated content
  canonical_sources:
    - source: string
      version: string
      accessed_at: timestamp
  validation_results:
    - check_id: string
      result: pass | fail | warning
  human_review:
    reviewed_by: string
    reviewed_at: timestamp
    approved: boolean
```

---

## APPENDIX A: QUICK REFERENCE CHECKLISTS

### Pre-Generation Checklist

- [ ] Seed input complete (all required fields)
- [ ] Seed input validated (enum values valid)
- [ ] Canonical sources accessible
- [ ] No duplicate card exists

### Post-Generation Checklist

- [ ] All validation checks pass
- [ ] Reading level verified (≤ 8th grade)
- [ ] Evidence citations complete
- [ ] Safety section has all three color tiers
- [ ] Determinism test passed (if applicable)
- [ ] Human review completed (if required)

---

## APPENDIX B: CHANGE LOG

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-12-05 | CMO Team | Initial specification |

---

**END OF SPECIFICATION**

*This document is the canonical source for all card generation. Any deviation requires documented approval and specification update.*
