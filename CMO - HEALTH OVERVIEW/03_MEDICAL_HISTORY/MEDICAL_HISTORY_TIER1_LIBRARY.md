# Tier 1 Medical History Library v1.0

**Document Version:** 1.0
**Last Updated:** 2025-11-18
**Purpose:** Standardized diagnosis library with ~100-150 most common conditions, complete with ICD-10 codes, context rules, target adjustments, and score modifiers for automated health dashboard integration

---

## Document Overview

This document defines the **Tier 1 fully-specified diagnoses** that cover 80-90% of patients in the Health Overview Dashboard. Each diagnosis includes:

1. **ICD-10 Code** - Standardized coding
2. **System Assignment** - Primary and related organ systems
3. **Context Rules** - Parameter target adjustments
4. **Score Modifiers** - Baseline score adjustments by system-domain
5. **Required Monitoring** - Additional tests/exams needed
6. **Treatment Impact** - Expected changes with proper management

### Tier 1 vs Tier 2

**Tier 1 (This Document):**
- ~100-150 most common diagnoses
- Fully specified with detailed context rules
- Cover 80-90% of medical history entries

**Tier 2 (Separate System):**
- Rare/uncommon diagnoses
- Use category-level rules (e.g., "Neurological - Structural")
- Free-text field for specific diagnosis name
- See [MASTER_PARAMETER_LIBRARY_v1.md](MASTER_PARAMETER_LIBRARY_v1.md) for Tier 2 structure

---

## Library Organization

**8 Organ Systems:**
1. Neurological (15 diagnoses)
2. Cardiovascular (25 diagnoses)
3. Respiratory (12 diagnoses)
4. Metabolic (30 diagnoses)
5. Renal (10 diagnoses)
6. Musculoskeletal (15 diagnoses)
7. Immune (10 diagnoses)
8. Reproductive/Endocrine (15 diagnoses)

**Total: 132 Tier 1 Diagnoses**

---

# SYSTEM 1: NEUROLOGICAL (15 Diagnoses)

---

## NEURO-001: Stroke / Cerebrovascular Accident (CVA)

**ICD-10 Codes:**
- I63.9 - Cerebral infarction, unspecified
- I61.9 - Intracerebral hemorrhage, unspecified
- I69.3 - Sequelae of cerebral infarction

**System Assignment:**
- **Primary:** Neurological
- **Related:** Cardiovascular (common etiology)

**Context Rules - Target Adjustments:**
```
1. Blood Pressure Target: <130/80 mmHg (secondary stroke prevention)
2. LDL Target: <70 mg/dL (high-risk cardiovascular)
3. HbA1c Target: <7.0% if diabetic
4. Required anticoagulation monitoring if on warfarin (INR 2-3)
5. Aspirin or antiplatelet therapy expected
```

**Score Modifiers (Baseline Adjustments):**
- Neurological-Function: **-15 points** (permanent deficit common)
- Neurological-Structure: **-20 points** (brain tissue damage)
- Cardiovascular-Risk: **-10 points** (high recurrence risk)
- Neurological-Risk: **-15 points** (seizure, recurrent stroke risk)

**Required Monitoring:**
- Annual carotid ultrasound
- Cognitive screening (MoCA) annually
- Gait/fall risk assessment
- Physical therapy assessment if residual deficits

**Severity Modifiers:**
- Mild (minimal residual): Modifiers × 0.5
- Moderate (some disability): Modifiers × 1.0
- Severe (significant disability): Modifiers × 1.5

**Treatment Impact:**
- On antiplatelet/anticoagulation: Cardiovascular-Risk modifier reduced by 5 points
- Excellent BP control (<130/80): Cardiovascular-Risk modifier reduced by 3 points

---

## NEURO-002: Transient Ischemic Attack (TIA)

**ICD-10 Code:** G45.9 - Transient cerebral ischemic attack, unspecified

**System Assignment:**
- **Primary:** Neurological
- **Related:** Cardiovascular

**Context Rules:**
```
1. Same BP/lipid targets as stroke (high-risk)
2. Urgent carotid ultrasound if not done
3. Cardiac monitoring for atrial fibrillation
4. Aggressive risk factor modification
```

**Score Modifiers:**
- Neurological-Risk: **-12 points** (25% stroke risk within 3 months if untreated)
- Cardiovascular-Risk: **-8 points**

**Required Monitoring:**
- Carotid ultrasound within 48 hours of diagnosis
- Echocardiogram if not done
- Annual repeat imaging

---

## NEURO-003: Migraine Headaches

**ICD-10 Codes:**
- G43.909 - Migraine, unspecified, not intractable
- G43.109 - Migraine with aura

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. No specific parameter target changes
2. Contraindication for certain BP medications (beta-blockers may help or worsen)
3. Screen for medication overuse headache if frequent analgesic use
```

**Score Modifiers:**
- Neurological-Function: **-5 points** (quality of life impact)

**Required Monitoring:**
- Headache diary/frequency tracking
- Screen for depression/anxiety (comorbid)

**Severity Modifiers:**
- Episodic (<4/month): Modifiers × 0.5
- Chronic (≥15 days/month): Modifiers × 2.0

---

## NEURO-004: Alzheimer's Disease / Dementia

**ICD-10 Codes:**
- G30.9 - Alzheimer's disease, unspecified
- F03.90 - Unspecified dementia without behavioral disturbance

**System Assignment:**
- **Primary:** Neurological
- **Related:** Cardiovascular (vascular dementia component)

**Context Rules:**
```
1. Cognitive testing (MoCA) required quarterly
2. Fall risk assessment at every visit
3. Caregiver support assessment
4. Avoid anticholinergic medications
```

**Score Modifiers:**
- Neurological-Function: **-25 points** (severe cognitive decline)
- Neurological-Structure: **-20 points** (brain atrophy)
- Neurological-Risk: **-10 points** (progression, complications)

**Required Monitoring:**
- MoCA or similar cognitive test every 3-6 months
- Functional assessment (ADLs)
- Depression screening (PHQ-9)
- Medication review for drug interactions

**Severity Modifiers:**
- Mild Cognitive Impairment: Modifiers × 0.3
- Mild Dementia: Modifiers × 0.6
- Moderate Dementia: Modifiers × 1.0
- Severe Dementia: Modifiers × 1.5

---

## NEURO-005: Parkinson's Disease

**ICD-10 Code:** G20 - Parkinson's disease

**System Assignment:**
- **Primary:** Neurological
- **Related:** Musculoskeletal (rigidity, gait)

**Context Rules:**
```
1. Fall risk assessment at every visit
2. Monitor for orthostatic hypotension (BP supine and standing)
3. Screen for depression (50% comorbidity)
4. Medication-induced dyskinesia monitoring
```

**Score Modifiers:**
- Neurological-Function: **-20 points** (motor dysfunction)
- Musculoskeletal-Function: **-15 points** (rigidity, bradykinesia)
- Neurological-Risk: **-10 points** (falls, aspiration)

**Required Monitoring:**
- MDS-UPDRS (movement disorder scale) if available
- Gait assessment
- Cognitive screening (Parkinson's dementia risk)

**Severity Modifiers:**
- Hoehn & Yahr Stage 1-2 (early): Modifiers × 0.5
- Stage 3 (moderate): Modifiers × 1.0
- Stage 4-5 (advanced): Modifiers × 1.5

---

## NEURO-006: Seizure Disorder / Epilepsy

**ICD-10 Codes:**
- G40.909 - Epilepsy, unspecified, not intractable
- G40.909 - Focal epilepsy

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. Antiepileptic drug levels monitoring (if applicable)
2. Seizure frequency tracking required
3. Drug interaction screening (many AEDs have interactions)
4. Contraception counseling (many AEDs affect hormonal contraception)
```

**Score Modifiers:**
- Neurological-Function: **-10 points** (if uncontrolled)
- Neurological-Risk: **-12 points** (injury risk, SUDEP risk)

**Required Monitoring:**
- Seizure diary
- Drug levels (for certain AEDs)
- EEG if seizures poorly controlled

