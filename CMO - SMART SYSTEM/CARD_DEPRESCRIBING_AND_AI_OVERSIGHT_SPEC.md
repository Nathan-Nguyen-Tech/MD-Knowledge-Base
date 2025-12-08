# SMART CARD DE-PRESCRIBING & AI CLINICAL OVERSIGHT SPECIFICATION
**Version:** 1.1
**Date:** 2025-12-05
**Section:** 3 (SMART Card/Deck System)
**Status:** Active

---

**Depends On:**
- INTEGRATION_ARCHITECTURE.md v2.0
- UNIVERSAL_CARD_TEMPLATE.md v2.0
- CARD_TYPE_SPECIFICATIONS.md v2.0
- CARD_LIFECYCLE_AND_AI_PARAMETERS.md v1.0 (NEW)

**Related Documents:**
- [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](docs/core/CARD_LIFECYCLE_AND_AI_PARAMETERS.md) - Complete lifecycle phases & AI bracket notation
- [UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) - Template with lifecycle sections

**Updates in v1.1:**
- Added 3 missing card types (Imaging Studies, DME, Environmental & Social Health) - now covers all 12
- Added reference to CARD_LIFECYCLE_AND_AI_PARAMETERS.md for complete lifecycle spec
- Aligned terminology with self-directed healthcare model

---

## PURPOSE

This document defines:
1. **Concrete processes** for patients to self-direct when to STOP using SMART Cards
2. **AI Agent oversight** for card prescription, management, and de-prescribing
3. **When human clinician involvement is required** vs. AI-autonomous decisions
4. **Specific de-loading criteria** for each card type

---

## THE PROBLEM STATEMENT

**What We Have:**
- ✅ Card creation/prescription logic (when to BEGIN cards)
- ✅ Card management/adherence tracking (how to PERFORM cards)

**What We're Missing:**
- ❌ Card de-loading/de-prescribing logic (when to STOP cards)
- ❌ AI agent playing expert clinician role
- ❌ Clear escalation criteria for human clinician involvement
- ❌ Patient self-directed stopping process

---

## SOLUTION ARCHITECTURE

### **Three-Layer Decision Model:**

```
┌─────────────────────────────────────────────────────────────┐
│  LAYER 1: AI AUTONOMOUS DECISIONS (80% of cases)           │
│  • Routine card recommendations                             │
│  • Standard de-prescribing based on clear criteria          │
│  • Low-risk medication adjustments                          │
│  • Lifestyle card progression/graduation                    │
└─────────────────────┬───────────────────────────────────────┘
                      ↓ (Escalation triggers)
┌─────────────────────────────────────────────────────────────┐
│  LAYER 2: AI + CLINICIAN REVIEW (15% of cases)             │
│  • AI recommends, clinician approves before action          │
│  • Moderate-risk decisions                                  │
│  • Unclear clinical scenarios                               │
│  • Patient preference conflicts                             │
└─────────────────────┬───────────────────────────────────────┘
                      ↓ (High-risk escalation)
┌─────────────────────────────────────────────────────────────┐
│  LAYER 3: HUMAN CLINICIAN REQUIRED (5% of cases)           │
│  • High-risk medication changes                             │
│  • Complex multi-morbidity cases                            │
│  • Safety concerns or adverse events                        │
│  • Patient requests human contact                           │
└─────────────────────────────────────────────────────────────┘
```

---

## AI AGENT ARCHITECTURE: "DR. ADAPT"

### **Agent Name:** Dr. ADAPT (Autonomous Decision & Prescription Tracking)

### **Role:**
AI clinical agent that serves as the primary "clinician" for routine SMART Card prescription, management, and de-prescribing, with seamless escalation to human clinicians when needed.

### **Core Capabilities:**

**1. Card Prescription (Creation)**
- Analyze Section 1 clinical data + Section 2 dashboard scores
- Recommend appropriate cards based on evidence-based triggers
- Check contraindications, drug-drug interactions, patient allergies
- Assign feasibility scores
- Present recommendations with rationale

**2. Card Management (Monitoring)**
- Track patient adherence to card actions
- Monitor for adverse events or barriers
- Adjust card complexity (beginner → intermediate → advanced)
- Provide encouragement and problem-solving suggestions
- Detect when cards are not working (low adherence, lack of progress)

**3. Card De-Prescribing (Stopping)**
- Continuously evaluate if card goals achieved
- Detect when cards no longer clinically indicated
- Recommend card graduation, pause, or discontinuation
- Ensure safe tapering for medications requiring it
- Prevent premature stopping

