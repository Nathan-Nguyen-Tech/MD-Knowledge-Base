# AI-FILLABLE SMART CARD TEMPLATES

> **12 Templates** (one per Tier 2 card type) with `[PLACEHOLDER]` fields for AI auto-generation.

## How It Works
1. Provide **SEED INPUT** (e.g., drug name, test name)
2. AI fills all `[BRACKETS]` using clinical knowledge
3. Human reviews for accuracy
4. `[PATIENT:]` fields filled during encounter

---

# TEMPLATE 1: MEDICATIONS 💊

## Seed Input
```
Drug: [DRUG_NAME]
Dose: [DOSE]
Route: [ROUTE]
Frequency: [FREQUENCY]
Indication: [INDICATION]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
Take [DRUG_NAME] [DOSE] [FREQUENCY_PLAIN_ENGLISH] to [SIMPLE_BENEFIT].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This medication [HOW_IT_HELPS_SIMPLY].

### HOW TO DO IT
- [TIMING_AND_FOOD_INSTRUCTION]
- [HOW_TO_TAKE]
- [MISSED_DOSE_INSTRUCTION]

### WHEN TO DO IT
[FREQUENCY_PLAIN_ENGLISH] | You may notice [PRIMARY_BENEFIT] in [TIME_TO_BENEFIT].

### WHAT TO WATCH FOR
- [RED_FLAG_1]
- [RED_FLAG_2]
- [RED_FLAG_3]

---

## Full Clinical View

### WHAT
- **Card Name**: [DRUG_NAME] [DOSE] [ROUTE] [FREQUENCY]
- **Brand Name(s)**: [BRAND_NAMES]
- **Drug Class**: [DRUG_CLASS]
- **Mechanism**: [MECHANISM_OF_ACTION]

### WHO
- **Primary Actor**: Patient
- **Prescriber**: [PATIENT: prescribing clinician]
- **Special Populations**:
  - Geriatric: [GERIATRIC_CONSIDERATIONS]
  - Renal Impairment: [RENAL_ADJUSTMENT]
  - Hepatic Impairment: [HEPATIC_ADJUSTMENT]
  - Pregnancy: [PREGNANCY_CATEGORY_AND_GUIDANCE]
  - Breastfeeding: [LACTATION_GUIDANCE]

### WHEN
- **Frequency**: [FREQUENCY]
- **Best Time**: [OPTIMAL_TIMING]
- **With Food**: [FOOD_REQUIREMENTS]
- **Duration**: [DURATION]
- **Missed Dose**: [MISSED_DOSE_INSTRUCTIONS]

### WHERE
- **Setting**: Home
- **Storage**: [STORAGE_REQUIREMENTS]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION_VERB] [DOMAIN]
- **Patient Goal**: [PATIENT: stated goal]
- **Evidence**: [GUIDELINE_SOURCE] | Grade [EVIDENCE_GRADE] | [KEY_FINDING]
- **Time-to-Benefit**: [EXPECTED_TIMELINE]

### HOW
- **Administration**: [DETAILED_ADMINISTRATION_INSTRUCTIONS]
- **Special Instructions**: [CRUSHING_SPLITTING_MIXING_IF_APPLICABLE]

### MEASURE
- **Primary Metric**: [WHAT_TO_TRACK]
- **Frequency**: [HOW_OFTEN_TO_MEASURE]
- **Tool**: [DEVICE_OR_METHOD]

### TARGET
- **Goal**: [SPECIFIC_TARGET_VALUE]
- **Timeline**: [WHEN_TO_ACHIEVE]

### SAFETY
- **Black Box Warning**: [IF_APPLICABLE]
- **Common Side Effects** (Yellow):
  - [SIDE_EFFECT_1_WITH_PERCENT]
  - [SIDE_EFFECT_2_WITH_PERCENT]
  - [SIDE_EFFECT_3_WITH_PERCENT]
- **Stop & Call** (Orange):
  - [WARNING_SIGN_BY_SYSTEM_1]
  - [WARNING_SIGN_BY_SYSTEM_2]
- **Emergency 911** (Red): [LIFE_THREATENING_REACTIONS]
- **Contraindications**: [ABSOLUTE_AND_RELATIVE]
- **Major Interactions**: [TOP_DRUG_INTERACTIONS]

### FOLLOW-UP
- **Lab Monitoring**: [LABS_AND_TIMING]
- **Visit Schedule**: [FOLLOW_UP_TIMING]
- **Titration**: [IF_APPLICABLE]

### NOTES
- **Evidence Grade**: [A_B_C]
- **Cost**: [COST_TIER_AND_GENERIC_AVAILABILITY]
- **Alternatives**: [THERAPEUTIC_ALTERNATIVES]

---

## Metadata
- **Card ID**: MED-[CLASS_ABBREV]-[NUMBER]
- **Tier Path**: Medical > Medications > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 2: DIAGNOSTIC TESTING 🔬

## Seed Input
```
Test: [TEST_NAME]
Type: [laboratory | home_monitoring]
Indication: [INDICATION]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[IF_LAB]: Get a [TEST_NAME] to check [WHAT_BEING_MEASURED_SIMPLY].
[IF_HOME]: Check your [TEST_NAME] at home to track [WHAT_BEING_MEASURED_SIMPLY].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This test helps [HOW_RESULTS_GUIDE_CARE].

