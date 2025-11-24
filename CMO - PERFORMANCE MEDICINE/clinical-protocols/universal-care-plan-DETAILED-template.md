# Universal Performance Medicine Care Plan Template (DETAILED)

> **Version**: DETAILED - Comprehensive reference document (15-25 pages when filled)
> **Use for**: Complex/high-risk patients, multiple conditions, new diagnoses, patients who want depth
> **Companion**: LITE version available for stable/simple cases

---

## AI GENERATION INSTRUCTIONS

This template contains three types of prompts:
- `[INPUT: field]` = Extract data directly from patient records
- `[AI ANALYZE: logic]` = Apply decision rules, calculate, categorize
- `[AI GENERATE: parameters]` = Synthesize narrative with specified constraints

**Critical**: Follow specificity guidelines in ai-care-plan-generation-instructions.md to prevent hallucinations.

---

## SECTION 0: WELCOME & HOW THIS PLAN WORKS

### What This Is

This is your **complete health roadmap** for the next 12 months. It connects:
- Your personal health goals
- Your age and life stage priorities  
- Your current health status across 8 body systems
- Medical treatments AND lifestyle actions in one unified plan

### What Makes It Different

✓ **Personalized to YOU**: Based on your age ([INPUT: patient_age]), sex ([INPUT: patient_sex]), life stage, and personal goal  
✓ **Full-body assessment**: Reviews all 8 health systems (brain, heart, lungs, metabolism, kidneys, muscles/bones, immune, hormones)  
✓ **Medical + Lifestyle integrated**: Not just prescriptions - includes movement, nutrition, sleep, stress management, environment  
✓ **Shared document**: One plan for you, your family, and your entire care team

### How to Use This Plan

**Start here** (spend 10-15 minutes):
1. **Section 1** - Your personal information and health goal
2. **Section 2** - Your life stage and why it matters
3. **Section 3-4** - Your health systems summary and top priorities

**Daily reference**:
- **Section 5** - Your action plan (what to do each day/week)
- **Section 6** - Safety net (when to call for help)

**Periodic review** (with your care team):
- **Section 7** - Monitoring and quarterly roadmap
- **Section 8** - Preventive care checklist

### When This Plan Changes

Your plan will be updated when:
- Your health goals change
- You enter a new life stage (e.g., pregnancy, retirement, advanced age)
- You start or complete major treatments
- Your health improves or worsens significantly
- **At minimum**: Full review every 12 months

---

## SECTION 1: PATIENT INFORMATION & WHAT MATTERS MOST

```markdown
**Patient Name**: [INPUT: patient_legal_name]  
**Preferred Name**: [INPUT: patient_preferred_name]  
**Pronouns**: [INPUT: patient_pronouns]  
**Date of Birth**: [INPUT: patient_dob] | **Age**: [INPUT: patient_age] years  
**Sex (biological)**: [INPUT: patient_biological_sex]  
**Gender identity** (if shared): [INPUT: patient_gender_identity]  

**Date of Care Plan**: [INPUT: care_plan_date]  
**Primary Provider**: [INPUT: primary_provider_name]  
**Care Team**: [INPUT: care_team_members]  
[AI GENERATE: List key clinicians, caregivers, family members involved in care - format as bullet list with roles]

---

### What I Want You to Know About Me

**1. What matters most to me in life right now**  
[INPUT: patient_life_priorities_free_text]

**2. My main health goal for the next 12 months**  
[INPUT: patient_primary_health_goal]

**3. Why this goal matters to me**  
[INPUT: patient_goal_rationale]

**4. Things that worry me most about my health**  
[INPUT: patient_health_concerns]

**5. People who are important in my care**  
[INPUT: patient_support_network]  
[AI GENERATE: If patient agrees, list names/roles/contact info for key support people - respect privacy preferences]

---

### How We'll Measure Success

[AI GENERATE: Create 3 specific, measurable success metrics from patient's goal. Parameters:
- Must be concrete and observable (not vague like "feel better")
- Mix of: (1) functional capacity, (2) health metrics, (3) patient-reported outcome
- Timeframe: 3-12 months
- Examples if goal is "stay independent at home": 
  * "Walk to mailbox and back without breathlessness"
  * "Weight stable (no further loss)"
  * "Zero falls in next 6 months"
]

✓ **Success metric 1**: [AI GENERATE]  
✓ **Success metric 2**: [AI GENERATE]  
✓ **Success metric 3**: [AI GENERATE]
```

