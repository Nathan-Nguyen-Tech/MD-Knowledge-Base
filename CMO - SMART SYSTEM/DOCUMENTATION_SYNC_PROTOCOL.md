# Documentation Sync Protocol

> **Purpose**: Prevent documentation drift by establishing clear rules for what documents are authoritative and how to keep them in sync.

---

## The Problem: Documentation Drift

When multiple documents describe the same concept, they can become inconsistent over time. This causes:
- Confusion about what's correct
- Wasted time reconciling differences
- Incorrect implementations

---

## Solution: Single Source of Truth (SSOT)

### Rule 1: Each concept has ONE authoritative document

| Concept | Authoritative Document | Other Docs Should Reference, Not Duplicate |
|---------|----------------------|-------------------------------------------|
| **Tier Structure (1-5)** | `LIBRARY_TIER_STRUCTURE.md` | All other docs link here |
| **Card Template** | `docs/core/02_UNIVERSAL_CARD_TEMPLATE.md` | Examples follow this |
| **Card Type Specs** | `docs/core/03_CARD_TYPE_SPECIFICATIONS.md` | - |
| **Validation Rules** | `docs/core/04_VALIDATION_CHECKLIST.md` | - |
| **Current Project State** | `CHANGELOG.md` | Read first each session |
| **AI Session Instructions** | `.claude/instructions.md` | Summary only, links to sources |

### Rule 2: Deprecated documents must be DELETED, not just updated

If a document is superseded, delete it. Don't leave old versions around.

**Deleted Documents (as of 2024-11-23)**:
- `docs/reference/TIER1_OUTLINE_CORRECTED.md` - superseded by LIBRARY_TIER_STRUCTURE.md
- `docs/reference/TIER2_OUTLINE_CORRECTED.md` - superseded by LIBRARY_TIER_STRUCTURE.md

---

## Update Protocol

### When Making Changes

1. **Identify the authoritative document** for what you're changing
2. **Update the authoritative document FIRST**
3. **Update CHANGELOG.md** with what changed and why
4. **Update .claude/instructions.md** if it affects AI workflow
5. **Search for other references** and update or delete them

### Checklist After Any Structural Change

- [ ] Is `LIBRARY_TIER_STRUCTURE.md` still accurate?
- [ ] Does `CHANGELOG.md` reflect current state?
- [ ] Does `.claude/instructions.md` match the authoritative docs?
- [ ] Are there any orphaned/outdated documents that should be deleted?

---

## Key Numbers to Keep Consistent

These numbers should be the same across all documents:

| Metric | Current Value | Source Document |
|--------|---------------|-----------------|
| Tier 1 Categories | 2 (Medical, Behavioral) | LIBRARY_TIER_STRUCTURE.md |
| Tier 2 Card Types | **12** | LIBRARY_TIER_STRUCTURE.md |
| Health Systems | 8 | 02_UNIVERSAL_CARD_TEMPLATE.md |
| Domains | 3 (Structure, Function, Risk) | 02_UNIVERSAL_CARD_TEMPLATE.md |
| Total Estimated Cards | ~1,000 | LIBRARY_TIER_STRUCTURE.md |

**If you see "10 card types" anywhere, that document is OUTDATED.**

---

## Session Start Protocol

At the start of each AI session:

1. Read `CHANGELOG.md` - Current State section
2. Note any "What's In Progress" items
3. Check Document Version Tracking table for outdated docs
4. If user mentions something that contradicts docs, VERIFY before proceeding

---

## Session End Protocol

After making changes:

1. Update `CHANGELOG.md` with changes made
2. Increment version numbers on modified documents
3. Update Document Version Tracking table
4. Note any follow-up items in "What's Next"

---

## Red Flags: Signs of Documentation Drift

Watch for these warning signs:

- Two documents have different numbers for the same metric
- A document references another document that doesn't exist
- CHANGELOG says something is "done" but it's not in the files
- User says "we decided X" but no document reflects that decision

**When you spot drift**: STOP and reconcile before proceeding.

---

## Document Hierarchy

```
CHANGELOG.md (Current State - READ FIRST)
    │
    ├── LIBRARY_TIER_STRUCTURE.md (Tier Structure - SINGLE SOURCE)
    │
    ├── docs/core/
    │   ├── 01_SYSTEM_OVERVIEW.md
    │   ├── 02_UNIVERSAL_CARD_TEMPLATE.md (Card Structure - SINGLE SOURCE)
    │   ├── 03_CARD_TYPE_SPECIFICATIONS.md (Type Details - SINGLE SOURCE)
    │   ├── 04_VALIDATION_CHECKLIST.md (Quality Rules - SINGLE SOURCE)
    │   ├── 05_EXAMPLE_SMART_CARDS.md (Examples - Follow Templates)
    │   └── 06_AI_AGENT_WORKFLOW.md
    │
    ├── docs/reference/ (Supporting docs - NOT authoritative)
    │
    └── .claude/instructions.md (AI Summary - References Sources)
```

---

## Quick Reference: What To Update When

| Change Type | Update These Documents |
|-------------|----------------------|
| Add/remove card type | LIBRARY_TIER_STRUCTURE.md → CHANGELOG.md → .claude/instructions.md |
| Change card template | 02_UNIVERSAL_CARD_TEMPLATE.md → 05_EXAMPLE_SMART_CARDS.md → CHANGELOG.md |
| Add new decision | CHANGELOG.md (Key Decisions Log) |
| Complete a phase | CHANGELOG.md (Current State + Change Log) |
| Structural change | All core docs + delete outdated files |

---

*Version 1.0 | Created: 2024-11-23*
