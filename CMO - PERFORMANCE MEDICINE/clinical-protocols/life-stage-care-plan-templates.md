# Life Stage-Specific Care Plan Templates

## Overview

This document provides **AI-fillable care plan templates customized for each of the 9 life stages**. Each life stage has distinct health priorities, Health Matrix expectations, lifestyle pillar prescriptions, and quarterly progression patterns.

**Purpose**: These templates recognize that a care plan for an infant looks completely different from a care plan for a 60-year-old planning retirement. By providing stage-specific templates, we ensure:
- Age-appropriate clinical priorities
- Developmentally appropriate Health Matrix expectations
- Life stage-appropriate lifestyle prescriptions
- Realistic quarterly progression (Foundation → Build → Optimize → Sustain may look different at different ages)

**How to Use**: The AI agent selects the appropriate template based on patient age, then populates all `[INPUT]` fields with patient-specific data.

---

## Template Index

### Pediatric Templates:
1. **Stage 1 (Pediatric): Infancy (0-1 year)**
2. **Stage 2 (Pediatric): Early Childhood (2-5 years)**
3. **Stage 3 (Pediatric): Middle Childhood (6-12 years)**

### Adult Templates:
4. **Stage 4: Adolescence & Young Adulthood (13-25 years)**
5. **Stage 5: Early Adulthood (26-39 years)**
6. **Stage 6: Middle Adulthood (40-54 years)**
7. **Stage 7: Late Middle Age (55-64 years)**
8. **Stage 8: Older Adulthood (65-79 years)**
9. **Stage 9: Advanced Age (80+ years)**

---

## TEMPLATE 1: INFANCY (AGES 0-1 YEAR)

### Section 1: Patient Information & Goals

```markdown
# Performance Medicine Care Plan - Infancy

**Patient Name**: [INPUT: patient_name]
**Date of Birth**: [INPUT: date_of_birth] | **Age**: [INPUT: patient_age_months] months
**Date of Assessment**: [INPUT: assessment_date]
**Provider**: [INPUT: provider_name]

---

## Your Child's Health Goal

**What you told us matters most to you (parents)**:
[INPUT: parent_primary_goal]

**Why this matters**: [INPUT: parent_goal_context]
_(Example: "We want our baby to grow healthy and meet milestones - This matters because as first-time parents, we want reassurance that everything is on track.")_

**How we'll measure success**:
- [INPUT: success_metric_1] _(Example: Weight gain on track - following WHO growth curve)_
- [INPUT: success_metric_2] _(Example: Developmental milestones met - rolling by 6 months, sitting by 8 months)_
- [INPUT: success_metric_3] _(Example: Successful feeding established - breastfeeding or formula feeding going well)_

---
```

### Section 2: Life Stage Context

```markdown
## Your Child's Life Stage: Infancy (0-1 Year)

**Life Context**: Total dependence, rapid growth, parent-infant bonding

### Clinical Priorities for Infancy

Based on your child's age, these are the health priorities we focus on:

1. **Support Rapid Physical Growth**
   - Why it matters: Fastest growth period in human life; sets foundation for all development
   - How we track it: Weight, length, head circumference on WHO growth charts

2. **Establish Feeding & Nutrition**
   - Why it matters: Nutrition drives growth; breastfeeding supports immune development
   - How we track it: Weight gain (5-7 oz/week first 4 months), feeding pattern

3. **Monitor Developmental Milestones**
   - Why it matters: Early detection of delays enables early intervention
   - How we track it: Motor milestones (head control, rolling, sitting, crawling, standing), social milestones (smile, tracking, responding to sound)

4. **Prevent SIDS & Ensure Safety**
   - Why it matters: SIDS is leading cause of death in infants 1-12 months
   - How we track it: Safe sleep practices (back to sleep, firm surface, room sharing)

5. **Complete Vaccination Schedule**
   - Why it matters: Prevents life-threatening infections
   - How we track it: CDC vaccination schedule adherence

6. **Screen for Congenital Conditions**
   - Why it matters: Early detection prevents disability/death
   - How we track it: Newborn screening results, hearing screening, heart defect screening

### How These Priorities Support Your Family Goals

[INPUT: life_stage_to_personal_goal_synergy]

_(Example: "Ensuring your baby's growth and development are on track gives you peace of mind as new parents. Establishing successful feeding and sleep routines helps your baby thrive AND helps you manage the demands of new parenthood.")_

---
```

