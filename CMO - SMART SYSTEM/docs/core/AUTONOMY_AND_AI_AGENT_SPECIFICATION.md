# AUTONOMY TIERS & AI AGENT SPECIFICATION

**Version:** 1.0
**Date:** 2025-12-07
**Status:** Draft for Review

---

## PURPOSE

This document defines:
1. Patient autonomy levels across card types
2. AI agent roles and responsibilities
3. Clinician oversight workflows
4. Legal sign-off requirements

**Core Principle:** Maximize patient self-direction while maintaining clinical safety and legal compliance. All clinical decisions require licensed clinician authorization, but the *timing and method* of that authorization varies by risk level.

---

## PART 1: AUTONOMY TIERS

### Overview

| Tier | Risk Level | Patient Role | AI Role | Clinician Role |
|------|------------|--------------|---------|----------------|
| **1** | Minimal | Full control | Tracks, encourages | Protocol approval only |
| **2** | Low | Guided control | Recommends, monitors | Batch approval + exceptions |
| **3** | Moderate | Executes approved plan | Recommends, adjusts within bounds | Individual approval |
| **4** | High | Follows direction | Recommends only | Approves all decisions |

---

### Tier 1: Protocol-Approved Autonomy

**Risk Level:** Minimal
**Legal Model:** Clinician pre-approves protocol; patient acts freely within it

**Card Types:**
- Micro-Learning (educational content)

**How It Works:**
```
1. Clinician approves: "Patient may access all Micro-Learning cards"
   (One-time blanket approval at onboarding)

2. Patient browses, starts, completes cards freely

3. AI tracks engagement, suggests relevant content

4. No per-card approval needed
```

**Clinician Touchpoint:** Annual protocol review

---

### Tier 2: AI-Guided Autonomy

**Risk Level:** Low
**Legal Model:** Clinician approves care plan category; AI guides within bounds; clinician reviews exceptions

**Card Types:**
- Nutrition
- Movement/Exercise
- Recovery/Sleep
- Mind-Body
- Environmental/Social

**Responsible AI Agents:**
- AI Health Coach (overall behavioral guidance)
- AI Nutritionist (nutrition cards)
- AI Physical Therapist (movement cards)

**How It Works:**
```
1. Clinician approves: "Patient cleared for behavioral interventions
   in Nutrition, Movement, Recovery. No restrictions."
   (Care plan approval at visit)

2. AI agents recommend specific cards based on patient goals/data
   Example: AI Nutritionist suggests "Increase Vegetable Intake" card

3. Patient can:
   - Accept/decline recommendations
   - Start cards immediately (no wait for approval)
   - Adjust intensity/frequency freely
   - Pause or stop anytime

4. AI monitors progress, adjusts recommendations

5. Clinician reviews:
   - Monthly summary (async, batch review)
   - Immediate alert if: safety flag, no progress 12 weeks, patient request
```

**Clinician Touchpoint:**
- Care plan approval (visit)
- Monthly async review (2-3 min)
- Exception alerts (as needed)

**Sign-Off Workflow:**
```
┌─────────────────────────────────────────────────────┐
│  CARE PLAN APPROVAL (One-time at visit)            │
│                                                     │
│  "I approve [Patient] for self-directed            │
│   behavioral interventions in:                      │
│   ☑ Nutrition  ☑ Movement  ☑ Recovery              │
│   ☑ Mind-Body  ☑ Environmental                     │
│                                                     │
│   Restrictions: None / [specify]                   │
│                                                     │
│   Valid until: Next visit / [date]                 │
│                                                     │
│   [Sign & Approve]                                 │
└─────────────────────────────────────────────────────┘
```

---

### Tier 3: AI-Assisted with Approval

**Risk Level:** Moderate
**Legal Model:** AI recommends; clinician approves (streamlined); patient executes

**Card Types:**
- OTC Medications
- Supplements
- Routine Diagnostic Testing (standard labs)
- Basic DME (BP cuff, scale, pill organizer)
- Specialist Referrals

**Responsible AI Agents:**
- AI Pharmacist (OTC, supplements)
- AI Care Coordinator (testing, referrals, DME)

**How It Works:**
```
1. AI agent identifies need
   Example: AI Pharmacist notes patient has occasional heartburn,
   no red flags, recommends OTC antacid card

2. Recommendation queued for clinician
   (Grouped with similar low-risk items for efficient review)

3. Clinician reviews batch (e.g., daily or twice-daily)
   - Quick approve: 1 click per item
   - Modify: adjust recommendation
   - Reject: with reason

4. Approved cards immediately available to patient

5. Patient executes, AI monitors

6. Changes within approved parameters: no re-approval
   Changes outside parameters: back to queue
```

