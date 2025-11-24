# PARAMETER NORMALIZATION SPECIFICATION
## Patient Health Dashboard - Clinical Foundation

**Document Type:** Core Clinical Logic  
**Version:** 2.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - Part 1 of 4  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

This document is part of the **Parameter Scoring Framework** (read all four together):

1. **PARAMETER_NORMALIZATION.md** (this document) - Core normalization methods and formulas
2. **CALIBRATION_VALIDATION.md** - How to calibrate coefficients and validate clinical fidelity
3. **CONTEXT_RULES.md** - Patient-specific scoring adjustments and overrides
4. **TEMPORAL_SCORING.md** - Handling measurements over time and aberrant values

Additionally references:
- `PROJECT_SPECIFICATION_v2.md` - Master project architecture (24-cell matrix, aggregation)
- `SYSTEM_DOMAIN_SCORING.md` (planned) - How normalized scores aggregate to system/overall scores

---

## DOCUMENT PURPOSE

This specification defines the **universal framework** for converting any clinical parameter into a standardized 0-100 normalized score. Every parameter added to the flowsheet and displayed on the dashboard must follow one of the normalization methods defined here.

**This document provides:**
1. The clinical philosophy behind our scoring approach
2. Five normalization methods with complete mathematical specifications
3. Framework for determining personalized targets for every patient
4. Systematic approach to classifying parameters (bidirectional vs unidirectional)
5. Basic worked examples demonstrating each method

**For detailed calibration, validation, and special cases, see companion documents listed above.**

---

## CORE PHILOSOPHY

### Principle 1: Personalized Clinical Targets

**Z-score = 0 represents the personalized clinical target for each individual patient.**

NOT population mean. NOT statistical average. The **evidence-based optimal value** for that specific patient given their:
- Age and sex
- Comorbidities (diabetes, CKD, CHF, CAD, etc.)
- Current medications
- Risk factors (smoking, family history, etc.)
- Special populations (pregnancy, athletes, etc.)

**Example:** LDL target for a 45-year-old with prior MI = 55 mg/dL (aggressive). LDL target for a healthy 30-year-old = 100 mg/dL (standard). Same parameter, different targets.

### Principle 2: Conservative But Motivating Baseline

**At personalized target (z = 0): Score = 85 points**

**Rationale:**
- Strong score (B+) that feels positive and motivating
- Leaves room for sustained excellence (85 â†’ 95+)
- Absorbs measurement variability and data noise
- Acknowledges that "at target" is excellent, not mediocre
- Allows composite scores to exceed individual scores when multiple parameters optimal

**Not 100:** Perfect scores reserved for sustained excellence over time or exceptional performance.  
**Not 50:** Too demotivating for patients meeting clinical targets.

### Principle 3: Tri-State Scoring (Numeric / No Score / Not Applicable)

**Not all parameters can or should produce a numeric score.**

**THREE STATES:**

1. **NUMERIC (5-100):** Valid measurement successfully normalized
   - Patient has the parameter measured
   - Value passes quality control
   - Normalization method applied
   - Display: Numeric score with color zone

2. **NO SCORE (NS):** Insufficient or invalid data
   - Sample hemolyzed, clotted, or rejected
   - QC failure (instrument error, invalid result)
   - Value physiologically impossible (likely error)
   - Missing required inputs for personalization
   - Display: "Insufficient data" with gray icon, no numeric score
   - Action: Recommend re-testing

3. **NOT APPLICABLE (NA):** Parameter not relevant for this patient
   - Sex-specific parameters (PSA in females, pregnancy tests in males)
   - Age-specific parameters (pediatric scales in adults)
   - Condition-specific parameters (dialysis adequacy in non-dialysis patients)
   - Display: Hide parameter entirely from dashboard

**Critical distinction:** Score of 5 (floor) means "measured extreme value" (critically abnormal but measured). NS means "no valid measurement obtained." These are fundamentally different.

**Implementation:**
```
IF parameter not applicable to patient:
  RETURN NA (hide from display)
  
ELSE IF measurement invalid OR missing required data:
  RETURN NS (display "insufficient data")
  
ELSE IF measurement valid:
  Calculate normalized score (5-100)
  RETURN numeric score
```

### Principle 4: Clinical Context Determines Classification

Every parameter must be evaluated for:
1. **Can this value be TOO LOW?** (pathophysiology, clinical outcomes)
2. **Can this value be TOO HIGH?** (pathophysiology, clinical outcomes)
3. **Are both directions equal concern?** (symmetric vs asymmetric)
4. **What does deviation indicate?** (disease, risk, dysfunction, artifact)

### Principle 4: Clinical Context Determines Classification

Every parameter must be evaluated for:
1. **Can this value be TOO LOW?** (pathophysiology, clinical outcomes)
2. **Can this value be TOO HIGH?** (pathophysiology, clinical outcomes)
3. **Are both directions equal concern?** (symmetric vs asymmetric)
4. **What does deviation indicate?** (disease, risk, dysfunction, artifact)

**Decision tree:**
- If BOTH directions have documented adverse outcomes â†’ **BIDIRECTIONAL**
- If ONLY ONE direction has documented adverse outcomes â†’ **UNIDIRECTIONAL**
- Consider clinical context: acute vs chronic, treated vs untreated, artifact vs pathology

*For context-dependent scoring adjustments (pregnancy, medications, comorbidities), see CONTEXT_RULES.md.*

### Principle 5: Asymmetry Reflects Clinical Reality

Most bidirectional parameters have **asymmetric concerns**:
- One direction more common (e.g., hypertension vs hypotension)
- One direction more dangerous (e.g., hyperkalemia vs hypokalemia)
- One direction more acute (e.g., hypoglycemia vs hyperglycemia)

### Principle 5: Asymmetry Reflects Clinical Reality

Most bidirectional parameters have **asymmetric concerns**:
- One direction more common (e.g., hypertension vs hypotension)
- One direction more dangerous (e.g., hyperkalemia vs hypokalemia)
- One direction more acute (e.g., hypoglycemia vs hyperglycemia)

**Scoring must reflect this:** Different penalty rates for each direction.

*For detailed coefficient selection and calibration methodology, see CALIBRATION_VALIDATION.md.*

### Principle 6: Display Clinical Meaning, Not Just Numbers

Every parameter score must be accompanied by:
- Patient's actual value with units
- Patient's personalized target
- Clinical zone labels (e.g., "Stage 1 Hypertension," "Prediabetes")
- Visual indicator of position relative to zones
- Plain language interpretation

