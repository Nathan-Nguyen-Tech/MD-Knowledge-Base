# CMO Platform - Project Context for Claude

## Project Overview

This is the **Comprehensive Medical Optimization (CMO) Platform** - a self-directed healthcare system enabling patients to manage their own health with AI assistance and clinician oversight.

**Philosophy**: Patients are their own primary healthcare providers. Clinicians are guidance counselors who guide, counsel, and redirect.

**Architecture Version**: 3.0 (December 2025)

---

## Project Structure (4 Sections)

### Section 1: DATA INPUT MANAGEMENT
**Location**: `CMO - DATA INPUT/`
- Patient intake forms, questionnaires
- Medical/family/surgical history libraries
- Allergy libraries
- Score calculations

### Section 2: HEALTH OVERVIEW DASHBOARD
**Location**: `CMO - DATA INPUT/`
- Live, continuously-updating health visualization
- Biological age, health scores, risk indicators
- Real-time data integration

### Section 3: SMART CARD/DECK SYSTEM
**Location**: `CMO - SMART SYSTEM/`
- **Medical Cards (6 types):** Medications, Testing, Imaging, Procedures, DME, Referrals
- **Behavioral Cards (5 pillars):** Nutrition, Movement, Recovery, Emotion, Environment
- **Educational Cards (1 type):** Micro-Learning
- Behavioral libraries organized by the 5 Lifestyle Pillars
- Card lifecycle: Initiation → Maintenance → De-loading
- **Care Plan = Organized Collection of SMART Cards** (not separate from cards)

### Section 4: PERFORMANCE MEDICINE PHILOSOPHY
**Location**: `CMO - PERFORMANCE MEDICINE/`
- Clinical framework and standards
- Evidence-based guidelines

---

## Critical Documents (Read First)

| Document | Purpose | Location |
|----------|---------|----------|
| `SOURCE_DOCUMENT_REGISTRY.md` | Canonical source for all specifications | Root |
| `00_START_HERE.md` | Navigation guide | Root |
| `INTEGRATION_ARCHITECTURE.md` | How sections connect (v3.0) | Root |
| `CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md` | **NEW** 3 Care Plan Types, 90/10 Model, Multi-Specialty AI | Root |
| `MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md` | 5 core + 14 specialist agents (v3.0) | Root |
| `CARD_TYPE_SPECIFICATIONS.md` | All 12 card types | SMART SYSTEM/docs/core/ |

---

## Key Specifications

### SMART Cards - CORE PRINCIPLE
**ONE ACTION = ONE CARD.** This is non-negotiable.

- If you can't describe it as **one verb + one object**, it's not a card
- A card answers: "What ONE specific thing should I do right now?"
- Yoga, Tai Chi, Qigong, "Sleep Hygiene Program" = **DECKS** (collections of cards)
- Each yoga pose, each Tai Chi movement, each specific action = **CARD**
- Cards combine into DECKS
- Template: `UNIVERSAL_CARD_TEMPLATE.md`

---

## THE 5 LIFESTYLE PILLARS (Behavioral Cards)

These are the ONLY 5 categories for behavioral SMART cards. Every behavioral card belongs to exactly ONE pillar.

| Pillar | Prefix | Covers | Examples |
|--------|--------|--------|----------|
| **1. Nutrition** | `NUT_` | Food, drink, eating behaviors, supplements | Eat vegetables, drink water, limit sugar, take vitamin D |
| **2. Movement** | `MOV_` | Physical activity, exercise, poses, physical movements | Walk, squat, warrior pose, wave hands like clouds (tai chi), cat-cow |
| **3. Recovery** | `REC_` | Sleep, physical rest, physical recovery, thermal exposure | Set bedtime, cold shower, take bath, use sauna, nap |
| **4. Emotion** | `EMO_` | Mental health, stress, mood, cognitive, psychological techniques | Practice gratitude, challenge negative thoughts, journal, meditate, breathwork |
| **5. Environment** | `ENV_` | Surroundings, community, relationships, substances, workspace | Call friend, improve lighting, quit smoking, declutter, join group |

### Pillar Placement Rules

