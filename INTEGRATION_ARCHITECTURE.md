# CMO PLATFORM - INTEGRATION ARCHITECTURE
**Version:** 1.0
**Date:** 2025-11-26
**Status:** Living Document - Update with any cross-project changes

---

## PURPOSE

This document defines how the three CMO projects integrate into a unified Performance Medicine platform. It serves as the **single source of truth** for cross-project dependencies, data flows, and update protocols.

---

## THE THREE PROJECTS

### 1. CMO - HEALTH OVERVIEW (Patient Data & Dashboard)
- **Purpose:** Collect, normalize, and visualize patient health data
- **Output:** 24-cell Health Matrix Dashboard, scores, biological age, alerts
- **Primary Users:** Patients, clinicians, caregivers

### 2. CMO - SMART SYSTEM (Intervention Library)
- **Purpose:** Evidence-based intervention cards and decks
- **Output:** Personalized card/deck recommendations, adherence tracking
- **Primary Users:** Patients (to take action), clinicians (to prescribe)

### 3. CMO - PERFORMANCE MEDICINE (Clinical Framework & Care Planning)
- **Purpose:** Integrated medical specialty framework and care planning methodology
- **Output:** Comprehensive care plans, quarterly implementation guides
- **Primary Users:** Clinicians, administrators, business development

---

## THE FOUR-SECTION WORKFLOW

The CMO Platform operates through four interconnected sections that create a continuous improvement cycle:

### **SECTION 1: DATA INPUT MANAGEMENT**
**Purpose:** Collect and process raw patient parameter data
**Components:** Patient intake forms, lab results, vital signs, imaging, lifestyle assessments
**Processing:** Clinical logic + mathematical algorithms for normalization and validation
**Output:** Clean, standardized patient data ready for analysis

### **SECTION 2: HEALTH OVERVIEW DASHBOARD MANAGEMENT**
**Purpose:** Transform input data into patient-centric, user-friendly visualization
**Components:** 24-cell Health Matrix, scoring algorithms, biological age, alerts
**Processing:** Aggregate Section 1 data + outputs from Section 3 (SMART Card adherence)
**Output:** Live, continuously-updating dashboard
**Patient Incentive:** More frequent data updates = more accurate dashboard = better health insights

### **SECTION 3: SMART CARD/DECK CARE PLAN SYSTEM**
**Purpose:** Generate actionable, interactable care plans
**Components:** Evidence-based intervention cards, progressive decks, adherence tracking
**Processing:** Uses outputs from Section 1 (clinical data) + Section 2 (dashboard scores)
**Key Features:**
- **Creation Process:** AI-driven recommendations based on dashboard + clinical data
- **Management Process:** Patient self-directed with clinician guidance
- **De-loading/De-prescribing Process:** Cards automatically retire when goals achieved
**Output:** Personalized SMART Cards that feed back into Section 2 dashboard

### **SECTION 4: PERFORMANCE MEDICINE PHILOSOPHY**
**Purpose:** Guide the specialty philosophy of care across all life stages
**Components:** Clinical framework, care planning methodology, evidence base
**Mission:** Optimize capacity, resilience, and flexibility for all ages
**Role:** Defines standards, protocols, and values that govern Sections 1-3

---

## WORKFLOW INTEGRATION MODEL