### HOW TO DO IT
- [PREPARATION_OR_TECHNIQUE_STEP_1]
- [WHAT_TO_EXPECT_OR_WHEN_TO_MEASURE]
- [HOW_LONG_OR_HOW_TO_RECORD]

### WHEN TO DO IT
[TIMING_REQUIREMENTS] | Results ready in [TURNAROUND_TIME].

### WHAT TO WATCH FOR
- [POST_COLLECTION_CONCERN_OR_THRESHOLD_TO_REPORT]

---

## Full Clinical View

### WHAT
- **Card Name**: [TEST_NAME]
- **Type**: [laboratory | home_monitoring]
- **CPT Code**: [CPT_CODE_IF_LAB]
- **LOINC Code**: [LOINC_CODE_IF_LAB]
- **Components**: [IF_PANEL_LIST_TESTS]

### WHO
- **Primary Actor**: [Lab tech | Patient]
- **Ordering Provider**: [PATIENT: ordering clinician]

### WHEN
- **Frequency**: [HOW_OFTEN]
- **Timing**: [FASTING_OR_SPECIFIC_TIMING]
- **Repeat Criteria**: [WHEN_TO_RECHECK]

### WHERE
- **Location**: [LAB_LOCATIONS | Home]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Indications**: [WHEN_APPROPRIATE]
- **Evidence**: [USPSTF_GRADE_IF_SCREENING]

### HOW
- **Preparation**:
  - Fasting: [YES_NO_DURATION]
  - Meds to Hold: [LIST_IF_ANY]
- **Collection/Technique**: [METHOD_DETAILS]

### MEASURE
| Component | Normal Range | Units | Critical Low | Critical High |
|-----------|--------------|-------|--------------|---------------|
| [COMPONENT_1] | [RANGE] | [UNITS] | [CRIT_LOW] | [CRIT_HIGH] |
| [COMPONENT_2] | [RANGE] | [UNITS] | [CRIT_LOW] | [CRIT_HIGH] |

### TARGET
- **Goal**: [TARGET_VALUE_BASED_ON_CONDITION]

### SAFETY
- **Critical Values**: [VALUES_REQUIRING_IMMEDIATE_CALL]
- **Preparation Risks**: [FASTING_IN_DIABETICS_ETC]

### FOLLOW-UP
- **Results Timeline**: [WHEN_AVAILABLE]
- **Next Steps**: [ACTION_BASED_ON_RESULTS]

### NOTES
- **Interfering Factors**: [DRUGS_CONDITIONS_AFFECTING_RESULTS]
- **Cost**: [TYPICAL_COST_COVERAGE]

---

## Metadata
- **Card ID**: DIAG-[CATEGORY]-[NUMBER]
- **Tier Path**: Medical > Diagnostic Testing > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 3: IMAGING STUDIES 🏥

## Seed Input
```
Study: [STUDY_NAME]
Modality: [xray | ct | mri | ultrasound | nuclear]
Body Region: [BODY_REGION]
Contrast: [yes | no]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
Get a [STUDY_NAME] to [SIMPLE_PURPOSE].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This imaging helps us see [WHAT_LOOKING_FOR].

### HOW TO DO IT
- [PREPARATION_STEP]
- [WHAT_TO_WEAR_BRING]
- [WHAT_HAPPENS_DURING]
- [HOW_LONG]

### WHEN TO DO IT
Schedule within [URGENCY_TIMEFRAME] | Results in [TURNAROUND].

### WHAT TO WATCH FOR
- [CONTRAST_REACTION_SIGNS_IF_APPLICABLE]
- [POST_PROCEDURE_CONCERN]

---

## Full Clinical View

### WHAT
- **Card Name**: [STUDY_NAME]
- **Modality**: [MODALITY]
- **Body Region**: [BODY_REGION]
- **CPT Code**: [CPT_CODE]
- **Contrast**: [YES_NO_TYPE]

### WHO
- **Primary Actor**: Radiologist/Technologist
- **Ordering Provider**: [PATIENT: ordering clinician]

### WHEN
- **Indication**: [WHEN_APPROPRIATE_ACR_CRITERIA]
- **Frequency**: [HOW_OFTEN_CAN_REPEAT]

### WHERE
- **Setting**: [HOSPITAL_IMAGING_CENTER_CLINIC]
- **Duration**: [APPOINTMENT_LENGTH]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **ACR Appropriateness**: [RATING]

### HOW
- **Preparation**:
  - Fasting: [IF_REQUIRED]
  - Contrast Prep: [ALLERGY_SCREENING_EGFR_METFORMIN]
  - Pregnancy Screening: [IF_RADIATION]
  - Metal Screening: [IF_MRI]
  - Claustrophobia Options: [IF_MRI]
- **Post-Procedure**: [RECOVERY_ACTIVITY_RESUMPTION]

### MEASURE
- **Findings Assessed**: [WHAT_RADIOLOGIST_EVALUATES]

### TARGET
- **Normal Finding**: [WHAT_CONSTITUTES_NORMAL]
- **Actionable Finding**: [WHAT_TRIGGERS_INTERVENTION]

### SAFETY
- **Radiation Dose**: [MSV_IF_APPLICABLE]
- **Contrast Risks**: [ALLERGIC_CIN_NSF]
- **Contraindications**: [ABSOLUTE_RELATIVE]

### FOLLOW-UP
- **Results Communication**: [HOW_WHEN]
- **Next Steps**: [BASED_ON_FINDINGS]

### NOTES
- **Alternatives**: [IF_CONTRAINDICATED]
- **Cost**: [RANGE_PRIOR_AUTH]

---

## Metadata
- **Card ID**: IMG-[MODALITY]-[NUMBER]
- **Tier Path**: Medical > Imaging Studies > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 4: PROCEDURES 🔧

## Seed Input
```
Procedure: [PROCEDURE_NAME]
Type: [diagnostic | therapeutic | surgical | preventive]
Setting: [office | outpatient | hospital]
Anesthesia: [none | local | sedation | general]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
Have a [PROCEDURE_NAME] to [SIMPLE_PURPOSE].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This procedure [WHAT_IT_ACCOMPLISHES].

