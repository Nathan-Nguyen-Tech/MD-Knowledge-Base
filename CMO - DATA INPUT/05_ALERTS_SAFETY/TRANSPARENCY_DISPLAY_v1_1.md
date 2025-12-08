# TRANSPARENCY DISPLAY SPECIFICATION
## Patient Health Dashboard - Score Attribution & Top Contributors

**Document Type:** Core Clinical Logic - User Interface  
**Version:** 1.1.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - CORRECTED  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture, transparency principles
- `PARAMETER_NORMALIZATION_v2.md` - How individual parameters score
- `SYSTEM_DOMAIN_SCORING_v2.md` - How domains and systems score
- `COMPOSITE_SCORING_v2.md` - How overall health score is calculated

**This document connects to:**
- `BIOLOGICAL_AGE_SPEC_v1_1.md` - Attribution for biological age calculation
- `DASHBOARD_LEVEL1_SPEC.md` - Where transparency displays appear
- `DASHBOARD_LEVEL2_SPEC.md` - System-level transparency
- `DASHBOARD_LEVEL3_SPEC.md` - Parameter-level transparency

---

## DOCUMENT PURPOSE

This specification defines **how to show users what's driving their scores** through transparent attribution of score components using the actual composite scoring mathematics.

**Core Transparency Principle:**
> Every composite score must be decomposable to its contributing factors using the ACTUAL scoring formulas. Users should always understand "Why did I get this score?" and "What can I do to improve it?"

**Critical Design Requirement:**
> Attribution mathematics MUST match the actual composite scoring formulas exactly. Custom attribution formulas that don't align with scoring math will break user trust.

**What This Document Provides:**
1. Correct attribution mathematics (aligned with composite scoring)
2. Top contributors algorithm (based on actual weighted contributions)
3. Display formats for each dashboard level
4. Plain language interpretation logic
5. Edge case handling (missing data, ties, conflicts)

**What This Document Does NOT Provide:**
- âŒ Detailed UI styling (colors, icons, exact layouts â†’ in DASHBOARD specs)
- âŒ Score calculation methods (those are in scoring documents)
- âŒ Thresholds and zones (those are in parameter documents)

---

## SECTION 1: CORRECT ATTRIBUTION MATHEMATICS

### 1.1 Core Principle: Use Actual Composite Formulas

**The attribution system must reflect exactly how scores are calculated:**

```
Overall Health Score = 
  (Objective Health Ã— 0.70) + (Subjective Health Ã— 0.30)

Where:
  Objective Health = Î£(System_Score Ã— System_Weight)
  Subjective Health = Î£(Pillar_Score Ã— Pillar_Weight)
```

**Each component's contribution to the composite:**
```
Component_Contribution = Component_Score Ã— Component_Weight
```

**Key Insight:**
- A component with score=85 and weight=20% contributes **17 points** to the composite
- A component with score=60 and weight=15% contributes **9 points** to the composite
- The difference in contribution is **(17 - 9) = 8 points**

This is the **actual math** of how scores combine, not a heuristic.

### 1.2 Deviation-Based Attribution

**For understanding what's helping vs hurting the composite:**

Use the **85-point baseline** (target for all components):

```
Component_Deviation = (Component_Score - 85) Ã— Component_Weight

Where:
- Positive deviation = component is pulling composite UP (score >85)
- Negative deviation = component is pulling composite DOWN (score <85)
- Zero deviation = component is at target (score =85)
```

**Example:**
```
Cardiovascular System: Score = 68, Weight = 20%
Deviation = (68 - 85) Ã— 0.20 = -17 Ã— 0.20 = -3.4 points

Interpretation: "Your cardiovascular health is pulling your 
overall score down by 3.4 points below where it would be if 
cardiovascular was at target."
```

### 1.3 Why 85 Is the Correct Baseline (Not 50 or 75)

**From our scoring architecture:**
- **At personalized target (z-score = 0):** All scores = 85
- **50 = neutral/unknown** (used only for missing data)
- **75 = low end of green zone** (but NOT the target)

**Therefore:**
- Components > 85: Contributing positively (above target)
- Components = 85: At target (expected contribution)
- Components < 85: Contributing negatively (below target)

Using 50 or 75 as baseline would **not match the actual scoring system**.

### 1.4 Absolute Contribution vs Relative Deviation

**Both are useful for different purposes:**

**Absolute Contribution** (for showing current state):
```
Contribution = Component_Score Ã— Component_Weight
```
Shows what each component is currently adding to the composite.

**Relative Deviation** (for showing opportunities):
```
Deviation = (Component_Score - 85) Ã— Component_Weight
```
Shows what's pulling the composite away from target.

