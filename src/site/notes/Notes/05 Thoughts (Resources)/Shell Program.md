---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/shell-program/","dgPassFrontmatter":true,"updated":"2026-10-13T18:10:59.974+05:30"}
---

# Shell Program: `shell new`

## 1. Overview

This paper describes a Windows command-line program named `shell` that can create and activate isolated shell environments.

The main command is:

```bat
shell new
```

When executed, it creates a new shell environment and stores its activation script at:

```text
.shell/
└── activate.bat
```

The generated `activate.bat` contains the environment configuration for that shell, including its own `PATH` and other environment variables.

The design is similar in concept to Python virtual environments, but it is implemented using Windows Batch (`.bat`) files and the Windows environment-variable mechanism.

---

# 2. Goals

The system should provide:

- A `shell` command.
- A `shell new` subcommand.
- Automatic creation of `.shell/`.
- A generated `.shell/activate.bat`.
- A separate `PATH` for the shell environment.
- Additional shell-specific environment variables.
- Activation and deactivation.
- No modification of the user's permanent Windows environment.
- Support for installing or adding programs into the shell's private directory.
- A predictable directory structure.
- Compatibility with normal Windows Command Prompt.

Example:

```bat
C:\project> shell new

Creating shell environment...

Created:
  .shell\
  .shell\bin\
  .shell\etc\
  .shell\activate.bat
  .shell\deactivate.bat

Shell created successfully.
```

The user can then run:

```bat
C:\project> call .shell\activate.bat
```

or, if `shell` handles activation:

```bat
C:\project> shell activate
```

---

# 3. Important Windows Environment Concept

Windows environment variables are inherited by child processes.

For example:

```text
cmd.exe
   |
   +-- program.exe
   |
   +-- another.exe
```

A child process receives a copy of the parent's environment.

A `.bat` file can modify the environment of the current `cmd.exe` process when it is executed using:

```bat
call activate.bat
```

Therefore:

```bat
call .shell\activate.bat
```

can modify variables such as:

```bat
PATH
SHELL_HOME
SHELL_ROOT
TEMP
```

for the current command prompt.

However, there is an important limitation:

> A normal Windows Batch script cannot create a completely independent environment inside the same `cmd.exe` process.

Instead, the activation script changes the current command prompt's environment.

A genuinely isolated environment requires a separate process.

---

# 4. Proposed Architecture

The project can use the following architecture:

```text
shell
│
├── shell new
│     │
│     ├── Create .shell\
│     ├── Create .shell\bin\
│     ├── Create .shell\etc\
│     ├── Create .shell\tmp\
│     ├── Generate activate.bat
│     └── Generate deactivate.bat
│
├── shell activate
│     │
│     └── call .shell\activate.bat
│
├── shell deactivate
│     │
│     └── call .shell\deactivate.bat
│
└── shell status
      │
      └── Display current shell information
```

---

# 5. Directory Structure

A shell environment could look like this:

```text
project/
│
├── .shell/
│   │
│   ├── activate.bat
│   ├── deactivate.bat
│   │
│   ├── bin/
│   │   ├── tool.exe
│   │   ├── python.exe
│   │   └── ...
│   │
│   ├── etc/
│   │   └── environment.bat
│   │
│   ├── tmp/
│   │
│   └── home/
│
├── src/
├── README.md
└── ...
```

The `.shell` directory is intended to belong to the project.

It can therefore be excluded from Git:

```gitignore
.shell/
```

or deliberately committed if reproducibility is required.

---

# 6. The `PATH` Problem

The most important feature is the private `PATH`.

Suppose the normal Windows environment contains:

```text
C:\Windows\System32
C:\Windows
C:\Program Files\Git\cmd
C:\Users\User\AppData\Local\Programs\Python
```

The shell could create its own path:

```text
C:\project\.shell\bin
C:\Windows\System32
C:\Windows
```

The shell's `PATH` therefore becomes:

```text
PATH=C:\project\.shell\bin;C:\Windows\System32;C:\Windows
```

The first directory has priority.

Consequently:

```bat
tool.exe
```

will first search:

```text
C:\project\.shell\bin\tool.exe
```

before searching later directories.

---

# 7. Two PATH Models

There are two possible designs.

## Model A — Private PATH

The shell completely replaces the normal `PATH`.

Example:

```bat
set "PATH=%SHELL_ROOT%\bin;C:\Windows\System32;C:\Windows"
```

This provides strong isolation.

