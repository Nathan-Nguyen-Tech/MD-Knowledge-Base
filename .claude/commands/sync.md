# Document Sync Command

Synchronize all documents after making changes to ensure consistency.

## Sync Tasks:

### 1. After Card Library Updates
When any TIER5_*_v2.md file is modified:
- Update the card count in LIBRARY_SUMMARY.md
- Update SOURCE_DOCUMENT_REGISTRY.md version number
- Check if CARD_TYPE_SPECIFICATIONS.md needs updating

### 2. After Specification Changes
When any *_SPEC*.md file is modified:
- Update SOURCE_DOCUMENT_REGISTRY.md
- Check dependent documents that reference this spec
- Update version numbers in referencing documents

### 3. After Adding New Files
When creating new .md files:
- Add to SOURCE_DOCUMENT_REGISTRY.md if canonical
- Add to appropriate index file (00_FILE_INDEX_AND_GUIDE.md)
- Update 00_START_HERE.md if major addition

### 4. Version Update File
If significant changes made during session:
- Create or update VERSION_UPDATE_[date].md
- List all files modified
- Summarize changes made

## Automatic Checks:

1. **Card Count Verification**
   - Read each TIER5_*_v2.md GRAND SUMMARY table
   - Sum total cards
   - Compare with LIBRARY_SUMMARY.md total
   - Flag mismatches

2. **Cross-Reference Verification**
   - Check that files mentioned in one doc exist
   - Check that version numbers match across docs

3. **Registry Completeness**
   - Every canonical spec should be in SOURCE_DOCUMENT_REGISTRY.md
   - Flag any spec files not in registry

## Output:

```
SYNC REPORT
===========
Date: [today]

CARD COUNTS:
- Movement: XXX (verified)
- Recovery: XX (verified)
- Nutrition: XXX (verified)
- Environmental: XX (verified)
- Mind-Body: XX (verified)
- TOTAL: XXX (matches/mismatches LIBRARY_SUMMARY.md)

REGISTRY STATUS:
- All canonical specs in registry: YES/NO
- Missing from registry: [list]

CROSS-REFERENCES:
- Broken links found: [list]
- Version mismatches: [list]

ACTIONS TAKEN:
- Updated [file] version to X.X
- Added [file] to registry
- ...
```
