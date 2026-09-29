# Janna Quick Start

This guide gets a Janna V3 program running quickly. For the complete language and runtime documentation, see `HANDBOOK.md`.

## 1. Check the installation

Open a new PowerShell window:

    janna version
    janna help

## 2. Create and run a project

    janna new hello_project
    cd hello_project
    janna run

A new project uses:

    hello_project/
        janna.toml
        src/
            app.ja
        tests/

Check, test, and build it with:

    janna check
    janna test
    janna build

## 3. Run a single file

Create `hello.ja`:

    name is "Ege"
    show "Hello {name}"

Run it:

    janna run hello.ja

On Windows you can use the short launcher:

    ja hello.ja

## 4. Values and input

    name is "Ege"
    age is 25
    active is yes
    empty is nothing

    answer is ask "Your name: "
    show "Welcome {answer}"

## 5. Conditions and loops

    age is 25

    when age is at least 18
        show "Adult"
    otherwise
        show "Under 18"

    repeat 3
        show "Hello"

    number is 1

    while number is at most 3
        show number
        increase number by 1

## 6. Tasks

    task greet person
        show "Hello {person}"

    greet "Ege"

A task can return a value:

    task add a b
        give a + b

    result is add 10 20
    show result

## 7. Lists and objects

    numbers is [10, 20, 30]
    show first of numbers
    add 40 to numbers

    player is
        name is "Ege"
        score is 100

    show player.name
    increase player.score by 50

## 8. Modules

Create `src/greeter.ja`:

    task greet name
        show "Hello {name}"

Use it from `src/app.ja`:

    use greeter
    greeter.greet "Janna"

## 9. Built-in services

Janna V3 built-in modules include:

    files
    json
    text
    random
    time
    env
    secrets
    http
    ai
    schema
    jobs
    context
    runtime

Example:

    use files

    files.write "note.txt" "Hello from Janna"
    content is files.read "note.txt"
    show content

For all actions and properties, see `STDLIB_REFERENCE.md`.

## 10. Program arguments

Run:

    ja hello.ja first second

Then read the arguments:

    use runtime
    show runtime.arguments

## 11. Error handling

    use json

    attempt
        player is json.read "missing.json"

    if fails
        player is
            name is "Guest"

    show player.name

## 12. Janna tests

    test "math works"
        expect 10 + 5 is 15

Project tests normally live in `tests/`.

Run:

    janna test

## 13. Keyboard shorthand

Canonical:

    name is "Janna"
    show name

Keyboard shorthand:

    name := "Janna"
    -> name

Shorthand is executable source syntax and is normalized before normal parsing.

AlienJanna is a separate symbolic rendering layer, not another parser mode. See `HANDBOOK.md` for the full syntax-layer explanation.

## 14. Editor Beta

The release contains Janna Editor Beta for VS Code and Cursor. The extension package version is `0.2.0`.

It provides syntax highlighting and Run / Check / Test / Build commands for both active files and projects.

## 15. Next references

- `HANDBOOK.md` — full handbook
- `CLI_REFERENCE.md` — CLI summary
- `STDLIB_REFERENCE.md` — standard-library summary
- `examples/` — runnable examples
- `examples/janna_frontier/` — larger project example

