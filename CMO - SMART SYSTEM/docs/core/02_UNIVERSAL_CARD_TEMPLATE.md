# UNIVERSAL SMART CARD TEMPLATE

**Version:** 4.0
**Updated:** 2025-12-08

**Related Documents:**
- [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](CARD_LIFECYCLE_AND_AI_PARAMETERS.md) - AI bracket notation & lifecycle phases
- [CARD_TYPE_SPECIFICATIONS.md](03_CARD_TYPE_SPECIFICATIONS.md) - 12 card type details
- [AUTONOMY_AND_AI_AGENT_SPECIFICATION.md](AUTONOMY_AND_AI_AGENT_SPECIFICATION.md) - 4-tier autonomy system
- [EVIDENCE_SECTION_SPECIFICATION.md](EVIDENCE_SECTION_SPECIFICATION.md) - Evidence grading A/B/C
- [CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md](../../CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md) - Exit criteria

**Reference Implementation:** [MED_DM_BIG_001_Metformin_IR.md](../../tier5_cards/medications/MED_DM_BIG_001_Metformin_IR.md)

---

## Template Structure (v4.0)

Every SMART Card follows this architecture:

```
1. AT-A-GLANCE (20 seconds)   ← NEW in v4.0
2. CONDENSED VIEW             ← Patient everyday use
3. EXPANDED VIEW              ← Full details for all users
4. EVIDENCE                   ← Trust-building citations
5. NOTES                      ← Clinician reference
6. AI METADATA (hidden)       ← Machine-readable YAML
```

---

# 📱 AT-A-GLANCE (20 seconds)

> Ultra-condensed quick reference. Fits on one mobile screen.

```
[CARD NAME] | [DOSE/ACTION] | [FREQUENCY] | [KEY REQUIREMENT]
─────────────────────────────────────────────────────────────
[Action line 1]
[Action line 2]

[Visual progression ladder if titratable]
🟢 [Starting level]
🟡 [Building level]
🟣 [Target level]

Watch: [Normal early effects]
Stop & call: [Red flags - brief]

Labs/Tracking: [What to measure]
Goal: [Target outcome + timeline]
─────────────────────────────────────────────────────────────
```

**Design Principles:**
- Viewable in <20 seconds
- One-thumb scrollable on mobile
- Color-coded progression
- No scrolling required for essentials

---

# 📱 CONDENSED VIEW

> Essentials for everyday use. 6th-8th grade reading level.

## WHAT YOU'RE DOING
[Simple action statement - 1 sentence]

