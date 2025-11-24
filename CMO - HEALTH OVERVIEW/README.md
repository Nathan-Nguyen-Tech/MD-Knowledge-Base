# HEALTH OVERVIEW DASHBOARD
## Project Documentation Index

**Last Updated:** November 19, 2025
**Project Phase:** MVP Development - Multi-User Dashboard
**Status:** Foundation + MVP Parameter Libraries Complete

---

## 📁 DOCUMENT ORGANIZATION

### [00_PROJECT_MASTER/](00_PROJECT_MASTER/)
**Start here** - Master project documentation and coordination

| Document | Purpose |
|----------|---------|
| **PROJECT_INSTRUCTIONS_MASTER.md** | ⭐ **START HERE** - Team coordination, document map, workflow guides |
| **PROJECT_SPECIFICATION_v2.md** | Master project vision and architecture |
| **PROJECT_ARCHITECTURE.md** | Technical architecture for multi-user system |
| **FRAMEWORK_SUMMARY.md** | Parameter scoring framework overview |

---

### [01_CLINICAL_LOGIC/](01_CLINICAL_LOGIC/)
Core scoring algorithms and calculation frameworks

| Document | Purpose |
|----------|---------|
| **PARAMETER_NORMALIZATION_v2.md** | Core normalization methods (5 methods) |
| **CALIBRATION_VALIDATION.md** | Validation methodology, governance |
| **CONTEXT_RULES.md** | Patient-specific adjustments (pregnancy, meds, conditions) |
| **TEMPORAL_SCORING.md** | Time-series handling, trends |
| **SYSTEM_DOMAIN_SCORING_v2.md** | 24-cell aggregation formulas |
| **COMPOSITE_SCORING_v2.md** | Overall health score calculation |
| **BIOLOGICAL_AGE_SPEC_v1_1.md** | Modified PhenoAge methodology |

---

### [02_PARAMETER_LIBRARIES/](02_PARAMETER_LIBRARIES/)
Complete parameter specifications with formulas and weights

| Document | Parameters | Purpose |
|----------|------------|---------|
| **MASTER_PARAMETER_LIBRARY_v1.md** | ~450 total | Complete parameter inventory |
| **PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md** | 150 MVP | Full specifications with formulas |
| **PARAMETER_WEIGHT_MATRIX_TEMPLATES.md** | 35 templates | 24-cell weight assignments |
| **STANDARDIZED_IMAGING_TEMPLATES.md** | 128 imaging | Imaging parameters across 10 modalities |

**MVP Coverage:** 150 fully-specified parameters
- Vital Signs: 15 | Labs: 45 | Urinalysis: 10 | Body Composition: 7
- Functional Tests: 6 | EKG: 10 | Lifestyle: 6 | Physical Exam: 15

---

### [03_MEDICAL_HISTORY/](03_MEDICAL_HISTORY/)
Medical history integration with diagnosis-based context rules

| Document | Diagnoses | Purpose |
|----------|-----------|---------|
| **MEDICAL_HISTORY_TIER1_LIBRARY.md** | 132 | Common diagnoses with context rules, score modifiers |

**What's Inside:**
- **Tier 1:** 132 fully-specified diagnoses across 8 organ systems
  - ICD-10 codes, context rules, score modifiers, monitoring requirements
  - Covers 80-90% of patient population
- **Tier 2:** Category-based rules for rare diagnoses
- **Score Modifiers:** Domain-level baseline adjustments
  - Example: Type 2 Diabetes → Metabolic-Function -15 points
- **Context Rules:** Automatic parameter target adjustments
  - Example: Diabetic HbA1c target <7.0% instead of <5.7%

---

### [04_LIFESTYLE_ASSESSMENT/](04_LIFESTYLE_ASSESSMENT/)
5-pillar lifestyle questionnaire framework

| Document | Purpose |
|----------|---------|
| **LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md** | Structure for 5-pillar assessment (detailed content TBD) |

