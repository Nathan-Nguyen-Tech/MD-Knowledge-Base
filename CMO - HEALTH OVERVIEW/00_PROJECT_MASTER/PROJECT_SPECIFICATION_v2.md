# PATIENT HEALTH DASHBOARD
## Master Project Specification

**Version:** 2.0.0  
**Date:** November 11, 2025  
**Document Type:** Master Architecture & Vision  
**Project Lead:** Performance Medicine Clinical Team  
**Status:** MVP Development Phase

---

## DOCUMENT STRUCTURE

This project uses a **hybrid documentation approach**:

### **Master Specification (This Document)**
- High-level architecture and vision
- Core principles and philosophy
- Feature overview
- User experience strategy
- Integration architecture

### **Technical Implementation Documents** (Separate .md Files)
- `CLINICAL_LOGIC_ENGINE.md` - All calculation formulas, algorithms, normalization methods Ã¢Å“â€¦ COMPLETE
- `DASHBOARD_ARCHITECTURE.md` - Detailed UI/UX specifications for Level 1/2/3 views (NEXT)
- `FLOWSHEET_SPECIFICATION.md` - Data entry interface and validation rules
- `DATA_MODEL.md` - Database schemas, structures, data flow
- `PARAMETER_LIBRARY.md` - Starter set of 50-100 parameters with all properties
- `IMPLEMENTATION_DECISIONS.md` - Design decisions and rationale log
- `CHANGELOG.md` - Version history and updates

---

## EXECUTIVE OVERVIEW

### Purpose

This dashboard creates a **unified health visualization system** for patients, caregivers, family members, and clinicians. It transforms objective clinical data and subjective lifestyle factors into a complete health picture using standardized language and progressive visual displays.

### Core Innovation

**Single Interface, Progressive Disclosure:** All users (patients, clinicians, caregivers) access the same dashboard with three levels of detail:
- **Level 1:** Hero view with overall score and top priorities (always visible)
- **Level 2:** System/pillar overview with interactive coxcomb charts (expandable)
- **Level 3:** Detailed parameter analysis with full transparency (drill-down)

### Target Users

- **Patients:** All walks of life seeking comprehensive health understanding
- **Clinicians:** Performance medicine specialists, consultants, medical specialists
- **Caregivers & Family:** Those involved in patient care decisions
- **Nurses & Support Staff:** Care coordination team members

### Clinical Specialty Context

**Performance Medicine** - An integrated approach combining:
- Family Medicine
- Internal Medicine
- Lifestyle Medicine
- Functional Medicine
- Sports Medicine

**Serving:** Elite athletes, executives, and all individuals seeking optimal health performance

---

## ARCHITECTURAL FOUNDATION

### Data Flow Architecture

```
EMR (Electronic Medical Record)
    Ã¢â€ â€œ
FLOWSHEET (The Bottleneck & Checkpoint)
    Ã¢â€ â€œ (manual entry, manual modification, AI/automation)
    Ã¢â€ â€œ
DASHBOARD (Visual Display Interface)
    Ã¢â€ â€œ
Progressive Disclosure (Level 1 Ã¢â€ â€™ 2 Ã¢â€ â€™ 3)
```

**Critical Understanding:**
- The **FLOWSHEET** is the central data collection and validation point
- All medical data flows through the flowsheet (manual or automated)
- The **DASHBOARD** is purely a visualization layer
- They are tightly integrated components of the broader EMR system

---

## CORE PRINCIPLES

### 1. Unified View
Single dashboard for all stakeholders - no separate "patient view" vs "clinician view"

### 2. Progressive Disclosure
Information revealed in layers based on user curiosity and need:
- Casual users stay at Level 1
- Engaged users explore Level 2
- Analytical users (clinicians, curious patients) dive into Level 3

### 3. Transparent Scoring
Every composite score must be decomposable to its contributing parameters. Never hide what drives a number.

### 4. Conservative But Motivating Baseline
"Perfect normal" (z-score = 0, at personalized target) maps to 85 points, not 100. This rewards patients for achieving healthy targets (B+ grade) while leaving room for sustained excellence (86-100). Prevents overconfidence without demotivating patients at goal.

