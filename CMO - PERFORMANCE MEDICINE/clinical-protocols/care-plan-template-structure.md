# AI-Fillable Care Plan Template Structure

## Overview

This document defines the structure for **AI-fillable Performance Medicine care plans** that can be auto-populated based on patient data input and handed directly to patients. The template integrates:

1. **Patient's personal health goal** (center point)
2. **Life stage health goals** (clinician-recommended priorities by age)
3. **Preventive care recommendations** (USPSTF Grade A/B)
4. **8 Health Systems assessment** (Health Matrix)
5. **Unified prescription** (medical + lifestyle interventions)

The template uses structured `[INPUT]` fields that AI can populate based on patient data (medical history, comprehensive assessment, projected risk).

---

## Template Structure

### Section 1: Patient Information & Goals
### Section 2: Life Stage Context & Clinical Priorities
### Section 3: Health Matrix Assessment Summary
### Section 4: Preventive Care Checklist
### Section 5: Unified Care Plan (Quarterly Breakdown)
### Section 6: Monitoring & Follow-Up Plan
### Section 7: Patient Education & Resources

---

## SECTION 1: PATIENT INFORMATION & GOALS

```markdown
# Performance Medicine Care Plan

**Patient Name**: [INPUT: patient_name]
**Date of Birth**: [INPUT: date_of_birth] | **Age**: [INPUT: patient_age] | **Sex**: [INPUT: patient_sex]
**Date of Assessment**: [INPUT: assessment_date]
**Provider**: [INPUT: provider_name]

---

## Your Health Goal

**What you told us matters most to you**:
[INPUT: patient_primary_health_goal]

**Why this matters**: [INPUT: patient_goal_context]
_(Example: "I want to be able to play with my grandkids without getting tired" - This matters because family connection and physical capacity are central to your quality of life.)_

**How we'll measure success**:
- [INPUT: success_metric_1]
- [INPUT: success_metric_2]
- [INPUT: success_metric_3]

_(Example metrics: "Walk 30 minutes without breathlessness," "Energy level 7/10 through full workday," "Complete 5K run in under 35 minutes")_

---
```

### AI Logic for Section 1:
- `patient_primary_health_goal`: Extract from intake form or conversation
- `patient_goal_context`: Synthesize why goal matters to patient (quality of life, life stage, values)
- `success_metric_1/2/3`: Generate 2-3 measurable outcomes tied to goal (functional capacity, patient-reported outcomes, performance metrics)

---

## SECTION 2: LIFE STAGE CONTEXT & CLINICAL PRIORITIES

```markdown
## Your Life Stage: [INPUT: life_stage_name]

**Life Stage**: [INPUT: life_stage_name] (Ages [INPUT: life_stage_age_range])
**Typical Life Context**: [INPUT: life_stage_context]

### Clinical Priorities for Your Life Stage

Based on evidence and your age, these are the health priorities that will support your personal goal:

1. **[INPUT: life_stage_priority_1_title]**
   - Why it matters: [INPUT: life_stage_priority_1_rationale]
   - How we'll track it: [INPUT: life_stage_priority_1_tracking]

2. **[INPUT: life_stage_priority_2_title]**
   - Why it matters: [INPUT: life_stage_priority_2_rationale]
   - How we'll track it: [INPUT: life_stage_priority_2_tracking]

3. **[INPUT: life_stage_priority_3_title]**
   - Why it matters: [INPUT: life_stage_priority_3_rationale]
   - How we'll track it: [INPUT: life_stage_priority_3_tracking]

### How These Priorities Support Your Goal

[INPUT: life_stage_to_personal_goal_synergy]

_(Example: "Cardiovascular disease prevention supports your goal to travel extensively in retirement by ensuring your heart can handle the physical demands of long flights, walking tours, and high-altitude destinations.")_

---
```

### AI Logic for Section 2:

**If-Then Rules for Life Stage Selection:**
```
IF patient_age 0-1 THEN life_stage_name = "Infancy (Stage 1 - Pediatric)"
IF patient_age 2-5 THEN life_stage_name = "Early Childhood (Stage 2 - Pediatric)"
IF patient_age 6-12 THEN life_stage_name = "Middle Childhood (Stage 3 - Pediatric)"
IF patient_age 13-25 THEN life_stage_name = "Adolescence & Young Adulthood (Stage 4)"
IF patient_age 26-39 THEN life_stage_name = "Early Adulthood (Stage 5)"
IF patient_age 40-54 THEN life_stage_name = "Middle Adulthood (Stage 6)"
IF patient_age 55-64 THEN life_stage_name = "Late Middle Age (Stage 7)"
IF patient_age 65-79 THEN life_stage_name = "Older Adulthood (Stage 8)"
IF patient_age ≥80 THEN life_stage_name = "Advanced Age (Stage 9)"
```

