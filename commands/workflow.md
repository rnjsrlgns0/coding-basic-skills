---
description: Complete development workflow integrating task-planner, branch-manager, and memory-bank-updater skills
---

# Complete Development Workflow

Execute the full development workflow following best practices:

## Workflow Steps:

### 1. Plan the Task
Use the `task-planner` skill to create a comprehensive plan:
- Review .serena/memories for context
- Analyze user requirements
- Break down into subtasks
- Assign appropriate subagents
- Plan parallel execution
- Specify tool usage (especially serena for codebase work)
- Update .serena/memories with the plan

### 2. Create Branch
Use the `branch-manager` skill to create appropriate Git branch:
- Determine feature name from task description
- Identify branch type (leaf for AI work, core for architecture)
- Create branch following naming convention: `feat:<feature-name>/leaf-<component>`
- Verify branch creation

### 3. Execute the Work
Perform the planned tasks:
- Follow the plan created in Step 1
- Use assigned subagents for each task
- Use serena tools for all codebase operations
- Make regular commits with clear messages
- Test functionality as you progress

### 4. Update Memory Bank
Use the `memory-bank-updater` skill to document work:
- Record completed work in progress.md
- Update techContext.md with technical decisions
- Update dataflow.md if data structures changed
- Save test results in test_results/ if applicable
- Clear activeContext.md after moving content to progress.md

### 5. Merge Branch
Use the `branch-manager` skill to complete the workflow:
- Merge to develop branch if successful
- Delete branch if task failed or approach changed
- Test integration in develop
- Document branch information in project history

## Usage:
Simply type `/workflow` followed by your task description.

Example:
```
/workflow Add a logout button to the navigation bar
```

This command will guide you through all steps automatically.
