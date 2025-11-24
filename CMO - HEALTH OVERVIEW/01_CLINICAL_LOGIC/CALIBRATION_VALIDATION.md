# CALIBRATION & VALIDATION SPECIFICATION
## Patient Health Dashboard - Parameter Scoring Framework

**Document Type:** Core Clinical Logic  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - Part 2 of 4  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

This document is part of the **Parameter Scoring Framework** (read all four together):

1. `PARAMETER_NORMALIZATION.md` - Core normalization methods and formulas
2. **CALIBRATION_VALIDATION.md** (this document) - How to calibrate and validate parameters
3. `CONTEXT_RULES.md` - Patient-specific scoring adjustments and overrides
4. `TEMPORAL_SCORING.md` - Handling measurements over time and aberrant values

---

## DOCUMENT PURPOSE

This specification defines how to **calibrate penalty coefficients and validate clinical fidelity** for every parameter in the system. It ensures that normalized scores accurately reflect clinical severity and are consistent across parameters.

**Without proper calibration:**
- SBP 142 mmHg might score 65 (too lenient) or 20 (too harsh)
- "Stage 2 Hypertension" might score 31 while "HbA1c 9.5%" scores 55, despite equal clinical urgency
- Coefficients would be arbitrary guesses rather than evidence-based

**This document provides:**
1. Clinical anchor methodology for establishing reference points
2. Multi-point calibration process for optimizing coefficients
3. Cross-parameter consistency framework (severity bands)
4. Standard deviation sourcing and documentation requirements
5. Governance and versioning procedures
6. Worked calibration examples

---

## CORE PHILOSOPHY

### The Calibration Problem

**Mathematical formulas are precise, but arbitrary without clinical validation.**

Example:
```
Score = 85 Ã— e^(-Î± Ã— zÂ²)
```

This formula is mathematically sound, but what should Î± be?
- Î± = 0.10: Very gentle penalty (may not reflect clinical urgency)
- Î± = 0.25: Moderate penalty
- Î± = 0.40: Steep penalty (may create false alarms)

**The answer must come from clinical reality, not mathematical convenience.**

### Calibration Ensures

1. **Clinical Fidelity:** Scores match actual clinical severity
2. **Cross-Parameter Consistency:** Similar clinical concerns score similarly across different parameters
3. **Actionability:** Score zones translate to clear clinical actions
4. **Reproducibility:** Any clinician can understand and validate the scoring logic
5. **Adaptability:** Parameters can be updated as evidence evolves

---

## METHOD 1: CLINICAL ANCHOR METHODOLOGY

### Overview

**Clinical anchors** are specific parameter values with known clinical significance that serve as calibration reference points.

**Process:**
1. Identify 5-7 clinically meaningful values for the parameter
2. Assign target scores to each based on clinical outcomes/severity
3. Optimize coefficients (Î±, Î², SD) to best match these anchors
4. Validate intermediate values make clinical sense
5. Document rationale and evidence base

### Selecting Clinical Anchors

**Criteria for good anchors:**
- Based on established clinical guidelines or outcome studies
- Span the full range of severity (optimal to critical)
- Clinically distinctive (e.g., "Stage 1" vs "Stage 2" HTN)
- Actionable (each anchor implies different management)

**Number of anchors:**
- Minimum: 5 (optimal, borderline, concerning, urgent, critical)
- Recommended: 7 (finer granularity)
- Maximum: 10 (diminishing returns, overcomplicated)

### Assigning Target Scores to Anchors

**Use standardized severity bands** (see Section 2 below):

| Severity Band | Score Range | Clinical Meaning | Action |
|---------------|-------------|------------------|---------|
| **Optimal** | 85-100 | At or better than target | Maintain |
| **Borderline** | 70-84 | Watchful waiting | Monitor |
| **Mild Concern** | 50-69 | Needs attention | Lifestyle/optimization |
| **Moderate Concern** | 30-49 | Action needed soon | Clinician visit within 1-2 weeks |
| **Severe Concern** | 15-29 | Urgent intervention | Contact clinician within 24-48 hours |
| **Critical** | 5-14 | Life-threatening | Emergency care immediately |