**5 Pillars:** Nutrition | Movement | Recovery | Emotion | Environment
**Note:** Detailed questionnaire content on hold - requires separate discussion

---

### [05_ALERTS_SAFETY/](05_ALERTS_SAFETY/)
Critical alerts, decision rules, and transparency logic

| Document | Purpose |
|----------|---------|
| **CRITICAL_ALERTS_v1_1.md** | Critical thresholds, alert logic |
| **CLINICAL_DECISION_RULES_v1_0.md** | Complex IF-THEN clinical rules |
| **TRANSPARENCY_DISPLAY_v1_1.md** | Top contributor logic, explainability |

---

### [06_DASHBOARD_SPECS/](06_DASHBOARD_SPECS/)
User interface specifications for 3-level progressive disclosure

| Document | Level | Purpose |
|----------|-------|---------|
| **DASHBOARD_LEVEL1_SPEC_v1_1.md** | Level 1 | Hero view (all users) |
| **DASHBOARD_LEVEL2_SPEC_v1_1.md** | Level 2 | System overview (engaged users) |
| **DASHBOARD_LEVEL3_SPEC_v1_1.md** | Level 3 | Detail analysis (analytical users) |

**Progressive Disclosure:**
- **Level 1:** Quick status overview (always visible)
- **Level 2:** System/pillar coxcomb charts (expandable)
- **Level 3:** Detailed parameter analysis (drill-down)

---

### [07_IMPLEMENTATION_SUPPORT/](07_IMPLEMENTATION_SUPPORT/)
Validation reports and implementation strategies

| Document | Purpose |
|----------|---------|
| **CALCULATION_STRESS_TEST_REPORT.md** | Mathematical validation of formulas |
| **PARAMETER_WEIGHT_MANAGEMENT_STRATEGY.md** | Weight assignment strategy & rationale |

---

## 🚀 QUICK START GUIDE

### For Clinical Team
1. **Start:** [PROJECT_INSTRUCTIONS_MASTER.md](00_PROJECT_MASTER/PROJECT_INSTRUCTIONS_MASTER.md)
2. **Understand Framework:** [FRAMEWORK_SUMMARY.md](00_PROJECT_MASTER/FRAMEWORK_SUMMARY.md)
3. **Review Parameters:** [PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md](02_PARAMETER_LIBRARIES/PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md)
4. **Explore Medical History:** [MEDICAL_HISTORY_TIER1_LIBRARY.md](03_MEDICAL_HISTORY/MEDICAL_HISTORY_TIER1_LIBRARY.md)

### For IT Development Team
1. **Start:** [PROJECT_ARCHITECTURE.md](00_PROJECT_MASTER/PROJECT_ARCHITECTURE.md)
2. **Understand Scoring:** [01_CLINICAL_LOGIC/](01_CLINICAL_LOGIC/) (read all 7 documents)
3. **Implementation Specs:** [PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md](02_PARAMETER_LIBRARIES/PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md)
4. **Dashboard Design:** [06_DASHBOARD_SPECS/](06_DASHBOARD_SPECS/) (all 3 levels)

### For Product/UX Team
1. **Start:** [PROJECT_SPECIFICATION_v2.md](00_PROJECT_MASTER/PROJECT_SPECIFICATION_v2.md)
2. **Dashboard UX:** [06_DASHBOARD_SPECS/](06_DASHBOARD_SPECS/) (all 3 levels)
3. **Transparency:** [TRANSPARENCY_DISPLAY_v1_1.md](05_ALERTS_SAFETY/TRANSPARENCY_DISPLAY_v1_1.md)

---

## 📊 PROJECT STATUS

### ✅ Complete
- **Foundation Documents** (4 documents)
- **Core Clinical Logic** (7 documents)
- **Parameter Libraries** (4 documents, 150 MVP parameters)
- **Medical History Library** (132 diagnoses)
- **Alert & Safety** (3 documents)
- **Dashboard Specifications** (3 levels)
- **Implementation Support** (2 documents)

