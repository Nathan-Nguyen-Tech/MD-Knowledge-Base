# DASHBOARD LEVEL 3 SPECIFICATION
## Patient Health Dashboard - Detail View

**Document Type:** User Interface Specification  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture
- `PARAMETER_NORMALIZATION_v2.md` - Individual parameter scoring
- `SYSTEM_DOMAIN_SCORING_v2.md` - Domain and system calculations
- `TRANSPARENCY_DISPLAY_v1_1.md` - Top contributors and attribution
- `DASHBOARD_LEVEL2_SPEC.md` - System overview (previous level)

**This document connects to:**
- `CRITICAL_ALERTS_v1_1.md` - Parameter-level alerts
- `CLINICAL_DECISION_RULES_v1_0.md` - Complex parameter interpretation
- `TEMPORAL_SCORING.md` - Time-series display requirements
- `CONTEXTUAL_HELP_CONTENT.md` - Educational popups
- All `PARAMETERS_*.md` files (when complete)

---

## GLOBAL ASSUMPTIONS (CRITICAL ALIGNMENT)

### Scoring Baseline & Color Zones

**85-at-Target Framework:**
- Individual parameters normalized so z-score = 0 (personalized target) â†’ **85 points**
- System and overall scores inherit this baseline
- **NOT a conservative 50-point baseline** (older project language being updated)

**Why 85 = target?**
- Prevents overconfidence at guideline targets
- Rewards sustained excellence (86-100 = exceptional)
- B+ at target, A/A+ for excellence

**Universal Color Zones (Applied to ALL Score Fields):**

| Zone | Range | Status | Meaning |
|------|-------|--------|---------|
| **Green** | 75-100 | Optimal | Excellent to optimal health |
| **Yellow** | 60-74 | Monitor | Good with room to improve |
| **Orange** | 40-59 | Act Soon | Attention needed |
| **Red** | 0-39 | Urgent | Urgent intervention required |

**These zones apply to:**
- Parameter scores (table column)
- Domain scores (Structure/Function/Risk)
- System score card
- All visual indicators (borders, icons, bars)

### Score Types & Temporal Logic

**Three Score Types (from TEMPORAL_SCORING.md):**

1. **Point Score:** Current reading, most recent value
2. **Stability Score:** Typical value over time window
3. **Display Score:** Hybrid of point + stability (default shown)

**Level 3 Scoring Convention:**

- **Parameter table "Score" column:** Shows **Display Score** (hybrid)
  - Hover tooltip reveals: "Point: 38 | Stability: 73 | Display: 58"
- **System score card:** Uses system-level **Display Score**
- **Domain scores:** Use domain-level **Display Score**

**Critical Safety Rule:**
- **Alerts always driven by Point Scores + hard clinical thresholds**
- Stability/Display scores influence colors and trends
- **Smoothing can NEVER downgrade or delay a critical alert**

### Tri-State Parameter Behavior (NUMERIC / NS / NA)

**From PARAMETER_NORMALIZATION_v2.md:**

**Three Parameter States:**

1. **NUMERIC (scored):** Valid score 5-100
   - Display: Normal row with score, color, trend
   - Always visible in table

2. **NS (No Score - insufficient data):**
   - Display: "NS" in score column, gray status icon
   - Value shown if exists (e.g., "Sample hemolyzed")
   - **Always visible** - patient needs to know data missing
   - Counts against completeness

3. **NA (Not Applicable):**
   - **Hidden entirely from default patient view**
   - Excluded from completeness denominator
   - Only visible in:
     - Clinician Mode with "Show non-applicable" filter
     - "Recommended Tests Library" (separate UI)
   - Never mixed into main "Your Data" table

**Example:**
- Male patient: Pregnancy tests = NA (hidden completely)
- Hemolyzed potassium sample = NS (visible, needs repeat)

### Transparency & Deviation Formula

**Attribution uses 85-point baseline:**

```
Deviation = (Parameter_Score - 85) Ã— Parameter_Weight
```

**Interpretation:**
- Positive deviation â†’ pulling composite UP (score >85)
- Zero deviation â†’ at target (score =85)
- Negative deviation â†’ pulling composite DOWN (score <85)

**This formula is consistent across:**
- Level 1 (overall score contributors)
- Level 2 (system contributors)
- Level 3 (parameter contributors)

### Alert Severity vs Score Color

**TWO SEPARATE SYSTEMS:**

**1. Score Color (0-100 continuous):**
- Reflects normalized score zones (green/yellow/orange/red)
- Uses Display Score for stability
- Visual cue for health status

**2. Alert Severity (threshold-based):**
- **Critical:** Life-threatening (e.g., troponin â‰¥0.5, SBP â‰¥180)
- **Urgent:** Same-day action (e.g., glucose â‰¥250, SpOâ‚‚ <88)
- **Warning:** Discuss soon (e.g., HbA1c 7.5-8.5)
- **Monitor:** Routine follow-up

**Determined by:**
- Hard clinical thresholds from CRITICAL_ALERTS_v1_1.md
- **Always uses Point Score values** (current reading)
- Independent of smoothing or color zones

**Example:**
- SBP = 184 mmHg
  - Point Score: 8 â†’ Red zone (0-39)
  - Alert Severity: "Critical - Hypertensive emergency"
  - Action: "Call emergency services immediately"

### Plain Language & Content Standards

**All text content must:**
- Target 6th-8th grade reading level
- Source from PLAIN_LANGUAGE_LIBRARY.md (when complete)
- Use CONTEXTUAL_HELP_CONTENT.md for educational tooltips
- Never improvise medical terminology in code

**Reading level enforcement:**
- Automated Flesch-Kincaid checks
- Clinical review required for all patient-facing text

---

## DOCUMENT PURPOSE

This specification defines **Level 3: Detail View** - the deepest level of analysis showing individual parameter data, historical trends, and complete transparency into score calculations.

**Design Philosophy:**
- Maximum information density WITHOUT overwhelming
- Every parameter accessible and explainable
- Complete transparency into scoring logic
- Clinicians can rapidly assess during visits
- Curious patients can explore thoroughly
- Critical findings ALWAYS visible first (regardless of composite score)

**User Goals:**
- Understand individual test results in context
- See historical trends for parameters
- Investigate what's driving system scores
- Access educational content for parameters
- Print/export detailed reports
- Track progress on specific metrics

