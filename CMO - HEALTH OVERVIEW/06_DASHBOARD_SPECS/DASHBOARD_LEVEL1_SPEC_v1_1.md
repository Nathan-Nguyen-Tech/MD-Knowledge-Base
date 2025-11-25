# DASHBOARD LEVEL 1 SPECIFICATION
## Patient Health Dashboard - Hero View

**Document Type:** User Interface Specification  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture and progressive disclosure model
- `COMPOSITE_SCORING_v2.md` - Overall health score calculation
- `BIOLOGICAL_AGE_SPEC_v1_1.md` - Biological age calculation
- `TRANSPARENCY_DISPLAY_v1_1.md` - Attribution and top contributors logic
- `CRITICAL_ALERTS_v1_1.md` - Alert prioritization and display

**This document connects to:**
- `DASHBOARD_LEVEL2_SPEC.md` - System overview (next level down)
- `DASHBOARD_LEVEL3_SPEC.md` - Detailed analysis (deepest level)
- `ALERT_MESSAGES.md` - Patient-facing alert text
- `PLAIN_LANGUAGE_LIBRARY.md` - All UI text content

---

## DOCUMENT PURPOSE

This specification defines **Level 1: Hero View** - the default landing page of the Patient Health Dashboard that every user sees when they first access the dashboard.

**Design Philosophy:**
- Maximum clarity, minimum cognitive load
- Critical information immediately visible
- No scrolling required on standard screens
- Suitable for quick check-ins (5-15 seconds)
- Works for all users (patients, clinicians, caregivers)

**User Goals:**
- Understand overall health status at a glance
- Identify critical issues requiring immediate attention
- Know top priorities for improvement
- Access deeper information when desired

---

## SECTION 1: OVERALL LAYOUT

### 1.1 Screen Structure

**Single-screen layout (no scrolling required):**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  HEADER: Logo | Patient Name | Last Updated | Settings  â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                           â”‚
â”‚  [CRITICAL ALERTS BANNER] (if any)                       â”‚
â”‚                                                           â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                           â”‚
â”‚              OVERALL HEALTH SCORE                        â”‚
â”‚                    [Big Number]                          â”‚
â”‚                [Visual Progress Ring]                    â”‚
â”‚                  [Status Message]                        â”‚
â”‚                                                           â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                           â”‚
â”‚              BIOLOGICAL AGE                              â”‚
â”‚           [Number with comparison]                       â”‚
â”‚                                                           â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                           â”‚
â”‚  What's Working Well  â”‚  What Needs Work                â”‚
â”‚  â€¢ Item 1              â”‚  â€¢ Item 1                       â”‚
â”‚  â€¢ Item 2              â”‚  â€¢ Item 2                       â”‚
â”‚  â€¢ Item 3              â”‚  â€¢ Item 3                       â”‚
â”‚                                                           â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                           â”‚
â”‚     [View System Details Button]                         â”‚
â”‚                                                           â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 1.2 Screen Regions

**Five Primary Regions (top to bottom):**

1. **Header Bar** (always visible)
   - Height: 60-80px
   - Background: White or light neutral
   - Contains: Logo, patient name, timestamp, settings icon