However, many normal Windows commands may stop working if their directories are omitted.

---

## Model B — Overlay PATH

The shell places its own directory before the original PATH:

```bat
set "PATH=%SHELL_ROOT%\bin;%PATH%"
```

Example:

```text
Before:

PATH=C:\Windows\System32;C:\Windows;C:\Program Files\Git\cmd


After:

PATH=C:\project\.shell\bin;C:\Windows\System32;C:\Windows;C:\Program Files\Git\cmd
```

This is safer and more convenient.

For most practical applications, the overlay model is preferable.

---

# 8. Shell Environment Variables

The shell can define its own variables.

For example:

```bat
set "SHELL_ROOT=C:\project\.shell"
set "SHELL_HOME=C:\project\.shell\home"
set "SHELL_BIN=C:\project\.shell\bin"
set "SHELL_ENV=project"
```

The resulting environment could contain:

```text
SHELL_ROOT
SHELL_HOME
SHELL_BIN
SHELL_ENV
PATH
```

Example:

```bat
echo %SHELL_ROOT%
```

Output:

```text
C:\project\.shell
```

---

# 9. Preserving the Original Environment

Activation should save the original values before changing them.

For example:

```bat
set "_SHELL_OLD_PATH=%PATH%"
```

Then:

```bat
set "PATH=%SHELL_BIN%;%PATH%"
```

When deactivating:

```bat
set "PATH=%_SHELL_OLD_PATH%"
set "_SHELL_OLD_PATH="
```

This restores the previous environment.

The same mechanism can be used for other variables.

---

# 10. Basic `activate.bat`

A simple implementation could be:

```bat
@echo off

if defined SHELL_ACTIVE (
    echo Shell is already active.
    exit /b 0
)

set "_SHELL_OLD_PATH=%PATH%"
set "_SHELL_OLD_SHELL_ROOT=%SHELL_ROOT%"
set "_SHELL_OLD_SHELL_HOME=%SHELL_HOME%"
set "_SHELL_OLD_SHELL_BIN=%SHELL_BIN%"

set "SHELL_ROOT=%~dp0"
set "SHELL_ROOT=%SHELL_ROOT:~0,-1%"

set "SHELL_BIN=%SHELL_ROOT%\bin"
set "SHELL_HOME=%SHELL_ROOT%\home"
set "SHELL_ENV=%SHELL_ROOT%"

set "PATH=%SHELL_BIN%;%PATH%"

set "SHELL_ACTIVE=1"

echo Shell activated.
echo.
echo SHELL_ROOT=%SHELL_ROOT%
echo SHELL_BIN=%SHELL_BIN%
echo.
```

---

# 11. Why `%~dp0` Is Important

The expression:

```bat
%~dp0
```

means the drive and path of the currently executing batch file.

If:

```text
C:\project\.shell\activate.bat
```

is executing, then:

```bat
%~dp0
```

resolves approximately to:

```text
C:\project\.shell\
```

This means the activation script does not need to know where the project is located.

The shell can therefore be moved to another directory.

---

# 12. `deactivate.bat`

A corresponding deactivation script could be:

```bat
@echo off

if not defined SHELL_ACTIVE (
    echo No shell is currently active.
    exit /b 0
)

set "PATH=%_SHELL_OLD_PATH%"

if defined _SHELL_OLD_SHELL_ROOT (
    set "SHELL_ROOT=%_SHELL_OLD_SHELL_ROOT%"
) else (
    set "SHELL_ROOT="
)

if defined _SHELL_OLD_SHELL_HOME (
    set "SHELL_HOME=%_SHELL_OLD_SHELL_HOME%"
) else (
    set "SHELL_HOME="
)

if defined _SHELL_OLD_SHELL_BIN (
    set "SHELL_BIN=%_SHELL_OLD_SHELL_BIN%"
) else (
    set "SHELL_BIN="
)

set "_SHELL_OLD_PATH="
set "_SHELL_OLD_SHELL_ROOT="
set "_SHELL_OLD_SHELL_HOME="
set "_SHELL_OLD_SHELL_BIN="
set "SHELL_ENV="
set "SHELL_ACTIVE="

echo Shell deactivated.
```

---

# 13. The `shell` Command

The user should be able to type:

```bat
shell new
```

The command itself can be implemented as:

```bat
shell.bat
```

Windows can locate it if its directory is included in the user's normal `PATH`.

For example:

```text
C:\Users\User\bin\shell.bat
```

with:

```text
C:\Users\User\bin
```

