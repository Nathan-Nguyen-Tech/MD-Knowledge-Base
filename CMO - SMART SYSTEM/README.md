# SMART Card Library System

> Transforming healthcare from passive education to active, measurable interventions

## Overview

The **SMART Card Library** is a comprehensive, evidence-based health action system that empowers patients with easily accessible, actionable health interventions under clear clinical guidance. This system replaces traditional patient education materials (PDFs, printouts) with progressive, trackable card sequences that combine learning with action.

### Key Innovation

**Education Through Action**: Every card teaches while directing measurable behavior change.

- ❌ **OLD**: Hand patient 10-page PDF → Hope they read it → No tracking → No behavior change
- ✅ **NEW**: Prescribe condition deck → Progressive unlocking → Each card = Learn + Do → Full tracking → Measurable outcomes

## Core Concepts

### SMART Cards
Individual holistic medical orders with **ONE action per card**:
- Follow universal template (WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY-FOLLOW-UP)
- Two-sided: Patient-facing (6th-8th grade) + Full Clinical View
- Evidence-graded (A/B/C) with feasibility scoring (0-100%)
- ~1,000 cards across 10 card types

### SMART Decks
Clusters of cards achieving a common clinical goal:
- Progressive unlocking: Complete Card 1 → Unlock Card 2
- Example: "Hypertension Management Deck" (7 progressively unlocked cards)
- Contain: Optional micro-learning intro + Action cards + Monitoring

### SMART Card Library
Hierarchical organization of all cards:
- **2 Tiers**: Medical Cards + Behavioral Cards
- **10 Card Types**: Medications, Labs, Imaging, Procedures, Referrals, Nutrition, Movement, Recovery, Mind-Body, Micro-Learning
- **Tag System**: Flexible cross-cutting organization

### SMART Deck Library
Pre-built condition-based decks replacing traditional patient education:
- Organized by body system and condition
- Examples: Hypertension Management, Type 2 Diabetes Starter, Heart Failure Support
- Progressive sequences optimized for adherence and outcomes

## System Architecture

### Performance Medicine Framework

All clinical goals reference **8 Health Systems** with **3 Domains**:

**8 Systems**: Neurological • Cardiovascular • Respiratory • Metabolic • Filtration/Urinary • Musculoskeletal • Immune • Reproduction

**3 Domains**: Structure • Function • Risk

**Example Goal**: "Cardiovascular System: Reduce Risk"

### Library Hierarchy (5 Levels)

```
Tier 1 → Medical vs Behavioral
  Tier 2 → Card Type (Medication, Lab, Nutrition, etc.)
    Tier 3 → Subcategory (Antihypertensives, Blood Tests, etc.)
      Tier 4 → Specific Category (ACE Inhibitors, Electrolytes, etc.)
        Tier 5 → Individual Card (Lisinopril 10mg, Potassium Test, etc.)
```

## Project Structure

