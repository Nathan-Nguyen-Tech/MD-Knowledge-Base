# HEALTH OVERVIEW DASHBOARD
## Master Project Instructions

**Last Updated:** November 19, 2025
**Project Phase:** MVP Development - Multi-User Dashboard
**Status:** Foundation + MVP Parameter Libraries Complete

---

## EXECUTIVE SUMMARY

### Project Vision
Create a unified **Health Overview Dashboard** that serves four distinct user groups through a single interface: **patients, caregivers, clinicians, and medical personnel**. The dashboard transforms clinical data into actionable health intelligence using progressive disclosure (Level 1→2→3), plain language translation, and transparent scoring methodology.

### Core Innovation
**One Dashboard, Universal Access:** No separate "patient view" vs "clinician view." All users access the same interface with role-aware features, language adaptation, and progressive disclosure allowing each person to control information depth based on their needs.

### Project Scope
- **MVP Target:** 50-100 clinical parameters across 8 organ systems and 5 lifestyle pillars
- **User Base:** Patients, caregivers/family, clinicians, medical personnel
- **Integration:** EMR → Flowsheet → Dashboard (with manual entry/edit capability)
- **Output:** Real-time health visualization with critical alerts, trend analysis, and biological age

---

## PROJECT TEAM ROLES

### Clinical Design Team (Current Phase Lead)
**Who We Are:** Clinical experts with product design expertise

**Our Responsibilities:**
- ✅ Define WHAT appears on dashboard (metrics, scores, alerts)
- ✅ Explain WHY it matters clinically (medical rationale)
- ✅ Specify HOW calculations work (formulas with inputs/outputs)
- ✅ Determine WHEN alerts trigger (thresholds, decision rules)
- ✅ Design HOW information displays (for all user types)
- ✅ Provide plain language translations

**What We DON'T Do:**
- ❌ Write code or pseudocode (IT team)
- ❌ Design databases or choose tech stack (IT team)
- ❌ Implement algorithms (IT team)
- ❌ Build actual interfaces (IT team with our specs)

### IT Development Team (Implementation Phase)
**Who They Are:** Software engineers, database architects, UX/UI developers

**Their Responsibilities:**
- Build calculation engines based on clinical specifications
- Design and implement database structures
- Create user interfaces per dashboard specifications
- Integrate with EMR systems
- Implement security and compliance (HIPAA)
- Performance optimization and scalability
- Testing and quality assurance

**What They Need From Us:**
- Complete clinical specifications (formulas, thresholds, logic)
- Visual design requirements (layouts, interactions)
- Plain language content (all user-facing text)
- Clinical validation of implementations
- User acceptance testing feedback

---

## CORE ARCHITECTURE OVERVIEW

### The Multi-User Design Principle

**Single Interface, Context-Aware Experience:**

```
Same Dashboard Application
    ↓
User Authentication → Role Detection
    ↓
┌──────────────┬──────────────┬──────────────┬──────────────┐
│   PATIENT    │  CAREGIVER   │  CLINICIAN   │   MEDICAL    │
│              │              │              │   PERSONNEL  │
├──────────────┼──────────────┼──────────────┼──────────────┤
│ Plain        │ Plain        │ Medical      │ Medical      │
│ Language     │ Language     │ Terminology  │ Terminology  │
│ Primary      │ Primary      │ Primary      │ Comfortable  │
├──────────────┼──────────────┼──────────────┼──────────────┤
│ Level 1: ✅  │ Level 1: ✅  │ Level 1: ✅  │ Level 1: ✅  │
│ Level 2: ✅  │ Level 2: ✅  │ Level 2: ✅  │ Level 2: ✅  │
│ Level 3: ✅  │ Level 3: ✅  │ Level 3: ✅  │ Level 3: ✅  │
│ (Plain Lang) │ (Plain Lang) │ (Full Analy) │ (Full Data)  │
├──────────────┼──────────────┼──────────────┼──────────────┤
│ View data    │ View data    │ View data    │ View data    │
│ Track trends │ Monitor      │ Deep analysis│ Data entry   │
│ Set goals*   │ loved ones   │ Clinical     │ Flowsheet    │
│ Export PDF   │ Export PDF   │ decisions    │ Alert mgmt   │
│              │ Alerts*      │ Export       │ Coordination │
└──────────────┴──────────────┴──────────────┴──────────────┘
                         * = Future features
```

### The 24-Cell Health Matrix

**Foundation:** 8 Organ Systems × 3 Evaluation Domains = 24 Assessment Cells

#### 8 Organ Systems:
1. **Neurological** - CNS, PNS, mental health, cognition
2. **Cardiovascular** - Heart + vascular system
3. **Respiratory** - Airways, gas exchange
4. **Metabolic** - GI, hepatobiliary, pancreatic, metabolic pathways
5. **Renal/Filtration** - Kidney function
6. **Musculoskeletal** - Bones, joints, muscles
7. **Immune** - Infection defense, inflammation, oncology
8. **Reproductive/Endocrine** - Hormones, reproductive health