```
┌─────────────────────────────────────────────────────────────────┐
│  SECTION 4: PERFORMANCE MEDICINE PHILOSOPHY                     │
│  • Defines clinical standards, protocols, evidence base         │
│  • Guides care philosophy: Capacity, Resilience, Flexibility    │
│  • Sets life-stage care planning methodology                    │
└─────────────┬───────────────────────────────────────────────────┘
              │ Philosophically guides all sections
              ↓
┌─────────────────────────────────────────────────────────────────┐
│  SECTION 1: DATA INPUT MANAGEMENT                               │
│  • Patient intake forms (demographics, medical history)         │
│  • Clinical data: Labs, vitals, imaging, physical exam          │
│  • Lifestyle assessments: 5-pillar questionnaires               │
│  PROCESSING: Clinical + mathematical logic                      │
│  OUTPUT: Clean, normalized patient parameters                   │
└─────────────┬───────────────────────────────────────────────────┘
              │ Feeds processed data
              ↓
┌─────────────────────────────────────────────────────────────────┐
│  SECTION 2: HEALTH OVERVIEW DASHBOARD                           │
│  INPUT: Section 1 data + Section 3 adherence data               │
│  PROCESSING: Scoring, aggregation, trend analysis               │
│  OUTPUT: 24-cell dashboard, biological age, alerts              │
│  LIVE UPDATES: Dashboard continuously refreshes with new data   │
└─────────────┬───────────────────┬───────────────────────────────┘
              │                   │ Adherence/outcome data loops back
              ↓                   │
┌─────────────────────────────────┼───────────────────────────────┐
│  SECTION 3: SMART CARD/DECK CARE PLAN SYSTEM                    │
│  INPUT: Section 1 clinical data + Section 2 dashboard scores    │
│  PROCESSING: AI recommendation engine                           │
│                                                                  │
│  CREATION: Cards recommended based on scores & diagnoses        │
│  MANAGEMENT: Patient self-directed actions with guidance        │
│  DE-LOADING: Cards retire when targets achieved                 │
│                                                                  │
│  OUTPUT: Personalized care plan cards                           │
└─────────────┬──────────────────────────────────────┬────────────┘
              │                                      │
              ↓                                      │
     [Patient Takes Action]                          │
              │                                      │
              ↓                                      │
     [New Data Generated] ─────────────────────────┘
              │
              └──────→ Back to Section 1 (cycle repeats)
```

**KEY PRINCIPLE:** The more frequently patients update their data (Section 1), the more accurate and dynamic their dashboard becomes (Section 2), creating a powerful incentive for active health engagement.

---

## WORKFLOW RULES FOR PROJECT DEVELOPMENT

### Rule 1: Master Project Governance
**All discussions and development work in this master project MUST:**
1. Reference these integration/README .md files first
2. Understand the four-section workflow before making changes
3. Create outputs relevant to ALL sub-projects AND the master project
4. Follow the update protocol to maintain cross-project consistency

### Rule 2: Section Definitions (Project Mapping)

| Section | Primary Project Location | Sub-Components |
|---------|-------------------------|----------------|
| **Section 1** | CMO - HEALTH OVERVIEW<br>→ 03_MEDICAL_HISTORY<br>→ 04_LIFESTYLE_ASSESSMENT<br>→ 02_PARAMETER_LIBRARIES | • Patient intake forms<br>• Medical history libraries<br>• Lifestyle questionnaires<br>• Parameter normalization logic |
| **Section 2** | CMO - HEALTH OVERVIEW<br>→ 01_CLINICAL_LOGIC<br>→ 05_ALERTS_SAFETY<br>→ 06_DASHBOARD_SPECS | • Scoring algorithms<br>• 24-cell dashboard<br>• Alert systems<br>• Biological age calculation |
| **Section 3** | CMO - SMART SYSTEM<br>→ library/<br>→ docs/core/ | • SMART Card library<br>• Deck structures<br>• AI recommendation engine<br>• Adherence tracking |
| **Section 4** | CMO - PERFORMANCE MEDICINE<br>→ architecture/<br>→ clinical-protocols/ | • Health Matrix framework<br>• Care planning methodology<br>• Evidence base<br>• Life-stage templates |

### Rule 3: Live Dashboard Principle
The Section 2 dashboard is **LIVE and CONTINUOUS**, meaning:
- It ingests data from Section 1 whenever new data is entered
- It updates when Section 3 cards are completed (adherence data)
- Patients can see real-time changes as they take actions
- The dashboard never "finalizes" - it's always current

### Rule 4: SMART Card Lifecycle (Section 3)

**Creation Process:**
- Triggered by low dashboard scores (Section 2) OR specific diagnoses (Section 1)
- AI recommends cards, clinician approves
- Cards assigned to patient's active deck

**Management Process:**
- Patient self-directs card actions (mostly)
- Clinician/medical staff provide guidance as needed
- Progress tracked automatically
- Adherence data feeds back to Section 2 dashboard

