# Tier 1 Medical History Library v1.1 - INTAKE INTEGRATED

**Document Version:** 1.1
**Last Updated:** 2025-11-25
**Purpose:** Standardized diagnosis library optimized for patient intake forms with smart expansion logic
**Changes from v1.0:** Added intake priority flags, patient-friendly labels, and expansion question specifications

---

## Document Overview

This document defines **132 Tier 1 diagnoses** organized for the patient intake workflow. Each diagnosis includes:

1. **ICD-10 Code** - Standardized coding
2. **Patient-Friendly Label** - How condition appears on intake form
3. **Intake Priority** - Visibility in form (1=always show, 2=common, 3=rare/free-text)
4. **Smart Expansion** - Whether follow-up questions appear when checked
5. **Expansion Questions** - Specific questions if smart expansion = Yes
6. **System Assignment** - Primary and related organ systems
7. **Score Modifiers** - Baseline score adjustments
8. **Severity Modifiers** - How expansion answers affect scores
9. **Treatment Impact** - Score adjustments based on therapy
10. **Required Monitoring** - Clinical follow-up needs

---

## Intake Priority System

**Priority 1 (40 conditions):** Always visible on main intake screen - most common, patient-recognizable
**Priority 2 (52 conditions):** Under expandable "Other common conditions" section
**Priority 3 (40 conditions):** Handled via "Other condition: [____]" free-text (Tier 2)

**Smart Expansion:** Only ~25 Priority 1 conditions trigger follow-up questions (2-3 max per condition)

---

# SYSTEM 1: NEUROLOGICAL / MENTAL HEALTH (15 Diagnoses)

---

## NEURO-001: Stroke / Cerebrovascular Accident (CVA)

**Patient-Friendly Label:** Stroke or mini-stroke (TIA)
**Intake Priority:** 1 (Always visible)
**Smart Expansion:** Yes

**Expansion Questions:**
1. **When did this happen?**
   - Options: Less than 1 year ago | 1-5 years ago | 5-10 years ago | More than 10 years ago
   - Maps to: Disease duration

2. **Do you have any lasting effects?** (Check all that apply)
   - Options: Weakness/paralysis | Speech problems | Memory issues | Vision problems | None
   - Maps to: Complications present
   - Score adjustment: Each complication adds -5 points to Neurological-Function

**ICD-10 Codes:**
- I63.9 - Cerebral infarction, unspecified
- I61.9 - Intracerebral hemorrhage, unspecified
- I69.3 - Sequelae of cerebral infarction
- G45.9 - Transient ischemic attack (TIA)

**System Assignment:**
- **Primary:** Neurological
- **Related:** Cardiovascular

**Score Modifiers (Baseline):**
- Neurological-Function: **-15 points**
- Neurological-Structure: **-20 points**
- Cardiovascular-Risk: **-10 points**
- Neurological-Risk: **-15 points**

**Severity Modifiers (based on expansion answers):**
- No lasting effects: Modifiers × 0.5
- 1-2 complications: Modifiers × 1.0
- 3+ complications: Modifiers × 1.5

**Treatment Impact:**
- On blood thinner/aspirin (inferred from medication section): Cardiovascular-Risk modifier reduced by 5 points

**Required Monitoring:**
- Annual carotid ultrasound
- Cognitive screening annually
- Fall risk assessment

---

## NEURO-002: Alzheimer's Disease / Dementia

**Patient-Friendly Label:** Alzheimer's disease or dementia
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How would you describe the memory/thinking problems?**
   - Options: Mild forgetfulness | Moderate difficulty with daily tasks | Severe difficulty
   - Maps to: Severity level

**ICD-10 Codes:**
- G30.9 - Alzheimer's disease, unspecified
- F03.90 - Unspecified dementia without behavioral disturbance

**System Assignment:**
- **Primary:** Neurological
- **Related:** Cardiovascular (vascular dementia)

**Score Modifiers:**
- Neurological-Function: **-25 points**
- Neurological-Structure: **-20 points**
- Neurological-Risk: **-10 points**

**Severity Modifiers:**
- Mild: Modifiers × 0.3
- Moderate: Modifiers × 1.0
- Severe: Modifiers × 1.5

**Required Monitoring:**
- Cognitive testing (MoCA) every 3-6 months
- Fall risk assessment
- Caregiver support assessment

---

## NEURO-003: Parkinson's Disease

**Patient-Friendly Label:** Parkinson's disease
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** G20 - Parkinson's disease

**System Assignment:**
- **Primary:** Neurological
- **Related:** Musculoskeletal

**Score Modifiers:**
- Neurological-Function: **-20 points**
- Musculoskeletal-Function: **-15 points**
- Neurological-Risk: **-10 points**

---

## NEURO-004: Seizures / Epilepsy

**Patient-Friendly Label:** Seizures or epilepsy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How well controlled are your seizures?**
   - Options: No seizures in over 1 year | Occasional seizures | Frequent seizures
   - Maps to: Disease control level