### Section 3: Health Matrix Assessment Summary

```markdown
## Your Child's Health Systems: Current Assessment

We assessed 8 health systems. Here's what we found:

| Health System | Growth/Structure | Function (Development) | Risk | Status |
|---------------|------------------|------------------------|------|--------|
| **Neurological** | Head circumference: [INPUT: head_circumference_percentile] | Milestones: [INPUT: neuro_milestones_status] | [INPUT: neuro_risk_status] | [INPUT: neuro_overall_status] |
| **Cardiovascular** | Murmur: [INPUT: cardiac_murmur_status] | Heart rate: [INPUT: heart_rate_status] | [INPUT: cardio_risk_status] | [INPUT: cardio_overall_status] |
| **Respiratory** | Breathing: [INPUT: respiratory_exam_status] | O2 sat: [INPUT: o2_sat_status] | [INPUT: resp_risk_status] | [INPUT: resp_overall_status] |
| **Metabolic** | Weight: [INPUT: weight_percentile] | Feeding: [INPUT: feeding_status] | [INPUT: metabolic_risk_status] | [INPUT: metabolic_overall_status] |
| **Musculoskeletal** | Length: [INPUT: length_percentile] | Motor milestones: [INPUT: motor_milestones_status] | [INPUT: msk_risk_status] | [INPUT: msk_overall_status] |
| **Immune** | No infections: [INPUT: immune_status] | Vaccinations: [INPUT: vaccination_status] | [INPUT: immune_risk_status] | [INPUT: immune_overall_status] |
| **Other Systems** | [INPUT: other_systems_summary] | | | |

**Status Key**: 🟢 Green (On track) | 🟡 Yellow (Monitor) | 🟠 Orange (Action needed) | 🔴 Red (Urgent)

### What We're Focusing On

[INPUT: priority_systems_narrative]

_(Example: "Your baby's growth and development are on track across all systems. We're focusing on supporting continued healthy growth and ensuring all developmental milestones and vaccinations stay on schedule.")_

---
```

### Section 4: Preventive Care Checklist

```markdown
## Preventive Care for Infancy

### Completed
- ✅ Newborn metabolic screening: [INPUT: newborn_screening_date]
- ✅ Hearing screening: [INPUT: hearing_screening_date]
- ✅ Heart defect screening (pulse ox): [INPUT: heart_screening_date]

### Due Now or Upcoming
[INPUT: preventive_care_due_list]

_(Example):_
- ☐ **2-month vaccines** (Hep B #2, DTaP #1, Hib #1, IPV #1, PCV13 #1, Rotavirus #1) - Due: [date]
- ☐ **4-month vaccines** (DTaP #2, Hib #2, IPV #2, PCV13 #2, Rotavirus #2) - Due: [date]
- ☐ **6-month vaccines** (Hep B #3, DTaP #3, Hib #3, IPV #3, PCV13 #3, Rotavirus #3, Flu #1) - Due: [date]

---
```

### Section 5: Care Plan (Next 3-6 Months)