**De-loading/De-prescribing Process:**
- When targets achieved → card automatically retires
- When diagnosis resolved → associated cards de-prescribe
- When patient preference changes → cards can be paused/removed
- Prevents card overload and keeps focus on current priorities

### Rule 5: Cross-Section Data Flows

**Section 1 → Section 2:**
- Raw parameters → Normalized scores → Dashboard display
- Diagnoses → Score modifiers → System scores adjusted
- Lifestyle data → Pillar scores → Behavioral insights

**Section 2 → Section 3:**
- Low system scores → Medical card recommendations
- Low pillar scores → Behavioral card recommendations
- Critical alerts → Urgent intervention cards

**Section 3 → Section 2:**
- Card completed → Parameters improve → Scores update
- Adherence tracking → Dashboard shows progress
- Goals achieved → Dashboard reflects success

**Section 4 → All Sections:**
- Clinical standards → Section 1 data collection requirements
- Scoring philosophy → Section 2 algorithm design
- Evidence base → Section 3 card content and grades
- Care planning methodology → Unifies all sections

### Rule 6: Update Protocol
When making ANY change to ANY section:

1. **Identify which section(s) affected** (use table in Rule 2)
2. **Check cross-section dependencies** (use Rule 5 flows)
3. **Update all connected sections in parallel**
4. **Document changes** in this integration architecture
5. **Validate data flows** end-to-end

---

## DATA FLOW SPECIFICATIONS

### Flow 1: Patient Onboarding → Dashboard → Recommendations

**Step 1:** Patient completes intake form (HEALTH OVERVIEW)
- Demographics, medical history (132 diagnoses), medications, allergies, family history, lifestyle pillars
- Output: Patient profile with diagnoses, baseline scores

**Step 2:** Initial clinical data collected
- Labs, vitals, imaging, physical exam findings
- Output: 24-cell dashboard populated, system scores calculated

**Step 3:** Dashboard triggers SMART Card recommendations (SMART SYSTEM)
- Low cardiovascular score → Hypertension Deck recommended
- High metabolic risk → Diabetes Prevention Deck recommended
- Poor nutrition pillar score → Nutrition Cards recommended

**Step 4:** Clinician reviews and approves recommendations (PERFORMANCE MEDICINE framework)
- Uses care planning methodology to prioritize
- Considers capacity, resilience, flexibility targets
- Prescribes SMART Decks as part of unified care plan

**Step 5:** Patient receives personalized SMART Cards
- Progressive unlocking based on adherence
- Adherence tracked in SMART SYSTEM
- New data flows back to HEALTH OVERVIEW dashboard

---

### Flow 2: Diagnosis → Score Modifiers → Card Recommendations

**Diagnosis Library Linkage:**

| Diagnosis (Health Overview) | Score Modifier | Triggered Cards (SMART System) |
|----------------------------|----------------|-------------------------------|
| Hypertension (ICD-10: I10) | Cardiovascular Structure -5, Function -5, Risk -10 | Lisinopril, HCTZ, Amlodipine, DASH Diet, Aerobic Exercise, BP Monitoring |
| Type 2 Diabetes (ICD-10: E11) | Metabolic Function -10, Risk -15 | Metformin, Insulin, A1C Testing, Carb Counting, CGM Monitoring |
| Obstructive Sleep Apnea (ICD-10: G47.33) | Respiratory Function -8, Cardiovascular Risk -5 | CPAP Therapy, Sleep Study, Weight Loss, Sleep Hygiene |

**Integration Rule:**
- When a diagnosis is entered in HEALTH OVERVIEW → automatic score modifiers applied
- Those modifiers trigger condition-specific card recommendations in SMART SYSTEM
- Recommendations follow care planning methodology from PERFORMANCE MEDICINE

---

### Flow 3: Lifestyle Pillar Scores → Behavioral Cards

**5-Pillar Questionnaire (Health Overview) → Behavioral Cards (SMART System):**