### 5. Critical Safety First
Outlier parameters always flagged regardless of composite scores. A good overall score cannot mask a critical finding.

### 6. Plain Language
Medical jargon translated to patient-friendly terms with contextual education available on-demand.

### 7. Personalized Targets
All reference ranges and targets adapt to patient demographics, comorbidities, and medications.

### 8. Actionable Intelligence
Not just data display - clear guidance on what needs attention and why.

---

## THE HEALTH MATRIX: 24-CELL FRAMEWORK

### The 8 Organ Systems

1. **Neurological** - CNS, PNS, mental health, cognitive function
2. **Cardiovascular** - Heart + vascular system
3. **Respiratory** - Upper and lower airways, gas exchange
4. **Metabolic** - GI, hepatobiliary, pancreatic, metabolic pathways
5. **Renal/Filtration** - Pre-renal, intrarenal, post-renal function
6. **Musculoskeletal** - Bones, joints, muscles, connective tissue
7. **Immune** - Infection defense, inflammation, oncology surveillance
8. **Reproductive/Endocrine** - Hormones, reproductive health

### The 3 Evaluation Domains (Per System)

1. **Structure (Anatomy)** - Organ integrity, tissue architecture, physical form
2. **Function (Physiology)** - Primary functional capacity, performance
3. **Risk (Prognosis)** - Future deterioration probability, adverse event likelihood

**Result:** 8 systems Ãƒâ€” 3 domains = **24-cell health matrix**

Each parameter contributes to multiple cells with different weights (0-100%), creating a comprehensive, interconnected view of health.

---

## THE FLOWSHEET: DATA FOUNDATION

### Purpose
The flowsheet is the **central data repository** where all health information is collected, validated, and stored before visualization in the dashboard.

### Data Categories

#### **Clinical Measurements**
- Vital signs (HR, BP, RR, Temp, SpO2)
- Biometrics (BMI, waist circumference, body fat %, hip-to-waist ratio)
- Laboratory diagnostics (blood panels, urinalysis, specialized tests)
- Pathology results (biopsy findings, tissue analysis)

#### **Diagnostic Imaging**
- Radiology findings (X-ray, CT, MRI, ultrasound)
- Standardized reporting with measurable parameters
- Trend tracking (e.g., nodule size over time)

#### **Functional Diagnostics**
- Cardiac studies (echocardiogram with EF, valve function, wall motion)
- Stress testing, ECG/EKG
- Pulmonary function tests
- Other specialized diagnostics

#### **Clinical Assessments**
- Physical examination findings
- Review of systems responses
- Symptom inventories and scales

#### **Lifestyle Pillars** (Subjective)
- Nutrition assessment questionnaires
- Movement/exercise patterns
- Recovery/sleep quality
- Emotional/mental health
- Environmental factors

#### **Historical Data**
- Past medical history
- Current medications (with dosages)
- Surgical history
- Family history
- Allergies and adverse reactions
- Social determinants of health

### Parameter Temporal Classification

#### **Dynamic Parameters** (High-Frequency Monitoring)
- Change frequently over time
- Require regular tracking (daily to weekly)
- Examples: vital signs, glucose, symptoms
- Dashboard role: Real-time health status

#### **Semi-Dynamic Parameters** (Periodic Monitoring)
- Change gradually or conditionally
- Reviewed at standard intervals (monthly to yearly)
- Examples: HbA1c, lipids, imaging
- Dashboard role: Trend tracking

#### **Static Parameters** (Historical Record)
- Permanent or minimally changing
- Examples: past MI, surgical history, congenital conditions
- Dashboard role: Risk stratification context

---

## SCORING METHODOLOGY (HIGH-LEVEL)

*Detailed formulas and algorithms in `CLINICAL_LOGIC_ENGINE.md`*

### Parameter Normalization

All parameters converted to **0-100 normalized scale** using appropriate methods:
- **Normal distribution** (bidirectional, unidirectional)
- **Lognormal/percentile-based** (skewed distributions)
- **Nonlinear risk curves** (parameters like BP, glucose with established risk relationships)
- **Binary** (present/absent with severity-based scoring)
- **Ordinal** (graded scales with pre-calibrated scores)

