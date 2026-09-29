# 7. Runtime Information, Arguments, and Exit Codes

Enable runtime access with:

```janna
use runtime
```

## 7.1 Runtime properties

The runtime exposes these read-only properties:

- `runtime.version`
- `runtime.channel`
- `runtime.generation`
- `runtime.capabilities`
- `runtime.arguments`
- `runtime.app_name`
- `runtime.app_path`
- `runtime.app_directory`

The current source snapshot reports generation `3`. `runtime.version` is derived from `version.py`; this snapshot is `0.3.0` on the `development` channel.

## 7.2 Program arguments

When a source file is launched as:

```text
janna run app.ja alpha beta
```

`runtime.arguments` is:

```text
[alpha, beta]
```

The Windows `ja` launcher is a short form:

```text
ja app.ja alpha beta
```

It forwards to `janna.exe run ...`, preserving the same runtime argument list. Built executables also receive their command-line arguments.

## 7.3 Application identity

`runtime.app_name`, `runtime.app_path`, and `runtime.app_directory` refer to the root application. Imported user modules retain that root application identity rather than becoming separate apps.

## 7.4 Exit codes

`runtime.exit code` terminates the program with an explicit whole-number exit code from 0 through 255.

```janna
use runtime
runtime.exit 7
```

The code propagates through source execution and built executables.

## 7.5 Capabilities

The current V3 capability contract includes: `projects`, `user_modules`, `tests`, `keyboard_shorthand`, `alien_syntax`, `task_trace`, `source_locations`, `http`, `ai`, `schema`, `structured_output`, `retry_resilience`, `jobs`, `checkpoints`, `large_text`, `document_output`, `files_paths`, `runtime_arguments`, `runtime_app_info`, `runtime_exit`, and `context_builder`.

