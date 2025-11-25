# SMART Card Library - Complete Tier Structure Definition

## Executive Summary

The SMART Card Library uses a **5-tier hierarchical structure** to organize the card library. This document provides the definitive structure for organizing, categorizing, and locating cards within the system.

**Key Update**: Tier 2 finalized at **12 card types** (6 Medical + 6 Behavioral) based on clinical pattern recognition and intervention modality analysis.

---

## Tier Structure Overview

```
Tier 1: Top-Level Categories (2) - MEDICAL vs BEHAVIORAL
  │
  ├─ Tier 2: Card Types (12) - Specific intervention modalities
  │    │
  │    ├─ Tier 3: Subcategories - Clinical or functional groupings
  │    │    │
  │    │    ├─ Tier 4: Specific Categories - Detailed classifications
  │    │    │    │
  │    │    │    └─ Tier 5: Individual Cards - Atomic actions
```

**Note**: Card volume estimates removed until library development is complete. Structure takes priority over premature quantification.

---

## TIER 1: Top-Level Categories (2 Categories)

### Purpose
Fundamental organizational split based on **who initiates the intervention** and **what resources are required**.

### Categories

#### 1. MEDICAL CARDS
- **Definition**: Interventions requiring prescription, medical supervision, or healthcare facility access
- **Who Initiates**: Clinician/healthcare provider
- **Requires Prescription/Order**: Yes (typically)
- **Examples**: Medications, lab tests, imaging, procedures, DME, referrals
- **Tier 2 Subtypes**: 6

#### 2. BEHAVIORAL CARDS
- **Definition**: Lifestyle modifications and self-management actions patients can initiate
- **Who Initiates**: Patient (with clinical guidance)
- **Requires Prescription/Order**: No
- **Examples**: Nutrition, exercise, sleep hygiene, environmental modifications, foundational learning
- **Tier 2 Subtypes**: 6

