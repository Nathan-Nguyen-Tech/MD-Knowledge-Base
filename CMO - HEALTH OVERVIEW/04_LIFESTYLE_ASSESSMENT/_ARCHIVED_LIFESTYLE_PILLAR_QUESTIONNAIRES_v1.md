# ⚠️ ARCHIVED - Lifestyle Pillar Assessment Questionnaires v1.0

**ARCHIVE NOTICE:** This document has been superseded by v2.0. Do not use for new implementations.

**Document Version:** 1.0 (ARCHIVED)
**Last Updated:** 2025-11-20
**Archived Date:** 2025-11-24
**Superseded By:** LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.md

**Original Purpose:** Comprehensive lifestyle assessment questionnaires across 5 pillars for patient self-reflection and clinical care planning

**Why Archived:**
- v2.0 reduces redundancy (100 → 85 questions)
- v2.0 uses patient-friendly language instead of medical jargon
- v2.0 implements frequency tiers (Every Visit, Quarterly, Semi-Annual, Annual)
- v2.0 embeds education within questions

---

## Document Overview

This document contains detailed questionnaires for assessing the **5 Lifestyle Pillars** that contribute to overall health and wellbeing. Each question represents a discrete **parameter** that can be tracked longitudinally to monitor lifestyle changes over time.

### Assessment Structure

**5 Lifestyle Pillars:**
1. **Nutrition** - Dietary quality, eating behaviors, and nutritional patterns
2. **Movement** - Physical activity, exercise, and non-exercise activity thermogenesis (NEAT)
3. **Sleep & Recovery** - Sleep quality, stress management, and recovery practices
4. **Mental Health & Emotional Care** - Emotional wellbeing, psychological health, and emotional regulation
5. **Environment** - Social connections, community, physical environment, and substance exposure

### Scoring Methodology

- **Individual Questions:** 0-10 Likert scale
- **Composite Pillar Score:** Average of all questions within that pillar (0-10)
- **Dashboard Integration:** Pillar scores × 10 = 0-100 points for Coxcomb chart
- **Assessment Frequency:** Quarterly (or as clinically indicated)

### Likert Scale Framework

**0-10 Scale Interpretation (Positive Behaviors):**
- **0-1:** Never / Not at all
- **2-3:** Rarely / Minimal
- **4-5:** Sometimes / Moderate
- **6-7:** Often / Frequently
- **8-9:** Very Often / Nearly Always
- **10:** Always / Completely

**Note:** For negative behaviors (marked with ⚠️), scoring is reversed:
- **10:** Never engage in this negative behavior
- **0:** Always engage in this negative behavior

---

## PILLAR 1: NUTRITION ASSESSMENT

**Composite Parameter:** LIFE_001 - Nutrition Score (0-10)
**Number of Questions:** 20 parameters
**Assessment Domains:** Dietary quality, portion control, eating behaviors, macronutrient balance, hydration, mindfulness

### Nutrition Parameters

#### 1.1 Dietary Quality & Variety

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_001 | **Whole Foods Consumption**: How often do you eat whole, minimally processed foods (fresh fruits, vegetables, whole grains, lean proteins)? | 0 = Never → 10 = Every meal |
| NUTR_002 | **Vegetable Intake**: How often do you include vegetables in your meals (lunch and dinner)? | 0 = Never → 10 = Always 2+ servings per meal |
| NUTR_003 | **Fruit Intake**: How often do you consume fresh fruit daily? | 0 = Never → 10 = 3+ servings daily |
| NUTR_004 | **Dietary Variety**: How varied is your diet (different types of foods across food groups each week)? | 0 = Very limited → 10 = Highly varied |

#### 1.2 Macronutrient Balance

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_005 | **Healthy Protein Intake**: How often do you consume adequate protein (lean meats, fish, eggs, legumes, tofu)? | 0 = Rarely/Never → 10 = Every day, every meal |
| NUTR_006 | **Healthy Fat Intake**: How often do you include healthy fats (avocados, nuts, seeds, olive oil, fatty fish) in your diet? | 0 = Never → 10 = Daily |
| NUTR_007 | **Complex Carbohydrates**: How often do you choose complex carbohydrates (whole grains, legumes, vegetables) over simple/refined carbs? | 0 = Never → 10 = Always |
| NUTR_008 | **Fiber Intake**: How adequate is your daily fiber intake from fruits, vegetables, and whole grains? | 0 = Very low → 10 = Excellent (25-35g daily) |