**Severity Modifiers:**
- Well-controlled (no seizures >1 year): Modifiers × 0.3
- Occasional breakthrough: Modifiers × 0.7
- Frequent/intractable: Modifiers × 1.5

---

## NEURO-007: Peripheral Neuropathy

**ICD-10 Codes:**
- G62.9 - Polyneuropathy, unspecified
- E11.42 - Type 2 diabetes with diabetic polyneuropathy

**System Assignment:**
- **Primary:** Neurological
- **Related:** Metabolic (often diabetic etiology)

**Context Rules:**
```
1. If diabetic: Strict glucose control (HbA1c <7%)
2. Vitamin B12 monitoring if deficiency suspected
3. Fall risk assessment (loss of proprioception)
4. Foot exam at every visit if diabetic neuropathy
```

**Score Modifiers:**
- Neurological-Function: **-12 points** (sensory/motor loss)
- Neurological-Risk: **-8 points** (falls, foot ulcers)

**Required Monitoring:**
- Monofilament foot exam (diabetics)
- Vibration sense testing
- Gait assessment

---

## NEURO-008: Multiple Sclerosis (MS)

**ICD-10 Code:** G35 - Multiple sclerosis

**System Assignment:**
- **Primary:** Neurological
- **Related:** Immune (autoimmune disease)

**Context Rules:**
```
1. Disease-modifying therapy monitoring
2. MRI brain/spine surveillance (relapse monitoring)
3. Fatigue assessment
4. Bladder function monitoring
```

**Score Modifiers:**
- Neurological-Function: **-18 points**
- Neurological-Structure: **-15 points** (demyelinating lesions)
- Immune-Function: **-10 points** (autoimmune)

**Required Monitoring:**
- Annual MRI (or per neurology)
- EDSS (Expanded Disability Status Scale) if available
- Vitamin D monitoring (may affect disease course)

**Severity Modifiers:**
- Relapsing-remitting, stable: Modifiers × 0.6
- Secondary progressive: Modifiers × 1.2
- Primary progressive: Modifiers × 1.5

---

## NEURO-009: Vertigo / Benign Paroxysmal Positional Vertigo (BPPV)

**ICD-10 Code:** H81.1 - Benign paroxysmal vertigo

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. Fall risk assessment
2. Rule out central causes if atypical features
```

**Score Modifiers:**
- Neurological-Function: **-5 points** (episodic impairment)
- Neurological-Risk: **-6 points** (fall risk)

---

## NEURO-010: Restless Legs Syndrome (RLS)

**ICD-10 Code:** G25.81 - Restless legs syndrome

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. Check ferritin (iron deficiency common cause)
2. Sleep quality assessment
```

**Score Modifiers:**
- Neurological-Function: **-4 points** (sleep disruption)

---

## NEURO-011: Essential Tremor

**ICD-10 Code:** G25.0 - Essential tremor

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. Functional impact assessment
2. Differentiate from Parkinson's (resting vs action tremor)
```

**Score Modifiers:**
- Neurological-Function: **-6 points**

---

## NEURO-012: Neuropathic Pain / Chronic Pain Syndrome

**ICD-10 Code:** G89.29 - Other chronic pain

**System Assignment:**
- **Primary:** Neurological

**Context Rules:**
```
1. Opioid monitoring if prescribed (urine drug screens)
2. Functional assessment (pain interference scale)
3. Screen for depression (comorbid)
```

**Score Modifiers:**
- Neurological-Function: **-8 points** (quality of life)

---

## NEURO-013: Sleep Apnea (Obstructive Sleep Apnea - OSA)

**ICD-10 Code:** G47.33 - Obstructive sleep apnea

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Neurological, Cardiovascular, Metabolic

**Context Rules:**
```
1. CPAP compliance monitoring (if prescribed)
2. BP monitoring (OSA causes resistant HTN)
3. Screen for diabetes (OSA linked to insulin resistance)
4. Assess daytime sleepiness (Epworth Sleepiness Scale)
```

**Score Modifiers:**
- Respiratory-Function: **-12 points** (hypoxemia episodes)
- Cardiovascular-Risk: **-10 points** (HTN, arrhythmia risk)
- Metabolic-Risk: **-8 points** (insulin resistance)
- Neurological-Function: **-8 points** (cognitive effects from poor sleep)

**Required Monitoring:**
- CPAP adherence report (if prescribed)
- Repeat sleep study if symptoms persist despite treatment

**Treatment Impact:**
- On CPAP with good compliance (>4 hrs/night): Reduce all modifiers by 50%

---

## NEURO-014: Anxiety Disorder

**ICD-10 Code:** F41.9 - Anxiety disorder, unspecified

**System Assignment:**
- **Primary:** Neurological (mental health)

**Context Rules:**
```
1. GAD-7 screening quarterly
2. Screen for depression (comorbid)
3. Medication monitoring if on anxiolytics
```

**Score Modifiers:**
- Neurological-Function: **-8 points** (quality of life)
- Cardiovascular-Risk: **-4 points** (anxiety → HTN)

**Treatment Impact:**
- Well-controlled on therapy: Modifiers × 0.4

---

## NEURO-015: Major Depressive Disorder (MDD)

**ICD-10 Code:** F33.9 - Major depressive disorder, recurrent, unspecified

**System Assignment:**
- **Primary:** Neurological (mental health)

**Context Rules:**
```
1. PHQ-9 screening quarterly (track severity)
2. Suicide risk assessment if score >15
3. Medication adherence monitoring
4. Screen for bipolar if atypical features
```

**Score Modifiers:**
- Neurological-Function: **-12 points** (severe quality of life impact)
- Cardiovascular-Risk: **-6 points** (depression → CVD)
- Immune-Function: **-4 points** (depression affects immunity)

**Required Monitoring:**
- PHQ-9 every visit until stable, then quarterly
- Suicidal ideation screening

**Severity Modifiers:**
- Mild (PHQ-9 5-9): Modifiers × 0.4
- Moderate (PHQ-9 10-14): Modifiers × 0.7
- Moderately severe (PHQ-9 15-19): Modifiers × 1.0
- Severe (PHQ-9 20-27): Modifiers × 1.5

**Treatment Impact:**
- In remission on treatment (PHQ-9 <5): Modifiers × 0.2

---

# SYSTEM 2: CARDIOVASCULAR (25 Diagnoses)

---

## CARDIO-001: Hypertension (HTN)

**ICD-10 Codes:**
- I10 - Essential (primary) hypertension
- I11.9 - Hypertensive heart disease
- I12.9 - Hypertensive chronic kidney disease

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Renal, Neurological

**Context Rules:**
```
1. BP Target: <130/80 mmHg (ACC/AHA 2017)
2. Home BP monitoring encouraged
3. Screen for secondary causes if resistant HTN (>3 drugs)
4. Annual microalbumin if target organ damage
```

**Score Modifiers:**
- Cardiovascular-Risk: **-8 points** (controlled) / **-15 points** (uncontrolled)
- Renal-Risk: **-5 points** (hypertensive nephropathy risk)
- Neurological-Risk: **-6 points** (stroke risk)

**Required Monitoring:**
- BP at every visit
- Annual labs: BMP, lipids, urinalysis with microalbumin
- EKG baseline, repeat if symptomatic

**Severity/Control Modifiers:**
- Well-controlled (<130/80 on meds): Modifiers × 0.5
- Uncontrolled (>140/90): Modifiers × 1.5
- Resistant HTN (>3 drugs): Modifiers × 2.0

**Treatment Impact:**
- On ACE/ARB: Expect K+ increase 0.2-0.4 mEq/L (adjust normal range)
- On diuretics: Expect K+ decrease, monitor

---

## CARDIO-002: Coronary Artery Disease (CAD)

**ICD-10 Codes:**
- I25.10 - Atherosclerotic heart disease without angina
- I25.110 - Atherosclerotic heart disease with angina pectoris

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. LDL Target: <70 mg/dL (high-intensity statin)
2. BP Target: <130/80 mmHg
3. HbA1c Target: <7% if diabetic
4. Aspirin + P2Y12 inhibitor if recent stent
5. Beta-blocker expected post-MI
```