**Movement vs Recovery:**
- If it's primarily PHYSICAL EXERTION → Movement
- If it's primarily REST/RESTORATION → Recovery
- Yoga poses = Movement (physical positions requiring muscle engagement)
- Relaxation techniques = Recovery (rest-focused)

**Recovery vs Emotion:**
- If it targets PHYSICAL restoration (sleep, body) → Recovery
- If it targets MENTAL/PSYCHOLOGICAL state (mood, thoughts) → Emotion
- Breathing for relaxation = Recovery (physical)
- Breathing for anxiety management = Emotion (psychological)
- Note: Some techniques serve both - place in ONE pillar, reference from other

**Emotion vs Environment:**
- If it's an INTERNAL state or self-directed technique → Emotion
- If it involves EXTERNAL factors or other people → Environment
- Journaling = Emotion (self-reflection)
- Call a friend = Environment (social action)
- Feeling lonely = Emotion (state); Joining a group = Environment (action)

### What is NOT a Pillar
- **Mind-Body** is NOT a pillar - it's a METHOD that serves Movement, Recovery, and Emotion
- **Meditation** goes in Emotion (mental technique) or Recovery (relaxation) depending on purpose
- **Yoga poses** go in Movement (physical positions)
- **Tai Chi movements** go in Movement (physical movements)
- **Breathing techniques** go in Recovery (physical) or Emotion (psychological) depending on purpose

### Cross-Pillar References
When a card could serve multiple pillars, place it in ONE pillar and add a cross-reference note:
```
**Cross-Reference:** This technique also supports [other pillar]. See [Card ID] for related cards.
```

---

## SMART CARD LIBRARY COMPLETION STATUS

**Last Updated:** 2025-12-14

### Library Coverage Summary

**Medical Cards:**
| Card Type | Target | Current | % Done | Status |
|-----------|--------|---------|--------|--------|
| **Medications** | ~3,000 | 484 entries | 16% | 🟡 Cardio/DM/Resp only |
| **Diagnostic Testing** | ~600 | 0 | 0% | 🔴 Not started |
| **Imaging Studies** | ~150 | 0 | 0% | 🔴 Not started |
| **Procedures** | ~400 | 0 | 0% | 🔴 Not started |
| **DME** | ~250 | 0 | 0% | 🔴 Not started |
| **Referrals** | ~100 | 0 | 0% | 🔴 Not started |

**Behavioral Cards (5 Pillars):**
| Pillar | Library File | Target | Current | % Done | Status | Notes |
|--------|--------------|--------|---------|--------|--------|-------|
| **Nutrition** | TIER5_NUTRITION_v2.md | ~250 | 195 | 78% | 🟡 | Includes monitoring, prep, assessment, maintenance, +27 pediatric |
| **Movement** | TIER5_MOVEMENT_EXERCISE_v2.md | ~450 | 378 | 84% | 🟢 | Yoga (92), Tai Chi (37), Qigong (36), monitoring, assessment |
| **Recovery** | TIER5_RECOVERY_v2.md | ~150 | 141 | 94% | 🟢 | Sleep, thermal, monitoring, assessment, maintenance, +27 pediatric |
| **Emotion** | TIER5_EMOTION_v2.md | ~150 | 118 | 79% | 🟡 | Meditation, cognitive, HRV, screening, monitoring, +32 pediatric |
| **Environment** | TIER5_ENVIRONMENTAL_SOCIAL_v2.md | ~200 | 137 | 69% | 🟡 | Social, substance use, monitoring, maintenance |

**Educational Cards:**
| Card Type | Target | Current | % Done | Status |
|-----------|--------|---------|--------|--------|
| **Micro-Learning** | ~800 | 54 | 7% | 🔴 Minimal |

**TOTALS:**
| Category | Target | Current | % Done |
|----------|--------|---------|--------|
| Medical | ~4,500 | 484 | 11% |
| Behavioral | ~1,200 | 883 | 74% |
| Educational | ~800 | 54 | 7% |
| **TOTAL** | **~6,500** | **1,421** | **22%** |

*Note: Major expansion Dec 2025 - Added monitoring, assessment, preparation, and maintenance action types to all behavioral pillars. Mind-Body library dissolved; cards redistributed.*

**Status Key:** 🟢 Complete (>80%) | 🟡 Partial (20-80%) | 🔴 Missing (<20%)

