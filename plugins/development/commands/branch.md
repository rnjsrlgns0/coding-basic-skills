---
description: Manage Git branches throughout the development lifecycle using branch-manager skill
---

# Branch Management

Use the `branch-manager` skill to systematically manage Git branches.

## Commands:

### Create Branch
Create a new branch before starting work:
```
/branch create [feature-description]
```

This will:
1. Extract feature name from description
2. Determine branch type (leaf for AI work)
3. Create branch with naming convention: `feat:<feature-name>/leaf-<component>`
4. Checkout to the new branch
5. Verify creation

Example:
```
/branch create button feature for user profile
```
Creates: `feat:button-feature/leaf-ui-component`

### Merge Branch
Merge completed work to develop:
```
/branch merge
```

This will:
1. Ensure all changes are committed
2. Update develop branch
3. Merge current branch into develop
4. Run tests if available
5. Delete branch after successful merge

### Delete Branch
Delete a failed or unnecessary branch:
```
/branch delete [branch-name]
```

This will:
1. Switch to develop branch
2. Delete the specified branch locally
3. Delete remote branch if pushed

### Check Status
View current branch and status:
```
/branch status
```

## Branch Structure:
```
main (production)
└── develop (integration)
    ├── feat:<feature>/leaf-<component>  (AI work)
    └── feat:<feature>/core-architecture (Human work)
```

## Naming Convention:
Format: `<type>:<feature-name>/<work-type>-<component-description>`

- **Type**: feat, bugfix, hotfix, refactor
- **Feature name**: lowercase-with-hyphens (2-4 words)
- **Work type**: leaf (AI) or core (human)
- **Component**: specific component being worked on

Valid examples:
- `feat:user-auth/leaf-login-form`
- `bugfix:header/leaf-responsive-layout`
- `refactor:database/leaf-query-optimization`
