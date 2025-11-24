# CARD TYPE-SPECIFIC SPECIFICATIONS

All card types use the universal WHO-WHAT-WHEN-WHERE-WHY-HOW-MEASURE-TARGET-SAFETY-FOLLOW-UP-NOTES template, but each has specific sub-data elements.

**UPDATED v2.0**: Aligned with 12 Tier 2 Card Types per LIBRARY_TIER_STRUCTURE.md

---

## TIER 2 CARD TYPE SUMMARY

| # | Card Type | Icon | Tier 1 | Rx Required | Key Tier 3 Subcategories |
|---|-----------|------|--------|-------------|--------------------------|
| 1 | Medications | 💊 | Medical | Yes | Prescription Meds, OTC/Supplements |
| 2 | Diagnostic Testing | 🔬 | Medical | Yes | Laboratory Tests, Home Monitoring |
| 3 | Imaging Studies | 🏥 | Medical | Yes | X-Ray, CT, MRI, Ultrasound, Other |
| 4 | Procedures | 🔧 | Medical | Yes | Diagnostic, Therapeutic, Surgical, Preventive |
| 5 | Durable Medical Equipment | 🩺 | Medical | Yes | Respiratory, Mobility, Sensory, Chronic Disease |
| 6 | Referrals | 👨‍⚕️ | Medical | Yes | Medical Specialists, Behavioral Health, Rehab, Allied Health |
| 7 | Nutrition | 🥗 | Behavioral | No | Diet Patterns, Food Focus, Eating Behaviors |
| 8 | Movement/Exercise | 🏃 | Behavioral | No | Aerobic, Strength, Flexibility, Balance |
| 9 | Recovery | 😴 | Behavioral | No | Sleep Hygiene, Stress Management, Breathing/Relaxation |
| 10 | Mind-Body Practices | 🧘 | Behavioral | No | Meditation, Yoga, Tai Chi, Other |
| 11 | Environmental & Social Health | 🌍 | Behavioral | No | Social, Environmental, Occupational, Substance Use, Financial |
| 12 | Micro-Learning | 📚 | Behavioral | No | Cardiovascular, Metabolic, Nutrition, Exercise, Medication Concepts |

---

# MEDICAL CARDS (Tier 1)

---

## 1. MEDICATIONS 💊

### Description
Interventions requiring prescription or OTC medications, supplements, and vitamins.

### Tier 3 Subcategories
- **Prescription Medications**: Require prescriber order (MD/DO/NP/PA)
- **OTC & Supplements**: Over-the-counter, vitamins, minerals, herbal products

### Sub-Data Elements
- **Drug name**: Generic + Brand
- **Dose**: Value + Unit (mg, mcg, mL, etc.)
- **Formulation**: Tablet, capsule, liquid, injection, topical, inhaler, patch
- **Route**: PO (oral), IV, IM, SC, topical, inhalation, sublingual, rectal
- **Frequency**: QD, BID, TID, QID, PRN (as needed), weekly, monthly
- **Timing**: Morning, bedtime, with meals, before meals, empty stomach
- **Duration**: Days, weeks, months, ongoing
- **Administration specifics**: With/without food, swallow whole vs chew, storage
- **Interactions/Contraindications**: Major drug interactions, absolute contraindications
- **Missed dose instructions**: What to do if dose is missed
- **Refill information**: Days supply, refills remaining

### Additional Fields for OTC/Supplements (Tier 3)
- **Quality certification**: USP, NSF, third-party tested
- **Evidence level**: Usually Grade B or C (note limitations)
- **FDA disclaimer**: "Not FDA-approved for [condition]"
- **Brand recommendations**: Trusted brands if applicable

### Template Mapping
- **WHO**: Patient self-administers; MD prescribes; Pharmacist dispenses
- **WHAT**: Drug name (generic + brand), dose, formulation
- **HOW**: Route, timing, administration specifics, storage
- **WHEN**: Frequency, timing, duration
- **WHERE**: Home, carry during travel
- **MEASURE**: Relevant vitals/labs (BP, HR, glucose, drug levels)
- **TARGET**: Goal ranges for monitored parameters
- **SAFETY**: Drug-specific side effects by health system, interactions, allergic reactions
- **FOLLOW-UP**: When to check labs, dose titration schedule