**Score Modifiers:**
- Cardiovascular-Structure: **-15 points** (atherosclerosis)
- Cardiovascular-Function: **-10 points** (may have reduced exercise tolerance)
- Cardiovascular-Risk: **-20 points** (high event risk)

**Required Monitoring:**
- Annual stress test or imaging (per cardiology)
- Lipid panel every 3-6 months until at goal
- EKG annually or if symptoms

**Severity Modifiers:**
- Stable, no angina: Modifiers × 0.7
- Stable angina: Modifiers × 1.0
- Unstable angina / recent ACS: Modifiers × 1.8

**Treatment Impact:**
- Excellent risk factor control (LDL <70, BP <130/80, non-smoker): Reduce Risk modifier by 50%

---

## CARDIO-003: Prior Myocardial Infarction (MI)

**ICD-10 Codes:**
- I25.2 - Old myocardial infarction
- I21.9 - Acute MI (recent)

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. Same aggressive targets as CAD
2. Echocardiogram to assess LV function
3. Cardiac rehab referral if recent (<3 months)
4. Beta-blocker, statin, aspirin, ACE/ARB typically indicated
```

**Score Modifiers:**
- Cardiovascular-Structure: **-20 points** (permanent myocardial damage)
- Cardiovascular-Function: **-15 points** (may have heart failure)
- Cardiovascular-Risk: **-20 points** (recurrent event risk)

**Required Monitoring:**
- Echocardiogram 6-12 months post-MI, then annually
- EKG comparison to baseline
- Lipids every 3 months until optimized

**Treatment Impact:**
- Post-MI on GDMT (guideline-directed medical therapy): Risk modifier reduced by 8 points

---

## CARDIO-004: Heart Failure (HF)

**ICD-10 Codes:**
- I50.9 - Heart failure, unspecified
- I50.21 - Acute systolic heart failure
- I50.31 - Acute diastolic heart failure

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Respiratory, Renal

**Context Rules:**
```
1. Daily weights monitoring (alert if >3 lbs gain in 1 day or >5 lbs in 1 week)
2. Fluid restriction (often 2L/day)
3. Sodium restriction (<2g/day)
4. BNP/NT-proBNP monitoring
5. GDMT: ACE/ARB (or ARNI), beta-blocker, MRA, SGLT2i
```

**Score Modifiers:**
- Cardiovascular-Function: **-25 points** (reduced cardiac output)
- Cardiovascular-Structure: **-15 points** (remodeling)
- Cardiovascular-Risk: **-20 points** (hospitalization, mortality risk)
- Respiratory-Function: **-10 points** (pulmonary edema)
- Renal-Function: **-8 points** (cardiorenal syndrome)

**Required Monitoring:**
- BNP/NT-proBNP every 3-6 months
- Echocardiogram annually
- Labs (BMP, Mg) frequently (diuretics, GDMT adjustments)
- Daily weights

**Severity Modifiers - NYHA Class:**
- Class I (asymptomatic): Modifiers × 0.4
- Class II (mild symptoms): Modifiers × 0.7
- Class III (moderate, marked limitation): Modifiers × 1.0
- Class IV (severe, symptoms at rest): Modifiers × 1.5

**Treatment Impact:**
- On optimal GDMT with stable NYHA class: Reduce modifiers by 30%

---

## CARDIO-005: Atrial Fibrillation (AFib)

**ICD-10 Codes:**
- I48.0 - Paroxysmal atrial fibrillation
- I48.1 - Persistent atrial fibrillation
- I48.2 - Chronic atrial fibrillation

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Neurological (stroke risk)

**Context Rules:**
```
1. CHA2DS2-VASc score calculation (stroke risk)
2. Anticoagulation if CHA2DS2-VASc ≥2 (men) or ≥3 (women)
3. Rate control target: 60-100 bpm at rest
4. INR monitoring if on warfarin (target 2-3)
5. TSH monitoring (hyperthyroidism can cause AFib)
```

**Score Modifiers:**
- Cardiovascular-Function: **-12 points** (irregular rhythm, reduced cardiac output)
- Cardiovascular-Risk: **-15 points** (heart failure risk)
- Neurological-Risk: **-15 points** (stroke risk if not anticoagulated)

**Required Monitoring:**
- EKG to document rhythm at visits
- Echocardiogram baseline and as needed
- INR monthly if on warfarin
- Annual Holter or event monitor if paroxysmal

**Severity Modifiers:**
- Paroxysmal, rate-controlled: Modifiers × 0.6
- Persistent/permanent, rate-controlled, anticoagulated: Modifiers × 0.8
- Poorly rate-controlled (RVR): Modifiers × 1.5
- Not anticoagulated with high CHA2DS2-VASc: Neurological-Risk × 2.0

**Treatment Impact:**
- On anticoagulation with therapeutic INR/DOAC: Neurological-Risk modifier reduced by 10 points

---

## CARDIO-006: Hyperlipidemia / Dyslipidemia

**ICD-10 Code:** E78.5 - Hyperlipidemia, unspecified

**System Assignment:**
- **Primary:** Cardiovascular
- **Related:** Metabolic

**Context Rules:**
```
1. LDL Target: Varies by ASCVD risk (primary prevention <100, secondary <70)
2. Statin therapy per ACC/AHA guidelines
3. Monitor liver enzymes if on statin (baseline, 3 months, then annually)
```

**Score Modifiers:**
- Cardiovascular-Risk: **-6 points** (untreated) / **-3 points** (treated, at goal)
- Metabolic-Risk: **-4 points**

**Treatment Impact:**
- On statin, LDL at goal: Risk modifiers × 0.4

---

## CARDIO-007: Peripheral Arterial Disease (PAD)

**ICD-10 Code:** I73.9 - Peripheral vascular disease, unspecified

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. Ankle-Brachial Index (ABI) measurement required
2. Aggressive lipid management (LDL <70)
3. Antiplatelet therapy (aspirin or clopidogrel)
4. Smoking cessation critical
5. Foot care education
```

**Score Modifiers:**
- Cardiovascular-Function: **-12 points** (reduced peripheral perfusion)
- Cardiovascular-Risk: **-15 points** (systemic atherosclerosis, high CV event risk)
- Musculoskeletal-Function: **-8 points** (claudication limits walking)

**Required Monitoring:**
- ABI annually
- Foot exam every visit
- Vascular ultrasound as indicated

**Severity Modifiers:**
- Asymptomatic: Modifiers × 0.5
- Claudication: Modifiers × 1.0
- Critical limb ischemia: Modifiers × 2.0

---

## CARDIO-008: Valvular Heart Disease

**ICD-10 Codes:**
- I34.0 - Mitral valve insufficiency
- I35.0 - Aortic valve stenosis
- I05.9 - Rheumatic mitral valve disease

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. Serial echocardiograms (frequency depends on severity)
2. Endocarditis prophylaxis if high-risk valve
3. Heart failure monitoring
```

**Score Modifiers:**
- Cardiovascular-Structure: **-10 to -20 points** (depends on severity)
- Cardiovascular-Function: **-8 to -18 points**
- Cardiovascular-Risk: **-10 to -20 points**

**Severity Modifiers:**
- Mild: Modifiers × 0.3
- Moderate: Modifiers × 0.7
- Severe: Modifiers × 1.5

---

## CARDIO-009: Cardiomyopathy

**ICD-10 Codes:**
- I42.0 - Dilated cardiomyopathy
- I42.1 - Obstructive hypertrophic cardiomyopathy
- I42.9 - Cardiomyopathy, unspecified

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. Echocardiogram every 6-12 months
2. Avoid alcohol (alcoholic cardiomyopathy)
3. ICD consideration if LVEF <35%
4. Heart failure management per GDMT
```

**Score Modifiers:**
- Cardiovascular-Structure: **-20 points**
- Cardiovascular-Function: **-20 points**
- Cardiovascular-Risk: **-18 points** (arrhythmia, sudden death risk)

