# SMART CARD LIFECYCLE & AI-MODIFIABLE PARAMETERS SPECIFICATION

**Version:** 1.0
**Date:** 2025-12-05
**Status:** Active

---

**Source Documents:**
- [UNIVERSAL_CARD_TEMPLATE.md](02_UNIVERSAL_CARD_TEMPLATE.md) - Base template structure
- [CARD_TYPE_SPECIFICATIONS.md](03_CARD_TYPE_SPECIFICATIONS.md) v2.0 - 12 card types
- [CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md](../../CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md) - De-prescribing framework

---

## PURPOSE

This specification defines:
1. **AI-Modifiable Parameter Notation** - Bracket `[ ]` syntax for fields that can be customized
2. **Card Lifecycle Phases** - Initiation → Maintenance → De-loading/De-prescribing
3. **Patient Self-Directed Healthcare Model** - Empowering patients with knowledge and autonomy

---

## CORE PHILOSOPHY: SELF-DIRECTED HEALTHCARE

> **"Patients are the primary healthcare providers for themselves. Clinicians are guidance counselors and specialists who guide, counsel, and redirect as needed."**

### What This Means:

1. **Patients control their health journey** - They decide pace, timing, and priorities
2. **Cards are tools, not orders** - Educational resources with clear action steps
3. **AI personalizes, not prescribes** - AI customizes parameters within safe ranges
4. **Clinicians guide, not dictate** - Available for complex decisions and safety concerns
5. **Every card has an exit strategy** - Clear criteria for starting, maintaining, and stopping

---

## PART 1: AI-MODIFIABLE PARAMETER NOTATION

### **The Bracket `[ ]` Convention**

Any field that can be customized by AI or clinicians uses bracket notation with modification guidance.

### **Notation Format:**

```
field_name: [DEFAULT_VALUE | OPTIONS | MODIFICATION_CRITERIA]
```

### **Examples:**

```yaml
# Frequency with options
frequency: "[Once daily → Twice daily → Three times daily | Increase if: response inadequate after 2 weeks, no side effects | Decrease if: side effects, elderly]"

# Duration with range
duration: "[15 minutes | Range: 5-60 min | Adjust based on: fitness level, time availability, cardiac status]"

# Intensity with progression tiers
intensity: "[RPE 4-5 (Moderate) | Range: RPE 2-8 | Tier 1: RPE 2-4 | Tier 2: RPE 4-6 | Tier 3: RPE 6-8 | Advance after 2 weeks sustained adherence]"

# Target with patient-specific goals
target: "[Systolic BP 120-130 mmHg | Adjust for: age >75 (target 140), diabetes (target 130), frailty (individualize)]"

# Timing with lifestyle alignment
timing: "[Morning | Options: Morning, Bedtime, With meals, Before exercise | Align with: patient schedule, optimal absorption, habit stacking]"
```

---

### **Parameter Categories**

#### **ALWAYS AI-MODIFIABLE (Dynamic per patient):**

| Parameter | Default Notation | AI Modification Criteria |
|-----------|-----------------|-------------------------|
| **Frequency** | `[Default | Options]` | Response, tolerance, schedule |
| **Duration** | `[Default | Range: min-max]` | Fitness level, time, capacity |
| **Intensity** | `[Default | Tier progression]` | Fitness level, cardiac status |
| **Target/Goal** | `[Standard | Patient-specific]` | Age, comorbidities, frailty |
| **Timing** | `[Default | Options]` | Patient schedule, absorption |
| **Follow-up interval** | `[Default | Based on: risk]` | Stability, risk level |

#### **NEVER AI-MODIFIABLE (Static, evidence-based):**

| Parameter | Why Static |
|-----------|-----------|
| **Mechanism of action** | Scientific fact |
| **Evidence citation** | Published literature |
| **Contraindications** | Safety-critical |
| **Drug interactions** | Safety-critical |
| **Critical alert thresholds** | Life-threatening levels |
| **Technique instructions** | Evidence-based protocol |

