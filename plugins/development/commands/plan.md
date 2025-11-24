---
description: Create a comprehensive task plan using task-planner skill
---

# Task Planning

Use the `task-planner` skill to create a detailed, executable plan for your task.

## What This Command Does:

1. **Collect Context**: Review .serena/memories and CLAUDE.md for project context
2. **Analyze Requirements**: Extract user requirements and provided guidelines
3. **Break Down Task**: Decompose into manageable subtasks
4. **Assign Agents**: Select appropriate subagents for each subtask
5. **Plan Parallelization**: Identify independent tasks for concurrent execution
6. **Specify Tools**: Detail which tools to use (especially serena for codebase work)
7. **Generate Plan Document**: Create structured plan following the template
8. **Update Memories**: Save plan to .serena/memories for future reference

## Key Features:

- **User-Centric**: Only includes explicitly requested features
- **Tool Enforcement**: Always specifies serena tools for codebase operations
- **Parallel Execution**: Maximizes efficiency by identifying concurrent tasks
- **Context Integration**: Leverages existing project knowledge from .serena/memories

## Usage:
```
/plan [task description]
```

Example:
```
/plan Build a user authentication system with login and registration
```

The command will create a comprehensive plan document with:
- Context summary
- User requirements
- Subtask breakdown
- Subagent assignments
- Tool specifications
- Execution strategy with parallel batches
- Validation checklist
