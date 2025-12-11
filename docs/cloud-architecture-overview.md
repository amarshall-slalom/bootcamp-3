# Cloud Architecture Overview

## Monorepo Architecture

```mermaid
graph TD
  A[Monorepo Root] --> B[Frontend Package]
  A --> C[Backend Package]

  subgraph Frontend
    B1[React App]
    B2[UI Components]
    B3[Local Storage]
    B --> B1
    B1 --> B2
    B1 --> B3
  end

  subgraph Backend
    C1[Express Server]
    C2[API Routes]
    C --> C1
    C1 --> C2
  end

  U[User Browser] --> B1
  B1 -. dev only .-> C1

  style A fill:#f5f5f5,stroke:#212121,stroke-width:1px
  style B fill:#1976d2,stroke:#212121,stroke-width:1px,color:#fff
  style C fill:#ff9800,stroke:#212121,stroke-width:1px,color:#fff
  style U fill:#9e9e9e,stroke:#212121,stroke-width:1px,color:#fff
  style B3 fill:#9e9e9e,stroke:#212121,stroke-width:1px,color:#fff
```

- Monorepo contains two packages: frontend (React) and backend (Express).
- Frontend manages UI and persists tasks in local storage.
- Backend provides an API server for future use; MVP operates without backend persistence.
- User interacts with the React app in the browser; backend may be used in development.

## Create TODO Sequence

```mermaid
sequenceDiagram
  participant User as User
  participant Browser as Browser App
  participant LocalStore as Local Storage
  participant API as Backend API
  participant DB as Database

  User->>Browser: Open app
  Browser->>LocalStore: Load existing tasks
  Note right of Browser: MVP uses local storage only

  User->>Browser: Create TODO (title, priority, due date)
  Browser->>Browser: Validate input (title required)
  alt Valid input
    Browser->>LocalStore: Save task
    LocalStore-->>Browser: Confirm saved
  else Invalid input
    Browser-->>User: Show validation error
  end

  opt Post-MVP with backend
    Browser->>API: POST /tasks
    API->>DB: Insert task
    DB-->>API: Write success
    API-->>Browser: Task created
  end
```

- Sequence shows user creating a TODO.
- MVP persists locally; optional post-MVP shows backend flow.
