# CARE PLAN & SMART CARD INTEGRATION SPECIFICATION
**Version:** 1.0
**Date:** 2025-12-12
**Status:** Master-Level Architectural Specification
**Scope:** Platform-Wide (All 4 Sections)

---

## PURPOSE

This specification defines how **Care Plans** and **SMART Cards** integrate into a unified, data-reactive healthcare system. It establishes:

1. **Care Plan as organized collection of SMART Cards** (not separate from cards)
2. **Three Care Plan Types** (Chronic, Subacute, Acute) that coexist and interact
3. **Data Reactivity Model** - how patient data input drives care plan generation
4. **Multi-Specialty AI Selection Logic** - how different clinical domains recommend cards
5. **Patient Visibility Architecture** - progressive disclosure from daily focus to full plan
6. **90/10 Self-Directed Model** - 90% patient autonomous, 10% clinician intervention

---

## CORE PRINCIPLE

> **"The Care Plan IS a grouping of SMART Cards, organized clinically and temporally."**

A Care Plan is NOT:
- A separate document from SMART Cards
- A static annual plan
- A clinician-only artifact

A Care Plan IS:
- A dynamically organized collection of SMART Cards
- Updated in real-time as data flows in
- Visible to patients at multiple levels of detail
- The container that makes 1,000+ cards manageable

---

## THE THREE CARE PLAN TYPES

### Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     THREE COEXISTING CARE PLAN TYPES                         │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                 CHRONIC CARE PLAN (Baseline)                         │   │
│   │                 ─────────────────────────────                        │   │
│   │   Timeframe: 12 months, reviewed quarterly                          │   │
│   │   Trigger: Comprehensive assessment, annual review                   │   │
│   │   Focus: Prevention, Maintenance, Enhancement, Treatment            │   │
│   │   Cards: Organized by quarter (Q1 active, Q2-4 queued)             │   │
│   │   Status: Always active for every patient                           │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    │ Can spawn when data triggers            │
│                                    ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                 SUBACUTE CARE PLAN (Overlay)                         │   │
│   │                 ────────────────────────────                         │   │
│   │   Timeframe: Days to weeks                                           │   │
│   │   Trigger: Trend change, new symptom, life event, lab result        │   │
│   │   Focus: Investigate, Adjust, Transition, Monitor                   │   │
│   │   Cards: Temporary additions to address emerging issue              │   │
│   │   Status: Active when triggered, resolves back to chronic           │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    │ Can spawn when critical trigger         │
│                                    ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                 ACUTE CARE PLAN (Emergency Overlay)                  │   │
│   │                 ───────────────────────────────                      │   │
│   │   Timeframe: Minutes to hours                                        │   │
│   │   Trigger: Critical value, emergency symptom, urgent need           │   │
│   │   Focus: Immediate intervention, Triage, Crisis response            │   │
│   │   Cards: Urgent action cards, may pause non-essential chronic       │   │
│   │   Status: Active during emergency, documents to chronic plan        │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Type 1: CHRONIC CARE PLAN

**Definition:** The baseline 12-month health roadmap containing all planned interventions.

**Structure:**
```yaml
chronic_care_plan:
  timeframe: 12_months
  review_cycle: quarterly

  patient_goal:
    primary: "Stay independent at home as I age"
    measurable: "No falls, maintain daily activities without assistance"

  life_stage: "Older Adulthood (65-79)"
  priority_systems: [musculoskeletal, cardiovascular]

  health_matrix:
    # 8 systems × 3 domains = 24 cells
    # Each cell: green/yellow/orange/red

  card_organization:
    by_time_interval:
      daily: [medications, micro_habits]
      weekly: [strength_training, meal_prep]
      monthly: [weight_check, bp_average]
      quarterly: [labs, care_plan_review]
      annually: [comprehensive_assessment, screenings]

    by_quarter:
      Q1_active:
        theme: "Foundation"
        cards: [lisinopril, atorvastatin, vitamin_d, walking, strength, sleep_hygiene]

      Q2_queued:
        theme: "Build"
        cards: [balance_training, protein_optimization, calcium]
        unlock_criteria: "Q1 adherence ≥70%"

      Q3_queued:
        theme: "Optimize"
        cards: [interval_walking, meal_timing, stress_breathing]

      Q4_queued:
        theme: "Sustain"
        cards: [maintenance_phase, annual_reassessment]

    by_clinical_intent:
      stabilize: [bp_management, glucose_control]  # Highest priority
      restore: [strength_training, walking]
      protect: [statin, screenings, fall_prevention]
      optimize: [advanced_nutrition, biohacking]  # Only after stabilized
```

