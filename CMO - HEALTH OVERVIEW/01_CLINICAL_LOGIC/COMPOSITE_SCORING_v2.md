# COMPOSITE SCORING SPECIFICATION
## Patient Health Dashboard - Overall Health Score

**Document Type:** Core Clinical Logic  
**Version:** 2.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document (REVISED)  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture and vision
- `SYSTEM_DOMAIN_SCORING_v2.md` - How system scores are calculated (input to this document)
- Parameter Scoring Framework (foundation for all scoring):
  - `PARAMETER_NORMALIZATION_v2.md`
  - `CALIBRATION_VALIDATION.md`
  - `CONTEXT_RULES.md`
  - `TEMPORAL_SCORING.md`

**This document connects to:**
- `BIOLOGICAL_AGE_SPEC.md` - Uses overall score as input
- `TRANSPARENCY_DISPLAY.md` - Attribution of overall score
- `CRITICAL_ALERTS.md` - Override logic
- `DASHBOARD_LEVEL1_SPEC.md` - Display of overall score
- `SCORING_GOVERNANCE.md` - QA and weight revision procedures (shared)

---

## DOCUMENT PURPOSE

This specification defines how **system health scores and lifestyle pillar scores combine into the overall health score (0-100)**.

**The final aggregation:**
```
8 System Health Scores (0-100 each)
    â†“ [weighted by system criticality]
Objective Health Component (0-100)
    â†“ [70% weight]
    +
5 Lifestyle Pillar Scores (0-100 each)
    â†“ [weighted by pillar importance]
Subjective Health Component (0-100)
    â†“ [30% weight]
    =
OVERALL HEALTH SCORE (0-100)
```

**This document provides:**
1. System weighting methodology and rationale
2. Objective health component calculation
3. Lifestyle pillar weighting methodology
4. Subjective health component calculation
5. Final overall health score formula
6. Worked examples with real patient data
7. Completeness governance
8. Edge case handling

---

## BASELINE CONVENTIONS (CRITICAL ALIGNMENT)

### The 85-Point Standard

**OFFICIAL PROJECT BASELINE (applies everywhere):**

**At Personalized Target (z-score = 0):**
- **Parameter scores: 85 points**
- **Domain scores: â‰ˆ 85 points** (when parameters at target)
- **System scores: â‰ˆ 85 points** (when domains at target)
- **Overall score: â‰ˆ 85 points** (when systems and lifestyle at target)

**This is consistent across all documents:**
- `PARAMETER_NORMALIZATION_v2.md` Principle 2
- `SYSTEM_DOMAIN_SCORING_v2.md` Section 2
- This document (all levels)

### The Role of 50 Points

**50 = Neutral/Unknown (NOT "at target")**

Used **ONLY** for:
1. **Completeness blending** when data sparse
2. **Unmeasured lifestyle pillars** (unknown behaviors)
3. **Display of truly missing information**

**NEVER used for:**
- Measured parameters at target (those = 85)
- Systems with complete data at target (those = 85)

### Key Distinctions

| Concept | Score | Meaning | When Used |
|---------|-------|---------|-----------|
| **At Target** | 85 | Optimal for this patient | Measured parameters meeting goals |
| **Neutral/Unknown** | 50 | No information available | Unmeasured/incomplete data |
| **Excellent/Reserve** | 86-100 | Sustained excellence beyond target | Exceptional performance over time |

**Cross-Reference:**
- See `PARAMETER_NORMALIZATION_v2.md` Principle 2 for full rationale
- See `PROJECT_SPECIFICATION_v2.md` Core Principle #4 for project-wide alignment

---

## CORE PRINCIPLES

### Principle 1: Dual Assessment (Objective + Subjective)

**Health is both measurable and lived:**
- **Objective (70%):** Clinical measurements, labs, imaging, functional tests
- **Subjective (30%):** Lifestyle behaviors, habits, environmental factors

**Rationale:**
- Objective data is more predictive of clinical outcomes (higher weight)
- Subjective factors are modifiable and influence objective health
- Balance prevents over-reliance on either component alone

