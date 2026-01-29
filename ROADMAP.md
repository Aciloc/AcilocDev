
# Aciloc Roadmap: The Journey to Deterministic Creation

**Mission:** To build the first visual, semantic, full-stack compiler that treats UI and Backend as a single, coherent system.

---

## 🏁 Definition of Success
Aciloc is complete when:
1.  **A Founder** can go from Idea → Working System without hiring an agency.
2.  **A Designer** can build something that *actually runs* (not just a prototype).
3.  **A Developer** trusts the generated backend (no black boxes).
4.  **A Demo** does not collapse in production.
5.  **The Product** scales without needing a rewrite.

**Long-Term Vision:** To become the default way software systems are designed — visually, semantically, and correctly.
*Not just faster apps. Better systems.*

---

## Phase 1: The Semantic Foundation (Year 0 - 1)
*Focus: Defining the Intermediate Representation (IR) and "Design-to-Code" parity.*

### Q1-Q2: The Core Compiler & Visual Editor
- [ ] **Definition of Aciloc IR (AIR):** Create the JSON schema that represents both UI layout and Data bindings.
- [ ] **Visual Component Library:** Build the core set of "semantic" components (Input, List, Card, Modal) that have strict state definitions.
- [ ] **The "No-Hallucination" Canvas:** A drag-and-drop interface that generates AIR, not raw code.
- [ ] **Design Import:** Import Figma tokens (variables, styles) directly into the Aciloc theme engine.

### Q3-Q4: Intent-Based Generation (Prompt-to-IR)
- [ ] **AI Reasoning Agent:** Integrate LLMs (Claude/OpenAI) to generate AIR instead of code.
    - *Constraint:* AI output is validated against the schema before rendering.
- [ ] **Static Data Binding:** Visual connectors between UI components and mock JSON data.
- [ ] **Code Export V1:** Compile AIR to clean, readable React/Next.js (Frontend only).

---

## Phase 2: The Backend Unification (Year 1 - 2)
*Focus: "If the backend is weak, the product is pretending." Moving from mock data to real infrastructure.*

### Year 2, H1: The Schema & DB Layer
- [ ] **Visual Schema Designer:** Define Postgres/SQL tables visually (Entities, Relationships, Enums).
- [ ] **Auto-Migration Engine:** Changes in the visual schema apply real migrations to the dev/prod databases.
- [ ] **Secure API Auto-Generation:** The compiler automatically generates strictly typed API endpoints (TRPC/GraphQL) based on the schema.
- [ ] **Auth & Permissions Node:** Visual definition of Row-Level Security (RLS) and Role-Based Access Control (RBAC).

### Year 2, H2: Visual Logic & Automation
- [ ] **The Logic Flow Editor:** A node-based editor (n8n-style) to define backend business logic.
    - *Nodes:* `OnCreate`, `Validate`, `ExternalFetch`, `Mutate`, `SendEmail`.
- [ ] **Deterministic Wiring:** "Clicking this Button runs this Flow." No glue code required.
- [ ] **Environment Management:** One-click deployment to Preview and Production environments (Serverless architecture).

---

## Phase 3: The Automation & Integration Ecosystem (Year 2 - 3)
*Focus: Workflow orchestration and external interoperability.*

### Year 3, H1: Advanced Automation
- [ ] **Cron & Scheduled Jobs:** Visual scheduler for background tasks.
- [ ] **Webhooks & Events:** Handle incoming external webhooks visually.
- [ ] **Testing Suite:**
    - *Visual Integration Tests:* Define "User creates account" flow visually.
    - *Auto-Validation:* Aciloc ensures UI inputs match Backend schema types automatically.

### Year 3, H2: Marketplace & Extensibility
- [ ] **Component Store:** Community-submitted semantic components.
- [ ] **Logic Templates:** Pre-built backend flows (e.g., Stripe Subscription handling, KYC flows).
- [ ] **Code Ejection:** "Break glass" mechanism to export the entire full-stack repo (Terraform + Docker + Code) for self-hosting.

---

## Phase 4: Decentralization & Enterprise Scale (Year 3 - 4)
*Focus: Web3 integration and high-complexity systems.*

### Year 4, H1: The Blockchain Layer
- [ ] **Smart Contract Visualizer:** Treat Smart Contracts as just another "Backend Node."
- [ ] **Wallet Connect Components:** Semantic UI components for Web3 auth.
- [ ] **On-Chain/Off-Chain Sync:** Visual flows that index blockchain events into the local database automatically.

### Year 4, H2: The Singularity (System Maturity)
- [ ] **Full-System Optimization:** Compiler optimizations to reduce bundle sizes and database query latency.
- [ ] **Collaboration Mode:** Multiplayer editing for teams (Designer working on UI while Engineer works on Logic Flow simultaneously).
- [ ] **Enterprise Governance:** Audit logs, version history, and diffing for the entire system architecture.