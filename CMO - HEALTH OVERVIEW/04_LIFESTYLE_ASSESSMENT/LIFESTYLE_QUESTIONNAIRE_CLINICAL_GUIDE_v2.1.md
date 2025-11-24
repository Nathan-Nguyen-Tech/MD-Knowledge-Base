# Lifestyle Questionnaire - Clinical Interpretation & Metadata Guide

**Document Version:** 2.1 (Companion to v2.0 Questionnaire)
**Last Updated:** 2025-11-20
**Purpose:** Clinical decision support, risk stratification, and digital implementation metadata

---

## HOW TO USE THIS GUIDE

This document provides:
1. **Per-question clinical interpretation** - What scores mean clinically
2. **Risk stratification** - Which questions are highest priority
3. **Clinical triggers** - Suggested follow-up actions
4. **System mapping** - How questions map to your 8-organ Compass framework
5. **Implementation metadata** - Technical specifications for developers

**For Clinicians:** Use Section 1-4 for patient review and care planning
**For Developers:** Use Section 5 for digital implementation

---

# SECTION 1: PER-QUESTION CLINICAL INTERPRET ATION CHARTS

## PILLAR 1: NUTRITION

| Question ID | Brief Description | Red Flag (0-3) | Yellow (4-6) | Green (7-10) | Clinical Significance |
|------------|-------------------|----------------|--------------|--------------|----------------------|
| **NUTR_Q01** 🟠 | Overall eating quality | Very poor diet quality | Mixed quality | Excellent quality | Correlates with metabolic syndrome, CVD risk |
| **NUTR_Q02** | Water intake | Chronic dehydration | Suboptimal | Well-hydrated | Affects kidney function, cognition, fatigue |
| **NUTR_Q03** 🟠 | Vegetable intake | Rarely eats vegetables | Sometimes | Daily vegetables | Fiber, micronutrients, CVD/cancer prevention |
| **NUTR_Q04** | Fruit intake | Rarely eats fruit | Sometimes | Daily fruit | Antioxidants, fiber, metabolic health |
| **NUTR_Q05** | Protein intake | Inadequate protein | Moderate | Adequate protein | Muscle maintenance, satiety, metabolic health |
| **NUTR_Q06** | Healthy fats | No healthy fats | Some | Regular healthy fats | Cardiovascular, brain, hormonal health |
| **NUTR_Q07** | Portion control | Frequent overeating | Sometimes overeat | Good control | Weight management, metabolic health |
| **NUTR_Q08** | Mindful eating | Always distracted eating | Sometimes mindful | Consistently mindful | Satiety signals, digestion, weight |
| **NUTR_Q09** 🔴 | Processed foods (⚠️) | Daily ultra-processed | Few times/week | Rare/never | Strong predictor of obesity, metabolic disease |
| **NUTR_Q10** 🔴 | Sugary foods (⚠️) | Daily sugar | Few times/week | Rare/never | Diabetes risk, inflammation, dental health |
| **NUTR_Q11** | Whole grains | Never | Sometimes | Always | Fiber, glycemic control, CV health |
| **NUTR_Q12** | Hunger cues awareness | Cannot differentiate | Sometimes | Excellent awareness | Emotional eating, weight management |
| **NUTR_Q13** | Meal planning | Never plans | Sometimes | Always plans | Consistency, food quality, budget |
| **NUTR_Q14** | Home cooking | Never cooks | Some meals | Most meals | Food quality, nutrient control, cost |
| **NUTR_Q15** 🔴 | Alcohol (⚠️) | Daily/excessive | Occasional | Rare/never | Liver, brain, cancer, addiction risk |
| **NUTR_Q16** | Food variety | Very limited | Some variety | Wide variety | Micronutrient adequacy |
| **NUTR_Q17** | Food access | Very difficult | Somewhat difficult | Easy access | Social determinant of health |

---

## PILLAR 2: MOVEMENT

| Question ID | Brief Description | Red Flag (0-3) | Yellow (4-6) | Green (7-10) | Clinical Significance |
|------------|-------------------|----------------|--------------|--------------|----------------------|
| **MOVE_Q01** 🟠 | Recent activity | No exercise | Some activity | Very active | Current fitness status |
| **MOVE_Q02** | Energy for movement | Very weak/unfit | Moderate | Strong/fit | Functional capacity |
| **MOVE_Q03** 🔴 | Moderate aerobic activity | Rarely/never | Few times/week | Most days | Cardiovascular health, all-cause mortality |
| **MOVE_Q04** | Vigorous exercise | Never | Monthly | 3+/week | Cardiorespiratory fitness, longevity |
| **MOVE_Q05** 🟠 | Strength training | Never | 1-2x/week | 3+/week | Sarcopenia prevention, bone density, metabolism |
| **MOVE_Q06** | Stretching | Never | Few times/week | Daily | Flexibility, injury prevention, mobility |
| **MOVE_Q07** | Daily movement (NEAT) | Minimal movement | Some movement | Very active | Energy expenditure, metabolic health |
| **MOVE_Q08** 🔴 | Sitting time (⚠️) | 10+ hours/day | ~6 hours | <4 hours | Independent CVD/mortality risk |
| **MOVE_Q09** 🟠 | Screen time (⚠️) | 6+ hours leisure | ~3 hours | <1 hour | Sedentary behavior, mental health |
| **MOVE_Q10** | Movement breaks | Never | Occasionally | Every 30 min | Interrupts sedentary time |
| **MOVE_Q11** | Exercise consistency | Very inconsistent | Somewhat | Very consistent | Adherence, long-term outcomes |
| **MOVE_Q12** | Balance exercises | Never | Sometimes | Regularly | Fall prevention (aging) |
| **MOVE_Q13** | Full-body strength | No program | Some groups | Complete program | Balanced strength, injury prevention |
| **MOVE_Q14** | Work activity level | Desk job | Some activity | Very active | Occupational contribution to TDEE |
| **MOVE_Q15** | Cardiovascular endurance | Very poor | Moderate | Excellent | VO2 max proxy, cardiovascular fitness |
| **MOVE_Q16** | Joint mobility | Very stiff | Moderate | Excellent | Functional capacity, ADL independence |

