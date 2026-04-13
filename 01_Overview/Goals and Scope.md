
## Last updated

| Version | Date       | Author | Commit |
|---------|------------|--------|--------|
| v1.0.0  | 2026-04-09 | Tycho  |        |

---

## Purpose
Define what this documentation system aims to achieve and where its boundaries lie.

## Scope
Covers:
- Documentation structure
- Documentation workflows
- Responsibilities around documentation

Does NOT cover:
- Enforcement mechanisms (team/process dependent)
- Tool-specific constraints beyond recommendations

## Content

### Goals
- **Single Source of Truth**
  - Avoid duplicated or conflicting documentation

- **Low Friction**
  - Developers can easily create/update docs
  - Minimal overhead for maintaining documentation

- **Clarity**
  - Prefer:
    - Bullet points
    - Diagrams (Excalidraw / draw.io)
  - Avoid large blocks of text

- **Traceability**
  - Decisions are recorded (ADR)
  - Features linked to architecture and decisions

- **Fast Onboarding**
  - New developers understand system quickly via:
    - Overview
    - Architecture diagrams
    - Feature docs

- **Scalability**
  - Structure should work for:
    - Small projects
    - Large multi-feature systems

---

### Non-Goals
- Full duplication of code in documentation
- Overly detailed documentation of trivial features

---

### Key Principles
- Documentation is **part of development**, not an afterthought
- Each PR should:
  - Validate existing documentation
  - Update if necessary
- Prefer **linking over repeating information**

## References
- [[Project Summary]]
- [[Getting Started]]

### Tags:
#overview