---

### **Complete AI Parameter Template**

```yaml
# === AI-MODIFIABLE PARAMETERS ===
# These fields use bracket [ ] notation

WHEN:
  frequency: "[VALUE | Options: OPTION_LIST | Increase if: CRITERIA | Decrease if: CRITERIA]"
  duration: "[VALUE | Range: MIN-MAX UNITS | Adjust based on: FACTORS]"
  intensity: "[VALUE | Tier 1: LOW | Tier 2: MED | Tier 3: HIGH | Advance if: CRITERIA]"
  timing: "[VALUE | Options: OPTION_LIST | Align with: PATIENT_FACTORS]"
  start_date: "[Immediately | After: PREREQUISITE | Wait for: CONDITION]"

TARGET:
  primary_goal: "[VALUE | Adjust for: PATIENT_FACTORS]"
  secondary_goal: "[VALUE | Optional if: CONDITION]"
  timeline: "[DURATION | Range: MIN-MAX | Depends on: FACTORS]"

FOLLOW-UP:
  first_check: "[TIMING | Adjust for: RISK_LEVEL]"
  routine_interval: "[INTERVAL | Range: MIN-MAX | Based on: STABILITY]"
  reassessment: "[INTERVAL | Triggers: CRITERIA]"

# === STATIC PARAMETERS (NO BRACKETS) ===
# These fields are evidence-based and fixed

WHAT:
  description: "Exact action statement"
  equipment: "Required items"

HOW:
  technique_steps:
    - "Step 1 - exact instruction"
    - "Step 2 - exact instruction"

SAFETY:
  contraindications: "List of absolute contraindications"
  critical_alerts: "Life-threatening thresholds"
  drug_interactions: "Major interactions"

EVIDENCE:
  source: "Guideline/Journal citation"
  grade: "A/B/C"
```

---

## PART 2: CARD LIFECYCLE PHASES

Every SMART Card has three distinct phases that patients navigate with AI/clinician support.

### **The Three Phases:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│  PHASE 1: INITIATION                                                     │
│  "Getting Started"                                                       │
│  Duration: Days 1-14                                                     │
│  Focus: Setup, education, habit formation                                │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↓
┌─────────────────────────────────────────────────────────────────────────┐
│  PHASE 2: MAINTENANCE                                                    │
│  "Staying on Track"                                                      │
│  Duration: Day 15 - Goal Achievement                                    │
│  Focus: Adherence, adjustment, optimization                              │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↓
┌─────────────────────────────────────────────────────────────────────────┐
│  PHASE 3: DE-LOADING / DE-PRESCRIBING                                   │
│  "Completing Your Journey"                                               │
│  Duration: When criteria met                                             │
│  Focus: Graduation, transition, or discontinuation                       │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## PHASE 1: INITIATION GUIDE

### **Purpose:** Help patient successfully START the intervention

### **Universal Initiation Elements:**

```yaml
INITIATION:
  # Who initiates?
  initiated_by: "[AI recommendation | Clinician prescription | Patient request]"

  # Prerequisites
  prerequisites:
    - "[Any required tests or clearances]"
    - "[Equipment or supplies needed]"
    - "[Education/understanding required]"

  # First Steps
  getting_started:
    day_1: "[Specific action for day 1]"
    days_2_7: "[Building routine - specific guidance]"
    days_8_14: "[Establishing habit - specific guidance]"

  # Starting Parameters (conservative)
  initial_parameters:
    frequency: "[Conservative starting point]"
    duration: "[Lower end of range]"
    intensity: "[Beginner level]"

  # Education Component
  what_you_need_to_know:
    - "[Key concept 1 - simple explanation]"
    - "[Key concept 2 - why this matters]"
    - "[Key concept 3 - what to expect]"

  # Expected Timeline
  expect_to_see:
    first_week: "[What patient might notice]"
    first_month: "[Expected progress]"
    disclaimer: "Individual results vary based on adherence and personal factors"

  # Barriers Anticipation
  common_challenges:
    - challenge: "[Common barrier 1]"
      solution: "[How to overcome]"
    - challenge: "[Common barrier 2]"
      solution: "[How to overcome]"

  # When to Ask for Help
  contact_care_team_if:
    - "[Specific concerning symptom]"
    - "[Uncertainty about how to proceed]"
    - "[Barrier that feels insurmountable]"
```