### Auto-Population from Drug Database
- Standard dosing (adult/pediatric/geriatric)
- Common side effects (top 5 most frequent with percentages)
- Monitoring requirements (labs, vitals)
- Drug interactions (major only)
- Contraindications (absolute and relative)
- Evidence citation (guideline source)
- Cost/generic availability

---

## 2. DIAGNOSTIC TESTING 🔬

### Description
Laboratory tests and home monitoring interventions that produce quantitative health data.

### Tier 3 Subcategories
- **Laboratory Tests**: Facility-based testing (blood, urine, stool, swabs)
- **Home Monitoring**: Patient-directed tracking (BP, glucose, weight, pulse ox)

### Sub-Data Elements (Laboratory Tests)
- **Test name**: Full name + common abbreviation
- **CPT code**: Billing code
- **LOINC code**: Standard identifier
- **Specimen type**: Blood (serum, plasma, whole blood), urine, stool
- **Collection method**: Venipuncture, finger stick, clean catch urine
- **Fasting requirements**: Hours needed, medications to hold, water allowed
- **Tube type**: Red top, gold top (SST), lavender top (EDTA), etc.
- **Preparation instructions**: Patient prep required
- **Expected turnaround time**: When results available
- **Normal reference ranges**: Note: may vary by lab
- **Critical values**: Values requiring immediate notification
- **Result interpretation guidance**: What results mean

### Sub-Data Elements (Home Monitoring)
- **Vital sign type**: BP, HR, weight, glucose, O2 sat, temperature
- **Device type**: BP cuff, scale, glucometer, pulse oximeter
- **Device specifications**: Brand recommendations, validation status
- **Measurement technique**: Proper positioning, timing, calibration
- **Frequency**: Daily, BID, weekly, before/after meals
- **Recording method**: App, paper log, portal entry
- **Notification thresholds**: When to contact clinician

### Template Mapping
- **WHO**: Patient presents to lab/self-monitors; MD orders; Lab tech performs; MD interprets
- **WHAT**: Test name, CPT code, specimen type OR vital sign, device type
- **HOW**: Collection method, preparation OR proper technique, device setup
- **WHEN**: Fasting duration, timing OR frequency, specific times
- **WHERE**: Lab location OR home, consistent location
- **MEASURE**: Lab values OR vital signs being assessed
- **TARGET**: Normal reference ranges OR goal ranges
- **SAFETY**: Critical values, preparation risks, when to escalate
- **FOLLOW-UP**: When results reviewed, trend analysis, next steps

### Reference Range Table Example
| Test | Normal Range | Units | Critical Low | Critical High |
|------|--------------|-------|--------------|---------------|
| Glucose (fasting) | 70-99 | mg/dL | <50 | >400 |
| Potassium | 3.5-5.0 | mEq/L | <2.5 | >6.5 |
| TSH | 0.4-4.0 | mIU/L | <0.1 | >20 |
| HbA1c | <5.7% | % | N/A | >14% |

### Device-Specific Instructions (Home Monitoring)

**Blood Pressure Monitoring**:
- Use upper arm cuff (not wrist)
- Validate device accuracy
- Sit quietly 5 minutes before measurement
- Feet flat on floor, back supported
- Arm at heart level
- Take 2 readings, 1 minute apart
- Record both readings with time

**Blood Glucose Monitoring**:
- Wash hands with warm water
- Use side of fingertip (less painful)
- Rotate fingers
- First drop: wipe away; second drop: test
- Record time of day and relation to meals

**Weight Monitoring**:
- Same time each day (morning preferred)
- After voiding, before eating
- Minimal clothing
- Same scale on hard surface

---

## 3. IMAGING STUDIES 🏥

### Description
Diagnostic imaging procedures using various modalities to visualize internal structures.

### Tier 3 Subcategories
- **X-Ray Imaging**: Plain radiographs (chest, abdomen, musculoskeletal)
- **CT Scans**: Computed tomography (with/without contrast)
- **MRI Studies**: Magnetic resonance imaging
- **Ultrasound**: Sonography (abdominal, pelvic, vascular, cardiac)
- **Specialized Imaging**: Nuclear medicine, mammography, fluoroscopy