```
CLAUDE - SMART/
├── README.md                          # This file
├── PROJECT_INSTRUCTIONS.md            # Complete project guide and roadmap
├── ARCHITECTURE.md                    # Technical architecture and system design
│
├── docs/
│   ├── core/                          # Core system documentation (6 files)
│   │   ├── 01_SYSTEM_OVERVIEW.md
│   │   ├── 02_UNIVERSAL_CARD_TEMPLATE.md
│   │   ├── 03_CARD_TYPE_SPECIFICATIONS.md
│   │   ├── 04_VALIDATION_CHECKLIST.md
│   │   ├── 05_EXAMPLE_SMART_CARDS.md
│   │   └── 06_AI_AGENT_WORKFLOW.md
│   │
│   └── reference/                     # Additional documentation (11+ files)
│       ├── 00_FILE_INDEX_AND_GUIDE.md
│       ├── 07_LIBRARY_HIERARCHY_AND_TAGS.md
│       ├── 08_BEHAVIORAL_DESIGN_AND_ADHERENCE.md
│       ├── 09_COMMUNITY_FEEDBACK_SYSTEM.md
│       ├── 10_SMART_DECK_ORGANIZATION.md
│       ├── 11_SMART_DECK_LIBRARY_INDEX.md
│       └── ... (tier outlines, location policy, etc.)
│
└── library/                           # Card library content (~1,000 cards)
    ├── medical/                       # Medical cards (~580 cards)
    │   ├── cardiovascular_meds.md
    │   ├── diabetes_meds.md
    │   ├── respiratory_meds.md
    │   ├── gi_meds.md
    │   ├── neuro_psych_meds.md
    │   ├── pain_meds.md
    │   ├── antibiotics_meds.md
    │   ├── endocrine_other_meds.md
    │   ├── blood_tests.md
    │   ├── urine_other_tests.md
    │   ├── imaging_procedures.md
    │   └── procedures_referrals.md
    │
    └── behavioral/                    # Behavioral cards (~391 cards)
        ├── dietary_patterns.md
        ├── specific_food_focus.md
        ├── eating_behaviors_meal_planning.md
        ├── aerobic_exercise.md
        ├── strength_flexibility_balance.md
        ├── sleep_stress_breathing.md
        └── mindbody_microlearning.md
```

## Quick Start

### For New Users
1. Read [README.md](README.md) (this file) - Project overview
2. Read [PROJECT_INSTRUCTIONS.md](PROJECT_INSTRUCTIONS.md) - Complete project guide
3. Review [docs/core/01_SYSTEM_OVERVIEW.md](docs/core/01_SYSTEM_OVERVIEW.md) - System philosophy
4. Explore [docs/core/05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md) - See examples

### For Developers
1. Read [ARCHITECTURE.md](ARCHITECTURE.md) - Technical architecture
2. Review [PROJECT_INSTRUCTIONS.md](PROJECT_INSTRUCTIONS.md) - Development phases
3. Study [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) - Data models
4. Explore [docs/core/06_AI_AGENT_WORKFLOW.md](docs/core/06_AI_AGENT_WORKFLOW.md) - AI integration

### For Clinicians
1. Read [docs/core/01_SYSTEM_OVERVIEW.md](docs/core/01_SYSTEM_OVERVIEW.md) - System overview
2. Review [docs/reference/11_SMART_DECK_LIBRARY_INDEX.md](docs/reference/11_SMART_DECK_LIBRARY_INDEX.md) - Pre-built condition decks
3. Study [docs/core/05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md) - Card examples
4. Explore [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md) - Quality standards

### For Content Creators
1. Read [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) - Card template
2. Review [docs/core/03_CARD_TYPE_SPECIFICATIONS.md](docs/core/03_CARD_TYPE_SPECIFICATIONS.md) - Type-specific guidance
3. Use [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md) - Validate cards
4. Reference [docs/core/05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md) - Examples

## Key Features

### For Patients
- **Progressive Learning**: Cards unlock sequentially, preventing overwhelm
- **Actionable**: Every card has ONE clear, measurable action
- **Accessible**: 6th-8th grade reading level, multilingual support
- **Trackable**: Log adherence, measurements, and barriers
- **Community-Driven**: See what works for others with ratings and reviews
- **Personalized**: AI-recommended cards matched to your profile

### For Clinicians
- **Evidence-Based**: All cards graded A/B/C with clinical citations
- **AI-Assisted**: Automated recommendations with clinician approval
- **Time-Saving**: NLP parsing converts notes to cards automatically
- **Comprehensive Monitoring**: Dashboards for patient adherence and outcomes
- **Flexible**: Prescribe individual cards or complete condition decks
- **EHR Integration**: Sync with existing electronic health records

