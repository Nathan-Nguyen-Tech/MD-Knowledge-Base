# CROSS-PROJECT UPDATE CHECKLIST
**Version:** 1.0
**Date:** 2025-11-26
**Purpose:** Quick reference for maintaining integration when updating any CMO project

---

## QUICK DECISION TREE

**Ask yourself:** "Does my change affect..."

- ✅ **Data that flows between projects?** → Update all 3 projects
- ✅ **Shared terminology or definitions?** → Update all 3 projects + [INTEGRATION_ARCHITECTURE.md](INTEGRATION_ARCHITECTURE.md)
- ✅ **Clinical logic or scoring?** → Update HEALTH OVERVIEW + SMART SYSTEM
- ✅ **Care planning methodology?** → Update PERFORMANCE MEDICINE + SMART SYSTEM
- ✅ **Patient workflows?** → Update all 3 projects
- ❌ **Only implementation details within one project?** → Update that project only

---

## CHECKLIST BY PROJECT

### When Updating HEALTH OVERVIEW

**If you changed...**

- [ ] **Diagnosis library** (added/modified diagnoses)
  - [ ] Update SMART SYSTEM card triggers for new diagnoses
  - [ ] Update PERFORMANCE MEDICINE care plan templates
  - [ ] Verify ICD-10 codes consistent across all projects

- [ ] **Parameter definitions** (new labs, vitals, imaging)
  - [ ] Update PERFORMANCE MEDICINE assessment templates
  - [ ] Update SMART SYSTEM to ensure relevant cards exist
  - [ ] Check INTEGRATION_ARCHITECTURE.md data models

- [ ] **Scoring algorithms** (normalization, aggregation, composite)
  - [ ] Update SMART SYSTEM recommendation thresholds
  - [ ] Update PERFORMANCE MEDICINE traffic-light criteria
  - [ ] Document changes in INTEGRATION_ARCHITECTURE.md

- [ ] **Lifestyle questionnaires** (added/modified questions)
  - [ ] Update SMART SYSTEM behavioral card mappings
  - [ ] Update PERFORMANCE MEDICINE Five Pillar definitions
  - [ ] Check score-to-card trigger logic

- [ ] **Patient intake form** (new fields, skip logic)
  - [ ] Update PERFORMANCE MEDICINE comprehensive assessment methodology
  - [ ] Verify data captured supports SMART SYSTEM recommendations

---

### When Updating SMART SYSTEM

**If you changed...**

- [ ] **Card library** (added new cards)
  - [ ] Verify HEALTH OVERVIEW collects data needed for card
  - [ ] Update PERFORMANCE MEDICINE unified prescription templates
  - [ ] Add to appropriate deck if condition-specific

- [ ] **Card types or categories** (modified Tier 1-5 structure)
  - [ ] Update PERFORMANCE MEDICINE care plan sections
  - [ ] Update HEALTH OVERVIEW if new data collection needed
  - [ ] Update INTEGRATION_ARCHITECTURE.md terminology table

- [ ] **Recommendation algorithms** (AI logic, feasibility scoring)
  - [ ] Verify HEALTH OVERVIEW dashboard provides required inputs
  - [ ] Update PERFORMANCE MEDICINE clinician approval workflow
  - [ ] Test end-to-end patient flow

- [ ] **Deck structures** (progressive unlocking, sequences)
  - [ ] Update PERFORMANCE MEDICINE quarterly implementation guides
  - [ ] Verify alignment with care planning methodology

- [ ] **Evidence grades** (updated A/B/C ratings)
  - [ ] Cross-check with PERFORMANCE MEDICINE evidence base
  - [ ] Update care plan references if major guideline changes

---

### When Updating PERFORMANCE MEDICINE

**If you changed...**

- [ ] **Clinical protocols or guidelines**
  - [ ] Update HEALTH OVERVIEW scoring/alert logic
  - [ ] Update SMART SYSTEM evidence grades for affected cards
  - [ ] Update critical thresholds if safety-related

- [ ] **Care planning templates** (life-stage, universal template)
  - [ ] Update SMART SYSTEM deck structures to match
  - [ ] Verify HEALTH OVERVIEW intake form captures needed data
  - [ ] Check unified prescription format consistency

- [ ] **Evidence base** (new citations, guideline updates)
  - [ ] Update SMART SYSTEM card evidence grades
  - [ ] Update HEALTH OVERVIEW parameter normalization if targets changed
  - [ ] Document major guideline changes

- [ ] **Life-stage goals or definitions**
  - [ ] Update HEALTH OVERVIEW parameter targets by age
  - [ ] Update SMART SYSTEM card recommendations by life stage
  - [ ] Verify age-based skip logic in intake form

