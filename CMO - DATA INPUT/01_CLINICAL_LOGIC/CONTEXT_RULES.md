# CONTEXT-DEPENDENT SCORING RULES
## Patient Health Dashboard - Parameter Scoring Framework

**Document Type:** Core Clinical Logic  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - Part 3 of 4  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

This document is part of the **Parameter Scoring Framework** (read all four together):

1. `PARAMETER_NORMALIZATION.md` - Core normalization methods and formulas
2. `CALIBRATION_VALIDATION.md` - How to calibrate and validate parameters
3. **CONTEXT_RULES.md** (this document) - Patient-specific scoring adjustments and overrides
4. `TEMPORAL_SCORING.md` - Handling measurements over time and aberrant values

---

## DOCUMENT PURPOSE

This specification defines **context-dependent scoring adjustments** that override or modify standard normalization when patient-specific factors alter clinical interpretation.

**Context matters:**
- eGFR 135 in healthy person = excellent. eGFR 135 in diabetic = hyperfiltration warning.
- HbA1c 6.2% in young diabetic = target. HbA1c 6.2% in elderly diabetic = dangerous hypoglycemia risk.
- Albumin 5.8 g/dL = dehydration artifact, not "better than normal."

**This document provides:**
1. Framework for identifying context-dependent parameters
2. Rule specification format (IF-THEN logic)
3. Override types (target adjustment, score modification, color override, interpretation change)
4. Common context categories (pregnancy, medications, comorbidities, age extremes)
5. Worked examples for key parameters

---

## CONTEXT RULE FRAMEWORK

### When Context Rules Apply

**Triggers for context-dependent adjustments:**
1. **Pregnancy** - alters normal ranges for many parameters
2. **Medications** - may cause expected abnormalities
3. **Comorbidities** - change interpretation and targets
4. **Age extremes** - pediatric (<18) or very elderly (>85)
5. **Acute vs chronic** - same value, different urgency
6. **Treatment context** - dialysis, transplant, chemotherapy
7. **Artifact conditions** - dehydration, recent meal, exercise

### Rule Types

**Type 1: Target Adjustment**
- Changes personalized target (z = 0) based on context
- Most common type
- Example: BP target 130 for diabetes vs 120 for healthy adult

**Type 2: Score Override**
- Modifies calculated score for specific context
- Use sparingly
- Example: Cap eGFR score at 90 if diabetic (hyperfiltration concern)

**Type 3: Color/Zone Override**
- Changes color independent of score
- For situations where standard zones don't apply
- Example: Mark "high-normal" as yellow during pregnancy despite green score

**Type 4: Interpretation Override**
- Changes plain language message
- Adds context-specific guidance
- Example: "This is normal for your medication" vs standard interpretation

### Rule Specification Format

```
PARAMETER: [Parameter name]
CONTEXT RULE ID: [Unique identifier]
CONDITION: [When this rule applies]
OVERRIDE TYPE: [Target/Score/Color/Interpretation]
ADJUSTMENT: [What changes]
RATIONALE: [Clinical reasoning]
EVIDENCE: [Guideline or study citation]
PRIORITY: [If multiple rules apply, which takes precedence]
VERSION: [Rule version]
```

---

## CATEGORY 1: PREGNANCY ADJUSTMENTS

### Hemoglobin in Pregnancy

```
PARAMETER: Hemoglobin
CONTEXT RULE ID: HGB_PREG_001
CONDITION: Patient is pregnant
OVERRIDE TYPE: Target Adjustment
ADJUSTMENT:
  Normal female target: 13.0 g/dL
  Pregnancy target: 11.0 g/dL (WHO threshold for anemia in pregnancy)
RATIONALE: Physiologic hemodilution in pregnancy lowers Hb; <11 indicates true anemia
EVIDENCE: WHO 2011 guidelines
PRIORITY: 1 (overrides standard female target)
```

### Blood Pressure in Pregnancy

