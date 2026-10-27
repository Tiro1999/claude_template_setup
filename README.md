# Claude Setup Template

A copy-ready `.claude/` folder: one fixed rule set and six role agents for every project – from embedded firmware to desktop apps.

## Use
1. New project: copy `.claude/` into the project root – without your private `*.local.*` files.
2. Project with an existing `.claude/`: back it up, copy as in Update, then merge the old `CLAUDE.md` into the new profile and move project-specific permissions into `.claude/settings.local.json`.
3. Fill in `.claude/CLAUDE.md` (project profile). Type `embedded` activates `rules/embedded.md`.
4. Optional: project-specific permissions (e.g. build or flash tools) go into `.claude/settings.local.json`.

## Update
1. Delete `.claude/agents/` and `.claude/rules/`, then copy both from the template – removed or renamed template files must not linger.
2. Copy `settings.json` and `.gitignore` over the existing ones.
3. Keep `CLAUDE.md` and `*.local.*` – everything except these comes from the template.

## Structure
```
.claude/
├── CLAUDE.md        project profile – filled in per project
├── settings.json    template – base permissions
├── .gitignore       template – keeps *.local.* private
├── agents/          template – six role agents
└── rules/           template – the rule set
    ├── core.md      always active
    ├── embedded.md  active only when Type is embedded
    └── tools.md     project tasks, local files, formats
```
Template files change only in this repository, never inside a project.
Agents keep logs and notes in `.claude-local/` in the project root; it is created on first use and ignores itself.

## Agents
sdk-researcher · implementer · test-runner · code-reviewer · dead-code-auditor · documentation-designer

Workflow and report format: `.claude/rules/core.md`.
