# TEMPORAL SCORING SPECIFICATION
## Patient Health Dashboard - Parameter Scoring Framework

**Document Type:** Core Clinical Logic  
**Version:** 1.0.0  
**Date:** November 12, 2025  
**Status:** Foundation Document - Part 4 of 4  
**Author:** Clinical Design Team

---

## RELATED DOCUMENTS

This document is part of the **Parameter Scoring Framework** (read all four together):

1. `PARAMETER_NORMALIZATION.md` - Core normalization methods and formulas
2. `CALIBRATION_VALIDATION.md` - How to calibrate and validate parameters
3. `CONTEXT_RULES.md` - Patient-specific scoring adjustments and overrides
4. **TEMPORAL_SCORING.md** (this document) - Handling measurements over time

---

## DOCUMENT PURPOSE

This specification defines how to **handle serial measurements over time** to prevent single aberrant values from inappropriately affecting scores and to incorporate trend information into scoring and display.

**The temporal problem:**
- Patient's BP usually 125/80, one reading 155/95 (anxious at appointment) â†’ Should score reflect single high reading or typical pattern?
- HbA1c drops from 9.5% to 7.2% â†’ Improvement trend should be acknowledged
- Troponin rising 0.02 â†’ 0.05 â†’ 0.12 over 6 hours â†’ Trend matters more than absolute value

**This document provides:**
1. Point score vs stability score framework
2. Temporal smoothing methods (EMA, median filtering)
3. Aberrant value detection and handling
4. Trend indicators and interpretation
5. Parameter-specific temporal strategies

---

## CORE CONCEPTS

### Point Score vs Stability Score

**Point Score:** Normalized score of the most recent measurement
- Reflects current state
- Sensitive to acute changes
- May be volatile

**Stability Score:** Smoothed score incorporating recent measurement history
- Reflects typical/average state
- More resistant to single outliers
- Better for chronic monitoring

**Display Score:** Weighted combination of point and stability, depending on clinical context

### When to Use Each

**Use Point Score for:**
- Acute parameters (troponin, glucose in ER, BP during crisis)
- First measurement (no history available)
- Rapidly changing clinical situations
- Parameters where every reading matters

**Use Stability Score for:**
- Chronic parameters (HbA1c, lipids, eGFR)
- Home monitoring with frequent readings (daily BP)
- Establishing baseline patterns
- Reducing alert fatigue

**Use Hybrid (weighted combination) for:**
- Vital signs in outpatient setting
- Parameters with moderate volatility
- Transitioning from acute to chronic management

---

## METHOD 1: EXPONENTIAL MOVING AVERAGE (EMA)

### Overview

**EMA** gives more weight to recent values while incorporating historical trend.

**Formula:**
```
EMA_new = Î± Ã— Score_current + (1 - Î±) Ã— EMA_previous

where:
- Î± = smoothing factor (0 < Î± â‰¤ 1)
- Higher Î± = more weight on current value (less smoothing)
- Lower Î± = more weight on history (more smoothing)
```

### Smoothing Factor Selection

**Î± = 1.0:** No smoothing (Point Score only)
- Use for: First measurement, acute parameters

**Î± = 0.5:** Moderate smoothing
- Use for: Vital signs, moderately volatile parameters
- Current reading contributes 50%, history 50%

**Î± = 0.3:** Substantial smoothing
- Use for: Home BP monitoring, frequent measurements
- Current reading contributes 30%, history 70%

**Î± = 0.2:** Heavy smoothing
- Use for: Chronic labs, establishing baseline
- Current reading contributes 20%, history 80%

**Clinical decision:** Choose Î± based on measurement frequency and clinical volatility.

### Worked Example: Home Blood Pressure Monitoring

**Patient monitors BP daily, 7 readings:**