### HOW TO DO IT
- [PRE_PROCEDURE_PREPARATION]
- [WHAT_TO_ARRANGE]
- [WHAT_HAPPENS_DURING]
- [RECOVERY_EXPECTATIONS]

### WHEN TO DO IT
Schedule within [TIMEFRAME] | Recovery takes [DURATION].

### WHAT TO WATCH FOR
- [POST_PROCEDURE_WARNING_1]
- [POST_PROCEDURE_WARNING_2]
- [WHEN_TO_CALL_VS_ER]

---

## Full Clinical View

### WHAT
- **Card Name**: [PROCEDURE_NAME]
- **CPT Code**: [CPT_CODE]
- **Type**: [TYPE]
- **Setting**: [SETTING]
- **Anesthesia**: [ANESTHESIA]

### WHO
- **Performing Provider**: [SPECIALIST_TYPE]
- **Patient Role**: Consent, prep compliance, recovery

### WHEN
- **Indications**: [WHEN_RECOMMENDED]
- **Timing**: [URGENT_VS_ELECTIVE]

### WHERE
- **Setting**: [SETTING]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Evidence**: [GUIDELINE_SUCCESS_RATE]

### HOW
- **Pre-Procedure**:
  - Labs Required: [LIST]
  - Meds to Hold: [ANTICOAGULANTS_ETC_WITH_TIMING]
  - NPO Status: [FASTING_REQUIREMENTS]
  - Bowel Prep: [IF_APPLICABLE]
- **Post-Procedure**:
  - Activity Restrictions: [DURATION_TYPE]
  - Diet: [PROGRESSION]
  - Wound Care: [IF_APPLICABLE]
  - Pain Management: [EXPECTED_AND_MANAGEMENT]

### MEASURE
- **Success Metrics**: [HOW_TO_KNOW_ACHIEVED_GOAL]

### TARGET
- **Expected Outcome**: [WHAT_SUCCESS_LOOKS_LIKE]
- **Timeline**: [WHEN_BENEFITS_REALIZED]

### SAFETY
- **Procedure Risks**: [RISKS_WITH_INCIDENCE]
- **Post-Procedure Complications**:
  - Expected: [LIST]
  - Call Office: [LIST]
  - Emergency: [LIST]
- **Contraindications**: [WHO_SHOULD_NOT_HAVE]

### FOLLOW-UP
- **Post-Procedure Visits**: [SCHEDULE]
- **Results Discussion**: [WHEN_HOW]

### NOTES
- **Alternatives**: [OTHER_OPTIONS]
- **Cost**: [RANGE_INSURANCE]

---

## Metadata
- **Card ID**: PROC-[SPECIALTY]-[NUMBER]
- **Tier Path**: Medical > Procedures > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 5: DURABLE MEDICAL EQUIPMENT 🩺

