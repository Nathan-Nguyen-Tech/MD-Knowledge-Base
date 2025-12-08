# Build Deck Command

Help assemble a SMART Deck from existing cards.

## Usage:
`/build-deck [condition or goal]`

Example: `/build-deck diabetes management` or `/build-deck morning routine`

## Process:

### 1. Identify Deck Purpose
- Condition-specific (Diabetes, Hypertension, Anxiety)
- Goal-specific (Weight Loss, Better Sleep, Stress Reduction)
- Time-specific (Morning Routine, Mealtime, Bedtime)
- Strategy-specific (Mediterranean Diet, HIIT Training)

### 2. Search Relevant Cards
Search across all 6 libraries for cards matching the purpose:
- Movement cards for physical activity goals
- Nutrition cards for dietary goals
- Recovery cards for sleep/stress goals
- Mind-Body cards for mental health goals
- Environmental cards for lifestyle/environment goals
- Micro-Learning cards for educational components

### 3. Assemble Deck Draft
Create a proposed deck with:
- Deck Name
- Deck Purpose
- Card list with IDs
- Suggested sequencing (which cards first)
- Estimated completion time

## Output Format:

```
DECK BUILDER: [Purpose]
=======================

Proposed Deck: [Name]
Purpose: [1-2 sentence description]
Target: [Who is this for]
Duration: [How long to complete deck]

CARDS INCLUDED:
---------------
Phase 1 - Foundation:
  1. [Card ID] - [Card Name] (from [Library])
  2. [Card ID] - [Card Name] (from [Library])

Phase 2 - Core Actions:
  3. [Card ID] - [Card Name] (from [Library])
  4. [Card ID] - [Card Name] (from [Library])
  ...

Phase 3 - Optimization:
  X. [Card ID] - [Card Name] (from [Library])

TOTAL: X cards from Y libraries

NOTES:
- [Any sequencing recommendations]
- [Prerequisites or warnings]
```

## Deck Types Reference:
- **Condition Decks**: Disease-specific management
- **Goal Decks**: Outcome-focused (weight, fitness, stress)
- **Routine Decks**: Time-based groupings (morning, mealtime)
- **Strategy Decks**: Method-based (Mediterranean, HIIT)