| Day | SBP | Point Score | EMA (Î±=0.3) |
|-----|-----|-------------|-------------|
| 1 | 125 | 78 | 78 (initial) |
| 2 | 130 | 73 | 0.3Ã—73 + 0.7Ã—78 = 77 |
| 3 | 122 | 82 | 0.3Ã—82 + 0.7Ã—77 = 78 |
| 4 | 152 | 38 | 0.3Ã—38 + 0.7Ã—78 = 66 |
| 5 | 128 | 75 | 0.3Ã—75 + 0.7Ã—66 = 69 |
| 6 | 126 | 77 | 0.3Ã—77 + 0.7Ã—69 = 71 |
| 7 | 124 | 79 | 0.3Ã—79 + 0.7Ã—71 = 73 |

**Analysis:**
- Day 4: Spike to 152 (anxious reading?) â†’ Point Score 38, but EMA only drops to 66
- EMA smooths the spike, reflecting that most readings are controlled
- Display Score on Day 4: Could show EMA (66) with note "Latest reading high, overall trend good"

**Advantage:** Single bad reading doesn't crater overall assessment.

---

## METHOD 2: MEDIAN FILTERING

### Overview

**Median filter** uses the median of the last N measurements, completely resistant to outliers.

**Formula:**
```
Stability_Score = median([Score_1, Score_2, ..., Score_N])

where N = window size (typically 3-5 most recent readings)
```

### Window Size Selection

**N = 3:** Minimal smoothing
- Median of last 3 readings
- Quick to adapt to true changes
- Some outlier protection

**N = 5:** Moderate smoothing
- Median of last 5 readings
- Good balance between responsiveness and stability
- Recommended for most parameters

**N = 7:** Heavy smoothing
- Median of last 7 readings
- Establishes robust baseline
- Slow to reflect true changes

### Worked Example: Home Blood Pressure (Same Data)

| Day | SBP | Point Score | Median (N=5) |
|-----|-----|-------------|--------------|
| 1 | 125 | 78 | 78 (only 1 value) |
| 2 | 130 | 73 | median(78,73) = 76 |
| 3 | 122 | 82 | median(78,73,82) = 78 |
| 4 | 152 | 38 | median(78,73,82,38) = 76 |
| 5 | 128 | 75 | median(78,73,82,38,75) = 75 |
| 6 | 126 | 77 | median(73,82,38,75,77) = 75 |
| 7 | 124 | 79 | median(82,38,75,77,79) = 77 |

**Analysis:**
- Day 4 spike completely ignored by median (38 is outlier)
- Median stays 75-78 throughout (reflects typical state)
- More resistant to outliers than EMA

**Advantage:** Complete outlier rejection. **Disadvantage:** Slower to detect true worsening trends.

---

## METHOD 3: HYBRID APPROACH (RECOMMENDED)

### Overview

Combine Point and Stability for optimal clinical utility:

```
Display_Score = w_point Ã— Point_Score + w_stability Ã— Stability_Score

where w_point + w_stability = 1
```

### Weighting Strategies by Parameter Type

**ACUTE Parameters (70% Point, 30% Stability):**
- Troponin, lactate, critical vitals in ER
- Emphasize current state
- History provides context but doesn't override

**DYNAMIC Parameters (50% Point, 50% Stability):**
- BP in outpatient, glucose monitoring
- Balance current reading with typical pattern
- Standard approach for most vital signs

**CHRONIC Parameters (30% Point, 70% Stability):**
- HbA1c, lipids, eGFR, tumor markers
- Emphasize established trend
- Single reading less influential

**STABLE Parameters (20% Point, 80% Stability):**
- Home monitoring with daily readings
- Baseline well-established
- Focus on detecting true changes

### Worked Example: Outpatient Blood Pressure (50/50 Hybrid)

Using Day 7 from previous examples:

```
Point_Score = 79
EMA_Score = 73

Display_Score = 0.5 Ã— 79 + 0.5 Ã— 73 = 76

Color: YELLOW (borderline, watch)
Interpretation: "Your latest reading (124 mmHg) is good. Overall trend this week is well-controlled."
```

**Benefits:**
- Acknowledges current good reading (point score 79)
- Reflects that one spike occurred (stability score 73)
- Fair assessment (display score 76)
- Provides both current and trend information