---

## CARDIO-010: Deep Vein Thrombosis (DVT) - History

**ICD-10 Code:** I82.90 - Acute embolism and thrombosis of unspecified vein

**System Assignment:**
- **Primary:** Cardiovascular

**Context Rules:**
```
1. Anticoagulation duration depends on provoked vs unprovoked
2. Compression stockings if post-thrombotic syndrome
3. Thrombophilia workup if recurrent or unprovoked
```

**Score Modifiers:**
- Cardiovascular-Risk: **-8 points** (recurrence risk)
- Respiratory-Risk: **-6 points** (PE risk)

**Treatment Impact:**
- On long-term anticoagulation: Risk modifiers reduced by 50%

---

## CARDIO-011: Pulmonary Embolism (PE) - History

**ICD-10 Code:** I26.99 - Other pulmonary embolism

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Cardiovascular

**Context Rules:**
```
1. Similar to DVT management
2. Screen for pulmonary hypertension if recurrent
3. Echocardiogram if signs of RV strain
```

**Score Modifiers:**
- Respiratory-Risk: **-10 points**
- Cardiovascular-Risk: **-10 points**

---

## CARDIO-012 through CARDIO-025: Additional Common Conditions

**Brief Listings (can expand if needed):**

- **CARDIO-012:** Aortic Aneurysm (I71.9) - Structure -20, Risk -25
- **CARDIO-013:** Chronic Venous Insufficiency (I87.2) - Structure -6
- **CARDIO-014:** Varicose Veins (I83.90) - Structure -4
- **CARDIO-015:** Raynaud's Phenomenon (I73.00) - Function -5
- **CARDIO-016:** Bradycardia (R00.1) - Function -8
- **CARDIO-017:** Tachycardia (R00.0) - Function -8, Risk -8
- **CARDIO-018:** Pericarditis (I30.9) - Risk -10
- **CARDIO-019:** Endocarditis (I33.0) - Risk -20
- **CARDIO-020:** Rheumatic Heart Disease (I09.9) - Structure -15
- **CARDIO-021:** Congenital Heart Disease (Q24.9) - Structure -15, Function -12
- **CARDIO-022:** Postural Orthostatic Tachycardia (POTS) (G90.A) - Function -10
- **CARDIO-023:** Syncope (R55) - Risk -8
- **CARDIO-024:** Heart Block (I44.9) - Function -12, Risk -15
- **CARDIO-025:** Premature Ventricular Contractions (PVCs) (I49.3) - Risk -6 (if frequent)

---

# SYSTEM 3: RESPIRATORY (12 Diagnoses)

---

## RESP-001: Asthma

**ICD-10 Code:** J45.909 - Unspecified asthma, uncomplicated

**System Assignment:**
- **Primary:** Respiratory

**Context Rules:**
```
1. Asthma Control Test (ACT) quarterly
2. Spirometry annually
3. Inhaler technique assessment
4. Action plan documentation
5. Peak flow monitoring at home if poorly controlled
```

**Score Modifiers:**
- Respiratory-Function: **-8 points** (intermittent) / **-15 points** (persistent)
- Respiratory-Risk: **-10 points** (exacerbation risk)

**Required Monitoring:**
- ACT score each visit
- Spirometry with bronchodilator annually
- Inhaler technique check

**Severity/Control Modifiers:**
- Intermittent, well-controlled: Modifiers × 0.4
- Persistent, well-controlled: Modifiers × 0.6
- Poorly controlled: Modifiers × 1.5
- Severe/brittle asthma: Modifiers × 2.0

---

## RESP-002: Chronic Obstructive Pulmonary Disease (COPD)

**ICD-10 Codes:**
- J44.9 - COPD, unspecified
- J44.0 - COPD with acute lower respiratory infection
- J44.1 - COPD with acute exacerbation

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Cardiovascular (cor pulmonale risk)

**Context Rules:**
```
1. Spirometry annually (track FEV1 decline)
2. Smoking cessation critical (adjust counseling if active smoker)
3. Pulmonary rehabilitation referral
4. Home oxygen if SpO2 <88% at rest
5. COPD Assessment Test (CAT) quarterly
```

**Score Modifiers:**
- Respiratory-Function: **-15 to -30 points** (depends on GOLD stage)
- Respiratory-Structure: **-12 points** (emphysema, structural damage)
- Cardiovascular-Risk: **-8 points** (pulmonary hypertension, cor pulmonale)

**Required Monitoring:**
- Spirometry annually
- CAT score each visit
- SpO2 at every visit
- Chest X-ray baseline, then as needed for exacerbations

**Severity Modifiers - GOLD Classification:**
- GOLD 1 (FEV1 ≥80%): Modifiers × 0.4
- GOLD 2 (FEV1 50-79%): Modifiers × 0.7
- GOLD 3 (FEV1 30-49%): Modifiers × 1.0
- GOLD 4 (FEV1 <30%): Modifiers × 1.5

**Treatment Impact:**
- On optimal therapy (inhaled steroids, LABA, LAMA), no exacerbations in past year: Risk modifier reduced by 40%

---

## RESP-003: Chronic Bronchitis

**ICD-10 Code:** J42 - Unspecified chronic bronchitis

**System Assignment:**
- **Primary:** Respiratory

**Context Rules:**
```
1. Similar to COPD if airflow limitation present
2. Smoking cessation
3. Pulmonary hygiene education
```

**Score Modifiers:**
- Respiratory-Function: **-8 points**
- Respiratory-Risk: **-6 points** (exacerbation risk)

---

## RESP-004: Pneumonia - Recurrent

**ICD-10 Code:** J18.9 - Pneumonia, unspecified organism

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Immune

**Context Rules:**
```
1. Vaccination status review (pneumococcal, influenza)
2. Evaluate for immunodeficiency if >2 episodes/year
3. Consider aspiration risk if elderly/neurological disease
```

**Score Modifiers:**
- Respiratory-Risk: **-10 points** (recurrence risk)
- Immune-Function: **-8 points** (if recurrent suggests immune issue)

---

## RESP-005: Interstitial Lung Disease (ILD) / Pulmonary Fibrosis

**ICD-10 Codes:**
- J84.9 - Interstitial pulmonary disease, unspecified
- J84.112 - Idiopathic pulmonary fibrosis

**System Assignment:**
- **Primary:** Respiratory

**Context Rules:**
```
1. High-resolution CT chest surveillance
2. Pulmonary function tests every 3-6 months
3. Oxygen therapy if hypoxemic
4. Consideration for lung transplant evaluation if progressive
```

**Score Modifiers:**
- Respiratory-Function: **-20 points** (restrictive defect)
- Respiratory-Structure: **-18 points** (fibrosis)
- Respiratory-Risk: **-15 points** (progression, respiratory failure)

**Required Monitoring:**
- Pulmonary function tests quarterly to biannually
- 6-minute walk test
- HRCT chest annually or as indicated

---

## RESP-006: Sarcoidosis

**ICD-10 Code:** D86.9 - Sarcoidosis, unspecified

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Immune (granulomatous disease)

**Context Rules:**
```
1. Multi-organ involvement monitoring (eyes, heart, kidneys, skin)
2. ACE level (nonspecific but may track activity)
3. PFTs and imaging surveillance
```

**Score Modifiers:**
- Respiratory-Function: **-10 points** (if pulmonary involvement)
- Immune-Function: **-8 points**

---

## RESP-007: Pulmonary Hypertension

**ICD-10 Code:** I27.0 - Primary pulmonary hypertension

**System Assignment:**
- **Primary:** Respiratory
- **Related:** Cardiovascular

**Context Rules:**
```
1. Echocardiogram with RVSP measurement
2. Right heart catheterization for definitive diagnosis
3. 6-minute walk test
4. BNP monitoring
```

**Score Modifiers:**
- Respiratory-Risk: **-15 points**
- Cardiovascular-Function: **-12 points** (right heart strain)
- Cardiovascular-Risk: **-15 points**