in the system PATH.

---

# 14. Basic `shell.bat`

A simple implementation:

```bat
@echo off
setlocal

if "%~1"=="new" goto new
if "%~1"=="status" goto status
if "%~1"=="help" goto help

echo Unknown command: %~1
echo.
goto help

:new

if exist ".shell\activate.bat" (
    echo A shell environment already exists.
    exit /b 1
)

echo Creating shell environment...

mkdir ".shell" >nul 2>&1
mkdir ".shell\bin" >nul 2>&1
mkdir ".shell\etc" >nul 2>&1
mkdir ".shell\tmp" >nul 2>&1
mkdir ".shell\home" >nul 2>&1

(
    echo @echo off
    echo.
    echo if defined SHELL_ACTIVE ^(
    echo     echo Shell is already active.
    echo     exit /b 0
    echo ^)
    echo.
    echo set "_SHELL_OLD_PATH=%%PATH%%"
    echo set "_SHELL_OLD_SHELL_ROOT=%%SHELL_ROOT%%"
    echo set "_SHELL_OLD_SHELL_HOME=%%SHELL_HOME%%"
    echo set "_SHELL_OLD_SHELL_BIN=%%SHELL_BIN%%"
    echo.
    echo set "SHELL_ROOT=%%~dp0"
    echo set "SHELL_ROOT=%%SHELL_ROOT:~0,-1%%"
    echo set "SHELL_BIN=%%SHELL_ROOT%%\bin"
    echo set "SHELL_HOME=%%SHELL_ROOT%%\home"
    echo set "SHELL_ENV=%%SHELL_ROOT%%"
    echo.
    echo set "PATH=%%SHELL_BIN%%;%%PATH%%"
    echo set "SHELL_ACTIVE=1"
    echo.
    echo echo Shell activated.
) > ".shell\activate.bat"

(
    echo @echo off
    echo.
    echo if not defined SHELL_ACTIVE ^(
    echo     echo No shell is currently active.
    echo     exit /b 0
    echo ^)
    echo.
    echo set "PATH=%%_SHELL_OLD_PATH%%"
    echo set "SHELL_ROOT=%%_SHELL_OLD_SHELL_ROOT%%"
    echo set "SHELL_HOME=%%_SHELL_OLD_SHELL_HOME%%"
    echo set "SHELL_BIN=%%_SHELL_OLD_SHELL_BIN%%"
    echo set "_SHELL_OLD_PATH="
    echo set "_SHELL_OLD_SHELL_ROOT="
    echo set "_SHELL_OLD_SHELL_HOME="
    echo set "_SHELL_OLD_SHELL_BIN="
    echo set "SHELL_ENV="
    echo set "SHELL_ACTIVE="
    echo echo Shell deactivated.
) > ".shell\deactivate.bat"

echo.
echo Shell created successfully.
echo.
echo Activation:
echo     call .shell\activate.bat

exit /b 0

:status

if defined SHELL_ACTIVE (
    echo Shell: ACTIVE
    echo Root:  %SHELL_ROOT%
    echo Bin:   %SHELL_BIN%
) else (
    echo Shell: INACTIVE
)

exit /b 0

:help

echo.
echo Shell Environment Manager
echo.
echo Commands:
echo.
echo   shell new       Create a new shell
echo   shell status    Show shell status
echo   shell help      Show this help
echo.
exit /b 0
```

---

# 15. Important `setlocal` Limitation

There is a critical detail in the implementation above.

The command:

```bat
setlocal
```

creates a local environment for the current batch script.

When the script reaches:

```bat
endlocal
```

or exits, those changes disappear.

Therefore, the `shell.bat` program should not try to activate the shell itself using ordinary `set` commands inside a `setlocal` scope.

Instead, it should generate the activation script and tell the user to run:

```bat
call .shell\activate.bat
```

This is one reason why activation is separated from shell creation.

---

# 16. Why `CALL` Matters

Consider:

```bat
activate.bat
```

versus:

```bat
call activate.bat
```

For batch-file chaining, `call` is the safer explicit mechanism.

The intended workflow is:

```bat
shell new
call .shell\activate.bat
```

After activation:

```bat
echo %SHELL_ACTIVE%
```

returns:

```text
1
```

and:

```bat
echo %SHELL_ROOT%
```

might return:

```text
C:\project\.shell
```

---

# 17. A Better User Interface

The command system can eventually support:

```text
shell new
shell activate
shell deactivate
shell status
shell path
shell env
shell destroy
shell reset
shell exec
shell run
shell help
```

Example:

```bat
shell new
```

creates the environment.

Then:

```bat
shell activate
```

could generate instructions such as:

```text
To activate the shell in this Command Prompt:

    call .shell\activate.bat
```

---

# 18. Why `shell activate` Cannot Normally Activate Its Parent CMD

This is a fundamental Windows process-model limitation.

Suppose the user executes:

```text
cmd.exe
   |
   +-- shell.bat
```

The batch script runs inside the command interpreter, but an independently launched executable cannot modify the environment of its parent process.

The environment relationship is:

```text
Parent Environment
        |
        v
Child Environment
```

Changes normally flow from parent to child during process creation.

They do not flow backward:

```text
Child
  X
  |
  v
Parent
```

Therefore, a native `shell.exe` cannot simply modify the environment of the already-running `cmd.exe`.

The practical solution is:

```bat
call .shell\activate.bat
```

---

# 19. An Alternative: `shell activate` as a Wrapper

A different architecture can create a new command prompt.

For example:

```bat
cmd /k ".shell\activate.bat"
```

This starts a new command interpreter whose environment is configured by the activation script.

The process tree becomes:

```text
Original CMD
    |
    +-- shell
          |
          +-- New CMD
                |
                +-- Programs
```

The new CMD can have its own environment.

This is closer to the concept of an independent shell.

---

# 20. Completely Separate Shell

A command such as:

```bat
shell open
```

could execute:

```bat
cmd.exe /K "%CD%\.shell\activate.bat"
```

The new shell starts with the environment configured by:

```text
.shell\activate.bat
```

Example:

```text
C:\project> shell open

Launching isolated shell...

C:\project>
```

Inside that shell:

```bat
echo %SHELL_ROOT%
```

returns:

```text
C:\project\.shell
```

---

# 21. Private Executables

The `.shell\bin` directory can contain shell-specific executables.

Example:

```text
.shell/
└── bin/
    ├── python.exe
    ├── node.exe
    ├── git.exe
    └── custom-tool.exe
```

Activation:

```bat
set "PATH=%SHELL_ROOT%\bin;%PATH%"
```

Now:

```bat
python
```

will preferentially resolve to:

```text
.shell\bin\python.exe
```

instead of the global installation.

---

# 22. Shell-Specific Configuration

The environment can have:

```text
.shell/
├── activate.bat
├── deactivate.bat
├── bin/
├── etc/
│   └── environment.bat
├── home/
└── tmp/
```

`environment.bat` could contain:

```bat
set "APP_ENV=development"
set "DEBUG=1"
set "PROJECT_NAME=my-project"
set "SHELL_ENV=project"
```

The activation script can load it:

```bat
call "%SHELL_ROOT%\etc\environment.bat"
```

---

# 23. Environment Manifest

A more advanced implementation should maintain a manifest:

```text
.shell/
└── shell.json
```

Example:

```json
{
  "name": "project",
  "version": "1",
  "platform": "windows",
  "shell": "cmd",
  "root": ".shell",
  "bin": ".shell/bin",
  "home": ".shell/home",
  "tmp": ".shell/tmp",
  "path_mode": "overlay",
  "variables": {
    "APP_ENV": "development",
    "PROJECT_NAME": "project"
  }
}
```

The `shell` program can use this file to reconstruct the environment.

---

# 24. Why a Manifest Is Useful

Without a manifest, the environment is mostly encoded directly into:

```text
activate.bat
```

With a manifest:

```text
shell.json
     |
     v
shell program
     |
     +----> activate.bat
     |
     +----> deactivate.bat
```

The manifest becomes the source of truth.

The batch files become generated artifacts.

This makes the system easier to extend.

---

# 25. Environment Isolation Levels

The project should distinguish several meanings of "isolated".

## Level 1 — Variable Isolation

Different environment variables:

```text
SHELL_ROOT
SHELL_HOME
SHELL_ENV
```

## Level 2 — PATH Isolation

The shell gets its own executable search path:

```text
.shell\bin
```

## Level 3 — Filesystem Isolation

Tools and configuration live under:

```text
.shell\
```

## Level 4 — Process Isolation

A separate:

```text
cmd.exe
```

is launched.

## Level 5 — OS-Level Isolation

A VM or container is used.

The proposed `.shell` system primarily provides Levels 1–4.

It does **not** provide security isolation comparable to a VM or container.

---