| Pillar | Low Score Trigger | Recommended Card Categories |
|--------|------------------|----------------------------|
| Nutrition | <60/100 | Dietary Patterns, Specific Foods, Meal Planning |
| Movement | <60/100 | Aerobic Exercise, Strength Training, Balance |
| Sleep & Recovery | <60/100 | Sleep Hygiene, Stress Management, Breathing |
| Mental/Emotional | <60/100 | Mind-Body Practices, Micro-Learning |
| Environment/Social | <60/100 | Environmental Health, Social Connection |

---

## CROSS-PROJECT DEPENDENCY MAPPING

### When You Update HEALTH OVERVIEW:

**If you modify:**
- Diagnosis library (add/change diagnoses) → **Update SMART SYSTEM** card triggers
- Parameter definitions → **Update PERFORMANCE MEDICINE** assessment templates
- Scoring algorithms → **Update SMART SYSTEM** recommendation logic
- Lifestyle questionnaires → **Update SMART SYSTEM** behavioral card mappings

**Update Checklist:**
1. Check if diagnosis exists in SMART SYSTEM card library
2. Verify card recommendations align with new score modifiers
3. Update PERFORMANCE MEDICINE care planning templates if new assessment added

---

### When You Update SMART SYSTEM:

**If you modify:**
- Card library (add new cards) → **Update HEALTH OVERVIEW** to ensure data collected supports card
- Card types or categories → **Update PERFORMANCE MEDICINE** unified prescription format
- Recommendation algorithms → **Update HEALTH OVERVIEW** to ensure dashboard provides needed inputs

**Update Checklist:**
1. Verify HEALTH OVERVIEW collects all parameters needed for card recommendations
2. Confirm cards align with PERFORMANCE MEDICINE evidence standards
3. Check that care planning templates reference new cards

---

### When You Update PERFORMANCE MEDICINE:

**If you modify:**
- Clinical protocols or guidelines → **Update HEALTH OVERVIEW** scoring/alert logic
- Care planning templates → **Update SMART SYSTEM** deck structures
- Evidence base → **Update SMART SYSTEM** card evidence grades
- Life-stage goals → **Update HEALTH OVERVIEW** target ranges by age

**Update Checklist:**
1. Ensure HEALTH OVERVIEW dashboard reflects new clinical priorities
2. Verify SMART SYSTEM cards align with updated evidence standards
3. Check that care plan templates can incorporate SMART Deck prescriptions

---

## UNIFIED WORKFLOWS

### Workflow 1: New Patient Comprehensive Care Plan

**Combines all three projects:**

1. **HEALTH OVERVIEW:** Patient completes intake form
   - Medical history, lifestyle pillars, demographics collected
   - Initial dashboard generated (may be incomplete pending labs)

2. **PERFORMANCE MEDICINE:** Clinician conducts comprehensive assessment
   - Uses physical examination standard
   - Orders appropriate labs/imaging based on life-stage template
   - Reviews preventive care integration matrix

3. **HEALTH OVERVIEW:** Clinical data entered
   - Labs, vitals, imaging results populate dashboard
   - 24-cell matrix complete, biological age calculated
   - Critical alerts flagged

4. **PERFORMANCE MEDICINE:** Data analyzed using Health Matrix framework
   - Red/Orange priorities identified
   - Capacity, resilience, flexibility assessed
   - Unified care plan drafted using life-stage template

5. **SMART SYSTEM:** AI recommends cards/decks
   - Based on dashboard scores and diagnoses
   - Clinician reviews and approves
   - Cards added to unified prescription in care plan

6. **Patient receives integrated care plan:**
   - Medical interventions (medications, procedures, referrals)
   - Lifestyle interventions (SMART Cards organized by pillar)
   - Monitoring plan (labs, follow-up visits)
   - 12-month roadmap with quarterly phases

---

### Workflow 2: Quarterly Follow-Up & Refinement

**Combines all three projects:**

1. **HEALTH OVERVIEW:** Updated data collected
   - New labs, vitals, imaging
   - Lifestyle pillar questionnaires repeated
   - Dashboard updated with trend analysis

