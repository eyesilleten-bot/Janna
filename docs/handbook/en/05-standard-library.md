# 5. Standard Library

Janna V3 ships thirteen built-in modules. Import a module with `use` before accessing it.

## 5.1 `text`

- `text.newline` — newline text value; takes no arguments.
- `text.lower text`
- `text.upper text`
- `text.trim text`
- `text.replace text old new`
- `text.split text separator` — returns a list.
- `text.contains text pattern` — returns boolean.
- `text.length text` — returns character count.
- `text.matches text regex` — regex search, returns boolean.
- `text.join list separator` — all list items must be text.
- `text.write path text` — UTF-8 text output, returns `yes` on success.
- `text.lexical_issues text language` — lexical analysis; current language support is English and Turkish.

## 5.2 `json`

- `json.read path`
- `json.parse text`
- `json.stringify value`
- `json.write path value`

JSON output is UTF-8, Unicode-preserving, and formatted with indentation.

## 5.3 `random`

- `random.number minimum maximum` — inclusive whole-number range.
- `random.choose list` — selects one item; empty lists are rejected.

## 5.4 `time`

- `time.now "iso"`
- `time.now "date"`
- `time.now "time"`
- `time.wait seconds`

Negative waits are rejected.

## 5.5 Other modules

`files`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, and `runtime` are large enough to have dedicated chapters.

## 5.6 Module contract

The V3 API-compatibility tests freeze the built-in module names above as a compatibility contract. Adding new actions is possible in future versions, but removing or renaming current public module families should be treated as a compatibility change.