### Principle 6: Display Clinical Meaning, Not Just Numbers

Every parameter score must be accompanied by:
- Patient's actual value with units
- Patient's personalized target
- Clinical zone labels (e.g., "Stage 1 Hypertension," "Prediabetes")
- Visual indicator of position relative to zones
- Plain language interpretation
- **Explainability on-demand** (show calculation formula, inputs, rationale)

**Users need context, not just scores.**

**Explainability Tooltip Example:**
```
Your Score: 38 [Why this score?]

When clicked/tapped, shows:
- Your value: 142 mmHg
- Your target: 130 mmHg (based on diabetes diagnosis)
- Deviation: +1.2 standard deviations above target
- Severity: Stage 1 Hypertension (moderate concern)
- Formula: 85 Ã— e^(-0.15 Ã— 1.2Â²) = 38
- Reference: ADA 2023 Guidelines
```

### Principle 7: Temporal Context Matters

Single aberrant readings should not disproportionately affect scores. Consider both point-in-time measurements and trends over time.

*For temporal smoothing, stability scoring, and handling aberrant values, see TEMPORAL_SCORING.md.*

### Principle 8: Accessibility is Non-Negotiable

Visual displays must be accessible to all users:
- **Color + Shape + Text:** Never rely on color alone
- **High contrast:** WCAG 2.1 AA standards minimum
- **Icons with labels:** Pair visual indicators with text
- **Screen reader compatible:** All scores and interpretations must be readable by assistive technology

---

## THE FIVE NORMALIZATION METHODS

### Overview Table

| Method | Use Case | Z-Score Based | Examples |
|--------|----------|---------------|----------|
| **Method 1** | Bidirectional parameters (symmetric or asymmetric) | Yes | BP, Glucose, Electrolytes, HbA1c, Creatinine |
| **Method 2** | Unidirectional - Lower is Better | Yes | hsCRP, Troponin, Liver Enzymes, LDL-P |
| **Method 3** | Unidirectional - Higher is Better | Yes | VO2max, Grip Strength, Albumin, eGFR |
| **Method 4** | Clinical Risk Categories | No | hsCRP zones, HbA1c diagnostic thresholds |
| **Method 5** | Binary/Ordinal | No | MI history, NYHA Class, Pain scales |

### Optional Pre-Transformations for Skewed Distributions

**For parameters with highly skewed distributions** (e.g., hsCRP, triglycerides where most values cluster near zero with long right tail):

**Option A: Log Transformation**
```
V_transformed = ln(V + 1)  // Add 1 to handle zeros
Calculate z-score using transformed values
Target and SD must also be in log space
```

**Option B: Use Method 4 (Clinical Categories) Instead**
- Often simpler and more clinically intuitive
- Map established risk categories directly to scores
- Avoid mathematical complexity of transforms

**Decision rule:** Try Method 2/3 with standard z-scores first. If calibration fails to match clinical anchors (see CALIBRATION_VALIDATION.md), then either:
1. Apply log transform, OR
2. Switch to Method 4 (Category-Based)

*For most parameters, standard z-score methods work well without transformation.*

---

## METHOD 1: BIDIRECTIONAL NORMALIZATION

### When to Use

**Clinical Criteria:**
- Deviations in BOTH directions have documented adverse outcomes
- Optimal value exists within a range (not just a threshold)
- Both too high AND too low are pathologic

**Common Examples:**
- **Electrolytes:** Sodium, potassium, calcium, magnesium
- **Metabolic:** Glucose, HbA1c, creatinine
- **Cardiovascular:** Blood pressure, heart rate
- **Hematologic:** Hemoglobin, WBC, platelets
- **Endocrine:** TSH, free T4
- **Lipids:** LDL (extreme asymmetry), HDL (moderate asymmetry)
- **Micronutrients:** Vitamin D, vitamin B12, ferritin

### Classification: Symmetric vs Asymmetric

**SYMMETRIC:** Both directions of equal clinical concern
- Example: Sodium (hypo and hypernatremia both cause seizures/death)
- Penalty rates similar in both directions

**ASYMMETRIC:** One direction is primary concern
- **Asymmetric-High Primary:** More concerned about HIGH values
  - Example: LDL (high = CVD common, low <40 = rare concern)
  - Example: Blood pressure (hypertension common/chronic, hypotension less common/acute)
  - Steeper penalty above target, gentler penalty below

- **Asymmetric-Low Primary:** More concerned about LOW values
  - Example: HDL (low = CVD established, very high >100 = uncertain harm)
  - Example: Hemoglobin in elderly (anemia more common than polycythemia)
  - Steeper penalty below target, gentler penalty above

### Mathematical Framework

**INPUTS:**
1. **Actual Value (V):** Patient's measured value
2. **Target Value (T):** Personalized clinical target (z = 0)
3. **Standard Deviation (SD):** Clinical variability from literature
4. **Penalty Coefficients:** Î± (above target), Î² (below target)
5. **Baseline Score (B):** 85 points (at target)

**STEP 1: Calculate Z-Score**
```
z = (V - T) / SD
```

**STEP 2: Calculate Score Based on Direction**

**For Symmetric Bidirectional:**
```
Score = B Ã— e^(-k Ã— zÂ²)

where:
- B = 85 (baseline score at target)
- k = penalty coefficient (typically 0.15-0.25)
- z = z-score (positive or negative)

Higher k = steeper penalty for deviation
```

**For Asymmetric Bidirectional:**
```
IF z â‰¥ 0 (above target):
  Score = B Ã— e^(-Î± Ã— zÂ²)
  
IF z < 0 (below target):
  Score = B Ã— e^(-Î² Ã— |z|Â²)

where:
- Î± = penalty coefficient for HIGH values
- Î² = penalty coefficient for LOW values
- For asymmetric-high: Î± > Î² (steeper penalty when high)
- For asymmetric-low: Î² > Î± (steeper penalty when low)
```

**STEP 3: Apply Floor and Ceiling**
```
Score_final = MAX(5, MIN(100, Score))
```
Floor at 5 (not 0) to distinguish measured values from missing data.
Ceiling at 100 for exceptional sustained performance.

### Penalty Coefficient Selection Guide

**Symmetric (Î± = Î²):**
- k = 0.15: Gradual penalty (e.g., calcium in stable patient)
- k = 0.20: Moderate penalty (e.g., sodium, magnesium)
- k = 0.25: Steep penalty (e.g., potassium, glucose)
- k = 0.30: Very steep penalty (e.g., life-threatening parameters)