---

## PILLAR 3: SLEEP & RECOVERY

| Question ID | Brief Description | Red Flag (0-3) | Yellow (4-6) | Green (7-10) | Clinical Significance |
|------------|-------------------|----------------|--------------|--------------|----------------------|
| **SLEEP_Q01** 🟠 | Sleep quality | Very poor | Okay | Excellent | Overall sleep health |
| **SLEEP_Q02** 🟠 | Energy level | Constantly exhausted | Moderate | High energy | Fatigue, recovery status |
| **SLEEP_Q03** 🔴 | Stress level | Extremely stressed | Moderate | Calm | Allostatic load, cortisol, immune function |
| **SLEEP_Q04** 🔴 | Sleep duration | ≤5 hours | ~6 hours | 7-9 hours | Sleep deprivation = ↑CVD, metabolic disease |
| **SLEEP_Q05** | Falling asleep | Hours to fall asleep | 30-60 min | <15 min | Sleep onset latency, insomnia |
| **SLEEP_Q06** | Staying asleep | Wake many times | 1-2 times | Through night | Sleep fragmentation, OSA screen |
| **SLEEP_Q07** | Waking refreshed | Exhausted upon waking | Somewhat rested | Fully refreshed | Sleep quality, restorative sleep |
| **SLEEP_Q08** 🔴 | Stress management | Overwhelmed constantly | Sometimes | Effective | Chronic stress = systemic inflammation |
| **SLEEP_Q09** | Relaxation practices | Never | Few times/week | Daily | Stress buffering, parasympathetic tone |
| **SLEEP_Q10** | Work-life balance | No balance | Some | Excellent | Burnout prevention |
| **SLEEP_Q11** | Downtime | Always busy | Sometimes | Daily | Recovery, nervous system regulation |
| **SLEEP_Q12** 🔴 | Daytime sleepiness (⚠️) | All day sleepy | Sometimes | Never | OSA, narcolepsy, chronic fatigue screen |
| **SLEEP_Q13** | Overall recovery | Never recovered | Somewhat | Fully recovered | Readiness for activity |
| **SLEEP_Q14** | Sleep schedule consistency | Very irregular | Somewhat | Very consistent | Circadian alignment |
| **SLEEP_Q15** | Bedroom environment | Poor | Okay | Optimal | Sleep hygiene |
| **SLEEP_Q16** 🟠 | Screen before bed (⚠️) | Every night | Few times/week | Rarely | Blue light, sleep onset delay |
| **SLEEP_Q17** | Physical recovery | Never rest | Sometimes | Appropriate rest | Overtraining prevention |
| **SLEEP_Q18** | Caffeine habits | Anytime | Try to avoid late | Never after noon | Sleep onset, quality interference |

---

## PILLAR 4: MENTAL HEALTH & EMOTIONAL CARE

| Question ID | Brief Description | Red Flag (0-3) | Yellow (4-6) | Green (7-10) | Clinical Significance |
|------------|-------------------|----------------|--------------|--------------|----------------------|
| **EMOT_Q01** 🔴 | Recent mood | Very depressed | Neutral | Very positive | Depression screen (PHQ-2 element) |
| **EMOT_Q02** 🔴 | Anxiety (⚠️) | Extremely anxious | Sometimes | Rarely | GAD screen (GAD-2 element) |
| **EMOT_Q03** | Positive emotions | Never | Sometimes | Daily | Positive affect, quality of life |
| **EMOT_Q04** | Emotional stability | Very unstable | Somewhat | Very stable | Mood regulation, psychiatric risk |
| **EMOT_Q05** | Emotion awareness | No awareness | Sometimes | Excellent | Emotional intelligence |
| **EMOT_Q06** | Managing emotions | Cannot manage | Sometimes | Very effective | Coping skills, emotional regulation |
| **EMOT_Q07** 🟠 | Self-worth | Very low | Neutral | Very high | Self-esteem, depression factor |
| **EMOT_Q08** | Self-kindness | Very self-critical | Sometimes kind | Very kind | Self-compassion, resilience |
| **EMOT_Q09** 🟠 | Life satisfaction | Very unsatisfied | Somewhat | Very satisfied | Quality of life, wellbeing |
| **EMOT_Q10** 🔴 | Sense of purpose | No purpose | Some | Strong | Existential wellbeing, depression/suicide risk |
| **EMOT_Q11** | Resilience | Cannot recover | Eventually | Quick recovery | Adaptive capacity |
| **EMOT_Q12** | Mental focus | Cannot focus | Somewhat | Excellent | Executive function, ADHD screen |
| **EMOT_Q13** | Mental clarity | Very foggy | Somewhat clear | Very clear | Cognitive function, brain fog |
| **EMOT_Q14** | Expressing emotions | Unable | Sometimes | Very comfortable | Emotional expression, relationships |
| **EMOT_Q15** 🔴 | Hope for future | Hopeless | Somewhat | Very hopeful | Suicidality risk factor |
| **EMOT_Q16** | Adapt to change | Very poorly | Manage | Very well | Psychological flexibility |
| **EMOT_Q17** | Seeking help | Never | Sometimes | Comfortable | Help-seeking behavior |
| **EMOT_Q18** | Mental health support | Never | Occasionally | Regularly | Treatment engagement |

