# 11. CLI, Projects, and Build

## 11.1 Main commands

```text
janna new <project_name>
janna run
janna run <file.ja> [arguments...]
janna check
janna check <file.ja>
janna build
janna build <file.ja>
janna test
janna test <file.ja>
janna version
janna help
```

Help aliases are `help`, `--help`, `-h`. Version aliases are `version`, `--version`, `-v`. Command-specific help accepts `janna <command> --help` (also `help` or `-h`).

## 11.2 Short Windows launcher

The SDK includes `ja.cmd`:

```text
ja app.ja arg1 arg2
```

This is a convenience wrapper for `janna.exe run app.ja arg1 arg2`.

## 11.3 Projects

A project is identified by `janna.toml` in the current directory.

```toml
name = "my_app"
entry = "src/app.ja"
```

`name` must be non-empty. `entry` must be a `.ja` file and must exist.

`janna new demo` creates:

```text
demo/
  janna.toml
  .gitignore
  src/app.ja
  tests/test_app.ja
```

With no file argument, `run`, `check`, `build`, and `test` operate on the current project.

## 11.4 Check

`janna check` validates the source tree without running the program. Source/module problems include source locations where available.

## 11.5 Build

`janna build` validates first, then creates a Windows executable under the source file's `dist` directory. User modules are collected recursively and bundled into the application. Circular imports and missing modules stop the build.

Installed Janna uses the SDK's private portable build runtime. Development mode uses the local Python/PyInstaller environment. Programs using `text.lexical_issues` include the optional English/Turkish morphology data needed by that feature; ordinary builds avoid that additional payload.