**4. Clinical Oversight & Safety**
- Real-time monitoring of dashboard for concerning trends
- Critical alert escalation to human clinicians
- Drug safety monitoring (new interactions, contraindications)
- Patient sentiment analysis (frustration, confusion, disengagement)
- Quality assurance (ensure evidence-based recommendations)

---

## CARD DE-PRESCRIBING FRAMEWORK

### **Three De-Prescribing Pathways:**

**1. GRADUATION (Goal Achieved)**
- Card target successfully met
- Behavior now habit (lifestyle cards)
- Parameter normalized (medical cards)
- Action: Card moves to "Graduated" status, patient celebrates success

**2. TRANSITION (Stepping Up/Down)**
- Need higher complexity (beginner → intermediate → advanced)
- Need simpler version (too difficult, low adherence)
- Need different card type (alternative intervention)
- Action: Current card replaced with new card

**3. DISCONTINUATION (No Longer Needed)**
- Diagnosis resolved
- Treatment failure (tried, didn't work, move on)
- Patient preference (not sustainable for them)
- Contraindication developed
- Action: Card removed entirely

---

## DE-PRESCRIBING CRITERIA BY CARD TYPE

### **1. MEDICATION CARDS**

#### **Graduation Criteria:**
- Diagnosis resolved (e.g., infection cleared → stop antibiotic)
- Parameter normalized for sustained period (e.g., BP controlled for 6 months → consider deprescribing)
- Trial period completed successfully

#### **Discontinuation Criteria:**
- Adverse event or intolerable side effect
- Drug-drug interaction newly identified
- Contraindication developed (e.g., pregnancy)
- Treatment ineffective (parameter not improving after adequate trial)
- Patient preference (after informed discussion of risks/benefits)

#### **AI Autonomous Decisions:**
- ✅ Stop antibiotic after completed course
- ✅ Stop PRN medication if no longer needed (e.g., albuterol if asthma controlled)
- ✅ Recommend deprescribing if parameter normalized (AI recommends, clinician approves)

#### **Human Clinician Required:**
- ❌ Stop chronic disease medication (e.g., insulin, blood pressure meds)
- ❌ Stop controlled substances
- ❌ Any medication requiring tapering

#### **Patient Self-Directed Actions:**
- Patient can FLAG card for review ("I want to stop this")
- Patient can report side effects → AI escalates
- Patient CANNOT independently stop without AI/clinician approval

---

### **2. DIAGNOSTIC TESTING CARDS (Labs, Imaging)**

#### **Graduation Criteria:**
- Test completed successfully
- Results reviewed and acted upon
- Follow-up plan established

#### **Discontinuation Criteria:**
- Test no longer clinically indicated (diagnosis ruled out/ruled in)
- Alternative test preferred
- Patient declined test

#### **AI Autonomous Decisions:**
- ✅ Mark test as complete once results in system
- ✅ Recommend next test based on results
- ✅ Stop repeat testing if parameter stabilized

#### **Human Clinician Required:**
- ❌ Cancel high-cost imaging without review
- ❌ Skip guideline-recommended screening (e.g., cancer screening)

#### **Patient Self-Directed Actions:**
- Patient can complete test and upload results
- Patient can request test postponement (AI reviews reason)

---

### **3. NUTRITION CARDS (Dietary Patterns, Food Focus, Eating Behaviors)**

#### **Graduation Criteria:**
- Behavior sustained for 90 days (habit formation threshold)
- Dashboard metrics improved (weight, lipids, glucose)
- Patient reports behavior now automatic

#### **Transition Criteria:**
- Ready for more advanced card (e.g., basic → intermediate meal planning)
- Need simpler card (current too complex)

#### **Discontinuation Criteria:**
- Patient tried earnestly but behavior unsustainable
- Cultural/preference/financial barriers insurmountable
- Alternative card preferred

#### **AI Autonomous Decisions:**
- ✅ Graduate card after 90-day adherence + parameter improvement
- ✅ Transition to advanced card if ready
- ✅ Pause card if adherence <30% for 2 weeks (suggest alternative)

#### **Human Clinician Involvement:**
- 💬 Optional review if patient frustrated or not improving

#### **Patient Self-Directed Actions:**
- ✅ Patient can request pause or switch to different nutrition card
- ✅ Patient can graduate self if confident behavior is habit
- ✅ Patient can request easier/harder version

---

### **4. MOVEMENT/EXERCISE CARDS**

#### **Graduation Criteria:**
- Exercise program sustained for 90 days
- Fitness metrics improved (Section 1 data: VO2 max, strength tests)
- Patient achieved target (e.g., walk 30 min daily for 3 months)

#### **Transition Criteria:**
- Ready for higher intensity
- Need modification due to injury or limitation

#### **Discontinuation Criteria:**
- Injury preventing exercise
- Medical contraindication developed
- Patient preference (alternative activity preferred)

#### **AI Autonomous Decisions:**
- ✅ Graduate card after 90-day adherence + fitness improvement
- ✅ Recommend intensity progression
- ✅ Pause card if patient reports pain/injury (escalate to clinician review)

#### **Human Clinician Required:**
- ❌ Exercise prescription changes if cardiac history
- ❌ Return to exercise after injury

#### **Patient Self-Directed Actions:**
- ✅ Patient can graduate self if exercise now routine
- ✅ Patient can request modification for accessibility
- ✅ Patient can pause temporarily (vacation, illness)

---

### **5. SLEEP & RECOVERY CARDS**

#### **Graduation Criteria:**
- Sleep quality score normalized (Section 1 data)
- Sleep hygiene practices sustained 90 days
- Patient reports restorative sleep consistently

#### **Discontinuation Criteria:**
- Intervention ineffective after 4-6 week trial
- Sleep disorder diagnosed requiring medical treatment

#### **AI Autonomous Decisions:**
- ✅ Graduate card if sleep metrics improved
- ✅ Recommend sleep study if insomnia persists despite interventions

#### **Human Clinician Required:**
- ❌ Sleep medication prescribing
- ❌ CPAP titration changes

#### **Patient Self-Directed Actions:**
- ✅ Patient can graduate card if sleep improved
- ✅ Patient can request alternative sleep intervention

---

### **6. MIND-BODY PRACTICE CARDS (Meditation, Yoga, Tai Chi)**

#### **Graduation Criteria:**
- Practice sustained 90 days
- Stress/anxiety metrics improved (Section 1 data)
- Patient reports benefit

#### **Discontinuation Criteria:**
- Practice not resonating with patient
- Alternative mind-body practice preferred

#### **AI Autonomous Decisions:**
- ✅ Graduate card after sustained practice + metric improvement
- ✅ Suggest alternative practice if low adherence

#### **Human Clinician Involvement:**
- 💬 Optional if patient has mental health diagnosis

#### **Patient Self-Directed Actions:**
- ✅ Fully self-directed
- ✅ Patient can graduate, pause, or switch practices

---

### **7. PROCEDURES CARDS (Surgeries, Interventions)**

#### **Graduation Criteria:**
- Procedure completed
- Post-procedure recovery plan established
- Follow-up appointments scheduled

#### **Discontinuation Criteria:**
- Patient declined procedure
- Procedure no longer indicated
- Contraindication identified

#### **AI Role:**
- 💬 AI facilitates scheduling and prep, but ALL procedure decisions require human clinician

#### **Human Clinician Required:**
- ❌ ALL procedure decisions

#### **Patient Self-Directed Actions:**
- ❌ None (procedures always require clinician involvement)

---

### **8. DME CARDS (CPAP, Glucose Monitor, etc.)**

#### **Graduation Criteria:**
- DME used consistently for 90 days
- Clinical parameter improved (e.g., A1C lowered with CGM use)
- Patient proficient with device

#### **Discontinuation Criteria:**
- DME no longer needed (diagnosis resolved)
- DME not tolerated (e.g., CPAP intolerance)
- Upgrade to newer device

#### **AI Autonomous Decisions:**
- ✅ Graduate card after sustained use + parameter improvement
- ✅ Recommend troubleshooting for low adherence

#### **Human Clinician Required:**
- ❌ Stop CPAP (requires sleep study review)
- ❌ Stop insulin pump or CGM

#### **Patient Self-Directed Actions:**
- ✅ Patient can request DME support/training
- ❌ Cannot discontinue without clinician approval

---

### **9. REFERRAL CARDS (Specialist Consultations)**

#### **Graduation Criteria:**
- Referral completed
- Specialist recommendations integrated into care plan
- Follow-up plan established

#### **Discontinuation Criteria:**
- Referral no longer needed (diagnosis ruled out)
- Patient declined referral

#### **AI Role:**
- ✅ AI facilitates scheduling and tracks completion
- 💬 AI cannot independently cancel specialist referrals (clinician reviews)

#### **Human Clinician Involvement:**
- 💬 Clinician reviews specialist recommendations before integrating

#### **Patient Self-Directed Actions:**
- ✅ Patient can complete referral appointment
- ❌ Cannot cancel referral without clinician discussion

---

### **10. IMAGING STUDIES CARDS (X-Ray, CT, MRI, Ultrasound)**

#### **Graduation Criteria:**
- Imaging completed successfully
- Results reviewed by clinician
- Findings communicated to patient
- Follow-up plan established based on findings

#### **Discontinuation Criteria:**
- Imaging no longer indicated (diagnosis established by other means)
- Contraindication identified (e.g., pregnancy for CT, metal implants for MRI)
- Patient declined after informed discussion
- Alternative study preferred

#### **AI Autonomous Decisions:**
- ✅ Mark study complete once results in system
- ✅ Recommend follow-up based on findings
- ✅ Flag if study ordered but not completed after reasonable period

#### **Human Clinician Required:**
- ❌ Cancel imaging without review (especially cancer screening/workup)
- ❌ Interpret complex findings
- ❌ Order contrast studies for patients with kidney disease or allergies

#### **Patient Self-Directed Actions:**
- ✅ Patient can complete study and update status
- ✅ Patient can request postponement (AI reviews reason)
- ❌ Cannot cancel without clinician discussion

---

### **11. ENVIRONMENTAL & SOCIAL HEALTH CARDS**

#### **Graduation Criteria:**
- Environmental modification implemented (e.g., ergonomic setup complete)
- Social goal sustained 90 days (e.g., regular community engagement)
- Substance use goal achieved (e.g., smoke-free for 90 days)
- Financial/resource navigation completed

#### **Transition Criteria:**
- Ready for more advanced goal (e.g., tobacco-free → healthier lifestyle overall)
- Need different approach (e.g., NRT → varenicline for smoking cessation)
- Barrier identified requiring different intervention

#### **Discontinuation Criteria:**
- Goal achieved and sustained
- Intervention not effective for this patient
- Patient preference for different approach
- Circumstances changed (e.g., job change, relocation)

#### **AI Autonomous Decisions:**
- ✅ Graduate card after 90-day sustained behavior (social, substance use goals)
- ✅ Mark one-time tasks complete (ergonomic assessment, resource navigation)
- ✅ Recommend alternatives if struggling

#### **Human Clinician Involvement:**
- 💬 Optional for most cards
- ❌ Required for substance use disorder treatment (MAT, detox referrals)
- ❌ Required for crisis situations (domestic violence, housing emergency)

#### **Patient Self-Directed Actions:**
- ✅ Fully self-directed for most environmental/social cards
- ✅ Patient can graduate, pause, or switch approaches
- ✅ Patient can access crisis resources directly

---

### **12. MICRO-LEARNING CARDS (Educational)**

#### **Graduation Criteria:**
- Content consumed (read, watched, or listened)
- Optional: Knowledge check passed
- Card automatically marks complete

#### **Transition Criteria:**
- N/A - Micro-Learning cards don't transition, they complete

#### **Discontinuation Criteria:**
- N/A - Micro-Learning cards are brief and complete upon consumption

#### **AI Role:**
- ✅ Track completion status
- ✅ Recommend related action cards after learning card completes
- ✅ Sequence learning cards appropriately within decks

#### **Human Clinician Involvement:**
- None required

#### **Patient Self-Directed Actions:**
- ✅ Fully self-directed
- ✅ Patient can complete at own pace
- ✅ Patient can skip if already knowledgeable (with acknowledgment)

---

## DE-PRESCRIBING SUMMARY: ALL 12 CARD TYPES

| # | Card Type | Patient Autonomy | AI Role | Clinician Role |
|---|-----------|------------------|---------|----------------|
| 1 | Medications | Request only | Recommend, escalate | Approve stops/changes |
| 2 | Diagnostic Testing | Request timing | Complete, recommend | Cancel screenings |
| 3 | Imaging Studies | Request timing | Complete, recommend | Cancel/interpret |
| 4 | Procedures | None | Facilitate | All decisions |
| 5 | DME | Request troubleshooting | Graduate, recommend | Approve discontinuation |
| 6 | Referrals | Complete appointment | Schedule, track | Cancel, integrate recs |
| 7 | Nutrition | **Full autonomy** | Graduate, offer alternatives | Optional consult |
| 8 | Movement/Exercise | **Full autonomy** | Graduate, progress | Post-injury return |
| 9 | Recovery | **Full autonomy** | Graduate, recommend | Sleep disorders |
| 10 | Mind-Body | **Full autonomy** | Graduate, suggest | Mental health concerns |
| 11 | Environmental/Social | **Full autonomy** | Graduate, resources | SUD treatment, crisis |
| 12 | Micro-Learning | **Full autonomy** | Track completion | None |

**Key Insight:**
- Behavioral cards (7-12): Patient self-directed, clinician optional
- Medical cards (1-6): Patient requests, clinician approves

---

## AI AGENT DECISION LOGIC: DE-PRESCRIBING ALGORITHM

### **Step 1: Continuous Monitoring**

AI agent monitors EVERY active card for:
- Adherence rate (% completion)
- Clinical parameters (from Section 2 dashboard)
- Time since card activation
- Patient-reported outcomes (surveys, reviews)
- Adverse events or barriers flagged

### **Step 2: Trigger Evaluation**

Every week, AI evaluates each card for de-prescribing triggers:

```python
# Pseudocode for AI decision logic

for each active_card in patient.active_cards:

    # GRADUATION TRIGGERS
    if card.goal_achieved() and card.sustained_90_days():
        if card.type in [NUTRITION, MOVEMENT, SLEEP, MIND_BODY]:
            → AI AUTONOMOUS: Graduate card, notify patient of success
        elif card.type in [MEDICATION, LAB, DME]:
            → AI RECOMMENDS: Escalate to clinician for approval

    # TRANSITION TRIGGERS
    if card.adherence_rate > 0.80 and card.duration > 30_days:
        if card.complexity == "beginner":
            → AI AUTONOMOUS: Recommend advancement to intermediate

    if card.adherence_rate < 0.30 and card.duration > 14_days:
        if card.complexity == "intermediate":
            → AI AUTONOMOUS: Offer simpler version
        else:
            → AI AUTONOMOUS: Suggest alternative card type

    # DISCONTINUATION TRIGGERS
    if card.adverse_event_reported():
        if card.type == MEDICATION:
            → ESCALATE IMMEDIATELY: Human clinician required
        else:
            → AI AUTONOMOUS: Pause card, recommend alternative

    if card.ineffective() and adequate_trial_completed():
        if card.type in [NUTRITION, MOVEMENT, SLEEP]:
            → AI AUTONOMOUS: Discontinue, try alternative
        elif card.type == MEDICATION:
            → AI RECOMMENDS: Escalate to clinician

    if card.contraindication_developed():
        → ESCALATE IMMEDIATELY: Human clinician required

    # SAFETY TRIGGERS (always escalate)
    if card.critical_alert_triggered():
        → ESCALATE IMMEDIATELY: Human clinician required
```

### **Step 3: Decision Execution**

**AI Autonomous (No Clinician Approval Needed):**
1. AI makes decision
2. AI notifies patient with clear rationale
3. Card status updated automatically
4. Dashboard reflects change
5. Clinician notified via summary report (not requiring action)

**AI Recommends (Clinician Approval Required):**
1. AI analyzes data and makes recommendation
2. Recommendation sent to clinician queue
3. Clinician reviews (approve/deny/modify)
4. AI executes approved decision
5. Patient notified

**Human Clinician Required:**
1. AI identifies need for human involvement
2. Case escalated to clinician immediately
3. Clinician makes decision
4. AI executes clinician's orders

---

## ESCALATION CRITERIA: WHEN AI MUST INVOLVE HUMAN CLINICIAN

### **Category 1: Safety-Critical (Immediate Escalation)**

- Critical dashboard alerts (life-threatening parameters)
- Adverse drug events reported
- New contraindication to active medication
- Patient reports severe symptoms
- Drug-drug interaction newly identified (high severity)
- Suicidal ideation or self-harm risk detected
- Pregnancy detected while on teratogenic medication

**AI Action:** Escalate within 15 minutes, hold any changes until clinician reviews

---

### **Category 2: High-Risk Clinical Decisions (Same-Day Escalation)**

- Stopping chronic disease medications (diabetes, hypertension, heart failure meds)
- Medication dose adjustments for high-risk drugs (insulin, warfarin, immunosuppressants)
- Canceling guideline-recommended screening tests
- Complex multi-morbidity cases (>5 active diagnoses)
- Patient declining evidence-based treatment

**AI Action:** Escalate within 4 hours, do not proceed without approval

---

### **Category 3: Moderate Complexity (Next Business Day)**

- De-prescribing medications where parameter normalized (e.g., BP meds after 6 months control)
- Ordering new diagnostic tests
- Changing treatment strategy after ineffective trial
- Patient-reported medication side effects (non-severe)
- DME discontinuation (CPAP, CGM)

**AI Action:** Recommend decision, queue for clinician review, patient notified review pending

---

### **Category 4: Routine Decisions (Summary Report Only)**

- Graduating lifestyle cards after 90 days + goal achievement
- Transitioning card complexity (beginner → intermediate)
- Pausing cards due to low adherence with alternative offered
- Completing diagnostic test cards
- Nutrition/movement/sleep card adjustments

**AI Action:** AI proceeds autonomously, clinician receives weekly summary

---

## PATIENT SELF-DIRECTED DE-LOADING PROCESS

### **Patient-Facing Interface:**

**Every SMART Card has three patient actions:**

```
┌────────────────────────────────────────────┐
│  CARD: Take Lisinopril 10mg Daily         │
│  Status: Active | Days Active: 45          │
│  Adherence: 88%                            │
├────────────────────────────────────────────┤
│  [✓ Mark Completed Today]                  │
│  [? Need Help]                             │
│  [⏸ Request to Stop/Change]               │
└────────────────────────────────────────────┘
```

### **When Patient Clicks "Request to Stop/Change":**

**Step 1: Patient Selects Reason**
- ☑ I achieved my goal
- ☑ I'm experiencing side effects
- ☑ This is too difficult for me
- ☑ I prefer a different approach
- ☑ I have questions about this card
- ☑ Other (free text)

**Step 2: AI Agent Evaluates Request**

**If reason = "Achieved goal":**
- AI checks: Has goal truly been met? (dashboard data)
- If yes → AI graduates card, celebrates success
- If no → AI provides encouragement, shows progress, suggests continuing

**If reason = "Side effects":**
- AI asks follow-up questions (severity, timing, specific symptoms)
- If severe → ESCALATE IMMEDIATELY to clinician
- If mild → AI recommends alternative card or dose adjustment, sends to clinician for approval

**If reason = "Too difficult":**
- AI offers simpler version of card (if available)
- AI suggests troubleshooting resources
- AI offers pause + alternative approach

**If reason = "Prefer different approach":**
- AI shows alternative cards for same goal
- Patient can select preferred alternative
- AI swaps cards (if low-risk) or escalates for approval

**Step 3: Decision Communicated**

AI responds within 1 hour (for routine requests) or immediately (for safety concerns):

```
┌────────────────────────────────────────────────────────────┐
│  Dr. ADAPT (AI Agent)                                      │
├────────────────────────────────────────────────────────────┤
│  I've reviewed your request to stop the Lisinopril card.  │
│                                                             │
│  Looking at your data:                                     │
│  • Your blood pressure is still elevated (142/88)          │
│  • You've been taking it consistently for 45 days          │
│  • Your side effect (dry cough) is mild but bothersome     │
│                                                             │
│  RECOMMENDATION:                                            │
│  I'm sending this to Dr. [Human Clinician] to review       │
│  switching you to Losartan, which rarely causes cough.     │
│                                                             │
│  You should hear back within 24 hours.                     │
│  Please continue Lisinopril until Dr. approves the switch. │
│                                                             │
│  [OK, I understand]                                         │
└────────────────────────────────────────────────────────────┘
```

---

## CONCRETE DE-LOADING WORKFLOWS BY SCENARIO

### **Scenario 1: Patient Achieves Goal (Lifestyle Card)**

**Context:** Patient completed "Walk 30 min daily" card for 90 days, adherence 85%

**Workflow:**
1. Day 90: AI detects sustained adherence + goal achievement
2. AI checks dashboard: Movement pillar score improved from 45 → 78
3. AI decision: AUTONOMOUS GRADUATION
4. AI sends congratulations message to patient
5. Card moves to "Graduated" tab with success badge
6. AI recommends next level: "Intermediate Walking Program: Hills & Intervals"
7. Patient can accept or decline next level
8. Dashboard updated: Movement pillar now "sustained behavior"

**Clinician Involvement:** None (summary report only)

---

### **Scenario 2: Patient Reports Medication Side Effect**

**Context:** Patient on Metformin 1000mg BID, reports severe nausea

**Workflow:**
1. Patient clicks "Request to Stop" → selects "Side effects"
2. AI asks: "How severe? Mild / Moderate / Severe / Emergency"
3. Patient selects "Severe"
4. AI asks: "When does it occur? After taking pill / All day / At night"
5. Patient selects "After taking pill"
6. AI DECISION: ESCALATE TO CLINICIAN (same-day priority)
7. AI pauses card temporarily
8. AI sends alert to clinician with patient responses
9. Clinician reviews within 4 hours
10. Clinician options:
    - Switch to extended-release Metformin
    - Reduce dose
    - Stop Metformin, try alternative (GLP-1 agonist)
11. Clinician selects: "Switch to Metformin ER 1000mg daily"
12. AI generates new card, notifies patient
13. Patient begins new card

**Clinician Involvement:** Required (medication change)

---

### **Scenario 3: Treatment Ineffective After Adequate Trial**

**Context:** Patient on DASH Diet card for 90 days, adherence 80%, but BP unchanged

**Workflow:**
1. Day 90: AI monitors dashboard: BP still 145/92 (target <130/80)
2. AI analyzes: Adherence good, adequate trial period, no improvement
3. AI DECISION: Treatment ineffective, escalate for review
4. AI message to patient: "You've done great following DASH diet, but your blood pressure hasn't improved as expected. I'm recommending Dr. [Clinician] consider adding medication."
5. AI sends recommendation to clinician
6. Clinician reviews, agrees
7. Clinician prescribes Lisinopril (new card generated)
8. DASH Diet card continues (lifestyle still important)
9. Patient now has both cards active

**Clinician Involvement:** Required (medication prescription)

---

### **Scenario 4: Patient Request to Stop Due to "Too Hard"**

**Context:** Patient struggling with "Carb Counting" card, adherence 20%

**Workflow:**
1. Patient clicks "Request to Stop" → selects "Too difficult"
2. AI analyzes: Low adherence, early in treatment (only 14 days)
3. AI DECISION: Offer simpler alternative (AUTONOMOUS)
4. AI message: "I see carb counting has been challenging. Let me offer something simpler that can still help your diabetes."
5. AI presents alternatives:
   - "Plate Method" (simpler, visual)
   - "Eat This, Not That" guide
   - "Reduce Sugary Drinks" (single behavior focus)
6. Patient selects "Plate Method"
7. AI swaps cards automatically
8. "Carb Counting" card archived with note "Too complex, transitioned to Plate Method"
9. Patient begins new card

**Clinician Involvement:** None (summary report: "Patient transitioned nutrition cards")

---

### **Scenario 5: Diagnosis Resolved**

**Context:** Patient had UTI, was on Nitrofurantoin card, now infection cleared

**Workflow:**
1. Patient uploads lab results: Urinalysis negative
2. AI detects: Infection resolved, completed 7-day antibiotic course
3. AI DECISION: AUTONOMOUS GRADUATION
4. AI message: "Great news! Your urinalysis is normal and you've completed your antibiotic course. I'm graduating your Nitrofurantoin card."
5. Card moves to "Graduated - Completed Successfully"
6. Dashboard updated: Infection resolved

**Clinician Involvement:** None (routine antibiotic completion)

---

## AI AGENT REPORTING TO CLINICIANS

### **Daily Summary (Automated Email/Dashboard)**

```
Dr. [Clinician Name] - Daily SMART Card Summary

AUTONOMOUS DECISIONS TODAY (No action needed):
• 3 cards graduated (goals achieved)
• 2 cards transitioned to advanced level
• 1 nutrition card swapped (patient preference)

PENDING YOUR REVIEW (Action needed):
• Patient A: Request to stop Lisinopril (side effect - dry cough)
  → AI Recommendation: Switch to Losartan 50mg daily
  [Approve] [Modify] [Discuss with Patient]

• Patient B: DASH Diet ineffective after 90 days, BP unchanged
  → AI Recommendation: Add Lisinopril 10mg daily
  [Approve] [Modify] [Order More Tests]

CRITICAL ALERTS (Immediate attention):
• Patient C: Reported severe chest pain while on exercise card
  → AI Action: Paused card, escalated for immediate review
  [Review Case]
```

### **Weekly Outcome Report**

```
Week of [Date] - SMART Card Outcomes

CARDS GRADUATED THIS WEEK: 24
• Medications: 5 (completed courses)
• Lifestyle: 19 (goals achieved, sustained 90 days)

CARDS DE-PRESCRIBED: 8
• Due to side effects: 3
• Due to ineffectiveness: 2
• Patient preference: 3

AI AUTONOMOUS DECISIONS: 156
AI RECOMMENDATIONS (clinician approved): 12
CLINICIAN OVERRIDES: 1 (noted for AI learning)

TOP PERFORMING CARDS (highest graduation rate):
1. Walking Program (92% graduation)
2. Sleep Hygiene (88% graduation)
3. Mediterranean Diet (85% graduation)

CARDS NEEDING ATTENTION (low adherence/completion):
1. Strength Training (32% adherence)
2. Meditation (40% adherence)
3. Carb Counting (28% adherence)
```

---

## PATIENT EDUCATION: "HOW TO KNOW WHEN TO STOP A CARD"

**In patient-facing documentation:**

### **When Can I Stop a SMART Card?**

**You've Achieved Your Goal**
- The behavior is now a habit (you do it automatically)
- Your health metrics have improved and stayed improved
- You feel confident continuing on your own
- Dr. ADAPT will celebrate with you and graduate your card!

**It's Not Working for You**
- You've tried earnestly but it's too difficult
- You prefer a different approach
- You're experiencing side effects (medications)
- Request a change anytime - Dr. ADAPT will help find an alternative

**You Have Questions**
- Not sure if you're doing it right
- Want to understand why it's important
- Concerned about continuing
- Dr. ADAPT can answer questions or connect you with your clinician

**IMPORTANT:**
- Some cards (like medications) require clinician approval to stop
- Dr. ADAPT will let you know if your request needs clinician review
- Never stop a medication without asking first - even if you feel better!

---

## TECHNICAL IMPLEMENTATION NOTES

### **Database Schema Additions**

**Table: card_instances**
- Add fields:
  - `de_prescribing_trigger` (enum: goal_achieved, ineffective, side_effect, patient_preference, contraindication, diagnosis_resolved)
  - `de_prescribed_date` (timestamp)
  - `de_prescribed_by` (AI_AGENT | CLINICIAN_ID)
  - `de_prescription_notes` (text)
  - `graduation_status` (boolean)

**Table: ai_decisions**
- Track every AI decision for auditing
- Fields: decision_type, confidence_score, data_used, outcome, clinician_override

**Table: clinician_queue**
- AI recommendations awaiting clinician approval
- Priority levels: CRITICAL | HIGH | MEDIUM | ROUTINE
- Expected response time based on priority

---

## FUTURE ENHANCEMENTS

1. **Machine Learning Improvement**
   - AI learns from clinician overrides
   - Improves recommendation accuracy over time
   - Personalized patient profiles (this patient responds better to X)

2. **Predictive De-Prescribing**
   - AI predicts when patient likely to request stopping
   - Proactively offers support or alternatives

3. **Patient Preference Learning**
   - AI learns patient's preferences over time
   - Recommends cards more aligned with patient values

4. **Outcome-Based Optimization**
   - Track which cards have highest success rates
   - Recommend most effective cards first

---

## SUMMARY

**This specification provides:**

✅ **Concrete de-loading processes** for all **12 card types** (v1.1 update)
✅ **AI agent (Dr. ADAPT) architecture** for autonomous oversight
✅ **Clear escalation criteria** (when human clinician required)
✅ **Patient self-directed workflows** for requesting card changes
✅ **Decision algorithms** for AI to determine when to stop cards
✅ **Safety mechanisms** to prevent premature or unsafe stopping
✅ **Self-directed healthcare model** with patient autonomy by card type

**Key Innovation:**
> AI handles 80% of routine card lifecycle decisions autonomously, escalating only when safety, complexity, or patient preference requires human clinical judgment.

**Self-Directed Healthcare Philosophy:**
> Patients are the primary healthcare providers for themselves. Clinicians are guidance counselors who guide, counsel, and redirect as needed. Behavioral cards (7-12) are fully patient self-directed; Medical cards (1-6) require appropriate clinical oversight.

**Related Documentation:**
- [CARD_LIFECYCLE_AND_AI_PARAMETERS.md](docs/core/CARD_LIFECYCLE_AND_AI_PARAMETERS.md) - Complete lifecycle phases (Initiation → Maintenance → De-loading) and AI bracket `[ ]` parameter notation
- [UNIVERSAL_CARD_TEMPLATE.md](docs/core/02_UNIVERSAL_CARD_TEMPLATE.md) v2.0 - Template with embedded lifecycle sections

---

**VERSION HISTORY**
- v1.1 (2025-12-05): Added 3 missing card types, linked to lifecycle spec, 12-type summary table
- v1.0 (2025-11-26): Initial specification with 9 card types

---

**END OF DOCUMENT**