---

### **Initiation Guide by Card Type:**

#### **MEDICAL CARDS (Medications, DME, Procedures, Referrals)**

```yaml
INITIATION:
  clinician_role: "Prescribes and explains rationale"
  ai_role: "Generates card, tracks adherence, answers questions"
  patient_role: "Fills prescription, learns technique, begins use"

  first_steps:
    - "Obtain medication/equipment from pharmacy/DME supplier"
    - "Review HOW section for proper technique"
    - "Set reminder at scheduled time"
    - "Complete first dose/use with checklist"

  education_required:
    - "Why this intervention was recommended (linked Micro-Learning card)"
    - "What to expect in first days/weeks"
    - "Side effects to watch for"
    - "When to contact care team"

  initial_check_in: "[7 days for medications | 14 days for DME | Post-procedure for procedures]"
```

#### **BEHAVIORAL CARDS (Nutrition, Movement, Recovery, Mind-Body, Environmental/Social)**

```yaml
INITIATION:
  clinician_role: "Optional guidance, available for questions"
  ai_role: "Recommends based on dashboard, personalizes parameters, supports habit formation"
  patient_role: "Commits to trying, begins practice, tracks progress"

  first_steps:
    - "Read card completely (takes ~3 minutes)"
    - "Gather any needed equipment/supplies"
    - "Choose best time in your schedule"
    - "Complete first session today"
    - "Log completion in app"

  habit_formation_support:
    week_1: "Focus on just doing it - don't worry about perfection"
    week_2: "Anchor to existing habit (after morning coffee, before dinner)"
    week_3: "Notice how you feel - building intrinsic motivation"
    week_4: "Celebrate consistency - you're building a habit!"

  initial_parameters:
    frequency: "[Start with 3x/week, build to daily]"
    duration: "[Start with minimum effective dose]"
    intensity: "[Start at Tier 1 - Beginner]"

  ai_check_in: "Day 7: How's it going? Need any adjustments?"
```

#### **MICRO-LEARNING CARDS (Educational)**

```yaml
INITIATION:
  purpose: "Build foundational knowledge before action cards"

  first_steps:
    - "Find 5 quiet minutes"
    - "Read/watch the content"
    - "Complete knowledge check (optional)"
    - "Card automatically graduates upon completion"

  sequence: "Usually assigned BEFORE related action card"

  example_flow:
    step_1: "Learn: 'Understanding Blood Pressure Numbers' (Micro-Learning)"
    step_2: "Do: 'Check Blood Pressure at Home' (Diagnostic Testing Card)"
```

---

## PHASE 2: MAINTENANCE GUIDE

### **Purpose:** Keep patient on track and optimize the intervention

### **Universal Maintenance Elements:**