**Conservative But Motivating Principle:** Z-score of 0 (at personalized target) = 85 points, not 100. This rewards achieving healthy targets while leaving room for sustained excellence.

### Weight Application

Each parameter receives a **24-cell weight matrix** indicating its contribution to each system-domain combination. Weights are:
- Auto-generated using rule-based ontology
- Validated by clinical experts for high-priority parameters
- Versioned and tracked for transparency

### Score Aggregation Hierarchy

```
Individual Parameters (0-100 normalized)
    Ã¢â€ â€œ (weighted by domain)
Domain Scores per System (Structure, Function, Risk: 0-100 each)
    Ã¢â€ â€œ (weighted combination: 0.25, 0.50, 0.25)
System Health Scores (8 systems: 0-100 each)
    Ã¢â€ â€œ (weighted by system criticality)
Objective Health Component (0-100)
    Ã¢â€ â€œ (70% weight)
    +
Lifestyle Pillar Scores (5 pillars: 0-100 each)
    Ã¢â€ â€œ (weighted by pillar criticality)
Subjective Health Component (0-100)
    Ã¢â€ â€œ (30% weight)
OVERALL HEALTH SCORE (0-100)
```

### Completeness Adjustment

When data is sparse, scores are adjusted based on what's measured vs recommended. The baseline for missing data is **50 (neutral/unknown)**, distinct from the **85 (at target)** baseline for measured parameters:
```
Adjusted_score = (Calculated_score Ã— Completeness) + (50 Ã— (1 - Completeness))
```
**Rationale:** Unmeasured â‰  At Target. We use 50 to avoid assuming health (85) or disease (low scores) for missing data.

---

## THE FIVE LIFESTYLE PILLARS

### Purpose
Capture subjective health behaviors that influence objective clinical outcomes.

### The Pillars

1. **Nutrition**
   - Macro/micronutrient intake
   - Eating behaviors and patterns
   - Hydration
   - *Objective correlate:* Metabolic system parameters

2. **Movement**
   - Exercise frequency/intensity
   - NEAT (non-exercise activity thermogenesis)
   - Physical activity patterns
   - *Objective correlate:* Musculoskeletal function, cardiorespiratory fitness

3. **Recovery**
   - Sleep quality and duration
   - Stress management
   - Restoration practices
   - *Objective correlate:* Recovery markers (cortisol, inflammatory markers)

4. **Emotion**
   - Mental health status
   - Stress levels
   - Psychological wellbeing
   - *Objective correlate:* Neurological system, psychosomatic manifestations

5. **Environment**
   - Social connections
   - Community engagement
   - Occupational health
   - Air/water quality exposure
   - *Objective correlate:* Exposure-related findings across systems

### Assessment Method

**Questionnaires per Pillar:**
- Multiple items scored 0-10 by patient
- Composite score calculated (0-100 scale)
- Identifies focus areas for lifestyle intervention
- Tracks subjective progress over time

---

## DASHBOARD VISUALIZATION: PROGRESSIVE DISCLOSURE

*Detailed UI/UX specifications in `DASHBOARD_ARCHITECTURE.md`*

### Level 1: Hero View (Always Visible)

**Purpose:** Immediate health status at a glance

**Components:**
- Overall Health Score (large, color-coded: 0-100)
- Status message in plain language
- Progress bar with color zones (green/yellow/orange/red)
- **Top 3-5 Priority Actions** (auto-generated, action-oriented)
- Single "Expand to see all systems" button
- Last updated timestamp

**Design Philosophy:**
- Maximum clarity, minimum cognitive load
- No scrolling required
- Suitable for quick check-ins

### Level 2: System Overview (Expandable)

**Purpose:** Understand which body systems and lifestyle areas need attention

**Components:**

#### **8-System Coxcomb Chart**
- Radial chart with 8 wedges (one per organ system)
- Each wedge's radius = System Health Score (0-100)
- Color-coded by status zones
- Click any wedge to drill down to Level 3

#### **System Summary Cards**
- One-line status per system
- Color indicator (green/yellow/orange/red)
- Click to expand details

