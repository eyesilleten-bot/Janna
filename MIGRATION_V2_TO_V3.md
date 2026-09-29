# Migrating from Janna V2 to Janna V3

Janna V3 is designed as an evolution of the existing Janna language rather than a replacement. Existing canonical Janna source should remain the preferred migration baseline.

This guide focuses on the user-facing changes introduced in V3.

## 1. Version and release state

V2 documentation and packaging used the 0.2.x line.

V3 moves the language/runtime release line to:

    0.3.0

Development builds reported:

    0.3.0-dev

The final V3 release reports:

    0.3.0

## 2. Canonical syntax remains valid

You do not need to rewrite normal canonical Janna code just because V3 adds new syntax layers.

Example:

    name is "Ege"
    show name

remains normal Janna source.

## 3. Keyboard shorthand is optional

V3 supports executable keyboard shorthand.

Canonical:

    name is "Ege"
    show name

Keyboard shorthand:

    name := "Ege"
    -> name

Shorthand is normalized before the normal parser. Use it only where you want a denser typing style.

Existing canonical code does not need conversion.

## 4. AlienJanna is not a source migration target

AlienJanna is a symbolic rendering layer.

It should not be treated as a new parser mode or a required replacement syntax for existing source files.

Keep canonical or keyboard Janna as executable source.

## 5. Program arguments

V3 adds runtime program arguments.

Run:

    janna run app.ja first second

or on Windows:

    ja app.ja first second

Read them in Janna:

    use runtime
    show runtime.arguments

If a V2 application previously depended on hard-coded startup values, it can now move those values to command-line arguments where appropriate.

## 6. Explicit exit codes

V3 supports explicit process exit codes:

    use runtime
    runtime.exit 7

This is especially useful for scripts, automation, CLI applications, and external process integration.

## 7. Project manifests

V3 formalizes project workflows around `janna.toml`.

A minimal project manifest is:

    name = "my_project"
    entry = "src/app.ja"

Both fields are part of the project contract.

For larger V2 projects, migrate toward a project layout such as:

    my_project/
        janna.toml
        src/
            app.ja
        tests/

## 8. Project commands

Use the V3 project workflow:

    janna run
    janna check
    janna test
    janna build

You can still work with explicit `.ja` files where supported.

## 9. Short Windows launcher

V3 Windows installs include:

    ja

Instead of:

    janna run app.ja

you may write:

    ja app.ja

Arguments are forwarded unchanged.

This is optional; existing `janna run` workflows remain valid.

## 10. Runtime module expansion

The `runtime` module now covers more application-level behavior, including:

- program arguments
- runtime/application information
- capabilities
- explicit exit codes

Applications that previously handled this outside Janna can migrate those concerns into the runtime module where useful.

## 11. Files, paths, and document output

V3 expands file/path functionality and adds document-oriented output.

If a V2 project manually assembled paths or relied on external helpers, review the V3 `files` surface before keeping that custom code.

Markdown and DOCX output are now part of the documented V3 feature set.

## 12. HTTP workflows

V3 adds a fuller HTTP runtime surface.

Projects that previously relied on custom external HTTP wrappers can review the built-in `http` module for:

- GET
- POST
- PUT
- DELETE
- query parameters
- headers
- JSON/text bodies
- timeout handling

## 13. Schema validation

V3 adds schema-driven validation for structured data.

This is useful when migrating code that previously performed repeated manual checks on nested values.

Supported schema families include text, number, boolean, list, object, nested fields, optional fields, enums, and common range/length constraints.

## 14. Jobs and checkpoints

Long-running V2 workflows can migrate to the V3 `jobs` module where resumability or progress tracking matters.

V3 supports job lifecycle state, progress, checkpoints, save/load behavior, and resume-oriented flows.

## 15. AI and structured output

V3 significantly expands AI workflows.

Important additions include:

- generation through `ai.generate`
- retry behavior
- timeout validation
- structured output
- schema forwarding
- invalid structured-output detection
- one repair attempt
- usage aggregation
- cost/pricing observability

If a V2 project directly parsed AI text into JSON, consider migrating to V3 structured-output support instead of keeping fragile manual parsing.

## 16. Context workflows

V3 adds:

- `context.split`
- `context.build`

Projects working with large text can migrate from ad-hoc chunking to these documented context tools.

## 17. Environment and secrets

Review V2 projects that contain API keys or credentials in source.

V3 provides:

- optional `.env` loading
- process environment overrides
- secret-safe values
- output/interpolation redaction
- nested redaction
- error redaction
- release filtering that prevents `.env` from being embedded

Do not commit or distribute `.env` files.

## 18. Diagnostics

V3 diagnostics are more structured and preserve more source context.

When migrating, avoid code that depends on exact old human-readable error strings unless you have a specific compatibility reason.

Prefer handling normal Janna behavior rather than parsing diagnostic text.

## 19. Editor migration

Janna Editor has moved from the earlier Alpha stage to Beta.

The current extension package version is:

    0.2.0

It supports VS Code and Cursor and provides Run, Check, Test, and Build commands at active-file and project level.

If you have an older Janna extension installed, install the V3 release VSIX before validating editor workflows.

## 20. Build and packaging

V3 production builds support project entry points and user/nested modules.

The Windows release also includes:

- portable SDK
- release ZIP
- installer
- global PATH setup
- `ja.cmd`

For migration testing, validate both source execution and the built executable.

## 21. Compatibility expectations

V3 includes regression coverage for the CLI surface, built-in module contracts, and runtime capability contracts.

Even so, migrate by testing the behavior your application actually depends on.

Recommended sequence:

1. run `janna check`
2. run project tests with `janna test`
3. run the application from source
4. build it with `janna build`
5. run the built executable
6. verify arguments, filesystem paths, environment behavior, and exit codes if used

## 22. Documentation changes

The V3 documentation is split by purpose:

- `README.md` / `README_TR.md` — overview
- `QUICKSTART.md` / `QUICKSTART_TR.md` — fast start
- `HANDBOOK.md` / `HANDBOOK_TR.md` — handbook navigation
- `docs/handbook/en/` and `docs/handbook/tr/` — detailed chapters
- `CLI_REFERENCE.md` / `CLI_REFERENCE_TR.md` — command reference
- `STDLIB_REFERENCE.md` / `STDLIB_REFERENCE_TR.md` — built-in module reference

When migrating a V2 project, use the Handbook as the authoritative user-facing guide for V3 behavior.

## 23. What not to migrate yet

Do not redesign a V2 project around features that are outside V3 scope.

The following remain future work rather than V3 migration requirements:

- package registry
- new compiler architecture
- self-hosting
- native compiler
- cross-platform runtime expansion
- large GUI/database/server framework additions
- other major new subsystems planned for later versions

Keep V2-to-V3 migration focused on the features that actually exist in V3.


