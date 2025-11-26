# SMART Card System - Complete Demo Case Presentation

> **Purpose**: This document demonstrates the complete SMART Card system workflow from patient presentation through card generation, selection, and delivery. Use this for team review and stakeholder presentations.
>
> **Version**: 1.0 | **Date**: 2024-11-23

---

# PART 1: THE CLINICAL CASE

## Patient Introduction

```
╔══════════════════════════════════════════════════════════════════╗
║                         PATIENT PROFILE                          ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  Name: Robert "Bobby" Martinez                                   ║
║  Age: 52 years old                                               ║
║  Sex: Male                                                       ║
║  Occupation: Long-haul truck driver                              ║
║                                                                  ║
║  ─────────────────────────────────────────────────────────────  ║
║                                                                  ║
║  PRESENTING COMPLAINT:                                           ║
║  "I'm always tired and my wife says I snore real loud.           ║
║   Doc says my sugar and pressure are too high."                  ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Clinical Encounter Note (Input)

```
══════════════════════════════════════════════════════════════════
                    CLINICAL ENCOUNTER NOTE
══════════════════════════════════════════════════════════════════

PATIENT: Robert Martinez, 52yo M
DATE: 2024-11-23
PROVIDER: Dr. Sarah Chen, MD (Primary Care)
VISIT TYPE: Comprehensive Health Assessment

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CHIEF CONCERNS (Patient's Own Words):
"I'm always tired, even after sleeping 8 hours. My wife recorded me
snoring and it sounds like a chainsaw. She says I stop breathing
sometimes. I can't lose weight no matter what I try. I want to
feel better so I can keep driving - that's my livelihood."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

VITALS:
  Blood Pressure: 158/94 mmHg (repeated: 154/92 mmHg)
  Heart Rate: 82 bpm
  Respiratory Rate: 16
  Temperature: 98.4°F
  SpO2: 95% on room air
  Weight: 268 lbs (121.6 kg)
  Height: 5'10" (178 cm)
  BMI: 38.5 kg/m² (Class II Obesity)
  Waist Circumference: 46 inches
  Neck Circumference: 18 inches

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HISTORY OF PRESENT ILLNESS:
52yo truck driver presenting for follow-up of abnormal labs and
new fatigue. Reports progressive daytime sleepiness x 6 months.
Falls asleep within 5 minutes of sitting down, even mid-day.
Wife reports loud snoring with witnessed apneas. Near-miss driving
incident last month due to drowsiness - very concerning given
occupation. Patient has tried to lose weight multiple times -
"I've tried every diet, nothing sticks." Diet consists mostly of
fast food and gas station meals on the road. Exercises rarely -
"hard to find time when you're driving 10 hours a day."

No chest pain, palpitations, edema. Reports occasional headaches,
worse in morning (improved after waking). Nocturia 2-3x/night.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PAST MEDICAL HISTORY:
- Obesity (long-standing, max weight 285 lbs 2 years ago)
- Hyperlipidemia (untreated, diagnosed 2 years ago)
- Pre-diabetes (A1c 6.2% last year - never followed up)
- GERD (uses Tums PRN)
- Low back pain (occupational)

PAST SURGICAL HISTORY:
- Appendectomy (age 24)
- Right knee arthroscopy (age 40)

MEDICATIONS:
- None regular
- Tums PRN
- Ibuprofen 400mg PRN for back pain (uses ~4-6x/week)

ALLERGIES:
- Sulfa drugs → Rash

FAMILY HISTORY:
- Father: Type 2 Diabetes, died age 68 from MI
- Mother: Alive, age 76, HTN, obesity
- Brother: Type 2 Diabetes, age 58
- Sister: Healthy

SOCIAL HISTORY:
- Occupation: Long-haul truck driver x 25 years
- Tobacco: Quit 5 years ago (20 pack-year history)
- Alcohol: 2-3 beers on weekends
- Diet: Fast food 5-6 days/week, drinks 3-4 sodas/day
- Exercise: None currently
- Sleep: 6-8 hours but unrefreshing
- Stress: Moderate (job demands, health worries)
- Insurance: Commercial (Trucking Union insurance)
- Lives with wife, 2 adult children out of home

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LABORATORY RESULTS (obtained 1 week ago):

METABOLIC PANEL:
  Glucose (fasting): 142 mg/dL (H) [70-99]
  HbA1c: 7.2% (H) [<5.7%]
  BUN: 18 mg/dL [7-20]
  Creatinine: 1.1 mg/dL [0.7-1.3]
  eGFR: 78 mL/min [>60]
  Sodium: 141 mEq/L [136-145]
  Potassium: 4.2 mEq/L [3.5-5.0]

LIPID PANEL:
  Total Cholesterol: 248 mg/dL (H) [<200]
  LDL: 162 mg/dL (H) [<100]
  HDL: 34 mg/dL (L) [>40]
  Triglycerides: 260 mg/dL (H) [<150]

OTHER:
  TSH: 2.1 mIU/L [0.4-4.0]
  ALT: 52 U/L (H) [7-56] - mild elevation
  AST: 38 U/L [10-40]
  Uric Acid: 7.8 mg/dL (H) [3.5-7.2]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PHYSICAL EXAMINATION:

General: Alert, obese male in NAD, appears tired
HEENT: Crowded oropharynx (Mallampati IV), large tongue,
       enlarged uvula, neck circumference 18"
CV: RRR, no murmurs, no JVD
Lungs: CTAB, no wheezes
Abdomen: Obese, soft, non-tender, no HSM
Extremities: No edema, pulses intact
Neuro: A&O x4, CN II-XII intact

STOP-BANG Score: 7/8 (HIGH RISK for OSA)
  - Snoring: YES
  - Tired: YES
  - Observed apnea: YES
  - Pressure (HTN): YES
  - BMI >35: YES
  - Age >50: YES
  - Neck >16": YES
  - Gender Male: YES

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ASSESSMENT & PLAN:

DIAGNOSIS LIST:
1. Obstructive Sleep Apnea (suspected) - HIGH probability
2. Type 2 Diabetes Mellitus (new diagnosis, A1c 7.2%)
3. Hypertension Stage 2 (new diagnosis)
4. Mixed Hyperlipidemia (untreated)
5. Class II Obesity (BMI 38.5)
6. NAFLD (probable, given metabolic syndrome + elevated ALT)

PLAN:

Problem 1: Obstructive Sleep Apnea (Suspected)
- Order Home Sleep Test (HST) - urgent given occupation
- Discuss CPAP therapy if confirmed
- CRITICAL: Patient should not drive commercially until
  treated if moderate-severe OSA confirmed
- Neck positioning while sleeping until diagnosed
- Refer to Sleep Medicine if complex

Problem 2: Type 2 Diabetes Mellitus (New)
- Start Metformin 500mg BID with meals, titrate to 1000mg BID
- Diabetes education referral
- Start home glucose monitoring
- A1c recheck in 3 months, goal <7%
- Dietary counseling - reduce carbs, especially sodas

Problem 3: Hypertension
- Start Lisinopril 10mg daily
- Home BP monitoring
- Goal BP <130/80
- Lifestyle modifications (weight loss, Na restriction)
- Recheck BP 2 weeks, labs (BMP) 4 weeks

Problem 4: Hyperlipidemia
- Start Atorvastatin 40mg daily (high-intensity per ASCVD risk)
- 10-year ASCVD risk: 18.2% (HIGH)
- Goal LDL <70 given diabetes + HTN
- Repeat lipids in 3 months

Problem 5: Obesity
- Discussed weight loss - goal 10% loss (27 lbs) in 6 months
- Dietary modifications for road lifestyle
- Start walking program - even 10 min/day to start
- Consider GLP-1 agonist if not meeting goals
- Referral to registered dietitian

Problem 6: NAFLD
- Lifestyle modifications
- Avoid alcohol excess
- Recheck LFTs in 3 months
- Consider hepatology referral if persists

ADDITIONAL:
- Discussed reducing ibuprofen use (NSAID + HTN + new ACEi)
- Alternative: Acetaminophen for back pain
- PT referral for low back pain

FOLLOW-UP:
- Phone call in 1 week to check medication tolerance
- Office visit in 2 weeks for BP check
- Sleep study results review as soon as available
- Full follow-up in 4 weeks (labs, medication adjustment)

PATIENT GOALS DOCUMENTED:
"I want to keep driving trucks - it's my livelihood and my identity.
I need to feel less tired so I can be safe on the road. I want to
be around to meet my grandkids someday."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Dr. Sarah Chen, MD
Internal Medicine

══════════════════════════════════════════════════════════════════
```

---

# PART 2: AI-POWERED CARD GENERATION

## System Analysis

The SMART Card AI parses the clinical note and extracts:

```
╔══════════════════════════════════════════════════════════════════╗
║               AI CARD GENERATION ENGINE                          ║
║                                                                  ║
║  📋 Clinical Note Parsed                                         ║
║  🔍 6 Active Problems Identified                                 ║
║  🎯 Patient Goals Extracted                                      ║
║  💊 14 Interventions Mapped to Cards                             ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  PATIENT GOALS CAPTURED:                                         ║
║  ────────────────────────────────────────────────────────────   ║
║  "I want to keep driving trucks - it's my livelihood"            ║
║  "I need to feel less tired so I can be safe on the road"        ║
║  "I want to be around to meet my grandkids someday"              ║
║                                                                  ║
║  → These will populate the "WHY THIS MATTERS" section            ║
║    of every card for personalization                             ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  CLINICAL GOALS (Performance Medicine Framework):                ║
║  ────────────────────────────────────────────────────────────   ║
║  • Cardiovascular System: Reduce Risk (HTN, Lipids)              ║
║  • Metabolic System: Improve Function (Diabetes, Obesity)        ║
║  • Respiratory System: Restore Function (Sleep Apnea)            ║
║  • Neurological System: Improve Function (Alertness, Safety)     ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Generated Card Deck

```
╔══════════════════════════════════════════════════════════════════╗
║         BOBBY MARTINEZ - SMART CARD DECK                         ║
║         "Road to Health" Care Plan                               ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  🎯 Primary Clinical Goals:                                      ║
║     • BP <130/80 mmHg (within 3 months)                          ║
║     • A1c <7.0% (within 6 months)                                ║
║     • LDL <70 mg/dL (within 3 months)                            ║
║     • Diagnose & treat OSA (within 1 month)                      ║
║     • 10% weight loss (within 6 months)                          ║
║                                                                  ║
║  📊 Deck Statistics:                                             ║
║     • Total Cards: 14                                            ║
║     • Medical Cards: 9                                           ║
║     • Behavioral Cards: 5                                        ║
║     • Estimated Daily Time: ~45 minutes                          ║
║     • Estimated Monthly Cost: ~$85-120                           ║
║     • Overall Deck Feasibility: 72%                              ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝

┌──────────────────────────────────────────────────────────────────┐
│  MEDICAL CARDS (9)                                               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  💊 MEDICATIONS (4)                                              │
│  ├─ Card 1: Lisinopril 10mg Daily                               │
│  ├─ Card 2: Metformin 500mg BID → 1000mg BID                    │
│  ├─ Card 3: Atorvastatin 40mg Daily                             │
│  └─ Card 4: Acetaminophen 650mg PRN (replace ibuprofen)         │
│                                                                  │
│  🔬 DIAGNOSTIC TESTING (3)                                       │
│  ├─ Card 5: Home Blood Glucose Monitoring                        │
│  ├─ Card 6: Home Blood Pressure Monitoring                       │
│  └─ Card 7: Basic Metabolic Panel (4 weeks)                      │
│                                                                  │
│  🏥 PROCEDURES (1)                                               │
│  └─ Card 8: Home Sleep Test (HST)                                │
│                                                                  │
│  👨‍⚕️ REFERRALS (1)                                               │
│  └─ Card 9: Registered Dietitian Referral                        │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│  BEHAVIORAL CARDS (5)                                            │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  🥗 NUTRITION (2)                                                │
│  ├─ Card 10: Reduce Sugary Drinks                                │
│  └─ Card 11: Healthy Eating on the Road                          │
│                                                                  │
│  🏃 MOVEMENT (1)                                                 │
│  └─ Card 12: Walking Program (Start 10 min/day)                  │
│                                                                  │
│  📚 MICRO-LEARNING (2)                                           │
│  ├─ Card 13: Understanding Your Blood Sugar                      │
│  └─ Card 14: How Metformin Works                                 │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

# PART 3: COMPLETE SMART CARDS

Below are the fully-developed SMART Cards for Bobby's care plan, demonstrating the complete template format.

---

## CARD 1: Lisinopril 10mg Daily

### 📱 PATIENT-FACING VIEW

```
╔════════════════════════════════════════════════════════════════╗
║  ←  SMART Card                                            ⋮   ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  💊 Lisinopril 10mg                                            ║
║  Take one pill every morning                                   ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📍 WHAT YOU'RE DOING                                          ║
║  Take Lisinopril to lower your blood pressure and protect      ║
║  your heart and kidneys.                                       ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  💙 WHY THIS MATTERS TO YOU                                    ║
║  Bobby, your blood pressure is putting strain on your heart.   ║
║  Taking this medication helps you stay safe on the road and    ║
║  be around for those grandkids you're hoping to meet.          ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ✅ HOW TO DO IT                                               ║
║  • Take one 10mg pill by mouth every morning                   ║
║  • Swallow whole with water                                    ║
║  • You can take it with or without food                        ║
║  • Keep it in your truck cab - take it when you wake up        ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⏰ WHEN TO DO IT                                              ║
║  Once daily every morning | BP may improve in 1-2 weeks        ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⚠️  WHAT TO WATCH FOR                                         ║
║  🔴 CALL 911: Swelling in face, lips, or throat                ║
║  🟠 CALL DOCTOR: Bad cough that won't go away                  ║
║  🟠 CALL DOCTOR: Extreme dizziness or fainting                 ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  [  See Full Details  ]                                        ║
║                                                                ║
║  ┌────────────────────────────────────────────────────────┐   ║
║  │ ✓ I took this today                                    │   ║
║  └────────────────────────────────────────────────────────┘   ║
║                                                                ║
║  🔥 0-day streak                                               ║
║  M T W T F S S                                                 ║
║  ○ ○ ○ ○ ○ ○ ○                                                 ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

### 📋 FULL CLINICAL VIEW

---

#### WHAT

**Card Name**: Lisinopril 10mg Daily
**Card ID**: MED_CARDIO_ACE_001
**Card Type**: Medication (Tier 2) > Prescription Medications (Tier 3) > ACE Inhibitors (Tier 4)

- **Generic Name**: Lisinopril
- **Brand Names**: Prinivil, Zestril
- **Dose**: 10 mg
- **Formulation**: Oral tablet
- **Route**: PO (oral)
- **Frequency**: Once daily
- **Duration**: Ongoing (chronic therapy)

---

#### WHO

**Primary Actor**: Patient (self-administers)
**Support Actors**:
- MD/NP/PA (prescribes, adjusts dose)
- Pharmacist (dispenses, counsels)
- Wife (can help remind)

**Target Population**: Adults with hypertension

**Special Considerations**:
- Geriatric: Start at lower dose (2.5-5mg), monitor for orthostatic hypotension
- Renal Impairment: Bobby's eGFR is 78 - no adjustment needed; monitor
- Hepatic Impairment: No adjustment needed
- **Pregnancy**: Category D - CONTRAINDICATED (N/A for this patient)
- Breastfeeding: N/A

---

#### WHEN

- **Frequency**: Once daily
- **Duration**: Ongoing (lifelong for most patients)
- **Best Time**: Morning (consistent timing more important than specific time)
- **Missed Dose**: Take as soon as remembered; skip if close to next dose; never double up
- **Start Date**: Today (2024-11-23)

**Titration Tiers** (within same card):
```
Tier 1: 5mg daily (starting dose for sensitive patients)
Tier 2: 10mg daily (standard starting dose) ← CURRENT
  Advance if: BP still >130/80 after 4 weeks
Tier 3: 20mg daily (if BP not at goal)
  Advance if: BP still >130/80 after 4 more weeks
Tier 4: 40mg daily (maximum dose)
```

---

#### WHERE

- **Setting**: Home / Truck cab (daily self-administration)
- **Location-Specific**: Store at room temperature, keep in truck for consistency
- **Access**: Any pharmacy with valid prescription

---

#### WHY

**Clinical Goal** (Performance Medicine Framework):
- **Primary**: Cardiovascular System: Reduce Risk
- **Secondary**: Filtration/Urinary System: Protect Function (nephroprotection with diabetes)

**Patient's Personal Goal**:
"I want to keep driving trucks - it's my livelihood. I want to be around to meet my grandkids someday."

**Connection**:
Bobby, your blood pressure of 158/94 is Stage 2 hypertension. Combined with your new diabetes diagnosis, this significantly increases your risk of heart attack and stroke - the same thing that killed your father. This medication directly lowers that risk. By taking it consistently, you're protecting yourself so you can keep doing what you love and be there for your family.

**Mechanism of Action**:
Lisinopril blocks angiotensin-converting enzyme (ACE), which reduces angiotensin II production. This causes blood vessels to relax and widen, lowering blood pressure. It also protects your kidneys - especially important since diabetes can damage kidneys over time.

**Evidence**:
- Source: ACC/AHA 2017 Hypertension Guidelines, updated 2023
- Grade: **A** (Multiple high-quality RCTs)
- Summary: ACE inhibitors reduce cardiovascular events by 20-25% in hypertensive patients; first-line therapy for patients with diabetes

**Expected Timeline (Time-to-Benefit)**:
You should notice: Blood pressure starting to improve in about 1-2 weeks. Maximum effect in 4-6 weeks.

**DISCLAIMER**: These timelines are based on average patient outcomes. Your individual results may vary based on adherence, your body's response, other health conditions, medications, and lifestyle factors. If you're not seeing improvement in the expected timeframe, contact your care team.

---

#### HOW

**Detailed Step-by-Step Instructions**:
1. Take one 10mg tablet by mouth every morning
2. Swallow whole with a full glass of water (8 oz)
3. May take with or without food
4. Take at the same time each day for best results
5. Do not crush, chew, or break the tablet
6. Store at room temperature (68-77°F)

**Trucking-Specific Tips**:
- Keep medication in your cab, not the trailer (temperature extremes)
- Set your phone alarm for the same time every day
- Take it as part of your morning start-up routine before hitting the road

**Synergy Tips** (Do This WITH...):
- Pair with: Home BP Monitoring card (check BP before taking medication)
- Pair with: Metformin card (both help protect your kidneys)
- Stacks well with: Healthy Eating on the Road card
- Time-Saving Combo: Take Lisinopril and Metformin together with breakfast

---

#### MEASURE

**Tracking Method**:
- Primary: Blood pressure (systolic/diastolic in mmHg)
- Secondary: Symptoms (dizziness, cough), adherence

**Frequency**:
- BP: Daily (morning before medication) for first month, then 2-3x/week
- Labs: BMP at baseline, 4 weeks, then every 6 months

**Tools Needed**:
- Upper arm blood pressure cuff (validated device, ~$30-50)
- BP tracking app or logbook
- Pill organizer (recommended for truckers)

---

#### TARGET

**Primary Goal**:
- Systolic BP: <130 mmHg
- Diastolic BP: <80 mmHg
- Current: 158/94 → Goal: <130/80

**Timeline**: Achieve goal BP within 3 months

**Success Criteria**:
- BP at goal on ≥80% of readings
- No significant side effects
- Labs remain stable (K+ 3.5-5.0, Cr stable)
- Patient reports good adherence

---

#### SAFETY

**🟡 YELLOW - Common Side Effects** (Monitor, usually can continue):
- Dry cough (5-10%) - may persist; tell your doctor if bothersome
- Dizziness (3-5%) - usually improves; get up slowly
- Headache (3-4%) - usually mild and temporary
- Fatigue (2-3%) - often improves after first few weeks

**🟠 ORANGE - Stop/Hold & Contact Care Team If**:
- **Cardiovascular Signs**: Severe dizziness, fainting, chest pain
- **Filtration/Urinary Signs**: Decreased urination, blood in urine, significant leg swelling
- **Immune/Allergic Signs**: Rash, hives, itching (non-emergency allergic reaction)
- **Metabolic Signs**: Severe nausea, muscle weakness/cramps (may indicate high potassium)

**🔴 RED - Emergency - Call 911 Immediately**:
- **Angioedema**: Swelling of face, lips, tongue, or throat (rare but serious)
- Severe allergic reaction with difficulty breathing
- Loss of consciousness
- Chest pain with shortness of breath

**App Button Actions**:
- [🚨 Emergency Help] → Call 911
- [📞 Contact My Team] → Message care team
- [⚠️ Report Side Effect] → Log adverse event

**When to Contact Provider**:
- **Routine**: Questions about medication, minor side effects → next scheduled visit
- **Urgent**: Persistent cough affecting quality of life, leg swelling → call within 24 hours
- **Emergency**: Facial/throat swelling, difficulty breathing, fainting → call 911

**Contraindications**:
- Absolute: History of angioedema with ACE inhibitors, pregnancy, bilateral renal artery stenosis
- Relative: Hyperkalemia (K+ >5.5)

**Drug Interactions**:
- Major: **Avoid ibuprofen** (Bobby's been using this for back pain - reduces medication effectiveness and increases kidney risk)
- Major: Potassium supplements (hyperkalemia risk)
- Moderate: Metformin - both are fine together, but monitor kidney function

---

#### FOLLOW-UP

**Review Timeline**:
- **Week 1**: Phone call to assess tolerance
- **Week 2**: Office visit for BP check
- **Week 4**: Office visit + BMP lab; dose adjustment if needed
- **Month 3**: Full assessment

**Monitoring Schedule**:
- Week 1: Phone call - "How are you tolerating the medication?"
- Week 2: Office visit - check BP, review home readings
- Week 4: Office visit + BMP lab; consider dose adjustment
- Every 6 months: Routine monitoring, labs

**Action Based on Results**:
- At goal (BP <130/80): Continue current dose, maintain lifestyle changes
- Above goal: Titrate to 20mg if tolerated; add second agent if needed
- Side effects intolerable: Switch to ARB (losartan)

---

#### NOTES

**Evidence**:
- Source: ACC/AHA 2017/2023 Hypertension Guidelines
- Grade: A
- Summary: ACE inhibitors are first-line for hypertension with diabetes. First choice given Bobby's new T2DM diagnosis for renal protection.

**Feasibility/Actionability Score**: **82%**

Base Score: 100%
- Deductions:
  - Daily timing requirement: -5%
  - Monitoring required (BP + labs): -10%
  - Drug interaction counseling needed (ibuprofen): -5%
- Additions:
  - Low time burden (<1 min/day): +10%
  - Generic widely available: +5%
  - Insurance covered (Tier 1): +10%
  - High evidence grade: +5%
  - Previously uncomplicated med history: +2%

**Final Score: 82%** - Highly feasible, recommend strongly

**Patient Confidence Score**: [To be asked: "Bobby, on a scale of 0-10, how confident are you that you can take this pill every morning?"]

**Barriers Checklist**:
- [ ] Cost/affordability - Generic ~$10/month, insurance covers
- [x] Irregular schedule (trucking) - Addressed with alarm + cab storage
- [x] Multiple new medications - Simplified by taking together
- [x] NSAID use - Education needed, switch to acetaminophen

**Success Tips**:
- Set a daily alarm on your phone for the same time every morning
- Keep your medication in your truck cab where you'll see it
- Use a weekly pill organizer to track if you took your dose
- Take it at the same time as your other morning pills

**Access Information**:
- Cost: $ (Generic: $4-10/month)
- Insurance: Covered - Tier 1 generic
- Where to Get: Any pharmacy with prescription
- Alternative Options: If cough intolerable, ARBs (losartan) are alternatives

**Community Feedback** (Patient Reviews):
- ⭐ Average Rating: 4.2/5 (based on 1,247 reviews)
- Adherence Rate: 78% (patients who stuck with it >30 days)
- Target Achievement: 72% (patients who met BP goals within 3 months)

Top Patient Comments:
- "Easy to take, no major issues. BP came down in 3 weeks." - Mike, 58
- "Had a dry cough for a month but it went away. Worth it for my numbers." - James, 55

Patient-Generated Tags: #Easy (892) #Affordable (756) #WorkedForMe (623)

---

#### METADATA

**Tags**:
- #ChronicManagement
- #ACC_AHA_GradeA
- #Home
- #Adult
- #Hypertension
- #Cardiovascular
- #Diabetes
- #Affordable
- #Easy

**Evidence Grade**: A

**Feasibility Score**: 82%

**Version**: v1.0

**Last Updated**: 2024-11-23

**Next Review**: 2025-05-23

---

## CARD 2: Metformin 500mg BID (with Titration to 1000mg BID)

### 📱 PATIENT-FACING VIEW

```
╔════════════════════════════════════════════════════════════════╗
║  ←  SMART Card                                            ⋮   ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  💊 Metformin 500mg                                            ║
║  Take with breakfast and dinner                                ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📍 WHAT YOU'RE DOING                                          ║
║  Take Metformin to lower your blood sugar and help your        ║
║  body use insulin better.                                      ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  💙 WHY THIS MATTERS TO YOU                                    ║
║  Bobby, your blood sugar is high enough that you now have      ║
║  diabetes - just like your father and brother. This medicine   ║
║  is the #1 treatment to control it. Managing your sugar now    ║
║  helps you stay alert on the road and avoid the complications  ║
║  that affected your dad.                                       ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ✅ HOW TO DO IT                                               ║
║  • Take one 500mg pill with breakfast                          ║
║  • Take one 500mg pill with dinner                             ║
║  • ALWAYS take with food (prevents stomach upset)              ║
║  • After 2 weeks, dose may increase to 1000mg twice daily      ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⏰ WHEN TO DO IT                                              ║
║  Twice daily with meals | Blood sugar may improve in 2-4 wks   ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⚠️  WHAT TO WATCH FOR                                         ║
║  🟡 COMMON: Upset stomach, loose stools (usually improves)     ║
║  🟠 CALL DOCTOR: Severe stomach pain, extreme tiredness        ║
║  🔴 CALL 911: Trouble breathing, muscle pain, confusion        ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  [  See Full Details  ]                                        ║
║                                                                ║
║  ┌────────────────────────────────────────────────────────┐   ║
║  │ ○ Morning dose    ○ Evening dose                       │   ║
║  └────────────────────────────────────────────────────────┘   ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

### 📋 FULL CLINICAL VIEW

---

#### WHAT

**Card Name**: Metformin 500mg BID → 1000mg BID
**Card ID**: MED_DM_BIG_001
**Card Type**: Medication (Tier 2) > Prescription Medications (Tier 3) > Diabetes > Biguanides (Tier 4)

- **Generic Name**: Metformin Hydrochloride
- **Brand Names**: Glucophage, Glumetza, Fortamet
- **Starting Dose**: 500 mg twice daily
- **Target Dose**: 1000 mg twice daily (titrate over 2-4 weeks)
- **Formulation**: Oral tablet (can switch to ER if GI intolerance)
- **Route**: PO (oral)
- **Frequency**: Twice daily with meals

---

#### WHO

**Primary Actor**: Patient (self-administers)
**Support Actors**:
- MD/NP/PA (prescribes, adjusts dose)
- Pharmacist (dispenses, counsels)
- Wife (meal planning support)

**Target Population**: Adults with Type 2 Diabetes

**Special Considerations**:
- **Renal Impairment**: Bobby's eGFR is 78 - safe to use. If eGFR drops <30, discontinue
- Hepatic Impairment: Use with caution; avoid if significant liver disease
- **Hold for contrast**: If Bobby gets imaging with IV contrast, hold metformin for 48 hours after
- B12 deficiency: Check B12 levels annually (metformin can cause deficiency)

---

#### WHEN

- **Frequency**: Twice daily
- **Duration**: Ongoing
- **Best Time**: With breakfast and dinner (food reduces GI side effects by 50%)
- **Missed Dose**: Take with next meal; don't double up

**Titration Tiers**:
```
Tier 1: 500mg once daily with dinner (if GI sensitive) - 1 week
Tier 2: 500mg BID with meals ← STARTING HERE
  Advance if: Tolerated after 1-2 weeks
Tier 3: 1000mg AM / 500mg PM with meals
  Advance if: A1c not at goal after 2 weeks
Tier 4: 1000mg BID with meals (TARGET DOSE)
  Maximum: 2550mg/day if needed
```

---

#### WHY

**Clinical Goal** (Performance Medicine Framework):
- **Primary**: Metabolic System: Improve Function (glucose regulation)
- **Secondary**: Cardiovascular System: Reduce Risk (metformin has CV benefits)

**Patient's Personal Goal**:
"I want to be around to meet my grandkids someday." "I don't want to end up like my dad."

**Connection**:
Bobby, your A1c of 7.2% means you have type 2 diabetes. Your father died from a heart attack at 68, and your brother also has diabetes. Metformin is the #1 medicine we start with because it works well, is affordable, and actually helps protect your heart - not just your sugar. Taking this consistently is one of the best things you can do to avoid your father's fate.

**Mechanism of Action**:
Metformin works in three ways: (1) It reduces how much sugar your liver makes, (2) It helps your muscles use insulin better, and (3) It slows sugar absorption from your food. Unlike some diabetes medicines, it doesn't cause low blood sugar or weight gain - it may actually help with weight loss.

**Evidence**:
- Source: ADA Standards of Care 2024; UKPDS Trial
- Grade: **A** (Extensive RCT evidence)
- Summary: First-line therapy for T2DM. Reduces A1c by 1-1.5%, reduces CV events by 32% in overweight diabetics (UKPDS). Proven safe for 60+ years.

**Expected Timeline**:
- Blood sugar improvement: 2-4 weeks
- Maximum A1c reduction: 3 months

---

#### HOW

**Detailed Step-by-Step Instructions**:
1. Take one 500mg tablet with breakfast
2. Take one 500mg tablet with dinner
3. **ALWAYS take with food** - this prevents stomach upset
4. Swallow whole with water
5. After 2 weeks (if tolerating well), dose will increase
6. Store at room temperature

**Trucking-Specific Tips**:
- Pack enough medication for your entire haul
- Always eat something when you take it (even a protein bar counts)
- Keep crackers in the cab for queasy days

**Synergy Tips**:
- Pair with: Lisinopril card (both protect kidneys - powerful combo)
- Pair with: Home Glucose Monitoring (see if it's working)
- Pair with: Reduce Sugary Drinks card (cutting sodas makes metformin work better)

---

#### MEASURE

**Tracking Method**:
- Primary: Fasting blood glucose (fingerstick)
- Secondary: A1c (every 3 months until stable, then every 6 months)

**Frequency**:
- Fasting glucose: Daily initially (first 2 weeks), then 2-3x/week
- A1c: At 3 months, then every 6 months if stable

**Tools Needed**:
- Blood glucose meter + test strips
- Lancets
- A1c lab order (covered by insurance)

---

#### TARGET

**Primary Goal**:
- A1c: <7.0% (currently 7.2%)
- Fasting glucose: 80-130 mg/dL (currently 142 mg/dL)

**Timeline**: A1c at goal within 3-6 months

**Success Criteria**:
- A1c <7.0%
- Fasting glucose consistently 80-130 mg/dL
- No hypoglycemia (metformin rarely causes this)
- GI side effects manageable
- No lactic acidosis symptoms

---

#### SAFETY

**🟡 YELLOW - Common Side Effects** (Monitor, usually improve):
- Stomach upset, nausea (30-50%) - **improves over 2-4 weeks**
- Diarrhea (10-30%) - **take with food to minimize**
- Metallic taste (3-5%)
- Gas, bloating

**Tip**: GI side effects are VERY common at first but almost always get better. Take with food, start low, go slow.

**🟠 ORANGE - Contact Care Team If**:
- GI symptoms don't improve after 4 weeks
- Severe stomach pain
- Extreme tiredness out of proportion
- Getting imaging with IV contrast (hold metformin)

**🔴 RED - Emergency - Call 911** (Lactic Acidosis - Very Rare):
- Trouble breathing
- Severe muscle pain
- Unusual sleepiness or weakness
- Feeling very cold
- Dizziness, lightheadedness
- Slow or irregular heartbeat

**Note**: Lactic acidosis is extremely rare (1 in 30,000) but serious. Most common in people with kidney failure or severe dehydration.

**Contraindications**:
- Absolute: eGFR <30, acute kidney injury, liver failure
- Relative: Heavy alcohol use (increases lactic acidosis risk), upcoming surgery/contrast

**Drug Interactions**:
- Lisinopril: Both fine together, both help kidneys
- Alcohol: Limit to 1-2 drinks (increases lactic acidosis risk)
- Ibuprofen: Avoid - can reduce kidney function

---

#### FOLLOW-UP

**Monitoring Schedule**:
- Week 1: Phone check-in on GI tolerance
- Week 2: If tolerating, increase to 1000mg BID
- Week 4: Office visit, review glucose logs
- Month 3: A1c recheck, full assessment

**Action Based on Results**:
- A1c at goal: Continue current therapy, maintain lifestyle
- A1c still elevated: Consider adding second agent (likely GLP-1 given weight)
- GI intolerable: Switch to extended-release (ER) formulation

---

#### NOTES

**Evidence Grade**: A

**Feasibility Score**: 75%

Base Score: 100%
- Deductions:
  - GI side effects common: -15%
  - Twice daily dosing: -5%
  - Glucose monitoring required: -10%
- Additions:
  - Very affordable ($4-10/month): +10%
  - Proven weight neutral/loss: +10%
  - Bobby motivated (family history): +10%
  - No hypoglycemia risk: +5%

**Patient Confidence**: [To assess]

**Barriers**:
- [x] GI side effects - Counseled on temporary nature, take with food
- [x] Twice daily dosing - Pair with meals (breakfast/dinner)
- [ ] Glucose monitoring learning curve - Diabetes education referral

**Access Information**:
- Cost: $ ($4-10/month generic)
- Insurance: Covered - Tier 1
- Alternative: Extended-release if GI intolerant

---

#### METADATA

**Tags**: #Diabetes #Metabolic #FirstLine #ChronicManagement #ADA_GradeA #Affordable

**Evidence Grade**: A

**Feasibility Score**: 75%

**Version**: v1.0

**Last Updated**: 2024-11-23

---

## CARD 8: Home Sleep Test (HST)

### 📱 PATIENT-FACING VIEW

```
╔════════════════════════════════════════════════════════════════╗
║  ←  SMART Card                                            ⋮   ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  🏥 Home Sleep Test                                            ║
║  Wear a device overnight to check for sleep apnea              ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📍 WHAT YOU'RE DOING                                          ║
║  Wearing a small device while you sleep at home to see if      ║
║  you stop breathing during sleep (sleep apnea).                ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  💙 WHY THIS MATTERS TO YOU                                    ║
║  Bobby, your tiredness, snoring, and near-miss on the road     ║
║  are serious warning signs. This test will show us if you're   ║
║  stopping breathing at night - which could explain everything. ║
║  YOUR CDL LICENSE AND LIVELIHOOD DEPEND ON THIS TEST.          ║
║  Untreated sleep apnea can disqualify you from driving.        ║
║  Getting diagnosed and treated keeps you on the road safely.   ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ✅ HOW TO DO IT                                               ║
║  1. Pick up the device from the sleep center                   ║
║  2. Sleep at home wearing the device for 1-2 nights            ║
║  3. Return the device the next day                             ║
║  4. Results in 3-5 business days                               ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⏰ TIMING                                                     ║
║  URGENT - Complete within 1 week | Results in 3-5 days         ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📋 PREPARATION                                                ║
║  • Sleep in your own bed (or truck sleeper if needed)          ║
║  • Avoid alcohol on test night                                 ║
║  • Don't take sleeping pills                                   ║
║  • Follow normal sleep routine                                 ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

### 📋 FULL CLINICAL VIEW

---

#### WHAT

**Card Name**: Home Sleep Test (Home Sleep Apnea Testing)
**Card ID**: PROC_DX_014
**Card Type**: Procedure (Tier 2) > Diagnostic Procedure (Tier 3) > Sleep Study (Tier 4)

- **Procedure**: Home Sleep Apnea Test (HSAT)
- **CPT Code**: 95806
- **Device Types**: WatchPAT, ApneaLink, various FDA-cleared devices

---

#### WHO

**Primary Actor**: Patient (self-administers device)
**Support Actors**:
- Sleep center staff (provides device, instructions)
- Sleep physician (interprets results)
- PCP (orders test, follows up)

**Target Population**: Adults with high pre-test probability of moderate-severe OSA

**Bobby's Pre-Test Probability**:
- STOP-BANG Score: 7/8 (HIGH RISK)
- Very high likelihood of moderate-severe OSA

---

#### WHEN

- **Urgency**: **URGENT** - Complete within 1 week
- **Reason for urgency**: Commercial driver with near-miss accident, DOT safety concern
- **Duration**: 1-2 nights of home testing
- **Results timeline**: 3-5 business days

---

#### WHERE

- **Device Pickup**: [Local sleep center - to be assigned]
- **Testing Location**: Patient's home or truck sleeper cab
- **Device Return**: Return to sleep center within 24 hours of test

---

#### WHY

**Clinical Goal** (Performance Medicine Framework):
- **Primary**: Respiratory System: Diagnose Dysfunction (OSA)
- **Secondary**: Neurological System: Identify Risk (drowsy driving)
- **Secondary**: Cardiovascular System: Identify Risk (OSA increases CV events)

**Patient's Personal Goal**:
"I want to keep driving trucks - it's my livelihood."

**Connection**:
Bobby, everything you've described - the exhaustion, the loud snoring, your wife seeing you stop breathing, the near-miss accident - points to sleep apnea. This isn't just about feeling tired. The FMCSA (Federal Motor Carrier Safety Administration) requires commercial drivers with untreated sleep apnea to be disqualified. **The GOOD NEWS**: If we diagnose it and you use treatment (CPAP), you can keep driving. This test protects your job.

**Why This Matters for Your CDL**:
- Untreated moderate-severe OSA = Medical disqualification
- Treated OSA with documented CPAP compliance = Can drive
- This test is the first step to keeping your license

**Evidence**:
- Source: AASM Clinical Practice Guidelines 2017
- Grade: **A** for diagnosis of moderate-severe OSA in high-probability patients
- Summary: HST has 85-90% sensitivity for moderate-severe OSA. Appropriate for Bobby given high pre-test probability and no comorbidities requiring in-lab PSG.

---

#### HOW

**Step-by-Step Instructions**:

**Day Before:**
1. Pick up device from sleep center
2. Watch instruction video provided
3. Practice putting on the device

**Night of Test:**
1. Follow your normal evening routine
2. Avoid alcohol and sleeping pills
3. Go to bed at your usual time
4. Apply the device per instructions:
   - Finger probe (oxygen sensor)
   - Chest strap (breathing effort)
   - Nasal cannula (airflow)
5. Press "Start" button
6. Sleep normally through the night
7. In the morning, press "Stop" and remove device

**Next Day:**
1. Return device to sleep center
2. Results interpreted within 3-5 business days
3. Follow-up call to discuss results

**Tips for Truckers:**
- Can do test in truck sleeper cab if needed
- Pick a night when you're home if possible
- Device is portable and easy to use

---

#### MEASURE

**What the Test Measures**:
- **AHI (Apnea-Hypopnea Index)**: Number of breathing pauses per hour
- **Oxygen Desaturation**: How low your oxygen drops
- **Sleep time**: Hours of recorded data

**Interpretation**:
| AHI | Severity | Meaning |
|-----|----------|---------|
| <5 | Normal | No sleep apnea |
| 5-14 | Mild | Some events, may not need CPAP |
| 15-29 | Moderate | Significant OSA, CPAP recommended |
| ≥30 | Severe | Serious OSA, CPAP required |

---

#### TARGET

**Diagnostic Goal**: Obtain interpretable study (≥4 hours sleep data)

**Expected Finding**: Given Bobby's STOP-BANG 7/8, very likely moderate-severe OSA (AHI ≥15)

**Next Steps Based on Results**:
- If AHI ≥15: Start CPAP therapy, DOT certification process
- If AHI 5-14: Discuss treatment options, positional therapy
- If AHI <5: Consider alternative diagnoses for fatigue
- If study non-diagnostic: May need in-lab polysomnography

---

#### SAFETY

**🟢 The test itself is very safe**

**Minor Issues**:
- Mild skin irritation from straps
- Difficulty sleeping with device (common first night)
- Device may come off during sleep (may need repeat)

**No Emergency Concerns** - This is a diagnostic test only

**Important Notes**:
- Continue all current medications
- Continue CPAP if already using one (this is new diagnosis)
- If you feel extremely unsafe to drive, do not drive until evaluated

---

#### FOLLOW-UP

**Timeline**:
- **Day 1-2**: Complete test, return device
- **Day 3-7**: Results reviewed by sleep physician
- **Day 7-10**: Follow-up call with results and treatment plan

**If OSA Confirmed (Likely)**:
- CPAP titration study or auto-CPAP prescribed
- DOT certification process initiated
- Follow-up in 30 days to assess compliance
- Letter for DOT medical examiner

**Critical for CDL**:
- Document CPAP usage ≥4 hours/night for 70% of nights
- This compliance data is required for medical certification
- Most truckers successfully continue driving with treatment

---

#### NOTES

**Evidence Grade**: A

**Feasibility Score**: 88%

Base Score: 100%
- Deductions:
  - Requires picking up/returning device: -5%
  - May need to do at home (scheduling): -5%
  - Small learning curve: -2%
- Additions:
  - High patient motivation (job depends on it): +20%
  - Insurance covers: +10%
  - Quick turnaround: +5%
  - Can do in truck if needed: +5%

**DOT/CDL Specific Information**:
- FMCSA allows CDL drivers with treated OSA to drive
- Must demonstrate CPAP compliance
- Annual recertification required
- Many trucking companies have OSA programs

**Access Information**:
- Cost: Usually covered by insurance; ~$150-300 self-pay
- Insurance: Covered with diagnosis of suspected OSA
- Where: Order sent to [local sleep center]

---

#### METADATA

**Tags**: #OSA #Diagnostic #Urgent #CDL #Respiratory #Sleep

**Evidence Grade**: A

**Feasibility Score**: 88%

**Version**: v1.0

**Last Updated**: 2024-11-23

---

## CARD 10: Reduce Sugary Drinks

### 📱 PATIENT-FACING VIEW

```
╔════════════════════════════════════════════════════════════════╗
║  ←  SMART Card                                            ⋮   ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  🥗 Reduce Sugary Drinks                                       ║
║  Cut back from 3-4 sodas/day to 1 or less                      ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📍 WHAT YOU'RE DOING                                          ║
║  Replacing sodas and sugary drinks with water, unsweetened     ║
║  tea, or zero-sugar options.                                   ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  💙 WHY THIS MATTERS TO YOU                                    ║
║  Bobby, you're drinking 3-4 sodas a day - that's about 120-    ║
║  160 grams of PURE SUGAR daily, just from drinks. That's like  ║
║  eating 30-40 sugar cubes every day. This is the single        ║
║  biggest thing spiking your blood sugar. Cutting this alone    ║
║  could drop your A1c significantly - possibly even avoid       ║
║  needing more diabetes medication.                             ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ✅ HOW TO DO IT                                               ║
║  Week 1-2: Cut from 4 sodas → 2 sodas per day                  ║
║  Week 3-4: Cut from 2 sodas → 1 soda per day                   ║
║  Week 5+:  Get to ≤1 soda per day (or zero!)                   ║
║                                                                ║
║  🔄 SWAP IDEAS:                                                ║
║  • Soda → Water with lemon/lime                                ║
║  • Soda → Diet/Zero-sugar soda (stepping stone)                ║
║  • Soda → Unsweetened iced tea                                 ║
║  • Soda → Sparkling water (La Croix, Bubly)                    ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ⏰ WHEN                                                       ║
║  Every day, all day | You may notice energy improvement in     ║
║  1-2 weeks, blood sugar improvement in 2-4 weeks               ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📊 TRACK YOUR PROGRESS                                        ║
║  ┌─────────────────────────────────────────────────────────┐  ║
║  │  Today's sodas: [ 0 ] [ 1 ] [ 2 ] [ 3 ] [ 4+ ]          │  ║
║  └─────────────────────────────────────────────────────────┘  ║
║                                                                ║
║  This week: ▓▓▓▓▓▓▓░░░ 70% days at goal                       ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

### 📋 FULL CLINICAL VIEW

---

#### WHAT

**Card Name**: Reduce Sugary Drinks
**Card ID**: NUT_RED_002
**Card Type**: Nutrition (Tier 2) > Reduce Harmful Foods (Tier 3) > Added Sugars (Tier 4)

**Specific Action**: Reduce sugar-sweetened beverage intake from 3-4 per day to ≤1 per day

**Current State**: ~3-4 sodas/day = 120-160g added sugar from beverages alone
**Goal State**: ≤1 soda/day = ≤40g added sugar from beverages

---

#### WHO

**Primary Actor**: Patient (Bobby)
**Support Actors**:
- Wife (support at home, not buying sodas)
- Dietitian (detailed meal planning - referral placed)

---

#### WHEN

**Frequency**: Daily behavior change

**Progression Tiers**:
```
Tier 0 (If struggling): Allow 3 sodas/day, swap 1 for water
Tier 1 (Weeks 1-2): 2 sodas/day max ← START HERE
Tier 2 (Weeks 3-4): 1 soda/day max
Tier 3 (Week 5+): 0-1 sodas/day (maintenance)
```

**Expected Timeline**:
- Energy improvement: 1-2 weeks
- Blood sugar improvement: 2-4 weeks
- Weight change: 4-8 weeks (if consistent)

---

#### WHY

**Clinical Goal** (Performance Medicine Framework):
- **Primary**: Metabolic System: Improve Function (glucose control)
- **Secondary**: Metabolic System: Improve Structure (weight loss)

**Patient's Personal Goal**:
"I've tried every diet, nothing sticks."

**Connection**:
Bobby, I know diets haven't worked before. But here's the thing - we're not talking about a complicated diet. We're talking about ONE change that could have MASSIVE impact. You're drinking about 600+ calories of pure sugar every day just from sodas. That's:
- 30-40 sugar cubes per day
- 4-5 pounds of sugar per month
- Straight to your bloodstream, spiking your glucose

This single change - just swapping drinks - could:
- Lower your A1c by 0.3-0.5%
- Help you lose 1-2 lbs/month without any other changes
- Reduce your fatigue (sugar crashes)
- Work WITH your metformin, not against it

**Evidence**:
- Source: ADA Nutrition Therapy Guidelines 2023
- Grade: **A**
- Summary: Reducing sugar-sweetened beverages improves glycemic control, reduces weight, and lowers cardiovascular risk in patients with T2DM.

---

#### HOW

**Detailed Step-by-Step Instructions**:

**Week 1-2: Half Your Intake**
1. Count how many sodas you drink today (baseline)
2. Tomorrow, stop at HALF that number
3. For each soda you skip, drink water or diet soda instead
4. If you're at 4/day, go to 2/day
5. Track daily using the app

**Week 3-4: Get to One**
1. Continue reducing
2. Allow yourself ONE soda per day - make it count
3. Pick your favorite time (with lunch? End of day?)
4. Everything else = water, diet soda, unsweetened tea

**Trucking-Specific Tips**:
- Stock your cooler with water bottles and diet sodas
- Buy a big insulated cup for water/tea
- Gas stations sell diet options and water - choose those
- Unsweetened iced tea is available at most stops

**Swap Guide**:
| Instead of... | Try... |
|---------------|--------|
| Regular Coke | Coke Zero, Diet Coke |
| Mountain Dew | Mtn Dew Zero, water with caffeine pills |
| Sweet tea | Unsweetened tea + squeeze of lemon |
| Energy drinks | Sugar-free energy drinks or black coffee |
| Any soda | Sparkling water (La Croix, Bubly) |

**Synergy Tips**:
- Pair with: Metformin card (both help control blood sugar)
- Pair with: Home Glucose Monitoring (see the improvement!)
- Pair with: Healthy Eating on the Road card

---

#### MEASURE

**Tracking Method**:
- Primary: Number of sugary drinks per day
- Secondary: Blood glucose readings, energy level, weight

**Frequency**: Daily tracking of beverages

**Tools**: App tracking, simple tally

---

#### TARGET

**Primary Goal**: ≤1 sugar-sweetened beverage per day

**Timeline**: Achieve within 4 weeks

**Success Criteria**:
- ≤1 soda/day on ≥80% of days
- Measurable improvement in fasting glucose
- Patient reports sustainable change

---

#### SAFETY

**🟢 This is a LOW-RISK intervention**

**Possible Adjustment Effects**:
- Caffeine withdrawal headaches (if sodas were main caffeine source) - temporary, 3-5 days
- Initial cravings - strongest days 3-7, then improve
- May feel less satisfied initially - normal, brain adjusts

**Tips for Cravings**:
- Diet sodas are fine as a bridge
- The taste preference WILL change over 2-3 weeks
- Drink water first when craving hits
- Allow yourself one regular soda if you really need it - don't give up

---

#### FOLLOW-UP

**Self-Monitoring**: Daily tracking in app

**Check-ins**:
- Week 2: Dietitian call (included in referral)
- Week 4: Office visit - review glucose, weight

**Action Based on Results**:
- Succeeding: Celebrate! Consider next nutrition goal
- Struggling: Identify specific barriers, adjust approach
- Caffeine issue: May need to address separately

---

#### NOTES

**Evidence Grade**: A

**Feasibility Score**: 68%

Base Score: 100%
- Deductions:
  - Significant habit change: -15%
  - Requires daily vigilance: -10%
  - Caffeine withdrawal possible: -5%
  - Limited options at truck stops: -10%
  - Strong cravings expected: -10%
- Additions:
  - Zero cost (saves money!): +15%
  - Diet alternatives available: +10%
  - High impact if achieved: +10%
  - Patient acknowledged this is a problem: +5%
  - Wife can support at home: +5%

**Money Saved**:
- Current: ~$6-8/day on sodas = $180-240/month
- Goal: ~$1-2/day = $30-60/month
- **Savings: $120-180/month!**

**Barriers Addressed**:
- [x] Caffeine dependence - Diet options have caffeine
- [x] Taste preference - Will change over 2-3 weeks
- [x] Truck stop availability - Diet options available everywhere
- [ ] Habit strength - May need ongoing support

---

#### METADATA

**Tags**: #Nutrition #Diabetes #Metabolic #HighImpact #ZeroCost #Behavioral

**Evidence Grade**: A

**Feasibility Score**: 68%

**Version**: v1.0

**Last Updated**: 2024-11-23

---

## CARD 13: Understanding Your Blood Sugar (Micro-Learning)

### 📱 PATIENT-FACING VIEW

```
╔════════════════════════════════════════════════════════════════╗
║  ←  SMART Card - Learn                                    ⋮   ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  📚 Understanding Your Blood Sugar                             ║
║  5-minute lesson                                               ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  🎯 WHAT YOU'LL LEARN                                          ║
║  • What blood sugar numbers mean                               ║
║  • Why your numbers matter for trucking                        ║
║  • What your A1c of 7.2% tells us                              ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📖 THE BASICS                                                 ║
║                                                                ║
║  Blood sugar (glucose) is fuel for your body - like diesel     ║
║  for your truck. But unlike a truck, too much fuel in your     ║
║  blood causes damage over time.                                ║
║                                                                ║
║  YOUR NUMBERS:                                                 ║
║  ┌─────────────────────────────────────────────────────────┐  ║
║  │  Fasting glucose: 142 mg/dL                             │  ║
║  │  Normal: 70-99 | Pre-diabetes: 100-125 | Diabetes: 126+ │  ║
║  │  Your number: DIABETES RANGE                            │  ║
║  └─────────────────────────────────────────────────────────┘  ║
║                                                                ║
║  ┌─────────────────────────────────────────────────────────┐  ║
║  │  A1c: 7.2%                                               │  ║
║  │  Normal: <5.7% | Pre-diabetes: 5.7-6.4% | Diabetes: 6.5+│  ║
║  │  Your number: DIABETES RANGE                            │  ║
║  │                                                          │  ║
║  │  A1c shows your AVERAGE blood sugar over 3 months.       │  ║
║  │  Think of it like your "average MPG" for blood sugar.    │  ║
║  └─────────────────────────────────────────────────────────┘  ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  🚛 WHY THIS MATTERS FOR DRIVING                               ║
║                                                                ║
║  High blood sugar can cause:                                   ║
║  • Fatigue (you've been feeling this!)                         ║
║  • Blurred vision                                              ║
║  • Slow reaction times                                         ║
║  • Poor concentration                                          ║
║                                                                ║
║  Controlled blood sugar = Safer driving = Keep your CDL        ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  ✅ KNOWLEDGE CHECK                                            ║
║                                                                ║
║  Q: What does A1c measure?                                     ║
║  ○ A) Blood sugar right now                                    ║
║  ○ B) Average blood sugar over 3 months                        ║
║  ○ C) How much insulin you make                                ║
║                                                                ║
║  [Check Answer]                                                ║
║                                                                ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                ║
║  📚 RELATED LEARNING:                                          ║
║  → How Metformin Works (Card 14)                               ║
║  → Understanding Carbohydrates                                 ║
║                                                                ║
║  [✓ Mark as Completed]                                         ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

