# Zeniark AI Kitchen v2 — Developer Field Guide (Internal)

## 1) Purpose
This guide defines how developers must work in Zeniark AI Kitchen v2 when using AI-assisted development.

The goal is not “more AI.”
The goal is correct, secure, production-ready software with enforced human understanding.

If you cannot explain your code, you cannot merge your code.

---

## 2) Non-Negotiable Developer Rules

1) **Context First**  
You may not implement or generate code without referencing current context in `/.specs`.  
If context is missing or unclear, you must request clarification and update specs before coding.

2) **Narrow AI, Not Wide AI**  
AI usage must be small, scoped, and diff-friendly.  
Large AI-generated code dumps are non-compliant.

3) **No AI Guessing**  
AI must not infer business rules.  
If business rules are not explicit, stop and escalate to BACP.

4) **No New Patterns Without TCP**  
You may not introduce new libraries, architectures, or patterns unless documented by TCP or explicitly approved by the Captain.

5) **Comprehension Gate Is Mandatory**  
You must be able to explain every line you submit:
- control flow
- data flow
- edge cases
- failure modes

---

## 3) Where Truth Lives (What to Read Before You Code)

### Business Truth (BACP)
Located in:
- `/.specs/business/business-requirements.md`
- `/.specs/business/use-cases.md`
- `/.specs/business/acceptance-criteria.md`
- `/.specs/business/business-glossary.md`
- `/.specs/business/regulatory-notes.md`

### Technical Truth (TCP)
Located in:
- `/.specs/technical/architecture.md`
- `/.specs/technical/security-baseline.md`
- `/.specs/technical/coding-standards.md`
- `/.cursorrules`

Rule: If it is not documented in specs, it is not authoritative.

---

## 4) AI Usage Boundaries

### 4.1 Always Allowed (within documented context)
- unit and integration test generation
- small refactors (naming, extraction, dead code removal)
- scaffolding and boilerplate
- documentation drafts (non-authoritative until reviewed)
- small helper functions with explicit inputs/outputs

### 4.2 Restricted (Captain or TCP approval required)
- data model changes or migrations
- query optimization and performance tuning
- complex state management changes
- cross-cutting refactors
- introducing new dependencies or frameworks
- modifying authentication or authorization flows

### 4.3 Forbidden (unless exception + documented risk)
- inventing business logic not in `/.specs/business`
- implementing authorization rules from assumptions
- security-sensitive logic (crypto, token validation, permissions) without TCP direction
- architectural rewrites
- automation that bypasses human review

If you believe an exception is required, escalate to the Captain and log the decision.

---

## 5) Mandatory AI Prompt Format

Any AI prompt that affects code must reference **both** business and technical context.

### Minimum Prompt Template

**Business Context:**
- `/.specs/business/<relevant-file>.md`

**Technical Context:**
- `/.specs/technical/<relevant-file>.md`
- `.cursorrules`

**Task:**
- Describe the exact, narrow change required

**Constraints:**
- do not invent business rules
- do not introduce new technical patterns
- produce a small, reviewable diff
- include or update tests
- ask for clarification if context is insufficient

If you cannot fill in the context sections, you are not ready to code.

---

## 6) Comprehension Gate (What You Must Explain)

Before a PR can be approved, you must be able to explain:

- what the change does and why
- which acceptance criteria it satisfies
- control flow
- data flow
- edge cases and failure modes
- what AI generated vs what you authored
- what AI output you rejected or rewrote
- how tests demonstrate correctness

Failure to explain any of the above will result in PR rejection.

---

## 7) Pull Request Hygiene

### Do This
- keep PRs small and focused
- reference relevant business and technical specs
- describe business impact in the PR summary
- include tests and explain coverage
- update specs when behavior changes
- log decisions when trade-offs are made

### Avoid This
- large “everything at once” PRs
- AI-generated code without explanation
- changes that contradict specs
- undocumented security behavior
- “works on my machine” justifications

---

## 8) When to Stop and Escalate

Stop and escalate to the Captain, BACP, or TCP when:
- business rules are ambiguous
- acceptance criteria are missing or unclear
- changes impact authentication, permissions, or data classification
- multiple modules are affected
- AI suggests a new library or architectural pattern
- you cannot fully explain the generated output

Escalation is a quality action, not a failure.

---

## 9) Definition of Done (Developer)

A story is considered done only when:
- acceptance criteria are met
- tests are updated and meaningful
- specs are updated if behavior changed
- decisions are logged if trade-offs occurred
- you can explain the code end-to-end
- Captain gates are satisfied

Zeniark AI Kitchen v2 optimizes for correctness and durability over short-term speed.