#### 1.3 Portion Control & Eating Behaviors

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_009 | **Portion Control**: How well do you control your portion sizes to match your body's energy needs? | 0 = No control, frequent overeating → 10 = Excellent control |
| NUTR_010 | **Mindful Eating**: How often do you eat slowly and pay attention to your food (vs. eating while distracted)? | 0 = Always distracted → 10 = Always mindful |
| NUTR_011 | **Hunger Cues**: How well do you recognize and respond to your body's hunger and fullness cues? | 0 = Cannot recognize → 10 = Excellent awareness |
| NUTR_012 | **Meal Regularity**: How consistent are your meal times each day? | 0 = Very irregular → 10 = Very consistent |

#### 1.4 Nutritional Restraint & Avoidance

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_013 ⚠️ | **Processed Food Consumption**: How often do you consume ultra-processed foods (packaged snacks, fast food, frozen meals)? | 0 = Multiple times daily → 10 = Rarely/Never |
| NUTR_014 ⚠️ | **Added Sugar Intake**: How often do you consume foods with added sugars (sodas, candy, baked goods, sweetened beverages)? | 0 = Daily, multiple servings → 10 = Rarely/Never |
| NUTR_015 ⚠️ | **Sodium Intake**: How often do you consume high-sodium foods (processed meats, salty snacks, fast food, canned foods)? | 0 = Daily → 10 = Rarely |
| NUTR_016 ⚠️ | **Alcohol Consumption**: How often do you consume alcohol? | 0 = Daily, excessive → 10 = Never/Rarely |

#### 1.5 Hydration & Supplementation

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_017 | **Water Intake**: How adequate is your daily water intake? | 0 = Minimal (\u003c2 cups) → 10 = Optimal (8+ cups) |
| NUTR_018 | **Hydration Awareness**: How well do you monitor and maintain proper hydration throughout the day? | 0 = Never think about it → 10 = Consistently aware |

#### 1.6 Eating Environment & Planning

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| NUTR_019 | **Meal Planning**: How often do you plan your meals in advance? | 0 = Never → 10 = Always plan ahead |
| NUTR_020 | **Home Cooking**: How often do you prepare meals at home (vs. eating out or ordering takeout)? | 0 = Never cook → 10 = Cook all meals |

### Nutrition Composite Score Calculation

**LIFE_001 (Nutrition Score)** = Average of NUTR_001 through NUTR_020

**Note:** For reverse-scored items (⚠️), invert the patient's response before averaging:
- Inverted Score = 10 - Patient Response

---

## PILLAR 2: MOVEMENT ASSESSMENT

**Composite Parameter:** LIFE_002 - Movement Score (0-10)
**Number of Questions:** 18 parameters
**Assessment Domains:** Aerobic activity, strength training, flexibility, NEAT, sedentary behavior

### Movement Parameters

#### 2.1 Cardiovascular & Aerobic Activity

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_001 | **Moderate-Intensity Aerobic Activity**: How often do you engage in moderate aerobic activities (brisk walking, cycling, swimming) for at least 30 minutes? | 0 = Never → 10 = 5+ days/week |
| MOVE_002 | **Vigorous-Intensity Aerobic Activity**: How often do you engage in vigorous aerobic activities (running, HIIT, sports) for at least 20 minutes? | 0 = Never → 10 = 3+ days/week |
| MOVE_003 | **Aerobic Endurance**: How would you rate your cardiovascular endurance and stamina? | 0 = Very poor → 10 = Excellent |
| MOVE_004 | **Weekly Aerobic Volume**: On average, how many total minutes of aerobic activity do you complete per week? | 0 = None → 10 = 150+ minutes |

#### 2.2 Strength & Resistance Training

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_005 | **Strength Training Frequency**: How often do you engage in resistance/strength training activities? | 0 = Never → 10 = 3+ days/week |
| MOVE_006 | **Full-Body Strengthening**: How well does your strength training routine cover all major muscle groups (legs, back, chest, core, arms)? | 0 = No routine → 10 = Comprehensive program |
| MOVE_007 | **Progressive Overload**: How consistently do you challenge yourself by progressively increasing weights, resistance, or difficulty? | 0 = No progression → 10 = Consistent progression |
| MOVE_008 | **Muscular Strength**: How would you rate your overall muscular strength? | 0 = Very weak → 10 = Very strong |