**ICD-10 Code:** G40.909 - Epilepsy, unspecified

**System Assignment:**
- **Primary:** Neurological

**Score Modifiers:**
- Neurological-Function: **-10 points**
- Neurological-Risk: **-12 points**

**Severity Modifiers:**
- Well-controlled (>1 year): Modifiers × 0.3
- Occasional: Modifiers × 0.7
- Frequent: Modifiers × 1.5

---

## NEURO-005: Peripheral Neuropathy (Nerve Damage)

**Patient-Friendly Label:** Neuropathy (numbness/tingling in hands or feet)
**Intake Priority:** 1
**Smart Expansion:** No

**ICD-10 Codes:**
- G62.9 - Polyneuropathy, unspecified
- E11.42 - Diabetic polyneuropathy

**System Assignment:**
- **Primary:** Neurological
- **Related:** Metabolic (if diabetic)

**Score Modifiers:**
- Neurological-Function: **-12 points**
- Neurological-Risk: **-8 points** (fall/injury risk)

---

## NEURO-006: Multiple Sclerosis (MS)

**Patient-Friendly Label:** Multiple sclerosis (MS)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** G35 - Multiple sclerosis

**System Assignment:**
- **Primary:** Neurological
- **Related:** Immune

**Score Modifiers:**
- Neurological-Function: **-18 points**
- Neurological-Structure: **-15 points**
- Immune-Function: **-10 points**

---

## NEURO-007: Migraines / Severe Headaches

**Patient-Friendly Label:** Chronic migraines or severe headaches
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** G43.909 - Migraine, unspecified

**System Assignment:**
- **Primary:** Neurological

**Score Modifiers:**
- Neurological-Function: **-5 points**

---

## NEURO-008: Chronic Pain

**Patient-Friendly Label:** Chronic pain syndrome
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** G89.29 - Other chronic pain

**System Assignment:**
- **Primary:** Neurological

**Score Modifiers:**
- Neurological-Function: **-8 points**

---

## NEURO-009: Sleep Apnea

**Patient-Friendly Label:** Sleep apnea
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Do you use a CPAP machine at night?**
   - Options: Yes, most nights | Yes, but rarely use it | No, don't have one
   - Maps to: Treatment adherence
   - Critical for score adjustment

**ICD-10 Code:** G47.33 - Obstructive sleep apnea

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Neurological, Cardiovascular, Metabolic

**Score Modifiers:**
- Respiratory-Function: **-12 points**
- Cardiovascular-Risk: **-10 points**
- Metabolic-Risk: **-8 points**
- Neurological-Function: **-8 points**

**Treatment Impact:**
- Using CPAP most nights: Reduce ALL modifiers by 50%

---

## NEURO-010: Depression

**Patient-Friendly Label:** Depression
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you currently being treated for depression?**
   - Options: Taking medication | In therapy/counseling | Both medication and therapy | No treatment
   - Maps to: Treatment status

**ICD-10 Code:** F33.9 - Major depressive disorder, recurrent

**System Assignment:**
- **Primary:** Neurological (Mental Health)

**Score Modifiers:**
- Neurological-Function: **-12 points**
- Cardiovascular-Risk: **-6 points**
- Immune-Function: **-4 points**

**Treatment Impact:**
- On treatment (medication or therapy): Modifiers × 0.6
- No treatment: Full modifiers apply

**Required Monitoring:**
- PHQ-9 screening quarterly
- Suicide risk assessment if severe

---

## NEURO-011: Anxiety Disorder

**Patient-Friendly Label:** Anxiety disorder or panic attacks
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you currently on medication for anxiety?**
   - Options: Yes | No
   - Maps to: Treatment status

**ICD-10 Code:** F41.9 - Anxiety disorder, unspecified

**System Assignment:**
- **Primary:** Neurological (Mental Health)

**Score Modifiers:**
- Neurological-Function: **-8 points**
- Cardiovascular-Risk: **-4 points**

**Treatment Impact:**
- On treatment: Modifiers × 0.4

---

## NEURO-012: Bipolar Disorder

**Patient-Friendly Label:** Bipolar disorder
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** F31.9 - Bipolar disorder, unspecified

**System Assignment:**
- **Primary:** Neurological (Mental Health)

**Score Modifiers:**
- Neurological-Function: **-12 points**

---

## NEURO-013: PTSD (Post-Traumatic Stress Disorder)

**Patient-Friendly Label:** PTSD (post-traumatic stress disorder)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** F43.10 - PTSD

**System Assignment:**
- **Primary:** Neurological (Mental Health)

**Score Modifiers:**
- Neurological-Function: **-10 points**

---

## NEURO-014: ADHD / ADD

**Patient-Friendly Label:** ADHD or ADD
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** F90.9 - ADHD, unspecified

**System Assignment:**
- **Primary:** Neurological (Mental Health)

**Score Modifiers:**
- Neurological-Function: **-5 points**

---

## NEURO-015: Restless Legs Syndrome

**Patient-Friendly Label:** Restless legs syndrome
**Intake Priority:** 3 (Tier 2)
**Smart Expansion:** No

