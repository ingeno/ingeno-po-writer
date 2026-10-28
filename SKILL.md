---
name: "ingeno-po-writer"
description: "Write Ingeno product epics, user stories and epic breakdowns (story maps), from raw notes or from scratch. Use for any request to write, draft or create an epic, a user story, acceptance criteria or a feature ticket (\"write a story for X\", \"rédige une story\", \"make a ticket for Y\"), to split an epic into stories or plan a sprint (\"découpe l'epic en stories\", \"what stories do we need\"), or to \"grill me\" on an epic or story. French and English."
---

# Ingeno PO Writer — Epics, User Stories & Story Maps

Three artifacts, one flow: **draft → grill → generate**.

| Artifact | When | Output |
|---|---|---|
| **Epic** | A larger initiative: context, audience, problem, outcomes, metrics, scope, dependencies | Markdown (Jira / Confluence) by default; Word .docx for a client deliverable or on request |
| **Story map** | The user has an epic and wants its stories, or asks for several stories at once (lightweight map if there's no epic) | Markdown story map, then stories one at a time |
| **User story** | One capability, shippable and demoable in ≤ 5 days | Markdown, paste-ready for Jira / Confluence / Notion |

If it's unclear whether the user wants an epic or a story, ask one question: *« Est-ce qu'on écrit un epic complet ou une user story ? »*

**Language**: answer in the language of the user's latest message (FR or EN). Keep product, tool, client and role names exactly as given — never translate them.

---

## The flow: draft → grill → generate

### 1. Draft first

- Before asking anything, use what's available: the user's notes, a pasted partial template, the epic, the earlier conversation — and, when a question can be answered there, shared documents or a connected tool (Jira, Confluence, Drive). Never re-ask what's already answered.
- Map it all onto the artifact's template and write a **complete draft** right away, with a working title.
- What the user did not state is marked, never presented as fact:
  - `[assumption: …]` — only for framing you can reasonably infer: context wording, the role, scope phrasing, the title.
  - `[à compléter]` (or `[to fill]`) — for every factual item: edge cases, error states, metric targets and baselines, dependencies, owners, dates, requirement IDs. These are never guessed inline; they go to the grilling rounds.
  - If most of a section would be assumptions, leave the whole section `[à compléter]` and grill it instead.
- Exception: if the user gave only a feature name or a single line, first ask the two questions a draft can't do without — **who** it's for and **what outcome** it must achieve — then draft.
- Every section of the template is required. Only the optional items (the story's **Epic** and **Requirements** lines, **Scenarios**, `Req. ref` columns) may be omitted.

### 2. Grill in rounds

Grilling turns every open point into a question **with a recommended answer**, so the user reacts instead of writing from scratch.

1. **List the open points**: every `[assumption]` and `[à compléter]`, every vague item, every failed coherence check, every unmet minimum (e.g. fewer than 2 edge cases).
2. **Order them as a decision tree**: some answers depend on others (the role before the permission edge cases; the outcomes before the metrics). Each round asks only the questions whose prerequisites are settled — up to ~6 per round, the ones that unblock the most first.
3. **Format each round** like this (illustrates the format only — never reuse its content):

```
**Ronde 1 — 3 questions.** « oui » = j'accepte tout · sinon réponds par numéro (ex. « 1 oui, 2 : plutôt … »).

1. **Rôle** — « Un utilisateur » est trop large : qui fait l'action, avec quels droits ?
   → Recommandé : le planificateur de production, avec droits d'écriture sur son usine.
2. **Double soumission** — Que se passe-t-il si la demande est envoyée deux fois ?
   → Recommandé : la 2e est bloquée avec le message « Demande déjà soumise ».
3. **Cible de la métrique** — « Moins d'erreurs », c'est combien ?
   → Recommandé : < 2 % de demandes en erreur après 30 jours ; baseline à mesurer avant le lancement (owner : PO).
```

4. « oui » accepts every recommendation of the round. When the user answers by number, the numbers they don't mention stay open and come back in the next round.
5. After each round, update the draft and show **only the sections that changed**, then move to the next round.
6. **Stop** when no open point remains, or when the user says to generate. If the user answers « je ne sais pas » twice on the same point, leave it marked (`[assumption: …]` or `[à compléter]`) in the final output and move on.

Grilling rules:
- Recommended answers come from what the user has shared plus sound product judgment. They become content **only once the user accepts them**.
- For facts you can't know (baselines, dates, owners, client constraints, requirement IDs), the recommendation is a method or a next step — « baseline à mesurer, owner : PO » — never a made-up value.
- Ask product questions, not form-filling ones. ✗ « Qu'est-ce que tu veux mettre dans Contexte ? » ✓ « Qu'est-ce qui se passe si on livre ça dans 6 mois ? »
- Don't accept vague answers (« les utilisateurs », « ça doit juste marcher »): put a sharper question with a concrete recommendation in the next round.
- If the user asks for « une question à la fois », switch to one question per message, still with a recommended answer.

**Fast path.** If the user wants « juste un brouillon » or to skip the questions: deliver the draft with its markers, followed by the numbered list of open points with recommended answers (including unmet minimums and, for an epic, the Markdown-or-Word choice). No rounds, no stress test, and no invented criteria to reach the minimums.

### 3. Generate

When no open point remains, or the user says to generate:
1. **Re-run the coherence checks** — later answers can break earlier ones. Any new gap → one more round.
2. **Output the full artifact** in its final format. This is also the user's full review: they can still ask for changes.
3. **Offer the stress test** (below).

For a Word .docx: show the full Markdown version first, offer the stress test, and build the file only once the user confirms.

Output rules: exact template format; no preamble or commentary inside the artifact; empty optional items omitted; unresolved markers stay visible.

### Stress test

Hard questions on the weakest points (angles listed per artifact below) — as if defending the artifact in front of a skeptical client (epic) or a dev/QA who must build and test it (story). Same numbered format with recommended answers; follow up wherever an answer opens a new issue, round after round, until every branch is resolved.

Always offer it for an epic; for a story, offer it only if the story is complex (3+ workflows, branching on role or state, external integration). The user can say **"grill me"** at any time: it runs the stress test on the current draft, and pending open points stay listed. If the stress test changes something, output the updated artifact.

---

## Guardrails (apply throughout)

- **Never invent content.** Factual items come from the user, from a source you looked up, or from a recommended answer the user accepted.
- **Size check.** A story must be shippable and demoable in ≤ 5 days. A "story" bigger than that, or with several outcomes, is an epic in disguise → flag it before going further and propose either splitting it into named stories or an epic + story map. An "epic" that is a single ≤ 5-day capability → propose a story instead.
- **Several stories requested at once** → story map first (Part 2) — a lightweight one if there's no epic — then write them one at a time.
- **Artifact switch mid-flow** (« finalement, faisons-en un epic ») → confirm, carry over everything already collected, continue from there.
- **Untestable or contradictory scope the user insists on** → raise the conflict once with a proposed fix; if they still insist, generate as asked and mark the item `[flagged: …]`.
- **Out of PM scope** (mockups, code, architecture decisions) → say so plainly, write the PM part, and record the rest as a dependency or open question.
- **Requirement references** (e.g. BR-121): include only when the client has a requirements document with IDs. Never invent an ID.

---

# PART 1 — EPIC

## Epic template

```
# [Title — product + version + main objective in one phrase]

| Epic ID | Status | Target Quarter |
|---------|--------|----------------|
| TBD     | Draft  | Qx 20xx        |

## Context
- [What exists today — live, pilot, not built]
- [What triggered this epic, and why now]
- [Why current alternatives or workarounds are not enough]

## Target Audience
- **[Group]** — [what they can't do (well) today that this epic fixes]

## Problem
- [Distinct blocker — who is affected, how often / how badly / at what scale, cost of doing nothing]

## Product Outcomes
- [Verb-first end state — Enable / Make / Ensure / Allow …]

## Product Metrics
| Product Metric | How we measure it |
|----------------|-------------------|
| [Metric] | [Data source + target number or threshold + baseline if known] |

## Scope — V[x]
**In Scope**
| Item | Description | Req. ref |
|------|-------------|----------|
| [Item] | [1–2 sentences] | [BR-xxx] |

**Out of Scope / Deferred**
- [Item — reason or target version]

## Dependencies
- [What is needed] — [why; which Scope item it affects]. Blocking | Parallel (by [date]). Owner: [name / role].
```

Drop the `Req. ref` column when there are no requirement IDs.

**Style**: concise, no padding — read by devs, PMs and ops as well as client stakeholders. Present tense for the current state; future or conditional for outcomes.

## Epic sections — what good looks like

Use these angles to write grilling questions and recommended answers.

- **Context** (2–5 bullets): what exists, what triggered the epic, why now, why alternatives fall short. Probe: what changed recently? Are there prerequisites to meet first? What happens if this slips a quarter?
- **Target Audience**: one bullet per group *that uses it differently or has different constraints*. Probe: who is affected? Do groups need different things? Is anyone currently excluded who must be included?
- **Problem** (2–4 bullets): real blockers, not nice-to-haves, with frequency, severity or scale. Probe: what can't happen today? What does it cost, and to whom? What's the risk if nothing is done? One problem with several facets, or several problems?
- **Product Outcomes**: end states, not features; verb-first; quantified targets where possible. Probe: once delivered, what's true that isn't today — for each group? How would you justify this epic to a stakeholder?
- **Product Metrics** (3–5): every metric has a number, threshold or time target — push until it does. Probe: what would you look at? Baseline today? Who collects the data? What result would mean failure?
- **Scope**: a commitment — honest and precise. Probe: what must be built for "done"? What could be simplified or deferred without blocking the main goal? What came up but should wait? Anything depending on work that isn't ready? Any UI/UX constraint?
- **Dependencies**: client inputs, approvals, decisions or research, other teams, technical prerequisites, assets (templates, configurations), regulatory or regional rules. For each: what, why, owner, blocking vs parallel (with date), which Scope item it affects.
- **Title & metadata**: the draft carries a working title; finalize it (product + version + main objective) once the content is settled. Epic ID = TBD; Status = Draft; Target Quarter → `[à compléter]` and ask if unknown.

## Epic coherence checks

Each failure becomes a grilling question.
1. The Context explains why the Problems exist.
2. Every Problem is addressed by at least one Outcome.
3. Every audience group has at least one Outcome and one In Scope item.
4. Every Outcome has at least one In Scope item that delivers it, and is still achievable after what was deferred to Out of Scope; every In Scope item serves an Outcome.
5. The Metrics measure the Outcomes, not just activity.
6. Every Dependency points to the Scope item it affects.

## Epic stress-test angles

Is the urgency real — what concretely happens if delayed 6 months? · Is anyone left out who will complain later? · Is the problem a root cause or a symptom? · Are the outcomes achievable within this epic? · Can the metrics be measured with what exists today, and who collects the data? · Is the scope realistic for the target quarter — what should be deferred? · Worst case if a dependency is late — is there a fallback?

## Epic output format

Default: Markdown per the template. Produce a **Word (.docx)** when the user asks for it or the epic is a client deliverable — if that's unclear, ask it in the last round (fast path: in the open-points list), with « → Recommandé : Markdown pour Jira ».

For the .docx (after the confirmation described in Generate): read the environment's docx skill before writing any code. A4, Arial throughout · title = Heading 1, sections = Heading 2 · metadata = 3-column table with light-blue header · Context, Target Audience, Problem, Outcomes, Dependencies = bullets · Metrics = 2-column table with light-blue header · In Scope = table (Item | Description, plus Req. ref when used) · Out of Scope = 1-column table · language of the conversation. Save as `epic-[slug-of-title].docx` and send it to the user.

---

# PART 2 — EPIC BREAKDOWN (STORY MAP)

## Principles

- **One story = one deliverable capability, ≤ 5 days.** Hard rule. Test: "Could a developer ship and demo this independently within a week?" If not, split it.
- **Group by Product Outcome, not by technical layer.** Every story serves an Outcome of the epic, and every Outcome has at least one story. A story that serves no Outcome probably doesn't belong in this epic.
- **Scope drives the stories.** Every In Scope item is covered by at least one story; no story touches an Out of Scope item.
- **Dependencies are explicit and sequenced.** A story that depends on another comes after it; work that can run in parallel is marked; a story blocked by an unresolved epic dependency is flagged and cannot start.
- **No Outcomes, no map.** If the epic has no usable Product Outcomes, don't fabricate them — offer to grill the epic's Outcomes first.

**No epic?** When the user wants several stories without an epic, build a lightweight map: one table with # | Story | One-line scope | Est. | Depends on. No Outcome grouping, no coverage sections. Then write the stories one at a time.

## Breakdown flow

1. Read the whole epic (document, pasted text, or one built earlier in the conversation). Extract Outcomes, Scope In/Out and Dependencies.
2. **The draft is the story map** below. Grill on: stories likely to exceed 5 days, uncovered scope items, Outcomes with no story, unclear dependencies, stories that could run in parallel, the order to write them in, and — as one question — whether any story should be split by technical layer.
3. Once the map is confirmed, write the stories one at a time with Part 3. Each story inherits the epic link, its Outcome and its requirement refs; its Context is written for the story itself (the specific gap it closes), not copied from the epic.

## Story map format

```
## Story Map — [Epic title]

### Blocking dependencies from the epic
- [Dependency] — blocks Story X until resolved. Owner: [name / role].

### Outcome 1: [Outcome from the epic]
| # | Story | Est. | Depends on | Req. ref | Notes |
|---|-------|------|------------|----------|-------|
| 1 | [Title] | ~X d | — | [BR-xxx] | [Rationale; "parallel with #2" if applicable] |

### Outcome 2: [Outcome from the epic]
| # | Story | Est. | Depends on | Req. ref | Notes |
|---|-------|------|------------|----------|-------|

### Scope coverage
- [In Scope item] → Story X, Y

### Flagged
- [Uncovered scope item, Outcome with no story, story over 5 days, unresolved dependency, or other concern]
```

Estimates are rough (1–5 days). Flag any story whose scope is vague enough to blow the estimate. Drop the `Req. ref` column when there are no requirement IDs.

## Technical layer split (optional — only if accepted)

Split a story into sub-stories only for the layers that actually apply:
- **Front End** — UI, forms, views, client state, client-side validation.
- **Back End** — business logic, APIs, data processing, server-side validation, integrations.
- **Infra / Platform** — provisioning, IAM / permissions, environment config, automation, CI/CD.

Each sub-story inherits the parent's Context; its Functionality and criteria are scoped to its layer; it stays ≤ 5 days and independently testable, with cross-layer dependencies stated. Present the split as an addendum to the map before writing the sub-stories.

---

# PART 3 — USER STORY

## Story template

```
## [Title — short, action-oriented]

**Product Outcome:** [One sentence — the value this story delivers.] (→ Epic outcome: [Outcome from the epic])

**Epic:** [Epic name]

**Requirements:** [BR-xxx]

### Context
[2–5 sentences: what exists today, what is broken, missing or manual, who is affected and what it costs them, why now. The "why" — not a summary of the feature.]

### Functionality
As a [specific role in context], I want [capability] so that [concrete outcome for that person].

This includes:
- [Workflow or sub-capability]

### Acceptance Criteria
**Happy Path**
- [ ] [Specific, testable condition]

**Edge Cases**
- [ ] [Condition]

**Error States & Failure Modes**
- [ ] [Condition]

**Out of Scope**
- [ ] [What this story explicitly does not cover]

### Scenarios
**Scenario: [Flow name]**
- Given [state]
- And [additional condition]
- When [action by the role]
- Then [observable outcome]
```

Omit the "(→ Epic outcome …)" part, the **Epic** and **Requirements** lines when there's no epic or no requirement IDs, and the whole **Scenarios** block when no scenarios were written.

## Story sections — what good looks like

Use these angles to write grilling questions and recommended answers.

- **Product Outcome**: one sentence of value for this story, not a restatement of the feature; when part of an epic, point to the epic Outcome it serves.
- **Context**: a specific gap and a real urgency. Reject « améliorer le processus » or « les utilisateurs ont de la difficulté ». Probe: what's manual or broken today? Who pays for it — time, risk, errors? What if it isn't in this sprint?
- **Functionality**: the role is specific (never just « un utilisateur » or « un admin »), the "so that" is concrete. Each "This includes" item is one workflow; flag any item that could be its own story. Probe: several entry points, permission levels, data states?
- **Acceptance Criteria — minimums** (missing ones become grilling questions):
  - ≥ 1 happy-path criterion per Functionality item (output or state change that proves it worked; SLA if any)
  - ≥ 2 edge cases
  - ≥ 2 error states (what the user sees; recovery path: retry, fallback, who to contact)
  - ≥ 1 out-of-scope boundary (something a dev might reasonably assume is included but isn't)

**Edge-case bank by feature type** — use it to write the *right* recommended answers; only what applies, and it enters the story only once the user confirms it.
- **CRUD / data entry**: empty submission, max-length input, duplicate record, editing a record someone just changed, deleting a record referenced elsewhere.
- **Workflow / approval**: approver absent, approved and rejected near-simultaneously, recalled after submission, step skipped or reordered, self-approval.
- **External integration**: partial response, timeout, stale data, rate limiting, "success" with an unexpected payload.
- **Upload / file**: unsupported format, too large, corrupted, interrupted upload, duplicate filename.
- **Permissions / roles**: can see but can't act, role changed mid-session, lower role attempting an elevated action, conflicting per-user rights on a shared resource.
- **Batch / bulk**: partial success, empty selection, very large selection, partial rollback.
- **Real-time / concurrency**: two users on the same item, request while another is in progress, out-of-order events, session expiry mid-action.

**Scenarios (Given-When-Then)** — optional. Recommend them (as a grilling question) when the story has 3+ workflows, branches on role, state or permission, or has concurrency or integration edge cases; skip them for simple single-path stories. One scenario per meaningful flow — at least the main happy path, the most important edge case and the most likely failure. Steps are concrete and observable. Every scenario traces to an existing criterion and introduces no new behaviour.

## Story coherence checks

Each failure becomes a grilling question.
1. The Context explains why the Functionality is needed.
2. Every Functionality item has at least one happy-path criterion.
3. Edge cases come from the described workflows, not generic placeholders.
4. Every external dependency or permission boundary has an error state.
5. The out-of-scope boundaries leave no room for a dev to add something unintended.
6. Every scenario maps to a criterion.
7. If part of an epic, the Product Outcome points to one of the epic's Outcomes.
8. The story is independently executable: a developer who has never heard of the feature knows what to build, how to test it and where it stops.

## Story stress-test angles

Is the urgency in the Context real and specific? · Is the role precise enough that two different people couldn't both think it means them? · Could any "This includes" item be read two ways? · Is there an implicit step in the happy path? · What's the weirdest valid thing a user could do? · What's most likely to break in production — is there a criterion for it? · What related feature could a dev assume is implied?

## Story output rules

- Clean Markdown in the exact template — copy-paste ready for Jira, Confluence or Notion.
- No commentary or headers outside the template.
- Language of the conversation.