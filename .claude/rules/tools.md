# Tools

## Project tasks
- Use the project's own toolbox for build, flash, test and logs. Find its tasks in `.vscode/tasks.json`, otherwise in the build files (e.g. Makefile, CMakePresets.json, package.json scripts). Default tasks in `.claude/CLAUDE.md` take precedence.
- Run a task through its `command` and `args`, using the override for the current OS; respect `${workspaceFolder}`, `options.cwd`, `options.env` and `dependsOn`. If the profile sets an Environment, run it in the same call: `<Environment> && <command>`.
- Never invent build commands. A task of an extension type (e.g. `espidf`, `cppbuild`) → use the equivalent CLI command or ask.
- Test build configurations beside the main build are allowed. Unclear how to create a test build → ask.
- Flash or erase only when the request asks for a hardware run, and only on approved test hardware (`.claude/CLAUDE.md` › Test hardware, otherwise ask).
- A project devcontainer (Docker) may always be used.
- Permanent permissions per project go into `.claude/settings.local.json`.

## Local files
- Logs and own notes are stored only in `.claude-local/` in the project root; create it on first use with a `.gitignore` containing `*`.

## Formats
- Markdown for text, `.drawio.svg` for diagrams, one HTML overview page (`documentation/index.html`).