---

## SECTION 1: OVERALL LAYOUT

### 1.1 Screen Structure

**Full-screen interface (scrollable):**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  HEADER: â† Back to Systems | Cardiovascular System   â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  [BREADCRUMB: Overview > Systems > Cardiovascular ]   â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  ðŸ”´ CRITICAL ALERTS (if any)                          â”‚
â”‚     - Always displayed first, above everything else   â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  SYSTEM SCORE CARD                                    â”‚
â”‚  [Score: 78] [Progress bar] [Status]                 â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  TRANSPARENCY SECTION (mandatory)                     â”‚
â”‚  What's Working Well  |  What Needs Work             â”‚
â”‚  â€¢ Parameter 1 (+3.2) â”‚  â€¢ Parameter 1 (-4.8)        â”‚
â”‚  â€¢ Parameter 2 (+2.1) â”‚  â€¢ Parameter 2 (-3.1)        â”‚
â”‚  â€¢ Parameter 3 (+1.8) â”‚  â€¢ Parameter 3 (-2.2)        â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  DOMAIN SCORES                                        â”‚
â”‚  Structure: 82  |  Function: 76  |  Risk: 75        â”‚
â”‚  [Click to see which parameters contribute]          â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  PARAMETER TABLE (sortable, filterable)              â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”â”‚
â”‚  â”‚ Status â”‚ Param â”‚ Value     â”‚ Range  â”‚ Trendâ”‚ â‹®  â”‚â”‚
â”‚  â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”¤â”‚
â”‚  â”‚ ðŸ”´     â”‚ SBP   â”‚ 158 mmHg  â”‚ <120   â”‚ â†‘   â”‚ > â”‚â”‚
â”‚  â”‚ ðŸŸ¢     â”‚ HR    â”‚ 68 bpm    â”‚ 60-100 â”‚ â†’   â”‚ > â”‚â”‚
â”‚  â”‚ ...    â”‚ ...   â”‚ ...       â”‚ ...    â”‚ ...  â”‚ > â”‚â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”˜â”‚
â”‚                                                        â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 1.2 Layout Sections (Top to Bottom)

**Seven Primary Sections:**

1. **Header with Navigation** (80px)
   - Back button to Level 2
   - System name display
   - Action buttons (print, export)

2. **Breadcrumb Trail** (40px)
   - Shows navigation path

3. **Critical Alerts Section** (variable, 0-400px)
   - ONLY displays if critical/urgent parameters present
   - Always above system score (overrides composite "good" score)

4. **System Score Card** (120-160px)
   - Overall system score
   - Status message
   - Trend indicator

5. **Transparency Section** (200-300px)
   - Top positive/negative contributors
   - Explanation of score drivers

6. **Domain Breakdown** (160px)
   - Structure/Function/Risk scores
   - Expandable to show parameters per domain

7. **Parameter Table** (variable, scrollable)
   - All parameters for this system
   - Sortable, filterable, expandable rows

### 1.3 Responsive Behavior

**Desktop (â‰¥1024px):**
- Side-by-side transparency columns
- Multi-column parameter table
- Inline expandable parameter details

**Tablet (768px - 1023px):**
- Single column transparency (stacked)
- Simplified parameter table
- Modal popups for parameter details

**Mobile (â‰¤767px):**
- Accordion-style sections (collapsible)
- Card-based parameter list (not table)
- Full-screen modals for details

---

## SECTION 2: HEADER & NAVIGATION

### 2.1 Header Components

**Left Side:**
- **Back Button**
  - Icon: â† Arrow left
  - Text: "Back to Systems"
  - Click: Returns to Level 2
  - Keyboard: Escape key also works

**Center:**
- **System Name** (prominent)
  - Format: "[Icon] Cardiovascular System"
  - Font: Bold, 20-24px
  - Icon: System-specific (heart, lungs, brain, etc.)

**Right Side:**
- **Action Buttons**
  - Print icon â†’ Print this system view
  - Export icon â†’ Download PDF report
  - Share icon â†’ Share with provider
  - Settings icon â†’ Preferences

### 2.2 Breadcrumb Navigation

**Format:**
```
Health Overview > System Details > Cardiovascular System
```

**Interactive:**
- "Health Overview" â†’ Level 1
- "System Details" â†’ Level 2
- "Cardiovascular System" = current (not clickable, bold)

**Visual:**
- Separator: > or /
- Current location: Bold, darker color
- Previous levels: Clickable links, lighter color

---

## SECTION 3: CRITICAL ALERTS SECTION

### 3.1 Display Logic (CRITICAL DESIGN RULE)

**ALWAYS DISPLAY THIS SECTION FIRST - ABOVE SYSTEM SCORE:**

**Purpose:**
- A composite system score of 75 (green/good) CANNOT hide a critical parameter
- Life-threatening findings must be impossible to miss
- Clinicians and patients see alerts before anything else

**Example scenario:**
```
Cardiovascular System Score: 78 (Good health)
  â†‘
  BUT... has systolic BP = 198 mmHg (critical)
  
Therefore:
  Critical Alerts section displays ABOVE the "78 Good health" score
  Alert cannot be dismissed or minimized
```

### 3.2 Alert Section Layout

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  ðŸ”´ CRITICAL FINDINGS IN CARDIOVASCULAR SYSTEM      â”‚
â”‚                                                      â”‚
â”‚  2 Parameters Require Immediate Attention           â”‚
â”‚                                                      â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”â”‚
â”‚  â”‚ ðŸ”´ Systolic Blood Pressure: 198 mmHg           â”‚â”‚
â”‚  â”‚    CRITICAL - Hypertensive Emergency           â”‚â”‚
â”‚  â”‚    Action: Seek emergency care immediately     â”‚â”‚
â”‚  â”‚    [Call 911] [View Details]                  â”‚â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜â”‚
â”‚                                                      â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”â”‚
â”‚  â”‚ ðŸŸ  Troponin I: 0.08 ng/mL                      â”‚â”‚
â”‚  â”‚    URGENT - Mildly elevated, cardiac concern  â”‚â”‚
â”‚  â”‚    Action: Contact cardiologist today         â”‚â”‚
â”‚  â”‚    [Call Clinic] [View Details]               â”‚â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜â”‚
â”‚                                                      â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 3.3 Alert Card Design

