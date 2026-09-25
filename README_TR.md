# Janna

Janna, programlamaya yeni başlayanlar için okunabilir, sade ve pratik olacak şekilde tasarlanmış bir programlama dilidir.

## Güncel sürüm

0.2.0

## Janna Frontier'ı çalıştırma

GitHub repository'sinden Janna Frontier'ı denemek için:

1. Repository'nin sağ tarafındaki **Releases** bölümüne gir.
2. **Janna 0.2.0** release'ini aç.
3. `JannaSetup.exe` dosyasını indir ve Janna'yı kur.
4. Kurulum klasöründeki `examples/janna_frontier` klasörünü aç.
5. Bu klasörde PowerShell aç ve şunu çalıştır:

    janna run

Önce kontrol veya test yapmak istersen:

    janna check
    janna test

Kurulum yapmak istemiyorsan `Janna-0.2.0-Windows.zip` dosyasını indirip çıkarabilirsin.

ZIP içindeki `examples/janna_frontier` klasöründe:

    ../../janna.exe run

## Janna V2 neler yapabiliyor?

- değişkenler, koşullar, döngüler, listeler ve object yapıları
- task yapısı ve geri dönüş değerleri
- kullanıcı modülleri ve çok dosyalı projeler
- `janna.toml` tabanlı proje sistemi
- dosya ve JSON işlemleri
- text, random ve time araçları
- terminalden kullanıcı girdisi
- `attempt ... if fails` ile hata yakalama
- Janna test sistemi
- `janna check` ile proje kontrolü
- klavye kısayol syntaxı
- `.ja` dosyalarını ve projeleri Windows `.exe` dosyasına dönüştürme
- VS Code / Cursor için Janna Editor Alpha

## Kurulum

`JannaSetup.exe` dosyasını çalıştır.

Kurulumdan sonra yeni bir PowerShell penceresi aç:

    janna version

## Yeni proje oluşturma

Yeni proje:

    janna new my_project

Proje klasörüne gir:

    cd my_project

Projeyi çalıştır:

    janna run

Kontrol et:

    janna check

Testleri çalıştır:

    janna test

Windows EXE oluştur:

    janna build

## İlk Janna programın

`hello.ja`:

    name is "Ege"

    show "Hello {name}"

Çalıştır:

    janna run hello.ja

EXE oluştur:

    janna build hello.ja

## Proje yapısı

    my_project/
        janna.toml
        src/
            app.ja
        tests/

Örnek `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

## Klavye kısayol syntaxı

Doğal syntax:

    name is "Janna"

    when name is "Janna"
        show "Hello"

Kısayol syntaxı:

    name = "Janna"

    if name == "Janna"
        show "Hello"

Janna V2 iki syntax biçimini de destekler.

## Editor Alpha

Release paketi VS Code / Cursor için Janna Editor Alpha paketini içerir:

    editor/janna-language-0.1.0.vsix

## Janna Frontier

Büyük V2 demo projesi:

    examples/janna_frontier/

Frontier; çok dosyalı modüller, test sistemi, kayıt sistemi, JSON, random event'ler, terminal girdisi ve executable build gibi V2 özelliklerini kullanır.

## Syntax katmanları

1. doğal / canonical başlangıç syntaxı
2. klavye kısayol syntaxı
3. sembolik / uzaylı görünüm syntaxı

V2 ilk iki katmanı destekler.

## Daha fazla yardım

    janna help

Daha ayrıntılı başlangıç rehberi:

    QUICKSTART_TR.md
