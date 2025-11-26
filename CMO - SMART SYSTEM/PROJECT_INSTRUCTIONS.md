# SMART Card Library System - Project Instructions

## Project Overview

The SMART Card Library is a comprehensive, evidence-based health action system designed to transform healthcare delivery from passive patient education to active, measurable interventions. This system empowers patients with easily accessible actionable steps under clear clinical guidance.

## Project Goals

1. **Build a comprehensive digital health intervention platform** with ~1,000 individual SMART cards
2. **Replace traditional patient education materials** (PDFs, printouts) with actionable, progressive card sequences
3. **Enable AI-driven personalized care recommendations** based on patient profiles and evidence-based guidelines
4. **Create condition-specific decks** that guide patients through progressive, unlockable care sequences
5. **Implement community-driven improvements** through patient feedback and reviews
6. **Support clinician workflow** with NLP parsing, automated deck assembly, and monitoring dashboards

## Core Concepts

### SMART Cards
- **Individual holistic medical orders/prescriptions** - ONE action per card
- Follow universal template (WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY-FOLLOW-UP-NOTES)
- Two-sided architecture: Patient-facing (6th-8th grade) + Full Clinical View
- Evidence-graded (A/B/C) with feasibility scoring (0-100%)

### SMART Decks
- **Clusters of cards** that achieve a common clinical goal
- Progressive unlocking: Complete Card 1 → Unlock Card 2
- Contain: Micro-learning cards (optional 5-min intro) + Action cards + Monitoring cards
- Example: "Hypertension Management Deck" (7 cards progressively unlocked)

### SMART Card Library
- **Hierarchical categorical system** organizing all individual cards
- 2-tier structure: Medical Cards + Behavioral Cards
- **12 card types** (see LIBRARY_TIER_STRUCTURE.md for complete list)
- ~1,000 total cards across all categories

### SMART Deck Library
- **Curated collection of condition-based decks** replacing traditional patient education
- Organized by body system and condition
- Pre-built templates for common conditions (Hypertension, Diabetes, Heart Failure, etc.)

## Key Innovation: Education Through Action

**OLD APPROACH**: Hand patient 10-page PDF → Hope they read it → No tracking → No behavior change

**NEW APPROACH**:
- Prescribe condition deck → Progressive card unlocking → Each card = Learn + Do → Full tracking → Measurable outcomes
- Education embedded in every card (WHY/HOW sections)
- Micro-learning cards provide brief (5-min) foundational concepts within decks
- No standalone "educational cards" - all cards are actionable

## System Architecture

### Performance Medicine Framework
All clinical goals reference **8 Health Systems** with **3 Domains**:

**8 Health Systems:**
1. Neurological (including mental health)
2. Cardiovascular
3. Respiratory
4. Metabolic (including digestive)
5. Filtration/Urinary
6. Musculoskeletal
7. Immune (inflammatory, infectious, oncology)
8. Reproduction (including hormones)

**3 Domains for Each System:**
- **Structure**: Anatomy, tissue integrity
- **Function**: Physiological performance
- **Risk**: Disease prevention, risk reduction

**Example Clinical Goal**: "Cardiovascular System: Reduce Risk"

### Library Hierarchy (5 Levels)

```
Tier 1 (Broad Category) - MEDICAL vs BEHAVIORAL
  └─ Tier 2 (Card Type) - Medication, Lab, Nutrition, Movement, etc.
      └─ Tier 3 (Subcategory) - Antihypertensives, Blood Tests, etc.
          └─ Tier 4 (Specific Category) - ACE Inhibitors, Electrolytes, etc.
              └─ Tier 5 (Individual Card) - Lisinopril 10mg, Potassium Test, etc.
```