---

## PILLAR 5: ENVIRONMENT

| Question ID | Brief Description | Red Flag (0-3) | Yellow (4-6) | Green (7-10) | Clinical Significance |
|------------|-------------------|----------------|--------------|--------------|----------------------|
| **ENVIR_Q01** 🔴 | Social connection | Very isolated | Somewhat | Very connected | Social isolation = mortality risk |
| **ENVIR_Q02** 🔴 | Feeling safe | Very unsafe | Somewhat | Very safe | Safety, trauma, stress |
| **ENVIR_Q03** 🔴 | Housing stability | Very unstable | Somewhat | Very stable | Social determinant, health equity |
| **ENVIR_Q04** 🟠 | Social support | No support | Some | Very strong | Protective factor for all health outcomes |
| **ENVIR_Q05** | Relationship quality | Very unsatisfied | Somewhat | Very satisfied | Relational wellbeing |
| **ENVIR_Q06** | Social contact frequency | Rarely | Few times/week | Daily | Loneliness prevention |
| **ENVIR_Q07** 🔴 | Loneliness (⚠️) | All the time | Sometimes | Rarely | Independent health risk (inflammation) |
| **ENVIR_Q08** | Air quality | Very poor | Okay | Excellent | Respiratory, cardiovascular impact |
| **ENVIR_Q09** | Living environment | Very poor | Okay | Excellent | Environmental health |
| **ENVIR_Q10** | Access to nature | No access | Some | Excellent | Mental health, physical activity |
| **ENVIR_Q11** 🔴 | Financial stress | Very insecure | Somewhat | Very secure | Social determinant, chronic stress |
| **ENVIR_Q12** | Community involvement | Not involved | Somewhat | Very active | Social capital, belonging |
| **ENVIR_Q13** | Sense of belonging | No belonging | Some | Strong | Psychological safety, identity |
| **ENVIR_Q14** 🔴 | Tobacco exposure (⚠️) | Daily | Occasional | Never | Lung/CV disease, cancer |
| **ENVIR_Q15** 🔴 | Drug use (⚠️) | Regular | Occasional | Never | Substance use disorder, safety |
| **ENVIR_Q16** 🟠 | Healthcare access | Very difficult | Somewhat | Very easy | Health equity, preventive care |

---

# SECTION 2: RISK STRATIFICATION SYSTEM

## Risk Flag Definitions

- **🔴 High-Impact Risk Item**: Scores <4 require immediate clinical discussion
- **🟠 Moderate-Risk Item**: Scores <4 warrant intervention planning
- *(No flag)* = Important for comprehensive assessment, lower clinical urgency

## High-Impact Risk Items (🔴) - Top Priority

**These questions, when scored <4, indicate significant clinical risk:**

| Question | Risk Domain | Why High-Impact |
|----------|-------------|-----------------|
| NUTR_Q09 | Processed foods | Strong obesity/metabolic disease predictor |
| NUTR_Q10 | Sugary foods | Diabetes, inflammation, dental disease |
| NUTR_Q15 | Alcohol | Liver disease, cancer, addiction, accidents |
| MOVE_Q03 | Aerobic activity | All-cause mortality, CVD risk |
| MOVE_Q08 | Sitting time | Independent mortality risk |
| SLEEP_Q03 | Stress level | Allostatic load, immune suppression |
| SLEEP_Q04 | Sleep duration | CVD, metabolic, neurodegenerative risk |
| SLEEP_Q08 | Stress management | Chronic inflammation, mental health |
| SLEEP_Q12 | Daytime sleepiness | OSA, safety (driving), chronic illness |
| EMOT_Q01 | Mood/depression | Suicide risk, treatment needed |
| EMOT_Q02 | Anxiety | Panic disorder, GAD, treatment needed |
| EMOT_Q10 | Sense of purpose | Existential crisis, suicide risk |
| EMOT_Q15 | Hopelessness | Suicide risk factor |
| ENVIR_Q01 | Social isolation | Mortality equivalent to smoking |
| ENVIR_Q02 | Safety | Domestic violence, trauma, PTSD |
| ENVIR_Q03 | Housing instability | Social determinant, health equity |
| ENVIR_Q07 | Loneliness | Inflammation, cognitive decline |
| ENVIR_Q11 | Financial stress | Chronic stress, social determinant |
| ENVIR_Q14 | Tobacco | Lung/CV disease, cancer |
| ENVIR_Q15 | Drug use | Addiction, overdose, safety |

**Total High-Impact Items: 20**

---

# SECTION 3: OPTIONAL CLINICAL FOLLOW-UP TRIGGERS

These are **automated clinical decision support suggestions** that can be implemented in digital systems or used as clinician prompts.

## Nutrition Triggers

| Score Condition | Suggested Action |
|-----------------|------------------|
| NUTR_Q01 < 4 | Nutrition counseling referral |
| NUTR_Q09 > 6 (high processed food) | Meal planning support, education on whole foods |
| NUTR_Q10 > 6 (high sugar) | Diabetes screen (HbA1c), nutrition education |
| NUTR_Q15 > 6 (high alcohol) | AUDIT-C screening, liver function tests, addiction assessment |
| NUTR_Q17 < 4 | Social work referral for food insecurity |

## Movement Triggers

