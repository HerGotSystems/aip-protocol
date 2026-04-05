# AIP — Artificial Intelligence Prompt Protocol

![Status: Public Draft](https://img.shields.io/badge/status-public_draft-1f6feb)
![Version: 1.1](https://img.shields.io/badge/version-1.1-111111)
![License: CC BY 4.0](https://img.shields.io/badge/license-CC_BY_4.0-0a7f3f)

**An open protocol standard for AI-agnostic software.**

Apps generate structured task packets. Users execute them with whatever AI they already have. No API keys. No vendor lock-in. No inference costs.

---

## Why this exists

Most “AI apps” are really wrappers around someone else’s model API.

That creates the same failure pattern every time:

- the developer pays for inference
- the product inherits vendor risk
- the app becomes fragile when APIs change
- users lose control over which AI they trust or already subscribe to

**AIP flips that model.**  
The app does not run the AI. The app emits a structured task. The user runs that task with their own AI. The result comes back in a format the app can parse.

That makes AIP useful for:
- AI task consoles
- browser tools
- mobile utilities
- internal workflow apps
- bridge automations
- local-first or privacy-sensitive software

---

## The idea in one screen

**App generates this:**

```text
=== AI_TASK ===
version: 1.1
task:    document_summary

input:
  text: [USER_INPUT]
  ... user's document content ...
  [/USER_INPUT]

rules:
  3_sentences_maximum
  plain_language
  no_preamble

output_format: text
=== END_TASK ===
```

**User runs it with their AI.**

**AI returns this:**

```text
=== AI_RESULT ===
task_id: sum-001
status:  ok

The document outlines a proposed change to the company's expense
policy, reducing the pre-approval threshold from £500 to £250.
It takes effect from the first of next month and applies to all departments.
=== END_RESULT ===
```

**App reads the result. Done.**  
No model API call required.

---

## Repository layout

```text
/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   └── config.yml
│   └── pull_request_template.md
├── docs/
│   ├── AIP-landing.html
│   └── index.html
├── examples/
│   ├── basic-task.txt
│   ├── json-mode.json
│   └── stateful-session.txt
├── reference/
│   └── AIP-v1.1-spec.html
├── spec/
│   └── AIP-v1.1.md
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── GOVERNANCE.md
├── LICENSE.txt
├── README.md
├── RELEASE_NOTES.md
└── SECURITY.md
```

---

## Start here

1. Open `docs/AIP-landing.html` for the public overview.
2. Open `reference/AIP-v1.1-spec.html` for the browser-readable spec.
3. Read `spec/AIP-v1.1.md` for the canonical source.
4. Use `examples/` to test parsers, prompts, bridges, and app flows.

Both HTML files are offline-safe and do not depend on external font CDNs.

---

## What v1.1 covers

| Area | What it defines |
|---|---|
| Architecture | The BYO-AI model and why it differs from API-coupled AI |
| Packet format | Block format and JSON mode |
| Task registry | Standard task identifiers and custom namespacing |
| Error handling | Failure codes, validation, and retry packets |
| Versioning | MAJOR.MINOR release rules |
| Context persistence | Session envelopes, history pruning, summarisation |
| Trust model | Input boundaries, sanitisation, and safety posture |

---

## What this repo is for

This repo is meant to be a **publishable protocol package**, not just a note dump.

It gives you:
- a canonical spec
- browser-readable reference pages
- examples that can be pasted into real systems
- contributor and governance scaffolding for public discussion

---

## Suggested release posture

AIP v1.1 should be presented as:

> **A public draft standard for Bring Your Own AI software.**

That wording is strong enough to ship and honest enough to invite feedback.

---

## Next practical builds

AIP becomes much stronger with live reference implementations around it.

High-value next steps:
- AI Task Console reference app
- parser / validator library
- bridge automation for desktop and mobile handoff
- compatibility examples for ChatGPT, Claude, Gemini, and local models

---

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a proposal or pull request.

When proposing protocol changes:
- name the exact section
- show the compatibility impact
- include an example packet when possible
- explain why the change improves interoperability

---

## Stewardship

Current status:
- **Status:** Public draft
- **Steward:** EMVY CHECK
- **Model:** Founder-led draft stewardship, open to implementer feedback

See [GOVERNANCE.md](GOVERNANCE.md) for the current change model.

---

## License / use

See [LICENSE.txt](LICENSE.txt).

This package is intended to be easy to read, discuss, implement, and extend. If you publish derivative work, keep the protocol wording clear and avoid implying official compatibility where none has been tested.
