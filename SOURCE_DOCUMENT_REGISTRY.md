# SOURCE DOCUMENT REGISTRY & VERIFICATION PROTOCOL
**Version:** 0.7
**Date:** 2025-12-14
**Status:** Pre-release (v1.0 = first production deployment)
**Purpose:** Prevent information loss by maintaining canonical source documents for every critical specification

---

## THE PROBLEM

**Information loss occurs when:**
1. Working from memory instead of reading source documents
2. Sub-project specifications buried in deep folder structures
3. No clear "source of truth" for critical definitions
4. Changes made to one document don't propagate to dependent documents

**Example of What Went Wrong:**
- Asked to document de-prescribing for "all card types"
- Listed 9 types from memory instead of reading [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md)
- Missed 3 types (Imaging Studies, DME, Environmental & Social Health)
- Only caught error when later re-reading source document

---

## THE SOLUTION: CANONICAL SOURCE DOCUMENT SYSTEM

### **Rule 1: Every Critical Specification Has ONE Canonical Source**

**No duplicate definitions.** If you need to reference a specification, link to the canonical source - don't copy/paste.

### **Rule 2: Before Writing About a Topic, READ the Source Document**

**NEVER work from memory.** Always open and read the canonical source first.

### **Rule 3: Cite Source Documents in Every Derivative Work**

**Every document that uses information from another document MUST cite it prominently.**

---

## CANONICAL SOURCE REGISTRY

### **Platform-Wide Specifications**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **4-Section Workflow** | [INTEGRATION_ARCHITECTURE.md](INTEGRATION_ARCHITECTURE.md) | 3.0 | How all 4 sections work together + 90/10 Self-Directed Model |
| **3 Care Plan Types** | [CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md](CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md) | 1.0 | Chronic/Subacute/Acute care plans, Data Reactivity Model |
| **Care Plan Digital Interface** | [CARE_PLAN_DIGITAL_INTERFACE_SPEC.md](CARE_PLAN_DIGITAL_INTERFACE_SPEC.md) | 0.1 | **NEW** Time-interval views (Daily/Weekly/Monthly/Quarterly/Annual), Card list display, Interactive expansion |
| **Multi-Specialty AI Selection** | [CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md](CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md) | 1.0 | **NEW** 14+ specialist agents, PCP AI orchestrator, Clinical Intent Hierarchy |
| **Multi-Agent AI Platform** | [MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md](MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md) | 3.0 | 5 core agents + 14 specialists, 4-tier automation |
| **90/10 Self-Directed Model** | [CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md](CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md) | 1.0 | **NEW** 90% patient autonomous, 10% clinician intervention |
| **8 Health Systems** | [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md) | Latest | Neurological, Cardiovascular, Respiratory, Metabolic, Renal, Musculoskeletal, Immune, Reproductive/Endocrine |
| **3 Clinical Domains** | [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md) | Latest | Structure, Function, Risk |
| **5 Lifestyle Pillars** | [LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1](CMO - DATA INPUT/04_LIFESTYLE_ASSESSMENT/LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1_OPTIMIZED.md) | 2.1 | Nutrition, Movement, Sleep/Recovery, Mental/Emotional, Environment/Social |
| **Capacity, Resilience, Flexibility** | [capacity-resilience-flexibility.md](CMO - PERFORMANCE MEDICINE/architecture/capacity-resilience-flexibility.md) | Latest | Performance Medicine targets |

---

### **Section 1: Data Input Management**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **132 Tier 1 Diagnoses** | [MEDICAL_HISTORY_TIER1_LIBRARY_v1.1](CMO - DATA INPUT/03_MEDICAL_HISTORY/MEDICAL_HISTORY_TIER1_LIBRARY_v1.1_INTAKE_READY.md) | 1.1 | All common diagnoses with ICD-10 codes, score modifiers |
| **Parameter Normalization Methods** | [PARAMETER_NORMALIZATION_v2.md](CMO - DATA INPUT/01_CLINICAL_LOGIC/PARAMETER_NORMALIZATION_v2.md) | 2.0 | 5 normalization methods, 150 MVP parameters |
| **Patient Intake Form** | [PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md](CMO - DATA INPUT/03_MEDICAL_HISTORY/PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md) | Latest | Complete database schema, validation rules |
| **Lifestyle Questionnaires** | [LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1](CMO - DATA INPUT/04_LIFESTYLE_ASSESSMENT/LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1_OPTIMIZED.md) | 2.1 | Questions, scoring, clinical interpretation |

