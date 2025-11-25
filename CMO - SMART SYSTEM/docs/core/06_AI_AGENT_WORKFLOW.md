# AI AGENT WORKFLOW & AUTOMATION

This document describes how AI agents interact with the SMART Card system to automate card selection, generation, and monitoring.

---

## AI AGENT ROLE IN CARD SELECTION

### Core Responsibilities

1. **Analyze patient's comprehensive health data** from medical record
2. **Identify eligible cards** based on diagnoses, labs, vitals
3. **Check contraindications and conflicts**
4. **Calculate feasibility/actionability scores**
5. **Prioritize cards** by evidence strength, burden, time-to-benefit
6. **Generate recommended deck**
7. **Present to clinician** with rationale

---

## DECISION LOGIC FOR AI

### Step 1: Patient Profile Analysis

**Data Sources to Analyze**:
- Demographics (age, sex, pregnancy status, race/ethnicity)
- Active diagnosis codes (ICD-10)
- Current medication list
- Recent lab values and vitals
- Allergies and contraindications
- Social determinants (insurance, housing, transportation, language)
- Previous card adherence rates
- Patient-reported barriers and goals
- Chief concerns/complaints

**Patient Profile Output**:
```json
{
  "patient_id": "12345",
  "age": 58,
  "sex": "M",
  "diagnoses": ["I10 - Essential hypertension", "E11.9 - Type 2 diabetes"],
  "medications": ["None currently"],
  "labs_recent": {
    "HbA1c": {"value": 8.2, "date": "2024-10-15", "normal": "4.0-5.6"},
    "BP": {"systolic": 165, "diastolic": 95, "date": "2024-11-16"}
  },
  "allergies": ["Penicillin"],
  "barriers": ["Limited transportation", "Fixed income"],
  "language": "English",
  "goals": ["Control blood pressure", "Avoid complications like my father had"]
}
```

### Step 2: Indication Matching

**Algorithm**:
```
FOR each active diagnosis:
  QUERY card library WHERE indication = diagnosis
  
FOR each card found:
  CHECK absolute contraindications
    IF present → EXCLUDE card
  CHECK relative contraindications  
    IF present → FLAG for clinician review
  CHECK drug-drug interactions with current meds
    IF major interaction → FLAG or EXCLUDE
  CHECK drug-condition interactions
    IF present → FLAG or modify dosing
```

**Output Example**:
```json
{
  "eligible_cards": [
    {
      "card_id": "MED_ACE_Lisinopril_10mg",
      "indication": "Hypertension",
      "contraindications": {"absolute": [], "relative": []},
      "interactions": [],
      "status": "ELIGIBLE"
    },
    {
      "card_id": "MED_DIABETIC_Metformin_500mg",
      "indication": "Type 2 Diabetes",
      "contraindications": {"absolute": [], "relative": ["Check renal function"]},
      "interactions": [],
      "status": "ELIGIBLE_WITH_LABS"
    }
  ],
  "excluded_cards": [
    {
      "card_id": "MED_BETA_BLOCKER_X",
      "reason": "Patient has asthma (absolute contraindication)"
    }
  ]
}
```

### Step 3: Prioritization Algorithm

**Scoring Formula**:
```
Total Score = (Evidence × 0.30) + (Feasibility × 0.25) + 
              (Time-to-Benefit × 0.15) + (Burden × 0.15) + 
              (Patient Priority × 0.10) + (Guideline Mandate × 0.05)
```

**Component Scores**:

**Evidence Strength** (30% weight):
- Grade A: 100 points
- Grade B: 70 points
- Grade C: 40 points

**Feasibility Score** (25% weight):
- Use calculated feasibility score (0-100%)
- Already accounts for barriers

**Time-to-Benefit** (15% weight):
- <1 week: 100 points
- 1-2 weeks: 85 points
- 2-4 weeks: 70 points
- 1-3 months: 50 points
- >3 months: 30 points

**Burden Score** (15% weight):
- Time <10 min/day: 100 points
- Time 10-30 min/day: 70 points
- Time >30 min/day: 40 points

