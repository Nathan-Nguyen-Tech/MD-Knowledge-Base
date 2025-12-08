# DASHBOARD LEVEL 2 SPECIFICATION
## Patient Health Dashboard - System Overview

**Document Type:** User Interface Specification  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

**Prerequisites (read first):**
- `PROJECT_SPECIFICATION_v2.md` - Master architecture
- `SYSTEM_DOMAIN_SCORING_v2.md` - How system and domain scores calculate
- `TRANSPARENCY_DISPLAY_v1_1.md` - Top contributors logic
- `DASHBOARD_LEVEL1_SPEC.md` - Hero view (previous level)

**This document connects to:**
- `DASHBOARD_LEVEL3_SPEC.md` - Detail view (next level down)
- `CRITICAL_ALERTS_v1_1.md` - System-level alerts
- `PLAIN_LANGUAGE_LIBRARY.md` - System descriptions

---

## GLOBAL ASSUMPTIONS (CRITICAL ALIGNMENT)

### Scoring Baseline Philosophy

**85-at-Target Framework:**
- Individual parameters normalized so z-score = 0 (personalized target) â†’ **85 points**
- System scores inherit this: well-controlled systems typically score ~85
- Overall health score follows same principle
- **This is NOT a conservative 50-point baseline** (older project language being updated)

**Why 85 = target, not 100?**
- Prevents overconfidence at guideline targets
- Rewards sustained excellence (86-100 = exceptional, rare)
- Still motivating: B+ at target, A/A+ for excellence

**Color Zones (Universal):**
- **Green (75-100)**: Optimal to excellent health
- **Yellow (60-74)**: Monitor - room to improve
- **Orange (40-59)**: Act soon - needs attention
- **Red (0-39)**: Urgent - high risk

**Composite Score Structure:**
- Overall Health = 70% Objective (8 systems) + 30% Subjective (5 pillars)
- System scores = 25% Structure + 50% Function + 25% Risk
- See COMPOSITE_SCORING_v2.md and SYSTEM_DOMAIN_SCORING_v2.md

### Status Language Standardization

**Across all dashboard levels, use these exact phrases:**
- Green: "Optimal" (with modifiers: Excellent/Good/Healthy)
- Yellow: "Monitor - room to improve"
- Orange: "Act soon - needs attention"
- Red: "Urgent - high risk"

**Avoid:** "Good health", "Fair health", "Poor health" (too vague)

### Lifestyle Pillars Naming

**Canonical Internal Names** (for scoring/documentation):
1. Movement
2. Nutrition
3. Recovery
4. Emotion
5. Environment

**UI Display Names** (for patients/dashboard):
1. "Exercise & Movement"
2. "Nutrition"
3. "Sleep & Recovery"
4. "Stress & Emotional Health"
5. "Social & Community"

**MAP/Purpose:** Separate hero element, NOT a pillar

---

## DOCUMENT PURPOSE

This specification defines **Level 2: System Overview** - the expandable view that shows health broken down by the 8 organ systems and 5 lifestyle pillars.

**Design Philosophy:**
- Visual comparison across all body systems
- Rapid identification of which systems need attention
- Progressive disclosure - still digestible, not overwhelming
- Interactive exploration encouraged
- Bridge between high-level (Level 1) and detailed analysis (Level 3)

**User Goals:**
- Understand which body systems are healthy vs problematic
- Compare organ system health visually
- Assess lifestyle factors
- Navigate to detailed parameter analysis
- Track changes over time

---

## SECTION 1: OVERALL LAYOUT

### 1.1 Screen Structure

**Scrollable layout (vertical):**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  HEADER: Collapse to Level 1 | Patient Name | ...    â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚  [BREADCRUMB: Overview > Systems ]                    â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚           OVERALL HEALTH SCORE (mini)                 â”‚
â”‚                    82                                 â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚       ORGAN SYSTEMS SECTION                           â”‚
â”‚                                                        â”‚
â”‚  [8-System Coxcomb Chart]    [System Cards Grid]     â”‚
â”‚                                                        â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚       LIFESTYLE PILLARS SECTION                       â”‚
â”‚                                                        â”‚
â”‚  [5-Pillar Coxcomb Chart]    [Pillar Cards Grid]     â”‚
â”‚                                                        â”‚
â”‚                                                        â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                        â”‚
â”‚       DATA COMPLETENESS SECTION                       â”‚
â”‚                                                        â”‚
â”‚  [Progress bar] 47/50 parameters (94%)               â”‚
â”‚                                                        â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 1.2 Layout Regions

**Six Primary Sections (top to bottom):**

1. **Header Bar with Collapse Control**
   - Height: 60-80px
   - Includes back button/collapse icon

2. **Breadcrumb Navigation**
   - Height: 40px
   - Shows navigation path

3. **Overall Score Mini Display**
   - Height: 120px
   - Condensed version of Level 1 hero element

4. **Organ Systems Section**
   - Height: Variable (500-800px)
   - Left: Coxcomb chart
   - Right: System cards grid

5. **Lifestyle Pillars Section**
   - Height: Variable (400-600px)
   - Left: Coxcomb chart
   - Right: Pillar cards grid

6. **Data Completeness Section**
   - Height: 200px
   - Shows assessment coverage