## Seed Input
```
Device: [DEVICE_NAME]
Category: [respiratory | mobility | sensory | chronic_disease]
Settings: [DEVICE_SETTINGS]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
Use your [DEVICE_NAME] [FREQUENCY] to [SIMPLE_BENEFIT].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This device [HOW_IT_HELPS].

### HOW TO DO IT
- [SETUP_STEP]
- [PROPER_USE_TECHNIQUE]
- [CLEANING_MAINTENANCE]
- [TROUBLESHOOTING_TIP]

### WHEN TO DO IT
[DAILY_SCHEDULE] | You should notice [BENEFIT] within [TIMEFRAME].

### WHAT TO WATCH FOR
- [DEVICE_NOT_WORKING_SIGN]
- [SYMPTOM_TO_REPORT]

---

## Full Clinical View

### WHAT
- **Card Name**: [DEVICE_NAME]
- **Category**: [CATEGORY]
- **Settings**: [DEVICE_SETTINGS]
- **HCPCS Code**: [HCPCS_CODE]

### WHO
- **Primary Actor**: Patient
- **Prescriber**: [PATIENT: prescribing clinician]
- **Supplier**: [DME_COMPANY]
- **Trainer**: [RT_PT_SPECIALIST]

### WHEN
- **Frequency**: [HOW_OFTEN]
- **Duration**: [HOURS_PER_DAY]
- **Schedule**: [SPECIFIC_TIMES]

### WHERE
- **Setting**: Home
- **Travel**: [PORTABLE_OPTIONS_CONSIDERATIONS]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Evidence**: [GUIDELINE]
- **Expected Benefit**: [IMPROVEMENT_TO_EXPECT]

### HOW
- **Setup**: [INITIAL_SETUP]
- **Daily Use**: [STEP_BY_STEP]
- **Cleaning**: [SCHEDULE_METHOD]
- **Troubleshooting**: [COMMON_ISSUES_FIXES]

### MEASURE
- **Compliance Data**: [WHAT_DEVICE_TRACKS]
- **Symptom Tracking**: [SYMPTOMS_TO_MONITOR]

### TARGET
- **Usage Goal**: [E.G._CPAP_4_HOURS_NIGHT]
- **Symptom Goal**: [SYMPTOM_IMPROVEMENT_TARGET]

### SAFETY
- **Device Warnings**: [SAFETY_WARNINGS]
- **Malfunction Signs**: [WHEN_NOT_WORKING]
- **When to Call**: [PROBLEMS_REQUIRING_CONTACT]

### FOLLOW-UP
- **Compliance Review**: [WHEN_DATA_REVIEWED]
- **Supply Reorder**: [WHEN_HOW]

### NOTES
- **Insurance**: [COVERAGE_PRIOR_AUTH]
- **Supplies Needed**: [CONSUMABLES_LIST]

---

## Metadata
- **Card ID**: DME-[CATEGORY]-[NUMBER]
- **Tier Path**: Medical > DME > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 6: REFERRALS 👨‍⚕️

## Seed Input
```
Specialty: [SPECIALTY]
Reason: [REFERRAL_REASON]
Urgency: [routine | urgent | emergent]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
See a [SPECIALTY] to [SIMPLE_REASON].

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — This specialist can [WHAT_SPECIALIST_PROVIDES].

### HOW TO DO IT
- [HOW_TO_SCHEDULE]
- [WHAT_TO_BRING]
- [QUESTIONS_TO_PREPARE]
- [WHAT_TO_EXPECT]

### WHEN TO DO IT
Schedule within [URGENCY_TIMEFRAME] | First visit lasts [DURATION].

### WHAT TO WATCH FOR
- [SYMPTOMS_NEEDING_SOONER_APPOINTMENT]
- [WHAT_TO_DO_IF_CANT_GET_TIMELY]

---

## Full Clinical View

### WHAT
- **Card Name**: [SPECIALTY] Referral - [REFERRAL_REASON]
- **Specialty**: [SPECIALTY]
- **Referral Question**: [SPECIFIC_CLINICAL_QUESTION]
- **Urgency**: [URGENCY]
- **Type**: [ONE_TIME_VS_ONGOING]

### WHO
- **Specialist Role**: [WHAT_SPECIALIST_DOES]
- **PCP Role**: Coordinates, implements recommendations
- **Patient Role**: Schedules, attends, follows through

### WHEN
- **Timeline**: Routine [2-4 weeks] | Urgent [1-7 days] | Emergent [same day/ED]
- **Expected Visits**: [INITIAL_PLUS_FOLLOWUPS]

### WHERE
- **Setting**: [SPECIALIST_OFFICE_TELEHEALTH]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Referral Indications**: [CRITERIA_WHEN_APPROPRIATE]
- **Expected Outcome**: [WHAT_REFERRAL_ACCOMPLISHES]

### HOW
- **Before Visit**:
  - Records to Bring: [LABS_IMAGING_NOTES]
  - Questions to Prepare: [SUGGESTED_QUESTIONS]
- **After Visit**: [HOW_RECOMMENDATIONS_FLOW_BACK]

### MEASURE
- **Referral Success**: [HOW_TO_KNOW_ACHIEVED_PURPOSE]

### TARGET
- **Goal**: [SPECIFIC_OUTCOME_EXPECTED]

### SAFETY
- **When to Escalate**: [SYMPTOMS_REQUIRING_FASTER_ACCESS]

### FOLLOW-UP
- **After Specialist**: Implement recommendations, follow up with PCP

### NOTES
- **Insurance**: [REFERRAL_PRIOR_AUTH_REQUIREMENTS]

---

## Metadata
- **Card ID**: REF-[SPECIALTY_ABBREV]-[NUMBER]
- **Tier Path**: Medical > Referrals > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 7: NUTRITION 🥗