**Data Source**: Pull from [life-stage-health-goals.md](life-stage-health-goals.md)
- `life_stage_context`: Pull "Life Context" section for matched stage
- `life_stage_priority_1/2/3`: Pull top 3 "Primary Clinical Goals" for matched stage
- `life_stage_to_personal_goal_synergy`: Synthesize connection between clinical priorities and patient's personal goal

---

## SECTION 3: HEALTH MATRIX ASSESSMENT SUMMARY

```markdown
## Your Health Systems: Current State

We assessed 8 core health systems across 3 clinical domains (Structure, Function, Risk). Here's what we found:

### Traffic Light Summary

| Health System | Structure | Function | Risk | Priority |
|---------------|-----------|----------|------|----------|
| **Neurological** | [INPUT: neuro_structure_status] | [INPUT: neuro_function_status] | [INPUT: neuro_risk_status] | [INPUT: neuro_priority_level] |
| **Cardiovascular** | [INPUT: cardio_structure_status] | [INPUT: cardio_function_status] | [INPUT: cardio_risk_status] | [INPUT: cardio_priority_level] |
| **Respiratory** | [INPUT: resp_structure_status] | [INPUT: resp_function_status] | [INPUT: resp_risk_status] | [INPUT: resp_priority_level] |
| **Metabolic/Digestive** | [INPUT: metabolic_structure_status] | [INPUT: metabolic_function_status] | [INPUT: metabolic_risk_status] | [INPUT: metabolic_priority_level] |
| **Filtration/Urinary** | [INPUT: filtration_structure_status] | [INPUT: filtration_function_status] | [INPUT: filtration_risk_status] | [INPUT: filtration_priority_level] |
| **Musculoskeletal** | [INPUT: msk_structure_status] | [INPUT: msk_function_status] | [INPUT: msk_risk_status] | [INPUT: msk_priority_level] |
| **Immune** | [INPUT: immune_structure_status] | [INPUT: immune_function_status] | [INPUT: immune_risk_status] | [INPUT: immune_priority_level] |
| **Reproductive/Hormonal** | [INPUT: repro_structure_status] | [INPUT: repro_function_status] | [INPUT: repro_risk_status] | [INPUT: repro_priority_level] |

**Status Key**: 🟢 Green (Optimal) | 🟡 Yellow (Watch) | 🟠 Orange (Action Needed) | 🔴 Red (High Priority)

### Priority Systems for Your Care Plan

Based on your assessment, we're focusing on these systems first:

#### [INPUT: priority_system_1_name] - Priority Level: [INPUT: priority_system_1_level]
**What we found**:
- Structure: [INPUT: priority_system_1_structure_findings]
- Function: [INPUT: priority_system_1_function_findings]
- Risk: [INPUT: priority_system_1_risk_findings]

**Why this matters for your goal**: [INPUT: priority_system_1_goal_connection]

#### [INPUT: priority_system_2_name] - Priority Level: [INPUT: priority_system_2_level]
**What we found**:
- Structure: [INPUT: priority_system_2_structure_findings]
- Function: [INPUT: priority_system_2_function_findings]
- Risk: [INPUT: priority_system_2_risk_findings]

**Why this matters for your goal**: [INPUT: priority_system_2_goal_connection]

#### [INPUT: priority_system_3_name] - Priority Level: [INPUT: priority_system_3_level]
**What we found**:
- Structure: [INPUT: priority_system_3_structure_findings]
- Function: [INPUT: priority_system_3_function_findings]
- Risk: [INPUT: priority_system_3_risk_findings]

**Why this matters for your goal**: [INPUT: priority_system_3_goal_connection]

---
```

### AI Logic for Section 3:

**Status Assignment Rules:**
```
FOR each health system:
  FOR each domain (Structure, Function, Risk):
    ANALYZE assessment data (history, exam, labs, imaging, functional tests, patient reports)

    IF all metrics optimal AND no concerning findings THEN status = 🟢 Green
    ELSE IF mild abnormalities OR early warning signs OR single elevated marker THEN status = 🟡 Yellow
    ELSE IF moderate abnormalities OR multiple elevated markers OR functional limitation THEN status = 🟠 Orange
    ELSE IF severe abnormalities OR acute concern OR very high risk THEN status = 🔴 Red
```

**Priority Level Assignment:**
```
FOR each health system:
  COUNT number of Orange or Red status across 3 domains

  IF ≥2 Red OR ≥1 Red + ≥2 Orange THEN priority_level = "High Priority"
  ELSE IF ≥1 Red OR ≥2 Orange THEN priority_level = "Action Needed"
  ELSE IF ≥1 Orange OR ≥2 Yellow THEN priority_level = "Watch"
  ELSE priority_level = "Maintain"

SORT systems by priority_level descending
SELECT top 2-3 systems as priority_system_1/2/3
```

**Data Sources:**
- Comprehensive assessment data from [comprehensive-health-assessment.md](../architecture/comprehensive-health-assessment.md) structure
- Traffic light thresholds from [health-matrix-framework.md](../architecture/health-matrix-framework.md)
- Synthesize `goal_connection` by linking system findings to patient's personal health goal