```yaml
MAINTENANCE:
  # Ongoing Tracking
  daily_actions:
    - "[What patient does each day/session]"
    - "[How to log completion]"

  # Progress Monitoring
  ai_monitoring:
    adherence_tracking: "AI monitors completion rate"
    parameter_trends: "AI watches dashboard metrics"
    barrier_detection: "AI notices patterns in missed days"

  # Adjustment Triggers
  adjustment_criteria:
    increase_if:
      - "[Criterion 1 - e.g., adherence >80% for 2 weeks]"
      - "[Criterion 2 - e.g., no side effects, feeling ready]"
    decrease_if:
      - "[Criterion 1 - e.g., side effects, fatigue]"
      - "[Criterion 2 - e.g., schedule conflicts, barriers]"
    hold_steady_if:
      - "[Criterion - e.g., currently optimized, stable]"

  # Tier Progression (for tierable cards)
  progression:
    tier_1_to_2: "[Criteria to advance - e.g., 2 weeks sustained, no issues]"
    tier_2_to_3: "[Criteria to advance]"
    regression: "[When to step back - e.g., prolonged break, illness recovery]"

  # Periodic Check-ins
  scheduled_reviews:
    weekly: "AI adherence check + encouragement"
    monthly: "Parameter effectiveness review"
    quarterly: "Comprehensive goal assessment"

  # Troubleshooting
  if_struggling:
    low_adherence:
      - "AI asks: What's getting in the way?"
      - "AI offers: Simpler version, different timing, alternative card"
    no_improvement:
      - "AI reviews: Has adequate trial occurred?"
      - "AI considers: Need to escalate or try alternative?"
    side_effects:
      - "AI assesses: Severity and pattern"
      - "AI action: Escalate if concerning, suggest modification if mild"

  # Synergy Reminders
  habit_stacking:
    - "Consider pairing with: [Related active card]"
    - "Time-saving combo: [How to bundle actions]"
```

---

### **Maintenance Guide by Card Type:**

#### **MEDICATION CARDS**

```yaml
MAINTENANCE:
  daily_action: "Take medication as prescribed, log in app"

  ai_monitoring:
    refill_tracking: "AI alerts when refill due"
    interaction_watch: "AI monitors for new drug interactions"
    parameter_trends: "AI tracks related dashboard metrics (BP, glucose, etc.)"

  adjustment_criteria:
    dose_increase_triggers:
      - "Target not achieved after [adequate trial period]"
      - "No significant side effects"
      - "Clinician approval required for: [HIGH_RISK_MEDS]"
    dose_decrease_triggers:
      - "Side effects limiting tolerability"
      - "Parameter over-corrected (e.g., BP too low)"
      - "Always require clinician approval"

  periodic_labs: "[Specific monitoring - e.g., K+ and creatinine for ACE-I]"

  patient_self_monitoring:
    - "[What patient should track - e.g., home BP]"
    - "[When to contact team - e.g., BP >180 or <90]"
```

#### **BEHAVIORAL CARDS**

```yaml
MAINTENANCE:
  daily_action: "Complete session, log in app"

  ai_monitoring:
    adherence_rate: "Target: 80%+ over rolling 14 days"
    parameter_improvement: "Track related dashboard score"
    habit_formation: "Note if behavior becoming automatic"

  progression_pathway:
    week_2: "If adherence >80%, offer intensity increase"
    week_4: "If sustained, offer advanced techniques"
    week_8: "If behavior automatic, discuss graduation"

  plateau_handling:
    if_no_improvement:
      - "AI checks: Is adherence adequate?"
      - "AI considers: Wrong approach or need to persist?"
      - "AI offers: Alternative card or additional support"

  motivation_support:
    milestones: "Celebrate 7-day, 30-day, 90-day streaks"
    progress_visualization: "Show parameter trends linked to behavior"
    community: "Share anonymous success rate for this card"
```

---

## PHASE 3: DE-LOADING / DE-PRESCRIBING GUIDE

### **Purpose:** Help patient successfully COMPLETE or STOP the intervention