#### 3 Evaluation Domains (per system):
1. **Structure (Anatomy)** - Organ integrity, physical form (25% weight)
2. **Function (Physiology)** - Current performance capacity (50% weight)
3. **Risk (Prognosis)** - Future deterioration probability (25% weight)

Each clinical parameter contributes to multiple cells with different weights (0-100%), creating a comprehensive interconnected health assessment.

### The Scoring Hierarchy

```
Individual Parameters (normalized 0-100)
    ↓ [weighted by domain]
Domain Scores per System (Structure/Function/Risk: 0-100)
    ↓ [weighted 25%/50%/25%]
System Health Scores (8 systems: 0-100)
    ↓ [weighted by criticality]
Objective Health Component (0-100) [70% weight]
    +
Lifestyle Pillar Scores (5 pillars: 0-100)
    ↓ [weighted by criticality]
Subjective Health Component (0-100) [30% weight]
    =
OVERALL HEALTH SCORE (0-100)
```

### Data Flow Architecture

```
EMR System
    ↓ [Import/Integration]
FLOWSHEET (Central Data Hub)
    ↓ [Validation, Manual Entry/Edit]
CLINICAL LOGIC ENGINE
    • Parameter Normalization
    • Context Rules
    • Temporal Scoring
    • Aggregation
    • Alert Detection
    • Transparency Calculation
    ↓ [Calculated Scores & Alerts]
DASHBOARD (Visual Display Layer)
    • Level 1: Hero View
    • Level 2: System Overview
    • Level 3: Detail Analysis
    ↓ [Role-Aware Display]
USER (Patient/Caregiver/Clinician/Staff)
```

---

## KEY CLINICAL PRINCIPLES

### 1. Conservative But Motivating Baseline
- **Z-score of 0** (at personalized target) = **85 points**, NOT 100
- Rewards patients for achieving healthy targets (B+ grade)
- Leaves room for sustained excellence (86-100)
- Prevents overconfidence without demotivating patients
- **Score 50** = neutral/unknown (used for incomplete data)
- **Rationale:** Unmeasured ≠ At Target. Missing data gets neutral score.

### 2. Transparent Scoring
- Every composite score decomposable to contributing parameters
- Always show "What's Working Well" and "What Needs Work"
- Never hide what drives a number
- Data completeness always displayed

### 3. Critical Safety First
- Life-threatening parameters flagged regardless of composite scores
- Good overall score cannot mask a critical finding
- Alert hierarchy: Critical → Urgent → Warning → Monitor
- Critical alerts always prominent, cannot be hidden

### 4. Plain Language Accessibility
- Medical jargon translated to 6th-8th grade reading level
- Contextual education available on-demand
- Never forced or condescending
- Clinicians can toggle to medical terminology

### 5. Personalized Targets
- Reference ranges adapt to age, sex, conditions, medications
- No one-size-fits-all thresholds
- Context rules adjust interpretation (pregnancy, medications, comorbidities)

### 6. Actionable Intelligence
- Not just data display - clear guidance on what needs attention
- Specific, achievable recommendations
- Priority-ranked action items
- Support shared decision-making

### 7. Progressive Disclosure
- Level 1: Quick status (all users)
- Level 2: System exploration (engaged users)
- Level 3: Deep analysis (analytical users, clinicians)
- User controls depth, not system-imposed limitations

### 8. Role-Aware Experience
- Same data, adapted presentation
- Language appropriate to user expertise
- Features relevant to user goals
- Workflow support for clinician efficiency

---

## DOCUMENT LIBRARY & DELIVERABLES

### Foundation Documents (Complete)

| Document | Status | Purpose |
|----------|--------|---------|
| **PROJECT_SPECIFICATION_v2.md** | ✅ Complete | Master project vision and scope |
| **PROJECT_ARCHITECTURE.md** | ✅ Complete | Technical architecture for multi-user system |
| **PROJECT_INSTRUCTIONS_MASTER.md** | ✅ Complete | This document - team coordination |
| **FRAMEWORK_SUMMARY.md** | ✅ Complete | Parameter scoring framework overview |

### Core Clinical Logic Documents (Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **PARAMETER_NORMALIZATION_v2.md** | ✅ Complete | ~15 | Core normalization methods (5 methods) |
| **CALIBRATION_VALIDATION.md** | ✅ Complete | ~12 | Validation methodology, governance |
| **CONTEXT_RULES.md** | ✅ Complete | ~8 | Patient-specific adjustments |
| **TEMPORAL_SCORING.md** | ✅ Complete | ~6 | Time-series handling, trends |

**How These Work Together:**
1. **PARAMETER_NORMALIZATION** defines WHAT methods exist
2. **CALIBRATION_VALIDATION** ensures clinical fidelity
3. **CONTEXT_RULES** handles special cases (pregnancy, meds, conditions)
4. **TEMPORAL_SCORING** smooths serial measurements over time

**Total Framework:** ~41 pages, ~1 hour read time

### Scoring & Aggregation Documents (Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **SYSTEM_DOMAIN_SCORING_v2.md** | ✅ Complete | ~15 | 24-cell aggregation formulas |
| **COMPOSITE_SCORING_v2.md** | ✅ Complete | ~13 | Overall health score calculation |
| **BIOLOGICAL_AGE_SPEC_v1_1.md** | ✅ Complete | ~18 | Modified PhenoAge methodology |