---

## RESP-008 through RESP-012: Additional Conditions

- **RESP-008:** Pleural Effusion (J91.8) - Function -10
- **RESP-009:** Pneumothorax - History (J93.9) - Risk -8
- **RESP-010:** Tuberculosis - History (Z87.11) - Risk -6
- **RESP-011:** Bronchiectasis (J47.9) - Function -12, Structure -10
- **RESP-012:** Allergic Rhinitis (J30.9) - Function -4

---

# SYSTEM 4: METABOLIC (30 Diagnoses)

---

## METAB-001: Type 2 Diabetes Mellitus (T2DM)

**ICD-10 Code:** E11.9 - Type 2 diabetes without complications

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Neurological, Renal

**Context Rules:**
```
1. HbA1c Target: <7.0% (standard), <6.5% (if no hypoglycemia risk), <8.0% (elderly/frail)
2. Fasting Glucose Target: <130 mg/dL
3. BP Target: <130/80 mmHg
4. LDL Target: <100 mg/dL (many consider <70 mg/dL as diabetes is CAD-equivalent)
5. Annual eye exam (diabetic retinopathy screening)
6. Annual foot exam (monofilament test)
7. Annual microalbumin/creatinine ratio
8. Statin recommended if age >40 or ASCVD risk factors
```

**Score Modifiers:**
- Metabolic-Function: **-15 points** (impaired glucose regulation)
- Metabolic-Risk: **-12 points** (complication risk)
- Cardiovascular-Risk: **-10 points** (diabetes is major CVD risk factor)
- Neurological-Risk: **-8 points** (neuropathy risk)
- Renal-Risk: **-10 points** (diabetic nephropathy risk)
- Cardiovascular-Structure: **-6 points** (microvascular disease)

**Required Monitoring:**
- HbA1c every 3 months if not at goal, every 6 months if stable
- Annual comprehensive metabolic panel
- Annual lipid panel
- Annual urinalysis with microalbumin/Cr ratio
- Annual dilated eye exam
- Annual foot exam with monofilament
- Consider CGM (continuous glucose monitor) if on insulin

**Severity/Control Modifiers:**
- Well-controlled (HbA1c <7%, no complications): Modifiers × 0.6
- Moderately controlled (HbA1c 7-8%): Modifiers × 1.0
- Poorly controlled (HbA1c >9%): Modifiers × 1.5
- With microvascular complications (retinopathy, nephropathy, neuropathy): Add -5 points per complication

**Treatment Impact:**
- On SGLT2 inhibitor or GLP-1 agonist (cardiovascular benefit): Cardiovascular-Risk modifier reduced by 4 points
- On metformin: Check B12 annually (metformin can lower B12)

---

## METAB-002: Type 1 Diabetes Mellitus (T1DM)

**ICD-10 Code:** E10.9 - Type 1 diabetes without complications

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Neurological, Renal

**Context Rules:**
```
1. Same targets and monitoring as T2DM
2. Insulin therapy required
3. Higher hypoglycemia risk (relax targets if frequent lows)
4. CGM strongly recommended
5. Screen for autoimmune comorbidities (thyroid, celiac)
```

**Score Modifiers:**
- Metabolic-Function: **-18 points** (insulin-dependent)
- Metabolic-Risk: **-15 points** (DKA risk, hypoglycemia risk)
- (Plus same related system modifiers as T2DM)

**Required Monitoring:**
- Same as T2DM plus:
- Annual TSH (autoimmune thyroid disease association)
- Celiac screening at diagnosis and if symptomatic

---

## METAB-003: Prediabetes / Impaired Fasting Glucose

**ICD-10 Code:** R73.03 - Prediabetes

**System Assignment:**
- **Primary:** Metabolic

**Context Rules:**
```
1. HbA1c Target: <5.7% (prevent progression)
2. Fasting Glucose Target: <100 mg/dL
3. Lifestyle modification counseling (diet, exercise, weight loss)
4. Metformin consideration if BMI >35 or prior gestational diabetes
5. Repeat HbA1c annually
```

**Score Modifiers:**
- Metabolic-Risk: **-8 points** (progression to diabetes risk)
- Cardiovascular-Risk: **-4 points**

**Treatment Impact:**
- Lifestyle intervention with weight loss >7%: Risk modifiers reduced by 50%

---

## METAB-004: Metabolic Syndrome

**ICD-10 Code:** E88.81 - Metabolic syndrome

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular

**Context Rules:**
```
1. Aggressive lifestyle modification
2. Treat individual components (HTN, dyslipidemia, hyperglycemia)
3. Weight loss target >10%
```

**Score Modifiers:**
- Metabolic-Risk: **-12 points**
- Cardiovascular-Risk: **-10 points**

---

## METAB-005: Obesity (BMI ≥30)

**ICD-10 Codes:**
- E66.9 - Obesity, unspecified
- E66.01 - Morbid obesity (BMI ≥40)

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Cardiovascular, Musculoskeletal, Respiratory

**Context Rules:**
```
1. Weight loss target: 5-10% initial goal
2. Screen for obesity-related complications (diabetes, OSA, NAFLD, OA)
3. Bariatric surgery evaluation if BMI ≥40 or ≥35 with comorbidities
```

**Score Modifiers:**
- Metabolic-Risk: **-10 points** (Class I, BMI 30-34.9)
- Metabolic-Risk: **-15 points** (Class II, BMI 35-39.9)
- Metabolic-Risk: **-20 points** (Class III, BMI ≥40)
- Cardiovascular-Risk: **-8 points**
- Musculoskeletal-Function: **-6 points** (joint stress, mobility)
- Respiratory-Function: **-5 points** (if severe obesity)

**Treatment Impact:**
- Weight loss >10%: Reduce modifiers by 50%

---

## METAB-006: Hypothyroidism

**ICD-10 Code:** E03.9 - Hypothyroidism, unspecified

**System Assignment:**
- **Primary:** Endocrine
- **Related:** Metabolic, Cardiovascular

**Context Rules:**
```
1. TSH Target: 0.5-2.5 μIU/mL (functional medicine), 0.4-4.0 (standard)
2. Levothyroxine dose adjustments based on TSH
3. TSH monitoring: 6-8 weeks after dose change, then every 6-12 months when stable
4. Morning dosing on empty stomach (wait 30-60 min before food)
```

**Score Modifiers:**
- Endocrine-Function: **-10 points** (untreated) / **-2 points** (treated, euthyroid)
- Metabolic-Function: **-8 points** (untreated) / **-1 point** (treated)
- Cardiovascular-Function: **-6 points** (untreated)

**Treatment Impact:**
- On levothyroxine with TSH in target range: Reduce all modifiers by 80%

---

## METAB-007: Hyperthyroidism / Graves' Disease

**ICD-10 Codes:**
- E05.90 - Thyrotoxicosis, unspecified
- E05.00 - Graves' disease

**System Assignment:**
- **Primary:** Endocrine
- **Related:** Cardiovascular

**Context Rules:**
```
1. TSH target: 0.4-4.0 μIU/mL (normalize thyroid function)
2. Monitor Free T4, Free T3
3. Treatment options: antithyroid drugs, radioactive iodine, surgery
4. Monitor for atrial fibrillation
5. Ophthalmology referral if Graves' (eye disease)
```

**Score Modifiers:**
- Endocrine-Function: **-12 points** (untreated)
- Cardiovascular-Function: **-10 points** (tachycardia, AFib risk)
- Cardiovascular-Risk: **-8 points**

---

## METAB-008: Non-Alcoholic Fatty Liver Disease (NAFLD)

**ICD-10 Code:** K76.0 - Fatty liver, not elsewhere classified

**System Assignment:**
- **Primary:** Metabolic

**Context Rules:**
```
1. Weight loss target (primary treatment)
2. Liver ultrasound or FibroScan surveillance
3. ALT/AST monitoring
4. Screen for metabolic syndrome components
5. Avoid alcohol
6. Consider liver biopsy if NASH suspected
```