### Why Only 2 Tiers?
**Historical Note**: Earlier versions included "Educational Cards" as a third Tier 1 category. This was **eliminated** because:
- Education is embedded in every card (WHY/HOW sections)
- Micro-learning cards now exist within Behavioral tier as foundational learning
- Education is not a standalone action ("do education" doesn't make clinical sense)

---

## TIER 2: Card Types (12 Types) - FINAL STRUCTURE

### Purpose
Specific intervention modalities that determine the card's **template structure** and **type-specific data fields**.

### Clinical Decision Criteria for Tier 2 Status

A card type qualifies for Tier 2 when it meets **3 or more** of these criteria:
1. **Distinct Template Structure** - Requires fundamentally different data fields (>50% different)
2. **Unique Delivery Mechanism** - Who performs it, where, how differs meaningfully
3. **Different Workflow** - Patient/clinician interaction pattern is structurally different
4. **Separate Tracking Metrics** - Adherence and outcomes measured differently
5. **Independent Reimbursement Model** - Billing, insurance, cost structure differs

---

### Medical Card Types (6 Types)

| # | Card Type | Icon | Rx? | Duration | Template Distinctions | Key Tier 3 Subcategories |
|---|-----------|------|-----|----------|----------------------|--------------------------|
| **1** | **Medications** | 💊 | Yes | Ongoing | Drug dosing, interactions, monitoring, safety by system | Prescription Meds + **OTC/Supplements** |
| **2** | **Diagnostic Testing** | 🔬 | Yes | Periodic | Specimen type, prep, reference ranges, trend analysis | Laboratory Tests + **Home Monitoring** |
| **3** | **Imaging Studies** | 🏥 | Yes | Periodic | Modality, contrast, radiation, body region | X-ray, CT, MRI, ultrasound, nuclear |
| **4** | **Procedures** | 🏥 | Yes | Varies | Invasiveness, sedation, recovery, complications | Diagnostic, Therapeutic, **Surgical**, Preventive |
| **5** | **Durable Medical Equipment** | 🩺 | Yes | Ongoing | Equipment specs, training, maintenance, compliance data | Respiratory, Mobility, Sensory, Chronic Disease Mgmt |
| **6** | **Referrals** | 👨‍⚕️ | Yes | Varies | Specialty, urgency, consult vs ongoing, insurance auth | Medical Specialists + **Behavioral Health** + Allied Health |

---

### Behavioral Card Types (6 Types)

| # | Card Type | Icon | Rx? | Duration | Template Distinctions | Key Tier 3 Subcategories |
|---|-----------|------|-----|----------|----------------------|--------------------------|
| **7** | **Nutrition** | 🥗 | No | Ongoing | Dietary pattern, food lists, portions, meal timing | Diet Patterns, Food Focus, Eating Behaviors |
| **8** | **Movement/Exercise** | 🏃 | No | Ongoing | Exercise type, intensity (RPE/HR), duration, progression | Aerobic, Strength, Flexibility, Balance |
| **9** | **Recovery** | 😴 | No | Ongoing | Sleep metrics, stress scales, breathing techniques | Sleep Hygiene, Stress Management, Breathing |
| **10** | **Mind-Body Practices** | 🧘 | No | Ongoing | Practice type, session length, mindfulness elements | Meditation, Yoga, Tai Chi, Mindfulness |
| **11** | **Environmental & Social Health** | 🌍 | No | Ongoing | Environmental exposures, social connections, community resources | Social, Environmental, Occupational, **Substance Use** |
| **12** | **Micro-Learning** | 📚 | No | 5 min | Learning objectives, knowledge checks, unlocking logic | Cardiovascular, Metabolic, Nutrition, Exercise Concepts |

---

## KEY TIER 3 CONSOLIDATIONS (New Structure)

### 1. OTC/Supplements → Tier 3 Under Medications
**Rationale**: Template is 85% identical to prescription medications. Only differences:
- No prescription required
- Different insurance coverage (usually patient pays)
- Quality/purity concerns (supplement-specific)
- Different evidence grades (often Grade B/C)

**Structure**:
```
Tier 2: Medications
  Tier 3: Prescription Medications
  Tier 3: Over-the-Counter & Supplements (NEW)
```

### 2. Home Monitoring → Tier 3 Under Diagnostic Testing
**Rationale**: Both are assessment interventions producing quantitative data. Key difference is location (home vs facility), not modality.

**Structure**:
```
Tier 2: Diagnostic Testing
  Tier 3: Laboratory Tests (facility-based)
  Tier 3: Home Monitoring (patient-directed) (NEW)
```

### 3. Surgical Procedures → Tier 3 Under Procedures
**Rationale**: Surgery is on a continuum with other procedures. No distinct template or workflow that warrants separation.

**Structure**:
```
Tier 2: Procedures
  Tier 3: Diagnostic Procedures
  Tier 3: Minor Therapeutic Procedures
  Tier 3: Surgical Procedures (NEW)
  Tier 3: Preventive Procedures
```

### 4. Behavioral Health Services → Tier 3 Under Referrals
**Rationale**: A referral is sending a patient to another provider. Whether for one-time consult or ongoing therapy is a characteristic, not a different intervention type.

**Structure**:
```
Tier 2: Referrals
  Tier 3: Medical Specialist Consultations
  Tier 3: Behavioral Health Providers (NEW)
  Tier 3: Rehabilitation Services
  Tier 3: Allied Health Professionals
```

### 5. Substance Use & Harm Reduction → Tier 3 Under Environmental/Social Health
**Rationale**: Substance use is fundamentally a social determinant of health. Social factors, environmental triggers, and community resources dominate intervention approach.

**Structure**:
```
Tier 2: Environmental & Social Health
  Tier 3: Social Connection & Community
  Tier 3: Environmental Quality
  Tier 3: Occupational Health
  Tier 3: Substance Use & Harm Reduction (NEW)
  Tier 3: Financial Health & Resources
```

---

## TIER 3: Detailed Subcategory Breakdown

### MEDICAL CARDS

#### 1. Medications

**Tier 3: Prescription Medications**
- Tier 4: Cardiovascular medications
  - ACE Inhibitors, ARBs, Beta Blockers, CCBs, Diuretics
  - Antiplatelet/Anticoagulants
  - Lipid-lowering (statins, fibrates, PCSK9 inhibitors)
  - Heart failure medications
- Tier 4: Diabetes medications
  - Oral agents (metformin, sulfonylureas, DPP-4i, SGLT2i)
  - Injectable agents (GLP-1 agonists, insulin)
- Tier 4: Respiratory medications
  - Asthma (SABA, ICS, LABA, combinations)
  - COPD (LAMA, LABA/LAMA, triple therapy)
- Tier 4: GI medications
  - Acid suppression (PPIs, H2 blockers)
  - Bowel motility (laxatives, antidiarrheals)
  - IBD medications
- Tier 4: Neurological/Psychiatric medications
  - Antidepressants (SSRIs, SNRIs, TCAs, MAOIs)
  - Anxiolytics (benzodiazepines, buspirone)
  - Antipsychotics (typical, atypical)
  - Mood stabilizers
  - Anti-seizure medications
  - Migraine medications
- Tier 4: Pain medications
  - Non-opioid analgesics (NSAIDs, acetaminophen)
  - Opioid analgesics
  - Neuropathic pain medications (gabapentin, pregabalin)
- Tier 4: Antibiotics/Antimicrobials
  - Beta-lactams (penicillins, cephalosporins)
  - Macrolides, fluoroquinolones, tetracyclines
  - Antifungals, antivirals
- Tier 4: Endocrine/Other medications
  - Thyroid medications
  - Bone health (bisphosphonates, vitamin D)
  - Corticosteroids
  - Rheumatologic/immunologic
  - Allergy medications

**Tier 3: Over-the-Counter & Supplements** ← NEW
- Tier 4: Vitamins & minerals (vitamin D, calcium, B12, iron)
- Tier 4: Herbal supplements (fish oil, probiotics, turmeric)
- Tier 4: OTC analgesics (ibuprofen, naproxen, acetaminophen)
- Tier 4: OTC gastrointestinal (antacids, laxatives, anti-diarrheals)
- Tier 4: OTC allergy/cold (antihistamines, decongestants, cough)

---

#### 2. Diagnostic Testing

**Tier 3: Laboratory Tests (facility-based)**
- Tier 4: Blood tests
  - Chemistry panels (BMP, CMP)
  - Lipid panel
  - Glucose & diabetes monitoring (HbA1c, fasting glucose)
  - Thyroid function (TSH, free T4)
  - Complete blood count (CBC)
  - Cardiac biomarkers (troponin, BNP)
  - Inflammatory markers (CRP, ESR)
  - Vitamins & minerals
  - Hormone testing
- Tier 4: Urine tests
  - Urinalysis
  - Urine microalbumin
  - Urine culture
  - Drug screening
- Tier 4: Other specimen tests
  - Stool tests (FOBT, culture, C. diff)
  - Throat/nasal swabs
  - Wound cultures

**Tier 3: Home Monitoring (patient-directed)** ← NEW
- Tier 4: Cardiovascular monitoring
  - Home blood pressure monitoring
  - Pulse/heart rate tracking
  - Pulse oximetry
- Tier 4: Metabolic monitoring
  - Home glucose monitoring
  - Ketone testing
- Tier 4: Weight/fluid tracking
  - Daily weight (for CHF management)
  - Fluid intake/output logs
- Tier 4: Symptom diaries/tracking
  - Pain scales
  - Mood logs
  - Headache diaries
  - Food/symptom journals

---

#### 3. Imaging Studies

**Tier 3: X-Ray Imaging**
- Tier 4: Chest X-ray
- Tier 4: Abdominal X-ray
- Tier 4: Musculoskeletal X-rays (extremities, spine)

**Tier 3: CT Scans**
- Tier 4: Head/brain CT
- Tier 4: Chest CT
- Tier 4: Abdominal/pelvic CT
- Tier 4: CT angiography

**Tier 3: MRI Studies**
- Tier 4: Brain MRI
- Tier 4: Spine MRI
- Tier 4: Joint MRI (knee, shoulder, hip)

**Tier 3: Ultrasound**
- Tier 4: Abdominal ultrasound
- Tier 4: Pelvic ultrasound
- Tier 4: Vascular ultrasound (carotid, DVT)

**Tier 3: Specialized Cardiac & Other**
- Tier 4: Echocardiography
- Tier 4: Nuclear medicine studies
- Tier 4: Mammography

---

#### 4. Procedures

**Tier 3: Diagnostic Procedures**
- Tier 4: Endoscopy (upper GI)
- Tier 4: Colonoscopy
- Tier 4: Bronchoscopy
- Tier 4: Cardiac catheterization

**Tier 3: Minor Therapeutic Procedures**
- Tier 4: Joint injections (corticosteroid)
- Tier 4: Trigger point injections
- Tier 4: Minor wound care/debridement

**Tier 3: Surgical Procedures** ← NEW
- Tier 4: Minor surgeries (skin lesion excision, cyst removal)
- Tier 4: Intermediate surgeries (appendectomy, hernia repair)
- Tier 4: Major surgeries (joint replacement, cardiac surgery)

**Tier 3: Preventive Procedures**
- Tier 4: Vaccinations (influenza, pneumonia, COVID, shingles)
- Tier 4: Screening procedures (skin checks, oral exam)

---

#### 5. Durable Medical Equipment (DME)

**Tier 3: Respiratory Equipment**
- Tier 4: CPAP/BiPAP devices
- Tier 4: Home oxygen (concentrators, tanks)
- Tier 4: Nebulizers

**Tier 3: Mobility & Assistive Devices**
- Tier 4: Wheelchairs & power chairs
- Tier 4: Walkers & canes
- Tier 4: Prosthetics & orthotics
- Tier 4: Grab bars & bathroom safety equipment

**Tier 3: Sensory Devices**
- Tier 4: Hearing aids
- Tier 4: Vision aids (magnifiers, special glasses)

**Tier 3: Chronic Disease Management Equipment**
- Tier 4: Insulin pumps
- Tier 4: Compression devices (for lymphedema, venous insufficiency)
- Tier 4: Hospital beds & mattresses

---

#### 6. Referrals

**Tier 3: Medical Specialist Consultations**
- Tier 4: Cardiology
- Tier 4: Endocrinology
- Tier 4: Pulmonology
- Tier 4: Gastroenterology
- Tier 4: Nephrology
- Tier 4: Neurology
- Tier 4: Hematology/Oncology
- Tier 4: Rheumatology
- Tier 4: Dermatology
- Tier 4: Urology
- Tier 4: Gynecology
- Tier 4: Ophthalmology
- Tier 4: Otolaryngology (ENT)

**Tier 3: Behavioral Health Providers** ← NEW
- Tier 4: Psychiatry (medication management)
- Tier 4: Psychotherapy (CBT, DBT, ACT, psychodynamic)
- Tier 4: Counseling (individual, couples, family)
- Tier 4: Support groups (grief, addiction, chronic illness)

**Tier 3: Rehabilitation Services**
- Tier 4: Physical therapy
- Tier 4: Occupational therapy
- Tier 4: Speech therapy
- Tier 4: Cardiac rehabilitation
- Tier 4: Pulmonary rehabilitation

**Tier 3: Allied Health Professionals**
- Tier 4: Registered dietitian/nutritionist
- Tier 4: Social work/case management
- Tier 4: Pharmacist consultation
- Tier 4: Diabetes education
- Tier 4: Wound care specialist

---

### BEHAVIORAL CARDS

#### 7. Nutrition

**Tier 3: Dietary Patterns**
- Tier 4: Evidence-based patterns (Mediterranean, DASH, MIND)
- Tier 4: Therapeutic patterns (low-sodium, renal, diabetic, cardiac)
- Tier 4: Macronutrient-focused (low-carb, ketogenic, high-protein)

**Tier 3: Specific Food Focus**
- Tier 4: Increase beneficial foods (vegetables, fruits, whole grains, fish, nuts)
- Tier 4: Reduce harmful foods (sodium, sugar, saturated fat, processed)
- Tier 4: Food substitutions & swaps

**Tier 3: Eating Behaviors & Meal Planning**
- Tier 4: Eating behaviors (mindful eating, portion control, slow eating)
- Tier 4: Meal timing patterns (intermittent fasting, time-restricted eating)
- Tier 4: Meal planning & preparation
- Tier 4: Dining out strategies

---

#### 8. Movement/Exercise

**Tier 3: Aerobic Exercise**
- Tier 4: Walking programs (various intensities/durations)
- Tier 4: Running/jogging programs
- Tier 4: Cycling programs
- Tier 4: Swimming programs
- Tier 4: Group fitness classes (aerobics, dance, spin)

**Tier 3: Strength Training**
- Tier 4: Bodyweight exercises
- Tier 4: Free weights (dumbbells, barbells)
- Tier 4: Resistance bands
- Tier 4: Weight machines
- Tier 4: Functional training

**Tier 3: Flexibility & Stretching**
- Tier 4: Static stretching routines
- Tier 4: Dynamic stretching/warm-ups
- Tier 4: Yoga for flexibility

**Tier 3: Balance Training**
- Tier 4: Static balance exercises
- Tier 4: Dynamic balance exercises
- Tier 4: Tai Chi for balance
- Tier 4: Fall prevention programs

---

#### 9. Recovery (Sleep/Stress)

**Tier 3: Sleep Hygiene & Optimization**
- Tier 4: Sleep schedule consistency
- Tier 4: Sleep environment optimization (darkness, temperature, noise)
- Tier 4: Pre-sleep routines (digital sunset, relaxation)
- Tier 4: Sleep restriction therapy (for insomnia)

**Tier 3: Stress Management**
- Tier 4: Cognitive techniques (reframing, thought stopping)
- Tier 4: Behavioral techniques (time management, boundary setting)
- Tier 4: Physical stress release (exercise, manual therapy)
- Tier 4: Social support mobilization

**Tier 3: Breathing & Relaxation Practices**
- Tier 4: Structured breathing (4-7-8, box breathing, diaphragmatic)
- Tier 4: Progressive muscle relaxation
- Tier 4: Guided imagery/visualization
- Tier 4: Autogenic training

---

#### 10. Mind-Body Practices (Self-Directed)

**Tier 3: Meditation & Mindfulness**
- Tier 4: Mindfulness meditation
- Tier 4: Focused attention meditation
- Tier 4: Loving-kindness meditation
- Tier 4: Body scan meditation
- Tier 4: Mindfulness-based stress reduction (MBSR) practices

**Tier 3: Yoga**
- Tier 4: Hatha yoga
- Tier 4: Restorative yoga
- Tier 4: Gentle/chair yoga
- Tier 4: Yoga for specific conditions (back pain, arthritis)

**Tier 3: Tai Chi & Qigong**
- Tier 4: Tai Chi for balance
- Tier 4: Tai Chi for arthritis
- Tier 4: Qigong practices

**Tier 3: Other Mind-Body Practices**
- Tier 4: Biofeedback
- Tier 4: Hypnosis/self-hypnosis
- Tier 4: Guided imagery

---

#### 11. Environmental & Social Health

**Tier 3: Social Connection & Community**
- Tier 4: Community engagement (join groups, clubs, volunteering)
- Tier 4: Relationship building & maintenance
- Tier 4: Social support network development
- Tier 4: Loneliness/isolation interventions

**Tier 3: Environmental Quality**
- Tier 4: Air quality improvement (HEPA filters, allergen reduction, ventilation)
- Tier 4: Housing safety & quality (mold remediation, lead testing, fall hazards)
- Tier 4: Neighborhood walkability & green space access
- Tier 4: Noise reduction

**Tier 3: Occupational Health**
- Tier 4: Workplace ergonomics (desk setup, chair, monitor height)
- Tier 4: Occupational safety measures
- Tier 4: Work-life balance interventions
- Tier 4: Movement breaks & posture

**Tier 3: Substance Use & Harm Reduction** ← NEW
- Tier 4: Tobacco/nicotine cessation
  - Smoking cessation programs (comprehensive)
  - Vaping cessation
  - Smokeless tobacco cessation
  - Nicotine replacement therapy (OTC)
- Tier 4: Alcohol reduction/moderation
  - Moderate drinking limits
  - Alcohol abstinence programs
  - Medication-assisted treatment (naltrexone - under Medications)
- Tier 4: Substance use disorder support
  - Recovery program participation (AA, SMART Recovery)
  - Harm reduction strategies
  - Relapse prevention techniques
- Tier 4: Harm reduction services
  - Naloxone access/training
  - Safe use education

**Tier 3: Financial Health & Resource Navigation**
- Tier 4: Financial assistance programs
- Tier 4: Transportation resources
- Tier 4: Food security programs (food banks, SNAP)
- Tier 4: Housing assistance

---

#### 12. Micro-Learning

**Tier 3: Cardiovascular Concepts**
- Tier 4: Understanding blood pressure numbers
- Tier 4: Cholesterol basics (LDL, HDL, triglycerides)
- Tier 4: Heart failure overview
- Tier 4: Atrial fibrillation explained

**Tier 3: Metabolic Concepts**
- Tier 4: Blood sugar regulation & insulin resistance
- Tier 4: Hemoglobin A1c explained
- Tier 4: Thyroid function basics
- Tier 4: Metabolic syndrome overview

**Tier 3: Nutrition Science**
- Tier 4: Macronutrients explained (protein, carbs, fats)
- Tier 4: Glycemic index & glycemic load
- Tier 4: Micronutrients & vitamins
- Tier 4: Reading nutrition labels

**Tier 3: Exercise Concepts**
- Tier 4: Heart rate zones for exercise
- Tier 4: Rate of perceived exertion (RPE) scale
- Tier 4: METs explained
- Tier 4: Exercise vs physical activity

**Tier 3: Medication Mechanisms**
- Tier 4: How ACE inhibitors work
- Tier 4: How statins lower cholesterol
- Tier 4: How metformin works
- Tier 4: How SSRIs work

---

## TIER 4 & TIER 5: Examples

### Complete Path Example 1: Medication Card

```
Tier 1: Medical Cards
  Tier 2: Medications
    Tier 3: Prescription Medications
      Tier 4: Cardiovascular Medications → Antihypertensives → ACE Inhibitors
        Tier 5: Lisinopril 10mg Daily
```

**Card Details:**
- **Card Name**: Lisinopril 10mg Daily
- **Card ID**: `MED_RX_CARDIO_ACE_Lisinopril_10mg`
- **Tags**: #Hypertension #Cardiovascular #ChronicManagement #ACC_AHA #Home #USPSTF_GradeA

---

### Complete Path Example 2: Monitoring Card

```
Tier 1: Medical Cards
  Tier 2: Diagnostic Testing
    Tier 3: Home Monitoring
      Tier 4: Cardiovascular Monitoring
        Tier 5: Home Blood Pressure Monitoring BID
```

**Card Details:**
- **Card Name**: Home Blood Pressure Monitoring BID
- **Card ID**: `DIAG_HOME_BP_BID`
- **Tags**: #Hypertension #Cardiovascular #Monitoring #Home #ChronicManagement

---

### Complete Path Example 3: Environmental Card

```
Tier 1: Behavioral Cards
  Tier 2: Environmental & Social Health
    Tier 3: Environmental Quality
      Tier 4: Air Quality Improvement
        Tier 5: Install HEPA Air Purifier + Reduce Home Allergens
```

**Card Details:**
- **Card Name**: Install HEPA Air Purifier + Reduce Home Allergens
- **Card ID**: `ENV_AIR_HEPA_Allergen_Reduction`
- **Tags**: #Asthma #Respiratory #Environmental #Home #PreventiveCare

---

### Complete Path Example 4: Micro-Learning Card

```
Tier 1: Behavioral Cards
  Tier 2: Micro-Learning
    Tier 3: Cardiovascular Concepts
      Tier 4: Blood Pressure Education
        Tier 5: Understanding Your Blood Pressure Numbers (5 min)
```

**Card Details:**
- **Card Name**: Understanding Your Blood Pressure Numbers
- **Card ID**: `MICRO_CARDIO_BP_Numbers`
- **Tags**: #MicroLearning #Cardiovascular #Hypertension #FoundationalCard #Education

---

## Navigation Rules

### Rule 1: Each Card Has ONE Primary Location
- No duplicate cards across the hierarchy
- Use **tags** for cross-referencing, not duplication
- Example: Metoprolol appears ONLY in cardiovascular_meds.md (not also in migraine medications)

### Rule 2: Card Location Decision Tree

When determining where a card belongs:

1. **Is it Medical or Behavioral?** → Determines Tier 1
2. **What type of intervention?** → Determines Tier 2 (1 of 12 types)
3. **Which major category?** → Determines Tier 3
4. **What's the specific subcategory?** → Determines Tier 4
5. **What's the specific action?** → Tier 5 (individual card)

### Rule 3: Multi-Use Cards Use Tags

If a card has multiple uses (e.g., Gabapentin for both neuropathic pain and seizures):
- **Primary Location**: Most common/primary use (neuro_psych_meds.md under "Anti-Seizure")
- **Cross-Reference**: Apply tags like #NeuropathicPain #Seizures #ChronicPain
- **Do NOT**: Create duplicate cards in multiple locations

### Rule 4: Titratable Cards = Single Card

Cards with progressive dosing stay as ONE card with internal tiers:
- Example: "Lisinopril" (not separate cards for 10mg, 20mg, 40mg)
- Internal progression within WHEN section using card tiers

---

## Database Implementation Guidance

### Recommended Schema

```sql
CREATE TABLE smart_cards (
    card_id UUID PRIMARY KEY,
    card_name TEXT NOT NULL,

    -- Tier Structure
    tier_1_category TEXT NOT NULL,  -- 'Medical' or 'Behavioral'
    tier_2_card_type TEXT NOT NULL, -- 1 of 12 types
    tier_3_subcategory TEXT,        -- Major grouping
    tier_4_category TEXT,           -- Specific classification
    tier_5_card_name TEXT,          -- Card name

    -- Content & Metadata
    patient_facing JSONB,
    clinical_details JSONB,
    tags TEXT[],
    evidence_grade CHAR(1),

    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Indexes for hierarchical navigation
CREATE INDEX idx_tier_1 ON smart_cards(tier_1_category);
CREATE INDEX idx_tier_2 ON smart_cards(tier_2_card_type);
CREATE INDEX idx_tier_3 ON smart_cards(tier_3_subcategory);
CREATE INDEX idx_tier_4 ON smart_cards(tier_4_category);

-- Index for tag-based search
CREATE INDEX idx_tags ON smart_cards USING GIN(tags);
```

---

## Quick Reference: Tier 2 Summary

| Tier 2 # | Card Type | Tier 1 | Key Tier 3 Additions |
|----------|-----------|--------|----------------------|
| 1 | Medications | Medical | + OTC/Supplements |
| 2 | Diagnostic Testing | Medical | + Home Monitoring |
| 3 | Imaging Studies | Medical | - |
| 4 | Procedures | Medical | + Surgical Procedures |
| 5 | Durable Medical Equipment | Medical | ✨ NEW TYPE |
| 6 | Referrals | Medical | + Behavioral Health |
| 7 | Nutrition | Behavioral | - |
| 8 | Movement/Exercise | Behavioral | - |
| 9 | Recovery | Behavioral | - |
| 10 | Mind-Body Practices | Behavioral | - |
| 11 | Environmental & Social Health | Behavioral | ✨ NEW TYPE (includes Substance Use) |
| 12 | Micro-Learning | Behavioral | ✨ NEW TYPE |

**Legend:**
- ✨ NEW TYPE = New Tier 2 type added
- + = New Tier 3 subcategory consolidated under existing type
- \- = No structural changes

---

## Tag System (Cross-Cutting Organization)

While the tier system provides **hierarchical navigation**, tags enable **flexible cross-cutting search**.

### Tag Categories (10+)
1. **Clinical Intent**: #PreventiveCare, #ChronicManagement, #AcuteCare
2. **Guidelines**: #USPSTF_GradeA, #ACC_AHA, #ADA, #KDIGO
3. **Care Setting**: #Home, #Outpatient, #Telehealth, #Inpatient
4. **Population**: #Adult, #Geriatric, #Pediatric, #Pregnancy
5. **Condition**: #Hypertension, #Diabetes, #CHF, #Asthma
6. **Organ System**: #Cardiology, #Metabolic, #Pulmonary, #Neurological
7. **Community**: #Easy, #Affordable, #WorkedForMe, #Effective
8. **Urgency**: #Routine, #Urgent, #Emergent
9. **Special Population**: #RenalDosing, #HepaticDosing, #Breastfeeding
10. **Card Function**: #MicroLearning, #ActionCard, #MonitoringCard, #FoundationalCard

---

## Summary

The SMART Card Library uses a **consistent 5-tier hierarchical structure** with **12 Tier 2 card types**:

- **Tier 1** (2): Medical vs Behavioral - Fundamental split by who initiates
- **Tier 2** (12): Card Types - Intervention modality (determines template)
- **Tier 3**: Major subcategories - Clinical/functional groupings
- **Tier 4**: Specific categories - Detailed classifications
- **Tier 5**: Individual cards - Atomic, actionable units

**Key Principles:**
- Each card has **ONE primary location** in the hierarchy
- Use **tags** for cross-referencing (not duplication)
- Tier 2 determines card template and type-specific fields
- **Elegant consolidation** - Tier 3 used effectively for related subtypes
- Card volume estimates deferred until library development complete

This structure enables both **intuitive browsing** (hierarchical) and **powerful searching** (tag-based) while maintaining clinical precision and avoiding over-categorization.
