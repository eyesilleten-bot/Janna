# 2. Syntax Layers

Janna V3 has three related syntax layers: canonical Janna, Keyboard Shorthand, and AlienJanna rendering.

## 2.1 Canonical Janna

Canonical syntax is the language form understood after normalization.

```janna
use text
name is "Ege"
when score is above 10
    show name
```

## 2.2 Keyboard Shorthand

Keyboard shorthand is ASCII source syntax. The lexer normalizes it before parsing, so shorthand and canonical forms share the same parser and runtime semantics. Quoted strings are protected from shorthand rewriting.

Common forms:

| Shorthand | Canonical |
|---|---|
| `+text` | `use text` |
| `name := "Ege"` | `name is "Ege"` |
| `name = "Ege"` | `name is "Ege"` |
| `-> name` or `>> name` | `show name` |
| `? score > 10` | `when score is above 10` |
| `?? score >= 5` | `otherwise when score is at least 5` |
| `:` | `otherwise` |
| `@5` | `repeat 5` |
| `@forever` | `repeat forever` |
| `@ item : items` | `each item in items` |
| `health += 5` | `increase health by 5` |
| `health -= 2` | `decrease health by 2` |
| `push value to items` | `add value to items` |
| `len items` | `count of items` |
| `first items` | `first of items` |
| `last items` | `last of items` |
| `input "Name: "` | `ask "Name: "` |
| `for item in items` | `each item in items` |
| `import files` | `use files` |
| `try` / `catch` | `attempt` / `if fails` |
| `assert condition` | `expect condition` |
| `fn greet name` | `task greet name` |
| `return value` | `give value` |
| `break` / `continue` | `stop` / `skip` |
| `if` / `else if` / `else` | `when` / `otherwise when` / `otherwise` |
| `== != > < >= <=` | canonical comparison vocabulary |
| `&& || !` | `and or not` |
| `true false null` | `yes no nothing` |

## 2.3 AlienJanna rendering

AlienJanna is currently a deterministic **presentation/rendering layer**, not a separate parser mode. `render_alien_source` first normalizes Keyboard Shorthand, then renders canonical vocabulary symbolically while preserving indentation, blank lines, comments, and the original source file itself.

The current renderer deliberately uses ASCII `?`-based symbols. There are no hidden non-ASCII glyphs in `alien_syntax.py` in this source snapshot.

Important: there is currently no public CLI or editor command that switches a `.ja` file into an executable AlienJanna source mode. The runtime advertises the `alien_syntax` capability because the rendering layer exists, but normal execution still goes through canonical/normalized Janna.

## 2.4 Same semantics

The syntax-layer tests verify that canonical and Keyboard Shorthand programs produce equivalent behavior and that shorthand continues to work through check, test, run, and build flows.