### Principle 2: System Criticality Weighting

**Not all organ systems have equal impact on survival and quality of life:**
- Cardiovascular and neurological systems: Most critical (mortality + disability)
- Other systems: Important but variable criticality
- Weights reflect both mortality risk and morbidity impact

### Principle 3: Completeness Governance

**Clear ownership of completeness adjustments:**
- **System scores:** Completeness handled UPSTREAM in `SYSTEM_DOMAIN_SCORING_v2.md`
- **This document:** Does NOT re-apply completeness to system scores
- **Lifestyle pillars:** Completeness handled HERE (unmeasured = 50)
- **Display:** Show completeness indicators at all levels

**Critical rule:** Avoid double-adjusting for completeness across scoring levels.

### Principle 4: Critical Findings Override

**Good overall score cannot mask critical findings:**
- Critical alerts displayed prominently regardless of composite scores
- Level 1 dashboard shows critical flags ABOVE overall score
- See `CRITICAL_ALERTS.md` for threshold definitions

### Principle 5: Clinical Interpretation Context

**The Overall Health Score is for:**
- Patient communication and motivation
- Longitudinal trending over time
- Summary understanding of health status

**The Overall Health Score is NOT for:**
- Primary clinical decision-making (use system scores + parameters)
- Diagnosis (use individual parameters and clinical judgment)
- Treatment planning alone (needs full clinical context)

**Guidance:** Objective Health Score drives medical risk management; Subjective score guides lifestyle counseling. Overall score is the patient-facing summary.

---

## OBJECTIVE HEALTH COMPONENT

### Input: 8 System Health Scores

From `SYSTEM_DOMAIN_SCORING_v2.md`, we receive completeness-adjusted system scores:

| System | Score Range | Already Includes |
|--------|-------------|------------------|
| Neurological | 0-100 | Weighted domains (S/F/R: 25%/50%/25%) + completeness adjustment |
| Cardiovascular | 0-100 | Weighted domains + completeness adjustment |
| Respiratory | 0-100 | Weighted domains + completeness adjustment |
| Metabolic | 0-100 | Weighted domains + completeness adjustment |
| Renal | 0-100 | Weighted domains + completeness adjustment |
| Musculoskeletal | 0-100 | Weighted domains + completeness adjustment |
| Immune | 0-100 | Weighted domains + completeness adjustment |
| Reproductive/Endocrine | 0-100 | Weighted domains + completeness adjustment |

**Important:** These scores already reflect any data incompleteness penalties from the system/domain level. We do not re-blend them toward 50 here.

### System Criticality Weights

**Methodology:**
1. **Mortality impact:** How quickly/severely does dysfunction threaten life?
2. **Morbidity impact:** How severely does dysfunction impair quality of life?
3. **Cascade effects:** How much does dysfunction affect other systems?
4. **Reversibility:** Less reversible dysfunction = higher weight

**System Weight Assignments (Version 1.0):**

| System | Weight | Rationale | Evidence |
|--------|--------|-----------|----------|
| **Cardiovascular** | 20% | Highest mortality risk; sudden death potential; affects all organs | WHO GBD 2023 |
| **Neurological** | 18% | Cognitive/motor function critical; stroke/dementia major causes of disability | GBD 2023 |
| **Respiratory** | 15% | Life-threatening when compromised; hypoxia affects all systems | GBD 2023 |
| **Metabolic** | 15% | Diabetes/liver disease cascade effects; chronic widespread impact | GBD 2023 |
| **Renal** | 12% | CKD progression irreversible; dialysis dramatically impacts QOL | KDIGO 2021 |
| **Immune** | 10% | Cancer/infection risk; autoimmune cascade effects | WHO 2023 |
| **Musculoskeletal** | 5% | Mobility/independence critical; lower mortality but high disability | GBD 2023 |
| **Reproductive/Endocrine** | 5% | QOL important; hormones affect multiple systems; lower mortality | Endo society |
| **TOTAL** | **100%** | Constraint: No single system >25% | â€” |

