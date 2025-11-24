# BEHAVIORAL DESIGN & ADHERENCE SUPPORT

## Core Principle
Cards should be selected and sequenced to naturally fit into patients' existing routines with minimal added friction.

---

## HABIT STACKING & SYNERGY INTEGRATION

### Concept
Link new health behaviors to existing habits and routines to increase adherence through automatic cue-action patterns.

### Implementation in Cards

#### 1. In "HOW" Section - Synergy Tips

Every card should include synergy guidance when applicable:

```markdown
**Synergy Tips** (Do This WITH...):

Pair with: [Related card in patient's deck]
  Example: "Take this medication when you check your blood pressure (BP Monitoring card)"
  Example: "Do your stretching right after your daily walk (Walking Exercise card)"

Stacks well with: [Complementary cards]
  Example: "This low-sodium meal plan works great with your DASH diet card and 
  potassium-rich foods card"

Time-Saving Combo: [Bundle actions]
  Example: "Batch your morning medications, BP check, and weight check into one 
  5-minute routine at the same time every day"
```

**Important**: Only sync with ACTIVE cards in the patient's current plan.

#### 2. Deck Assembly Level

When AI and clinician select cards, prioritize:
- **Similar timing**: Morning med cluster, evening routine
- **Natural transitions**: Exercise → hydrate → stretch → log
- **Shared preparation**: Meal prep → cook → eat → log food
- **Sequential dependencies**: Check BP → take BP med → log reading

### Example Synergistic Deck

**Morning Routine Cluster** (bundled in 10 minutes):
1. Wake up → bathroom
2. Weigh yourself (Weight Monitoring card)
3. Check BP (BP Monitoring card)
4. Take Lisinopril (Medication card)
5. Take Metformin with breakfast (Medication card)
6. Log all readings in app

**Evening Routine Cluster** (bundled in 15 minutes):
1. After dinner
2. Take second Metformin dose (Medication card)
3. Check BP (BP Monitoring card)
4. 5-minute deep breathing (Stress Management card)
5. Prepare tomorrow's medications in pill organizer

---

## FRICTION REDUCERS

### Built into HOW Section

Include practical tips to reduce barriers:

```markdown
**Friction Reducers**:
- "Set up pill organizer on Sundays" (reduces daily decision)
- "Keep BP cuff on nightstand (visible = remembered)"
- "Pre-portion snacks on meal prep day" (removes in-the-moment prep)
- "Lay out exercise clothes night before" (removes morning friction)
- "Set phone alarm/reminder for first week until habit forms"
- "Keep medication with toothbrush" (visual cue + existing habit)
```

### Environmental Design Principles

**Make Good Choices Easy**:
- Place health tools in visible, convenient locations
- Pre-decide and pre-prepare when possible
- Remove steps between decision and action

**Make Bad Choices Harder**:
- Keep unhealthy foods out of house (or out of sight)
- Add friction to undesired behaviors
- Create physical barriers to old habits

---

## REWARD STRUCTURE

### Design Principles

1. **Passive tracking when possible** (no manual entry burden)
2. **Simple one-tap logging** for actions requiring confirmation
3. **Visual feedback** (not intrusive notifications)
4. **Positive reinforcement only** (no punishment for missed days)
5. **Appropriate for diverse tech literacy levels**

### App Features for Adherence

#### Simple Daily Check-In
```
Patient opens app:
→ Sees today's active cards
→ One-tap ✓ to mark complete (3 seconds per card)
→ Streak counter visible (motivating without pressure)
→ Done for the day
```

#### Passive Tracking (When Technology Allows)
- **Medication adherence**: Smart pill bottle or pharmacy refill data auto-syncs
- **Exercise**: Phone's step counter or Apple Health/Google Fit integration
- **Weight**: Bluetooth scale auto-syncs
- **Blood pressure**: Bluetooth cuff auto-syncs
- **No manual entry required** for these metrics

#### Visual Progress (Non-Intrusive)