### Coverage Gaps by Population

| Population | Coverage | Priority Gap |
|------------|----------|--------------|
| **Prenatal/Pregnancy** | 🔴 0% | OB cards, prenatal nutrition, prenatal movement |
| **Pediatric (0-12)** | 🟡 25% | 86 pediatric cards added (Nutrition, Recovery, Emotion); still need Movement, vaccines, meds |
| **Adolescent (13-17)** | 🔴 0% | Mental health, reproductive health, risk behaviors |
| **Adult (18-64)** | 🟡 40% | Most behavioral cards apply; meds partial |
| **Geriatric (65+)** | 🟡 20% | Fall prevention partial; polypharmacy, dementia missing |
| **End of Life** | 🔴 0% | Palliative, hospice, comfort care |

### Coverage Gaps by Specialty

| Specialty | Coverage | Missing |
|-----------|----------|---------|
| **Primary Care** | 🟡 30% | Many common conditions |
| **Cardiology** | 🟡 40% | Meds present, rehab/procedures missing |
| **Endocrinology** | 🟡 25% | Diabetes partial; thyroid/adrenal missing |
| **Pulmonology** | 🟡 30% | Meds present; sleep/DME missing |
| **Psychiatry** | 🔴 5% | Almost entirely missing |
| **Neurology** | 🔴 5% | Almost entirely missing |
| **GI/Hepatology** | 🔴 0% | Not started |
| **Nephrology** | 🔴 0% | Not started |
| **Rheumatology** | 🔴 0% | Not started |
| **Oncology** | 🔴 0% | Not started |
| **OB/GYN** | 🔴 0% | Not started |
| **Pediatrics** | 🔴 0% | Not started |
| **Orthopedics/PT** | 🟡 20% | Movement partial; rehab protocols missing |
| **Pain Management** | 🔴 0% | Not started |
| **Dermatology** | 🔴 0% | Not started |

### Library Development Strategy

**Phase 1 (Current):** Library REGISTRY (Card ID + Name + Description)
- Complete enumeration of all cards that SHOULD exist
- Organized in TIER5 files with coverage checklists

**Phase 2 (Next):** Full Cards On-Demand
- When card is needed for care plan, expand to full SMART card
- Use UNIVERSAL_CARD_TEMPLATE.md
- Clinical review before production use

**Phase 3 (Future):** Batch Generation
- Top 50 conditions get full cards generated in batches
- AI + clinical review workflow

**Key Insight:** The library is a REGISTRY first, CONTENT second. Having comprehensive coverage of what SHOULD exist is more important than having every card fully written.

### Card Lifecycle
- **Phase 1 - Initiation**: Days 1-14, building habit
- **Phase 2 - Maintenance**: Day 15 to goal achievement
- **Phase 3 - De-loading**: Graduation, transition, or discontinuation

### AI Parameters
- Bracket notation `[ ]` for AI-modifiable fields
- AI can adjust within brackets; outside requires clinician approval

---

## CARE PLAN PHILOSOPHY (Critical - Read This First)

### The Care Plan is a GATEWAY to SMART Cards

> **"The Care Plan empowers patients and caregivers with the knowledge and tools to self-direct healthcare at home."**

The Care Plan is NOT:
- A prescription from the doctor to be passively followed
- A list of specialist appointments to attend
- A document only clinicians understand

The Care Plan IS:
- A **patient-facing roadmap** written in language families understand
- A **gateway** to specific SMART Cards and Decks patients can act on TODAY
- An **empowerment tool** that gives families the same knowledge specialists have
- A **living document** that adapts to the patient's progress and circumstances

### Specialists Add Value, But Are Not Gatekeepers

**Traditional Model (Gatekeeper):**
```
Clinician prescribes → Patient attends specialist → Specialist creates plan → Patient follows
```

**CMO Model (Empowerment):**
```
Clinician + Patient create Care Plan → Care Plan CONTAINS the specialist knowledge
Patient has direct access to SMART Cards/Decks → Specialist available for complex cases
```

**Reality check:** Specialist sessions yield a care plan and recommendations. Then it's up to the patient to implement at home. **So give patients the implementation tools directly.**