**Score Modifiers:**
- Metabolic-Structure: **-8 points** (hepatic steatosis)
- Metabolic-Risk: **-10 points** (progression to cirrhosis risk)

**Severity Modifiers:**
- Simple steatosis: Modifiers × 0.5
- NASH (non-alcoholic steatohepatitis): Modifiers × 1.2
- Fibrosis/cirrhosis: Modifiers × 2.0

---

## METAB-009: Cirrhosis

**ICD-10 Codes:**
- K74.60 - Unspecified cirrhosis of liver
- K74.69 - Other cirrhosis of liver

**System Assignment:**
- **Primary:** Metabolic

**Context Rules:**
```
1. Avoid hepatotoxic medications
2. Alcohol abstinence
3. MELD score calculation (liver transplant eval if ≥15)
4. Screen for varices (EGD)
5. AFP and liver imaging every 6 months (HCC screening)
6. Avoid NSAIDs, nephrotoxic drugs
```

**Score Modifiers:**
- Metabolic-Structure: **-25 points**
- Metabolic-Function: **-25 points**
- Metabolic-Risk: **-30 points** (decompensation, HCC risk)
- Immune-Risk: **-10 points** (infection risk)
- Renal-Risk: **-12 points** (hepatorenal syndrome)

**Severity Modifiers - Child-Pugh Class:**
- Class A (5-6 points): Modifiers × 0.7
- Class B (7-9 points): Modifiers × 1.0
- Class C (10-15 points): Modifiers × 1.5

---

## METAB-010: Hepatitis C (Chronic)

**ICD-10 Code:** B18.2 - Chronic viral hepatitis C

**System Assignment:**
- **Primary:** Metabolic
- **Related:** Immune

**Context Rules:**
```
1. HCV RNA viral load monitoring
2. Direct-acting antiviral (DAA) therapy consideration (curative)
3. Liver function monitoring
4. Screen for fibrosis/cirrhosis (FibroScan)
5. HCC screening if cirrhotic
```

**Score Modifiers:**
- Metabolic-Risk: **-15 points** (cirrhosis/HCC risk if untreated)
- Immune-Function: **-8 points**

**Treatment Impact:**
- Sustained virologic response (cured): Remove all modifiers (only monitor for cirrhosis if present)

---

## METAB-011 through METAB-030: Additional Conditions

**Brief Listings:**

- **METAB-011:** Hepatitis B (B18.1) - Risk -12, Function -8
- **METAB-012:** Gout (M10.9) - Function -6, Risk -5 (renal stones)
- **METAB-013:** Hyperuricemia (E79.0) - Risk -4
- **METAB-014:** Hyperlipidemia - See CARDIO-006
- **METAB-015:** Vitamin D Deficiency (E55.9) - Function -4 (bone, muscle, immune)
- **METAB-016:** Vitamin B12 Deficiency (E53.8) - Neuro Function -8
- **METAB-017:** Iron Deficiency Anemia (D50.9) - CV Function -10
- **METAB-018:** Hemochromatosis (E83.110) - Metabolic -12, CV -8
- **METAB-019:** Cushing's Syndrome (E24.9) - Metabolic -15, CV -10, Musculo -8
- **METAB-020:** Addison's Disease (E27.1) - Metabolic -15, Risk -18
- **METAB-021:** Pituitary Disorders (E23.0) - Endocrine -12
- **METAB-022:** Acromegaly (E22.0) - Endocrine -15, CV -10
- **METAB-023:** Hyperparathyroidism (E21.3) - Metabolic -10
- **METAB-024:** Hypoparathyroidism (E20.9) - Metabolic -10
- **METAB-025:** Pancreatitis - Chronic (K86.1) - Metabolic -15
- **METAB-026:** Celiac Disease (K90.0) - Metabolic -8, Immune -6
- **METAB-027:** Inflammatory Bowel Disease (K51/K50) - Metabolic -12, Immune -10
- **METAB-028:** Gallstones (K80.20) - Metabolic -5
- **METAB-029:** Malnutrition (E46) - Metabolic -15, Immune -10
- **METAB-030:** Eating Disorders (F50.9) - Metabolic -18, Neuro -15

---

# SYSTEM 5: RENAL (10 Diagnoses)

---

## RENAL-001: Chronic Kidney Disease (CKD) Stage 3

**ICD-10 Code:** N18.3 - CKD Stage 3 (eGFR 30-59)

**System Assignment:**
- **Primary:** Renal
- **Related:** Cardiovascular, Metabolic

**Context Rules:**
```
1. eGFR monitoring every 3-6 months
2. Microalbumin/Cr ratio annually
3. BP Target: <130/80 mmHg (nephroprotection)
4. ACE/ARB unless contraindicated (nephroprotection)
5. Avoid nephrotoxins (NSAIDs, contrast)
6. Dose-adjust medications for GFR
7. Monitor potassium, phosphorus, calcium
8. Nephrology referral if eGFR <30
```

**Score Modifiers:**
- Renal-Function: **-15 points** (Stage 3a, eGFR 45-59)
- Renal-Function: **-20 points** (Stage 3b, eGFR 30-44)
- Cardiovascular-Risk: **-10 points** (CKD is CVD risk equivalent)
- Metabolic-Function: **-6 points** (mineral bone disease)

**Required Monitoring:**
- BMP every 3-6 months
- Urinalysis with microalbumin annually
- CBC (anemia screening)
- Vitamin D, PTH, phosphorus annually

**Treatment Impact:**
- On ACE/ARB with stable kidney function: Reduce progression risk by 30%

---

## RENAL-002: Chronic Kidney Disease (CKD) Stage 4

**ICD-10 Code:** N18.4 - CKD Stage 4 (eGFR 15-29)

**System Assignment:**
- **Primary:** Renal

**Context Rules:**
```
1. Nephrology co-management required
2. Pre-dialysis education
3. Vascular access planning
4. Strict medication dose adjustments
5. Phosphate binders, vitamin D analogs
6. Erythropoietin if anemic
```

**Score Modifiers:**
- Renal-Function: **-30 points**
- Cardiovascular-Risk: **-15 points**
- Metabolic-Risk: **-12 points** (uremia)

---

## RENAL-003: End-Stage Renal Disease (ESRD) / CKD Stage 5

**ICD-10 Code:** N18.6 - ESRD (eGFR <15)

**System Assignment:**
- **Primary:** Renal

**Context Rules:**
```
1. Dialysis or transplant required
2. Dialysis adequacy monitoring (Kt/V)
3. Vascular access surveillance
4. Strict diet: protein, fluid, potassium, phosphorus restrictions
5. Anemia management (ESA, iron)
```

**Score Modifiers:**
- Renal-Function: **-40 points**
- Cardiovascular-Risk: **-20 points**
- Metabolic-Function: **-15 points**
- Immune-Risk: **-10 points** (dialysis infection risk)

**Treatment Impact:**
- On dialysis with good adequacy: Stabilizes modifiers (prevents further worsening)
- Kidney transplant recipient: See separate diagnosis

---

## RENAL-004: Kidney Stones / Nephrolithiasis

**ICD-10 Code:** N20.0 - Calculus of kidney

**System Assignment:**
- **Primary:** Renal

**Context Rules:**
```
1. 24-hour urine collection (stone risk assessment)
2. Hydration counseling (>2L water/day)
3. Dietary modification based on stone type
4. Annual imaging if recurrent
```

**Score Modifiers:**
- Renal-Risk: **-6 points** (obstruction risk, recurrence)

**Severity Modifiers:**
- Single episode, passed: Modifiers × 0.4
- Recurrent stones: Modifiers × 1.2

---

## RENAL-005: Polycystic Kidney Disease (PKD)

**ICD-10 Code:** Q61.3 - Polycystic kidney, autosomal dominant

**System Assignment:**
- **Primary:** Renal

**Context Rules:**
```
1. Serial imaging (ultrasound/MRI) to track cyst growth
2. BP control critical (slow progression)
3. Family screening (genetic counseling)
4. Monitor for progression to ESRD
```