#### **5-Pillar Coxcomb Chart**
- Radial chart with 5 wedges (lifestyle pillars)
- Each wedge's radius = Pillar Score (0-100)
- Visual identification of lifestyle improvement areas

#### **Data Completeness Indicator**
- Percentage of recommended parameters assessed
- Link to missing assessments

**Design Philosophy:**
- Visual comparison across systems/pillars
- Identify focus areas quickly
- Encourage exploration through interaction

### Level 3: Detailed Analysis (Full Drill-Down)

**Purpose:** Deep dive into specific system or clinical parameters for analysis

**Components:**

#### **System Detail View**
1. **Critical Alerts Section** (always displayed first, above composite score)
   - Parameters in red/orange zones
   - Urgency indicators
   - Recommended actions

2. **Transparency Section** (mandatory for every composite score)
   - "What's Working Well" - top 3 positive contributors
   - "What Needs Work" - top 3 negative contributors
   - Explanation of score drivers

3. **Complete Parameter Table** (sortable, filterable)
   - Columns: Parameter name, value, reference range, status, trend, sparkline
   - Default sort: Critical first, then by recent changes
   - Expandable rows showing historical data
   - Color-coded status indicators

4. **Domain Breakdown**
   - Structure Score
   - Function Score
   - Risk Score
   - Visual breakdown of how each contributes

5. **Parameter Detail Cards** (click any parameter)
   - Full historical values with dates
   - Trend graph
   - Plain language explanation: "What is this?" "Why it matters"
   - Reference ranges personalized to patient
   - Related educational resources

**Design Philosophy:**
- Information density optimized for analysis
- Never overwhelming due to progressive disclosure
- Clinicians can rapidly assess during visits
- Curious patients can explore thoroughly

---

## COLOR-CODED STATUS SYSTEM

### Universal Color Zones

**GREEN (75-100)** - Optimal
- Status: Excellent to optimal health
- Action: Maintain current approach
- Display: Positive reinforcement messaging

**YELLOW (60-74)** - Monitor
- Status: Good health with improvement opportunities
- Action: Continue routine monitoring, consider optimization
- Display: Encouraging with specific improvement suggestions

**ORANGE (40-59)** - Act Soon
- Status: Fair health, attention needed
- Action: Clinician consultation within days to weeks
- Display: Clear action items with urgency

**RED (0-39)** - Urgent
- Status: Poor health, urgent intervention required
- Action: Same-day clinician contact or emergency intervention
- Display: Prominent alerts with immediate action steps

### Application Hierarchy

1. **Critical Parameter Thresholds** override composite scores
2. **Individual Parameters** show their own color
3. **Domain Scores** show composite color
4. **System Scores** show weighted composite color
5. **Overall Health Score** shows final composite color

**Rule:** A red parameter always displays prominently, even if system score is green.

---

## TRANSPARENCY & CRITICAL FLAGS

### Mandatory Transparency

**Every composite score must display:**
1. What parameters contribute positively (top 3)
2. What parameters contribute negatively (top 3)
3. Data completeness percentage
4. Number of parameters assessed vs recommended

### Critical Flag System

**Priority Logic:**
1. **Life-threatening parameters** always flagged first (regardless of composite score)
2. **High-impact abnormalities** flagged second
3. **Moderate concerns** flagged third
4. Normal/optimal parameters in "What's Working Well" section

**Critical Parameter Examples:**
- Troponin Ã¢â€°Â¥0.5 ng/mL Ã¢â€ â€™ Critical cardiac alert
- Glucose Ã¢â€°Â¥250 mg/dL Ã¢â€ â€™ Critical metabolic alert
- SpO2 <88% Ã¢â€ â€™ Critical respiratory alert
- eGFR <30 mL/min Ã¢â€ â€™ Critical renal alert

*Full critical threshold table in `CLINICAL_LOGIC_ENGINE.md`*

### Display Rule

**Critical alerts ALWAYS appear:**
- Above composite scores
- In prominent red/orange alert boxes
- With clear next actions
- Cannot be hidden or minimized

---

## BIOLOGICAL AGE CALCULATION

