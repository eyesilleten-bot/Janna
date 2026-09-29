# Janna CLI Reference

| Command | Purpose |
|---|---|
| `janna new <project_name>` | Create a project |
| `janna run` | Run current project entry |
| `janna run <file.ja> [args...]` | Run file with arguments |
| `janna check` | Check current project |
| `janna check <file.ja>` | Check file |
| `janna build` | Build current project |
| `janna build <file.ja>` | Build file |
| `janna test` | Run project tests |
| `janna test <file.ja>` | Run one Janna test file |
| `janna version`, `--version`, `-v` | Version |
| `janna help`, `--help`, `-h` | Main help |
| `ja <file.ja> [args...]` | Windows short launcher for `janna run` |

Project manifest: `janna.toml` with non-empty `name` and existing `.ja` `entry`.

