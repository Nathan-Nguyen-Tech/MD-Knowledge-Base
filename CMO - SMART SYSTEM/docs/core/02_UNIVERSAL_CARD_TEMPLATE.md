# UNIVERSAL SMART CARD TEMPLATE

**Version:** 0.5
**Updated:** 2025-12-13
**Status:** Pre-release (v1.0 = first production deployment)

**Related Documents:**
- [CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md](../../../CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md) - 3 Care Plan Types, 90/10 Model
- [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](CARD_LIFECYCLE_AND_AI_PARAMETERS.md) - AI bracket notation & lifecycle phases
- [CARD_TYPE_SPECIFICATIONS.md](03_CARD_TYPE_SPECIFICATIONS.md) - 12 card type details
- [AUTONOMY_AND_AI_AGENT_SPECIFICATION.md](AUTONOMY_AND_AI_AGENT_SPECIFICATION.md) - 4-tier autonomy system
- [EVIDENCE_SECTION_SPECIFICATION.md](EVIDENCE_SECTION_SPECIFICATION.md) - Evidence grading A/B/C
- [CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md](../../CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md) - Exit criteria

**Reference Implementation:** [MED_DM_BIG_001_Metformin_IR.md](../../tier5_cards/medications/MED_DM_BIG_001_Metformin_IR.md)

---

## Template Philosophy

### Audience-Specific Sections

| Section | Primary Audience | Purpose |
|---------|------------------|---------|
| **AT-A-GLANCE** | Patient | 20-second quick reference for everyday use |
| **CONDENSED VIEW** | Patient | Everyday essentials; what patients need to know |
| **EXPANDED VIEW** | Patient | Deep-dive information; clinicians guide patients using THIS language |
| **EVIDENCE** | Patient | Brief trust-builder; authoritative sources (not detailed) |
| **CLINICIAN & AI REFERENCE** | Clinician + AI | Like UpToDate/OpenEvidence; medical encyclopedia for clinical decisions |
| **AI METADATA** | AI Systems | Machine-readable YAML for automated processing |

### Key Principles

1. **Patient-Centered Language**: The Condensed and Expanded Views use patient-friendly language. Clinicians read these sections to understand HOW to guide patients in language patients understand.

2. **Clinicians as Guidance Counselors**: In patient views, clinicians are not making clinical decisions—they're helping patients understand and follow through. Clinical decision-making happens in the Clinician & AI Reference section.

3. **Evidence for Trust**: The Evidence section is brief and authoritative. It answers "Why should I trust this?" not "What are all the studies?" Detailed evidence goes in the Clinician Reference.

4. **AI Reference = Medical Encyclopedia**: The Clinician & AI Reference section is like a condensed UpToDate page—comprehensive clinical information for clinician decision-making, with AI-readable YAML underneath.

---

## Template Structure

```
1. AT-A-GLANCE (20 seconds)      ← Patient: Quick mobile reference
2. CONDENSED VIEW                ← Patient: Everyday use
3. EXPANDED VIEW                 ← Patient: Deep dive (clinicians guide in this language)
4. EVIDENCE                      ← Patient: Trust-building (brief, authoritative)
5. CLINICIAN & AI REFERENCE      ← Clinician: Medical encyclopedia + AI YAML
```

### Care Plan Integration

**Cards exist within Care Plans**, not in isolation:
- **Chronic Care Plan**: Long-term cards organized by quarter
- **Subacute Overlay**: Temporary cards for emerging issues
- **Acute Overlay**: Emergency cards (may pause non-essential cards)

**Card Selection by Multi-Specialty AI**:
- 14 specialist agents query card library
- PCP AI orchestrates and resolves conflicts
- Clinical Intent Hierarchy: Stabilize → Restore → Protect → Optimize
- Maximum 3 active behavioral cards at any time

---

# 📱 AT-A-GLANCE (20 seconds)

> Ultra-condensed quick reference. Fits on one mobile screen. Patients use this daily.

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

> Your everyday quick guide. 6th-8th grade reading level.

## WHAT YOU'RE DOING
[Simple action statement - 1 sentence]

## WHY THIS MATTERS
**Your goal:** [Your own words - what you want to achieve]

**Why this [medication/action]:** [1-2 sentence rationale in plain language]

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
*Only increase when you're tolerating well.*

## WHAT TO WATCH FOR

| Level | Signs | What to Do |
|-------|-------|------------|
| 🟡 Normal | [Expected early effects] | [Wait X time - this improves] |
| 🟠 Call us | [Warning signs] | [Schedule a visit] |
| 🔴 Emergency | [Critical symptoms] | Call 911 |

