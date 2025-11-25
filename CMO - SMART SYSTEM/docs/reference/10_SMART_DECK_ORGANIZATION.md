# SMART DECK ORGANIZATION

## Deck Definition

A **SMART Deck** is a collection of individual SMART Cards that work together to achieve a common clinical goal.

**Examples**:
- "Hypertension Management Deck"
- "Type 2 Diabetes Control Deck"
- "Sleep Hygiene Deck"
- "Weight Loss Deck"
- "Post-MI Recovery Deck"

---

## DECK ASSEMBLY PRINCIPLES

### Principle 1: Derive Deck Metadata from Individual Cards

**Do NOT create separate deck structure**. Instead, **auto-generate deck properties** from the active cards within the deck.

#### Auto-Generated Deck Properties

```json
{
  "deck_name": "Hypertension Management Deck",
  "deck_id": "DECK_HTN_001",
  "active_cards": [
    "MED_ACE_Lisinopril_10mg",
    "VITAL_BP_Home_Monitoring",
    "NUTR_DASH_Diet",
    "EXER_Walking_30min",
    "LAB_BMP_Q6months"
  ],
  "clinical_goals": [
    "Cardiovascular System: Reduce Risk"
  ],
  "evidence_grade": "A",  // Lowest grade among all cards
  "total_time_burden": "45 min/day",  // Sum of all card times
  "overall_feasibility": "78%",  // Weighted average
  "conflict_check": "CLEAR",  // AI flags any card-to-card issues
  "created_date": "2024-11-16",
  "last_modified": "2024-11-16",
  "active_since": "2024-11-16"
}
```

#### Deck Evidence Grade Logic
```
IF any card is Grade C → Deck is Grade C
ELSE IF any card is Grade B → Deck is Grade B  
ELSE → Deck is Grade A

(Lowest common denominator approach)
```

#### Deck Feasibility Score
```
Overall Feasibility = Weighted Average of Individual Card Feasibility

Example:
- Lisinopril: 85% (weight: 30% - high priority)
- BP Monitoring: 90% (weight: 20%)
- DASH Diet: 65% (weight: 25%)
- Walking: 75% (weight: 25%)

Deck Feasibility = (85×0.30) + (90×0.20) + (65×0.25) + (75×0.25)
                 = 25.5 + 18 + 16.25 + 18.75
                 = 78.5%
```

---

## PRINCIPLE 2: CARD SELECTION FOR SYNERGY

Cards within a deck should be selected to:

### A. Work Toward Common Goal
All cards should contribute to the same clinical outcome:
```
Goal: Lower BP to <130/80 mmHg

Supporting Cards:
✅ Lisinopril (directly lowers BP)
✅ Low sodium diet (reduces BP 4-8 mmHg)
✅ DASH diet (reduces BP 8-14 mmHg)
✅ Walking (reduces BP 5-8 mmHg)
✅ Stress management (reduces BP 4-6 mmHg)
❌ Diabetes education (unrelated to BP goal)
```

### B. Minimize Time Burden Through Natural Bundling
```
Bundle Compatible Actions:

Morning Cluster (10 min):
- Wake up → Weigh → Check BP → Take meds → Log

Evening Cluster (15 min):
- After dinner → Check BP → Deep breathing → Log

Weekly Cluster (Sunday, 2 hours):
- Meal prep for DASH diet → Pre-portion snacks
```

### C. Avoid Conflicts
```
Check for:
❌ Drug-drug interactions
❌ Contradictory instructions
❌ Incompatible timing
❌ Redundant actions

Example Conflicts:
❌ ACE inhibitor + ARB (duplicate mechanism)
❌ Low sodium diet + high potassium supplements (hyperkalemia risk)
❌ Keto diet + DASH diet (contradictory)
```