### Alert & Safety Documents (Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **CRITICAL_ALERTS_v1_1.md** | ✅ Complete | ~22 | Critical thresholds, alert logic |
| **CLINICAL_DECISION_RULES_v1_0.md** | ✅ Complete | ~17 | Complex IF-THEN clinical rules |
| **TRANSPARENCY_DISPLAY_v1_1.md** | ✅ Complete | ~20 | Top contributor logic, explainability |

### Dashboard Specifications (Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **DASHBOARD_LEVEL1_SPEC_v1_1.md** | ✅ Complete | ~22 | Hero view (all users) |
| **DASHBOARD_LEVEL2_SPEC_v1_1.md** | ✅ Complete | ~26 | System overview (engaged users) |
| **DASHBOARD_LEVEL3_SPEC_v1_1.md** | ✅ Complete | ~38 | Detail analysis (analytical users) |

### Parameter Library Documents (MVP Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **MASTER_PARAMETER_LIBRARY_v1.md** | ✅ Complete | ~40 | Complete parameter inventory (~450 params) |
| **PARAMETER_NORMALIZATION_SPECIFICATIONS_MVP.md** | ✅ Complete | ~85 | Full specifications for 150 MVP parameters |
| **PARAMETER_WEIGHT_MATRIX_TEMPLATES.md** | ✅ Complete | ~35 | 35 weight templates for 24-cell matrix |
| **STANDARDIZED_IMAGING_TEMPLATES.md** | ✅ Complete | ~45 | 128 imaging parameters across 10 modalities |

**MVP Coverage:** 150 fully-specified parameters
- Vital Signs: 15 parameters
- Laboratory Tests: 45 parameters
- Urinalysis: 10 parameters
- Body Composition: 7 parameters (InBody H20N)
- Functional Tests: 6 parameters
- EKG Findings: 10 parameters
- Lifestyle Assessment: 6 parameters (5 pillars + composite)
- Physical Examination: 15 parameters

**Future Expansion Documents (Planned):**

| Document | Status | Est. Pages | Purpose |
|----------|--------|------------|---------|
| **PARAMETERS_ADVANCED_LABS.md** | 📋 Planned | 25-30 | Additional 100+ specialized labs |
| **PARAMETERS_ADVANCED_IMAGING.md** | 📋 Planned | 20-25 | Advanced imaging parameters |
| **PARAMETERS_WEARABLES.md** | 📋 Planned | 15-20 | Wearable device integration |

### Medical History & Context Documents (MVP Complete)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **MEDICAL_HISTORY_TIER1_LIBRARY.md** | ✅ Complete | ~120 | 132 common diagnoses with context rules |
| **CALCULATION_STRESS_TEST_REPORT.md** | ✅ Complete | ~18 | Mathematical validation of formulas |
| **PARAMETER_WEIGHT_MANAGEMENT_STRATEGY.md** | ✅ Complete | ~12 | Weight assignment strategy & rationale |

**Medical History Integration:**
- **Tier 1:** 132 fully-specified diagnoses across 8 organ systems
  - Each includes: ICD-10 codes, context rules, score modifiers, monitoring requirements
  - Covers 80-90% of patient population
- **Tier 2:** Category-based rules for rare diagnoses
  - 30 diagnostic categories provide fallback for "zebra" conditions
- **Score Modifiers:** Domain-level baseline adjustments
  - Example: Type 2 Diabetes → Metabolic-Function -15 points, Cardiovascular-Risk -10 points
- **Context Rules:** Automatic parameter target adjustments
  - Example: Diabetic HbA1c target <7.0% instead of <5.7%

**Future Medical History Documents (Planned):**

| Document | Status | Est. Pages | Purpose |
|----------|--------|------------|---------|
| **SURGICAL_HISTORY_LIBRARY.md** | 📋 Planned | 30-40 | Common surgical procedures with implications |
| **MEDICATION_CONTEXT_LIBRARY.md** | 📋 Planned | 40-50 | 50-100 common medications with expected parameter changes |
| **FAMILY_HISTORY_TEMPLATE.md** | 📋 Planned | 15-20 | Heritable conditions with risk multipliers |

### Lifestyle Assessment Documents (Placeholder)

| Document | Status | Pages | Purpose |
|----------|--------|-------|---------|
| **LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md** | ✅ Placeholder | ~8 | Structure for 5-pillar assessment (content TBD) |

**Note:** Detailed lifestyle questionnaire content development on hold per user request - requires separate discussion for instrument selection, question count, cultural adaptation, and scoring algorithms.

**Parameter Specification Template:**
Each parameter requires:
- Name (medical + plain language)
- Clinical significance
- Measurement details and units
- Normalization method and configuration (α, β, SD)
- Reference ranges (default + personalized)
- Critical thresholds with rationale
- 24-cell weight matrix with justification
- Context rules (if any)
- Temporal strategy
- Alert messages (patient + clinician versions)
- Related parameters
- Clinical notes and evidence base

