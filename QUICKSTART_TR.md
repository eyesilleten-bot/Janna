# Janna H?zl? Ba?lang??

## 1. Janna'y? kontrol et

Kurulumdan sonra yeni bir PowerShell penceresi a?:

    janna version

Mevcut komutlar? g?rmek i?in:

    janna help

## 2. Yeni proje olu?tur

Yeni proje olu?tur:

    janna new hello_project

Klas?re gir:

    cd hello_project

Tipik bir proje yap?s?:

    janna.toml
    src/
        app.ja
    tests/

## 3. Projeyi ?al??t?r

Projeyi ?al??t?r:

    janna run

?al??t?rmadan kontrol et:

    janna check

Testleri ?al??t?r:

    janna test

Windows EXE olu?tur:

    janna build

## 4. Tek dosyal? programlar

Janna'y? proje olu?turmadan da kullanabilirsin.

?rnek `hello.ja`:

    name is "Ege"

    show "Hello {name}"

?al??t?r:

    janna run hello.ja

Kontrol et:

    janna check hello.ja

EXE olu?tur:

    janna build hello.ja

## 5. De?i?kenler

    name is "Ege"
    age is 25
    active is yes
    empty is nothing

## 6. ??kt? ve kullan?c? girdisi

    show "Hello"
    show name
    show "Hello {name}"

    answer is ask "Your name: "
    show "Welcome {answer}"

## 7. Ko?ullar

    age is 25

    when age is at least 18
        show "Adult"
    otherwise
        show "Under 18"

## 8. D?ng?ler

    repeat 3
        show "Hello"

    number is 1

    while number is at most 3
        show number
        increase number by 1

## 9. Task yap?s?

    task greet person
        show "Hello {person}"

    greet "Ege"

Task'ler de?er d?nd?rebilir:

    task add a b
        give a + b

    result is add 10 20
    show result

## 10. Listeler ve object yap?lar?

    numbers is [10, 20, 30]

    show first of numbers
    show last of numbers
    show count of numbers

    add 40 to numbers

Object:

    player is
        name is "Ege"
        score is 100

    show player.name
    increase player.score by 50

## 11. Mod?ller

`src/greeter.ja` olu?tur:

    task greet name
        show "Hello {name}"

`src/app.ja` i?inden kullan:

    use greeter

    greeter.greet "Janna"

## 12. Dosya ve JSON i?lemleri

Dosyalar:

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

## 13. Text, random ve time

    use text
    use random
    use time

    show text.upper "janna"

    number is random.number 1 10
    show number

    show time.now

## 14. Hata yakalama

    use json

    attempt
        player is json.read "missing.json"

    if fails
        player is
            name is "Guest"

    show player.name

## 15. Janna testleri

?rnek:

    test "math works"
        expect 10 + 5 is 15

Proje testleri genellikle ?urada bulunur:

    tests/

?al??t?r:

    janna test

## 16. Klavye k?sayol syntax?

Janna V2 klavye k?sayol syntax?n? destekler.

Do?al syntax:

    name is "Janna"

    when name is "Janna"
        show "Hello"

K?sayol syntax?:

    name = "Janna"

    if name == "Janna"
        show "Hello"

Di?er baz? k?sayollar:

    +=
    -=
    ==
    !=
    >=
    <=
    &&
    ||
    !

V2 i?inde do?al ve k?sayol syntax? birlikte kullan?labilir.

## 17. Proje dosyas?

?rnek `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

Proje dosyas? bulundu?unda ?u komutlar entry dosyas?n? otomatik kullan?r:

    janna run
    janna check
    janna test
    janna build

## 18. Editor Alpha

Windows release paketinde ?u dosya bulunur:

    editor/janna-language-0.1.0.vsix

Bu VSIX dosyas?n? VS Code veya Cursor i?ine kurarak Janna dil deste?ini etkinle?tirebilirsin.

Editor syntax highlighting ve Janna run/check/test/build komutlar?n? sa?lar.

## 19. Janna Frontier

Release paketinde b?y?k V2 ?rnek projesi bulunur:

    examples/janna_frontier/

Bu proje ?unlar? g?sterir:

- ?ok dosyal? mod?ller
- proje yap?s?
- test sistemi
- dosya ve JSON kal?c?l???
- random event sistemi
- terminal girdisi
- oyun state y?netimi
- executable build

Klas?re girip ?unlar? deneyebilirsin:

    janna check
    janna test
    janna run

## 20. Yard?m

    janna help
