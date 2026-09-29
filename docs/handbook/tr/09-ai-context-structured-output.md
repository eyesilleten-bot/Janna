# 9. AI, Context ve Structured Output

## 9.1 `ai.generate`

`use ai` sonrasında `ai.generate` tek options object alır. Required: `api_key`, text `model`, text `input`. Optional: `provider` (default `openai`), `base_url`, `timeout` (default 60), `instructions`, `max_output_tokens`, `retry`, `pricing`, `schema`.

Bu source snapshot'ındaki provider registry OpenAI provider'ını implement eder; bilinmeyen provider adı Janna runtime error üretir.

## 9.2 Retry ve observability

`retry` object'i `max_attempts`, `initial_delay`, `backoff_multiplier`, `max_delay` alanlarını destekler.

Response alanları `text`, `model`, `response_id`, `usage`, `provider`, `duration_ms`, `attempts`, `retry_count`, `raw`, `estimated_cost`, `structured`, `schema_valid`, `schema_errors` içerir.

`pricing` için `input_per_million` ve `output_per_million` verildiğinde, token usage mevcutsa estimated cost hesaplanır. `ai.usage` aggregate request/success/failure, token, süre, attempt/retry, pricing coverage ve son provider/model/error durumunu döndürür. User module'ler aynı usage state'i paylaşır.

## 9.3 Structured output

`schema` option'ı verilirse model text'i parse edilir ve Janna schema validator ile kontrol edilir. İlk sonuç invalid ise Janna bir kez repair request yapar, sonra repaired result'ı tekrar validate eder.

## 9.4 Context

`context.split text [chunk_size]` indexed chunk listesi üretir; default chunk size 4000 karakterdir.

`context.build options`, `max_chars` alanını zorunlu tutar; `pinned` text listesi ve `recent` chunk object'leri kabul eder. Character budget içinde layered context üretir ve pinned/recent ayrımını korur.

Context helper'ları kendileri AI call yapmaz.