### **Three Exit Pathways:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│  PATHWAY A: GRADUATION 🎓                                                │
│  "You achieved your goal!"                                               │
│  Outcome: Card moves to "Completed Successfully" with celebration        │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│  PATHWAY B: TRANSITION 🔄                                                │
│  "Time for something different"                                          │
│  Outcome: Current card replaced with alternative/advanced card           │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│  PATHWAY C: DISCONTINUATION ⏹️                                          │
│  "This isn't right for you"                                              │
│  Outcome: Card removed (with safety checks for medical cards)            │
└─────────────────────────────────────────────────────────────────────────┘
```

---

### **Universal De-Loading Elements:**

```yaml
DE_LOADING:
  # Graduation Criteria
  graduation_triggers:
    - "[Goal achieved - specific metric]"
    - "[Behavior now habitual - 90 days sustained]"
    - "[Diagnosis resolved]"
    - "[Treatment course completed]"

  # Transition Criteria
  transition_triggers:
    advance_to_higher:
      - "[Ready for more challenge]"
      - "[Current level too easy]"
    step_down_to_lower:
      - "[Current level too difficult]"
      - "[Temporary setback - illness, injury, life stress]"
    switch_to_alternative:
      - "[Current approach not resonating]"
      - "[Patient preference for different method]"
      - "[Better option available]"

  # Discontinuation Criteria
  discontinuation_triggers:
    - "[Adverse event or intolerable side effect]"
    - "[Treatment ineffective after adequate trial]"
    - "[Contraindication developed]"
    - "[Patient informed decision to stop]"

  # Who Can Initiate De-Loading?
  autonomy_by_card_type:
    patient_fully_autonomous:
      - "Behavioral cards (Nutrition, Movement, Recovery, Mind-Body)"
      - "Micro-Learning cards"
    patient_requests_ai_approves:
      - "Low-risk medical cards"
      - "Lifestyle changes affecting parameters"
    clinician_required:
      - "Chronic disease medications"
      - "Controlled substances"
      - "High-risk medical interventions"
      - "DME with safety implications (CPAP, insulin pump)"

  # Off-Ramp Process
  graduation_process:
    step_1: "Criteria met → AI or patient initiates graduation"
    step_2: "Final review of achievements"
    step_3: "Card moves to 'Graduated' status"
    step_4: "Celebration message + success badge"
    step_5: "Recommendation for next step (optional)"

  transition_process:
    step_1: "Trigger identified (ready for more, need simpler, prefer alternative)"
    step_2: "AI presents options with rationale"
    step_3: "Patient selects new card"
    step_4: "Current card archived with outcome note"
    step_5: "New card begins in Initiation phase"

  discontinuation_process:
    step_1: "Trigger identified"
    step_2: "Safety check (does stopping require tapering? clinician review?)"
    step_3: "If safe → AI discontinues with explanation"
    step_4: "If needs review → Escalate to clinician"
    step_5: "Card archived with outcome note"

  # Patient Messaging
  graduation_message: |
    🎓 Congratulations! You've successfully completed your [CARD_NAME] card!

    Your Achievement:
    - [SPECIFIC_OUTCOME - e.g., "30 days of consistent walking"]
    - [METRIC_IMPROVEMENT - e.g., "Cardiovascular score improved from 62 to 78"]

    What's Next?
    - This behavior is now a habit - keep it up!
    - [OPTIONAL_NEXT_CARD - e.g., "Ready for Hill Walking?"]

  transition_message: |
    🔄 Time for a change!

    Your [CURRENT_CARD] has served its purpose. Based on your progress,
    I recommend transitioning to [NEW_CARD].

    Why? [RATIONALE - e.g., "You've mastered the basics and are ready for more challenge"]

    [Accept New Card] [See Other Options] [Stay with Current]

  discontinuation_message: |
    ⏹️ Stopping [CARD_NAME]

    Reason: [REASON - e.g., "This approach wasn't a good fit for you"]

    What We Learned: [INSIGHT - e.g., "Carb counting was too complex;
    simpler approaches may work better"]

    Alternative: [SUGGESTION - e.g., "Would you like to try the Plate Method instead?"]

    [Try Alternative] [Take a Break] [Talk to Care Team]
```

---

### **De-Loading Guide by Card Type:**

#### **MEDICATIONS**

```yaml
DE_LOADING:
  graduation_criteria:
    - "Completed prescribed course (e.g., antibiotic 7 days)"
    - "Diagnosis resolved with documentation"
    - "Parameter normalized for sustained period (clinician-approved deprescribing)"

  discontinuation_criteria:
    - "Adverse drug reaction"
    - "Drug-drug interaction identified"
    - "Contraindication developed"
    - "Ineffective after adequate trial"

  tapering_required:
    - "Beta-blockers: Gradual reduction over 1-2 weeks"
    - "Corticosteroids: Depends on duration/dose"
    - "Benzodiazepines: Slow taper over weeks-months"
    - "Opioids: Supervised taper"
    - "SSRIs/SNRIs: Gradual reduction to avoid discontinuation syndrome"

  patient_autonomy:
    can_request: "Patient can flag card for review anytime"
    cannot_stop_independently:
      - "Chronic disease medications without clinician approval"
      - "Medications requiring tapering"
      - "Controlled substances"

  clinician_role: "Required for dose changes and discontinuation of chronic meds"

  ai_role:
    - "Detects when graduation criteria met"
    - "Flags potential interactions or side effects"
    - "Recommends deprescribing when appropriate (clinician approves)"
```

#### **BEHAVIORAL CARDS (Nutrition, Movement, Recovery, Mind-Body, Environmental/Social)**

```yaml
DE_LOADING:
  graduation_criteria:
    - "Behavior sustained 90 days"
    - "Related dashboard parameter improved"
    - "Patient reports behavior now automatic"

  transition_criteria:
    ready_for_more:
      - "80%+ adherence for 2+ weeks at current level"
      - "Patient expresses desire for challenge"
      - "Fitness/capacity improved per Section 1 data"
    need_simpler:
      - "<50% adherence for 2+ weeks"
      - "Patient reports struggling"
      - "Life circumstances changed (injury, stress, time)"

  discontinuation_criteria:
    - "Patient tried earnestly but not sustainable"
    - "Alternative approach preferred"
    - "No longer clinically indicated"

  patient_autonomy:
    fully_self_directed:
      - "Patient can graduate own card if confident behavior is habit"
      - "Patient can request pause anytime"
      - "Patient can switch to alternative anytime"

  ai_role:
    - "Celebrates graduation, awards badges"
    - "Recommends next-level cards"
    - "Offers alternatives if struggling"

  clinician_role: "Optional - patient can request consultation"
```

#### **DME (CPAP, CGM, etc.)**

```yaml
DE_LOADING:
  graduation_criteria:
    - "Device used consistently 90 days"
    - "Clinical parameter improved (e.g., AHI normalized with CPAP)"
    - "Patient proficient and independent with device"

  discontinuation_criteria:
    - "Device no longer needed (rare for chronic conditions)"
    - "Device not tolerated after troubleshooting"
    - "Upgrade to newer device"

  patient_autonomy:
    can_request: "Discontinuation review"
    cannot_stop_independently:
      - "CPAP (requires sleep study confirmation)"
      - "CGM (requires diabetes care team approval)"
      - "Oxygen therapy (requires clinician assessment)"

  clinician_role: "Required for discontinuation of most DME"

  two_step_workflow:
    note: "DME cards are TWO linked cards - see DME_MONITORING_WORKFLOW_PATTERN.md"
    step_1: "Obtain DME card → graduates when device received + training complete"
    step_2: "Use DME card → graduates when sustained use + parameter improvement"
```

#### **MICRO-LEARNING (Educational)**

```yaml
DE_LOADING:
  graduation_criteria:
    - "Content consumed (read/watched)"
    - "Optional: Knowledge check passed"

  auto_graduation: true

  no_discontinuation:
    note: "Micro-Learning cards complete, not discontinue"
    outcome: "Card moves to 'Learned' status"

  patient_autonomy: "Fully self-directed - complete at own pace"
```

---

## PART 3: COMPLETE CARD TEMPLATE WITH LIFECYCLE

### **Full Template Combining All Elements:**

```yaml
# ============================================================================
# SMART CARD COMPLETE TEMPLATE
# Version: 2.0
# Includes: AI Parameters (brackets) + Lifecycle Phases
# ============================================================================

card_id: "[CATEGORY]_[SUBCATEGORY]_[NUMBER]"
card_name: "Action Name"
card_type: "[One of 12 types]"
card_tier: "[Tier 1-5 per LIBRARY_TIER_STRUCTURE]"
version: "1.0"
last_updated: "YYYY-MM-DD"

# ============================================================================
# SECTION 1: STATIC CONTENT (Pre-generated, evidence-based)
# ============================================================================

WHAT:
  description: "Clear, simple description of the action"
  details:
    # Card-type specific (e.g., drug name, exercise type, food action)

WHO:
  primary_actor: "Patient | Clinician | Specialist"
  support_actors: ["List of support roles"]
  special_populations:
    geriatric: "Considerations"
    pediatric: "Considerations"
    pregnancy: "Category and guidance"
    renal_impairment: "Adjustments"
    hepatic_impairment: "Adjustments"

HOW:
  step_by_step:
    - "Step 1 - specific instruction"
    - "Step 2 - specific instruction"
    - "Step 3 - specific instruction"
  technique_tips:
    - "Practical tip 1"
    - "Practical tip 2"
  equipment_needed: "List of required items"

WHERE:
  setting: "Home | Clinic | Gym | Outdoors | etc."
  location_notes: "Specific location guidance"

WHY:
  clinical_goal: "[System]: [Domain] - e.g., Cardiovascular: Reduce Risk"
  patient_motivation: "[To be personalized with patient's own words]"
  mechanism: "How this intervention works (simplified)"

EVIDENCE:
  source: "Guideline or journal citation"
  grade: "A | B | C"
  summary: "One-sentence evidence summary"
  time_to_benefit: "When patient should expect to see results"

SAFETY:
  # Organized by severity (static, evidence-based)
  common_side_effects:  # Yellow - monitor, usually continue
    - "Side effect 1 (frequency %)"
    - "Side effect 2 (frequency %)"
  stop_and_contact:  # Orange - hold and contact care team
    - "Warning sign 1"
    - "Warning sign 2"
  emergency_911:  # Red - call 911
    - "Life-threatening sign 1"
    - "Life-threatening sign 2"
  contraindications:
    absolute: ["List"]
    relative: ["List"]
  interactions: ["Drug/food/activity interactions"]

MEASURE:
  primary_metric: "What to track"
  secondary_metrics: ["Additional metrics"]
  tracking_method: "How to measure"
  tracking_frequency: "How often to measure"

# ============================================================================
# SECTION 2: AI-MODIFIABLE PARAMETERS (Bracket notation)
# ============================================================================

WHEN:
  frequency: "[DEFAULT | Options: OPTION_LIST | Increase if: CRITERIA | Decrease if: CRITERIA]"
  duration: "[DEFAULT | Range: MIN-MAX | Adjust based on: FACTORS]"
  intensity: "[DEFAULT | Tier 1: LOW | Tier 2: MED | Tier 3: HIGH | Advance if: CRITERIA]"
  timing: "[DEFAULT | Options: OPTION_LIST | Align with: PATIENT_FACTORS]"
  start_date: "[Immediately | After: PREREQUISITE]"

TARGET:
  primary_goal: "[VALUE | Adjust for: PATIENT_FACTORS]"
  timeline: "[DURATION | Range: MIN-MAX]"
  success_criteria: "[How to know it's working]"

FOLLOW_UP:
  initial_check: "[TIMING | Adjust for: RISK_LEVEL]"
  routine_interval: "[INTERVAL | Based on: STABILITY]"
  reassessment_trigger: "[CRITERIA for review]"

# ============================================================================
# SECTION 3: LIFECYCLE PHASES
# ============================================================================

INITIATION:
  initiated_by: "[AI recommendation | Clinician prescription | Patient request]"
  prerequisites:
    - "Prerequisite 1"
    - "Prerequisite 2"
  getting_started:
    day_1: "What to do on day 1"
    week_1: "First week focus"
    week_2: "Second week focus"
  initial_parameters:
    # Conservative starting values
    frequency: "[Starting frequency]"
    duration: "[Starting duration]"
    intensity: "[Starting intensity - Tier 1]"
  education_link: "[MICRO_LEARNING_CARD_ID for foundational knowledge]"
  common_early_challenges:
    - challenge: "Challenge 1"
      solution: "How to overcome"
    - challenge: "Challenge 2"
      solution: "How to overcome"
  contact_care_team_if:
    - "Concerning symptom"
    - "Uncertainty requiring guidance"

MAINTENANCE:
  daily_actions:
    - "What patient does each day/session"
    - "How to log completion"
  ai_monitoring:
    adherence_target: "80%+ over 14 days"
    parameter_tracking: "Which dashboard metrics AI watches"
    barrier_detection: "How AI notices struggles"
  adjustment_triggers:
    increase_if: ["Criteria"]
    decrease_if: ["Criteria"]
    hold_if: ["Criteria"]
  progression_pathway:
    tier_1_to_2: "Criteria to advance"
    tier_2_to_3: "Criteria to advance"
    regression: "When to step back"
  troubleshooting:
    low_adherence: "AI offers simpler version or alternative"
    no_improvement: "AI reviews and considers alternatives"
    side_effects: "AI assesses and escalates if needed"
  scheduled_reviews:
    weekly: "Adherence check"
    monthly: "Parameter review"
    quarterly: "Goal assessment"
  synergy_tips:
    pair_with: "[Related active cards for habit stacking]"

DE_LOADING:
  graduation_criteria:
    - "Goal achieved - specific metric"
    - "Behavior sustained 90 days (behavioral cards)"
    - "Treatment course completed (medical cards)"
  transition_criteria:
    advance_to_higher: ["Ready for more challenge"]
    step_down: ["Need simpler approach"]
    switch_alternative: ["Different method preferred"]
  discontinuation_criteria:
    - "Adverse event"
    - "Ineffective after adequate trial"
    - "Contraindication developed"
    - "Patient informed preference"
  autonomy_level: "Fully self-directed | Needs AI approval | Needs clinician approval"
  tapering_required: "Yes/No - if yes, protocol reference"
  off_ramp_options:
    graduation: "Move to Completed Successfully"
    transition: "Switch to [ALTERNATIVE_CARD_IDS]"
    discontinuation: "Archive with outcome note"
  messaging:
    graduation: "Celebration message template"
    transition: "Change explanation template"
    discontinuation: "Compassionate stop message"

# ============================================================================
# SECTION 4: METADATA
# ============================================================================

METADATA:
  tags: ["Clinical intent", "Evidence", "Condition", "System", "Population"]
  evidence_grade: "A | B | C"
  feasibility_score: "[AI-calculated based on barriers]"
  version_history:
    - version: "1.0"
      date: "YYYY-MM-DD"
      changes: "Initial creation"
```

---

## IMPLEMENTATION PRIORITY

### **Phase 1: Template Updates (Immediate)**
1. Update UNIVERSAL_CARD_TEMPLATE.md with lifecycle sections
2. Add bracket notation examples to CARD_TYPE_SPECIFICATIONS.md
3. Update CARD_DEPRESCRIBING spec to reference this document

### **Phase 2: Library Updates (Next)**
1. Add lifecycle sections to Tier 5 card templates
2. Ensure all card type-specific de-loading criteria documented

### **Phase 3: Generation Integration (Future)**
1. CARD_GENERATION_SPECIFICATION.md uses this for AI parameter bounds
2. AI agent uses lifecycle phases for patient journey management

---

## SUMMARY

This specification provides:

✅ **Bracket `[ ]` notation** for AI-modifiable fields with modification guidance
✅ **Three-phase lifecycle** for every card (Initiation → Maintenance → De-loading)
✅ **Patient self-directed model** empowering patients with knowledge and autonomy
✅ **Clear autonomy levels** by card type (fully self-directed vs. clinician required)
✅ **Exit strategies** for every card (graduation, transition, discontinuation)
✅ **Complete template** combining all elements

**Key Innovation:**
> Patients are equipped with complete knowledge to manage their own health journey, with AI personalization and clinician guidance available when needed.

---

**END OF DOCUMENT**
