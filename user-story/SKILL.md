---
name: user-story
description: Creates development-ready user stories in a structured template for healthcare product work. Use this skill whenever someone asks for a user story, a Jira ticket, acceptance criteria, or a story writeup — even informal requests like "can you write this up as a ticket?", "give me the AC for this", "write a story for X feature", "I need a dev-ready ticket", or "turn this into a story". Also trigger when someone describes a feature or requirement and needs it turned into a structured deliverable with background, problem, solution, acceptance criteria, and QA scenarios.
---

## Story Structure

Every story follows this sequence of emoji-labelled sections. See `template.md` for the fill-in version.

| Section | Emoji | Purpose | Optional? |
|---|---|---|---|
| Background / Context | 📝 | Why this work exists; what preceded it | No |
| Problem | ❓ | What is broken or missing today | No |
| Impact | ⚠ | Consequence of the problem (user or business) | No |
| Proposed Solution | 💡 | Summary of the intended solution; may include informal "As a user / When / Then" statements | No |
| Figma Designs | 🖼 | Screenshots of relevant Figma frames | Yes — only when frames exist |
| User Story | 👤 | Formal Mike Cohn statement (see below) | No |
| Acceptance Criteria | ✅ | Bulleted functional requirements (not Gherkin) | No |
| QA / Test Scenarios | 🔍 or 🧪 | Numbered test cases with step-by-step actions | No |
| Dependencies | 🔗 | Other tickets, components, or decisions this story relies on | Yes — include when blockers exist |
| Open Questions | ❔ | Unresolved decisions that must be answered before or during dev | Yes — include when unknowns exist |

---

## The User Story Statement (Mike Cohn Format)

The `👤 User Story` section contains one formal statement:

```
As a [role],
[when <context>],
I want [action or outcome],
so that [benefit].
```

Use a specific role where possible (care manager, clinician, admin, resident) rather than a generic "user". Add a qualifier in the "when" clause to anchor the context.

**Good:**
> As a care manager,
> when reviewing a resident's care plan,
> I want to see flagged quality gaps with suggested improvement actions,
> so that I can prioritise and act on issues before they escalate.

**Avoid:**
> As a user, I want to see gaps, so that I can fix them. *(too vague — no role, no context, no outcome)*

---

## Acceptance Criteria Format

AC is written as **bulleted functional requirements**, not Gherkin. Use plain declarative language:

```markdown
✅ Acceptance Criteria

- Quality gaps page is accessible from the main navigation
- Page displays gaps in chronological order with category, severity, and date raised
- Each gap shows an improvement action if one has been assigned
- Empty state is shown when no gaps exist for the selected service
- Filter persists across page refreshes within the same session
```

**Rules:**
- One bullet per testable requirement
- Use present tense ("displays", "is accessible", "applies")
- Group related requirements under a sub-heading if there are many (e.g., `**Trigger / Visibility**`, `**Create Action Flow**`)
- Do NOT use Given/When/Then here — that belongs in QA Scenarios

---

## QA / Test Scenarios Format

Use numbered scenarios with step-by-step actions for the QA team:

```markdown
🔍 QA / Test Scenarios

1. Single service with gaps
   - Log in as a care manager with one service assigned
   - Navigate to the quality gaps page
   - Verify gaps display with correct category, severity, and date

2. Empty state
   - Log in as a care manager with a service that has no recorded gaps
   - Navigate to the quality gaps page
   - Verify the empty state message is shown and no gap rows appear
```

---

## Domain Terminology

Use these terms consistently in healthcare product stories:

| Term | Meaning |
|---|---|
| care provider | An organisation delivering care services (e.g. a care home group) |
| care service | A single registered service or location within a provider |
| resident / patient | The person receiving care |
| care plan | A document describing a resident's needs, preferences, and agreed care |
| care record | A log of care activities and observations for a resident |
| quality gap | An identified issue or inconsistency in a care plan or care record |
| improvement action | A task created to resolve a quality gap |
| audit | A structured review of care quality, either self-assessed or externally inspected |
| regulatory body | The external authority inspecting care quality (e.g. CQC in England) |
| care manager | A manager responsible for a care service's day-to-day quality |
| deputy manager | A care manager's second-in-command, often responsible for compliance |
| compliance | Adherence to regulatory standards and internal policies |

---

## Dependencies and Open Questions

### 🔗 Dependencies

List anything this story relies on that is outside its own scope:

```markdown
🔗 Dependencies

- Search component variant may need to be added to the design system before build
- Service selector story must be merged before this work begins
```

**Rules:**
- Reference related ticket IDs where known
- Include component-library or design-system blockers
- Delete this section if there are genuinely no dependencies

### ❔ Open Questions

Capture unresolved decisions that must be answered before or during development:

```markdown
❔ Open Questions

- **Client-side vs server-side filtering:** Are all gaps already loaded into the client, or does filtering need an API call?
- **Severity definition:** Who defines severity — the AI, the care manager, or a fixed ruleset?
```

**Rules:**
- Bold the question topic for scannability
- Remove each question once answered (move the answer into AC if it affects behaviour)
- Delete this section once all questions are resolved

---

## Figma Frame Images

When a story has associated Figma frames, capture and embed them so the output markdown is fully self-contained.

### Workflow

1. **Identify node IDs** — from the Figma URL or by calling `figma_navigate` / `figma_execute` to list the relevant frames.
2. **Capture each frame** — call `figma_take_screenshot` (REST, returns a URL) or `figma_capture_screenshot` (Desktop Bridge plugin, returns PNG bytes) per frame.
3. **Save locally** — download the image with `curl` into: `user-story/outputs/images/<story-slug>/frame-<N>.png`
4. **Embed in the story** — add a `🖼 Figma Designs` section with relative markdown image links.

### When to include

- Only when Figma frames have been created or identified as part of the same task.
- Skip the section (and delete it from the output) if no Figma designs exist yet.

---

## Anti-Patterns

**Too vague a "so that":**
- ❌ "so that I can use the feature"
- ✅ "so that I can identify and act on quality issues before they affect residents"

**AC written as Gherkin (use QA Scenarios instead):**
- ❌ "Given I am on the care plan page / When I view a flagged gap / Then it shows the improvement action"
- ✅ "Each flagged gap displays the associated improvement action, or a 'No action assigned' label if none exists"

**Story too large (multiple unrelated outcomes):**
- Split into child stories under the same parent epic
- Each story should be completable in a single sprint

**Technical task as a user story:**
- ❌ "As a developer, I want to refactor the care plan endpoint"
- ✅ Use an engineering task ticket instead; no user outcome = not a story

---

## References

- `template.md` — Fill-in template for the full story structure
- Mike Cohn, *User Stories Applied* (2004) — origin of the "As a / I want / so that" format
- INVEST criteria — Independent, Negotiable, Valuable, Estimable, Small, Testable
