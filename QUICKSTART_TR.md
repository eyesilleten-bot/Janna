# Janna Hızlı Başlangıç

Bu rehber Janna V3 ile hızlıca çalışan bir program oluşturmak içindir. Dilin ve runtime'ın tam dokümantasyonu için `HANDBOOK_TR.md` dosyasına bak.

## 1. Kurulumu kontrol et

Yeni bir PowerShell penceresi aç:

    janna version
    janna help

## 2. Proje oluştur ve çalıştır

    janna new hello_project
    cd hello_project
    janna run

Yeni proje şu yapıyı kullanır:

    hello_project/
        janna.toml
        src/
            app.ja
        tests/

Kontrol, test ve build:

    janna check
    janna test
    janna build

## 3. Tek dosya çalıştır

`hello.ja` oluştur:

    name is "Ege"
    show "Hello {name}"

Çalıştır:

    janna run hello.ja

Windows'ta kısa launcher'ı da kullanabilirsin:

    ja hello.ja

## 4. Değerler ve input

    name is "Ege"
    age is 25
    active is yes
    empty is nothing

    answer is ask "Adın: "
    show "Merhaba {answer}"

## 5. Koşullar ve döngüler

    age is 25

    when age is at least 18
        show "Adult"
    otherwise
        show "Under 18"

    repeat 3
        show "Hello"

    number is 1

    while number is at most 3
        show number
        increase number by 1

## 6. Task'lar

    task greet person
        show "Hello {person}"

    greet "Ege"

Task bir değer döndürebilir:

    task add a b
        give a + b

    result is add 10 20
    show result

## 7. Listeler ve object'ler

    numbers is [10, 20, 30]
    show first of numbers
    add 40 to numbers

    player is
        name is "Ege"
        score is 100

    show player.name
    increase player.score by 50

## 8. Modüller

`src/greeter.ja` oluştur:

    task greet name
        show "Hello {name}"

`src/app.ja` içinden kullan:

    use greeter
    greeter.greet "Janna"

## 9. Built-in servisler

Janna V3 built-in modülleri:

    files
    json
    text
    random
    time
    env
    secrets
    http
    ai
    schema
    jobs
    context
    runtime

Örnek:

    use files

    files.write "note.txt" "Hello from Janna"
    content is files.read "note.txt"
    show content

Tüm action ve property'ler için `STDLIB_REFERENCE_TR.md` dosyasına bak.

## 10. Program argümanları

Çalıştır:

    ja hello.ja first second

Sonra argümanları oku:

    use runtime
    show runtime.arguments

## 11. Hata yakalama

    use json

    attempt
        player is json.read "missing.json"

    if fails
        player is
            name is "Guest"

    show player.name

## 12. Janna testleri

    test "math works"
        expect 10 + 5 is 15

Proje testleri normalde `tests/` klasöründe bulunur.

Çalıştır:

    janna test

## 13. Keyboard shorthand

Canonical:

    name is "Janna"
    show name

Keyboard shorthand:

    name := "Janna"
    -> name

Shorthand çalıştırılabilir source syntaxıdır ve normal parsing öncesinde normalize edilir.

AlienJanna ayrı bir sembolik rendering katmanıdır; başka bir parser modu değildir. Syntax katmanlarının tam açıklaması için `HANDBOOK_TR.md` dosyasına bak.

## 14. Editor Beta

Release paketi VS Code ve Cursor için Janna Editor Beta içerir. Extension package sürümü `0.2.0`'dır.

Syntax highlighting ile hem active file hem de project için Run / Check / Test / Build komutları sağlar.

## 15. Sonraki referanslar

- `HANDBOOK_TR.md` — tam handbook
- `CLI_REFERENCE_TR.md` — CLI özeti
- `STDLIB_REFERENCE_TR.md` — standard library özeti
- `examples/` — çalıştırılabilir örnekler
- `examples/janna_frontier/` — daha büyük proje örneği

