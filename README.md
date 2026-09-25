# Janna

Janna is a beginner-first programming language designed to be readable, simple, and practical.

## Current version

0.2.0

## Run Janna Frontier

To try Janna Frontier from GitHub:

1. Open the **Releases** section of this repository.
2. Open **Janna 0.2.0**.
3. Download and run `JannaSetup.exe`.
4. Open the installed `examples/janna_frontier` folder.
5. Open PowerShell in that folder and run:

    janna run

You can also check or test the project first:

    janna check
    janna test

If you prefer the portable ZIP, download `Janna-0.2.0-Windows.zip`, extract it, open `examples/janna_frontier`, and run:

    ../../janna.exe run

## What Janna V2 can do

- variables, conditions, loops, lists, and objects
- tasks and return values
- user modules and multi-file projects
- project files with `janna.toml`
- files and JSON
- text, random, and time utilities
- terminal input
- error handling with `attempt ... if fails`
- built-in Janna tests
- project checking with `janna check`
- keyboard shorthand syntax
- build `.ja` programs and projects into Windows `.exe` files
- Janna Editor Alpha for VS Code / Cursor

## Installation

Run:

    JannaSetup.exe

After installation, open a new PowerShell window and run:

    janna version

## Create a project

Create a new Janna project:

    janna new my_project

Then enter the project folder:

    cd my_project

Run the project:

    janna run

Check it:

    janna check

Run tests:

    janna test

Build a Windows executable:

    janna build

## Your first Janna program

You can also work with a single `.ja` file.

Create `hello.ja`:

    name is "Ege"

    show "Hello {name}"

Run it:

    janna run hello.ja

Build it:

    janna build hello.ja

## Project structure

A Janna project normally looks like this:

    my_project/
        janna.toml
        src/
            app.ja
        tests/

Example `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

## Keyboard shorthand

Janna V2 supports both canonical beginner syntax and keyboard shorthand.

Canonical:

    name is "Janna"

    when name is "Janna"
        show "Hello"

Keyboard shorthand:

    name = "Janna"

    if name == "Janna"
        show "Hello"

Both forms are valid Janna V2.

## Editor Alpha

The release includes the Janna Editor Alpha VSIX package.

It provides Janna language support for VS Code and Cursor, including syntax highlighting and Janna commands.

The VSIX file is inside:

    editor/

## Examples

The `examples` folder contains small examples and the larger V2 demo project:

    01_hello.ja
    02_conditions.ja
    03_loops.ja
    04_tasks.ja
    05_lists.ja
    06_objects.ja
    07_files_json.ja
    janna_frontier/

`janna_frontier` is a multi-file terminal colony survival game used to demonstrate and test Janna V2 project features.

## Syntax layers

Janna has three planned syntax layers:

1. natural/canonical beginner syntax
2. keyboard shorthand
3. symbolic/alien display syntax

V2 supports the first two layers.

The symbolic/alien layer is planned for a later version.

## More help

Use:

    janna help

For a compact walkthrough, see:

    QUICKSTART.md