| Score Condition | Suggested Action |
|-----------------|------------------|
| MOVE_Q01 < 4 and MOVE_Q03 < 4 | Exercise prescription, physical therapy evaluation |
| MOVE_Q05 < 4 | Strength training education, PT referral for sarcopenia risk |
| MOVE_Q08 > 6 (high sitting) | Workstation assessment, movement breaks education |
| MOVE_Q12 < 4 | Fall risk assessment (if age >65) |
| MOVE_Q15 < 4 | Cardiopulmonary exercise testing consideration |

## Sleep & Recovery Triggers

| Score Condition | Suggested Action |
|-----------------|------------------|
| SLEEP_Q04 < 4 | Sleep hygiene education, rule out OSA/insomnia |
| SLEEP_Q12 > 6 (⚠️ = high sleepiness) | **STOP-BANG questionnaire**, consider sleep study referral |
| SLEEP_Q03 < 4 or SLEEP_Q08 < 4 | Stress management program, mindfulness referral, rule out burnout |
| SLEEP_Q06 < 4 | Evaluate for sleep apnea, periodic limb movements |
| SLEEP_Q01 < 4 AND SLEEP_Q04 < 4 | Sleep medicine referral |

## Mental Health Triggers

| Score Condition | Suggested Action |
|-----------------|------------------|
| EMOT_Q01 < 4 OR EMOT_Q02 > 6 (⚠️) | **PHQ-9 or GAD-7 full screening**, mental health referral |
| EMOT_Q10 < 3 OR EMOT_Q15 < 3 | **Suicide risk assessment (Columbia scale)**, urgent psychiatric consultation |
| EMOT_Q01 < 4 for 2 consecutive assessments | Depression treatment  (therapy, medication, psychiatric referral) |
| EMOT_Q12 < 4 AND Age <40 | Consider ADHD evaluation |
| EMOT_Q17 < 4 AND (EMOT_Q01 <4 OR EMOT_Q02 >6) | Motivational interviewing for treatment engagement |

## Environment Triggers

| Score Condition | Suggested Action |
|-----------------|------------------|
| ENVIR_Q01 < 4 OR ENVIR_Q07 > 6 (⚠️ lonely) | Screen for depression, social work referral, community programs |
| ENVIR_Q02 < 4 | **Safety assessment**, domestic violence screen, trauma-informed care |
| ENVIR_Q03 < 4 OR ENVIR_Q11 < 4 | Social work referral for housing/financial support |
| ENVIR_Q14 > 6 (⚠️ tobacco) | Tobacco cessation counseling, pharmacotherapy |
| ENVIR_Q15 > 4 (⚠️ drugs) | Substance use disorder assessment (DAST-10), addiction medicine referral |
| ENVIR_Q16 < 4 | Patient navigator, transportation assistance, telemedicine options |

---

# SECTION 4: SYSTEM MAPPING TO COMPASS FRAMEWORK

## How Lifestyle Questions Map to 8-Organ Systems

This table shows **primary** and **secondary** organ system impacts for each lifestyle pillar.

### Nutrition Questions → Organ Systems

| Question | Primary System | Secondary Systems | Clinical Rationale |
|----------|----------------|-------------------|---------------------|
| NUTR_Q01-Q06, Q11 | **Metabolic** | Cardiovascular, Renal | Diet quality → glucose, lipids, inflammation |
| NUTR_Q03, Q04 | **Cardiovascular** | Metabolic, Immune | Fruits/vegetables → endothelial function, BP |
| NUTR_Q05 | **Musculoskeletal** | Metabolic | Protein → muscle maintenance, sarcopenia |
| NUTR_Q07-Q12 | **Metabolic** | Neurological | Portion control, mindful eating → weight, dopamine regulation |
| NUTR_Q09, Q10 | **Metabolic** | Cardiovascular, Immune | Processed/sugar → metabolic syndrome, inflammation |
| NUTR_Q15 (alcohol) | **Metabolic** | Neurological, Cardiovascular | Liver damage, brain, CVD risk |
| NUTR_Q02, Q17 (water, access) | **Renal** | Metabolic | Hydration → kidney function, electrolytes |

### Movement Questions → Organ Systems

| Question | Primary System | Secondary Systems | Clinical Rationale |
|----------|----------------|-------------------|---------------------|
| MOVE_Q01, Q03, Q04 | **Cardiovascular** | Metabolic, Respiratory | Aerobic activity → VO2max, cardiac output |
| MOVE_Q05, Q06, Q13 | **Musculoskeletal** | Metabolic, Neurological | Strength → muscle mass, bone density, fall risk |
| MOVE_Q09, Q12 | **Neurological** | Musculoskeletal | Balance → proprioception, fall prevention |
| MOVE_Q07, Q08, Q09, Q10 | **Metabolic** | Cardiovascular | NEAT, sedentary → insulin sensitivity, energy expenditure |
| MOVE_Q15 | **Respiratory** | Cardiovascular | Cardiorespiratory fitness → lung capacity |
| MOVE_Q16 | **Musculoskeletal** | Neurological | Joint health → mobility, pain, function |

### Sleep & Recovery Questions → Organ Systems

| Question | Primary System | Secondary Systems | Clinical Rationale |
|----------|----------------|-------------------|---------------------|
| SLEEP_Q01, Q04-Q07 | **Neurological** | Cardiovascular, Metabolic, Immune | Sleep → brain clearance, memory, hormone regulation |
| SLEEP_Q12 (daytime sleepiness) | **Respiratory** | Neurological, Cardiovascular | OSA screen → hypoxia, CVD risk |
| SLEEP_Q03, Q08-Q11 | **Neurological** | Immune, Cardiovascular | Stress → HPA axis, cortisol, inflammation |
| SLEEP_Q02, Q13 | **Immune** | Neurological, Metabolic | Recovery → immune function, tissue repair |