---

### **Section 2: Health Overview Dashboard**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **Scoring Algorithms** | [SYSTEM_DOMAIN_SCORING_v2.md](CMO - DATA INPUT/01_CLINICAL_LOGIC/SYSTEM_DOMAIN_SCORING_v2.md) | 2.0 | 24-cell aggregation formulas |
| **Biological Age Calculation** | [BIOLOGICAL_AGE_SPEC_v1_1.md](CMO - DATA INPUT/01_CLINICAL_LOGIC/BIOLOGICAL_AGE_SPEC_v1_1.md) | 1.1 | Modified PhenoAge methodology |
| **Dashboard UI Specifications** | [DASHBOARD_LEVEL1_SPEC_v1_1.md](CMO - DATA INPUT/06_DASHBOARD_SPECS/DASHBOARD_LEVEL1_SPEC_v1_1.md) | 1.1 | Level 1 (Hero), Level 2 (Systems), Level 3 (Detailed) |
| **Critical Alerts** | [CRITICAL_ALERTS_v1_1.md](CMO - DATA INPUT/05_ALERTS_SAFETY/CRITICAL_ALERTS_v1_1.md) | 1.1 | Life-threatening thresholds |

---

### **Section 3: SMART Card/Deck System**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **12 Card Types** | [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) | 0.2 | **ALL 12 types** - MUST be read before writing about card types |
| **Universal Card Template** | [UNIVERSAL_CARD_TEMPLATE.md](CMO - SMART SYSTEM/docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) | 0.5 | Patient Views (Condensed/Expanded) + Evidence (brief) + Clinician & AI Reference + YAML Metadata |
| **Card Lifecycle & AI Parameters** | [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](CMO - SMART SYSTEM/docs/core/CARD_LIFECYCLE_AND_AI_PARAMETERS.md) | 1.0 | **NEW** - Bracket `[ ]` notation for AI-modifiable fields, 3-phase lifecycle |
| **Card De-prescribing & AI Oversight** | [CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md](CMO - SMART SYSTEM/CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md) | 1.1 | De-prescribing for ALL 12 types, AI agent (Dr. ADAPT), patient autonomy levels |
| **Card Generation Specification** | [CARD_GENERATION_SPECIFICATION.md](CMO - SMART SYSTEM/docs/core/CARD_GENERATION_SPECIFICATION.md) | 1.0 | **DETERMINISTIC GENERATION** - Seed inputs, canonical sources, phrase libraries, validation rules |
| **DME + Monitoring Workflow** | [DME_MONITORING_WORKFLOW_PATTERN.md](CMO - SMART SYSTEM/docs/core/DME_MONITORING_WORKFLOW_PATTERN.md) | 1.0 | **TWO-STEP PATTERN** - DME acquisition + ongoing monitoring as separate cards |
| **Library Hierarchy** | [LIBRARY_TIER_STRUCTURE.md](CMO - SMART SYSTEM/LIBRARY_TIER_STRUCTURE.md) | Latest | Tier 1-5 organization |
| **Evidence Grading** | [EVIDENCE_SECTION_SPECIFICATION.md](CMO - SMART SYSTEM/docs/core/EVIDENCE_SECTION_SPECIFICATION.md) | 1.0 | A/B/C evidence grades, required sources, trust elements |
| **Autonomy Tiers & AI Agents** | [AUTONOMY_AND_AI_AGENT_SPECIFICATION.md](CMO - SMART SYSTEM/docs/core/AUTONOMY_AND_AI_AGENT_SPECIFICATION.md) | 1.0 | 4-tier autonomy, AI agent ecosystem, legal sign-off workflows |

