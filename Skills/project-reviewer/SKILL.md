---
name: project-reviewer
description: This skill should be used when users explicitly request a project review (e.g., "review this project", "project review", "create a project review"). Generates comprehensive yet concise onboarding documentation using serena MCP tools to analyze codebase structure, data flows, and module interactions. Outputs four review documents in /review directory - project brief, structure, flow diagrams (mermaid), and pre-tested quick start guide - all in bullet-point format for rapid onboarding.
---

# Project Reviewer

## Overview

Generate comprehensive project review documentation for rapid user onboarding. Use serena MCP tools for efficient codebase analysis and create four concise documents in `/review` directory: project brief, structure overview, flow diagrams, and pre-tested quick start guide.

## When to Use This Skill

Use this skill when users explicitly request project review with phrases like:
- "review this project"
- "create a project review"
- "project review"
- "generate project review documentation"

## Review Workflow

### 1. Initial Analysis

Before starting, use serena MCP tools for efficient exploration:

```
mcp__serena-mcp__list_memories
mcp__serena-mcp__list_dir (relative_path: ".", recursive: true)
mcp__serena-mcp__get_symbols_overview
mcp__serena-mcp__find_file
```

Analyze:
- Project root directory structure
- Key configuration files (package.json, requirements.txt, etc.)
- Main entry points and core modules
- Existing documentation and README files
- Available memories for project context

### 2. Generate Review Documents

Create four documents in `/review` directory following the templates in `references/review_templates.md`:

#### a. project_brief.md
- **Purpose**: Ultra-concise project overview
- **Format**: Bullet points only
- **Content**:
  - Project name and primary purpose
  - Core technology stack
  - Main features (3-5 items max)
  - Target use case
- **Length**: < 200 words

#### b. project_structure.md
- **Purpose**: Directory structure overview
- **Format**: Tree structure with brief annotations
- **Content**:
  - Key directories and their purposes
  - Important files and their roles
  - Module organization
- **Style**: Use tree format with inline comments
- **Length**: Focus on top 2-3 levels, annotate critical paths only

#### c. project_flow.md
- **Purpose**: Visualize system architecture and interactions
- **Format**: Mermaid diagrams
- **Content**:
  - Data flow diagram
  - Module interaction diagram
  - Request/response flow (if applicable)
  - Key process workflows
- **Requirements**: All diagrams in mermaid syntax
- **Quality**: Use `mcp__serena-mcp__find_referencing_symbols` to verify actual relationships

#### d. quick_start.md
- **Purpose**: Pre-tested setup and run instructions
- **Format**: Numbered steps with commands
- **Content**:
  - Environment setup (prerequisites, virtual env, dependencies)
  - Configuration steps
  - Development server/build commands
  - Common development tasks
- **CRITICAL**: Test ALL commands before documenting
  - Execute setup commands in test environment
  - Verify build and run processes work
  - Document actual output/behavior
  - Note any environment-specific requirements

### 3. Testing Requirements

Before finalizing quick_start.md:

1. **Environment Setup Testing**:
   ```bash
   # Test virtual environment creation
   # Test dependency installation
   # Verify configuration files
   ```

2. **Build and Run Testing**:
   ```bash
   # Test development server startup
   # Test build processes
   # Verify common scripts work
   ```

3. **Documentation**:
   - Include actual command output snippets
   - Note expected behavior
   - Document any warnings or common issues
   - Specify tested environment (Python version, OS, etc.)

### 4. Quality Standards

All documents must follow these rules:

**Format**:
- Bullet points and outline format only
- No lengthy paragraphs
- Use `-` for bullets, `###` for subheadings
- Keep each bullet to single line when possible

**Conciseness**:
- Project brief: < 200 words
- Project structure: Focus on top 2-3 directory levels
- Project flow: 2-4 mermaid diagrams maximum
- Quick start: Essential steps only (< 15 steps)

**Accuracy**:
- Use serena MCP tools to verify information
- Test all commands before documenting
- Reference actual file paths and symbols
- Validate module relationships with `find_referencing_symbols`

## Output Structure

Create this exact directory structure:

```
/review/
├── project_brief.md        # Ultra-concise overview
├── project_structure.md    # Directory tree with annotations
├── project_flow.md         # Mermaid diagrams
└── quick_start.md          # Pre-tested setup guide
```

## Tool Usage Strategy

Maximize efficiency with serena MCP tools:

1. **For Structure Analysis**:
   - `list_dir` with `recursive: true` for directory tree
   - `get_symbols_overview` for module understanding
   - `find_file` for locating key files

2. **For Flow Analysis**:
   - `find_symbol` to understand core functions/classes
   - `find_referencing_symbols` to map dependencies
   - `search_for_pattern` for tracing data flows

3. **For Quick Start**:
   - `read_file` for package.json, requirements.txt, etc.
   - `execute_shell_command` to test setup commands
   - Check memories for existing setup documentation

## Example Usage

**User request**: "project review"

**Process**:
1. List memories and check for project context
2. Analyze directory structure with `list_dir`
3. Identify entry points with `get_symbols_overview`
4. Generate project_brief.md (concise overview)
5. Create project_structure.md (annotated tree)
6. Build project_flow.md (mermaid diagrams using symbol analysis)
7. Test and document quick_start.md (verify all commands)
8. Place all files in `/review` directory

**Output**: Four concise, pre-tested markdown files ready for immediate use.

## Resources

### references/
- `review_templates.md`: Detailed templates for each review document with examples

Delete scripts/ and assets/ directories as they are not needed for this skill.
