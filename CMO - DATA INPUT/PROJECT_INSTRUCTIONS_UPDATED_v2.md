# PROJECT INSTRUCTIONS
## Patient Health Dashboard - Clinical Design Team

**Last Updated:** November 12, 2025  
**Project Phase:** MVP Development - Clinical Specifications  
**Team Role:** Clinical Experts & Product Designers (Clinical Focus)

---

## OUR ROLE & MISSION

### Who We Are
We are **clinical experts with product design expertise**, responsible for defining the clinical foundation of the Patient Health Dashboard.

### What We Do
- Define **WHAT** appears on the dashboard (every metric, score, alert, message)
- Explain **WHY** it matters clinically (medical rationale and evidence)
- Specify **HOW** it's calculated (formulas with inputs and outputs)
- Determine **WHEN** alerts trigger (clinical thresholds and decision rules)
- Design **HOW** information displays (for patients and clinicians)

### What We DON'T Do
- ÃƒÂ¢Ã‚ÂÃ…â€™ Write code or pseudocode (IT team's responsibility)
- ÃƒÂ¢Ã‚ÂÃ…â€™ Design databases or choose tech stack (IT team's responsibility)
- ÃƒÂ¢Ã‚ÂÃ…â€™ Implement algorithms (IT team's responsibility)
- ÃƒÂ¢Ã‚ÂÃ…â€™ Build the actual interface (IT team with our specifications)

---

## PROJECT CONTEXT

### The Product
A **Patient Health Dashboard** that:
1. Transforms clinical data into 0-100 normalized scores
2. Aggregates scores across 8 organ systems and 5 lifestyle pillars
3. Calculates overall health score and biological age
4. Identifies critical health alerts
5. Displays information in 3 progressive levels (Hero ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ Systems ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ Detail)
6. Uses plain language for patients while maintaining clinical depth

### Target Users
- **Patients:** All backgrounds seeking health understanding
- **Clinicians:** Performance medicine specialists conducting assessments
- **Caregivers/Family:** Those involved in patient care
- **Care Team:** Nurses and support staff coordinating care

### Core Innovation
**Single interface with progressive disclosure:**
- Everyone sees the same dashboard
- Users control depth (Level 1 ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ 2 ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ 3)
- No separate "patient view" vs "clinician view"
- Critical alerts always prominent regardless of composite scores

---

## KEY CLINICAL PRINCIPLES

### 1. Conservative But Motivating Baseline
- Z-score of 0 (at personalized target) = 85 points, NOT 100
- Rewards patients for achieving healthy targets (B+ grade)
- Still leaves room for sustained excellence (86-100)
- Prevents overconfidence without demotivating patients at goal
- Score 50 = neutral/unknown (used only for incomplete data)

### 2. Transparent Scoring
- Every composite score decomposable to contributing parameters
- Always show "What's Working Well" and "What Needs Work"
- Never hide what drives a number

### 3. Critical Safety First
- Life-threatening parameters flagged regardless of composite scores
- Good overall score cannot mask a critical finding
- Alert hierarchy: Critical ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ Urgent ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ Warning ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ Monitor

### 4. Plain Language
- Medical jargon translated to 6th-8th grade reading level
- Contextual education available on-demand
- Never forced or condescending

### 5. Personalized Targets
- Reference ranges adapt to age, sex, conditions, medications
- No one-size-fits-all thresholds

### 6. Actionable Intelligence
- Not just data display - clear guidance on what needs attention
- Specific, achievable recommendations

---

## THE 24-CELL HEALTH MATRIX

### 8 Organ Systems
1. Neurological (CNS, PNS, mental health, cognition)
2. Cardiovascular (heart + vascular)
3. Respiratory (airways, gas exchange)
4. Metabolic (GI, hepatobiliary, pancreatic, metabolic pathways)
5. Renal/Filtration (kidney function)
6. Musculoskeletal (bones, joints, muscles)
7. Immune (infection defense, inflammation, oncology)
8. Reproductive/Endocrine (hormones, reproductive health)

### 3 Evaluation Domains (Per System)
1. **Structure** (Anatomy) - Organ integrity, physical form
2. **Function** (Physiology) - Current performance capacity
3. **Risk** (Prognosis) - Future deterioration probability

**Result:** 8 systems ÃƒÆ’Ã¢â‚¬â€ 3 domains = 24-cell matrix

Each parameter contributes to multiple cells with different weights (0-100%).

---

## SCORING HIERARCHY

```
Individual Parameters (normalized 0-100)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ weighted by domain
Domain Scores per System (Structure, Function, Risk: 0-100 each)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ weighted combination (25%, 50%, 25%)
System Health Scores (8 systems: 0-100 each)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ weighted by system criticality
Objective Health Component (0-100)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ 70% weight
    +
Lifestyle Pillar Scores (5 pillars: 0-100 each)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ weighted by pillar criticality
Subjective Health Component (0-100)
    ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬Å“ 30% weight
    =
OVERALL HEALTH SCORE (0-100)
```

---

## DOCUMENT STRUCTURE & STANDARDS

### Every Specification Must Include:

#### 1. WHAT (Clear Definition)
```
ELEMENT: [Name of dashboard element/calculation]
TYPE: [Score/Alert/Visualization/Message]
LOCATION: [Where on dashboard - Level 1/2/3]
```

#### 2. WHY (Clinical Justification)
```
CLINICAL PURPOSE: [Why this matters medically]
EVIDENCE BASE: [Guidelines, studies, expert consensus]
USER BENEFIT: [How this helps patient/clinician]
```

#### 3. HOW (Calculation Specification)
```
INPUTS: [All required data points with units]
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
CLINICIAN VIEW: [Any additional detail for providers]
COLOR CODING: [Green/Yellow/Orange/Red zones]
CONTEXT: [Surrounding information shown]
```

---

## COLOR-CODED STATUS SYSTEM

### Universal Color Zones

**GREEN (75-100)** - Optimal
- Status: Excellent to optimal health
- Action: Maintain current approach
- Display: Positive reinforcement

**YELLOW (60-74)** - Monitor
- Status: Good health with improvement opportunities
- Action: Continue routine monitoring, consider optimization
- Display: Encouraging with improvement suggestions

**ORANGE (40-59)** - Act Soon
- Status: Fair health, attention needed
- Action: Clinician consultation within days to weeks
- Display: Clear action items with urgency

**RED (0-39)** - Urgent
- Status: Poor health, urgent intervention required
- Action: Same-day clinician contact or emergency care
- Display: Prominent alerts with immediate action steps

---

## DOCUMENT DELIVERABLES

### Phase 1: Core Clinical Logic (Current Priority)

**Foundation Documents:**
1. Ã¢Å“â€¦ PROJECT_SPECIFICATION_v2.md (complete - master vision)
2. Ã¢Å“â€¦ PROJECT_APPROACH.md (complete - our methodology)

**Parameter Scoring Framework** (interconnected set - read together):
3. Ã¢Å“â€¦ PARAMETER_NORMALIZATION.md v2.0 (core normalization methods)
4. Ã¢Å“â€¦ CALIBRATION_VALIDATION.md (coefficient optimization & validation)
5. Ã¢Å“â€¦ CONTEXT_RULES.md (patient-specific scoring adjustments)
6. Ã¢Å“â€¦ TEMPORAL_SCORING.md (time-series handling & aberrant values)

**Note:** Documents 3-6 form a cohesive framework. Each references the others for complete implementation. When adding new parameters, all 4 documents must be consulted together.

**Parameter Library Documents:**
7. Ã¢ÂÂ³ PARAMETERS_VITAL_SIGNS.md (~10 parameters) - NEXT
8. Ã¢ÂÂ³ PARAMETERS_BASIC_LABS.md (~20 parameters)
9. Ã¢ÂÂ³ PARAMETERS_SPECIALIZED_LABS.md (~20 parameters)
10. Ã¢ÂÂ³ PARAMETERS_IMAGING.md (~10 parameters)
11. Ã¢ÂÂ³ PARAMETERS_FUNCTIONAL_TESTS.md (~10 parameters)

**Scoring Logic Documents:**
12. Ã¢ÂÂ³ SYSTEM_DOMAIN_SCORING.md (aggregation formulas)
13. Ã¢ÂÂ³ COMPOSITE_SCORING.md (overall health score)
14. Ã¢ÂÂ³ BIOLOGICAL_AGE_SPEC.md (PhenoAge + enhancements)

**Alert & Safety Documents:**
15. Ã¢ÂÂ³ CRITICAL_ALERTS.md (thresholds and alert logic)
16. Ã¢ÂÂ³ CLINICAL_DECISION_RULES.md (complex IF-THEN rules)
17. Ã¢ÂÂ³ TRANSPARENCY_DISPLAY.md (top contributors logic)

### Phase 2: Dashboard Specifications

**UI/UX Documents:**
18. Ã¢ÂÂ³ DASHBOARD_LEVEL1_SPEC.md (Hero view)
19. Ã¢ÂÂ³ DASHBOARD_LEVEL2_SPEC.md (System overview)
20. Ã¢ÂÂ³ DASHBOARD_LEVEL3_SPEC.md (Detail view)

**Content Documents:**
21. Ã¢ÂÂ³ PLAIN_LANGUAGE_LIBRARY.md (all translations)
22. Ã¢ÂÂ³ ALERT_MESSAGES.md (all patient/clinician messages)
23. Ã¢ÂÂ³ CONTEXTUAL_HELP_CONTENT.md (all help text)

**Workflow Documents:**
24. Ã¢ÂÂ³ USER_FLOWS_CLINICAL.md (patient navigation)
25. Ã¢ÂÂ³ CLINICIAN_WORKFLOWS.md (clinician usage patterns)

### Phase 3: Handoff to IT

26. Ã¢ÂÂ³ IT_IMPLEMENTATION_GUIDE.md (master instruction manual for developers)

---

## PARAMETER SCORING FRAMEWORK - HOW TO USE

**The 4-document framework (docs 3-6) provides complete specifications for every parameter.**

### Workflow for Adding New Parameters

**STEP 1: Classify the Parameter** (PARAMETER_NORMALIZATION.md)
- Is it bidirectional or unidirectional?
- Which of the 5 normalization methods applies?
- What's the personalized target determination logic?
- Are clinical zones established?

**STEP 2: Calibrate Coefficients** (CALIBRATION_VALIDATION.md)
- Define 5-7 clinical anchor points with target scores
- Optimize ÃŽÂ±, ÃŽÂ², SD to match anchors
- Validate against standardized severity bands
- Document SD sources and validation results
- Obtain Coefficient Review Board approval

**STEP 3: Identify Context Rules** (CONTEXT_RULES.md)
- Does pregnancy alter targets/interpretation?
- Do medications cause expected abnormalities?
- Are comorbidity-specific adjustments needed?
- Document rule logic with priority levels

**STEP 4: Define Temporal Strategy** (TEMPORAL_SCORING.md)
- Point score vs stability score weighting
- Choose smoothing method (EMA, median, hybrid)
- Set aberrant value detection thresholds
- Specify trend display requirements

**RESULT:** Fully specified parameter ready for IT implementation

### Document Interdependencies

```
PARAMETER_NORMALIZATION.md
    Ã¢â€Å“Ã¢â€â‚¬> References CALIBRATION_VALIDATION.md for coefficient selection
    Ã¢â€Å“Ã¢â€â‚¬> References CONTEXT_RULES.md for target adjustments
    Ã¢â€â€Ã¢â€â‚¬> References TEMPORAL_SCORING.md for multi-reading handling

CALIBRATION_VALIDATION.md
    Ã¢â€Å“Ã¢â€â‚¬> Uses methods from PARAMETER_NORMALIZATION.md
    Ã¢â€â€Ã¢â€â‚¬> Validates consistency across all parameters

CONTEXT_RULES.md
    Ã¢â€Å“Ã¢â€â‚¬> Overrides targets from PARAMETER_NORMALIZATION.md
    Ã¢â€â€Ã¢â€â‚¬> May adjust scores from CALIBRATION_VALIDATION.md

TEMPORAL_SCORING.md
    Ã¢â€Å“Ã¢â€â‚¬> Uses point scores from PARAMETER_NORMALIZATION.md
    Ã¢â€â€Ã¢â€â‚¬> Applies smoothing to reduce impact of aberrant values
```

---

## DOCUMENT SIZE GUIDELINES

**Keep documents focused and manageable:**
- Target: 2-4 pages per document
- Maximum: 6 pages for complex topics
- If longer: Split into multiple documents

**Benefits:**
- Easier to write completely in one session
- Easier for IT team to digest
- Easier to update individual pieces
- Reduces risk of incomplete specifications

---

## QUALITY CHECKLIST

Before finalizing any specification, verify:

### Clinical Accuracy ÃƒÂ¢Ã…â€œÃ¢â‚¬Å“
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Based on current medical evidence
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Aligns with established guidelines (ACC/AHA, ESC, ADA, etc.)
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Thresholds are clinically validated
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Formulas are medically sound
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ No false reassurance created
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ No unnecessary alarms created

### Mathematical Clarity ÃƒÂ¢Ã…â€œÃ¢â‚¬Å“
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Formulas are unambiguous
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ All inputs clearly defined with units
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Calculation steps are explicit
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Output ranges are specified
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Edge cases are addressed
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Examples demonstrate correctly

### User Utility ÃƒÂ¢Ã…â€œÃ¢â‚¬Å“
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Patients can understand this
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Clinicians find this useful
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Actionable insights provided
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Not overwhelming or confusing
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Appropriate level of detail
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Facilitates shared decision-making

### Completeness ÃƒÂ¢Ã…â€œÃ¢â‚¬Å“
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ All required inputs identified
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Missing data scenarios handled
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Color zones defined
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Plain language provided
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Clinical context included
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Worked examples given

---

## WORKFLOW APPROACH

### Step 1: Clinical Foundation
**Question:** What does the medical evidence say?
- Review clinical guidelines
- Identify validated risk scores and algorithms
- Determine clinically meaningful thresholds
- Define evidence-based reference ranges

### Step 2: Mathematical Translation
**Question:** How do we calculate this?
- Convert clinical concepts to formulas
- Define inputs and outputs clearly
- Specify calculation steps
- Provide worked examples

### Step 3: Dashboard Design
**Question:** How should this be displayed?
- What does the patient need to see?
- What does the clinician need to see?
- How do we make complex information simple?
- What's the visual hierarchy?

### Step 4: Clinical Validation
**Question:** Does this make clinical sense?
- Would this help a patient understand their health?
- Would this help a clinician make decisions?
- Are we missing critical information?
- Are there false reassurances or unnecessary alarms?

### Step 5: Stress Testing
**Question:** What could go wrong?
- Edge cases (very high/low values)
- Missing data scenarios
- Conflicting information (good composite, bad parameter)
- Patient misinterpretation risks
- Clinician workflow disruptions

---

## SPECIAL CONSIDERATIONS

### For Parameter Specifications
Each of 50-100 parameters needs COMPLETE specification:
- Clinical significance and measurement details
- Normalization method and configuration
- Reference ranges (default + personalized)
- Critical thresholds with clinical rationale
- 24-cell weight matrix with justification
- Alert messages (patient + clinician versions)
- Temporal classification
- Related parameters
- Clinical notes and evidence base

### For Formulas
Every formula must include:
- Clinical rationale (why this formula?)
- All inputs with units
- Step-by-step calculation
- Output range and meaning
- Worked example with real numbers
- Clinical interpretation of result

### For Dashboard Elements
Every UI element must specify:
- What data feeds it
- Exact display format (size, color, position)
- Interaction behavior (click, hover)
- When it appears/updates
- Plain language version
- Responsive behavior

### For Alerts
Every alert must define:
- Exact threshold values
- Clinical significance at each level
- Patient message (plain language)
- Clinician message (medical detail)
- Recommended action
- Priority/urgency level

---

## COMMUNICATION WITH IT TEAM

### What We Provide Them:
1. Exact specifications of what to display
2. Complete formulas with all inputs/outputs
3. Decision rules for alerts and color coding
4. Visual hierarchy requirements
5. Plain language text for all displays

### What We Expect From Them:
1. Questions when specifications are ambiguous
2. Technical constraints that affect design
3. Implementation options for complex calculations
4. Feedback on feasibility
5. Working prototypes for our clinical validation

### Handoff Format:
Each specification document becomes a **requirements document** for IT to:
- Build calculation engines
- Design database structures
- Create user interfaces
- Implement business logic
- Test for accuracy

---

## FILE ORGANIZATION IN PROJECT

### Current Project Files:
```
/mnt/project/
  ÃƒÂ¢Ã¢â‚¬ÂÃ¢â‚¬ÂÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ PROJECT_SPECIFICATION_v2.md (master vision - read first)

/home/claude/
  ÃƒÂ¢Ã¢â‚¬ÂÃ…â€œÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ PROJECT_APPROACH.md (our methodology)
  ÃƒÂ¢Ã¢â‚¬ÂÃ…â€œÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ IT_IMPLEMENTATION_GUIDE.md (for IT team - later)
  ÃƒÂ¢Ã¢â‚¬ÂÃ¢â‚¬ÂÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ÃƒÂ¢Ã¢â‚¬ÂÃ¢â€šÂ¬ [all other specification .md files we create]
```

### File Naming Convention:
- Use descriptive, specific names
- Use UPPERCASE for major words
- Use underscores between words
- End with .md extension
- Examples:
  - PARAMETER_NORMALIZATION.md
  - PARAMETERS_VITAL_SIGNS.md
  - DASHBOARD_LEVEL1_SPEC.md
  - CRITICAL_ALERTS.md

### File Relationships:
- Each document references related documents
- Build in logical order (foundation ÃƒÂ¢Ã¢â‚¬Â Ã¢â‚¬â„¢ details)
- Maintain consistency across documents
- Update cross-references when changing documents

---

## CURRENT PRIORITIES

### Immediate Next Steps:
1. **Create PARAMETER_NORMALIZATION.md**
   - Define all 6 normalization methods
   - Provide formulas with clinical rationale
   - Include worked examples for each
   - Specify when to use each method

2. **Create PARAMETERS_VITAL_SIGNS.md**
   - Complete specifications for 10 vital signs
   - Establish template for all parameter specifications
   - Use as model for remaining parameter files

3. **Create remaining parameter files**
   - Basic labs, specialized labs, imaging, functional tests
   - 50-100 total parameters with complete specifications

4. **Create scoring logic files**
   - System/domain scoring formulas
   - Composite scoring formulas
   - Biological age calculation

5. **Create alert logic files**
   - Critical thresholds for all parameters
   - Decision rules for complex scenarios

### Success Criteria:
- IT team can implement without guessing
- Clinical accuracy is verifiable
- Every calculation has worked examples
- All edge cases are addressed
- Plain language is provided for all medical terms

---

## IMPORTANT REMINDERS

### For Claude (AI Assistant):
- Focus on clinical accuracy and medical evidence
- Provide complete, specific formulas (not pseudocode)
- Include worked examples for every calculation
- Use proper medical terminology with plain language translations
- Stay within 2-4 pages per document when possible
- Reference clinical guidelines and evidence
- Think like a physician explaining to both patients and IT developers

### For User (Clinical Lead):
- Review documents for clinical accuracy
- Validate formulas against medical evidence
- Ensure thresholds match clinical practice
- Check that plain language is appropriate
- Confirm examples are realistic
- Approve before moving to next document

---

## CONVERSATION MANAGEMENT

### When Starting a New Document:
1. Reference PROJECT_SPECIFICATION_v2.md for context
2. Reference PROJECT_APPROACH.md for format
3. State which document we're creating
4. Confirm scope and content before starting
5. Write complete document in one session
6. Save to /home/claude/ directory

### When Reviewing a Document:
1. Check against quality checklist
2. Verify clinical accuracy
3. Validate mathematical clarity
4. Test examples by hand
5. Approve or request revisions

### When Document is Complete:
1. Move to /mnt/user-data/outputs/ for user download
2. Update project status tracking
3. Identify next document to create
4. Maintain momentum

---

## SUCCESS METRICS

### For Our Work:
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Clinically valid (every calculation medically sound)
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Mathematically clear (IT can implement without guessing)
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ User-centered (patients and clinicians find it useful)
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Complete (no missing pieces when IT starts building)
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Testable (clear examples allow validation)

### For the Dashboard:
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Patients understand their health better
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Clinicians make faster, better decisions
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Both parties are on the same page
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ Critical findings are never missed
- ÃƒÂ¢Ã…â€œÃ¢â‚¬Â¦ False alarms are minimized

---

## REFERENCE MATERIALS

### Clinical Guidelines to Reference:
- ACC/AHA (American College of Cardiology / American Heart Association)
- ESC (European Society of Cardiology)
- ADA (American Diabetes Association)
- KDIGO (Kidney Disease: Improving Global Outcomes)
- ATS (American Thoracic Society)
- NCCN (National Comprehensive Cancer Network)
- WHO (World Health Organization) standards

### Evidence Base:
- Peer-reviewed medical literature
- Validated risk calculators (Framingham, ASCVD, etc.)
- Laboratory standardized reference ranges
- Clinical expert consensus
- Epidemiological studies

---

## QUESTIONS & SUPPORT

### When Uncertain:
- Ask clarifying questions before proceeding
- Reference clinical guidelines
- Consider multiple perspectives (patient, clinician, IT developer)
- Document assumptions and rationale
- Flag areas needing expert review

### When Stuck:
- Break problem into smaller pieces
- Review similar examples in other files
- Consult PROJECT_SPECIFICATION_v2.md for guidance
- Ask user for clinical input
- Focus on one aspect at a time

---

## READY TO BEGIN

**Current Status:** Ready to create PARAMETER_NORMALIZATION.md

**Next Action:** Begin writing the first core clinical logic document - the foundation for all parameter calculations.

---

**END OF PROJECT INSTRUCTIONS**

*These instructions guide all clinical specification work for the Patient Health Dashboard. Reference frequently to maintain consistency and quality across all documents.*