Example: Instead of "Referral to Occupational Therapist" as the card, the Care Plan includes:
- **The actual OT curriculum** as a SMART Deck (Fine Motor Development Deck, Self-Care Skills Deck)
- **Assessment cards** the parent can use at home
- **Progress tracking** built into the cards
- **When to escalate:** Clear criteria for when specialist consultation IS needed

### Care Plans Are Patient + Caregiver Facing

**Who reads the Care Plan:**
- The patient (when capable)
- Parents/guardians (for pediatric, cognitively impaired)
- Hired caregivers (who implement daily)
- Extended family (who support)

**Language rules:**
- Write at 6th-8th grade reading level
- Use "you" and "your child" not medical jargon
- Remove internal team terminology (90/10 model, Tier 1, etc.)
- Be actionable: "Do this" not "Consider doing this"

### The Patient IS the Main Character (But Not the Only One)

For pediatric, geriatric, or cognitively impaired patients:
- **The patient** is the main character in the health journey
- **The caregivers** are ALSO receiving care through this plan
- **Caregiver education** is a core component, not an afterthought
- **Caregiver wellness** matters - burned out caregivers can't provide good care

### Care Plan Components

Every Care Plan MUST include:

1. **Patient Summary** - Who this is for, in plain language
2. **Family Goals** - What the family wants, in their own words
3. **Clinician Perspective** - What the clinician is focusing on clinically (can be different framing of same goals)
4. **The Actual Plan** - Organized by time interval, with SMART Cards/Decks
5. **Caregiver Section** - Education, support, wellness for those providing care
6. **When to Escalate** - Clear criteria for when to call the clinic/ER
7. **Progress Tracking** - How to know if it's working

---

## v3.0 Architecture (December 2025)

### Three Care Plan Types
| Type | Timeframe | Purpose |
|------|-----------|---------|
| **Chronic** | 12 months, quarterly review | Baseline care plan - always active |
| **Subacute** | Days to weeks | Overlay for emerging issues (trends, symptoms) |
| **Acute** | Minutes to hours | Emergency overlay (critical values, urgent symptoms) |

### 90/10 Self-Directed Model
- **65% Tier 1**: Patient + AI Autonomous (behavioral cards, pre-authorized adjustments)
- **25% Tier 2**: Patient + AI + Allied Health (dietitian, pharmacist review)
- **10% Tier 3**: Physician Required (new prescriptions, complex cases)

### Multi-Specialty AI Selection
14 specialist agents query the card library, coordinated by PCP AI:
- Cardiologist AI, Endocrinologist AI, Neurologist AI, Pulmonologist AI
- Nephrologist AI, MSK/PT AI, Immunologist AI, OB-GYN/Uro AI
- Nutritionist AI, Exercise Physiology AI, Sleep Medicine AI
- Mental Health AI, Pharmacist AI, Preventive Care AI

### Clinical Intent Hierarchy (Selection Priority)
1. **Stabilize** - Address acute/unstable issues FIRST
2. **Restore** - Rebuild lost function
3. **Protect** - Prevent future problems
4. **Optimize** - Enhance beyond baseline (ONLY when stable)

### 3-Card Maximum Rule
- Never more than 3 active behavioral cards at any time
- Medications don't count against behavioral limit
- Cards must graduate/transition before new cards unlock

---

## File Naming Conventions

| Pattern | Meaning |
|---------|---------|
| `TIER5_*.md` | Individual card library |
| `*_v2.md` | Version 2 (atomic cards) |
| `*_LIBRARY.md` | Reference library |
| `*_SPEC.md` | Technical specification |

---

## Common Tasks

### Before modifying any specification:
1. Check `SOURCE_DOCUMENT_REGISTRY.md` for canonical source
2. Read the source document
3. Cite sources in modifications