## Seed Input
```
Intervention: [DIETARY_INTERVENTION]
Type: [pattern | food_focus | behavior]
Condition: [TARGET_CONDITION]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[SIMPLE_ACTION_STATEMENT]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — [HOW_DIET_HELPS_GOAL].

### HOW TO DO IT
- [PRACTICAL_FIRST_STEP]
- [SPECIFIC_FOOD_SWAP_OR_ADDITION]
- [PORTION_OR_TIMING_TIP]
- [EASY_MEAL_IDEA]

### WHEN TO DO IT
[MEAL_TIMING_DAILY] | You may notice [BENEFIT] in [TIMEFRAME].

### WHAT TO WATCH FOR
- [SIGN_DIET_WORKING]
- [SIGN_ADJUSTMENT_NEEDED]

---

## Full Clinical View

### WHAT
- **Card Name**: [DIETARY_INTERVENTION]
- **Type**: [TYPE]
- **Target Condition**: [CONDITION]
- **Core Principles**: [KEY_PRINCIPLES]

### WHO
- **Primary Actor**: Patient
- **RD/Nutritionist**: [ROLE]
- **Family Support**: [HOW_FAMILY_HELPS]

### WHEN
- **Implementation**: [HOW_TO_PHASE_IN]
- **Duration**: [SHORT_TERM_VS_LIFELONG]

### WHERE
- **Home Kitchen**: Primary
- **Restaurants**: [EATING_OUT_STRATEGIES]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Mechanism**: [HOW_DIET_AFFECTS_HEALTH]
- **Evidence**: [GUIDELINE_GRADE_STUDY]
- **Expected Benefits**: [QUANTIFIED_IF_AVAILABLE]

### HOW
- **Foods to INCLUDE**:
  | Category | Examples | Portions/Day |
  |----------|----------|--------------|
  | [CATEGORY_1] | [EXAMPLES] | [PORTIONS] |
  | [CATEGORY_2] | [EXAMPLES] | [PORTIONS] |

- **Foods to LIMIT**:
  | Category | Limit To | Swap With |
  |----------|----------|-----------|
  | [CATEGORY_1] | [LIMIT] | [SWAP] |
  | [CATEGORY_2] | [LIMIT] | [SWAP] |

- **Sample Day**:
  - Breakfast: [MEAL_WITH_PORTIONS]
  - Lunch: [MEAL_WITH_PORTIONS]
  - Dinner: [MEAL_WITH_PORTIONS]

- **Budget-Friendly**: [COST_SAVING_TIPS]
- **Cultural Adaptations**: [ETHNIC_OPTIONS]

### MEASURE
- **Track**: [WEIGHT_FOOD_DIARY_LABS]
- **Frequency**: [HOW_OFTEN]

### TARGET
- **Dietary Targets**: [SPECIFIC_NUMERIC_GOALS]
- **Clinical Targets**: [HEALTH_OUTCOMES]

### SAFETY
- **Nutritional Concerns**: [POTENTIAL_DEFICIENCIES]
- **Medication Interactions**: [WARFARIN_VITAMIN_K_ETC]
- **When to Consult RD**: [SCENARIOS]

### FOLLOW-UP
- Week 1-2: Establish habits
- Month 1: Assess adherence
- Month 3: Check clinical outcomes

### NOTES
- **Resources**: [APPS_WEBSITES_RECIPES]

---

## Metadata
- **Card ID**: NUT-[DIET_TYPE]-[NUMBER]
- **Tier Path**: Behavioral > Nutrition > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 8: MOVEMENT/EXERCISE 🏃

## Seed Input
```
Exercise: [EXERCISE_TYPE]
Modality: [aerobic | strength | flexibility | balance]
Intensity: [light | moderate | vigorous]
Equipment: [none | minimal | gym]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[SIMPLE_ACTION_STATEMENT]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — [HOW_EXERCISE_HELPS_GOAL].

### HOW TO DO IT
- [STARTING_POINT_FOR_BEGINNERS]
- [KEY_TECHNIQUE_TIP]
- [HOW_TO_KNOW_RIGHT_INTENSITY]
- [WARMUP_COOLDOWN_REMINDER]

### WHEN TO DO IT
[FREQUENCY_PER_WEEK] | Start seeing benefits in [TIMEFRAME].

### WHAT TO WATCH FOR
- [STOP_IF_THIS_HAPPENS]
- [SIGN_TO_REDUCE_INTENSITY]

---

## Full Clinical View

### WHAT
- **Card Name**: [EXERCISE_TYPE]
- **Modality**: [MODALITY]
- **Intensity**: [INTENSITY]
- **Equipment**: [EQUIPMENT]

### WHO
- **Primary Actor**: Patient
- **PT/Trainer**: [ROLE_IF_APPLICABLE]
- **Appropriate For**: [WHO_BENEFITS]
- **Precautions For**: [WHO_NEEDS_MODIFICATION]

### WHEN
- **Frequency**: [DAYS_PER_WEEK]
- **Duration**: [MINUTES_PER_SESSION]
- **Best Time**: [OPTIMAL_TIMING]