### Sub-Data Elements
- **Study name**: Full name + common abbreviation
- **CPT code**: Billing code
- **Modality**: X-ray, CT, MRI, US, nuclear, mammography
- **Body region**: Specific anatomical area
- **Purpose/indication**: Why study is being ordered
- **Contrast media**: Type (oral, IV, none), allergy screening required
- **Preparation requirements**: Fasting, bowel prep, medication holds
- **Radiation exposure**: Effective dose in mSv (if applicable)
- **Duration**: How long study takes
- **Claustrophobia considerations**: MRI-specific
- **Metal screening**: MRI safety checklist
- **Results timeline**: When to expect results

### Template Mapping
- **WHO**: Patient undergoes; Radiologist/Tech performs; MD orders and interprets
- **WHAT**: Study name, modality, body region, purpose
- **HOW**: Preparation steps, what happens during procedure
- **WHEN**: Scheduling considerations, how often repeated
- **WHERE**: Hospital, imaging center, clinic
- **MEASURE**: Findings from study (anatomical, pathological)
- **TARGET**: Normal findings vs abnormal requiring intervention
- **SAFETY**: Radiation exposure, contrast reactions, complications, pregnancy screening
- **FOLLOW-UP**: Results discussion, next steps based on findings

### Radiation Exposure Reference
| Study | Effective Dose (mSv) | Equivalent Background Radiation |
|-------|---------------------|--------------------------------|
| Chest X-ray | 0.1 | 10 days |
| Mammogram | 0.4 | 7 weeks |
| CT Head | 2 | 8 months |
| CT Chest | 7 | 2 years |
| CT Abdomen/Pelvis | 10 | 3 years |

---

## 4. PROCEDURES 🔧

### Description
Diagnostic, therapeutic, surgical, and preventive interventions performed on the patient.

### Tier 3 Subcategories
- **Diagnostic Procedures**: Endoscopy, colonoscopy, bronchoscopy, cardiac cath, biopsy
- **Minor Therapeutic Procedures**: Injections, wound care, minor excisions
- **Surgical Procedures**: Minor to major surgeries
- **Preventive Procedures**: Vaccinations, screening procedures

### Sub-Data Elements
- **Procedure name**: Full name + common abbreviation
- **CPT code**: Billing code
- **Procedure type**: Diagnostic, therapeutic, surgical, preventive
- **Purpose/indication**: Why procedure is being done
- **Setting**: Office, outpatient surgery center, hospital, bedside
- **Anesthesia type**: None, local, sedation, general
- **Preparation requirements**: Fasting, bowel prep, medication holds, labs
- **Pre-procedure clearance**: Cardiac, pulmonary if needed
- **Duration**: How long procedure takes
- **Sedation/anesthesia**: Type and recovery requirements
- **Recovery time**: When patient can resume activities
- **Post-procedure restrictions**: Activity, diet, driving
- **Results timeline**: When to expect results/pathology
- **Follow-up plan**: What happens based on findings

### Template Mapping
- **WHO**: Patient undergoes; Specialist performs; MD orders and coordinates
- **WHAT**: Procedure name, purpose, what's being done
- **HOW**: Preparation steps, what happens during procedure
- **WHEN**: Scheduling considerations, timing relative to other treatments
- **WHERE**: Setting (office, ASC, hospital)
- **MEASURE**: Findings, pathology results, outcomes
- **TARGET**: Successful completion, normal findings, therapeutic goal
- **SAFETY**: Procedural risks, complications, post-procedure warning signs
- **FOLLOW-UP**: Results discussion, wound care, activity resumption

### Procedure Risk Categories
| Category | Examples | Typical Setting | Anesthesia |
|----------|----------|-----------------|------------|
| Minor | Skin biopsy, joint injection | Office | Local/None |
| Intermediate | Colonoscopy, endoscopy | ASC | Sedation |
| Major | Joint replacement, cardiac surgery | Hospital | General |

---

## 5. DURABLE MEDICAL EQUIPMENT (DME) 🩺

### Description
Medical devices and equipment prescribed for ongoing home use.

### Tier 3 Subcategories
- **Respiratory Equipment**: CPAP/BiPAP, home oxygen, nebulizers
- **Mobility & Assistive Devices**: Wheelchairs, walkers, canes, prosthetics
- **Sensory Devices**: Hearing aids, vision aids
- **Chronic Disease Management**: Insulin pumps, compression devices, hospital beds