2. **SMART SYSTEM:** Adherence data reviewed
   - Which cards completed, which skipped
   - Patient reviews and ratings analyzed
   - Barriers to adherence identified

3. **PERFORMANCE MEDICINE:** Quarterly implementation guide applied
   - Progress toward capacity/resilience/flexibility targets assessed
   - Care plan refined based on what's working
   - Next quarter interventions selected

4. **SMART SYSTEM:** New cards/decks prescribed
   - Based on updated dashboard and adherence data
   - Progressive complexity (beginner → advanced)
   - New cards unlock as previous completed

---

## SHARED DATA MODELS

### Patient Profile (Unified across all projects)

```json
{
  "patient_id": "UUID",
  "demographics": {
    "age": 52,
    "sex": "M",
    "life_stage": "Middle_Age_40_64"
  },
  "diagnoses": [
    {
      "icd10": "I10",
      "name": "Essential Hypertension",
      "score_modifiers": {
        "cardiovascular_structure": -5,
        "cardiovascular_function": -5,
        "cardiovascular_risk": -10
      },
      "triggered_cards": ["lisinopril", "hctz", "dash_diet", "bp_monitoring"]
    }
  ],
  "dashboard_scores": {
    "overall_health": 72,
    "biological_age": 57,
    "system_scores": {
      "cardiovascular": {
        "structure": 65,
        "function": 70,
        "risk": 60
      }
      // ... 7 more systems
    },
    "pillar_scores": {
      "nutrition": 58,
      "movement": 72,
      "sleep_recovery": 65,
      "mental_emotional": 80,
      "environment_social": 70
    }
  },
  "smart_cards": {
    "active_decks": ["hypertension_management", "weight_loss_foundation"],
    "completed_cards": ["lisinopril_card", "dash_diet_intro"],
    "adherence_rate": 0.78
  },
  "care_plan": {
    "current_quarter": "Q2_Build",
    "primary_goals": ["Lower BP to <130/80", "Lose 15 lbs", "Improve sleep quality"],
    "capacity_targets": {...},
    "resilience_targets": {...},
    "flexibility_targets": {...}
  }
}
```

---

## UPDATE PROTOCOL

### When Making Changes to Any Project:

**Step 1: Identify Cross-Project Impact**
- Review this integration document
- Check dependency mapping sections
- Identify which other projects are affected

**Step 2: Update All Affected Projects**
- Make changes in parallel across projects
- Use consistent terminology and data structures
- Update integration documentation if dependencies change

**Step 3: Document Changes**
- Update this INTEGRATION_ARCHITECTURE.md file
- Note changes in each project's CHANGELOG
- Flag breaking changes clearly

**Step 4: Validate Integration**
- Test data flows across projects
- Verify no broken dependencies
- Check that workflows still function end-to-end

---

## TERMINOLOGY CONSISTENCY

### Shared Terms (Must be identical across all projects):

| Term | Definition | Used In |
|------|-----------|---------|
| **8 Health Systems** | Neurological, Cardiovascular, Respiratory, Metabolic, Renal, Musculoskeletal, Immune, Reproductive/Endocrine | All 3 projects |
| **3 Clinical Domains** | Structure, Function, Risk | All 3 projects |
| **24-Cell Matrix** | 8 Systems × 3 Domains dashboard | All 3 projects |
| **5 Lifestyle Pillars** | Nutrition, Movement, Sleep/Recovery, Mental/Emotional, Environment/Social | All 3 projects |
| **Capacity** | What you can do today (functional performance) | All 3 projects |
| **Resilience** | How quickly you recover from stress/illness/injury | All 3 projects |
| **Flexibility** | How well you adapt (metabolic, circadian, training, stress) | All 3 projects |
| **SMART Card** | Single, specific, measurable, actionable intervention | SMART SYSTEM, PERFORMANCE MEDICINE |
| **SMART Deck** | Progressive sequence of related cards | SMART SYSTEM, PERFORMANCE MEDICINE |
| **Unified Prescription** | Care plan combining medical + lifestyle interventions | PERFORMANCE MEDICINE, SMART SYSTEM |
| **Life Stage** | Age-based categorization (9 groups from infancy to 80+) | PERFORMANCE MEDICINE, HEALTH OVERVIEW |
| **Evidence Grade** | A/B/C rating based on clinical guidelines | SMART SYSTEM, PERFORMANCE MEDICINE |