**Asymmetric:**
- **Primary direction:** 0.20-0.30 (steep penalty)
- **Secondary direction:** 0.10-0.15 (gentle penalty)

**Clinical reasoning determines coefficients based on:**
- Severity of outcomes
- Speed of harm (acute vs chronic)
- Reversibility
- Established risk curves from literature

*For detailed coefficient optimization and validation methodology, see CALIBRATION_VALIDATION.md Section 3.*

### Worked Example 1: Systolic Blood Pressure (Asymmetric-High)

**Patient:** 55-year-old male, no CVD, diabetes  
**Target (T):** 130 mmHg (ADA guideline for diabetes)  
**SD:** 10 mmHg  
**Coefficients:** Î± = 0.25 (high BP primary concern), Î² = 0.15 (low BP secondary concern)

**Scenario A: Patient SBP = 130 mmHg (at target)**
```
z = (130 - 130) / 10 = 0
Score = 85 (at target, no deviation)
Color: GREEN
Interpretation: "Optimal - at your target blood pressure"
```

**Scenario B: Patient SBP = 150 mmHg (Stage 2 Hypertension)**
```
z = (150 - 130) / 10 = +2.0
Score = 85 Ã— e^(-0.25 Ã— 2Â²) = 85 Ã— e^(-1.0) = 85 Ã— 0.368 = 31
Color: ORANGE
Interpretation: "High - Stage 2 Hypertension. Contact your doctor this week."
```

**Scenario C: Patient SBP = 110 mmHg (Hypotension)**
```
z = (110 - 130) / 10 = -2.0
Score = 85 Ã— e^(-0.15 Ã— 2Â²) = 85 Ã— e^(-0.60) = 85 Ã— 0.549 = 47
Color: ORANGE
Interpretation: "Low - May cause dizziness. Discuss with your doctor."
```

**Note asymmetry:** SBP 150 scores 31 (worse), SBP 110 scores 47 (less penalized). Reflects clinical reality that chronic hypertension is more damaging than mild hypotension in this context.

### Worked Example 2: Potassium (Symmetric, Steep Penalty)

**Patient:** 60-year-old on ACE inhibitor  
**Target (T):** 4.0 mEq/L  
**SD:** 0.5 mEq/L  
**Coefficient:** k = 0.30 (both directions dangerous)

**Scenario A: Patient K+ = 5.5 mEq/L (Hyperkalemia)**
```
z = (5.5 - 4.0) / 0.5 = +3.0
Score = 85 Ã— e^(-0.30 Ã— 3Â²) = 85 Ã— e^(-2.7) = 85 Ã— 0.067 = 6
Color: RED
Critical Alert: "CRITICAL: Severe hyperkalemia. Risk of cardiac arrest. Seek emergency care immediately."
```

**Scenario B: Patient K+ = 2.8 mEq/L (Hypokalemia)**
```
z = (2.8 - 4.0) / 0.5 = -2.4
Score = 85 Ã— e^(-0.30 Ã— 2.4Â²) = 85 Ã— e^(-1.73) = 85 Ã— 0.177 = 15
Color: RED
Critical Alert: "CRITICAL: Severe hypokalemia. Risk of arrhythmia. Seek emergency care immediately."
```

**Note symmetry:** Both deviations severely penalized. Reflects equal danger of hyper- and hypokalemia.

### Worked Example 3: HbA1c (Asymmetric-High, Context-Dependent)

**Patient A:** 35-year-old with Type 1 diabetes, no complications  
**Target (T):** 6.5% (tight control appropriate)  
**SD:** 0.8%  
**Coefficients:** Î± = 0.25 (high = poor control), Î² = 0.20 (low = hypoglycemia risk)

**Patient A has HbA1c = 5.8%**
```
z = (5.8 - 6.5) / 0.8 = -0.875
Score = 85 Ã— e^(-0.20 Ã— 0.875Â²) = 73
Color: YELLOW
Interpretation: "Below target - monitor for hypoglycemic episodes."
```

**Patient B:** 78-year-old with Type 2 diabetes, CVD, on insulin  
**Target (T):** 7.5% (relaxed control to avoid hypoglycemia)  
**Patient B has HbA1c = 6.2%**
```
z = (6.2 - 7.5) / 0.8 = -1.625
Score = 85 Ã— e^(-0.30 Ã— 1.625Â²) = 39
Color: RED
Alert: "TOO LOW for your age and conditions. High risk of dangerous hypoglycemia."
```

**Same HbA1c value (6.2%), different patients, different targets, different scores and interpretations.**

*For comprehensive context-dependent target logic and scoring overrides, see CONTEXT_RULES.md.*

### Clinical Zone Mapping

For dashboard display, map z-scores to clinical labels:

**Example: Systolic Blood Pressure**
```
Clinical Zones:
- <90 mmHg: "Severe Hypotension" (RED)
- 90-100 mmHg: "Hypotension" (ORANGE)
- 100-120 mmHg: "Normal" (GREEN)
- 120-130 mmHg: "Elevated" (YELLOW if target <120, GREEN if target 130)
- 130-140 mmHg: "Stage 1 Hypertension" (ORANGE)
- 140-180 mmHg: "Stage 2 Hypertension" (RED)
- â‰¥180 mmHg: "Hypertensive Crisis" (RED - Critical Alert)
```

Display shows:
- Patient's value: 150 mmHg
- Their target: 130 mmHg
- Clinical zone: "Stage 2 Hypertension"
- Visual position on scale
- Score: 31 (ORANGE)

---

## METHOD 2: UNIDIRECTIONAL - LOWER IS BETTER

### When to Use

**Clinical Criteria:**
- Only HIGH values are pathologic
- LOW values approach physiologic minimum (floor exists)
- No documented harm from low values within physiologic range
- Represents disease/injury markers or risk factors

**Common Examples:**
- **Inflammatory markers:** hsCRP, ESR, ferritin (inflammation context)
- **Cardiac injury:** Troponin, BNP, NT-proBNP
- **Liver injury:** ALT, AST, GGT, bilirubin
- **Kidney injury:** Creatinine (context), UACR (albumin/creatinine ratio)
- **Metabolic risk:** Triglycerides, fasting insulin, homocysteine
- **Genetic risk:** Lp(a)
- **Tumor markers:** PSA (context), CA 19-9, CEA

### Mathematical Framework

**INPUTS:**
1. **Actual Value (V):** Patient's measured value
2. **Target Value (T):** Optimal target (often at or near physiologic minimum)
3. **Standard Deviation (SD):** Clinical variability
4. **Penalty Coefficient (Î±):** Penalty rate for values above target
5. **Floor Value (F):** Physiologic or assay minimum