### Sub-Data Elements
- **Device name**: Specific equipment type
- **Device category**: Respiratory, mobility, sensory, chronic disease
- **Prescription details**: Settings, parameters, specifications
- **Fitting/sizing**: Measurements required
- **Supplier information**: Where to obtain, DME company
- **Training requirements**: Patient/caregiver education needed
- **Use instructions**: Daily schedule, cleaning, maintenance
- **Compliance tracking**: Usage data if device tracks (CPAP hours, etc.)
- **Troubleshooting guide**: Common issues and solutions
- **Replacement schedule**: When to replace supplies/device
- **Insurance coverage**: Prior auth requirements, coverage details

### Template Mapping
- **WHO**: Patient uses; DME company supplies; Specialist prescribes; RT/PT trains
- **WHAT**: Device name, specifications, settings
- **HOW**: Proper use technique, cleaning, maintenance
- **WHEN**: Daily schedule, frequency of use
- **WHERE**: Home, travel considerations
- **MEASURE**: Compliance data (hours used), symptom improvement
- **TARGET**: Usage goals (e.g., CPAP >4 hours/night), symptom targets
- **SAFETY**: Device-specific warnings, malfunction signs, when to call
- **FOLLOW-UP**: Compliance review, device check, supply reorder

### DME Category Examples
| Category | Examples | Typical Training | Compliance Tracking |
|----------|----------|------------------|---------------------|
| Respiratory | CPAP, BiPAP, O2 | RT education | Machine data download |
| Mobility | Walker, wheelchair | PT evaluation | Self-report |
| Sensory | Hearing aids | Audiologist fitting | Self-report |
| Chronic Disease | Insulin pump | Diabetes educator | Device data |

---

## 6. REFERRALS 👨‍⚕️

### Description
Orders for consultation with specialists, therapists, and allied health professionals.

### Tier 3 Subcategories
- **Medical Specialist Consultations**: Cardiology, endocrinology, neurology, etc.
- **Behavioral Health Providers**: Psychiatry, psychology, counseling, support groups
- **Rehabilitation Services**: Physical therapy, occupational therapy, speech therapy, cardiac/pulmonary rehab
- **Allied Health Professionals**: Dietitian, social work, pharmacist, diabetes educator

### Sub-Data Elements
- **Specialist type**: Specific specialty or service
- **Referral category**: Medical, behavioral health, rehab, allied health
- **Reason for referral**: Specific clinical question/concern
- **Urgency**: Routine, urgent, emergent
- **Referral type**: One-time consult vs ongoing care
- **Information to send**: Labs, imaging, notes, medication list
- **Questions to ask**: Prepare patient for consultation
- **Expected timeline**: When appointment should occur
- **Insurance considerations**: Referral/prior auth requirements
- **Expected duration of care**: Single visit, series, ongoing

### Template Mapping
- **WHO**: Patient schedules and attends; Specialist evaluates; PCP coordinates
- **WHAT**: Type of specialist, reason for consultation
- **HOW**: How to schedule, what to bring, what to expect
- **WHEN**: Timing of appointment (routine vs urgent)
- **WHERE**: Specialist office location, telehealth option
- **MEASURE**: Assessment findings, recommendations received
- **TARGET**: Diagnosis, treatment plan, clinical question answered
- **SAFETY**: When to escalate if can't get timely appointment
- **FOLLOW-UP**: Report back to PCP, implement recommendations

### Referral Urgency Guide
| Urgency | Timeline | Examples |
|---------|----------|----------|
| Routine | 2-4 weeks | Chronic condition optimization |
| Urgent | 1-7 days | Concerning symptoms, abnormal results |
| Emergent | Same day/ED | Acute symptoms, safety concerns |

---

# BEHAVIORAL CARDS (Tier 1)

---

## 7. NUTRITION 🥗

### Description
Dietary interventions including eating patterns, specific food changes, and meal behaviors.

### Tier 3 Subcategories
- **Diet Patterns**: Evidence-based patterns (Mediterranean, DASH, MIND, therapeutic diets)
- **Specific Food Focus**: Increase/decrease specific foods or nutrients
- **Eating Behaviors & Meal Planning**: Meal timing, portion control, mindful eating, prep strategies