```
PARAMETER: Systolic Blood Pressure
CONTEXT RULE ID: SBP_PREG_001
CONDITION: Patient is pregnant
OVERRIDE TYPE: Target + Interpretation
ADJUSTMENT:
  Target: 120 mmHg (same as non-pregnant)
  BUT: â‰¥140 = gestational hypertension (requires immediate OB referral)
  AND: â‰¥160 = severe, emergency care
INTERPRETATION OVERRIDE: Add "Contact your OB immediately" for orange/red zones
RATIONALE: Hypertensive disorders of pregnancy are high-risk
EVIDENCE: ACOG 2019 guidelines
PRIORITY: 1
```

### Glucose in Pregnancy

```
PARAMETER: Fasting Glucose
CONTEXT RULE ID: GLU_PREG_001
CONDITION: Patient is pregnant
OVERRIDE TYPE: Target + Clinical Zones
ADJUSTMENT:
  Target: 90 mg/dL (tighter than non-pregnant)
  â‰¥92 mg/dL = gestational diabetes threshold (not 100)
  Clinical zones shift downward
RATIONALE: Tighter glucose control needed in pregnancy
EVIDENCE: IADPSG/ADA gestational diabetes criteria
PRIORITY: 1
```

---

## CATEGORY 2: MEDICATION-INDUCED CHANGES

### Creatinine on Dialysis

```
PARAMETER: Creatinine
CONTEXT RULE ID: CREAT_DIAL_001
CONDITION: Patient on hemodialysis or peritoneal dialysis
OVERRIDE TYPE: Interpretation + Color
ADJUSTMENT:
  Score calculation remains standard
  BUT: Color override - even red scores shown as yellow/orange with message:
  "Elevated between dialysis sessions is expected. Dialysis adequacy is being monitored."
RATIONALE: Creatinine elevation expected between sessions; focus on dialysis adequacy (Kt/V) instead
EVIDENCE: KDOQI dialysis adequacy guidelines
PRIORITY: 1
```

### Potassium on ACE Inhibitor/ARB

```
PARAMETER: Potassium
CONTEXT RULE ID: K_ACEI_001
CONDITION: Patient taking ACE inhibitor OR ARB
OVERRIDE TYPE: Interpretation
ADJUSTMENT:
  Score calculation unchanged
  Mild hyperkalemia (5.2-5.5 mEq/L): Add note
  "Your blood pressure medication can raise potassium. Your doctor is monitoring this."
RATIONALE: Expected mild elevation; avoid alarm if clinician aware
EVIDENCE: Standard clinical practice
PRIORITY: 2 (still alert if >5.8)
```

### INR on Warfarin

```
PARAMETER: INR
CONTEXT RULE ID: INR_WARF_001
CONDITION: Patient on warfarin therapy
OVERRIDE TYPE: Target Adjustment + Zones
ADJUSTMENT:
  Standard target: 1.0 (not therapeutic)
  Warfarin target: 2.0-3.0 (most indications) or 2.5-3.5 (mechanical valve)
  Redefine zones:
    <1.5: Subtherapeutic (orange) - bleeding risk reduced but clot risk increased
    1.5-2.0: Low therapeutic (yellow) - adjust dose
    2.0-3.0: Therapeutic (green) - optimal
    3.0-4.0: High therapeutic (yellow) - monitor closely
    >4.0: Supratherapeutic (red) - bleeding risk, hold dose
RATIONALE: INR target depends on indication; therapeutic range is abnormal without warfarin
EVIDENCE: ACC/AHA anticoagulation guidelines
PRIORITY: 1
```

---

## CATEGORY 3: COMORBIDITY-SPECIFIC RULES

### eGFR in Diabetes (Hyperfiltration)

```
PARAMETER: eGFR
CONTEXT RULE ID: eGFR_DM_001
CONDITION: Patient has diabetes diagnosis
OVERRIDE TYPE: Score Cap + Color + Interpretation
ADJUSTMENT:
  IF eGFR >120 mL/min:
    Cap score at 90 (even if calculation gives 95+)
    Color: YELLOW (override GREEN)
    Interpretation: "Very high kidney function may indicate hyperfiltration, an early sign of diabetic kidney stress. Your doctor will monitor closely."
RATIONALE: Hyperfiltration in diabetes precedes progressive CKD decline
EVIDENCE: KDIGO diabetes + CKD guidelines
PRIORITY: 1
```

