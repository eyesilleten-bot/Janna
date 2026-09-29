# 4. Task'ler, Modüller ve Testler

## 4.1 Task'ler

Task tanımları top-level olmalıdır.

```janna
task greet person
    show "Merhaba {person}"

greet "Ege"
```

`give` task'ten değer döndürür. Aynı task adının veya aynı parameter adının tekrarlanması reddedilir.

## 4.2 User module'ler

`use actions`, normal source execution'da önce aktif source dosyasının yanında `actions.ja` arar; sonra varsa module search path'lerine bakar. Circular import algılanır.

```janna
use actions
result is actions.explore state
```

Module'ün top-level variable ve task'leri property/call biçiminde erişilebilir. Build sırasında user module'ler recursive olarak toplanıp executable içine bundle edilir.

## 4.3 Built-in module seti

V3 public built-in module seti: `files`, `json`, `text`, `random`, `time`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context`, `runtime`.

## 4.4 Testler

```janna
test "addition works"
    expect 2 + 3 is 5
```

`janna test` project'in `tests` klasörünü; `janna test file.ja` belirli bir test dosyasını çalıştırır. CLI PASS/FAIL özetini verir ve başarısız test varsa non-zero exit code döndürür.

## 4.5 Hata yakalama

```janna
attempt
    risky_task
if fails
    show "Kurtarıldı"
```

`attempt` aynı indentation seviyesinde bir `if fails` bloğu ile takip edilmelidir.