**Each critical parameter gets own card:**

**Components:**
1. **Severity Icon** (left)
   - ðŸ”´ Critical (red)
   - ðŸŸ  Urgent (orange)
   - ðŸŸ¡ Warning (yellow)

2. **Parameter Name + Value** (bold)
   - Format: "Systolic Blood Pressure: 198 mmHg"
   - Font: Bold, 16-18px

3. **Clinical Interpretation** (line 2)
   - Plain language severity
   - Example: "CRITICAL - Hypertensive Emergency"
   - Example: "URGENT - Mildly elevated, cardiac concern"

4. **Recommended Action** (line 3)
   - Clear, specific instruction
   - Example: "Action: Seek emergency care immediately"
   - Example: "Action: Contact cardiologist today"

5. **Action Buttons** (bottom)
   - Primary: "Call 911" or "Call Clinic" (clickable phone number)
   - Secondary: "View Details" (opens parameter detail modal)

**Visual Design:**
- Border: 3px solid, matches severity color
- Background: Very light tint of severity color
- Drop shadow: Prominent elevation
- Padding: Generous (16-24px)
- Margin: Spaced between cards

### 3.4 Alert Sorting

**If multiple alerts:**

**Priority order:**
1. Life-threatening (critical red) first
2. Urgent (orange) second
3. Warning (yellow) third

**Within same severity:**
1. By clinical impact weight (CRITICAL_ALERTS_v1_1.md)
2. By time since detection (newest first)

### 3.5 No Alerts State

**If no critical/urgent/warning parameters:**
- This section does NOT display at all
- System score card appears immediately below breadcrumb
- No empty placeholder

---

## SECTION 4: SYSTEM SCORE CARD

### 4.1 Display Format

**Horizontal card layout:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Cardiovascular System                               â”‚
â”‚                                                       â”‚
â”‚         Score: 78                                    â”‚
â”‚  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘]                    â”‚
â”‚         Good Health â†‘ (+4 from last assessment)     â”‚
â”‚                                                       â”‚
â”‚  Last Updated: Nov 12, 2025                         â”‚
â”‚  Based on 12 of 12 parameters (100% complete)      â”‚
â”‚                                                       â”‚
â”‚  [How is this calculated?]                           â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 4.2 Components

**Score Number:**
- Size: 48-60px
- Weight: Extra bold
- Color: Dynamic (green/yellow/orange/red)

**Progress Bar:**
- Horizontal bar showing 0-100 scale
- Color-coded zones visible
- Current score position marked

**Status Message:**
- Plain language interpretation
- Trend indicator: â†‘â†“â†’ with numerical change
- Comparison to previous assessment

**Metadata:**
- Last updated timestamp
- Completeness: "X of Y parameters"
- Percentage complete

**Info Link:**
- "How is this calculated?"
- Click: Opens modal explaining system score formula

### 4.3 Interactive Behavior

**Hover over score:**
- Tooltip: "System score = 25% Structure + 50% Function + 25% Risk"
- Show: Domain score breakdown in mini-bars

**Click "How is this calculated?":**
- Opens modal with:
  - Full scoring formula
  - Domain contributions (Structure/Function/Risk)
  - Parameter weights and contributions
  - Link to SYSTEM_DOMAIN_SCORING_v2.md concepts

---

## SECTION 5: TRANSPARENCY SECTION

### 5.1 Two-Column Layout

**From TRANSPARENCY_DISPLAY_v1_1.md:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  What's Working Well âœ“   â”‚  What Needs Work âš        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚  â€¢ HDL Cholesterol       â”‚  â€¢ Systolic BP           â”‚
â”‚    Protective level      â”‚    Stage 2 HTN           â”‚
â”‚    Score: 92 (+3.2 pts)  â”‚    Score: 38 (-4.8 pts)  â”‚
â”‚                          â”‚                          â”‚
â”‚  â€¢ Resting Heart Rate    â”‚  â€¢ LDL Cholesterol       â”‚
â”‚    Optimal range         â”‚    Elevated              â”‚
â”‚    Score: 88 (+2.1 pts)  â”‚    Score: 62 (-3.1 pts)  â”‚
â”‚                          â”‚                          â”‚
â”‚  â€¢ Troponin I            â”‚  â€¢ Triglycerides         â”‚
â”‚    Normal                â”‚    Borderline high       â”‚
â”‚    Score: 85 (+1.8 pts)  â”‚    Score: 68 (-2.2 pts)  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 5.2 Selection Algorithm

**From TRANSPARENCY_DISPLAY_v1_1.md Section 2:**

**For this system's parameters:**

**Step 1:** Calculate deviation for each parameter
```
Deviation = (Parameter_Score - 85) Ã— Parameter_Weight_in_System
```

**Step 2:** Sort by absolute deviation

**Step 3:** Select top 3 positive and top 3 negative

**Result:**
- 3 parameters pulling system UP (left column)
- 3 parameters pulling system DOWN (right column)

### 5.3 Display Format Per Parameter

**Each line shows:**

1. **Parameter Name** (bold)
   - Plain language version
   - Example: "HDL Cholesterol" (not "HDL-C")

2. **Clinical Status** (regular text)
   - One-line plain language interpretation
   - Example: "Protective level" or "Stage 2 HTN"

3. **Score and Contribution** (semi-bold, colored)
   - Format: "Score: 92 (+3.2 pts)"
   - Color: Green for positive, Orange/Red for negative

**Interactive:**
- Hover: Highlight, show tooltip with actual value
- Click: Opens parameter detail modal

### 5.4 Mobile Layout

**On mobile (<768px):**
- Single column (stacked)
- "What's Working Well" first
- "What Needs Work" second
- Collapsible headers to save space

---

## SECTION 6: DOMAIN BREAKDOWN

### 6.1 Display Format

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Score Breakdown by Domain                           â”‚
â”‚                                                       â”‚
â”‚  Structure (Anatomy)           82                    â”‚
â”‚  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘]                              â”‚
â”‚  5 parameters assessed         [Show Details â–¼]     â”‚
â”‚                                                       â”‚
â”‚  Function (Physiology)         76                    â”‚
â”‚  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘]                              â”‚
â”‚  4 parameters assessed         [Show Details â–¼]     â”‚
â”‚                                                       â”‚
â”‚  Risk (Prognosis)              75                    â”‚
â”‚  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘]                              â”‚
â”‚  3 parameters assessed         [Show Details â–¼]     â”‚
â”‚                                                       â”‚
â”‚  Overall System Score: 78                           â”‚
â”‚  = (82 Ã— 0.25) + (76 Ã— 0.50) + (75 Ã— 0.25)        â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 6.2 Components