**Patient Priority** (10% weight):
- Patient explicitly requested: 100 points
- Aligns with patient goals: 70 points
- Not mentioned: 40 points

**Guideline Mandate** (5% weight):
- USPSTF Grade A preventive: 100 points
- Strong guideline (Class 1): 80 points
- Moderate guideline (Class 2a): 60 points
- Weak recommendation: 40 points

**Ranking Example**:
```
Card 1: Lisinopril 10mg
  Evidence: 30 (Grade A × 0.30)
  Feasibility: 21 (85% × 0.25)
  Time-to-Benefit: 10.5 (70 × 0.15)
  Burden: 15 (100 × 0.15)
  Patient Priority: 10 (100 × 0.10)
  Guideline: 5 (100 × 0.05)
  TOTAL: 91.5

Card 2: Mediterranean Diet
  Evidence: 21 (Grade B × 0.30)
  Feasibility: 16.25 (65% × 0.25)
  Time-to-Benefit: 10.5 (70 × 0.15)
  Burden: 6 (40 × 0.15)
  Patient Priority: 4 (40 × 0.10)
  Guideline: 4 (80 × 0.05)
  TOTAL: 61.75
```

### Step 4: Deck Assembly & Presentation

**AI Generates Recommended Deck**:

```json
{
  "deck_name": "Hypertension & Diabetes Management Deck",
  "clinical_goals": [
    "Cardiovascular System: Reduce Risk",
    "Metabolic System: Improve Function"
  ],
  "recommended_cards": [
    {
      "card": "Lisinopril 10mg Daily",
      "priority": 1,
      "score": 91.5,
      "rationale": "Grade A evidence, high feasibility, patient goal aligned"
    },
    {
      "card": "Home BP Monitoring",
      "priority": 2,
      "score": 88.0,
      "rationale": "Essential for medication titration, low burden"
    },
    {
      "card": "Metformin 500mg BID",
      "priority": 3,
      "score": 85.0,
      "rationale": "HbA1c 8.2% requires treatment, first-line therapy"
    },
    {
      "card": "DASH Diet",
      "priority": 4,
      "score": 78.0,
      "rationale": "Synergistic with BP medication, evidence-based"
    },
    {
      "card": "Walking Exercise 30min",
      "priority": 5,
      "score": 72.0,
      "rationale": "Benefits both HTN and DM, patient able"
    }
  ],
  "alternative_cards": [
    {
      "card": "Stress Management - Deep Breathing",
      "score": 65.0,
      "note": "Lower priority but may help with BP"
    }
  ],
  "synergy_notes": [
    "Lisinopril + DASH diet + BP monitoring work together for BP control",
    "Metformin + Walking + Diet work together for glucose control"
  ],
  "total_time_burden": "~45 min/day",
  "overall_feasibility": "78%"
}
```

**Clinician View**:
```
╔═══════════════════════════════════════════════╗
║  AI RECOMMENDED DECK                          ║
║  Patient: John Doe (58M)                      ║
║  Conditions: HTN, Type 2 DM                   ║
╠═══════════════════════════════════════════════╣
║                                               ║
║  5 RECOMMENDED CARDS (sorted by priority):    ║
║                                               ║
║  1. ✅ Lisinopril 10mg Daily                  ║
║     Score: 91.5 | Evidence: A | Feasible: 85% ║
║     → Start immediately for BP control        ║
║                                               ║
║  2. ✅ Home BP Monitoring                     ║
║     Score: 88.0 | Evidence: A | Feasible: 90% ║
║     → Track medication effectiveness          ║
║                                               ║
║  3. ⚠️  Metformin 500mg BID                   ║
║     Score: 85.0 | Evidence: A | Feasible: 80% ║
║     ⚠️  Check renal function first (Cr, GFR)  ║
║                                               ║
║  4. ✅ DASH Diet                              ║
║     Score: 78.0 | Evidence: A | Feasible: 65% ║
║     → Synergistic with HTN treatment          ║
║                                               ║
║  5. ✅ Walking Exercise 30min                 ║
║     Score: 72.0 | Evidence: A | Feasible: 75% ║
║     → Benefits both HTN and DM                ║
║                                               ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                               ║
║  DECK SUMMARY:                                ║
║  Overall Feasibility: 78%                     ║
║  Total Time: ~45 min/day                      ║
║  Expected BP Reduction: 25-35 mmHg            ║
║  Expected HbA1c Reduction: 1-2%               ║
║                                               ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                               ║
║  BARRIERS IDENTIFIED:                         ║
║  • Limited transportation (-15% feasibility)  ║
║    → Telehealth follow-ups recommended        ║
║  • Fixed income (-10% feasibility)            ║
║    → Generic meds selected, free exercise     ║
║                                               ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                               ║
║  [ ✓ Approve All ]  [ ✏️ Modify ]  [ ✖ Reject ] ║
║                                               ║
╚═══════════════════════════════════════════════╝
```