# PART 4: DECK SYNERGY & DAILY ROUTINE

## How Bobby's Cards Work Together

```
╔══════════════════════════════════════════════════════════════════╗
║                     CARD SYNERGY MAP                             ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  ┌──────────────┐      ┌──────────────┐      ┌──────────────┐   ║
║  │  Lisinopril  │──────│  Metformin   │──────│ Atorvastatin │   ║
║  │  (BP)        │      │  (Sugar)     │      │ (Cholesterol)│   ║
║  └──────────────┘      └──────────────┘      └──────────────┘   ║
║         │                    │                      │            ║
║         │                    │                      │            ║
║         └────────────────────┼──────────────────────┘            ║
║                              │                                   ║
║                              ▼                                   ║
║                    ┌──────────────────┐                          ║
║                    │  CARDIOVASCULAR  │                          ║
║                    │  RISK REDUCTION  │                          ║
║                    │  (All 3 protect  │                          ║
║                    │   the heart)     │                          ║
║                    └──────────────────┘                          ║
║                              │                                   ║
║         ┌────────────────────┼────────────────────┐              ║
║         │                    │                    │              ║
║         ▼                    ▼                    ▼              ║
║  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐       ║
║  │  Home BP     │    │ Home Glucose │    │   Labs       │       ║
║  │  Monitoring  │    │  Monitoring  │    │   (BMP)      │       ║
║  └──────────────┘    └──────────────┘    └──────────────┘       ║
║         │                    │                    │              ║
║         └────────────────────┴────────────────────┘              ║
║                              │                                   ║
║                              ▼                                   ║
║                    ┌──────────────────┐                          ║
║                    │     TRACKING     │                          ║
║                    │  (See if it's    │                          ║
║                    │   working!)      │                          ║
║                    └──────────────────┘                          ║
║                                                                  ║
║  ════════════════════════════════════════════════════════════   ║
║                                                                  ║
║  ┌──────────────┐      ┌──────────────┐      ┌──────────────┐   ║
║  │ Home Sleep   │──────│    CPAP      │──────│   Energy     │   ║
║  │    Test      │      │  (if needed) │      │  Improvement │   ║
║  └──────────────┘      └──────────────┘      └──────────────┘   ║
║         │                                           │            ║
║         └───────────────────────────────────────────┘            ║
║                              │                                   ║
║                              ▼                                   ║
║                    ┌──────────────────┐                          ║
║                    │   SAFE DRIVING   │                          ║
║                    │   KEEP CDL       │                          ║
║                    └──────────────────┘                          ║
║                                                                  ║
║  ════════════════════════════════════════════════════════════   ║
║                                                                  ║
║  ┌──────────────┐      ┌──────────────┐      ┌──────────────┐   ║
║  │ Cut Sodas    │──────│ Healthy Road │──────│  Walking     │   ║
║  │              │      │   Eating     │      │  Program     │   ║
║  └──────────────┘      └──────────────┘      └──────────────┘   ║
║         │                    │                      │            ║
║         └────────────────────┴──────────────────────┘            ║
║                              │                                   ║
║                              ▼                                   ║
║                    ┌──────────────────┐                          ║
║                    │   WEIGHT LOSS    │                          ║
║                    │  BLOOD SUGAR     │                          ║
║                    │    CONTROL       │                          ║
║                    └──────────────────┘                          ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Bobby's Daily Routine with SMART Cards

```
══════════════════════════════════════════════════════════════════
                    DAILY ROUTINE INTEGRATION
