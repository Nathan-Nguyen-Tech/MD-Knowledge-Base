# Document Audit Command

Perform a comprehensive audit of the CMO - HEALTH OVERVIEW project documents.

## Audit Tasks:

### 1. Version Conflicts
Find files where both v1 and v2 exist:
- List any `TIER5_*.md` files that have both versioned and non-versioned copies
- Identify which version is current (check the version footer)
- Recommend: Delete or archive the older version

### 2. Archived Files
Find all `_ARCHIVED_*.md` files:
- List them
- Check if they're referenced anywhere
- Recommend: Delete if not referenced

### 3. Standalone vs Organized Files
Find behavioral library files that exist both:
- In root `library/behavioral/` (old location)
- In subfolder like `library/behavioral/movement/` (new location)
- Recommend: Delete root-level duplicates

### 4. Orphaned Documents
Find .md files that:
- Are not referenced in SOURCE_DOCUMENT_REGISTRY.md
- Are not linked from any other document
- Recommend: Add to registry or mark for deletion

### 5. Version Inconsistencies
Check version numbers match across:
- Footer version statement
- Changelog entries
- SOURCE_DOCUMENT_REGISTRY.md listing

## Output Format:

```
DOCUMENT AUDIT REPORT
=====================
Date: [today]

VERSION CONFLICTS (need resolution):
- [file1] has v1 and v2 - KEEP: v2, DELETE: v1
- ...

ARCHIVED FILES (recommend deletion):
- [file] - not referenced anywhere
- ...

DUPLICATE LOCATIONS (recommend deletion):
- [root file] duplicated in [subfolder] - DELETE root
- ...

ORPHANED DOCUMENTS (need review):
- [file] - not in registry, not linked
- ...

VERSION MISMATCHES:
- [file] says v1.1 in footer but registry says v1.0
- ...

RECOMMENDED ACTIONS:
1. DELETE: [list of files]
2. ARCHIVE: [list of files]
3. UPDATE REGISTRY: [list of files]
```