### When adding cards:
1. Check existing library for redundancy
2. Use proper Card ID format (e.g., `MOV_NEAT_001`)
3. Add appropriate tags (#micro, #biohacking, etc.)
4. Update card count in summary table

### When updating documents:
1. Increment version number
2. Add changelog entry at bottom
3. Update `SOURCE_DOCUMENT_REGISTRY.md` if canonical source

---

## Tags System

### Action Tags
| Tag | Meaning |
|-----|---------|
| `#micro` | Quick actions (seconds to minutes) |
| `#NEAT` | Non-Exercise Activity Thermogenesis |
| `#biohacking` | Evidence-based optimization |
| `#circadian` | Circadian rhythm interventions |
| `#seated` | Can be done while sitting |
| `#mindful` | Mindfulness-based |

### Age Classification Tags (REQUIRED for age-specific cards)

Cards apply to ALL ages by default. Only add age tags when a card is age-SPECIFIC.

| Tag | Age Range | Life Stage | Notes |
|-----|-----------|------------|-------|
| `#infant` | 0-1 years | Infancy | Parent/caregiver executes |
| `#toddler` | 1-3 years | Toddlerhood | Parent/caregiver executes |
| `#preschool` | 3-5 years | Early Childhood | Parent/caregiver executes, child participates |
| `#school-age` | 6-12 years | Middle Childhood | Child executes with supervision |
| `#adolescent` | 13-17 years | Adolescence | Teen executes, parent supports |
| `#adult` | 18-64 years | Adulthood | Default - rarely needs tag |
| `#older-adult` | 65-79 years | Later Adulthood | May need modifications |
| `#geriatric` | 80+ years | Advanced Age | Often needs modifications |
| `#prenatal` | Pregnancy | Prenatal | Pregnancy-specific |
| `#postpartum` | 0-1 year post-birth | Postpartum | Recovery period |

**Age Tag Rules:**
1. Most cards apply to adults by default - no tag needed
2. Pediatric cards (`#infant` through `#school-age`) often need `#caregiver-executed` tag
3. Cards can have MULTIPLE age tags if they span ranges (e.g., `#toddler #preschool`)
4. Age-specific VARIANTS of existing cards use same Card ID base + age suffix
   - Example: `NUT_MEAL_001` (adult) → `NUT_MEAL_001_PED` (pediatric variant)
5. Completely unique pediatric cards get their own ID with `_PED` suffix

### Executor Tags (WHO does the action)
| Tag | Meaning |
|-----|---------|
| `#self-directed` | Patient executes independently (default for adults) |
| `#caregiver-executed` | Caregiver performs action FOR patient |
| `#caregiver-supervised` | Patient does action, caregiver supervises |
| `#clinician-assisted` | Requires clinician involvement |

**Pediatric Executor Rule:**
- `#infant`, `#toddler`: Always `#caregiver-executed`
- `#preschool`: Usually `#caregiver-executed` or `#caregiver-supervised`
- `#school-age`: Mix of `#caregiver-supervised` and `#self-directed`
- `#adolescent`: Usually `#self-directed` with parent support

---

## Versioning Philosophy

**ALL documents are pre-release (v0.x) until first production deployment with real patients.**

| Version | Meaning |
|---------|---------|
| **v0.x** | Pre-release/development (current state) |
| **v1.0** | First production deployment with real patients |
| **v2.0+** | Major production updates |

**Current Versions (All Pre-release):**
- Universal Card Template: v0.4
- Metformin Reference Card: v0.4
- Integration Architecture: v0.3
- Multi-Agent AI Platform: v0.3
- Master Roadmap: v0.2
- All other documents: v0.1-0.2

**Total Behavioral Cards**: 1,023 (Movement 378, Nutrition 195, Recovery 141, Environment 137, Emotion 118, Micro-Learning 54)
*Each pillar now includes: Treatment/Intervention + Monitoring + Assessment + Preparation + Maintenance action types*
*Mind-Body library dissolved; cards redistributed to Movement, Recovery, and Emotion pillars*
*December 14, 2025: Added 86 pediatric cards (27 Nutrition, 27 Recovery, 32 Emotion) with age classification tags*

---

## PROACTIVE BEHAVIORS (Automatic - No User Request Needed)

### At Session Start
Claude MUST automatically:
1. **Read this file** (CLAUDE.md) for project context
2. **Check SOURCE_DOCUMENT_REGISTRY.md** for current versions
3. **Note any files modified** in the git status

### AUTO-CONTEXT TRIGGERS (Critical - Prevents Information Loss)

When user mentions ANY of these topics, Claude MUST automatically search and read ALL related files BEFORE responding:

| User Mentions | Auto-Search Locations | Key Files to Read |
|---------------|----------------------|-------------------|
| "Care Plan" | `CMO - PERFORMANCE MEDICINE/clinical-protocols/`, Root `*care-plan*.md` | CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md, CARE_PLAN_DIGITAL_INTERFACE_SPEC.md, universal-care-plan-DETAILED-template.md, example-care-plan-84yo-female.md |
| "SMART Card", "SMART Deck" | `CMO - SMART SYSTEM/docs/core/` | CARD_TYPE_SPECIFICATIONS.md, UNIVERSAL_CARD_TEMPLATE.md, CARD_LIFECYCLE_AND_AI_PARAMETERS.md |
| "Dashboard", "Health Overview" | `CMO - DATA INPUT/`, Root integration specs | health-matrix-framework.md, INTEGRATION_ARCHITECTURE.md |
| "AI Agent", "Multi-Agent" | Root master files | MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md, CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md |
| "Intake", "Patient Form" | `CMO - DATA INPUT/` | Patient intake forms, medical history libraries |
| "Movement", "Exercise", "Yoga", "Tai Chi" | `CMO - SMART SYSTEM/library/behavioral/` | TIER5_MOVEMENT_EXERCISE_v2.md |
| "Nutrition", "Diet" | `CMO - SMART SYSTEM/library/behavioral/` | TIER5_NUTRITION_v2.md |
| "Recovery", "Sleep" | `CMO - SMART SYSTEM/library/behavioral/` | TIER5_RECOVERY_v2.md |
| "Emotion", "Mental Health", "Stress", "Meditation" | `CMO - SMART SYSTEM/library/behavioral/` | TIER5_EMOTION_v2.md (to be created) |
| "Environment", "Social", "Relationships" | `CMO - SMART SYSTEM/library/behavioral/` | TIER5_ENVIRONMENTAL_SOCIAL_v2.md |
| "Life Stage" | `CMO - PERFORMANCE MEDICINE/` | life-stage-health-goals.md, life-stage-care-plan-templates.md |
| "Preventive Care" | `CMO - PERFORMANCE MEDICINE/clinical-protocols/` | preventive-care-integration-matrix.md |
| "Library", "Card Coverage", "Card Gaps" | `CMO - SMART SYSTEM/library/`, `CMO - SMART SYSTEM/tier5_cards/` | All TIER5_*.md files, T3.1_prescription_pharmaceuticals.md, CLAUDE.md (Library Completion Status section) |

**Failure to auto-search = Information Loss.** The user cannot remember where everything is. Claude MUST be comprehensive.

### BEFORE CREATING ANY NEW FILE

Claude MUST run a mental `/preflight` check:
1. **Search** for existing files on the same topic
2. **Read** SOURCE_DOCUMENT_REGISTRY.md for canonical sources
3. **List** what already exists to the user
4. **Ask** if this should be a NEW file or an UPDATE to existing
5. **Identify** all files that will need updating when this is created
6. **TELL THE USER** what was found before proceeding

**DO NOT create new specifications without showing the user what already exists first.**

### After ANY File Modification
Claude MUST automatically:
1. **Update card counts** - If a TIER5 library was edited, update:
   - The library's GRAND SUMMARY table
   - CLAUDE.md "Total Behavioral Cards" line
   - SOURCE_DOCUMENT_REGISTRY.md card count column
   - 00_START_HERE.md if counts changed significantly
2. **Increment version numbers** - Update footer version if content changed
3. **Check cross-references** - Verify no broken links created

### After Updating a Template/Specification
Claude MUST automatically:
1. **Update Reference Implementations** - If UNIVERSAL_CARD_TEMPLATE.md is updated:
   - Update MED_DM_BIG_001_Metformin_IR.md (the reference implementation)
   - Update version number and template reference in footer
2. **Update Dependent Documents** - Check Related Documents links in the modified file and update those too if they reference the changed content
3. **Propagate Version Numbers** - If a spec goes v2.0 → v3.0, update all files that cite that version

### After Creating New Files
Claude MUST automatically:
1. **Add to SOURCE_DOCUMENT_REGISTRY.md** if it's a canonical source
2. **Update 00_START_HERE.md** file structure if it's a master-level file
3. **Update CLAUDE.md** if it affects project structure

### After Deleting Files
Claude MUST automatically:
1. **Remove from SOURCE_DOCUMENT_REGISTRY.md**
2. **Search for broken references** in other files
3. **Update file counts** in CLAUDE.md

### Consistency Checks (Run Automatically When Relevant)
| Trigger | Check | Fix |
|---------|-------|-----|
| Mentioned card count | Verify against library totals | Update if wrong |
| Referenced deleted file | Check if file exists | Remove reference or note issue |
| Version mentioned | Verify current version | Update if outdated |
| Card added to library | Check subtotals and grand total | Update counts |

### Self-Healing Rules
- **Never leave inconsistent state** - If you update one file, update ALL dependent files in the same response
- **Cite sources always** - Before writing about a topic, read the canonical source first
- **Fail-safe on counts** - If unsure of a count, READ the actual file rather than trusting memory

### AUTOMATIC FILE ORGANIZATION (Librarian Behavior)

**Before creating ANY new file, Claude MUST:**

1. **Identify the correct section** - Which of the 4 sections does this belong to?
   - Section 1 (DATA INPUT): Patient intake, questionnaires, history libraries → `CMO - DATA INPUT/`
   - Section 2 (HEALTH OVERVIEW): Dashboard specs, health matrix → `CMO - DATA INPUT/`
   - Section 3 (SMART SYSTEM): Cards, decks, card specs, behavioral libraries → `CMO - SMART SYSTEM/`
   - Section 4 (PERFORMANCE MEDICINE): Clinical protocols, care plans, guidelines → `CMO - PERFORMANCE MEDICINE/`
   - **Master/Integration docs**: Root level only if they span multiple sections

2. **Check existing folder structure** - Run `ls` on the target folder to see subfolders
   - DON'T create files at folder root if subfolders exist
   - MATCH existing organization patterns

3. **File Type → Location Map**:
   | File Type | Correct Location |
   |-----------|------------------|
   | SMART Card (individual) | `CMO - SMART SYSTEM/tier5_cards/[type]/` |
   | Card Library (TIER5_*) | `CMO - SMART SYSTEM/library/behavioral/[pillar]/` |
   | Card Spec/Template | `CMO - SMART SYSTEM/docs/core/` |
   | Care Plan (patient) | `CMO - PERFORMANCE MEDICINE/care-plans/` |
   | Care Plan (template) | `CMO - PERFORMANCE MEDICINE/clinical-protocols/` |
   | Intake Form | `CMO - DATA INPUT/forms/` |
   | Medical History Library | `CMO - DATA INPUT/libraries/` |
   | Integration Spec | Root (if cross-section) or relevant section `/docs/` |

4. **Patient-specific files** - NEVER at project root
   - Care Plans: `CMO - PERFORMANCE MEDICINE/care-plans/[patient-id]/`
   - Patient registries: With the care plan

**After creating any file, Claude MUST ask:**
- "Is this file in the correct location according to the 4-section structure?"
- "Did I follow the existing folder patterns?"
- "Would a human looking for this file know where to find it?"

**If unsure, ASK THE USER before creating the file.**

### Dependency Chains (Update These Together)

**Card Count Chain:**
```
TIER5_*_v2.md (source of truth for card counts)
    ↓ updates
SOURCE_DOCUMENT_REGISTRY.md (card count column)
    ↓ updates
CLAUDE.md (Total Behavioral Cards line)
    ↓ updates (if significant)
00_START_HERE.md (behavioral card total)
```
**When you modify a TIER5 file, you MUST update all 4 files in one session.**

**Template → Reference Implementation Chain:**
```
UNIVERSAL_CARD_TEMPLATE.md (source of truth for card structure)
    ↓ MUST update
MED_DM_BIG_001_Metformin_IR.md (reference implementation)
    ↓ check for alignment
All other existing SMART Cards (if new required fields added)
```
**When you modify the Universal Template, you MUST update the Metformin reference card.**

**Architecture Version Chain:**
```
CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md (v3.0 architecture source)
    ↓ updates
INTEGRATION_ARCHITECTURE.md
MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md
MASTER_ROADMAP.md
00_START_HERE.md
CLAUDE.md
SOURCE_DOCUMENT_REGISTRY.md
```
**When you add major architecture concepts, you MUST update ALL master-level documents.**

---

## Custom Slash Commands

### Context & Pre-Work (NEW)
| Command | Purpose |
|---------|---------|
| `/context [topic]` | **Load ALL context before working on a topic** - reads CLAUDE.md, SOURCE_DOCUMENT_REGISTRY.md, and ALL files related to the topic |
| `/preflight [task]` | **Pre-flight check before creating new content** - searches for existing files, identifies what will need updating, prevents redundancy |

### Document Management
| Command | Purpose |
|---------|---------|
| `/audit` | Comprehensive document audit - find duplicates, orphans, version conflicts |
| `/sync` | Synchronize documents - verify counts, update registry |
| `/cleanup` | Execute cleanup - delete obsolete files after audit |
| `/status` | Quick snapshot - file count, card totals, recent changes (30 sec) |
| `/update-registry` | Sync SOURCE_DOCUMENT_REGISTRY.md with current files |

### Card Operations
| Command | Purpose |
|---------|---------|
| `/find-card [term]` | Search for cards across all libraries by name, ID, or tag |
| `/add-cards [library] [category]` | Guided workflow for adding new cards with duplicate checking |
| `/build-deck [purpose]` | Assemble a SMART Deck from existing cards for a condition/goal |

### Session Management
| Command | Purpose |
|---------|---------|
| `/session-log` | Log changes made this session for continuity (run at end of session) |

### Recommended Workflow
1. **Start of session**: `/status` for quick orientation
2. **Before working on a topic**: `/context [topic]` to load all related files
3. **Before creating new files**: `/preflight [task]` to check for redundancy
4. **Before adding cards**: `/find-card` to check for duplicates
5. **After making changes**: `/sync` to verify consistency
6. **End of session**: `/session-log` to capture what was done
7. **Periodically**: `/audit` + `/cleanup` for maintenance

---

## Cleanup Completed (December 7, 2025)

**Files Deleted (14 total):**

### Obsolete v1 TIER5 Files (5 files)
- ~~`TIER5_MOVEMENT_EXERCISE.md`~~ → Replaced by v2 (150 cards)
- ~~`TIER5_RECOVERY.md`~~ → Replaced by v2 (78 cards)
- ~~`TIER5_NUTRITION.md`~~ → Replaced by v2 (102 cards)
- ~~`TIER5_ENVIRONMENTAL_SOCIAL.md`~~ → Replaced by v2 (85 cards)
- ~~`TIER5_MIND_BODY.md`~~ → Replaced by v2 (62 cards)

### Archived Files (2 files)
- ~~`_ARCHIVED_LIFESTYLE_PILLAR_QUESTIONNAIRES_v1.md`~~
- ~~`_ARCHIVED_LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md`~~

### Root-Level Planning Documents (7 files)
- ~~`aerobic_exercise.md`~~ → Covered by TIER5_MOVEMENT_EXERCISE_v2.md
- ~~`dietary_patterns.md`~~ → Covered by TIER5_NUTRITION_v2.md (diets = DECKS)
- ~~`eating_behaviors_meal_planning.md`~~ → Covered by TIER5_NUTRITION_v2.md
- ~~`strength_flexibility_balance.md`~~ → Covered by TIER5_MOVEMENT_EXERCISE_v2.md
- ~~`sleep_stress_breathing.md`~~ → Covered by TIER5_RECOVERY_v2.md
- ~~`specific_food_focus.md`~~ → Covered by TIER5_NUTRITION_v2.md
- ~~`mindbody_microlearning.md`~~ → Covered by TIER5_MIND_BODY_v2.md + TIER5_MICRO_LEARNING.md

**Result:** 152 → 138 files (-14 files, -9.2%)

---

## Do NOT:
- Create redundant cards without checking existing libraries
- Use "stacks" - call them "decks"
- Create new subcategories for micro-actions or biohacking (use tags instead)
- Modify specifications without reading source documents first
- Create new files without adding to SOURCE_DOCUMENT_REGISTRY.md if canonical
- Delete files without running `/audit` first