---

## SECTION 4: PREVENTIVE CARE CHECKLIST

```markdown
## Preventive Care: What You Need at Your Age

Based on USPSTF Grade A/B recommendations for your age and sex, here's what preventive care you need:

### Due Now or Overdue
[INPUT: preventive_care_due_list]

_(Example):_
- ☐ **Colorectal cancer screening** (Colonoscopy) - Due now (age 52, last was 10 years ago)
- ☐ **Lipid panel** - Overdue (last checked 6 years ago, recommend every 5 years)
- ☐ **Blood pressure check** - Due today (recommend every visit)

### Up to Date
[INPUT: preventive_care_current_list]

_(Example):_
- ✅ **Mammography** - Completed 8 months ago, next due in 16 months
- ✅ **Cervical cancer screening** (Pap + HPV) - Completed 2 years ago, next due in 3 years
- ✅ **Diabetes screening** - Completed today, normal, recheck in 3 years

### Not Yet Applicable
[INPUT: preventive_care_not_applicable_list]

_(Example):_
- **Lung cancer screening (low-dose CT)** - Not applicable (no smoking history)
- **Osteoporosis screening (DEXA)** - Not applicable until age 65 (currently 52)

---
```

### AI Logic for Section 4:

**Data Source**: [preventive-care-integration-matrix.md](preventive-care-integration-matrix.md)

**If-Then Rules:**
```
SELECT recommendations FROM preventive-care-integration-matrix
WHERE patient_age IN age_range
  AND (patient_sex = recommendation_sex OR recommendation_sex = "All")

FOR each recommendation:
  CHECK patient_medical_history for:
    - Last completion date
    - Risk factors that modify screening interval

  IF never completed OR (last_date + screening_interval) ≤ today THEN
    ADD to preventive_care_due_list

  ELSE IF last_date < (today - screening_interval/2) THEN
    ADD to preventive_care_current_list with next_due_date

  ELSE IF patient does not meet criteria (e.g., no smoking for lung CT) THEN
    ADD to preventive_care_not_applicable_list
```

**Special Logic:**
```
IF patient_sex = "Female" AND patient_age ≥40 THEN include mammography
IF patient_sex = "Male" AND patient_age 65-75 AND smoking_history = "Yes" THEN include AAA ultrasound
IF patient_age ≥35 AND (BMI ≥25 OR diabetes_risk_factors) THEN include diabetes screening
IF patient_age ≥50 AND ≤75 THEN include colorectal cancer screening
```

---

## SECTION 5: UNIFIED CARE PLAN (QUARTERLY BREAKDOWN)