**Clinician Touchpoint:**
- Batch review 1-2x daily (5-10 min total)
- Individual review if complex

**Sign-Off Workflow:**
```
┌─────────────────────────────────────────────────────┐
│  AI RECOMMENDATIONS - BATCH REVIEW                  │
│  12 items pending (estimated 4 min)                │
│                                                     │
│  LOW-RISK OTC/SUPPLEMENTS (8 items)                │
│  ┌────────────────────────────────────────────┐    │
│  │ ☑ J. Smith - Antacid PRN for heartburn     │    │
│  │ ☑ M. Jones - Melatonin 3mg for sleep       │    │
│  │ ☑ R. Lee - Vitamin D 2000IU daily          │    │
│  │ ...                                         │    │
│  │ [Approve All Selected] [Review Individually]│    │
│  └────────────────────────────────────────────┘    │
│                                                     │
│  ROUTINE LABS (3 items)                            │
│  ┌────────────────────────────────────────────┐    │
│  │ ☑ J. Smith - Annual lipid panel            │    │
│  │ ☑ M. Jones - A1c (3-month f/u)             │    │
│  │ ...                                         │    │
│  └────────────────────────────────────────────┘    │
│                                                     │
│  DME (1 item)                                      │
│  ┌────────────────────────────────────────────┐    │
│  │ ☑ R. Lee - Home BP monitor                 │    │
│  └────────────────────────────────────────────┘    │
│                                                     │
│  [Approve All] [Sign & Complete Batch]             │
└─────────────────────────────────────────────────────┘
```

---

### Tier 4: Clinician-Directed

**Risk Level:** High
**Legal Model:** AI recommends; clinician individually reviews and approves; patient executes

**Card Types:**
- Prescription Medications
- Controlled Substances
- Procedures
- Imaging Studies
- High-risk Diagnostic Testing
- Critical DME (CPAP, CGM, oxygen, insulin pumps)

**Responsible AI Agents:**
- AI Pharmacist (medication recommendations)
- AI Cardiologist, AI Endocrinologist, etc. (specialty recommendations)
- AI Care Coordinator (procedures, imaging)

**How It Works:**
```
1. AI specialist agent analyzes patient data
   Example: AI Endocrinologist reviews A1c 7.8%, recommends Metformin

2. AI generates detailed recommendation with rationale
   - Why this medication
   - Dose justification
   - Relevant patient factors considered
   - Alternatives if applicable

3. Recommendation appears in clinician queue
   (Flagged by urgency: routine, soon, urgent)

4. Clinician reviews individually
   - Approve as recommended
   - Modify (dose, timing, alternative)
   - Reject with reason
   - Request more information

5. Approved card assigned to patient

6. ALL changes require clinician approval:
   - Dose adjustments
   - Discontinuation
   - Switching medications

7. Exceptions (patient can act, AI alerts clinician):
   - Emergency hold for safety concern
   - Resume after brief (<7 day) pause
```

**Clinician Touchpoint:**
- Individual review for each recommendation
- All transitions and changes

**Sign-Off Workflow:**
```
┌─────────────────────────────────────────────────────┐
│  AI RECOMMENDATION - INDIVIDUAL REVIEW              │
│                                                     │
│  Patient: Robert Chen, 58M                          │
│  Recommendation: Initiate Metformin IR              │
│                                                     │
│  AI AGENT: AI Endocrinologist                       │
│                                                     │
│  CLINICAL RATIONALE:                                │
│  • Diagnosis: Type 2 Diabetes (A1c 7.8%)           │
│  • First-line therapy per ADA guidelines           │
│  • eGFR 68 - no renal contraindication             │
│  • No metformin allergies documented               │
│  • BMI 31 - weight neutrality beneficial           │
│                                                     │
│  RECOMMENDED:                                       │
│  • Metformin IR 500mg BID with meals               │
│  • Titrate to 1000mg BID over 4 weeks              │
│  • A1c recheck in 3 months                         │
│                                                     │
│  PATIENT FACTORS APPLIED:                           │
│  • No adjustments needed (standard protocol)        │
│                                                     │
│  ALTERNATIVES CONSIDERED:                           │
│  • Metformin ER - if GI intolerance develops       │
│  • GLP-1 - if weight loss primary goal             │
│                                                     │
│  [✓ Approve] [✎ Modify] [✗ Reject] [? More Info]   │
└─────────────────────────────────────────────────────┘
```

---

## PART 2: AI AGENT ECOSYSTEM

### Agent Architecture