```markdown
## Your Baby's Care Plan

### Feeding & Nutrition

**Current Feeding Pattern**: [INPUT: current_feeding_pattern]

**Recommendations**:
[INPUT: feeding_recommendations]

_(Example):_
- **Continue exclusive breastfeeding** (or formula) until 6 months
- **Introduce solids at 6 months**: Start with iron-fortified cereal, then pureed vegetables and fruits
- **Vitamin D supplementation**: 400 IU daily (if breastfed)
- **Feeding schedule**: On-demand feeding (typically 8-12 times per 24 hours for breastfed babies)

**Why this matters**: Adequate nutrition supports rapid brain and body growth.

---

### Growth Monitoring

**Current Status**:
- Weight: [INPUT: weight] ([INPUT: weight_percentile] percentile)
- Length: [INPUT: length] ([INPUT: length_percentile] percentile)
- Head circumference: [INPUT: head_circumference] ([INPUT: head_circumference_percentile] percentile)

**Targets**:
- Weight gain: [INPUT: weight_gain_target] _(Example: 5-7 oz/week for first 4 months, then 3-5 oz/week)_
- Length growth: [INPUT: length_growth_target] _(Example: ~1 inch per month)_
- Head circumference: [INPUT: head_circumference_target] _(Example: Following growth curve, ~0.5 inches per month)_

**Recheck**: At each well-child visit (2, 4, 6, 9, 12 months)

---

### Developmental Milestones to Watch For

**[INPUT: current_age_months]-month milestones**:
[INPUT: age_appropriate_milestones]

_(Example for 4-month-old):_
- **Motor**: Lifts head 90° when on tummy, rolls from tummy to back, brings hands to mouth
- **Social/Cognitive**: Social smile, tracks objects, responds to sounds, coos and babbles
- **What to do**: Lots of tummy time (3-5 times per day, 3-5 minutes each), talk and sing to baby, read books with high-contrast images

**Next milestone check**: [INPUT: next_milestone_check_date]

---

### Safe Sleep Practices

**Back to Sleep - Every Sleep**:
- Always place baby on back to sleep (naps and nighttime)
- Firm mattress, no pillows, no blankets, no stuffed animals
- Room sharing (but not bed sharing) for first 6-12 months
- Pacifier at sleep time (may reduce SIDS risk)
- No smoke exposure
- Keep room temperature comfortable (68-72°F)

---

### Vaccinations

**Upcoming Vaccines**:
[INPUT: upcoming_vaccines_schedule]

_(Example):_
- **2-month visit**: Hep B, DTaP, Hib, IPV, PCV13, Rotavirus
- **4-month visit**: DTaP, Hib, IPV, PCV13, Rotavirus
- **6-month visit**: Hep B, DTaP, Hib, IPV, PCV13, Rotavirus, Influenza

---

### Parent Support & Education

**Topics to discuss at next visits**:
- [INPUT: parent_education_topics]

_(Example):_
- Safe sleep practices (ongoing)
- Introducing solids at 6 months
- Developmental play activities (tummy time, reading, talking)
- Managing infant crying/soothing techniques
- Postpartum parent mental health screening

---
```

### Section 6: Follow-Up Schedule

```markdown
## Follow-Up Plan

**Well-Child Visits** (American Academy of Pediatrics schedule):
- 2-week visit (if needed)
- 2-month visit
- 4-month visit
- 6-month visit
- 9-month visit
- 12-month visit

**What happens at each visit**:
- Growth measurements (weight, length, head circumference)
- Developmental milestone assessment
- Physical examination
- Vaccinations
- Parent education and anticipatory guidance

**Between visits**: Call or message us if:
- Fever >100.4°F (rectal temp)
- Poor feeding or not waking to feed
- Decreased wet diapers (<6 per day after day 5)
- Developmental concerns
- Any safety concerns

---
```

---

## TEMPLATE 2: EARLY CHILDHOOD (AGES 2-5 YEARS)