```markdown
## Your Unified Care Plan: [INPUT: plan_timeframe]

This plan integrates medical interventions AND lifestyle actions into one prescription. We're breaking it into **quarterly themes** to keep it manageable and progressive.

---

### Quarter 1 (Next 3 Months): [INPUT: Q1_theme_name]
**Focus**: [INPUT: Q1_theme_description]

#### Target Systems:
1. **[INPUT: Q1_system_1_name]**
2. **[INPUT: Q1_system_2_name]**

#### Medical Interventions

**Medications:**
[INPUT: Q1_medications_list]

_(Example):_
- **Atorvastatin 20mg** - Take 1 tablet by mouth every evening
  - **Purpose**: Lower LDL cholesterol to reduce cardiovascular risk
  - **Target**: LDL <70 mg/dL
  - **Monitoring**: Recheck lipid panel in 8 weeks, liver function test at 12 weeks

**Procedures/Screenings:**
[INPUT: Q1_procedures_list]

_(Example):_
- **Colonoscopy** - Scheduled [date] at [location]
  - **Purpose**: Colorectal cancer screening (overdue, last was 11 years ago)
- **Exercise stress test** - Scheduled [date]
  - **Purpose**: Assess cardiovascular function and exercise capacity baseline

**Supplements:**
[INPUT: Q1_supplements_list]

_(Example):_
- **Vitamin D3 2000 IU daily**
  - **Purpose**: Support bone health, immune function (current level 22 ng/mL, target >30)
- **Magnesium glycinate 400mg nightly**
  - **Purpose**: Support sleep quality, muscle recovery

#### Lifestyle Prescription

**Movement** (Musculoskeletal, Cardiovascular, Metabolic)
[INPUT: Q1_movement_prescription]

_(Example):_
- **Strength training**: 2 sessions per week, 30-40 minutes
  - Exercises: Squats, deadlifts, push-ups, rows (focus on major muscle groups)
  - Intensity: Start with body weight or light weights, progress 10% per week
  - **Purpose**: Build muscle mass (currently low), improve insulin sensitivity, support cardiovascular function

- **Aerobic training**: 3-4 sessions per week, 20-30 minutes
  - Type: Walking, cycling, swimming (low-impact given knee pain)
  - Intensity: Zone 2 (can talk in full sentences, slight breathlessness)
  - **Purpose**: Build cardiovascular capacity (current 6-minute walk test: 380m, target >400m)

- **Daily movement**: 8,000 steps per day minimum
  - Break up sitting every 60 minutes with 2-minute walk

**Nutrition** (Metabolic, Cardiovascular, Musculoskeletal)
[INPUT: Q1_nutrition_prescription]

_(Example):_
- **Protein target**: 100g per day (currently ~60g)
  - Distribute across meals: 25-30g per meal
  - **Purpose**: Support muscle building, improve satiety, stabilize blood sugar

- **Meal timing**: 3 meals within 12-hour eating window (7am-7pm)
  - Stop eating by 7pm (currently eating until 10pm)
  - **Purpose**: Improve metabolic flexibility, support circadian rhythm

- **Fiber target**: 25-30g per day
  - Focus on vegetables (5 servings/day), whole grains, legumes
  - **Purpose**: Improve gut health, stabilize glucose, lower LDL cholesterol

- **Hydration**: 2-3 liters water per day
  - Front-load hydration (most by 5pm to avoid nighttime urination)

**Sleep & Recovery** (Neurological, Immune, Metabolic)
[INPUT: Q1_sleep_prescription]

_(Example):_
- **Sleep window**: 10:30pm - 6:30am (8 hours) every night
  - Currently: Irregular (midnight-6am some nights, 11pm-7am others)
  - **Purpose**: Improve sleep consistency, support HRV recovery, reduce daytime fatigue

- **Sleep hygiene**:
  - No screens 60 minutes before bed (currently using phone until 11:30pm)
  - Bedroom temperature 65-68°F
  - Blackout curtains or eye mask
  - White noise if needed

- **Recovery day**: 1 full rest day per week (no structured exercise, light movement only)

**Mental & Emotional Health** (Neurological, Immune)
[INPUT: Q1_mental_health_prescription]

_(Example):_
- **Stress management**: 10 minutes daily breathwork or meditation
  - Recommend: Box breathing (4-4-4-4) or Headspace app
  - **Purpose**: Lower sympathetic tone, improve HRV (currently low variability)

- **Mood tracking**: Daily 0-10 scale (morning energy, evening mood)
  - Use simple journal or app (Daylio, Bearable)
  - **Purpose**: Identify patterns, track response to interventions

**Surroundings & Social Context** (All Systems)
[INPUT: Q1_surroundings_prescription]

_(Example):_
- **Morning light exposure**: 10-15 minutes outdoor light within 1 hour of waking
  - **Purpose**: Anchor circadian rhythm, improve sleep onset, boost mood

- **Ergonomics**: Workstation assessment and adjustment
  - Standing desk or sit-stand converter
  - Monitor at eye level
  - **Purpose**: Reduce neck/back pain (current pain interference 5/10)

- **Social support**: Schedule 2 social activities per week
  - Walking with friend, family dinner, hobby group
  - **Purpose**: Reduce isolation (lives alone, works from home), improve adherence

---

### Quarter 2 (Months 4-6): [INPUT: Q2_theme_name] _(Evolving Roadmap)_
**Focus**: [INPUT: Q2_theme_description]

**Projected Targets:**
[INPUT: Q2_projected_targets]

_(Example):_
- Increase strength training to 3x/week with progressive load
- Add interval training 1x/week (if cardiovascular capacity improved)
- Taper atorvastatin if LDL <70 and no side effects
- Add bone density scan (DEXA) if not completed in Q1
- Focus on metabolic flexibility (experiment with 14-16 hour fasting windows)

**Note**: This plan will evolve based on your Q1 progress. We'll refine Q2 at your 3-month follow-up.

---

### Quarter 3 (Months 7-9): [INPUT: Q3_theme_name] _(Evolving Roadmap)_
**Focus**: [INPUT: Q3_theme_description]

---

### Quarter 4 (Months 10-12): [INPUT: Q4_theme_name] _(Evolving Roadmap)_
**Focus**: [INPUT: Q4_theme_description]

---
```

### AI Logic for Section 5:

**Quarterly Theme Selection:**
```
Q1_theme = "Foundation" (default for most new patients)
Q1_theme_description = "Establish baseline capacity, address highest-priority risks, build sustainable habits"

IF patient has acute high-risk findings THEN
  Q1_theme = "Stabilization"
  Q1_theme_description = "Address immediate health risks, prevent acute events"

IF patient is high-performing athlete or already optimized THEN
  Q1_theme = "Optimization"
  Q1_theme_description = "Fine-tune performance, address marginal gains"
```

**Target Systems for Q1:**
```
SELECT top 2-3 priority systems from Section 3 Health Matrix Assessment
WHERE priority_level IN ("High Priority", "Action Needed")

IF <2 systems meet criteria THEN
  ALSO SELECT systems most relevant to patient_primary_health_goal
```