### For the Healthcare System
- **Measurable Outcomes**: Track clinical targets (BP control, HbA1c improvement)
- **Higher Adherence**: Progressive unlocking and gamification boost engagement
- **Cost-Effective**: Replace expensive patient education programs
- **Scalable**: AI automation reduces clinician burden
- **Evidence-Generating**: Real-world data feeds continuous improvement
- **Interoperable**: FHIR-compliant, integrates with existing systems

## Critical Design Principles

1. **One Action Per Card** - Keep focused and manageable
2. **Patient Goals First** - Link to intrinsic motivation
3. **Evidence-Based** - Grade all recommendations (A/B/C)
4. **Accessibility Always** - 6th-8th grade language, multilingual
5. **Education Through Action** - No passive learning
6. **Community Wisdom** - Balance evidence with lived experience
7. **Safety by Design** - Organize warnings by health system
8. **Progressive Unlocking** - Prevent overwhelm with sequencing
9. **Dual Confidence Scoring** - AI feasibility + patient confidence
10. **Version Control** - Cards evolve with evidence updates

## Statistics

| Metric | Count |
|--------|-------|
| **Total Cards** | ~1,000 |
| **Medical Cards** | ~580 |
| **Behavioral Cards** | ~391 |
| **Card Types** | 10 |
| **Pre-Built Decks** | 17+ |
| **Tier Levels** | 5 |
| **Tag Categories** | 10+ |

### Card Breakdown
- Medication Cards: ~355
- Lab/Test Cards: ~90
- Imaging Cards: ~50
- Procedure Cards: ~55
- Referral Cards: ~30
- Nutrition Cards: ~105
- Movement Cards: ~81
- Recovery Cards: ~60
- Mind-Body Cards: ~45
- Micro-Learning Cards: ~100

## Example Use Cases

### Case 1: New Hypertension Diagnosis

