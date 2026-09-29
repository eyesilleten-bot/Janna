# 14. SDK, Packaging, and Installation

## 14.1 Windows SDK

The V3 SDK contains `janna.exe`, `ja.cmd`, and a private `builder_runtime`. The build runtime carries the Python components and Janna engine bytecode needed for `janna build` without requiring the user to install a separate development Python toolchain.

`ja.cmd` expands:

```text
ja app.ja arg1 arg2
```

into the equivalent `janna.exe run ...` command.

## 14.2 Release package

The Windows release package copies the SDK, release documentation, Editor Beta VSIX, examples, and install/uninstall scripts. Sensitive `.env` files are excluded and checked before ZIP creation.

## 14.3 Installer

The Inno Setup installer installs under the current user's Local AppData `Programs\Janna` directory, includes `janna.exe`, `ja.cmd`, `builder_runtime`, documentation, examples, and the Editor Beta VSIX, and adds the Janna installation directory to the user PATH. Administrative privileges are not required by the installer configuration.

After installation, a new terminal session can use:

```text
janna version
janna help
```

and the short launcher:

```text
ja app.ja
```

## 14.4 Build output

A built Janna application is a one-file Windows executable in `dist\<app>.exe`. Its bundled user modules and runtime metadata preserve root application identity and command-line arguments.

