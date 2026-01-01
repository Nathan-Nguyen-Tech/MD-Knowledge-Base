# Pre-Flight Check Command

Run before creating any new specification or major document.

## Usage
`/preflight [what you're about to create]`

Examples:
- `/preflight care plan digital interface spec`
- `/preflight autism behavioral card library`
- `/preflight new medication card template`

## What This Command Does

### Step 1: Search for Existing Content
1. Search for files with similar names
2. Grep for related keywords in existing documents
3. Check SOURCE_DOCUMENT_REGISTRY.md for canonical sources on this topic

### Step 2: Identify What Already Exists
List all files that touch on this topic:
- Direct matches (same topic)
- Partial overlaps (related topics)
- Potential conflicts (contradicting approaches)

### Step 3: Identify What Will Need Updating
When this new document is created, what else needs to change?
- SOURCE_DOCUMENT_REGISTRY.md (add new entry)
- CLAUDE.md (if major feature)
- 00_START_HERE.md (if navigation changes)
- Related specifications (if they reference this topic)
- Version numbers in dependent documents

### Step 4: Check for Redundancy
Ask:
- Does this duplicate existing content?
- Should this be an UPDATE to an existing file instead of a new file?
- Is there a better location for this content?

### Step 5: Output Pre-Flight Report

```
PRE-FLIGHT CHECK: [what you're creating]
========================================
Date: [today]

EXISTING FILES ON THIS TOPIC:
✓ [file1] - [description] - MUST READ BEFORE PROCEEDING
✓ [file2] - [description] - Related, should review
○ [file3] - [description] - Tangentially related

REDUNDANCY CHECK:
[ ] This appears to be NEW content (no duplicates found)
[ ] WARNING: This may duplicate [existing file] - consider updating instead
[ ] WARNING: Potential conflict with [existing file] approach

FILES THAT WILL NEED UPDATING:
1. SOURCE_DOCUMENT_REGISTRY.md - Add new entry
2. [file] - Update reference to include this
3. [file] - Version bump if dependent

RECOMMENDED APPROACH:
[ ] Proceed with new file at [location]
[ ] Update existing file [name] instead
[ ] Consolidate with [existing file]

CHECKLIST BEFORE PROCEEDING:
☐ Read all files marked "MUST READ"
☐ Confirm approach with user
☐ Plan updates to dependent files
☐ Proceed with creation
```

## When to Use This Command

MANDATORY before:
1. Creating any new *_SPEC.md file
2. Creating any new *_LIBRARY.md file
3. Creating any new master-level document
4. Making major changes to existing specifications

## Auto-Preflight Triggers

Claude should AUTOMATICALLY run preflight check (without explicit command) when:
- About to create a new file with Write tool
- User says "create a new..." or "write a specification for..."
- User asks to "document" or "spec out" something new

Claude should PAUSE and show the preflight report before proceeding.
