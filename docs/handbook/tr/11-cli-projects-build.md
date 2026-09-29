# 11. CLI, Projects ve Build

Ana commands:

```text
janna new <project_name>
janna run
janna run <file.ja> [arguments...]
janna check
janna check <file.ja>
janna build
janna build <file.ja>
janna test
janna test <file.ja>
janna version
janna help
```

Help aliases: `help`, `--help`, `-h`. Version aliases: `version`, `--version`, `-v`. Command-specific help `janna <command> --help` biçimini destekler.

Windows SDK'daki `ja app.ja arg1 arg2`, `janna.exe run app.ja arg1 arg2` için kısa launcher'dır.

Project root'ta `janna.toml` gerekir:

```toml
name = "my_app"
entry = "src/app.ja"
```

`name` boş olamaz; `entry` `.ja` olmalı ve var olmalıdır. `janna new demo`; `src/app.ja`, `tests/test_app.ja`, `janna.toml` ve `.gitignore` oluşturur.

File argümanı verilmediğinde `run`, `check`, `build`, `test` current project üzerinde çalışır.

`janna build`, önce source'u validate eder, sonra `dist\<name>.exe` üretir. User module'ler recursive bundle edilir; missing/circular modules build'i durdurur. Installed Janna private portable builder runtime kullanır. `text.lexical_issues` kullanan build'ler English/Turkish morphology data'sını dahil eder; ordinary build'ler bu ekstra payload'ı taşımaz.

