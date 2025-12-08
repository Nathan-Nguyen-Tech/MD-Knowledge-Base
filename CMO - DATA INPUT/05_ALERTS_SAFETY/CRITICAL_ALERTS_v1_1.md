# CRITICAL ALERTS SPECIFICATION
## Patient Health Dashboard - Safety Alert System

**Document Type:** Core Clinical Logic - Safety Critical  
**Version:** 1.1.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - CORRECTED  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture, safety-first principles
- `PARAMETER_NORMALIZATION_v2.md` - How individual parameters are scored
- `CONTEXT_RULES.md` - Patient-specific adjustments to thresholds
- `TEMPORAL_SCORING.md` - Trend detection and velocity scoring

**This document connects to:**
- `CLINICAL_DECISION_RULES.md` - Multi-parameter alert patterns (sepsis, DKA, etc.)
- `ALERT_MESSAGES.md` - Patient and clinician alert text
- `DASHBOARD_LEVEL1_SPEC.md` - How alerts display on hero view
- All `PARAMETERS_*.md` files - Parameter-specific alert thresholds (SOURCE OF TRUTH)

---

## DOCUMENT PURPOSE

This specification defines **alert system logic, prioritization, and workflows** that ensure critical findings are never masked by good composite scores.

**Critical Safety Principle:**
> A patient with an excellent Overall Health Score (95/100) but a life-threatening potassium level (7.5 mEq/L) MUST see a CRITICAL ALERT prominently displayed, regardless of all other scores.

**What This Document Provides:**
1. Four-tier alert hierarchy (Critical â†’ Urgent â†’ Warning â†’ Monitor)
2. Alert prioritization and display logic (NOT thresholds - those live in parameter files)
3. Alert escalation rules (temporal trends, multi-parameter patterns)
4. Time-to-action guidance for each alert level
5. Override rules and suppression logic
6. Workflow specifications for clinicians and patients

**What This Document Does NOT Provide:**
- âŒ Specific threshold values (those are in PARAMETERS_*.md files)
- âŒ Parameter-specific context rules (those are in CONTEXT_RULES.md)
- âŒ Complex multi-parameter patterns (those are in CLINICAL_DECISION_RULES.md)

---

## SECTION 1: ALERT HIERARCHY

### 1.1 Four Alert Tiers

| Tier | Name | Urgency | Time to Action | Color | Icon |
|------|------|---------|----------------|-------|------|
| 1 | **CRITICAL** | Life-threatening | Immediate (minutes to hours) | Red | ðŸš¨ |
| 2 | **URGENT** | Serious, rapid intervention needed | Same day | Orange | âš ï¸ |
| 3 | **WARNING** | Attention needed soon | Within days to 1 week | Yellow | âš¡ |
| 4 | **MONITOR** | Watch closely, recheck | Within 1-4 weeks | Blue | ðŸ‘ï¸ |

### 1.2 Tier Definitions

#### TIER 1: CRITICAL

**Definition:** Imminent threat to life or organ function requiring immediate medical attention.

**Action Required:**
- **Patient:** Call 911 or go to emergency department immediately
- **Clinician:** Contact patient immediately, may need emergency department referral
- **Display:** Prominent, cannot be dismissed without acknowledgment

**Examples:**
- Severe electrolyte disturbances (per PARAMETERS_ELECTROLYTES.md)
- Profound hypoglycemia (per PARAMETERS_GLUCOSE.md)
- Severe hypoxemia (per PARAMETERS_VITAL_SIGNS.md)
- Multi-parameter critical patterns (sepsis, DKA - see CLINICAL_DECISION_RULES.md)

#### TIER 2: URGENT

**Definition:** Significant abnormality requiring same-day medical evaluation or intervention.

**Action Required:**
- **Patient:** Contact clinician same day
- **Clinician:** See patient same day or provide urgent guidance
- **Display:** Prominent, but less alarming than critical

#### TIER 3: WARNING

**Definition:** Abnormality that needs attention within days, before it worsens.

**Action Required:**
- **Patient:** Schedule appointment within 1 week
- **Clinician:** Address within 1 week, adjust treatment
- **Display:** Visible but not alarming, can review systematically

#### TIER 4: MONITOR

**Definition:** Trending toward abnormal; recheck and monitor closely.

**Action Required:**
- **Patient:** Recheck in 1-4 weeks, lifestyle modifications
- **Clinician:** Monitor trend, consider intervention if worsening
- **Display:** Subtle, informational, not alarming

---

## SECTION 2: ALERT THRESHOLD ARCHITECTURE

### 2.1 Threshold Source of Truth

**All parameter-specific thresholds are defined in their respective parameter files:**

```
PARAMETERS_VITAL_SIGNS.md
  â”œâ”€ Blood Pressure thresholds (clinic vs home)
  â”œâ”€ Heart Rate thresholds (by age, athletic status)
  â”œâ”€ Temperature thresholds (by age)
  â””â”€ Oxygen Saturation thresholds (by baseline condition)

PARAMETERS_ELECTROLYTES.md
  â”œâ”€ Potassium thresholds (by CKD stage, medications)
  â”œâ”€ Sodium thresholds (by chronicity, symptoms)
  â””â”€ Calcium thresholds (corrected vs ionized)

PARAMETERS_GLUCOSE.md
  â”œâ”€ Hypoglycemia thresholds (by diabetes status, treatment)
  â””â”€ Hyperglycemia thresholds (by DKA risk)

[etc. for all parameters]
```