---

## ABERRANT VALUE DETECTION

### Criteria for Flagging Aberrant Values

**Statistical outliers:**
- Value >3 SD from patient's recent mean
- Value >2.5 IQR from patient's recent median

**Physiologically implausible:**
- BP 250/180 (measurement error likely)
- Glucose 28 mg/dL in non-diabetic (lab error likely)
- Potassium 8.2 without symptoms (hemolyzed sample likely)

**Contextual outliers:**
- Single very different reading in otherwise stable series
- Inconsistent with patient's known condition

### Handling Aberrant Values

**Step 1: Flag for Review**
```
IF value meets aberrant criteria:
  Mark as "Possible aberrant reading - verification recommended"
  Do NOT hide from clinician
  Do NOT automatically exclude from calculations
```

**Step 2: Reduce Influence on Stability Score**
```
IF flagged aberrant:
  Use median filter (resistant to outliers)
  OR reduce weight in EMA calculation
  OR calculate stability with and without the value
```

**Step 3: Display with Context**
```
Show both:
- Point Score (includes aberrant value) with warning icon
- Stability Score (minimizes aberrant influence)

Example display:
"Latest reading: 152 mmHg (Score 38 âš  Unusually high for you)
Your typical range: 122-130 mmHg (Score 75-78)"
```

**Step 4: Recommend Repeat**
```
IF aberrant AND clinically significant:
  Interpretation: "This reading is unusual for you. Please recheck."
```

### Aberrant vs True Worsening

**Distinguishing features:**

| Feature | Aberrant | True Worsening |
|---------|----------|----------------|
| **Pattern** | Single outlier | Progressive trend |
| **Repeatability** | Not reproducible | Consistent on recheck |
| **Clinical context** | No symptoms/changes | Symptoms or known cause |
| **Related parameters** | Others normal | Multiple parameters affected |

**Example - Aberrant:**
- BP readings: 122, 125, 124, 168, 126, 123
- 168 is isolated outlier
- Patient felt fine
- Recheck: 125

**Example - True Worsening:**
- BP readings: 128, 135, 142, 148, 155
- Progressive upward trend
- Patient reports headaches
- Medication non-adherence identified

---

## TREND INDICATORS

### Trend Calculation

**Simple trend (last 3-5 readings):**
```
IF all readings increasing: â†‘ Rising
ELSE IF all readings decreasing: â†“ Falling
ELSE IF relatively stable (within 10%): â†’ Stable
ELSE: â†• Variable
```

**Slope-based trend (regression):**
```
Fit linear regression to last N scores
IF slope > +5 points per reading: â†‘â†‘ Rapidly rising
ELSE IF slope > +2: â†‘ Rising
ELSE IF slope > -2: â†’ Stable
ELSE IF slope > -5: â†“ Falling
ELSE: â†“â†“ Rapidly falling
```

### Trend Display

**Visual indicators:**
- Arrow direction (â†‘â†“â†’)
- Sparkline of recent values
- Color-coded: Green â†“ for improving, Red â†‘ for worsening

**Text interpretation:**
```
"Trend: â†‘ Rising (Last 3 readings: 125, 135, 145 mmHg)"
"Trend: â†“ Improving (Last 3 HbA1c: 8.5%, 7.8%, 7.2%)"
"Trend: â†’ Stable (Consistently 122-128 mmHg this week)"
```

### Clinical Significance of Trends

**Worsening trend overrides good point score:**
```
IF trend = â†‘â†‘ Rapidly rising:
  Even if current score GREEN: Flag as YELLOW with warning
  "Your latest value is normal, but it's been rising rapidly. Monitor closely."
```

**Improving trend provides encouragement:**
```
IF trend = â†“ Improving:
  Even if current score ORANGE: Add positive note
  "Your value is still elevated, but trending in the right direction. Keep up the good work!"
```

---

## PARAMETER-SPECIFIC STRATEGIES

### Strategy Matrix