### D. Maximize Synergy
```
Look for Complementary Effects:

Synergistic Combo 1:
✅ ACE inhibitor + Low sodium diet + DASH diet
→ All lower BP through different mechanisms
→ Additive effect: 25-35 mmHg reduction

Synergistic Combo 2:
✅ Metformin + Low-carb diet + Walking
→ All improve glucose control
→ Additive effect: 1.5-2% HbA1c reduction
```

---

## PRINCIPLE 3: PATIENT DECK VIEW

### What Patients See in Their App

```
╔════════════════════════════════════════════╗
║  MY CARE PLAN                              ║
║  Hypertension Management Deck             ║
╠════════════════════════════════════════════╣
║                                            ║
║  Overall Progress: 78% ████████░░          ║
║  Time in Plan: 23 days                     ║
║  Next Review: Dec 9, 2024                  ║
║                                            ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                            ║
║  ACTIVE CARDS (5):                         ║
║                                            ║
║  1. 💊 Lisinopril 10mg Daily               ║
║     ✓ On track (95% adherence)            ║
║     Last dose: Today at 8:15am            ║
║     [View Card]                            ║
║                                            ║
║  2. 📊 Home BP Monitoring                  ║
║     ✓ On track (85% adherence)            ║
║     Latest: 138/86 (Nov 16, 7am)          ║
║     Target: <130/80                        ║
║     [View Card] [Log Reading]              ║
║                                            ║
║  3. 🥗 DASH Diet                           ║
║     ⚠️  Needs attention (60% adherence)    ║
║     [View Card] [Tips]                     ║
║                                            ║
║  4. 🏃 Walking 30 Minutes                  ║
║     ✓ On track (70% adherence)            ║
║     This week: 4/5 walks done             ║
║     [View Card] [Start Walk]               ║
║                                            ║
║  5. 🔬 BMP Lab Every 6 Months              ║
║     📅 Next due: May 16, 2025              ║
║     [View Card] [Schedule]                 ║
║                                            ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                            ║
║  [ View Full Deck Details ]                ║
║  [ Message Care Team ]                     ║
║                                            ║
╚════════════════════════════════════════════╝
```

### Key Features for Patients

**1. One-Page Overview**
- See all active cards at once
- Quick status check (✓ on track, ⚠️ needs attention)
- Easy navigation to individual cards

**2. Overall Progress Bar**
```
Progress = % of cards meeting adherence targets

Example:
- 4 out of 5 cards at >70% adherence
- Progress: 80%
```

**3. Visual Status Indicators**
- ✓ Green = On track
- ⚠️ Yellow = Needs attention
- ❌ Red = Off track / urgent

**4. Time in Deck**
- Shows how long patient has been following this plan
- Motivational (celebrates longevity)

**5. Next Review Date**
- When clinician will reassess plan
- Creates accountability and expectation

**6. One-Tap Actions**
- [View Card] → Opens full card details
- [Log Reading] → Quick data entry
- [Start Walk] → Timer/tracker
- [Schedule] → Calendar integration

---

## PRINCIPLE 4: DECK LIFECYCLE

### Phase 1: Deck Initiation

```
Process:
1. AI analyzes patient data → Suggests initial deck
2. Clinician reviews AI suggestion
3. Clinician modifies (adds/removes/adjusts cards)
4. Clinician documents clinical reasoning
5. Deck published to patient
6. Patient receives notification
7. Patient reviews cards and asks questions
8. Deck officially starts
```

**Initiation Checklist**:
- [ ] All cards reviewed for appropriateness
- [ ] Conflicts checked (drug interactions, contradictions)
- [ ] Feasibility assessed (time burden, barriers)
- [ ] Patient goals incorporated
- [ ] Follow-up schedule set
- [ ] Patient education provided

### Phase 2: Active Management

**Patient Responsibilities**:
- Execute cards daily/weekly as prescribed
- Log data (medications, vitals, activities)
- Report barriers and side effects
- Ask questions when confused

**System Responsibilities**:
- Send reminders (if enabled)
- Track adherence and outcomes
- Flag issues (low adherence, worsening metrics)
- Generate reports for clinician