### 2.2 This Document's Role

**This specification defines:**
1. **How to use** thresholds from parameter files
2. **When to escalate** alert tier based on temporal trends
3. **How to combine** multiple parameters into critical patterns
4. **How to prioritize** when multiple alerts exist
5. **How to display** and **workflow** alerts

**This specification does NOT:**
- Define specific threshold values (parameter files own this)
- Duplicate context rules (CONTEXT_RULES.md owns this)
- Define multi-parameter algorithms (CLINICAL_DECISION_RULES.md owns this)

### 2.3 Reference Pattern

When this document refers to thresholds, it uses this format:

> "If potassium exceeds CRITICAL threshold (as defined in PARAMETERS_ELECTROLYTES.md, adjusted by CONTEXT_RULES.md for CKD, ACE-I use, etc.)..."

NOT:

> ~~"If potassium >6.5 mEq/L..."~~ (threshold lives elsewhere)

---

## SECTION 3: ALERT TRIGGERING LOGIC

### 3.1 Single-Parameter Alerts

**Basic trigger:**
```
IF parameter value crosses threshold (from PARAMETERS_*.md)
AND context rules allow alert (from CONTEXT_RULES.md)
THEN trigger alert at specified tier
```

**Example:**
```
Patient: 65-year-old with CKD Stage 3
Parameter: Potassium = 5.8 mEq/L
Baseline: 4.8 mEq/L (stable for 6 months)

Step 1: Check PARAMETERS_ELECTROLYTES.md
  â†’ K+ 5.8 in general population = WARNING tier
  
Step 2: Check CONTEXT_RULES.md
  â†’ Patient has CKD Stage 3 â†’ lower threshold for concern
  â†’ 5.8 in CKD Stage 3 = URGENT tier (escalated)
  
Step 3: Check TEMPORAL_SCORING.md
  â†’ Rising from 4.8 to 5.8 in 1 week = rapid change
  â†’ Escalate 1 tier: URGENT â†’ CRITICAL
  
Result: Trigger CRITICAL alert
```

### 3.2 Temporal Escalation Rules

**From TEMPORAL_SCORING.md, apply these escalation rules:**

| Change Pattern | Escalation Action |
|----------------|-------------------|
| **Rapid worsening** (>20% change in <1 week) | Escalate 1 tier |
| **Steady worsening** (trending worse over 3+ readings) | Escalate 1 tier |
| **First-time critical** (no history of this abnormality) | No change (already critical) |
| **Improving after treatment** | Consider suppression (see Section 4) |
| **Stable chronic abnormality** | De-escalate 1 tier or suppress |

**Example escalations:**
- BP 155/95 stable for 6 months â†’ WARNING
- BP 155/95 jumped from 130/80 last week â†’ URGENT
- Creatinine 1.5 stable for 2 years (CKD) â†’ MONITOR
- Creatinine 1.5 rose from 0.9 this week (AKI) â†’ CRITICAL

### 3.3 Multi-Parameter Critical Patterns

**Some emergencies require MULTIPLE abnormal parameters.**

These patterns are fully defined in **CLINICAL_DECISION_RULES.md** and referenced here:

#### Pattern 1: Sepsis Risk

```
IF (Temperature >101Â°F OR <96Â°F)
AND (Heart Rate >100 bpm)
AND (WBC >12k OR <4k OR >10% bands)
AND (Systolic BP <100 mmHg OR down >40 mmHg from baseline)
THEN trigger CRITICAL alert: "Possible Sepsis - Emergency Evaluation Needed"
```

#### Pattern 2: Diabetic Ketoacidosis (DKA)

```
IF (Glucose >250 mg/dL)
AND (Ketones >15 mg/dL OR moderate-large on urine dipstick)
AND (Anion gap >12 OR bicarb <18)
THEN trigger CRITICAL alert: "Possible DKA - Emergency Evaluation Needed"
```

#### Pattern 3: Acute Stroke Risk

```
IF (Systolic BP >200 mmHg OR >180 with symptoms)
AND (New neurological symptom flagged in assessment)
AND (No recent stroke history OR symptoms <48 hours)
THEN trigger CRITICAL alert: "Possible Stroke - Call 911 Immediately"
```

#### Pattern 4: Cardiogenic Shock

```
IF (Systolic BP <90 mmHg OR down >40 from baseline)
AND (Heart Rate >100 bpm)
AND (SpOâ‚‚ <92% OR dropping)
THEN trigger CRITICAL alert: "Possible Shock - Emergency Evaluation Needed"
```

#### Pattern 5: CHF Exacerbation