### Mental Health Questions → Organ Systems

| Question | Primary System | Secondary Systems | Clinical Rationale |
|----------|----------------|-------------------|---------------------|
| EMOT_Q01-Q18 (all) | **Neurological** | Cardiovascular, Immune | Mental health → brain chemistry, inflammation, autonomic tone |
| EMOT_Q01, Q02, Q10, Q15 | **Neurological** | Cardiovascular | Depression/anxiety → cortisol, catecholamines, CVD risk |

### Environment Questions → Organ Systems

| Question | Primary System | Secondary Systems | Clinical Rationale |
|----------|----------------|-------------------|---------------------|
| ENVIR_Q01, Q04-Q07 | **Neurological** | Immune, Cardiovascular | Social connection → stress buffering, inflammation |
| ENVIR_Q08, Q09 | **Respiratory** | Immune, Cardiovascular | Air quality → lung function, systemic inflammation |
| ENVIR_Q14 (tobacco) | **Respiratory** | Cardiovascular, Immune | Smoking → COPD, CAD, cancer |
| ENVIR_Q11, Q16 | **All Systems** | N/A | Social determinants → access to care, chronic stress |
| ENVIR_Q02, Q03 | **Neurological** | All Systems | Safety/housing → chronic stress → systemic impact |

---

# SECTION 5: IMPLEMENTATION METADATA (For Developers)

## Complete Metadata Table

This table contains all technical specifications needed for digital implementation.