**STEP 1: Calculate Z-Score**
```
z = (V - T) / SD
```

**STEP 2: Calculate Score**

**For values AT or BELOW target (z â‰¤ 0):**
```
Score = 85 (no penalty, optimal range)
```

**For values ABOVE target (z > 0):**
```
Score = 85 Ã— e^(-Î± Ã— zÂ²)

where Î± = penalty coefficient (typically 0.20-0.30)
```

**STEP 3: Apply Floor**
```
Score_final = MAX(5, Score)
```

### Penalty Coefficient Selection

- Î± = 0.20: Gradual penalty (e.g., mildly elevated ALT, interpretation context-dependent)
- Î± = 0.25: Moderate penalty (e.g., hsCRP, standard CV risk marker)
- Î± = 0.30: Steep penalty (e.g., troponin, severe injury marker)

### Worked Example 1: hsCRP (Cardiovascular Risk Marker)

**Patient:** 50-year-old male, assessing CV risk  
**Target (T):** 1.0 mg/L (low CV risk threshold)  
**SD:** 2.0 mg/L (highly skewed distribution)  
**Coefficient:** Î± = 0.25  
**Floor:** 0 mg/L (assay minimum)

**Scenario A: Patient hsCRP = 0.5 mg/L (Low Risk)**
```
z = (0.5 - 1.0) / 2.0 = -0.25 (below target)
Score = 85 (at or below target = optimal)
Color: GREEN
Interpretation: "Optimal - Low cardiovascular inflammation"
```

**Scenario B: Patient hsCRP = 1.8 mg/L (Moderate Risk)**
```
z = (1.8 - 1.0) / 2.0 = +0.4
Score = 85 Ã— e^(-0.25 Ã— 0.4Â²) = 85 Ã— e^(-0.04) = 85 Ã— 0.961 = 82
Color: GREEN (borderline)
Interpretation: "Normal - Low-moderate cardiovascular risk"
```

**Scenario C: Patient hsCRP = 4.5 mg/L (High Risk)**
```
z = (4.5 - 1.0) / 2.0 = +1.75
Score = 85 Ã— e^(-0.25 Ã— 1.75Â²) = 85 Ã— e^(-0.766) = 85 Ã— 0.465 = 40
Color: ORANGE
Interpretation: "Elevated - High cardiovascular inflammation. Discuss with doctor."
```

**Scenario D: Patient hsCRP = 15 mg/L (Very High, Possible Infection)**
```
z = (15 - 1.0) / 2.0 = +7.0
Score = 85 Ã— e^(-0.25 Ã— 7Â²) = 85 Ã— e^(-12.25) â‰ˆ 0 â†’ Floor = 5
Color: RED
Critical Alert: "VERY HIGH - May indicate active infection or severe inflammation. Contact doctor today."
```

### Worked Example 2: Troponin (Cardiac Injury)

**Patient:** 60-year-old with chest pain  
**Target (T):** 0.01 ng/mL (upper limit of normal, assay-dependent)  
**SD:** 0.05 ng/mL  
**Coefficient:** Î± = 0.35 (very steep penalty, critical marker)  
**Floor:** 0 ng/mL

**Scenario A: Patient Troponin = 0.008 ng/mL (Normal)**
```
z = (0.008 - 0.01) / 0.05 = -0.04 (below target)
Score = 85 (normal, no cardiac injury detected)
Color: GREEN
Interpretation: "Normal - No cardiac injury detected"
```

**Scenario B: Patient Troponin = 0.08 ng/mL (Mildly Elevated)**
```
z = (0.08 - 0.01) / 0.05 = +1.4
Score = 85 Ã— e^(-0.35 Ã— 1.4Â²) = 85 Ã— e^(-0.686) = 85 Ã— 0.503 = 43
Color: ORANGE
Alert: "ELEVATED - Possible cardiac injury. Requires immediate evaluation."
```

**Scenario C: Patient Troponin = 2.5 ng/mL (Acute MI)**
```
z = (2.5 - 0.01) / 0.05 = +49.8
Score â†’ Floor = 5
Color: RED
Critical Alert: "CRITICAL - Acute myocardial infarction. CALL 911 IMMEDIATELY."
```

### Clinical Zone Mapping

**Example: hsCRP (CV Risk Categories)**
```
Clinical Zones (ACC/AHA guidelines):
- <1.0 mg/L: "Low CV Risk" (GREEN)
- 1.0-3.0 mg/L: "Moderate CV Risk" (YELLOW)
- 3.0-10.0 mg/L: "High CV Risk" (ORANGE)
- >10.0 mg/L: "Very High - Possible Infection/Inflammation" (RED)
```

---

## METHOD 3: UNIDIRECTIONAL - HIGHER IS BETTER

### When to Use

**Clinical Criteria:**
- Only LOW values are pathologic
- HIGH values indicate better function/capacity/reserve
- Physiologic or functional ceiling exists but is desirable
- Represents protective factors or functional capacity

**Common Examples:**
- **Cardiorespiratory fitness:** VO2max, exercise capacity
- **Functional capacity:** Grip strength, 6-minute walk distance, FEV1
- **Kidney function:** eGFR (with caveat about hyperfiltration >120)
- **Protective factors:** HDL cholesterol (moderate ceiling concern)
- **Nutritional status:** Albumin, prealbumin (dehydration artifact >5.5)
- **Bone density:** T-score
- **Muscle mass:** Lean body mass, FFMI

### Mathematical Framework

**INPUTS:**
1. **Actual Value (V):** Patient's measured value
2. **Target Value (T):** Minimum acceptable or "good" level
3. **Standard Deviation (SD):** Clinical variability
4. **Penalty Coefficient (Î²):** Penalty rate for values below target
5. **Ceiling Value (C):** Physiologic maximum or plateau point
6. **Reward Coefficient (Î³):** Reward rate for exceeding target (optional)

**STEP 1: Calculate Z-Score**
```
z = (V - T) / SD
```

**STEP 2: Calculate Score**

**For values BELOW target (z < 0):**
```
Score = 85 Ã— e^(-Î² Ã— |z|Â²)

where Î² = penalty coefficient (typically 0.20-0.30)
```

**For values AT target (z = 0):**
```
Score = 85 (at acceptable minimum)
```

**For values ABOVE target (z > 0):**

**Option A: Linear reward (simple)**
```
Score = 85 + (15 Ã— z / z_ceiling)

where z_ceiling = (C - T) / SD
Maximum score approaches 100 as value approaches ceiling
```

