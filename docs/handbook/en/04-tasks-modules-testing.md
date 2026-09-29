# 4. Tasks, Modules, and Testing

## 4.1 Tasks

Tasks are top-level definitions. Parameters are whitespace-separated identifiers.

```janna
task greet person
    show "Hello {person}"

greet "Ege"
```

A task returns a value with `give`.

```janna
task add_two value
    give value + 2

result is add_two 5
```

Duplicate task names and duplicate parameter names are rejected.

## 4.2 User modules

A user module is another `.ja` file. `use inventory` loads `inventory.ja`. During normal source execution Janna first resolves the module relative to the current source file, then any configured module search paths. Circular imports are detected.

```janna
use actions
result is actions.explore state
```

A module exposes its top-level variables and tasks through property-style access/calls. Builds collect user modules recursively and bundle them into the executable.

## 4.3 Built-in modules

The stable V3 built-in module set is:

`files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, `runtime`.

Built-ins still require `use <module>` before access.

## 4.4 Tests

Tests are top-level blocks.

```janna
test "addition works"
    expect 2 + 3 is 5
```

`expect` evaluates a condition. The CLI reports each test as PASS or FAIL and returns a non-zero code if failures occur.

Project tests live under the project `tests` directory and run with `janna test`. A specific test file can be run with `janna test file.ja`.

## 4.5 Error handling

```janna
attempt
    risky_task
if fails
    show "Recovered"
```

`attempt` must be followed by an `if fails` block at the same indentation level. Janna also adds source/task/module context to runtime diagnostics where available.

