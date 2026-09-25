# Janna

Janna, programlamaya yeni ba?layanlar i?in okunabilir, sade ve pratik olacak ?ekilde tasarlanm?? bir programlama dilidir.

## G?ncel s?r?m

0.1.1

## Janna V2 neler yapabiliyor?

- de?i?kenler, ko?ullar, d?ng?ler, listeler ve object yap?lar?
- task yap?s? ve geri d?n?? de?erleri
- kullan?c? mod?lleri ve ?ok dosyal? projeler
- `janna.toml` tabanl? proje sistemi
- dosya ve JSON i?lemleri
- text, random ve time ara?lar?
- terminalden kullan?c? girdisi
- `attempt ... if fails` ile hata yakalama
- Janna test sistemi
- `janna check` ile proje kontrol?
- klavye k?sayol syntax?
- `.ja` dosyalar?n? ve projeleri Windows `.exe` dosyas?na d?n??t?rme
- VS Code / Cursor i?in Janna Editor Alpha

## Kurulum

?unu ?al??t?r:

    JannaSetup.exe

Kurulumdan sonra yeni bir PowerShell penceresi a? ve ?unu yaz:

    janna version

## Yeni proje olu?turma

Yeni bir Janna projesi olu?tur:

    janna new my_project

Sonra proje klas?r?ne gir:

    cd my_project

Projeyi ?al??t?r:

    janna run

Kontrol et:

    janna check

Testleri ?al??t?r:

    janna test

Windows EXE olu?tur:

    janna build

## ?lk Janna program?n

Tek bir `.ja` dosyas?yla da ?al??abilirsin.

`hello.ja` olu?tur:

    name is "Ege"

    show "Hello {name}"

?al??t?r:

    janna run hello.ja

EXE olu?tur:

    janna build hello.ja

## Proje yap?s?

Tipik bir Janna projesi ??yle g?r?n?r:

    my_project/
        janna.toml
        src/
            app.ja
        tests/

?rnek `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

## Klavye k?sayol syntax?

Janna V2 hem do?al ba?lang?? syntax?n? hem de klavye k?sayol syntax?n? destekler.

Do?al syntax:

    name is "Janna"

    when name is "Janna"
        show "Hello"

Klavye k?sayol syntax?:

    name = "Janna"

    if name == "Janna"
        show "Hello"

?ki kullan?m da Janna V2 i?inde ge?erlidir.

## Editor Alpha

Release paketi Janna Editor Alpha VSIX dosyas?n? i?erir.

Bu extension VS Code ve Cursor i?inde Janna syntax highlighting ve Janna komutlar? sa?lar.

VSIX dosyas? ?urada bulunur:

    editor/

## ?rnekler

`examples` klas?r?nde k???k ?rneklerin yan?nda b?y?k V2 demo projesi de bulunur:

    01_hello.ja
    02_conditions.ja
    03_loops.ja
    04_tasks.ja
    05_lists.ja
    06_objects.ja
    07_files_json.ja
    janna_frontier/

`janna_frontier`, Janna V2 proje ?zelliklerini g?stermek ve test etmek i?in geli?tirilmi? ?ok dosyal? terminal tabanl? bir koloni hayatta kalma oyunudur.

## Syntax katmanlar?

Janna i?in ?? syntax katman? planlanm??t?r:

1. do?al / canonical ba?lang?? syntax?
2. klavye k?sayol syntax?
3. sembolik / uzayl? g?r?n?m syntax?

V2 ilk iki katman? destekler.

Sembolik/uzayl? katman? daha sonraki bir s?r?m i?in planlanm??t?r.

## Daha fazla yard?m

?unu kullan:

    janna help

K?sa ba?lang?? rehberi i?in:

    QUICKSTART_TR.md