### Step 5: Clinician Review & Publish

**Clinician Actions**:
1. **Approve** → AI deck published to patient immediately
2. **Modify** → Clinician adds/removes/adjusts cards, then publishes
3. **Reject** → Clinician selects cards manually

**Clinical Override Options**:
- Remove cards from recommendation
- Add cards not in AI recommendation
- Adjust dosing/frequency/targets
- Add custom instructions
- Set different follow-up schedule
- Document clinical reasoning for audit

**Publish to Patient**:
Once approved, deck appears in patient's app with:
- All active cards displayed
- Instructions to start immediately
- Follow-up appointments auto-scheduled
- Reminders set up

---

## NATURAL LANGUAGE PARSING (NLP)

### Vision: Parse Clinician MDM to Generate Cards

**Input Example** (Clinician dictates/types):
```
"54yo M with uncontrolled HTN, BP 165/95 today. 

Assessment & Plan:
1. Hypertension - not at goal
   - Start lisinopril 10mg daily
   - Low sodium diet <2000mg/day
   - Home BP monitoring BID
   - Check BP in 2 weeks, labs (BMP) in 4 weeks
   
2. Stress management
   - Patient reports work stress
   - Teach deep breathing exercises
   - Goal: practice 5 min twice daily
   
3. Follow-up: RTC 2 weeks for BP check"
```

**NLP Extraction Algorithm**:

**Step 1: Identify Sections**
```
Sections detected:
- Assessment & Plan
- Condition: Hypertension
- Condition: Stress
- Follow-up plan
```

**Step 2: Extract Actionable Items**
```
Medications:
- Drug: Lisinopril
- Dose: 10mg
- Route: Oral (implied)
- Frequency: Daily
- Duration: Ongoing (implied for chronic condition)

Lifestyle Interventions:
- Type: Diet
- Specifics: Low sodium <2000mg/day

Monitoring:
- Type: Blood pressure
- Frequency: BID (twice daily)
- Setting: Home

Labs:
- Test: BMP (Basic Metabolic Panel)
- Timing: 4 weeks

Behavioral:
- Type: Stress management
- Technique: Deep breathing
- Duration: 5 minutes
- Frequency: Twice daily

Follow-up:
- Timing: 2 weeks
- Purpose: BP check
```

**Step 3: Map to Card Templates**
```
Card 1: Medication Card
  Template: MED_ACE_Lisinopril
  Dose: 10mg daily
  
Card 2: Nutrition Card
  Template: NUTR_LowSodium
  Target: <2000mg/day
  
Card 3: Monitoring Card
  Template: VITAL_BP_Home
  Frequency: BID
  
Card 4: Lab Card
  Template: LAB_BMP
  Timing: 4 weeks from today
  
Card 5: Behavioral Card
  Template: BEHAV_DeepBreathing
  Duration: 5 min
  Frequency: BID
```

**Step 4: Auto-Populate Cards**
AI fills in card templates using:
- Drug database for medication details
- Standard protocols for each intervention type
- Evidence citations automatically added
- Safety information from knowledge base