### HbA1c Target by Age and Comorbidity

```
PARAMETER: HbA1c
CONTEXT RULE ID: HbA1c_AGE_001
CONDITION: Patient has diabetes
OVERRIDE TYPE: Target Adjustment

TARGET LOGIC:
IF age <65 AND no CVD AND no hypoglycemia history:
  Target = 6.5% (tight control, prevent complications)

ELSE IF age 65-75 AND (CVD OR limited life expectancy):
  Target = 7.5% (moderate control, avoid hypoglycemia)

ELSE IF age >75 OR frailty OR frequent hypoglycemia:
  Target = 8.0% (relaxed control, safety priority)

ELSE:
  Target = 7.0% (standard ADA target)

RATIONALE: Individualized A1c targets balance benefit vs hypoglycemia risk
EVIDENCE: ADA Standards of Care 2023
PRIORITY: 1
```

### Blood Pressure in CKD with Proteinuria

```
PARAMETER: Systolic Blood Pressure
CONTEXT RULE ID: SBP_CKD_001
CONDITION: Patient has CKD AND UACR >300 mg/g (proteinuria)
OVERRIDE TYPE: Target Adjustment
ADJUSTMENT:
  Standard target: 130 mmHg
  CKD + proteinuria target: 120 mmHg (more aggressive)
RATIONALE: Lower BP target slows CKD progression in proteinuric CKD
EVIDENCE: KDIGO 2021 guidelines
PRIORITY: 1
```

---

## CATEGORY 4: AGE-SPECIFIC ADJUSTMENTS

### Creatinine in Elderly

```
PARAMETER: Creatinine
CONTEXT RULE ID: CREAT_ELDERLY_001
CONDITION: Age â‰¥75
OVERRIDE TYPE: Target + Interpretation
ADJUSTMENT:
  Standard target (age 30-60): 1.0 mg/dL
  Elderly target: 1.1 mg/dL (slightly higher acceptable due to decreased muscle mass)
  
  IF creatinine <0.6 mg/dL:
    Interpretation override: "Low creatinine may indicate decreased muscle mass (sarcopenia). Nutrition and physical therapy may help."
RATIONALE: Elderly have lower muscle mass, affecting baseline creatinine
EVIDENCE: Geriatric medicine consensus
PRIORITY: 1
```

### Blood Pressure in Elderly

```
PARAMETER: Systolic Blood Pressure
CONTEXT RULE ID: SBP_ELDERLY_001
CONDITION: Age â‰¥80
OVERRIDE TYPE: Target Adjustment
ADJUSTMENT:
  Standard target: 120 mmHg
  Age â‰¥80 target: 140 mmHg (more permissive to avoid orthostatic hypotension)
RATIONALE: Very elderly benefit less from intensive BP lowering; fall risk from hypotension
EVIDENCE: HYVET trial, geriatric guidelines
PRIORITY: 1
```

---

## CATEGORY 5: ACUTE VS CHRONIC CONTEXT

### Glucose: Fasting vs Non-Fasting

```
PARAMETER: Glucose
CONTEXT RULE ID: GLU_TIMING_001
CONDITION: Glucose measured <2 hours after meal (non-fasting)
OVERRIDE TYPE: Interpretation
ADJUSTMENT:
  Score calculation uses fasting targets
  BUT: Add interpretation note:
  "This was measured after eating. A fasting glucose test provides more accurate assessment."
  Do NOT alarm for values <200 mg/dL if post-meal
RATIONALE: Post-meal glucose naturally elevated; different thresholds apply
EVIDENCE: ADA diagnostic criteria
PRIORITY: 1
```

### Troponin: Acute vs Chronic Elevation