**Validation:**
- CV + Neuro = 38% (leading causes of death/disability) âœ“
- Resp + Metab + Renal = 42% (major chronic diseases) âœ“
- Immune + MSK + Repro = 20% (important but lower immediate mortality) âœ“

### Objective Health Score Calculation

**Formula:**
```
Objective_Health_Score = Î£(System_Score Ã— System_Weight)

= (CV Ã— 0.20) + (Neuro Ã— 0.18) + (Resp Ã— 0.15) + (Metab Ã— 0.15) 
  + (Renal Ã— 0.12) + (Immune Ã— 0.10) + (MSK Ã— 0.05) + (Repro Ã— 0.05)
```

**Where:**
- Each System_Score is from SYSTEM_DOMAIN_SCORING_v2.md (0-100, already completeness-adjusted)
- Weights sum to 1.0 (100%)

**Output:** Single score (0-100) representing objective clinical health

### NA System Handling

**If a system is marked NA (Not Applicable):**

Systems marked NA at the parameter level propagate as NA to system level and are **excluded** from composite calculation.

**Implementation (Option 1 - CANONICAL):**
```
IF system = NA:
  Exclude from numerator and denominator
  Renormalize remaining weights to sum to 100%
```

**Example:** Reproductive system NA for elderly male patient:
```
Available weights: CV(20) + Neuro(18) + Resp(15) + Metab(15) + Renal(12) + Immune(10) + MSK(5) = 95%

Renormalized weights:
CV: 20/95 = 21.1%
Neuro: 18/95 = 18.9%
Resp: 15/95 = 15.8%
(etc., scale all by 1/0.95)
```

**NS (No Score) systems:**
- Systems with NS (insufficient data) remain in calculation
- Their system scores will already have completeness penalties from SYSTEM_DOMAIN_SCORING_v2.md
- We do NOT further adjust or exclude them here

### Worked Example: Objective Health Score

**Patient: 55-year-old male with diabetes, hypertension**

| System | Score (from SYSTEM_DOMAIN_SCORING) | Weight | Contribution |
|--------|-------------------------------------|--------|--------------|
| Cardiovascular | 68 | 20% | 13.6 |
| Neurological | 78 | 18% | 14.0 |
| Respiratory | 82 | 15% | 12.3 |
| Metabolic | 62 | 15% | 9.3 |
| Renal | 70 | 12% | 8.4 |
| Immune | 75 | 10% | 7.5 |
| Musculoskeletal | 80 | 5% | 4.0 |
| Reproductive | NA | 5% | â€” |

**Calculation:**
```
Available weight = 0.95
Sum of contributions = 69.1

Objective_Health_Score = 69.1 / 0.95 = 72.7 â‰ˆ 73
```

**Interpretation:** Good objective health (YELLOW zone: 60-74)

**Completeness indicator:**
```
Objective_Completeness = 7/8 systems assessed (88%)
```

---

## SUBJECTIVE HEALTH COMPONENT

### Input: 5 Lifestyle Pillar Scores

Lifestyle pillars assessed via questionnaires (each scored 0-100):

| Pillar | Assessment Method | Objective Correlate |
|--------|-------------------|---------------------|
| **Nutrition** | Diet quality questionnaire | Metabolic markers, weight, lipids |
| **Movement** | Physical activity questionnaire | Fitness tests, MSK function |
| **Recovery** | Sleep & stress questionnaire | Cortisol, inflammatory markers |
| **Emotion** | Mental health questionnaire | Neurological function, psychosomatic |
| **Environment** | Social & occupational questionnaire | Exposure-related findings |

### Lifestyle Pillar Weighting

**Methodology:**
1. **Evidence strength:** Quality of data linking behavior to outcomes
2. **Modifiability:** How much can patients change this factor?
3. **Impact magnitude:** Effect size on objective health
4. **Universality:** Applies to all patients vs. specific populations