### 📋 In Progress / Planned
- Lifestyle questionnaire detailed content (on hold)
- Surgical history library
- Medication context library
- Family history template
- Advanced parameter libraries (wearables, advanced imaging)

---

## 🎯 THE 24-CELL HEALTH MATRIX

**8 Organ Systems × 3 Evaluation Domains = 24 Assessment Cells**

| System | Structure | Function | Risk |
|--------|-----------|----------|------|
| Neurological | Brain/nerve integrity | Cognitive/motor function | Stroke/dementia risk |
| Cardiovascular | Vessel/heart anatomy | Cardiac output | MI/CHF risk |
| Respiratory | Airway/lung structure | Gas exchange | COPD/failure risk |
| Metabolic | GI/liver/pancreas | Metabolic function | Diabetes/cirrhosis risk |
| Renal | Kidney structure | Filtration capacity | CKD progression |
| Musculoskeletal | Bone/joint/muscle | Strength/mobility | Fracture/disability |
| Immune | Lymph/immune organs | Infection defense | Cancer/autoimmune |
| Reproductive/Endocrine | Gland/organ structure | Hormone production | Hormone disorders |

---

## 🔢 SCORING HIERARCHY

```
Individual Parameters (0-100 normalized)
    ↓ [weighted by 24-cell matrix]
Domain Scores per System (Structure/Function/Risk: 0-100 each)
    ↓ [weighted 25%/50%/25%]
System Health Scores (8 systems: 0-100 each)
    ↓ [weighted by criticality]
Objective Health Component (0-100) [70% weight]
    +
Lifestyle Pillar Scores (5 pillars: 0-100)
    ↓ [weighted by importance]
Subjective Health Component (0-100) [30% weight]
    =
OVERALL HEALTH SCORE (0-100)
```

---

## 🎨 COLOR-CODED STATUS ZONES

| Color | Score | Status | Action |
|-------|-------|--------|--------|
| 🟢 **Green** | 75-100 | Optimal | Maintain current approach |
| 🟡 **Yellow** | 60-74 | Monitor | Routine follow-up, consider optimization |
| 🟠 **Orange** | 40-59 | Act Soon | Clinician consultation (days to weeks) |
| 🔴 **Red** | 0-39 | Urgent | Same-day clinician contact or emergency |

---

## 💡 KEY PRINCIPLES

1. **Conservative Baseline:** At personalized target (z=0) = **85 points** (not 100)
   - Rewards achieving healthy targets (B+ grade)
   - Leaves room for sustained excellence (86-100)

2. **Progressive Disclosure:** 3 levels (Level 1→2→3)
   - Users control information depth
   - Same interface for all user types

3. **Transparent Scoring:** Every composite score decomposable to contributing parameters

4. **Critical Safety First:** Life-threatening parameters flagged regardless of composite scores

5. **Medical History Integration:** Diagnosis-based score modifiers and context rules
   - Domain-level baseline adjustments
   - Automatic parameter target changes

---

## 📞 NEED HELP?

**Clinical Questions:** Refer to [PROJECT_INSTRUCTIONS_MASTER.md](00_PROJECT_MASTER/PROJECT_INSTRUCTIONS_MASTER.md)

**Technical Questions:** Review [PROJECT_ARCHITECTURE.md](00_PROJECT_MASTER/PROJECT_ARCHITECTURE.md) and [01_CLINICAL_LOGIC/](01_CLINICAL_LOGIC/)

**Getting Started:** Follow the Quick Start Guide above for your role

---

**Last Updated:** November 19, 2025
**Project Team:** Performance Medicine Clinical Design Team

---

*This Health Overview Dashboard transforms clinical data into actionable health intelligence for patients, caregivers, clinicians, and medical personnel through a unified, transparent, and progressive interface.*