**Home Screen Display**:
```
╔════════════════════════════════════╗
║  Today's Progress                  ║
║  4/5 cards completed today ✓       ║
║                                    ║
║  🔥 7-day streak                   ║
╚════════════════════════════════════╝
```

**Weekly Calendar View**:
```
Week View:
M  T  W  T  F  S  S
🟢 🟢 🟢 🟢 🟢 ⚪ 🟢

🟢 = All cards done
🟡 = Partial completion
⚪ = Nothing logged (no shame colors)
```

**Trend Graphs**:
```
Blood Pressure Trend (30 days):
160 |     •
150 |   •   •
140 | •       • •
130 |           • • 
120 |_______________|→ Goal: <130
```

#### Milestone Celebrations (Not Push Notifications)

**When patient opens app after achieving milestone**:
- Brief animation + badge (no sound)
- Appears at top of screen
- Dismissible immediately

**Examples**:
- "7 Day Warrior! 🏆" (7-day streak)
- "30 Day Champion! 🎉" (30-day streak)
- "Target Achieved! 🎯" (met clinical goal)
- "100 Days Strong! 💪" (100-day streak)

**No push notifications that annoy**. Only celebrate when they voluntarily check in.

---

## LOW-TECH & INCLUSIVE OPTIONS

### For Elderly, Non-Tech-Savvy, or Busy Users

#### Option 1: Phone Call Logging
```
Automated daily call at preferred time:
"Press 1 if you took your medication today"
"Press 2 if you checked your blood pressure"
"Press 3 if you need help"
```

#### Option 2: Paper Tracking Sheet
```
Printable weekly tracker:

Week of: ___________

           M  T  W  T  F  S  S
Medication ☐ ☐ ☐ ☐ ☐ ☐ ☐
BP Check   ☐ ☐ ☐ ☐ ☐ ☐ ☐
Walk 30min ☐ ☐ ☐ ☐ ☐ ☐ ☐

BP Readings:
M: ___/___ T: ___/___ W: ___/___
```

#### Option 3: Caregiver/Family App Access
- Family member can log on behalf of patient
- Notifications go to caregiver
- Shared responsibility

#### Option 4: No App Penalty
- App is a **tool, not a requirement**
- Patients can still receive care without using app
- Paper-based system equally valid
- Clinician reviews logs at visit (paper or digital)

---

## PERSONALIZED TIMING RECOMMENDATIONS

### AI-Suggested Optimal Times

Based on patient data, AI suggests best times for each action:

**Morning Person vs Night Person**:
- Morning person → Exercise at 6am, meds at 7am
- Night person → Exercise at 6pm, meds at 10am

**Work Schedule**:
- 9-5 worker → Lunch walk at 12pm
- Night shift → Adjust all timings to sleep-wake cycle

**Existing Routines**:
- Always drinks coffee at 7am → Take morning meds with coffee
- Always watches TV at 8pm → Do stretching during commercials

**Weather & Context**:
- Rain forecast → Suggest indoor exercise alternative
- Hot day → Suggest early morning or evening walk

---

## SOCIAL SUPPORT & ACCOUNTABILITY

### Built-in Support Features

#### Accountability Partner
```
Optional feature:
- Designate family member or friend
- They receive notification if patient misses 2+ days
- Can send encouragement messages through app
- See progress (with patient permission)
```

#### Group Challenges
```
Optional community feature:
- Join "Walking Challenge" with other patients
- See anonymized leaderboard
- Share tips and encouragement
- No pressure, just motivation
```

#### Clinician Check-Ins
```
Automated prompts for care team:
- Low adherence alert → RN calls patient
- Repeated missed doses → PharmD counseling
- Target not met → MD reviews and adjusts plan
```

---

## MOTIVATIONAL INTERVIEWING INTEGRATION

### Embed MI Principles in Card Delivery

#### Express Empathy
```
Card introduction message:
"We know starting something new can feel overwhelming. 
This walking program is designed to start slow and 
build gradually. You've got this."
```

#### Develop Discrepancy
```
WHY THIS MATTERS TO YOU section:
Link action to patient's own stated goals:
"You said you want to play with your grandchildren 
without getting tired. Walking strengthens your heart 
so you'll have more energy for the moments that matter."
```

