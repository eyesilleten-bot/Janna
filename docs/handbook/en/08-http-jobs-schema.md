# 8. HTTP, Jobs, and Schema Validation

## 8.1 HTTP

```janna
use http
response is http.get "https://example.com"
show response.status
```

Supported methods are `http.get`, `http.post`, `http.put`, and `http.delete`. Each takes a URL and optionally one options object.

Supported options are:

- `headers` — object; underscores in header names are converted to hyphens.
- `query` — object.
- `json` — JSON request body.
- `text` — text request body.
- `timeout` — positive number, default 30 seconds.

A request cannot provide both JSON and text bodies. Responses expose `status`, `text`, `headers`, and parsed `json` when available. HTTP error status codes such as 404 are represented as normal responses rather than automatically becoming Janna exceptions.

## 8.2 Jobs

```janna
use jobs
job is jobs.create nothing
job is jobs.start job "Working"
job is jobs.progress job 0.5 "Halfway"
job is jobs.complete job "Done"
```

Job objects contain `job_id`, `status`, `progress`, `message`, `checkpoint`, and `error`. Statuses are `pending`, `running`, `completed`, and `failed`.

Actions:

- `jobs.create nothing`
- `jobs.start job [message]`
- `jobs.progress job progress [message]` — progress from 0 to 1.
- `jobs.checkpoint job object`
- `jobs.complete job [message]`
- `jobs.fail job error_text`
- `jobs.save job path`
- `jobs.load path`

Only running jobs may update progress, checkpoint, complete, or fail. Job state is persisted as JSON.

## 8.3 Schema validation

`schema.validate schema value` returns an object with `valid`, `value`, and `errors`.

Supported schema types are `text`, `number`, `boolean`, `list`, and `object`.

Constraints include:

- text: `min_length`, `max_length`
- number: `min`, `max`
- primitive values: `one_of`
- list: required `items` schema
- object: required `fields` object; a field schema may set `optional is yes`

Nested validation errors include paths such as object field names and `items[index]`.

