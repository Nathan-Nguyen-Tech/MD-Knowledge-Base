# Context Loading Command

Load comprehensive context before working on a topic.

## Usage
`/context [topic]`

Examples:
- `/context care-plan` - Load all care plan related documents
- `/context smart-cards` - Load SMART card specifications
- `/context dashboard` - Load dashboard/data input specs
- `/context ai-agents` - Load multi-agent architecture

## What This Command Does

### Step 1: Core Documents (Always Read)
1. Read CLAUDE.md for project overview
2. Read SOURCE_DOCUMENT_REGISTRY.md for canonical sources
3. Check git status for recent changes

### Step 2: Topic-Specific Search
Based on [topic], search relevant locations:

| Topic | Search Locations |
|-------|-----------------|
| `care-plan` | CMO - PERFORMANCE MEDICINE/clinical-protocols/, Root *care-plan*.md files |
| `smart-cards` | CMO - SMART SYSTEM/docs/core/, UNIVERSAL_CARD_TEMPLATE.md |
| `dashboard` | CMO - DATA INPUT/, health-matrix-framework.md |
| `ai-agents` | MULTI_AGENT_AI_PLATFORM_ARCHITECTURE.md, CARE_PLAN_SMART_CARD_INTEGRATION_SPEC.md |
| `intake` | CMO - DATA INPUT/, patient intake forms |
| `lifestyle` | CMO - SMART SYSTEM/library/behavioral/, LIFESTYLE_PILLAR_QUESTIONNAIRES |
| `movement` | TIER5_MOVEMENT_EXERCISE_v2.md |
| `nutrition` | TIER5_NUTRITION_v2.md |
| `recovery` | TIER5_RECOVERY_v2.md |

### Step 3: Comprehensive File Discovery
1. Glob for files with [topic] in filename
2. Grep for [topic] mentions in file contents
3. Check SOURCE_DOCUMENT_REGISTRY.md for related canonical sources

### Step 4: Read and Summarize
1. Read the top 5-10 most relevant files
2. Note version numbers and last update dates
3. Identify any conflicts or inconsistencies

### Step 5: Output Context Report

```
CONTEXT LOADED: [topic]
=======================
Date: [today]

CORE DOCUMENTS READ:
- CLAUDE.md (v3.0)
- SOURCE_DOCUMENT_REGISTRY.md (v0.4)

TOPIC-SPECIFIC DOCUMENTS FOUND:
1. [file1] - v1.0 - [brief description]
2. [file2] - v0.5 - [brief description]
...

KEY SPECIFICATIONS:
- [key fact 1]
- [key fact 2]
...

RELATED DOCUMENTS (may also be relevant):
- [file] in [location]
...

POTENTIAL CONFLICTS/GAPS:
- [any inconsistencies found]

READY TO PROCEED WITH: [topic]
```

## When to Use This Command

Use `/context [topic]` when:
1. Starting work on a new feature or specification
2. Returning to a topic after time away
3. Before making significant changes to existing specs
4. When unsure what already exists on a topic

## Auto-Context Triggers

Claude should AUTOMATICALLY run context loading (without explicit command) when user mentions:
- "Care Plan" → auto-load care-plan context
- "SMART Card" or "SMART Deck" → auto-load smart-cards context
- "Dashboard" or "Health Overview" → auto-load dashboard context
- "AI Agent" or "Multi-Agent" → auto-load ai-agents context
- Any specific card library (Movement, Nutrition, etc.)
