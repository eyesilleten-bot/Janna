# 8. HTTP, Jobs ve Schema Validation

## 8.1 HTTP

Supported actions: `http.get`, `http.post`, `http.put`, `http.delete`. Her biri URL ve optional bir options object alır.

Options: `headers`, `query`, `json`, `text`, `timeout`. `timeout` varsayılan 30 saniyedir ve pozitif sayı olmalıdır. `json` ve `text` body aynı request'te birlikte kullanılamaz. Header key'lerindeki `_` karakterleri `-` olarak normalize edilir.

Response object alanları: `status`, `text`, `headers`, `json`. 404 gibi HTTP status'ları otomatik Janna exception'ına çevrilmeden normal response olarak dönebilir.

## 8.2 Jobs

Actions: `jobs.create nothing`, `jobs.start job [message]`, `jobs.progress job progress [message]`, `jobs.checkpoint job object`, `jobs.complete job [message]`, `jobs.fail job error_text`, `jobs.save job path`, `jobs.load path`.

Job alanları: `job_id`, `status`, `progress`, `message`, `checkpoint`, `error`. Status değerleri `pending`, `running`, `completed`, `failed`. Progress 0–1 aralığındadır. Yalnız running job progress/checkpoint/complete/fail işlemi yapabilir. State JSON olarak persist edilir.

## 8.3 Schema

`schema.validate schema value` sonucu `valid`, `value`, `errors` alanlarını içerir.

Supported type'lar: `text`, `number`, `boolean`, `list`, `object`. Constraint'ler: text için `min_length`/`max_length`; number için `min`/`max`; primitive değerler için `one_of`; list için `items`; object için `fields`; object field schema'sında `optional is yes`.

Nested error path'leri field adlarını ve `items[index]` biçimini korur.

