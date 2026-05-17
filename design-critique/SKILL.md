---
name: design-critique
description: Run a structured design critique on a UI screenshot, Figma frame, or described interface. Covers usability, information hierarchy, consistency, actionability, and edge cases. Use this skill proactively whenever someone shares a design, screenshot, or Figma link and asks for feedback — even informal requests like "what do you think?", "how does this look?", "anything wrong here?", "quick thoughts?", or "can you review this?". Also trigger when someone is preparing for a stakeholder review, user research session, or design handoff and wants to sense-check their work before the milestone.
---

## Overview

Run a structured design critique grounded in what the user is trying to achieve. Focus on real problems, not aesthetic preferences. Be direct and specific — cite what you see, not what you imagine.

---

## Step 1 — Gather context

Before critiquing, check if you have:
- **The design** — screenshot, Figma URL, or description
- **The user and job** — who uses this, what are they trying to do?
- **The stage** — early concept, hi-fi prototype, or near-production?
- **Known constraints** — design system, accessibility requirements, platform (desktop/mobile)

If any of these are missing and they would materially change the critique, ask one focused question before proceeding. Do not assume — ask. Do not ask more than one question at a time.

If context is available from open files or prior conversation (e.g. a discovery plan, PRD, or user research doc), read it before critiquing — ground the feedback in stated goals and known user assumptions.

---

## Step 2 — Run the critique

Be thorough. Cover every meaningful issue you can identify — err on the side of depth rather than curation. A designer can decide what to act on; your job is to surface everything that might matter. Structure feedback under these lenses. Skip any lens that is not relevant to this design.

### What's working
Lead with this. Be specific — say what works and why. Do not pad this section; only include genuine strengths.

### Critical issues
Problems that will cause user failure, trust loss, or implementation blockers. These must be fixed before research, handoff, or build. Call out:
- Data/filter disconnects (e.g. a date picker that doesn't control visible data)
- Missing states (empty, error, loading)
- Broken flows (no way to complete a task)
- Contradictions between what the UI implies and what it does

### Usability issues
Things that will confuse or slow users but won't cause failure:
- Ambiguous labels or missing context
- No escape hatches ("view all", cancel, back)
- Inconsistent status conventions
- Information hierarchy that doesn't match user priority

### Consistency and system fit
- Does it match the design system (spacing, colour, typography, component usage)?
- Are patterns consistent within the screen (e.g. badge styles, column alignment)?
- Does it feel like the same product as adjacent screens?

### Data and edge cases
- What does this look like with no data, sparse data, or a very large dataset?
- Are any numbers in the prototype unrealistic (skewing what the design looks like)?
- Are any charts or tables dependent on backend data that may not be ready at launch?

### Questions to probe in user research
If this design will be tested with users, list 3–5 specific questions to ask during sessions, grounded in unresolved assumptions visible in the design.

---

## Step 3 — Prioritise

End with a **Priority fixes** summary: a short list of the 2–4 things that must change before the next milestone (research session, stakeholder review, handoff, or build). Be explicit about which milestone.
