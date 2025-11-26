# Claude Code Instructions for SMART Card Library Project

> **Version**: 2.0 | **Last Updated**: 2024-11-23
>
> **IMPORTANT**: Always read `CHANGELOG.md` first for the latest project state and decisions.

---

## Project Context

This is the **SMART Card Library System** - a comprehensive, evidence-based health action platform that transforms traditional patient education into actionable, trackable interventions.

**Current Phase**: Phase 1 Foundation (90% complete) → Moving to Phase 2 Content Creation

---

## Key Project Files (Read Order)

1. **CHANGELOG.md** - READ FIRST - Current state, recent decisions, what needs work
2. **PROJECT_INSTRUCTIONS.md** - Complete project guide, goals, and roadmap
3. **docs/core/02_UNIVERSAL_CARD_TEMPLATE.md** - THE source of truth for card structure
4. **docs/core/03_CARD_TYPE_SPECIFICATIONS.md** - Type-specific guidance (12 types)
5. **docs/core/04_VALIDATION_CHECKLIST.md** - Quality assurance checklist
6. **docs/core/05_EXAMPLE_SMART_CARDS.md** - Reference examples

---

## 12 Card Types (v2.0 - Current)

| # | Card Type | Icon | Tier 1 | Rx Required |
|---|-----------|------|--------|-------------|
| 1 | Medications | 💊 | Medical | Yes |
| 2 | Diagnostic Testing | 🔬 | Medical | Yes |
| 3 | Imaging Studies | 🏥 | Medical | Yes |
| 4 | Procedures | 🔧 | Medical | Yes |
| 5 | Durable Medical Equipment (DME) | 🩺 | Medical | Yes |
| 6 | Referrals | 👨‍⚕️ | Medical | Yes |
| 7 | Nutrition | 🥗 | Behavioral | No |
| 8 | Movement/Exercise | 🏃 | Behavioral | No |
| 9 | Recovery | 😴 | Behavioral | No |
| 10 | Mind-Body Practices | 🧘 | Behavioral | No |
| 11 | Environmental & Social Health | 🌍 | Behavioral | No |
| 12 | Micro-Learning | 📚 | Behavioral | No |

---

## Core Principles (ALWAYS Follow)

1. **ONE ACTION PER CARD** - Never combine multiple actions
2. **6th-8th GRADE READING LEVEL** - Patient-facing content must be simple
3. **EVIDENCE-BASED** - All cards must have citations and grades (A/B/C)
4. **UNIVERSAL TEMPLATE** - Follow WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY-FOLLOW-UP-NOTES
5. **PERFORMANCE MEDICINE FRAMEWORK** - Link all clinical goals to 8 health systems and 3 domains
6. **TAG COMPREHENSIVELY** - Apply 5-10 tags minimum
7. **SAFETY BY HEALTH SYSTEMS** - Organize warnings with Yellow/Orange/Red tiers
8. **EDUCATION EMBEDDED** - No standalone educational cards; education is in action cards

---

## Performance Medicine Framework

### 8 Health Systems
1. Neurological (including mental health)
2. Cardiovascular
3. Respiratory
4. Metabolic (including digestive)
5. Filtration/Urinary
6. Musculoskeletal
7. Immune (inflammatory, infectious, oncology)
8. Reproduction (including hormones)

### 3 Domains
- **Structure**: Anatomy, tissue integrity
- **Function**: Physiological performance
- **Risk**: Disease prevention, risk reduction

### Clinical Goal Format
`[System] System: [Action Verb] [Domain]`

**Examples**:
- "Cardiovascular System: Reduce Risk"
- "Metabolic System: Improve Function"
- "Musculoskeletal System: Restore Structure"

---

## Required Card Structure

### Patient-Facing View (6th-8th Grade)
- WHAT YOU'RE DOING - 1 sentence, simple action
- WHY THIS MATTERS TO YOU - Patient's personal goal
- HOW TO DO IT - 3-5 bullet points, active voice
- WHEN TO DO IT - Frequency | Timeline to benefit
- WHAT TO WATCH FOR - Top 2-3 red flags only

### Full Clinical View
- WHAT - Complete detailed action/prescription
- WHO - Target population + special considerations
- WHEN - Frequency, duration, timing, progression tiers
- WHERE - Setting, location-specific instructions
- WHY - Clinical goal, patient goal, mechanism, evidence, timeline
- HOW - Detailed protocol, synergy tips
- MEASURE - Tracking method, frequency, tools
- TARGET - Specific goal values, timeline, success criteria
- SAFETY - Organized by health systems (Yellow/Orange/Red)
- FOLLOW-UP - Review timeline, checkpoints, action based on results
- NOTES - Evidence, feasibility score, barriers, community feedback

