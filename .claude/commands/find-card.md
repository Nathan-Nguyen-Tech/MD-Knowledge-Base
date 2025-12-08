# Find Card Command

Search for cards across all behavioral libraries.

## Usage:
`/find-card [search term]`

Example: `/find-card walking` or `/find-card cold exposure`

## Search Locations:
1. TIER5_MOVEMENT_EXERCISE_v2.md
2. TIER5_RECOVERY_v2.md
3. TIER5_NUTRITION_v2.md
4. TIER5_ENVIRONMENTAL_SOCIAL_v2.md
5. TIER5_MIND_BODY_v2.md
6. TIER5_MICRO_LEARNING.md

## Search Fields:
- Card ID (e.g., MOV_NEAT_001)
- Card Name (e.g., "Post-Meal Walk")
- Description
- Tags (#micro, #biohacking, etc.)

## Output Format:

```
CARD SEARCH: "[term]"
====================
Found X matches:

1. [Card ID] - [Card Name]
   Library: [which TIER5 file]
   Category: [Tier 3 > Tier 4]
   Tags: [tags if any]
   Description: [brief description]

2. [Card ID] - [Card Name]
   ...

No matches? Suggest:
- Check spelling
- Try broader term
- Card may need to be created
```

## Use Cases:
- Check if a card exists before creating
- Find related cards for deck building
- Locate cards by tag (#biohacking, #micro)
