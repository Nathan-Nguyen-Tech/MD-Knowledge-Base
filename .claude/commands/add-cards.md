# Add Cards Command

Guided workflow for adding new cards to a library.

## Usage:
`/add-cards [library] [category]`

Example: `/add-cards movement NEAT` or `/add-cards nutrition glucose`

## Pre-Flight Checks:

### 1. Verify Library Exists
Valid libraries:
- `movement` → TIER5_MOVEMENT_EXERCISE_v2.md
- `recovery` → TIER5_RECOVERY_v2.md
- `nutrition` → TIER5_NUTRITION_v2.md
- `environmental` → TIER5_ENVIRONMENTAL_SOCIAL_v2.md
- `mind-body` → TIER5_MIND_BODY_v2.md
- `micro-learning` → TIER5_MICRO_LEARNING.md

### 2. Verify Category Exists
Check if the Tier 3/Tier 4 category exists in the target library.
If not, ask user if they want to create a new category.

### 3. Check for Duplicates
Before adding any card, search existing cards for:
- Same or very similar name
- Same action/behavior described differently
- Warn user if potential duplicate found

## Card Creation Checklist:

For each new card, ensure:
- [ ] Unique Card ID following format (e.g., MOV_NEAT_008)
- [ ] Card Name (verb + object, atomic action)
- [ ] Description (what the action is)
- [ ] Method/Technique (how to do it)
- [ ] Tags (if applicable: #micro, #biohacking, #circadian, etc.)
- [ ] Not a duplicate of existing card

## Post-Addition Tasks:

### Automatic Updates:
1. Update subtotal count for the Tier 4 category
2. Update GRAND SUMMARY table total
3. Update CLAUDE.md card count if significant change

### Manual Reminders:
- Consider if SOURCE_DOCUMENT_REGISTRY.md needs update
- Consider if related documents reference this category

## Output Format:

```
ADD CARDS: [Library] > [Category]
=================================

Pre-flight:
✓ Library exists: [path]
✓ Category exists: [Tier 3 > Tier 4]
✓ Current count: X cards in category, Y total in library

Cards to Add:
1. [Card ID] - [Card Name]
   Description: [...]
   Tags: [...]
   Duplicate check: ✓ No duplicates found

2. [Card ID] - [Card Name]
   ...

Post-Addition:
✓ Category subtotal: X → Y
✓ Library total: X → Y
✓ CLAUDE.md updated: Total cards now XXX

Ready to proceed? [Y/N]
```