**Option B: Logarithmic reward (physiologic ceiling)**
```
Score = 85 + 15 Ã— (1 - e^(-Î³ Ã— z))

where Î³ = reward coefficient (typically 0.3-0.5)
Asymptotically approaches 100, never exceeds
```

**STEP 3: Apply Ceiling**
```
Score_final = MIN(100, Score)
```

### Worked Example 1: VO2max (Cardiorespiratory Fitness)

**Patient:** 45-year-old male  
**Target (T):** 38 mL/kg/min (50th percentile "good" fitness for age)  
**SD:** 8 mL/kg/min  
**Ceiling (C):** 70 mL/kg/min (elite athlete range)  
**Coefficients:** Î² = 0.25 (penalty below), Î³ = 0.4 (reward above)

**Scenario A: Patient VO2max = 28 mL/kg/min (Poor Fitness)**
```
z = (28 - 38) / 8 = -1.25
Score = 85 Ã— e^(-0.25 Ã— 1.25Â²) = 85 Ã— e^(-0.391) = 85 Ã— 0.677 = 58
Color: YELLOW
Interpretation: "Below target - Fair cardiorespiratory fitness. Regular aerobic exercise recommended."
```

**Scenario B: Patient VO2max = 38 mL/kg/min (At Target)**
```
z = 0
Score = 85
Color: GREEN
Interpretation: "Good fitness - At target for your age. Maintain regular exercise."
```

**Scenario C: Patient VO2max = 52 mL/kg/min (Excellent Fitness)**
```
z = (52 - 38) / 8 = +1.75
Score = 85 + 15 Ã— (1 - e^(-0.4 Ã— 1.75)) = 85 + 15 Ã— (1 - e^(-0.7))
     = 85 + 15 Ã— (1 - 0.497) = 85 + 15 Ã— 0.503 = 85 + 7.5 = 92.5 â‰ˆ 93
Color: GREEN
Interpretation: "Excellent - Well above target. Elite cardiorespiratory fitness!"
```

**Scenario D: Patient VO2max = 65 mL/kg/min (Elite Athlete)**
```
z = (65 - 38) / 8 = +3.375
Score = 85 + 15 Ã— (1 - e^(-0.4 Ã— 3.375)) = 85 + 15 Ã— (1 - e^(-1.35))
     = 85 + 15 Ã— (1 - 0.259) = 85 + 15 Ã— 0.741 = 85 + 11.1 = 96
Color: GREEN
Interpretation: "Exceptional - Elite athlete level fitness!"
```

### Worked Example 2: eGFR (Kidney Function with Hyperfiltration Caveat)

**Patient:** 55-year-old with diabetes  
**Target (T):** 90 mL/min/1.73mÂ² (normal kidney function)  
**SD:** 15 mL/min/1.73mÂ²  
**Ceiling concern:** >120 may indicate hyperfiltration (early diabetic nephropathy)  
**Coefficients:** Î² = 0.25 (penalty below), Î³ = 0.3 (modest reward above, with caution)

**Scenario A: Patient eGFR = 55 mL/min/1.73mÂ² (CKD Stage 3a)**
```
z = (55 - 90) / 15 = -2.33
Score = 85 Ã— e^(-0.25 Ã— 2.33Â²) = 85 Ã— e^(-1.36) = 85 Ã— 0.257 = 22
Color: RED
Alert: "LOW - Stage 3a Chronic Kidney Disease. Nephrology referral needed."
```

**Scenario B: Patient eGFR = 90 mL/min/1.73mÂ² (Normal)**
```
z = 0
Score = 85
Color: GREEN
Interpretation: "Normal kidney function for your age."
```

**Scenario C: Patient eGFR = 105 mL/min/1.73mÂ² (Above Normal)**
```
z = (105 - 90) / 15 = +1.0
Score = 85 + 15 Ã— (1 - e^(-0.3 Ã— 1.0)) = 85 + 15 Ã— (1 - 0.741) = 85 + 3.9 = 89
Color: GREEN
Interpretation: "Excellent kidney function."
```

**Scenario D: Patient eGFR = 135 mL/min/1.73mÂ² (Hyperfiltration in Diabetic)**
```
z = (135 - 90) / 15 = +3.0
Score = 85 + 15 Ã— (1 - e^(-0.3 Ã— 3.0)) = 85 + 15 Ã— (1 - 0.407) = 85 + 8.9 = 94

BUT: Clinical context matters
IF patient has diabetes: Flag for hyperfiltration
Alert: "VERY HIGH - May indicate hyperfiltration (early kidney stress in diabetes). Monitor closely."
Color: YELLOW (override GREEN due to context)
```

**This demonstrates context-dependent interpretation - same eGFR can be excellent in healthy person, concerning in diabetic.**

### Clinical Zone Mapping

**Example: eGFR (CKD Stages)**
```
Clinical Zones (KDIGO):
- â‰¥90 mL/min: "Normal Kidney Function" (GREEN)
- 60-89 mL/min: "Mildly Decreased" (YELLOW if elderly/expected, ORANGE if young)
- 45-59 mL/min: "Mild-Moderate Decrease (Stage 3a CKD)" (ORANGE)
- 30-44 mL/min: "Moderate-Severe Decrease (Stage 3b CKD)" (ORANGE)
- 15-29 mL/min: "Severe Decrease (Stage 4 CKD)" (RED)
- <15 mL/min: "Kidney Failure (Stage 5 CKD)" (RED - Critical)
```

---

## METHOD 4: CLINICAL CATEGORY-BASED NORMALIZATION

### When to Use

**Clinical Criteria:**
- Established clinical risk categories or diagnostic thresholds exist
- Categories based on large outcome studies (not arbitrary)
- Nonlinear relationship between value and risk
- Standard of care uses categorical interpretation

**Common Examples:**
- **hsCRP:** CV risk categories (<1, 1-3, >3 mg/L)
- **HbA1c:** Diagnostic categories (normal, prediabetes, diabetes)
- **Blood Pressure:** JNC categories (normal, elevated, Stage 1/2 HTN)
- **BMI:** Weight categories (underweight, normal, overweight, obese classes)
- **Bone density:** T-score categories (normal, osteopenia, osteoporosis)

### Mathematical Framework

**INPUTS:**
1. **Actual Value (V):** Patient's measured value
2. **Clinical Categories:** Defined threshold ranges
3. **Category Scores:** Pre-assigned scores for each category
4. **Interpolation:** Linear interpolation within categories (optional)