---

### **Section 3: SMART Card Libraries (Tier 5 Enumerations)**

#### **Behavioral Card Libraries - THE 5 LIFESTYLE PILLARS (v2.4 - Updated 2025-12-14)**

| Pillar | Library File | Current Version | Card Count | Coverage |
|--------|--------------|----------------|------------|----------|
| **1. Nutrition** | [TIER5_NUTRITION_v2.md](CMO - SMART SYSTEM/library/behavioral/nutrition/TIER5_NUTRITION_v2.md) | 2.2 | 168 cards | ~67% |
| **2. Movement** | [TIER5_MOVEMENT_EXERCISE_v2.md](CMO - SMART SYSTEM/library/behavioral/movement/TIER5_MOVEMENT_EXERCISE_v2.md) | 2.4 | 378 cards | ~84% |
| **3. Recovery** | [TIER5_RECOVERY_v2.md](CMO - SMART SYSTEM/library/behavioral/recovery/TIER5_RECOVERY_v2.md) | 2.3 | 114 cards | ~76% |
| **4. Emotion** | [TIER5_EMOTION_v2.md](CMO - SMART SYSTEM/library/behavioral/emotion/TIER5_EMOTION_v2.md) | 2.1 | 86 cards | ~57% |
| **5. Environment** | [TIER5_ENVIRONMENTAL_SOCIAL_v2.md](CMO - SMART SYSTEM/library/behavioral/environmental_social/TIER5_ENVIRONMENTAL_SOCIAL_v2.md) | 2.3 | 137 cards | ~69% |
| **Educational** | [TIER5_MICRO_LEARNING.md](CMO - SMART SYSTEM/library/behavioral/micro_learning/TIER5_MICRO_LEARNING.md) | 1.0 | 54 cards | ~7% |

**TOTAL BEHAVIORAL CARDS: 883** (excluding Micro-Learning educational content)
**WITH MICRO-LEARNING: 937 cards**

**v2.4 MAJOR EXPANSION (2025-12-14):**
- **ALL 5 ACTION TYPES now in every pillar:**
  - Treatment/Intervention (original cards - behaviors, exercises, techniques)
  - Monitoring (tracking metrics, logging data)
  - Assessment/Screening (standardized tests, questionnaires)
  - Preparation (pre-activity setup)
  - Maintenance (equipment care, habit sustainability)
- **Movement expanded:** Yoga (23→92), Tai Chi (6→37), Qigong (4→36)
- **Mind-Body library DELETED** - Cards redistributed to Movement, Emotion pillars

**v2.3 RESTRUCTURING (Earlier 2025-12-14):**
- **Mind-Body library DISSOLVED** - Cards redistributed to correct pillars
- **Duplicate cards removed** across all libraries
- **Cross-references added** between pillars for related cards
- Each card belongs to exactly ONE pillar (no duplicates)

**PILLAR PLACEMENT RULES:**
- **Movement** = Physical exertion (exercise, poses, physical movements)
- **Recovery** = Physical rest/restoration (sleep, thermal, physical relaxation)
- **Emotion** = Mental/psychological (meditation, cognitive, mood, stress management)
- **Environment** = External factors (social, surroundings, substances, workspace)
- **Nutrition** = Food/drink behaviors

**IMPORTANT PRINCIPLES:**
- **ONE ACTION = ONE CARD** (if you can't describe it as verb + object, it's not a card)
- Yoga, Tai Chi, Qigong = DECKS (collections of movement cards)
- Each yoga pose, each tai chi movement = individual CARD
- Duration/intensity/frequency are TEMPLATE PARAMETERS, not separate cards
- Supplements belong in Medication category, not Behavioral

#### **Medical Card Libraries (In Progress)**