### WHERE
- **Home**: [SPACE_NEEDED]
- **Outdoors**: [TERRAIN_WEATHER]
- **Gym**: [EQUIPMENT_ACCESS]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Benefits**: [HOW_EXERCISE_IMPROVES_HEALTH]
- **Evidence**: [ACSM_AHA_GUIDELINES_GRADE]

### HOW
- **Technique**: [DETAILED_INSTRUCTIONS]
- **Intensity Guidance**:
  - RPE Target: [RANGE_1_10]
  - HR Target: [PERCENT_MAX_OR_ZONE]
  - Talk Test: [DESCRIPTION]

- **Progression Tiers**:
  ```
  Tier 1 (Weeks 1-2): [DURATION_FREQUENCY_INTENSITY]
    Advance when: [CRITERIA]
  Tier 2 (Weeks 3-6): [DURATION_FREQUENCY_INTENSITY]
    Advance when: [CRITERIA]
  Tier 3 (Ongoing): [DURATION_FREQUENCY_INTENSITY]
  ```

- **Warm-Up**: [ROUTINE]
- **Cool-Down**: [ROUTINE]
- **Modifications**:
  - Easier: [OPTION]
  - Harder: [OPTION]
  - Joint-Friendly: [OPTION]

### MEASURE
- **Track**: [METRICS_TO_MONITOR]
- **Tools**: [FITNESS_TRACKER_APP]

### TARGET
- **Short-term** (4-6 weeks): [INITIAL_TARGET]
- **Long-term** (3-6 months): [MAINTENANCE_TARGET]

### SAFETY
- **Pre-Exercise Screening**: [PARQ_CLEARANCE]
- **Stop If**: [RED_FLAG_SYMPTOMS]
- **Condition Precautions**:
  - Cardiac: [PRECAUTIONS]
  - Diabetes: [BLOOD_SUGAR_MANAGEMENT]
  - Arthritis: [JOINT_PROTECTION]

### FOLLOW-UP
- Weekly: Self-assessment
- Monthly: Progress review

### NOTES
- **Equipment Guide**: [WHAT_TO_BUY_COSTS]
- **Motivation Tips**: [ADHERENCE_STRATEGIES]

---

## Metadata
- **Card ID**: MOV-[MODALITY]-[NUMBER]
- **Tier Path**: Behavioral > Movement > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 9: RECOVERY 😴

## Seed Input
```
Intervention: [INTERVENTION_NAME]
Type: [sleep | stress | breathing_relaxation]
Target: [TARGET_OUTCOME]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[SIMPLE_ACTION_STATEMENT]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — [HOW_RECOVERY_HELPS_GOAL].

### HOW TO DO IT
- [MOST_IMPORTANT_HABIT]
- [PRACTICAL_TIP]
- [ENVIRONMENT_SETUP]
- [TIMING_TIP]

### WHEN TO DO IT
[DAILY_TIMING_FREQUENCY] | You may notice improvement in [TIMEFRAME].

### WHAT TO WATCH FOR
- [SIGN_WORKING]
- [WHEN_TO_SEEK_HELP]

---

## Full Clinical View

### WHAT
- **Card Name**: [INTERVENTION_NAME]
- **Type**: [TYPE]
- **Target**: [TARGET_OUTCOME]

### WHO
- **Primary Actor**: Patient
- **Support**: [THERAPIST_COACH_FAMILY]

### WHEN
- **Frequency**: [DAILY_OR_AS_NEEDED]
- **Timing**: [BEST_TIME]
- **Duration**: [PER_SESSION]

### WHERE
- **Setting**: [BEDROOM_QUIET_SPACE]
- **Environment**: [OPTIMAL_CONDITIONS]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Mechanism**: [HOW_IMPROVES_HEALTH]
- **Evidence**: [GUIDELINE_GRADE]

### HOW
- **Technique**: [STEP_BY_STEP_INSTRUCTIONS]

- **[If Sleep]**:
  - Bedtime Routine: [STEPS]
  - Environment: Temperature [RANGE], Light [DARKNESS], Sound [NOISE_MGMT]
  - Screen Curfew: [TIMING]

- **[If Breathing]**:
  ```
  [TECHNIQUE_NAME]:
  1. [STEP_WITH_COUNTS]
  2. [STEP_WITH_COUNTS]
  3. [STEP_WITH_COUNTS]
  Repeat: [CYCLES]
  ```

### MEASURE
- **Track**: [SLEEP_DURATION_QUALITY_STRESS_RATING]
- **Tools**: [DIARY_APPS_WEARABLES]

### TARGET
- **Goal**: [SPECIFIC_TARGET]
- **Timeline**: [WHEN_TO_EXPECT]

### SAFETY
- **When Not Enough**: [SIGNS_OF_DISORDER]
- **Mental Health Concerns**: [WARNING_SIGNS]

### FOLLOW-UP
- Weekly: Self-assessment
- Escalate if: [CRITERIA]

### NOTES
- **Resources**: [APPS_GUIDES]

---

## Metadata
- **Card ID**: REC-[TYPE]-[NUMBER]
- **Tier Path**: Behavioral > Recovery > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 10: MIND-BODY PRACTICES 🧘

## Seed Input
```
Practice: [PRACTICE_NAME]
Category: [meditation | yoga | tai_chi | other]
Level: [beginner | intermediate | advanced]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[SIMPLE_ACTION_STATEMENT]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — [HOW_PRACTICE_HELPS_GOAL].

