# Claude Behavior Kit

Portable, project-agnostic Claude Code setup — the reusable behavioral core
extracted from a personal `~/.claude` config, with everything project- or
infra-specific left out. Drop it into any coding project.

## What's inside

| File                  | Purpose                                                                 |
|-----------------------|-------------------------------------------------------------------------|
| `CLAUDE.md`           | Universal behavioral rules: git, code editing, answer format, task loop |
| `rules/code-style.md` | KISS / DRY / YAGNI / SOLID + naming, functions, comments, structure     |
| `settings.json`       | Portable Claude Code settings: permissions, hooks, statusLine, prefs    |

## Install

**Per project** — copy `CLAUDE.md` + `rules/` to the repo root (or append
`CLAUDE.md` to an existing one):

```bash
cp CLAUDE.md /path/to/project/CLAUDE.md
cp -r rules   /path/to/project/.claude/rules   # then @-include from CLAUDE.md
```

Reference the rules from `CLAUDE.md` with `@rules/code-style.md`.

**Globally** — merge `settings.json` into `~/.claude/settings.json` and put
`CLAUDE.md` at `~/.claude/CLAUDE.md` to apply across every project.

## Design boundary — what is NOT here

Deliberately excluded because it's tied to one person/stack and would not
transfer:

- **Memory** — all infra/domain facts (k3s, WebRTC, iOS, cloud, product repos).
- **Framework rules** — e.g. Vue/iOS-specific style guides.
- **Trust/environment config** — `autoMode.environment`, private repo paths,
  secrets locations.
- **Task-specific allowlists** — `WebFetch(domain:…)` entries, deploy skills,
  project TODO pointers.

## Localization

`CLAUDE.md` ends with a **Localization** section holding the few
language/workflow conventions (Russian UI terms, language split, proxy `unset`).
Adjust or remove those to fit your team — everything above that section is
generic.

## Credit

The "Working On A Task" rules (loop-until-verified, list interpretations, the
overcomplication self-check) are inspired by the
[Karpathy-style coding guidelines](https://github.com/allright/andrej-karpathy-skills).
