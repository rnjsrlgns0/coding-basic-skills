# Project Review Templates

This file provides detailed templates and examples for each review document.

## Template 1: project_brief.md

### Structure
```markdown
# [Project Name]

## Purpose
- [Primary purpose in one line]

## Technology Stack
- **Language**: [Primary language]
- **Framework**: [Main framework/library]
- **Database**: [Database if applicable]
- **Key Dependencies**: [2-3 critical dependencies]

## Core Features
- [Feature 1]
- [Feature 2]
- [Feature 3]
- [Feature 4 - optional]
- [Feature 5 - optional]

## Use Case
- [Who uses it and why]
```

### Example
```markdown
# TaskFlow API

## Purpose
- RESTful API for task management with real-time collaboration

## Technology Stack
- **Language**: Python 3.11
- **Framework**: FastAPI
- **Database**: PostgreSQL + Redis
- **Key Dependencies**: SQLAlchemy, Pydantic, WebSocket

## Core Features
- Task CRUD operations with role-based access
- Real-time task updates via WebSocket
- User authentication (JWT)
- Task assignment and notifications
- Activity logging and audit trails

## Use Case
- Teams need collaborative task tracking with instant updates
```

---

## Template 2: project_structure.md

### Structure
```markdown
# Project Structure

## Directory Tree

\`\`\`
project-root/
├── [dir1]/              # [Purpose]
│   ├── [subdir]/        # [Purpose]
│   └── [key-file]       # [Purpose]
├── [dir2]/              # [Purpose]
│   ├── [module1]/       # [Purpose]
│   └── [module2]/       # [Purpose]
├── [config-file]        # [Purpose]
└── [entry-point]        # [Purpose]
\`\`\`

## Key Directories

### [Directory 1]
- **Purpose**: [What it contains]
- **Key Files**: [Important files and their roles]

### [Directory 2]
- **Purpose**: [What it contains]
- **Key Files**: [Important files and their roles]

## Critical Files

- **[file1]**: [Role and importance]
- **[file2]**: [Role and importance]
```

### Example
```markdown
# Project Structure

## Directory Tree

\`\`\`
taskflow-api/
├── src/                 # Application source code
│   ├── api/             # API endpoints and routes
│   │   ├── v1/          # API version 1
│   │   └── deps.py      # Shared dependencies
│   ├── core/            # Core configuration and security
│   │   ├── config.py    # App settings
│   │   └── security.py  # Auth handlers
│   ├── models/          # Database models (SQLAlchemy)
│   ├── schemas/         # Pydantic schemas
│   └── services/        # Business logic
├── tests/               # Test suites
│   ├── unit/            # Unit tests
│   └── integration/     # Integration tests
├── alembic/             # Database migrations
├── main.py              # Application entry point
├── requirements.txt     # Python dependencies
└── .env.example         # Environment variables template
\`\`\`

## Key Directories

### src/api/
- **Purpose**: API route handlers and endpoint definitions
- **Key Files**: `deps.py` (dependency injection), `v1/tasks.py` (task endpoints)

### src/models/
- **Purpose**: SQLAlchemy ORM models for database tables
- **Key Files**: `task.py`, `user.py`, `activity.py`

### src/services/
- **Purpose**: Business logic layer between API and database
- **Key Files**: `task_service.py`, `notification_service.py`

## Critical Files

- **main.py**: FastAPI app initialization, middleware setup, route registration
- **src/core/config.py**: Centralized settings using Pydantic BaseSettings
- **requirements.txt**: Pinned dependencies for reproducible builds
```

---

## Template 3: project_flow.md

### Structure
```markdown
# Project Flow

## Data Flow Diagram

\`\`\`mermaid
[Mermaid diagram showing data flow]
\`\`\`

## Module Interaction Diagram

\`\`\`mermaid
[Mermaid diagram showing module relationships]
\`\`\`

## [Specific Process Flow - if applicable]

\`\`\`mermaid
[Mermaid diagram for specific process like authentication, request handling, etc.]
\`\`\`

## Key Interactions

- **[Module A] → [Module B]**: [What data/calls flow between them]
- **[Module C] → [Module D]**: [What data/calls flow between them]
```

### Example
```markdown
# Project Flow

## Request Flow Diagram

\`\`\`mermaid
sequenceDiagram
    participant Client
    participant API
    participant Auth
    participant Service
    participant DB
    participant WebSocket

    Client->>API: POST /api/v1/tasks
    API->>Auth: Validate JWT token
    Auth-->>API: User authenticated
    API->>Service: Create task
    Service->>DB: Insert task record
    DB-->>Service: Task created
    Service->>WebSocket: Broadcast task update
    WebSocket-->>Client: Real-time notification
    Service-->>API: Task response
    API-->>Client: 201 Created
\`\`\`

## Module Interaction Diagram

\`\`\`mermaid
graph TB
    API[API Routes] --> Services[Business Services]
    API --> Auth[Auth Middleware]
    Services --> Models[Database Models]
    Services --> Schemas[Pydantic Schemas]
    Models --> DB[(PostgreSQL)]
    Services --> Cache[(Redis Cache)]
    Services --> WS[WebSocket Manager]

    Auth -.-> Cache
    WS --> Client[Connected Clients]
\`\`\`

## Authentication Flow

\`\`\`mermaid
flowchart LR
    A[Login Request] --> B{Validate Credentials}
    B -->|Valid| C[Generate JWT]
    B -->|Invalid| D[401 Error]
    C --> E[Store in Redis]
    E --> F[Return Token]
    F --> G[Protected Endpoints]
    G --> H{Verify JWT}
    H -->|Valid| I[Process Request]
    H -->|Invalid| D
\`\`\`

## Key Interactions

- **API → Services**: Delegates business logic, passes validated schemas
- **Services → Models**: ORM operations (CRUD) via SQLAlchemy
- **Services → WebSocket**: Broadcasts real-time updates to connected clients
- **Auth Middleware → Cache**: Validates JWT against Redis for quick lookup
```