**Clinician Responsibilities**:
- Review progress reports weekly/monthly
- Respond to patient messages
- Adjust cards as needed
- Celebrate wins and troubleshoot barriers

### Phase 3: Monitoring & Adjustment

**Weekly Auto-Generated Report**:
```
╔═══════════════════════════════════════════╗
║  DECK MONITORING REPORT                   ║
║  Patient: John Doe                        ║
║  Deck: Hypertension Management            ║
║  Week: Nov 10-16, 2024                    ║
╠═══════════════════════════════════════════╣
║                                           ║
║  ADHERENCE SUMMARY:                       ║
║  • Lisinopril: 7/7 days ✓                 ║
║  • BP Monitoring: 12/14 checks ✓          ║
║  • DASH Diet: 4/7 days ⚠️                 ║
║  • Walking: 3/5 planned ⚠️                ║
║                                           ║
║  OUTCOME TRENDS:                          ║
║  • BP: 142/88 → 138/86 (improving)        ║
║  • Weight: 185 lbs (stable)               ║
║                                           ║
║  ALERTS:                                  ║
║  ⚠️  DASH diet adherence declining        ║
║     → Patient reports: "Too hard to cook" ║
║     → Suggestion: Meal delivery service?  ║
║                                           ║
║  ⚠️  Walking frequency suboptimal         ║
║     → Patient reports: "Too tired"        ║
║     → Suggestion: Reduce to 3x/week?      ║
║                                           ║
║  [ Contact Patient ]  [ Adjust Deck ]     ║
║                                           ║
╚═══════════════════════════════════════════╝
```

**Trigger Events for Adjustment**:
- Adherence <50% on any card for 2+ weeks
- No progress toward target after 4-6 weeks
- Patient reports intolerable side effects
- New diagnosis or condition changes
- Patient requests modification

### Phase 4: Graduation or Completion

**Deck Graduation Criteria**:
```
Deck can be graduated when:
✅ Target goal achieved for 3 months
✅ Patient confident in maintaining independently
✅ No adverse events
✅ Clinician approves graduation

Example: HTN Deck Graduation
- BP <130/80 for 3 consecutive months
- Patient taking meds consistently
- Lifestyle changes habituated
- Patient knows when to check BP

→ Transition to "Maintenance Deck" (simplified version)
```

**Maintenance Deck** (post-graduation):
```
Hypertension Maintenance Deck:
1. Continue Lisinopril daily
2. BP check 1x/week (reduced from daily)
3. Continue DASH principles (less rigid tracking)
4. Continue walking (habit established)
5. BMP every 6 months

→ Fewer cards, less intensive monitoring
→ Patient self-manages with periodic clinician check-ins
```

**Deck Termination** (goal no longer relevant):
```
Reasons to End Deck:
- Condition resolved (e.g., gestational diabetes post-delivery)
- Patient preference (wants to stop)
- Card replaced by better alternative
- Patient transfers care

Process:
1. Clinician documents reason for termination
2. Patient notified
3. Deck archived (data retained for history)
4. Follow-up plan documented
```

---

## DECK SYNERGY ANALYSIS

### How Cards Work Together

```
Example: Hypertension Management Deck

Card 1: Lisinopril 10mg Daily
↓ Primary BP reduction (10-15 mmHg)

Card 2: DASH Diet
↓ Additive BP reduction (8-14 mmHg)

Card 3: Low Sodium (<2000mg/day)
↓ Enhances DASH effect (4-8 mmHg)

Card 4: Walking 30min 5x/week
↓ Further BP reduction (5-8 mmHg)

Card 5: Stress Management (Deep Breathing)
↓ Acute BP lowering during stress (4-6 mmHg)

Card 6: BP Monitoring BID
↓ Tracks effectiveness of all above

Card 7: BMP Every 6 Months
↓ Monitors safety of Lisinopril (K+, Creatinine)

═══════════════════════════════════════════════
CUMULATIVE EFFECT: 31-51 mmHg reduction expected
(Individual effects may not be fully additive, but synergistic)
```