**Step 5: Present for Clinician Review**
```
╔════════════════════════════════════════╗
║  CARDS GENERATED FROM YOUR NOTE        ║
╠════════════════════════════════════════╣
║                                        ║
║  5 cards created. Review before        ║
║  publishing to patient.                ║
║                                        ║
║  ✅ Lisinopril 10mg Daily              ║
║     [Preview] [Edit] [Remove]          ║
║                                        ║
║  ✅ Low Sodium Diet <2000mg            ║
║     [Preview] [Edit] [Remove]          ║
║                                        ║
║  ✅ Home BP Monitoring BID             ║
║     [Preview] [Edit] [Remove]          ║
║                                        ║
║  ✅ BMP Lab in 4 Weeks                 ║
║     [Preview] [Edit] [Remove]          ║
║                                        ║
║  ✅ Deep Breathing 5min BID            ║
║     [Preview] [Edit] [Remove]          ║
║                                        ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                        ║
║  [ Publish All to Patient ]            ║
║  [ Save as Draft ]                     ║
║                                        ║
╚════════════════════════════════════════╝
```

---

## PATIENT-INITIATED AI TRIAGE

### AI Chatbot Workflow (Pre-Visit)

**Step 1: Patient Enters Chief Complaint**

```
Patient input:
"I've been having headaches and my blood pressure 
at the pharmacy was high. I'm worried because my 
dad had a stroke. I want to make sure I'm healthy 
for my kids."
```

**Step 2: AI Asks Structured Clarifying Questions**

```
AI: Thank you for sharing. I'd like to ask a few 
questions to help your doctor prepare for your visit.

1. How long have you had these headaches?
   [Patient: About 2 weeks]

2. Do you know what your blood pressure numbers were?
   [Patient: The pharmacist said 165 over something, 
   I don't remember the bottom number]

3. Any chest pain, vision changes, numbness, or weakness?
   [Patient: No]

4. What medications are you currently taking?
   [Patient: None right now]

5. Besides your father's stroke, any other family 
   history of heart disease?
   [Patient: My mom has high blood pressure too]
```

**Step 3: AI Generates Preliminary Assessment**

```json
{
  "triage_level": "URGENT",
  "rationale": "Elevated BP + symptoms + family history",
  "chief_complaint": "Headaches + elevated BP reading",
  "patient_goals": [
    "Avoid stroke like father",
    "Stay healthy for children"
  ],
  "preliminary_cards": [
    "Home BP monitoring",
    "Low sodium diet",
    "Stress management",
    "Headache diary"
  ],
  "structured_data": {
    "HPI": "2 weeks of headaches, BP 165/? at pharmacy",
    "ROS": "Denies chest pain, vision changes, numbness, weakness",
    "FHx": "Father: stroke, Mother: hypertension",
    "Medications": "None",
    "Allergies": "Unknown"
  }
}
```

**Step 4: Clinician Reviews Pre-Visit**

```
╔════════════════════════════════════════╗
║  PRE-VISIT SUMMARY (AI-Generated)      ║
║  Patient: John Doe (Next appt: Today)  ║
╠════════════════════════════════════════╣
║                                        ║
║  🚨 TRIAGE: URGENT                     ║
║                                        ║
║  CHIEF COMPLAINT:                      ║
║  Headaches (2 weeks) + elevated BP     ║
║  reading at pharmacy (165/?)           ║
║                                        ║
║  PATIENT'S GOALS:                      ║
║  • "Avoid stroke like my dad had"      ║
║  • "Stay healthy for my kids"          ║
║                                        ║
║  RED FLAGS:                            ║
║  • Family history: Father (stroke),    ║
║    Mother (HTN)                        ║
║  • Symptomatic hypertension            ║
║  • No current treatment                ║
║                                        ║
║  PRELIMINARY CARD SUGGESTIONS:         ║
║  [AI recommends based on presentation] ║
║                                        ║
║  [ View Full AI Assessment ]           ║
║  [ Start Visit ]                       ║
║                                        ║
╚════════════════════════════════════════╝
```

