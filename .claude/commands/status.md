# Quick Status Command

Provide a fast snapshot of project state (30-second check, not full audit).

## Quick Checks:

1. **File Count**: Count .md files in project
2. **Card Totals**: Read GRAND SUMMARY from each TIER5_*_v2.md
3. **Recent Changes**: Check git status for uncommitted changes
4. **Last Update**: Find most recently modified .md file

## Output Format:

```
CMO STATUS (Quick)
==================
Files: XXX markdown files
Cards: XXX total (Movement: XXX, Recovery: XX, Nutrition: XXX, Environmental: XX, Mind-Body: XX)
Git: X files modified, X untracked
Last Edit: [filename] ([time ago])
```

## Do NOT:
- Read full file contents
- Check cross-references
- Verify version numbers
- Run cleanup recommendations

This is for quick orientation, not comprehensive audit.
