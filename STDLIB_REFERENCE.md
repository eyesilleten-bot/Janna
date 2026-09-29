# Janna Standard Library Reference

Built-in modules: `files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, `runtime`.

## Actions

- **files**: `read`, `write`, `write_markdown`, `write_docx`, `append`, `delete`, `make_folder`, `list`, `exists`, `join`, `name`, `extension`, `parent`, `absolute`, `is_file`, `is_folder`, `delete_folder`.
- **json**: `read`, `parse`, `stringify`, `write`.
- **text**: `newline`, `lower`, `upper`, `trim`, `replace`, `split`, `contains`, `length`, `matches`, `join`, `write`, `lexical_issues`.
- **random**: `number`, `choose`.
- **time**: `now`, `wait`.
- **env**: `get`.
- **secrets**: `get`, `require`.
- **http**: `get`, `post`, `put`, `delete`.
- **ai**: `generate`, `usage`.
- **schema**: `validate`.
- **jobs**: `create`, `start`, `progress`, `checkpoint`, `complete`, `fail`, `save`, `load`.
- **context**: `split`, `build`.
- **runtime**: `exit`; properties: `version`, `channel`, `generation`, `capabilities`, `arguments`, `app_name`, `app_path`, `app_directory`.

See handbook chapters 5–10 for signatures, validation rules, and examples.

