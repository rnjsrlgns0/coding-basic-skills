---
description: Update project memory bank after completing work using memory-bank-updater skill
---

# Update Memory Bank

Use the `memory-bank-updater` skill to document completed work in .serena/memories.

## What This Command Does:

Automatically updates the appropriate memory files based on the type of work completed:

### Files Updated:

1. **activeContext.md** - Current work in progress
2. **progress.md** - Historical record of completed tasks
3. **techContext.md** - Technical decisions and stack
4. **dataflow.md** - Data flow and structure changes
5. **test_results/** - Test reports and benchmarks

## Update Process:

### Step 1: Analyze Completed Work
- What was accomplished?
- Which files were changed/added?
- Were there technical decisions?
- Did data flow change?
- Are there test results?

### Step 2: Determine Target Files
| Work Type | Files to Update |
|-----------|----------------|
| New feature | progress.md, techContext.md, activeContext.md |
| Tech stack change | techContext.md, progress.md |
| Data structure change | dataflow.md, techContext.md, progress.md |
| Testing | test_results/, progress.md |
| Project scope change | projectBrief.md, progress.md |

### Step 3: Update Each File
- Write concise summaries in Korean
- Follow the template for each file
- Maintain chronological order (progress.md in reverse)
- Avoid duplication across files

### Step 4: Verify Updates
- No duplicate content across files
- Information in most appropriate file
- Correct chronological order
- Korean language (except code/filenames)

## Usage:

After completing any significant work:
```
/update-memory
```

Or specify the type of work:
```
/update-memory [work-description]
```

Example:
```
/update-memory Completed user authentication feature with JWT
```

The command will:
1. Review your recent changes
2. Update appropriate memory files
3. Move completed tasks from activeContext to progress
4. Document technical decisions
5. Record test results if applicable

## Important Notes:

- **Always use after completing work** to maintain project context
- **Write in Korean** except for code and filenames
- **Avoid duplication** - each information in its appropriate file
- **Use serena tools** for all memory file operations