### Sub-Data Elements
- **Dietary intervention type**: Pattern, food focus, behavior
- **Specific dietary action/change**: Clear, actionable instruction
- **Food examples**: Include, avoid, limit (with specific foods)
- **Portion sizes**: Grams, cups, hand-sizing method, plate method
- **Frequency**: Daily, per meal, weekly targets
- **Timing**: Breakfast, with meals, before exercise, fasting windows
- **Meal ideas and recipes**: Practical examples
- **Food preparation tips**: Cooking methods, batch prep
- **Substitutions and alternatives**: Swaps for restricted foods
- **Cultural food adaptations**: Ethnically appropriate options
- **Budget considerations**: Low-cost alternatives
- **Difficulty level**: Easy, moderate, requires cooking skills

### Template Mapping
- **WHO**: Patient implements; RD/Nutritionist designs; Family supports meal prep
- **WHAT**: Specific dietary change, portions, food types
- **HOW**: Meal ideas, prep tips, portion measuring methods, substitutions
- **WHEN**: Meal timing, frequency
- **WHERE**: Home kitchen, restaurants, grocery shopping
- **MEASURE**: Weight, waist circumference, blood sugar, lipids, food diary
- **TARGET**: Goal weight, glucose ranges, lipid levels, intake targets
- **SAFETY**: Food allergies, religious restrictions, signs of malnutrition, eating disorders
- **FOLLOW-UP**: Weekly weigh-ins, monthly nutrition check, RD visits

### Portion Guide Methods

**Hand-Sizing Method**:
- Protein: Palm-sized (3-4 oz)
- Vegetables: 2 fists (2 cups)
- Carbs: Cupped hand (1/2 cup cooked)
- Fats: Thumb-sized (1 tablespoon)

**Plate Method**:
- 1/2 plate: Non-starchy vegetables
- 1/4 plate: Lean protein
- 1/4 plate: Whole grains/starchy vegetables

---

## 8. MOVEMENT/EXERCISE 🏃

### Description
Physical activity interventions across aerobic, strength, flexibility, and balance domains.

### Tier 3 Subcategories
- **Aerobic Exercise**: Walking, running, cycling, swimming, group fitness
- **Strength Training**: Bodyweight, free weights, resistance bands, machines
- **Flexibility & Stretching**: Static stretching, dynamic warm-ups, yoga for flexibility
- **Balance Training**: Static balance, dynamic balance, fall prevention

### Sub-Data Elements
- **Exercise type/modality**: Specific activity
- **Intensity level**: RPE (1-10), Heart Rate zones, METs
- **Duration per session**: Minutes
- **Frequency per week**: Days/week
- **Progression criteria**: When to increase intensity/duration
- **Regression criteria**: When to decrease (illness, injury)
- **Modifications for limitations**: Joint issues, cardiac conditions, obesity
- **Equipment needed**: None, shoes, weights, bands, gym access
- **Technique cues**: Form guidance, breathing patterns
- **Warm-up instructions**: Pre-exercise routine
- **Cool-down instructions**: Post-exercise routine
- **Safety precautions by condition**: Cardiac, orthopedic, metabolic

### Template Mapping
- **WHO**: Patient performs; PT/Exercise Physiologist designs; Family provides accountability
- **WHAT**: Exercise type, intensity (RPE/HR/METs), duration
- **HOW**: Technique cues, form guidance, equipment setup, modifications
- **WHEN**: Frequency (x/week), time of day, progression schedule
- **WHERE**: Home, gym, outdoors, PT clinic
- **MEASURE**: Heart rate, distance, steps, weight lifted, flexibility, RPE
- **TARGET**: HR zones, step goals, strength benchmarks, flexibility goals
- **SAFETY**: Activity-specific by health system (cardiovascular signs, joint pain, dizziness)
- **FOLLOW-UP**: Weekly self-assessment, monthly PT check, progression review

### Intensity Scales