**Medical Interventions Logic:**
```
MEDICATIONS:
  FOR each priority system:
    IF risk markers elevated AND lifestyle intervention insufficient alone THEN
      RECOMMEND evidence-based medication
      INCLUDE: medication_name, dose, frequency, purpose, target, monitoring_plan

PROCEDURES/SCREENINGS:
  PULL from Section 4 preventive_care_due_list
  ADD any diagnostic procedures needed based on assessment findings

SUPPLEMENTS:
  IF lab deficiency identified (Vitamin D, B12, Iron, etc.) THEN recommend repletion
  IF evidence-based benefit for priority system (Omega-3 for CVD, Creatine for muscle, etc.) THEN recommend
```

**Lifestyle Prescription Logic:**

Each of 5 lifestyle pillars should map to priority health systems:

```
MOVEMENT:
  TARGET: Priority systems Musculoskeletal, Cardiovascular, Metabolic
  COMPONENTS:
    - Strength training (frequency, intensity, exercises) IF musculoskeletal or metabolic priority
    - Aerobic training (type, duration, intensity) IF cardiovascular or metabolic priority
    - Balance/mobility IF neurological or musculoskeletal priority AND age ≥55
    - Daily movement target (steps, active minutes)

  DOSE based on:
    - Current functional capacity (from assessment)
    - Patient goal (performance vs. general health)
    - Injury/pain limitations

NUTRITION:
  TARGET: Priority systems Metabolic, Cardiovascular, Musculoskeletal, Immune
  COMPONENTS:
    - Protein target (g/day) IF musculoskeletal priority OR weight management goal
    - Meal timing/fasting window IF metabolic priority
    - Fiber target IF metabolic or cardiovascular priority
    - Specific macronutrient targets IF diabetes, CVD, or performance goal
    - Hydration target

SLEEP:
  TARGET: All systems, especially Neurological, Metabolic, Immune
  COMPONENTS:
    - Sleep window (bedtime, wake time, duration)
    - Sleep hygiene recommendations
    - Recovery days IF training load high

MENTAL & EMOTIONAL HEALTH:
  TARGET: Neurological, Immune (HRV, stress response)
  COMPONENTS:
    - Stress management technique (breathwork, meditation, therapy)
    - Mood/energy tracking
    - Cognitive tools IF attention/executive function impaired

SURROUNDINGS & SOCIAL:
  TARGET: All systems (enablers)
  COMPONENTS:
    - Light exposure (circadian health)
    - Ergonomics (musculoskeletal)
    - Social connection (adherence, emotional health)
    - Air quality, temperature (respiratory, sleep quality)
```

**Q2-Q4 Roadmap Logic:**
```
Q2_theme = "Build" (typical progression from Q1 Foundation)
Q3_theme = "Optimize" (typical progression from Q2 Build)
Q4_theme = "Sustain" (typical final quarter)

FOR Q2-Q4:
  PROJECT next steps based on expected Q1 outcomes
  KEEP vague/flexible (will be refined at each quarterly follow-up)
  EXAMPLES:
    - "Increase training volume if capacity improved"
    - "Add challenging system if priority systems stabilized"
    - "Taper medications if targets achieved"
    - "Focus on metabolic flexibility if metabolic system stable"
```

---

## SECTION 6: MONITORING & FOLLOW-UP PLAN