**ICD-10 Code:** G25.81 - Restless legs syndrome

---

# SYSTEM 2: CARDIOVASCULAR (25 Diagnoses)

---

## CARDIO-001: Hypertension (High Blood Pressure)

**Patient-Friendly Label:** High blood pressure (hypertension)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you taking blood pressure medication?**
   - Options: Yes, daily | No
   - Maps to: Treatment status

**ICD-10 Codes:**
- I10 - Essential hypertension
- I11.9 - Hypertensive heart disease

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Renal, Neurological

**Score Modifiers:**
- Cardiovascular-Risk: **-8 points** (on meds, controlled)
- Cardiovascular-Risk: **-15 points** (untreated or uncontrolled)
- Renal-Risk: **-5 points**
- Neurological-Risk: **-6 points**

**Treatment Impact:**
- On medication: Use -8 point modifier
- Not on medication: Use -15 point modifier

**Required Monitoring:**
- BP at every visit
- Annual labs (BMP, lipids, urinalysis)

---

## CARDIO-002: High Cholesterol

**Patient-Friendly Label:** High cholesterol
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you taking cholesterol medication (like a statin)?**
   - Options: Yes, daily | No
   - Maps to: Treatment status

**ICD-10 Code:** E78.5 - Hyperlipidemia, unspecified

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Metabolic

**Score Modifiers:**
- Cardiovascular-Risk: **-6 points** (untreated)
- Cardiovascular-Risk: **-3 points** (on statin)
- Metabolic-Risk: **-4 points**

**Treatment Impact:**
- On statin: Use -3 point modifier

---

## CARDIO-003: Heart Attack (Myocardial Infarction)

**Patient-Friendly Label:** Heart attack
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **When did this happen?**
   - Options: Less than 1 year ago | 1-5 years ago | 5-10 years ago | More than 10 years ago
   - Maps to: Disease duration

2. **Are you taking heart medications now?**
   - Options: Yes | No | Not sure
   - Maps to: Treatment adherence

**ICD-10 Codes:**
- I25.2 - Old myocardial infarction
- I21.9 - Acute myocardial infarction

**System Assignment:**
- **Primary:** Cardiovascular

**Score Modifiers:**
- Cardiovascular-Structure: **-20 points**
- Cardiovascular-Function: **-15 points**
- Cardiovascular-Risk: **-20 points**

**Treatment Impact:**
- On guideline-directed medications (inferred from med list): Risk modifier reduced by 8 points

**Required Monitoring:**
- Echocardiogram annually
- Lipid panel every 3 months until optimized

---

## CARDIO-004: Coronary Artery Disease / Angina

**Patient-Friendly Label:** Coronary artery disease or chest pain (angina)
**Intake Priority:** 1
**Smart Expansion:** No

**ICD-10 Code:** I25.10 - Atherosclerotic heart disease

**System Assignment:**
- **Primary:** Cardiovascular

**Score Modifiers:**
- Cardiovascular-Structure: **-15 points**
- Cardiovascular-Function: **-10 points**
- Cardiovascular-Risk: **-20 points**

---

## CARDIO-005: Heart Failure

**Patient-Friendly Label:** Heart failure or weak heart
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How much does shortness of breath limit your activities?**
   - Options: Only with heavy exercise | With normal daily tasks (walking, stairs) | Even when resting
   - Maps to: NYHA class (I-II | III | IV)

2. **Do you use oxygen at home?**
   - Options: Yes | No
   - Maps to: Severity marker

**ICD-10 Codes:**
- I50.9 - Heart failure, unspecified
- I50.21 - Acute systolic heart failure

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Respiratory, Renal

**Score Modifiers:**
- Cardiovascular-Function: **-25 points**
- Cardiovascular-Structure: **-15 points**
- Cardiovascular-Risk: **-20 points**
- Respiratory-Function: **-10 points**
- Renal-Function: **-8 points**

**Severity Modifiers:**
- NYHA I-II: Modifiers × 0.7
- NYHA III: Modifiers × 1.0
- NYHA IV or on oxygen: Modifiers × 1.5

**Required Monitoring:**
- BNP monitoring
- Echocardiogram annually
- Daily weights

---

## CARDIO-006: Irregular Heartbeat (Atrial Fibrillation)

**Patient-Friendly Label:** Irregular heartbeat (atrial fibrillation)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you on a blood thinner for this?**
   - Options: Yes | No | Not sure
   - Maps to: Treatment status (critical for stroke risk)

**ICD-10 Codes:**
- I48.0 - Paroxysmal atrial fibrillation
- I48.2 - Chronic atrial fibrillation

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Neurological (stroke risk)

**Score Modifiers:**
- Cardiovascular-Function: **-12 points**
- Cardiovascular-Risk: **-15 points**
- Neurological-Risk: **-15 points** (if not anticoagulated)

**Treatment Impact:**
- On blood thinner: Neurological-Risk modifier reduced by 10 points

---

## CARDIO-007: Heart Valve Disease