#### 2.3 Flexibility & Mobility

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_009 | **Stretching & Flexibility Work**: How often do you perform stretching or flexibility exercises? | 0 = Never → 10 = Daily |
| MOVE_010 | **Joint Mobility**: How would you rate your overall joint range of motion and mobility? | 0 = Very limited/stiff → 10 = Excellent mobility |
| MOVE_011 | **Balance & Stability**: How often do you practice balance exercises or activities that challenge stability? | 0 = Never → 10 = Regularly (3+ times/week) |

#### 2.4 Non-Exercise Activity Thermogenesis (NEAT)

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_012 | **Daily Steps**: How many steps do you typically walk per day? | 0 = \u003c2,000 → 10 = 10,000+ |
| MOVE_013 | **Active Lifestyle**: How physically active are you during your daily routine (taking stairs, walking, active hobbies)? | 0 = Completely sedentary → 10 = Very active throughout day |
| MOVE_014 | **Occupational Movement**: How much physical activity is involved in your work or daily responsibilities? | 0 = Desk-bound, no movement → 10 = Highly active role |

#### 2.5 Sedentary Behavior

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_015 ⚠️ | **Prolonged Sitting**: How many hours per day do you spend sitting (work, TV, computer, driving)? | 0 = 12+ hours → 10 = \u003c4 hours |
| MOVE_016 ⚠️ | **Screen Time**: How many hours per day do you spend on screens during leisure time (TV, phone, gaming)? | 0 = 8+ hours → 10 = \u003c1 hour |
| MOVE_017 | **Movement Breaks**: How often do you take breaks to stand, stretch, or move during prolonged sitting? | 0 = Never → 10 = Every 30 minutes |

#### 2.6 Movement Consistency & Enjoyment

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| MOVE_018 | **Exercise Consistency**: How consistent are you with maintaining your physical activity routine? | 0 = Very inconsistent → 10 = Highly consistent |

### Movement Composite Score Calculation

**LIFE_002 (Movement Score)** = Average of MOVE_001 through MOVE_018

**Note:** Reverse-scored items (⚠️) are inverted before averaging.

---

## PILLAR 3: SLEEP & RECOVERY ASSESSMENT

**Composite Parameter:** LIFE_003 - Recovery Score (0-10)
**Number of Questions:** 20 parameters
**Assessment Domains:** Sleep quality, sleep duration, sleep hygiene, stress management, recovery practices

### Sleep & Recovery Parameters

#### 3.1 Sleep Duration & Quality

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| SLEEP_001 | **Sleep Duration**: On average, how many hours of sleep do you get per night? | 0 = \u003c5 hours → 10 = 7-9 hours |
| SLEEP_002 | **Sleep Quality**: How would you rate the overall quality of your sleep? | 0 = Very poor → 10 = Excellent |
| SLEEP_003 | **Sleep Onset**: How easily do you fall asleep at bedtime? | 0 = Takes hours → 10 = Fall asleep within 15 min |
| SLEEP_004 | **Sleep Continuity**: How often do you sleep through the night without waking? | 0 = Wake many times → 10 = Sleep continuously |
| SLEEP_005 | **Morning Restedness**: How rested and refreshed do you feel when you wake up? | 0 = Exhausted → 10 = Fully refreshed |

#### 3.2 Sleep Hygiene & Routine

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| SLEEP_006 | **Consistent Sleep Schedule**: How consistent is your sleep and wake time (even on weekends)? | 0 = Highly irregular → 10 = Very consistent |
| SLEEP_007 | **Bedroom Environment**: How optimized is your sleep environment (dark, quiet, cool, comfortable)? | 0 = Very poor → 10 = Optimal |
| SLEEP_008 | **Pre-Sleep Routine**: How often do you follow a relaxing bedtime routine? | 0 = Never → 10 = Always |
| SLEEP_009 ⚠️ | **Screen Use Before Bed**: How often do you use screens (phone, TV, computer) within 1 hour of bedtime? | 0 = Always → 10 = Never |
| SLEEP_010 ⚠️ | **Caffeine Timing**: How often do you consume caffeine within 6 hours of bedtime? | 0 = Every day → 10 = Never |