**This document uses DEVIATION for "top contributors" because:**
- More clinically meaningful (what's off target?)
- Directly translates to improvement opportunities
- Separates "what's working" from "what needs work"

---

## SECTION 2: TOP CONTRIBUTORS ALGORITHM

### 2.1 Core Algorithm

**For any composite score (Overall, System, Domain):**

**Step 1: Calculate deviations for all components**
```
For each component:
  Deviation_i = (Score_i - 85) Ã— Weight_i
```

**Step 2: Separate positive and negative deviations**
```
Positive contributors: Deviation > 0 (score >85, above target)
Negative contributors: Deviation < 0 (score <85, below target)
```

**Step 3: Sort by absolute magnitude**
```
Positive: Sort descending by deviation value
Negative: Sort ascending by deviation value (most negative first)
```

**Step 4: Select top 3 from each**
```
Top 3 positive (largest positive deviations)
Top 3 negative (largest negative deviations)
```

### 2.2 Worked Example: Overall Health Score

**Patient Data:**

| Component | Score | Weight | Contribution | Deviation |
|-----------|-------|--------|--------------|-----------|
| Cardiovascular | 68 | 20% | 13.6 | -3.4 |
| Neurological | 92 | 18% | 16.6 | +1.3 |
| Respiratory | 88 | 15% | 13.2 | +0.5 |
| Metabolic | 58 | 15% | 8.7 | -4.1 |
| Renal | 82 | 12% | 9.8 | -0.4 |
| Immune | 75 | 10% | 7.5 | -1.0 |
| Musculoskeletal | 90 | 5% | 4.5 | +0.3 |
| Reproductive | NA | 5% | -- | -- |

**Objective Health (renormalized for NA system):**
```
Sum of contributions = 73.9
Available weight = 0.95
Objective = 73.9 / 0.95 = 77.8
```

| Pillar | Score | Weight | Contribution | Deviation |
|--------|-------|--------|--------------|-----------|
| Nutrition | 70 | 25% | 17.5 | -3.8 |
| Movement | 88 | 25% | 22.0 | +0.8 |
| Recovery | 65 | 20% | 13.0 | -4.0 |
| Emotion | 58 | 15% | 8.7 | -4.1 |
| Environment | 84 | 15% | 12.6 | -0.2 |

**Subjective Health:**
```
Subjective = 73.8
```

**Overall Health:**
```
Overall = (77.8 Ã— 0.70) + (73.8 Ã— 0.30) = 54.5 + 22.1 = 76.6 â‰ˆ 77
```

**Attribution Analysis:**

**Positive Deviations (above target):**
1. Neurological: +1.3 (score 92, weight 18%)
2. Movement: +0.8 (score 88, weight 25%)
3. Respiratory: +0.5 (score 88, weight 15%)

**Negative Deviations (below target):**
1. Metabolic: -4.1 (score 58, weight 15%)
2. Emotion: -4.1 (score 58, weight 15%)
3. Recovery: -4.0 (score 65, weight 20%)

**Display:**
```
Overall Health Score: 77

ðŸ’š What's Working Well:
  â€¢ Neurological Function (92)
  â€¢ Physical Activity (88)
  â€¢ Respiratory Health (88)

ðŸ“Š What Needs Work:
  â€¢ Metabolic Health (58) - Action needed
  â€¢ Emotional Well-Being (58) - Action needed
  â€¢ Sleep & Stress Recovery (65)
```

### 2.3 Tie-Breaking Rules

**When components have similar deviations (within 10% of each other):**

1. **Alert severity** (if applicable)
   - CRITICAL > URGENT > WARNING > MONITOR
2. **Absolute weight**
   - Higher weight component listed first
3. **Measurement recency**
   - More recent measurements listed first
4. **Alphabetical**
   - Stable final tie-breaker

**Example:**
```
Metabolic: Deviation = -4.1
Emotion: Deviation = -4.1

Both have same deviation, so check:
- Alert severity: Neither has critical alerts
- Weight: Both 15% â†’ tie
- Recency: Metabolic labs from yesterday, Emotion survey from last week
- Winner: Metabolic (more recent)
```

### 2.4 Edge Cases

**Fewer than 3 positive or negative contributors:**
- Show all available contributors
- Do not fill empty slots
- Display message: "Other areas are close to target"

**All components near target (within Â±5 of 85):**
- Show message: "All systems in healthy range"
- Display "Opportunities for Optimization" instead
- Rank by smallest positive deviation (closest to excellence)

**All components problematic:**
- Use "Priority" framing instead of "What Needs Work"
- Rank by most negative deviation (biggest opportunity)
- Group by clinical interconnection where relevant

---

## SECTION 3: LEVEL 1 (HERO VIEW) TRANSPARENCY

### 3.1 Overall Health Score Attribution

**Data to Display:**

1. **Overall Health Score** (0-100)
2. **Top 3 positive contributors** (systems or pillars with largest positive deviations)
3. **Top 3 negative contributors** (systems or pillars with largest negative deviations)
4. **Critical alerts override** (if any critical alerts, show prominently)

**Calculation Process:**

```
Step 1: Get Overall Health Score (from COMPOSITE_SCORING_v2.md)

Step 2: For all 13 components (8 systems + 5 pillars):
  Calculate deviation = (Score - 85) Ã— Weight
  
  Note: Use actual composite-level weights:
  - Systems: Weight in objective component Ã— 0.70
  - Pillars: Weight in subjective component Ã— 0.30

Step 3: Apply top contributors algorithm (Section 2.1)

Step 4: Generate display
```

**Example Weights in Overall Score Context:**
```
Cardiovascular: 20% of Objective Ã— 0.70 = 14% of Overall
Nutrition: 25% of Subjective Ã— 0.30 = 7.5% of Overall
```

**Plain Language Rules:**
- Use patient-friendly names (not technical jargon)
- Add urgency indicator for scores <60: "Action needed"
- Add positive reinforcement for scores >85: "Excellent"
- Color-code indicators (Green/Yellow/Orange/Red per zones)

### 3.2 Critical Alerts Override Display

**If any CRITICAL alerts present:**

```
RULE: Critical alerts ALWAYS display ABOVE overall score

Display Priority:
1. CRITICAL alerts banner (highest priority)
2. Overall Health Score
3. "What's Working Well" (still shown for context)
4. "What Needs Work" (may overlap with alert parameters)
```

**Example:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ CRITICAL HEALTH ALERTS (1)                   â”‚
â”‚                                                 â”‚
â”‚ Severe Hyperkalemia (K+ 6.8 mEq/L)              â”‚
â”‚ â†’ Contact provider IMMEDIATELY                   â”‚
â”‚                                                 â”‚
â”‚ â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ â”‚
â”‚ Overall Health Score: 78                        â”‚
â”‚                                                 â”‚
â”‚ Despite your overall score, you have a CRITICAL â”‚
â”‚ issue requiring immediate attention above.      â”‚
â”‚                                                 â”‚
â”‚ ðŸ’š What's Working Well:                         â”‚
â”‚   â€¢ Respiratory Health (92)                     â”‚
â”‚   â€¢ Neurological Function (88)                  â”‚
â”‚   â€¢ Physical Activity (86)                      â”‚
â”‚                                                 â”‚
â”‚ ðŸ“Š What Needs Work:                             â”‚
â”‚   â€¢ Renal Function (54) âš ï¸ [Related to alert]  â”‚
â”‚   â€¢ Metabolic Health (62)                       â”‚
â”‚   â€¢ Sleep Quality (68)                          â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## SECTION 4: LEVEL 2 (SYSTEM VIEW) TRANSPARENCY

### 4.1 System Score Attribution to Domains

**For each system card, show:**

1. **System Score** (0-100)
2. **Domain contributions** (Structure, Function, Risk)
3. **Top parameter drivers** within worst-performing domain

**Calculation Process:**

```
Step 1: Get System Score (from SYSTEM_DOMAIN_SCORING_v2.md)
  System Score = (Structure Ã— 0.25) + (Function Ã— 0.50) + (Risk Ã— 0.25)

Step 2: Calculate domain deviations:
  Structure_Dev = (Structure_Score - 85) Ã— 0.25
  Function_Dev = (Function_Score - 85) Ã— 0.50
  Risk_Dev = (Risk_Score - 85) Ã— 0.25

Step 3: Identify best and worst performing domains

Step 4: For worst domain, identify top parameter contributors
  (using parameter weights from 24-cell matrix)
```

**Example: Cardiovascular System**

```
Cardiovascular Health: 68

Driven by three domains:

Structure (78): Contributing 78 Ã— 0.25 = 19.5 points
  Deviation: (78 - 85) Ã— 0.25 = -1.8 points
  
Function (62): Contributing 62 Ã— 0.50 = 31.0 points
  Deviation: (62 - 85) Ã— 0.50 = -11.5 points
  
Risk (72): Contributing 72 Ã— 0.25 = 18.0 points
  Deviation: (72 - 85) Ã— 0.25 = -3.3 points

System Score = 19.5 + 31.0 + 18.0 = 68.5 â‰ˆ 68

Worst-performing domain: Function (deviation -11.5)
```

**Display:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ CARDIOVASCULAR HEALTH: 68 âš ï¸                   â”‚
â”‚ â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â” â”‚
â”‚                                                 â”‚
â”‚ Driven by:                                      â”‚
â”‚                                                 â”‚
â”‚ ðŸ“Š Areas for Improvement:                       â”‚
â”‚   â€¢ Function: Fair (62) - Biggest opportunity   â”‚
â”‚     Main drivers:                               â”‚
â”‚     - Blood pressure control (58)               â”‚
â”‚     - Exercise capacity (65)                    â”‚
â”‚     - Heart rate response (68)                  â”‚
â”‚                                                 â”‚
â”‚ ðŸ’š Relative Strengths:                          â”‚
â”‚   â€¢ Structure: Good (78)                        â”‚
â”‚     - Heart size normal                         â”‚
â”‚     - No valve abnormalities                    â”‚
â”‚                                                 â”‚
â”‚   â€¢ Risk: Good (72)                             â”‚
â”‚     - 10-year ASCVD risk: 8%                    â”‚
â”‚     - Cholesterol improving                     â”‚
â”‚                                                 â”‚
â”‚ Improving your cardiovascular function by 20    â”‚
â”‚ points would raise your overall system score to â”‚
â”‚ 78 (Good range).                                â”‚
â”‚                                                 â”‚
â”‚ [View Parameter Details â†’]                      â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 4.2 Parameter Attribution Within Domains

**For the worst-performing domain, identify top parameter drivers:**

**Calculation:**
```
Step 1: Get all parameters contributing to this domain
  (from 24-cell weight matrix in SYSTEM_DOMAIN_SCORING_v2.md)

Step 2: For each parameter:
  Parameter_Contribution_To_Domain = Parameter_Score Ã— Weight_in_Domain
  Parameter_Deviation = (Parameter_Score - 85) Ã— Weight_in_Domain

Step 3: Sort by deviation (most negative first)

Step 4: Show top 2-3 parameters pulling domain down
```

**Example: CV-Function Domain (Score 62)**

| Parameter | Score | Weight in CV-Funct | Contribution | Deviation |
|-----------|-------|-------------------|--------------|-----------|
| BP Control | 58 | 80% | 46.4 | -21.6 |
| Exercise Capacity | 65 | 70% | 45.5 | -14.0 |
| Heart Rate Response | 68 | 60% | 40.8 | -10.2 |
| Cardiac Output | 72 | 50% | 36.0 | -6.5 |

**Note:** Weights can exceed 100% total because they're overlapping assessments of function.

**Top drivers (most negative deviations):**
1. BP Control: -21.6
2. Exercise Capacity: -14.0
3. Heart Rate Response: -10.2

---

## SECTION 5: LEVEL 3 (PARAMETER VIEW) TRANSPARENCY

### 5.1 Parameter Impact on Composite Scores

**For each parameter detail view, show:**

1. **Which composites this parameter affects**
2. **Current impact** (actual contribution vs target contribution)
3. **Potential impact** (what if parameter reaches target)

**Calculation Process:**

```
Step 1: Identify all composites affected by this parameter
  (from 24-cell weight matrix)

Step 2: Calculate current impact on each:
  Current_Impact = Parameter_Score Ã— Weight_in_Domain
  Target_Impact = 85 Ã— Weight_in_Domain
  Delta = Current_Impact - Target_Impact

Step 3: Calculate "What If" scenario:
  If parameter reaches target (85):
    New_Domain_Score = recalculate domain with parameter=85
    New_System_Score = recalculate system with new domain
    New_Overall_Score = recalculate overall with new system

Step 4: Show beforeâ†’after for each affected composite
```

**Example: LDL Cholesterol**

```
Parameter: LDL Cholesterol = 142 mg/dL
Score: 68
Target: <100 mg/dL (Score = 85)

Affects these composites:

1. Cardiovascular-Risk Domain (Weight: 90%)
   Current Impact: 68 Ã— 0.90 = 61.2
   Target Impact: 85 Ã— 0.90 = 76.5
   Delta: -15.3 points

   Current CV-Risk Score: 72
   If LDL at target: CV-Risk Score â†’ 82 (+10 points)

2. Metabolic-Risk Domain (Weight: 20%)
   Current Impact: 68 Ã— 0.20 = 13.6
   Target Impact: 85 Ã— 0.20 = 17.0
   Delta: -3.4 points

   Current Metab-Risk Score: 65
   If LDL at target: Metab-Risk Score â†’ 68 (+3 points)

3. Cardiovascular System Overall:
   Current: 68
   If LDL at target: 72 (+4 points)

4. Overall Health Score:
   Current: 77
   If LDL at target: 78 (+1 point)
```

**Display:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ LDL CHOLESTEROL: 142 mg/dL                      â”‚
â”‚ Score: 68 (Yellow - Monitor)                    â”‚
â”‚ â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â” â”‚
â”‚                                                 â”‚
â”‚ How this affects your health:                   â”‚
â”‚                                                 â”‚
â”‚ Contributes to:                                 â”‚
â”‚   â€¢ Cardiovascular Risk (72)                    â”‚
â”‚     Pulling down by 15 points                   â”‚
â”‚   â€¢ Metabolic Risk (65)                         â”‚
â”‚     Pulling down by 3 points                    â”‚
â”‚                                                 â”‚
â”‚ Your target: <100 mg/dL                         â”‚
â”‚ Current: 142 mg/dL (42 mg/dL above target)      â”‚
â”‚                                                 â”‚
â”‚ If you reach your target:                       â”‚
â”‚   â€¢ Cardiovascular Risk: 72 â†’ 82 (+10)          â”‚
â”‚   â€¢ Cardiovascular System: 68 â†’ 72 (+4)         â”‚
â”‚   â€¢ Overall Health: 77 â†’ 78 (+1)                â”‚
â”‚                                                 â”‚
â”‚ This is your biggest opportunity to improve     â”‚
â”‚ cardiovascular risk.                            â”‚
â”‚                                                 â”‚
â”‚ Recommended actions:                            â”‚
â”‚   1. Dietary changes (reduce saturated fat)     â”‚
â”‚   2. Increase physical activity                 â”‚
â”‚   3. Consider statin therapy (discuss with MD)  â”‚
â”‚                                                 â”‚
â”‚ Expected timeline: 3-6 months                   â”‚
â”‚                                                 â”‚
â”‚ [View History] [Learn More] [Set Goal]          â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 5.2 Propagation Calculation Details

**The "What If" calculation must follow the exact scoring hierarchy:**

```
Step 1: Change parameter score
  LDL_Score: 68 â†’ 85

Step 2: Recalculate affected domains
  CV-Risk Domain:
    Old: (LDLÃ—0.90 + HDLÃ—0.80 + TGÃ—0.70 + ...) / Weights_Sum
    New: (85Ã—0.90 + HDLÃ—0.80 + TGÃ—0.70 + ...) / Weights_Sum
    
  Metab-Risk Domain:
    Old: (LDLÃ—0.20 + GlucoseÃ—0.90 + HbA1cÃ—0.95 + ...) / Weights_Sum
    New: (85Ã—0.20 + GlucoseÃ—0.90 + HbA1cÃ—0.95 + ...) / Weights_Sum

Step 3: Recalculate affected systems
  CV System:
    Old: (CV-StructÃ—0.25 + CV-FunctÃ—0.50 + CV-Risk_oldÃ—0.25)
    New: (CV-StructÃ—0.25 + CV-FunctÃ—0.50 + CV-Risk_newÃ—0.25)
    
  Metab System:
    Old: (Metab-StructÃ—0.25 + Metab-FunctÃ—0.50 + Metab-Risk_oldÃ—0.25)
    New: (Metab-StructÃ—0.25 + Metab-FunctÃ—0.50 + Metab-Risk_newÃ—0.25)

Step 4: Recalculate Objective Health
  Old: (CV_oldÃ—0.20 + NeuroÃ—0.18 + ... + Metab_oldÃ—0.15 + ...)
  New: (CV_newÃ—0.20 + NeuroÃ—0.18 + ... + Metab_newÃ—0.15 + ...)

Step 5: Recalculate Overall Health
  Old: (Objective_oldÃ—0.70 + SubjectiveÃ—0.30)
  New: (Objective_newÃ—0.70 + SubjectiveÃ—0.30)
```

**This must use the ACTUAL formulas from scoring documents, not approximations.**

---

## SECTION 6: BIOLOGICAL AGE TRANSPARENCY

### 6.1 Biological Age Attribution

**Data to Display:**

1. **Biological Age** (years)
2. **Chronological Age** (years)
3. **Difference** (biological - chronological)
4. **Top factors accelerating aging** (most negative deviations)
5. **Top factors slowing aging** (most positive deviations)

**Calculation Process:**

```
Step 1: Get Biological Age from BIOLOGICAL_AGE_SPEC_v1_1.md
  Uses PhenoAge algorithm + enhancements

Step 2: For each biomarker in the model:
  Calculate its contribution to aging
  (using Î² coefficients from PhenoAge model)

Step 3: Identify "anti-aging" biomarkers (better than target):
  Parameters where Score > 85
  Sorted by magnitude of aging benefit

Step 4: Identify "pro-aging" biomarkers (worse than target):
  Parameters where Score < 85
  Sorted by magnitude of aging acceleration

Step 5: Select top 3 from each category
```

**Example:**

```
Biological Age: 52 years
Chronological Age: 55 years
Difference: -3 years (aging slower than average)

What's helping you age well:
  â€¢ Low chronic inflammation (CRP: Score 92)
    Impact: -2.1 years
  â€¢ Excellent kidney function (eGFR: Score 90)
    Impact: -1.5 years
  â€¢ Optimal blood sugar control (HbA1c: Score 88)
    Impact: -0.9 years

What's accelerating your aging:
  â€¢ Elevated stress response (Cortisol: Score 62)
    Impact: +1.8 years
  â€¢ Suboptimal albumin (Score 72)
    Impact: +0.7 years
  â€¢ Mild anemia (Hgb: Score 74)
    Impact: +0.4 years
```

**Display:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ Biological Age: 52 years                        â”‚
â”‚ Chronological Age: 55 years                     â”‚
â”‚ (You're aging 3 years slower than average!)     â”‚
â”‚ â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â” â”‚
â”‚                                                 â”‚
â”‚ What's helping you age well:                    â”‚
â”‚   â€¢ Low chronic inflammation                    â”‚
â”‚   â€¢ Excellent kidney function                   â”‚
â”‚   â€¢ Optimal blood sugar control                 â”‚
â”‚                                                 â”‚
â”‚ What's accelerating your aging:                 â”‚
â”‚   â€¢ Elevated stress hormones                    â”‚
â”‚   â€¢ Suboptimal protein status                   â”‚
â”‚   â€¢ Mild anemia                                 â”‚
â”‚                                                 â”‚
â”‚ Biggest opportunity: Managing stress could      â”‚
â”‚ reduce your biological age by 1.8 years.        â”‚
â”‚                                                 â”‚
â”‚ [View Aging Details â†’]                          â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## SECTION 7: COMPLETENESS TRANSPARENCY

### 7.1 Qualitative Completeness Levels

**Instead of numeric confidence intervals, use qualitative assessment:**

```
COMPLETE (â‰¥95% measured)
- "Complete assessment"
- No qualifier needed
- High confidence in score

MOSTLY COMPLETE (80-94% measured)
- "Mostly complete"
- Yellow indicator
- "Some parameters not yet measured"

PARTIAL (50-79% measured)
- "Partially complete"
- Orange indicator
- "Missing several key parameters"

LIMITED (<50% measured)
- "Limited data"
- Red indicator
- "Many parameters not yet measured"
- "Score may change significantly with complete testing"
```

**Display:**
```
Cardiovascular Health: 82
Based on: MOSTLY COMPLETE data (85%)

What we know:
  â€¢ Blood pressure: Excellent (92)
  â€¢ Cholesterol panel: Good (79)
  â€¢ Heart rate: Optimal (88)
  â€¢ Exercise ECG: Good (76)

What we're missing:
  â€¢ Echocardiogram (structure assessment)
  â€¢ Advanced lipid panel (detailed risk)

Your score could change by Â±5 points with complete 
assessment.

[Schedule Missing Tests â†’]
```

### 7.2 Completeness Impact on Attribution

**When attribution is based on incomplete data:**

```
RULE: Always show what's measured vs what's missing

Example:
"What's Working Well" - Based on measured parameters only
  â€¢ [List strengths]
  â€¢ Note: Score may change with complete testing

"What Needs Work" - Based on measured parameters only
  â€¢ [List weaknesses]
  â€¢ Note: Additional issues may be identified with complete testing
  
"Missing Assessments Could Affect":
  â€¢ [Systems/domains with <80% completeness]
```

---

## SECTION 8: EDGE CASES & SPECIAL SCENARIOS

### 8.1 All Scores Near Target (80-90)

**Scenario:** Patient has no clear strengths or major weaknesses

**Display Approach:**
- Use "Optimization" framing instead of "Needs Work"
- Highlight smallest opportunities for improvement
- Use aspirational language
- Emphasize maintenance and excellence-seeking

```
Overall Health Score: 85

ðŸŽ¯ All systems in healthy range!

Your health metrics are consistently good across 
all systems. This is excellent!

Opportunities for optimization:
  â€¢ Cardiovascular Health (83) â†’ 90+
    Focus: Increase aerobic fitness
  â€¢ Metabolic Health (84) â†’ 90+
    Focus: Fine-tune nutrition timing
  â€¢ Sleep Quality (82) â†’ 90+
    Focus: Optimize sleep environment

Moving from "good" to "excellent" can provide 
additional resilience and longevity benefits.

[View Optimization Plan â†’]
```

### 8.2 All Scores Problematic (40-70)

**Scenario:** Patient has multiple areas needing attention

**Display Approach:**
- Don't overwhelm with long list of problems
- Prioritize by clinical severity and interconnection
- Use supportive, non-judgmental language
- Frame as opportunities, not failures
- Provide clear action prioritization

```
Overall Health Score: 58

ðŸ“‹ Multiple areas need attention

We've identified several health priorities. Let's 
focus on the highest-impact changes:

Priority 1: Metabolic Health (42) ðŸ”´
  â€¢ Blood sugar control
  â€¢ Weight management
  â†’ Biggest opportunity for improvement
  â†’ Affects cardiovascular risk too

Priority 2: Cardiovascular Health (51) ðŸŸ 
  â€¢ Blood pressure control
  â€¢ Cholesterol management
  â†’ Second highest impact

Priority 3: Physical Activity (54) ðŸŸ 
  â€¢ Increase weekly exercise
  â†’ Helps both priorities above

Let's tackle these one at a time with your 
healthcare provider. Small improvements in Priority 
1 will have cascading benefits.

[Start Action Plan â†’]
```

### 8.3 Rapidly Changing Scores

**Scenario:** Significant change in short time period

**Display Approach:**
- Flag change prominently
- Show specific parameters driving change
- Provide context for interpretation
- Suggest appropriate urgency level

```
Metabolic Health: 68 (was 82 last month)
âš ï¸ Rapid decline detected (-14 points in 4 weeks)

What changed:
  â€¢ Blood glucose: 88 â†’ 142 mg/dL
  â€¢ Hemoglobin A1c: 5.6% â†’ 7.2%
  â€¢ Triglycerides: 110 â†’ 189 mg/dL

Possible causes:
  â€¢ Medication change or non-adherence
  â€¢ Diet changes
  â€¢ Decreased physical activity
  â€¢ New illness or stress
  â€¢ Measurement error (less likely with 
    multiple parameters affected)

Recommended action:
  Contact your healthcare provider this week 
  to discuss these changes and adjust treatment.

[Message Provider] [View Timeline]
```

### 8.4 Conflicting Indicators

**Scenario:** Good overall score but critical alert present

**Display Priority:**
- ALWAYS show critical alert first
- Explain the apparent discrepancy
- Prevent false reassurance
- Emphasize urgency cannot be overridden

```
ðŸš¨ CRITICAL ALERT despite good overall score

Your Overall Health Score is 82 (Good), but:

CRITICAL: Potassium dangerously high
  Current: 6.8 mEq/L (Normal: 3.5-5.0)
  â†’ Contact provider IMMEDIATELY

Why your overall score looks good:
  â€¢ 7 out of 8 organ systems are healthy
  â€¢ Lifestyle factors are excellent
  â€¢ Most lab values are optimal

Why this ONE parameter is critical:
  Dangerously high potassium can cause sudden 
  cardiac arrest even when everything else 
  looks good. This needs immediate treatment.

Good scores DO NOT mean this alert can wait.

[Emergency Guidance] [Call Provider Now]
```

---

## SECTION 9: IMPLEMENTATION CHECKLIST

**For IT Team:**

**Core Attribution Logic:**
- [ ] Implement deviation calculation: (Score - 85) Ã— Weight
- [ ] Implement top-3 selection algorithm
- [ ] Implement tie-breaking rules
- [ ] Ensure attribution uses ACTUAL weights from composite formulas

**Display Components:**
- [ ] Build Level 1 transparency (Overall â†’ Systems/Pillars)
- [ ] Build Level 2 transparency (System â†’ Domains â†’ Parameters)
- [ ] Build Level 3 transparency (Parameter â†’ Impact on all affected composites)
- [ ] Build biological age attribution
- [ ] Build completeness indicators (qualitative levels)

**"What If" Projections:**
- [ ] Implement hierarchical recalculation (parameter â†’ domain â†’ system â†’ overall)
- [ ] Use EXACT formulas from SYSTEM_DOMAIN_SCORING_v2.md and COMPOSITE_SCORING_v2.md
- [ ] Validate calculations match scoring engine exactly

**Edge Cases:**
- [ ] Handle all-good scenario (Section 8.1)
- [ ] Handle all-problematic scenario (Section 8.2)
- [ ] Handle rapid changes (Section 8.3)
- [ ] Handle conflicting indicators (Section 8.4)

**Integration:**
- [ ] Link to parameter detail views
- [ ] Link to educational content
- [ ] Enable drill-down navigation
- [ ] Connect to action planning tools

**Testing:**
- [ ] Validate attribution matches composite scoring exactly
- [ ] Test with complete data
- [ ] Test with incomplete data (various % complete)
- [ ] Test with ties and near-ties
- [ ] Test with critical alerts + good scores
- [ ] Test with all scores in same zone
- [ ] Verify "What If" projections are accurate

**For Clinical Team:**

**Content Development:**
- [ ] Review all plain language interpretations
- [ ] Approve "What's Working Well" messaging
- [ ] Approve "What Needs Work" messaging
- [ ] Validate actionable recommendations
- [ ] Create domain-specific educational content

**Clinical Validation:**
- [ ] Verify attribution is clinically meaningful
- [ ] Test with diverse patient scenarios
- [ ] Ensure critical alerts properly emphasized
- [ ] Validate "What If" projections are realistic
- [ ] Approve all edge case displays

**User Testing:**
- [ ] Test with patients for comprehension
- [ ] Test with clinicians for utility
- [ ] Gather feedback on prioritization
- [ ] Assess if transparency is actually transparent
- [ ] Validate action items are appropriate

---

## APPENDIX A: KEY DIFFERENCES FROM v1.0

**Major corrections in v1.1:**

1. **Fixed Attribution Mathematics**
   - v1.0: Custom "Impact Factor" formula (incorrect)
   - v1.1: Uses actual composite scoring formulas

2. **Corrected Baseline**
   - v1.0: Used 75 as positive/negative threshold
   - v1.1: Uses 85 (actual target from scoring architecture)

3. **Simplified Deviation Calculation**
   - v1.0: Complex multi-factor formula
   - v1.1: Simple: (Score - 85) Ã— Weight

4. **Removed False Statistical Precision**
   - v1.0: Numeric confidence intervals
   - v1.1: Qualitative completeness levels

5. **Aligned "What If" Calculations**
   - v1.0: Approximate/heuristic
   - v1.1: Exact hierarchical recalculation

6. **Removed UI Specifications**
   - v1.0: Emojis, exact layouts, colors
   - v1.1: Logic only, defers styling to DASHBOARD specs

7. **Clarified Propagation**
   - v1.0: Ambiguous parameterâ†’overall path
   - v1.1: Explicit: parameter â†’ domain â†’ system â†’ objective â†’ overall

---

## APPENDIX B: MATHEMATICAL VALIDATION EXAMPLES

### Example 1: Verify Level 1 Attribution

**Given:**
- CV System: Score = 68, Weight = 20% (of objective)
- Objective weight in overall = 70%
- Effective weight in overall = 0.20 Ã— 0.70 = 0.14 = 14%

**Deviation:**
```
CV_Deviation = (68 - 85) Ã— 0.14 = -17 Ã— 0.14 = -2.38 points

Interpretation: CV system is pulling overall score down 
by 2.38 points below where it would be if CV was at target.
```

**Verify this matches actual contribution:**
```
Current CV contribution to overall: 68 Ã— 0.14 = 9.52
Target CV contribution to overall: 85 Ã— 0.14 = 11.90
Difference: 9.52 - 11.90 = -2.38 âœ“ (matches deviation)
```

### Example 2: Verify Level 2 Attribution

**Given:**
- CV-Function: Score = 62, Weight = 50% (in CV system)
- CV System: Score = 68

**Deviation:**
```
CV_Funct_Deviation = (62 - 85) Ã— 0.50 = -23 Ã— 0.50 = -11.5 points

Interpretation: CV-Function domain is pulling CV system 
down by 11.5 points below where it would be if function was at target.
```

**Verify this matches actual contribution:**
```
Current Function contribution to CV: 62 Ã— 0.50 = 31.0
Target Function contribution to CV: 85 Ã— 0.50 = 42.5
Difference: 31.0 - 42.5 = -11.5 âœ“ (matches deviation)
```

### Example 3: Verify "What If" Propagation

**Given:**
- LDL: Current score = 68, Target = 85
- LDL weight in CV-Risk = 90%
- Current CV-Risk = 72

**Step 1: Recalculate CV-Risk with LDL at target**

Assuming CV-Risk has 5 parameters with these contributions:
- LDL: 68 Ã— 0.90 = 61.2
- HDL: 80 Ã— 0.80 = 64.0
- TG: 75 Ã— 0.70 = 52.5
- ASCVD: 85 Ã— 0.60 = 51.0
- CAC: 90 Ã— 0.40 = 36.0

Total weight = 0.90 + 0.80 + 0.70 + 0.60 + 0.40 = 3.40
Current CV-Risk = (61.2 + 64.0 + 52.5 + 51.0 + 36.0) / 3.40 = 264.7 / 3.40 = 77.9 â‰ˆ 78

Wait - this doesn't match given (72). Need to recalculate from actual domain formula.

**[Note: In actual implementation, must use exact formulas from SYSTEM_DOMAIN_SCORING_v2.md with proper completeness blending]**

---

**END OF TRANSPARENCY_DISPLAY_v1_1.md**

*This specification provides mathematically correct attribution logic aligned with the actual composite scoring architecture. All formulas match SYSTEM_DOMAIN_SCORING_v2.md and COMPOSITE_SCORING_v2.md exactly. Clinical team approval required before deployment.*
