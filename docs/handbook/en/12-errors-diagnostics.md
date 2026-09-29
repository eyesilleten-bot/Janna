# 12. Errors and Diagnostics

Janna separates user-facing language/runtime errors from unexpected internal failures.

## 12.1 Syntax diagnostics

Examples of syntax problems include invalid indentation, malformed expressions, missing blocks, invalid task/module identifiers, malformed object entries, invalid tests, and incomplete `attempt` structures. Diagnostics include line numbers when the parser knows the source line.

## 12.2 Runtime diagnostics

Runtime errors cover unknown variables/tasks/actions, wrong argument counts or types, invalid paths, invalid schema definitions, unavailable secrets, HTTP/AI option errors, illegal job transitions, and division by zero.

## 12.3 Source and task context

The V3 runtime capability set includes `source_locations` and `task_trace`. Errors are enriched with source-file context and task/module trace information where the execution path provides it.

## 12.4 User modules

Errors originating in imported modules retain module/source context. Circular module imports are explicitly detected instead of recursing indefinitely.

## 12.5 CLI behavior

Expected Janna errors are printed as understandable Janna diagnostics and normally return exit code 1. `runtime.exit` is handled separately and returns the requested 0–255 code. Unexpected internal exceptions are caught at the CLI boundary and reported without exposing a Python traceback to normal users.

## 12.6 Secret-safe diagnostics

Registered `SecretValue` contents are redacted from display and diagnostic text. This includes nested display structures and text generated while propagating errors.