### Content & UX Documents (To Be Created)

| Document | Status | Est. Pages | Purpose |
|----------|--------|------------|---------|
| **PLAIN_LANGUAGE_LIBRARY.md** | 📋 Planned | 20-25 | All medical → plain translations |
| **ALERT_MESSAGES.md** | 📋 Planned | 15-20 | Patient & clinician alert messages |
| **CONTEXTUAL_HELP_CONTENT.md** | 📋 Planned | 25-30 | All help text and education |
| **USER_FLOWS_MULTI_ROLE.md** | 📋 Planned | 20-25 | User navigation patterns (all roles) |

### Implementation Handoff Documents (To Be Created)

| Document | Status | Est. Pages | Purpose |
|----------|--------|------------|---------|
| **IT_IMPLEMENTATION_GUIDE.md** | 📋 Planned | 30-40 | Master developer instruction manual |
| **API_SPECIFICATION.md** | 📋 Planned | 20-30 | RESTful API endpoints, data models |
| **DATA_MODEL.md** | 📋 Planned | 20-25 | Database schemas, relationships |
| **INTEGRATION_SPECIFICATION.md** | 📋 Planned | 15-20 | EMR integration requirements |
| **TESTING_VALIDATION_PLAN.md** | 📋 Planned | 20-25 | UAT, clinical validation procedures |

---

## WORKFLOW: ADDING A NEW PARAMETER

When specifying a new clinical parameter, follow this systematic process:

### Step 1: Clinical Classification
**Document:** PARAMETER_NORMALIZATION_v2.md

**Questions to Answer:**
- What is this parameter measuring?
- Is it bidirectional (can be too high or too low) or unidirectional?
- Which normalization method applies?
  - Normal distribution (bidirectional)
  - Normal distribution (unidirectional)
  - Lognormal/percentile-based
  - Nonlinear risk curve
  - Binary
  - Ordinal
- What is the personalized target determination logic?
- What are the clinical zones (Green/Yellow/Orange/Red)?

### Step 2: Calibration & Validation
**Document:** CALIBRATION_VALIDATION.md

**Process:**
1. Define 5-7 clinical anchor points with target scores
   - Example: SBP 90 → Score 20, SBP 120 → Score 85, SBP 180 → Score 5
2. Optimize α, β, SD coefficients to match anchors
3. Validate against standardized severity bands
   - Ensure "Stage 2 HTN" scores similarly to "Poor diabetes control"
4. Document SD sources (literature, lab ranges, guidelines, expert consensus)
5. Record validation results
6. Obtain Coefficient Review Board approval

### Step 3: Identify Context Rules
**Document:** CONTEXT_RULES.md

**Questions to Answer:**
- Does pregnancy alter targets or interpretation?
- Do medications cause expected abnormalities?
  - Example: ACE inhibitors raise potassium (expected, not alarming)
- Are comorbidity-specific adjustments needed?
  - Example: eGFR >120 is hyperfiltration in diabetics, excellent in healthy
- Are age-specific adjustments needed?
- Does acute vs chronic context matter?
- Are there artifact conditions (dehydration, post-exercise)?

**If YES to any:** Document rule logic with priority level (1=must, 2=should, 3=may)

### Step 4: Define Temporal Strategy
**Document:** TEMPORAL_SCORING.md

**Questions to Answer:**
- How volatile is this parameter?
  - Acute/Dynamic: Home BP readings (high volatility)
  - Semi-dynamic: HbA1c (quarterly trending)
  - Stable: Imaging findings (annual or less)
- Point score vs stability score weighting?
  - High volatility → Higher stability weight
  - Low volatility → Higher point score weight
- Smoothing method?
  - EMA (Exponential Moving Average)
  - Median filtering (window size 3, 5, or 7)
  - Hybrid (weighted combination)
- Aberrant value detection thresholds?
- Trend display requirements (↑↓→)?

### Step 5: System-Domain Weight Assignment
**Document:** SYSTEM_DOMAIN_SCORING_v2.md

**Process:**
1. Identify primary system (100% relevance)
2. Identify related systems (0-50% relevance)
3. For each system, assign domain weights:
   - Structure (Anatomy): Does it reflect organ integrity?
   - Function (Physiology): Does it measure performance?
   - Risk (Prognosis): Does it predict future deterioration?
4. Sum to reasonable totals (typically 2-4 across all 24 cells)
5. Validate with clinical panel for high-priority parameters

**Example: Systolic Blood Pressure**
```
Cardiovascular System:
  - Structure: 30% (vessel integrity)
  - Function: 80% (hemodynamic performance)
  - Risk: 100% (cardiovascular event risk)
Neurological System:
  - Risk: 30% (stroke risk)
Renal System:
  - Risk: 40% (kidney damage risk)
```

### Step 6: Critical Thresholds
**Document:** CRITICAL_ALERTS_v1_1.md

**Define:**
- Critical Low (Red): Immediate danger
- Urgent Low (Orange): Same-day attention
- Warning Low (Yellow): Address soon
- Warning High (Yellow): Address soon
- Urgent High (Orange): Same-day attention
- Critical High (Red): Immediate danger

