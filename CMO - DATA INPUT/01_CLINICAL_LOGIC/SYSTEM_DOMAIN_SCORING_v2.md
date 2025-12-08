# SYSTEM & DOMAIN SCORING SPECIFICATION
## Patient Health Dashboard - Aggregation Framework

**Document Type:** Core Clinical Logic  
**Version:** 2.0.0  
**Date:** November 12, 2025  
**Status:** Critical Foundation Document  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture (24-cell matrix concept, baseline conventions)
- Parameter Scoring Framework:
  - `PARAMETER_NORMALIZATION_v2.md` - How individual parameters are scored (0-100)
  - `CALIBRATION_VALIDATION.md` - Coefficient optimization and validation
  - `CONTEXT_RULES.md` - Patient-specific adjustments
  - `TEMPORAL_SCORING.md` - Point vs stability vs display scores

**This document connects to:**
- `COMPOSITE_SCORING.md` - Next layer up (system Ã¢â€ â€™ overall health score)
- All `PARAMETERS_*.md` files - Individual parameter weight assignments

---

## DOCUMENT PURPOSE

This specification defines how **individual parameter scores (0-100) aggregate into system health scores** through the 24-cell health matrix.

**The aggregation hierarchy:**
```
Individual Parameters (0-100 normalized scores)
    Ã¢â€ â€œ [weighted by 24-cell matrix]
Domain Scores per System (Structure, Function, Risk: 0-100 each)
    Ã¢â€ â€œ [weighted combination: 25%, 50%, 25%]
System Health Scores (8 systems: 0-100 each)
```

**This document provides:**
1. Baseline scoring conventions (85 vs 50)
2. The 24-cell weight matrix framework
3. Parameter weight assignment methodology
4. Domain score calculation formulas with weight-based completeness
5. Tri-state score handling (Numeric/NS/NA)
6. System score calculation formulas
7. Worked examples for cardiovascular system
8. Weight assignment templates and QA guidelines

---

## BASELINE SCORING CONVENTIONS

### The 85-Point Standard

**Critical alignment with Parameter Scoring Framework:**

**At Personalized Target (z-score = 0):**
- **Parameter scores: 85 points**
- This propagates through domain and system scores
- A well-controlled system with all parameters at target Ã¢â€ â€™ System score Ã¢â€°Ë† 85

**The Role of 50 Points:**
- **50 = Neutral/Unknown** (NOT "normal health")
- Used ONLY for:
  - Incomplete data blending (completeness adjustment)
  - Truly missing or unscored composites
  - Never for measured parameters at target

**Why 85, not 50?**
- **Clinically motivating:** Patients at target feel successful (B+ grade)
- **Room for excellence:** Scores 86-100 achievable through sustained optimal health
- **Absorbs noise:** Normal measurement variability doesn't drop scores below green zone
- **Consistent across levels:** Parameter Ã¢â€ â€™ Domain Ã¢â€ â€™ System Ã¢â€ â€™ Overall all use same baseline

**Cross-Reference:**
- See `PARAMETER_NORMALIZATION_v2.md` Principle 2 for parameter-level rationale
- See `PROJECT_SPECIFICATION_v2.md` Core Principle #4 for project-wide alignment

---

## THE 24-CELL HEALTH MATRIX

### Matrix Structure

**8 Organ Systems Ãƒâ€” 3 Evaluation Domains = 24 Cells**

| System | Structure (Anatomy) | Function (Physiology) | Risk (Prognosis) |
|--------|--------------------|-----------------------|------------------|
| **Neurological** | Brain/nerve integrity | Cognitive/motor function | Stroke/dementia risk |
| **Cardiovascular** | Vessel/heart anatomy | Cardiac output/perfusion | MI/CHF risk |
| **Respiratory** | Airway/lung structure | Gas exchange capacity | COPD/failure risk |
| **Metabolic** | GI/liver/pancreas anatomy | Metabolic function | Diabetes/cirrhosis risk |
| **Renal** | Kidney structure | Filtration capacity | CKD progression risk |
| **Musculoskeletal** | Bone/joint/muscle integrity | Strength/mobility | Fracture/disability risk |
| **Immune** | Lymph/immune organ structure | Infection defense | Cancer/autoimmune risk |
| **Reproductive/Endocrine** | Gland/organ structure | Hormone production | Hormone disorder risk |