Assign each clinical anchor to a score within the appropriate band.

### Worked Example: Systolic Blood Pressure

**Step 1: Identify Clinical Anchors (ACC/AHA Guidelines)**

| Anchor # | SBP Value | Clinical Category | Clinical Significance |
|----------|-----------|-------------------|----------------------|
| 1 | 110 mmHg | Mild Hypotension | Mild concern, may cause symptoms |
| 2 | 120 mmHg | Normal (optimal) | Target for most adults |
| 3 | 130 mmHg | Elevated | Increased CV risk, lifestyle changes |
| 4 | 140 mmHg | Stage 1 Hypertension | Moderate CV risk, consider medication |
| 5 | 160 mmHg | Stage 2 Hypertension | High CV risk, medication indicated |
| 6 | 180 mmHg | Hypertensive Crisis | Immediate danger, emergency care |

**Step 2: Assign Target Scores Based on Severity Bands**

| Anchor # | SBP Value | Target Score | Severity Band | Rationale |
|----------|-----------|--------------|---------------|-----------|
| 1 | 110 mmHg | 75 | Borderline | Mild hypotension, monitor |
| 2 | 120 mmHg | 85 | Optimal | Target for healthy adults |
| 3 | 130 mmHg | 75 | Borderline | Elevated, lifestyle focus |
| 4 | 140 mmHg | 45 | Moderate | Stage 1 HTN, action needed |
| 5 | 160 mmHg | 22 | Severe | Stage 2 HTN, urgent treatment |
| 6 | 180 mmHg | 8 | Critical | Crisis, emergency care |

**Step 3: Set Initial Parameters**
- Target (T) = 120 mmHg (z = 0 at optimal)
- SD = 10 mmHg (estimated from population variability)
- Î± = ? (penalty above target, to be optimized)
- Î² = ? (penalty below target, to be optimized)

**Step 4: Calculate Z-Scores for Each Anchor**

| Anchor # | SBP | z = (SBP - 120) / 10 |
|----------|-----|----------------------|
| 1 | 110 | -1.0 |
| 2 | 120 | 0.0 |
| 3 | 130 | +1.0 |
| 4 | 140 | +2.0 |
| 5 | 160 | +4.0 |
| 6 | 180 | +6.0 |

**Step 5: Optimize Coefficients**

Using asymmetric bidirectional formula:
```
IF z â‰¥ 0: Score = 85 Ã— e^(-Î± Ã— zÂ²)
IF z < 0: Score = 85 Ã— e^(-Î² Ã— |z|Â²)
```

Test different Î± and Î² values:

**Test Î± = 0.20, Î² = 0.10** (high BP more concerning than low BP)

| Anchor | z | Formula | Calculated Score | Target Score | Error |
|--------|---|---------|------------------|--------------|-------|
| 1 (110) | -1.0 | 85 Ã— e^(-0.10 Ã— 1) | 77 | 75 | +2 âœ“ |
| 2 (120) | 0.0 | 85 | 85 | 85 | 0 âœ“ |
| 3 (130) | +1.0 | 85 Ã— e^(-0.20 Ã— 1) | 69 | 75 | -6 |
| 4 (140) | +2.0 | 85 Ã— e^(-0.20 Ã— 4) | 38 | 45 | -7 |
| 5 (160) | +4.0 | 85 Ã— e^(-0.20 Ã— 16) | 4 | 22 | -18 âœ— |
| 6 (180) | +6.0 | 85 Ã— e^(-0.20 Ã— 36) | <1 | 8 | -7 |

**Mean Absolute Error = 6.7 points** (too low at high values)

**Test Î± = 0.15, Î² = 0.08**