---

## Template 4: quick_start.md

### Structure
```markdown
# Quick Start Guide

## Prerequisites
- [Requirement 1 with version]
- [Requirement 2 with version]
- [Requirement 3 with version]

## Environment Setup

### 1. [Step 1 Title]
\`\`\`bash
[command]
\`\`\`
**Expected**: [What should happen]

### 2. [Step 2 Title]
\`\`\`bash
[command]
\`\`\`
**Expected**: [What should happen]

[Continue for all setup steps...]

## Configuration

### [Configuration aspect 1]
\`\`\`bash
[command or file edit]
\`\`\`

### [Configuration aspect 2]
\`\`\`bash
[command or file edit]
\`\`\`

## Running the Application

### Development Mode
\`\`\`bash
[command]
\`\`\`
**Output**: [Expected output or URL]

### [Alternative run mode if applicable]
\`\`\`bash
[command]
\`\`\`
**Output**: [Expected output]

## Common Commands

| Command | Purpose |
|---------|---------|
| \`[cmd]\` | [What it does] |
| \`[cmd]\` | [What it does] |
| \`[cmd]\` | [What it does] |

## Verification

- [ ] [Check 1]
- [ ] [Check 2]
- [ ] [Check 3]

## Tested Environment
- **OS**: [Tested OS]
- **Python/Node**: [Version]
- **Date**: [Test date]
```

### Example
```markdown
# Quick Start Guide

## Prerequisites
- Python 3.11+
- PostgreSQL 14+
- Redis 6+
- pip or uv package manager

## Environment Setup

### 1. Clone and Navigate
\`\`\`bash
cd taskflow-api
\`\`\`

### 2. Create Virtual Environment
\`\`\`bash
python -m venv .venv
source .venv/bin/activate  # Mac/Linux
# .venv\Scripts\activate   # Windows
\`\`\`
**Expected**: Prompt shows `(.venv)`

### 3. Install Dependencies
\`\`\`bash
pip install -r requirements.txt
\`\`\`
**Expected**: ~45 packages installed, no errors

### 4. Start Required Services
\`\`\`bash
# PostgreSQL (if not running)
brew services start postgresql@14  # Mac
# sudo service postgresql start    # Linux

# Redis
brew services start redis          # Mac
# sudo service redis-server start  # Linux
\`\`\`
**Expected**: Services running on default ports (5432, 6379)

## Configuration

### Database Setup
\`\`\`bash
# Create database
createdb taskflow_db

# Copy environment template
cp .env.example .env

# Edit .env with your database credentials
# DATABASE_URL=postgresql://user:password@localhost:5432/taskflow_db
\`\`\`

### Run Migrations
\`\`\`bash
alembic upgrade head
\`\`\`
**Expected**: "Running upgrade ... -> ..., create initial tables"

## Running the Application

### Development Mode
\`\`\`bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
\`\`\`
**Output**:
\`\`\`
INFO:     Uvicorn running on http://0.0.0.0:8000
INFO:     Application startup complete.
\`\`\`
**Access**: http://localhost:8000/docs for API documentation

### Production Mode
\`\`\`bash
uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
\`\`\`

## Common Commands

| Command | Purpose |
|---------|---------|
| \`pytest\` | Run all tests |
| \`pytest tests/unit\` | Run unit tests only |
| \`alembic revision --autogenerate -m "msg"\` | Create new migration |
| \`alembic upgrade head\` | Apply migrations |
| \`python -m src.scripts.seed_data\` | Seed sample data |

## Verification

- [ ] Server starts without errors
- [ ] API docs accessible at http://localhost:8000/docs
- [ ] Database contains expected tables (tasks, users, activities)
- [ ] WebSocket connection works (check /ws endpoint)
- [ ] Health check returns 200: http://localhost:8000/health

## Troubleshooting

**Port already in use**:
\`\`\`bash
lsof -ti:8000 | xargs kill -9
\`\`\`

**Database connection failed**:
- Verify PostgreSQL is running: \`pg_isready\`
- Check credentials in .env file

## Tested Environment
- **OS**: macOS Sonoma 14.2, Ubuntu 22.04
- **Python**: 3.11.6
- **PostgreSQL**: 14.10
- **Redis**: 6.2.7
- **Date**: 2025-01-15
```

---

## Notes

- Keep all content concise and scannable
- Test every command before documenting
- Use actual file/directory names from the project
- Include version numbers where applicable
- Provide realistic examples, not placeholders