```csv
QuestionID,Pillar,PillarCode,Subdomain,SubdomainCode,Frequency,FrequencyCode,ReverseScored,RiskFlag,Weight,QuestionIntent,ClinicalTriggerThreshold,SuggestedFollowUp,PrimarySystem,SecondarySystem1,SecondarySystem2
NUTR_Q01,Nutrition,NUTR,Diet Quality,QUAL,Every Visit,EV,No,Moderate,1.5,Overall diet quality assessment for baseline,<4,Nutrition counseling referral,Metabolic,Cardiovascular,Immune
NUTR_Q02,Nutrition,NUTR,Hydration,HYDR,Every Visit,EV,No,None,1.0,Daily water intake adequacy,<4,Hydration education,Renal,Metabolic,
NUTR_Q03,Nutrition,NUTR,Vegetables,VEG,Quarterly,Q,No,Moderate,1.5,Vegetable consumption frequency,<4,Meal planning support,Cardiovascular,Metabolic,Immune
NUTR_Q04,Nutrition,NUTR,Fruits,FRUIT,Quarterly,Q,No,None,1.0,Fruit consumption frequency,<4,Nutrition education,Cardiovascular,Metabolic,Immune
NUTR_Q05,Nutrition,NUTR,Protein,PROT,Quarterly,Q,No,None,1.0,Adequate protein intake,<4,Protein education,Musculoskeletal,Metabolic,
NUTR_Q06,Nutrition,NUTR,Healthy Fats,FAT,Quarterly,Q,No,None,1.0,Healthy fat sources,<4,Fat education,Cardiovascular,Metabolic,Neurological
NUTR_Q07,Nutrition,NUTR,Portion Control,PORT,Quarterly,Q,No,None,1.0,Portion size control,<4,Weight management,Metabolic,Cardiovascular,
NUTR_Q08,Nutrition,NUTR,Mindful Eating,MIND,Quarterly,Q,No,None,1.0,Eating awareness and attention,<4,Mindful eating education,Metabolic,Neurological,
NUTR_Q09,Nutrition,NUTR,Processed Foods,PROC,Quarterly,Q,Yes,High,2.0,Ultra-processed food consumption,>6 (after flip <4),Nutrition counseling,Metabolic,Cardiovascular,Immune
NUTR_Q10,Nutrition,NUTR,Sugar,SUGAR,Quarterly,Q,Yes,High,2.0,Added sugar intake,>6 (after flip <4),Diabetes screen,Metabolic,Cardiovascular,
NUTR_Q11,Nutrition,NUTR,Whole Grains,GRAIN,Quarterly,Q,No,None,1.0,Complex carbohydrate choices,<4,Carb education,Metabolic,Cardiovascular,
NUTR_Q12,Nutrition,NUTR,Hunger Cues,CUES,Quarterly,Q,No,None,1.0,Interoceptive awareness,<4,Intuitive eating education,Neurological,Metabolic,
NUTR_Q13,Nutrition,NUTR,Meal Planning,PLAN,Semi-Annual,SA,No,None,1.0,Advance meal preparation,<4,Meal planning resources,Metabolic,,,
NUTR_Q14,Nutrition,NUTR,Cooking,COOK,Semi-Annual,SA,No,None,1.0,Home cooking frequency,<4,Cooking classes,Metabolic,,,
NUTR_Q15,Nutrition,NUTR,Alcohol,ALCO,Semi-Annual,SA,Yes,High,2.0,Alcohol consumption,>6 (after flip <4),AUDIT-C / addiction eval,Metabolic,Neurological,Cardiovascular
NUTR_Q16,Nutrition,NUTR,Variety,VAR,Annual,A,No,None,1.0,Dietary diversity,<4,Nutrition variety education,Metabolic,Immune,
NUTR_Q17,Nutrition,NUTR,Food Access,ACC,Annual,A,No,None,1.0,Food security,<4,Social work referral,All Systems,,,
MOVE_Q01,Movement,MOVE,Activity Status,STAT,Every Visit,EV,No,Moderate,1.5,Current physical activity level,<4,Exercise prescription,Cardiovascular,Metabolic,
MOVE_Q02,Movement,MOVE,Fitness Status,FIT,Every Visit,EV,No,None,1.0,Perceived fitness and strength,<4,Fitness assessment,Musculoskeletal,Cardiovascular,
MOVE_Q03,Movement,MOVE,Aerobic Moderate,AERO_MOD,Quarterly,Q,No,High,2.0,Moderate-intensity aerobic activity,<4,Exercise prescription,Cardiovascular,Respiratory,Metabolic
MOVE_Q04,Movement,MOVE,Aerobic Vigorous,AERO_VIG,Quarterly,Q,No,None,1.0,Vigorous aerobic activity,<4,Exercise consultation,Cardiovascular,Respiratory,
MOVE_Q05,Movement,MOVE,Strength Training,STR,Quarterly,Q,No,Moderate,1.5,Resistance training frequency,<4,Strength training education,Musculoskeletal,Metabolic,
MOVE_Q06,Movement,MOVE,Flexibility,FLEX,Quarterly,Q,No,None,1.0,Stretching and flexibility,<4,Flexibility program,Musculoskeletal,Neurological,
MOVE_Q07,Movement,MOVE,NEAT,NEAT,Quarterly,Q,No,None,1.0,Non-exercise activity,<4,Activity counseling,Metabolic,Cardiovascular,
MOVE_Q08,Movement,MOVE,Sitting Time,SIT,Quarterly,Q,Yes,High,2.0,Daily sedentary time,>6 (after flip <4),Workstation assessment,Cardiovascular,Metabolic,
MOVE_Q09,Movement,MOVE,Screen Time,SCREEN,Quarterly,Q,Yes,Moderate,1.5,Leisure screen time,>6 (after flip <4),Screen time reduction,Neurological,Metabolic,
MOVE_Q10,Movement,MOVE,Movement Breaks,BREAK,Quarterly,Q,No,None,1.0,Interrupting sitting,<4,Movement break education,Metabolic,Cardiovascular,
MOVE_Q11,Movement,MOVE,Consistency,CONS,Quarterly,Q,No,None,1.0,Exercise adherence,<4,Adherence strategies,All Systems,,,
MOVE_Q12,Movement,MOVE,Balance,BAL,Semi-Annual,SA,No,None,1.0,Balance training,<4,Fall risk assessment (if >65),Neurological,Musculoskeletal,
MOVE_Q13,Movement,MOVE,Full Body Strength,STR_FULL,Semi-Annual,SA,No,None,1.0,Comprehensive strength program,<4,PT referral,Musculoskeletal,,,
MOVE_Q14,Movement,MOVE,Occupational Activity,OCC,Semi-Annual,SA,No,None,1.0,Work-related physical activity,N/A,N/A,Musculoskeletal,Cardiovascular,
MOVE_Q15,Movement,MOVE,Endurance,END,Annual,A,No,None,1.0,Cardiovascular endurance,<4,Cardiopulmonary testing,Cardiovascular,Respiratory,
MOVE_Q16,Movement,MOVE,Joint Health,JOINT,Annual,A,No,None,1.0,Overall joint mobility,<4,Rheumatology/PT,Musculoskeletal,,,
SLEEP_Q01,Sleep & Recovery,SLEEP,Sleep Quality,QUAL,Every Visit,EV,No,Moderate,1.5,Overall sleep quality,<4,Sleep evaluation,Neurological,Cardiovascular,Immune
SLEEP_Q02,Sleep & Recovery,SLEEP,Energy,ENRG,Every Visit,EV,No,Moderate,1.5,Daytime energy level,<4,Fatigue workup,Neurological,Immune,Metabolic
SLEEP_Q03,Sleep & Recovery,SLEEP,Stress Level,STRESS,Every Visit,EV,No,High,2.0,Current perceived stress,<4,Stress management,Neurological,Cardiovascular,Immune
SLEEP_Q04,Sleep & Recovery,SLEEP,Duration,DUR,Quarterly,Q,No,High,2.0,Sleep hours per night,<4,Sleep hygiene / OSA screen,Neurological,Cardiovascular,Metabolic
SLEEP_Q05,Sleep & Recovery,SLEEP,Sleep Onset,ONSET,Quarterly,Q,No,None,1.0,Ease of falling asleep,<4,Insomnia evaluation,Neurological,,,
SLEEP_Q06,Sleep & Recovery,SLEEP,Sleep Continuity,CONT,Quarterly,Q,No,None,1.0,Sleeping through night,<4,OSA / nocturia evaluation,Neurological,Respiratory,Renal
SLEEP_Q07,Sleep & Recovery,SLEEP,Morning Refresh,REFRESH,Quarterly,Q,No,None,1.0,Waking refreshed,<4,Sleep disorder screen,Neurological,,,
SLEEP_Q08,Sleep & Recovery,SLEEP,Stress Management,STRESS_MGT,Quarterly,Q,No,High,2.0,Stress coping effectiveness,<4,Stress program / therapy,Neurological,Cardiovascular,Immune
SLEEP_Q09,Sleep & Recovery,SLEEP,Relaxation,RELAX,Quarterly,Q,No,None,1.0,Relaxation practice frequency,<4,Mindfulness program,Neurological,Immune,
SLEEP_Q10,Sleep & Recovery,SLEEP,Work-Life Balance,BALANCE,Quarterly,Q,No,None,1.0,Balance work and personal,<4,Burnout assessment,Neurological,,,
SLEEP_Q11,Sleep & Recovery,SLEEP,Downtime,DOWN,Quarterly,Q,No,None,1.0,Unstructured rest time,<4,Rest education,Neurological,Immune,
SLEEP_Q12,Sleep & Recovery,SLEEP,Daytime Sleepiness,SLEEPY,Quarterly,Q,Yes,High,2.0,Excessive daytime sleepiness,>6 (after flip <4),STOP-BANG / sleep study,Respiratory,Neurological,Cardiovascular
SLEEP_Q13,Sleep & Recovery,SLEEP,Overall Recovery,RECOV,Quarterly,Q,No,None,1.0,General recovery status,<4,Recovery optimization,Immune,Neurological,
SLEEP_Q14,Sleep & Recovery,SLEEP,Schedule,SCHED,Semi-Annual,SA,No,None,1.0,Sleep schedule consistency,<4,Circadian education,Neurological,,,
SLEEP_Q15,Sleep & Recovery,SLEEP,Environment,ENV,Semi-Annual,SA,No,None,1.0,Bedroom optimization,<4,Sleep hygiene,Neurological,,,
SLEEP_Q16,Sleep & Recovery,SLEEP,Screen Before Bed,SCREEN_BED,Semi-Annual,SA,Yes,Moderate,1.5,Screen use before sleep,>6 (after flip <4),Blue light education,Neurological,,,
SLEEP_Q17,Sleep & Recovery,SLEEP,Recovery Days,RECOV_DAY,Annual,A,No,None,1.0,Physical recovery from exercise,<4,Athlete education,Musculoskeletal,,,
SLEEP_Q18,Sleep & Recovery,SLEEP,Caffeine,CAFF,Annual,A,No,None,1.0,Caffeine timing,<4,Caffeine education,Neurological,,,
EMOT_Q01,Mental Health,EMOT,Mood,MOOD,Every Visit,EV,No,High,2.0,Overall mood state,<4,PHQ-9 screening,Neurological,Cardiovascular,Immune
EMOT_Q02,Mental Health,EMOT,Anxiety,ANX,Every Visit,EV,Yes,High,2.0,Anxiety level,>6 (after flip <4),GAD-7 screening,Neurological,Cardiovascular,Immune
EMOT_Q03,Mental Health,EMOT,Positive Emotions,POS,Quarterly,Q,No,None,1.0,Positive affect frequency,<4,Positive psychology,Neurological,,,
EMOT_Q04,Mental Health,EMOT,Emotional Stability,STAB,Quarterly,Q,No,None,1.0,Mood stability,<4,Mood disorder evaluation,Neurological,,,
EMOT_Q05,Mental Health,EMOT,Emotion Awareness,AWARE,Quarterly,Q,No,None,1.0,Emotional intelligence,<4,Emotional literacy,Neurological,,,
EMOT_Q06,Mental Health,EMOT,Emotion Regulation,REG,Quarterly,Q,No,None,1.0,Managing difficult emotions,<4,DBT / CBT referral,Neurological,,,
EMOT_Q07,Mental Health,EMOT,Self-Worth,WORTH,Quarterly,Q,No,Moderate,1.5,Self-esteem level,<4,Therapy / self-esteem work,Neurological,,,
EMOT_Q08,Mental Health,EMOT,Self-Compassion,COMP,Quarterly,Q,No,None,1.0,Kindness to self,<4,Self-compassion training,Neurological,,,
EMOT_Q09,Mental Health,EMOT,Life Satisfaction,SAT,Quarterly,Q,No,Moderate,1.5,Overall life satisfaction,<4,Life coaching / therapy,Neurological,,,
EMOT_Q10,Mental Health,EMOT,Purpose,PURP,Quarterly,Q,No,High,2.0,Sense of meaning,<3,Suicide risk assessment,Neurological,,,
EMOT_Q11,Mental Health,EMOT,Resilience,RESIL,Quarterly,Q,No,None,1.0,Bounce back from adversity,<4,Resilience training,Neurological,,,
EMOT_Q12,Mental Health,EMOT,Focus,FOCUS,Quarterly,Q,No,None,1.0,Concentration ability,<4,ADHD evaluation (if <40),Neurological,,,
EMOT_Q13,Mental Health,EMOT,Mental Clarity,CLARITY,Quarterly,Q,No,None,1.0,Cognitive clarity,<4,Brain fog workup,Neurological,Metabolic,
EMOT_Q14,Mental Health,EMOT,Expression,EXPRESS,Semi-Annual,SA,No,None,1.0,Expressing emotions,<4,Communication skills,Neurological,,,
EMOT_Q15,Mental Health,EMOT,Hope,HOPE,Semi-Annual,SA,No,High,2.0,Hopefulness about future,<3,Suicide risk assessment,Neurological,,,
EMOT_Q16,Mental Health,EMOT,Adaptability,ADAPT,Semi-Annual,SA,No,None,1.0,Adapting to change,<4,Flexibility training,Neurological,,,
EMOT_Q17,Mental Health,EMOT,Help-Seeking,HELP,Annual,A,No,None,1.0,Comfort seeking support,<4,Motivational interviewing,Neurological,,,
EMOT_Q18,Mental Health,EMOT,Mental Health Support,SUPPORT,Annual,A,No,None,1.0,Use of MH resources,<4,Treatment engagement,Neurological,,,
ENVIR_Q01,Environment,ENVIR,Social Connection,CONN,Every Visit,EV,No,High,2.0,Feeling connected to others,<4,Social isolation screen,Neurological,Cardiovascular,Immune
ENVIR_Q02,Environment,ENVIR,Safety,SAFETY,Every Visit,EV,No,High,2.0,Feeling safe at home,<4,Safety assessment / DV screen,Neurological,All Systems,
ENVIR_Q03,Environment,ENVIR,Housing Stability,HOUSING,Every Visit,EV,No,High,2.0,Housing security,<4,Social work / housing assist,All Systems,,,
ENVIR_Q04,Environment,ENVIR,Social Support,SUPPORT,Quarterly,Q,No,Moderate,1.5,Strength of support network,<4,Support group / therapy,Neurological,Immune,
ENVIR_Q05,Environment,ENVIR,Relationship Quality,REL_QUAL,Quarterly,Q,No,None,1.0,Satisfaction with relationships,<4,Couples / family therapy,Neurological,,,
ENVIR_Q06,Environment,ENVIR,Social Contact,CONTACT,Quarterly,Q,No,None,1.0,Frequency of social interaction,<4,Social engagement,Neurological,,,
ENVIR_Q07,Environment,ENVIR,Loneliness,LONELY,Quarterly,Q,Yes,High,2.0,Loneliness feelings,>6 (after flip <4),Depression screen / social work,Neurological,Cardiovascular,Immune
ENVIR_Q08,Environment,ENVIR,Air Quality,AIR,Quarterly,Q,No,None,1.0,Environmental air quality,<4,Environmental assessment,Respiratory,Cardiovascular,Immune
ENVIR_Q09,Environment,ENVIR,Living Environment,LIVE,Quarterly,Q,No,None,1.0,Home environment quality,<4,Housing assessment,Respiratory,Immune,
ENVIR_Q10,Environment,ENVIR,Nature Access,NATURE,Quarterly,Q,No,None,1.0,Access to green spaces,<4,Activity recommendations,Neurological,,,
ENVIR_Q11,Environment,ENVIR,Financial Stress,FIN,Quarterly,Q,No,High,2.0,Financial security,<4,Financial counseling / social work,All Systems,,,
ENVIR_Q12,Environment,ENVIR,Community Involvement,COMMUNITY,Semi-Annual,SA,No,None,1.0,Community participation,<4,Community resources,Neurological,,,
ENVIR_Q13,Environment,ENVIR,Belonging,BELONG,Semi-Annual,SA,No,None,1.0,Sense of belonging,<4,Support groups,Neurological,,,
ENVIR_Q14,Environment,ENVIR,Tobacco,TOBACCO,Semi-Annual,SA,Yes,High,2.0,Tobacco smoke exposure,>6 (after flip <4),Tobacco cessation,Respiratory,Cardiovascular,Immune
ENVIR_Q15,Environment,ENVIR,Drug Use,DRUGS,Annual,A,Yes,High,2.0,Recreational drug use,>4 (after flip <6),DAST-10 / addiction medicine,Neurological,All Systems,
ENVIR_Q16,Environment,ENVIR,Healthcare Access,HC_ACCESS,Annual,A,No,Moderate,1.5,Ease of accessing healthcare,<4,Patient navigator,All Systems,,,
```

