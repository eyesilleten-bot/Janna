# Janna Hızlı Başlangıç

## 1. Janna'yı kontrol et

Kurulumdan sonra yeni bir PowerShell penceresi aç:

    janna version

Komutları gör:

    janna help

## 2. Yeni proje oluştur

    janna new hello_project
    cd hello_project

Tipik proje yapısı:

    janna.toml
    src/
        app.ja
    tests/

## 3. Projeyi kullan

Çalıştır:

    janna run

Kontrol et:

    janna check

Testleri çalıştır:

    janna test

Windows EXE oluştur:

    janna build

## 4. Tek dosyalı programlar

`hello.ja`:

    name is "Ege"

    show "Hello {name}"

Çalıştır:

    janna run hello.ja

Kontrol et:

    janna check hello.ja

Build:

    janna build hello.ja

## 5. Değişkenler

    name is "Ege"
    age is 25
    active is yes
    empty is nothing

## 6. Çıktı ve kullanıcı girdisi

    show "Hello"
    show name
    show "Hello {name}"

    answer is ask "Your name: "
    show "Welcome {answer}"

## 7. Koşullar

    age is 25

    when age is at least 18
        show "Adult"
    otherwise
        show "Under 18"

## 8. Döngüler

    repeat 3
        show "Hello"

    number is 1

    while number is at most 3
        show number
        increase number by 1

## 9. Task yapısı

    task greet person
        show "Hello {person}"

    greet "Ege"

Değer döndüren task:

    task add a b
        give a + b

    result is add 10 20
    show result

## 10. Listeler ve object yapıları

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

## 11. Modüller

`src/greeter.ja`:

    task greet name
        show "Hello {name}"

`src/app.ja`:

    use greeter

    greeter.greet "Janna"

## 12. Dosya ve JSON işlemleri

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

## 15. Janna testleri

    test "math works"
        expect 10 + 5 is 15

Testler genellikle:

    tests/

klasöründe bulunur.

Çalıştır:

    janna test

## 16. Klavye kısayol syntaxı

Doğal:

    name is "Janna"

    when name is "Janna"
        show "Hello"

Kısayol:

    name = "Janna"

    if name == "Janna"
        show "Hello"

Diğer bazı kısayollar:

    +=
    -=
    ==
    !=
    >=
    <=
    &&
    ||
    !

## 17. Proje dosyası

`janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

Bundan sonra:

    janna run
    janna check
    janna test
    janna build

komutları proje entry dosyasını otomatik kullanır.

## 18. Editor Alpha

Release paketindeki:

    editor/janna-language-0.1.0.vsix

dosyası VS Code veya Cursor'a kurulabilir.

## 19. Janna Frontier'ı çalıştır

GitHub'da **Releases > Janna 0.2.0** yolunu aç.

`JannaSetup.exe` indirip kurduktan sonra:

    examples/janna_frontier/

klasöründe PowerShell aç ve:

    janna run

yaz.

Kontrol ve test:

    janna check
    janna test

ZIP kullanıyorsan Frontier klasöründen:

    ../../janna.exe run

## 20. Yardım

    janna help