**For Each Threshold:**
- Clinical rationale (evidence-based)
- Patient message (plain language)
- Clinician message (clinical detail)
- Recommended action
- Display priority

### Step 7: Documentation & Review
**Document:** Parameter library files (PARAMETERS_*.md)

**Complete Specification Includes:**
- All steps above
- Worked example with real numbers
- Plain language description ("What is this?" "Why it matters")
- Clinical notes and evidence references
- Related parameters
- Version and approval date

**Result:** Fully specified parameter ready for IT implementation

---

## SPECIFICATION STANDARDS

### Every Specification Must Include

#### 1. WHAT (Clear Definition)
```
ELEMENT: [Name of element/calculation]
TYPE: [Score/Alert/Visualization/Message]
LOCATION: [Dashboard Level 1/2/3]
USER VISIBILITY: [Patient/Caregiver/Clinician/Staff/All]
```

#### 2. WHY (Clinical Justification)
```
CLINICAL PURPOSE: [Medical rationale]
EVIDENCE BASE: [Guidelines, studies, expert consensus]
USER BENEFIT: [How this helps each user type]
```

#### 3. HOW (Calculation Specification)
```
INPUTS: [All required data with units]
FORMULA: [Mathematical calculation]
CALCULATION STEPS: [Step-by-step process]
OUTPUT: [What is produced, range, format]
EXAMPLE: [Worked example with real numbers]
```

#### 4. WHEN (Trigger Conditions)
```
DISPLAY RULES: [When does this appear?]
ALERT TRIGGERS: [What values trigger alerts?]
UPDATE FREQUENCY: [How often recalculated?]
```

#### 5. HOW DISPLAYED (Presentation)
```
VISUAL FORMAT: [Number/graph/color/icon/text]
PATIENT LANGUAGE: [Plain English version]
CAREGIVER VIEW: [Any specific adaptations]
CLINICIAN VIEW: [Medical terminology, additional detail]
STAFF VIEW: [Workflow considerations]
COLOR CODING: [Green/Yellow/Orange/Red zones]
CONTEXT: [Surrounding information shown]
INTERACTIVE BEHAVIOR: [Click, hover, expand]
```

### Quality Checklist

Before finalizing any specification:

#### Clinical Accuracy ✓
- ☐ Based on current medical evidence
- ☐ Aligns with established guidelines
- ☐ Thresholds clinically validated
- ☐ Formulas medically sound
- ☐ No false reassurance created
- ☐ No unnecessary alarms created

#### Mathematical Clarity ✓
- ☐ Formulas unambiguous
- ☐ All inputs defined with units
- ☐ Calculation steps explicit
- ☐ Output ranges specified
- ☐ Edge cases addressed
- ☐ Examples demonstrate correctly

#### Multi-User Utility ✓
- ☐ Patients can understand (plain language)
- ☐ Caregivers find it useful (accessible)
- ☐ Clinicians find it useful (actionable)
- ☐ Staff can use it (workflow-optimized)
- ☐ Actionable insights provided
- ☐ Not overwhelming or confusing
- ☐ Facilitates shared decision-making

#### Completeness ✓
- ☐ All required inputs identified
- ☐ Missing data scenarios handled
- ☐ Color zones defined
- ☐ Plain language provided
- ☐ Clinical context included
- ☐ Worked examples given
- ☐ Role-specific adaptations specified

---

## COLOR-CODED STATUS SYSTEM

### Universal Color Zones

| Color | Score | Status | Action | Display Strategy |
|-------|-------|--------|--------|------------------|
| 🟢 **Green** | 75-100 | Optimal | Maintain current approach | Positive reinforcement, celebrate wins |
| 🟡 **Yellow** | 60-74 | Monitor | Routine follow-up, consider optimization | Encouraging with improvement suggestions |
| 🟠 **Orange** | 40-59 | Act Soon | Clinician consultation (days to weeks) | Clear action items with appropriate urgency |
| 🔴 **Red** | 0-39 | Urgent | Same-day clinician contact or emergency | Prominent alerts with immediate actions |

### Application Hierarchy

1. **Critical Parameter Thresholds** override composite scores
2. **Individual Parameters** show their own color
3. **Domain Scores** (Structure/Function/Risk) show composite color
4. **System Scores** show weighted composite color
5. **Overall Health Score** shows final composite color

**Critical Rule:** A red parameter ALWAYS displays prominently, even if system score is green. Safety first.

---

## USER EXPERIENCE DESIGN PRINCIPLES

### For All Users

1. **Same Interface:** No separate "views" - everyone sees same dashboard
2. **Choose Your Depth:** Progressive disclosure (Level 1→2→3) lets users control detail
3. **Plain Language Foundation:** Medical terms always translated, contextual help available
4. **Action-Oriented:** Focus on "what to do" not just "what is"
5. **Visual First:** Charts and colors before tables and numbers
6. **Contextual Education:** Help available on-demand, never forced
7. **Transparent Scoring:** Always show what drives a number

### Patient-Specific Considerations

