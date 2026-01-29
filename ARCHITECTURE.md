
# Aciloc System Architecture

**Core Philosophy:**
Aciloc is not a code generator; it is a **system compiler**.
We do not glue strings of code together; we manipulate a deterministic **Intermediate Representation (IR)** of the full stack.

---

## 1. High-Level Diagram

```mermaid
graph TD
    User[Developer / Designer] -->|Interacts with| Visual[1. Visual Layer]
    Visual -->|Extracts Intent| Semantic[2. Semantic Layer]
    Semantic -->|Compiles to| IR[3. Intermediate Representation (IR)]
    
    subgraph "Aciloc Compiler"
        IR -->|Validates & Compiles| Compiler[4. Compilation Layer]
    end
    
    subgraph "5. Runtime / Execution Layer"
        Compiler -->|Generates| FE[Frontend App]
        Compiler -->|Generates| BE[Backend / API]
        Compiler -->|Generates| DB[Database / Store]
        Compiler -->|Generates| Workflow[Workflows / Jobs]
        
        FE <-->|Typed API| BE
        BE <--> DB
        BE --> Workflow
    end
```

---

## 2. Aciloc’s Internal Model (The 5 Layers)

Aciloc operates on five distinct layers. Each layer transforms intent into reality with increasing specificity.

### Layer 1: The Visual Layer
*Where the user interacts.*
*   **UI Components:** Semantic elements (Cards, Forms, Lists) not just raw HTML/CSS.
*   **Flow Nodes:** Logic blocks for backend processes.
*   **Connections:** Visual lines representing data flow and control flow.

### Layer 2: The Semantic Layer
*Where intent is extracted.*
*   **Intent Extraction:** Translating "User drags a line from Form to Database" into "Create Record Action".
*   **Meaningful Abstractions:** Understanding that a field named "Email" has specific validation rules, not just a string type.
*   **Domain-Specific Logic:** Capturing business rules before they become code.

### Layer 3: The Intermediate Representation (IR)
*The immutable source of truth.*
*   **Structure:** A strictly typed JSON/Graph structure.
*   **Properties:**
    *   **Versioned:** Every change is a commit.
    *   **Diffable:** You can see exactly what changed in the system logic.
    *   **Auditable:** Full history of who changed what logic node.
*   *This layer prevents hallucinations. If it's not in the IR, it doesn't exist.*

### Layer 4: The Compilation Layer
*Where code is assembled.*
*   **Frontend Assembly:** React/Next.js code generated from UI + State definitions.
*   **Backend Generation:** Node/Go specific logic derived from Flow Nodes.
*   **Workflow Logic:** Orchestration rules committed to code.
*   **Guarantees:** Type safety, Referencial integrity (no broken links), and Schema validation.

### Layer 5: The Runtime / Execution Layer
*Where the system runs.*
*   **Real Infrastructure:** Not a simulation. Real Postgres, Real Redis, Real Docker containers.
*   **Real Data:** Production-grade persistence.
*   **Real Guarantees:** Transactionality, Scalability, and Security.

---

## 3. Key Technical Decisions

### A. Determinism Over Intelligence
The Compiler is **deterministic**. Given the same IR, it produces the exact same code every time.
AI is used only in **Layer 1 (Visual)** and **Layer 2 (Semantic)** to help the user express intent. It explicitly **does NOT touch Layer 4 (Compilation)** directly.
*   *AI suggests the graph; The Compiler builds the system.*

### B. The "No Glue Code" Rule
Developers spend 50% of their time writing "glue code" (API clients, type definitions, database migrations).
Aciloc eliminates this by sharing the **Same Source of Truth (IR)** across the full stack.
*   The Frontend knows the Backend's types because they were born from the same parent.

### C. Security by Definition
Security rules (RLS, Permissions) are defined in the **Semantic Layer**.
Because they are part of the core definition, the Compiler injects them into *every* relevant API endpoint and Database query. You cannot "forget" to add auth checks.

---

## 4. Deployment Pipeline
1.  **Snapshot:** Current IR is locked.
2.  **Validation:** Checker ensures no cycles in logic or type mismatches.
3.  **Build:** Code is generated in a clean container.
4.  **Provision:** Infrastructure is updated (Terraform/Pulumi).
5.  **Live:** Atomic deployment.