**Card Limit Rules:**
- Maximum 3 active behavioral cards at any time
- Medications don't count against behavioral limit
- Cards must graduate/transition before new cards unlock

---

### Type 2: SUBACUTE CARE PLAN

**Definition:** Temporary overlay triggered by emerging issues requiring investigation or adjustment.

**Trigger Conditions:**
```yaml
subacute_triggers:
  trend_changes:
    - "Parameter increased/decreased >15% from baseline over 2 weeks"
    - "Adherence dropped >25% from previous month"
    - "Three consecutive out-of-range readings"

  new_symptoms:
    - "Patient reports new symptom not previously documented"
    - "Side effect reported for active medication"
    - "Pain level increased >2 points on 0-10 scale"

  life_events:
    - "Major stress event (job change, divorce, bereavement)"
    - "Travel/vacation disrupting routine"
    - "Illness (cold, flu, injury)"

  lab_results:
    - "A1c increased despite adherence"
    - "New abnormal finding requiring follow-up"
    - "Medication level outside therapeutic range"
```

**Example Subacute Plan:**
```yaml
subacute_plan:
  id: "SUB_2025_001"
  trigger: "Fasting glucose trending up 25% over 4 days"
  trigger_date: "2025-12-10"

  investigation_cards:
    - card_id: "DIAG_GLUCOSE_PATTERN"
      duration: "7 days"
      purpose: "Track glucose with meals to identify pattern"

    - card_id: "EDU_BLOOD_SUGAR_FACTORS"
      type: "micro_learning"
      purpose: "Patient education on what affects glucose"

  scheduled_check_in: "Day 7"

  resolution_paths:
    lifestyle_identified:
      criteria: "Pattern shows meal/activity correlation"
      action: "Add targeted nutrition/movement card"
      return_to: "chronic_plan"

    medication_needed:
      criteria: "Pattern persists despite lifestyle factors controlled"
      action: "Escalate to Tier 3 for medication review"
      clinician_notification: true

    resolved_spontaneously:
      criteria: "Glucose returns to baseline within 7 days"
      action: "Document and close subacute plan"
      return_to: "chronic_plan"
```

**Patient Experience:**
```
┌─────────────────────────────────────────────────────────────────┐
│  ⚠️ ATTENTION NEEDED                                            │
│                                                                 │
│  Your fasting glucose has been higher than usual this week.    │
│  Average: 149 mg/dL (was 112)                                   │
│                                                                 │
│  NEW CARDS ACTIVATED (temporary):                               │
│  📋 Glucose Pattern Logging - Track meals + glucose for 7 days │
│  📚 "What Affects Blood Sugar" - Quick learning module         │
│                                                                 │
│  📱 Check-in scheduled: December 17                             │
│                                                                 │
│  Your regular care plan continues unchanged for now.            │
│  We're gathering more data before making changes.               │
│                                                                 │
│  [VIEW MY CARE PLAN]  [LOG TODAY'S GLUCOSE]                    │
└─────────────────────────────────────────────────────────────────┘
```

---

### Type 3: ACUTE CARE PLAN

**Definition:** Emergency overlay activated by critical values or urgent symptoms requiring immediate response.

**Trigger Conditions:**
```yaml
acute_triggers:
  critical_vitals:
    - "BP systolic >180 or diastolic >120"
    - "BP systolic <90 or diastolic <60"
    - "Heart rate >150 or <40"
    - "Oxygen saturation <90%"
    - "Temperature >103°F or <95°F"
    - "Blood glucose <54 or >400 mg/dL"

  emergency_symptoms:
    - "Chest pain"
    - "Difficulty breathing"
    - "Stroke symptoms (FAST)"
    - "Severe allergic reaction"
    - "Suicidal ideation"
    - "Severe bleeding"

  urgent_situations:
    - "Medication error detected"
    - "Dangerous drug interaction identified"
    - "Critical lab value (K+ <2.5 or >6.5, etc.)"
    - "Patient requests emergency help"
```

