# Update Registry Command

Synchronize SOURCE_DOCUMENT_REGISTRY.md with current project state.

## When to Run:
- After creating new canonical documents
- After updating version numbers
- After structural reorganization
- Weekly maintenance

## Process:

### 1. Scan for Canonical Documents
Find all documents that should be in registry:
- `*_SPEC*.md` files
- `*_LIBRARY*.md` files
- `TIER5_*.md` files
- Core documentation (ARCHITECTURE, TEMPLATE, etc.)

### 2. Compare with Registry
For each canonical document:
- Check if it exists in SOURCE_DOCUMENT_REGISTRY.md
- Verify version number matches file footer
- Verify file path is correct

### 3. Identify Discrepancies
- Files in project but not in registry (MISSING)
- Files in registry but not in project (ORPHANED)
- Version mismatches (OUTDATED)
- Path changes (MOVED)

### 4. Generate Updates
Produce exact edits needed to fix registry.

## Output Format:

```
REGISTRY UPDATE CHECK
=====================

Scanned: XX canonical documents
In Registry: XX entries

MISSING FROM REGISTRY (need to add):
- [file path] (v[version]) - [category]
- ...

ORPHANED IN REGISTRY (file deleted/moved):
- [registry entry] - File not found at path
- ...

VERSION MISMATCHES:
- [file]: Registry says vX.X, file says vY.Y
- ...

PATH CHANGES:
- [file]: Registry path outdated
- ...

RECOMMENDED ACTIONS:
1. Add X entries to registry
2. Remove X orphaned entries
3. Update X version numbers
4. Fix X paths

Proceed with updates? [Y/N]
```

## Registry Entry Format:

When adding new entries, use this format:
```markdown
| [Document Name] | [Purpose] | [Location] | vX.X |
```

Categories in registry:
- Master Documents
- SMART System Core
- Behavioral Libraries
- Medical Libraries
- Clinical Logic
- Dashboard Specs