### HOW TO DO IT
- [HOW_TO_START]
- [KEY_INSTRUCTION]
- [WHAT_TO_DO_WHEN_MIND_WANDERS]
- [HOW_TO_END]

### WHEN TO DO IT
[FREQUENCY_DURATION] | Many notice [BENEFIT] within [TIMEFRAME].

### WHAT TO WATCH FOR
- [SIGN_HELPING]
- [WHEN_TO_TALK_TO_PROVIDER]

---

## Full Clinical View

### WHAT
- **Card Name**: [PRACTICE_NAME]
- **Category**: [CATEGORY]
- **Level**: [LEVEL]

### WHO
- **Primary Actor**: Patient
- **Guidance**: [APP_AUDIO_VIDEO_CLASS]

### WHEN
- **Frequency**: [TIMES_PER_WEEK]
- **Duration**: [MINUTES_PER_SESSION]
- **Best Time**: [WHEN_MOST_EFFECTIVE]

### WHERE
- **Setting**: [QUIET_SPACE_STUDIO_ANYWHERE]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Mechanism**: [PSYCHOLOGICAL_NEUROLOGICAL_EFFECTS]
- **Evidence**: [GUIDELINE_GRADE_CONDITIONS_STUDIED]

### HOW
- **Technique**: [COMPLETE_INSTRUCTIONS]
- **Progression**:
  - Beginner: [STARTING_PRACTICE]
  - Intermediate: [BUILDING_SKILL]
  - Advanced: [DEEPER_PRACTICE]

### MEASURE
- **Track**: [MOOD_ANXIETY_PRACTICE_FREQUENCY]
- **Tools**: [APPS_JOURNALS]

### TARGET
- **Goal**: [IMPROVEMENT_TARGET]
- **Timeline**: [WHEN_TO_EXPECT]

### SAFETY
- **Considerations**: [WHEN_NOT_APPROPRIATE]
- **Trauma**: [TRAUMA_INFORMED_CONSIDERATIONS]
- **Crisis Resources**: 988 Lifeline, Crisis Text: HOME to 741741

### FOLLOW-UP
- Practice log review
- Technique refinement

### NOTES
- **Resources**: [APPS_BOOKS_VIDEOS]

---

## Metadata
- **Card ID**: MB-[CATEGORY]-[NUMBER]
- **Tier Path**: Behavioral > Mind-Body > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 11: ENVIRONMENTAL & SOCIAL HEALTH 🌍

## Seed Input
```
Intervention: [INTERVENTION_NAME]
Area: [social | environmental | occupational | substance | financial]
Target: [TARGET_OUTCOME]
```

---

## Patient-Facing View

### WHAT YOU'RE DOING
[SIMPLE_ACTION_STATEMENT]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — [HOW_CHANGE_HELPS_GOAL].

### HOW TO DO IT
- [IMMEDIATE_FIRST_ACTION]
- [RESOURCE_TO_ACCESS]
- [SUPPORT_TO_ENGAGE]
- [HOW_TO_SUSTAIN]

### WHEN TO DO IT
[TIMELINE_FREQUENCY] | You may notice [BENEFIT] in [TIMEFRAME].

### WHAT TO WATCH FOR
- [SIGN_WORKING]
- [WHEN_TO_SEEK_HELP]

---

## Full Clinical View

### WHAT
- **Card Name**: [INTERVENTION_NAME]
- **Area**: [AREA]
- **Target**: [TARGET_OUTCOME]

### WHO
- **Primary Actor**: Patient
- **Support Network**: [FAMILY_FRIENDS_COMMUNITY]
- **Professional**: [SOCIAL_WORKER_COUNSELOR]

### WHEN
- **Timeline**: [IMMEDIATE_SHORT_ONGOING]
- **Frequency**: [HOW_OFTEN]

### WHERE
- **Setting**: [HOME_WORK_COMMUNITY]

### WHY
- **Clinical Goal**: [HEALTH_SYSTEM]: [ACTION] [DOMAIN]
- **Mechanism**: [HOW_AFFECTS_HEALTH]
- **Evidence**: [RESEARCH]

### HOW
- **Implementation**: [DETAILED_ACTION_PLAN]
- **Resources**: [PROGRAMS_NUMBERS_WEBSITES]
- **Support**: [WHO_CAN_HELP]
- **Barriers Plan**: [OBSTACLES_AND_SOLUTIONS]

- **[If Substance Use]**:
  - Cessation Resources: [QUITLINES_PROGRAMS]
  - Support Groups: [AA_SMART_RECOVERY]
  - Medications: [OPTIONS_WITH_REFERRAL]

### MEASURE
- **Track**: [SPECIFIC_METRICS]

### TARGET
- **Goal**: [SPECIFIC_OUTCOME]
- **Timeline**: [WHEN_TO_ACHIEVE]