```markdown
## How We'll Track Your Progress

### Metrics We're Tracking

#### Capacity Measures (What you can do today)
[INPUT: capacity_metrics_list]

_(Example):_
- **Energy level**: Daily 0-10 scale (morning and evening)
  - **Baseline**: 4/10 by 2pm
  - **Target**: 7/10 through full day

- **6-minute walk test**: Distance covered in 6 minutes
  - **Baseline**: 380 meters
  - **Target**: >400 meters (normal for age/sex)

- **Sit-to-stand test**: Repetitions in 30 seconds
  - **Baseline**: 9 reps
  - **Target**: ≥12 reps

#### Resilience Measures (How quickly you recover)
[INPUT: resilience_metrics_list]

_(Example):_
- **Post-exertion fatigue**: Hours to return to baseline energy after workout
  - **Baseline**: 24-36 hours
  - **Target**: <12 hours

- **Heart rate recovery**: HR drop 1 minute after stopping exercise
  - **Baseline**: 15 bpm drop
  - **Target**: ≥25 bpm drop

- **Sleep consistency**: Night-to-night bedtime variability
  - **Baseline**: 2-3 hour variability (10pm-1am)
  - **Target**: <30 minute variability

#### Flexibility Measures (How well you adapt)
[INPUT: flexibility_metrics_list]

_(Example):_
- **Fasted morning comfort**: Can skip breakfast without energy crash (yes/no)
  - **Baseline**: No (must eat within 30 min of waking)
  - **Target**: Yes (can comfortably delay breakfast 2-3 hours)

- **Training variety tolerance**: Can perform both strength and cardio in same week without injury
  - **Baseline**: Yes, but with soreness/fatigue
  - **Target**: Yes, with quick recovery

#### Risk Markers (Traditional labs/tests)
[INPUT: risk_metrics_list]

_(Example):_
- **LDL cholesterol**:
  - **Baseline**: 142 mg/dL
  - **Target**: <70 mg/dL
  - **Recheck**: 8 weeks

- **Hemoglobin A1c**:
  - **Baseline**: 5.9% (prediabetes)
  - **Target**: <5.7% (normal)
  - **Recheck**: 12 weeks

- **Blood pressure**:
  - **Baseline**: 138/86 mmHg
  - **Target**: <130/80 mmHg
  - **Recheck**: Every visit

### Follow-Up Schedule

[INPUT: follow_up_schedule]

_(Example):_

| Timepoint | Visit Type | What We'll Do |
|-----------|------------|---------------|
| **Week 2** | Phone check-in (15 min) | Troubleshoot any barriers to starting plan, answer questions |
| **Week 6** | In-person or telehealth (30 min) | Review adherence, adjust plan if needed, check early progress (energy, sleep, movement tolerance) |
| **Week 12** | In-person (60 min) | **Q1 comprehensive reassessment**: Repeat functional tests, labs, Health Matrix evaluation; refine Q2 plan |
| **Month 6** | In-person (60 min) | **Q2 reassessment**: Update Health Matrix, adjust medications/interventions, refine Q3 plan |
| **Month 9** | In-person or telehealth (30 min) | **Q3 check-in**: Track progress toward annual goal, refine Q4 plan |
| **Month 12** | In-person (60 min) | **Annual comprehensive reassessment**: Full Health Matrix re-evaluation, celebrate progress, set next year's goals |

**Between visits**: Use [patient portal/app] to track daily metrics (energy, sleep, pain, adherence). Message care team anytime with questions.

---
```

### AI Logic for Section 6:

**Capacity Metrics Selection:**
```
SELECT 2-4 metrics directly tied to patient_primary_health_goal
EXAMPLES:
  IF goal = "play with grandkids" THEN include walk_test, sit_to_stand, energy_level
  IF goal = "run 5K" THEN include running_distance, heart_rate_recovery, soreness_duration
  IF goal = "finish workday without crashing" THEN include energy_level, attention_span, sleep_quality

FOR each metric:
  EXTRACT baseline from comprehensive assessment
  SET target based on:
    - Age/sex norms (for functional tests)
    - Patient goal requirements
    - Clinical judgment (realistic 3-12 month improvement)
```

**Resilience Metrics Selection:**
```
SELECT 1-3 recovery-related metrics
PRIORITIZE:
  - Heart rate recovery IF cardiovascular priority system
  - Post-exertion fatigue duration IF musculoskeletal or metabolic priority
  - Sleep consistency IF neurological priority
  - Illness recovery time IF immune priority
```

**Flexibility Metrics Selection:**
```
SELECT 1-2 adaptability metrics
EXAMPLES:
  - Fasted comfort IF metabolic priority
  - Training variety tolerance IF musculoskeletal or cardiovascular priority
  - Schedule disruption tolerance IF neurological priority (sleep, mood stability)
```

**Risk Markers Selection:**
```
SELECT lab/imaging values from priority systems that are Orange or Red status
FOR each:
  INCLUDE baseline, target, recheck_interval
  TARGET based on clinical guidelines (ATP III for lipids, ADA for glucose, ACC/AHA for BP, etc.)
```

**Follow-Up Schedule:**
```
DEFAULT schedule:
  Week 2: Phone check-in
  Week 6: Brief visit
  Week 12: Q1 comprehensive reassessment
  Month 6: Q2 reassessment
  Month 9: Q3 check-in
  Month 12: Annual comprehensive reassessment

MODIFY IF:
  High-risk patient → Add week 4 visit
  Medication titration needed → Add specific recheck visits
  Highly motivated/stable patient → Reduce to quarterly only
```

---

## SECTION 7: PATIENT EDUCATION & RESOURCES