**RPE (Rate of Perceived Exertion) Scale**:
- 1-2: Very light (sitting, standing)
- 3-4: Light (easy walk, can sing)
- 5-6: Moderate (brisk walk, can talk but not sing)
- 7-8: Hard (jogging, difficult to talk)
- 9-10: Very hard (sprinting, can't speak)

**Heart Rate Zones** (based on max HR = 220 - age):
- Zone 1 (50-60%): Very light activity
- Zone 2 (60-70%): Fat burning, base fitness
- Zone 3 (70-80%): Aerobic endurance
- Zone 4 (80-90%): Anaerobic threshold
- Zone 5 (90-100%): Maximum effort

**MET (Metabolic Equivalent) Examples**:
- 1 MET: Resting
- 2-3 METs: Light housework, slow walking
- 4-6 METs: Brisk walking, light cycling
- 7-9 METs: Jogging, swimming, heavy yard work
- 10+ METs: Running, vigorous sports

### Progression Tier Example
```
Tier 1 (Beginner):
  Walk 10 minutes, 3x/week, RPE 3-4/10
  Advance if: Completing comfortably for 2 weeks, no pain

Tier 2 (Intermediate):
  Walk 20 minutes, 4x/week, RPE 5-6/10
  Advance if: Comfortable for 2 weeks

Tier 3 (Advanced):
  Walk 30 minutes, 5x/week, RPE 6-7/10
  Can add intervals or inclines
```

---

## 9. RECOVERY 😴

### Description
Sleep optimization, stress management, and relaxation/breathing interventions.

### Tier 3 Subcategories
- **Sleep Hygiene & Optimization**: Sleep schedule, environment, pre-sleep routines
- **Stress Management**: Cognitive techniques, behavioral strategies, social support
- **Breathing & Relaxation Practices**: Structured breathing, PMR, guided imagery

### Sub-Data Elements
- **Recovery type**: Sleep, stress, breathing/relaxation
- **Specific intervention**: Technique or practice name
- **Duration per session**: Minutes
- **Frequency**: Daily, as needed, specific times
- **Timing**: Bedtime routine, morning, when stressed
- **Environment setup**: Room conditions, equipment needed
- **Tools/resources**: Apps, audio guides, worksheets
- **Technique instructions**: Step-by-step guidance
- **Progression**: Simple to advanced techniques
- **Integration with routines**: How to build into daily life

### Template Mapping
- **WHO**: Patient practices; Therapist/Coach teaches; Family supports environment
- **WHAT**: Specific recovery technique or practice
- **HOW**: Step-by-step instructions, environment setup
- **WHEN**: Frequency, optimal timing, triggers for use
- **WHERE**: Bedroom, quiet space, anywhere
- **MEASURE**: Sleep duration/quality, stress rating (1-10), HRV if available
- **TARGET**: Sleep hours (7-9), sleep efficiency, stress reduction
- **SAFETY**: Signs of sleep disorders, worsening anxiety, when to escalate
- **FOLLOW-UP**: Sleep diary review, technique adjustment, specialist referral if needed

### Sleep Hygiene Checklist
- Same bedtime/wake time daily (even weekends)
- No screens 1 hour before bed
- Cool room (65-68°F / 18-20°C)
- Dark room (blackout curtains or eye mask)
- Quiet or white noise
- No caffeine after 2pm
- No alcohol within 3 hours of bed
- Light snack if hungry (avoid heavy meals)

### Breathing Techniques Reference

**4-7-8 Breathing**:
1. Breathe in through nose for 4 counts
2. Hold breath for 7 counts
3. Exhale through mouth for 8 counts
4. Repeat 4 cycles

**Box Breathing**:
1. Inhale for 4 counts
2. Hold for 4 counts
3. Exhale for 4 counts
4. Hold for 4 counts
5. Repeat 4-6 cycles

**Diaphragmatic Breathing**:
1. Place hand on belly
2. Breathe in slowly, belly rises
3. Exhale slowly, belly falls
4. Focus on belly movement, not chest

---

## 10. MIND-BODY PRACTICES 🧘

### Description
Self-directed contemplative and movement practices for mental and physical well-being.

### Tier 3 Subcategories
- **Meditation & Mindfulness**: Focused attention, mindfulness, loving-kindness, body scan, MBSR
- **Yoga**: Hatha, restorative, gentle/chair, condition-specific
- **Tai Chi & Qigong**: Balance-focused, arthritis-appropriate, traditional forms
- **Other Mind-Body**: Biofeedback, guided imagery, self-hypnosis

### Sub-Data Elements
- **Practice type**: Specific mind-body modality
- **Session duration**: Minutes per session
- **Frequency**: Times per week
- **Guidance type**: App-guided, audio, video, self-directed, in-person class
- **Experience level**: Beginner, intermediate, advanced
- **Physical requirements**: Standing, seated, lying down, movement
- **Equipment needed**: Mat, cushion, chair, none
- **Technique instructions**: Core practices
- **Progression path**: Building skill over time
- **Integration suggestions**: When/how to practice

### Template Mapping
- **WHO**: Patient practices; Instructor teaches (if class); App guides (if digital)
- **WHAT**: Specific mind-body practice, duration
- **HOW**: Step-by-step technique, posture, guidance resources
- **WHEN**: Frequency, optimal timing (morning, evening, when stressed)
- **WHERE**: Home (quiet space), studio, outdoors, anywhere
- **MEASURE**: Practice frequency, duration, mood/stress ratings (1-10), PHQ/GAD scores
- **TARGET**: Regular practice, symptom improvement, skill development
- **SAFETY**: Physical limitations, trauma considerations, dissociation awareness
- **FOLLOW-UP**: Practice log review, technique refinement, class progression

### Mind-Body Practice Comparison
| Practice | Primary Benefit | Physical Demand | Equipment | Time/Session |
|----------|-----------------|-----------------|-----------|--------------|
| Mindfulness meditation | Stress, focus | None | None | 5-20 min |
| Yoga (gentle) | Flexibility, stress | Low-moderate | Mat | 20-60 min |
| Tai Chi | Balance, calm | Low | None | 20-45 min |
| Body scan | Body awareness | None | None | 10-20 min |
| Guided imagery | Relaxation | None | Audio | 10-15 min |

---

## 11. ENVIRONMENTAL & SOCIAL HEALTH 🌍

### Description
Interventions addressing social connections, environmental factors, occupational health, substance use, and social determinants.

### Tier 3 Subcategories
- **Social Connection & Community**: Relationship building, support networks, community engagement
- **Environmental Quality**: Air quality, housing safety, neighborhood factors
- **Occupational Health**: Workplace ergonomics, work-life balance, safety
- **Substance Use & Harm Reduction**: Tobacco cessation, alcohol moderation, recovery support
- **Financial Health & Resource Navigation**: Assistance programs, food security, transportation

### Sub-Data Elements
- **Intervention area**: Social, environmental, occupational, substance, financial
- **Specific change/action**: Concrete, actionable step
- **Support people involved**: Family, friends, community members
- **Resources needed**: Programs, services, equipment
- **Barriers identified**: Specific obstacles to address
- **First step defined**: Immediate action to take
- **Community resources**: Local programs, support groups, services
- **Follow-up accountability**: How to track progress

### Template Mapping
- **WHO**: Patient implements; Social worker/counselor guides; Support network assists
- **WHAT**: Specific environmental or social change
- **HOW**: Step-by-step implementation, resources to access
- **WHEN**: Timeline for change, ongoing vs one-time
- **WHERE**: Home, work, community
- **MEASURE**: Specific metrics vary by intervention (visits/week, exposures reduced, etc.)
- **TARGET**: Defined goals (e.g., 2 social activities/week, smoke-free, ergonomic setup complete)
- **SAFETY**: Crisis resources, escalation plan, harm reduction principles
- **FOLLOW-UP**: Regular check-ins, resource utilization, goal adjustment

### Substance Use Resources

**Tobacco Cessation**:
- Quitline: 1-800-QUIT-NOW
- Nicotine replacement (OTC): Patch, gum, lozenge
- Prescription options: Varenicline, bupropion
- Apps: Smoke Free, QuitNow

**Alcohol Moderation/Cessation**:
- Moderate drinking limits: ≤1 drink/day (women), ≤2 drinks/day (men)
- AUDIT-C screening for assessment
- Support: AA, SMART Recovery, therapy
- Medications: Naltrexone, acamprosate, disulfiram

**Crisis Resources**:
- 988 Suicide & Crisis Lifeline
- SAMHSA National Helpline: 1-800-662-4357
- Crisis Text Line: Text HOME to 741741

---

## 12. MICRO-LEARNING 📚

### Description
Brief (5-minute) educational cards that provide foundational knowledge within decks, setting context for action cards.

### Tier 3 Subcategories
- **Cardiovascular Concepts**: Blood pressure, cholesterol, heart failure, AFib
- **Metabolic Concepts**: Blood sugar, HbA1c, insulin resistance, thyroid
- **Nutrition Science**: Macronutrients, glycemic index, reading labels
- **Exercise Concepts**: Heart rate zones, RPE, METs, progression principles
- **Medication Mechanisms**: How drug classes work (simplified)

### Sub-Data Elements
- **Topic**: Specific educational concept
- **Learning objective**: What patient will understand after
- **Related condition**: Condition this knowledge supports
- **Format**: Text, video, interactive, infographic
- **Duration**: Time to complete (target: 5 minutes)
- **Reading level**: 6th-8th grade
- **Key points**: 3-5 main takeaways
- **Common misconceptions**: Myths to address
- **Knowledge check**: Optional quiz or teach-back prompt
- **Next action card**: What this unlocks in the deck

### Template Mapping
- **WHO**: Patient learns; Care team assigns within deck
- **WHAT**: Specific concept, learning objective
- **HOW**: Format, step-by-step content delivery
- **WHEN**: Before related action card, self-paced
- **WHERE**: App, patient portal, anywhere
- **MEASURE**: Completion, knowledge check score (if applicable)
- **TARGET**: Demonstrated understanding, readiness for action card
- **SAFETY**: Correct dangerous misconceptions
- **FOLLOW-UP**: Unlock next card in deck sequence

### Micro-Learning Design Principles
1. **5 minutes or less** - Respect patient time
2. **One concept per card** - Focused learning
3. **6th-8th grade level** - Accessible language
4. **Visual when possible** - Diagrams, infographics
5. **Immediately applicable** - Connects to next action card
6. **Myth-busting included** - Address misconceptions
7. **Optional deeper dive** - Link to more info for curious patients

### Example Micro-Learning Topics
| Topic | Duration | Unlocks |
|-------|----------|---------|
| Understanding Your Blood Pressure Numbers | 5 min | BP monitoring card |
| How ACE Inhibitors Protect Your Heart | 4 min | Lisinopril card |
| What HbA1c Tells You | 5 min | HbA1c lab card |
| The Plate Method for Portion Control | 4 min | Nutrition card |
| Heart Rate Zones Explained | 5 min | Exercise card |

---

## CARD TYPE SUMMARY TABLE

| # | Card Type | Icon | Tier 1 | Primary Actor | Key MEASURE | Typical Duration |
|---|-----------|------|--------|---------------|-------------|------------------|
| 1 | Medications | 💊 | Medical | Patient | Vitals, Labs | Ongoing |
| 2 | Diagnostic Testing | 🔬 | Medical | Lab/Patient | Lab Values, Vitals | Periodic |
| 3 | Imaging Studies | 🏥 | Medical | Radiologist | Imaging Findings | One-time/Periodic |
| 4 | Procedures | 🔧 | Medical | Specialist | Outcomes, Pathology | One-time/Series |
| 5 | DME | 🩺 | Medical | Patient | Compliance, Symptoms | Ongoing |
| 6 | Referrals | 👨‍⚕️ | Medical | Specialist | Assessment | Varies |
| 7 | Nutrition | 🥗 | Behavioral | Patient | Weight, Labs | Ongoing |
| 8 | Movement | 🏃 | Behavioral | Patient | HR, Steps, Strength | Ongoing |
| 9 | Recovery | 😴 | Behavioral | Patient | Sleep, Stress | Ongoing |
| 10 | Mind-Body | 🧘 | Behavioral | Patient | Mood, Practice Log | Ongoing |
| 11 | Environmental/Social | 🌍 | Behavioral | Patient | Varies | Varies |
| 12 | Micro-Learning | 📚 | Behavioral | Patient | Completion | 5 minutes |

---

## VERSION HISTORY

- **v2.0** (November 2025): Major update to align with 12 Tier 2 types per LIBRARY_TIER_STRUCTURE.md
  - Consolidated: Supplements → Medications (Tier 3), Vital Monitoring → Diagnostic Testing (Tier 3)
  - Split: Imaging/Procedures into separate Tier 2 types
  - Added: DME, Mind-Body Practices, Environmental & Social Health
  - Renamed: Education → Micro-Learning
- **v1.0** (Original): 10 card types