**APPROACH:**

**STEP 1: Identify Category**
```
Determine which clinical category V falls into
```

**STEP 2: Assign Base Score**
```
Each category has a pre-defined score range
```

**STEP 3: Interpolate Within Category (Optional)**
```
For smooth transitions, interpolate linearly within category bounds

Score = Score_low + (V - V_low) / (V_high - V_low) Ã— (Score_high - Score_low)

where:
- V_low, V_high = category boundaries
- Score_low, Score_high = score boundaries for category
```

### Worked Example: HbA1c Diagnostic Categories

**Clinical Categories (ADA):**
- <5.7%: Normal (non-diabetic)
- 5.7-6.4%: Prediabetes
- 6.5-7.0%: Diabetes, excellent control
- 7.1-8.0%: Diabetes, good control
- 8.1-9.0%: Diabetes, fair control
- >9.0%: Diabetes, poor control

**Category Score Assignment:**

| HbA1c Range | Category | Score Range | Color |
|-------------|----------|-------------|-------|
| <5.0% | Too Low (possible hypoglycemia) | 70-75 | YELLOW |
| 5.0-5.6% | Normal | 82-88 | GREEN |
| 5.7-6.4% | Prediabetes | 60-75 | YELLOW |
| 6.5-7.0% | Diabetes - Excellent | 75-82 | GREEN |
| 7.1-8.0% | Diabetes - Good | 55-70 | YELLOW |
| 8.1-9.0% | Diabetes - Fair | 30-50 | ORANGE |
| 9.1-10.0% | Diabetes - Poor | 15-25 | RED |
| >10.0% | Diabetes - Very Poor | 5-10 | RED |

**Scenario A: Patient HbA1c = 5.3% (Normal, Non-Diabetic)**
```
Category: Normal (5.0-5.6%)
Position within category: (5.3 - 5.0) / (5.6 - 5.0) = 0.5 (middle)
Score = 82 + 0.5 Ã— (88 - 82) = 82 + 3 = 85
Color: GREEN
Interpretation: "Normal - Excellent glucose control"
```

**Scenario B: Patient HbA1c = 6.0% (Prediabetes)**
```
Category: Prediabetes (5.7-6.4%)
Position: (6.0 - 5.7) / (6.4 - 5.7) = 0.43
Score = 60 + 0.43 Ã— (75 - 60) = 60 + 6.5 = 66.5 â‰ˆ 67
Color: YELLOW
Interpretation: "Prediabetes - Increased risk of developing diabetes. Lifestyle changes recommended."
```

**Scenario C: Patient HbA1c = 7.8% (Diabetes, Good Control)**
```
Category: Diabetes - Good (7.1-8.0%)
Position: (7.8 - 7.1) / (8.0 - 7.1) = 0.78
Score = 55 + 0.78 Ã— (70 - 55) = 55 + 11.7 = 66.7 â‰ˆ 67
Color: YELLOW
Interpretation: "Good diabetes control. Work with your doctor to optimize further."
```

**Scenario D: Patient HbA1c = 10.5% (Very Poor Control)**
```
Category: Very Poor (>10.0%)
Score = 8 (within 5-10 range)
Color: RED
Critical Alert: "VERY POOR diabetes control. High risk of complications. Contact endocrinologist urgently."
```

### Worked Example: BMI Categories

**Clinical Categories (CDC):**

| BMI Range | Category | Score | Color |
|-----------|----------|-------|-------|
| <16.0 | Severe Underweight | 20 | RED |
| 16.0-18.4 | Underweight | 50 | ORANGE |
| 18.5-24.9 | Normal Weight | 85 | GREEN |
| 25.0-29.9 | Overweight | 65 | YELLOW |
| 30.0-34.9 | Obese Class I | 40 | ORANGE |
| 35.0-39.9 | Obese Class II | 25 | RED |
| â‰¥40.0 | Obese Class III | 10 | RED |

**Note:** Interpolation within categories smooths transitions.

---

## METHOD 5: BINARY AND ORDINAL NORMALIZATION

### Binary Parameters (Present/Absent)

**Use Case:**
- Past medical history (MI, stroke, cancer)
- Risk factors (smoking, family history)
- Presence/absence findings (murmur, edema)

**Scoring Approach:**

**Base Binary:**
```
IF absent: Score = 85 (no risk factor)
IF present: Score = Base_penalty (e.g., 30-50 depending on severity)
```

**Severity-Modified Binary:**
```
IF absent: Score = 85
IF present - mild: Score = 60
IF present - moderate: Score = 40
IF present - severe: Score = 20
```

**Example: Prior Myocardial Infarction**
```
IF no prior MI: Score = 85
IF prior MI (>5 years ago, no complications): Score = 50
IF prior MI (recent or with complications): Score = 30
IF prior MI with reduced EF: Score = 20
```

### Ordinal Parameters (Graded Scales)

**Use Case:**
- Functional status scales (NYHA, ECOG)
- Pain scales (0-10)
- Edema grading (0-4+)
- Symptom severity scales

**Scoring Approach:**

**Direct Mapping:**
```
Each ordinal level maps to a pre-defined score
```

**Example: NYHA Heart Failure Classification**

| NYHA Class | Description | Score | Color |
|------------|-------------|-------|-------|
| Class I | No symptoms with ordinary activity | 85 | GREEN |
| Class II | Slight limitation, comfortable at rest | 65 | YELLOW |
| Class III | Marked limitation, comfortable only at rest | 35 | ORANGE |
| Class IV | Symptoms at rest, any activity worsens | 15 | RED |

**Example: Pain Scale (0-10)**

| Pain Level | Score | Color |
|------------|-------|-------|
| 0 (No pain) | 85 | GREEN |
| 1-3 (Mild) | 70-75 | YELLOW |
| 4-6 (Moderate) | 45-60 | ORANGE |
| 7-9 (Severe) | 20-35 | RED |
| 10 (Worst possible) | 10 | RED |

---

## PERSONALIZED TARGET DETERMINATION

### Framework for Every Parameter

For each parameter in the system, we must define logic to determine the patient's personalized target (z = 0).

**INPUTS (Patient Characteristics):**
1. Age
2. Sex
3. Comorbidities (diabetes, CKD, CHF, CAD, COPD, etc.)
4. Current medications
5. Risk factors (smoking, family history)
6. Race/ethnicity (when clinically relevant per guidelines)
7. Special populations (pregnancy, athletes, post-surgery, etc.)

### Target Determination Methods

#### Method A: Guideline-Based Decision Trees