**For each domain:**

1. **Domain Name + Label**
   - Name: "Structure" / "Function" / "Risk"
   - Label: "(Anatomy)" / "(Physiology)" / "(Prognosis)"

2. **Score Number**
   - Size: 32-36px
   - Color-coded by zone

3. **Progress Bar**
   - Shows 0-100 scale with score position

4. **Parameter Count**
   - "5 parameters assessed"
   - Click: Expand to see parameter list

5. **Expand/Collapse Button**
   - "Show Details" â–¼ / "Hide Details" â–²

**Formula Display:**
- Shows how domains combine into system score
- Weights clearly shown (25%, 50%, 25%)

### 6.3 Expanded Domain Detail

**When user clicks "Show Details":**

```
  Function (Physiology)          76
  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘]
  4 parameters assessed

  â–¼ Parameters contributing to Function:
    â€¢ Ejection Fraction: 62% (Score: 82, Weight: 40%)
    â€¢ VO2 Max: 32 ml/kg/min (Score: 75, Weight: 30%)
    â€¢ Exercise Capacity: Good (Score: 78, Weight: 20%)
    â€¢ Resting Heart Rate: 68 bpm (Score: 88, Weight: 10%)

  Function Score = (82Ã—0.4) + (75Ã—0.3) + (78Ã—0.2) + (88Ã—0.1) = 76
```

**Shows:**
- Each parameter name
- Current value with units
- Normalized score (0-100)
- Weight in domain calculation (%)
- Formula showing how domain score calculated

### 6.4 Interactive Behavior

**Click on parameter name:**
- Opens full parameter detail modal (see Section 8)

**Hover over domain score:**
- Tooltip: "This domain is weighted at [X]% of overall system score"

---

## SECTION 7: PARAMETER TABLE

### 7.1 Table Structure & Tri-State Behavior

**Multi-column sortable table:**

```
â”Œâ”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”
â”‚ St â”‚ Parameter            â”‚ Value       â”‚ Ref Range     â”‚ Score â”‚ Trendâ”‚ â‹®  â”‚
â”œâ”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”¤
â”‚ ðŸ”´ â”‚ Systolic BP          â”‚ 158 mmHg    â”‚ <120 optimal  â”‚ 38    â”‚ â†‘   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ HDL Cholesterol      â”‚ 65 mg/dL    â”‚ >40 (M)       â”‚ 92    â”‚ â†’   â”‚ >  â”‚
â”‚ ðŸŸ¡ â”‚ LDL Cholesterol      â”‚ 142 mg/dL   â”‚ <100 optimal  â”‚ 62    â”‚ â†“   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ Resting Heart Rate   â”‚ 68 bpm      â”‚ 60-100        â”‚ 88    â”‚ â†’   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ Diastolic BP         â”‚ 82 mmHg     â”‚ <80 optimal   â”‚ 78    â”‚ â†‘   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ Total Cholesterol    â”‚ 198 mg/dL   â”‚ <200          â”‚ 82    â”‚ â†’   â”‚ >  â”‚
â”‚ ðŸŸ¡ â”‚ Triglycerides        â”‚ 165 mg/dL   â”‚ <150          â”‚ 68    â”‚ â†‘   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ Troponin I           â”‚ <0.01 ng/mL â”‚ <0.04         â”‚ 85    â”‚ â†’   â”‚ >  â”‚
â”‚ NS â”‚ BNP                  â”‚ Not tested  â”‚ <100 pg/mL    â”‚ NS    â”‚ -   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ EKG: QRS Duration    â”‚ 92 ms       â”‚ <120 ms       â”‚ 90    â”‚ â†’   â”‚ >  â”‚
â”‚ ðŸŸ¢ â”‚ Ejection Fraction    â”‚ 62%         â”‚ >55%          â”‚ 88    â”‚ â†’   â”‚ >  â”‚
â””â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”˜
```

**CRITICAL: Tri-State Display Logic (from PARAMETER_NORMALIZATION_v2.md):**

**NUMERIC Parameters (scored 5-100):**
- Display: Full row with all columns populated
- Status icon: Color-coded circle (ðŸ”´ðŸŸ ðŸŸ¡ðŸŸ¢) based on score zone
- Score column: Shows Display Score (hybrid point + stability)
- Always visible in table

**NS Parameters (No Score - insufficient data):**
- Display: Row shows in table with "NS" in status and score columns
- Status icon: Gray "NS" badge
- Value: Shows reason if known ("Sample hemolyzed", "Not tested", "Incomplete draw")
- **Always visible** - patient needs to know data is missing/invalid
- Counts against completeness percentage
- Example: BNP not tested, Potassium sample hemolyzed