## WHY THIS MATTERS
**Your goal:** [Patient's own words - captured at intake]

**Why prescribed:** [1-2 sentence clinical rationale in plain language]

**Evidence:** Grade [A/B/C] - [One sentence plain-language summary]

## HOW TO DO IT
1. [Step 1 - action verb, simple language]
2. [Step 2 - specific, measurable]
3. [Step 3 - practical detail]
4. [Step 4 if needed]

**Tip:** [One practical habit anchor]

## DOSE PROGRESSION (if titratable)

```
🟢 [Phase 1] → [Starting dose/level]   (starting)
🟡 [Phase 2] → [Intermediate level]    (building)
🟣 [Phase 3] → [Target level]          (target)
```
*Advance only when tolerating well.*

## WHAT TO WATCH FOR

| Level | Signs | Action |
|-------|-------|--------|
| 🟡 Normal | [Expected early effects] | [Wait X time, improves] |
| 🟠 Call doctor | [Warning signs] | [Schedule visit] |
| 🔴 Emergency | [Critical symptoms] | Call 911 |

## DIFFICULTY
[⭐⭐☆☆☆] **[Easy/Moderate/Hard]** - [Brief descriptor]

## CHECK-INS

| When | What We'll Ask |
|------|----------------|
| [Day X] | [Question] |
| [Day Y] | [Question] |
| [Month X] | [Assessment] |

## COMMUNITY
⭐ [X.X]/5 | [X]% still doing at [timeframe] | [X]% reached their goal

---

# 📋 EXPANDED VIEW

> Full details for clinicians, advanced users, and curious patients.

---

## WHO

| Role | Responsibility |
|------|----------------|
| Patient | [Primary responsibilities] |
| [Role 2] | [Responsibilities] |
| [Role 3] | [Responsibilities] |
| Family | [Support role] |

---

## WHAT

| Field | Value |
|-------|-------|
| [Name field] | [Value] |
| [Class/Type] | [Value] |
| [Starting] | [Value] |
| [Target] | [Value] |
| [Maximum] | [Value] |
| [Form] | [Value] |

---

## WHEN

**Schedule:** [Frequency and timing]
**Duration:** [Ongoing/limited course]
**Missed dose/session:** [Recovery instructions]

---

## WHERE

**Setting:** [Location]
**Storage:** [If applicable]

---

## WHY (Mechanism)

1. **[Action 1]** [description]
2. **[Action 2]** [description]
3. **[Action 3]** [description]

**Benefits:** [Key benefits in plain language]

---

## HOW

**Instructions:**
1. [Detailed step 1]
2. [Detailed step 2]
3. [Detailed step 3]

**If [common issue]:**
- [Solution 1]
- [Solution 2]
- [Escalation if needed]

---

## MEASURE

| Test/Metric | Frequency | Purpose |
|-------------|-----------|---------|
| [Metric 1] | [Frequency] | [Purpose] |
| [Metric 2] | [Frequency] | [Purpose] |
| [Metric 3] | [Frequency] | [Purpose] |

**What you may notice:** [Subjective improvements]

---

## TARGET

| Metric | Goal | Timeline |
|--------|------|----------|
| [Primary] | [Value] | [Timeframe] |
| [Secondary] | [Value] | [Timeframe] |

---

## SAFETY

### Common Side Effects (Temporary)
- [Effect 1] ([percentage])
- [Effect 2]
- [Effect 3]

### Hold/Stop If:
| Situation | Action |
|-----------|--------|
| [Situation 1] | [Action] |
| [Situation 2] | [Action] |

### Interactions:
| Substance | Guidance |
|-----------|----------|
| [Item 1] | [Guidance] |
| [Item 2] | [Guidance] |

---

## DECISION PATHWAY

```
START: [Initial state]
         │
         ▼
    ┌─────────────────────────────────────────┐
    │     [CHECKPOINT]: [Assessment]          │
    └─────────────────────────────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
 [OUTCOME A]  [OUTCOME B]
    │            │
    ▼            ▼
[Action A]   [Action B]
    │
    ▼
    ┌─────────────────────────────────────────┐
    │     ONGOING MONITORING                  │
    └─────────────────────────────────────────┘
    │
    ├── [Trigger 1]? → [Response 1]
    ├── [Trigger 2]? → [Response 2]
    └── [Trigger 3]? → [Response 3]
```

---

## FOLLOW-UP SCHEDULE

### Phase 1: Initiation (Days 1-14)
| Day | Method | Focus |
|-----|--------|-------|
| [X] | [Method] | [Focus] |
| [Y] | [Method] | [Focus] |

### Phase 2: Titration/Building (Weeks 3-12)
| When | Method | Focus |
|------|--------|-------|
| [X] | [Method] | [Focus] |
| [Y] | [Method] | [Focus] |

### Phase 3: Maintenance (Month 4+)
| When | Method | Focus |
|------|--------|-------|
| [X] | [Method] | [Focus] |
| [Y] | [Method] | [Focus] |

---

## IF YOU'RE STRUGGLING

**Missed [short time]?** [Recovery instruction]
**Missed [longer time]?** [Recovery instruction]

### Common Barriers & Solutions

| Barrier | Solution |
|---------|----------|
| [Barrier 1] | [Solution] |
| [Barrier 2] | [Solution] |
| [Barrier 3] | [Solution] |
| [Barrier 4] | [Solution] |

---

## YOUR PROGRESS

**Baseline:** [Metric]: _____ | Date started: _____

**Milestones:**
- [ ] [Milestone 1]
- [ ] [Milestone 2]
- [ ] [Milestone 3]
- [ ] [Milestone 4]

---

## EVIDENCE

### Summary
[2-3 sentence plain-language summary accessible to patients]

### Grade: [A/B/C] ([Strongest/Good/Limited])

### Grading Criteria Met
- [x] [Criterion 1]
- [x] [Criterion 2]
- [x] [Criterion 3]

### Key Studies

| Study | Finding |
|-------|---------|
| **[Study 1]** ([details]) | [Key finding] |
| **[Study 2]** ([details]) | [Key finding] |
| **[Guideline]** | [Recommendation] |

**NNT/NNH:** [If applicable]

### Evidence Gaps
- [Gap 1]
- [Gap 2]

**Last Reviewed:** [Month Year]

*See [EVIDENCE_SECTION_SPECIFICATION.md](EVIDENCE_SECTION_SPECIFICATION.md) for detailed grading criteria.*

---

## NOTES

### Feasibility Score: [X]/100 (Clinician Reference)
| Factor | Impact |
|--------|--------|
| Base | 100 |
| [Deduction 1] | -X |
| [Deduction 2] | -X |
| [Booster 1] | +X |
| [Booster 2] | +X |

### Patient Confidence Assessment
*Ask at prescribing:* "On a scale of 0-10, how confident are you that you can [action] consistently?"

| Score | Interpretation | Action |
|-------|----------------|--------|
| 8-10 | Ready | Proceed |
| 5-7 | Uncertain | Explore barriers |
| 0-4 | Concerned | Address before starting |

### Version History
| Version | Date | Changes |
|---------|------|---------|
| [X.X] | [Date] | [Changes] |

---

# 🔧 AI METADATA

<!--
Hidden from user interface.
Parsed by AI agents for decision-making.
Clinician override via interface dropdown.
-->

```yaml
# === IDENTIFIERS ===
card_id: [CARD_ID]
name: [Name]
class: [Class/Category]
path: [Hierarchy > Path > To > Card]

# === AUTONOMY ===
# See AUTONOMY_AND_AI_AGENT_SPECIFICATION.md for tier definitions
autonomy:
  tier: [1-4]  # 1=Protocol-Approved, 2=AI-Guided, 3=AI-Assisted, 4=Clinician-Directed
  responsible_agent: [AI_Agent_Name]
  specialist_consult: [Specialist_Agent if applicable]
  approval_type: [protocol|batch|individual]
  patient_can_initiate: [true|false]
  patient_can_adjust: [true|false]
  patient_can_pause: [true|false]
  patient_can_discontinue: [true|false]

# === TAGS ===
tags:
  clinical: [tag1, tag2, tag3]
  evidence: [grade_A, guideline_recommended, etc.]
  properties: [oral, BID, chronic, etc.]
  systems: [metabolic, cardiovascular, etc.]

# === RELATED CARDS ===
related:
  alternative: [CARD_ID]  # If this doesn't work
  add_on:
    - [CARD_ID]  # Complementary cards
  synergy:
    - [CARD_ID]  # Cards that enhance effect
  prerequisite: [CARD_ID or none]
  leads_to: [CARD_IDs]  # Next steps if inadequate

# === PARAMETERS (Card-Type Specific) ===
# Include relevant parameters for card type:
# - dosing (medications)
# - frequency/duration/intensity (behavioral)
# - test_details (diagnostic)
# - equipment (DME)

# === CONTRAINDICATIONS ===
contraindications:
  - [condition1]
  - [condition2]

# === ADJUSTMENTS ===
adjustments:
  [factor]:
    - condition: [condition]
      action: [adjustment]

# === HOLD CONDITIONS (if applicable) ===
hold:
  - condition: [condition]
    action: [action]
    auto_resume: [yes|no]

# === INTERACTIONS (if applicable) ===
interactions:
  - item: [item]
    severity: [low|moderate|high]
    action: [action]

# === MONITORING ===
monitoring:
  [metric1]: {initial: [freq], stable: [freq]}
  [metric2]: [frequency]

# === ALERTS ===
alerts:
  efficacy:
    - condition: [condition]
      action: [action]
      urgency: [routine|soon|urgent]
  safety:
    - condition: [condition]
      action: [action]
      urgency: [routine|soon|urgent]
  adherence:
    - condition: [condition]
      action: [action]
      urgency: [routine|soon|urgent]

# === PROACTIVE CHECK-INS ===
checkins:
  initiation:
    - day: [X]
      questions: [question_ids]
      escalate_if: [condition]
  maintenance:
    - interval: [frequency]
      focus: [focus_area]

# === LIFECYCLE ===
lifecycle:
  initiation:
    duration: [timeframe]
    focus: [focus]
    success: [criteria]
  maintenance:
    adherence_target: [percentage]
    review: [schedule]
  de_loading:
    graduation:
      criteria: [criteria]
      action: [action]
    transition:
      criteria: [criteria]
      action: [action]
    discontinue:
      criteria: [criteria]
      action: [action]

# === EVIDENCE (AI Reference) ===
evidence:
  grade: [A|B|C]
  last_reviewed: [YYYY-MM]
  primary_guideline: [guideline_name]
  key_trials: [trial_names]
  evidence_gaps: [gaps]

# === FEASIBILITY ===
feasibility:
  score: [0-100]
  difficulty: [easy|moderate|hard]
  deductions: {factor: -X}
  boosters: {factor: +X}
```

---

**END OF TEMPLATE**

---

## Quick Reference: v4.0 Changes from v3.0

| Section | v3.0 | v4.0 |
|---------|------|------|
| **New: AT-A-GLANCE** | N/A | 20-second quick card with visual dose ladder |
| **CONDENSED VIEW** | Separate sections | Added DOSE PROGRESSION with color coding |
| **EXPANDED VIEW** | Paragraph-heavy | Converted to tables for scannability |
| **New: DECISION PATHWAY** | Buried in FOLLOW-UP | Promoted to visual ASCII flowchart |
| **EVIDENCE** | Verbose citations | Condensed to table + key stats |
| **NOTES** | Inline in EVIDENCE | Separate section with Feasibility breakdown |
| **AI METADATA** | Basic YAML | Complete YAML with autonomy tiers, alerts, lifecycle |

---

## Template Usage Guidelines

### For Card Authors:
1. Start with the AT-A-GLANCE - if it doesn't fit in 20 seconds, the card is too complex
2. Use tables over paragraphs for scannability
3. Color-code progression with 🟢🟡🟣 emoji
4. Include ASCII decision pathway for any titratable card
5. ALWAYS cite evidence with specific studies/NNT

### For AI Agents:
- Parse YAML metadata for decision-making
- Respect autonomy tier for patient actions
- Use checkins schedule for proactive outreach
- Reference alerts for safety monitoring
- Follow lifecycle for de-loading decisions

### For Clinicians:
- NOTES section contains Feasibility Score for prescribing decisions
- Patient Confidence Assessment guides readiness
- Decision Pathway shows escalation triggers
- Evidence section provides citation backup

---

*Template: Universal Card Template v4.0*
*Reference: MED_DM_BIG_001_Metformin_IR.md*