**Response Protocol:**
```yaml
acute_plan:
  id: "ACUTE_2025_001"
  trigger: "BP reading 182/108 with headache"
  trigger_time: "2025-12-12 09:45:00"
  severity: "urgent"

  immediate_actions:
    patient_facing:
      - instruction: "Sit down and rest"
      - instruction: "Retake BP in 5 minutes"
      - question: "Did you take your Lisinopril today?"
      - warning: "If BP still >180 OR headache worsens, call 911"

    system_actions:
      - action: "Pause exercise cards temporarily"
      - action: "Alert care team (DataWatch → Clinician)"
      - action: "Log critical event in record"

  clinician_notification:
    method: "immediate_push"
    recipient: "primary_care_physician"
    expected_response: "30 minutes"
    includes: [patient_context, recent_vitals, current_medications, AI_assessment]

  resolution:
    if_resolved:
      document: "Missed Lisinopril dose, BP normalized after rest"
      add_card: "Medication reminder enhancement"
      return_to: "chronic_plan"

    if_escalates:
      action: "Direct to ER"
      maintain_tracking: true
```

**Patient Experience:**
```
┌─────────────────────────────────────────────────────────────────┐
│  🔴 URGENT: HIGH BLOOD PRESSURE + HEADACHE                      │
│                                                                 │
│  Your BP reading of 182/108 with headache needs attention NOW. │
│                                                                 │
│  IMMEDIATE ACTIONS:                                             │
│  1. ✓ Sit down, rest, breathe slowly                           │
│  2. ☐ Retake BP in 5 minutes                                    │
│  3. ☐ Did you take your Lisinopril today? [YES] [NO]           │
│                                                                 │
│  ⚠️ IF BP still >180 OR headache worsens OR new symptoms:      │
│  ☎️ CALL 911 or go to ER immediately                           │
│                                                                 │
│  Your care team has been notified.                              │
│  Expect a call within 30 minutes.                               │
│                                                                 │
│  [RETAKE BP NOW]  [CALL 911]  [I FEEL BETTER]                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## CARE PLAN INTERACTION RULES

### How the Three Types Coexist

```
NORMAL STATE:
┌─────────────────────────────────────────────────────────────────┐
│  CHRONIC CARE PLAN (Active)                                     │
│  ├── Q1 Active Cards: Medications + Walking + Sleep Hygiene    │
│  └── Status: GREEN - All systems stable                         │
└─────────────────────────────────────────────────────────────────┘

SUBACUTE TRIGGERED:
┌─────────────────────────────────────────────────────────────────┐
│  CHRONIC CARE PLAN (Active - continues unchanged)              │
│  ├── Q1 Active Cards: Medications + Walking + Sleep Hygiene    │
│  └── Status: YELLOW - Monitoring emerging issue                 │
│                                                                 │
│  + SUBACUTE OVERLAY (Temporary)                                 │
│    ├── Investigation Cards: Glucose logging, education         │
│    └── Duration: 7 days, then resolves                          │
└─────────────────────────────────────────────────────────────────┘

ACUTE TRIGGERED:
┌─────────────────────────────────────────────────────────────────┐
│  CHRONIC CARE PLAN (Partially paused)                          │
│  ├── Medications: CONTINUE                                      │
│  ├── Exercise Cards: PAUSED temporarily                         │
│  └── Status: RED - Crisis mode                                  │
│                                                                 │
│  + ACUTE OVERLAY (Priority)                                     │
│    ├── Crisis Protocol: BP emergency response                   │
│    ├── Clinician Notified: Yes                                  │
│    └── Duration: Until resolved (minutes to hours)              │
└─────────────────────────────────────────────────────────────────┘
```

### Resolution and Documentation

**Subacute Resolution:**
- Pattern identified → Add/adjust cards in chronic plan
- Medication needed → Tier 3 clinician review
- Spontaneous resolution → Document and close
- All subacute events logged for quarterly review

**Acute Resolution:**
- Crisis resolved → Document cause and resolution
- Adjust chronic plan if needed (e.g., add medication reminder card)
- If hospitalization → Chronic plan paused, resumed post-discharge
- All acute events trigger clinician review within 24 hours

---

## DATA REACTIVITY MODEL

### Core Principle

> **"The more data patients input, the smarter and more responsive their care plan becomes."**

### Data Input → System Response Spectrum

```
DATA INPUT LEVEL          SYSTEM CAPABILITY             CARE PLAN RESPONSE
═══════════════════════════════════════════════════════════════════════════

MINIMAL (Annual only)     Basic chronic care            Static annual plan
                         No dynamic adjustment          Reactive only

                                    │
                                    ▼

