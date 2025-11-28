# SOURCE DOCUMENT REGISTRY & VERIFICATION PROTOCOL
**Version:** 1.0
**Date:** 2025-11-26
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
| **4-Section Workflow** | [INTEGRATION_ARCHITECTURE.md](INTEGRATION_ARCHITECTURE.md) | 2.0 | How all 4 sections work together |
| **8 Health Systems** | [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md) | Latest | Neurological, Cardiovascular, Respiratory, Metabolic, Renal, Musculoskeletal, Immune, Reproductive/Endocrine |
| **3 Clinical Domains** | [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md) | Latest | Structure, Function, Risk |
| **5 Lifestyle Pillars** | [LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1](CMO - HEALTH OVERVIEW/04_LIFESTYLE_ASSESSMENT/LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1_OPTIMIZED.md) | 2.1 | Nutrition, Movement, Sleep/Recovery, Mental/Emotional, Environment/Social |
| **Capacity, Resilience, Flexibility** | [capacity-resilience-flexibility.md](CMO - PERFORMANCE MEDICINE/architecture/capacity-resilience-flexibility.md) | Latest | Performance Medicine targets |

---

### **Section 1: Data Input Management**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **132 Tier 1 Diagnoses** | [MEDICAL_HISTORY_TIER1_LIBRARY_v1.1](CMO - HEALTH OVERVIEW/03_MEDICAL_HISTORY/MEDICAL_HISTORY_TIER1_LIBRARY_v1.1_INTAKE_READY.md) | 1.1 | All common diagnoses with ICD-10 codes, score modifiers |
| **Parameter Normalization Methods** | [PARAMETER_NORMALIZATION_v2.md](CMO - HEALTH OVERVIEW/01_CLINICAL_LOGIC/PARAMETER_NORMALIZATION_v2.md) | 2.0 | 5 normalization methods, 150 MVP parameters |
| **Patient Intake Form** | [PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md](CMO - HEALTH OVERVIEW/03_MEDICAL_HISTORY/PATIENT_INTAKE_FORM_PRODUCTION_SPEC.md) | Latest | Complete database schema, validation rules |
| **Lifestyle Questionnaires** | [LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1](CMO - HEALTH OVERVIEW/04_LIFESTYLE_ASSESSMENT/LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1_OPTIMIZED.md) | 2.1 | Questions, scoring, clinical interpretation |

---

### **Section 2: Health Overview Dashboard**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **Scoring Algorithms** | [SYSTEM_DOMAIN_SCORING_v2.md](CMO - HEALTH OVERVIEW/01_CLINICAL_LOGIC/SYSTEM_DOMAIN_SCORING_v2.md) | 2.0 | 24-cell aggregation formulas |
| **Biological Age Calculation** | [BIOLOGICAL_AGE_SPEC_v1_1.md](CMO - HEALTH OVERVIEW/01_CLINICAL_LOGIC/BIOLOGICAL_AGE_SPEC_v1_1.md) | 1.1 | Modified PhenoAge methodology |
| **Dashboard UI Specifications** | [DASHBOARD_LEVEL1_SPEC_v1_1.md](CMO - HEALTH OVERVIEW/06_DASHBOARD_SPECS/DASHBOARD_LEVEL1_SPEC_v1_1.md) | 1.1 | Level 1 (Hero), Level 2 (Systems), Level 3 (Detailed) |
| **Critical Alerts** | [CRITICAL_ALERTS_v1_1.md](CMO - HEALTH OVERVIEW/05_ALERTS_SAFETY/CRITICAL_ALERTS_v1_1.md) | 1.1 | Life-threatening thresholds |

---

### **Section 3: SMART Card/Deck System**

| Topic | Canonical Source | Current Version | What It Defines |
|-------|-----------------|----------------|-----------------|
| **12 Card Types** | [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) | 2.0 | **ALL 12 types** - MUST be read before writing about card types |
| **Universal Card Template** | [UNIVERSAL_CARD_TEMPLATE.md](CMO - SMART SYSTEM/docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) | Latest | WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY structure |
| **Library Hierarchy** | [LIBRARY_TIER_STRUCTURE.md](CMO - SMART SYSTEM/LIBRARY_TIER_STRUCTURE.md) | Latest | Tier 1-5 organization |
| **Evidence Grading** | [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) | 2.0 | A/B/C evidence grades |

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

**Platform Architecture:**
- [ ] 4-Section Workflow → INTEGRATION_ARCHITECTURE.md
- [ ] 8 Health Systems → health-matrix-framework.md
- [ ] 3 Clinical Domains → health-matrix-framework.md
- [ ] 5 Lifestyle Pillars → LIFESTYLE_PILLAR_QUESTIONNAIRES

**Card System:**
- [ ] 12 Card Types → CARD_TYPE_SPECIFICATIONS.md (CRITICAL - often missed!)
- [ ] Card Template → UNIVERSAL_CARD_TEMPLATE.md
- [ ] Evidence Grades → CARD_TYPE_SPECIFICATIONS.md

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
Card Types                       → CARD_TYPE_SPECIFICATIONS.md
Diagnoses                        → MEDICAL_HISTORY_TIER1_LIBRARY
Parameters                       → PARAMETER_NORMALIZATION_v2.md
8 Health Systems                 → health-matrix-framework.md
5 Lifestyle Pillars              → LIFESTYLE_PILLAR_QUESTIONNAIRES
Scoring Algorithms               → SYSTEM_DOMAIN_SCORING_v2.md
Dashboard UI                     → DASHBOARD_LEVEL*_SPEC files
Care Planning                    → comprehensive-care-planning-methodology.md
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

**END OF DOCUMENT**
