# Janna CLI Referansı

| Command | Amaç |
|---|---|
| `janna new <project_name>` | Project oluştur |
| `janna run` | Current project entry çalıştır |
| `janna run <file.ja> [args...]` | Dosyayı argümanlarla çalıştır |
| `janna check` | Current project kontrolü |
| `janna check <file.ja>` | Dosya kontrolü |
| `janna build` | Current project build |
| `janna build <file.ja>` | Dosya build |
| `janna test` | Project testlerini çalıştır |
| `janna test <file.ja>` | Tek Janna test dosyası çalıştır |
| `janna version`, `--version`, `-v` | Version |
| `janna help`, `--help`, `-h` | Ana help |
| `ja <file.ja> [args...]` | `janna run` için Windows kısa launcher |

Project manifest: `janna.toml` with non-empty `name` and existing `.ja` `entry`.