---

## SECTION 2: LIFE STAGE CONTEXT - WHERE YOU ARE IN YOUR LIFE

### Your Current Life Stage

**Life Stage**: [AI ANALYZE: patient_age → life_stage_name using these rules:
- IF age 0-1 → "Infancy (Stage 1)"
- IF age 2-5 → "Early Childhood (Stage 2)"
- IF age 6-12 → "Middle Childhood (Stage 3)"
- IF age 13-25 → "Adolescence & Young Adulthood (Stage 4)"
- IF age 26-39 → "Early Adulthood (Stage 5)"
- IF age 40-54 → "Middle Adulthood (Stage 6)"
- IF age 55-64 → "Late Middle Age (Stage 7)"
- IF age 65-79 → "Older Adulthood (Stage 8)"
- IF age ≥80 → "Advanced Age (Stage 9)"]

**Typical Age Range**: [AI PULL: age range for matched life stage from life-stage-health-goals.md]

**Life Context** (typical for this stage):  
[AI PULL: "Life Context" description for matched stage from life-stage-health-goals.md - copy verbatim]

---

### Stage-Specific Clinical Priorities for You

[AI PULL: Pull "Primary Clinical Goals" (top 3) for matched life stage from life-stage-health-goals.md]

Based on evidence and your age of [INPUT: patient_age], these are the health priorities that matter most at your life stage:

#### 1. [AI PULL: Priority 1 title from life-stage-health-goals.md]

**Why it matters at your age**:  
[AI PULL: "Why it matters" rationale from life-stage-health-goals.md for this priority]

**How we'll track it in your plan**:  
[AI GENERATE: 1-2 sentences explaining which sections of THIS care plan address this priority - reference specific systems, interventions, or metrics]

---

#### 2. [AI PULL: Priority 2 title from life-stage-health-goals.md]

**Why it matters at your age**:  
[AI PULL: rationale from life-stage-health-goals.md]

**How we'll track it**:  
[AI GENERATE: connection to this care plan]

---

#### 3. [AI PULL: Priority 3 title from life-stage-health-goals.md]

**Why it matters at your age**:  
[AI PULL: rationale from life-stage-health-goals.md]

**How we'll track it**:  
[AI GENERATE: connection to this care plan]

---

### How Your Life Stage Priorities Support Your Main Goal

**Your goal**: "[INPUT: patient_primary_health_goal]"

**Connection**:  
[AI GENERATE: Write 2-4 sentences explaining how the 3 clinical priorities above support the patient's personal goal. Make it PERSONAL and CONCRETE. 

Parameters:
- Tone: conversational, hopeful, empowering
- Length: 50-100 words
- Required elements: (1) acknowledge patient's goal, (2) link each priority to goal, (3) explain mechanism
- Example if 84yo goal="stay at home": "Preventing falls (Priority 1) directly protects your ability to stay home independently - a hip fracture is the #1 reason people your age move to nursing homes. Maintaining muscle and nutrition (Priority 2) gives you the strength to get out of chairs, walk to the bathroom, and prepare meals. Managing your chronic conditions (Priority 3) prevents hospitalizations that could trigger a cascade toward loss of independence."
]

---

## SECTION 3: HEALTH MATRIX SUMMARY - YOUR 8 SYSTEMS AT A GLANCE

### How We Assess Your Health

We evaluated 8 core body systems across 3 dimensions:
- **Structure**: The anatomy and "hardware" (like looking at the structure of your heart or bones)
- **Function**: How well things work day-to-day (like your energy level or walking ability)  
- **Risk**: Your future risk of disease or complications (like cholesterol levels or blood sugar trends)

### Your Health Matrix (Traffic Light Summary)