| Topic | Canonical Source | Current Version | Card Count | Status |
|-------|-----------------|----------------|------------|--------|
| **Prescription Medications** | [T3.1_prescription_pharmaceuticals.md](CMO - SMART SYSTEM/tier5_cards/medications/T3.1_prescription_pharmaceuticals.md) | 0.1 | 484 entries | 🟡 Cardio/DM/Resp only |
| **Metformin Reference Card** | [MED_DM_BIG_001_Metformin_IR.md](CMO - SMART SYSTEM/tier5_cards/medications/MED_DM_BIG_001_Metformin_IR.md) | 0.5 | 1 full card | 🟢 Reference implementation |
| **Diagnostic Testing** | Not created | - | 0 | 🔴 Not started |
| **Imaging Studies** | Not created | - | 0 | 🔴 Not started |
| **Procedures** | Not created | - | 0 | 🔴 Not started |
| **DME** | Not created | - | 0 | 🔴 Not started |
| **Referrals** | Not created | - | 0 | 🔴 Not started |

**NOTE:** The medical card libraries listed in previous versions were PLANNED but NOT YET CREATED. Only T3.1_prescription_pharmaceuticals.md and the Metformin reference card exist. See CLAUDE.md "SMART CARD LIBRARY COMPLETION STATUS" for full gap analysis.

---

### **Section 4: Performance Medicine Philosophy**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **Health Matrix Framework** | [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md) | Latest | 8 systems × 3 domains model |
| **Care Planning Methodology** | [comprehensive-care-planning-methodology.md](CMO - PERFORMANCE MEDICINE/clinical-protocols/comprehensive-care-planning-methodology.md) | Latest | 6-phase workflow |
| **Life-Stage Templates** | [life-stage-care-plan-templates.md](CMO - PERFORMANCE MEDICINE/clinical-protocols/life-stage-care-plan-templates.md) | Latest | 9 age-based templates |
| **Evidence Base** | [primary-sources.md](CMO - PERFORMANCE MEDICINE/evidence-base/primary-sources.md) | Latest | Clinical guideline sources |

---

## VERIFICATION PROTOCOL

### **Before Writing About ANY Topic:**

**STEP 1: Identify Canonical Source**
- Look up topic in this registry
- Find the canonical source document

**STEP 2: Read Source Document**
- Open and read the ENTIRE relevant section
- Note version number
- Copy exact terminology/definitions

**STEP 3: Cite Source in Your Document**
- Add citation at top: "Source: [filename](path) v.X"
- If you quote/reference, link back to source

**STEP 4: Validate Against Source**
- Before finalizing, cross-check your work against source
- Ensure no omissions (like missing 3 card types!)

---

## EXAMPLE: HOW TO USE THIS PROTOCOL

### **Bad Example (What I Did Wrong):**

**Task:** Document de-prescribing for all card types

**What I Did:**
- Worked from memory
- Listed 9 types
- Missed 3 types (Imaging, DME, Environmental & Social Health)

**Result:** Incomplete specification

---

### **Good Example (What I Should Have Done):**

**Task:** Document de-prescribing for all card types

**STEP 1:** Look up "12 Card Types" in Source Document Registry
- Canonical Source: [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) v2.0

**STEP 2:** Open and read CARD_TYPE_SPECIFICATIONS.md
- See Table on lines 11-24
- Count 12 types (not 9!)
- Copy exact list with icons

**STEP 3:** Cite in my document header
```markdown
---
**Source:** CARD_TYPE_SPECIFICATIONS.md v2.0
**Topic:** De-prescribing criteria for all 12 card types
---
```

**STEP 4:** Write de-prescribing spec for ALL 12 types
- Check off each type as I complete it
- Result: Nothing missed!

---

## CRITICAL TOPICS REQUIRING SOURCE VERIFICATION

### **When Writing About These Topics, ALWAYS Read Source First:**

**v3.0 Architecture (NEW 2025-12-12):**
- [ ] 3 Care Plan Types → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md (CRITICAL!)
- [ ] 90/10 Self-Directed Model → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md
- [ ] Multi-Specialty AI Selection → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md
- [ ] Multi-Agent AI Platform → MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md v3.0
- [ ] Clinical Intent Hierarchy → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md

