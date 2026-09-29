# 1. Language Basics

Janna is an indentation-based programming language built around readable statements. The command-line tool accepts `.ja` source files. Source is read as UTF-8; a UTF-8 BOM is accepted. Blank lines are ignored, and a line whose first non-space character is `#` is a comment.

## 1.1 First program

```janna
name is "Ege"
show "Hello {name}"
```

`is` assigns a value. `show` displays an expression. String interpolation uses `{name}` inside a string.

## 1.2 Indentation

Blocks are defined by indentation. Tabs are rejected. Each block level is exactly four spaces.

```janna
repeat 3
    show "Hello"
```

## 1.3 Values

Canonical Janna literals include text, whole numbers, decimal numbers, `yes`, `no`, and `nothing`.

```janna
message is "Hello"
count is 10
ratio is 1.5
ready is yes
finished is no
result is nothing
```

Keyboard shorthand also accepts `true`, `false`, and `null`, which normalize to `yes`, `no`, and `nothing` before parsing.

## 1.4 Expressions

Arithmetic supports `+`, `-`, `*`, `/`, `%`, unary minus, and parentheses. Multiplication, division, and modulo bind more tightly than addition and subtraction.

```janna
score is 10 + 2 * 3
negative is -5
value is (10 + 2) * 3
```

## 1.5 Conditions

Canonical comparison vocabulary is:

- `is`
- `is not`
- `is above`
- `is below`
- `is at least`
- `is at most`
- `is in`
- `is not in`

Conditions can be combined with `and`, `or`, and `not`. A bare value in a condition is compared with `yes`.

```janna
when age is at least 18 and ready
    show "Ready"
otherwise
    show "Not ready"
```

## 1.6 Input and output

`ask` reads input. `show` writes a value.

```janna
name is ask "Name: "
show "Hello {name}"
```

## 1.7 Blocks and core statements

Core statement families include `use`, `show`, assignment with `is`, `when`, `otherwise when`, `otherwise`, `repeat`, `repeat forever`, `while`, `each`, `add`, `remove`, `increase`, `decrease`, `task`, `give`, `attempt`, `if fails`, `test`, `expect`, `stop`, and `skip`. Later chapters document their context and behavior.