[AI ANALYZE: For each of 8 systems × 3 domains = 24 cells, assign status using assessment data:

Status rules:
- 🟢 Green: Optimal/normal for age
- 🟡 Yellow: Mild abnormalities or early warning signs  
- 🟠 Orange: Moderate abnormalities requiring intervention
- 🔴 Red: Severe abnormalities or acute concern

Then populate this table:]

| Health System | Structure | Function | Risk | Priority Level |
|---------------|-----------|----------|------|----------------|
| **Neurological** (brain, nerves, mood) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Cardiovascular** (heart, blood vessels) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Respiratory** (lungs, breathing) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Metabolic/Digestive** (energy, gut, liver) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Filtration/Urinary** (kidneys, bladder) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Musculoskeletal** (muscles, bones, joints) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Immune** (infection, inflammation, cancer) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |
| **Reproductive/Hormonal** (hormones, reproduction) | [STATUS] | [STATUS] | [STATUS] | [PRIORITY] |

**Status Key**: 🟢 Optimal | 🟡 Watch | 🟠 Action Needed | 🔴 High Priority

**Priority Level** options: Maintain | Watch | Action Needed | High Priority

[AI ANALYZE: Assign priority level per system using:
- IF ≥2 Red OR (≥1 Red AND ≥2 Orange) → "High Priority"
- IF ≥1 Red OR ≥2 Orange → "Action Needed"  
- IF ≥1 Orange OR ≥2 Yellow → "Watch"
- ELSE → "Maintain"
]

---

## SECTION 4: YOUR TOP PRIORITY SYSTEMS (DETAILED)

[AI ANALYZE: Select top 2-3 systems with highest priority levels from Section 3. If tie, choose systems most relevant to patient's goal.]

### Priority System #1: [AI SELECT: System name] — [Priority Level]

**What we found** (in your assessment):

- **Structure**: [AI GENERATE: 1-2 sentences summarizing structural findings from imaging, exam, relevant labs. Age/sex context if relevant. Example: "Your bone density scan (DEXA) shows osteopenia (T-score -1.8), which is concerning at age 68, especially post-menopause."]

- **Function**: [AI GENERATE: 1-2 sentences summarizing functional findings from tests, patient-reported outcomes. Example: "Your sit-to-stand test showed 7 repetitions in 30 seconds (normal for your age is ≥10), indicating mild lower extremity weakness. You report difficulty rising from low chairs without using arms."]

- **Risk**: [AI GENERATE: 1-2 sentences summarizing risk markers and projected outcomes. Example: "With current bone density and strength, your 10-year fracture risk is 18% (FRAX score). Falls combined with weak bones significantly increase fracture risk."]

**Why this system matters for YOUR goal**:  
[AI GENERATE: 2-3 sentences linking this system to patient's personal goal. Make it concrete and motivating. Length: 40-80 words.]

**12-month system goal** (shared):  
[AI GENERATE: ONE specific, measurable goal for this system over 12 months. Must be: (1) concrete, (2) achievable, (3) tied to Structure/Function/Risk improvement. Example: "Improve bone density T-score from -1.8 to -1.5 AND increase sit-to-stand reps from 7 to ≥12 AND reduce 10-year fracture risk to <15%."]

---

### Priority System #2: [System name] — [Priority Level]

[AI GENERATE: Same structure as Priority System #1]

**What we found**:
- **Structure**: [AI GENERATE]
- **Function**: [AI GENERATE]
- **Risk**: [AI GENERATE]

**Why this matters for YOUR goal**: [AI GENERATE]

**12-month system goal**: [AI GENERATE]

---

### Priority System #3: [IF APPLICABLE - only include if 3rd system warrants priority]

[AI GENERATE: Same structure]

---

### Systems We're Monitoring (Not Immediate Focus)

[AI GENERATE: Brief 1-2 sentence summary of the non-priority systems that are green or yellow. Example: "Your cardiovascular, respiratory, and immune systems are all functioning well for your age with no immediate concerns. We'll continue routine monitoring but no active intervention needed in these areas right now."]

---