**Step 5: During/After Visit**

Clinician:
1. Confirms diagnosis (Stage 2 Hypertension)
2. Adds clinical MDM and orders
3. AI regenerates deck combining:
   - Patient's reported goals
   - Clinician's medical orders
   - Evidence-based complementary cards

**Step 6: Clinician Approves & Publishes**

Final deck goes to patient with:
- Their voice captured ("I want to avoid stroke like my dad")
- Clinician's expertise (medication, labs)
- AI's evidence-based additions (diet, exercise)

**Result**: True co-creation among patient, AI, and clinician

---

## CONFLICT CHECKING ALGORITHMS

### Drug-Drug Interaction Checking

**AI checks against drug interaction database**:

```python
def check_drug_interactions(new_card, current_meds):
    interactions = []
    
    for med in current_meds:
        severity = check_interaction_database(new_card.drug, med)
        
        if severity == "CONTRAINDICATED":
            return {
                "status": "BLOCKED",
                "reason": f"{new_card.drug} + {med}: Contraindicated",
                "action": "Do not prescribe. Consider alternative."
            }
        
        elif severity == "MAJOR":
            interactions.append({
                "status": "WARNING",
                "drug_pair": f"{new_card.drug} + {med}",
                "severity": "Major",
                "action": "Monitor closely. May require dose adjustment."
            })
        
        elif severity == "MODERATE":
            interactions.append({
                "status": "CAUTION",
                "drug_pair": f"{new_card.drug} + {med}",
                "severity": "Moderate",
                "action": "Be aware. Usually manageable."
            })
    
    return {
        "status": "CLEARED" if not interactions else "WARNINGS",
        "interactions": interactions
    }
```

### Drug-Condition Contraindications

```python
def check_drug_condition_contraindications(card, patient_diagnoses):
    contraindications = []
    
    for condition in patient_diagnoses:
        if condition in card.absolute_contraindications:
            return {
                "status": "BLOCKED",
                "reason": f"{card.drug} contraindicated in {condition}",
                "action": "Do not prescribe. Select alternative card."
            }
        
        if condition in card.relative_contraindications:
            contraindications.append({
                "status": "WARNING",
                "condition": condition,
                "reason": card.relative_contraindication_reasons[condition],
                "action": "Use with caution. May require dose adjustment or close monitoring."
            })
    
    return {
        "status": "CLEARED" if not contraindications else "WARNINGS",
        "contraindications": contraindications
    }
```

### Card-Card Conflicts Within Deck

```python
def check_deck_conflicts(proposed_deck):
    conflicts = []
    
    # Check for duplicate therapy (e.g., two ACE inhibitors)
    drug_classes = [card.drug_class for card in proposed_deck if card.type == "medication"]
    duplicates = [cls for cls in set(drug_classes) if drug_classes.count(cls) > 1]
    
    if duplicates:
        conflicts.append({
            "type": "DUPLICATE_THERAPY",
            "classes": duplicates,
            "action": "Remove duplicate. Keep higher priority card."
        })
    
    # Check for synergies that might be excessive
    # Example: ACE inhibitor + ARB + K supplement = hyperkalemia risk
    
    return {
        "status": "CONFLICTS_FOUND" if conflicts else "CLEAR",
        "conflicts": conflicts
    }
```

---

## CONTINUOUS MONITORING & ALERTS

### AI Monitors Patient Data