---

## FUTURE INTEGRATION OPPORTUNITIES

1. **Wearable Device Data → Real-Time Dashboard Updates**
   - Continuous glucose monitors, fitness trackers, sleep monitors
   - Auto-populate HEALTH OVERVIEW dashboard
   - Trigger real-time SMART Card recommendations

2. **EHR Integration**
   - Pull diagnosis codes, medications, lab results automatically
   - Reduce manual data entry in HEALTH OVERVIEW
   - Push care plans back to EHR

3. **Predictive Analytics**
   - Use dashboard trends to predict future health risks
   - Preemptively recommend SMART Cards before problems emerge

4. **Community Data Aggregation**
   - Aggregate SMART Card adherence data across patients
   - Identify which cards work best for specific demographics/conditions
   - Refine recommendations using real-world evidence

---

## MAINTAINER RESPONSIBILITIES

**When working on any of the three projects, you MUST:**

1. **Check this document first** before making structural changes
2. **Update this document** if you change cross-project dependencies
3. **Maintain terminology consistency** across all three projects
4. **Test integration** after significant changes to any project
5. **Document breaking changes** prominently

---

## VERSION HISTORY

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 2.0 | 2025-11-26 | Consolidated cross-project update checklist and version control protocol as appendices | Claude |
| 1.1 | 2025-11-26 | Revised to reflect four-section workflow, added workflow rules, clarified SMART card lifecycle | Claude |
| 1.0 | 2025-11-26 | Initial integration architecture created | Claude |

---

## APPENDIX A: CROSS-PROJECT UPDATE CHECKLIST

### Quick Decision Tree

**Ask yourself:** "Does my change affect..."

- ✅ **Data that flows between projects?** → Update all 3 projects
- ✅ **Shared terminology or definitions?** → Update all 3 projects + this document
- ✅ **Clinical logic or scoring?** → Update HEALTH OVERVIEW + SMART SYSTEM
- ✅ **Care planning methodology?** → Update PERFORMANCE MEDICINE + SMART SYSTEM
- ✅ **Patient workflows?** → Update all 3 projects
- ❌ **Only implementation details within one project?** → Update that project only

### Checklist When Updating HEALTH OVERVIEW

**If you changed:**
- [ ] **Diagnosis library** → Update SMART SYSTEM card triggers + PERFORMANCE MEDICINE care templates
- [ ] **Parameter definitions** → Update PERFORMANCE MEDICINE assessments + SMART SYSTEM cards
- [ ] **Scoring algorithms** → Update SMART SYSTEM thresholds + PERFORMANCE MEDICINE criteria
- [ ] **Lifestyle questionnaires** → Update SMART SYSTEM behavioral cards + PERFORMANCE MEDICINE pillars
- [ ] **Patient intake form** → Update PERFORMANCE MEDICINE methodology + verify SMART SYSTEM data support

### Checklist When Updating SMART SYSTEM

**If you changed:**
- [ ] **Card library** → Verify HEALTH OVERVIEW collects needed data + update PERFORMANCE MEDICINE templates
- [ ] **Card types/categories** → Update PERFORMANCE MEDICINE prescription format + HEALTH OVERVIEW data collection
- [ ] **Recommendation algorithms** → Verify HEALTH OVERVIEW provides inputs + update PERFORMANCE MEDICINE workflow
- [ ] **Deck structures** → Update PERFORMANCE MEDICINE quarterly guides

### Checklist When Updating PERFORMANCE MEDICINE

**If you changed:**
- [ ] **Clinical protocols/guidelines** → Update HEALTH OVERVIEW scoring + SMART SYSTEM evidence grades
- [ ] **Care planning templates** → Update SMART SYSTEM deck structures
- [ ] **Evidence base** → Update SMART SYSTEM card grades + HEALTH OVERVIEW parameters
- [ ] **Life-stage goals** → Update HEALTH OVERVIEW targets + SMART SYSTEM recommendations