### Tag System
Flexible cross-cutting organization with 10+ tag categories:
- Clinical Intent (#PreventiveCare, #ChronicManagement)
- Guidelines (#USPSTF_GradeA, #ACC_AHA, #ADA)
- Care Setting (#Home, #Outpatient, #Telehealth)
- Population (#Adult, #Geriatric, #Pediatric)
- Condition (#Hypertension, #Diabetes)
- Organ System (#Cardiology, #Metabolic)
- Community (#Easy, #Affordable, #WorkedForMe)

## User Roles

### Patients
- Receive personalized card decks from clinicians
- Execute actions and log data
- Progress through unlockable card sequences
- Report barriers and provide feedback
- Rate cards and contribute community reviews
- Learn by doing, not passive reading

### Clinicians
- Select and prescribe individual cards or condition decks
- Review AI recommendations before publishing
- Monitor patient progress via dashboards
- Modify cards as conditions change
- Use NLP parsing to auto-generate cards from clinical notes

### AI Agent
- Analyze patient data and suggest appropriate cards
- Check contraindications and drug interactions
- Calculate feasibility scores based on patient barriers
- Prioritize cards by evidence, burden, time-to-benefit
- Parse natural language orders into structured cards
- Recommend condition decks and sequence cards optimally
- Monitor adherence and alert clinicians to issues

## Critical Design Principles

1. **One Action Per Card** - Keep cards focused and manageable
2. **Patient Personal Goals First** - Link to intrinsic motivation
3. **Evidence-Based with Community Input** - Balance research with lived experience
4. **Universal Template** - Consistent structure across all card types
5. **Performance Medicine Framework** - Link to 8 health systems and 3 domains
6. **Dual Confidence Scoring** - AI feasibility score + patient self-confidence score
7. **Safety by Health Systems** - Organize warnings by body system
8. **Tag System for Flexibility** - Don't over-hierarchize; use tags for cross-cutting concepts
9. **Titratable Cards Have Tiers** - Progress forward or backward within same card
10. **Synergy Over Silos** - Cards should stack naturally into routines
11. **Accessibility Always** - 6th-8th grade reading level, plain language, multilingual
12. **Community Moderation** - Patient reviews enhance system but requires oversight
13. **Time-to-Benefit Transparency** - Set realistic expectations with disclaimer
14. **Version Control** - Cards evolve with evidence; track changes
15. **Education is Embedded, Not Separate** - Every card teaches while directing action
16. **Decks Replace PDFs** - Transform traditional education materials into actionable sequences

## Development Phases

### Phase 1: Foundation (Current)
- [x] Establish system architecture and core philosophy
- [x] Define universal card template
- [x] Create library hierarchy (5 tiers, ~1,000 cards enumerated)
- [x] Design tag system
- [x] Document card type specifications (10 types)
- [x] Build validation checklist
- [ ] **Create example cards for each card type**
- [ ] **Organize project documentation**

### Phase 2: Content Creation
- [ ] Generate all ~355 medication cards
- [ ] Generate all ~90 lab/test cards
- [ ] Generate all ~50 imaging cards
- [ ] Generate all ~55 procedure cards
- [ ] Generate all ~30 referral cards
- [ ] Generate all ~105 nutrition cards
- [ ] Generate all ~81 movement cards
- [ ] Generate all ~60 recovery cards
- [ ] Generate all ~45 mind-body cards
- [ ] Generate all ~100 micro-learning cards
- [ ] Apply comprehensive tags to all cards
- [ ] Validate all cards against checklist

### Phase 3: Deck Assembly
- [ ] Build condition-based decks (Hypertension, Diabetes, Heart Failure, etc.)
- [ ] Define progressive unlocking sequences
- [ ] Create deck metadata and success metrics
- [ ] Test deck synergy and conflict checking
- [ ] Build preventive care decks
- [ ] Build symptom-based decks

### Phase 4: AI Integration
- [ ] Implement patient profile analysis
- [ ] Build indication matching algorithm
- [ ] Create card prioritization scoring system
- [ ] Develop deck assembly and presentation logic
- [ ] Build NLP parsing for clinical notes
- [ ] Implement conflict checking (drug-drug, drug-condition, card-card)
- [ ] Create continuous monitoring and alerting system
- [ ] Develop AI recommendation dashboard for clinicians

### Phase 5: Patient Experience
- [ ] Design patient-facing app interface
- [ ] Implement progressive card unlocking
- [ ] Build adherence tracking and logging
- [ ] Create reward and gamification features
- [ ] Implement community review system
- [ ] Build barrier reporting and mitigation
- [ ] Design low-tech alternatives (phone, paper)

### Phase 6: Clinician Tools
- [ ] Build clinician dashboard for patient monitoring
- [ ] Implement deck prescription workflow
- [ ] Create AI recommendation approval interface
- [ ] Build clinical note parsing integration
- [ ] Design patient progress analytics
- [ ] Implement deck customization tools

### Phase 7: Quality & Governance
- [ ] Establish quarterly evidence review cycle
- [ ] Implement version control system
- [ ] Build community feedback moderation
- [ ] Create reading level validation tools
- [ ] Establish clinical accuracy review process
- [ ] Implement deck effectiveness tracking

## Technical Requirements

### Data Models
- **Card Model**: Full template with metadata, tags, versions
- **Deck Model**: Collection of cards with sequencing logic
- **Patient Model**: Profile, barriers, goals, active cards, adherence data
- **Evidence Model**: Guidelines, grades, citations with version tracking
- **Community Model**: Reviews, ratings, adherence rates, outcomes

### APIs Needed
- `POST /api/cards/recommend` - AI generates recommendations
- `GET /api/cards/library` - Retrieve card library with filters
- `POST /api/cards/publish` - Publish deck to patient
- `GET /api/patient/adherence` - Get adherence data
- `POST /api/patient/report` - Patient reports side effect or barrier
- `GET /api/monitoring/alerts` - Get AI-generated alerts
- `POST /api/nlp/parse` - Parse clinical notes into cards

### Integration Points
- EHR systems (HL7 FHIR, Epic, Cerner)
- Drug interaction databases
- Guideline databases (USPSTF, ACC/AHA, ADA, etc.)
- Patient apps (iOS, Android, web)
- Wearables and home monitoring devices
- Pharmacy systems
- Lab systems

## Success Metrics

### Card-Level Metrics
- Adherence rate (% completing card >30 days)
- Target achievement rate (% meeting clinical goals)
- Patient confidence scores (pre/post)
- Community ratings (average stars)
- Time-to-benefit accuracy

### Deck-Level Metrics
- Deck completion rate
- Overall outcome achievement
- Patient satisfaction ratings
- Clinician adoption rate
- Time saved vs traditional care

### System-Level Metrics
- Total cards in library
- Evidence grade distribution (% Grade A)
- Patient engagement (daily active users)
- Clinician engagement (decks prescribed per month)
- Community contributions (reviews per card)
- Clinical outcomes (BP control, HbA1c improvement, etc.)

## File Organization

```
CLAUDE - SMART/
├── README.md                          # Project overview and quick start
├── PROJECT_INSTRUCTIONS.md            # This file - complete project guide
├── ARCHITECTURE.md                    # System design and technical architecture
│
├── .claude/
│   └── instructions.md               # Claude-specific context for AI assistance
│
├── docs/
│   ├── core/                         # Core system documentation
│   │   ├── 01_SYSTEM_OVERVIEW.md
│   │   ├── 02_UNIVERSAL_CARD_TEMPLATE.md
│   │   ├── 03_CARD_TYPE_SPECIFICATIONS.md
│   │   ├── 04_VALIDATION_CHECKLIST.md
│   │   ├── 05_EXAMPLE_SMART_CARDS.md
│   │   └── 06_AI_AGENT_WORKFLOW.md
│   │
│   └── reference/                    # Additional reference documentation
│       ├── 07_LIBRARY_HIERARCHY_AND_TAGS.md
│       ├── 08_BEHAVIORAL_DESIGN_AND_ADHERENCE.md
│       ├── 09_COMMUNITY_FEEDBACK_SYSTEM.md
│       ├── 10_SMART_DECK_ORGANIZATION.md
│       └── 11_SMART_DECK_LIBRARY_INDEX.md
│
└── library/                          # Card library content files
    ├── medical/                      # Medical cards (~580 cards)
    │   ├── medications/
    │   │   ├── cardiovascular_meds.md
    │   │   ├── diabetes_meds.md
    │   │   ├── respiratory_meds.md
    │   │   ├── gi_meds.md
    │   │   ├── neuro_psych_meds.md
    │   │   ├── pain_meds.md
    │   │   ├── antibiotics_meds.md
    │   │   └── endocrine_other_meds.md
    │   ├── labs/
    │   │   ├── blood_tests.md
    │   │   └── urine_other_tests.md
    │   ├── imaging_procedures.md
    │   └── procedures_referrals.md
    │
    └── behavioral/                   # Behavioral cards (~391 cards)
        ├── nutrition/
        │   ├── dietary_patterns.md
        │   ├── specific_food_focus.md
        │   └── eating_behaviors_meal_planning.md
        ├── movement/
        │   ├── aerobic_exercise.md
        │   └── strength_flexibility_balance.md
        ├── recovery/
        │   └── sleep_stress_breathing.md
        └── mindbody_microlearning.md
```

## Next Steps for Implementation

1. **Review and organize existing documentation** into folder structure above
2. **Create example cards** for each of the 10 card types
3. **Begin systematic card generation** starting with highest-priority conditions
4. **Build condition decks** for common diagnoses (HTN, DM, CHF, COPD)
5. **Develop technical architecture** for database, APIs, and AI integration
6. **Design patient and clinician interfaces** with UX/UI mockups
7. **Implement MVP** with limited card set for pilot testing
8. **Gather feedback** from patients and clinicians
9. **Iterate and expand** library based on real-world usage

## References to Core Documentation

- **System Overview**: See [docs/core/01_SYSTEM_OVERVIEW.md](docs/core/01_SYSTEM_OVERVIEW.md)
- **Universal Template**: See [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md)
- **Card Types**: See [docs/core/03_CARD_TYPE_SPECIFICATIONS.md](docs/core/03_CARD_TYPE_SPECIFICATIONS.md)
- **Validation**: See [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md)
- **Examples**: See [docs/core/05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md)
- **AI Workflow**: See [docs/core/06_AI_AGENT_WORKFLOW.md](docs/core/06_AI_AGENT_WORKFLOW.md)
- **Library Structure**: See [docs/reference/07_LIBRARY_HIERARCHY_AND_TAGS.md](docs/reference/07_LIBRARY_HIERARCHY_AND_TAGS.md)
- **Deck Library**: See [docs/reference/11_SMART_DECK_LIBRARY_INDEX.md](docs/reference/11_SMART_DECK_LIBRARY_INDEX.md)

## Questions or Issues

When working on this project:
- Reference the universal template for all card creation
- Use the validation checklist before finalizing cards
- Apply comprehensive tags (5-10 minimum per card)
- Link cards to Performance Medicine Framework (8 systems, 3 domains)
- Always write patient-facing content at 6th-8th grade level
- Ensure ONE action per card (not multiple actions)
- Include evidence grades and citations
- Calculate feasibility scores based on patient barriers
