# 15. Compatibility and Versioning

## 15.1 V3 compatibility contract

Automated compatibility tests freeze three public surfaces in this snapshot:

1. CLI help/version aliases and the primary commands `new`, `build`, `check`, `test`, and `run`.
2. The built-in module names: `files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, `runtime`.
3. The V3 runtime capability names exposed through `runtime.capabilities`.

This does not mean future versions cannot add features. It means removal or incompatible renaming of these V3 surfaces should be treated deliberately as an API compatibility change.

## 15.2 Runtime generation

`runtime.generation` is `3` in this source snapshot. Generation is separate from the textual package version and can be used to reason about broad runtime capability families.

## 15.3 Current source version

`version.py` in the supplied source snapshot defines release version `0.3.0`, channel `release`, and therefore reports `0.3.0`. When the final release channel/version switch is performed, release-facing documentation should be regenerated or checked against the final value.

## 15.4 Living handbook policy

This handbook is designed to grow without renumbering existing concepts unnecessarily. Future V4/V5 work should extend an existing chapter when it belongs to the same feature family. Add a new numbered chapter only for a genuinely new public subsystem. Source and regression tests remain the final authority when documentation and implementation disagree.