| Parameter | Point/Stability Weight | Smoothing Method | Window Size | Rationale |
|-----------|------------------------|------------------|-------------|-----------|
| **Troponin** | 90/10 | EMA | Î±=0.8 | Current value critical, trend secondary |
| **BP (Office)** | 70/30 | EMA | Î±=0.5 | Current reading primary, history context |
| **BP (Home)** | 30/70 | Median | N=5 | Many readings, establish baseline |
| **Glucose (ER)** | 100/0 | None | N/A | Every reading matters acutely |
| **Glucose (Home)** | 40/60 | EMA | Î±=0.3 | Frequent readings, reduce noise |
| **HbA1c** | 40/60 | EMA | Î±=0.4 | Slow-changing, trend important |
| **LDL** | 30/70 | Median | N=3 | Stable, occasional labs |
| **Creatinine** | 40/60 | EMA | Î±=0.4 | GFR derived, trend critical |
| **eGFR** | 30/70 | Median | N=5 | Establish CKD progression rate |
| **Weight** | 20/80 | EMA | Î±=0.2 | Daily fluctuations, long-term trend matters |

### Example: HbA1c Temporal Strategy

**Measurement frequency:** Every 3 months (quarterly)

**Scoring approach:**
```
Point Score: Current HbA1c normalized score
Stability Score: EMA with Î±=0.4

Display Score = 0.4 Ã— Point + 0.6 Ã— EMA

Trend: Calculate slope over last 4 readings (1 year)
```

**Scenario: Patient improving diabetes control**

| Date | HbA1c | Point Score | EMA | Display (40/60) | Trend |
|------|-------|-------------|-----|-----------------|-------|
| Jan | 9.5% | 28 | 28 | 28 | - |
| Apr | 8.2% | 48 | 0.4Ã—48+0.6Ã—28 = 36 | 36 | â†“ |
| Jul | 7.8% | 58 | 0.4Ã—58+0.6Ã—36 = 45 | 45 | â†“ |
| Oct | 7.2% | 68 | 0.4Ã—68+0.6Ã—45 = 54 | 54 | â†“ |

**Display on October visit:**
```
HbA1c: 7.2%
Score: 54 (YELLOW - still needs improvement)
Trend: â†“ Significantly improving! (Down from 9.5% in January)

Interpretation:
"Your diabetes control is improving steadily. You've dropped from 9.5% to 7.2% this year - excellent progress! Continue working toward your target of 7.0%."
```

**Why this works:**
- Point score (68) acknowledges current improvement
- Stability score (54) reflects that still below optimal
- Trend (â†“) provides motivation
- Display score (54 YELLOW) is honest but encouraging

---

## IMPLEMENTATION PSEUDOCODE

```
FUNCTION get_temporal_score(patient, parameter, current_value):
  
  # Get parameter temporal strategy
  strategy = get_temporal_strategy(parameter)
  
  # Calculate point score (current reading)
  point_score = calculate_normalized_score(current_value, ...)
  
  # Get recent measurement history
  history = get_measurement_history(patient, parameter, n=strategy.window_size)
  
  IF history.length == 0:
    # First measurement - no history
    RETURN {
      display_score: point_score,
      stability_score: null,
      trend: null,
      aberrant_flag: false
    }
  
  # Check for aberrant value
  aberrant = detect_aberrant(current_value, history)
  
  # Calculate stability score
  IF strategy.method == "EMA":
    previous_ema = get_last_ema(patient, parameter)
    stability_score = strategy.alpha Ã— point_score + (1 - strategy.alpha) Ã— previous_ema
  
  ELSE IF strategy.method == "MEDIAN":
    recent_scores = [score for each value in last N readings]
    stability_score = median(recent_scores)
  
  # Calculate display score (weighted combination)
  display_score = (strategy.w_point Ã— point_score) + 
                  (strategy.w_stability Ã— stability_score)
  
  # Calculate trend
  trend = calculate_trend(history)
  
  # Adjust interpretation based on trend
  IF trend == "RAPIDLY_RISING" AND display_score > 70:
    color_override = "YELLOW"  # Flag even if score is green
  
  RETURN {
    display_score: display_score,
    point_score: point_score,
    stability_score: stability_score,
    trend: trend,
    aberrant_flag: aberrant,
    history_length: history.length
  }
```