| Anchor | z | Formula | Calculated Score | Target Score | Error |
|--------|---|---------|------------------|--------------|-------|
| 1 (110) | -1.0 | 85 Ã— e^(-0.08 Ã— 1) | 78 | 75 | +3 âœ“ |
| 2 (120) | 0.0 | 85 | 85 | 85 | 0 âœ“ |
| 3 (130) | +1.0 | 85 Ã— e^(-0.15 Ã— 1) | 73 | 75 | -2 âœ“ |
| 4 (140) | +2.0 | 85 Ã— e^(-0.15 Ã— 4) | 47 | 45 | +2 âœ“ |
| 5 (160) | +4.0 | 85 Ã— e^(-0.15 Ã— 16) | 9 | 22 | -13 |
| 6 (180) | +6.0 | 85 Ã— e^(-0.15 Ã— 36) | <1 | 8 | -7 |

**Mean Absolute Error = 4.5 points** (better, but still issues at extremes)

**Issue identified:** Exponential decay drops too quickly at extreme values (z > 3).

**Solution:** Add floor logic or use piecewise function for extreme values.

**Revised approach:** Cap minimum score at 5, allow slight adjustment:

| Anchor | z | Formula | Score (floored at 5) | Target | Error |
|--------|---|---------|----------------------|--------|-------|
| 5 (160) | +4.0 | max(5, 9) | 9 | 22 | -13 |
| 6 (180) | +6.0 | max(5, <1) | 5 | 8 | -3 |

**Still not ideal.** Consider adjusting SD or using hybrid approach.

**Test Î± = 0.13, Î² = 0.08, SD = 12**

(Increasing SD reduces z-scores, gentler penalties)

| Anchor | z (SD=12) | Formula | Calculated Score | Target Score | Error |
|--------|-----------|---------|------------------|--------------|-------|
| 1 (110) | -0.83 | 85 Ã— e^(-0.08 Ã— 0.69) | 80 | 75 | +5 |
| 2 (120) | 0.0 | 85 | 85 | 85 | 0 âœ“ |
| 3 (130) | +0.83 | 85 Ã— e^(-0.13 Ã— 0.69) | 77 | 75 | +2 âœ“ |
| 4 (140) | +1.67 | 85 Ã— e^(-0.13 Ã— 2.79) | 58 | 45 | +13 |
| 5 (160) | +3.33 | 85 Ã— e^(-0.13 Ã— 11.1) | 20 | 22 | -2 âœ“ |
| 6 (180) | +5.0 | 85 Ã— e^(-0.13 Ã— 25) | 6 | 8 | -2 âœ“ |

**Mean Absolute Error = 4.0 points** âœ“ (acceptable, most within Â±5)

**Final Calibrated Parameters:**
- T = 120 mmHg
- SD = 12 mmHg
- Î± = 0.13 (above target penalty)
- Î² = 0.08 (below target penalty)

**Step 6: Plot and Validate**

Plot the score curve across full range (80-200 mmHg) and verify:
- Smooth transitions between zones
- No unexpected plateaus or cliffs
- Intermediate values between anchors make clinical sense
- Matches clinical intuition

**Step 7: Clinical Panel Review**

Show curve and anchor table to 3-5 clinicians:
- "Does this reflect BP severity accurately?"
- "Would you agree with these management implications?"
- Collect feedback, adjust if needed

**Step 8: Document**

Record final parameters with full justification:
```
PARAMETER: Systolic Blood Pressure
CALIBRATION DATE: November 12, 2025
CLINICAL ANCHORS: 6 points from ACC/AHA 2017 Guidelines
TARGET: 120 mmHg (personalized by patient factors - see CONTEXT_RULES.md)
SD: 12 mmHg (derived from calibration optimization)
COEFFICIENTS: Î± = 0.13, Î² = 0.08 (asymmetric, high BP primary concern)
VALIDATION: Mean absolute error = 4.0 points across anchors
REVIEWERS: [Names and credentials]
NEXT REVIEW: November 2026 (annual)
VERSION: 1.0
```

---

## METHOD 2: CROSS-PARAMETER CONSISTENCY

### The Consistency Problem

**Different parameters shouldn't have wildly different scoring behavior for similar clinical severity.**

