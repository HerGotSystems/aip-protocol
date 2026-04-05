# Contributing to AIP

AIP is a public draft standard. Contributions are welcome and the process is deliberately lightweight for v1.x.

---

## What you can contribute

### Spec clarifications
Wording that is ambiguous, contradictory, or missing detail. Open an issue labelled `spec-clarification`. No implementation required.

### Spec bug reports
A case where following the spec produces a broken or undefined outcome. Open an issue labelled `spec-bug`. Include a concrete example of the failure.

### New task types
A new entry for the standard task type registry. See the full process below.

### Major structural proposals
Changes that would require a MAJOR version increment. See the bar for these below.

### Examples and worked implementations
Additional worked examples (new domains, edge cases, language-specific parsers). Open a PR against the `examples/` directory.

---

## Proposing a new task type

Task type proposals are the most common contribution. The bar is intentionally low but one requirement is firm: **you must have a working implementation before a proposal can be ratified.**

**Step 1 — Open an issue**

Label it `task-type-proposal`. Include:

- **Type identifier** — snake_case, descriptive, domain-neutral where possible
- **Category** — one of: Game, Narrative, Music, Visual, Education, Text, Utility, Session, or propose a new category
- **Required input fields** — name, type, and whether mandatory or optional
- **Output format** — text, json, or markdown
- **Return schema** — for JSON mode, the fields the result must contain
- **Worked example** — a complete task packet and a plausible result packet
- **Link to implementation** — a public repository, live tool, or documented usage

**Step 2 — Discussion**

The issue stays open for at least 14 days to allow comment. The steward or community members may request changes to the identifier, field names, or format.

**Step 3 — Ratification**

If the proposal meets the criteria and has no blocking objections, the steward ratifies it and it enters the registry in the next MINOR release. The proposal author is credited in the changelog.

**What makes a good task type:**
- Domain-neutral enough that multiple unrelated apps could use it
- Input fields are the minimum necessary — not every possible parameter
- Identifier is unambiguous and self-describing
- Works with any sufficiently capable AI, not just specific models

**What will not be accepted:**
- Types that require vendor-specific model features
- Types that duplicate existing registered types with minor variation
- Types without a demonstrated working implementation

---

## Proposing a structural change (MAJOR)

Structural changes — modifications to required fields, packet delimiters, error codes, versioning rules, or governance — require a MAJOR version increment and a higher bar.

Requirements before a MAJOR proposal can proceed:

1. Open an issue with label `major-proposal`
2. Clearly document what breaks under the current spec and why it cannot be solved with a MINOR addition
3. Provide a full draft of the changed sections
4. Demonstrate at least one independent (non-steward) implementation of the proposed changes
5. Allow a minimum 60-day discussion period

MAJOR proposals that lack independent implementation or clear justification for the breaking change will be closed without ratification.

---

## Opening a pull request

For spec text changes: PRs against `spec/AIP-v1.1.md`. Changes must be minimal, targeted, and reference an open issue.

For examples: PRs against `examples/`. No issue required for new worked examples. Follow the existing file naming convention.

For the README: only open README PRs if something is factually incorrect. The README reflects the spec — change the spec first.

---

## Code of conduct

AIP is a technical standard. Discussions should be specific, referenced, and constructive. Proposals are evaluated on technical merit, not on who proposes them.

---

## Questions

Open an issue with the label `question`. If you are building something on AIP and want to share it, open an issue with the label `built-on-aip`.