### 1.3 Responsive Behavior

**Desktop (â‰¥1024px):**
- Two-column layout (chart + cards side-by-side)
- Coxcomb charts: 400-500px diameter
- Cards: 2-3 columns grid

**Tablet (768px - 1023px):**
- Single column layout (chart above cards)
- Coxcomb charts: 350px diameter
- Cards: 2 columns grid

**Mobile (â‰¤767px):**
- Single column layout
- Coxcomb charts: 280px diameter
- Cards: 1 column (stacked)
- Collapsible sections

---

## SECTION 2: HEADER & NAVIGATION

### 2.1 Header Components

**Left Side:**
- **Collapse Button** 
  - Icon: Chevron up â†‘ or collapse icon
  - Text: "Back to Overview"
  - Click: Smooth collapse to Level 1
  - Animation: 0.3s ease

**Center:**
- **Patient Name** (smaller than Level 1)
  - Font: Semi-bold, 16px

**Right Side:**
- **Last Updated** (smaller)
  - Font: Regular, 12px, gray
- **Settings Icon**

### 2.2 Breadcrumb Navigation

**Format:** "Health Overview > System Details"

**Interactive:**
- "Health Overview" clickable â†’ collapse to Level 1
- "System Details" = current location (not clickable, bold)

**When in specific system view (Level 3):**
- Format: "Overview > Systems > Cardiovascular"
- Each segment clickable to navigate up

---

## SECTION 3: OVERALL SCORE MINI DISPLAY

### 3.1 Condensed Format

**Horizontal layout:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Overall Health Score: 82 (Good Health)        â”‚
â”‚  [Small progress bar]                          â”‚
â”‚  Bio Age: 45 (Chrono: 48) âœ“                  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Components:**
1. **Score number** (36-48px, color-coded)
2. **Status text** in parentheses
3. **Horizontal progress bar** (not ring) showing 0-100 scale with color zones
4. **Biological age** one-liner with comparison icon

**Purpose:**
- Maintain context while exploring systems
- Quick reference without returning to Level 1
- Smaller footprint to prioritize system details

### 3.2 Interaction

**Click on mini score:**
- Collapses back to Level 1 (same as back button)

**No hover tooltips** (saves space)

---

## SECTION 4: ORGAN SYSTEMS SECTION

### 4.1 Section Header

**Title:** "Your Body Systems"

**Subtitle:** "Each system is scored 0-100 based on structure, function, and risk"

**View Toggle Options (NEW):**
- **Chart View** (default for engaged users): Coxcomb radial chart
- **Bar View** (default for first-time/lower-literacy patients): Horizontal bar chart (worst â†’ best)
- User preference saved per account
- Clinic can configure default view

**Rationale for bar chart option:**
- Radial/coxcomb charts are powerful but cognitively heavy for some patients
- Bar charts more intuitive for comparing magnitudes
- Both views show same data, just different visualizations

### 4.2 8-System Coxcomb Chart

**Visual Design:**

**Radial/spider chart with 8 wedges:**

```
              Neurological
                   â”‚
      Reproductive â”‚ Cardiovascular
           â•²       â”‚       â•±
            â•²      â”‚      â•±
   Immune â”€â”€â”€â”¼â”€â”€â”€â”€â”€â—â”€â”€â”€â”€â”€â”¼â”€â”€â”€ Respiratory
            â•±      â”‚      â•²
           â•±       â”‚       â•²
  Musculoskeletal  â”‚    Metabolic
                   â”‚
                 Renal
```

**Properties:**
- **Center point:** (0,0) = score of 0
- **Outer edge:** Maximum radius = score of 100
- **Each wedge:** Filled to radius = system score
- **Colors:** Match score zones (green/yellow/orange/red)
- **Grid lines:** Concentric circles at 25, 50, 75, 100
- **Labels:** System names around perimeter
- **CRITICAL:** All wedges share same 0-100 radial scale (no per-system rescaling)

**Size:**
- Desktop: 450px diameter
- Tablet: 350px diameter
- Mobile: 280px diameter

**Visual Enhancements:**
- Semi-transparent fill for each wedge
- Solid border line at edge of filled area
- Subtle glow effect for green systems
- Warning icon overlay on orange/red systems

**Accessibility - Textual Summary (NEW):**
- Screen readers announce aggregate first:
  - "Overall, most systems are optimal. Notable concerns in Metabolic and Cardiovascular systems."
- Then announce individual wedges on arrow key navigation
- Prevents need to step through all 8 wedges to get big picture

### 4.2b Alternative View: Horizontal Bar Chart

**When "Bar View" toggle selected:**

```
Renal            â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘ 92 âœ“
Respiratory      â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘ 88 âœ“
Neurological     â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘ 85 âœ“
Immune           â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘ 80 âœ“
Musculoskeletal  â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘ 78 â†’
Cardiovascular   â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘ 68 âš 
Metabolic        â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘ 58 âš 
Reproductive     â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘â–‘â–‘â–‘ 62 âš 

(Systems sorted: Best â†’ Worst or Worst â†’ Best, user toggle)
```

**Format:**
- Horizontal bars (100px width = 100 points)
- System name on left
- Score number on right
- Status icon (âœ“ green, âš  orange/red)
- Color-coded bars match score zones
- Click bar â†’ jump to Level 3 for that system