**Patient-Friendly Label:** Heart valve problem
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Codes:**
- I34.0 - Mitral valve insufficiency
- I35.0 - Aortic valve stenosis

**System Assignment:**
- **Primary:** Cardiovascular

**Score Modifiers:**
- Cardiovascular-Structure: **-15 points** (moderate)
- Cardiovascular-Function: **-12 points**
- Cardiovascular-Risk: **-15 points**

---

## CARDIO-008: Peripheral Artery Disease (Poor Leg Circulation)

**Patient-Friendly Label:** Poor circulation in legs (peripheral artery disease)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** I73.9 - Peripheral vascular disease

**System Assignment:**
- **Primary:** Cardiovascular

**Score Modifiers:**
- Cardiovascular-Function: **-12 points**
- Cardiovascular-Risk: **-15 points**
- Musculoskeletal-Function: **-8 points**

---

## CARDIO-009: Blood Clots (DVT/PE)

**Patient-Friendly Label:** Blood clots in legs or lungs (DVT or pulmonary embolism)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you currently on blood thinners?**
   - Options: Yes, still taking | No, stopped | Never prescribed
   - Maps to: Treatment status

**ICD-10 Codes:**
- I82.90 - DVT
- I26.99 - Pulmonary embolism

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Respiratory (if PE)

**Score Modifiers:**
- Cardiovascular-Risk: **-8 points**
- Respiratory-Risk: **-10 points** (if PE)

**Treatment Impact:**
- On anticoagulation: Risk modifiers × 0.5

---

## CARDIO-010: Cardiomyopathy

**Patient-Friendly Label:** Cardiomyopathy (enlarged or thickened heart)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** I42.9 - Cardiomyopathy, unspecified

**System Assignment:**
- **Primary:** Cardiovascular

**Score Modifiers:**
- Cardiovascular-Structure: **-20 points**
- Cardiovascular-Function: **-20 points**
- Cardiovascular-Risk: **-18 points**

---

## CARDIO-011 through CARDIO-025: Additional Conditions (Priority 2-3)

**Priority 2 (Show in "Other Common Conditions"):**
- CARDIO-011: Aortic Aneurysm
- CARDIO-012: Chronic Venous Insufficiency
- CARDIO-013: Varicose Veins
- CARDIO-014: Pacemaker or Defibrillator (ICD)
- CARDIO-015: Heart Block

**Priority 3 (Free-text "Other"):**
- Raynaud's Phenomenon
- Bradycardia
- Tachycardia
- Pericarditis
- Endocarditis
- Rheumatic Heart Disease
- Congenital Heart Disease
- POTS (Postural Orthostatic Tachycardia)
- Syncope (Fainting)
- PVCs (Premature Ventricular Contractions)

---

# SYSTEM 3: RESPIRATORY (12 Diagnoses)

---

## RESP-001: Asthma

**Patient-Friendly Label:** Asthma
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How do you use your inhalers?**
   - Options: Daily controller medication | Only rescue/emergency inhaler | No inhaler
   - Maps to: Treatment type and disease severity

**ICD-10 Code:** J45.909 - Asthma, uncomplicated

**System Assignment:**
- **Primary:** Respiratory

**Score Modifiers:**
- Respiratory-Function: **-8 points** (intermittent)
- Respiratory-Function: **-15 points** (persistent, on daily controller)
- Respiratory-Risk: **-10 points**

**Severity Modifiers:**
- Rescue only (intermittent): Use -8 point modifier
- Daily controller (persistent): Use -15 point modifier

---

## RESP-002: COPD / Emphysema / Chronic Bronchitis

**Patient-Friendly Label:** COPD, emphysema, or chronic bronchitis
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Do you use oxygen at home?**
   - Options: Yes, all the time | Yes, sometimes | No
   - Maps to: Disease severity

**ICD-10 Codes:**
- J44.9 - COPD, unspecified
- J42 - Chronic bronchitis

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Cardiovascular

**Score Modifiers:**
- Respiratory-Function: **-15 to -30 points** (based on severity)
- Respiratory-Structure: **-12 points**
- Cardiovascular-Risk: **-8 points**

**Severity Modifiers:**
- No oxygen: Modifiers × 0.7 (GOLD 1-2)
- Oxygen sometimes: Modifiers × 1.0 (GOLD 3)
- Oxygen all the time: Modifiers × 1.5 (GOLD 4)

---

## RESP-003: Pulmonary Fibrosis / Interstitial Lung Disease

**Patient-Friendly Label:** Pulmonary fibrosis or scarred lungs
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** J84.9 - Interstitial pulmonary disease

**System Assignment:**
- **Primary:** Respiratory

**Score Modifiers:**
- Respiratory-Function: **-20 points**
- Respiratory-Structure: **-18 points**
- Respiratory-Risk: **-15 points**

---

## RESP-004: Pulmonary Hypertension

**Patient-Friendly Label:** Pulmonary hypertension (high blood pressure in lungs)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** I27.0 - Primary pulmonary hypertension

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Cardiovascular

