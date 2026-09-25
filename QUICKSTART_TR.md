# Janna Hızlı Başlangıç

## Değişkenler

name is "Ege"
age is 25
active is yes
empty is nothing

## Ekrana çıktı verme

show "Hello"
show name
show "Hello {name}"

## Koşullar

age is 25

when age is at least 18
    show "Adult"
otherwise
    show "Under 18"

## Döngüler

repeat 3
    show "Hello"

number is 1

while number is at most 3
    show number
    increase number by 1

## Task yapısı

task greet person
    show "Hello {person}"

greet "Ege"

## Listeler

numbers is [10, 20, 30]

show first of numbers
show last of numbers
show count of numbers

add 40 to numbers

## Object yapısı

player is
    name is "Ege"
    score is 100

show player.name
increase player.score by 50

## Dosyalar

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

## Hata yakalama

use json

attempt
    player is json.read "missing.json"

if fails
    player is
        name is "Guest"

show player.name

## Program çalıştırma

janna run app.ja

## EXE oluşturma

janna build app.ja

## Test

janna test

## Sürüm kontrolü

janna version