#### Roll with Resistance
```
When patient reports barriers:
"It sounds like finding 30 minutes is tough with your 
schedule. What if we started with just 10 minutes 
3 times a week? Would that feel more doable?"

→ AI suggests lower-tier version of card
```

#### Support Self-Efficacy
```
After small wins:
"You walked 3 times this week! That's exactly what 
we were aiming for. How did it feel?"

→ Build confidence before increasing difficulty
```

---

## GAMIFICATION (OPTIONAL, NOT REQUIRED)

### Light Gamification Elements

For patients who respond well to game-like features:

#### Points & Levels
```
Earn points for:
- Completing cards (10 points each)
- Maintaining streaks (bonus points)
- Reaching targets (50 bonus points)

Levels:
- Beginner (0-100 points)
- Intermediate (101-500 points)
- Advanced (501+ points)

No penalties for low points. Only positive progression.
```

#### Badges
```
Earn badges for:
- First week complete
- 30-day streak
- Target achieved
- Tried all cards in deck

Display on profile (if patient wants)
```

#### Challenges
```
Optional weekly challenges:
- "Walk 10,000 steps this week"
- "Cook 3 DASH meals this week"
- "Meditate 5 days this week"

Opt-in only. No pressure.
```

**Critical**: Gamification is **opt-in** and **never punitive**. Some patients love it, others find it stressful.

---

## RELAPSE PREVENTION & RECOVERY

### When Patients Fall Off Track

#### Normalize Setbacks
```
Message after 3 missed days:
"Life happens! You missed a few days, and that's okay. 
Ready to restart? Your care team is here to help."

[Button: "Yes, let's restart"]
[Button: "I need help with barriers"]
```

#### Identify Triggers
```
AI asks:
"What made it hard to keep going?"
☐ Too busy
☐ Felt overwhelmed
☐ Didn't see results
☐ Side effects
☐ Cost
☐ Other: _______

Based on response → Suggest modifications or alternatives
```

#### Tier Down (Not Quit)
```
Instead of giving up entirely:
"Let's scale back to something more manageable right now.
You were walking 30 minutes 5x/week. 
How about 10 minutes 3x/week for now?"

→ Lower tier of same card, not abandonment
```

#### Care Team Reaches Out
```
After 7 days no activity:
RN calls patient:
"We noticed you haven't been able to complete your 
walking card. What's going on? How can we help?"

→ Troubleshoot barriers
→ Adjust plan
→ Provide encouragement
```

---

## SUCCESS METRICS FOR BEHAVIORAL DESIGN

Track at system level:

1. **Adherence Rate**: % of days cards completed
2. **Streak Length**: Average longest streak per patient
3. **Time to First Lapse**: How long before first missed day
4. **Recovery Rate**: % who restart after lapse
5. **Target Achievement**: % who reach clinical goals
6. **Patient Satisfaction**: Self-reported satisfaction scores
7. **Retention**: % still active after 30/90/180 days

Use data to continuously improve behavioral design features.

---

## BEHAVIORAL NUDGES IN CARD DESIGN

### Micro-Interventions

#### Default Options
- Pre-select most evidence-based option
- "Start with Tier 1 (Beginner)" pre-checked

#### Social Proof
- "85% of patients like you succeeded with this card"
- "Most people find this easier than they expected"

#### Loss Aversion
- "You're 3 days away from losing your 10-day streak"
  - (Use sparingly, can backfire)

#### Implementation Intentions
- Force specification: "I will walk at [time] on [days]"
- Concrete plans increase follow-through

#### Fresh Start Effect
- "New month, fresh start! Ready to restart your streak?"
- Leverage natural motivation cycles

---

## CONCLUSION

Behavioral design is woven throughout the SMART Card system:
- **Habit stacking** in card synergy
- **Friction reduction** in instructions
- **Positive reinforcement** in app features
- **Personalized timing** via AI
- **Social support** built-in
- **Relapse recovery** normalized

The goal: Make doing the right thing for health **easier** than not doing it.