**Score Modifiers:**
- Respiratory-Risk: **-15 points**
- Cardiovascular-Function: **-12 points**
- Cardiovascular-Risk: **-15 points**

---

## RESP-005: Sarcoidosis

**Patient-Friendly Label:** Sarcoidosis
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** D86.9 - Sarcoidosis, unspecified

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Immune

**Score Modifiers:**
- Respiratory-Function: **-10 points**
- Immune-Function: **-8 points**

---

## RESP-006 through RESP-012: Additional Conditions (Priority 2-3)

**Priority 2:**
- Recurrent Pneumonia
- Bronchiectasis

**Priority 3:**
- Pleural Effusion
- Pneumothorax (History)
- Tuberculosis (History)
- Allergic Rhinitis

---

# SYSTEM 4: METABOLIC / ENDOCRINE (30 Diagnoses)

---

## METAB-001: Type 2 Diabetes

**Patient-Friendly Label:** Diabetes (Type 2)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How is your diabetes treated?**
   - Options: Diet and exercise only | Pills/medication | Insulin | Both pills and insulin
   - Maps to: Treatment intensity

2. **Has a doctor told you diabetes has affected any of these?** (Check all that apply)
   - Options: Eyes/vision | Kidneys | Nerves/feet | None of these | Not sure
   - Maps to: Microvascular complications
   - Score adjustment: -5 points per complication

**ICD-10 Code:** E11.9 - Type 2 diabetes without complications

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Neurological, Renal

**Score Modifiers:**
- Metabolic-Function: **-15 points**
- Metabolic-Risk: **-12 points**
- Cardiovascular-Risk: **-10 points**
- Neurological-Risk: **-8 points**
- Renal-Risk: **-10 points**

**Complications Impact:**
- Add -5 points to relevant domain for each complication checked

**Required Monitoring:**
- HbA1c every 3-6 months
- Annual eye exam
- Annual foot exam
- Annual kidney function tests

---

## METAB-002: Type 1 Diabetes

**Patient-Friendly Label:** Diabetes (Type 1)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Do you use an insulin pump?**
   - Options: Yes | No, I use injections | Not sure
   - Maps to: Treatment modality

**ICD-10 Code:** E10.9 - Type 1 diabetes without complications

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Neurological, Renal

**Score Modifiers:**
- Metabolic-Function: **-18 points**
- Metabolic-Risk: **-15 points**
- (Plus same related modifiers as Type 2)

---

## METAB-003: Prediabetes / Borderline Diabetes

**Patient-Friendly Label:** Prediabetes or borderline diabetes
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** R73.03 - Prediabetes

**System Assignment:**
- **Primary:** Metabolic

**Score Modifiers:**
- Metabolic-Risk: **-8 points**
- Cardiovascular-Risk: **-4 points**

---

## METAB-004: Thyroid Problem

**Patient-Friendly Label:** Thyroid problem (underactive or overactive)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What type of thyroid problem?**
   - Options: Underactive (hypothyroid) | Overactive (hyperthyroid) | Not sure
   - Maps to: Condition type

2. **Are you taking thyroid medication?**
   - Options: Yes, daily | No
   - Maps to: Treatment status

**ICD-10 Codes:**
- E03.9 - Hypothyroidism, unspecified
- E05.90 - Hyperthyroidism, unspecified

**System Assignment:**
- **Primary:** Endocrine
- **Related:** Metabolic, Cardiovascular

**Score Modifiers (Hypothyroid):**
- Endocrine-Function: **-10 points** (untreated) / **-2 points** (treated)
- Metabolic-Function: **-8 points** (untreated) / **-1 point** (treated)

**Score Modifiers (Hyperthyroid):**
- Endocrine-Function: **-12 points**
- Cardiovascular-Function: **-10 points**

**Treatment Impact:**
- On medication with normal thyroid levels: Reduce modifiers by 80%

---

## METAB-005: Obesity (BMI ≥30)

**Patient-Friendly Label:** Obesity
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** E66.9 - Obesity, unspecified

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Musculoskeletal, Respiratory

**Score Modifiers:**
- Metabolic-Risk: **-10 to -20 points** (based on BMI class)
- Cardiovascular-Risk: **-8 points**
- Musculoskeletal-Function: **-6 points**

---

## METAB-006: Fatty Liver Disease

**Patient-Friendly Label:** Fatty liver disease
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** K76.0 - Fatty liver

**System Assignment:**
- **Primary:** Metabolic

**Score Modifiers:**
- Metabolic-Structure: **-8 points**
- Metabolic-Risk: **-10 points**

---

## METAB-007: Liver Cirrhosis

**Patient-Friendly Label:** Liver cirrhosis or severe liver disease
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What caused the cirrhosis?**
   - Options: Alcohol | Hepatitis | Other/Unknown
   - Maps to: Etiology

**ICD-10 Code:** K74.60 - Unspecified cirrhosis of liver

**System Assignment:**
- **Primary:** Metabolic