#### 3.3 Stress Management

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| SLEEP_011 | **Perceived Stress Level**: How would you rate your overall stress level? | 0 = Extremely high → 10 = Very low/minimal |
| SLEEP_012 | **Stress Coping Skills**: How effectively do you manage and cope with stress? | 0 = Very poorly → 10 = Very effectively |
| SLEEP_013 | **Relaxation Practices**: How often do you engage in relaxation practices (meditation, deep breathing, yoga, prayer)? | 0 = Never → 10 = Daily |
| SLEEP_014 | **Work-Life Balance**: How well do you maintain balance between work/responsibilities and personal time? | 0 = No balance → 10 = Excellent balance |

#### 3.4 Recovery Practices

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| SLEEP_015 | **Rest Days**: How often do you take adequate rest/recovery days from intense physical activity? | 0 = Never → 10 = Appropriate recovery |
| SLEEP_016 | **Recovery Activities**: How often do you engage in active recovery (gentle movement, stretching, massage, foam rolling)? | 0 = Never → 10 = Regularly |
| SLEEP_017 | **Downtime**: How often do you allow yourself unstructured time for rest and relaxation? | 0 = Never → 10 = Daily |

#### 3.5 Energy & Vitality

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| SLEEP_018 | **Daytime Energy**: How would you rate your energy levels throughout the day? | 0 = Constantly exhausted → 10 = High energy all day |
| SLEEP_019 ⚠️ | **Daytime Sleepiness**: How often do you feel excessively sleepy or struggle to stay awake during the day? | 0 = Constantly → 10 = Never |
| SLEEP_020 | **Overall Recovery**: How well-recovered do you generally feel day-to-day? | 0 = Always fatigued → 10 = Fully recovered |

### Sleep & Recovery Composite Score Calculation

**LIFE_003 (Recovery Score)** = Average of SLEEP_001 through SLEEP_020

**Note:** Reverse-scored items (⚠️) are inverted before averaging.

---

## PILLAR 4: MENTAL HEALTH & EMOTIONAL CARE ASSESSMENT

**Composite Parameter:** LIFE_004 - Emotion Score (0-10)
**Number of Questions:** 22 parameters
**Assessment Domains:** Mood, anxiety, emotional regulation, self-esteem, life satisfaction, resilience

### Mental Health & Emotional Care Parameters

#### 4.1 Mood & Emotional State

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_001 | **Overall Mood**: How would you describe your overall mood over the past 2 weeks? | 0 = Very depressed → 10 = Very positive |
| EMOT_002 | **Positive Emotions**: How often do you experience positive emotions (joy, contentment, gratitude, excitement)? | 0 = Never → 10 = Daily/frequently |
| EMOT_003 ⚠️ | **Sadness/Depression**: How often do you feel sad, down, or depressed? | 0 = Constantly → 10 = Rarely/Never |
| EMOT_004 ⚠️ | **Anxiety/Worry**: How often do you feel anxious, worried, or on edge? | 0 = Constantly → 10 = Rarely/Never |
| EMOT_005 | **Emotional Stability**: How emotionally stable do you feel day-to-day? | 0 = Very unstable/volatile → 10 = Very stable |

#### 4.2 Emotional Regulation & Awareness

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_006 | **Emotional Awareness**: How well do you recognize and understand your own emotions? | 0 = No awareness → 10 = Excellent awareness |
| EMOT_007 | **Emotional Expression**: How comfortable are you expressing your emotions in healthy ways? | 0 = Unable to express → 10 = Very comfortable |
| EMOT_008 | **Emotional Regulation**: How effectively can you manage difficult emotions when they arise? | 0 = Cannot manage → 10 = Very effective |
| EMOT_009 | **Impulse Control**: How well do you control impulsive reactions to emotional situations? | 0 = Poor control → 10 = Excellent control |

#### 4.3 Self-Esteem & Self-Compassion

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_010 | **Self-Esteem**: How would you rate your overall self-esteem and self-worth? | 0 = Very low → 10 = Very high |
| EMOT_011 | **Self-Compassion**: How kind and compassionate are you toward yourself when facing difficulties or mistakes? | 0 = Very self-critical → 10 = Very self-compassionate |
| EMOT_012 | **Body Image**: How satisfied are you with your body and physical appearance? | 0 = Very dissatisfied → 10 = Very satisfied |

