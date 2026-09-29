# 7. Runtime Bilgisi, Argümanlar ve Exit Code'ları

`use runtime` sonrasında read-only property'ler: `runtime.version`, `runtime.channel`, `runtime.generation`, `runtime.capabilities`, `runtime.arguments`, `runtime.app_name`, `runtime.app_path`, `runtime.app_directory`.

Bu source snapshot'ında runtime generation `3`, version `0.3.0`, channel `release` olarak tanımlıdır.

`janna run app.ja alpha beta` çalıştırmasında `runtime.arguments` `[alpha, beta]` olur. Windows'taki `ja app.ja alpha beta` aynı argümanları `janna.exe run` üzerinden forward eder. Built executable'lar da kendi command-line argümanlarını alır.

Imported user module'ler root application'ın `app_name`, `app_path` ve `app_directory` kimliğini korur.

`runtime.exit code`, 0–255 arasında tam sayı exit code ile programı sonlandırır ve kod source/built execution'da dışarı taşınır.

V3 capability contract'i şunları içerir: `projects`, `user_modules`, `tests`, `keyboard_shorthand`, `alien_syntax`, `task_trace`, `source_locations`, `http`, `ai`, `schema`, `structured_output`, `retry_resilience`, `jobs`, `checkpoints`, `large_text`, `document_output`, `files_paths`, `runtime_arguments`, `runtime_app_info`, `runtime_exit`, `context_builder`.