### Key Principle

**Every parameter contributes to multiple cells with different weights.**

Example: Systolic Blood Pressure (SBP)
- Cardiovascular-Structure: 10% (vessel stress/damage)
- Cardiovascular-Function: 80% (perfusion adequacy)
- Cardiovascular-Risk: 90% (future MI/stroke)
- Metabolic-Risk: 15% (metabolic syndrome indicator)
- Renal-Risk: 10% (hypertension Ã¢â€ â€™ CKD)
- All other cells: 0%

**Total across all 24 cells: 205%** (weights can exceed 100% total because they're applied to different domains)

**Note on Multi-System Contributions:**
- This document does NOT attempt to de-duplicate parameter effects across systems
- SBP legitimately affects several systemsÃ¢â‚¬â€this is physiologically accurate
- Any global "double counting" concerns are handled at the **COMPOSITE_SCORING** layer via system-level weights, not by restricting cross-system contributions here

---

## PARAMETER WEIGHT ASSIGNMENT FRAMEWORK

### Weight Matrix for Each Parameter

Every parameter receives a **24-cell weight matrix** defining its contribution to each cell.

**Format:**
```
PARAMETER: [Name]
WEIGHT MATRIX (% contribution to each cell):

                Structure  Function  Risk
Neurological         X%        Y%      Z%
Cardiovascular       X%        Y%      Z%
Respiratory          X%        Y%      Z%
Metabolic            X%        Y%      Z%
Renal                X%        Y%      Z%
Musculoskeletal      X%        Y%      Z%
Immune               X%        Y%      Z%
Reproductive         X%        Y%      Z%

RATIONALE: [Why these weights]
EVIDENCE: [Citations]
VERSION: [X.Y]
VALIDATED BY: [Names]
RECOMMENDED PARAMETERS: [List of parameters typically measured for this domain]
```

**Note on Recommended Parameters:**
The "recommended parameters" used for completeness calculations are defined in the parameter library documents (e.g., `PARAMETERS_VITAL_SIGNS.md`, `PARAMETERS_BASIC_LABS.md`) and can be updated over time as evidence evolves.

### Weight Assignment Principles

**Principle 1: Primary vs Related Contributions**
- **Primary system:** Parameter's main system of origin/effect
  - Usually receives highest weights
  - Can contribute to multiple domains within primary system
- **Related systems:** Secondary effects on other systems
  - Typically 20-50% of primary system weights
  - Represents interconnected physiology

**Principle 2: Domain Weighting Logic**

**Structure (Anatomy):**
- Direct evidence of organ damage or integrity
- Imaging findings, tissue architecture
- Examples: LV wall thickness, liver nodules, bone density

**Function (Physiology):**
- Current performance capacity
- How well the organ/system is working NOW
- Examples: EF, FEV1, creatinine clearance, cognitive scores

**Risk (Prognosis):**
- Predictors of future deterioration
- Risk factors for adverse events
- Examples: High BP (future MI), HbA1c (future complications), hsCRP (future CVD)

**Principle 3: Evidence-Based Weighting**
- Weights based on established relationships in medical literature
- Outcome studies, epidemiological data
- Clinical guidelines and consensus

**Principle 4: Weight Semantics**
- **Within a domain:** Only relative weight ratios matter (absolute magnitudes are arbitrary)
- **Across domains:** Each domain is independent (no constraint on total across all 24 cells)
- **Clinical meaning:** Higher weight = stronger contribution to that domain's assessment

---

## WEIGHT ASSIGNMENT METHODOLOGY

### Method 1: Rule-Based Ontology (Auto-Generate Baseline)

**For new parameters, auto-generate starting weights using parameter classification:**

**Step 1: Identify Parameter Class**
- Vital sign (BP, HR, RR, Temp, SpO2)
- Lab - structural marker (albumin, hemoglobin, platelets)
- Lab - functional marker (creatinine, BNP, liver enzymes)
- Lab - risk marker (lipids, HbA1c, hsCRP)
- Imaging - structural finding
- Functional test (VO2max, FEV1, grip strength)
- Clinical assessment (NYHA class, pain scale)

**Step 2: Apply Template Weights**

**Example Template: Vital Sign - Blood Pressure**
```
Primary System: Cardiovascular
Secondary Systems: Renal (related), Metabolic (related)

Auto-weights:
- Cardiovascular-Structure: 10% (vessel damage)
- Cardiovascular-Function: 80% (perfusion)
- Cardiovascular-Risk: 90% (future events)
- Renal-Risk: 10% (HTN Ã¢â€ â€™ CKD)
- Metabolic-Risk: 15% (metabolic syndrome)
```

**Example Template: Lab - Functional Marker (Creatinine)**
```
Primary System: Renal
Secondary Systems: Cardiovascular (related - uremic effects)

Auto-weights:
- Renal-Structure: 20% (kidney damage)
- Renal-Function: 90% (filtration capacity)
- Renal-Risk: 80% (progression to ESRD)
- Cardiovascular-Risk: 15% (CKD Ã¢â€ â€™ CVD)
```

**Step 3: Clinical Validation**
- Present auto-generated weights to clinical panel
- Adjust based on expert consensus
- Document rationale for changes

### Method 2: Expert Panel Assignment (Manual)

**For high-priority or complex parameters:**

**Process:**
1. **Clinical panel** (Ã¢â€°Â¥3 experts from different specialties)
2. **Round 1:** Each expert assigns weights independently
3. **Discussion:** Present differences, discuss evidence
4. **Round 2:** Consensus voting
5. **Documentation:** Record final weights with rationale

**Validation criteria:**
- >80% agreement among panelists
- Evidence-based rationale documented
- Cross-parameter consistency checked

### Method 3: Outcome-Based Weighting (Future Enhancement)

**Use machine learning on patient outcomes:**
- Correlate parameter changes with system-specific outcomes
- Identify strongest predictive relationships
- Generate data-driven weights

**For MVP:** Use Methods 1 and 2 (rule-based + expert validation)

---

## WEIGHT QA GUIDELINES

**Quality assurance for weight assignments:**

1. **Minimum Weight Threshold**
   - Weights <5% may be effectively noise
   - Either set to 0 or document specific rationale

2. **Domain Coverage**
   - Each major domain should have 3-5 substantive contributors (weights Ã¢â€°Â¥20%)
   - Avoid orphaned domains with only 1-2 parameters

3. **Single-Parameter Dominance**
   - If a single parameter carries >70% of total weight in a domain, document why
   - Ensure clinical justification (e.g., EF is legitimately dominant for CV-Function)
   - Flag for review in calibration validation (see `CALIBRATION_VALIDATION.md`)

4. **Cross-Parameter Consistency**
   - Similar clinical contributions should have similar weight magnitudes
   - Example: If hsCRP has 75% CV-Risk weight, troponin should have comparable weight

5. **Evidence Documentation**
   - All weights >20% must have cited evidence or expert consensus rationale
   - Version and approval tracking required

---

## DOMAIN SCORE CALCULATION

### Input: Temporal Display Scores

**Unless otherwise specified for acute contexts, domain calculations use each parameter's Temporal Display Score** as defined in `TEMPORAL_SCORING.md` (hybrid of point and stability scores).

**Exceptions:**
- Acute-only parameters (e.g., troponin in ER) may use point scores only
- Context-specific configurations documented per parameter

### Formula: Weight-Based Average

For each system, calculate 3 domain scores (Structure, Function, Risk):

```
Domain_Score_Raw = ÃŽÂ£(Display_Score Ãƒâ€” Weight) / ÃŽÂ£(Weight)

where:
- Display_Score: Temporal display score (0-100) from TEMPORAL_SCORING.md
- Weight: Parameter's weight for this specific domain (0-100%)
- Sum is over all NUMERIC-scored parameters with weight > 0 for this domain
```

**Simplifying:** Domain score is a weighted average of contributing parameters' display scores.

### Tri-State Score Handling

**The three parameter states from `PARAMETER_NORMALIZATION_v2.md`:**

**NUMERIC (5-100):**
- Valid measurement, successfully normalized
- **Included** in domain calculation with full weight
- Contributes to both numerator and denominator

**NS (No Score - Insufficient Data):**
- Invalid/rejected measurement, QC failure
- **Excluded** from domain calculation (no contribution)
- **Included** in recommended parameter count (lowers completeness)
- Effect: Encourages re-testing

**NA (Not Applicable):**
- Parameter not relevant for this patient (e.g., PSA in women)
- **Excluded** from both domain calculation AND recommended count
- Effect: No penalty for inapplicable parameters

### Completeness Adjustment: Weight-Based

**Problem with count-based completeness:**
- Measuring 5 low-weight parameters appears "complete" but provides little information
- Missing 2 high-weight parameters (e.g., EF, LV wall) creates large information gap

**Solution: Weight-based completeness**

```
Completeness_Ratio = (ÃŽÂ£ weights of NUMERIC-scored parameters) / (ÃŽÂ£ weights of all recommended parameters)

Where:
- Numerator: Sum of weights for parameters with NUMERIC scores
- Denominator: Sum of weights for all recommended parameters (excludes NA)
- NS parameters: weight in denominator only (not numerator)
```

**Adjusted Domain Score:**
```
Domain_Score_Adjusted = (Domain_Score_Raw Ãƒâ€” Completeness_Ratio) + (50 Ãƒâ€” (1 - Completeness_Ratio))
```

**Effect:** 
- Incomplete data pulls score toward neutral 50
- Weight-based: capturing high-yield parameters yields higher completeness
- Prevents overconfidence from sparse data

**Display:** Show both completeness percentage and what it represents:
```
"Cardiovascular Function: 72 (65% of recommended clinical information captured)"
```

### Worked Example: Cardiovascular Function Score

**Scenario: Patient with 5 parameters measured**

| Parameter | Display Score | Weight (CV-Function) | State |
|-----------|---------------|----------------------|-------|
| SBP | 75 | 80% | NUMERIC |
| DBP | 78 | 70% | NUMERIC |
| HR | 82 | 60% | NUMERIC |
| Ejection Fraction | 88 | 100% | NUMERIC |
| BNP | 70 | 85% | NUMERIC |
| Exercise Tolerance | - | 60% | NS (not measured) |
| Cardiac Output | - | 75% | NA (requires cath, not indicated) |
| Troponin | - | 15% | NA (acute marker, not indicated) |
| ECG QRS Duration | - | 25% | NS (not measured) |
| NT-proBNP | - | 80% | NS (alternative to BNP, not both) |

**Step 1: Calculate Raw Domain Score**
```
Numerator = (75Ãƒâ€”0.80) + (78Ãƒâ€”0.70) + (82Ãƒâ€”0.60) + (88Ãƒâ€”1.00) + (70Ãƒâ€”0.85)
         = 60.0 + 54.6 + 49.2 + 88.0 + 59.5
         = 311.3

Denominator = 0.80 + 0.70 + 0.60 + 1.00 + 0.85 = 3.95

CV-Function Score (raw) = 311.3 / 3.95 = 78.8
```

**Step 2: Calculate Weight-Based Completeness**
```
Measured weights (NUMERIC):
SBP(80%) + DBP(70%) + HR(60%) + EF(100%) + BNP(85%) = 395%

Recommended weights (all except NA):
All above + Exercise(60%) + ECG(25%) + NT-proBNP(80%) = 560%
(Cardiac Output and Troponin excluded as NA)

Completeness = 395% / 560% = 0.71 (71%)
```

**Step 3: Adjust for Completeness**
```
Adjusted Score = (78.8 Ãƒâ€” 0.71) + (50 Ãƒâ€” 0.29) = 55.9 + 14.5 = 70.4 Ã¢â€°Ë† 70
```

**Display:**
```
Cardiovascular Function: 70 (71% of recommended information captured)
Ã¢â€ â€˜ "Key measurements obtained. Additional testing (exercise tolerance, ECG timing) 
   would provide fuller assessment."
```

**Comparison to Count-Based:**
- Count-based: 5 measured / 8 recommended = 62.5% (would give score 68)
- Weight-based: 71% (gives score 70)
- Difference is small here, but becomes significant when high-weight parameters missing

---

## SYSTEM SCORE CALCULATION

### Formula

Each system's overall health score combines its 3 domain scores:

```
System_Score = (Structure Ãƒâ€” 0.25) + (Function Ãƒâ€” 0.50) + (Risk Ãƒâ€” 0.25)
```

**Weighting rationale:**
- **Function (50%):** Most important - how well system works NOW
- **Structure (25%):** Important - foundation for function
- **Risk (25%):** Important - future trajectory

**These weights are fixed across all systems.**

### Color Zone Alignment

**System scores use the same universal color zones as parameter scores:**
- **GREEN (75-100):** Optimal - maintain approach
- **YELLOW (60-74):** Monitor - good with room for improvement
- **ORANGE (40-59):** Act Soon - attention needed
- **RED (0-39):** Urgent - intervention required

(Reference: `PROJECT_SPECIFICATION_v2.md` and `PROJECT_INSTRUCTIONS.md`)

### Worked Example: Cardiovascular System Score

**Given domain scores:**
- Cardiovascular-Structure: 72 (vessel/heart anatomy)
- Cardiovascular-Function: 70 (current cardiac performance)
- Cardiovascular-Risk: 65 (future event probability)

**Calculation:**
```
CV System Score = (72 Ãƒâ€” 0.25) + (70 Ãƒâ€” 0.50) + (65 Ãƒâ€” 0.25)
                = 18 + 35 + 16.25
                = 69.25
                Ã¢â€°Ë† 69
```

**Color Zone:** YELLOW (60-74) - Good health with improvement opportunities

**Display:**
```
CARDIOVASCULAR HEALTH: 69 (YELLOW - Monitor)

Breakdown:
- Structure: 72 (Good - vessel integrity preserved)
- Function: 70 (Good - cardiac output adequate)
- Risk: 65 (Fair - moderate risk of future events)

Action: Continue routine monitoring. Consider optimization strategies 
for cardiovascular risk factors. Follow-up in 3-6 months.
```

---

## CALCULATION STEPS SUMMARY

**For IT implementation, the calculation sequence is:**

**1. Gather Parameter Data**
- Retrieve all measured parameters for patient
- Identify state (NUMERIC / NS / NA) for each
- Obtain temporal display scores for NUMERIC parameters

**2. For Each Domain (24 total):**
- Filter to parameters with weight >0 for this domain
- Calculate weighted sum of NUMERIC parameter scores
- Calculate sum of weights (NUMERIC only)
- Compute raw domain score = weighted sum / weight sum
- Calculate weight-based completeness ratio
- Apply completeness adjustment: blend with 50
- Result: Adjusted domain score (0-100)

**3. For Each System (8 total):**
- Retrieve 3 adjusted domain scores (Structure, Function, Risk)
- Apply fixed weighting: 25% / 50% / 25%
- Result: System health score (0-100)

**4. Map to Color Zones**
- Apply universal thresholds to all scores
- Generate plain language interpretations

**5. Prepare Transparency Display**
- Identify top 3 positive contributors ("What's Working Well")
- Identify top 3 negative contributors ("What Needs Work")
- See `TRANSPARENCY_DISPLAY.md` for detailed logic

---

## APPENDIX A: COMPLETE CARDIOVASCULAR WORKED EXAMPLE

### Patient Profile
- 55-year-old male
- Diabetes, hypertension
- Current medications: Metformin, Lisinopril

### Parameters Measured

| Parameter | Raw Value | Display Score | CV-Struct | CV-Funct | CV-Risk | State |
|-----------|-----------|---------------|-----------|----------|---------|-------|
| SBP | 142 mmHg | 45 | 10% | 80% | 90% | NUMERIC |
| DBP | 88 mmHg | 65 | 10% | 70% | 85% | NUMERIC |
| Heart Rate | 78 bpm | 80 | 0% | 60% | 20% | NUMERIC |
| Ejection Fraction | 58% | 85 | 30% | 100% | 40% | NUMERIC |
| LV Wall Thickness | 1.1 cm | 82 | 90% | 20% | 30% | NUMERIC |
| BNP | 85 pg/mL | 78 | 5% | 85% | 70% | NUMERIC |
| Troponin | <0.01 ng/mL | 85 | 5% | 15% | 80% | NUMERIC |
| LDL | 135 mg/dL | 58 | 0% | 0% | 85% | NUMERIC |
| HDL | 48 mg/dL | 72 | 0% | 0% | 60% | NUMERIC |
| hsCRP | 3.2 mg/L | 62 | 0% | 0% | 75% | NUMERIC |
| Exercise Tolerance | - | - | 10% | 65% | 40% | NS |
| Coronary Calcium | - | - | 80% | 10% | 95% | NS |

### Step 1: CV-Structure Domain

**NUMERIC contributors:**
- SBP: 45 Ãƒâ€” 0.10 = 4.5
- DBP: 65 Ãƒâ€” 0.10 = 6.5
- EF: 85 Ãƒâ€” 0.30 = 25.5
- LV Wall: 82 Ãƒâ€” 0.90 = 73.8
- BNP: 78 Ãƒâ€” 0.05 = 3.9
- Troponin: 85 Ãƒâ€” 0.05 = 4.25

```
Raw score = (4.5 + 6.5 + 25.5 + 73.8 + 3.9 + 4.25) / (0.10 + 0.10 + 0.30 + 0.90 + 0.05 + 0.05)
          = 118.45 / 1.50 = 79.0
```

**Completeness:**
```
Measured weights: 1.50 (150%)
Recommended weights: 1.50 + 0.10(exercise) + 0.80(calcium) = 2.40 (240%)
Completeness = 150% / 240% = 0.625 (62.5%)
```

**Adjusted:**
```
= (79.0 Ãƒâ€” 0.625) + (50 Ãƒâ€” 0.375) = 49.4 + 18.75 = 68.15 Ã¢â€°Ë† 68
```

### Step 2: CV-Function Domain

**NUMERIC contributors:**
- SBP: 45 Ãƒâ€” 0.80 = 36.0
- DBP: 65 Ãƒâ€” 0.70 = 45.5
- HR: 80 Ãƒâ€” 0.60 = 48.0
- EF: 85 Ãƒâ€” 1.00 = 85.0
- LV Wall: 82 Ãƒâ€” 0.20 = 16.4
- BNP: 78 Ãƒâ€” 0.85 = 66.3
- Troponin: 85 Ãƒâ€” 0.15 = 12.75

```
Raw score = 309.95 / 4.30 = 72.1
```

**Completeness:**
```
Measured: 4.30 (430%)
Recommended: 4.30 + 0.65(exercise) = 4.95 (495%)
Completeness = 430% / 495% = 0.87 (87%)
```

**Adjusted:**
```
= (72.1 Ãƒâ€” 0.87) + (50 Ãƒâ€” 0.13) = 62.7 + 6.5 = 69.2 Ã¢â€°Ë† 69
```

### Step 3: CV-Risk Domain

**NUMERIC contributors:**
- SBP: 45 Ãƒâ€” 0.90 = 40.5
- DBP: 65 Ãƒâ€” 0.85 = 55.25
- HR: 80 Ãƒâ€” 0.20 = 16.0
- EF: 85 Ãƒâ€” 0.40 = 34.0
- LV Wall: 82 Ãƒâ€” 0.30 = 24.6
- BNP: 78 Ãƒâ€” 0.70 = 54.6
- Troponin: 85 Ãƒâ€” 0.80 = 68.0
- LDL: 58 Ãƒâ€” 0.85 = 49.3
- HDL: 72 Ãƒâ€” 0.60 = 43.2
- hsCRP: 62 Ãƒâ€” 0.75 = 46.5

```
Raw score = 431.95 / 6.35 = 68.0
```

**Completeness:**
```
Measured: 6.35 (635%)
Recommended: 6.35 + 0.40(exercise) + 0.95(calcium) = 7.70 (770%)
Completeness = 635% / 770% = 0.82 (82%)
```

**Adjusted:**
```
= (68.0 Ãƒâ€” 0.82) + (50 Ãƒâ€” 0.18) = 55.8 + 9.0 = 64.8 Ã¢â€°Ë† 65
```

### Step 4: CV System Score

```
CV System = (68 Ãƒâ€” 0.25) + (69 Ãƒâ€” 0.50) + (65 Ãƒâ€” 0.25)
          = 17 + 34.5 + 16.25
          = 67.75 Ã¢â€°Ë† 68
```

### Step 5: Dashboard Display

```
Ã¢â€¢â€Ã¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢â€”
Ã¢â€¢â€˜  CARDIOVASCULAR HEALTH SYSTEM                         Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  Overall Score: 68  Ã°Å¸Å¸Â¡ YELLOW - Monitor             Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  Domain Breakdown:                                    Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢â€Å“Ã¢â€â‚¬ Structure: 68 (Good - 63% complete)             Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢â€Å“Ã¢â€â‚¬ Function: 69 (Good - 87% complete)              Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢â€â€Ã¢â€â‚¬ Risk: 65 (Fair - 82% complete)                  Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  What's Working Well:                                 Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€œ Heart structure preserved (EF 58%, normal wall)   Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€œ No acute injury (troponin normal)                 Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€œ Adequate cardiac function at rest                 Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  What Needs Work:                                     Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€” Blood pressure above target (142/88 mmHg)        Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€” LDL cholesterol elevated (135 mg/dL)             Ã¢â€¢â€˜
Ã¢â€¢â€˜  Ã¢Å“â€” Inflammation present (hsCRP 3.2 mg/L)            Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  Recommended Action:                                  Ã¢â€¢â€˜
Ã¢â€¢â€˜  Your cardiovascular health is good overall. Focus onÃ¢â€¢â€˜
Ã¢â€¢â€˜  optimizing blood pressure and cholesterol through   Ã¢â€¢â€˜
Ã¢â€¢â€˜  medication adjustment and lifestyle changes.        Ã¢â€¢â€˜
Ã¢â€¢â€˜  Follow-up in 3 months. Consider stress test.        Ã¢â€¢â€˜
Ã¢â€¢â€˜                                                       Ã¢â€¢â€˜
Ã¢â€¢â€˜  [View detailed parameters] [See trends]              Ã¢â€¢â€˜
Ã¢â€¢Å¡Ã¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢ÂÃ¢â€¢Â
```

---

## WEIGHT ASSIGNMENT TEMPLATES

### Template: Vital Sign

```
PARAMETER CLASS: Vital Sign
PRIMARY SYSTEM: [Cardiovascular/Respiratory/Neurological]
SECONDARY SYSTEMS: [List related systems]

DEFAULT WEIGHTS:
- Primary-Structure: 5-15%
- Primary-Function: 60-90%
- Primary-Risk: 70-95%
- Secondary-Risk: 10-20% each

RATIONALE: Vital signs primarily reflect current function with strong risk prediction
```

### Template: Lab - Structural Marker

```
PARAMETER CLASS: Lab - Structural Marker
PRIMARY SYSTEM: [System]
EXAMPLES: Albumin, Hemoglobin, Platelets

DEFAULT WEIGHTS:
- Primary-Structure: 70-90%
- Primary-Function: 30-50%
- Primary-Risk: 40-60%

RATIONALE: Direct markers of organ/system integrity
```

### Template: Lab - Functional Marker

```
PARAMETER CLASS: Lab - Functional Marker
PRIMARY SYSTEM: [System]
EXAMPLES: Creatinine, Liver enzymes, BNP

DEFAULT WEIGHTS:
- Primary-Structure: 20-40%
- Primary-Function: 80-100%
- Primary-Risk: 60-80%

RATIONALE: Direct measures of current organ performance
```

### Template: Lab - Risk Marker

```
PARAMETER CLASS: Lab - Risk Marker
PRIMARY SYSTEM: [System]
EXAMPLES: HbA1c, LDL, hsCRP

DEFAULT WEIGHTS:
- Primary-Structure: 0-10%
- Primary-Function: 0-20%
- Primary-Risk: 80-100%
- Secondary-Risk: 40-70% (related systems)

RATIONALE: Primarily predictive of future events
```

### Template: Imaging Finding

```
PARAMETER CLASS: Imaging - Structural Finding
PRIMARY SYSTEM: [System]
EXAMPLES: LV wall thickness, liver nodule, bone density

DEFAULT WEIGHTS:
- Primary-Structure: 80-100%
- Primary-Function: 30-60%
- Primary-Risk: 50-80%

RATIONALE: Direct visualization of anatomy
```

### Template: Functional Test

```
PARAMETER CLASS: Functional Test
PRIMARY SYSTEM: [System]
EXAMPLES: VO2max, FEV1, Grip strength

DEFAULT WEIGHTS:
- Primary-Structure: 10-30%
- Primary-Function: 90-100%
- Primary-Risk: 60-80%

RATIONALE: Direct measurement of functional capacity
```

---

## QUALITY ASSURANCE

### Validation Checklist

**For Each Parameter's Weight Matrix:**
- [ ] Weights assigned for all 24 cells
- [ ] Primary system identified correctly
- [ ] Related systems have justified weights (<5% excluded or documented)
- [ ] Rationale documented with evidence
- [ ] Clinical panel reviewed (if high-priority parameter)
- [ ] Cross-parameter consistency checked
- [ ] Version and approval documented
- [ ] Recommended parameter list defined

**For Domain Score Calculations:**
- [ ] Formula implemented correctly (weight-based averaging)
- [ ] Completeness calculation uses weights, not counts
- [ ] Tri-state handling (NA/NS/NUMERIC) implemented correctly
- [ ] Temporal display scores used (not raw point scores)
- [ ] Edge cases tested (0 parameters, 1 parameter, all parameters)
- [ ] Results validated against hand calculations

**For System Score Calculations:**
- [ ] Domain weights correct (25/50/25)
- [ ] Color zone thresholds applied correctly
- [ ] Worked examples validated by clinicians
- [ ] Display format clear and actionable

---

## REVISION HISTORY

**Version 2.0.0 - November 12, 2025**
- **CRITICAL FIX:** Baseline conventions clarified (85 vs 50)
- **CRITICAL FIX:** Completeness changed to weight-based (not count-based)
- **CRITICAL FIX:** Tri-state handling (NA/NS/NUMERIC) explicitly specified
- **IMPROVEMENT:** Temporal display scores clarified as input
- **IMPROVEMENT:** Weight QA guidelines added
- **IMPROVEMENT:** Cross-system contribution note added
- **CLEANUP:** Pseudocode removed (clinical spec only)
- **CLEANUP:** Cardiovascular example moved to appendix
- **ALIGNMENT:** Cross-references to Parameter Scoring Framework docs added

**Version 1.0.0 - November 12, 2025**
- Initial specification
- 24-cell matrix framework defined
- Weight assignment methodology established
- Domain and system score formulas specified
- Completeness adjustment logic defined (count-based)
- Worked cardiovascular example provided

---

## RELATED DOCUMENTS

**Uses:**
- `PARAMETER_NORMALIZATION_v2.md` - Individual parameter scores (input)
- `TEMPORAL_SCORING.md` - Display scores (input)
- `CONTEXT_RULES.md` - Patient-specific adjustments (applied before aggregation)
- `CALIBRATION_VALIDATION.md` - Validation requirements

**Feeds into:**
- `COMPOSITE_SCORING.md` - System scores Ã¢â€ â€™ Overall health score (next layer)

**Referenced by:**
- All `PARAMETERS_*.md` files - Each parameter needs weight matrix

---

**END OF SYSTEM & DOMAIN SCORING SPECIFICATION v2.0**

*This document connects individual parameter scores to system health through the 24-cell matrix. Every parameter must have assigned weights before it can contribute to system scores. All calculations use weight-based averaging and respect the 85-point baseline convention.*