### Metadata (Required)
- Tags: 5-10 tags from multiple categories
- Evidence Grade: A/B/C
- Feasibility Score: 0-100% with calculation
- Version: vX.X
- Last Updated: Date

---

## Safety Section Format (Required)

**Yellow - Common Side Effects** (Monitor, usually can continue):
- Effect 1 with percentage
- Effect 2 with percentage

**Orange - Stop/Hold & Contact Care Team If**:
- Cardiovascular Signs: specifics
- Respiratory Signs: specifics
- Other relevant systems

**Red - Emergency - Call 911 Immediately**:
- Loss of consciousness
- Chest pain with shortness of breath
- Severe allergic reaction (tongue/throat swelling)
- Other emergencies

---

## Library Hierarchy (5 Tiers)

Tier 1: Medical vs Behavioral (2 categories)
  Tier 2: Card Type (12 types listed above)
    Tier 3: Subcategory (e.g., Cardiovascular_Medications)
      Tier 4: Specific Category (e.g., ACE Inhibitors)
        Tier 5: Individual Card (e.g., Lisinopril 10mg)

### Tag Categories (Apply 5-10 per card)
1. Clinical Intent (#PreventiveCare, #ChronicManagement, #AcuteTreatment)
2. Guidelines (#USPSTF_GradeA, #ACC_AHA, #ADA, #KDIGO)
3. Care Setting (#Home, #Outpatient, #Telehealth, #Hospital)
4. Population (#Adult, #Geriatric, #Pediatric, #Pregnancy)
5. Condition (#Hypertension, #Diabetes, #HeartFailure)
6. Organ System (#Cardiology, #Metabolic, #Pulmonary)
7. Community (#Easy, #Affordable, #WorkedForMe)

---

## Quick Validation Checklist

Before finalizing ANY card:
- [ ] All sections complete (Patient + Clinical + Metadata)?
- [ ] Patient-facing is 6th-8th grade?
- [ ] Clinical goal mapped to 8 Systems + Domain?
- [ ] Evidence grade assigned (A/B/C)?
- [ ] Safety organized by health systems (Yellow/Orange/Red)?
- [ ] At least 5 tags applied?
- [ ] Feasibility score calculated with breakdown?
- [ ] Action is clear and measurable?
- [ ] Emergency criteria specified?

---

## Feasibility Score Calculation

**Base Score**: 100%

**Deductions**:
- No insurance coverage: -25%
- High cost (>$100/month): -20%
- Requires equipment patient lacks: -15%
- Transportation barriers: -15%
- Time intensive (>30 min/day): -10%
- Complex instructions (>5 steps): -10%
- Language barriers: -15%
- Contraindication/allergy: -100% (Card not offered)

**Additions**:
- Patient specifically requested: +20%
- Previously succeeded with similar: +15%
- Low time burden (<10 min/day): +10%
- Free or fully covered: +10%
- Can do at home: +10%
- Strong social support: +10%

**Interpretation**:
- 90-100%: Highly feasible - recommend strongly
- 70-89%: Feasible with support
- 50-69%: Challenging - need barrier mitigation
- <50%: Low feasibility - consider alternatives

---

## Statistics

- **Total Cards**: ~1,000
- **Medical Cards**: ~580
- **Behavioral Cards**: ~391
- **Card Types**: 12
- **Pre-Built Decks**: 17+
- **Tier Levels**: 5
- **Tag Categories**: 7+

---

## DO / DON'T

### DO:
- Read CHANGELOG.md first each session
- Use universal template for ALL cards
- Apply 5-10 tags minimum
- Write patient content at 6th-8th grade
- Include evidence citations and grades
- Organize safety by health systems with color tiers
- Calculate feasibility scores
- Keep ONE action per card

### DON'T:
- Create standalone "educational cards" (education is embedded)
- Combine multiple actions in one card
- Use medical jargon in patient-facing content
- Skip evidence citations
- Forget tags or feasibility scores
- Use old 10-card-type references (now 12 types)
- Skip the safety color tiers (Yellow/Orange/Red)

---

## Remember

This system transforms healthcare from **"here's information"** to **"here's what to do, and here's why."**

Every card must be:
- **Actionable** (ONE clear action)
- **Measurable** (trackable outcomes)
- **Evidence-based** (graded A/B/C)
- **Accessible** (6th-8th grade language)
- **Safe** (organized by health systems with escalation tiers)

---

*Version 2.0 | Last Updated: 2024-11-23*
