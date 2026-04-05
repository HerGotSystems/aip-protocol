# Changelog

All notable changes to the AIP specification are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versioning follows the MAJOR.MINOR scheme defined in §5 of the spec.

---

## [1.1] — First public draft release

### Added
- § 4 Error handling and retry protocol
  - Six error codes: E01–E06
  - Validation checklist
  - Retry packet format with `retry_for_error`, `original_task_id`, `attempt`, and `correction` fields
  - Retry policy including maximum attempt limits and E04 (refusal) handling
- § 5 Versioning discipline and governance
  - MAJOR.MINOR version scheme
  - Backwards compatibility rules for parsers
  - 12-month maintenance window for previous MAJOR versions
  - v1.x governance model: steward, proposal process, ratification criteria
- § 6 Context persistence and stateful tasks
  - Session envelope with `session_id` and `turn` counter
  - Rolling history block
  - History pruning: rolling window and summarisation methods
  - Pinned turns
  - `session_summarise` task type added to registry
  - Session integrity contract
- § 7 Trust model and safety
  - Attack surface taxonomy: user input, external data, stored data, file content
  - Sanitisation rules for untrusted strings
  - Role-boundary pattern with `[USER_INPUT]` delimiters
  - Explicit out-of-scope items: authentication, data residency, model-side filtering
- Task type registry expanded to 12 types
  - Added: `document_summary`, `rewrite`, `translate`, `classify`, `logic_reasoning`, `session_summarise`
- Appendix A with four complete worked examples
  - Stateful NPC dialogue (session, turn 3, with pruned history)
  - Lyrics generation (JSON mode)
  - Retry packet for E02 preamble contamination
  - Session summarise round-trip

### Changed
- `version` field clarified: must be a `MAJOR.MINOR` string, not an integer

---

## [1.0] — Foundation release

### Added
- § 1 Motivation and architecture — BYO-AI model, design principles, stack comparison
- § 2 Packet format — block format and JSON mode for task and result packets; required fields; status values (`ok`, `partial`, `refused`, `error`)
- § 3 Standard task type registry — initial 6 types: `npc_dialogue`, `story_generation`, `lyrics`, `image_description`, `painting_ideas`, `learning_activity`
- Custom type namespacing via reverse-domain convention
- `task_id` field as recommended (not required) for correlation
- `output_format` values: `text`, `json`, `markdown`
