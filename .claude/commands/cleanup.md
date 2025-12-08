# Document Cleanup Command

Execute cleanup actions after audit identifies issues.

## Cleanup Actions:

### 1. Delete Obsolete Version Files
After confirming v2 exists and is current, delete v1 files:
```
Files to evaluate for deletion:
- TIER5_MOVEMENT_EXERCISE.md (v2 exists)
- TIER5_RECOVERY.md (v2 exists)
- TIER5_NUTRITION.md (v2 exists)
- TIER5_ENVIRONMENTAL_SOCIAL.md (v2 exists)
- TIER5_MIND_BODY.md (v2 exists)
- _ARCHIVED_*.md files
```

### 2. Delete Root-Level Duplicate Behavioral Files
These exist in both `library/behavioral/` and subfolders:
```
Evaluate for deletion (if duplicated in subfolder):
- library/behavioral/aerobic_exercise.md
- library/behavioral/dietary_patterns.md
- library/behavioral/eating_behaviors_meal_planning.md
- library/behavioral/sleep_stress_breathing.md
- library/behavioral/specific_food_focus.md
- library/behavioral/strength_flexibility_balance.md
- library/behavioral/mindbody_microlearning.md
```

### 3. Consolidate Lifestyle Questionnaires
Multiple versions exist:
```
- LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.md (old)
- LIFESTYLE_PILLAR_QUESTIONNAIRES_v2.1_OPTIMIZED.md (current)
- LIFESTYLE_QUESTIONNAIRE_CLINICAL_GUIDE_v2.1.md
- _ARCHIVED_LIFESTYLE_PILLAR_QUESTIONNAIRES_v1.md (archive)
- _ARCHIVED_LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md (archive)
```
Action: Keep v2.1_OPTIMIZED as canonical, delete archives

### 4. Consolidate Medical History
```
- MEDICAL_HISTORY_TIER1_LIBRARY.md (old)
- MEDICAL_HISTORY_TIER1_LIBRARY_v1.1_INTAKE_READY.md (current)
```
Action: Keep v1.1, delete original

## Safety Protocol:

1. **Before deleting**:
   - Verify the newer version contains all content
   - Check no other files reference the old version
   - Git commit current state first

2. **After deleting**:
   - Update SOURCE_DOCUMENT_REGISTRY.md
   - Update any index files
   - Git commit with deletion summary

## Output:

```
CLEANUP REPORT
==============
Date: [today]

FILES DELETED:
- [file] - Reason: Superseded by [new file]
- ...

FILES KEPT:
- [file] - Reason: Still referenced / Current version
- ...

REGISTRY UPDATES:
- Removed [file] from registry
- Updated [file] version reference
- ...

POST-CLEANUP FILE COUNT:
- Before: XXX .md files
- After: XXX .md files
- Reduction: XX files
```
