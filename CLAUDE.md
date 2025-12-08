# CMO Platform - Project Context for Claude

## Project Overview

This is the **Comprehensive Medical Optimization (CMO) Platform** - a self-directed healthcare system enabling patients to manage their own health with AI assistance and clinician oversight.

**Philosophy**: Patients are their own primary healthcare providers. Clinicians are guidance counselors who guide, counsel, and redirect.

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
- 12 card types (Medications, Testing, Imaging, Procedures, DME, Referrals, Nutrition, Movement, Recovery, Mind-Body, Environmental/Social, Micro-Learning)
- Behavioral libraries (Movement, Recovery, Nutrition, Environmental, Mind-Body)
- Card lifecycle: Initiation → Maintenance → De-loading

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
| `INTEGRATION_ARCHITECTURE.md` | How sections connect | Root |
| `CARD_TYPE_SPECIFICATIONS.md` | All 12 card types | SMART SYSTEM/docs/core/ |

---

## Key Specifications

### SMART Cards
- **477 total cards** across 5 behavioral libraries
- Each card = ONE atomic action
- Cards combine into DECKS
- Template: `UNIVERSAL_CARD_TEMPLATE.md`

### Card Lifecycle
- **Phase 1 - Initiation**: Days 1-14, building habit
- **Phase 2 - Maintenance**: Day 15 to goal achievement
- **Phase 3 - De-loading**: Graduation, transition, or discontinuation

### AI Parameters
- Bracket notation `[ ]` for AI-modifiable fields
- AI can adjust within brackets; outside requires clinician approval

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

| Tag | Meaning |
|-----|---------|
| `#micro` | Quick actions (seconds to minutes) |
| `#NEAT` | Non-Exercise Activity Thermogenesis |
| `#biohacking` | Evidence-based optimization |
| `#circadian` | Circadian rhythm interventions |
| `#seated` | Can be done while sitting |
| `#mindful` | Mindfulness-based |

---

## Current Version
- **Behavioral Libraries**: v2.1 (December 7, 2025)
- **Universal Card Template**: v2.0
- **Total Behavioral Cards**: 531 (Movement 150, Nutrition 102, Recovery 78, Mind-Body 62, Environmental 85, Micro-Learning 54)

---

## PROACTIVE BEHAVIORS (Automatic - No User Request Needed)

### At Session Start
Claude MUST automatically:
1. **Read this file** (CLAUDE.md) for project context
2. **Check SOURCE_DOCUMENT_REGISTRY.md** for current versions
3. **Note any files modified** in the git status

### After ANY File Modification
Claude MUST automatically:
1. **Update card counts** - If a TIER5 library was edited, update:
   - The library's GRAND SUMMARY table
   - CLAUDE.md "Total Behavioral Cards" line
   - SOURCE_DOCUMENT_REGISTRY.md card count column
   - 00_START_HERE.md if counts changed significantly
2. **Increment version numbers** - Update footer version if content changed
3. **Check cross-references** - Verify no broken links created

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

### Dependency Chain (Update These Together)
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

---

## Custom Slash Commands

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
2. **Before adding cards**: `/find-card` to check for duplicates
3. **After making changes**: `/sync` to verify consistency
4. **End of session**: `/session-log` to capture what was done
5. **Periodically**: `/audit` + `/cleanup` for maintenance

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