```
                    ┌─────────────────────┐
                    │   DR. ADAPT         │
                    │   (Orchestrator)    │
                    │                     │
                    │   Coordinates all   │
                    │   AI agents         │
                    └──────────┬──────────┘
                               │
        ┌──────────────────────┼──────────────────────┐
        │                      │                      │
        ▼                      ▼                      ▼
┌───────────────┐    ┌───────────────┐    ┌───────────────┐
│  BEHAVIORAL   │    │   MEDICAL     │    │  OPERATIONAL  │
│  AGENTS       │    │   AGENTS      │    │  AGENTS       │
└───────┬───────┘    └───────┬───────┘    └───────┬───────┘
        │                    │                    │
   ┌────┴────┐          ┌────┴────┐          ┌────┴────┐
   │         │          │         │          │         │
   ▼         ▼          ▼         ▼          ▼         ▼
Health    Physical   Pharmacist Specialists  Care     Data
Coach     Therapist             (Cardio,    Coord    Watch
          Nutritionist          Endo, etc)
```

### Agent Definitions

#### DR. ADAPT (Orchestrator)
**Role:** Coordinates all AI agents, resolves conflicts, presents unified recommendations

**Responsibilities:**
- Routes patient data to appropriate specialist agents
- Synthesizes recommendations from multiple agents
- Resolves conflicts between agent recommendations
- Prioritizes recommendations by urgency
- Presents unified care plan to clinician

**Does NOT:** Make final clinical decisions (always defers to clinician)

---

#### Behavioral Agents (Tier 2)

**AI Health Coach**
- **Scope:** Overall behavioral strategy, motivation, habit formation
- **Cards:** All behavioral cards (coordination)
- **Autonomy:** High - guides patient directly within approved care plan
- **Escalates to clinician:** No progress 12 weeks, safety concerns, patient request

**AI Nutritionist**
- **Scope:** Dietary recommendations, meal planning, nutrition education
- **Cards:** Nutrition cards
- **Autonomy:** High - recommends and adjusts within care plan
- **Escalates to clinician:** Disordered eating signs, significant weight change, medical nutrition therapy needed

**AI Physical Therapist**
- **Scope:** Movement, exercise, physical rehabilitation
- **Cards:** Movement/Exercise cards
- **Autonomy:** High - recommends and adjusts within care plan
- **Escalates to clinician:** Injury, pain during exercise, cardiac symptoms, mobility decline

---

#### Medical Agents (Tier 3-4)

**AI Pharmacist**
- **Scope:** Medication recommendations, interactions, OTC guidance
- **Cards:** All medication cards (OTC through Rx)
- **Autonomy:**
  - Tier 3 (OTC/supplements): Recommends, batch approval
  - Tier 4 (Rx): Recommends, individual approval
- **Escalates to clinician:** All Rx decisions, interaction concerns, adverse effects

**AI Cardiologist**
- **Scope:** Cardiovascular assessment, BP/lipid management
- **Cards:** CV medications, cardiac testing, cardiac DME
- **Autonomy:** Recommends only (Tier 4)
- **Escalates to clinician:** All recommendations require approval

**AI Endocrinologist**
- **Scope:** Diabetes, thyroid, metabolic conditions
- **Cards:** Diabetes medications, metabolic testing
- **Autonomy:** Recommends only (Tier 4)
- **Escalates to clinician:** All recommendations require approval

*[Additional specialist agents as needed: Pulmonologist, Nephrologist, etc.]*

---

#### Operational Agents (Supporting)

**AI Care Coordinator**
- **Scope:** Scheduling, referrals, DME ordering, care transitions
- **Cards:** Referral cards, DME cards, Testing cards
- **Autonomy:**
  - Tier 3 (routine): Batch approval
  - Tier 4 (complex): Individual approval
- **Escalates to clinician:** Urgent referrals, complex DME

**DataWatch**
- **Scope:** Continuous monitoring, alert generation, trend analysis
- **Cards:** None (monitors all)
- **Autonomy:** Monitors and alerts only
- **Escalates to clinician:** Threshold breaches, concerning trends, missed check-ins

---

### Agent Interaction Rules

**Rule 1: Single Recommendation per Issue**
- Multiple agents may analyze same data
- DR. ADAPT synthesizes into ONE recommendation
- No conflicting cards presented to patient

**Rule 2: Specialist Deference**
- General agents defer to specialists for their domain
- AI Health Coach defers to AI Nutritionist on diet specifics
- AI Pharmacist defers to AI Cardiologist on cardiac drugs

**Rule 3: Safety Agent Override**
- DataWatch can flag ANY recommendation for safety review
- Safety flags go to clinician regardless of tier