**Goals:**
- Understand health status without medical degree
- Know what needs attention and why
- Track progress over time
- Communicate effectively with care team
- Feel empowered, not overwhelmed

**Design Approach:**
- Start simple (Level 1 sufficient for quick check)
- Celebrate wins (positive reinforcement for healthy parameters)
- Clear next steps (specific, achievable recommendations)
- Progress tracking (visual trends show improvement)
- Shared language (common ground with providers)

### Caregiver-Specific Considerations

**Goals:**
- Monitor loved one's health without confusion
- Understand priority concerns
- Know when to seek help
- Support care decisions
- Coordinate with healthcare team

**Design Approach:**
- Accessible language (no medical degree required)
- Focus on priorities (Level 1 clearly shows what needs attention)
- Shared understanding (common view facilitates discussions)
- Trend awareness (see if improving or declining)
- Alert routing (optional critical alert notifications)

### Clinician-Specific Considerations

**Goals:**
- Rapid comprehensive assessment
- Deep analytical capability when needed
- Never miss critical findings
- Support clinical decision-making
- Efficient documentation and workflow

**Design Approach:**
- Rapid assessment (Level 1 sufficient for quick status)
- Deep dive available (Level 3 full analytical capability)
- Critical flags first (never miss urgent findings)
- Efficient workflow (default filters show "what matters now")
- Export & share (easy report generation for consultations)
- Evidence access (references and guidelines integrated)

### Medical Personnel-Specific Considerations

**Goals:**
- Care coordination across team
- Patient triage and prioritization
- Data entry and validation
- Alert management
- Support clinician workflow

**Design Approach:**
- Workflow-optimized (task-oriented interfaces)
- Data entry efficiency (flowsheet optimized for speed and accuracy)
- Alert management (acknowledge, route, escalate)
- Care coordination tools (team communication)
- Quality assurance (validation, completeness checks)

---

## IMPLEMENTATION PRIORITIES & ROADMAP

### Phase 1: MVP Foundation (Current - Months 1-6)

**Clinical Logic: ✅ COMPLETE**
- ✅ Parameter normalization framework
- ✅ Calibration and validation methodology
- ✅ Context rules engine
- ✅ Temporal scoring strategies
- ✅ System-domain aggregation
- ✅ Composite scoring
- ✅ Biological age calculation
- ✅ Critical alert logic
- ✅ Transparency and explainability
- ✅ Clinical decision rules

**Dashboard Architecture: ✅ COMPLETE**
- ✅ Multi-user architecture design
- ✅ Level 1/2/3 specifications
- ✅ Progressive disclosure model
- ✅ Role-aware display strategy

**Next Steps (Months 2-4):**
- 📋 Create parameter library (50-100 parameters)
  - Vital signs (~10 parameters)
  - Basic labs (~20 parameters)
  - Specialized labs (~20 parameters)
  - Imaging findings (~10 parameters)
  - Functional tests (~10 parameters)
  - Lifestyle assessments (5 pillars)
- 📋 Plain language library
- 📋 Alert message library
- 📋 Contextual help content

**IT Handoff (Months 4-6):**
- 📋 IT implementation guide
- 📋 API specifications
- 📋 Data model documentation
- 📋 Integration requirements
- 📋 Testing and validation plan

### Phase 2: Development & Testing (Months 7-12)

**Development:**
- Build calculation engine
- Implement database structures
- Create dashboard interface
- EMR integration
- Security and compliance implementation

**Testing:**
- Unit testing (calculation accuracy)
- Integration testing (data flow)
- Clinical validation (50-100 patient datasets)
- User acceptance testing
  - 5-10 clinicians in practice
  - 20-30 patients reviewing dashboards
  - 10-20 caregivers providing feedback
  - Medical staff testing workflows

**Refinement:**
- Address validation findings
- Optimize performance
- Refine user experience
- Complete documentation

### Phase 3: Pilot Deployment (Months 13-18)

**Initial Rollout:**
- 100-500 patients
- 5-10 clinicians
- Single clinic/practice
- Intensive monitoring and support

**Metrics Tracking:**
- Technical performance (load times, uptime, errors)
- Clinical accuracy (alert sensitivity, false positives)
- User adoption (engagement, return visits, feature use)
- User satisfaction (NPS, feedback surveys)

**Iteration:**
- Weekly feedback review
- Bi-weekly updates and improvements
- Monthly clinician check-ins
- Quarterly patient surveys

### Phase 4: Full Production (Months 19-24)

**Scale-Up:**
- 5,000+ patients
- 50+ clinicians
- Multiple clinics/practices
- Automated monitoring

**Feature Expansion:**
- Advanced analytics
- Trend predictions
- Patient goal setting
- Family/caregiver sharing (with consent)
- Mobile optimization

### Phase 5: Advanced Features (Year 2+)

**Enhancement Priorities:**
- Wearable device integration
- Patient-entered lifestyle data
- Machine learning for prediction
- Automated intervention recommendations
- Population health analytics
- Outcomes research capability

---

## COMMUNICATION PROTOCOLS

### Clinical Team ↔ IT Team