---

## APPENDIX B: VERSION CONTROL & FILE DEPENDENCIES

### Document Dependency Principles

**Every significant file must declare:**
1. What it depends on (upstream dependencies)
2. What depends on it (downstream impacts)
3. Version number and last updated date

### Update Workflow (6 Steps)

**When updating ANY file:**

1. **Check dependencies BEFORE editing**
   - Look up file in dependency registry
   - Identify upstream (what it depends on) and downstream (what depends on it)

2. **Make your changes**
   - Edit target file
   - Increment version number
   - Update "Last Updated" date

3. **Update downstream files**
   - For each file listed in "Updates Required In"
   - Make necessary alignment updates
   - Increment their versions too

4. **Update this integration document**
   - Document changes in Version History below
   - Update dependency mappings if changed

5. **Validate integration**
   - Review data flows still work
   - Check no broken dependencies
   - Test critical chains

6. **Commit to git**
   - Commit all updated files together
   - Clear commit message noting all files changed

### Critical Dependency Chains

**Chain 1: Diagnosis → Cards**
```
MEDICAL_HISTORY_TIER1_LIBRARY.md
  ↓ (diagnosis codes + score modifiers)
INTEGRATION_ARCHITECTURE.md (this doc)
  ↓ (diagnosis → card mappings)
SMART SYSTEM card library
  ↓ (individual cards)
AI recommendation logic
```

**Chain 2: Parameters → Scoring → Dashboard → Recommendations**
```
PARAMETER_NORMALIZATION_v2.md
  ↓ (parameter definitions)
SYSTEM_DOMAIN_SCORING_v2.md
  ↓ (24-cell scores)
DASHBOARD specs
  ↓ (visualization)
SMART SYSTEM AI
  ↓ (recommendations)
```

**Chain 3: Lifestyle Pillars → Behavioral Cards**
```
LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1.md
  ↓ (questions + scoring)
INTEGRATION_ARCHITECTURE.md
  ↓ (pillar → card mappings)
SMART SYSTEM behavioral cards
```

---

## RELATED DOCUMENTS

**MASTER GOVERNANCE:**
- [SOURCE_DOCUMENT_REGISTRY.md](SOURCE_DOCUMENT_REGISTRY.md) ⚠️ **Read FIRST to find canonical sources**
- [MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md](MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md) - Platform-wide AI (all 4 sections)
- [MASTER_ROADMAP.md](MASTER_ROADMAP.md)
- [00_START_HERE.md](00_START_HERE.md)

**HEALTH OVERVIEW:**
- [PROJECT_SPECIFICATION_v2.md](CMO - DATA INPUT/00_PROJECT_MASTER/PROJECT_SPECIFICATION_v2.md)
- [MEDICAL_HISTORY_TIER1_LIBRARY.md](CMO - DATA INPUT/03_MEDICAL_HISTORY/MEDICAL_HISTORY_TIER1_LIBRARY_v1.1_INTAKE_READY.md)

**SMART SYSTEM:**
- [ARCHITECTURE.md](CMO - SMART SYSTEM/ARCHITECTURE.md)
- [LIBRARY_TIER_STRUCTURE.md](CMO - SMART SYSTEM/LIBRARY_TIER_STRUCTURE.md)
- [CARD_TYPE_SPECIFICATIONS.md](CMO - SMART SYSTEM/docs/core/03_CARD_TYPE_SPECIFICATIONS.md) ⚠️ **SOURCE OF TRUTH for 12 Card Types**
- [CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md](CMO - SMART SYSTEM/CARD_DEPRESCRIBING_AND_AI_OVERSIGHT_SPEC.md)

**PERFORMANCE MEDICINE:**
- [health-matrix-framework.md](CMO - PERFORMANCE MEDICINE/architecture/health-matrix-framework.md)
- [comprehensive-care-planning-methodology.md](CMO - PERFORMANCE MEDICINE/clinical-protocols/comprehensive-care-planning-methodology.md)

---

**END OF DOCUMENT**
