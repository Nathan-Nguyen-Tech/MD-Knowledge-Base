# Session Log Command

Track changes made during this conversation session for continuity.

## When to Use:
- At END of each significant work session
- Before closing conversation
- After major changes to any files

## What to Log:

### 1. Files Modified
List every .md file that was edited with:
- File path
- What changed (brief)
- New version number if applicable

### 2. Files Created
List any new files with:
- File path
- Purpose

### 3. Files Deleted
List any removed files with:
- File path
- Reason for deletion

### 4. Card Changes
- Cards added (with IDs)
- Cards modified
- New card count totals

### 5. Open Issues
- Anything left incomplete
- Known issues discovered
- Recommendations for next session

## Output Location:
Append to or create: `SESSION_LOGS/[YYYY-MM-DD].md`

## Output Format:

```
# Session Log: [Date] [Time Range]

## Summary
[1-2 sentence summary of what was accomplished]

## Files Modified
| File | Change | Version |
|------|--------|---------|
| [path] | [description] | vX.X |

## Files Created
- [path]: [purpose]

## Files Deleted
- [path]: [reason]

## Card Changes
- Added: X cards
- New totals: Movement (XXX), Recovery (XX), etc.
- Total: XXX cards

## Open Issues
- [ ] [Issue 1]
- [ ] [Issue 2]

## Next Session Recommendations
1. [Recommendation]
2. [Recommendation]

---
*Logged by Claude at [timestamp]*
```

## Benefits:
- Start next session with `/session-log` to see what happened last time
- Track project evolution over time
- Never lose context between conversations