```
IF (BNP >5000 pg/mL OR NT-proBNP >10000 pg/mL)
AND (Weight gain >5 lbs in 1 week)
AND (SpOâ‚‚ <92% OR new dyspnea)
THEN trigger URGENT alert: "Possible Heart Failure Worsening - Contact Doctor Today"
```

**Note:** Full algorithmic details, sensitivity/specificity tuning, and validation in CLINICAL_DECISION_RULES.md.

### 3.4 Measurement Source Adjustments

**Home monitoring vs clinic measurements require different handling:**

#### Home Blood Pressure

**Rules from PARAMETERS_VITAL_SIGNS.md:**
- First elevated home reading â†’ Generate informational note
- Second consecutive elevated reading (same session) â†’ WARNING
- Third consecutive elevated reading (next day) â†’ URGENT
- Extremely high reading (>200/>120) with symptoms â†’ CRITICAL (override repeat rule)

**Never trigger CRITICAL on single home BP without symptoms.**

#### Home Glucose

**Rules from PARAMETERS_GLUCOSE.md:**
- Hypoglycemia <54 mg/dL â†’ URGENT (even on first reading)
- Hypoglycemia <40 mg/dL â†’ CRITICAL (immediate)
- Hyperglycemia >300 mg/dL â†’ WARNING (if isolated)
- Hyperglycemia >400 mg/dL â†’ URGENT
- Hyperglycemia >500 mg/dL â†’ CRITICAL

#### Home Pulse Oximetry

**Rules from PARAMETERS_VITAL_SIGNS.md:**
- <92% on first reading â†’ Prompt to repeat
- <92% on two consecutive readings â†’ WARNING
- <88% on any reading â†’ URGENT
- <85% on any reading â†’ CRITICAL (override repeat rule)

**Always consider baseline in COPD/pulmonary disease (from CONTEXT_RULES.md).**

---

## SECTION 4: ALERT SUPPRESSION & OVERRIDE LOGIC

### 4.1 Automatic Suppression (System-Driven)

**Scenario 1: Recent Treatment with Improving Trend**
```
IF parameter triggered alert
AND patient received appropriate treatment (documented)
AND parameter is improving (trending toward normal)
AND last measurement within 24 hours
THEN suppress duplicate alert, show "Improving: [old value] â†’ [new value]"
```

**Example:**
- K+ 7.2 mEq/L â†’ CRITICAL alert, patient treated in ED
- K+ rechecked 4 hours later: 6.5 mEq/L
- Do NOT re-trigger CRITICAL (already aware, trending better)
- Display: "Improving: K+ 7.2 â†’ 6.5 mEq/L after treatment"

**Scenario 2: Known Chronic Stable Abnormality**
```
IF parameter abnormal
AND baseline established (3+ measurements over 3+ months)
AND current value within 10% of baseline
AND no rapid change (per TEMPORAL_SCORING.md)
THEN suppress alert OR downgrade 1 tier
```

**Example:**
- CKD Stage 4 patient with stable Cr 3.0 mg/dL for 2 years
- New measurement: Cr 3.1 mg/dL
- Do NOT alert on absolute value (expected)
- Alert only if: Cr jumps to 4.0+ (significant worsening)

**Scenario 3: Acute Illness Flag Active**
```
IF patient has acute illness flag (from CONTEXT_RULES.md)
AND parameter abnormality is expected (e.g., elevated WBC, CRP)
THEN suppress low-priority alerts (WARNING/MONITOR)
BUT maintain CRITICAL alerts (life-threatening always alert)
```

**Scenario 4: Medication-Expected Abnormality**
```
IF patient on medication (e.g., warfarin, ACE-I)
AND abnormality is expected therapeutic effect (e.g., INR 2.5, K+ 5.2)
AND value within therapeutic/expected range
THEN suppress alert
```

**From CONTEXT_RULES.md:**
- Warfarin patient: INR 2.0-3.5 expected (no alert)
- ACE-I patient: K+ 5.0-5.5 expected (lower alert threshold)
- Diuretic patient: K+ 3.3-3.8 acceptable (monitor only)

### 4.2 Clinician Override (Human-Driven)

**When clinicians can override alerts:**

1. **Known chronic condition with documented plan**
   - Example: CKD patient with stable Cr 3.0 mg/dL
   - Requires: Documented chronic condition + management plan

2. **Expected post-procedure finding**
   - Example: Troponin elevation after cardiac catheterization
   - Requires: Procedure documented + expected timeline

3. **Laboratory artifact/error**
   - Example: Hemolyzed sample causing false hyperkalemia
   - Requires: Repeat measurement ordered + rationale documented

4. **Patient refuses intervention (documented choice)**
   - Example: Patient declines ED visit despite critical finding
   - Requires: Informed refusal documented + follow-up plan

**Override Requirements:**
- âœ… Clinician authentication
- âœ… Documented rationale (dropdown + free text)
- âœ… Acknowledgment of risk
- âœ… Follow-up plan specified
- âœ… Re-alert if value worsens beyond threshold

**Override does NOT:**
- Delete alert from record (audit trail preserved)
- Prevent re-triggering if value deteriorates
- Remove from alert log or metrics

