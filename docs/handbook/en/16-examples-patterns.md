# 16. Examples and Patterns

The repository includes small examples for hello/output, conditions, loops, tasks, lists, objects, and files/JSON, plus the larger Janna Frontier project.

## 16.1 Small complete program

```janna
use random

name is ask "Name: "
roll is random.number 1 6

show "Hello {name}"
show "You rolled:"
show roll
```

## 16.2 State object + task

```janna
state is
    food is 50
    morale is 75

task eat amount
    decrease state.food by amount
    give state.food

remaining is eat 5
show remaining
```

## 16.3 Module pattern

`actions.ja`:

```janna
task rest state
    increase state.morale by 5
    give yes
```

`app.ja`:

```janna
use actions

state is
    morale is 50

result is actions.rest state
show state.morale
```

## 16.4 Persistence pattern

```janna
use files
use json

state is
    name is "Ege"
    level is 7

json.write "save.json" state
loaded is json.read "save.json"
show loaded.level
```

## 16.5 Long-running job pattern

```janna
use jobs

job is jobs.create nothing
job is jobs.start job "Started"
job is jobs.progress job 0.5 "Halfway"
checkpoint is
    page is 5
job is jobs.checkpoint job checkpoint
job is jobs.complete job "Finished"
```


## 16.6 Frontier as a dogfood example

Janna Frontier demonstrates multi-file user modules, shared mutable object state, tasks, random events, `repeat forever`, `stop`, `skip`, JSON save/load, tests, and project build behavior. It is the repository's broad end-to-end example and should remain a useful compatibility/dogfood target as Janna evolves.