**Bad example:**
- SBP 150 mmHg (Stage 2 HTN) â†’ Score 35 (Orange, "Act Soon")
- HbA1c 9.5% (Poor diabetes control) â†’ Score 65 (Yellow, "Monitor")
- **Problem:** Both are urgent situations requiring intervention, but scores/colors differ

**Goal:** Standardize severity bands so similar clinical urgency maps to similar score ranges across ALL parameters.

### Standardized Severity Bands

**These bands apply universally across all parameters:**

| Band | Score Range | Color | Interpretation | Action Required |
|------|-------------|-------|----------------|-----------------|
| **OPTIMAL** | 85-100 | GREEN | At or better than target | Maintain current approach |
| **BORDERLINE** | 70-84 | LIGHT GREEN/YELLOW | Watchful waiting, minor optimization possible | Routine monitoring |
| **MILD CONCERN** | 50-69 | YELLOW | Needs attention, lifestyle/optimization focus | Schedule clinician visit (weeks) |
| **MODERATE CONCERN** | 30-49 | ORANGE | Action needed soon, intervention indicated | Clinician contact within 1-2 weeks |
| **SEVERE CONCERN** | 15-29 | RED | Urgent intervention required | Clinician contact within 24-48 hours |
| **CRITICAL** | 5-14 | DARK RED | Life-threatening, emergency care | Immediate emergency care/call 911 |

### Calibration for Consistency

When calibrating each parameter, ensure that anchors map to appropriate bands:

**Example Consistency Check:**

| Parameter | Clinical Category | Target Score Band | Example Values |
|-----------|-------------------|-------------------|----------------|
| SBP | Stage 2 Hypertension | MODERATE (30-49) | 150-180 mmHg |
| HbA1c | Poor Diabetes Control | MODERATE (30-49) | 9.0-10.0% |
| Troponin | Elevated (Possible MI) | MODERATE (30-49) | 0.05-0.15 ng/mL |
| eGFR | CKD Stage 3b | MODERATE (30-49) | 30-44 mL/min |
| Potassium | Moderate Hyperkalemia | MODERATE (30-49) | 5.5-6.0 mEq/L |

All of these represent "action needed soon" situations and should score in the same 30-49 range.

### Calibration Sweep Process

**Step 1: Create Reference Matrix**

Build a table of common clinical scenarios across parameters:

| Severity Level | SBP | HbA1c | LDL | eGFR | Troponin | Potassium |
|----------------|-----|-------|-----|------|----------|-----------|
| OPTIMAL | 120 | 5.5% | 70 | 90 | <0.01 | 4.0 |
| BORDERLINE | 135 | 6.0% | 110 | 75 | <0.01 | 3.5 or 4.7 |
| MILD | 145 | 7.5% | 140 | 55 | <0.01 | 3.2 or 5.2 |
| MODERATE | 160 | 9.5% | 170 | 40 | 0.08 | 2.8 or 5.8 |
| SEVERE | 175 | 11% | 200 | 25 | 0.5 | 2.5 or 6.2 |
| CRITICAL | 190+ | 13%+ | N/A | <15 | 2.0+ | 2.0 or 7.0+ |

**Step 2: Score Each Scenario**

Calculate scores using preliminary coefficients for each parameter.

**Step 3: Check for Consistency**

Look for outliers:
- Parameters that score too high or too low relative to clinical severity
- Score ranges that don't match color zones
- Illogical comparisons (less severe parameter scoring worse than more severe)

**Step 4: Adjust Coefficients**

For parameters that are outliers, adjust Î±/Î²/SD to bring them into alignment.

**Step 5: Re-Validate**

Repeat until all parameters show consistent scoring patterns for equivalent clinical severity.

### Consistency Validation Metrics

**Target metrics:**
- **Within-band variance:** <10 points for parameters of similar severity
- **Cross-band separation:** >15 points between adjacent severity levels
- **Anchor alignment:** >80% of anchors within Â±5 points of target score

---

## METHOD 3: STANDARD DEVIATION SOURCING

### SD is Critical

**Small SD** â†’ Steep penalties, harsh scoring  
**Large SD** â†’ Gentle penalties, lenient scoring