**Override Template:**
```
Alert: Potassium 7.2 mEq/L (CRITICAL)
Clinician: Dr. Smith
Override Reason: [Dropdown: Chronic stable condition]
Details: Patient has ESRD on HD, post-dialysis K+ typically 6.5-7.0. 
         Patient asymptomatic, EKG shows no changes from baseline.
         Scheduled for dialysis tomorrow AM.
Action Plan: Recheck K+ post-dialysis. Alert if >7.5 or symptoms develop.
Override Approved: [Timestamp]
```

### 4.3 Suppression vs Override Decision Tree

```
Alert triggered
    â”‚
    â”œâ”€ Is this a known chronic stable condition?
    â”‚   â””â”€ YES â†’ Auto-suppress OR clinician override
    â”‚   â””â”€ NO â†’ Continue
    â”‚
    â”œâ”€ Is this expected from recent treatment?
    â”‚   â””â”€ YES â†’ Auto-suppress "improving" message
    â”‚   â””â”€ NO â†’ Continue
    â”‚
    â”œâ”€ Is this medication-expected?
    â”‚   â””â”€ YES â†’ Check CONTEXT_RULES.md for suppression
    â”‚   â””â”€ NO â†’ Continue
    â”‚
    â”œâ”€ Is patient in acute illness window?
    â”‚   â””â”€ YES â†’ Suppress WARNING/MONITOR, keep CRITICAL/URGENT
    â”‚   â””â”€ NO â†’ Continue
    â”‚
    â””â”€ No suppression criteria met
        â””â”€ Display alert (no suppression)
```

---

## SECTION 5: ALERT PRIORITIZATION & DISPLAY

### 5.1 Priority Ranking (When Multiple Alerts)

**Display order:**
1. **Multi-parameter critical patterns** (sepsis, DKA, shock) - HIGHEST
2. **Single-parameter CRITICAL alerts** - by severity hierarchy:
   a. Electrolytes (K+, Na+, CaÂ²+)
   b. Glucose (hypoglycemia > hyperglycemia)
   c. Cardiac (troponin, arrhythmia)
   d. Respiratory (SpOâ‚‚)
   e. Other CRITICAL
3. **URGENT alerts** (top 3 only, rest in "See All")
4. **WARNING alerts** (top 3 only, rest in "See All")
5. **MONITOR alerts** (grouped, collapsed by default)

**Severity hierarchy within same tier:**
```
Potassium > Sodium > Glucose (hypo) > SpOâ‚‚ > Calcium > Others
```

### 5.2 Hero View Display

**Location:** Prominent alert banner at TOP of dashboard, ABOVE overall health score