### SAFETY
- **Crisis Resources**:
  - 988 Suicide & Crisis Lifeline
  - SAMHSA: 1-800-662-4357
  - Crisis Text: HOME to 741741
- **Escalation**: [WHEN_TO_SEEK_IMMEDIATE_HELP]

### FOLLOW-UP
- Check-ins: [FREQUENCY]
- Goal adjustment: [BASED_ON_PROGRESS]

### NOTES
- **Community Resources**: [LOCAL_PROGRAMS]

---

## Metadata
- **Card ID**: ENV-[AREA]-[NUMBER]
- **Tier Path**: Behavioral > Environmental/Social > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS]

---
---

# TEMPLATE 12: MICRO-LEARNING 📚

## Seed Input
```
Topic: [TOPIC_NAME]
Condition: [RELATED_CONDITION]
Unlocks: [NEXT_ACTION_CARD]
```

---

## Patient-Facing View

### WHAT YOU'RE LEARNING
[TOPIC_TITLE]

### WHY THIS MATTERS TO YOU
[PATIENT: their personal goal] — Understanding this helps you [HOW_KNOWLEDGE_CONNECTS_TO_ACTION].

### KEY POINTS (5 Minutes)
1. [KEY_CONCEPT_1]
2. [KEY_CONCEPT_2]
3. [KEY_CONCEPT_3]
4. [KEY_CONCEPT_4]
5. [ACTIONABLE_TAKEAWAY]

### CHECK YOUR UNDERSTANDING
- Q: [SIMPLE_QUESTION_1]
  A: [ANSWER]
- Q: [SIMPLE_QUESTION_2]
  A: [ANSWER]

---

## Full Clinical View

### WHAT
- **Card Name**: [TOPIC_NAME]
- **Condition**: [RELATED_CONDITION]
- **Learning Objective**: [WHAT_PATIENT_WILL_UNDERSTAND]
- **Unlocks**: [NEXT_ACTION_CARD]
- **Duration**: 5 minutes

### WHO
- **Learner**: Patient
- **Assigned By**: Care team (within deck)

### WHEN
- **Timing**: Before [NEXT_ACTION_CARD]

### WHERE
- **Access**: App, patient portal

### WHY
- **Relevance**: [WHY_UNDERSTANDING_IMPROVES_OUTCOMES]
- **Connection**: [HOW_PREPARES_FOR_NEXT_CARD]

### HOW
**Section 1: [SUBTOPIC]**
[CONTENT_6TH_8TH_GRADE_LEVEL]

**Section 2: [SUBTOPIC]**
[CONTENT_6TH_8TH_GRADE_LEVEL]

**Section 3: [SUBTOPIC]**
[CONTENT_6TH_8TH_GRADE_LEVEL]

**Common Misconceptions**:
| Myth | Truth |
|------|-------|
| [MYTH_1] | [TRUTH_1] |
| [MYTH_2] | [TRUTH_2] |

**Glossary**:
| Term | Definition |
|------|------------|
| [TERM_1] | [SIMPLE_DEFINITION] |
| [TERM_2] | [SIMPLE_DEFINITION] |

### MEASURE
- **Completion**: Card marked complete
- **Understanding**: [QUIZ_OR_TEACHBACK]

### TARGET
- **Goal**: [WHAT_PATIENT_SHOULD_EXPLAIN_AFTER]

### SAFETY
- **Misinformation**: [DANGEROUS_MISCONCEPTIONS_CORRECTED]

### FOLLOW-UP
- **Next**: [NEXT_ACTION_CARD] unlocked

### NOTES
- **Resources**: [TRUSTED_WEBSITES_VIDEOS]

---

## Metadata
- **Card ID**: MICRO-[CATEGORY]-[NUMBER]
- **Tier Path**: Behavioral > Micro-Learning > [TIER_3] > [TIER_4] > This Card
- **Tags**: [RELEVANT_TAGS], #MicroLearning, #FoundationalCard

---
---

# QUICK REFERENCE

| # | Type | Icon | Seed Input |
|---|------|------|------------|
| 1 | Medications | 💊 | Drug, dose, route, frequency, indication |
| 2 | Diagnostic Testing | 🔬 | Test, type, indication |
| 3 | Imaging Studies | 🏥 | Study, modality, body region, contrast |
| 4 | Procedures | 🔧 | Procedure, type, setting, anesthesia |
| 5 | DME | 🩺 | Device, category, settings |
| 6 | Referrals | 👨‍⚕️ | Specialty, reason, urgency |
| 7 | Nutrition | 🥗 | Intervention, type, condition |
| 8 | Movement | 🏃 | Exercise, modality, intensity, equipment |
| 9 | Recovery | 😴 | Intervention, type, target |
| 10 | Mind-Body | 🧘 | Practice, category, level |
| 11 | Environmental/Social | 🌍 | Intervention, area, target |
| 12 | Micro-Learning | 📚 | Topic, condition, unlocks |

---

**Version**: v1.0 | **Created**: November 2025
