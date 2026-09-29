# 3. Values, Collections, and Control Flow

## 3.1 Lists

Lists use square brackets.

```janna
numbers is [10, 20, 30]
show count of numbers
show first of numbers
show last of numbers
add 40 to numbers
remove 20 from numbers
```

`count of`, `first of`, and `last of` are expressions. `add ... to ...` and `remove ... from ...` mutate a named list.

## 3.2 Objects

Objects are indentation-based.

```janna
player is
    name is "Ege"
    level is 1
    stats is
        score is 100
```

Properties are read with dotted access and can be assigned through dotted paths.

```janna
show player.name
player.stats.score is 150
increase player.level by 1
```

## 3.3 Conditional flow

```janna
when score is above 90
    show "High"
otherwise when score is at least 50
    show "Medium"
otherwise
    show "Low"
```

`otherwise when` may chain recursively. `otherwise` closes the chain.

## 3.4 Loops

```janna
repeat 3
    show "Three times"

number is 1
while number is at most 3
    show number
    increase number by 1

each item in items
    show item
```

`repeat forever` creates an unbounded loop. `stop` exits the active loop and `skip` continues to its next iteration.

## 3.5 Mutation

`increase target by value` and `decrease target by value` support variables and dotted property paths. They require numeric values at runtime.

## 3.6 Membership and logic

Conditions support list membership with `is in` and `is not in`, logical `and` / `or`, and unary `not`.