**Rule 4: Patient Preference Integration**
- Agents consider patient's stated preferences
- Preference conflicts flagged to clinician (not overridden by AI)

---

## PART 3: LEGAL SIGN-OFF FRAMEWORK

### Core Requirement
**All clinical decisions require licensed clinician authorization.**

### Authorization Methods by Tier

| Tier | Method | Timing | Documentation |
|------|--------|--------|---------------|
| 1 | Protocol Approval | Prospective (onboarding) | Signed protocol consent |
| 2 | Care Plan Approval | Prospective (per visit) | Signed care plan |
| 3 | Batch Approval | Near-real-time (1-2x daily) | Electronic signature per batch |
| 4 | Individual Approval | Real-time (before patient sees) | Electronic signature per item |

### Protocol Approval (Tier 1)
```
Document: "Self-Directed Education Protocol"

I authorize [Patient Name] to access educational Micro-Learning
content through the CMO platform without individual approval
for each item.

I have reviewed the content categories and confirm they are
appropriate for this patient.

This authorization is valid until: [Date/Next Visit]

Clinician Signature: _____________  Date: _______
```

### Care Plan Approval (Tier 2)
```
Document: "Behavioral Care Plan Authorization"

I authorize [Patient Name] to engage in self-directed behavioral
interventions with AI guidance in the following categories:

☑ Nutrition     ☑ Movement     ☑ Recovery
☑ Mind-Body     ☑ Environmental

Restrictions/Modifications:
☐ None
☐ Specific restrictions: _______________________

I will review monthly progress summaries and respond to
exception alerts within 48 hours.

This authorization is valid until: [Date/Next Visit]

Clinician Signature: _____________  Date: _______
```

### Batch Approval (Tier 3)
```
Document: "Low-Risk Recommendation Batch"

Date: [Date]  Time: [Time]
Items in batch: [N]

I have reviewed the AI-generated recommendations below and
authorize their implementation:

[List of approved items with patient names]

Electronic Signature: [Clinician Name]
Timestamp: [Auto-generated]
```

### Individual Approval (Tier 4)
```
Document: "Clinical Order Authorization"

Patient: [Name]  DOB: [DOB]  MRN: [MRN]

Order: [Medication/Procedure/Test]
Dose/Details: [Specifics]

AI Agent: [Which agent recommended]
AI Rationale: [Summary of reasoning]

I have reviewed this recommendation, the patient's clinical
status, and approve this order.

☐ Approved as recommended
☐ Approved with modifications: _______________

Electronic Signature: [Clinician Name]
Timestamp: [Auto-generated]
```

---

## PART 4: PATIENT ACTIONS BY TIER

### What Patients Can Do Without Approval

| Action | Tier 1 | Tier 2 | Tier 3 | Tier 4 |
|--------|--------|--------|--------|--------|
| Start card | ✓ | ✓ | After approval | After approval |
| Adjust intensity | ✓ | ✓ | Within bounds | Needs approval |
| Pause | ✓ | ✓ | ✓ (AI notified) | ✓ (AI alerts clinician) |
| Resume <7 days | ✓ | ✓ | ✓ | ✓ |
| Resume >7 days | ✓ | ✓ | ✓ | Needs approval |
| Stop/discontinue | ✓ | ✓ | ✓ (logged) | Needs approval |
| Request change | N/A | ✓ (AI adjusts) | Queued | Queued |

### Emergency Patient Actions (All Tiers)
Patients can ALWAYS:
- Hold any medication for safety concern (AI immediately alerts clinician)
- Report adverse effects (AI escalates appropriately)
- Request to speak with clinician
- Decline any recommendation

---

## PART 5: IMPLEMENTATION NOTES

### Card Metadata Addition
Each card should include in AI metadata:
```yaml
autonomy:
  tier: 2  # or 1, 3, 4
  responsible_agent: AI_Nutritionist
  approval_type: care_plan  # protocol, batch, individual
  patient_can_initiate: true
  patient_can_adjust: true
  patient_can_discontinue: true
  escalation_triggers:
    - safety_concern
    - no_progress_12_weeks
```

### Clinician Workload Estimates

| Tier | Time per Patient per Month |
|------|---------------------------|
| Tier 1 | ~0 (protocol set once) |
| Tier 2 | 2-3 min (monthly summary review) |
| Tier 3 | 5-10 min (batch reviews) |
| Tier 4 | Varies (individual review each) |

**Total for 100 patients (mixed acuity):** ~2-3 hours/week

---

## CHANGELOG

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-12-07 | Initial draft |

---

**END OF DOCUMENT**
