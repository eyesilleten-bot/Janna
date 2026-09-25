# Janna Quick Start

## Variables

name is "Ege"
age is 25
active is yes
empty is nothing

## Output

show "Hello"
show name
show "Hello {name}"

## Conditions

age is 25

when age is at least 18
    show "Adult"
otherwise
    show "Under 18"

## Loops

repeat 3
    show "Hello"

number is 1

while number is at most 3
    show number
    increase number by 1

## Tasks

task greet person
    show "Hello {person}"

greet "Ege"

## Lists

numbers is [10, 20, 30]

show first of numbers
show last of numbers
show count of numbers

add 40 to numbers

## Objects

player is
    name is "Ege"
    score is 100

show player.name
increase player.score by 50

## Files

use files

files.write "note.txt" "Hello from Janna"
text is files.read "note.txt"
show text

## JSON

use json

player is
    name is "Ege"
    level is 7

json.write "player.json" player
loaded is json.read "player.json"

show loaded.name

## Error handling

use json

attempt
    player is json.read "missing.json"

if fails
    player is
        name is "Guest"

show player.name

## Run a program

janna run app.ja

## Build an EXE

janna build app.ja

## Test

janna test

## Version

janna version