**Single CRITICAL Alert:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ CRITICAL ALERT                                       â”‚
â”‚ Potassium: 7.2 mEq/L (Dangerously High)               â”‚
â”‚ [Emergency Guidance] [View Details]                    â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Multiple CRITICAL Alerts:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ MULTIPLE CRITICAL ALERTS (3)                        â”‚
â”‚ 1. Sepsis Risk Pattern - CALL 911 NOW                 â”‚
â”‚ 2. Potassium: 7.2 mEq/L (Dangerously High)            â”‚
â”‚ 3. Glucose: 38 mg/dL (Dangerously Low)                â”‚
â”‚ [Emergency Action Plan]                                â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Multi-Parameter Pattern Alert (Highest Priority):**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ðŸš¨ POSSIBLE MEDICAL EMERGENCY                         â”‚
â”‚                                                         â”‚
â”‚ SEPSIS RISK DETECTED                                    â”‚
â”‚ â€¢ Fever: 102.5Â°F                                       â”‚
â”‚ â€¢ Fast heart rate: 118 bpm                             â”‚
â”‚ â€¢ Low blood pressure: 88/52                            â”‚
â”‚ â€¢ Elevated WBC: 16,000                                 â”‚
â”‚                                                         â”‚
â”‚ âš ï¸ CALL 911 IMMEDIATELY                                â”‚
â”‚ Do not drive yourself                                  â”‚
â”‚                                                         â”‚
â”‚ [What to Tell 911] [I've Called 911]                   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 5.3 Alert Acknowledgment Requirements

**CRITICAL alerts cannot be dismissed until:**
1. âœ… Patient reads full emergency guidance
2. âœ… Patient checks box: "I understand this is a medical emergency"
3. âœ… Patient selects action:
   - "I am calling 911 now"
   - "I am going to the ER now"
   - "I am calling my doctor now"
   - "I choose not to seek care (requires additional confirmation)"

**If patient selects "I choose not to seek care":**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ âš ï¸ CRITICAL ALERT REFUSAL WARNING                      â”‚
â”‚                                                         â”‚
â”‚ This condition can be life-threatening. By choosing    â”‚
â”‚ not to seek emergency care, you accept the risk of:    â”‚
â”‚                                                         â”‚
â”‚ â€¢ Cardiac arrest (heart stopping)                      â”‚
â”‚ â€¢ Coma                                                  â”‚
â”‚ â€¢ Permanent organ damage                               â”‚
â”‚ â€¢ Death                                                 â”‚
â”‚                                                         â”‚
â”‚ Your doctor will be notified immediately.              â”‚
â”‚                                                         â”‚
â”‚ [I Still Refuse Care] [Change Mind - Get Help]         â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Refusal triggers:**
- Immediate clinician notification (escalated priority)
- Documented in medical record
- Follow-up workflow initiated
- Depending on severity and liability policies: wellness check consideration

### 5.4 Override Logic (Alerts Trump Composite Scores)

**Fundamental principle:**

**CRITICAL alerts override ALL scoring displays.**

**Example scenario:**
- Overall Health Score: 95/100 (Excellent) âœ¨
- Cardiovascular Score: 92/100 (Excellent) âœ¨
- **BUT:** Potassium 7.2 mEq/L ðŸš¨

**Display hierarchy:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ CRITICAL ALERT OVERRIDES SCORES       â”‚
â”‚                                          â”‚
â”‚ Your overall health scores look good,   â”‚
â”‚ BUT you have a life-threatening         â”‚
â”‚ electrolyte imbalance that requires     â”‚
â”‚ IMMEDIATE medical attention.            â”‚
â”‚                                          â”‚
â”‚ Your good scores cannot protect you     â”‚
â”‚ from this emergency.                    â”‚
â”‚                                          â”‚
â”‚ [Emergency Guidance]                     â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Never allow:**
- Good scores to minimize critical alerts
- Patients to bypass critical alerts to view scores
- Critical alerts hidden in detail views only

---

## SECTION 6: TIME-TO-ACTION & WORKFLOWS

### 6.1 CRITICAL Alert Workflow

**Patient Actions:**
1. **0-5 minutes:** Read alert, understand severity
2. **5-15 minutes:** Call 911 or leave for ED
3. **Do NOT wait** for clinician callback
4. **Do NOT drive yourself** if symptomatic

**Clinician Actions:**
1. **0-15 minutes:** Automated notification sent (SMS, app push, page)
2. **15-30 minutes:** Clinician calls patient to verify action taken
3. **30 minutes+:** If no patient contact, escalate to wellness check protocol
4. **Documentation:** All actions timestamped in medical record

**System Actions:**
1. **Immediate:** Display CRITICAL banner (cannot dismiss)
2. **0-5 minutes:** Send clinician notification (all channels)
3. **15 minutes:** If patient hasn't acknowledged, send reminder notification
4. **30 minutes:** If patient hasn't acknowledged, escalate clinician alert
5. **Alert persistence:** Remains until patient confirms action OR clinician overrides

### 6.2 URGENT Alert Workflow

**Patient Actions:**
1. **0-2 hours:** Call clinician's office
2. **If after hours:** Call on-call service
3. **Same day:** Speak with clinician or get appointment

**Clinician Actions:**
1. **2-4 hours:** Review alert, contact patient
2. **Same day:** See patient OR provide urgent telemedicine guidance
3. **Document:** Plan in medical record

**System Actions:**
1. **Immediate:** Display URGENT alert (prominent)
2. **0-1 hour:** Add to clinician alert queue
3. **4 hours:** If unaddressed, send reminder to clinician
4. **8 hours:** Escalate to supervising clinician

### 6.3 WARNING Alert Workflow

**Patient Actions:**
1. **Within 1 week:** Schedule appointment
2. **Call office** during business hours
3. **Implement recommended actions** (e.g., BP monitoring)

**Clinician Actions:**
1. **24-48 hours:** Review alert
2. **Within 1 week:** See patient OR adjust treatment remotely
3. **Document:** Plan in medical record

**System Actions:**
1. **Immediate:** Display WARNING indicator
2. **24 hours:** Add to clinician review queue
3. **3 days:** If unaddressed, reminder to clinician
4. **7 days:** If still unaddressed, escalate

### 6.4 MONITOR Alert Workflow

**Patient Actions:**
1. **1-4 weeks:** Recheck parameter
2. **Lifestyle modifications** as recommended
3. **Watch for symptoms**

**Clinician Actions:**
1. **Next visit:** Review trend
2. **Monitor:** No urgent action needed
3. **Consider intervention** if worsening

**System Actions:**
1. **Immediate:** Add to "Items to Monitor" list (collapsed)
2. **No urgent notifications**
3. **Trend tracking:** Flag if upgrades to WARNING

---

## SECTION 7: CLINICIAN ALERT MANAGEMENT

### 7.1 Clinician Alert Queue

**Dashboard view shows:**

**Active CRITICAL Alerts:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸš¨ CRITICAL - IMMEDIATE ACTION REQUIRED (2)          â”‚
â”‚                                                       â”‚
â”‚ 1. Smith, John (DOB 3/15/1965)                      â”‚
â”‚    Sepsis Risk Pattern                               â”‚
â”‚    Triggered: 8 min ago                              â”‚
â”‚    Status: Patient not yet contacted                 â”‚
â”‚    [Call Now] [View Chart] [Override]               â”‚
â”‚                                                       â”‚
â”‚ 2. Jones, Mary (DOB 7/22/1958)                      â”‚
â”‚    Potassium: 7.4 mEq/L                             â”‚
â”‚    Triggered: 12 min ago                             â”‚
â”‚    Status: Patient acknowledged - going to ED        â”‚
â”‚    [Call Patient] [View Chart]                       â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Active URGENT Alerts:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ âš ï¸ URGENT - SAME DAY ACTION REQUIRED (5)            â”‚
â”‚                                                       â”‚
â”‚ [Show all 5 alerts]                                  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Active WARNING Alerts:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ âš¡ WARNING - THIS WEEK ACTION (12)                   â”‚
â”‚                                                       â”‚
â”‚ [Show all 12 alerts]                                 â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 7.2 Clinician Notification Delivery

**CRITICAL Alerts:**
- **SMS to on-call clinician** (immediate)
- **App push notification** (immediate)
- **Email** (immediate, backup)
- **Phone call** (if no response in 5 minutes - automated system)

**URGENT Alerts:**
- **App push notification** (immediate)
- **Email** (immediate)
- **SMS** (if no response in 2 hours)

**WARNING Alerts:**
- **In-app queue** (immediate)
- **Daily digest email** (end of day)

**MONITOR Alerts:**
- **In-app queue** only
- **Weekly summary report**

### 7.3 Escalation Protocol

**If CRITICAL alert not addressed:**

```
0 min: Alert triggered â†’ SMS/Push to on-call clinician
15 min: No response â†’ Second SMS/Push
30 min: No response â†’ Automated phone call
45 min: No response â†’ Escalate to supervising physician
60 min: No response â†’ Escalate to medical director
```

**Rationale:** Life-threatening alerts cannot be missed.

---

## SECTION 8: QUALITY ASSURANCE & MONITORING

### 8.1 Alert Metrics Dashboard (Required)

**Track daily/weekly/monthly:**

**Volume Metrics:**
- Total alerts per tier (Critical/Urgent/Warning/Monitor)
- Alert rate per 1000 active patients
- Multi-parameter pattern detections

**Response Metrics:**
- Time to clinician acknowledgment (target: <15 min for CRITICAL)
- Time to patient contact (target: <30 min for CRITICAL)
- Time to resolution (parameter back to normal range)

**Outcome Metrics:**
- % of CRITICAL alerts â†’ ED visit (target: >80%)
- % of URGENT alerts â†’ same-day intervention (target: >90%)
- % of WARNING alerts â†’ scheduled visit (target: >70%)

**Quality Metrics:**
- Override rate (should be <10% of alerts)
- False positive rate (alerts that were artifacts/errors)
- False negative rate (adverse events WITHOUT preceding alert)

**Alarm Fatigue Indicators:**
- Increasing acknowledgment time (suggests fatigue)
- Increasing override rate (suggests poor calibration or fatigue)
- Clinician feedback scores

### 8.2 Alert Calibration Reviews

**Quarterly reviews:**
1. **Are thresholds appropriate?**
   - Review false positive/negative rates
   - Adjust parameter thresholds in PARAMETERS_*.md if needed
   
2. **Are we missing critical events?**
   - Audit all ED visits/hospitalizations
   - Were there preceding abnormal parameters WITHOUT alert?
   - Add missing alert rules

3. **Are we over-alerting?**
   - Review override reasons
   - Identify systematic false positives
   - Refine context rules or thresholds

4. **Are temporal rules working?**
   - Review escalations due to rapid changes
   - Validate sensitivity/specificity

**Clinical committee approval required for any threshold changes.**

### 8.3 Safety Audits

**Monthly:**
- Review all CRITICAL alerts: Appropriate? Outcome?
- Review all adverse events: Was there a preceding alert? If not, why not?
- Review all overrides: Justified? Appropriate follow-up?

**Quarterly:**
- Compare alert outcomes to national benchmarks
- Review multi-parameter pattern detection rates
- Update CLINICAL_DECISION_RULES.md based on new evidence

**Annually:**
- Comprehensive alert system review
- Literature review for new critical patterns
- Validation of all threshold sources against current guidelines

---

## SECTION 9: EDGE CASES

### 9.1 Conflicting Lab Values (Possible Hemolysis)

**Scenario:** K+ 7.5 mEq/L (CRITICAL), repeated 1 hour later: 5.0 mEq/L

**Likely cause:** Hemolyzed sample (false elevation)

**Action:**
```
Display: 
"Potassium Alert - Repeat Measurement Recommended"

Initial: 7.5 mEq/L âš ï¸ (possible lab error)
Repeat: 5.0 mEq/L âœ“ (normal)

The initial measurement may have been affected by sample 
handling. Your repeat measurement is normal. Your clinician 
has been notified and will review.

Status: CRITICAL alert downgraded to RESOLVED
```

**System action:**
- Notify clinician of discrepancy
- Flag potential lab quality issue
- Maintain audit trail

### 9.2 Patient in Transit to ED

**Scenario:** CRITICAL alert triggered, patient already en route to ED

**Action:**
```
Patient status: "I am going to the ER now" âœ“

Next steps:
â€¢ Your clinician has been notified
â€¢ Bring your medication list
â€¢ Tell ER staff about [specific alert]

[What to Tell ER Staff]
```

**System action:**
- Mark alert as "patient action taken"
- Alert remains visible but de-emphasized
- Clinician notified of patient status

### 9.3 Refused Care (Informed Refusal)

**Scenario:** Patient with CRITICAL alert refuses ED visit

**Action:**
```
1. Document refusal (timestamped)
2. Escalate to clinician IMMEDIATELY (highest priority)
3. Clinician attempts phone contact (multiple attempts)
4. If successful contact:
   - Assess decision-making capacity
   - Document conversation
   - Create follow-up plan
5. If unsuccessful contact after 3 attempts:
   - Consider wellness check (case-by-case, liability-dependent)
   - Document all attempts
```

**Medicolegal protection:**
- Clear documentation of informed refusal
- Evidence of escalation attempts
- Follow-up plan (even if refused)

### 9.4 Multiple Critical Alerts (Triage)

**Scenario:** Sepsis pattern + Hyperkalemia + Hypoglycemia simultaneously

**Display Priority:**
1. **Sepsis pattern** (multi-parameter, highest mortality risk)
2. **Hypoglycemia** (immediately reversible, immediate action)
3. **Hyperkalemia** (serious but slower onset)

**Message:**
```
ðŸš¨ðŸš¨ MULTIPLE EMERGENCIES DETECTED

You have THREE critical conditions that need IMMEDIATE 
attention:

1. SEPSIS RISK (most urgent)
   â†’ CALL 911 NOW

2. LOW BLOOD SUGAR (treat first while waiting)
   â†’ Drink juice or eat glucose tablets NOW
   â†’ Recheck in 15 minutes

3. HIGH POTASSIUM
   â†’ Tell ER staff when you arrive

[Call 911 Now] [Emergency Guidance]
```

### 9.5 After-Hours Alert

**Scenario:** CRITICAL alert at 2 AM, clinician not immediately available

**Action:**
```
1. Display alert to patient immediately (no delay)
2. Trigger on-call clinician notification
3. If no clinician response in 15 minutes:
   - Escalate to backup on-call
   - Automated phone call system
4. Patient message emphasizes: "Do not wait for callback - 
   seek emergency care now"
```

---

## SECTION 10: SPECIAL POPULATIONS

### 10.1 Pediatric Patients (Age <18)

**Modifications:**
- Different thresholds (reference PARAMETERS_*.md pediatric sections)
- Age-specific normal ranges (heart rate, respiratory rate, BP)
- Parental notification required (legal guardian)
- Some alerts require lower threshold (dehydration risk in infants)

**Example:**
- Adult: HR >120 = WARNING
- Infant (<1 yr): HR >160 = WARNING (age-appropriate)

### 10.2 Elderly (Age >75)

**Modifications:**
- Some thresholds relaxed (BP, glucose targets less aggressive)
- Falls risk assessment included in alert logic
- Polypharmacy considerations (more drug-drug interactions)
- Cognitive status assessment (can patient respond appropriately?)

**Example:**
- General: BP target <140/90
- Elderly (>75): BP target <150/90 (per guidelines)

### 10.3 Pregnancy

**Modifications:**
- Pregnancy-specific thresholds (from CONTEXT_RULES.md)
- Preeclampsia pattern recognition (BP + proteinuria + symptoms)
- HELLP syndrome detection (BP + platelets + liver enzymes)
- Lower threshold for glucose concerns (gestational diabetes)

**Example:**
- Non-pregnant: BP >140/90 = hypertension
- Pregnant: BP >140/90 = preeclampsia concern (URGENT)
- Pregnant + BP >140/90 + proteinuria + headache = preeclampsia/eclampsia risk (CRITICAL)

### 10.4 Chronic Disease Populations

**CKD Patients:**
- Different creatinine thresholds (focus on change, not absolute)
- Lower potassium alert threshold
- Expected anemia (adjust Hb thresholds)

**COPD Patients:**
- Lower SpOâ‚‚ targets (88-92% may be baseline)
- Don't over-alert on chronic hypercapnia

**Diabetes Patients:**
- More aggressive glucose alert thresholds
- Hypoglycemia awareness assessment
- DKA risk stratification

**All handled via CONTEXT_RULES.md integration.**

---

## IMPLEMENTATION CHECKLIST

**For IT Team:**

**Core Alert Logic:**
- [ ] Implement four-tier hierarchy (Section 1)
- [ ] Create threshold reference system to PARAMETERS_*.md files (Section 2)
- [ ] Implement single-parameter alert triggers (Section 3.1)
- [ ] Implement temporal escalation rules (Section 3.2)
- [ ] Implement multi-parameter patterns (Section 3.3)
- [ ] Implement home monitoring adjustments (Section 3.4)
- [ ] Create measurement source detection (clinic vs home)

**Suppression & Override:**
- [ ] Implement auto-suppression logic (Section 4.1)
- [ ] Implement clinician override system (Section 4.2)
- [ ] Create suppression decision tree (Section 4.3)

**Display & Workflow:**
- [ ] Create alert prioritization ranking (Section 5.1)
- [ ] Implement hero view alert banner (Section 5.2)
- [ ] Implement acknowledgment requirements (Section 5.3)
- [ ] Implement override-scores logic (Section 5.4)
- [ ] Create time-to-action workflows (Section 6)
- [ ] Build clinician alert queue (Section 7.1)
- [ ] Implement clinician notifications (Section 7.2)
- [ ] Create escalation protocols (Section 7.3)

**Quality & Safety:**
- [ ] Build alert metrics dashboard (Section 8.1)
- [ ] Create calibration review tools (Section 8.2)
- [ ] Implement safety audit reports (Section 8.3)
- [ ] Handle edge cases (Section 9)
- [ ] Implement special population rules (Section 10)

**Integration:**
- [ ] Link to all PARAMETERS_*.md threshold tables
- [ ] Link to CONTEXT_RULES.md patient adjustments
- [ ] Link to TEMPORAL_SCORING.md trend detection
- [ ] Link to CLINICAL_DECISION_RULES.md multi-parameter patterns
- [ ] Link to ALERT_MESSAGES.md for all text content

**Testing:**
- [ ] Unit test all alert triggers
- [ ] Test suppression logic
- [ ] Test escalation logic
- [ ] Test multi-parameter patterns
- [ ] Stress test with high alert volume
- [ ] Validate notification delivery
- [ ] Test override workflows

**For Clinical Team:**

**Threshold Validation:**
- [ ] Review threshold tables in all PARAMETERS_*.md files
- [ ] Validate multi-parameter patterns in CLINICAL_DECISION_RULES.md
- [ ] Approve context-specific adjustments in CONTEXT_RULES.md

**Message Review:**
- [ ] Review all patient alert messages (in ALERT_MESSAGES.md)
- [ ] Review all clinician alert messages (in ALERT_MESSAGES.md)
- [ ] Validate emergency guidance content

**Workflow Validation:**
- [ ] Approve time-to-action targets (Section 6)
- [ ] Approve escalation protocols (Section 7.3)
- [ ] Define on-call coverage requirements

**Safety Validation:**
- [ ] Pilot test with 100 simulated patients
- [ ] Review all CRITICAL alert scenarios
- [ ] Stress test escalation protocols
- [ ] Approve monitoring metrics (Section 8)

**Final Approval:**
- [ ] Clinical committee review
- [ ] Safety committee review
- [ ] Legal/compliance review
- [ ] Sign-off for deployment

---

## APPENDIX A: ALERT ARCHITECTURE DIAGRAM

```
Patient Parameter Measured
    â”‚
    â”œâ”€> Read threshold from PARAMETERS_*.md
    â”‚
    â”œâ”€> Apply context adjustments (CONTEXT_RULES.md)
    â”‚
    â”œâ”€> Check temporal trends (TEMPORAL_SCORING.md)
    â”‚
    â”œâ”€> Check multi-parameter patterns (CLINICAL_DECISION_RULES.md)
    â”‚
    â”œâ”€> Determine alert tier (CRITICAL/URGENT/WARNING/MONITOR)
    â”‚
    â”œâ”€> Check suppression rules (Section 4)
    â”‚   â”œâ”€> Auto-suppress? â†’ Skip alert
    â”‚   â””â”€> No suppression â†’ Continue
    â”‚
    â”œâ”€> Prioritize with other active alerts (Section 5)
    â”‚
    â”œâ”€> Display to patient (Section 5.2)
    â”‚
    â”œâ”€> Notify clinician (Section 7.2)
    â”‚
    â”œâ”€> Track in metrics (Section 8.1)
    â”‚
    â””â”€> Escalate if not addressed (Section 7.3)
```

---

## APPENDIX B: KEY DIFFERENCES FROM v1.0

**v1.1 Improvements:**

1. **Moved thresholds out** - Now references parameter files (single source of truth)
2. **Added temporal escalation** - Rapid changes escalate alert tier
3. **Added multi-parameter patterns** - Sepsis, DKA, shock, stroke patterns
4. **Added home monitoring rules** - Different handling for home vs clinic measurements
5. **Strengthened context integration** - More explicit links to CONTEXT_RULES.md
6. **Improved suppression logic** - More sophisticated auto-suppression
7. **Added special populations** - Pediatric, elderly, pregnancy considerations
8. **Clarified architecture** - What this doc owns vs what lives elsewhere

**v1.0 Issues Resolved:**
- âŒ Duplicated thresholds â†’ âœ… References parameter files
- âŒ Static thresholds â†’ âœ… Context-sensitive via rules
- âŒ Home = clinic â†’ âœ… Different handling
- âŒ Single-parameter only â†’ âœ… Multi-parameter patterns
- âŒ No temporal logic â†’ âœ… Trending escalates alerts
- âŒ Missing patterns â†’ âœ… Added sepsis, DKA, shock, etc.

---

**END OF CRITICAL_ALERTS_v1.1.md**

*This specification provides the complete alert system logic and workflows. Thresholds are defined in PARAMETERS_*.md files. Clinical committee approval required before deployment.*
