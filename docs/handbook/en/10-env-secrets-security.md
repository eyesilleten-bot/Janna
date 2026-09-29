# 10. Environment, Secrets, and Release Security

## 10.1 Environment values

`env.get name` returns an environment value or `nothing` when missing.

Janna loads dotenv-style values relative to the source directory. Process environment values override dotenv values. Quoted and unquoted values are supported; malformed lines produce friendly errors.

## 10.2 Secrets

`secrets.get name` returns a secret wrapper or `nothing` when missing. `secrets.require name` fails when the secret is absent.

Secret values are deliberately redacted when displayed, converted to text, interpolated into strings, represented inside lists/objects, or included in diagnostic text. The visible form is `[REDACTED]`.

Use a secret value directly in supported runtime operations, such as HTTP headers or AI credentials, rather than displaying it.

## 10.3 Release protection

Project creation writes a `.gitignore` that excludes `.env` and `.env.*` while allowing `.env.example`. Release packaging also filters sensitive `.env` files and performs a final scan; packaging stops if a sensitive environment file is found in the release output.

Build tests also verify that local `.env` files are not embedded into generated applications.

## 10.4 Scope

Secret redaction protects values that entered Janna through the secret wrapper. It is not a substitute for operating-system permissions, safe credential rotation, or avoiding hard-coded credentials in source files.

