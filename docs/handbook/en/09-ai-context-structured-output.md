# 9. AI, Context, and Structured Output

## 9.1 AI generation

Enable AI with `use ai`. The public generation action is `ai.generate` with one options object.

Required options:

- `api_key`
- `model` — text
- `input` — text

Optional options:

- `provider` — defaults to `openai`
- `base_url`
- `timeout` — positive number, default 60 seconds
- `instructions`
- `max_output_tokens` — positive integer
- `retry`
- `pricing`
- `schema`

The current provider registry implements OpenAI. Unknown provider names are rejected with a Janna runtime error.

## 9.2 Retry policy

`retry` is an object supporting `max_attempts`, `initial_delay`, `backoff_multiplier`, and `max_delay`. Provider failures record attempt and retry metadata for observability.

## 9.3 AI response object

`ai.generate` returns fields including `text`, `model`, `response_id`, `usage`, `provider`, `duration_ms`, `attempts`, `retry_count`, `raw`, `estimated_cost`, `structured`, `schema_valid`, and `schema_errors`.

If provider token usage is available, `usage` contains `input_tokens`, `output_tokens`, and `total_tokens`.

## 9.4 Cost observability

A `pricing` object may supply `input_per_million` and `output_per_million`. When token usage and pricing are both available, Janna computes `estimated_cost`.

`ai.usage` returns aggregate state for the interpreter, including request/success/failure counts, token totals, duration, attempts, retries, pricing coverage, last provider/model, and the last error. Imported modules share the same AI usage state.

## 9.5 Structured output

Provide a Janna schema through the `schema` option. Janna parses the model text, validates it, and fills `structured`, `schema_valid`, and `schema_errors`. If the first response is invalid, Janna performs one structured-output repair request and validates the repaired result.

## 9.6 Context helpers

`context.split text [chunk_size]` splits text into indexed chunks; the default chunk size is 4000 characters.

`context.build options` requires `max_chars` and accepts `pinned` text items plus `recent` chunk objects. It builds a bounded layered context that prioritizes pinned context and keeps recent content within the character budget.

These helpers are runtime primitives; they do not automatically call an AI provider.