**Score Modifiers:**
- Metabolic-Structure: **-25 points**
- Metabolic-Function: **-25 points**
- Metabolic-Risk: **-30 points**
- Immune-Risk: **-10 points**
- Renal-Risk: **-12 points**

**Required Monitoring:**
- Liver cancer screening every 6 months
- Avoid hepatotoxic medications

---

## METAB-008: Hepatitis B or C

**Patient-Friendly Label:** Hepatitis B or hepatitis C
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which type?**
   - Options: Hepatitis B | Hepatitis C | Both | Not sure
   - Maps to: Condition type

2. **Have you been treated or cured?**
   - Options: Yes, cured | Currently being treated | Not treated
   - Maps to: Treatment status

**ICD-10 Codes:**
- B18.1 - Chronic hepatitis B
- B18.2 - Chronic hepatitis C

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Immune

**Score Modifiers:**
- Metabolic-Risk: **-15 points** (if untreated)
- Immune-Function: **-8 points**

**Treatment Impact:**
- Hepatitis C cured (SVR): Remove all modifiers

---

## METAB-009: Metabolic Syndrome

**Patient-Friendly Label:** Metabolic syndrome
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** E88.81 - Metabolic syndrome

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular

**Score Modifiers:**
- Metabolic-Risk: **-12 points**
- Cardiovascular-Risk: **-10 points**

---

## METAB-010: Gout

**Patient-Friendly Label:** Gout
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** M10.9 - Gout, unspecified

**System Assignment:**
- **Primary:** Metabolic

**Score Modifiers:**
- Metabolic-Function: **-6 points**
- Metabolic-Risk: **-5 points**

---

## METAB-011 through METAB-030: Additional Conditions (Priority 2-3)

