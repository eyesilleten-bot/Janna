# 5. Standard Library

Built-in modüller kullanılmadan önce `use` ile etkinleştirilir.

## 5.1 `text`

`text.newline`, `text.lower`, `text.upper`, `text.trim`, `text.replace`, `text.split`, `text.contains`, `text.length`, `text.matches`, `text.join`, `text.write`, `text.lexical_issues`.

`text.lexical_issues text language` için mevcut lexical language desteği English ve Turkish'tir.

## 5.2 `json`

`json.read path`, `json.parse text`, `json.stringify value`, `json.write path value`.

JSON output UTF-8 ve Unicode-preserving biçimde yazılır.

## 5.3 `random`

`random.number minimum maximum` inclusive tam sayı üretir. `random.choose list` listeden bir değer seçer; boş liste reddedilir.

## 5.4 `time`

`time.now "iso"`, `time.now "date"`, `time.now "time"`, `time.wait seconds`.

## 5.5 Diğer modüller

`files`, `env`, `secrets`, `http`, `ai`, `schema`, `jobs`, `context` ve `runtime` ayrı bölümlerde ayrıntılandırılır.

V3 API compatibility testleri built-in module adlarını public contract olarak sabitler.