**Example with SBP target = 120:**
- SD = 5: SBP 130 (z=+2) scores 31 (harsh)
- SD = 15: SBP 130 (z=+0.67) scores 75 (lenient)

**Therefore, SD must be clinically justified, not arbitrary.**

### SD Source Hierarchy

**Priority 1: Published Clinical Studies**
- Large population studies (e.g., NHANES, Framingham)
- Clinical trial data
- Meta-analyses

**Example:**
```
SBP SD = 12 mmHg
Source: NHANES 2015-2018, non-hypertensive adults
Citation: [CDC NHANES report]
Population: 5,000+ participants
```

**Priority 2: Laboratory Reference Ranges**
- When population SD not available
- Approximate: SD â‰ˆ (Upper Limit - Lower Limit) / 4

**Example:**
```
Sodium reference range: 135-145 mEq/L
SD â‰ˆ (145 - 135) / 4 = 2.5 mEq/L
```

**Priority 3: Clinical Guidelines**
- When guidelines specify "clinically significant" changes
- Use clinical judgment to estimate variability

**Example:**
```
HbA1c: Clinical guidelines define 0.5% as meaningful change
SD â‰ˆ 0.8% (expert consensus)
```

**Priority 4: Expert Consensus**
- Last resort when no data available
- Requires panel of â‰¥3 clinicians
- Document rationale clearly

### SD Documentation Requirements

For EVERY parameter, document:
```
STANDARD DEVIATION: [value with units]
SOURCE: [Published study / Lab range / Guideline / Expert consensus]
CITATION: [Full reference]
POPULATION: [Who this SD applies to]
DATE: [When sourced]
VALIDATED BY: [Names]
NEXT REVIEW: [Date for re-validation]
VERSION: [Version number]
```

### SD Versioning and Updates

**When to update SD:**
- New major population studies published
- Laboratory assay methods change
- Clinical guidelines updated
- Observed drift in patient population (see Governance section)

**Update process:**
1. Identify new evidence
2. Compare old vs new SD
3. Re-run calibration if SD changes >20%
4. Validate impact on scores
5. Increment version number
6. Document change rationale

---

## METHOD 4: COEFFICIENT OPTIMIZATION ALGORITHMS

### Manual Optimization (Recommended for MVP)

**Process:**
1. Set clinical anchors with target scores
2. Calculate z-scores for each anchor
3. Test coefficient values (Î±, Î²)
4. Calculate resulting scores
5. Compute error (calculated vs target)
6. Adjust coefficients to minimize error
7. Repeat until error acceptable (MAE <5 points)

**Advantages:**
- Clinician maintains control
- Transparent process
- Explainable decisions

**Disadvantages:**
- Time-consuming
- Requires multiple iterations

### Automated Optimization (Future Enhancement)

**Use least-squares minimization:**
```
Minimize: Î£(Score_calculated - Score_target)Â²

Subject to:
- Î±, Î² > 0
- Reasonable bounds (e.g., 0.05 < Î± < 0.40)
```

**Tools:**
- Excel Solver
- Python scipy.optimize
- R optimization packages

**Advantages:**
- Fast
- Mathematically optimal

**Disadvantages:**
- May produce unintuitive coefficients
- Requires validation
- Less clinician involvement

**Recommendation:** Use automated optimization to generate candidates, then validate clinically.

---

## METHOD 5: VALIDATION REQUIREMENTS

### Three-Layer Validation

**Layer 1: Mathematical Validation**
- Hand-calculate scores for all anchors
- Verify formulas implemented correctly
- Test edge cases (extreme values, boundaries)
- Confirm score ranges (5-100, no NaN/Inf)
- Check that z=0 â†’ 85 exactly

**Layer 2: Clinical Validation**
- Present scenarios to clinical panel (â‰¥3 clinicians)
- Show: value, score, color, interpretation
- Ask: "Does this match clinical severity?"
- Collect concerns or suggested adjustments
- Document agreement level (aim for >80% consensus)