2. **Critical Alerts Banner** (conditional - only if alerts present)
   - Height: Variable (stacks multiple alerts)
   - Background: Red (#DC2626) for critical, Orange (#F59E0B) for urgent
   - Contains: Alert icon, message, action button

3. **Overall Health Score Section** (hero element)
   - Height: 40% of viewport
   - Contains: Large score display, progress ring, status message

4. **Biological Age Section**
   - Height: 15% of viewport
   - Contains: Biological age number, chronological age comparison

5. **Top Contributors Section**
   - Height: 30% of viewport
   - Contains: Two-column layout showing top positive and negative factors

6. **Navigation Footer**
   - Height: 10% of viewport
   - Contains: Primary action button to expand to Level 2

### 1.3 Responsive Behavior

**Desktop (â‰¥1024px):**
- Two-column layout for "What's Working" / "What Needs Work"
- Wider progress ring (400px diameter)
- Larger font sizes

**Tablet (768px - 1023px):**
- Single column for top contributors (stacked)
- Medium progress ring (300px diameter)
- Adjusted font sizes

**Mobile (â‰¤767px):**
- Single column layout throughout
- Smaller progress ring (240px diameter)
- Condensed spacing
- May require minimal scrolling on small devices

---

## SECTION 2: HEADER BAR

### 2.1 Components (Left to Right)

**Left Side:**
- **Logo/Clinic Name** (clickable â†’ home)
  - Size: 40px height
  - Format: Image or text logo

**Center:**
- **Patient Name** (prominent)
  - Format: "FirstName LastName"
  - Font: Bold, 18-20px
  - For clinician view: Include patient ID/MRN

**Right Side:**
- **Last Updated Timestamp**
  - Format: "Updated: Nov 12, 2025 at 2:34 PM"
  - Font: Regular, 14px, gray
  - Tooltip on hover: "Data freshness: All values current as of this time"
  - **Staleness warning:** If data >180 days old, display orange badge: "âš  Data may be out of date"
  - Aligns with TEMPORAL_SCORING temporal reliability principles

- **Settings Icon** (gear icon)
  - Click: Opens settings menu
  - Options: Print, Export PDF, Preferences, Help

### 2.2 Visual Design

**Colors:**
- Background: White (#FFFFFF) or Light Gray (#F9FAFB)
- Text: Dark Gray (#1F2937)
- Border Bottom: Light Gray (#E5E7EB), 1px

**Accessibility:**
- High contrast text (WCAG AAA)
- Keyboard navigable
- Screen reader labels

---

## SECTION 3: CRITICAL ALERTS BANNER

### 3.1 Display Logic (CRITICAL DESIGN RULE)

**LEVEL 1 BANNER = CRITICAL & URGENT ONLY:**
- âœ… Critical alerts (Red zone, life-threatening parameters)
- âœ… Urgent alerts (Orange zone, same-day/next-day action required)
- âŒ Yellow "Warning" alerts DO NOT appear in Level 1 banner

**Why exclude yellow warnings from Level 1?**
- Prevents alarm fatigue and banner overload
- Keeps Level 1 focused on true emergencies
- Yellow warnings appear in Level 2 "Issues to Address" section
- Maintains "Critical Safety First" without chronic anxiety

**Banner appears ABOVE overall health score**
- Cannot be dismissed (only acknowledged)
- Remains visible until alert condition resolved
- Multiple alerts stack vertically

**If â‰¥5 critical/urgent alerts:**
- Show top 2 most severe
- Add summary: "+ 3 more urgent issues requiring attention"
- **HIDE "What's Working Well" section** to keep focus on safety
- Prominent "Review All Alerts" button â†’ Level 2

### 3.2 Alert Severity Levels (Level 1 Banner)

**CRITICAL (Red) - Life-Threatening**
- Background: Red (#DC2626)
- Icon: âš ï¸ Warning triangle
- Text: White
- Action: Emergency care NOW
- Example: "CRITICAL: Troponin elevated - Seek emergency care immediately"

**URGENT (Orange) - Requires Prompt Action**
- Background: Orange (#F59E0B)
- Icon: âš¡ Lightning bolt
- Text: White
- Action: Contact clinician today
- Example: "URGENT: Blood pressure severely elevated - Contact clinician today"

**Yellow "WARNING" Alerts:**
- DO NOT display in Level 1 banner
- Appear in Level 2 as "Issues to Discuss"
- Or shown as small badge near overall score: "âš  3 items need attention"
- Click badge â†’ jumps to Level 2 filtered to warnings

### 3.3 Alert Banner Structure

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  [Icon]  Alert Message in Plain Language           â”‚
â”‚          Recommended Action                         â”‚
â”‚                               [Action Button]       â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Components:**
1. **Alert Icon** (left aligned)
   - Size: 32px Ã— 32px
   - Color: White

2. **Alert Message** (2-line maximum)
   - Line 1: Parameter name + severity in plain language
   - Line 2: Immediate recommended action
   - Font: Bold 16-18px

3. **Action Button** (right aligned)
   - Text: "View Details" or "Call Clinic" or "Emergency"
   - Style: White background, dark text for critical
   - Click: Opens Level 3 detail for that parameter OR triggers phone call

### 3.4 Multiple Alerts Handling

**If 1 alert:** Display full banner (as described)

**If 2 alerts:** Stack vertically

**If 3+ alerts:** 
- Display top 2 most critical
- Add summary line: "+ 3 more alerts requiring attention"
- Click summary â†’ expands to show all OR jumps to Level 2 alerts section

### 3.5 Example Alert Text

**From CRITICAL_ALERTS_v1_1.md:**

```
Critical: "CRITICAL: Troponin I 2.8 ng/mL - Possible heart attack. 
          Call 911 or go to emergency room NOW."

Urgent:   "URGENT: Blood glucose 312 mg/dL - Dangerously high. 
          Contact your clinician today."

Warning:  "WARNING: Potassium 5.6 mEq/L - Above normal range. 
          Discuss with clinician at next appointment."
```

---

## SECTION 4: OVERALL HEALTH SCORE DISPLAY

### 4.1 Primary Score Display

**The Big Number:**

**Visual Design:**
```
        Your Overall Health Score
        
                 78
        [Progress Ring Visualization]
        
            Good Health
```

**Score Number:**
- Size: 72-96px font
- Weight: Extra bold
- Color: Dynamic based on score zone:
  - Green (#059669) for 75-100
  - Yellow (#D97706) for 60-74
  - Orange (#EA580C) for 40-59
  - Red (#DC2626) for 0-39

**"Your Overall Health Score" Label:**
- Size: 16-18px
- Weight: Medium
- Color: Gray (#6B7280)
- Position: Above the number

**Status Message:**
- Size: 20-24px
- Weight: Semi-bold
- Color: Same as score color
- Position: Below the progress ring
- Text: Status phrase based on score (see Section 4.4)

**Trend Indicator (NEW):**
- Size: 16px
- Position: Below status message
- Format: "Trend: [Stable/Improving/Worsening]" with icon
- Icons:
  - â†‘ Green: "Improving" (score increased â‰¥3 points from last assessment)
  - â†’ Gray: "Stable" (score within Â±2 points)
  - â†“ Orange: "Worsening" (score decreased â‰¥3 points)
- Derived from TEMPORAL_SCORING.md Display_Score trend logic
- Comparison: vs most recent previous assessment (typically 3 months)

**Purpose of trend indicator:**
- Surfaces temporal context at Level 1
- Reassures patients that single aberrant readings don't dominate
- Aligns with TEMPORAL_SCORING philosophy: "trends matter, not just point values"

### 4.2 Progress Ring Visualization

**Circular Progress Indicator:**

**Visual Specifications:**
- **Diameter:** 300-400px (desktop), scales for mobile
- **Ring thickness:** 24-32px
- **Background ring:** Light gray (#E5E7EB)
- **Filled portion:** Dynamic color matching score zone
- **Animation:** Fills clockwise from top (12 o'clock position)
- **Duration:** 1.5 seconds smooth animation on page load

**Score Zones Marked on Ring:**
- Four colored segments:
  - 0-39: Red section (bottom quarter)
  - 40-59: Orange section (left quarter)
  - 60-74: Yellow section (right quarter)
  - 75-100: Green section (top quarter)

**Visual indicator of current score:**
- Filled portion stops at score value
- Small circle marker at end of filled portion
- Score number displayed in center of ring

**Completeness Badge (NEW):**
- Position: Bottom of progress ring
- Format: "Data: 94% complete" or "47/50 parameters"
- Size: 12-14px, gray text
- Icon: Small info icon (i)
- Click: Shows breakdown of NS/NA parameters

**Tri-State Handling:**
- **NS (Not Scored)**: Parameters with insufficient data â†’ reduce denominator
- **NA (Not Applicable)**: Parameters not needed for patient â†’ excluded from count
- **Numeric**: Normal scored parameters
- Example: "47 numeric + 2 NS + 1 NA = 47/49 effective parameters = 96% complete"
- Completeness % = Numeric / (Numeric + NS), excluding NA entirely

### 4.3 Understanding the Score Scale

**CRITICAL CLARIFICATION:**

Our scoring system uses an **85-at-target baseline** throughout:
- Individual parameters normalized so z-score = 0 (personalized target) â†’ 85 points
- This means **most well-controlled patients score around 85**, NOT 100
- Composite scores inherit this: 85 = "at target for your profile"
- Scores 86-100 = sustained excellence beyond target (rare, exceptional)

**Why not 100 = target?**
- Prevents overconfidence at target
- Rewards sustained excellence (B+ grade at target, A/A+ for exceptional)
- Still leaves room for improvement motivation

**Overall Health Score is a weighted blend:**
- 70% Objective Health (8 organ systems)
- 30% Subjective Health (5 lifestyle pillars)

**Color zones remain intuitive:**
- Green (75-100) = Optimal to excellent
- Yellow (60-74) = Fair, room for improvement  
- Orange (40-59) = Attention needed
- Red (0-39) = Urgent intervention required

### 4.4 Status Message Mapping

**Green Zone (75-100):**
- 90-100: "Excellent Health" or "Exceptional Performance"
- 85-89: "Very Good Health" or "At Target"
- 80-84: "Good Health" or "Above Average"
- 75-79: "Good Health" or "Healthy Range"

**Yellow Zone (60-74):**
- 70-74: "Fair Health" or "Room for Improvement"
- 65-69: "Fair Health" or "Needs Monitoring"
- 60-64: "Fair Health" or "Action Recommended"

**Orange Zone (40-59):**
- 50-59: "Attention Needed" or "Multiple Concerns"
- 40-49: "Serious Concerns" or "Urgent Action Needed"

**Red Zone (0-39):**
- 25-39: "Critical Health Issues" or "Immediate Attention Required"
- 0-24: "Severe Health Issues" or "Emergency Intervention Needed"

**Plain Language Emphasis:**
- Avoid medical jargon
- Action-oriented when appropriate
- Encouraging tone even in lower zones
- Never alarmist or judgmental

### 4.5 Interactive Behavior

**Hover over score number:**
- Tooltip appears
- Shows: 
  - Date of calculation
  - Completeness percentage  
  - **Temporal context**: "Includes both your latest results and recent trends. Sudden spikes are softened if your usual pattern is healthier."
- Example: "Based on 47 of 50 recommended parameters (94% complete). Calculated Nov 12, 2025. Score reflects stability over time, not just today's values."

**Click on progress ring:**
- Opens modal overlay
- Shows: Score breakdown into Objective (70%) and Subjective (30%)
- Displays: Mini bar chart showing system and pillar contributions
- Includes: "View Full System Details" button â†’ jumps to Level 2

### 4.6 Accessibility Features

**For Screen Readers:**
- "Overall health score: 78 out of 100. Status: Good health. In the green zone."
- Describe progress ring: "Visual progress indicator showing 78 percent filled"

**Keyboard Navigation:**
- Tab key cycles through interactive elements
- Enter/Space activates click behavior

**Color Blind Support:**
- Icons/patterns supplement color coding
- Text labels always present alongside colors
- High contrast mode available

---

## SECTION 5: BIOLOGICAL AGE DISPLAY

### 5.1 Layout

**Horizontal display under overall score:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚                                                       â”‚
â”‚         Your Biological Age: 52 years                â”‚
â”‚                                                       â”‚
â”‚      (Chronological Age: 48 years)                  â”‚
â”‚                                                       â”‚
â”‚     You're aging 4 years faster than calendar       â”‚
â”‚                                                       â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 5.2 Biological Age Number

**Primary Display:**
- Size: 48-60px font
- Weight: Bold
- Color: Dynamic based on comparison to chronological age:
  - **Green (#059669):** Bio age < Chrono age (aging slower)
  - **Yellow (#D97706):** Bio age within Â±2 years of Chrono age (normal)
  - **Orange (#EA580C):** Bio age 3-7 years > Chrono age (accelerated aging)
  - **Red (#DC2626):** Bio age >7 years > Chrono age (severe accelerated aging)

**Label:** "Your Biological Age:"
- Size: 16px
- Color: Gray

### 5.3 Chronological Age Reference

**Secondary Display:**
- Size: 18-20px font
- Weight: Regular
- Color: Gray (#6B7280)
- Format: "(Chronological Age: [X] years)"
- Position: Directly below biological age number

### 5.4 Interpretation Message

**Dynamic Text Based on Comparison:**

**If Bio Age < Chrono Age (Positive):**
- "You're aging [X] years slower than your calendar age" (Green)
- "Your body is [X] years younger than your birthdate suggests" (Green)

**If Bio Age â‰ˆ Chrono Age (Â±2 years) (Neutral):**
- "Your biological age matches your calendar age" (Yellow)
- "You're aging at a normal rate" (Yellow)

**If Bio Age > Chrono Age (Negative - with changeability emphasis):**
- Ages 3-7 faster: "You're aging [X] years faster than your calendar age. **The good news: this can often be improved with focused changes.**" (Orange)
- Ages 8+ faster: "Your body shows signs of accelerated aging. **This is a strong signal to intervene now, not a permanent label. Many of these factors are modifiable.**" (Red)

**Key principle:** 
- Always pair urgency with **hope and agency**
- Biological age is a **warning signal**, not a fixed destiny
- Frame as **opportunity for intervention**, especially when paired with red alerts

**Font Size:** 14-16px  
**Position:** Below chronological age reference  
**Icon:** Optional â†‘ or â†“ arrow to indicate direction

### 5.5 Interactive Behavior

**Hover over biological age number:**
- Tooltip appears
- Shows: Calculation method summary
- Example: "Based on PhenoAge algorithm plus system and lifestyle adjustments. Click for details."

**Click on biological age:**
- Opens modal overlay
- Shows: Detailed breakdown from BIOLOGICAL_AGE_SPEC_v1_1.md
  - PhenoAge contribution
  - System score adjustments
  - Lifestyle score adjustments
  - Total deviation from chronological age
- Includes: "What Can I Do?" section with top improvement opportunities

### 5.6 Special Cases

**If calculation not possible (insufficient data):**
- Display: "Biological Age: Not Yet Calculated"
- Message: "Complete [X] additional biomarkers to calculate biological age"
- Button: "See Required Tests"

**If patient is very young (<30 years):**
- Note: "Biological age is most meaningful for adults 30+ years old"
- Still display calculation if possible

**If patient is very old (>85 years):**
- Note: "Biological age estimates are less precise over age 85"
- Display calculation with caveat

---

## SECTION 6: TOP CONTRIBUTORS & PRIORITY ACTIONS

### 6.1 Two-Column Layout

**Left Column: "What's Working Well" (Positive Contributors)**
**Right Column: "Priority Actions / What Needs Work" (Negative Contributors)**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  What's Working Well âœ“   â”‚  Priority Actions âš       â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚  â€¢ Respiratory System    â”‚  â€¢ Blood Pressure        â”‚
â”‚    Excellent lung        â”‚    Stage 2 HTN           â”‚
â”‚    function             â”‚    â†’ Review with clinicianâ”‚
â”‚    +2.1 points          â”‚    -3.4 points           â”‚
â”‚                          â”‚                          â”‚
â”‚  â€¢ Exercise Habits       â”‚  â€¢ Blood Glucose         â”‚
â”‚    Very active           â”‚    Pre-diabetic range    â”‚
â”‚    +1.8 points          â”‚    â†’ Test HbA1c, adjust dietâ”‚
â”‚                          â”‚    -2.8 points           â”‚
â”‚                          â”‚                          â”‚
â”‚  â€¢ Immune Function       â”‚  â€¢ Sleep Quality         â”‚
â”‚    Strong immunity       â”‚    Poor sleep patterns   â”‚
â”‚    +1.5 points          â”‚    â†’ Improve sleep routineâ”‚
â”‚                          â”‚    -1.2 points           â”‚
â”‚                          â”‚                          â”‚
â”‚  Tap any item for detailsâ”‚  Tap any item for action â”‚
â”‚                          â”‚  steps                   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Key Change from Previous Version:**
- Right column renamed to "Priority Actions / What Needs Work"
- Each item includes brief **action hint** (â†’ symbol + 2-5 words)
- Footer text explicitly mentions "action steps" available on tap
- Aligns with PROJECT_SPECIFICATION promise of "Top 3-5 Priority Actions"

### 6.2 Selection Algorithm

**From TRANSPARENCY_DISPLAY_v1_1.md Section 2:**

**Step 1: Calculate Deviations**
```
For each system/pillar:
  Deviation = (Score - 85) Ã— Weight
```

**Step 2: Sort by Absolute Deviation**
- Positive deviations â†’ "What's Working Well"
- Negative deviations â†’ "Priority Actions / What Needs Work"

**Step 3: Select Top 3 Per Column**
- Display 3 largest positive deviations (left column)
- Display 3 largest negative deviations (right column)

**System vs Parameter Hierarchy (NEW):**
- **Prefer system-level entries** over individual parameters at Level 1
- If both "Cardiovascular System" (score 58) and "Blood Pressure" (score 38) qualify:
  - Show "Cardiovascular System" at Level 1
  - Defer "Blood Pressure" specifics to Level 2/3
  - Exception: If parameter is in CRITICAL alert, show parameter explicitly
- Prevents duplication and maintains Level 1 simplicity
- Full parameter breakdown available in Level 2/3

**Tie-Breaking:**
1. Larger absolute deviation wins
2. If still tied, higher criticality weight wins
3. If still tied, prefer system over pillar (objective over subjective)
4. If still tied, alphabetical by name

### 6.3 Display Format for Each Item

**For "What's Working Well" (Left Column):**

**Line 1: System/Pillar Name**
- Font: Bold, 16-18px
- Color: Dark gray (#1F2937)
- Icon: Optional indicator (heart for cardiovascular, lungs for respiratory, etc.)

**Line 2: Plain Language Description**
- Font: Regular, 14-16px
- Color: Medium gray (#6B7280)
- Text: One-line clinical interpretation
  - Good: "Excellent lung function"
  - Fair: "Borderline kidney function"

**Line 3: Point Contribution**
- Font: Semi-bold, 14px
- Color: Green (#059669) with +
- Format: "+2.1 points"

---

**For "Priority Actions / What Needs Work" (Right Column):**

**Line 1: System/Pillar Name**
- Font: Bold, 16-18px
- Color: Dark gray (#1F2937)
- Icon: Alert indicator matching severity

**Line 2: Plain Language Description**
- Font: Regular, 14-16px
- Color: Medium gray (#6B7280)
- Text: One-line clinical interpretation
  - Example: "Stage 2 Hypertension"
  - Example: "Poor sleep patterns"

**Line 3: Micro-Action Hint (NEW)**
- Font: Regular, 13-14px
- Color: Blue (#2563EB) - clickable appearance
- Format: "â†’ [Action verb phrase]"
- Examples:
  - "â†’ Review with clinician"
  - "â†’ Test HbA1c, adjust diet"
  - "â†’ Improve sleep routine"
  - "â†’ Address with provider"
  - "â†’ Complete assessment"
- **Limited to 2-5 words** to maintain Level 1 simplicity

**Line 4: Point Contribution**
- Font: Semi-bold, 14px
- Color: Orange/Red (#EA580C or #DC2626) with -
- Format: "-3.4 points"

**Action Hint Guidelines:**
- Use active verbs (Review, Test, Improve, Address, Complete)
- Be specific but brief
- Link to detailed action plan in Level 2/3
- Never overwhelming or prescriptive at Level 1

### 6.4 Plain Language Mapping

**For each system/pillar, choose description based on score:**

**Cardiovascular System:**
- 90-100: "Excellent heart health"
- 75-89: "Good cardiovascular function"
- 60-74: "Borderline blood pressure concerns"
- 40-59: "High blood pressure detected"
- 0-39: "Severe cardiovascular issues"

**Metabolic System:**
- 90-100: "Optimal metabolism"
- 75-89: "Healthy blood sugar control"
- 60-74: "Pre-diabetic indicators"
- 40-59: "Diabetes management needed"
- 0-39: "Critical metabolic dysfunction"

**Exercise Pillar:**
- 90-100: "Very active lifestyle"
- 75-89: "Regular exercise habits"
- 60-74: "Moderate activity level"
- 40-59: "Insufficient physical activity"
- 0-39: "Sedentary lifestyle"

**(Full mapping in PLAIN_LANGUAGE_LIBRARY.md)**

### 6.5 Interactive Behavior

**Hover over any item:**
- Highlight background (light gray)
- Cursor changes to pointer
- Tooltip: "Click to see full details"

**Click on any item:**
- If system: Jump to Level 2, scroll to that system
- If parameter: Jump to Level 3, open that parameter detail
- If pillar: Open lifestyle assessment detail modal

### 6.6 Mobile Optimization

**On mobile (<768px):**
- Single column layout
- "What's Working Well" section first (fold if needed)
- "What Needs Work" section second
- Show top 2 items per category instead of 3 (to reduce scrolling)
- Collapsible sections with headers

---

## SECTION 7: NAVIGATION FOOTER

### 7.1 Primary Action Button

**"View System Details" Button:**

**Visual Design:**
- Width: 60% of screen width (max 400px)
- Height: 56px
- Background: Primary brand color (e.g., Blue #2563EB)
- Text: White, 18px, bold
- Text: "View System Details" or "See All Health Systems"
- Icon: Chevron down â–¼ or expand icon
- Border radius: 8px
- Drop shadow: Subtle elevation

**Position:**
- Centered horizontally
- Bottom of screen (above footer padding)
- Fixed 24px margin from bottom

**Interaction:**
- Hover: Background darkens 10%
- Click: Smooth scroll/transition to Level 2
- Animation: Expand down transition (0.3s ease)

### 7.2 Secondary Actions

**Small text links below button:**

- "Print Summary" (opens print dialog)
- "Share with Provider" (opens share modal)
- "Export PDF" (generates PDF report)

**Style:**
- Font: 14px, regular
- Color: Gray (#6B7280)
- Underline on hover
- Spaced evenly

---

## SECTION 8: EDGE CASES & SPECIAL STATES

### 8.1 Insufficient Data State

**When <30% of parameters are measured (high NS proportion):**

**Overall Score Display:**
- Show: Score with asterisk "78*"
- Add message: "Preliminary score based on limited data"
- Color: Score displayed but ring partially grayed out
- Display completeness: "Based on 15 of 50 parameters (30%)"
- **Tri-state breakdown**: "12 numeric, 3 NS, 35 not yet measured"

**Completeness badge shows:**
- "Data: 30% complete (preliminary)"
- Orange/yellow color to signal caution
- Click: Expands to show which systems have gaps

**Top Contributors:**
- May show fewer than 3 items per column
- Add note: "Complete assessment for personalized insights"
- Button: "See Recommended Tests"

**Scoring approach for low completeness:**
- Per COMPOSITE_SCORING_v2.md completeness governance
- High NS count triggers conservative estimation
- Score reliability explicitly communicated
- User encouraged to complete missing assessments

**NA (Not Applicable) parameters:**
- Excluded from completeness calculation entirely
- Example: Pregnancy tests for male patient don't count against completeness
- Denominator = Total relevant parameters - NA parameters

### 8.2 First-Time User (No Data)

**Welcome Screen Variation:**

Replace score section with:
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚                                           â”‚
â”‚      Welcome to Your Health Dashboard    â”‚
â”‚                                           â”‚
â”‚      Get started by completing your      â”‚
â”‚         initial health assessment        â”‚
â”‚                                           â”‚
â”‚     [Start Assessment Button]            â”‚
â”‚                                           â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Show:**
- What assessments are recommended
- Estimated time to complete
- Benefits of completing full assessment

### 8.3 Data Refresh State

**While scores are recalculating:**

**Overlay on score section:**
- Semi-transparent background
- Spinner animation
- Text: "Updating your scores..."
- Previous scores visible but dimmed

**Duration:** Typically <2 seconds

### 8.4 Multiple Critical Alerts

**If 5+ critical/urgent alerts:**

**Modified layout:**
- Alerts section expands to 50% of screen
- Overall score section compressed
- **"What's Working Well" section HIDDEN** (safety-first principle)
- **"Priority Actions" section remains visible** (still shows top issues)
- Prominent message: "Multiple urgent health issues detected - review immediately"

**Rationale:**
- Critical safety first: focus on problems, not positives
- Don't sugarcoat with "what's working" when 5+ urgent issues present
- Patient/clinician attention must go to action items
- Positives return to display once critical alerts resolve below 5

**Explicit state transitions:**
- 0-2 critical/urgent alerts: Normal layout (both columns visible)
- 3-4 critical/urgent alerts: Alerts expanded, both columns visible
- 5+ critical/urgent alerts: **Hide left column**, keep right column, alerts dominate screen

**Visual treatment:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  ðŸ”´ MULTIPLE URGENT HEALTH ISSUES               â”‚
â”‚  5 Critical/Urgent Parameters Detected          â”‚
â”‚  [Shows top 2-3 most critical]                  â”‚
â”‚  [+ 3 more requiring immediate attention]       â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜

Overall Score: 38 (displayed but de-emphasized)

Priority Actions (What Needs Work):
â€¢ Item 1
â€¢ Item 2  
â€¢ Item 3

[Review All Urgent Issues] [Contact Clinician]
```

### 8.5 Score Boundary Cases

**Exactly 75 (boundary between yellow and green):**
- Display in green (optimistic rounding)
- Status: "Good Health"

**Score of 50 (neutral):**
- Display in orange
- Status: "Fair Health"
- Note: "This typically indicates incomplete assessment data"

**Score of 100 (perfect):**
- Display in green with special indicator
- Status: "Exceptional Health!"
- Add celebration micro-animation (optional)

---

## SECTION 9: IMPLEMENTATION NOTES

### 9.1 Data Refresh Logic

**Automatic refresh triggers:**
- New lab results uploaded
- Flowsheet data updated
- Lifestyle assessment completed
- Manual refresh by user

**Refresh indicator:**
- Small circular arrow icon next to timestamp
- Spins during refresh
- Click: Force refresh (check for new data)

### 9.2 Performance Requirements

**Page load time:**
- Initial render: <1 second
- Score calculation: <2 seconds
- Full page interactive: <3 seconds

**Optimization strategies:**
- Cache calculated scores
- Load critical alerts first
- Lazy load biographical age modal
- Defer non-critical animations

### 9.3 Print Layout

**When user clicks "Print":**

**Simplified layout:**
- Remove interactive elements
- Single column layout
- Black and white color scheme (with grayscale zones)
- Include all text content
- Add footer: Patient name, date generated, page numbers

### 9.4 Accessibility Compliance

**WCAG 2.1 Level AA:**
- Color contrast â‰¥4.5:1 for text
- Color contrast â‰¥3:1 for graphics
- Keyboard navigation throughout
- Screen reader compatible
- Focus indicators visible
- Skip navigation link
- Semantic HTML structure
- ARIA labels where needed

### 9.5 Internationalization

**Text externalization:**
- All user-facing text in language files
- Support for right-to-left languages
- Date/time formatting per locale
- Number formatting per locale

**Initially supported:**
- English (US)
- Spanish (ES)

---

## SECTION 10: CLINICAL VALIDATION CHECKLIST

### 10.1 Before Launch

**Clinical Review:**
- â˜ Alert thresholds match CRITICAL_ALERTS_v1_1.md
- â˜ Status messages appropriate for patient audience
- â˜ Plain language accurate and non-alarmist
- â˜ Top contributors reflect actual score drivers
- â˜ Biological age interpretation clinically sound

**Usability Review:**
- â˜ Patients can understand their score in <30 seconds
- â˜ Critical alerts impossible to miss
- â˜ Navigation to Level 2 is intuitive
- â˜ No overwhelming information density
- â˜ Consistent with design system

**Technical Review:**
- â˜ Scores calculate correctly per COMPOSITE_SCORING_v2.md
- â˜ Biological age calculates per BIOLOGICAL_AGE_SPEC_v1_1.md
- â˜ Top contributors algorithm matches TRANSPARENCY_DISPLAY_v1_1.md
- â˜ Data refresh reliable and fast
- â˜ Edge cases handled gracefully

---

## SECTION 11: EXAMPLE SCENARIOS

### 11.1 Healthy Patient (Score 88)

**Display:**
- Overall Score: **88** (green)
- Progress Ring: 88% filled, green
- Status: "Very Good Health"
- Bio Age: 42 (Chrono: 45) - "You're aging 3 years slower"
- No critical alerts
- Top Working: Respiratory +2.8, Immune +2.1, Exercise +1.9
- Top Needs Work: Sleep -1.2, Stress -0.8, Nutrition -0.5

**User Experience:**
- Positive, encouraging
- Focus on maintaining strengths
- Minor improvements suggested gently

### 11.2 Patient with Concerns (Score 64)

**Display:**
- Overall Score: **64** (yellow)
- Progress Ring: 64% filled, yellow
- Status: "Fair Health - Action Recommended"
- Bio Age: 58 (Chrono: 52) - "You're aging 6 years faster"
- 1 Urgent Alert: Blood pressure 158/96
- Top Working: Immune +1.5, Neuro +1.2, Sleep +0.8
- Top Needs Work: Cardio -4.2, Metabolic -3.1, Exercise -2.4

**User Experience:**
- Clear but not alarming
- Specific systems identified for focus
- Urgent alert prominent but actionable

### 11.3 Critical Patient (Score 38)

**Display:**
- Overall Score: **38** (red)
- Progress Ring: 38% filled, red
- Status: "Critical Health Issues - Immediate Attention Required"
- Bio Age: 71 (Chrono: 58) - "You're aging 13 years faster"
- 3 Critical Alerts stacked:
  - Troponin elevated
  - Glucose 289 mg/dL
  - eGFR 22 mL/min
- Top Working: Only 1 item - Immune +0.8
- Top Needs Work: Renal -6.8, Metabolic -6.2, Cardio -5.9

**User Experience:**
- Urgent but not panicking
- Clear action steps in alerts
- Multiple pathways to care (call clinic, emergency)
- Level 2 button still accessible for full picture

### 11.4 New Patient (No Data)

**Display:**
- Welcome message replaces score
- "Get started by completing your initial health assessment"
- No alerts
- No top contributors
- Button: "Start Assessment" (instead of View System Details)

**User Experience:**
- Inviting and clear
- Sets expectations for what's coming
- Guides to first action

---

## SECTION 12: SUMMARY

### 12.1 Key Features

**Level 1 Hero View provides:**
1. âœ… Overall health score at a glance (0-100)
2. âœ… Biological age comparison to chronological age
3. âœ… Critical alerts that cannot be missed
4. âœ… Top 3 positive and negative health contributors
5. âœ… Clear navigation to deeper analysis (Level 2)
6. âœ… No scrolling required for essential information
7. âœ… Works for all users (patients, clinicians, family)

### 12.2 Success Criteria

**A successful Level 1 Hero View means:**
- New users understand their overall health status in <60 seconds
- Critical alerts result in appropriate action >95% of time
- Users can identify top priorities without confusion
- >80% of casual check-ins (quick health status views) don't require Level 2
- Clinical accuracy maintained throughout simplification
- Design scales from mobile to desktop seamlessly

### 12.3 Next Steps

**After Level 1 approval:**
- Proceed to DASHBOARD_LEVEL2_SPEC.md (System Overview)
- Design transition animations between levels
- Create PLAIN_LANGUAGE_LIBRARY.md for all UI text
- Develop ALERT_MESSAGES.md for all alert scenarios
- Build prototype for user testing

---

**END OF DASHBOARD LEVEL 1 SPECIFICATION**

*This document defines the primary landing page and most critical user interface of the Patient Health Dashboard. All specifications align with clinical logic defined in core framework documents.*