**Platform Architecture:**
- [ ] 4-Section Workflow → INTEGRATION_ARCHITECTURE.md v3.0
- [ ] 8 Health Systems → health-matrix-framework.md
- [ ] 3 Clinical Domains → health-matrix-framework.md
- [ ] 5 Lifestyle Pillars → LIFESTYLE_PILLAR_QUESTIONNAIRES

**Card System:**
- [ ] 12 Card Types → CARD_TYPE_SPECIFICATIONS.md (CRITICAL - often missed!)
- [ ] Card Template → UNIVERSAL_CARD_TEMPLATE.md
- [ ] Card Lifecycle → CARD_LIFECYCLE_AND_AI_PARAMETERS.md
- [ ] Evidence Grades → EVIDENCE_SECTION_SPECIFICATION.md

**Clinical Data:**
- [ ] 132 Diagnoses → MEDICAL_HISTORY_TIER1_LIBRARY
- [ ] 150 Parameters → PARAMETER_NORMALIZATION_v2.md
- [ ] Scoring Formulas → SYSTEM_DOMAIN_SCORING_v2.md

---

## PREVENTING INFORMATION DRIFT

### **Problem:** Source document updated, but dependent documents not

**Solution: Dependency Tracking**

When you UPDATE a canonical source document:

1. **Check Dependency Registry** (see INTEGRATION_ARCHITECTURE.md Appendix B)
2. **Identify all dependent documents**
3. **Update ALL dependent documents** (or mark as "pending update")
4. **Increment version numbers** on all updated files
5. **Document in changelog**

---

## CANONICAL SOURCE QUICK REFERENCE CARD

**Keep this visible when working:**

```
BEFORE WRITING ABOUT...          MUST READ...
─────────────────────────────────────────────────────────────
** NEW v3.0 ARCHITECTURE (2025-12-12) **
3 Care Plan Types                → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md
  • Chronic (12-month baseline)
  • Subacute (days-weeks overlay)
  • Acute (emergency overlay)
Care Plan Digital Interface      → CARE_PLAN_DIGITAL_INTERFACE_SPEC.md (NEW!)
  • Time-interval views (Daily/Weekly/Monthly/Quarterly/Annual)
  • Card list display with expandable AT-A-GLANCE
  • Contextual guidance per interval
90/10 Self-Directed Model        → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md (NEW!)
Multi-Specialty AI Selection     → CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md (NEW!)
  • 14 specialist agents
  • PCP AI orchestrator
  • Clinical Intent Hierarchy
Multi-Agent AI Platform          → MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md v3.0
4-Section Workflow               → INTEGRATION_ARCHITECTURE.md v3.0
─────────────────────────────────────────────────────────────
** CARD SYSTEM **
Card Types (12 types)            → CARD_TYPE_SPECIFICATIONS.md v0.2
Card Template Structure          → UNIVERSAL_CARD_TEMPLATE.md v0.5
  • AT-A-GLANCE (patient quick ref)
  • CONDENSED VIEW (patient everyday)
  • EXPANDED VIEW (patient deep-dive)
  • EVIDENCE (patient trust-builder)
  • CLINICIAN & AI REFERENCE (like UpToDate)
  • AI METADATA (YAML)
Card Lifecycle Phases            → CARD_LIFECYCLE_AND_AI_PARAMETERS.md
  • Initiation Guide
  • Maintenance Guide
  • De-loading/De-prescribing
AI-Modifiable Parameters [ ]     → CARD_LIFECYCLE_AND_AI_PARAMETERS.md
De-prescribing Criteria          → CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md
Autonomy Tiers (4 tiers)         → AUTONOMY_AND_AI_AGENT_SPECIFICATION.md
AI Agent Ecosystem               → AUTONOMY_AND_AI_AGENT_SPECIFICATION.md
Evidence Grading & Sources       → EVIDENCE_SECTION_SPECIFICATION.md
Card Generation/Mass Production  → CARD_GENERATION_SPECIFICATION.md
DME + Home Monitoring Workflow   → DME_MONITORING_WORKFLOW_PATTERN.md
─────────────────────────────────────────────────────────────
** LIBRARIES **
Behavioral Card Libraries        → TIER5_*_v2.md files (v2.0!)
Medical Card Libraries           → TIER5_*.md files
Card vs Deck distinction         → BEHAVIORAL_LIBRARY_v2_CHANGELOG.md
─────────────────────────────────────────────────────────────
** CLINICAL DATA **
Diagnoses                        → MEDICAL_HISTORY_TIER1_LIBRARY
Parameters                       → PARAMETER_NORMALIZATION_v2.md
8 Health Systems                 → health-matrix-framework.md
5 Lifestyle Pillars              → LIFESTYLE_PILLAR_QUESTIONNAIRES
Scoring Algorithms               → SYSTEM_DOMAIN_SCORING_v2.md
Dashboard UI                     → DASHBOARD_LEVEL*_SPEC files
Care Planning                    → comprehensive-care-planning-methodology.md
```