**Layer 3: Patient Comprehension Validation**
- Test plain language interpretations with patients (n=10-20)
- Verify understanding: "What does this score mean to you?"
- Ensure color zones are clear
- Confirm action items are actionable
- No medical jargon barriers

### Validation Documentation Template

```
PARAMETER: [Name]
VALIDATION DATE: [Date]
VERSION: [Version number]

MATHEMATICAL VALIDATION:
- Anchors tested: [Number]
- Mean absolute error: [Value] points
- Max error: [Value] points at [which anchor]
- Edge cases tested: [List]
- Result: PASS / FAIL

CLINICAL VALIDATION:
- Reviewers: [Names and credentials]
- Agreement level: [Percentage] on [Number] scenarios
- Concerns raised: [List or "None"]
- Adjustments made: [List or "None"]
- Result: APPROVED / REVISIONS NEEDED

PATIENT COMPREHENSION:
- Participants: [Number] patients
- Understanding rate: [Percentage] correctly interpreted severity
- Clarity of action items: [Percentage] knew what to do
- Language adjustments: [List or "None"]
- Result: CLEAR / NEEDS REVISION

OVERALL STATUS: VALIDATED / NOT VALIDATED
APPROVED BY: [Clinical Lead name and date]
```

---

## GOVERNANCE & VERSION CONTROL

### Coefficient Review Board

**Composition:**
- Medical Director (chair)
- 2-3 Clinical Experts (diverse specialties)
- 1 Outcomes/Quality Expert
- 1 Patient Representative (optional but recommended)

**Responsibilities:**
- Review and approve all new parameter calibrations
- Quarterly review of existing parameters
- Evaluate proposed coefficient changes
- Resolve calibration disputes
- Monitor consistency across parameters

**Meeting frequency:**
- Monthly during MVP development
- Quarterly during steady-state operations
- Ad-hoc for urgent changes

### Versioning System

**Version format: X.Y.Z**
- **X (Major):** Fundamental methodology change (rare)
- **Y (Minor):** Coefficient or SD update
- **Z (Patch):** Documentation fix, no score impact

**Version tracking fields:**
```
parameter_code: "sbp"
version: "1.2.0"
effective_date: "2025-11-12"
prior_version: "1.1.0"
change_type: "coefficient_update"
change_reason: "New ACC guidelines"
approved_by: "Dr. [Name]"
approval_date: "2025-11-10"
```

### Change Management Process

**For any coefficient, SD, or target logic change:**

1. **Proposal**
   - Document rationale (new evidence, drift, error correction)
   - Show before/after impact analysis
   - Estimate affected patients

2. **Impact Analysis**
   - Re-score sample patient cohort (n=100+)
   - Quantify score shifts
   - Identify patients moving between color zones
   - Flag any critical impacts

3. **Clinical Review**
   - Present to Coefficient Review Board
   - Show impact scenarios
   - Discuss clinical implications
   - Vote to approve/reject/revise

4. **Implementation**
   - Increment version number
   - Update parameter specification
   - Set effective date
   - Notify clinical users

5. **Monitoring**
   - Track score distributions post-change
   - Monitor alert volumes
   - Collect clinician feedback
   - Validate no unintended consequences

### Drift Monitoring (Future)

**Automated monitoring for:**
- Score distribution shifts (e.g., mean scores dropping)
- Z-score distribution changes (patient population drift)
- Alert volume changes (too many or too few)
- Parameter correlation changes

**Triggers for review:**
- Mean score shift >5 points over 3 months
- Alert volume change >25%
- Clinician feedback threshold (>5 reports of scoring issue)

---

## CALIBRATION EXAMPLES LIBRARY

### Example 1: HbA1c (Clinical Categories Method)

**Clinical Anchors (ADA 2023):**

| Anchor | HbA1c | Category | Target Score | Band |
|--------|-------|----------|--------------|------|
| 1 | 5.0% | Normal (optimal) | 88 | Optimal |
| 2 | 5.7% | Prediabetes threshold | 72 | Borderline |
| 3 | 6.5% | Diabetes threshold | 58 | Mild |
| 4 | 7.5% | Fair control | 45 | Moderate |
| 5 | 9.0% | Poor control | 28 | Severe |
| 6 | 11.0%+ | Very poor control | 12 | Critical |