---

# SECTION 6: IMPLEMENTATION NOTES

## Reverse-Scored Question Handling

⚠️ **CRITICAL**: All questions marked with ⚠️ in the questionnaire require reverse scoring.

**Formula:**
```
Adjusted Score = 10 - Raw Patient Response  
```

**Reverse-Scored Questions** (17 total):
- NUTR_Q09, NUTR_Q10, NUTR_Q15
- MOVE_Q08, MOVE_Q09
- SLEEP_Q12, SLEEP_Q16
- EMOT_Q02
- ENVIR_Q07, ENVIR_Q14, ENVIR_Q15

**Implementation Check:**
After flipping, higher scores should always = better health.

---

## Weighting System (Optional)

Default = equal weighting (all questions weight = 1.0)

**Risk-Weighted Option:**
- High-impact (🔴) questions: weight = 2.0
- Moderate-risk (🟠) questions: weight = 1.5
- Standard questions: weight = 1.0

This can be toggled on/off in the system.

---

## Pillar Score Calculation Algorithm

```python
def calculate_pillar_score(responses, question_metadata):
    total_weighted_score = 0
    total_weight = 0
    
    for question_id, raw_score in responses.items():
        # Get metadata
        is_reverse_scored = question_metadata[question_id]['reverse_scored']
        weight = question_metadata[question_id]['weight']
        
        # Adjust for reverse scoring
        if is_reverse_scored:
            adjusted_score = 10 - raw_score
        else:
            adjusted_score = raw_score
        
        # Apply weighting
        total_weighted_score += (adjusted_score * weight)
        total_weight += weight
    
    # Calculate weighted average
    pillar_score = total_weighted_score / total_weight
    
    return round(pillar_score, 1)  # Return 0-10 scale
```

---

## Alert System Logic

```python
def generate_alerts(question_scores, metadata):
    critical_alerts = []
    high_priority_alerts = []
    moderate_alerts = []
    
    for question_id, score in question_scores.items():
        risk_flag = metadata[question_id]['risk_flag']
        trigger_threshold = metadata[question_id]['trigger_threshold']
        
        # Check if scorebelow threshold
        if score < trigger_threshold:
            alert = {
                'question_id': question_id,
                'score': score,
                'follow_up': metadata[question_id]['suggested_followup']
            }
            
            if risk_flag == 'High':
                critical_alerts.append(alert)
            elif risk_flag == 'Moderate':
                high_priority_alerts.append(alert)
            else:
                moderate_alerts.append(alert)
    
    return {
        'critical': critical_alerts,
        'high_priority': high_priority_alerts,
        'moderate': moderate_alerts
    }
```

---

**Document Status:** ✅ Complete - Implementation Ready
**Companion to:** LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.md
**Use Cases:** Clinical interpretation, risk stratification, digital implementation, Compass framework integration