## CHECK-INS

| When | What We'll Ask |
|------|----------------|
| [Day X] | [Question in patient-friendly language] |
| [Day Y] | [Question] |
| [Month X] | [Assessment] |

## HOW OTHERS ARE DOING
⭐ [X.X]/5 rating | [X]% still doing at [timeframe] | [X]% reached their goal

---

# 📋 EXPANDED VIEW

> Everything you might want to know. Your care team uses this same information to guide you.

---

## UNDERSTANDING YOUR [MEDICATION/INTERVENTION]

**What is [Name]?**
[2-3 sentence explanation in plain language]

**How does it work?**
[Mechanism explained simply - what happens in your body]
1. [Action 1]
2. [Action 2]
3. [Action 3]

**What makes it special?**
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

---

## YOUR [DOSING/ACTION] SCHEDULE

| Form | Options |
|------|---------|
| [Type 1] | [Options] |
| [Type 2] | [Options] |

**Your schedule:** [Frequency and timing]
**Why [timing requirement]?** [Simple explanation]

**If you miss a [dose/session]:** [Recovery instruction]

---

## WHAT TO EXPECT

### First [Time Period] (Getting Started)
[What commonly happens early on - normalize the experience]
- [Common experience 1]
- [Common experience 2]
- [Common experience 3]

**These typically improve by [timeframe].** If they don't, we have solutions.

### After [Time Period]
- [Expected improvement 1]
- [Expected improvement 2]
- [Expected improvement 3]

### Long-Term Benefits
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

---

## MONITORING & [LABS/TRACKING]

| Test/Metric | How Often | Why |
|-------------|-----------|-----|
| [Metric 1] | [Frequency] | [Simple explanation] |
| [Metric 2] | [Frequency] | [Simple explanation] |
| [Metric 3] | [Frequency] | [Simple explanation] |

**Your target:** [Goal in patient-friendly terms]

---

## WHEN TO PAUSE [OR HOLD]

There are specific times when you should temporarily stop:

| Situation | What to Do |
|-----------|------------|
| [Situation 1] | [Action] |
| [Situation 2] | [Action] |
| [Situation 3] | [Action] |

**When in doubt, call us.** You can always restart when the situation resolves.

---

## LIFESTYLE & INTERACTIONS

**Food:** [Guidance]

**Alcohol:** [Guidance]

**Other things to know:**
- [Interaction/consideration 1]
- [Interaction/consideration 2]

---

## COMMON QUESTIONS

**"[Common question 1]?"**
[Answer in patient-friendly language]

**"[Common question 2]?"**
[Answer]

**"[Common question 3]?"**
[Answer]

**"[Common question 4]?"**
[Answer]

---

## WHEN TO REACH OUT

**Schedule a visit for:**
- [Reason 1]
- [Reason 2]
- [Reason 3]

**Seek immediate care for:**
- [Emergency sign 1]
- [Emergency sign 2]
- [Emergency sign 3]

---

## YOUR PROGRESS TRACKER

**Your starting [metric]:** _____ | **Date started:** _____

**Milestones:**
- [ ] [Milestone 1]
- [ ] [Milestone 2]
- [ ] [Milestone 3]
- [ ] [Milestone 4]

---

# 📚 EVIDENCE

> Why you can trust this recommendation.

**Bottom line:** [One sentence summary of why this is trustworthy]

| Source | What They Say |
|--------|---------------|
| **[Authoritative Body 1]** | "[Key recommendation quote]" |
| **[Years of Use/Data]** | [Trust-building fact] |
| **[Major Trials]** | [Key outcome in patient terms] |

**Evidence Grade: [A/B/C]** ([Strongest/Good/Limited])

---

# 🏥 CLINICIAN & AI REFERENCE

> Clinical decision support for care teams. AI-readable specifications below.

---

## CLINICAL SUMMARY

### Overview
[1-2 paragraph clinical summary as would appear in UpToDate or OpenEvidence. Include mechanism, indications, key clinical pearls.]

### Key Clinical Points
- **[Point 1]:** [Value/detail]
- **[Point 2]:** [Value/detail]
- **[Point 3]:** [Value/detail]
- **[Point 4]:** [Value/detail]
- **[Point 5]:** [Value/detail]

### Contraindications
- [Contraindication 1]
- [Contraindication 2]
- [Contraindication 3]
- [Contraindication 4]