### Purpose
Provide a single, intuitive metric that reflects true health status beyond chronological age.

### Methodology

**Foundation:** Levine's PhenoAge (9 biomarkers + chronological age)

**Enhancement:** System score adjustments + Lifestyle pillar adjustments

**Formula:**
```
Modified Biological Age = Chronological Age 
                        + PhenoAge Deviation 
                        + System Score Adjustments 
                        + Lifestyle Score Adjustments
```

**System Adjustments:**
- Each organ system score contributes based on predefined coefficient
- Healthy systems (score >50): Reduce biological age
- Unhealthy systems (score <50): Increase biological age
- Cardiovascular/metabolic weighted highest

**Lifestyle Adjustments:**
- Each pillar score contributes based on predefined coefficient
- Healthy behaviors: Reduce biological age
- Poor behaviors: Increase biological age

*Detailed formulas and coefficients in `CLINICAL_LOGIC_ENGINE.md`*

### Display

**Primary:**
- Chronological Age: X years
- Modified Biological Age: Y years
- Difference: +/- Z years

**Visual:**
- Side-by-side comparison
- Color-coded (green if younger, red if older)
- Trend graph over time

**Metadata (expandable):**
- Levine PhenoAge calculation
- Breakdown by system contribution
- Breakdown by lifestyle contribution

---

## PARAMETER LIBRARY FRAMEWORK

*Complete starter library in `PARAMETER_LIBRARY.md`*

### Library Philosophy

**Extensible:** New parameters continuously added as medical evidence evolves

**Structured:** Every parameter includes:
- Name (medical term + plain language)
- Type (bidirectional, unidirectional, binary, ordinal)
- Temporal class (dynamic, semi-dynamic, static)
- Primary and related systems
- Reference ranges (default + age/condition adjusted)
- Normalization method
- 24-cell weight matrix
- Critical thresholds
- Clinical notes and evidence sources

### Starter Set for MVP

**50-100 core parameters** covering:
- Most common vital signs (10 parameters)
- Essential labs (30-40 parameters)
- Key imaging findings (10-15 parameters)
- Critical biometrics (5-10 parameters)
- High-impact functional tests (5-10 parameters)

**Coverage Goal:** 80% of typical patient assessments

### Weight Assignment Strategy

**Rule-Based Ontology:**
- Auto-generate baseline weights based on parameter classification
- Parameters categorized by class (vital sign, lab structural, lab functional, risk marker, etc.)
- Each class has template weights for domains
- Primary system gets full weight, related systems get 50%

**Expert Validation:**
- Top 100 high-frequency/high-impact parameters: Full clinical panel review
- Tier 2 parameters: Sampling validation (20% reviewed)
- Tier 3 parameters: Auto-assigned with periodic audits

**Versioning:**
- Every parameter weight set has version number
- Track who validated and when
- Schedule periodic review dates
- Update as new evidence emerges

---

## USER EXPERIENCE PRINCIPLES

### For All Users

1. **Same Interface:** No separate "views" - everyone sees the same dashboard
2. **Choose Your Depth:** Progressive disclosure lets users control detail level
3. **Plain Language:** Medical terms always translated with contextual help
4. **Action-Oriented:** Focus on "what to do" not just "what is"
5. **Visual First:** Charts and colors before tables and numbers
6. **Contextual Education:** Help available on-demand, never forced

### For Patients

1. **Start Simple:** Level 1 hero view sufficient for casual monitoring
2. **Celebrate Wins:** Positive reinforcement for healthy parameters
3. **Clear Next Steps:** Specific, actionable recommendations
4. **Progress Tracking:** Visual trends show improvement over time
5. **Shared Language:** Common ground with healthcare team

### For Clinicians

1. **Rapid Assessment:** Level 1 sufficient for quick status check
2. **Deep Dive Available:** Level 3 provides full analytical capability
3. **Critical Flags First:** Never miss urgent findings
4. **Efficient Workflow:** Default filters show "what matters now"
5. **Export & Share:** Easy report generation for consultations

### For Caregivers & Family

