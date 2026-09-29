# 16. Örnekler ve Pattern'ler

Repository; hello/output, conditions, loops, tasks, lists, objects, files/JSON örneklerinin yanında daha büyük Janna Frontier project'ini içerir.

## 16.1 Küçük program

```janna
use random

name is ask "Ad: "
roll is random.number 1 6
show "Merhaba {name}"
show roll
```

## 16.2 State + task

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

## 16.3 User module

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

## 16.4 Persistence

```janna
use json
state is
    name is "Ege"
    level is 7
json.write "save.json" state
loaded is json.read "save.json"
show loaded.level
```

## 16.5 Long-running job

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

## 16.6 Janna Frontier

Janna Frontier; multi-file user modules, shared mutable object state, tasks, random events, `repeat forever`, `stop`, `skip`, JSON save/load, tests ve project build davranışını birlikte gösteren geniş end-to-end dogfood örneğidir. Janna geliştikçe compatibility/dogfood hedefi olarak korunması değerlidir.

