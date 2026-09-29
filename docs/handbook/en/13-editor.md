# 13. Janna Editor Beta

The repository contains the Janna language extension package `janna-language` version `0.2.0`, publisher `eyesilleten-bot`. It targets the VS Code extension API and has been packaged as `janna-language-0.2.0.vsix`; the same VSIX can be installed in compatible editors such as Cursor.

## 13.1 Language support

The extension registers the Janna language, syntax grammar, and language configuration. The editor recognizes `.ja` and `.janna` files. The Janna CLI itself currently requires `.ja` for run/check/build inputs, so `.ja` is the portable project/source extension.

## 13.2 Commands

The Beta exposes eight commands:

- `Janna: Run`
- `Janna: Check`
- `Janna: Test`
- `Janna: Build`
- `Janna: Run Project`
- `Janna: Check Project`
- `Janna: Test Project`
- `Janna: Build Project`

File commands are available from editor/explorer surfaces, while project commands operate on the project workspace.

## 13.3 Development engine setting

`janna.developmentEnginePath` optionally points the extension at a development `janna.py`. Installed/release use can rely on the normal Janna CLI instead.

## 13.4 Beta scope

The editor is a language-support and command-integration layer. It is not a separate Janna runtime, parser, or compiler. Execution and validation remain owned by the Janna CLI/runtime.