**CARD LIBRARY RULES (v2.0):**
```
CARD = ONE atomic action patient can do independently
DECK = Collection of cards grouped by condition/strategy

WRONG: "Mediterranean Diet" as a card
RIGHT: "Mediterranean Diet" as a DECK containing:
       - "Eat Fatty Fish" (card)
       - "Use Olive Oil" (card)
       - "Eat Leafy Greens" (card)
       - etc.

WRONG: "Walk 10 min", "Walk 20 min", "Walk 30 min" as 3 cards
RIGHT: "Walk" as ONE card with duration as template parameter
```

---

## AUDIT CHECKLIST

**Use this to audit any document for source verification:**

- [ ] Does this document define specifications used elsewhere?
  - If YES → Add to Canonical Source Registry

- [ ] Does this document reference specifications from elsewhere?
  - If YES → Verify citations to canonical sources

- [ ] Are all lists/enumerations complete?
  - Cross-check against canonical source (don't trust memory!)

- [ ] Are version numbers cited?
  - Ensure you're referencing current version of source

- [ ] Would changes to this document require updates elsewhere?
  - Document in dependency chain

---

## WHEN TO UPDATE THIS REGISTRY

**Add new entries when:**
1. Creating a new canonical specification
2. Discovering an uncatalogued source document
3. Consolidating multiple sources into one canonical source

**Update existing entries when:**
1. Source document version changes
2. Source document moved to new location
3. Source document superseded by newer version

---

## SUMMARY

**The Three Rules to Prevent Information Loss:**

1. **ONE Canonical Source** per topic (no duplicates)
2. **ALWAYS Read Source** before writing (no memory)
3. **CITE and LINK** to sources (no copying)

**The Registry:**
- Lists canonical source for every critical specification
- Forces you to look up and read source documents
- Prevents working from incomplete/outdated memory

**The Verification Protocol:**
- 4-step process before writing about any topic
- Ensures completeness and accuracy
- Catches errors like "missing 3 card types"

---

## VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 0.6 | 2025-12-14 | **5 LIFESTYLE PILLARS RESTRUCTURING**: Dissolved Mind-Body library, created Emotion pillar (TIER5_EMOTION_v2.md), redistributed all cards to correct pillars, removed duplicates, added cross-references. Total: 528 behavioral cards across 5 pillars. |
| 0.5 | 2025-12-14 | Added Library Coverage tracking, corrected medical library status (most were planned, not created), added coverage % column |
| 0.4 | 2025-12-13 | Added CARE_PLAN_DIGITAL_INTERFACE_SPEC.md for time-interval Care Plan views |
| 0.3 | 2025-12-13 | Updated UNIVERSAL_CARD_TEMPLATE to v0.5 with audience-specific sections |
| 0.2 | 2025-12-12 | Added CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md, updated architecture references |
| 0.1 | 2025-11-26 | Initial source document registry |

**Note:** v1.0 will be assigned at first production deployment with real patients.

---

**END OF DOCUMENT**