**Real-Time Alerts**:
```python
def monitor_patient_adherence_and_outcomes(patient_id):
    patient_data = get_patient_data(patient_id)
    active_deck = get_active_deck(patient_id)
    
    alerts = []
    
    # Check adherence
    for card in active_deck:
        adherence = calculate_adherence(card, patient_data.logs)
        
        if adherence < 50%:
            alerts.append({
                "type": "LOW_ADHERENCE",
                "card": card.name,
                "adherence_rate": f"{adherence}%",
                "action": "Contact patient to discuss barriers"
            })
    
    # Check outcome measures
    for card in active_deck:
        current_value = patient_data.measures[card.measure]
        target_value = card.target
        
        if not approaching_target(current_value, target_value, card.timeline):
            alerts.append({
                "type": "NOT_IMPROVING",
                "card": card.name,
                "current": current_value,
                "target": target_value,
                "action": "Consider dose adjustment or alternative therapy"
            })
    
    # Check for adverse events
    if patient_data.reported_symptoms:
        for symptom in patient_data.reported_symptoms:
            if is_serious_side_effect(symptom, active_deck):
                alerts.append({
                    "type": "ADVERSE_EVENT",
                    "symptom": symptom,
                    "suspected_card": identify_likely_culprit(symptom, active_deck),
                    "action": "Contact patient immediately. May need to stop card."
                })
    
    return alerts
```

**Weekly Summary for Clinician**:
```
╔═══════════════════════════════════════╗
║  PATIENT MONITORING SUMMARY           ║
║  Week of November 10-16, 2025         ║
╠═══════════════════════════════════════╣
║                                       ║
║  📊 ADHERENCE:                        ║
║  • Lisinopril: 95% (excellent)        ║
║  • BP monitoring: 85% (good)          ║
║  • DASH diet: 60% (needs support)     ║
║  • Walking: 40% (poor) ⚠️             ║
║                                       ║
║  📈 OUTCOMES:                         ║
║  • BP: 145/88 → Improving but not     ║
║    at goal yet (target <130/80)       ║
║  • Weight: Stable                     ║
║                                       ║
║  ⚠️  ALERTS (2):                      ║
║  1. Low adherence to walking card     ║
║     → Patient reports "too tired"     ║
║     → Suggest: Reduce to 10 min/day   ║
║                                       ║
║  2. BP not improving as expected      ║
║     → Consider: Increase lisinopril   ║
║       to 20mg if tolerated            ║
║                                       ║
║  [ View Details ]  [ Contact Patient ]║
║                                       ║
╚═══════════════════════════════════════╝
```

---

## TECHNICAL IMPLEMENTATION NOTES

### JSON Schema for Card Storage

```json
{
  "card_id": "MED_ACE_Lisinopril_10mg",
  "card_type": "medication",
  "version": "2.1",
  "last_updated": "2024-11-01",
  "patient_facing": {
    "what": "Take Lisinopril to lower your blood pressure.",
    "why": "This helps protect your heart and kidneys.",
    "how": ["Step 1", "Step 2", "Step 3"],
    "when": "Once daily in the morning",
    "watch_for": ["Red flag 1", "Red flag 2"]
  },
  "clinical_details": {
    "what": {...},
    "who": {...},
    "when": {...},
    "where": {...},
    "why": {...},
    "how": {...},
    "measure": {...},
    "target": {...},
    "safety": {...},
    "follow_up": {...},
    "notes": {...}
  },
  "metadata": {
    "tags": ["#ChronicManagement", "#Cardiology", "#Home"],
    "evidence_grade": "A",
    "feasibility_score": 85,
    "guidelines": ["ACC/AHA 2017"]
  }
}
```

### API Endpoints Needed

- `POST /api/cards/recommend` - AI generates recommendations
- `GET /api/cards/library` - Retrieve card library
- `POST /api/cards/publish` - Publish deck to patient
- `GET /api/patient/adherence` - Get adherence data
- `POST /api/patient/report` - Patient reports side effect
- `GET /api/monitoring/alerts` - Get AI-generated alerts

---

## FUTURE ENHANCEMENTS

1. **Predictive Analytics**: Predict which patients likely to be non-adherent
2. **Personalized Timing**: AI suggests optimal times for each patient
3. **Smart Notifications**: Context-aware reminders (weather, schedule)
4. **Voice Interface**: Voice commands for logging adherence
5. **Integration with Wearables**: Auto-sync BP, glucose, steps
6. **Multi-Language NLP**: Parse notes in multiple languages