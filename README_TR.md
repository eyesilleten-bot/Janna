# Janna

Janna; okunabilir, doğrudan ve pratik olmayı hedefleyen, aynı zamanda gerçek çok dosyalı uygulamaları, build süreçlerini, runtime servislerini, AI iş akışlarını ve Windows dağıtımını destekleyen beginner-first bir programlama dilidir.

## Güncel sürüm

`0.3.0`

Janna V3 şu anda final release kapanış aşamasındadır. Final public release `0.3.0` sürümünü kullanacaktır.

## Janna V3 neler içeriyor?

- okunabilir canonical Janna syntaxı
- keyboard shorthand syntaxı
- AlienJanna sembolik rendering katmanı
- değişkenler, koşullar, döngüler, listeler ve object yapıları
- task'lar, return değerleri, user module'ler ve çok dosyalı projeler
- built-in test sistemi ve source checking
- `janna.toml` proje manifestleri
- Windows executable build
- files, paths, JSON, text, random ve time araçları
- Markdown ve DOCX document output
- terminal input ve runtime program arguments
- runtime version, capability, application path ve exit-code bilgileri
- HTTP istekleri
- schema validation
- resumable jobs ve checkpoints
- environment variables ve secret-safe handling
- AI generation, structured output, retry/repair davranışı ve usage bilgileri
- büyük metinler için context splitting ve context building
- source location ile task/module trace içeren diagnostics
- VS Code ve Cursor için Janna Editor Beta
- portable SDK ve Windows installer
- kısa Windows launcher: `ja`

## Kurulum

`JannaSetup.exe` dosyasını çalıştır.

Ardından yeni bir PowerShell penceresi açıp kurulumu doğrula:

    janna version

CLI yardımını göster:

    janna help

## Yeni proje oluşturma

Yeni bir Janna projesi oluştur:

    janna new my_project
    cd my_project

Projeyi çalıştır:

    janna run

Çalıştırmadan kontrol et:

    janna check

Proje testlerini çalıştır:

    janna test

Windows executable oluştur:

    janna build

Normal bir proje şu yapıyla başlar:

    my_project/
        janna.toml
        src/
            app.ja
        tests/

Örnek `janna.toml`:

    name = "my_project"
    entry = "src/app.ja"

## Tek dosya çalıştırma

`hello.ja` oluştur:

    name is "Ege"
    show "Hello {name}"

Çalıştır:

    janna run hello.ja

Ya da kısa Windows launcher'ını kullan:

    ja hello.ja

Program argümanları iki kullanımda da aktarılır:

    janna run hello.ja first second
    ja hello.ja first second

`runtime` modülünü kullanan program bu değerleri `runtime.arguments` üzerinden okuyabilir.

## Syntax katmanları

Janna V3 üç syntax katmanına sahiptir.

### Canonical syntax

    name is "Janna"

    when name is "Janna"
        show "Hello"

### Keyboard shorthand

    name := "Janna"

    ? name == "Janna"
        -> "Hello"

Keyboard shorthand çalıştırılabilir Janna source syntaxıdır. Normal parsing öncesinde normalize edilir ve canonical Janna ile aynı temel semantiği kullanır.

### AlienJanna

AlienJanna deterministik bir sembolik rendering katmanıdır. Canonical/keyboard Janna kodunu orijinal source'u değiştirmeden alternatif bir görsel biçimde render eder.

AlienJanna ayrı bir parser modu veya source dilinin yerine geçen başka bir syntax değildir.

## Standard library

Built-in modüller:

`files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context` ve `runtime`.

Kompakt action listesi için:

- `STDLIB_REFERENCE.md`
- `STDLIB_REFERENCE_TR.md`

## CLI reference

Kompakt komut referansı için:

- `CLI_REFERENCE.md`
- `CLI_REFERENCE_TR.md`

Ana komutlar:

    janna new <project_name>
    janna run [file.ja] [args...]
    janna check [file.ja]
    janna test [file.ja]
    janna build [file.ja]
    janna version
    janna help

Windows ayrıca şunu içerir:

    ja <file.ja> [args...]

Bu, `janna run` için kısa launcher'dır.

## Editor Beta

Janna Editor Beta, VS Code ve Cursor için Janna language support sağlar.

Güncel extension package sürümü `0.2.0`'dır.

Syntax highlighting ile birlikte active-file ve project seviyesinde şu komutları sağlar:

- Run
- Check
- Test
- Build

Release paketi VSIX dosyasını `editor/` klasörü altında içerir.

## Janna Frontier

`examples/janna_frontier/`, Janna'yı daha büyük bir uygulamada göstermek için kullanılan public örnek projedir.

Kurulumdan sonra proje klasöründe:

    janna run

çalıştır.

Ayrıca:

    janna check
    janna test
    janna build

komutlarını kullanabilirsin.

## Dokümantasyon

Başlangıç noktaları:

- `QUICKSTART.md` — hızlı İngilizce başlangıç
- `QUICKSTART_TR.md` — hızlı Türkçe başlangıç
- `HANDBOOK.md` — tam İngilizce handbook dizini
- `HANDBOOK_TR.md` — tam Türkçe handbook dizini
- `JANNA_HANDBOOK_EN.md` — birleştirilmiş İngilizce handbook
- `JANNA_HANDBOOK_TR.md` — birleştirilmiş Türkçe handbook
- `CLI_REFERENCE.md` / `CLI_REFERENCE_TR.md`
- `STDLIB_REFERENCE.md` / `STDLIB_REFERENCE_TR.md`

Handbook yaşayan dokümantasyon olarak tutulur: gelecekteki Janna sürümleri mevcut feature-family bölümlerini genişletir; gerçekten yeni subsystem'ler için yeni numaralı bölümler eklenebilir.

## Daha fazla yardım

    janna help