#### 4.4 Life Satisfaction & Purpose

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_013 | **Life Satisfaction**: How satisfied are you with your life overall? | 0 = Very dissatisfied → 10 = Very satisfied |
| EMOT_014 | **Sense of Purpose**: How strong is your sense of purpose and meaning in life? | 0 = No purpose → 10 = Strong purpose |
| EMOT_015 | **Hopefulness**: How hopeful do you feel about your future? | 0 = Hopeless → 10 = Very hopeful |

#### 4.5 Resilience & Coping

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_016 | **Resilience**: How well do you bounce back from setbacks, challenges, or adversity? | 0 = Cannot recover → 10 = Highly resilient |
| EMOT_017 | **Problem-Solving**: How confident are you in your ability to solve problems and handle challenges? | 0 = No confidence → 10 = Very confident |
| EMOT_018 | **Adaptability**: How well do you adapt to change and new situations? | 0 = Very poorly → 10 = Very well |

#### 4.6 Mental Health Support

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_019 | **Support-Seeking**: How comfortable are you seeking help when experiencing emotional or mental health difficulties? | 0 = Never seek help → 10 = Proactive about seeking support |
| EMOT_020 | **Mental Health Practices**: How often do you engage in mental health practices (therapy, counseling, support groups, journaling)? | 0 = Never → 10 = Regularly |

#### 4.7 Cognitive Function & Focus

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| EMOT_021 | **Concentration**: How well can you concentrate and maintain focus on tasks? | 0 = Cannot focus → 10 = Excellent focus |
| EMOT_022 | **Mental Clarity**: How clear and sharp does your thinking feel? | 0 = Very foggy → 10 = Very clear |

### Mental Health & Emotional Care Composite Score Calculation

**LIFE_004 (Emotion Score)** = Average of EMOT_001 through EMOT_022

**Note:** Reverse-scored items (⚠️) are inverted before averaging.

---

## PILLAR 5: ENVIRONMENT ASSESSMENT

**Composite Parameter:** LIFE_005 - Environment Score (0-10)
**Number of Questions:** 20 parameters
**Assessment Domains:** Social connections, community engagement, physical environment, safety, substance exposure

### Environment Parameters

#### 5.1 Social Connections & Relationships

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_001 | **Social Support Network**: How strong is your social support network (family, friends, community)? | 0 = No support → 10 = Very strong support |
| ENVIR_002 | **Quality Relationships**: How satisfied are you with the quality of your close relationships? | 0 = Very dissatisfied → 10 = Very satisfied |
| ENVIR_003 | **Social Interaction**: How often do you have meaningful social interactions with others? | 0 = Isolated/Never → 10 = Daily |
| ENVIR_004 ⚠️ | **Loneliness**: How often do you feel lonely or socially isolated? | 0 = Constantly → 10 = Never |
| ENVIR_005 | **Relationship Communication**: How effective is communication in your important relationships? | 0 = Very poor → 10 = Excellent |

#### 5.2 Community & Belonging

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_006 | **Community Connection**: How connected do you feel to your local community? | 0 = Not connected → 10 = Deeply connected |
| ENVIR_007 | **Community Engagement**: How often do you participate in community activities, groups, or organizations? | 0 = Never → 10 = Regularly engaged |
| ENVIR_008 | **Sense of Belonging**: How strong is your sense of belonging in your community or social groups? | 0 = No belonging → 10 = Strong belonging |

#### 5.3 Physical Environment Quality

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_009 | **Home Environment**: How safe, clean, and comfortable is your living environment? | 0 = Very poor → 10 = Excellent |
| ENVIR_010 | **Air Quality**: How would you rate the air quality in your home and neighborhood? | 0 = Very poor → 10 = Excellent |
| ENVIR_011 | **Noise Pollution**: How much are you exposed to excessive noise in your environment? | 0 = Constantly noisy → 10 = Very quiet |
| ENVIR_012 | **Access to Nature**: How much access do you have to green spaces, parks, or natural environments? | 0 = No access → 10 = Excellent access |