```
PARAMETER: Troponin
CONTEXT RULE ID: TROP_CHRONIC_001
CONDITION: Patient has CKD Stage 4-5 (eGFR <30)
OVERRIDE TYPE: Interpretation
ADJUSTMENT:
  Mild elevations (0.02-0.05 ng/mL): Add note
  "Mild troponin elevation can occur with advanced kidney disease. Your doctor will assess if this represents heart injury."
  Do NOT auto-alarm for values <0.05 unless rising trend
RATIONALE: Chronic troponin elevation common in CKD; focus on changes not absolute level
EVIDENCE: Cardiology/nephrology literature
PRIORITY: 2 (still alarm if >0.10 or rapidly rising)
```

---

## CATEGORY 6: ARTIFACT CONDITIONS

### Albumin in Dehydration

```
PARAMETER: Albumin
CONTEXT RULE ID: ALB_DEHY_001
CONDITION: Albumin >5.5 g/dL (above physiologic maximum)
OVERRIDE TYPE: Interpretation + Color
ADJUSTMENT:
  Score calculation may give 90-95
  Color: YELLOW (override GREEN)
  Interpretation: "Very high albumin suggests dehydration (concentrated blood). Drink fluids and recheck when well-hydrated."
RATIONALE: Albumin >5.5 is hemoconcentration, not true elevation
EVIDENCE: Clinical chemistry principles
PRIORITY: 1
```

### Hemoglobin Post-Exercise

```
PARAMETER: Hemoglobin
CONTEXT RULE ID: HGB_EXERCISE_001
CONDITION: Blood drawn <2 hours after intense exercise
OVERRIDE TYPE: Interpretation
ADJUSTMENT:
  Add note: "Blood drawn shortly after exercise may show falsely elevated hemoglobin due to temporary hemoconcentration. Retest at rest if concerned."
RATIONALE: Exercise causes transient hemoconcentration
EVIDENCE: Exercise physiology literature
PRIORITY: 3 (low priority, informational)
```

---

## IMPLEMENTATION LOGIC

### Rule Engine Pseudocode

```
FUNCTION calculate_parameter_score(patient, parameter, value):
  
  # Step 1: Get base target and normalization parameters
  base_target = get_personalized_target(patient, parameter)
  SD = get_standard_deviation(parameter)
  coefficients = get_penalty_coefficients(parameter)
  
  # Step 2: Check for applicable context rules
  applicable_rules = find_context_rules(patient, parameter)
  
  # Step 3: Apply rules in priority order
  FOR EACH rule IN applicable_rules SORTED BY priority:
    
    IF rule.type == "TARGET_ADJUSTMENT":
      base_target = rule.adjusted_target
    
    ELSE IF rule.type == "SCORE_OVERRIDE":
      # Calculate base score first
      base_score = calculate_normalized_score(value, base_target, SD, coefficients)
      # Apply override
      base_score = rule.apply_score_adjustment(base_score, value, patient)
    
    ELSE IF rule.type == "COLOR_OVERRIDE":
      # Score unchanged, but color may be overridden later
      color_override = rule.get_color_override(value, patient)
    
    ELSE IF rule.type == "INTERPRETATION_OVERRIDE":
      # Store interpretation override to apply to display
      interpretation_override = rule.get_interpretation(value, patient)
  
  # Step 4: Calculate final score with adjusted target
  final_score = calculate_normalized_score(value, base_target, SD, coefficients)
  
  # Step 5: Determine color zone (with possible override)
  IF color_override EXISTS:
    color = color_override
  ELSE:
    color = get_color_from_score(final_score)
  
  # Step 6: Generate interpretation (with possible override)
  IF interpretation_override EXISTS:
    interpretation = interpretation_override
  ELSE:
    interpretation = get_standard_interpretation(final_score, color, parameter)
  
  RETURN {
    score: final_score,
    color: color,
    interpretation: interpretation,
    rules_applied: [list of rule IDs],
    target_used: base_target
  }
```

### Rule Priority System

**Priority 1:** Must apply (safety-critical, guideline-mandated)
- Pregnancy targets
- Dialysis patients
- Critical medication interactions

**Priority 2:** Should apply (clinically important, common scenarios)
- Age-based adjustments
- Common comorbidity targets
- Expected medication effects

**Priority 3:** May apply (informational, context-dependent)
- Timing issues (post-meal, post-exercise)
- Minor artifacts
- Educational notes