**Pillar Weight Assignments (Version 1.0):**

| Pillar | Weight | Rationale | Evidence |
|--------|--------|-----------|----------|
| **Nutrition** | 25% | Strong metabolic/CV evidence; highly modifiable | ACLM 2024 |
| **Movement** | 25% | Robust multi-system evidence; highly modifiable | Exercise medicine |
| **Recovery** | 20% | Growing sleep/stress impact evidence; modifiable | Sleep medicine |
| **Emotion** | 15% | Strong psychosomatic links; moderately modifiable | Behavioral med |
| **Environment** | 15% | Social determinants critical for whole-person health | SDOH literature |
| **TOTAL** | **100%** | Balanced across domains | â€” |

**Note on Version 1.0 vs Future:**
These weights emphasize **modifiable clinical risk factors** (Nutrition, Movement) for MVP. Future versions will likely increase Emotion/Environment weights as we integrate more wellness and social determinants data. See `SCORING_GOVERNANCE.md` for weight revision process.

**Comparison to v1.0 draft:**
- Emotion increased: 15% â†’ 15% (maintained)
- Environment increased: 10% â†’ 15% (strengthened for whole-person emphasis)
- Nutrition/Movement each reduced: 30%/25% â†’ 25%/25% (balanced)
- Recovery maintained: 20% â†’ 20%

### Subjective Health Score Calculation

**Formula:**
```
Subjective_Health_Score = Î£(Pillar_Score Ã— Pillar_Weight)

= (Nutrition Ã— 0.25) + (Movement Ã— 0.25) + (Recovery Ã— 0.20) 
  + (Emotion Ã— 0.15) + (Environment Ã— 0.15)
```

**Where:**
- Each Pillar_Score is from patient questionnaires (0-100)
- Weights sum to 1.0 (100%)

**Output:** Single score (0-100) representing lifestyle/behavioral health

### Unmeasured Pillar Handling

**If pillar questionnaire not completed:**

Treat as **neutral/unknown (score = 50)** and apply normal weights:
```
IF pillar unavailable:
  Use score = 50 for that pillar
  Apply normal weight
  Flag as "incomplete" in completeness indicator
```