**Use When:** Strong clinical guidelines exist with specific targets

**Example Structure:**
```
IF patient has [condition A] AND [risk factor B]:
  Target = X (guideline reference)
ELSE IF patient has [condition C]:
  Target = Y (guideline reference)
ELSE IF age > [threshold] AND [other criteria]:
  Target = Z (guideline reference)
ELSE:
  Target = Default (general population guideline)
```

#### Method B: Age/Sex-Stratified Tables

**Use When:** Parameters vary significantly by demographics but no disease-specific targets

**Example Structure:**
```
Lookup table by age and sex:

Males:
  Age 18-39: Target = X
  Age 40-59: Target = Y
  Age 60+: Target = Z
  
Females:
  Age 18-39: Target = A
  Age 40-59: Target = B
  Age 60+: Target = C
  
  IF pregnant: Target = D (pregnancy-specific)
  IF post-menopausal: Adjust by factor
```

#### Method C: Risk Calculator-Informed

**Use When:** Established risk calculators guide target selection

**Example: ASCVD Risk Calculator for Lipid Targets**
```
Calculate 10-year ASCVD risk:
  Inputs: Age, sex, race, TC, HDL, SBP, BP meds, diabetes, smoker
  
IF risk â‰¥20% OR known ASCVD: LDL target = 55-70 mg/dL (high-risk)
ELSE IF risk 7.5-19.9%: LDL target = 100 mg/dL (intermediate-risk)
ELSE IF risk <7.5%: LDL target = 100 mg/dL (low-risk, lifestyle focus)

IF diabetes + age >40: LDL target = 70 mg/dL regardless of risk score
```

#### Method D: Comorbidity-Adjusted Targets

**Use When:** Specific conditions alter optimal targets

**Example: Blood Pressure Targets**
```
Base target (healthy adult <65): SBP = 120 mmHg

IF age â‰¥65 AND no major comorbidities:
  Target SBP = 130 mmHg (SPRINT trial)

IF diabetes:
  Target SBP = 130 mmHg (ADA 2023)
  
IF CKD with proteinuria (UACR >300):
  Target SBP = 120 mmHg (KDIGO)
  
IF CKD without proteinuria:
  Target SBP = 130 mmHg
  
IF CHF:
  Target SBP = 120-130 mmHg (maintain perfusion, avoid hypotension)
  
IF prior stroke:
  Target SBP = 130 mmHg (ASA/AHA)

IF multiple conditions: Use most stringent target OR shared decision-making
```

### Standard Deviation Sources

For each parameter, SD must be sourced from:
1. **Published literature:** Clinical studies, population data
2. **Laboratory reference ranges:** SD = (Upper Limit - Lower Limit) / 4 (approximate)
3. **Clinical experience:** Expert consensus when literature sparse
4. **Risk curve slopes:** For parameters with established risk relationships

**Documentation Required:**
- SD value with units
- Source citation
- Validation date
- Review schedule

---

## PARAMETER CLASSIFICATION DECISION TREE

### Systematic Approach to Classify ANY Parameter

**STEP 1: Ask Core Questions**

1. **Can this parameter be TOO LOW?**
   - What happens physiologically?
   - What are clinical outcomes?
   - Is this documented in literature?

2. **Can this parameter be TOO HIGH?**
   - What happens physiologically?
   - What are clinical outcomes?
   - Is this documented in literature?

3. **Are both directions of EQUAL concern?**
   - Same severity of outcomes?
   - Same speed of harm?
   - Same frequency of occurrence?

**STEP 2: Apply Decision Logic**

```
IF both directions have documented adverse outcomes:
  â†’ BIDIRECTIONAL
  
  IF severity/frequency roughly equal:
    â†’ Symmetric bidirectional
  ELSE:
    â†’ Asymmetric bidirectional
    â†’ Identify primary vs secondary concern
    
ELSE IF only HIGH values pathologic:
  â†’ UNIDIRECTIONAL - Lower is Better
  â†’ Confirm: Is there a physiologic floor?
  
ELSE IF only LOW values pathologic:
  â†’ UNIDIRECTIONAL - Higher is Better
  â†’ Confirm: Is there a physiologic ceiling?
  â†’ Check: Does very high indicate pathology? (e.g., hyperfiltration)
```

**STEP 3: Consider Context**

- Acute vs chronic presentations
- Treated vs untreated patients
- Age-dependent interpretations
- Artifact vs true pathology (e.g., high albumin = dehydration, not good)

**STEP 4: Check for Established Categories**

```
IF clinical guidelines define risk/diagnostic categories:
  â†’ Consider METHOD 4 (Category-Based) in addition to or instead of z-score
```

---

## IMPLEMENTATION CHECKLIST

For each parameter added to the system, complete:

### 1. Clinical Classification
- [ ] Parameter type identified (bidirectional/unidirectional/category/binary/ordinal)
- [ ] Asymmetry characterized (if applicable)
- [ ] Clinical rationale documented
- [ ] Literature evidence cited
- [ ] Optional transform needed? (see above)

### 2. Target Determination Logic
- [ ] Personalization factors identified (age, sex, conditions, meds)
- [ ] Decision tree or lookup table created (see methods below)
- [ ] Guideline sources cited with version/date
- [ ] Edge cases considered
- [ ] Default values specified
- [ ] Context rules identified (see CONTEXT_RULES.md)

### 3. Normalization Parameters
- [ ] Standard deviation sourced and documented (see CALIBRATION_VALIDATION.md)
- [ ] Penalty coefficients selected and justified (see CALIBRATION_VALIDATION.md)
- [ ] Coefficients validated against clinical anchors (see CALIBRATION_VALIDATION.md)
- [ ] Ceiling/floor values defined
- [ ] Scoring formula specified completely

### 4. Clinical Zones
- [ ] Zone thresholds defined (numerical boundaries)
- [ ] Zone labels written (plain language)
- [ ] Color + shape + text assignments specified (accessibility)
- [ ] Clinical interpretation for each zone documented

### 5. Critical Thresholds
- [ ] Life-threatening values identified
- [ ] Urgent values identified
- [ ] Alert messages written (patient and clinician versions)
- [ ] Recommended actions specified

### 6. Temporal Considerations
- [ ] Single reading vs trend approach determined (see TEMPORAL_SCORING.md)
- [ ] Stability scoring requirements specified (see TEMPORAL_SCORING.md)
- [ ] Aberrant value handling defined (see TEMPORAL_SCORING.md)