1. **Accessible Language:** No medical degree required
2. **Focus on Priorities:** Level 1 clearly shows what needs attention
3. **Shared Understanding:** Common view facilitates discussions
4. **Trend Awareness:** See if loved one improving or declining

---

## IMPLEMENTATION PRIORITIES

### Phase 1: MVP Foundation (Current Phase)

**Clinical Logic:**
- Ã¢Å“â€¦ Complete normalization framework
- Ã¢Å“â€¦ Parameter weighting system
- Ã¢Å“â€¦ Score calculation algorithms
- Ã¢Å“â€¦ Transparency and critical flag logic
- Ã¢Å“â€¦ Biological age calculation

**Dashboard Architecture:**
- Ã°Å¸â€â€ž Level 1/2/3 detailed specifications (NEXT)
- Ã¢ÂÂ³ Visual design system
- Ã¢ÂÂ³ Interaction patterns
- Ã¢ÂÂ³ Component specifications

**Data Foundation:**
- Ã¢ÂÂ³ Flowsheet structure
- Ã¢ÂÂ³ Database schema
- Ã¢ÂÂ³ 50-100 parameter starter library
- Ã¢ÂÂ³ Data validation rules

**Integration:**
- Ã¢ÂÂ³ Flowsheet Ã¢â€ â€™ Dashboard data flow
- Ã¢ÂÂ³ EMR integration points
- Ã¢ÂÂ³ API specifications

### Phase 2: Enhancement (Future)

- Expanded parameter library (500+ parameters)
- Advanced analytics and trend detection
- Predictive modeling (ML integration)
- Wearable device integration
- Mobile-optimized interface
- Family/caregiver sharing features

### Phase 3: Advanced (Future)

- Leading indicator identification (ML)
- Personalized risk modeling
- Environmental correlation analysis
- Population health insights
- Automated intervention recommendations

---

## TECHNICAL ARCHITECTURE NOTES

*For IT Development Team*

### Technology Stack
**Determined by IT team** - This specification is stack-agnostic

**Requirements:**
- Support for complex calculations (see `CLINICAL_LOGIC_ENGINE.md`)
- Real-time or near-real-time data visualization
- Responsive design (desktop primary, tablet/mobile secondary)
- HIPAA compliance for data storage and transmission
- Role-based access control (if needed for future phases)
- Export functionality (PDF, CSV)

### Performance Requirements

**Load Times:**
- Level 1: <2 seconds
- Level 2: <3 seconds
- Level 3: <5 seconds (initial load), then cached

**Data Refresh:**
- Real-time for critical parameters (if monitoring device connected)
- On-demand refresh button always available
- Automatic refresh on flowsheet updates

### Integration Points

**Primary Integration:** EMR Ã¢â€ â€ Flowsheet Ã¢â€ â€ Dashboard

**Data Entry Methods:**
1. Manual entry by clinician/staff
2. Manual modification of auto-imported data
3. AI/automation import from EMR
4. (Future) Wearable device integration
5. (Future) Patient self-entry for lifestyle questionnaires

### Security & Privacy

- HIPAA-compliant data handling
- Audit logging for all data access
- Encryption at rest and in transit
- User authentication and authorization
- (Future) Patient consent management for data sharing

---

## QUALITY ASSURANCE

### Clinical Validation Required

Before deployment, all following must be validated by clinical panel:

1. **Parameter Weights** - Top 100 parameters fully reviewed
2. **Critical Thresholds** - All life-threatening parameters confirmed
3. **Biological Age Coefficients** - System and pillar adjustments validated
4. **Reference Ranges** - Age and condition adjustments verified
5. **Plain Language Translations** - Patient-friendly terminology reviewed

### User Testing Required

1. **Pilot Testing:** 50-100 real patient datasets
2. **Clinician Usability:** 5-10 clinicians using in actual patient visits
3. **Patient Comprehension:** 20-30 patients testing understanding
4. **Caregiver Feedback:** 10-20 family members reviewing interface

### Technical Validation

1. **Calculation Accuracy:** Unit tests for all formulas
2. **Performance Benchmarks:** Load time targets met
3. **Cross-Browser Testing:** Desktop and mobile browsers
4. **Accessibility Compliance:** WCAG 2.1 AA standards
5. **Security Audit:** HIPAA compliance verification