**What Clinical Team Provides:**
1. Complete specifications (all WHAT, WHY, HOW, WHEN, HOW DISPLAYED)
2. Formulas with all inputs/outputs explicitly defined
3. Decision rules for alerts and color coding
4. Visual hierarchy requirements
5. Plain language text for all displays
6. Worked examples for validation
7. Clinical validation of implementations

**What IT Team Provides:**
1. Questions when specifications ambiguous
2. Technical constraints affecting design
3. Implementation options for complex calculations
4. Feasibility assessments
5. Working prototypes for validation
6. Performance and scalability analysis
7. Security and compliance implementation

**Handoff Format:**
- Each specification document = requirements document for IT
- IT builds: calculation engines, databases, UIs, business logic
- Clinical team validates: accuracy, usability, clinical appropriateness

### Communication Cadence

**Development Phase:**
- Daily standups (15 min) - blockers and progress
- Weekly planning (1 hour) - sprint planning
- Bi-weekly demos (1 hour) - working software review
- Monthly reviews (2 hours) - clinical validation, user feedback

**Post-Launch:**
- Weekly metrics review
- Monthly feature planning
- Quarterly strategic review
- Annual roadmap planning

---

## SUCCESS METRICS

### Technical Metrics (IT Responsibility)
- ✅ Dashboard load time <3 seconds (Level 1)
- ✅ API response time <500ms (p95)
- ✅ Calculation accuracy 100% (vs manual validation)
- ✅ System uptime 99.9%
- ✅ Zero data breaches
- ✅ HIPAA compliance maintained

### Clinical Metrics (Joint Responsibility)
- ✅ Critical alerts detected 100% (sensitivity)
- ✅ False positive rate <5%
- ✅ Clinician satisfaction >4/5
- ✅ Patient comprehension >80%
- ✅ Time to identify priorities <2 minutes
- ✅ Clinical decision support effectiveness

### Adoption Metrics (Product Team)
- ✅ 80% user activation within 30 days
- ✅ Level 2+ engagement >50%
- ✅ Return visits >2x per month
- ✅ Feature utilization >60%
- ✅ Net Promoter Score >50
- ✅ Patient-clinician communication improved

### Outcome Metrics (Long-Term)
- Improved patient engagement with health data
- Increased adherence to treatment plans
- Earlier detection of health deterioration
- Better patient-clinician communication
- Reduced time explaining results
- Higher patient satisfaction scores

---

## RISK MANAGEMENT

### Top Risks & Mitigations

#### Technical Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Calculation errors | Critical | Comprehensive testing, validation datasets |
| Performance degradation | High | Load testing, caching, optimization |
| Data breach | Critical | Security best practices, audits, compliance |
| EMR integration failure | High | Fallback to manual entry, phased integration |

#### Clinical Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| False reassurance (missed critical) | Critical | Mandatory alert displays, validation, clinical review |
| Unnecessary alarm (patient anxiety) | Medium | Clinical threshold validation, evidence-based criteria |
| Patient misinterpretation | Medium | Plain language, contextual help, user testing |
| Clinician over-reliance | High | Clinical judgment emphasis, training, disclaimers |

#### Adoption Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| User adoption failure | High | Training, change management, user-centered design |
| Workflow disruption | Medium | Iterative rollout, feedback loops, workflow analysis |
| Scope creep | Medium | Phased roadmap, prioritization, MVP discipline |

---

## REFERENCE MATERIALS

### Clinical Guidelines to Reference
- **ACC/AHA** - American College of Cardiology / American Heart Association
- **ESC** - European Society of Cardiology
- **ADA** - American Diabetes Association
- **KDIGO** - Kidney Disease: Improving Global Outcomes
- **ATS** - American Thoracic Society
- **NCCN** - National Comprehensive Cancer Network
- **WHO** - World Health Organization standards
- **ACSM** - American College of Sports Medicine
- **AAN** - American Academy of Neurology

### Evidence Base
- Peer-reviewed medical literature
- Validated risk calculators (Framingham, ASCVD, QRISK, etc.)
- Laboratory standardized reference ranges
- Clinical expert consensus
- Epidemiological studies
- Comparative effectiveness research

### Design Resources
- **WCAG 2.1** - Web Content Accessibility Guidelines
- **Plain Language Action Network** - Writing guidelines
- **Health literacy best practices** - Patient communication
- **Clinical decision support literature** - CDS design patterns

---

## APPENDIX: KEY TERMINOLOGY

### Clinical Terms

**24-Cell Matrix:** 8 organ systems × 3 domains (Structure/Function/Risk) = 24 evaluation points

**Normalized Score:** All parameters converted to 0-100 scale for standardized comparison

**Z-Score:** Statistical measure of standard deviations from ideal target

**Conservative Baseline:** Design principle where "at target" (z=0) = 85 points, not 100

**Completeness Factor:** Adjustment when data sparse, blending calculated scores with neutral baseline

**Critical Flag:** Alert for dangerous parameters, displayed regardless of composite scores

**Biological Age:** Health-based age calculation reflecting physiological status beyond chronological years

**Context Rules:** Patient-specific adjustments (pregnancy, medications, comorbidities)