### 7. Validation
- [ ] Worked examples completed (minimum 3 scenarios)
- [ ] Edge cases tested
- [ ] Clinical review completed (see CALIBRATION_VALIDATION.md)
- [ ] Cross-parameter consistency validated (see CALIBRATION_VALIDATION.md)
- [ ] Documentation approved

---

## VISUAL DISPLAY REQUIREMENTS

### Mandatory Components for Each Parameter Display

**Level 3 (Parameter Detail View):**

1. **Patient's Value**
   - Numerical value with units
   - Large, prominent display
   - Color-coded by zone

2. **Personalized Target**
   - "Your target: [value] [units]"
   - Explanation of why this is their target (if requested)

3. **Clinical Zone Visualization**
   - Horizontal scale showing all zones
   - Color-coded segments with labels
   - Patient's position marked clearly
   - Target position marked

4. **Score and Status**
   - Normalized score (0-100)
   - Color indicator
   - Status word (Optimal/Good/Fair/Poor/Critical)

5. **Interpretation**
   - Plain language explanation
   - "What this means" - clinical significance
   - "What to do" - recommended action

6. **Trend (if available)**
   - Sparkline of recent values
   - Arrow indicating direction (â†‘â†“â†’)
   - Date of last measurement

7. **Context Button**
   - "Learn more about [parameter name]"
   - Expands to educational content

**Example Mockup (Text):**
```
â•”â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•—
â•‘  SYSTOLIC BLOOD PRESSURE                                   â•‘
â•‘                                                             â•‘
â•‘  Your value: 142 mmHg                    Score: 38 ðŸŸ      â•‘
â•‘  Your target: 130 mmHg                                     â•‘
â•‘                                                             â•‘
â•‘  [â”â”â”â”â”â”|â”â”â”â”â”â”|â”â”â”â”â”â”|â”â”â”â”â”â”|â”â”â”â”â”â”]                    â•‘
â•‘    90   110   130   150   170   190                        â•‘
â•‘   Hypo  Normal  Elevated  Stage1  Stage2                   â•‘
â•‘                    â†‘ YOU                                    â•‘
â•‘                                                             â•‘
â•‘  Status: Stage 1 Hypertension - Act Soon                   â•‘
â•‘                                                             â•‘
â•‘  What this means:                                           â•‘
â•‘  Your blood pressure is above your target range. This      â•‘
â•‘  increases your risk of heart attack and stroke.           â•‘
â•‘                                                             â•‘
â•‘  What to do:                                                â•‘
â•‘  Contact your doctor within 1-2 weeks to discuss blood     â•‘
â•‘  pressure management. Monitor at home if possible.         â•‘
â•‘                                                             â•‘
â•‘  Trend: â†‘ Increasing (Last 3 readings)                     â•‘
â•‘  Last measured: Nov 10, 2025                               â•‘
â•‘                                                             â•‘
â•‘  [Learn more about blood pressure] [View history]          â•‘
â•šâ•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

---

## QUALITY ASSURANCE

### Validation Requirements

**For Each Parameter:**

1. **Mathematical Validation**
   - Hand-calculate 3+ scenarios
   - Verify formula implementation
   - Test edge cases (very high, very low, at boundaries)
   - Confirm score ranges (5-100)

2. **Clinical Validation**
   - Scenarios reviewed by clinician
   - Interpretations clinically accurate
   - Alert thresholds appropriate
   - Recommendations evidence-based

3. **User Experience Validation**
   - Plain language comprehensible (6th-8th grade reading level)
   - Visual display clear and unambiguous
   - Actions specific and achievable
   - No medical jargon without explanation

4. **Documentation Review**
   - All formulas complete
   - All sources cited
   - All decision trees explicit
   - All edge cases addressed

---

## GLOSSARY

**Z-Score:** Statistical measure of how many standard deviations a value is from the target. For our system, z = 0 represents the patient's personalized clinical target, NOT population mean.

**Standard Deviation (SD):** Measure of variability around the target. Sourced from clinical literature, population data, or laboratory reference ranges.

**Penalty Coefficient:** Parameter controlling how steeply scores decrease as values deviate from target. Higher coefficients = steeper penalties = more concern about deviation.

**Personalized Target:** The optimal value for a specific patient based on their age, sex, comorbidities, medications, and risk factors. This is z = 0 for that patient.

**Clinical Zones:** Ranges of parameter values with established clinical labels (e.g., "Normal," "Stage 1 Hypertension"). Used for dashboard display and patient communication.

**Bidirectional Parameter:** A parameter where deviations in BOTH directions (too high and too low) are pathologic.

**Unidirectional Parameter:** A parameter where only ONE direction of deviation is pathologic. The other direction approaches a physiologic floor or ceiling.

**Asymmetric Bidirectional:** A bidirectional parameter where one direction of deviation is of greater clinical concern than the other (different penalty rates).

---

## REVISION HISTORY

**Version 2.0.0 - November 12, 2025**
- Split from single comprehensive document into 4-document framework
- Added tri-state scoring (Numeric/NS/NA)
- Added explainability requirements
- Added accessibility requirements (color + shape + text)
- Added optional transformation guidance for skewed distributions
- Added temporal scoring principles
- Added cross-references to companion documents
- Slimmed core document to focus on normalization methods

**Version 1.0.0 - November 12, 2025**
- Initial comprehensive specification (single document)
- Five normalization methods defined with worked examples
- Personalized target determination framework established
- Z = 0 â†’ 85 points baseline established

---

## RELATED DOCUMENTS

### Companion Documents (Parameter Scoring Framework)
- `CALIBRATION_VALIDATION.md` - Coefficient optimization, clinical anchoring, governance
- `CONTEXT_RULES.md` - Patient-specific adjustments and scoring overrides
- `TEMPORAL_SCORING.md` - Point vs stability scores, aberrant value handling

### Project Architecture
- `PROJECT_SPECIFICATION_v2.md` - Master project vision (24-cell matrix, aggregation hierarchy)
- `PROJECT_INSTRUCTIONS.md` - Team methodology and standards

### Next Implementation Documents
- `PARAMETERS_VITAL_SIGNS.md` - Vital signs parameter specifications (NEXT)
- `PARAMETERS_BASIC_LABS.md` - Laboratory parameter specifications (PLANNED)
- `SYSTEM_DOMAIN_SCORING.md` - Aggregation to system scores (PLANNED)
- `COMPOSITE_SCORING.md` - Overall health score calculation (PLANNED)

---

**END OF PARAMETER NORMALIZATION SPECIFICATION**

*This document defines the core normalization methods. Read companion documents for complete implementation guidance.*