```markdown
## Understanding Your Plan

### Key Concepts

**The Health Matrix**: We assess 8 health systems (Neurological, Cardiovascular, Respiratory, Metabolic, Filtration, Musculoskeletal, Immune, Reproductive/Hormonal) across 3 domains (Structure, Function, Risk). This gives us a complete picture of your health.

**Capacity, Resilience, Flexibility**: These are the three performance targets we're building:
- **Capacity** = What you can do today (energy, strength, function)
- **Resilience** = How quickly you recover (from workouts, stress, illness)
- **Flexibility** = How well you adapt (to schedule changes, fasting, varied training)

**Unified Prescription**: Your plan integrates medical interventions (medications, procedures) AND lifestyle actions (movement, nutrition, sleep, stress management, environment) into one prescription. Both are equally important.

### Your Resources

**Educational Materials**:
[INPUT: patient_education_resources]

_(Example):_
- [Understanding Your Cholesterol Results](link)
- [Zone 2 Cardio Training: How-To Guide](link)
- [Sleep Hygiene Checklist](link)
- [Protein-Rich Meal Ideas](link)

**Apps & Tools**:
[INPUT: recommended_apps_tools]

_(Example):_
- **Tracking**: Bearable (symptom/mood tracking), MyFitnessPal (nutrition), Whoop/Oura (sleep/HRV)
- **Movement**: Nike Training Club (strength workouts), Couch to 5K (running progression)
- **Mental Health**: Headspace (meditation), Insight Timer (breathwork)

**Support**:
- **Care team contact**: [phone/email/portal]
- **Urgent concerns**: Call [number] or go to ED if chest pain, severe shortness of breath, etc.
- **Questions between visits**: Message via patient portal, response within 24-48 hours

---

## Your Signature

I have reviewed this care plan with my provider. I understand the goals, the plan, and how we'll track progress. I agree to actively participate in this plan.

**Patient Signature**: _________________________ **Date**: _________

**Provider Signature**: _________________________ **Date**: _________

---

**Document Version**: 1.0
**Care Plan ID**: [INPUT: care_plan_id]
**Next Scheduled Review**: [INPUT: next_review_date]

```

### AI Logic for Section 7:

```
RESOURCES:
  SELECT educational materials relevant to:
    - Priority health systems
    - Specific interventions prescribed (e.g., if prescribing Zone 2 training, include "What is Zone 2?" guide)
    - Patient's health literacy level (adjust complexity)

APPS:
  RECOMMEND based on:
    - Metrics patient needs to track (sleep, HRV, nutrition, etc.)
    - Patient's tech comfort level
    - Budget (free vs. paid options)
```

---

## AI IMPLEMENTATION SPECIFICATIONS

### Required Input Data Fields

To populate this template, the AI agent needs the following structured input data:

#### 1. Patient Demographics
```json
{
  "patient_name": "string",
  "date_of_birth": "YYYY-MM-DD",
  "patient_age": integer,
  "patient_sex": "Male" | "Female" | "Other",
  "assessment_date": "YYYY-MM-DD",
  "provider_name": "string"
}
```

#### 2. Patient Goals
```json
{
  "primary_health_goal": "string (free text from patient)",
  "goal_context": "string (why this matters to patient)",
  "goal_timeframe": "string (e.g., '3 months', '1 year')"
}
```

#### 3. Comprehensive Assessment Data

**Medical History:**
```json
{
  "chief_complaint": "string",
  "medical_history": {
    "chronic_conditions": ["array of strings"],
    "past_surgeries": ["array of strings"],
    "medications_current": ["array of {name, dose, frequency}"],
    "allergies": ["array of strings"],
    "family_history": ["array of strings"],
    "social_history": {
      "smoking": "Never" | "Former" | "Current",
      "alcohol": "string",
      "exercise": "string",
      "occupation": "string",
      "living_situation": "string"
    }
  },
  "review_of_systems": {
    "neurological": "string (narrative or structured findings)",
    "cardiovascular": "string",
    "respiratory": "string",
    "metabolic": "string",
    "filtration": "string",
    "musculoskeletal": "string",
    "immune": "string",
    "reproductive_hormonal": "string"
  }
}
```

**Physical Examination:**
```json
{
  "vitals": {
    "height_cm": number,
    "weight_kg": number,
    "BMI": number,
    "blood_pressure": "string (systolic/diastolic)",
    "heart_rate": number,
    "respiratory_rate": number,
    "oxygen_saturation": number,
    "temperature": number
  },
  "exam_by_system": {
    "neurological": "string (structured findings)",
    "cardiovascular": "string",
    "respiratory": "string",
    "metabolic": "string",
    "musculoskeletal": "string",
    "reproductive_hormonal": "string",
    "other": "string"
  }
}
```

**Laboratory Data:**
```json
{
  "labs": [
    {
      "test_name": "string",
      "value": number,
      "unit": "string",
      "reference_range": "string",
      "status": "Normal" | "Low" | "High",
      "date": "YYYY-MM-DD"
    }
  ]
}
```

**Imaging/Diagnostic Tests:**
```json
{
  "imaging": [
    {
      "test_type": "string (e.g., 'Chest X-ray', 'Echocardiogram')",
      "date": "YYYY-MM-DD",
      "findings": "string",
      "interpretation": "Normal" | "Abnormal"
    }
  ]
}
```

**Functional Tests:**
```json
{
  "functional_tests": [
    {
      "test_name": "string (e.g., '6-minute walk test', 'Sit-to-stand')",
      "result": number,
      "unit": "string",
      "date": "YYYY-MM-DD"
    }
  ]
}
```