══════════════════════════════════════════════════════════════════

⏰ MORNING (Before Starting Drive) - 15 minutes
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  1. Check blood sugar (fasting)              📊 Card 5    [2 min]
  2. Check blood pressure                     📊 Card 6    [3 min]
  3. Take medications WITH breakfast:
     • Lisinopril 10mg                        💊 Card 1    [30 sec]
     • Metformin 500mg                        💊 Card 2    [30 sec]
     • Atorvastatin 40mg                      💊 Card 3    [30 sec]
  4. Log everything in app                                 [2 min]
  5. Fill water bottles for the day           🥗 Card 10   [2 min]
  6. Quick walk around truck (pre-trip + steps) 🏃 Card 12 [5 min]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🚛 ON THE ROAD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  • Drink water instead of soda              🥗 Card 10
  • At rest stops:
    - Walk around truck 2-3 times           🏃 Card 12   [5-10 min]
    - Choose healthier food options         🥗 Card 11
    - Use bathroom (staying hydrated!)
  • Lunch: Take Metformin with meal         💊 Card 2

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🌙 EVENING (After Day's Drive) - 10 minutes
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  1. Check blood pressure                     📊 Card 6    [3 min]
  2. Take Metformin with dinner              💊 Card 2    [30 sec]
  3. Log day's readings and adherence                     [2 min]
  4. Review one Micro-Learning card          📚 Card 13/14 [5 min]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📅 WEEKLY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  • Review weekly BP and glucose averages
  • Stock truck with healthy snacks and water
  • Refill pill organizer for the week
  • Check in with wife on progress

══════════════════════════════════════════════════════════════════

TOTAL DAILY TIME INVESTMENT: ~35-40 minutes
TOTAL MONTHLY COST: ~$85-120 (medications + supplies)

══════════════════════════════════════════════════════════════════
```

---

# PART 5: EXPECTED OUTCOMES

## 3-Month Projection

```
╔══════════════════════════════════════════════════════════════════╗
║                    EXPECTED OUTCOMES                             ║
║                    Bobby Martinez                                ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  IF BOBBY FOLLOWS HIS SMART CARD DECK:                          ║
║                                                                  ║
║  ┌────────────────────────────────────────────────────────────┐ ║
║  │  BLOOD PRESSURE                                            │ ║
║  │  ──────────────────────────────────────────────────────── │ ║
║  │  Current:  158/94 mmHg (Stage 2 HTN)                       │ ║
║  │  Month 1:  ~145/88 mmHg                                    │ ║
║  │  Month 3:  ~130/82 mmHg (NEAR GOAL)                        │ ║
║  │  Goal:     <130/80 mmHg                                    │ ║
║  │                                                            │ ║
║  │  Contributors:                                              │ ║
║  │  • Lisinopril: -10-15 mmHg                                  │ ║
║  │  • Weight loss (if achieved): -5-10 mmHg                    │ ║
║  │  • Reduced sodium (cutting sodas): -3-5 mmHg                │ ║
║  │  • Walking: -3-5 mmHg                                       │ ║
║  └────────────────────────────────────────────────────────────┘ ║
║                                                                  ║
║  ┌────────────────────────────────────────────────────────────┐ ║
║  │  BLOOD SUGAR (A1c)                                         │ ║
║  │  ──────────────────────────────────────────────────────── │ ║
║  │  Current:  7.2%                                             │ ║
║  │  Month 3:  ~6.5-6.8%                                        │ ║
║  │  Goal:     <7.0%                                            │ ║
║  │                                                            │ ║
║  │  Contributors:                                              │ ║
║  │  • Metformin: -1.0-1.5%                                     │ ║
║  │  • Cutting sodas: -0.3-0.5%                                 │ ║
║  │  • Weight loss: -0.1% per 1 kg lost                        │ ║
║  └────────────────────────────────────────────────────────────┘ ║
║                                                                  ║
║  ┌────────────────────────────────────────────────────────────┐ ║
║  │  CHOLESTEROL (LDL)                                         │ ║
║  │  ──────────────────────────────────────────────────────── │ ║
║  │  Current:  162 mg/dL                                        │ ║
║  │  Month 3:  ~85-100 mg/dL                                    │ ║
║  │  Goal:     <70 mg/dL (given diabetes + HTN)                 │ ║
║  │                                                            │ ║
║  │  Contributors:                                              │ ║
║  │  • Atorvastatin 40mg: ~45-50% reduction                     │ ║
║  │  • May need to increase to 80mg if not at goal             │ ║
║  └────────────────────────────────────────────────────────────┘ ║
║                                                                  ║
║  ┌────────────────────────────────────────────────────────────┐ ║
║  │  SLEEP APNEA & ENERGY                                      │ ║
║  │  ──────────────────────────────────────────────────────── │ ║
║  │  If moderate-severe OSA (expected): CPAP therapy           │ ║
║  │  • Week 1-2: Adjustment period                              │ ║
║  │  • Week 2-4: Noticeable energy improvement                  │ ║
║  │  • Month 1+: "Life-changing" per most patients              │ ║
║  │                                                            │ ║
║  │  CDL STATUS: Maintain certification with documented        │ ║
║  │  CPAP compliance                                            │ ║
║  └────────────────────────────────────────────────────────────┘ ║
║                                                                  ║
║  ┌────────────────────────────────────────────────────────────┐ ║
║  │  WEIGHT                                                    │ ║
║  │  ──────────────────────────────────────────────────────── │ ║
║  │  Current:  268 lbs                                          │ ║
║  │  Month 3:  ~258-262 lbs (-6-10 lbs)                         │ ║
║  │  Month 6:  ~245-250 lbs (10% loss goal)                     │ ║
║  │                                                            │ ║
║  │  Note: Weight loss with lifestyle alone is modest.          │ ║
║  │  If not meeting goals, consider GLP-1 agonist (Ozempic)    │ ║
║  │  which helps both diabetes AND weight.                      │ ║
║  └────────────────────────────────────────────────────────────┘ ║
║                                                                  ║
║  ════════════════════════════════════════════════════════════   ║
║                                                                  ║
║  CARDIOVASCULAR RISK REDUCTION:                                 ║
║                                                                  ║
║  Current 10-Year ASCVD Risk: 18.2%                              ║
║  Projected with Treatment: ~10-12%                              ║
║                                                                  ║
║  Translation: Bobby's chance of heart attack or stroke          ║
║  in the next 10 years drops from ~1 in 5 to ~1 in 10            ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

# PART 6: SUMMARY FOR TEAM REVIEW

## What This Demo Shows

### 1. **Complete Workflow**
- Clinical note → AI parsing → Card generation → Patient delivery

### 2. **Personalization**
- Patient goals ("keep driving," "meet grandkids") woven into every card
- Occupation-specific tips (trucking lifestyle accommodations)
- Family history context (father's MI, brother's diabetes)

### 3. **Template Compliance**
- Every card follows the Universal Card Template
- Patient-Facing View (6th-8th grade reading level)
- Full Clinical View (complete clinical details)
- All required sections present

### 4. **Safety Framework**
- Yellow/Orange/Red tiered warnings
- System-specific safety alerts
- Clear escalation pathways

### 5. **Performance Medicine Integration**
- Clinical goals mapped to 8 Health Systems
- Structure/Function/Risk domains applied

### 6. **Feasibility Scoring**
- Objective deductions and additions
- Patient-specific adjustments
- Realistic assessment of adherence likelihood

### 7. **Card Synergy**
- How medications work together
- How monitoring validates treatment
- How behavioral changes amplify medical therapy

### 8. **Practical Implementation**
- Daily routine integration
- Time burden estimates
- Cost projections

---

## Questions for Team Review

1. **Template Completeness**: Are all required sections adequately addressed?

2. **Reading Level**: Is the patient-facing content truly accessible?

3. **Safety Coverage**: Are the Yellow/Orange/Red tiers clear and actionable?

4. **Feasibility Scoring**: Does the methodology make sense? Adjustments needed?

5. **Synergy Mapping**: Is the card interaction logic clear?

6. **Occupational Adaptation**: Are the trucking-specific modifications appropriate?

7. **Outcome Projections**: Are the expected results realistic and evidence-based?

8. **Missing Elements**: What's not covered that should be?

---

## Next Steps After Review

1. **Incorporate feedback** into template refinements
2. **Begin Phase 2**: Create actual card content for priority cards
3. **Develop card ordering logic** (which cards to present first)
4. **Build patient app mockups** based on this framework
5. **Create provider-facing workflow** for card approval/modification

---

*Demo Version 1.0 | Created: 2024-11-23*
*For Internal Team Review*

---

**END OF DEMO CASE PRESENTATION**
