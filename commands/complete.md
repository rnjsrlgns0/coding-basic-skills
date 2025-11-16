---
description: Complete current task by updating memory and managing branch
---

# Complete Task

Execute the completion workflow after finishing a task.

## What This Command Does:

Combines `memory-bank-updater` and `branch-manager` skills to properly close out completed work.

## Workflow:

### 1. Update Memory Bank
Using `memory-bank-updater`:
- Analyze completed work
- Update progress.md with accomplishments
- Record technical decisions in techContext.md
- Update dataflow.md if applicable
- Save test results if available
- Clear activeContext.md and move content to progress.md

### 2. Manage Branch
Using `branch-manager`:
- Ensure all changes are committed
- Merge to develop if successful
- Delete branch if task failed
- Test integration
- Document branch information

## Usage:

For successful completion:
```
/complete success
```

For failed/abandoned task:
```
/complete fail [reason]
```

## Success Path:
```
/complete success
```
Will:
1. Update all relevant memory files
2. Commit final changes with proper message
3. Merge current branch to develop
4. Run integration tests
5. Delete merged branch
6. Update project documentation

## Failure Path:
```
/complete fail trying different approach
```
Will:
1. Update memory with attempted approach
2. Document why it failed
3. Switch to develop branch
4. Delete failed branch
5. Clean up temporary files
6. Prepare for new attempt

## Examples:

Successful completion:
```
/complete success
```

Failed with reason:
```
/complete fail API integration didn't work as expected
```

## Post-Completion:

After running this command:
- Your work is documented in .serena/memories
- Branch is properly merged or deleted
- Project is ready for next task
- Context is maintained for future reference

## Important Notes:

- **Always commit before running** - ensure no uncommitted changes
- **Provide clear reason for failures** - helps future planning
- **Review memory updates** - verify documentation is accurate
- **Check develop branch** - ensure integration is successful
