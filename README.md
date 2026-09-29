# Janna

Janna is a beginner-first programming language designed to be readable, direct, and practical while still supporting real multi-file applications, builds, runtime services, AI workflows, and Windows distribution.

## Current release

`0.3.0`

Janna V3 is in final release-closure work. The final public release will use the `0.3.0` release version.

## What Janna V3 includes

- readable canonical Janna syntax
- keyboard shorthand syntax
- AlienJanna symbolic rendering layer
- variables, conditions, loops, lists, and objects
- tasks, return values, user modules, and multi-file projects
- built-in tests and source checking
- `janna.toml` project manifests
- Windows executable builds
- files, paths, JSON, text, random, and time utilities
- Markdown and DOCX document output
- terminal input and runtime program arguments
- runtime version, capability, application-path, and exit-code information
- HTTP requests
- schema validation
- resumable jobs and checkpoints
- environment variables and secret-safe handling
- AI generation, structured output, retry/repair behavior, and usage information
- context splitting and context building for large text
- diagnostics with source locations and task/module traces
- Janna Editor Beta for VS Code and Cursor
- portable SDK and Windows installer
- short Windows launcher: `ja`

## Install

Run:

    JannaSetup.exe

Then open a new PowerShell window and verify the installation:

    janna version

Show the CLI help:

    janna help

## Create a project

Create a new Janna project:

    janna new my_project
    cd my_project

Run it:

    janna run

Check it without running:

    janna check

Run project tests:

    janna test

Build a Windows executable:

    janna build

A normal project begins with:

    my_project/
        janna.toml
        src/
            app.ja
        tests/

Example `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

## Run a single file

Create `hello.ja`:

    name is "Ege"
    show "Hello {name}"

Run it:

    janna run hello.ja

Or use the short Windows launcher:

    ja hello.ja

Program arguments are forwarded by both forms:

    janna run hello.ja first second
    ja hello.ja first second

A program using the runtime module can read those values through `runtime.arguments`.

## Syntax layers

Janna V3 has three syntax layers.

### Canonical syntax

    name is "Janna"

    when name is "Janna"
        show "Hello"

### Keyboard shorthand

    name := "Janna"

    ? name == "Janna"
        -> "Hello"

Keyboard shorthand is executable source syntax. It is normalized before normal parsing and shares the same underlying semantics as canonical Janna.

### AlienJanna

AlienJanna is a deterministic symbolic rendering layer. It renders canonical/keyboard Janna into an alternate visual form without mutating the original source.

AlienJanna is not a separate parser mode or a replacement source language.

## Standard library

Built-in modules include:

`files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, and `runtime`.

For the compact action list, see:

- `STDLIB_REFERENCE.md`
- `STDLIB_REFERENCE_TR.md`

## CLI reference

For the compact command reference, see:

- `CLI_REFERENCE.md`
- `CLI_REFERENCE_TR.md`

The main commands are:

    janna new <project_name>
    janna run [file.ja] [args...]
    janna check [file.ja]
    janna test [file.ja]
    janna build [file.ja]
    janna version
    janna help

Windows also includes:

    ja <file.ja> [args...]

which is a short launcher for `janna run`.

## Editor Beta

Janna Editor Beta provides Janna language support for VS Code and Cursor.

The current extension package version is `0.2.0`.

It provides syntax highlighting plus active-file and project commands for:

- Run
- Check
- Test
- Build

The release package contains the VSIX under the `editor/` directory.

## Janna Frontier

`examples/janna_frontier/` is the public example project used to demonstrate Janna in a larger application.

After installation, open that project directory and run:

    janna run

You can also run:

    janna check
    janna test
    janna build

## Documentation

Start here:

- `QUICKSTART.md` — fast English walkthrough
- `QUICKSTART_TR.md` — hızlı Türkçe başlangıç
- `HANDBOOK.md` — complete English handbook index
- `HANDBOOK_TR.md` — tam Türkçe handbook dizini
- `JANNA_HANDBOOK_EN.md` — combined English handbook
- `JANNA_HANDBOOK_TR.md` — birleştirilmiş Türkçe handbook
- `CLI_REFERENCE.md` / `CLI_REFERENCE_TR.md`
- `STDLIB_REFERENCE.md` / `STDLIB_REFERENCE_TR.md`

The Handbook is maintained as living documentation: future Janna versions extend the existing feature-family chapters, while genuinely new subsystems can add new numbered chapters.

## More help

    janna help