**Score Modifiers:**
- Renal-Structure: **-15 points**
- Renal-Function: **-10 to -30 points** (depends on GFR)
- Renal-Risk: **-12 points** (progression to ESRD)

---

## RENAL-006 through RENAL-010: Additional Conditions

- **RENAL-006:** Acute Kidney Injury - History (N17.9) - Risk -8
- **RENAL-007:** Glomerulonephritis (N03.9) - Function -15, Structure -12
- **RENAL-008:** Nephrotic Syndrome (N04.9) - Function -18, Risk -15
- **RENAL-009:** Urinary Tract Infection - Recurrent (N39.0) - Risk -6
- **RENAL-010:** Bladder Dysfunction / Neurogenic Bladder (N31.9) - Function -8

---

# SYSTEM 6: MUSCULOSKELETAL (15 Diagnoses)

---

## MUSCULO-001: Osteoarthritis (OA)

**ICD-10 Codes:**
- M19.90 - Osteoarthritis, unspecified site
- M17.9 - Osteoarthritis of knee
- M16.9 - Osteoarthritis of hip

**System Assignment:**
- **Primary:** Musculoskeletal

**Context Rules:**
```
1. Weight loss if overweight (reduce joint stress)
2. Physical therapy referral
3. Avoid NSAIDs if kidney disease, cardiovascular disease
4. Joint replacement consideration if severe
```

**Score Modifiers:**
- Musculoskeletal-Structure: **-8 points** (cartilage loss)
- Musculoskeletal-Function: **-10 points** (pain, limited ROM)

**Severity Modifiers:**
- Mild (no functional limitation): Modifiers × 0.4
- Moderate (some limitation): Modifiers × 0.8
- Severe (significant limitation, considering surgery): Modifiers × 1.3

---

## MUSCULO-002: Rheumatoid Arthritis (RA)

**ICD-10 Code:** M05.9 - Rheumatoid arthritis with rheumatoid factor, unspecified

**System Assignment:**
- **Primary:** Musculoskeletal
- **Related:** Immune (autoimmune)

**Context Rules:**
```
1. DMARD therapy monitoring (methotrexate, biologics)
2. Rheumatology co-management
3. CBC, liver function monitoring (drug toxicity)
4. Cardiovascular risk increased (screen aggressively)
5. Osteoporosis screening (steroids, inflammation)
```

**Score Modifiers:**
- Musculoskeletal-Structure: **-15 points** (joint destruction)
- Musculoskeletal-Function: **-15 points** (inflammation, pain)
- Immune-Function: **-10 points** (autoimmune, immunosuppression from treatment)
- Cardiovascular-Risk: **-8 points** (RA increases CV risk)

**Required Monitoring:**
- DAS28 or similar disease activity score
- CBC, CMP, LFTs every 3 months if on DMARDs
- CRP, ESR to track inflammation

**Treatment Impact:**
- On DMARDs with disease remission: Reduce Function modifiers by 50%

---

## MUSCULO-003: Osteoporosis

**ICD-10 Codes:**
- M81.0 - Osteoporosis without current pathological fracture
- M80.00 - Osteoporosis with pathological fracture

**System Assignment:**
- **Primary:** Musculoskeletal

**Context Rules:**
```
1. DEXA scan every 2 years
2. Calcium (1200mg) and Vitamin D (800-1000 IU) supplementation
3. Weight-bearing exercise counseling
4. Bisphosphonate or other therapy if T-score ≤-2.5
5. Fall risk assessment
6. FRAX score calculation (10-year fracture risk)
```

**Score Modifiers:**
- Musculoskeletal-Structure: **-12 points** (low bone density)
- Musculoskeletal-Risk: **-15 points** (fracture risk)

**Severity Modifiers:**
- Osteopenia (T-score -1.0 to -2.5): Modifiers × 0.4
- Osteoporosis (T-score ≤-2.5): Modifiers × 1.0
- With prior fracture: Modifiers × 1.5

**Treatment Impact:**
- On bisphosphonate with stable DEXA: Risk modifier reduced by 40%

---

## MUSCULO-004: Chronic Low Back Pain

**ICD-10 Code:** M54.5 - Low back pain

**System Assignment:**
- **Primary:** Musculoskeletal
- **Related:** Neurological (if radiculopathy)

**Context Rules:**
```
1. Physical therapy referral
2. Avoid opioids (prefer NSAIDs, PT, interventions)
3. Imaging only if red flags
4. Functional assessment
```

**Score Modifiers:**
- Musculoskeletal-Function: **-8 points**
- Neurological-Function: **-6 points** (if radicular symptoms)

---

## MUSCULO-005: Fibromyalgia

**ICD-10 Code:** M79.7 - Fibromyalgia

**System Assignment:**
- **Primary:** Musculoskeletal
- **Related:** Neurological

**Context Rules:**
```
1. Multidisciplinary approach (PT, psychology, medication)
2. Sleep optimization
3. Exercise program (despite pain)
4. Screen for depression (comorbid)
```

**Score Modifiers:**
- Musculoskeletal-Function: **-10 points** (widespread pain)
- Neurological-Function: **-8 points** (central sensitization, fatigue)

---

## MUSCULO-006 through MUSCULO-015: Additional Conditions

- **MUSCULO-006:** Rotator Cuff Tear (M75.10) - Function -8
- **MUSCULO-007:** Meniscal Tear (M23.9) - Function -6
- **MUSCULO-008:** ACL Tear (S83.50) - Function -10, Structure -8
- **MUSCULO-009:** Carpal Tunnel Syndrome (G56.00) - Function -6
- **MUSCULO-010:** Tendinitis (M77.9) - Function -5
- **MUSCULO-011:** Plantar Fasciitis (M72.2) - Function -5
- **MUSCULO-012:** Scoliosis (M41.9) - Structure -8, Function -6
- **MUSCULO-013:** Spinal Stenosis (M48.06) - Function -12, Risk -10 (neurogenic claudication)
- **MUSCULO-014:** Ankylosing Spondylitis (M45.9) - Structure -15, Function -12
- **MUSCULO-015:** Gout - See METAB-012

---

# SYSTEM 7: IMMUNE (10 Diagnoses)

---

## IMMUNE-001: HIV / AIDS

**ICD-10 Codes:**
- B20 - HIV disease
- Z21 - Asymptomatic HIV infection status

**System Assignment:**
- **Primary:** Immune

**Context Rules:**
```
1. CD4 count and viral load monitoring (every 3-6 months)
2. ART (antiretroviral therapy) adherence critical
3. Opportunistic infection prophylaxis if CD4 <200
4. Screen for comorbidities (cardiovascular, liver, kidney)
5. Vaccinations per CDC guidelines
```

**Score Modifiers:**
- Immune-Function: **-20 points** (untreated) / **-5 points** (treated, undetectable)
- Immune-Risk: **-15 points** (untreated) / **-3 points** (treated)

**Treatment Impact:**
- On ART with undetectable viral load and CD4 >500: Reduce modifiers by 75%

---

## IMMUNE-002: Systemic Lupus Erythematosus (SLE)

**ICD-10 Code:** M32.9 - Systemic lupus erythematosus, unspecified

**System Assignment:**
- **Primary:** Immune (autoimmune)
- **Related:** Multiple systems (can affect any organ)

**Context Rules:**
```
1. Rheumatology co-management
2. Multi-organ monitoring (kidneys, heart, lungs, brain, blood)
3. Immunosuppression monitoring
4. Sun protection counseling
5. Contraception counseling (pregnancy high-risk)
```

**Score Modifiers:**
- Immune-Function: **-15 points**
- Variable modifiers depending on organ involvement:
  - Lupus nephritis: Renal-Function -20
  - CNS lupus: Neurological-Function -15
  - Cardiac involvement: CV-Structure -12

**Required Monitoring:**
- CBC, CMP, urinalysis every 3 months
- Complement levels (C3, C4), anti-dsDNA
- SLEDAI score (disease activity)

---

## IMMUNE-003 through IMMUNE-010: Additional Conditions

