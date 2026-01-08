# Zeniark AI Kitchen v2 — Captain Playbook (Internal)

## 1) Purpose of the Captain Role
The Captain is the single point of accountability for delivery quality, governance enforcement, and AI usage control.

The Captain does not need to write the most code.
The Captain must ensure:
- correct intent,
- controlled AI usage,
- enforced comprehension,
- and production readiness.

Rule: A project without an active Captain is non-compliant.

---

## 2) Captain Authority (Non-Negotiable)

The Captain has final authority over:
- merge approval or rejection,
- enforcement of context and comprehension gates,
- arbitration between Business and Technical context,
- declaring work non-compliant and requiring rework,
- approving or denying AI usage exceptions.

The Captain’s decisions are not overridden by developer preference or velocity pressure.

---

## 3) When a Captain Is Required
A Captain is required when:
- AI-assisted development is used,
- more than one developer is working on the repo,
- the system handles non-trivial business logic, data, or security,
- the work will reach production or client environments.

Rule: If in doubt, assign a Captain.

---

## 4) Captain Responsibilities by Phase

### 4.1 Phase 0 — Mise en Place (Before Any Build)
Captain ensures:
- repo structure is v2-compliant,
- `.specs/business` has baseline business context,
- `.specs/technical` has baseline technical context,
- `.cursorrules` is present and reviewed,
- BACP and TCP are assigned and active,
- `main` branch protection is enabled.

No build begins until Phase 0 is complete.

---

### 4.2 Phase 1 — Plan (Per Story / Cycle)
Captain must review and approve:
- the story scope (single responsibility),
- referenced business context,
- referenced technical context,
- declared AI usage scope (what AI may and may not do).

Captain questions to ask:
- Is this story narrow enough?
- Is business intent explicit?
- Is technical impact understood?
- Is AI usage justified and constrained?

If the answer to any is “no”, planning is incomplete.

---

### 4.3 Phase 2 — Build (In Progress)
Captain monitors for:
- scope creep,
- undocumented decisions,
- AI-generated large diffs without explanation,
- developers bypassing context.

Captain may:
- pause work,
- require context updates,
- require AI usage to stop and switch to manual implementation.

Rule: Velocity never overrides correctness.

---

### 4.4 Phase 3 — Comprehension Gate (Mandatory)
Before merge, the Captain must verify that the submitting developer can explain:

- overall control flow,
- data flow and state changes,
- edge cases and failure modes,
- what AI generated vs what was manually authored,
- what AI output was rejected or rewritten,
- how tests prove correctness.

If the developer cannot explain any part:
- the gate fails,
- the PR is rejected,
- remediation is required.

“No time to explain” is not an acceptable reason.

---

### 4.5 Phase 4 — QA + Merge
Captain confirms:
- acceptance criteria are met,
- tests are present and meaningful,
- specs are updated if behavior changed,
- decision log entries exist for new trade-offs,
- security baseline is respected.

Only then may the Captain approve the merge.

---

## 5) Captain Gates (Checklist Summary)

### Gate A — Context Completeness (Pre-Build)
- [ ] Business context exists and is current
- [ ] Technical context exists and is current
- [ ] Story references correct specs
- [ ] No unresolved context conflicts

### Gate B — Comprehension (Pre-Merge)
- [ ] Developer explains all logic
- [ ] AI usage is explicit and justified
- [ ] No unexplained code paths
- [ ] Tests cover behavior

### Gate C — Production Readiness
- [ ] Security baseline respected
- [ ] Performance expectations considered
- [ ] No “temporary” hacks without documentation
- [ ] Decision log updated

Failure at any gate blocks merge.

---

## 6) Handling AI Misuse (Common Scenarios)

### Scenario: Large AI-generated file with minimal understanding
Action:
- Reject PR
- Require manual rewrite or scoped AI usage
- Document lesson learned if recurring

### Scenario: AI invented business rules
Action:
- Reject PR
- Require BACP clarification
- Update business specs before continuing

### Scenario: AI introduced insecure patterns
Action:
- Immediate rejection
- TCP updates security baseline if needed
- Potential rollback of affected changes

---

## 7) Conflict Resolution (BACP vs TCP)

When business and technical context conflict:
1. Captain halts merge
2. Conflict is logged in `decision-log.md`
3. Captain evaluates:
   - regulatory/compliance impact,
   - business risk,
   - security and data risk,
   - maintainability,
   - delivery impact
4. Captain records:
   - decision,
   - rationale,
   - required follow-up actions

Rule: No merge with unresolved material conflicts.

---

## 8) Captain Anti-Patterns (What NOT to Do)

A Captain must not:
- rubber-stamp PRs,
- approve code they do not understand,
- allow AI to “figure it out”,
- trade long-term quality for short-term speed,
- bypass gates to “unblock the team”.

If a Captain bypasses gates, the system has already failed.

---

## 9) Captain Success Metrics (Internal)

A Captain is successful when:
- defects decrease over time,
- rework decreases over time,
- AI usage becomes more targeted and effective,
- developers demonstrate increasing understanding,
- specs become clearer instead of stale.

Speed alone is not a success metric.

---

## 10) Escalation and Overrides
In exceptional cases (critical incidents, deadlines):
- Captain may approve a controlled exception,
- exception must be documented,
- remediation plan must be defined,
- follow-up review is mandatory.

Rule: Exceptions are visible, rare, and temporary.

---

## 11) Captain Mindset (Final Word)
The Captain is not a bottleneck.
The Captain is the quality amplifier.

Zeniark AI Kitchen v2 only works when Captains enforce it consistently.
