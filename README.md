AIP — Artificial Intelligence Prompt Protocol
![Status: Public Draft](https://img.shields.io/badge/status-public_draft-1f6feb)
![Version: 1.1](https://img.shields.io/badge/version-1.1-111111)
![License: CC BY 4.0](https://img.shields.io/badge/license-CC_BY_4.0-0a7f3f)
AIP is an open format for AI-agnostic software.
Apps generate structured tasks.  
Users run them with any AI they already have.  
No API keys. No inference costs. No vendor lock-in.
---
Start here:
Try the console — generate a task packet in 30 seconds
Landing page — what AIP is and why it exists
Spec — the full protocol specification
Examples — ready-to-use packet templates
---
How it works
```
=== AI_TASK ===
version: 1.1
task:    document_summary

input:
  text: [USER_INPUT]
  ... any document ...
  [/USER_INPUT]

rules:
  3_sentences_maximum
  plain_language
  no_preamble

output_format: text
=== END_TASK ===
```
1. App generates a packet like this.  
2. User pastes it into ChatGPT, Claude, Gemini, or any local model.  
3. Result comes back in a structured format the app can read.
That's it. No model API. No cost. Works with any AI, now and in the future.
---
Why this exists
Most "AI apps" are wrappers around a model API. That creates the same failure pattern every time:
developer pays per inference
app inherits vendor risk
product breaks when APIs change
user has no say in which AI they trust
AIP flips the model. The app emits a task. The user's AI executes it. The result comes back structured. The AI is already in the user's pocket — AIP just gives it a job to do.
---
What's in this repo
```
docs/
  index.html          — front door (GitHub Pages entry point)
  console.html        — interactive task packet generator
  AIP-landing.html    — full public landing page
spec/
  AIP-v1.1.md         — canonical specification
examples/
  basic-task.txt      — minimal block format task
  json-mode.json      — JSON mode task and result
  stateful-session.txt — multi-turn session with history
  retry-packet.txt    — retry packets for all six error codes
reference/
  AIP-v1.1-spec.html  — rendered spec (open in browser)
```
---
Standard task types
Type	What it does
`document_summary`	Summarise any document
`rewrite`	Change the tone or style of text
`translate`	Translate to any language
`classify`	Sort an item into your categories
`lyrics`	Write song lyrics
`painting_ideas`	Generate visual concepts
`learning_activity`	Create an activity for a learner
`story_generation`	Write a short story
`logic_reasoning`	Work through a problem
`session_summarise`	Compress a conversation history
Custom types use reverse-domain namespacing: `com.yourapp.task_name`
---
Contributing
See CONTRIBUTING.md for the full process.
Short version:
Spec issue? Open a `spec-clarification` or `spec-bug` issue
New task type? Open a `task-type-proposal` issue — include a working example
Structural change? Open a `major-proposal` issue — requires independent implementation
---
Repo files
File	Purpose
CHANGELOG.md	What changed and when
CONTRIBUTING.md	How to propose changes
GOVERNANCE.md	Stewardship and decision model
SECURITY.md	How to report protocol-level risks
CODE_OF_CONDUCT.md	How we work together
LICENSE.txt	CC BY 4.0 — free to use and build on
---
Build once. Run with any AI.