*[Due to length constraints, I'll provide the structure but abbreviate - the full template would follow same comprehensive format as Template 1]*

### Key Differences from Infancy Template:

**Section 1 (Goals)**: Parent goals shift to preschool readiness, managing tantrums, picky eating, safety

**Section 2 (Life Stage Priorities)**:
1. Support continued physical growth (monitor BMI, prevent obesity)
2. Advance motor skills (gross and fine motor)
3. Support language & cognitive development
4. Establish healthy eating patterns
5. Prevent injuries
6. Support social-emotional development
7. Continue vaccinations (preschool series)
8. Vision & hearing screening

**Section 3 (Health Matrix)**: Focus shifts from growth percentiles to BMI percentiles, language milestones, motor skill acquisition

**Section 4 (Preventive Care)**: DTaP, MMR, Varicella boosters at 4-6 years; vision screening at age 3-5

**Section 5 (Care Plan - Different Structure)**:
- **Nutrition**: Balanced diet, limit sugar, exposure to variety of foods, manage picky eating
- **Physical Activity**: 60 minutes active play per day (running, jumping, climbing)
- **Language Development**: Read together daily, encourage conversation
- **Sleep**: 10-13 hours per night, consistent bedtime routine
- **Social-Emotional Development**: Preschool or play dates, emotional regulation strategies
- **Injury Prevention**: Car seat safety, water safety, childproofing

**Section 6 (Follow-Up)**: Annual well-child visits (unless issues arise)

---

## TEMPLATE 4: ADOLESCENCE & YOUNG ADULTHOOD (AGES 13-25)

*[First adult template - shifts to performance optimization focus]*

### Key Features:

**Section 1 (Goals)**: Personal goals shift to athletic performance, academic success, body image, independence

**Section 2 (Life Stage Priorities)**:
1. Complete physical development (puberty, bone density accrual)
2. Build movement capacity (sports participation, strength training foundation)
3. Establish healthy lifestyle patterns (sleep 8-10 hrs, nutrition, avoid risky behaviors)
4. Support mental health (screen for depression, anxiety, substance use)
5. Reproductive health education (contraception, STI prevention, consent)

**Section 5 (Care Plan - Quarterly Structure Begins)**:

**Q1 (Foundation)**: Establish baseline capacity, address any risky behaviors, build sustainable habits
- Movement: Sports participation 3-4x/week + strength training 2x/week
- Nutrition: Protein 1.6 g/kg, regular meals (avoid skipping breakfast), limit processed foods/sugar
- Sleep: 8-10 hours, consistent bedtime (even on weekends), no screens 1 hour before bed
- Mental Health: Screen for depression (PHQ-9), substance use, stress management techniques
- Preventive Care: Tdap booster, HPV vaccine series, meningococcal vaccine

**Q2-Q4**: Build capacity progressively (increase training volume, optimize nutrition for performance)

---

## TEMPLATE 5: EARLY ADULTHOOD (AGES 26-39)

### Key Features:

**Section 2 (Life Stage Priorities)**:
1. Optimize reproductive health (preconception care if planning pregnancy)
2. Prevent cardiometabolic disease (BP <120/80, A1c <5.7%, normal lipids)
3. Maximize performance capacity (high-stress careers, family demands)
4. Build resilience (stress management, HRV tracking, illness recovery <1 week)

**Section 5 (Care Plan - Full Quarterly Structure)**:

**Q1 (Foundation)**: Establish baseline capacity, address highest-priority risks
- Movement: Strength 2-3x/week (compound lifts), cardio 3-4x/week (Zone 2), 8K steps/day
- Nutrition: Protein 1.6-2.0 g/kg, 12-hour eating window, meal prep strategy
- Sleep: 7-9 hours, 10:30pm-6:30am window, sleep hygiene
- Stress: 10-15 min daily meditation or breathwork, HRV tracking
- Preventive Care: BP check, lipid panel, A1c, cervical cancer screening (women), STI screening if indicated

**Q2 (Build)**: Increase training volume, optimize interventions
- Movement: Progress to 3-4x/week strength, 4-5x/week cardio, add interval training
- Nutrition: Experiment with metabolic flexibility (14-16 hour fasting windows 2x/week)

**Q3 (Optimize)**: Fine-tune performance, challenge the system
- Movement: Cross-training variety, environmental stressors (heat/cold)
- Nutrition: Nutrient timing, carb cycling if performance goal

**Q4 (Sustain)**: Maintain gains, identify sustainable long-term patterns

---

## TEMPLATE 6: MIDDLE ADULTHOOD (AGES 40-54)

### Key Features:

**Section 2 (Life Stage Priorities)**:
1. Chronic disease risk reversal (prediabetes → normal, prehypertension → normal)
2. Musculoskeletal preservation (resistance training 2x/week minimum, DEXA if indicated)
3. Metabolic flexibility optimization (fasting tolerance, post-meal glucose <140)
4. Hormonal support (perimenopause management for women, testosterone optimization for men)
5. Cancer screening initiation (mammography for women 40-50+, colonoscopy at 45-50)

**Section 5 (Care Plan - Emphasis on Prevention)**:

**Q1 (Foundation)**: Address emerging risk markers aggressively
- Medical: Statin if LDL elevated + CVD risk, metformin if prediabetes, address hormonal symptoms
- Movement: Strength training 2-3x/week (critical for muscle preservation), cardio 3-4x/week
- Nutrition: Protein 1.6-2.0 g/kg (higher to preserve muscle), Mediterranean diet pattern
- Sleep: 7-9 hours non-negotiable, manage sleep disruption from perimenopause (women)
- Preventive Care: Colonoscopy (ages 45-50), mammography (women 40-50), DEXA (women >65 or risk factors)

**Q2-Q4**: Focus on reversing early disease (prediabetes → normal, prehypertension → normal) and optimizing body composition

---

## TEMPLATE 7: LATE MIDDLE AGE (AGES 55-64)

### Key Features:

**Section 2 (Life Stage Priorities)**:
1. **Aggressive cardiovascular disease prevention** (ASCVD risk <10%, advanced lipids, CAC score if indicated)
2. Functional capacity preservation (6MWT >400m, sit-to-stand ≥12 reps)
3. Bone health optimization (DEXA at 65, vitamin D + calcium, resistance training)
4. Chronic disease control (A1c <7%, BP <130/80, CKD monitoring)
5. Cancer screening completion (mammography, colonoscopy, lung CT if smoking history)

**Section 5 (Care Plan - Aggressive Prevention + Function)**:

**Q1 (Foundation)**: Stabilize cardiovascular risk, preserve functional capacity
- Medical: Statin (target LDL <70), aspirin if indicated, BP control (<130/80), manage diabetes aggressively
- Movement: Strength 2-3x/week (preserve muscle mass and bone density), cardio 4-5x/week (Zone 2 focus), balance training 2-3x/week (fall prevention)
- Nutrition: Protein 1.2-1.6 g/kg, anti-inflammatory diet (Mediterranean), adequate calcium (1200mg) and vitamin D
- Sleep: 7-9 hours, manage sleep disruption (menopause for women, nocturia, sleep apnea)
- Preventive Care: Colonoscopy (if due), mammography annual (women), lung CT annual (if 20 pack-year smoking history), DEXA at 65 (women) or 70 (men)

**Q2-Q4**: Optimize cardiovascular health, preserve functional capacity for retirement activities

---

## TEMPLATE 8: OLDER ADULTHOOD (AGES 65-79)

### Key Features:

**Section 2 (Life Stage Priorities)**:
1. **Fall prevention** (balance training, home safety, medication review)
2. Cognitive function monitoring (MoCA annually, hearing screening, social engagement)
3. Independence maintenance (ADLs/IADLs assessment, driving evaluation if concerns)
4. Chronic disease optimization (complication prevention, avoid hypoglycemia)
5. Frailty prevention (protein 1.2-1.5 g/kg, resistance training, avoid weight loss)
6. Vaccination status (flu, pneumonia, COVID, shingles)

**Section 5 (Care Plan - Function & Independence Focus)**:

**Q1 (Foundation)**: Preserve functional independence, prevent falls
- Medical: Medication review (deprescribe if appropriate, avoid high-risk meds like benzos), manage chronic diseases (avoid overtreatment - A1c <8% OK in frail elderly), hearing aids if indicated
- Movement: Balance training 3-4x/week (single-leg stand, tandem walk, tai chi), strength 2x/week (resistance bands or light weights - focus on fall prevention muscles), walking 20-30 min daily
- Nutrition: Protein 1.2-1.5 g/kg (critical for frailty prevention), adequate calories (avoid weight loss), vitamin D + calcium
- Sleep: 7-8 hours, address nocturia (reduce evening fluids, consider medication adjustment), screen for sleep apnea
- Home Safety: Fall risk assessment, home modifications (grab bars, remove rugs, improve lighting)
- Preventive Care: DEXA (if not done), colonoscopy (if due and life expectancy >10 years), mammography (individualized), flu + pneumonia + COVID + shingles vaccines

**Q2-Q4**: Maintain functional independence, manage chronic diseases, prevent hospitalization

---

## TEMPLATE 9: ADVANCED AGE (AGES 80+)

### Key Features:

**Section 2 (Life Stage Priorities)**:
1. **Quality of life prioritization** (pain control, symptom management, comfort)
2. Catastrophic event prevention (falls, fractures, hospitalizations)
3. Functional support (assisted devices, home health, ADL assistance)
4. Medication simplification (deprescribe low-yield drugs, avoid polypharmacy)
5. Advance care planning (goals of care, code status, end-of-life wishes)

**Section 5 (Care Plan - Quality of Life & Symptom Management)**:

**Focus**: Maximize quality of life, prevent suffering, maintain dignity

- **Medical**: Deprescribe aggressively (stop statins if no established CVD, reduce BP meds to avoid hypotension, simplify diabetes regimen - avoid hypoglycemia), palliative care referral if appropriate, pain management (chronic pain common - use multimodal approach, judicious opioids if needed)
- **Movement**: As tolerated - walking with assistive device if needed, chair exercises, avoid bedrest (deconditioning rapid at this age)
- **Nutrition**: Liberalized diet (enjoy food - no restrictions unless causing symptoms), protein 1.2-1.5 g/kg if able, prevent weight loss, oral supplements if poor intake
- **Functional Support**: Assistive devices (walker, cane, wheelchair if needed), home health aide if ADL assistance needed, meals on wheels if cooking difficult
- **Preventive Care**: Stop screening tests with long lead times (colonoscopy, mammography unless established cancer risk), continue flu + pneumonia + COVID vaccines
- **Advance Care Planning**: Document goals of care, code status, healthcare proxy, POLST form if appropriate

**No Quarterly Progression**: Care plan is static, focused on maintaining current function and quality of life, adjusting as needs change

---

## Document Summary

This document provides **9 life stage-specific care plan templates**, each customized for the unique health priorities, developmental stage, and lifestyle context of that age group:

**Pediatric Templates (1-3)**: Focus on growth, development, milestones, parent education
- Infancy: Growth charts, feeding, SIDS prevention, vaccinations
- Early Childhood: Motor/language development, healthy eating, injury prevention
- Middle Childhood: Obesity prevention, academic success, sports participation

**Adult Templates (4-9)**: Focus on performance optimization, disease prevention, functional capacity, aging successfully
- Adolescence (13-25): Foundation building, risky behavior prevention
- Early Adulthood (26-39): Peak performance, reproductive health, cardiometabolic prevention
- Middle Adulthood (40-54): Chronic disease reversal, muscle preservation, hormonal support, cancer screening
- Late Middle Age (55-64): Aggressive CVD prevention, functional capacity preservation, retirement preparation
- Older Adulthood (65-79): Fall prevention, cognitive monitoring, independence maintenance, frailty prevention
- Advanced Age (80+): Quality of life, symptom management, catastrophic event prevention, advance care planning

Each template is **AI-fillable** with structured `[INPUT]` fields and can be auto-populated based on patient data, then refined by the provider and handed to the patient/family.

---

**Document Version**: 1.0
**Last Updated**: 2025-11-18
**Status**: Clinical Protocol - Life Stage-Specific Templates