MODERATE (Quarterly +     Chronic + Some subacute       Quarterly adjustments
sporadic monitoring)      Catches some trends           Somewhat proactive

                                    │
                                    ▼

ACTIVE (Regular home      Full dynamic care             Real-time response
data: glucose, BP,        Trend detection               Proactive intervention
symptoms, adherence)      Subacute triggering           Early problem catching

                                    │
                                    ▼

CONTINUOUS (Wearables,    Anticipatory care             Predictive adjustments
CGM, smart devices,       Predicts before symptoms      "Your A1c may rise if
daily logging)            Pattern correlation            current pattern continues"
```

### Patient Incentive Model

```yaml
patient_messaging:

  data_equals_better_care:
    - "Every BP reading helps us catch trends faster"
    - "Logging your meals reveals YOUR personal patterns"
    - "Symptom reports help us adjust before problems grow"
    - "Adherence tracking shows what's working FOR YOU"

  tangible_benefits:
    - more_data: "We catch issues in 3 days instead of 3 months"
    - symptom_logging: "We understand YOUR unique patterns"
    - side_effect_reports: "We adjust faster, less suffering"
    - wearable_integration: "We predict problems before you feel them"
```

---

## MULTI-SPECIALTY AI SELECTION ARCHITECTURE

### Overview

The SMART Card library (1,000+ cards) is queried by **domain-specific AI specialists**, not a single AI. Each specialist owns specific health systems and lifestyle pillars.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    MULTI-SPECIALTY AI SELECTION                              │
│                                                                              │
│                         ┌─────────────────────┐                             │
│                         │   PATIENT DATA      │                             │
│                         │   (Health Matrix)   │                             │
│                         └──────────┬──────────┘                             │
│                                    │                                         │
│                         ┌──────────▼──────────┐                             │
│                         │   PCP AI            │                             │
│                         │   (Orchestrator)    │                             │
│                         └──────────┬──────────┘                             │
│                                    │                                         │
│         ┌──────────────────────────┼──────────────────────────┐             │
│         │                          │                          │             │
│         ▼                          ▼                          ▼             │
│  ┌─────────────┐           ┌─────────────┐           ┌─────────────┐       │
│  │ CARDIOLOGIST│           │ENDOCRINOLOG │           │  MSK / PT   │       │
│  │     AI      │           │     AI      │           │     AI      │       │
│  │             │           │             │           │             │       │
│  │ CV System   │           │ Metabolic   │           │ MSK System  │       │
│  │ BP, Lipids  │           │ Glucose     │           │ Strength    │       │
│  │ Zone 2 cardio│          │ Nutrition   │           │ Balance     │       │
│  └─────────────┘           └─────────────┘           └─────────────┘       │
│         │                          │                          │             │
│         └──────────────────────────┼──────────────────────────┘             │
│                                    │                                         │
│                         ┌──────────▼──────────┐                             │
│                         │   PCP AI            │                             │
│                         │   (Synthesizer)     │                             │
│                         │   - Resolve conflicts│                            │
│                         │   - Prioritize       │                            │
│                         │   - Apply 3-card limit│                           │
│                         └──────────┬──────────┘                             │
│                                    │                                         │
│                         ┌──────────▼──────────┐                             │
│                         │   UNIFIED CARE PLAN │                             │
│                         └─────────────────────┘                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Specialist Agent Domains

| Agent | Health Systems | Lifestyle Pillars | Card Types Owned |
|-------|---------------|-------------------|------------------|
| **Cardiologist AI** | CV Structure/Function/Risk | Movement (Zone 2) | CV meds, cardiac testing, cardiac rehab |
| **Endocrinologist AI** | Metabolic S/F/R | Nutrition | DM meds, thyroid, metabolic testing |
| **Neurologist AI** | Neuro S/F/R | Mind-Body, Sleep | Neuro meds, cognitive cards |
| **Pulmonologist AI** | Respiratory S/F/R | — | Resp meds, pulm testing, resp DME |
| **Nephrologist AI** | Filtration S/F/R | Nutrition (renal) | Renal meds, kidney testing |
| **MSK/PT AI** | MSK S/F/R | Movement, Recovery | PT cards, MSK meds, mobility DME |
| **Immunologist AI** | Immune S/F/R | — | Immune meds, vaccinations |
| **OB-GYN/Uro AI** | Reproductive S/F/R | — | Hormone meds, screening |
| **Nutritionist AI** | — | Nutrition Pillar | All 102 nutrition cards |
| **Exercise Physiology AI** | — | Movement Pillar | All 150 movement cards |
| **Sleep Medicine AI** | — | Sleep, Recovery | Sleep + recovery cards |
| **Mental Health AI** | Neuro (mood) | Mind-Body | Psych meds, mind-body cards |
| **Pharmacist AI** | All (safety) | — | Drug interactions, optimization |

### Selection Priority: Clinical Intent

```yaml
clinical_intent_hierarchy:
  1_stabilize:  # Highest priority - reduce volatility
    description: "Address acute/unstable issues first"
    examples: ["BP spikes", "glucose out of control", "severe pain", "falls risk"]

  2_restore:    # Second priority - rebuild capacity
    description: "Rebuild lost function"
    examples: ["deconditioning", "post-illness", "strength loss"]

  3_protect:    # Third priority - reduce future risk
    description: "Prevent future problems"
    examples: ["CV risk reduction", "cancer screening", "osteoporosis prevention"]

  4_optimize:   # Lowest priority - only when stable
    description: "Enhance beyond baseline"
    examples: ["performance", "longevity", "biohacking"]

  rule: "Never optimize before stabilized. Never protect before restored (mostly)."