#### 5.4 Safety & Security

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_013 | **Physical Safety**: How safe do you feel in your home and neighborhood? | 0 = Very unsafe → 10 = Very safe |
| ENVIR_014 | **Financial Security**: How financially secure do you feel? | 0 = Very insecure → 10 = Very secure |
| ENVIR_015 | **Housing Stability**: How stable is your current housing situation? | 0 = Very unstable → 10 = Very stable |

#### 5.5 Substance Exposure & Use

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_016 ⚠️ | **Tobacco Exposure**: How often are you exposed to tobacco smoke (personal use or secondhand)? | 0 = Daily exposure → 10 = Never |
| ENVIR_017 ⚠️ | **Recreational Drug Use**: How often do you use recreational drugs (excluding prescribed medications)? | 0 = Regularly → 10 = Never |
| ENVIR_018 ⚠️ | **Environmental Toxins**: How much are you exposed to environmental toxins (chemicals, pollutants, pesticides) at home or work? | 0 = High exposure → 10 = Minimal exposure |

#### 5.6 Resource Access

| Parameter ID | Question | Scoring (0-10) |
|--------------|----------|----------------|
| ENVIR_019 | **Healthcare Access**: How easy is it for you to access healthcare services when needed? | 0 = Very difficult → 10 = Very easy |
| ENVIR_020 | **Healthy Food Access**: How easy is it for you to access fresh, healthy food in your area? | 0 = Very difficult → 10 = Very easy |

### Environment Composite Score Calculation

**LIFE_005 (Environment Score)** = Average of ENVIR_001 through ENVIR_020

**Note:** Reverse-scored items (⚠️) are inverted before averaging.

---

## OVERALL LIFESTYLE COMPOSITE SCORE

**Composite Parameter:** LIFE_006 - Lifestyle Composite Score (0-10)

### Calculation Method

**LIFE_006** = Weighted average of 5 pillar scores

**Default Weighting (Equal):**
- LIFE_001 (Nutrition): 20%
- LIFE_002 (Movement): 20%
- LIFE_003 (Recovery): 20%
- LIFE_004 (Emotion): 20%
- LIFE_005 (Environment): 20%

**Formula:**
```
LIFE_006 = (LIFE_001 × 0.20) + (LIFE_002 × 0.20) + (LIFE_003 × 0.20) + (LIFE_004 × 0.20) + (LIFE_005 × 0.20)
```

**Optional Custom Weighting:**
Weights can be adjusted based on individual patient priorities or clinical focus areas, maintaining total weight = 100%.

### Dashboard Integration

**Lifestyle Composite Score → Overall Health Score:**
1. LIFE_006 (0-10 scale) × 10 = Lifestyle Points (0-100)
2. Lifestyle Points contribute **30%** to Overall Health Score
3. Remaining **70%** from 8 Organ System Scores (objective data)

---

## QUESTIONNAIRE ADMINISTRATION GUIDE

### Assessment Frequency

**Standard Schedule:**
- **Baseline:** Complete assessment at initial comprehensive evaluation
- **Quarterly:** Repeat assessment every 3 months
- **Interval:** As clinically indicated (following interventions, care plan changes)

**Gamification Opportunities:**
- Random "check-in" questions via app (1-2 questions per pillar)
- Weekly mini-assessments (5-10 questions)
- Post-appointment reflection prompts

### Administration Formats

1. **Digital (Preferred):**
   - Integrated app questionnaire with auto-scoring
   - Tablet/computer at clinic visit
   - Patient portal for home completion

2. **Paper:**
   - Printed questionnaire with bubble-sheet responses
   - Manual data entry for scoring

3. **Hybrid:**
   - Clinician-guided interview using digital entry
   - Useful for patients with limited literacy or technology access

### Clinical Use Guidelines

**For Patients:**
- Promote self-reflection and awareness of lifestyle patterns
- Track progress over time
- Identify areas for improvement
- Set personalized goals

**For Clinicians:**
- Discussion starter for lifestyle counseling
- Identify intervention priorities
- Monitor response to lifestyle interventions
- Document patient engagement and progress
- Support shared decision-making for care plans

### Interpretation Thresholds

**Pillar Score Ranges:**
- **8.0-10.0:** Excellent - Maintain current practices
- **6.0-7.9:** Good - Minor adjustments recommended
- **4.0-5.9:** Fair - Structured intervention recommended
- **2.0-3.9:** Poor - Intensive support needed
- **0-1.9:** Critical - Urgent intervention required