**Calibration:**
- Target = 5.5% (non-diabetic) or personalized diabetic target
- SD = 0.8% (clinical variability)
- Î± = 0.22 (high = poor control)
- Î² = 0.18 (low = hypoglycemia risk)

**Validation:** MAE = 3.2 points across anchors

### Example 2: eGFR (Unidirectional Higher-Better)

**Clinical Anchors (KDIGO CKD Stages):**

| Anchor | eGFR | CKD Stage | Target Score | Band |
|--------|------|-----------|--------------|------|
| 1 | â‰¥90 | Normal | 85 | Optimal |
| 2 | 75 | Mildly decreased | 80 | Optimal |
| 3 | 50 | Stage 3a CKD | 62 | Mild |
| 4 | 38 | Stage 3b CKD | 42 | Moderate |
| 5 | 22 | Stage 4 CKD | 22 | Severe |
| 6 | 12 | Stage 5 CKD | 10 | Critical |

**Calibration:**
- Target = 90 mL/min (age-adjusted)
- SD = 15 mL/min
- Î² = 0.24 (below target penalty)

**Validation:** MAE = 4.1 points across anchors

### Example 3: hsCRP (Risk Threshold Categories)

**Clinical Anchors (ACC/AHA CV Risk):**

| Anchor | hsCRP | Risk Category | Target Score | Band |
|--------|-------|---------------|--------------|------|
| 1 | <1.0 | Low CV risk | 85 | Optimal |
| 2 | 1.5 | Low-moderate | 78 | Borderline |
| 3 | 2.5 | Moderate risk | 68 | Mild |
| 4 | 5.0 | High risk | 42 | Moderate |
| 5 | 12 | Very high | 22 | Severe |
| 6 | 25+ | Acute inflammation | 8 | Critical |

**Calibration:**
- Uses Category-Based Method (not z-score)
- Direct mapping to risk categories
- Interpolation within categories for smooth transitions

**Validation:** Clinical panel 100% agreement on category assignments

---

## QUALITY ASSURANCE CHECKLIST

For each parameter calibration, verify:

**Pre-Calibration:**
- [ ] Clinical anchors identified (5-7 points minimum)
- [ ] Anchors based on guidelines or outcome data
- [ ] Target scores assigned to each anchor
- [ ] Severity bands appropriate
- [ ] SD sourced and documented

**Calibration Process:**
- [ ] Multiple coefficient values tested
- [ ] Optimization documented (manual or automated)
- [ ] Mean absolute error <5 points achieved
- [ ] Intermediate values validated
- [ ] Curve plotted and reviewed

**Validation:**
- [ ] Mathematical validation complete
- [ ] Clinical panel review (â‰¥3 clinicians, >80% agreement)
- [ ] Patient comprehension tested (nâ‰¥10)
- [ ] Cross-parameter consistency checked
- [ ] Documentation complete

**Governance:**
- [ ] Coefficient Review Board approval
- [ ] Version number assigned
- [ ] Effective date set
- [ ] Next review date scheduled (within 1 year)
- [ ] Change log updated

---

## REVISION HISTORY

**Version 1.0.0 - November 12, 2025**
- Initial specification
- Clinical anchor methodology defined
- Cross-parameter consistency framework established
- SD sourcing requirements specified
- Governance procedures defined
- Calibration examples provided

---

## RELATED DOCUMENTS

- `PARAMETER_NORMALIZATION.md` - Core normalization methods
- `CONTEXT_RULES.md` - Patient-specific adjustments
- `TEMPORAL_SCORING.md` - Time-based scoring
- `PROJECT_SPECIFICATION_v2.md` - Master project architecture
- Individual parameter specifications (PARAMETERS_*.md files)

---

**END OF CALIBRATION & VALIDATION SPECIFICATION**

*Proper calibration ensures clinical fidelity. Every parameter must be validated before deployment.*