- [ ] **8 Systems or 3 Domains framework** (structural changes)
  - [ ] Update HEALTH OVERVIEW dashboard structure
  - [ ] Update SMART SYSTEM card organization
  - [ ] **CRITICAL:** Update INTEGRATION_ARCHITECTURE.md immediately

---

## TERMINOLOGY CONSISTENCY CHECK

**Before finalizing any update, verify these terms are used identically:**

- [ ] **8 Health Systems:** Neurological, Cardiovascular, Respiratory, Metabolic, Renal, Musculoskeletal, Immune, Reproductive/Endocrine
- [ ] **3 Clinical Domains:** Structure, Function, Risk
- [ ] **5 Lifestyle Pillars:** Nutrition, Movement, Sleep/Recovery, Mental/Emotional, Environment/Social
- [ ] **Capacity, Resilience, Flexibility** definitions match across projects
- [ ] **SMART Card** and **SMART Deck** definitions consistent
- [ ] **Life Stage** categories identical (9 groups from infancy to 80+)
- [ ] **Evidence Grade** criteria (A/B/C) aligned

---

## DATA FLOW VALIDATION

**After any significant update, test these workflows:**

- [ ] **Patient Onboarding:** Intake form → Dashboard → Card recommendations → Care plan
- [ ] **Quarterly Follow-Up:** Updated data → Dashboard refresh → Card adherence review → Care plan refinement
- [ ] **Diagnosis Entry:** New diagnosis → Score modifiers applied → Cards triggered → Care plan updated
- [ ] **Lifestyle Assessment:** Pillar questionnaire → Scores calculated → Behavioral cards recommended

---

## DOCUMENTATION UPDATE PROTOCOL

**Always update:**

1. [ ] Project-specific CHANGELOG or README
2. [ ] [INTEGRATION_ARCHITECTURE.md](INTEGRATION_ARCHITECTURE.md) if cross-project dependencies changed
3. [ ] This checklist if new integration patterns emerge

---

## BREAKING CHANGE PROTOCOL

**If your change breaks existing integration:**

1. [ ] Document the breaking change prominently in all affected projects
2. [ ] Update INTEGRATION_ARCHITECTURE.md with migration path
3. [ ] Create versioned backups before implementing
4. [ ] Update data models in INTEGRATION_ARCHITECTURE.md
5. [ ] Test all workflows end-to-end before considering complete

---

## QUICK VALIDATION COMMANDS

**Use these to verify integration integrity:**

- **Terminology search:** Search for key terms across all projects to ensure consistency
- **Cross-reference check:** Verify diagnosis codes match between HEALTH OVERVIEW and SMART SYSTEM
- **Workflow trace:** Manually trace a patient scenario through all three projects
- **Version alignment:** Check that referenced features exist in all projects

---

## EMERGENCY CONTACTS

**If you break integration and need to rollback:**

- Git commit history: Review recent changes
- INTEGRATION_ARCHITECTURE.md version history: Check what changed
- Project-specific CHANGELOGs: Identify when breaking change introduced

---

## EXAMPLES OF INTEGRATED UPDATES

### Example 1: Adding a New Diagnosis

**Scenario:** Adding "Chronic Kidney Disease Stage 3" to HEALTH OVERVIEW

**Required updates:**
1. **HEALTH OVERVIEW:** Add to diagnosis library with ICD-10 code (N18.3), score modifiers, parameter targets
2. **SMART SYSTEM:** Create CKD cards (eGFR monitoring, diet modifications, medication adjustments, BP control)
3. **PERFORMANCE MEDICINE:** Add to care planning templates, update filtration system assessment
4. **INTEGRATION_ARCHITECTURE.md:** Add to diagnosis → card trigger mapping table

---

### Example 2: Updating Evidence Grade

**Scenario:** New guideline changes Aspirin for primary prevention from Grade A to Grade C

**Required updates:**
1. **SMART SYSTEM:** Update Aspirin card evidence grade from A to C
2. **PERFORMANCE MEDICINE:** Update evidence base with new citation, update preventive care matrix
3. **HEALTH OVERVIEW:** No changes needed (dashboard doesn't use evidence grades)
4. **INTEGRATION_ARCHITECTURE.md:** No changes needed (evidence grades defined in SMART SYSTEM)

---

### Example 3: Adding a New Lifestyle Pillar Question

**Scenario:** Adding "Do you eat breakfast daily?" to Nutrition pillar

**Required updates:**
1. **HEALTH OVERVIEW:** Add question to lifestyle questionnaire, update scoring algorithm
2. **SMART SYSTEM:** Add breakfast-related behavioral cards, update recommendation triggers
3. **PERFORMANCE MEDICINE:** Update Five Pillar definitions if needed, update clinical interpretation guide
4. **INTEGRATION_ARCHITECTURE.md:** Update pillar score → card mapping if new triggers added

---

**END OF CHECKLIST**

**Last updated:** 2025-11-26