**Temporal Scoring:** Handling serial measurements to smooth volatility and detect trends

### Dashboard Terms

**Progressive Disclosure:** UI pattern revealing information in layers (Level 1→2→3) based on engagement

**Level 1 (Hero View):** Quick status overview for all users

**Level 2 (System Overview):** System-level exploration with coxcomb charts

**Level 3 (Detail Analysis):** Deep parameter-level analysis for clinicians and analytical users

**Coxcomb Chart:** Radial visualization where wedge size represents score

**Transparency Section:** Decomposition showing "what's working" and "what needs work"

**Role-Aware Display:** Same interface adapting presentation based on user context

### Technical Terms

**Flowsheet:** Central data collection interface where all health information is entered and validated

**EMR (Electronic Medical Record):** Source system for patient clinical data

**Clinical Logic Engine:** Calculation system transforming raw data into normalized scores

**API (Application Programming Interface):** Programmatic interface for data exchange

**HIPAA:** Health Insurance Portability and Accountability Act (U.S. privacy regulation)

**SSO (Single Sign-On):** Authentication allowing access with one login

**RBAC (Role-Based Access Control):** Permission system based on user roles

---

## DOCUMENT CONTROL

### Version History
- **v3.0.0** (November 17, 2025) - Multi-user architecture, updated for all user types
- **v2.0.0** (November 12, 2025) - Clinical framework complete, dashboard specs complete
- **v1.0.0** (Initial) - Original project instructions

### Related Documents

**Foundation:**
- [PROJECT_SPECIFICATION_v2.md](PROJECT_SPECIFICATION_v2.md) - Master vision
- [PROJECT_ARCHITECTURE.md](PROJECT_ARCHITECTURE.md) - Technical architecture
- [FRAMEWORK_SUMMARY.md](FRAMEWORK_SUMMARY.md) - Parameter scoring overview

**Clinical Logic (Complete):**
- [PARAMETER_NORMALIZATION_v2.md](PARAMETER_NORMALIZATION_v2.md)
- [CALIBRATION_VALIDATION.md](CALIBRATION_VALIDATION.md)
- [CONTEXT_RULES.md](CONTEXT_RULES.md)
- [TEMPORAL_SCORING.md](TEMPORAL_SCORING.md)
- [SYSTEM_DOMAIN_SCORING_v2.md](SYSTEM_DOMAIN_SCORING_v2.md)
- [COMPOSITE_SCORING_v2.md](COMPOSITE_SCORING_v2.md)
- [BIOLOGICAL_AGE_SPEC_v1_1.md](BIOLOGICAL_AGE_SPEC_v1_1.md)

**Alerts & Safety (Complete):**
- [CRITICAL_ALERTS_v1_1.md](CRITICAL_ALERTS_v1_1.md)
- [CLINICAL_DECISION_RULES_v1_0.md](CLINICAL_DECISION_RULES_v1_0.md)
- [TRANSPARENCY_DISPLAY_v1_1.md](TRANSPARENCY_DISPLAY_v1_1.md)

**Dashboard (Complete):**
- [DASHBOARD_LEVEL1_SPEC_v1_1.md](DASHBOARD_LEVEL1_SPEC_v1_1.md)
- [DASHBOARD_LEVEL2_SPEC_v1_1.md](DASHBOARD_LEVEL2_SPEC_v1_1.md)
- [DASHBOARD_LEVEL3_SPEC_v1_1.md](DASHBOARD_LEVEL3_SPEC_v1_1.md)

**Parameter Library (Planned):**
- PARAMETERS_VITAL_SIGNS.md
- PARAMETERS_BASIC_LABS.md
- PARAMETERS_SPECIALIZED_LABS.md
- PARAMETERS_IMAGING.md
- PARAMETERS_FUNCTIONAL_TESTS.md
- PARAMETERS_LIFESTYLE.md

**Content (Planned):**
- PLAIN_LANGUAGE_LIBRARY.md
- ALERT_MESSAGES.md
- CONTEXTUAL_HELP_CONTENT.md
- USER_FLOWS_MULTI_ROLE.md

**Implementation (Planned):**
- IT_IMPLEMENTATION_GUIDE.md
- API_SPECIFICATION.md
- DATA_MODEL.md
- INTEGRATION_SPECIFICATION.md
- TESTING_VALIDATION_PLAN.md

### Approval & Sign-Off

**Clinical Lead:** _____________________
**Technical Architect:** _____________________
**Product Owner:** _____________________
**User Experience Lead:** _____________________
**Date:** _____________________

---

## READY TO PROCEED

**Current Status:** Foundation complete, ready for parameter library creation

**Next Priority:** Create PARAMETERS_VITAL_SIGNS.md as first parameter specification document

**Success Criteria:**
- IT team can implement without guessing
- Clinical accuracy is verifiable
- Every calculation has worked examples
- All edge cases addressed
- Plain language provided for all terms
- All four user types supported

---

**END OF PROJECT INSTRUCTIONS**

*This master document coordinates all work across the Health Overview Dashboard project, ensuring clinical specifications, technical architecture, and multi-user design work together seamlessly.*