**Alert Triggers:**
- **Critical:** Any pillar \u003c 2.0, Emotion \u003c 3.0, Recovery \u003c 2.0
- **High-Risk:** Any pillar \u003c 4.0, ≥2 point decline over 6 months
- **Moderate:** Any pillar \u003c 6.0

---

## PARAMETER TRACKING & TRENDING

### Longitudinal Monitoring

Each individual parameter (100 total across 5 pillars) can be tracked over time to identify:
- **Trends:** Improving/declining patterns
- **Intervention Response:** Changes following specific interventions
- **Seasonal Variations:** Patterns related to time of year
- **Life Events:** Impact of major life changes on specific behaviors

### Data Visualization

**Individual Parameter Trends:**
- Line graphs showing score changes over time (0-10 scale)
- Color-coding: Green (improving), Yellow (stable), Red (declining)

**Pillar Composite Scores:**
- Coxcomb (radar) chart showing all 5 pillars simultaneously
- Historical overlays to compare baseline vs. current
- Traffic light indicators for at-risk pillars

**Overall Lifestyle Score:**
- Single metric (0-100) integrated into Overall Health Score dashboard
- Contribution breakdown showing which pillars are strongest/weakest

---

## CUSTOMIZATION & CLINICAL NOTES

### Question Adaptations

**Cultural Sensitivity:**
- Questions can be adapted for cultural context
- Food examples adjusted for regional/cultural diets
- Social norms considered in relationship questions

**Age Appropriateness:**
- Pediatric versions (with parent/guardian input)
- Young adult modifications
- Geriatric considerations (mobility, social isolation)

**Condition-Specific Additions:**
- Additional questions for specific diagnoses (e.g., diabetes nutrition focus)
- Disease-specific recovery parameters (e.g., cardiac rehab)

### Clinical Documentation

**For Each Pillar Score:**
- Document composite score (0-10)
- Identify lowest-scoring individual parameters
- Note patient-identified barriers
- Record patient goals and priorities
- Plan interventions and follow-up

**Sample Clinical Note:**
```
LIFESTYLE ASSESSMENT (2025-11-20):
- Nutrition: 5.2/10 (Low scores: whole foods consumption, vegetable intake, meal prep)
- Movement: 6.8/10 (Low score: sedentary time, needs more strength training)
- Recovery: 4.5/10 (Low scores: sleep duration, stress management, energy) ⚠️
- Emotion: 7.2/10 (Good overall, mild anxiety reported)
- Environment: 8.1/10 (Strong social support, safe housing)
- COMPOSITE: 6.4/10 (64 points)

PRIORITY INTERVENTIONS:
1. Sleep hygiene counseling - target 7-8 hrs/night
2. Stress management referral (mindfulness program)
3. Nutrition education - meal planning support
4. Follow-up: 6 weeks
```

---

## SUMMARY

### Total Parameter Count

| Pillar | Parameters | Key Domains |
|--------|-----------|-------------|
| **Nutrition** | 20 | Diet quality, macronutrients, portions, hydration |
| **Movement** | 18 | Aerobic, strength, flexibility, NEAT, sedentary behavior |
| **Sleep & Recovery** | 20 | Sleep quality/duration, hygiene, stress, recovery |
| **Mental Health** | 22 | Mood, emotional regulation, resilience, life satisfaction |
| **Environment** | 20 | Social support, community, safety, substance exposure |
| **TOTAL** | **100** | Comprehensive lifestyle assessment |

### Implementation Pathway

1. ✅ Questionnaire content finalized (this document)
2. ⏭️ Digital platform development (app/portal integration)
3. ⏭️ Scoring algorithm implementation
4. ⏭️ Clinical workflow integration
5. ⏭️ Staff training on administration and interpretation
6. ⏭️ Patient education materials creation
7. ⏭️ Pilot testing with patient cohort
8. ⏭️ Refinement based on feedback
9. ⏭️ Full deployment

---

**Document Status:** ✅ Complete - Ready for review
**Next Steps:** Review with clinical team, refine based on feedback, proceed to digital implementation
**Version Control:** v1.0 - Initial comprehensive questionnaire