### Synergy Score (AI-Calculated)
```
Synergy Score = Measure of how well cards complement each other

High Synergy (>80):
- Multiple cards target same outcome
- Mechanisms don't conflict
- Timing compatible
- Patient able to manage combined burden

Low Synergy (<50):
- Cards target different outcomes
- Risk of conflicts
- Timing incompatible
- Patient overwhelmed by burden
```

---

## DECK COMPLEXITY MANAGEMENT

### Simple Deck (Beginner)
```
Characteristics:
- 2-3 cards only
- Low time burden (<20 min/day)
- High feasibility (>80%)
- Minimal drug interactions
- Easy to track

Example: "Simple HTN Deck"
1. Lisinopril 10mg daily
2. Home BP monitoring
```

### Moderate Deck (Intermediate)
```
Characteristics:
- 4-6 cards
- Moderate time burden (20-40 min/day)
- Moderate feasibility (60-80%)
- Some monitoring required

Example: "Standard HTN Deck"
1. Lisinopril 10mg daily
2. Home BP monitoring BID
3. DASH diet
4. Walking 30 min 3x/week
5. BMP every 6 months
```

### Complex Deck (Advanced)
```
Characteristics:
- 7+ cards
- High time burden (>40 min/day)
- Multiple medications
- Intensive monitoring

Example: "Comprehensive HTN + DM Deck"
1. Lisinopril 10mg daily
2. Metformin 1000mg BID
3. Atorvastatin 20mg daily
4. Home BP monitoring BID
5. Home glucose monitoring TID
6. DASH diet
7. Walking 30 min 5x/week
8. Stress management
9. BMP every 3 months
10. HbA1c every 3 months
```

**Important**: Start simple, add complexity gradually as patient demonstrates adherence.

---

## DECK SUCCESS METRICS

### Definition of Deck Success

```
Deck is successful when:

1. Clinical Targets Met:
   ✓ Primary outcome achieved (e.g., BP <130/80)
   ✓ No adverse events
   ✓ Patient safe and stable

2. Behavioral Targets Met:
   ✓ Adherence >70% on all cards
   ✓ Patient confident in self-management
   ✓ Lifestyle changes sustained

3. Patient Experience Positive:
   ✓ Patient satisfied with care
   ✓ Feels empowered and in control
   ✓ Quality of life maintained or improved
```

### Tracking Deck Performance

```
Metrics Dashboard:

Overall Deck Adherence: 73% ████████░░
Target Achievement: 80% ████████░░
Time to Target: 8 weeks (expected: 6-12 weeks)
Patient Satisfaction: 9/10 ⭐⭐⭐⭐⭐

Card-by-Card Performance:
1. Lisinopril: 95% adherence ✓
2. BP Monitoring: 85% adherence ✓
3. DASH Diet: 60% adherence ⚠️
4. Walking: 70% adherence ✓
5. BMP: Completed on time ✓

Barriers Reported:
• DASH diet too time-consuming (patient struggling)

Action Needed:
→ Simplify DASH diet or provide meal delivery option
```

---

## DECK VS. INDIVIDUAL CARDS

### When to Use a Deck
- Complex condition requiring multimodal approach
- Multiple interventions work synergistically
- Long-term management needed (chronic disease)
- Patient able to manage multiple cards

### When to Use Individual Cards
- Simple, acute issue
- Single intervention sufficient
- Patient overwhelmed by complexity
- Testing patient's readiness before adding more

**Principle**: Start simple, build complexity as patient demonstrates capability.

---

## CONCLUSION

SMART Decks organize individual cards into cohesive, goal-directed care plans that:
- ✅ Work synergistically toward common outcomes
- ✅ Minimize patient burden through smart bundling
- ✅ Adapt based on patient progress and feedback
- ✅ Balance clinical rigor with real-world feasibility

The deck is the **operational unit** of patient care, while individual cards remain the **building blocks**.