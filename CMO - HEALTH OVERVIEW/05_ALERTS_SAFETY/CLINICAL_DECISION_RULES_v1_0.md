# CLINICAL DECISION RULES SPECIFICATION
## Patient Health Dashboard - Multi-Parameter Alert Patterns

**Document Type:** Core Clinical Logic - Safety Critical  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - REVISED  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture and safety principles
- `CRITICAL_ALERTS_v1_1.md` - Alert tier hierarchy and display logic
- `PARAMETER_NORMALIZATION_v2.md` - Individual parameter scoring
- `TEMPORAL_SCORING.md` - Temporal flags and trend detection
- `CONTEXT_RULES.md` - Patient-specific adjustments

**This document connects to:**
- `PARAMETERS_*.md` files - **SINGLE SOURCE OF TRUTH for all numeric thresholds**
- `ALERT_MESSAGES.md` - Patient and clinician alert text
- `DASHBOARD_LEVEL1_SPEC.md` - How multi-parameter alerts display

---

## DOCUMENT PURPOSE

This specification defines **safety-critical multi-parameter decision rules** that detect clinical emergencies requiring immediate attention.

**Scope of This Document:**
- **CRITICAL tier patterns** (life-threatening, immediate action)
- **URGENT tier patterns** (same-day evaluation required)
- **WARNING tier patterns** are in a separate document: `RISK_WORKUP_RULES.md` (not safety-critical)

**Critical Design Principle:**
> This document contains NO numeric thresholds. All numeric values are defined in PARAMETERS_*.md files. This document references **severity tiers** and **derived temporal flags** only.

**What This Document Provides:**
1. Boolean logic for combining parameter severity tiers
2. Temporal flag requirements for each pattern
3. Context rule dependencies
4. Validation targets (not claims)
5. Display and workflow specifications