# 26. Security Consideration

A private `PATH` does not make a shell a security sandbox.

For example, if the shell contains:

```text
.shell\bin\program.exe
```

that program still runs with the permissions of the user.

Likewise:

```bat
set "PATH=..."
```

does not prevent access to:

```text
C:\Users\User
```

or other filesystem locations.

Therefore:

> Environment isolation is not security isolation.

This distinction is important.

---

# 27. Nested Shells

The system should support nested environments.

Example:

```text
Normal CMD
   |
   +-- Shell A
         |
         +-- Shell B
```

Shell A:

```text
SHELL_ROOT=C:\project\.shell
```

Shell B:

```text
SHELL_ROOT=C:\project\subproject\.shell
```

Each activation should preserve the previous environment.

A stack-based implementation is better than a single backup variable.

---

# 28. Environment Stack

Instead of:

```text
_SHELL_OLD_PATH
```

the system can maintain:

```text
_SHELL_LEVEL
```

Example:

```text
_SHELL_LEVEL=0
```

After activation:

```text
_SHELL_LEVEL=1
```

After another activation:

```text
_SHELL_LEVEL=2
```

This makes nested shells possible.

---

# 29. Example Workflow

Create a project:

```bat
mkdir MyProject
cd MyProject
```

Create the environment:

```bat
shell new
```

Activate it:

```bat
call .shell\activate.bat
```

Check the environment:

```bat
shell status
```

Example:

```text
Shell: ACTIVE
Root:  C:\MyProject\.shell
Bin:   C:\MyProject\.shell\bin
```

Check PATH:

```bat
echo %PATH%
```

The beginning should contain:

```text
C:\MyProject\.shell\bin;
```

---

# 30. Example of Private PATH Resolution

Suppose the system contains:

```text
C:\Windows\System32\tool.exe
```

and the shell contains:

```text
C:\MyProject\.shell\bin\tool.exe
```

After activation:

```text
PATH=C:\MyProject\.shell\bin;...
```

Running:

```bat
tool.exe
```

will resolve to:

```text
C:\MyProject\.shell\bin\tool.exe
```

because Windows searches PATH entries in order.

---

# 31. Deactivation

When finished:

```bat
call .shell\deactivate.bat
```

The shell-specific variables are removed/restored.

The PATH returns to its previous value.

Example:

```text
Before:

PATH=C:\Windows\System32;...


Activated:

PATH=C:\MyProject\.shell\bin;C:\Windows\System32;...


Deactivated:

PATH=C:\Windows\System32;...
```

---

# 32. Destruction

A future command could be:

```bat
shell destroy
```

which removes:

```text
.shell\
```

The implementation should require confirmation because this is destructive.

Example:

```text
This will delete:

    .shell\

Continue? [y/N]
```

---

# 33. Reproducibility

A shell environment can be made reproducible using:

```text
shell.json
```

For example:

```json
{
  "name": "web-project",
  "variables": {
    "NODE_ENV": "development"
  },
  "path": [
    ".shell/bin"
  ]
}
```

Another computer can run:

```bat
shell new
```

and the shell manager can reconstruct the directory and activation files.

For complete reproducibility, dependency versions should also be recorded.

---

# 34. Recommended Architecture

A mature implementation should use:

```text
shell.exe
│
├── command parser
│
├── environment manager
│
├── manifest manager
│
├── activation generator
│
├── process launcher
│
└── filesystem manager
```

The generated environment:

```text
project/
└── .shell/
    ├── shell.json
    ├── activate.bat
    ├── deactivate.bat
    ├── bin/
    ├── etc/
    ├── home/
    └── tmp/
```

---

# 35. Recommended Command Set

```text
shell new
```

Creates a shell.

```text
shell open
```

Opens a new CMD using the shell environment.

```text
shell activate
```

Provides or performs activation where possible.

```text
shell deactivate
```

Deactivates the current shell.

```text
shell status
```

Displays shell information.

```text
shell env
```

Displays shell variables.

```text
shell path
```

Displays the shell PATH.

```text
shell destroy
```

Deletes the shell environment.

```text
shell reset
```

Recreates generated files.

```text
shell help
```

Displays documentation.

---

# 36. Core Design Principle

The central idea is:

```text
shell new
      |
      v
Create .shell/
      |
      +--> bin/
      |
      +--> home/
      |
      +--> tmp/
      |
      +--> etc/
      |
      +--> shell.json
      |
      +--> activate.bat
      |
      +--> 