**Traditional Approach:**
1. Hand patient "Understanding Hypertension" PDF (10 pages)
2. Write prescription for Lisinopril
3. Tell them to "follow up in 4 weeks"
4. Hope they read the PDF (they usually don't)

**SMART Card Approach:**
1. Prescribe "Hypertension Management Deck" in EHR
2. Patient receives 7 progressively unlocked cards:
   - Card 1: Micro-Learning - Understanding BP Numbers (5 min)
   - Card 2: Take Lisinopril 10mg daily
   - Card 3: Monitor BP at home twice daily
   - Card 4: DASH diet
   - Card 5: Walking program 30min, 5x/week
   - Card 6: Stress management (deep breathing)
   - Card 7: Follow-up labs (BMP) in 4 weeks
3. System tracks adherence, BP readings, and outcomes
4. Clinician reviews dashboard weekly
5. **Result**: Patient learns progressively while taking action at each step

### Case 2: Type 2 Diabetes Starter

**SMART Deck includes:**
- Micro-Learning: Understanding Insulin Resistance
- Metformin 500mg BID
- Home glucose monitoring
- Low-carb diet
- Walking 30min daily after meals
- Daily foot care
- HbA1c lab every 3 months
- Annual eye exam referral

**Expected Outcomes**: HbA1c reduction 1-2% in 3 months, weight loss 5-10 lbs

## Development Roadmap

### Phase 1: Foundation ✅ (Current)
- [x] System architecture and philosophy
- [x] Universal card template
- [x] Library hierarchy (~1,000 cards enumerated)
- [x] Tag system design
- [x] Documentation complete
- [ ] Example cards for each type

### Phase 2: Content Creation
- [ ] Generate all ~1,000 individual cards
- [ ] Apply comprehensive tags
- [ ] Validate with checklist

### Phase 3: Deck Assembly
- [ ] Build condition-based decks (HTN, DM, CHF, etc.)
- [ ] Define progressive unlocking sequences
- [ ] Test synergy and conflicts

### Phase 4: AI Integration
- [ ] Patient profile analysis
- [ ] Card recommendation engine
- [ ] NLP parsing for clinical notes
- [ ] Conflict checking algorithms

### Phase 5: Patient Experience
- [ ] Patient-facing app (iOS, Android, web)
- [ ] Adherence tracking and logging
- [ ] Gamification and rewards
- [ ] Community review system

### Phase 6: Clinician Tools
- [ ] Clinician dashboard
- [ ] Deck prescription workflow
- [ ] AI recommendation approval
- [ ] Patient progress analytics

### Phase 7: Quality & Governance
- [ ] Quarterly evidence review
- [ ] Version control system
- [ ] Community moderation
- [ ] Clinical accuracy checks

## Technology Stack (Recommended)

**Backend**: TypeScript (Node.js) or Python
**Frontend**: React + TypeScript, React Native
**Database**: PostgreSQL 15+
**Cache**: Redis 7+
**AI/ML**: OpenAI GPT-4, spaCy, scikit-learn
**Cloud**: AWS (ECS Fargate, RDS, S3, CloudFront)
**Integration**: FHIR, HL7

See [ARCHITECTURE.md](ARCHITECTURE.md) for complete technical details.

## Success Metrics

### Card-Level
- Adherence rate (% completing card >30 days)
- Target achievement rate (% meeting clinical goals)
- Patient confidence scores
- Community ratings (average stars)

### Deck-Level
- Deck completion rate
- Overall outcome achievement
- Patient satisfaction ratings
- Clinician adoption rate

### System-Level
- Total active patients
- Cards prescribed per month
- Clinical outcomes (BP control, HbA1c improvement)
- Cost savings vs traditional care

## Contributing

This is a healthcare innovation project. When creating cards or decks:

1. **Follow the universal template** - See [docs/core/02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md)
2. **Use the validation checklist** - See [docs/core/04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md)
3. **Apply comprehensive tags** - 5-10 minimum per card
4. **Write at 6th-8th grade level** - Patient-facing content must be simple
5. **Include evidence citations** - Grade all cards A/B/C
6. **ONE action per card** - Not multiple actions
7. **Link to Performance Medicine Framework** - 8 systems, 3 domains

## Documentation

### Core Documentation (Essential Reading)
- [01_SYSTEM_OVERVIEW.md](docs/core/01_SYSTEM_OVERVIEW.md) - Philosophy and core principles
- [02_UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) - Complete card structure
- [03_CARD_TYPE_SPECIFICATIONS.md](docs/core/03_CARD_TYPE_SPECIFICATIONS.md) - Type-specific guidance
- [04_VALIDATION_CHECKLIST.md](docs/core/04_VALIDATION_CHECKLIST.md) - Quality assurance
- [05_EXAMPLE_SMART_CARDS.md](docs/core/05_EXAMPLE_SMART_CARDS.md) - Visual examples
- [06_AI_AGENT_WORKFLOW.md](docs/core/06_AI_AGENT_WORKFLOW.md) - AI decision logic

### Reference Documentation
- [07_LIBRARY_HIERARCHY_AND_TAGS.md](docs/reference/07_LIBRARY_HIERARCHY_AND_TAGS.md) - Organization system
- [08_BEHAVIORAL_DESIGN_AND_ADHERENCE.md](docs/reference/08_BEHAVIORAL_DESIGN_AND_ADHERENCE.md) - Engagement strategies
- [09_COMMUNITY_FEEDBACK_SYSTEM.md](docs/reference/09_COMMUNITY_FEEDBACK_SYSTEM.md) - Reviews and ratings
- [10_SMART_DECK_ORGANIZATION.md](docs/reference/10_SMART_DECK_ORGANIZATION.md) - How decks work
- [11_SMART_DECK_LIBRARY_INDEX.md](docs/reference/11_SMART_DECK_LIBRARY_INDEX.md) - Pre-built condition decks

## License

[To be determined - likely open source with clinical safety review requirements]

## Contact

[Project contact information to be added]

---

**Mission**: Transform healthcare from "here's information" to "here's what to do, and here's why."