---

## DISPLAY REQUIREMENTS

### Mandatory Temporal Information

**For parameters with history (â‰¥2 readings):**

1. **Current Reading Info**
   - Latest value and date
   - Point score (may be hidden in UI, shown on hover)

2. **Stability/Trend Info**
   - Display score (primary score shown)
   - Trend arrow and direction
   - Brief trend description

3. **Historical Context**
   - Sparkline (last 5-10 readings)
   - Range of recent values
   - Time span of data

**Example Display:**
```
â•”â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•—
â•‘  SYSTOLIC BLOOD PRESSURE                    â•‘
â•‘                                              â•‘
â•‘  Latest: 128 mmHg (Nov 12)    Score: 75 ðŸŸ¡  â•‘
â•‘  Typical: 124-132 mmHg                       â•‘
â•‘                                              â•‘
â•‘  Trend: â†’ Stable (last 7 days)              â•‘
â•‘  [â–ƒâ–„â–…â–„â–ƒâ–…â–„] Sparkline                        â•‘
â•‘                                              â•‘
â•‘  Well-controlled this week.                  â•‘
â•šâ•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

### Aberrant Value Display

**If current reading flagged as aberrant:**

```
â•”â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•—
â•‘  SYSTOLIC BLOOD PRESSURE                    â•‘
â•‘                                              â•‘
â•‘  Latest: 168 mmHg (Nov 12) âš  Score: 38 ðŸŸ   â•‘
â•‘  Typical: 122-128 mmHg                       â•‘
â•‘                                              â•‘
â•‘  âš  This reading is unusually high for you.  â•‘
â•‘  Please recheck your blood pressure.        â•‘
â•‘                                              â•‘
â•‘  Your average: 125 mmHg (Score: 78 ðŸŸ¢)     â•‘
â•‘  [â–ƒâ–„â–ƒâ–ˆâ–„â–ƒâ–„] Sparkline (spike visible)        â•‘
â•šâ•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

**Key features:**
- Warning icon (âš ) on aberrant reading
- Show both current score (38) and typical score (78)
- Clear guidance to recheck
- Visual spike in sparkline

---

## QUALITY ASSURANCE

### Validation Checklist

For each parameter's temporal strategy:
- [ ] Temporal parameters defined (weights, smoothing method, window size)
- [ ] Clinical rationale documented
- [ ] Tested with simulated data (stable, trending, aberrant patterns)
- [ ] Aberrant detection validated (sensitivity/specificity)
- [ ] Display mockups reviewed by clinicians
- [ ] Patient comprehension tested (understand trend indicators)

### Common Pitfalls

**1. Over-smoothing acute parameters**
- Bad: Use 7-day median for troponin
- Good: Use point score or minimal smoothing (Î±=0.8)

**2. Under-smoothing chronic parameters**
- Bad: Show volatile home BP readings without smoothing
- Good: Use median filter or EMA with Î±=0.3

**3. Hiding aberrant values**
- Bad: Automatically exclude outliers from display
- Good: Show with warning, recommend recheck

**4. Ignoring trends**
- Bad: Only show current score
- Good: Show score + trend arrow + context

---

## REVISION HISTORY

**Version 1.0.0 - November 12, 2025**
- Initial specification
- Point vs stability scoring framework defined
- EMA and median filtering methods specified
- Aberrant value detection and handling
- Parameter-specific strategies
- Display requirements

---

## RELATED DOCUMENTS

- `PARAMETER_NORMALIZATION.md` - Core normalization methods
- `CALIBRATION_VALIDATION.md` - Coefficient optimization
- `CONTEXT_RULES.md` - Patient-specific adjustments
- `PROJECT_SPECIFICATION_v2.md` - Master project architecture

---

**END OF TEMPORAL SCORING SPECIFICATION**

*Time matters. Serial measurements provide richer clinical context than single readings.*