```

---

## PATIENT VISIBILITY ARCHITECTURE

### Progressive Disclosure Model

Patients see their care plan at three levels of detail:

```
LEVEL 1: DAILY FOCUS (Default View)
════════════════════════════════════
"Here's what to do today"
• 1-3 active behavioral cards
• Today's medications
• One tap to see more

                    ↓ One tap

LEVEL 2: QUARTERLY VIEW
════════════════════════════════════
"Here's this quarter's focus"
• Current quarter's 6-8 active cards
• Quarter theme and milestones
• Preview of upcoming quarters

                    ↓ One tap

LEVEL 3: FULL CARE PLAN
════════════════════════════════════
"Here's your complete 12-month plan"
• All cards (Active, Queued, Completed)
• Health Matrix visualization
• Goals and success metrics
• Full roadmap
```

### Example Screens

**Level 1: Daily Focus**
```
┌─────────────────────────────────────────────────────────────────┐
│  Good morning, Margaret! Here's your focus for today:          │
│                                                                 │
│  💊 MEDICATIONS                                                 │
│  ├─ ☐ Lisinopril 10mg - Take with breakfast                   │
│  ├─ ☐ Atorvastatin 20mg - Take with dinner                    │
│  └─ ☐ Vitamin D 2000IU - Take with breakfast                  │
│                                                                 │
│  🚶 TODAY'S ACTION                                              │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Morning Walk - 20 minutes                               │   │
│  │  Why now: Your BP responds best to morning movement.    │   │
│  │  🔥 12-day streak!                                       │   │
│  │                                                          │   │
│  │  [MARK DONE]  [I'LL DO IT LATER]                        │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Tomorrow: Strength Training Day                                │
│                                                                 │
│  ──────────────────────────────────────────────────────────────│
│  [SEE MY CARE PLAN]    [I'M STRUGGLING]    [TALK TO TEAM]      │
└─────────────────────────────────────────────────────────────────┘
```

**Level 2: Quarterly View**
```
┌─────────────────────────────────────────────────────────────────┐
│  Q1: FOUNDATION (Current)                                       │
│  ─────────────────────────                                      │
│  Theme: "Build base strength, stabilize blood pressure"        │
│                                                                 │
│  ACTIVE CARDS THIS QUARTER:                                     │
│  ├─ 💊 Lisinopril 10mg → Protecting your heart & kidneys       │
│  ├─ 💊 Atorvastatin 20mg → Lowering heart attack risk          │
│  ├─ 💊 Vitamin D 2000IU → Supporting bones & immune            │
│  ├─ 🚶 Morning Walk 20min → Building cardiovascular base       │
│  ├─ 🏋️ Strength Training 2x → Preventing falls                 │
│  └─ 😴 Sleep Hygiene → Recovery & brain health                 │
│                                                                 │
│  Q1 MILESTONES:                                                 │
│  ☑ Week 2: First strength session completed                    │
│  ☑ Week 4: Walking 20 min without stopping                     │
│  ☐ Week 8: BP stable < 130/80                                  │
│  ☐ Week 12: Sit-to-stand improved 7 → 10 reps                  │
│                                                                 │
│  ──────────────────────────────────────────────────────────────│
│  Q2 PREVIEW: BUILD                                              │
│  "Add balance training, increase protein"                       │
│  Cards unlocking: Balance Practice, Protein Target              │
│                                                                 │
│  [VIEW FULL CARE PLAN]                                          │
└─────────────────────────────────────────────────────────────────┘
```

**Level 3: Full Care Plan**
```
┌─────────────────────────────────────────────────────────────────┐
│  YOUR COMPLETE 12-MONTH CARE PLAN                               │
│                                                                 │
│  GOAL: "Stay independent at home as I age"                     │
│  Life Stage: Older Adulthood (65-79)                           │
│  Priority: Musculoskeletal 🔴, Cardiovascular 🟠               │
│                                                                 │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │  HEALTH MATRIX (8 Systems × 3 Domains)                   │  │
│  │  [Traffic light visualization]                           │  │
│  └──────────────────────────────────────────────────────────┘  │
│                                                                 │
│  YOUR COMPLETE CARD DECK:                                       │
│                                                                 │
│  MEDICATIONS (4 cards)           LIFESTYLE (12 cards)          │
│  ├─ Lisinopril ✓ Active          ├─ Morning Walk ✓ Active     │
│  ├─ Atorvastatin ✓ Active        ├─ Strength 2x/wk ✓ Active   │
│  ├─ Vitamin D ✓ Active           ├─ Balance ○ Q2              │
│  └─ Calcium ○ Q2                 ├─ Sleep Hygiene ✓ Active    │
│                                   ├─ Protein Target ○ Q2       │
│  DIAGNOSTICS (3 cards)           └─ ... (7 more)               │
│  ├─ DEXA Scan ✓ Completed                                      │
│  ├─ Lipid Panel ○ Month 3                                      │
│  └─ A1c ○ Month 3                                              │
│                                                                 │
│  TOTAL: 19 cards | Active: 6 | Upcoming: 10 | Completed: 3    │
│                                                                 │
│  [DOWNLOAD PDF]  [SHARE WITH FAMILY]  [TALK TO TEAM]           │
└─────────────────────────────────────────────────────────────────┘
```

---

## 90/10 SELF-DIRECTED MODEL

### Decision Tier Distribution

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        90/10 SELF-DIRECTED MODEL                             │
│                                                                              │
│  TIER 1: PATIENT + AI AUTONOMOUS (65%)                                      │
│  ██████████████████████████████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░  │
│  • All behavioral cards (start, adjust, stop, graduate)                     │
│  • Pre-authorized medication titrations                                      │
│  • Standing order labs                                                       │
│  • Deck building from approved cards                                         │
│  → Patient action = Immediate effect                                        │
│                                                                              │
│  TIER 2: PATIENT + AI + ALLIED HEALTH (25%)                                 │
│  █████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  │
│  • OTC/supplement requests                                                   │
│  • Complex nutrition (dietitian review)                                      │
│  • Post-injury exercise (PT review)                                          │
│  • Medication questions (pharmacist)                                         │
│  → Patient request + AI + Allied health = 4-24 hour turnaround             │
│                                                                              │
│  TIER 3: PHYSICIAN REQUIRED (10%)                                           │
│  ████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  │
│  • New prescriptions                                                         │
│  • Complex multi-morbidity                                                   │
│  • Treatment failures                                                        │
│  • Safety events                                                             │
│  → Patient request + AI summary + Clinician decision                        │
│                                                                              │
│  GOAL: 90% of patient actions happen immediately or within hours.          │
│        Clinicians focus on complex 10%, not routine care.                   │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Pre-Authorization Framework

Clinicians can pre-authorize patient actions to increase autonomy:

```yaml
pre_authorization_examples:

  medication_titration:
    patient: "Margaret Johnson"
    medication: "Lisinopril"
    authorized_range: "10mg to 40mg"
    increment: "10mg per week"
    conditions:
      - "No severe hypotension (<90/60)"
      - "No hyperkalemia (K+ < 5.5)"
      - "BP not at goal (<130/80)"
    patient_can: "Increase dose by 10mg after 1 week if tolerating well"
    clinician_notified: "async, weekly summary"

  standing_lab_orders:
    patient: "Margaret Johnson"
    tests: [A1c, lipid_panel, CMP]
    frequency: "quarterly"
    patient_can: "Schedule lab anytime within ±2 weeks of due date"
    auto_order: true

  formulation_switch:
    patient: "Margaret Johnson"
    from: "Metformin IR"
    to: "Metformin ER"
    trigger: "GI symptoms > 2 weeks despite taking with food"
    patient_can: "Request pharmacy switch (same daily dose)"
    clinician_notified: true
```

---

## CARD ORGANIZATION WITHIN CARE PLAN

### Temporal Organization

| Interval | Card Types | Examples |
|----------|-----------|----------|
| **Daily** | Medications, Micro-habits | Take Metformin, 10-min walk, gratitude journaling |
| **Weekly** | Structured activities | Strength training 2x, Meal prep Sunday |
| **Monthly** | Monitoring, Check-ins | Weight log, BP average review, symptom assessment |
| **Quarterly** | Assessments, Adjustments | Lab work, Care plan review, Goal check |
| **Annually** | Comprehensive | Full assessment, Screenings, New care plan |
| **As Needed** | Acute response | PRN medications, Symptom-triggered cards |

### Clinical Intent Organization

| Category | Purpose | Example Cards |
|----------|---------|---------------|
| **Prevention** | Stop problems before they start | Screenings, Vaccines, Risk-reduction behaviors |
| **Maintenance** | Keep stable what's working | Chronic medications, Established habits |
| **Enhancement** | Improve capacity beyond baseline | Progressive exercise, Optimization cards |
| **Treatment** | Address active problems | Acute medications, Therapeutic interventions |

### Status Categories

```yaml
card_statuses:
  active:
    description: "Currently assigned and executing"
    display: "✓ Active"
    color: green

  queued:
    description: "Planned for future quarter"
    display: "○ Q2/Q3/Q4"
    color: gray
    unlock_criteria: "Adherence ≥70% in previous quarter"

  paused:
    description: "Temporarily on hold"
    display: "⏸ Paused"
    color: yellow
    max_duration: "30 days"

  completed:
    description: "Goal achieved, graduated"
    display: "🎓 Completed"
    color: blue

  discontinued:
    description: "Stopped (not needed or patient preference)"
    display: "✗ Discontinued"
    color: gray
```

---

## INTEGRATION WITH EXISTING ARCHITECTURE

### Connection to 4-Section Workflow

```
SECTION 1: DATA INPUT → Triggers care plan creation/adjustment
SECTION 2: DASHBOARD  → Visualizes care plan status
SECTION 3: SMART CARDS → The building blocks OF care plans
SECTION 4: PHILOSOPHY → Governs care planning methodology
```

### Connection to Universal Card Template

Add to every SMART Card:

```yaml
# === CARE PLAN CONTEXT ===
care_plan_context:
  plan_types: [chronic, subacute, acute]  # Which plans can contain this card

  chronic_placement:
    interval: daily                        # daily/weekly/monthly/quarterly/annual
    category: treatment                    # prevention/maintenance/enhancement/treatment
    typical_quarter: Q1                    # When usually activated

  clinical_intent: stabilize               # stabilize/restore/protect/optimize

  selection_triggers:
    dashboard_triggers:
      - "cardiovascular_risk > 15%"
      - "BP_systolic > 130 OR BP_diastolic > 80"
    diagnosis_triggers:
      - "I10 - Essential Hypertension"

  graduation_criteria:
    - "BP < 130/80 sustained 3 months"
    - "Adherence ≥ 80% for 90 days"
```

---

## RELATED DOCUMENTS

- [INTEGRATION_ARCHITECTURE.md](INTEGRATION_ARCHITECTURE.md) - 4-Section workflow
- [MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md](MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md) - AI agent ecosystem
- [comprehensive-care-planning-methodology.md](CMO - PERFORMANCE MEDICINE/clinical-protocols/comprehensive-care-planning-methodology.md) - Care planning workflow
- [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) - 12 card types
- [UNIVERSAL_CARD_TEMPLATE.md](CMO - SMART SYSTEM/docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) - Card structure
- [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](CMO - SMART SYSTEM/docs/core/CARD_LIFECYCLE_AND_AI_PARAMETERS.md) - Card phases
- [AUTONOMY_AND_AI_AGENT_SPECIFICATION.md](CMO - SMART SYSTEM/docs/core/AUTONOMY_AND_AI_AGENT_SPECIFICATION.md) - 4-tier autonomy

---

## VERSION HISTORY

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0 | 2025-12-12 | Initial specification based on architecture discussions | Claude |

---

**END OF DOCUMENT**
