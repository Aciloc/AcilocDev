# Contributing to Aciloc

**Thank you for helping us build the visual compiler.**

Aciloc is not just another open-source project. We have a strict philosophy: **System > Code.**
Please read this carefully before opening a PR.

---

## 🛑 The Golden Rules

1.  **No "Glue Code"**: Do not simply write code to connect A to B. If a connection is needed, it must be defined in the **Intermediate Representation (AIR)** so the system can reason about it.
2.  **Determinism First**: If your code produces different outputs for the same input, it will be rejected. The compiler must be deterministic.
3.  **The Backend is Sacred**: Do not compromise backend security or type safety for a "nice UI feature." The generated backend must be production-grade.

---

## 🛠 Architectural Integrity

*   **Do not bypass the IR**: If you add a feature to the Visual Editor, it *must* emit a corresponding node in the AIR. Do not hack the runtime directly.
*   **Layer Separation**: Respect the 5-layer model (Visual -> Semantic -> IR -> Compiler -> Runtime).
    *   *Example:* The "Visual Layer" should not know about "SQL migrations." It only knows about "Entities." The "Compiler" handles the translation.

---

## 📝 Commit Standards

We follow [Conventional Commits](https://www.conventionalcommits.org/):

*   `feat: add new node type for Auth`
*   `fix: resolve race condition in compiler`
*   `docs: update architecture diagram`
*   `refactor: optimize graph traversal`

**Do not push vague commits like "fixes" or "wip".**

---

##  workflow

1.  **Fork & Clone**: Fork the repo and work on a feature branch.
2.  **Test**: Ensure the `compiler` tests pass.
3.  **PR**: Open a Pull Request. Explain *why* this change is needed, effectively linking it to the Roadmap.