**Patient-Reported Outcomes:**
```json
{
  "patient_reported": {
    "energy_level": number (0-10),
    "sleep_quality": number (0-10),
    "sleep_duration_hours": number,
    "pain_level": number (0-10),
    "pain_interference": number (0-10),
    "mood": number (0-10),
    "stress_level": number (0-10),
    "quality_of_life": number (0-10)
  }
}
```

#### 4. Preventive Care History
```json
{
  "preventive_care": [
    {
      "screening_name": "string (e.g., 'Colonoscopy', 'Mammography')",
      "last_completed_date": "YYYY-MM-DD" | null,
      "next_due_date": "YYYY-MM-DD" | null,
      "status": "Current" | "Due" | "Overdue" | "Not applicable"
    }
  ],
  "vaccinations": [
    {
      "vaccine_name": "string",
      "last_dose_date": "YYYY-MM-DD",
      "up_to_date": boolean
    }
  ]
}
```

---

### AI Processing Workflow

```
STEP 1: INTAKE
  ↓ Receive structured patient data (demographics, assessment, history)

STEP 2: LIFE STAGE ASSIGNMENT
  ↓ Match patient_age to life stage (use if-then rules)
  ↓ Pull life stage clinical priorities from life-stage-health-goals.md

STEP 3: HEALTH MATRIX ANALYSIS
  ↓ FOR each of 8 systems:
      ↓ FOR each of 3 domains (Structure, Function, Risk):
          ↓ Analyze assessment data
          ↓ Assign traffic light status (Green/Yellow/Orange/Red)
  ↓ Calculate priority level for each system
  ↓ Identify top 2-3 priority systems

STEP 4: PREVENTIVE CARE MAPPING
  ↓ Match patient age/sex/risk factors to USPSTF recommendations
  ↓ Cross-reference with preventive_care_history
  ↓ Generate due/current/not-applicable lists

STEP 5: GOAL SYNTHESIS
  ↓ Connect patient personal goal → life stage priorities → priority systems
  ↓ Generate synergy narratives ("How X supports your goal to Y")

STEP 6: INTERVENTION GENERATION
  ↓ FOR each priority system:
      ↓ Generate medical interventions (medications, procedures, supplements)
      ↓ Generate lifestyle interventions (5 pillars: movement, nutrition, sleep, mental health, surroundings)
  ↓ Dose interventions based on current capacity, goal, and evidence
  ↓ Organize into Q1 detailed plan + Q2-Q4 roadmap

STEP 7: METRICS & MONITORING
  ↓ Select capacity/resilience/flexibility metrics tied to goal
  ↓ Set baselines (from assessment) and targets (based on norms + goal)
  ↓ Generate follow-up schedule

STEP 8: TEMPLATE POPULATION
  ↓ Fill all [INPUT] fields with generated content
  ↓ Format for human readability (markdown with tables, bullets, emphasis)

STEP 9: OUTPUT
  ↓ Return completed care plan document
  ↓ Ready to review with patient and hand over
```

---

## Example: Filled Template (Abbreviated)

### Patient: Sarah Johnson, Age 52, Female

**Primary Goal**: "I want to travel extensively in retirement (in 3 years) without worrying about my health holding me back."

**Life Stage**: Late Middle Age (Stage 7, Ages 55-64)
- Clinical priorities: Aggressive CVD prevention, functional capacity preservation, cancer screening

**Health Matrix Priority Systems**:
1. **Cardiovascular - Action Needed** (🟠 Risk: LDL 142, BP 138/86; 🟡 Function: 6MWT 380m)
2. **Metabolic - Action Needed** (🟠 Risk: A1c 5.9%, fasting glucose 108; 🟡 Function: energy 4/10 by 2pm)
3. **Musculoskeletal - Watch** (🟡 Structure: lumbar spine arthritis; 🟡 Function: sit-to-stand 9 reps)

**Preventive Care Due**:
- ☐ Colonoscopy (overdue, last 11 years ago)
- ☐ Lipid panel recheck (last 6 years ago)

**Q1 Plan (Foundation - Next 3 Months)**:

*Medical*:
- Start atorvastatin 20mg nightly (target LDL <70)
- Schedule colonoscopy
- Vitamin D3 2000 IU daily (current level 22 ng/mL)

*Lifestyle*:
- **Movement**: Strength 2x/week, walking 3-4x/week (20-30 min Zone 2), 8000 steps/day
- **Nutrition**: 100g protein/day, 12-hour eating window (7am-7pm), 25g fiber/day
- **Sleep**: 10:30pm-6:30am consistent window
- **Stress**: 10 min daily breathwork
- **Light**: 10-15 min morning outdoor exposure

**Metrics Tracking**:
- Energy: 4/10 → 7/10 target
- 6MWT: 380m → 400m target
- LDL: 142 → <70 target
- A1c: 5.9% → <5.7% target

**Follow-Up**: Week 2 phone, Week 6 visit, Week 12 Q1 reassessment

---

**Document Version**: 1.0
**Last Updated**: 2025-11-18
**Status**: Clinical Protocol - AI Implementation Specifications