---

## SUCCESS METRICS

### Clinical Outcomes
- Improved patient engagement with health data
- Increased adherence to treatment plans
- Earlier detection of health deterioration
- Better patient-clinician communication

### Operational Metrics
- Reduced time spent explaining results to patients
- Increased efficiency in identifying priority issues
- Improved care coordination among team members
- Higher patient satisfaction scores

### Technical Metrics
- Dashboard load times <3 seconds average
- >95% uptime
- <1% calculation errors
- Positive user experience scores

---

## FUTURE ENHANCEMENTS

### Machine Learning Integration

**Leading Indicator Discovery:**
- Identify which parameters predict changes in others
- Find non-obvious relationships in patient data
- Early warning system before clinical thresholds

**Personalized Risk Modeling:**
- Predict individual patient trajectories
- Identify early warning signs
- Adapt recommendations based on patient-specific patterns

**Environmental Correlation:**
- Link lifestyle/environmental data to objective measures
- Quantify impact of behaviors on biomarkers

### Advanced Features

- **Intervention Tracking:** Monitor specific treatment/lifestyle changes and their effects
- **Goal Setting:** Patient-defined health goals with progress tracking
- **Comparative Analytics:** "How am I doing compared to similar patients?"
- **Automated Recommendations:** AI-suggested focus areas and interventions
- **Family Health Patterns:** Identify familial risk factors and trends

---

## APPENDIX: GLOSSARY

### Key Terms

**Flowsheet:** Central data collection interface where all health information is entered, validated, and stored before dashboard visualization

**24-Cell Matrix:** Framework evaluating 8 organ systems across 3 domains (Structure, Function, Risk) = 24 unique evaluation points

**Progressive Disclosure:** UI design pattern revealing information in layers (Level 1 Ã¢â€ â€™ 2 Ã¢â€ â€™ 3) based on user engagement

**Normalized Score:** All parameters converted to 0-100 scale for standardized comparison

**Z-Score:** Statistical measure of how many standard deviations a value is from the ideal target

**Conservative But Motivating Baseline:** Design principle where "at personalized target" (z=0) equals 85 points, not 100. This rewards achieving healthy goals while maintaining room for sustained excellence.

**Completeness Factor:** Adjustment when data is sparse, blending calculated scores with neutral baseline (50 for unknown/unmeasured, 85 for normal expectations)

**Critical Flag:** Alert for parameters in dangerous zones, displayed regardless of composite scores

**Biological Age:** Health-based age calculation reflecting true physiological status beyond chronological years

**Coxcomb Chart:** Radial visualization where each wedge's size represents a system/pillar score

---

## DOCUMENT CONTROL

### Version History

**v2.0.0** - November 11, 2025
- Restructured as master specification with separate technical documents
- Added progressive disclosure UI strategy
- Refined flowsheet integration architecture
- Clarified single-interface approach (no separate views)
- Enhanced transparency and critical flag requirements

**v1.0.0** - [Original Date]
- Initial comprehensive specification
- All details in single document

### Related Documents

- `CLINICAL_LOGIC_ENGINE.md` - Complete calculation framework Ã¢Å“â€¦
- `DASHBOARD_ARCHITECTURE.md` - UI/UX detailed specifications (IN PROGRESS)
- `FLOWSHEET_SPECIFICATION.md` - Data entry interface (PLANNED)
- `DATA_MODEL.md` - Database and API specs (PLANNED)
- `PARAMETER_LIBRARY.md` - Starter parameter set (PLANNED)
- `IMPLEMENTATION_DECISIONS.md` - Design decision log (ONGOING)

### Approval & Sign-Off

**Clinical Lead:** _____________________
**Product Owner:** _____________________
**Technical Lead:** _____________________
**Date:** _____________________

---

## CONTACT & SUPPORT

For questions about this specification or implementation guidance, contact the Performance Medicine Product Development Team.

---

**END OF MASTER PROJECT SPECIFICATION**

*This document is the authoritative source for project vision and architecture. Refer to technical implementation documents for detailed specifications.*