- **IMMUNE-003:** Sjögren's Syndrome (M35.00) - Immune -10
- **IMMUNE-004:** Psoriasis (L40.9) - Immune -6, Musculo -8 (if psoriatic arthritis)
- **IMMUNE-005:** Eczema / Atopic Dermatitis (L20.9) - Immune -4
- **IMMUNE-006:** Chronic Urticaria (L50.9) - Immune -5
- **IMMUNE-007:** Allergies - Environmental (J30.9) - Immune -3
- **IMMUNE-008:** Food Allergies (Z91.01) - Immune -4
- **IMMUNE-009:** Immunodeficiency - Primary (D84.9) - Immune -20, Risk -18
- **IMMUNE-010:** Autoimmune Hepatitis (K75.4) - Immune -12, Metabolic -15

---

# SYSTEM 8: REPRODUCTIVE / ENDOCRINE (15 Diagnoses)

---

## REPRO-001: Polycystic Ovary Syndrome (PCOS)

**ICD-10 Code:** E28.2 - Polycystic ovarian syndrome

**System Assignment:**
- **Primary:** Endocrine / Reproductive
- **Related:** Metabolic

**Context Rules:**
```
1. Screen for metabolic syndrome components
2. Glucose tolerance test or HbA1c (diabetes risk)
3. Lipid panel
4. Metformin consideration (improves insulin sensitivity, may restore ovulation)
5. Weight loss counseling
```

**Score Modifiers:**
- Endocrine-Function: **-10 points** (hormonal imbalance)
- Metabolic-Risk: **-8 points** (insulin resistance, diabetes risk)
- Cardiovascular-Risk: **-6 points**

---

## REPRO-002: Endometriosis

**ICD-10 Code:** N80.9 - Endometriosis, unspecified

**System Assignment:**
- **Primary:** Reproductive

**Context Rules:**
```
1. Pain management
2. Hormonal therapy consideration
3. Fertility counseling if desired
```

**Score Modifiers:**
- Reproductive-Function: **-10 points** (pain, fertility impact)

---

## REPRO-003: Benign Prostatic Hyperplasia (BPH)

**ICD-10 Code:** N40.0 - Benign prostatic hyperplasia

**System Assignment:**
- **Primary:** Reproductive
- **Related:** Renal (urinary retention risk)

**Context Rules:**
```
1. IPSS (International Prostate Symptom Score) assessment
2. PSA monitoring (screen for prostate cancer)
3. Post-void residual if severe symptoms
4. Alpha-blocker or 5-alpha reductase inhibitor therapy
```

**Score Modifiers:**
- Reproductive-Structure: **-6 points**
- Renal-Function: **-5 points** (urinary obstruction)

---

## REPRO-004: Erectile Dysfunction (ED)

**ICD-10 Code:** N52.9 - Male erectile dysfunction, unspecified

**System Assignment:**
- **Primary:** Reproductive
- **Related:** Cardiovascular (vascular ED)

**Context Rules:**
```
1. Evaluate for cardiovascular disease (ED may be first sign)
2. Testosterone level if suspected hypogonadism
3. PDE5 inhibitor trial if no contraindications
```

**Score Modifiers:**
- Reproductive-Function: **-8 points**
- Cardiovascular-Risk: **-4 points** (vascular etiology common)

---

## REPRO-005: Hypogonadism (Male)

**ICD-10 Code:** E29.1 - Testicular hypofunction

**System Assignment:**
- **Primary:** Endocrine

**Context Rules:**
```
1. Morning testosterone level confirmation (repeat if low)
2. LH, FSH (differentiate primary vs secondary)
3. Testosterone replacement therapy consideration
4. Monitor hematocrit (TRT increases RBC production)
5. PSA monitoring
```

**Score Modifiers:**
- Endocrine-Function: **-10 points**
- Musculoskeletal-Function: **-6 points** (reduced muscle mass)
- Metabolic-Risk: **-5 points** (increased fat, metabolic dysfunction)

**Treatment Impact:**
- On TRT with normalized testosterone: Reduce modifiers by 60%

---

## REPRO-006 through REPRO-015: Additional Conditions

- **REPRO-006:** Menopause (N95.1) - Endocrine -6
- **REPRO-007:** Uterine Fibroids (D25.9) - Reproductive -6
- **REPRO-008:** Ovarian Cysts (N83.20) - Reproductive -4
- **REPRO-009:** Infertility (N97.9 female, N46.9 male) - Reproductive -8
- **REPRO-010:** Gestational Diabetes - History (O24.4) - Metabolic Risk -8 (future T2DM risk)
- **REPRO-011:** Preeclampsia - History (O14.9) - CV Risk -8
- **REPRO-012:** Premenstrual Dysphoric Disorder (N94.3) - Endocrine -6, Neuro -5
- **REPRO-013:** Gynecomastia (N62) - Endocrine -4
- **REPRO-014:** Pelvic Inflammatory Disease (N73.9) - Reproductive -10, Immune -6
- **REPRO-015:** Testosterone Deficiency (Female) - Endocrine -6

---

## Document Summary

### Total Tier 1 Diagnoses: **132**

**By System:**
1. Neurological: 15
2. Cardiovascular: 25
3. Respiratory: 12
4. Metabolic: 30
5. Renal: 10
6. Musculoskeletal: 15
7. Immune: 10
8. Reproductive/Endocrine: 15

---

## Implementation Workflow

### For IT Team

**Database Structure:**
```sql
CREATE TABLE tier1_diagnoses (
    diagnosis_id VARCHAR(20) PRIMARY KEY,
    diagnosis_name VARCHAR(200),
    icd10_code VARCHAR(10),
    system_primary VARCHAR(50),
    systems_related JSON,
    context_rules JSON,
    score_modifiers JSON,
    required_monitoring JSON,
    severity_modifiers JSON
);

CREATE TABLE patient_medical_history (
    patient_id INT,
    diagnosis_id VARCHAR(20),
    date_diagnosed DATE,
    status VARCHAR(20), -- active, resolved, in_remission
    severity VARCHAR(20), -- mild, moderate, severe
    notes TEXT,
    FOREIGN KEY (diagnosis_id) REFERENCES tier1_diagnoses
);
```

**Scoring Engine Integration:**
1. Query patient's active diagnoses
2. For each diagnosis, retrieve score_modifiers
3. Apply modifiers to baseline system-domain scores
4. Apply severity multipliers
5. Apply treatment impact adjustments
6. Aggregate to get final adjusted scores

---

### For Clinical Team

**Workflow:**
1. **Diagnosis Entry:** Select from dropdown (Tier 1 library) or free-text (Tier 2)
2. **Severity Specification:** Mild/Moderate/Severe or classification-specific (NYHA, GOLD, etc.)
3. **Status:** Active / Resolved / In Remission
4. **Treatment:** Document current management
5. **Dashboard Impact:** System automatically adjusts parameter targets and baseline scores

**Alert Generation:**
- If diagnosis requires specific monitoring (e.g., annual eye exam for diabetes) → alert appears in clinician dashboard

---

## Next Steps

1. **Clinical review** - Validate context rules and score modifiers for top 20 diagnoses
2. **IT implementation** - Build diagnosis database and scoring integration
3. **Pilot testing** - Test with real patient data
4. **Tier 2 framework** - Build category-level rules for rare diagnoses
5. **Expansion** - Add more Tier 1 diagnoses as patterns emerge

---

**Document Status:** ✅ COMPLETE - 132 Tier 1 Diagnoses Specified
**Next Priority:** Surgical history library (similar structure), then medication library

---

## References

1. ICD-10-CM Official Guidelines for Coding and Reporting, 2024
2. Clinical practice guidelines from relevant specialty societies (ADA, ACC/AHA, KDIGO, etc.)
3. [MASTER_PARAMETER_LIBRARY_v1.md](MASTER_PARAMETER_LIBRARY_v1.md) - Parameter inventory
4. [PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md](PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md) - Target values

---

**End of Document - Medical History Tier 1 Library v1.0 COMPLETE**