**Benefits:**
- Easier magnitude comparison
- More familiar to general population
- Screen reader friendly
- Still shows relative health across systems

### 4.3 System Label Positions

**8 cardinal/intercardinal directions:**

1. **Neurological** (Top - 12 o'clock)
2. **Cardiovascular** (Top-right - 1:30)
3. **Respiratory** (Right - 3 o'clock)
4. **Metabolic** (Bottom-right - 4:30)
5. **Renal** (Bottom - 6 o'clock)
6. **Musculoskeletal** (Bottom-left - 7:30)
7. **Immune** (Left - 9 o'clock)
8. **Reproductive/Endocrine** (Top-left - 10:30)

**Label format:**
- System name
- Score number (e.g., "78")
- Color-coded icon

### 4.4 Coxcomb Interactivity

**Hover over wedge:**
- Wedge brightens/highlights
- Tooltip appears with:
  - System name
  - Score (e.g., "Cardiovascular: 78")
  - Status (e.g., "Good health")
  - Domain breakdown: Structure/Function/Risk mini-bars
  - "Click for details"

**Click on wedge:**
- Navigate to Level 3 for that system
- Smooth transition with animation
- Coxcomb fades, system detail expands in

**Keyboard navigation:**
- Tab cycles through wedges clockwise
- Enter opens detail view

### 4.5 System Cards Grid

**Right side of coxcomb (or below on mobile):**

**Grid layout:** 2-3 columns depending on screen width

**Each card shows one system:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  [Icon] Cardiovascular          â”‚
â”‚                                  â”‚
â”‚         Score: 78                â”‚
â”‚         [Mini progress bar]     â”‚
â”‚                                  â”‚
â”‚  Status: Optimal                â”‚
â”‚  Data confidence: High (12/12)  â”‚
â”‚                                  â”‚
â”‚  âœ“ Heart function normal        â”‚
â”‚  âš  Blood pressure elevated      â”‚
â”‚                                  â”‚
â”‚  [View Details â†’]               â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Card Components:**

1. **Header:**
   - System icon (left)
   - System name (bold, 18px)
   - Alert icon if critical/urgent (right)

2. **Score Display:**
   - Large number (36-42px, color-coded)
   - Mini horizontal progress bar below
   - **Status text** (14px) using standardized language:
     - 75-100: "Optimal" or "Excellent" or "Good"
     - 60-74: "Monitor - room to improve"
     - 40-59: "Act soon - needs attention"
     - 0-39: "Urgent - high risk"

3. **Data Confidence Line (NEW):**
   - Format: "Data confidence: High (12/12 parameters)"
   - Thresholds:
     - **High**: â‰¥90% complete
     - **Moderate**: 70-89% complete
     - **Low**: <70% complete
   - Purpose: Surfaces completeness, encourages ordering missing tests
   - Tied to tri-state logic (Numeric/NS/NA from PARAMETER_NORMALIZATION_v2.md)

4. **Quick Insights (2 lines max):**
   - Top positive finding (âœ“ green icon)
   - Top concern (âš  orange/red icon)
   - Plain language, very brief
   - **Derived from TRANSPARENCY_DISPLAY_v1_1.md** top contributors logic for this system
   - Ensures consistent "what matters" messaging across all dashboard levels

5. **Trend Indicator (NEW):**
   - Format: "Score: 78 â†‘ (+5 from last assessment)"
   - Symbols:
     - â†‘ Green: Improved â‰¥3 points
     - â†’ Gray: Stable (within Â±2 points)
     - â†“ Red: Declined â‰¥3 points
   - Time frame: Comparison to most recent previous assessment (typically 3 months)
   - **Source:** Uses **Display Score** from TEMPORAL_SCORING.md (hybrid of point score + stability score)
   - **Critical alignment:** Trend reflects true pattern, not single aberrant readings
   - Comparison uses last two assessments for this system

6. **Action Button:**
   - "View Details" link/button
   - Chevron right icon â†’

**Card Colors:**
- Border: Matches system score zone color
- Background: White or very light tint of zone color
- Drop shadow: Subtle elevation

### 4.6 System Card Interaction

**Hover:**
- Entire card elevates (stronger shadow)
- Background brightens slightly
- Cursor: pointer

**Click anywhere on card:**
- Navigate to Level 3 for that system

**Card Order:**
- Default: By criticality weight (most important systems first)
- User can toggle: By score (worst first) | Alphabetical | Anatomical grouping

### 4.7 Domain Breakdown Display

**Within each system card, show mini-visualization:**

```
Structure (organ integrity)    â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘  72 Monitor
Function (performance)         â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘  82 Optimal
Risk (future complications)    â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘â–‘  56 Act soon
```

**Format:**
- Three horizontal mini-bars
- Each bar: 0-100 scale, 100px width
- **Color-coded by domain score** (green/yellow/orange/red zones)
- **Explicit domain labels** with plain language explanations:
  - "Structure (organ integrity)"
  - "Function (how well it's working now)"
  - "Risk (chance of future problems)"
- Score number on right
- **Status word** after number (Optimal/Monitor/Act soon/Urgent)
- Grayed-out if not measured

**Purpose:**
- Show which aspect of system needs attention
- Maps directly to 24-cell matrix (8 systems Ã— 3 domains)
- Structure/Function/Risk at a glance
- Color + text ensures accessibility

**Alignment with SYSTEM_DOMAIN_SCORING_v2.md:**
- Domain scores calculated as weighted average of parameters
- Each domain follows same 0-100 normalization
- Same color zones apply (75-100 green, etc.)
- Weights: 25% Structure + 50% Function + 25% Risk = System Score

---

## SECTION 5: LIFESTYLE PILLARS SECTION

### 5.1 Section Header

**Title:** "Your Lifestyle Factors"

**Subtitle:** "Subjective health based on your habits and wellbeing"

**Note:** "Based on self-reported questionnaires"

**Pillar Naming Clarification:**

**Canonical Internal Names** (used in scoring/backend):
1. Movement
2. Nutrition
3. Recovery
4. Emotion
5. Environment

**UI Display Names** (shown to patients on dashboard):
1. "Exercise & Movement"
2. "Nutrition"
3. "Sleep & Recovery"
4. "Stress & Emotional Health"
5. "Social & Community"

**Rationale:**
- Internal names maintain conceptual coherence across framework
- UI names are patient-friendly and intuitive
- "Movement" encompasses all physical activity (not just formal exercise)
- "Recovery" includes sleep, rest, and restoration
- "Emotion" covers stress, mental health, resilience
- "Environment" encompasses social connections, community, physical surroundings
- MAP (Meaning-Aspiration-Purpose) remains separate as hero element, NOT a pillar

### 5.2 5-Pillar Coxcomb Chart

**Similar design to systems chart:**

**5 wedges (pentagon shape):**

```
           Nutrition
               â”‚
 Sleep &       â”‚      Exercise &
 Recovery      â”‚      Movement
        â•²      â”‚      â•±
         â•²     â”‚     â•±
          â”¼â”€â”€â”€â”€â—â”€â”€â”€â”€â”¼
         â•±     â”‚     â•²
        â•±      â”‚      â•²
 Stress &      â”‚    Social &
 Emotional     â”‚    Community
```

**Properties:**
- Same visual design as system chart
- 5 wedges instead of 8 (pentagon)
- Regular pentagon shape
- Same color coding and interactivity
- Same 0-100 radial scale (no rescaling)

**Pillar Positions (clockwise from top):**
1. **Nutrition** (Top - 12 o'clock)
2. **Exercise & Movement** (Top-right - 2 o'clock)
3. **Social & Community** (Bottom-right - 4 o'clock)
4. **Stress & Emotional Health** (Bottom-left - 8 o'clock)
5. **Sleep & Recovery** (Top-left - 10 o'clock)

### 5.3 Pillar Cards Grid

**Same format as system cards:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  [Icon] Exercise & Movement       â”‚
â”‚                                   â”‚
â”‚         Score: 65                 â”‚
â”‚         [Mini progress bar]       â”‚
â”‚                                   â”‚
â”‚  Status: Monitor - room to improveâ”‚
â”‚                                   â”‚
â”‚  Strengths: Daily walking habit   â”‚
â”‚  Improve: Add strength training   â”‚
â”‚                                   â”‚
â”‚  Last updated: Oct 15, 2025       â”‚
â”‚  âš  Update recommended (>90 days)  â”‚
â”‚                                   â”‚
â”‚  [Update Assessment â†’]            â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Key Differences from System Cards:**

1. **Action button text:** "Update Assessment" (not "View Details")
   - Click: Opens lifestyle questionnaire modal
   - Pre-filled with previous responses
   
2. **Quick insights format:**
   - "Strengths:" (what's going well)
   - "Improve:" (specific recommendation)

3. **Last Updated indicator with staleness warnings (ENHANCED):**
   - "Last updated: [Date]"
   - **90-180 days old**: "âš  Update recommended"
   - **>180 days old**: "ðŸ”´ Data outdated - please update"
   - **Score influence adjustment:**
     - Data >180 days: Down-weight influence by 50% in overall calculation
     - User notification: "This pillar has reduced impact due to data age"
     - Rationale: Old subjective data less reliable than recent objective tests
   - Tied to COMPOSITE_SCORING_v2.md completeness governance

4. **Completeness indicator:**
   - "Questionnaire: 8/10 questions answered (80%)"
   - Incomplete questionnaires flagged
   - Missing questions highlighted when reopening

### 5.4 Pillar Interaction

**Click on pillar card:**
- Opens lifestyle questionnaire modal
- Pre-filled with previous responses
- Can update responses
- Saves and recalculates scores immediately

**No Level 3 detail view for pillars** (subjective data, no parameters to drill into)

---

## SECTION 6: CRITICAL ALERTS IN LEVEL 2

### 6.1 System-Level Alerts

**If system has critical parameters:**

**Alert badge on system card:**
```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  ðŸ”´ Cardiovascular              â”‚
â”‚                                  â”‚
â”‚  2 Critical Issues Detected     â”‚
â”‚                                  â”‚
â”‚  â€¢ Blood pressure critically highâ”‚
â”‚  â€¢ Troponin elevated             â”‚
â”‚                                  â”‚
â”‚  [Review Now]                    â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Visual treatment:**
- Red border (thick, 3-4px)
- Red alert icon in header
- Alert badge count
- Brief list of critical parameters
- Prominent action button

**CRITICAL SAFETY RULE - Visual Override (NEW):**

**If ANY parameter in a system is critical or urgent, the system card's visual treatment overrides the numeric score color:**

**Example Scenario:**
- Cardiovascular System Score: 72 (would normally be yellow/green)
- BUT Troponin is CRITICAL (red alert)
- **Card displays:** RED BORDER + RED ALERT ICON + "ðŸ”´ Critical"
- Score still shows "72" but visual screams emergency

**Override Rules:**
1. **Any Critical parameter** â†’ Card border/icon = RED, regardless of system score
2. **Any Urgent parameter** (no critical) â†’ Card border/icon = ORANGE, regardless of system score
3. **No critical/urgent parameters** â†’ Card follows normal score color (green/yellow/orange/red based on system score)

**Purpose:**
- Prevents composite "good" score from masking life-threatening parameters
- Visual safety net: critical findings always prominent
- Aligns with "Critical Safety First" principle

**Sort order:**
- Systems with critical alerts always displayed first
- Then by number of alerts
- Then by system score

### 6.2 Alert Summary Banner

**Above organ systems section:**

**If any critical alerts exist:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  âš ï¸ 3 Systems Require Immediate Attention        â”‚
â”‚                                                   â”‚
â”‚  â€¢ Cardiovascular: 2 critical parameters         â”‚
â”‚  â€¢ Renal: 1 critical parameter                   â”‚
â”‚  â€¢ Metabolic: 1 urgent parameter                 â”‚
â”‚                                                   â”‚
â”‚  [View All Alerts]  [Contact Clinician]         â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Color:** Red background for critical, Orange for urgent

**Interaction:**
- "View All Alerts" â†’ Opens alerts modal with full details
- "Contact Clinician" â†’ Opens contact options (call, message, portal)

---

## SECTION 7: DATA COMPLETENESS SECTION

### 7.1 Visual Display

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Assessment Completeness                           â”‚
â”‚                                                     â”‚
â”‚  [â–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–ˆâ–‘â–‘â–‘â–‘] 47/50 (94%)           â”‚
â”‚                                                     â”‚
â”‚  You've completed 94% of recommended assessments  â”‚
â”‚                                                     â”‚
â”‚  Missing assessments:                              â”‚
â”‚  â€¢ Vitamin D level                                 â”‚
â”‚  â€¢ DEXA bone density scan                         â”‚
â”‚  â€¢ VO2 max cardiopulmonary test                   â”‚
â”‚                                                     â”‚
â”‚  [Schedule Missing Tests]                          â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### 7.2 Components

**Progress bar:**
- Width: 100% of section
- Height: 24px
- Filled: Green (#059669)
- Empty: Light gray (#E5E7EB)
- Text overlay: "47/50 (94%)"

**Status interpretation:**
- 90-100%: "Excellent assessment coverage" (green)
- 75-89%: "Good coverage, some gaps" (yellow)
- 50-74%: "Fair coverage, important tests missing" (orange)
- <50%: "Limited data - complete assessment recommended" (red)

**Missing assessments list:**
- Show up to 5 missing parameters
- Grouped by type (labs, imaging, functional tests)
- Brief name only (not technical jargon)

**Action button:**
- "Schedule Missing Tests" â†’ Opens test ordering interface or clinic contact

### 7.3 Completeness by System

**Expandable breakdown:**

**Click "Show by System":**

```
System Completeness:
â€¢ Cardiovascular: 12/12 (100%) âœ“
â€¢ Metabolic: 8/9 (89%) 
â€¢ Renal: 4/4 (100%) âœ“
â€¢ Respiratory: 3/5 (60%) âš 
â€¢ Neurological: 5/5 (100%) âœ“
...
```

**Purpose:**
- Identify which systems have data gaps
- Prioritize which tests to order
- Understand scoring confidence by system

---

## SECTION 8: HISTORICAL TRENDS

### 8.1 System Score Trends

**Optional expandable section:**

**"View Score History" button**

**Expands to show:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  System Scores Over Time                        â”‚
â”‚                                                  â”‚
â”‚  [Line graph]                                   â”‚
â”‚  3-4 system lines displayed by default         â”‚
â”‚  X-axis: Time (last 6-12 months)               â”‚
â”‚  Y-axis: Score (0-100)                         â”‚
â”‚                                                  â”‚
â”‚  Legend:                                        â”‚
â”‚  â”€â”€â”€ Cardiovascular (declining â†“)  âœ“ visible   â”‚
â”‚  â”€â”€â”€ Metabolic (improving â†‘)       âœ“ visible   â”‚
â”‚  â”€â”€â”€ Renal (stable â†’)              âœ“ visible   â”‚
â”‚  â”€â”€â”€ Respiratory                   â˜ hidden    â”‚
â”‚  â”€â”€â”€ [toggle other systems]        â˜ hidden    â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Default Display Logic (NEW):**

**Show 3-4 systems automatically (prioritized by):**
1. **Systems with critical/urgent alerts** (always shown)
2. **Systems with largest recent changes** (|Î”| â‰¥ 10 points in last 3 months)
3. **Systems with highest risk scores** (Risk domain <60)
4. **Systems specified by clinician** (if flagged for monitoring)

**Purpose:** 
- Prevents visual clutter (8 lines too busy)
- Focuses on clinically important trends
- User can toggle other systems on/off via legend

**Temporal Alignment (CRITICAL):**

**System trend lines reflect Display Scores from TEMPORAL_SCORING.md:**
- **NOT raw point scores** (which can be noisy)
- Uses **Display Score** = hybrid of point score + stability score
- Already integrates temporal smoothing at parameter level
- Ensures trends show true patterns, not aberrant readings

**Example:**
- Single aberrant BP reading doesn't create false "decline" in cardiovascular trend
- Trend shows underlying pattern after temporal smoothing applied

**Features:**
- Toggle systems on/off (click legend items)
- Hover over line shows exact Display Score and date
- Trend indicators: â†‘â†“â†’ (improving/declining/stable)
- Compare current to 3, 6, 12 months ago
- Annotations: Mark interventions (started medication, lifestyle change)

### 8.2 Trend Indicators on Cards

**Each system card shows trend:**

```
Score: 78 â†‘ (+5 from last assessment)
```

**Trend symbols:**
- â†‘ Green: Improved â‰¥5 points
- â†’ Gray: Stable (within Â±4 points)
- â†“ Red: Declined â‰¥5 points

**Time frame:** Comparison to last assessment (default 3 months)

**Source Alignment (CRITICAL):**

**Trend comparison uses Display Scores from TEMPORAL_SCORING.md:**
- Compares **Display Score** (hybrid of point + stability) for last two assessments
- **NOT raw point scores** which can be volatile
- Ensures trend indicators reflect true system trajectory
- Single aberrant parameter reading won't falsely show "declining"

**Example:**
- Last assessment (3 months ago): Cardiovascular Display Score = 73
- Current assessment: Cardiovascular Display Score = 78
- **Trend shown:** â†‘ (+5 points)
- Even if one parameter spiked today, smoothing prevents false negative trend

**Formula:**
```
Trend_Change = Current_Display_Score - Previous_Display_Score
```

**Display Logic:**
- If Trend_Change â‰¥ +5: Show â†‘ green "Improving"
- If -4 â‰¤ Trend_Change â‰¤ +4: Show â†’ gray "Stable"
- If Trend_Change â‰¤ -5: Show â†“ red "Worsening"

---

## SECTION 9: SYSTEM COMPARISON FEATURES

### 9.1 Sort & Filter Options

**Toolbar above system cards:**

**Sort by:**
- Critical alerts first (default)
- Score (worst to best)
- Score (best to worst)
- Alphabetical
- Anatomical grouping
- Recent changes (biggest declines first)

**Filter by:**
- Show all (default)
- Problems only (red/orange)
- Good health only (green)
- Recently changed (trend â‰  â†’)

**CRITICAL SAFETY RULE - Filter Override (NEW):**

**Filters and sorting NEVER hide systems with critical or urgent alerts:**

**Example Scenarios:**
1. User selects "Good health only" filter (green systems)
2. Cardiovascular system has score 78 (green) BUT troponin is critical (red alert)
3. **Result:** Cardiovascular system REMAINS VISIBLE with prominent red visual treatment
4. Other yellow/orange/red systems without alerts are hidden as expected

**Filter Behavior:**
- **"Good health only":** Shows green systems + ANY system with critical/urgent alerts (pinned at top)
- **"Problems only":** Shows orange/red systems + ALL systems with critical/urgent alerts
- **"Recently changed":** Shows changed systems + ALL systems with critical/urgent alerts

**Visual Treatment of Pinned Systems:**
- Clear indicator: "âš  Pinned - Critical Alert" badge
- Red/orange border overrides normal color
- Cannot be dismissed or filtered away
- Remains at top of list regardless of sort order

**Purpose:**
- Prevents user from accidentally filtering away life-threatening findings
- "Critical Safety First" principle enforced in UI behavior
- Aligns with CRITICAL_ALERTS_v1_1.md hierarchy

**Implementation Note for IT:**
- Filter logic: `(system matches filter) OR (system has critical/urgent alerts)`
- Alert systems always pass through filters

### 9.2 Comparison View

**Toggle: "Compare Systems Side-by-Side"**

**Activates 2-3 system comparison:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ Cardiovascularâ”‚ Respiratory  â”‚ Metabolic    â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚ Score: 68    â”‚ Score: 92    â”‚ Score: 72    â”‚
â”‚ Status: Fair â”‚ Status: Exc. â”‚ Status: Good â”‚
â”‚              â”‚              â”‚              â”‚
â”‚ Structure: 70â”‚ Structure: 95â”‚ Structure: 88â”‚
â”‚ Function: 72 â”‚ Function: 94 â”‚ Function: 68 â”‚
â”‚ Risk: 62     â”‚ Risk: 88     â”‚ Risk: 65     â”‚
â”‚              â”‚              â”‚              â”‚
â”‚ [Details]    â”‚ [Details]    â”‚ [Details]    â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜

[+ Add System to Compare]
```

**Use cases:**
- Compare related systems (cardio + respiratory)
- Track improvement in targeted systems
- Understand interdependencies

---

## SECTION 10: MOBILE OPTIMIZATIONS

### 10.1 Mobile-Specific Layout

**On screens <768px:**

**Tabbed interface:**
```
[Systems] [Pillars] [Completeness]
   (tabs at top)

[Active tab content below]
```

**Systems tab:**
- Coxcomb chart (smaller, 240px)
- System cards (1 column, stacked)
- Swipe gesture to navigate cards

**Pillars tab:**
- Pillar chart
- Pillar cards

**Completeness tab:**
- Progress bar
- Missing tests list

### 10.2 Mobile Interactions

**Swipe gestures:**
- Swipe left/right on cards: Navigate between systems
- Swipe up on card: Open detail view (Level 3)
- Swipe down from top: Collapse to Level 1

**Touch targets:**
- Minimum 44px Ã— 44px
- Adequate spacing between interactive elements

**Scrolling:**
- Smooth scroll with momentum
- Sticky header (stays at top while scrolling)

---

## SECTION 11: ANIMATIONS & TRANSITIONS

### 11.1 Transition from Level 1 to Level 2

**Expand animation:**
- Duration: 0.4 seconds
- Easing: ease-out
- Sequence:
  1. Level 1 score shrinks and moves to top
  2. Coxcomb charts fade in and grow
  3. System cards slide up from bottom
  4. Stagger: 0.05s delay between each card

### 11.2 Coxcomb Animation

**On initial load:**
- Wedges draw from center outward
- Duration: 0.8 seconds
- Stagger: 0.1s between each wedge
- Easing: ease-in-out

**On score update:**
- Wedges animate to new size
- Duration: 0.6 seconds
- Color transitions smoothly if zone changes

### 11.3 Card Interactions

**Hover:**
- Elevation increases over 0.2s
- Subtle scale: 1.02x

**Click:**
- Scale down briefly (0.98x) for 0.1s
- Then transition to Level 3

---

## SECTION 12: ACCESSIBILITY

### 12.1 Keyboard Navigation

**Tab order:**
1. Collapse button
2. Overall score mini display
3. System coxcomb wedges (clockwise)
4. System cards (left-to-right, top-to-bottom)
5. Pillar coxcomb wedges
6. Pillar cards
7. Completeness section elements

**Enter/Space:**
- Activates focused element
- Opens Level 3 for systems
- Opens questionnaire for pillars

**Arrow keys:**
- Navigate between coxcomb wedges
- Up/Down: Previous/Next wedge
- Left/Right: Same as Up/Down

### 12.2 Screen Reader Support

**Coxcomb chart:**
- Announce: "System health visualization. Use arrow keys to explore each system."
- For each wedge: "Cardiovascular system: Score 78, Good health. Press Enter for details."

**System cards:**
- Announce: "Cardiovascular system card. Score 78. Good health. Heart function normal. Blood pressure elevated. Activate to view details."

**Section headers:**
- ARIA landmark: `<section aria-label="Organ Systems">`

### 12.3 Visual Accessibility

**Color blindness support:**
- Patterns overlay on coxcomb wedges (not just color)
- Icons supplement color coding
- Text labels always present
- Red/green not used as only differentiator

**Contrast:**
- All text â‰¥4.5:1 contrast ratio
- Interactive elements â‰¥3:1

**Font sizes:**
- Minimum 14px for body text
- Scalable without breaking layout

---

## SECTION 13: PERFORMANCE REQUIREMENTS

### 13.1 Load Time

**Initial render:**
- Overall score mini: <0.5s
- Coxcomb charts: <1s
- All system cards: <1.5s
- Complete interactive: <2s

### 13.2 Interaction Response

**Hover effects:** <50ms
**Click to Level 3:** <200ms
**Collapse to Level 1:** <300ms
**Score recalculation:** <2s

### 13.3 Optimization Strategies

- Lazy load trend graphs (only when expanded)
- Cache coxcomb SVG renders
- Throttle hover events
- Debounce search/filter inputs
- Virtual scrolling for long card lists (if >20 systems in future)

---

## SECTION 14: CLINICAL VALIDATION CHECKLIST

### 14.1 Before Launch

**Clinical Accuracy:**
- â˜ System scores calculate per SYSTEM_DOMAIN_SCORING_v2.md
- â˜ Domain breakdowns accurate
- â˜ Top contributors match TRANSPARENCY_DISPLAY_v1_1.md
- â˜ Critical alerts match CRITICAL_ALERTS_v1_1.md
- â˜ Plain language appropriate and accurate

**User Experience:**
- â˜ Users can identify problem systems in <30s
- â˜ Coxcomb chart intuitive (tested with patients)
- â˜ Card sorting/filtering improves usability
- â˜ Navigation to Level 3 obvious
- â˜ Mobile experience functional

**Technical:**
- â˜ Calculations match specifications
- â˜ Data refresh reliable
- â˜ Animations smooth (60fps)
- â˜ Accessibility compliant (WCAG AA)
- â˜ Performance targets met

---

## SECTION 15: EXAMPLE SCENARIOS

### 15.1 Healthy Active Adult (Age 35)

**System Scores:**
- Cardiovascular: 92 (green)
- Respiratory: 94 (green)
- Metabolic: 88 (green)
- Renal: 91 (green)
- Neurological: 89 (green)
- Musculoskeletal: 85 (green)
- Immune: 86 (green)
- Reproductive: 87 (green)

**Coxcomb appearance:**
- Large, symmetrical shape (all wedges near max)
- All green coloring
- Visually balanced

**User experience:**
- Positive reinforcement
- Focus on maintenance
- No critical alerts
- Completeness: 96%

### 15.2 Middle-Aged with Metabolic Concerns (Age 52)

**System Scores:**
- Cardiovascular: 68 (yellow) â†“
- Respiratory: 82 (green)
- Metabolic: 58 (orange) âš 
- Renal: 75 (green)
- Neurological: 80 (green)
- Musculoskeletal: 72 (yellow)
- Immune: 78 (green)
- Reproductive: 71 (yellow)

**Coxcomb appearance:**
- Irregular shape (metabolic wedge noticeably small)
- Mixed colors (mostly green/yellow, one orange)
- Visual imbalance draws attention to metabolic

**Alerts:**
- 1 Urgent: HbA1c 8.2% (metabolic)
- Warning badge on Metabolic card

**User experience:**
- Clear focus area: Metabolic system
- Actionable: "Review Now" prominent
- Encouraging: Most systems healthy

### 15.3 Elderly with Multiple Conditions (Age 78)

**System Scores:**
- Cardiovascular: 52 (orange) âš 
- Respiratory: 65 (yellow)
- Metabolic: 58 (orange) âš 
- Renal: 42 (orange) ðŸ”´
- Neurological: 72 (yellow)
- Musculoskeletal: 48 (orange)
- Immune: 68 (yellow)
- Reproductive: 70 (yellow)

**Coxcomb appearance:**
- Small, very irregular shape
- Predominantly orange/yellow
- Multiple systems below target

**Alerts:**
- 2 Critical parameters (renal)
- 4 Urgent parameters (cardio, metabolic)
- Alert banner prominent

**User experience:**
- Multiple focus areas identified
- Prioritized by severity (renal first)
- Not overwhelming due to clear organization
- Clear action steps per system

---

## SECTION 16: IMPLEMENTATION NOTES

### 16.1 Coxcomb Chart Technology

**Recommended library:**
- D3.js or Chart.js for SVG rendering
- Alternatively: HTML Canvas for better performance
- Must support interactive hover/click

**Data structure:**
```javascript
systems: [
  {
    name: "Cardiovascular",
    score: 78,
    color: "#D97706", // Yellow zone
    status: "Good health",
    domains: {
      structure: 82,
      function: 76,
      risk: 75
    },
    alertCount: 0
  },
  // ... 7 more systems
]
```

### 16.2 Card Component

**Reusable React/Vue component:**
- Props: system data, interactive callbacks
- State: hover, expanded
- Events: onClick, onHover

**Modularity:**
- Easy to reorder
- Easy to filter/sort
- Can be used in other views

### 16.3 Real-Time Updates

**When new data arrives:**
1. Fade out affected cards
2. Recalculate scores
3. Animate coxcomb to new shape
4. Fade cards back in with new values
5. Show toast notification: "Scores updated with latest results"

---

## SECTION 17: FUTURE ENHANCEMENTS

### 17.1 Phase 2 Features

**System comparisons:**
- Side-by-side comparison tool
- Historical overlay (compare current to past)

**Predictive insights:**
- "If you improve metabolic by 10 points, overall score would increase to 84"
- Simulation mode

**Social sharing:**
- "Share progress with care team"
- Privacy-respecting exports

### 17.2 Advanced Visualizations

**Alternative chart types:**
- Bar chart view (for users who prefer linear)
- Heatmap grid (8x3 cells for systemsÃ—domains)
- Sankey diagram (showing how parameters flow into systems)

**Customization:**
- User can choose chart type
- Save preferences

---

## SECTION 18: SUMMARY

### 18.1 Key Features

**Level 2 System Overview provides:**
1. âœ… Visual comparison of 8 organ systems via coxcomb chart
2. âœ… Quick identification of problem areas
3. âœ… Individual system cards with scores and insights
4. âœ… Domain breakdown (Structure/Function/Risk) per system
5. âœ… Lifestyle pillar assessment and updating
6. âœ… Data completeness tracking
7. âœ… System-level critical alerts
8. âœ… Clear navigation to Level 3 details

### 18.2 Success Criteria

**A successful Level 2 view means:**
- Users can identify which system(s) need attention in <20 seconds
- Coxcomb chart immediately communicates health balance/imbalance
- System cards provide enough detail to triage without overwhelming
- Critical alerts cannot be missed
- Navigation to Level 3 is intuitive and purposeful
- Works seamlessly on all device sizes

### 18.3 Integration Points

**Level 2 sits between:**
- **Level 1 (Hero):** High-level overview â†’ Expands into system breakdown
- **Level 3 (Detail):** System selection â†’ Drills into parameter analysis

**Data dependencies:**
- SYSTEM_DOMAIN_SCORING_v2.md calculations
- TRANSPARENCY_DISPLAY_v1_1.md top contributors
- CRITICAL_ALERTS_v1_1.md alert logic
- Parameter data from all PARAMETERS_*.md files (when complete)

---

**END OF DASHBOARD LEVEL 2 SPECIFICATION**

*This document defines the system overview interface that bridges high-level health status and detailed parameter analysis. All specifications align with clinical logic defined in core framework documents.*