**What This Document Does NOT Provide:**
- âŒ Numeric threshold values (those are in PARAMETERS_*.md)
- âŒ Temporal calculations (those are in TEMPORAL_SCORING.md)
- âŒ Context adjustments (those are in CONTEXT_RULES.md)
- âŒ Non-urgent clinical decision support (that's in RISK_WORKUP_RULES.md)

---

## SECTION 1: RULE ARCHITECTURE

### 1.1 Severity Tier Reference System

**Instead of hard-coding numbers, rules reference parameter severity tiers:**

```
Example (WRONG - what we used to do):
  IF potassium >6.5 mEq/L
  THEN trigger alert

Example (CORRECT - what we do now):
  IF POTASSIUM_TIER = CRITICAL
  THEN trigger alert
  
Where POTASSIUM_TIER_CRITICAL is defined in PARAMETERS_ELECTROLYTES.md
with context-adjusted numeric thresholds
```

**Standard tier naming convention:**
```
[PARAMETER]_TIER_[SEVERITY]

Severity levels:
- CRITICAL: Life-threatening, immediate action
- URGENT: Same-day evaluation required
- WARNING: Attention needed within days
- MONITOR: Watch closely, recheck soon
- NORMAL: Within acceptable range
```

### 1.2 Temporal Flag Reference System

**Instead of inline temporal calculations, rules reference derived flags:**

```
Example (WRONG - what we used to do):
  IF (Creatinine_current - Creatinine_48h_ago) â‰¥0.3 mg/dL
  THEN AKI present

Example (CORRECT - what we do now):
  IF CREATININE_DELTA_48H_FLAG = AKI_STAGE1_OR_HIGHER
  THEN AKI present
  
Where CREATININE_DELTA_48H_FLAG is calculated in TEMPORAL_SCORING.md
using proper time-windowing and data quality checks
```

**Standard temporal flag naming:**
```
[PARAMETER]_DELTA_[TIMEWINDOW]_FLAG
[PARAMETER]_TREND_[PATTERN]_FLAG
[PARAMETER]_VELOCITY_[SPEED]_FLAG

Examples:
- CREATININE_DELTA_48H_FLAG
- HGB_DROP_3M_FLAG
- WEIGHT_GAIN_3D_FLAG
- GLUCOSE_TREND_WORSENING_FLAG
```

### 1.3 Rule Component Structure

**Every clinical decision rule must include:**

```
RULE_ID: [Unique identifier]
RULE_NAME: [Clinical syndrome name]
TIER: [CRITICAL or URGENT only in this document]
PRIORITY: [1-20, lower = more urgent]
EVIDENCE_BASE: [Guidelines, validation studies]

PARAMETER_DEPENDENCIES:
  - [List of parameter tiers referenced]
  
TEMPORAL_DEPENDENCIES:
  - [List of temporal flags referenced]
  
CONTEXT_DEPENDENCIES:
  - [List of context rules that modify this pattern]

BOOLEAN_LOGIC:
  [Combination of parameter tiers, temporal flags, and context flags]
  
VALIDATION_TARGETS:
  - Target Sensitivity: [X]% (from literature; to be validated)
  - Target Specificity: [Y]% (from literature; to be validated)
  - Target PPV: [Z]% (to be validated on our population)

PATIENT_MESSAGE_TEMPLATE: [Reference to ALERT_MESSAGES.md]
CLINICIAN_MESSAGE_TEMPLATE: [Reference to ALERT_MESSAGES.md]
```

### 1.4 Rule Priority Ordering

**When multiple rules trigger simultaneously:**

1. **Life-threatening infections first** (Sepsis, Septic Shock)
2. **Immediate cardiovascular threats** (STEMI, Cardiogenic Shock)
3. **Acute metabolic crises** (Severe DKA, Profound Hypoglycemia)
4. **Pregnancy emergencies** (Eclampsia, Severe Preeclampsia)
5. **Other critical patterns** (Acute Liver Failure, Severe AKI)
6. **Urgent patterns** (all lower priority than CRITICAL)

---

## SECTION 2: CRITICAL TIER PATTERNS

### 2.1 Sepsis Suspicion Pattern

**Clinical Background:**
Early sepsis detection before hemodynamic collapse. Based on Sepsis-3 definitions with qSOFA and SIRS criteria.

**Evidence Base:**
- Singer M, et al. JAMA 2016 (Sepsis-3 definitions)
- Seymour CW, et al. JAMA 2016 (qSOFA validation)
- Surviving Sepsis Campaign Guidelines 2021

**Rule Logic:**

```
RULE_ID: SEPSIS_SUSPECTED
RULE_NAME: Suspected Sepsis (Early Detection)
TIER: URGENT (escalates to CRITICAL if hypotension present)
PRIORITY: 2

PARAMETER_DEPENDENCIES:
  - TEMPERATURE_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - HEART_RATE_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - RESPIRATORY_RATE_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - WBC_TIER (from PARAMETERS_BASIC_LABS.md)
  - SYSTOLIC_BP_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - LACTATE_TIER (from PARAMETERS_SPECIALIZED_LABS.md, if available)

TEMPORAL_DEPENDENCIES:
  - INFECTION_SUSPECTED_FLAG (clinical input or dx code)
  - VITAL_SIGNS_TREND_WORSENING_FLAG (optional)

CONTEXT_DEPENDENCIES:
  - IMMUNOSUPPRESSION_FLAG (lowers threshold)
  - POST_OPERATIVE_FLAG (modifies interpretation)
  - CHRONIC_CONDITION_FLAGS (adjusts baseline expectations)

BOOLEAN_LOGIC:

Option A - qSOFA-Based (preferred if complete vitals):
  IF (INFECTION_SUSPECTED_FLAG = TRUE)
  AND (qSOFA_SCORE â‰¥ 2)
  WHERE qSOFA_SCORE = count of:
    - RESPIRATORY_RATE_TIER â‰¥ WARNING (RRâ‰¥22, defined in parameter file)
    - MENTAL_STATUS_ALTERED_FLAG = TRUE
    - SYSTOLIC_BP_TIER â‰¤ WARNING (SBPâ‰¤100, defined in parameter file)
  THEN trigger URGENT alert "SEPSIS_SUSPECTED"

Option B - SIRS-Based (fallback if mental status not assessable):
  IF (INFECTION_SUSPECTED_FLAG = TRUE)
  AND (SIRS_CRITERIA â‰¥ 2)
  WHERE SIRS_CRITERIA = count of:
    - TEMPERATURE_TIER = FEVER_HIGH OR HYPOTHERMIA
    - HEART_RATE_TIER â‰¥ WARNING
    - RESPIRATORY_RATE_TIER â‰¥ WARNING OR PaCO2_TIER = LOW
    - WBC_TIER = HIGH OR LOW OR BANDS_ELEVATED_FLAG
  THEN trigger URGENT alert "SEPSIS_SUSPECTED"

ESCALATION TO CRITICAL:
  IF (SEPSIS_SUSPECTED triggered)
  AND (SYSTOLIC_BP_TIER = CRITICAL OR HYPOTENSION_PERSISTENT_FLAG)
  THEN escalate to CRITICAL "SEPTIC_SHOCK_RISK"

VALIDATION_TARGETS:
  - Target Sensitivity: 70-80% for sepsis (per Sepsis-3 validation)
  - Target Specificity: 60-70% (trades specificity for early detection)
  - Target PPV: To be validated on Compass population
  - Note: These are TARGETS pending retrospective validation

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_SEPSIS_SUSPECTED
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_SEPSIS_CLINICIAN

IMPLEMENTATION_NOTES:
- Requires INFECTION_SUSPECTED_FLAG from clinical input or 
  ICD-10 infection codes or positive cultures
- If lactate available and LACTATE_TIER = CRITICAL, 
  escalate directly to CRITICAL tier
- Monitor false positive rate; adjust SIRS threshold to â‰¥3 
  if FPR >40%
```

---

### 2.2 Septic Shock Pattern

```
RULE_ID: SEPTIC_SHOCK
RULE_NAME: Septic Shock
TIER: CRITICAL
PRIORITY: 1 (HIGHEST)

PARAMETER_DEPENDENCIES:
  - SYSTOLIC_BP_TIER
  - MAP_TIER (mean arterial pressure)
  - LACTATE_TIER
  - All parameters from SEPSIS_SUSPECTED

TEMPORAL_DEPENDENCIES:
  - HYPOTENSION_PERSISTENT_FLAG (>30 min despite fluids)
  - BP_DROPPING_RAPIDLY_FLAG

CONTEXT_DEPENDENCIES:
  - BASELINE_BP_CONTEXT (for relative hypotension)

BOOLEAN_LOGIC:
  IF (SEPSIS_SUSPECTED = TRUE OR INFECTION_SUSPECTED_FLAG = TRUE)
  AND (
    (SYSTOLIC_BP_TIER = CRITICAL) OR
    (MAP_TIER = CRITICAL) OR
    (HYPOTENSION_PERSISTENT_FLAG = TRUE)
  )
  AND (LACTATE_TIER â‰¥ WARNING OR LACTATE_RISING_FLAG)
  THEN trigger CRITICAL "SEPTIC_SHOCK"

VALIDATION_TARGETS:
  - Target Sensitivity: >90% for septic shock
  - Target Specificity: >85%
  - Note: Septic shock has clearer definition, higher validation confidence

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_SEPTIC_SHOCK_911
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_SEPTIC_SHOCK_CLINICIAN
```

---

### 2.3 Diabetic Ketoacidosis (DKA) Pattern

**Clinical Background:**
Life-threatening complication of diabetes with hyperglycemia, ketosis, and metabolic acidosis. Special considerations for SGLT2 inhibitor users (euglycemic DKA).

**Evidence Base:**
- ADA Standards of Care 2024
- Kitabchi AE, et al. Diabetes Care 2009
- Gallo LA, et al. Diabetes Care 2019 (SGLT2i-associated DKA)

```
RULE_ID: DKA_PATTERN
RULE_NAME: Diabetic Ketoacidosis
TIER: CRITICAL
PRIORITY: 3

PARAMETER_DEPENDENCIES:
  - GLUCOSE_TIER (from PARAMETERS_GLUCOSE.md)
  - KETONES_TIER (from PARAMETERS_SPECIALIZED_LABS.md)
  - ANION_GAP_TIER (from PARAMETERS_ELECTROLYTES.md)
  - BICARBONATE_TIER (from PARAMETERS_ELECTROLYTES.md)
  - PH_TIER (from PARAMETERS_BLOOD_GAS.md, if available)

TEMPORAL_DEPENDENCIES:
  - GLUCOSE_RISING_RAPIDLY_FLAG (optional, increases suspicion)
  - KETONES_TREND_WORSENING_FLAG (optional)

CONTEXT_DEPENDENCIES:
  - DIABETES_TYPE1_FLAG
  - DIABETES_TYPE2_FLAG
  - SGLT2_INHIBITOR_FLAG (enables euglycemic variant)
  - PREGNANCY_FLAG (lowers threshold for concern)
  - INSULIN_PUMP_USER_FLAG

BOOLEAN_LOGIC:

Standard DKA:
  IF (GLUCOSE_TIER = SEVERE_HYPER) 
  AND (KETONES_TIER â‰¥ MODERATE)
  AND (
    (ANION_GAP_TIER = HIGH) OR
    (BICARBONATE_TIER = CRITICAL_LOW) OR
    (PH_TIER = ACIDOSIS)
  )
  THEN trigger CRITICAL "DKA_PATTERN"

Euglycemic DKA (SGLT2 inhibitor users):
  IF (SGLT2_INHIBITOR_FLAG = TRUE)
  AND (GLUCOSE_TIER â‰¥ WARNING) [Note: lower threshold]
  AND (KETONES_TIER = HIGH)
  AND (ANION_GAP_TIER = HIGH OR BICARBONATE_TIER = LOW)
  THEN trigger CRITICAL "DKA_EUGLYCEMIC_PATTERN"

Pregnancy-associated DKA:
  IF (PREGNANCY_FLAG = TRUE)
  AND (GLUCOSE_TIER â‰¥ WARNING) [Note: lower threshold]
  AND (KETONES_TIER â‰¥ MODERATE)
  AND acidosis criteria
  THEN trigger CRITICAL "DKA_PREGNANCY"

SEVERITY ESCALATION:
  IF (DKA triggered)
  AND (PH_TIER = SEVERE_ACIDOSIS OR BICARBONATE_TIER = PROFOUND_LOW)
  THEN add SEVERE_DKA flag with 911 guidance

VALIDATION_TARGETS:
  - Target Sensitivity: >95% for confirmed DKA
  - Target Specificity: >90%
  - Note: DKA has well-defined triad, high validation confidence

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_DKA_EMERGENCY
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_DKA_CLINICIAN

IMPLEMENTATION_NOTES:
- SGLT2i users: Always check ketones even with "normal" glucose
- Pregnancy: Very high risk, low threshold
- Type 1 > Type 2 risk, but don't exclude Type 2
```

---

### 2.4 Acute Coronary Syndrome (ACS) Pattern

**Clinical Background:**
STEMI and NSTEMI detection based on symptoms, troponin, and ECG changes.

**Evidence Base:**
- ACC/AHA STEMI Guidelines 2013 (updated 2015)
- AHA/ACC NSTEMI Guidelines 2014
- Thygesen K, et al. J Am Coll Cardiol 2018 (Fourth Universal Definition of MI)

```
RULE_ID: ACS_PATTERN
RULE_NAME: Acute Coronary Syndrome
TIER: CRITICAL
PRIORITY: 4

PARAMETER_DEPENDENCIES:
  - TROPONIN_TIER (from PARAMETERS_SPECIALIZED_LABS.md)
  - ECG_STEMI_FLAG (from PARAMETERS_ECG.md)
  - ECG_ISCHEMIA_FLAG (from PARAMETERS_ECG.md)
  - CHEST_PAIN_FLAG (from clinical input)

TEMPORAL_DEPENDENCIES:
  - TROPONIN_DELTA_FLAG (rise/fall pattern over 3-6 hours)
  - TROPONIN_RISING_RAPIDLY_FLAG
  - CHEST_PAIN_DURATION_FLAG

CONTEXT_DEPENDENCIES:
  - CKD_CHRONIC_TROPONIN_ELEVATION (adjusts baseline)
  - POST_CARDIAC_SURGERY_FLAG (adjusts interpretation)
  - BASELINE_TROPONIN_CONTEXT

BOOLEAN_LOGIC:

STEMI Pattern (highest priority):
  IF (CHEST_PAIN_CARDIAC_FLAG = TRUE)
  AND (ECG_STEMI_FLAG = TRUE)
  AND (TROPONIN_TIER â‰¥ WARNING OR TROPONIN_RISING_FLAG)
  THEN trigger CRITICAL "STEMI_PATTERN" with cath lab activation

ACS/NSTEMI Pattern:
  IF (CHEST_PAIN_CARDIAC_FLAG = TRUE)
  AND (TROPONIN_TIER â‰¥ ELEVATED)
  AND (
    (TROPONIN_DELTA_FLAG = SIGNIFICANT_RISE) OR
    (TROPONIN_TIER = CRITICAL)
  )
  AND (ECG_STEMI_FLAG = FALSE)
  THEN trigger CRITICAL "ACS_NSTEMI_PATTERN"

High-Risk Unstable Angina:
  IF (CHEST_PAIN_CARDIAC_FLAG = TRUE)
  AND (ECG_ISCHEMIA_FLAG = TRUE)
  AND (TROPONIN_TIER = BORDERLINE OR RISING)
  THEN trigger URGENT "UNSTABLE_ANGINA" [Note: URGENT, not CRITICAL]

VALIDATION_TARGETS:
  - Target Sensitivity: >90% for ACS when troponin available
  - Target Specificity: 80-85%
  - Note: Heavily dependent on troponin assay characteristics

PATIENT_MESSAGE_TEMPLATE: 
  - STEMI: ALERT_MSG_STEMI_911
  - NSTEMI: ALERT_MSG_ACS_ER_NOW
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_ACS_CLINICIAN

IMPLEMENTATION_NOTES:
- CKD patients: Focus on TROPONIN_DELTA_FLAG, not absolute value
- Troponin rise/fall pattern more specific than single value
- CHEST_PAIN_CARDIAC_FLAG requires symptom assessment quality
```

---

### 2.5 Severe Hypoglycemia Pattern

**Clinical Background:**
Dangerously low blood glucose requiring immediate treatment.

**Evidence Base:**
- ADA Standards of Care 2024
- Cryer PE. Diabetes Care 2013 (hypoglycemia classification)
- Seaquist ER, et al. Diabetes Care 2013 (severe hypoglycemia)

```
RULE_ID: SEVERE_HYPOGLYCEMIA
RULE_NAME: Severe Hypoglycemia
TIER: CRITICAL
PRIORITY: 5

PARAMETER_DEPENDENCIES:
  - GLUCOSE_TIER (from PARAMETERS_GLUCOSE.md)

TEMPORAL_DEPENDENCIES:
  - GLUCOSE_DROPPING_RAPIDLY_FLAG
  - HYPOGLYCEMIA_RECURRENT_FLAG (within 24 hours)

CONTEXT_DEPENDENCIES:
  - INSULIN_USER_FLAG
  - SULFONYLUREA_USER_FLAG
  - HYPOGLYCEMIA_UNAWARENESS_FLAG
  - ELDERLY_FLAG (>75 years)
  - CKD_STAGE_4_5_FLAG

BOOLEAN_LOGIC:

Severe Hypoglycemia (by definition):
  IF (GLUCOSE_TIER = SEVERE_HYPO)
  THEN trigger CRITICAL "SEVERE_HYPOGLYCEMIA"

Critical with Neurological Risk:
  IF (GLUCOSE_TIER = SEVERE_HYPO OR PROFOUND_HYPO)
  AND (
    (ALTERED_MENTAL_STATUS_FLAG = TRUE) OR
    (SEIZURE_FLAG = TRUE) OR
    (UNABLE_TO_SELF_TREAT_FLAG = TRUE)
  )
  THEN trigger CRITICAL "SEVERE_HYPOGLYCEMIA_NEURO" with 911 guidance

Recurrent Hypoglycemia (urgent medication adjustment):
  IF (HYPOGLYCEMIA_RECURRENT_FLAG = TRUE)
  AND (GLUCOSE_TIER â‰¥ MODERATE_HYPO)
  THEN trigger URGENT "RECURRENT_HYPOGLYCEMIA"

VALIDATION_TARGETS:
  - Sensitivity: 100% (by definition, threshold-based)
  - Specificity: 100% (clear glucose cutoff)
  - Note: Validation is about threshold accuracy, not pattern recognition

PATIENT_MESSAGE_TEMPLATE: 
  - ALERT_MSG_SEVERE_HYPO_TREAT_NOW
  - With neuro symptoms: ALERT_MSG_SEVERE_HYPO_911
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_SEVERE_HYPO_CLINICIAN

IMPLEMENTATION_NOTES:
- Home glucose values: Consider sensor vs fingerstick reliability
- CGM users: Confirm with fingerstick if possible
- Elderly: Lower threshold for intervention
```

---

### 2.6 Hypertensive Emergency Pattern

**Clinical Background:**
Severely elevated blood pressure with acute end-organ damage.

**Evidence Base:**
- AHA/ACC 2017 Hypertension Guidelines
- Whelton PK, et al. Hypertension 2018
- Van den Born BH, et al. Eur Heart J 2019

```
RULE_ID: HYPERTENSIVE_EMERGENCY
RULE_NAME: Hypertensive Emergency with End-Organ Damage
TIER: CRITICAL
PRIORITY: 6

PARAMETER_DEPENDENCIES:
  - SYSTOLIC_BP_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - DIASTOLIC_BP_TIER (from PARAMETERS_VITAL_SIGNS.md)
  - CREATININE_TIER (renal damage marker)
  - TROPONIN_TIER (cardiac damage marker)
  - BNP_TIER (heart failure marker)

TEMPORAL_DEPENDENCIES:
  - BP_RAPID_RISE_FLAG
  - CREATININE_DELTA_48H_FLAG (acute renal injury)

CONTEXT_DEPENDENCIES:
  - CHRONIC_HYPERTENSION_FLAG (adjusts baseline)
  - PREGNANCY_FLAG (preeclampsia pathway instead)
  - BASELINE_BP_CONTEXT

CLINICAL_INPUT_FLAGS:
  - SEVERE_HEADACHE_FLAG
  - VISUAL_CHANGES_FLAG
  - CHEST_PAIN_FLAG
  - ALTERED_MENTAL_STATUS_FLAG
  - DYSPNEA_SEVERE_FLAG

BOOLEAN_LOGIC:

Hypertensive Emergency:
  IF (SYSTOLIC_BP_TIER = HYPERTENSIVE_CRISIS)
  OR (DIASTOLIC_BP_TIER = HYPERTENSIVE_CRISIS)
  AND (ANY_END_ORGAN_DAMAGE = TRUE)
  
  WHERE ANY_END_ORGAN_DAMAGE includes:
    - SEVERE_HEADACHE_FLAG + VISUAL_CHANGES_FLAG (CNS)
    - CHEST_PAIN_FLAG + TROPONIN_TIER â‰¥ WARNING (cardiac)
    - CREATININE_DELTA_48H_FLAG = AKI (renal)
    - BNP_TIER = ACUTE_ELEVATION + DYSPNEA (heart failure)
    - ALTERED_MENTAL_STATUS_FLAG (encephalopathy)
  THEN trigger CRITICAL "HYPERTENSIVE_EMERGENCY"

Possible Stroke Pattern (highest priority):
  IF (SYSTOLIC_BP_TIER = HYPERTENSIVE_CRISIS)
  AND (SEVERE_HEADACHE_FLAG + VISUAL_CHANGES_FLAG)
  AND (NEUROLOGICAL_DEFICIT_FLAG OR ALTERED_MENTAL_STATUS_FLAG)
  THEN trigger CRITICAL "POSSIBLE_STROKE" (Priority 1-2)

Hypertensive Urgency (not in this document):
  [Deferred to RISK_WORKUP_RULES.md]

VALIDATION_TARGETS:
  - Target Sensitivity: 75-85% for true hypertensive emergency
  - Target Specificity: 70-80%
  - Note: Relies heavily on symptom reporting quality

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_HYPERTENSIVE_EMERGENCY
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_HTN_EMERGENCY_CLINICIAN
```

---

### 2.7 Preeclampsia / Eclampsia Pattern

**Clinical Background:**
Hypertensive disorder of pregnancy with systemic effects, can progress to seizures or HELLP syndrome.

**Evidence Base:**
- ACOG Practice Bulletin No. 222, 2020
- Hypertension in Pregnancy Guidelines
- Gestational Hypertension and Preeclampsia: ACOG Practice Bulletin 2019

```
RULE_ID: PREECLAMPSIA_PATTERN
RULE_NAME: Preeclampsia with or without Severe Features
TIER: CRITICAL
PRIORITY: 2 (second only to septic shock in pregnant patients)

PREREQUISITE:
  - PREGNANCY_FLAG = TRUE
  - GESTATIONAL_AGE â‰¥ 20 weeks

PARAMETER_DEPENDENCIES:
  - SYSTOLIC_BP_TIER (pregnancy-specific thresholds)
  - DIASTOLIC_BP_TIER (pregnancy-specific thresholds)
  - PROTEINURIA_TIER (from PARAMETERS_URINE.md)
  - PLATELETS_TIER
  - CREATININE_TIER
  - AST_TIER / ALT_TIER (liver enzymes)

TEMPORAL_DEPENDENCIES:
  - BP_PERSISTENT_ELEVATION_FLAG (4+ hours apart)
  - CREATININE_DOUBLING_FLAG
  - PLATELETS_DROPPING_FLAG

CONTEXT_DEPENDENCIES:
  - GESTATIONAL_AGE_CONTEXT
  - PREEXISTING_HYPERTENSION_FLAG
  - PRIOR_PREECLAMPSIA_FLAG

CLINICAL_INPUT_FLAGS:
  - SEVERE_HEADACHE_UNRESPONSIVE_FLAG
  - VISUAL_DISTURBANCE_FLAG
  - RIGHT_UPPER_QUADRANT_PAIN_FLAG
  - PULMONARY_EDEMA_FLAG

BOOLEAN_LOGIC:

Preeclampsia (without severe features):
  IF (PREGNANCY_FLAG = TRUE AND GESTATIONAL_AGE â‰¥ 20w)
  AND (BP_TIER = GESTATIONAL_HTN OR HIGHER)
  AND (BP_PERSISTENT_ELEVATION_FLAG = TRUE)
  AND (
    (PROTEINURIA_TIER â‰¥ SIGNIFICANT) OR
    (END_ORGAN_DYSFUNCTION = TRUE)
  )
  AND (NO_SEVERE_FEATURES = TRUE)
  THEN trigger CRITICAL "PREECLAMPSIA"

Preeclampsia with Severe Features:
  IF (PREECLAMPSIA criteria met)
  AND (ANY_SEVERE_FEATURE = TRUE)
  
  WHERE SEVERE_FEATURES include:
    - BP_TIER = SEVERE_GESTATIONAL_HTN
    - PLATELETS_TIER = CRITICAL_LOW
    - AST_OR_ALT_TIER = MARKEDLY_ELEVATED
    - CREATININE_TIER = HIGH OR CREATININE_DOUBLING_FLAG
    - PULMONARY_EDEMA_FLAG
    - SEVERE_HEADACHE_UNRESPONSIVE_FLAG
    - VISUAL_DISTURBANCE_FLAG
  THEN trigger CRITICAL "PREECLAMPSIA_SEVERE_FEATURES"

HELLP Syndrome:
  IF (PREGNANCY_FLAG = TRUE)
  AND (HEMOLYSIS_FLAG = TRUE) [LDH high, haptoglobin low, schistocytes]
  AND (AST_OR_ALT_TIER = MARKEDLY_ELEVATED)
  AND (PLATELETS_TIER = CRITICAL_LOW)
  THEN trigger CRITICAL "HELLP_SYNDROME"

Eclampsia:
  IF (PREECLAMPSIA present OR suspected)
  AND (SEIZURE_FLAG = TRUE)
  THEN trigger CRITICAL "ECLAMPSIA" (Priority 1 - highest)

VALIDATION_TARGETS:
  - Target Sensitivity: >90% for preeclampsia
  - Target Specificity: 80-85%
  - Note: ACOG criteria well-validated

PATIENT_MESSAGE_TEMPLATE: 
  - ALERT_MSG_PREECLAMPSIA_LABOR_DELIVERY
  - Severe features: ALERT_MSG_PREECLAMPSIA_SEVERE_NOW
  - HELLP: ALERT_MSG_HELLP_911
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_PREECLAMPSIA_CLINICIAN
```

---

## SECTION 3: URGENT TIER PATTERNS

### 3.1 Acute Kidney Injury (AKI) Pattern

**Clinical Background:**
Rapid decline in kidney function requiring same-day evaluation to prevent progression.

**Evidence Base:**
- KDIGO AKI Guidelines 2012

```
RULE_ID: AKI_PATTERN
RULE_NAME: Acute Kidney Injury
TIER: URGENT (escalates to CRITICAL if severe)
PRIORITY: 7

PARAMETER_DEPENDENCIES:
  - CREATININE_TIER

TEMPORAL_DEPENDENCIES:
  - CREATININE_DELTA_48H_FLAG (from TEMPORAL_SCORING.md)
  - CREATININE_DELTA_7D_FLAG
  - URINE_OUTPUT_6H_FLAG (if monitored)
  - URINE_OUTPUT_12H_FLAG (if monitored)

CONTEXT_DEPENDENCIES:
  - CKD_BASELINE_CREATININE
  - NEPHROTOXIC_MEDICATION_FLAG
  - RECENT_CONTRAST_EXPOSURE_FLAG

BOOLEAN_LOGIC:

AKI Stage 1:
  IF (CREATININE_DELTA_48H_FLAG = AKI_STAGE1)
  OR (CREATININE_DELTA_7D_FLAG = AKI_STAGE1)
  OR (URINE_OUTPUT_6H_FLAG = OLIGURIA)
  THEN trigger URGENT "AKI_STAGE1"

AKI Stage 2:
  IF (CREATININE_DELTA_48H_FLAG = AKI_STAGE2)
  OR (CREATININE_DELTA_7D_FLAG = AKI_STAGE2)
  OR (URINE_OUTPUT_12H_FLAG = SEVERE_OLIGURIA)
  THEN trigger URGENT "AKI_STAGE2"

AKI Stage 3 (escalate to CRITICAL):
  IF (CREATININE_DELTA_FLAG = AKI_STAGE3)
  OR (CREATININE_TIER = CRITICAL_ABSOLUTE)
  OR (URINE_OUTPUT_FLAG = ANURIA)
  THEN trigger CRITICAL "AKI_STAGE3"

VALIDATION_TARGETS:
  - Target Sensitivity: >85% for AKI
  - Target Specificity: 75-80%

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_AKI_CONTACT_TODAY
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_AKI_CLINICIAN

IMPLEMENTATION_NOTES:
- Requires time-stamped creatinine values
- TEMPORAL_SCORING.md handles the 48h/7d calculations
- All numeric thresholds defined in PARAMETERS_RENAL.md
```

---

### 3.2 Acute Heart Failure Decompensation

```
RULE_ID: ACUTE_HEART_FAILURE
RULE_NAME: Acute Heart Failure Decompensation
TIER: URGENT (escalates to CRITICAL if severe)
PRIORITY: 8

PARAMETER_DEPENDENCIES:
  - BNP_TIER or NT_PROBNP_TIER
  - OXYGEN_SATURATION_TIER
  - SYSTOLIC_BP_TIER

TEMPORAL_DEPENDENCIES:
  - BNP_RISING_FLAG
  - WEIGHT_GAIN_3D_FLAG
  - OXYGEN_SAT_DROPPING_FLAG

CONTEXT_DEPENDENCIES:
  - CHRONIC_HF_FLAG (adjusts BNP baseline)
  - AGE_CONTEXT (adjusts BNP thresholds)
  - OBESITY_FLAG (lowers BNP threshold)

CLINICAL_INPUT_FLAGS:
  - DYSPNEA_AT_REST_FLAG
  - ORTHOPNEA_FLAG
  - PND_FLAG (paroxysmal nocturnal dyspnea)
  - LOWER_EXTREMITY_EDEMA_FLAG

BOOLEAN_LOGIC:

Acute Heart Failure:
  IF (BNP_TIER = ACUTE_ELEVATION OR NT_PROBNP_TIER = ACUTE_ELEVATION)
  AND (ANY_HF_SYMPTOM = TRUE)
  AND (NO_SEVERE_FEATURES)
  THEN trigger URGENT "ACUTE_HEART_FAILURE"

Severe Heart Failure (escalate to CRITICAL):
  IF (ACUTE_HEART_FAILURE triggered)
  AND (ANY_SEVERE_FEATURE = TRUE)
  
  WHERE SEVERE_FEATURES include:
    - OXYGEN_SATURATION_TIER = CRITICAL
    - SYSTOLIC_BP_TIER = CRITICAL_LOW
    - ALTERED_MENTAL_STATUS_FLAG
    - RESPIRATORY_DISTRESS_FLAG
  THEN trigger CRITICAL "SEVERE_HEART_FAILURE"

VALIDATION_TARGETS:
  - Target Sensitivity: 80-85% for acute HF
  - Target Specificity: 70-75%
  - Note: BNP has many non-HF causes

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_HF_CONTACT_TODAY
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_HF_CLINICIAN
```

---

### 3.3 Acute Liver Injury / Failure

```
RULE_ID: ACUTE_LIVER_INJURY
RULE_NAME: Acute Liver Injury or Failure
TIER: URGENT (escalates to CRITICAL if liver failure)
PRIORITY: 9

PARAMETER_DEPENDENCIES:
  - ALT_TIER
  - AST_TIER
  - ALKALINE_PHOSPHATASE_TIER
  - BILIRUBIN_TIER
  - INR_TIER
  - ALBUMIN_TIER

TEMPORAL_DEPENDENCIES:
  - LIVER_ENZYMES_RISING_FLAG
  - INR_RISING_FLAG

CONTEXT_DEPENDENCIES:
  - CHRONIC_LIVER_DISEASE_FLAG
  - MEDICATION_LIVER_TOXIC_FLAG
  - ACETAMINOPHEN_OVERDOSE_FLAG

CLINICAL_INPUT_FLAGS:
  - JAUNDICE_FLAG
  - CONFUSION_FLAG (encephalopathy)
  - ASTERIXIS_FLAG

BOOLEAN_LOGIC:

Acute Liver Injury:
  IF (ALT_TIER = MARKEDLY_ELEVATED OR AST_TIER = MARKEDLY_ELEVATED)
  OR (BILIRUBIN_TIER = HIGH)
  AND (NO_LIVER_FAILURE_FEATURES)
  THEN trigger URGENT "ACUTE_LIVER_INJURY"

Acute Liver Failure (escalate to CRITICAL):
  IF (ACUTE_LIVER_INJURY triggered)
  AND (ANY_FAILURE_FEATURE = TRUE)
  
  WHERE FAILURE_FEATURES include:
    - INR_TIER = MARKEDLY_ELEVATED (without anticoagulation)
    - ALBUMIN_TIER = CRITICAL_LOW (acute drop)
    - CONFUSION_FLAG OR ASTERIXIS_FLAG (encephalopathy)
  THEN trigger CRITICAL "ACUTE_LIVER_FAILURE"

VALIDATION_TARGETS:
  - Target Sensitivity: >90% for significant liver injury
  - Target Specificity: 80-85%

PATIENT_MESSAGE_TEMPLATE: ALERT_MSG_LIVER_INJURY_TODAY
CLINICIAN_MESSAGE_TEMPLATE: ALERT_MSG_LIVER_CLINICIAN
```

---

## SECTION 4: RULE VALIDATION & GOVERNANCE

### 4.1 Pre-Deployment Validation Requirements

**Every clinical decision rule must complete:**

1. **Clinical Literature Review**
   - Evidence base documented with citations
   - Guideline alignment confirmed
   - Published algorithm validation data reviewed
   - Target sensitivity/specificity identified

2. **Retrospective Testing**
   - Test against â‰¥100 confirmed cases
   - Test against â‰¥1000 negative controls
   - Calculate actual sensitivity, specificity, PPV, NPV
   - Compare to target values
   - Identify failure modes

3. **Clinical Expert Review**
   - Multidisciplinary committee review
   - Specialty-specific sign-off (cardiology for ACS, OB for preeclampsia, etc.)
   - Consensus on final logic
   - Approval of patient/clinician messages

4. **Simulation Testing**
   - Run through 50+ clinical scenarios
   - Test edge cases (missing data, borderline values)
   - Confirm alert prioritization
   - Validate escalation logic

### 4.2 Post-Deployment Monitoring

**Continuous quality improvement metrics:**

1. **Weekly Monitoring (first 3 months)**
   - Rules triggered per week
   - True positive rate (chart review)
   - False positive rate
   - Response time metrics
   - Patient outcomes

2. **Monthly Review (ongoing)**
   - Aggregate performance metrics
   - Failure case analysis
   - User feedback compilation
   - Threshold drift assessment

3. **Quarterly Comprehensive Review**
   - Compare actual vs target sensitivity/specificity
   - Analyze false negatives (missed cases)
   - Review rule interactions
   - Update evidence base
   - Propose rule modifications

4. **Annual External Audit**
   - Independent clinical expert review
   - Comparison to updated guidelines
   - Population-level outcome analysis
   - Major version updates

### 4.3 Rule Modification Process

**When a rule needs updating:**

1. **Trigger Identification**
   - New clinical evidence
   - Unacceptable false positive rate (>30% for CRITICAL)
   - Missed cases (false negatives)
   - Guideline updates
   - Parameter threshold changes

2. **Change Proposal**
   - Document specific changes
   - Cite rationale and evidence
   - Predict impact on sensitivity/specificity
   - Model effect on alert volume

3. **Clinical Committee Approval**
   - Present to multidisciplinary committee
   - Require consensus approval
   - Patient safety officer sign-off
   - Document decision

4. **A/B Testing (if feasible)**
   - Run old and new rule in parallel
   - Compare performance over 30-90 days
   - Select better performer
   - Document results

5. **Deployment & Monitoring**
   - Deploy new rule version
   - Intensive monitoring first 30 days
   - Return to standard monitoring
   - Document version change

### 4.4 Sensitivity/Specificity Updates

**All validation targets must be updated after retrospective testing:**

```
BEFORE retrospective validation:
  VALIDATION_TARGETS:
    - Target Sensitivity: ~85% (from literature)
    - Target Specificity: ~75% (from literature)
    - Status: TARGETS PENDING VALIDATION

AFTER retrospective validation:
  VALIDATION_RESULTS:
    - Achieved Sensitivity: 82% (CI: 76-88%)
    - Achieved Specificity: 71% (CI: 68-74%)
    - PPV: 45% (population-specific)
    - NPV: 94% (population-specific)
    - Status: VALIDATED on Compass data as of [date]
    - Cases reviewed: 150 positive, 1200 negative
    - Next validation: [date]
```

---

## SECTION 5: IMPLEMENTATION CHECKLIST

**For IT Team:**

**Core Infrastructure:**
- [ ] Build parameter severity tier reference system
- [ ] Integrate with PARAMETERS_*.md tier definitions
- [ ] Build temporal flag reference system
- [ ] Integrate with TEMPORAL_SCORING.md calculations
- [ ] Build context flag reference system
- [ ] Integrate with CONTEXT_RULES.md logic
- [ ] Create Boolean logic evaluation engine (AND, OR, NOT)
- [ ] Implement rule priority ordering
- [ ] Build escalation logic (URGENT â†’ CRITICAL)

**Individual Rules (CRITICAL):**
- [ ] Implement SEPSIS_SUSPECTED
- [ ] Implement SEPTIC_SHOCK
- [ ] Implement DKA_PATTERN (+ euglycemic variant)
- [ ] Implement ACS_PATTERN (STEMI + NSTEMI)
- [ ] Implement SEVERE_HYPOGLYCEMIA
- [ ] Implement HYPERTENSIVE_EMERGENCY
- [ ] Implement PREECLAMPSIA_PATTERN (+ HELLP + Eclampsia)

**Individual Rules (URGENT):**
- [ ] Implement AKI_PATTERN (stages 1-3)
- [ ] Implement ACUTE_HEART_FAILURE
- [ ] Implement ACUTE_LIVER_INJURY

**Alert Display:**
- [ ] Link to ALERT_MESSAGES.md for all message text
- [ ] Implement patient message display
- [ ] Implement clinician message display
- [ ] Create emergency guidance workflows (911, ED, call provider)

**Validation Infrastructure:**
- [ ] Build retrospective testing framework
- [ ] Create alert metrics dashboard
- [ ] Implement outcome tracking
- [ ] Build rule modification workflow
- [ ] Create A/B testing capability

**Testing:**
- [ ] Unit test each rule logic
- [ ] Test rule combinations (simultaneous triggers)
- [ ] Test priority ordering
- [ ] Test escalation logic
- [ ] Validate against 50+ clinical scenarios
- [ ] Test with missing data
- [ ] Test with borderline values

**For Clinical Team:**

**Pre-Deployment:**
- [ ] Validate all rule logic against current guidelines
- [ ] Approve all parameter severity tier definitions (in PARAMETERS_*.md)
- [ ] Approve all temporal flag logic (in TEMPORAL_SCORING.md)
- [ ] Approve all context rules (in CONTEXT_RULES.md)
- [ ] Review and approve all patient messages
- [ ] Review and approve all clinician messages
- [ ] Conduct retrospective validation (100+ cases per rule)
- [ ] Update validation targets with actual performance
- [ ] Final sign-off by clinical committee

**Post-Deployment:**
- [ ] Review alert metrics weekly (first 3 months)
- [ ] Chart review all CRITICAL alerts
- [ ] Collect clinician feedback
- [ ] Track patient outcomes
- [ ] Monthly performance review
- [ ] Quarterly comprehensive review
- [ ] Annual external audit
- [ ] Update rules based on new evidence

---

## APPENDIX A: TIER FLAG NAMING CONVENTIONS

### Parameter Severity Tiers

**Defined in PARAMETERS_*.md files:**

```
[PARAMETER]_TIER values:
- NORMAL
- MONITOR (borderline, watch closely)
- WARNING (attention needed, not urgent)
- URGENT (same-day evaluation)
- CRITICAL (immediate action)

May also have parameter-specific tiers:
- GLUCOSE_TIER: SEVERE_HYPO, MODERATE_HYPO, NORMAL, ELEVATED, SEVERE_HYPER
- BP_TIER: HYPOTENSIVE, NORMAL, ELEVATED, HYPERTENSIVE, HYPERTENSIVE_CRISIS
- POTASSIUM_TIER: CRITICAL_LOW, LOW, NORMAL, HIGH, CRITICAL_HIGH
```

### Temporal Flags

**Defined in TEMPORAL_SCORING.md:**

```
[PARAMETER]_DELTA_[TIMEWINDOW]_FLAG:
- CREATININE_DELTA_48H_FLAG: NO_CHANGE, RISING, AKI_STAGE1, AKI_STAGE2, AKI_STAGE3
- TROPONIN_DELTA_FLAG: STABLE, RISING, FALLING, SIGNIFICANT_RISE
- WEIGHT_GAIN_3D_FLAG: NORMAL, CONCERNING, SIGNIFICANT
- HGB_DROP_3M_FLAG: STABLE, MILD_DROP, SIGNIFICANT_DROP

[PARAMETER]_TREND_[PATTERN]_FLAG:
- GLUCOSE_TREND_FLAG: STABLE, IMPROVING, WORSENING
- BP_TREND_FLAG: STABLE, TRENDING_UP, TRENDING_DOWN

[PARAMETER]_VELOCITY_[SPEED]_FLAG:
- GLUCOSE_VELOCITY_FLAG: NORMAL, DROPPING_FAST, RISING_FAST
- BP_VELOCITY_FLAG: STABLE, RISING_RAPIDLY
```

### Context Flags

**Defined in CONTEXT_RULES.md:**

```
Clinical context flags:
- PREGNANCY_FLAG: TRUE/FALSE
- DIABETES_TYPE1_FLAG: TRUE/FALSE
- CKD_STAGE_4_5_FLAG: TRUE/FALSE
- IMMUNOSUPPRESSION_FLAG: TRUE/FALSE
- SGLT2_INHIBITOR_FLAG: TRUE/FALSE

Baseline context:
- BASELINE_BP_CONTEXT: adjusts what counts as "hypotension"
- BASELINE_TROPONIN_CONTEXT: CKD patients' chronic elevation
- CHRONIC_HF_FLAG: adjusts BNP interpretation
```

---

## APPENDIX B: DEFERRED PATTERNS (NOT IN V1.0)

**The following patterns are clinically important but NOT safety-critical:**

Deferred to **RISK_WORKUP_RULES.md** (separate document):
- Concerning anemia patterns (workup needed)
- Thyroid dysfunction (non-emergent)
- Hypertensive urgency (no end-organ damage)
- Chronic heart failure stable worsening
- Mild AKI (Stage 1 without risk factors)
- Electrolyte abnormalities (non-critical ranges)
- Metabolic syndrome detection
- Osteoporosis risk patterns

These will use the same architecture but require less rigorous validation since they're not life-threatening.

---

## APPENDIX C: DIFFERENCES FROM DRAFT VERSION

**Major improvements in v1.0:**

1. **Eliminated all numeric thresholds**
   - Now references parameter severity tiers only
   - Single source of truth in PARAMETERS_*.md

2. **Wired in temporal layer**
   - Uses explicit temporal flags from TEMPORAL_SCORING.md
   - No inline temporal calculations

3. **Wired in context layer**
   - Uses explicit context flags from CONTEXT_RULES.md
   - No inline context logic

4. **Fixed sepsis logic**
   - Added SEPSIS_SUSPECTED (early detection, URGENT)
   - Separated SEPTIC_SHOCK (late presentation, CRITICAL)
   - Uses qSOFA + SIRS appropriately

5. **Narrowed scope to safety-critical**
   - Removed WARNING-tier patterns
   - Deferred to RISK_WORKUP_RULES.md

6. **Downgraded sensitivity/specificity to targets**
   - Clear language: "Target (pending validation)"
   - Process for updating after retrospective testing

7. **Added SGLT2i euglycemic DKA variant**
   - Separate logic path for SGLT2 inhibitor users
   - Lower glucose threshold

8. **Improved governance**
   - Explicit pre-deployment validation requirements
   - Post-deployment monitoring metrics
   - Rule modification process

---

**END OF CLINICAL_DECISION_RULES_v1.0.md**

*This specification provides complete multi-parameter clinical decision rule logic for safety-critical alerts. All numeric thresholds defined in PARAMETERS_*.md. All temporal calculations defined in TEMPORAL_SCORING.md. All context logic defined in CONTEXT_RULES.md. Clinical committee approval and retrospective validation required before deployment.*
