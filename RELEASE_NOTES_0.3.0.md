# Janna 0.3.0 Release Notes

Janna 0.3.0 is the V3 release. It expands Janna from the V2 language/runtime baseline into a more complete project, runtime, tooling, editor, packaging, and AI-capable development environment.

## Highlights

### Syntax and language layers

Janna V3 keeps canonical Janna syntax as the primary readable form and adds two additional syntax layers:

- Keyboard Shorthand: directly executable shorthand syntax normalized before normal parsing.
- AlienJanna: a deterministic symbolic rendering layer for presentation and transformation. It does not replace the parser or mutate the original source.

Examples of keyboard shorthand include:

    name := "Ege"
    -> name
    @5
        -> "Hello"

Canonical and shorthand forms share the same underlying semantics.

### Runtime arguments and application information

Programs can access command-line arguments through the `runtime` module.

Example:

    use runtime
    show runtime.arguments

Both of these forms forward program arguments:

    janna run app.ja first second
    ja app.ja first second

The runtime also exposes application/runtime metadata and explicit process exit support.

### Runtime exit codes

Janna programs can terminate with an explicit process exit code.

Example:

    use runtime
    runtime.exit 7

This works in normal source execution and built applications.

### Files, paths, and directories

The files/runtime surface was expanded to support production-oriented path and filesystem workflows, including path composition, file/folder inspection, and directory operations.

### Document output

Janna V3 adds first-class document-oriented output alongside normal text file operations, including Markdown and DOCX generation.

### HTTP

The `http` module supports common request workflows, including:

- GET
- POST
- PUT
- DELETE
- request options
- query/header handling
- timeouts
- JSON/text bodies

Error cases are surfaced as Janna-friendly diagnostics.

### Jobs and checkpoints

The `jobs` module supports longer-running workflows with lifecycle state, progress, checkpoints, save/load behavior, and resume-oriented flows.

### Schema validation

The `schema` module supports validation for:

- text
- number
- boolean
- list
- object
- nested structures
- optional fields
- enum constraints
- text length constraints
- numeric min/max constraints

Validation errors preserve useful paths into nested data.

### AI runtime

Janna V3 expands the AI surface with:

- `ai.generate`
- provider validation
- timeout validation
- structured output
- schema forwarding
- structured JSON validation
- one repair attempt for invalid structured output
- retry behavior
- usage aggregation
- pricing/cost observability

### Context building

The `context` module supports large-text workflows through:

- `context.split`
- `context.build`

This allows long source material to be broken into manageable sections and assembled into bounded context.

### Environment and secrets

V3 adds hardened environment and secret handling:

- optional `.env` loading
- quoted/unwrapped value parsing
- process environment override behavior
- safe parse errors
- secret-safe display/interpolation behavior
- nested redaction
- error-trace redaction
- release filtering so `.env` is not embedded into distributed builds

### Diagnostics and hardening

V3 improves diagnostics for:

- parse errors
- runtime errors
- task/module traces
- file/module context
- invalid project files
- missing variables/tasks
- circular module problems
- wrong argument counts
- division-by-zero and related runtime failures

### Projects and production builds

Janna V3 formalizes project workflows around `janna.toml`.

A standard project uses:

    name = "my_project"
    entry = "src/app.ja"

Core project commands include:

    janna new
    janna run
    janna check
    janna test
    janna build

Builds support source files, project entry points, user modules, and nested modules.

### Windows short launcher

The Windows SDK and installer include:

    ja

This is a short launcher for:

    janna run

Example:

    ja app.ja alpha beta

### Editor Beta

Janna Editor Beta supports VS Code and Cursor.

Current extension package version:

    0.2.0

It provides syntax highlighting plus active-file and project commands for:

- Run
- Check
- Test
- Build

### SDK, packaging, and installer

V3 includes a portable Windows SDK, release ZIP, installer, PATH integration, and packaging acceptance coverage.

The release pipeline includes security checks and excludes sensitive `.env` content.

### Compatibility freeze

V3 includes compatibility coverage for:

- primary CLI commands
- help/version aliases
- built-in module contracts
- runtime capability contracts

This is intended to make later V3 maintenance safer and give V4 a clearer compatibility boundary.

## Documentation

Janna V3 includes a reorganized documentation set:

- `README.md`
- `README_TR.md`
- `QUICKSTART.md`
- `QUICKSTART_TR.md`
- `HANDBOOK.md`
- `HANDBOOK_TR.md`
- `docs/handbook/en/`
- `docs/handbook/tr/`
- `CLI_REFERENCE.md`
- `CLI_REFERENCE_TR.md`
- `STDLIB_REFERENCE.md`
- `STDLIB_REFERENCE_TR.md`

The Handbook is designed as living documentation. Future versions can extend existing feature-family chapters or add new numbered chapters for genuinely new subsystems.

## Public repository boundary

The public Janna repository should contain release-facing material and examples, not Janna implementation source.

Allowed public material includes:

- README/docs
- LICENSE
- `.gitignore`
- examples
- `.ja` source examples
- `janna.toml`
- release ZIP/EXE/VSIX artifacts
- the Janna Frontier example project

Interpreter/compiler/runtime implementation source, internal Python files, tests, editor implementation source, and installer source are not part of the public-source surface.

## Release status

Janna 0.3.0 documentation and packaging are prepared for final V3 closure.

Before the final public release, complete the final version switch, clean-machine validation, final regression/release build, and GitHub release publication.

