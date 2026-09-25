# Janna Quick Start

## 1. Check Janna

After installation, open a new PowerShell window:

    janna version

Show available commands:

    janna help

## 2. Create a project

Create a new project:

    janna new hello_project

Enter the folder:

    cd hello_project

A project normally contains:

    janna.toml
    src/
        app.ja
    tests/

## 3. Run the project

Run the current project:

    janna run

Check it without running:

    janna check

Run its tests:

    janna test

Build a Windows executable:

    janna build

## 4. Single-file programs

You can also use Janna without a project.

Example `hello.ja`:

    name is "Ege"

    show "Hello {name}"

Run:

    janna run hello.ja

Check:

    janna check hello.ja

Build:

    janna build hello.ja

## 5. Variables

    name is "Ege"
    age is 25
    active is yes
    empty is nothing

## 6. Output and input

    show "Hello"
    show name
    show "Hello {name}"

    answer is ask "Your name: "
    show "Welcome {answer}"

## 7. Conditions

    age is 25

    when age is at least 18
        show "Adult"
    otherwise
        show "Under 18"

## 8. Loops

    repeat 3
        show "Hello"

    number is 1

    while number is at most 3
        show number
        increase number by 1

## 9. Tasks

    task greet person
        show "Hello {person}"

    greet "Ege"

Tasks can return values:

    task add a b
        give a + b

    result is add 10 20
    show result

## 10. Lists and objects

    numbers is [10, 20, 30]

    show first of numbers
    show last of numbers
    show count of numbers

    add 40 to numbers

Objects:

    player is
        name is "Ege"
        score is 100

    show player.name
    increase player.score by 50

## 11. Modules

Create `src/greeter.ja`:

    task greet name
        show "Hello {name}"

Use it from `src/app.ja`:

    use greeter

    greeter.greet "Janna"

## 12. Files and JSON

Files:

    use files

    files.write "note.txt" "Hello from Janna"
    content is files.read "note.txt"

    show content

JSON:

    use json

    player is
        name is "Ege"
        level is 7

    json.write "player.json" player

    loaded is json.read "player.json"

    show loaded.name

## 13. Text, random, and time

    use text
    use random
    use time

    show text.upper "janna"

    number is random.number 1 10
    show number

    show time.now

## 14. Error handling

    use json

    attempt
        player is json.read "missing.json"

    if fails
        player is
            name is "Guest"

    show player.name

## 15. Janna tests

Example:

    test "math works"
        expect 10 + 5 is 15

Project tests normally live inside:

    tests/

Run them with:

    janna test

## 16. Keyboard shorthand

Janna V2 supports keyboard shorthand.

Canonical:

    name is "Janna"

    when name is "Janna"
        show "Hello"

Shorthand:

    name = "Janna"

    if name == "Janna"
        show "Hello"

Other shorthand forms include:

    +=
    -=
    == 
    !=
    >=
    <=
    &&
    ||
    !

Canonical and shorthand syntax can both be used in V2.

## 17. Project file

Example `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

With a project file, these commands use the configured entry automatically:

    janna run
    janna check
    janna test
    janna build

## 18. Editor Alpha

The Windows release includes:

    editor/janna-language-0.1.0.vsix

Install this VSIX in VS Code or Cursor to enable Janna language support.

The editor provides syntax highlighting and Janna run/check/test/build commands.

## 19. Janna Frontier

The release includes the larger V2 example project:

    examples/janna_frontier/

It demonstrates:

- multi-file modules
- project structure
- tests
- file and JSON persistence
- random events
- terminal input
- game state
- executable builds

Enter its folder and try:

    janna check
    janna test
    janna run

## 20. Help

    janna help
