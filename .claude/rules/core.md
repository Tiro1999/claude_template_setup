# Core Rules

Binding for every project, the main session and every agent.
Project facts live in `.claude/CLAUDE.md`; values in `<angle brackets>` are unset.
A needed fact is missing → ask (agents report `needs-decision`), never guess.

## 1. Architecture (one of the most important rules)
- One module per functionality; the folder tree mirrors the functional tree.
- Modules are configurable via build config and can be included or excluded by it.
- Extend the structure or split modules further – never bypass it.

## 2. Code
- Code explains itself and stays maintainable without AI.
- KISS – keep it simple.
- Reuse helpers, never duplicate them.
- Comments only when short; longer explanations link into `documentation/`.

## 3. Naming
- `documentation/glossar.md` is binding for code, comments and documentation – including the mapping SDK name ↔ project name.
- New names and naming conventions go into the glossary.
- Unclear or conflicting name → `NAMING-CHECK` marker.

## 4. SDK first
- Before implementing, check whether the SDK, framework or a library already solves it – then use that.

## 5. Security
- Validate every external input.
- No secrets and no personal data in the repository – including its git history.
- Always report security concerns.

## 6. Logging
- Maturity levels: `dev` → `experimental` → `release`.
- Debug logs per module may stay in the code if the build config can exclude them; they are active only in `dev` and `experimental`.
- Info logs describe the flow for the user.

## 7. Documentation
- Single source of truth: `documentation/` in the project root. Create missing parts on first use.
- Prefer diagrams (`.drawio.svg`) over text; keep them simple and free of long text. Diagrams live in `documentation/software/`.
- A `.drawio.svg` embeds its draw.io model, so it stays editable.
- Every diagram carries the software version (`.claude/CLAUDE.md` › Version source) and the date (`dd.mm.yyyy`) in a small text block at the bottom right.

```
documentation/
├── glossar.md
├── index.html      overview page
├── software/       mirrors the modules, e.g. interfaces/…, user-com/fault-handling/…
└── hardware/       embedded only
```

## 8. Markers
Written in the language's comment syntax, e.g. `// NAMING-CHECK` or `# NAMING-CHECK`.

| Marker | Meaning | Set by |
|---|---|---|
| `NAMING-CHECK` | name unclear or conflicting with the glossary | implementer |
| `DEADCODE-CHECK` | probably unused, not yet removable | dead-code-auditor |

Read-only agents report the same as a finding.

## 9. Agents
The main session orchestrates; agents never delegate to other agents.

```
task ─▶ sdk-researcher ─▶ implementer ─▶ test-runner ─▶ code-reviewer ─┬─▶ documentation-designer
       (SDK or library      ▲          (build/flash/test)              │   (structure, interfaces
        involved)           └──────── fail / blocker / major ──────────┘    or naming changed)

dead-code-auditor: after refactorings or on request
```

Models: writing and reviewing code → `inherit` · bounded tasks → `sonnet` · test runs → `haiku`.

### Report
Every agent ends with this report:

```
Status:   done | failed | blocked | needs-decision
Changed:  <files> | none
Findings: <blocker|major|minor> <file:line> <issue> → <fix>
Markers:  <MARKER> <file:line>
Open:     <questions for the user>
```
