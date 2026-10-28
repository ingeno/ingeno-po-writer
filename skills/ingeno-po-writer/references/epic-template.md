# Ingeno Epic Template Reference

## Document Structure

### 1. Title & Metadata Table

```
[Epic Title — product name + version + main objective in one phrase]

| Epic ID | Status | Target Quarter |
|---------|--------|----------------|
| TBD     | Draft  | Qx 20xx        |
```

**Metadata fields:**
- **Epic ID**: TBD at draft stage
- **Status**: Draft / In Review / Approved
- **Target Quarter**: e.g. Q2 2026

---

### 2. Context

2–5 bullet points. Covers: current state of the product, what triggered this epic, and why now.

---

### 3. Target Audience

One bullet per user group. Each bullet names the group and describes the specific need this epic fulfills for them.

---

### 4. Problem

2–4 bullet points. Each = one distinct problem or blocker. Focus on what cannot happen today, and why that matters now.

---

### 5. Product Outcomes

Bullet points. These are objectives — the end states that must be true once the epic is delivered. They guide all user stories. Start each with a verb (Enable, Make, Ensure, Allow...).

---

### 6. Product Metrics

Table format:

```
| Product Metric | How we measure it |
|----------------|-------------------|
| [Metric name]  | [Concrete, measurable definition with number or threshold] |
```

3–5 metrics. Each must be measurable and unambiguous (time, rate, count, threshold).

---

### 7. Scope

Two tables:

**In Scope:**
```
| In Scope — Vx | Description |
|----------------|-------------|
| [Item name]    | [1–2 sentence description of what it involves] |
```

**Out of Scope / Deferred:**
```
| Out of Scope / Deferred |
|--------------------------|
| [Item — reason or future version reference] |
```

---

### 8. Dependencies

Bullet points. For each: what is needed, why it matters, who owns it.

Format: `[What is needed] — [context/reason]. Owner: [Name / Role].`

---

## Style Guide

- **Tone**: Professional, clear, concise
- **Audience**: Internal teams (devs, PMs, ops) + external client stakeholders
- **Length**: Tight — no padding, no redundancy
- **Language**: Match the user's language (English or French)
- **Tense**: Present for current state; future/conditional for outcomes
