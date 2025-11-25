# Claude Code Instructions for SMART Card Library Project

## Project Context

This is the **SMART Card Library System** - a comprehensive, evidence-based health action platform that transforms traditional patient education into actionable, trackable interventions.

## Key Project Files

When working on this project, you should be familiar with:

1. **README.md** - Project overview and quick start guide
2. **PROJECT_INSTRUCTIONS.md** - Complete project guide, goals, and roadmap
3. **ARCHITECTURE.md** - Technical architecture and system design
4. **docs/core/** - 6 core documentation files (system overview, templates, specifications, validation, examples, AI workflow)
5. **docs/reference/** - Additional reference documentation (hierarchy, behavioral design, community feedback, deck organization)
6. **library/** - Card library content organized by medical/behavioral categories

## Core Principles (ALWAYS Follow)

When creating or modifying cards:

1. **ONE ACTION PER CARD** - Never combine multiple actions in a single card
2. **6th-8th GRADE READING LEVEL** - Patient-facing content must be simple and accessible
3. **EVIDENCE-BASED** - All cards must have citations and evidence grades (A/B/C)
4. **UNIVERSAL TEMPLATE** - Follow the WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY-FOLLOW-UP-NOTES structure
5. **PERFORMANCE MEDICINE FRAMEWORK** - Link all clinical goals to 8 health systems and 3 domains
6. **TAG COMPREHENSIVELY** - Apply 5-10 tags minimum from multiple categories
7. **SAFETY BY HEALTH SYSTEMS** - Organize safety warnings by body system
8. **EDUCATION EMBEDDED** - No standalone educational cards; education is woven into action cards

## System Architecture Overview

### Library Hierarchy (5 Tiers)
```
Tier 1: Medical vs Behavioral (2 categories)
  Tier 2: Card Type - 10 types (Medication, Lab, Imaging, Procedure, Referral, Nutrition, Movement, Recovery, Mind-Body, Micro-Learning)
    Tier 3: Subcategory (e.g., Cardiovascular_Medications)
      Tier 4: Specific Category (e.g., ACE Inhibitors)
        Tier 5: Individual Card (e.g., Lisinopril 10mg)
```

### Performance Medicine Framework
- **8 Health Systems**: Neurological • Cardiovascular • Respiratory • Metabolic • Filtration/Urinary • Musculoskeletal • Immune • Reproduction
- **3 Domains**: Structure • Function • Risk
- **Example**: "Cardiovascular System: Reduce Risk"

### Tag Categories (Apply 5-10 per card)
1. Clinical Intent (#PreventiveCare, #ChronicManagement)
2. Guidelines (#USPSTF_GradeA, #ACC_AHA, #ADA)
3. Care Setting (#Home, #Outpatient, #Telehealth)
4. Population (#Adult, #Geriatric, #Pediatric)
5. Condition (#Hypertension, #Diabetes)
6. Organ System (#Cardiology, #Metabolic)
7. Community (#Easy, #Affordable, #WorkedForMe)

## Common Tasks & How to Handle Them

### Task: Create a New Card

1. **Identify Card Type** - Which of the 10 types? (Medication, Lab, Nutrition, etc.)
2. **Reference Type Specification** - See [docs/core/03_CARD_TYPE_SPECIFICATIONS.md](docs/core/03_CARD_TYPE_SPECIFICATIONS.md)
3. **Use Universal Template** - See [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md)
4. **Write Patient-Facing Content First** - 6th-8th grade level (WHAT, WHY, HOW, WHEN, WATCH FOR)
5. **Complete Clinical Details** - All sections of universal template
6. **Add Evidence Citations** - Include guideline sources and evidence grade
7. **Calculate Feasibility Score** - Use scoring methodology from template
8. **Apply Comprehensive Tags** - Minimum 5-10 tags
9. **Link to Performance Framework** - Which health system(s) and domain(s)?
10. **Validate** - Use checklist in [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md)

### Task: Create a Condition Deck

1. **Review Deck Organization** - See [docs/reference/10_SMART_DECK_ORGANIZATION.md](docs/reference/10_SMART_DECK_ORGANIZATION.md)
2. **Check Existing Decks** - See [docs/reference/11_SMART_DECK_LIBRARY_INDEX.md](docs/reference/11_SMART_DECK_LIBRARY_INDEX.md)
3. **Design Progressive Sequence**:
   - Phase 1: Foundation (Micro-learning + primary intervention + monitoring)
   - Phase 2: Building habits (Additional lifestyle changes)
   - Phase 3: Optimization (Fine-tuning, follow-ups)
4. **Define Unlock Logic** - Card 1 unlocks Card 2, etc.
5. **Calculate Deck Metadata** - Evidence grade (lowest among cards), time burden (sum), feasibility (average)
6. **Specify Expected Outcomes** - Primary outcome, timeline, success criteria

### Task: Validate Card Quality

Use the checklist from [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md):

**Completeness Check:**
- [ ] All required sections present (WHO, WHAT, WHEN, WHERE, WHY, HOW, MEASURE, TARGET, SAFETY, FOLLOW-UP, NOTES)
- [ ] Patient-facing view complete (WHAT, WHY, HOW, WHEN, WATCH FOR)
- [ ] Metadata complete (tags, evidence grade, feasibility score)

**Quality Check:**
- [ ] Patient-facing language at 6th-8th grade level
- [ ] One action per card (not multiple)
- [ ] Evidence citations present with grade A/B/C
- [ ] Clinical accuracy verified
- [ ] Safety warnings organized by health system

**Actionability Check:**
- [ ] Action is specific and measurable
- [ ] Timeline is realistic
- [ ] Target is achievable
- [ ] Measurement method is defined

### Task: AI Recommendation Logic

Reference [docs/core/06_AI_AGENT_WORKFLOW.md](docs/core/06_AI_AGENT_WORKFLOW.md):

**Prioritization Scoring Formula:**
```
Total Score = (Evidence × 0.30) + (Feasibility × 0.25) +
              (Time-to-Benefit × 0.15) + (Burden × 0.15) +
              (Patient Priority × 0.10) + (Guideline Mandate × 0.05)
```

**Conflict Checking Priority:**
1. Absolute contraindications → BLOCK
2. Drug-drug major interactions → WARN/BLOCK
3. Drug-condition contraindications → WARN
4. Card-card conflicts → FLAG
5. Moderate interactions → INFORM

## File Naming Conventions

### Library Files
- Use lowercase with underscores: `cardiovascular_meds.md`, `blood_tests.md`
- Medical cards in `library/medical/`
- Behavioral cards in `library/behavioral/`

### Documentation Files
- Core docs numbered: `01_SYSTEM_OVERVIEW.md`, `02_UNIVERSAL_CARD_TEMPLATE.md`
- Reference docs numbered or descriptive: `TIER1_OUTLINE.md`, `CARD_LOCATION_POLICY.md`

## When User Asks About...

### "How do I create a card?"
→ Direct to [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) and [docs/core/03_CARD_TYPE_SPECIFICATIONS.md](docs/core/03_CARD_TYPE_SPECIFICATIONS.md)

### "What are the card types?"
→ 10 types: Medication, Lab, Imaging, Procedure, Referral, Nutrition, Movement, Recovery, Mind-Body, Micro-Learning

### "How do decks work?"
→ Direct to [docs/reference/10_SMART_DECK_ORGANIZATION.md](docs/reference/10_SMART_DECK_ORGANIZATION.md) and [docs/reference/11_SMART_DECK_LIBRARY_INDEX.md](docs/reference/11_SMART_DECK_LIBRARY_INDEX.md)

### "What's the library structure?"
→ Direct to [docs/reference/07_LIBRARY_HIERARCHY_AND_TAGS.md](docs/reference/07_LIBRARY_HIERARCHY_AND_TAGS.md)

### "How does the AI recommendation work?"
→ Direct to [docs/core/06_AI_AGENT_WORKFLOW.md](docs/core/06_AI_AGENT_WORKFLOW.md)

### "What's the technical architecture?"
→ Direct to [ARCHITECTURE.md](ARCHITECTURE.md)

### "What are the development phases?"
→ Direct to [PROJECT_INSTRUCTIONS.md](PROJECT_INSTRUCTIONS.md) - Development Phases section

## Critical Reminders

### DO:
- Always use the universal template for cards
- Apply comprehensive tags (5-10 minimum)
- Write patient-facing content at 6th-8th grade level
- Include evidence citations and grades
- Link to Performance Medicine Framework (8 systems, 3 domains)
- Organize safety warnings by health system
- Calculate feasibility scores
- ONE action per card

### DON'T:
- Create standalone "educational cards" (education is embedded in action cards)
- Combine multiple actions in one card
- Use medical jargon in patient-facing content
- Skip evidence citations
- Forget to apply tags
- Create duplicate cards (use tags for cross-referencing)
- Violate HIPAA or patient privacy principles

## Example Card Structure (Quick Reference)

```markdown
# [Card Name]

## PATIENT-FACING VIEW
### WHAT YOU'RE DOING
[1 sentence - simple action]

### WHY THIS MATTERS TO YOU
[Patient's personal goal]

### HOW TO DO IT
- [Step 1]
- [Step 2]
- [Step 3]

### WHEN TO DO IT
[Frequency] | [Timeline]

### WHAT TO WATCH FOR
- [Red flag 1]
- [Red flag 2]

## FULL CLINICAL VIEW
### WHAT
[Detailed action, drug info, etc.]

### WHO
[Patient, clinician, support actors]

### WHEN
[Frequency, duration, best time]

### WHERE
[Setting, location]

### WHY
**Clinical Goal**: [System]: [Action] [Domain]
**Patient's Personal Goal**: [Their words]
**Mechanism**: [How it works]
**Evidence**: Grade [A/B/C] - [Citation]
**Timeline**: [Time-to-benefit]

### HOW
[Detailed step-by-step instructions]
[Synergy tips with active cards]

### MEASURE
[Tracking method, frequency, tools]

### TARGET
[Specific goal value, timeline, success criteria]

### SAFETY
[Organized by health system]
- Common Side Effects (Yellow)
- Stop & Contact (Orange)
- Emergency (Red)
- Contraindications
- Interactions

### FOLLOW-UP
[Review timeline, checkpoints, action based on results]

### NOTES
**Evidence**: [Source, Grade, Summary]
**Feasibility Score**: [0-100%]
**Barriers Checklist**: [Interactive]
**Community Feedback**: [Ratings, reviews]

## METADATA
**Tags**: [5-10 tags]
**Evidence Grade**: [A/B/C]
**Version**: [v1.0]
**Last Updated**: [Date]
```

## Statistics to Remember

- **Total Cards**: ~1,000
- **Medical Cards**: ~580 (Medications: ~355, Labs: ~90, Imaging: ~50, Procedures: ~55, Referrals: ~30)
- **Behavioral Cards**: ~391 (Nutrition: ~105, Movement: ~81, Recovery: ~60, Mind-Body: ~45, Micro-Learning: ~100)
- **Card Types**: 10
- **Pre-Built Decks**: 17+
- **Tier Levels**: 5
- **Tag Categories**: 10+

## Questions or Clarifications

If the user asks something not covered:
1. First check [PROJECT_INSTRUCTIONS.md](PROJECT_INSTRUCTIONS.md) for high-level guidance
2. Then check relevant doc in [docs/core/](docs/core/) or [docs/reference/](docs/reference/)
3. If creating new content, follow the universal template and validation checklist
4. When in doubt, reference existing examples in [docs/core/05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md)

## Working with This Project

When you're helping the user with this project:
- **Be proactive** about referencing the relevant documentation
- **Use the universal template** as the source of truth for card structure
- **Validate** all card content against the checklist before finalizing
- **Apply comprehensive tags** - this is critical for discoverability
- **Link to the Performance Medicine Framework** - always connect to health systems and domains
- **Write simply** for patient-facing content - use online readability checkers if needed
- **Include evidence** - never create cards without clinical backing

## Remember

This system transforms healthcare from **"here's information"** to **"here's what to do, and here's why."**

Every card should be:
- **Actionable** (ONE clear action)
- **Measurable** (trackable outcomes)
- **Evidence-based** (graded A/B/C)
- **Accessible** (6th-8th grade language)
- **Educational** (teaches while directing action)