**NA Parameters (Not Applicable):**
- **HIDDEN from default patient view** - do not display in table
- Excluded from completeness denominator
- Only visible in:
  1. **Clinician Mode** with "Show Non-Applicable Parameters" toggle enabled
  2. **Recommended Tests Library** (separate UI, not mixed with patient's data)
- Example: Pregnancy tests for male patient, PSA for female patient

**Implementation Note:**
The example table above shows NS (BNP) but does NOT show NA parameters because they are hidden. The "Stress Test - Not needed - NA" row from v1.0 was INCORRECT and has been removed from this spec per tri-state rules.

### 7.2 Column Definitions

**Column 1: Status Icon**
- Width: 40px
- Icons based on **Alert Severity** (separate from score color):
  - ðŸ”´ **Critical** - Life-threatening (troponin â‰¥0.5, SBP â‰¥180)
  - ðŸŸ  **Urgent** - Same-day action (glucose â‰¥250, SpOâ‚‚ <88)
  - ðŸŸ¡ **Warning** - Discuss soon (HbA1c 7.5-8.5)
  - ðŸŸ¢ **Good** - Within acceptable range
  - **NS** - Gray badge "Not Scored" (insufficient data)
  - **NA** - HIDDEN from default view (not applicable)

**Alert Severity Source:**
- Determined by CRITICAL_ALERTS_v1_1.md clinical thresholds
- Uses **Point Score** (current reading), never smoothed
- Independent of Display Score color zones

**Column 2: Parameter Name**
- Width: 25% of table
- Text: Plain language name from PLAIN_LANGUAGE_LIBRARY.md
- Sortable: Alphabetically
- Hover: Full technical name in tooltip

**Column 3: Value**
- Width: 15% of table
- Text: Actual measured value with units
- Format: Numbers rounded appropriately
- Sortable: Numerically
- **Aberrant Value Flag:** âš  icon if flagged by TEMPORAL_SCORING aberrant detection
  - Hover: "This reading is unusual for you. Please recheck."

**Column 4: Reference Range**
- Width: 20% of table
- Text: Personalized target range for this patient
- Format: Accounts for age, sex, conditions, medications
- Example: "<120 optimal" or "40-60 mg/dL"
- Source: PARAMETER_NORMALIZATION_v2.md personalized targets + CONTEXT_RULES.md

**Column 5: Score**
- Width: 10% of table
- Text: **Display Score (0-100)** - hybrid of point + stability
- Color-coded by universal zone (Green 75-100, Yellow 60-74, Orange 40-59, Red 0-39)
- Sortable: By score value
- **Hover tooltip reveals temporal detail:**
  - "Point Score: 38 (current reading)"
  - "Stability Score: 73 (typical value)"
  - "Display Score: 58 (shown)"
  - Source: TEMPORAL_SCORING.md
- Shows: "NS" (gray) for insufficient data, never "NA" (hidden)

**Column 6: Trend**
- Width: 8% of table
- Icons:
  - â†‘ Green: Improving (Display Score increased â‰¥5 points)
  - â†“ Red: Declining (Display Score decreased â‰¥5 points)
  - â†’ Gray: Stable (within Â±4 points)
  - - (dash): No historical data for comparison
- **Trend Logic:** Compares Display Scores from last two assessments
- Source: TEMPORAL_SCORING.md trend detection
- Sortable: By trend direction

**Column 7: Domain Tag (NEW - Optional for Clinician Mode)**
- Width: 5% of table
- Shows which domain(s) parameter contributes to:
  - **S** (Structure), **F** (Function), **R** (Risk)
  - If multi-domain: "S+R" with tooltip showing weights
- Purpose: Maps to 24-cell matrix
- Helps clinicians understand parameter's clinical role

**Column 8: Actions**
- Width: 5% of table
- Icon: â‹® (three dots) or > (chevron)
- Click: Opens parameter detail modal (Section 8)

### 7.3 Table Sorting

**Default sort order:**
1. Critical (red) first
2. Urgent (orange) second
3. Warning (yellow) third
4. Good (green) last
5. NS/NA at bottom

**User can re-sort by clicking column headers:**
- Status (by severity)
- Parameter (alphabetically)
- Value (numerically)
- Score (numerically)
- Trend (improving first, declining last)

**Sort indicator:**
- â–² Ascending
- â–¼ Descending
- Appears next to column header

### 7.4 Table Filtering

**Filter toolbar above table:**

```
[Search: ____] [Filter by status: All â–¼] [Show: All parameters â–¼]
```

**Search box:**
- Live search by parameter name
- Updates table as user types

**Status filter dropdown:**
- All (default)
- Critical only
- Needs attention (orange + red)
- Good health only (green)
- Not assessed (NS/NA)

**Parameter type filter:**
- All parameters (default)
- Labs only
- Imaging only
- Functional tests only
- Vital signs only

### 7.5 Expandable Rows

**Click anywhere on row (except action icon):**
- Row expands downward
- Shows inline detail panel

**Expanded view contains:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Systolic Blood Pressure                             â”‚
â”‚                                                       â”‚
â”‚  Current: 158 mmHg (Score: 38) ðŸ”´ Critical          â”‚
â”‚                                                       â”‚
â”‚  Historical Trend (last 12 months):                  â”‚
â”‚  [Line graph showing values over time]              â”‚
â”‚                                                       â”‚
â”‚  What this means:                                    â”‚
â”‚  "Your blood pressure is in the Stage 2 Hypertensionâ”‚
â”‚   range. This significantly increases risk of heart  â”‚
â”‚   attack, stroke, and kidney damage. Immediate      â”‚
â”‚   treatment is strongly recommended."               â”‚
â”‚                                                       â”‚
â”‚  Your personalized target: <120 mmHg                â”‚
â”‚  Last 3 readings: 162, 155, 158 mmHg                â”‚
â”‚                                                       â”‚
â”‚  [View Full Details] [Print] [Share with Provider]  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Contents:**
- Current value with score
- Mini trend graph (last 6-12 months)
- Plain language explanation
- Personalized target
- Recent readings
- Action buttons

### 7.6 Mobile Optimization

**On mobile (<768px):**

**Replace table with card list:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸ”´ Systolic BP              â”‚
â”‚ 158 mmHg (Target: <120)     â”‚
â”‚ Score: 38 - Critical        â”‚
â”‚ Trend: â†‘ Rising             â”‚
â”‚ [View Details >]            â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜

â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ ðŸŸ¢ HDL Cholesterol          â”‚
â”‚ 65 mg/dL (Target: >40)      â”‚
â”‚ Score: 92 - Excellent       â”‚
â”‚ Trend: â†’ Stable             â”‚
â”‚ [View Details >]            â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
...
```

**Card format:**
- Status icon + Parameter name (header)
- Value + Target (line 2)
- Score + Status (line 3)
- Trend (line 4)
- View Details button

**Sorting/Filtering:**
- Accessible via hamburger menu
- Applied to card list

---

## SECTION 8: PARAMETER DETAIL MODAL

### 8.1 Modal Trigger

**Opens when user:**
- Clicks action icon (â‹® or >) in table
- Clicks parameter in transparency section
- Clicks parameter in expanded domain breakdown
- Clicks parameter card on mobile

### 8.2 Modal Layout

**Full-screen overlay (desktop: centered modal, mobile: full screen):**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  [X Close]                  Systolic Blood Pressure â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  CURRENT STATUS                                     â”‚
â”‚  158 mmHg - Stage 2 Hypertension ðŸ”´                â”‚
â”‚  Score: 38 (Critical - Urgent attention needed)    â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  HISTORICAL TREND                                   â”‚
â”‚  [Large line graph showing last 12 months]         â”‚
â”‚  - Hover points for exact values                   â”‚
â”‚  - Target line displayed                           â”‚
â”‚  - Color-coded zones (green/yellow/orange/red)     â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  WHAT THIS MEANS (Plain Language)                  â”‚
â”‚  Blood pressure is the force of blood against      â”‚
â”‚  artery walls. At 158 mmHg, your systolic         â”‚
â”‚  pressure is high enough to significantly increase â”‚
â”‚  risk of heart attack, stroke, and kidney damage.  â”‚
â”‚                                                      â”‚
â”‚  [Learn More About Blood Pressure]                 â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  YOUR DETAILS                                       â”‚
â”‚  â€¢ Personalized Target: <120 mmHg (age, conditions)â”‚
â”‚  â€¢ Recent Readings: 162, 155, 158 mmHg             â”‚
â”‚  â€¢ Measurement Method: Automated cuff               â”‚
â”‚  â€¢ Last Measured: Nov 12, 2025 at 9:15 AM         â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  SCORING DETAILS                                    â”‚
â”‚  â€¢ Normalized Score: 38 / 100                      â”‚
â”‚  â€¢ Reference: Stage 2 Hypertension (â‰¥140 mmHg)    â”‚
â”‚  â€¢ This parameter contributes to:                  â”‚
â”‚    - Cardiovascular Function: 40% weight           â”‚
â”‚    - Cardiovascular Risk: 30% weight               â”‚
â”‚                                                      â”‚
â”‚  [How is this score calculated?]                   â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  RELATED PARAMETERS                                 â”‚
â”‚  â€¢ Diastolic Blood Pressure: 82 mmHg (Score: 78)  â”‚
â”‚  â€¢ Heart Rate: 68 bpm (Score: 88)                 â”‚
â”‚  â€¢ Pulse Pressure: 76 mmHg (Calculated)           â”‚
â”‚                                                      â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                      â”‚
â”‚  ACTIONS                                            â”‚
â”‚  [Print This Report]  [Share with Provider]        â”‚
â”‚  [Add to Watch List]  [Set Reminder]               â”‚
â”‚                                                      â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 8.3 Modal Sections

**Section 1: Current Status**
- Current value (large, prominent)
- Clinical zone/status
- Normalized score with interpretation

**Section 2: Historical Trend**
- Interactive line graph
- Minimum 6 months of data (if available)
- Hover: Exact value and date
- Target line overlay
- Color-coded zones in background

**Section 3: Plain Language Explanation**
- What this parameter measures
- Why it matters for health
- Clinical significance of current value
- Link to educational content

**Section 4: Patient-Specific Details**
- Personalized target (why this target for this patient)
- Recent measurements (last 3-5 readings)
- Measurement method
- Last measurement date/time

**Section 5: Scoring Details**
- How normalized score calculated
- Reference ranges used
- Which systems/domains it contributes to
- Weights in those systems
- Link to scoring methodology

**Section 6: Related Parameters**
- Other parameters that interact with this one
- Quick view of their status
- Click to jump to that parameter

**Section 7: Actions**
- Print individual parameter report
- Share with healthcare provider
- Add to personal watch list
- Set reminder to retest

### 8.4 Graph Interactivity

**Trend graph features:**

- **Hover:** Show exact value, date, score at that point
- **Zoom:** Click-drag to zoom into time period
- **Toggle:** Show/hide target line
- **Toggle:** Show/hide confidence intervals (if temporal smoothing applied)
- **Annotations:** Mark interventions (e.g., "Started medication 8/1/25")

**Time range selector:**
- 3 months | 6 months | 1 year | 2 years | All time

**Export:**
- Download graph as image
- Download data as CSV

---

## SECTION 9: CONTEXTUAL HELP SYSTEM

### 9.1 Help Icons Throughout Interface

**Small (i) or (?) icons next to:**
- Domain names (Structure, Function, Risk)
- Scoring terminology (normalized score, etc.)
- Clinical terms in plain language explanations
- Complex calculations

**Hover over icon:**
- Tooltip appears with brief definition
- Example: "(i) next to 'Function': How well this organ system performs its job"

**Click icon:**
- Opens detailed help modal with more information

### 9.2 "What is..." Links

**For clinical concepts:**

**Example: "What is systolic blood pressure?"**
- Opens layered explanation:
  - **Simple:** "The pressure when your heart beats"
  - **Intermediate:** "Maximum pressure in arteries during heart contraction"
  - **Advanced:** "Measured in mmHg, reflects cardiac output and arterial stiffness"

**User can toggle complexity level:**
- ðŸ™‚ Simple | ðŸ§ Intermediate | ðŸ”¬ Advanced

### 9.3 Educational Content Links

**"Learn More About..." buttons:**
- Link to curated educational resources
- Topics:
  - What affects this parameter?
  - How to improve this parameter?
  - Why does this matter for my health?
  - What treatments are available?

**Content sources:**
- Internally created patient education
- Vetted external resources (Mayo Clinic, AHA, CDC, etc.)
- Videos, infographics, articles

---

## SECTION 10: PRINT & EXPORT

### 10.1 Print System View

**"Print" button in header:**

**Generates printable report:**

```
PATIENT HEALTH REPORT
Cardiovascular System

Patient: John Doe
Date: November 12, 2025

SYSTEM OVERVIEW
Overall Score: 78 (Good Health)
Structure: 82  |  Function: 76  |  Risk: 75

CRITICAL FINDINGS
â€¢ Systolic Blood Pressure: 158 mmHg - Stage 2 HTN
  Action: Contact physician immediately

PARAMETERS ASSESSED
[Table of all parameters with values, ranges, scores]

TOP CONTRIBUTORS
What's Working Well:
â€¢ HDL Cholesterol (92)
â€¢ Resting Heart Rate (88)
â€¢ Troponin I (85)

What Needs Work:
â€¢ Systolic Blood Pressure (38)
â€¢ LDL Cholesterol (62)
â€¢ Triglycerides (68)

[Page 1 of 2]
```

**Print formatting:**
- Black and white optimized
- Page breaks at logical sections
- Header/footer with patient info and page numbers
- QR code linking back to dashboard (optional)

### 10.2 Export PDF Report

**"Export PDF" button:**

**Generates comprehensive PDF:**
- All sections from print view
- PLUS historical trend graphs (in color)
- PLUS detailed scoring calculations
- PLUS educational summaries

**PDF metadata:**
- Title: "Cardiovascular System Report - [Patient Name]"
- Author: Clinic name
- Creation date
- Watermark: "Confidential Medical Information"

### 10.3 Share with Provider

**"Share" button:**

**Options:**
- Email to provider (enter email address)
- Upload to patient portal
- Generate shareable link (expires in 7 days)
- Print and bring to appointment

**Shared report includes:**
- System score and breakdown
- Critical findings prominently
- All parameter data
- Trend graphs
- Clinician notes section (blank for provider to fill)

---

## SECTION 11: SPECIAL STATES & EDGE CASES

### 11.1 Incomplete System Data

**If <30% of parameters measured:**

**Show warning banner:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  âš ï¸ Limited Data for Cardiovascular System      â”‚
â”‚                                                  â”‚
â”‚  Only 3 of 12 parameters assessed (25%)        â”‚
â”‚  Score reliability: LOW                         â”‚
â”‚                                                  â”‚
â”‚  Recommended assessments:                       â”‚
â”‚  â€¢ Lipid panel                                  â”‚
â”‚  â€¢ Echocardiogram                               â”‚
â”‚  â€¢ Exercise stress test                         â”‚
â”‚  â€¢ ...                                          â”‚
â”‚                                                  â”‚
â”‚  [Schedule Complete Assessment]                 â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Transparency section:**
- May show fewer than 3 items per column
- Note: "Complete assessment for more insights"

**Domain scores:**
- Display with asterisk: "76*"
- Note: "Based on limited data"

### 11.2 No Critical Alerts But Low Score

**Example: System Score = 45 (orange), no critical parameters**

**User might wonder: "Why is score low if nothing critical?"**

**Explanation section:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Why is this score low?                          â”‚
â”‚                                                  â”‚
â”‚  While no single parameter is critically        â”‚
â”‚  abnormal, multiple parameters are below        â”‚
â”‚  optimal ranges. This combination reflects      â”‚
â”‚  compromised system health.                     â”‚
â”‚                                                  â”‚
â”‚  Top issues:                                     â”‚
â”‚  â€¢ 5 parameters in yellow zone (suboptimal)    â”‚
â”‚  â€¢ 2 parameters in orange zone (action needed) â”‚
â”‚                                                  â”‚
â”‚  [See What Needs Work]                          â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 11.3 Perfect Score Scenario

**If system score = 100:**

**Celebration design:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  ðŸŒŸ Exceptional Cardiovascular Health! ðŸŒŸ      â”‚
â”‚                                                  â”‚
â”‚  Score: 100 / 100                               â”‚
â”‚                                                  â”‚
â”‚  All parameters are at optimal levels.          â”‚
â”‚  This represents sustained excellence.          â”‚
â”‚                                                  â”‚
â”‚  Keep up your healthy habits!                   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Subtle celebration animation:** (Optional)
- Confetti effect (brief, 2 seconds)
- Success sound (if user has audio enabled)

### 11.4 Parameter Not Applicable (NA)

**Example: Pregnancy-related tests for male patient**

**In table, show:**
- Status: NA (gray)
- Value: "Not applicable"
- Score: NA
- No alert icon

**Hover tooltip:**
- "This test is not needed for your demographic profile"

### 11.5 Parameter Not Scored (NS)

**Example: Recent test result not yet integrated into scoring**

**In table, show:**
- Status: NS (gray)
- Value: Actual measured value
- Score: NS
- Reference range: Standard range

**Hover tooltip:**
- "Result recorded but not yet included in score calculation. Check back soon."

**OR: Missing required data for scoring**
- Example: Need both systolic AND diastolic BP for pulse pressure

---

## SECTION 12: TEMPORAL FEATURES

### 12.1 Time Travel Feature

**Date selector at top of page:**

```
[View data as of: Nov 12, 2025 â–¼] (default: most recent)
```

**Dropdown shows:**
- Most recent (default)
- 1 month ago
- 3 months ago
- 6 months ago
- 1 year ago
- Custom date picker

**When historical date selected:**
- All scores recalculate for that date
- Parameter table shows values as of that date
- Trend graphs highlight selected point
- Banner: "Viewing data as of [Date]. [Return to current â†’]"

**Use cases:**
- Review progress over time
- Compare before/after intervention
- Understand score changes

### 12.2 Comparison Mode

**Toggle: "Compare to Previous Assessment"**

**Activates split-screen view:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Current (Nov 2025)  â”‚  Previous (Aug 2025) â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚  Score: 78           â”‚  Score: 74           â”‚
â”‚  SBP: 158            â”‚  SBP: 152            â”‚
â”‚  HDL: 65             â”‚  HDL: 62             â”‚
â”‚  ...                 â”‚  ...                 â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜

â–³ Changes: +4 points overall, SBP +6 (worsened), HDL +3 (improved)
```

**Highlights:**
- Parameters that improved (green)
- Parameters that worsened (red)
- Parameters that stayed stable (gray)

### 12.3 Annotations on Timeline

**Clinicians/patients can add notes:**

**Example annotations:**
- "Started lisinopril 10mg"
- "Began exercise program"
- "Dietary changes"
- "Stressful period at work"

**Display on trend graphs:**
- Vertical line at annotation date
- Hover: Shows note text
- Helps correlate changes with interventions

---

## SECTION 13: CLINICIAN-SPECIFIC FEATURES

### 13.1 Clinician Mode Toggle

**Setting: "Clinician View" (optional enhancement)**

**When enabled:**
- Shows technical parameter names alongside plain language
- Displays ICD-10 codes for conditions
- Shows CPT codes for tests
- Includes medication reconciliation section
- Adds clinical note entry field

**Purpose:**
- Efficiency during clinical encounters
- Documentation support
- Billing code reference

### 13.2 Clinical Notes Section

**Expandable section at bottom:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Clinical Notes (Clinician Only)                â”‚
â”‚  â–¼                                               â”‚
â”‚  [Text entry field]                             â”‚
â”‚                                                  â”‚
â”‚  Assessment: Uncontrolled Stage 2 HTN          â”‚
â”‚  Plan: Increase lisinopril to 20mg daily       â”‚
â”‚        Recheck BP in 2 weeks                    â”‚
â”‚        Repeat labs in 3 months                  â”‚
â”‚                                                  â”‚
â”‚  [Save Note]  [Sign & Lock]                     â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Features:**
- Rich text editor
- Voice-to-text dictation
- Template insertion
- Auto-saves as draft
- Sign & lock = final note

### 13.3 Quick Order Entry

**"Order Tests" button (clinicians only):**

**Opens order panel:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Order Tests for Cardiovascular System          â”‚
â”‚                                                  â”‚
â”‚  Recommended:                                    â”‚
â”‚  â˜ Lipid Panel (due in 3 months)               â”‚
â”‚  â˜ Echocardiogram (due for baseline)           â”‚
â”‚  â˜ Exercise Stress Test (suggested)            â”‚
â”‚                                                  â”‚
â”‚  Custom:                                         â”‚
â”‚  [Search tests...________________________]      â”‚
â”‚                                                  â”‚
â”‚  [Add to Order Set]  [Send to Lab]             â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Integration:**
- Links to EMR order entry system
- Pre-fills patient information
- Adds clinical indication automatically

---

## SECTION 14: PERFORMANCE & OPTIMIZATION

### 14.1 Load Time Requirements

**Initial page load:**
- Critical alerts: <0.5s
- System score card: <1s
- Transparency section: <1.5s
- Parameter table (first 20 rows): <2s
- Complete page interactive: <3s

### 14.2 Large Dataset Handling

**If system has >50 parameters:**

**Virtual scrolling:**
- Only render visible rows
- Lazy load as user scrolls
- Maintains smooth 60fps scrolling

**Pagination option:**
- 20 parameters per page
- "Load more" button at bottom
- OR infinite scroll

### 14.3 Caching Strategy

**Client-side caching:**
- Cache system scores for 5 minutes
- Cache parameter data for 5 minutes
- Cache trend graphs for 15 minutes
- Invalidate on data update

**Progressive loading:**
- Load critical content first
- Load trend graphs on-demand
- Load historical data when accessed

---

## SECTION 15: ACCESSIBILITY (WCAG 2.1 AA)

### 15.1 Keyboard Navigation

**Full keyboard access:**
- Tab: Navigate through interactive elements
- Enter/Space: Activate buttons and links
- Escape: Close modals
- Arrow keys: Navigate table rows

**Skip links:**
- "Skip to critical alerts"
- "Skip to parameter table"
- "Skip to navigation"

### 15.2 Screen Reader Support

**ARIA labels:**
- Table: "Cardiovascular parameters table"
- Status icons: "Status: Critical" (not just red circle)
- Trends: "Trend: Improving, increased 5 points"

**Live regions:**
- Announce when alerts appear
- Announce when data updates

**Descriptive text:**
- Every graph has text alternative
- Complex tables have summary text

### 15.3 Visual Accessibility

**High contrast mode:**
- Toggle available in settings
- Increased border weights
- Stronger color differences

**Font scaling:**
- Respects browser/OS font size settings
- Layout doesn't break at 200% zoom

**Color blindness:**
- Icons supplement all color coding
- Patterns on graphs
- Text labels always present

---

## SECTION 16: IMPLEMENTATION CHECKLIST

### 16.1 Pre-Launch Validation

**Clinical Review:**
- â˜ Critical alerts display correctly per CRITICAL_ALERTS_v1_1.md
- â˜ Transparency calculations match TRANSPARENCY_DISPLAY_v1_1.md
- â˜ Domain scoring matches SYSTEM_DOMAIN_SCORING_v2.md
- â˜ Parameter normalization aligns with PARAMETER_NORMALIZATION_v2.md
- â˜ Plain language accurate and appropriate
- â˜ Reference ranges personalized correctly

**Usability Testing:**
- â˜ Patients can find critical findings in <10 seconds
- â˜ Parameter table sortable and filterable intuitively
- â˜ Modal details helpful and not overwhelming
- â˜ Print output clinically useful
- â˜ Mobile experience functional

**Technical Testing:**
- â˜ All calculations verified against specs
- â˜ Performance targets met
- â˜ Accessibility audit passed (WCAG AA)
- â˜ Data refresh works reliably
- â˜ Edge cases handled gracefully
- â˜ Security review completed

---

## SECTION 17: SUMMARY

### 17.1 Key Features

**Level 3 Detail View provides:**
1. âœ… Critical alerts ALWAYS displayed first (override composite good scores)
2. âœ… Complete system score breakdown (domains + transparency)
3. âœ… Sortable, filterable parameter table with all data
4. âœ… Historical trends for every parameter
5. âœ… Plain language explanations with educational content
6. âœ… Interactive parameter detail modals
7. âœ… Contextual help throughout
8. âœ… Print/export/share capabilities
9. âœ… Temporal features (time travel, comparisons)
10. âœ… Clinician-specific tools (notes, orders)

### 17.2 Success Criteria

**A successful Level 3 view means:**
- Critical findings impossible to miss
- Patients can explore any parameter deeply
- Clinicians can rapidly assess during appointments
- Complete transparency into scoring
- No feeling of information overload (progressive disclosure works)
- Educational needs met through contextual help
- Actionable insights for improvement
- Clinical documentation supported

### 17.3 Integration Summary

**Level 3 represents the deepest layer:**
- Receives system selection from Level 2
- Displays all parameters for that system
- Provides complete transparency
- Enables investigation and education
- Supports clinical decision-making

**Data dependencies:**
- All PARAMETERS_*.md specifications (when complete)
- SYSTEM_DOMAIN_SCORING_v2.md formulas
- TRANSPARENCY_DISPLAY_v1_1.md algorithms
- CRITICAL_ALERTS_v1_1.md thresholds
- CLINICAL_DECISION_RULES_v1_0.md logic
- TEMPORAL_SCORING.md display requirements

---

**END OF DASHBOARD LEVEL 3 SPECIFICATION**

*This document defines the most detailed view of the Patient Health Dashboard, providing complete parameter-level analysis and transparency. The three-level progressive disclosure system (Hero â†’ Systems â†’ Detail) is now fully specified.*