### [Dosing Adjustments / Special Populations]
| [Factor] | Recommendation |
|----------|----------------|
| [Condition 1] | [Adjustment] |
| [Condition 2] | [Adjustment] |
| [Condition 3] | [Adjustment] |
| [Condition 4] | [Adjustment] |

### Common Drug Interactions / Considerations
| Agent | Severity | Management |
|-------|----------|------------|
| [Item 1] | [High/Moderate/Low] | [Action] |
| [Item 2] | [Severity] | [Action] |
| [Item 3] | [Severity] | [Action] |

### Monitoring Protocol
| Parameter | Frequency |
|-----------|-----------|
| [Metric 1] | [Schedule] |
| [Metric 2] | [Schedule] |
| [Metric 3] | [Schedule] |

### Treatment Failure Considerations
If [goal not met] after [timeframe]:
- **With [condition A]:** [Recommendation]
- **With [condition B]:** [Recommendation]
- **With [condition C]:** [Recommendation]

### Evidence Base
| Study | Design | Key Finding |
|-------|--------|-------------|
| [Study 1] | [Design] | [Finding] |
| [Study 2] | [Design] | [Finding] |
| [Study 3] | [Design] | [Finding] |

**Evidence gaps:** [Known limitations in the evidence]

### Feasibility Score: [X]/100

| Factor | Points |
|--------|--------|
| Baseline | 100 |
| [Deduction 1] | -X |
| [Deduction 2] | -X |
| [Booster 1] | +X |
| [Booster 2] | +X |

### Patient Confidence Assessment
Ask at prescribing: "On a scale of 0-10, how confident are you that you can [action]?"

| Score | Interpretation | Action |
|-------|----------------|--------|
| 8-10 | High confidence | Proceed with standard initiation |
| 5-7 | Moderate confidence | Explore barriers, consider additional support |
| 0-4 | Low confidence | Address barriers before starting |

---

## AI METADATA

<!--
AI-readable specifications for automated processing.
Clinicians: The above reference section summarizes this data in readable format.
-->

```yaml
# === IDENTIFIERS ===
card_id: [CARD_ID]
generic: [Generic name]
brand: [Brand name if applicable]
class: [Class/Category]
path: [Hierarchy > Path > To > Card]

# === CARE PLAN CONTEXT ===
care_plan:
  typical_plan_type: [chronic|subacute|acute]
  clinical_intent: [stabilize|restore|protect|optimize]
  time_interval: [daily|weekly|monthly|quarterly|annually]
  specialist_owner: [Specialist_AI_Agent]  # e.g., Cardiologist_AI, Nutritionist_AI
  max_concurrent_behavioral: 3  # 3-card rule for behavioral cards

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

### Version History
| Version | Date | Changes |
|---------|------|---------|
| 0.5 | 2025-12-13 | Major restructure: Clarified audience for each section (Patient vs Clinician vs AI); replaced NOTES with CLINICIAN & AI REFERENCE; condensed Evidence for patients |
| 0.4 | 2025-12-12 | Added care_plan context block, Care Plan Integration section |
| 0.3 | 2025-12-08 | Added AT-A-GLANCE quick card, visual dose ladder, decision pathway |
| 0.2 | 2025-12-07 | Converted to tables, added Evidence section structure |
| 0.1 | 2024-11-23 | Initial template structure |

**Note:** v1.0 will be assigned at first production deployment with real patients.

---

## Template Usage Guidelines

### For Card Authors:
1. Start with the AT-A-GLANCE - if it doesn't fit in 20 seconds, the card is too complex
2. Write Condensed and Expanded views in patient-friendly language (6th-8th grade)
3. Keep Evidence brief - just enough to build trust, not a literature review
4. Put detailed clinical information in Clinician & AI Reference
5. Specify which Care Plan Type and Clinical Intent this card serves
6. Use tables over paragraphs for scannability

### For AI Agents:
- Parse YAML metadata for decision-making
- Respect autonomy tier for patient actions
- Use checkins schedule for proactive outreach
- Reference alerts for safety monitoring
- Follow lifecycle for de-loading decisions
- Check `care_plan.specialist_owner` to route to correct specialist agent
- Apply `clinical_intent` hierarchy when selecting cards

### For Clinicians:
- **Patient Views (Condensed/Expanded):** Read these to understand how to guide patients in their language
- **Evidence:** Use to answer patient questions about trustworthiness
- **Clinician & AI Reference:** Use for clinical decision-making (like UpToDate)
- Feasibility Score and Patient Confidence Assessment guide prescribing decisions
- See CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md for care plan organization

---

*Template: Universal Card Template v0.5*
*Reference: MED_DM_BIG_001_Metformin_IR.md*