**Conflict resolution:** If multiple rules of same priority, use most specific rule (e.g., "diabetes + CKD" beats "diabetes alone").

---

## RULE DOCUMENTATION TEMPLATE

Use this template for every new context rule:

```markdown
### [Rule Title]

```
PARAMETER: [Name]
CONTEXT RULE ID: [ID]
CONDITION: [Specific trigger condition]
OVERRIDE TYPE: [Target/Score/Color/Interpretation]
ADJUSTMENT: [Detailed description of change]
RATIONALE: [Clinical reasoning]
EVIDENCE: [Citation]
PRIORITY: [1/2/3]
EFFECTIVE DATE: [Date]
VERSION: [X.Y]
REVIEWERS: [Names]
NEXT REVIEW: [Date]
```

**Example scenarios:**
- Patient A: [Describe patient] â†’ [Describe how rule applies]
- Patient B: [Describe patient] â†’ [Describe standard scoring without rule]

**Validation:**
- [ ] Clinical panel reviewed (â‰¥2 clinicians agreed)
- [ ] Edge cases tested
- [ ] Conflicts with other rules checked
- [ ] Patient comprehension validated
```

---

## QUALITY ASSURANCE

### Rule Validation Checklist

For each context rule:
- [ ] Condition is clearly defined and testable
- [ ] Clinical rationale is evidence-based
- [ ] Adjustment is specific and implementable
- [ ] Priority level assigned appropriately
- [ ] Conflicts with other rules resolved
- [ ] Tested with real patient scenarios
- [ ] Clinical panel approval (â‰¥2 clinicians)
- [ ] Documentation complete

### Common Pitfalls to Avoid

**1. Over-specification**
- Bad: "IF age = 67.3 AND HbA1c = 7.23..."
- Good: "IF age >65 AND HbA1c >7.0..."

**2. Circular logic**
- Bad: Rule adjusts target based on score that depends on target
- Good: Rules based on independent patient characteristics

**3. Conflicting rules**
- Bad: Rule A says target 120, Rule B says target 140 for same patient
- Good: Clear priority system, specific conditions

**4. Overly complex conditions**
- Bad: "IF (age >65 OR (age >60 AND smoker)) AND (diabetes OR (prediabetes AND BMI >30)) AND..."
- Good: Break into multiple simpler rules with clear priorities

---

## REVISION HISTORY

**Version 1.1.0 - November 19, 2025**
- Added integration with Medical History Library
- Enhanced comorbidity-specific rules section
- Cross-referenced diagnosis-based context rules

**Version 1.0.0 - November 12, 2025**
- Initial specification
- Six context categories defined
- Rule framework and implementation logic specified
- Priority system established
- Example rules for common scenarios

---

## RELATED DOCUMENTS

**Core Framework:**
- `PARAMETER_NORMALIZATION_v2.md` - Core normalization methods
- `CALIBRATION_VALIDATION.md` - Coefficient optimization and validation
- `TEMPORAL_SCORING.md` - Time-based scoring
- `SYSTEM_DOMAIN_SCORING_v2.md` - Domain-level score aggregation

**Medical History Integration:**
- `MEDICAL_HISTORY_TIER1_LIBRARY.md` - 132 diagnoses with detailed context rules and score modifiers
  - **Note:** For diagnosis-based context rules (diabetes targets, CKD adjustments, etc.), refer to Medical History Library for complete specifications including:
    - Parameter target adjustments by diagnosis
    - Baseline score modifiers (domain-level)
    - Severity/control modifiers
    - Treatment impact adjustments
  - This document (CONTEXT_RULES.md) provides the **framework** for how rules apply
  - Medical History Library provides **specific rules** for each diagnosis

**Architecture:**
- `PROJECT_SPECIFICATION_v2.md` - Master project architecture
- `PROJECT_INSTRUCTIONS_MASTER.md` - Team coordination and document map

---

**END OF CONTEXT-DEPENDENT SCORING RULES**

*Context matters. Rules ensure clinical interpretation adapts to patient-specific factors.*