**Rationale:**
- Unlike objective data (where we don't assume health/disease), lifestyle is inherently estimable
- 50 = "average" lifestyle behaviors when not assessed
- Neutral assumption avoids penalizing or rewarding unmeasured behaviors

**Completeness indicator required:**
```
Lifestyle_Completeness = (# of pillars with â‰¥1 completed item) / 5
```

**Display requirement:**
```
IF Lifestyle_Completeness < 60%:
  Show âš ï¸ "Your Lifestyle score is based on limited questionnaire responses"
```

### Worked Example: Subjective Health Score

**Same patient: 55-year-old male**

| Pillar | Score | Weight | Contribution | Status |
|--------|-------|--------|--------------|--------|
| Nutrition | 68 | 25% | 17.0 | Complete |
| Movement | 52 | 25% | 13.0 | Complete |
| Recovery | 58 | 20% | 11.6 | Complete |
| Emotion | 72 | 15% | 10.8 | Complete |
| Environment | (Not assessed) | 15% | 7.5 (default 50) | Incomplete |

**Calculation:**
```
Subjective_Health_Score = 17.0 + 13.0 + 11.6 + 10.8 + 7.5 = 59.9 â‰ˆ 60
```

**Interpretation:** Fair lifestyle (YELLOW zone: 60-74) - primarily limited by low movement

**Completeness indicator:**
```
Lifestyle_Completeness = 4/5 pillars assessed (80%)
```

---

## OVERALL HEALTH SCORE

### Final Weighted Combination

**Formula:**
```
Overall_Health_Score = (Objective Ã— 0.70) + (Subjective Ã— 0.30)
```

**Rationale for 70/30 split:**
- **Objective data (70%):** More predictive of clinical outcomes, mortality, disease burden
- **Subjective factors (30%):** Significant modifiable influence on long-term health, QOL critical
- Balance ensures lifestyle matters without overwhelming clinical reality
- Evidence from predictive validity studies supports this ratio

### Worked Example: Overall Health Score

**Using previous examples:**

```
Objective_Health_Score = 73
Subjective_Health_Score = 60

Overall_Health_Score = (73 Ã— 0.70) + (60 Ã— 0.30)
                     = 51.1 + 18.0
                     = 69.1 â‰ˆ 69
```

**Color Zone:** YELLOW (60-74) - Good health with improvement opportunities

**Completeness:**
```
Objective: 7/8 systems (88%)
Subjective: 4/5 pillars (80%)
Overall data coverage: 85%
```

### Dashboard Display Example (Level 1)

```
â•”â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•—
â•‘  YOUR HEALTH SCORE: 69 / 100                             â•‘
â•‘  â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘             â•‘
â•‘  ðŸŸ¡ GOOD - Keep improving                                â•‘
â•‘                                                           â•‘
â•‘  Based on 85% of recommended assessments                 â•‘
â•‘  â€¢ Clinical data: 88% complete (7/8 systems)             â•‘
â•‘  â€¢ Lifestyle data: 80% complete (4/5 pillars)            â•‘
â•‘                                                           â•‘
â•‘  â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”  â•‘
â•‘                                                           â•‘
â•‘  WHAT'S WORKING WELL:                                    â•‘
â•‘  âœ“ Respiratory health excellent (82)                     â•‘
â•‘  âœ“ Musculoskeletal function strong (80)                  â•‘
â•‘  âœ“ Good emotional wellbeing (72)                         â•‘
â•‘                                                           â•‘
â•‘  WHAT NEEDS WORK:                                        â•‘
â•‘  âœ— Metabolic control needs improvement (62)              â•‘
â•‘  âœ— Physical activity below target (52)                   â•‘
â•‘  âœ— Cardiovascular risk elevated (68)                     â•‘
â•‘                                                           â•‘
â•‘  TOP PRIORITY: Increase physical activity                â•‘
â•‘  Adding 30 minutes of exercise 5Ã—/week can improve       â•‘
â•‘  both metabolic and cardiovascular health.               â•‘
â•‘                                                           â•‘
â•‘  [View detailed breakdown] [See action plan]             â•‘
â•šâ•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

**Note:** For detailed display specifications, see `DASHBOARD_LEVEL1_SPEC.md`.

---

## EDGE CASES & SPECIAL SCENARIOS

### Edge Case 1: All Parameters at Target

**Scenario:** Healthy patient with every parameter at personalized target

**Expected behavior:**
```
All parameters â‰ˆ 85
â†’ All domains â‰ˆ 85
â†’ All systems â‰ˆ 85
â†’ Objective component â‰ˆ 85
â†’ Lifestyle (if all optimal) â‰ˆ 85
â†’ Overall â‰ˆ 85
```

**Validation:**
```
Objective = 85
Subjective = 85
Overall = (85 Ã— 0.70) + (85 Ã— 0.30) = 59.5 + 25.5 = 85 âœ“
```

**Interpretation:** GREEN zone. Patient is at all targets = B+ grade. Scores 86-100 require sustained excellence beyond basic goals.

### Edge Case 2: Critical Finding with Good Composite

**Scenario:** Troponin 2.5 ng/mL (acute MI) but other systems normal

**Scores:**
- Cardiovascular System: 15 (critical troponin)
- All other systems: 85
- Objective: (15Ã—0.20) + (85Ã—0.80) = 71
- Subjective: 75
- Overall: (71Ã—0.70) + (75Ã—0.30) = 72 (YELLOW)

**Critical override:**
- Troponin flagged as **CRITICAL (RED)** above overall score
- Dashboard Level 1 shows: "âš ï¸ CRITICAL: Possible heart attack. CALL 911 IMMEDIATELY."
- Good overall score (72) does NOT hide the critical finding

**Lesson:** Composite scores never mask critical findings. See `CRITICAL_ALERTS.md`.

### Edge Case 3: Very Sparse Data

**Scenario:** Only 15% of recommended assessments completed

**Approach:**
- Systems with 0 parameters: Excluded (NA handling)
- Systems with sparse data: Already have completeness penalties from SYSTEM_DOMAIN_SCORING_v2.md
- Display prominent completeness warning

**Display:**
```
Overall Health Score: 62
âš ï¸ INCOMPLETE ASSESSMENT (15% of recommended data)

This score is based on limited information. We recommend:
â€¢ Basic metabolic panel
â€¢ Lipid panel  
â€¢ Complete blood count
â€¢ Vital signs check
â€¢ Lifestyle questionnaire completion

[Schedule comprehensive assessment]
```

### Edge Case 4: Excellent Objective, Poor Lifestyle

**Scenario:**
- Objective: 88 (young, no disease, good genetics)
- Subjective: 35 (poor diet, sedentary, smoking, high stress)

```
Overall = (88 Ã— 0.70) + (35 Ã— 0.30) = 61.6 + 10.5 = 72 (YELLOW)
```

**Interpretation:**
"Your clinical health is excellent now, but your lifestyle behaviors are putting you at significant risk for future disease. This is a critical prevention windowâ€”small changes now can preserve your health for decades."

**Focus:** Emphasize **Risk domain** scores and predictive nature of lifestyle.

### Edge Case 5: Poor Objective, Excellent Lifestyle

**Scenario:**
- Objective: 40 (established chronic diseases)
- Subjective: 92 (exemplary lifestyle modifications)

```
Overall = (40 Ã— 0.70) + (92 Ã— 0.30) = 28 + 27.6 = 56 (ORANGE)
```

**Interpretation:**
"You're managing your conditions admirably with excellent lifestyle choices. These behaviors are slowing disease progression and improving your quality of life. Continue working with your care team on medical optimization."

**Focus:** Positive reinforcement for high subjective score, optimize medical therapy.

---

## COMPLETENESS GOVERNANCE

### Completeness Adjustment Ownership

**Clear responsibility by layer:**

| Layer | Completeness Owner | Method |
|-------|-------------------|--------|
| **Parameters** | PARAMETER_NORMALIZATION_v2.md | Tri-state: Numeric/NS/NA |
| **Domains** | SYSTEM_DOMAIN_SCORING_v2.md | Weight-based completeness |
| **Systems** | SYSTEM_DOMAIN_SCORING_v2.md | Blend toward 50 when sparse |
| **Objective Component** | THIS DOCUMENT | Exclude NA systems, renormalize |
| **Lifestyle Pillars** | THIS DOCUMENT | Unmeasured = 50 |
| **Overall Score** | THIS DOCUMENT | No additional adjustment |

### Key Rule

**Do NOT double-adjust for completeness.**

System scores arriving at this layer already include completeness penalties. We do not re-blend them toward 50 here.

### Completeness Indicators (Required for Display)

**Objective Completeness:**
```
Objective_Completeness = (# of systems with â‰¥1 domain assessed) / 8
```

**Subjective Completeness:**
```
Subjective_Completeness = (# of pillars with â‰¥1 item completed) / 5
```

**Overall Data Coverage:**
```
Overall_Coverage = (Objective_Completeness Ã— 0.70) + (Subjective_Completeness Ã— 0.30)
```

**Display requirements:**
- Show all three percentages on Level 1 dashboard
- If Overall_Coverage < 60%: Prominent warning about limited data
- If Overall_Coverage < 30%: Recommend comprehensive assessment before clinical decisions

---

## QUALITY ASSURANCE

### Validation Requirements

**Mathematical Validation:**
- [ ] All weights sum to 100% (objective systems, subjective pillars)
- [ ] Formula produces scores in 0-100 range for all valid inputs
- [ ] At-target patient (all 85s) yields overall = 85 âœ“
- [ ] Edge cases produce expected scores
- [ ] Hand calculations verified for 10+ patient scenarios

**Clinical Validation:**
- [ ] System weights reviewed by clinical panel (â‰¥3 experts)
- [ ] Pillar weights validated against lifestyle medicine evidence
- [ ] 70/30 split (objective/subjective) approved
- [ ] Worked examples make clinical sense
- [ ] Score interpretations appropriate

**User Experience Validation:**
- [ ] Patients understand overall score meaning (n=20+ tested)
- [ ] Breakdown (objective/subjective) is clear
- [ ] Action priorities resonate with users
- [ ] Completeness warnings are understandable

### Sensitivity Analysis

See `SCORING_GOVERNANCE.md` for detailed sensitivity testing procedures.

**Key tests:**
1. Vary system weights Â±5%: Overall scores shift <5 points (stable)
2. Test 60/40, 70/30, 80/20 objective/subjective splits
3. Vary pillar weights Â±10%: Overall scores remain clinically sensible

---

## WEIGHT REVISION PROCESS

### Governance

All weight changes follow the procedure defined in `SCORING_GOVERNANCE.md`:

1. **Proposal** - Document rationale and evidence
2. **Impact Analysis** - Recompute sample cohort (n=100+)
3. **Clinical Review** - Panel approval required
4. **Implementation** - Version increment, effective date
5. **Monitoring** - Track post-change effects

### Version Control

**Current weights are Version 1.0:**
- System weights: Evidence from WHO GBD 2023
- Pillar weights: Evidence from ACLM 2024, exercise medicine literature
- Objective/Subjective split: 70/30 from predictive validity studies
- Effective date: November 12, 2025
- Next scheduled review: November 2026

### Likely Future Revisions

**Flagged for future consideration:**
1. **Lifestyle pillar weights** - May increase Emotion/Environment as wellness integration matures
2. **Objective/Subjective split** - May adjust based on longitudinal outcome data
3. **System weights** - May refine based on population-specific mortality/morbidity data

---

## REVISION HISTORY

**Version 2.0.0 - November 12, 2025**
- **CRITICAL FIX:** Aligned 85-point baseline across all documents
- **CRITICAL FIX:** Clarified completeness governance (no double-adjustment)
- **IMPROVEMENT:** Rebalanced lifestyle pillar weights (Environment 10%â†’15%)
- **IMPROVEMENT:** Added explicit completeness indicators (objective/subjective/overall)
- **IMPROVEMENT:** Added clinical interpretation context guidance
- **CLEANUP:** Offloaded QA details to SCORING_GOVERNANCE.md
- **CLEANUP:** Offloaded detailed UI specs to DASHBOARD_LEVEL1_SPEC.md
- **ALIGNMENT:** Cross-referenced all related documents properly

**Version 1.0.0 - November 12, 2025**
- Initial specification (draft, had baseline inconsistency)

---

## RELATED DOCUMENTS

**Uses (inputs):**
- `SYSTEM_DOMAIN_SCORING_v2.md` - System health scores (already completeness-adjusted)
- Lifestyle questionnaires - Pillar scores

**Feeds into (outputs):**
- `BIOLOGICAL_AGE_SPEC.md` - Uses overall score
- `TRANSPARENCY_DISPLAY.md` - Attribution logic
- `DASHBOARD_LEVEL1_SPEC.md` - Display specifications

**Governance & Process:**
- `SCORING_GOVERNANCE.md` - QA, sensitivity analysis, weight revision procedures (shared)
- `CRITICAL_ALERTS.md` - Override logic for critical findings
- `CALIBRATION_VALIDATION.md` - Validation framework

---

**END OF COMPOSITE SCORING SPECIFICATION v2.0**

*This document defines the final aggregation of system and lifestyle data into a single overall health score. The 85-point baseline, evidence-based weighting, completeness governance, and critical alert overrides ensure clinical fidelity while maintaining patient comprehension.*

*Key Changes in v2.0: Fixed baseline inconsistency, clarified completeness handling, rebalanced lifestyle weights, streamlined content by offloading to governance and display docs.*