**Priority 2:**
- Vitamin D Deficiency
- Vitamin B12 Deficiency
- Iron Deficiency Anemia
- Celiac Disease
- Inflammatory Bowel Disease (Crohn's or Ulcerative Colitis)
- Gallstones
- Chronic Pancreatitis

**Priority 3:**
- Hemochromatosis
- Cushing's Syndrome
- Addison's Disease
- Pituitary Disorders
- Acromegaly
- Hyperparathyroidism
- Hypoparathyroidism
- Malnutrition
- Eating Disorders (Anorexia, Bulimia)

---

# SYSTEM 5: RENAL (10 Diagnoses)

---

## RENAL-001: Chronic Kidney Disease

**Patient-Friendly Label:** Chronic kidney disease
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What stage kidney disease (if you know)?**
   - Options: Stage 3 | Stage 4 | Stage 5 | On dialysis | Don't know
   - Maps to: Disease severity

**ICD-10 Codes:**
- N18.3 - CKD Stage 3
- N18.4 - CKD Stage 4
- N18.6 - ESRD / Stage 5

**System Assignment:**
- **Primary:** Renal
- **Related:** Cardiovascular, Metabolic

**Score Modifiers:**
- Renal-Function: **-15 points** (Stage 3a)
- Renal-Function: **-20 points** (Stage 3b)
- Renal-Function: **-30 points** (Stage 4)
- Renal-Function: **-40 points** (Stage 5/ESRD)
- Cardiovascular-Risk: **-10 to -20 points** (increases with stage)

**Severity Modifiers:**
- Based on stage selection from expansion question

---

## RENAL-002: Dialysis (End-Stage Kidney Disease)

**Patient-Friendly Label:** On dialysis (end-stage kidney disease)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you getting regular dialysis treatments?**
   - Options: Yes, 3 times per week | Yes, different schedule | Not currently dialyzing
   - Maps to: Treatment adherence

**ICD-10 Code:** N18.6 - ESRD

**System Assignment:**
- **Primary:** Renal

**Score Modifiers:**
- Renal-Function: **-40 points**
- Cardiovascular-Risk: **-20 points**
- Metabolic-Function: **-15 points**
- Immune-Risk: **-10 points**

---

## RENAL-003: Kidney Stones

**Patient-Friendly Label:** Kidney stones (recurrent or multiple)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** N20.0 - Calculus of kidney

**System Assignment:**
- **Primary:** Renal

**Score Modifiers:**
- Renal-Risk: **-6 points**

---

## RENAL-004: Polycystic Kidney Disease

**Patient-Friendly Label:** Polycystic kidney disease
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** Q61.3 - Polycystic kidney, autosomal dominant

**System Assignment:**
- **Primary:** Renal

**Score Modifiers:**
- Renal-Structure: **-15 points**
- Renal-Function: **-10 to -30 points**
- Renal-Risk: **-12 points**

---

## RENAL-005 through RENAL-010: Additional Conditions (Priority 2-3)

**Priority 2:**
- Acute Kidney Injury (History)

**Priority 3:**
- Glomerulonephritis
- Nephrotic Syndrome
- Recurrent Urinary Tract Infections
- Bladder Dysfunction

---

# SYSTEM 6: MUSCULOSKELETAL (15 Diagnoses)

---

## MUSCULO-001: Osteoarthritis (Wear-and-Tear Arthritis)

**Patient-Friendly Label:** Osteoarthritis (wear-and-tear arthritis)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which joints are affected?** (Check all that apply)
   - Options: Knee | Hip | Back/spine | Hands | Shoulder | Other
   - Maps to: Joint involvement

**ICD-10 Codes:**
- M19.90 - Osteoarthritis, unspecified site
- M17.9 - Osteoarthritis of knee
- M16.9 - Osteoarthritis of hip

**System Assignment:**
- **Primary:** Musculoskeletal

**Score Modifiers:**
- Musculoskeletal-Structure: **-8 points**
- Musculoskeletal-Function: **-10 points**

---

## MUSCULO-002: Rheumatoid Arthritis

**Patient-Friendly Label:** Rheumatoid arthritis
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you taking medication for this?**
   - Options: Yes, daily medication | No
   - Maps to: Treatment status

**ICD-10 Code:** M05.9 - Rheumatoid arthritis with rheumatoid factor

**System Assignment:**
- **Primary:** Musculoskeletal
- **Related:** Immune

**Score Modifiers:**
- Musculoskeletal-Structure: **-15 points**
- Musculoskeletal-Function: **-15 points**
- Immune-Function: **-10 points**
- Cardiovascular-Risk: **-8 points**

**Treatment Impact:**
- On DMARDs with remission: Function modifiers × 0.5

---

## MUSCULO-003: Osteoporosis (Weak Bones)

**Patient-Friendly Label:** Osteoporosis (weak bones)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Have you had a fracture from weak bones?**
   - Options: Yes | No
   - Maps to: Complications

2. **Are you taking medication for osteoporosis?**
   - Options: Yes | No
   - Maps to: Treatment status

**ICD-10 Code:** M81.0 - Osteoporosis without fracture

**System Assignment:**
- **Primary:** Musculoskeletal

**Score Modifiers:**
- Musculoskeletal-Structure: **-12 points**
- Musculoskeletal-Risk: **-15 points**

**Severity Modifiers:**
- With prior fracture: Modifiers × 1.5

**Treatment Impact:**
- On bisphosphonate: Risk modifier × 0.6

---

## MUSCULO-004: Chronic Back Pain

**Patient-Friendly Label:** Chronic back pain or spine problems
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** M54.5 - Low back pain

**System Assignment:**
- **Primary:** Musculoskeletal

**Score Modifiers:**
- Musculoskeletal-Function: **-8 points**

---

## MUSCULO-005: Fibromyalgia

**Patient-Friendly Label:** Fibromyalgia
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** M79.7 - Fibromyalgia

**System Assignment:**
- **Primary:** Musculoskeletal
- **Related:** Neurological

**Score Modifiers:**
- Musculoskeletal-Function: **-10 points**
- Neurological-Function: **-8 points**

---

## MUSCULO-006 through MUSCULO-015: Additional Conditions (Priority 2-3)

**Priority 2:**
- Spinal Stenosis
- Ankylosing Spondylitis

**Priority 3:**
- Rotator Cuff Tear
- Meniscal Tear (Knee)
- ACL Tear
- Carpal Tunnel Syndrome
- Tendinitis
- Plantar Fasciitis
- Scoliosis

---

# SYSTEM 7: IMMUNE / CANCER (10 Diagnoses)

---

## IMMUNE-001: Cancer (Any Type)

**Patient-Friendly Label:** Cancer (any type)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What type of cancer?**
   - Free-text field: [________________]
   - Maps to: Cancer type

2. **Current status:**
   - Options: Cured/in remission | Currently being treated | Monitoring/surveillance
   - Maps to: Disease status

**ICD-10 Code:** C80.1 - Malignant neoplasm, unspecified

**System Assignment:**
- **Primary:** Immune
- **Related:** Variable by cancer type

**Score Modifiers:**
- Immune-Risk: **-15 to -30 points** (based on type and status)
- Variable by organ system involved

**Severity Modifiers:**
- In remission >5 years: Modifiers × 0.5
- Currently treating: Modifiers × 1.5

---

## IMMUNE-002: HIV / AIDS

**Patient-Friendly Label:** HIV or AIDS
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you taking HIV medications daily?**
   - Options: Yes, every day | Sometimes | No
   - Maps to: Treatment adherence (CRITICAL)

**ICD-10 Codes:**
- B20 - HIV disease
- Z21 - Asymptomatic HIV

**System Assignment:**
- **Primary:** Immune

**Score Modifiers:**
- Immune-Function: **-20 points** (untreated)
- Immune-Risk: **-15 points** (untreated)

**Treatment Impact:**
- On ART with undetectable viral load: Modifiers × 0.25 (reduce by 75%)

---

## IMMUNE-003: Lupus (Systemic Lupus Erythematosus)

**Patient-Friendly Label:** Lupus (systemic lupus erythematosus)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** M32.9 - Systemic lupus erythematosus

**System Assignment:**
- **Primary:** Immune
- **Related:** Multiple systems

**Score Modifiers:**
- Immune-Function: **-15 points**
- Variable by organ involvement

---

## IMMUNE-004: Psoriasis / Psoriatic Arthritis

**Patient-Friendly Label:** Psoriasis or psoriatic arthritis
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** L40.9 - Psoriasis

**System Assignment:**
- **Primary:** Immune
- **Related:** Musculoskeletal (if arthritis)

**Score Modifiers:**
- Immune-Function: **-6 points**
- Musculoskeletal-Function: **-8 points** (if arthritis)

---

## IMMUNE-005 through IMMUNE-010: Additional Conditions (Priority 2-3)

**Priority 2:**
- Sjögren's Syndrome
- Chronic Urticaria (Hives)
- Severe Environmental Allergies
- Autoimmune Hepatitis

**Priority 3:**
- Eczema / Atopic Dermatitis
- Severe Food Allergies (Anaphylaxis)
- Primary Immunodeficiency

---

# SYSTEM 8: REPRODUCTIVE / HORMONAL (15 Diagnoses)

---

## REPRO-001: Polycystic Ovary Syndrome (PCOS)

**Patient-Friendly Label:** PCOS (polycystic ovary syndrome)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** E28.2 - Polycystic ovarian syndrome

**System Assignment:**
- **Primary:** Endocrine / Reproductive
- **Related:** Metabolic

**Score Modifiers:**
- Endocrine-Function: **-10 points**
- Metabolic-Risk: **-8 points**
- Cardiovascular-Risk: **-6 points**

---

## REPRO-002: Endometriosis

**Patient-Friendly Label:** Endometriosis
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** N80.9 - Endometriosis, unspecified

**System Assignment:**
- **Primary:** Reproductive

**Score Modifiers:**
- Reproductive-Function: **-10 points**

---

## REPRO-003: Benign Prostatic Hyperplasia (BPH)

**Patient-Friendly Label:** Enlarged prostate (BPH)
**Intake Priority:** 2
**Smart Expansion:** No

**ICD-10 Code:** N40.0 - Benign prostatic hyperplasia

**System Assignment:**
- **Primary:** Reproductive
- **Related:** Renal

**Score Modifiers:**
- Reproductive-Structure: **-6 points**
- Renal-Function: **-5 points**

---

## REPRO-004: Low Testosterone (Male Hypogonadism)

**Patient-Friendly Label:** Low testosterone
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Are you on testosterone replacement therapy?**
   - Options: Yes | No
   - Maps to: Treatment status

**ICD-10 Code:** E29.1 - Testicular hypofunction

**System Assignment:**
- **Primary:** Endocrine

**Score Modifiers:**
- Endocrine-Function: **-10 points**
- Musculoskeletal-Function: **-6 points**
- Metabolic-Risk: **-5 points**

**Treatment Impact:**
- On TRT: Modifiers × 0.4

---

## REPRO-005 through REPRO-015: Additional Conditions (Priority 2-3)

**Priority 2:**
- Menopause
- Gestational Diabetes (History)
- Preeclampsia (History)

**Priority 3:**
- Uterine Fibroids
- Ovarian Cysts
- Infertility
- Premenstrual Dysphoric Disorder (PMDD)
- Gynecomastia
- Pelvic Inflammatory Disease
- Erectile Dysfunction

---

# INTAKE PRIORITY SUMMARY

## PRIORITY 1 (Always Visible - 40 Conditions)

**Cardiovascular (9):**
- High blood pressure
- High cholesterol
- Heart attack
- Coronary artery disease
- Heart failure
- Irregular heartbeat (AFib)
- Blood clots (DVT/PE)
- Stroke or mini-stroke

**Neurological/Mental Health (8):**
- Stroke (covered above)
- Alzheimer's/Dementia
- Seizures/Epilepsy
- Neuropathy
- Sleep apnea
- Depression
- Anxiety
- Chronic pain

**Respiratory (2):**
- Asthma
- COPD/Emphysema

**Metabolic (6):**
- Diabetes Type 1
- Diabetes Type 2
- Thyroid problem
- Liver cirrhosis

**Renal (2):**
- Chronic kidney disease
- Dialysis

**Musculoskeletal (3):**
- Osteoarthritis
- Rheumatoid arthritis
- Osteoporosis

**Immune/Cancer (2):**
- Cancer (any type)
- HIV/AIDS

**TOTAL: 32 core conditions + 8 high-priority mental health/neurological = 40**

## PRIORITY 2 (Expandable "Other Common Conditions" - 52 Conditions)

All other conditions with Priority 2 designation

## PRIORITY 3 (Free-Text "Other" - 40 Conditions)

Rare or highly technical diagnoses

---

**Document Status:** ✅ READY FOR INTAKE IMPLEMENTATION
**Next Steps:**
1. Create Family History Library
2. Create Surgical History Library
3. Create Allergy Library
4. Create Patient-Facing Form Mockup

---

**End of Document - Medical History Tier 1 Library v1.1 INTAKE INTEGRATED**
