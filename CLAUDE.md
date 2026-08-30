# CLAUDE.md — Universal Behavior Kit

Project-agnostic behavioral rules for Claude Code (or any coding-agent setup).
Drop this file at the repo root (or append to a project `CLAUDE.md`) and merge
with project-specific instructions. Code principles live in `rules/code-style.md`.

The **Localization** section at the bottom holds the few personal/language
conventions — adjust those per team; everything above is generic.

---

## Git

- Never add AI / tool-vendor attribution to commits. No `Co-Authored-By` for an
  AI, and no mention of any AI product or vendor anywhere in code comments or
  commit messages (subject and body). Write as if authored by a human engineer.
- Commit message bodies: **one thought per line**. Don't hard-wrap a single
  thought across lines at a fixed column width — each line is one complete
  thought; a long thought stays on its own (possibly long) line.
- When a change describes a chain of several events/steps, write them as a
  numbered list (`1. … 2. … 3. …`), one step per line.
- BEFORE/AFTER in a commit body is a **tester instruction**: concrete steps
  (where to click) and the observable behavior — not architecture notes. If a
  BEFORE/AFTER is a chain of steps, make it a numbered list.
- Before committing, run `git diff --cached` and confirm the commit contains
  only what you intend — never let pre-staged unrelated changes ride along.
- Atomic commits: 1 feature = 1 commit. Never delete tests without approval.

## Network

- Before external commands (npm, docker, go, curl, etc.) neutralize a stale
  proxy: `unset HTTPS_PROXY` (adjust to your own network/proxy setup).

## Code Editing

- Never introduce or remove trailing whitespace on lines you didn't
  intentionally change. Before committing, verify with `git diff` that only
  meaningful changes are present — no whitespace-only diffs.

## Function Parameters

- No more than 3–4 parameters (hard max 7). If more are needed, group them into
  a config/options struct.

## Markdown Tables

- Align table columns to the maximum content width in each column.

## Answer Formatting

When answering questions (especially review/analysis answers), break the
reasoning into one thought per line:

- Each line is a separate, complete thought.
- Start each thought line with `- `.
- One thought per line — never run several thoughts together in one sentence,
  and never hard-wrap a single thought across lines.
- A long thought stays on its own (possibly long) line.

When asked for a "short" answer, give the answer in the requested number of
sentences first; only break into the `- ` per-thought list when explicitly asked
to split into thoughts (or when listing several reasons).

When the answer includes a suggested improvement, put it after a `Предлагаю:` /
`Suggested:` header and break the proposal into several `- ` lines (one step per
line) instead of one long sentence.

## Working On A Task

(dovetails with KISS/YAGNI in `rules/code-style.md` and the assumption rule below)

- **Loop-until-verified.** Turn a task into a verifiable goal and iterate to
  green on your own instead of asking at each step: "fix the bug" → first a test
  that reproduces it, then make it pass; "add validation" → tests for invalid
  input, then the implementation; "refactor X" → tests green before and after.
  Convert a weak criterion ("make it work") into a strong one yourself.
- **Don't pick an interpretation silently.** If a request has several readings,
  list them and ask — don't implement one by default.
- **Overcomplication self-check.** Before handing off, ask: "would a senior
  engineer call this overcomplicated?" If you wrote 200 lines where 50 suffice,
  rewrite it.
- **Mark assumptions.** Label them (`Assumption:` / `Предположение:`) and seek
  evidence rather than proceeding on a guess.
- **Verify prerequisites are actually deployed/present.** Before building a fix
  on top of a controller/operator/mechanism, confirm it is really running — an
  annotation or a plan is not proof.

## Surgical Changes

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- Remove imports/variables/functions that YOUR changes made unused; don't remove
  pre-existing dead code unless asked — mention it instead.
- The test: every changed line should trace directly to the request.

---

## Localization (adjust per team / language)

These reflect a Russian-language workflow; change or drop them to fit yours.

- **Language split:** documentation and discussion in the team's language;
  commit messages in English.
- **UI terms (Russian):** write «правый клик», never «ПКМ».
- A UI navigation chain in a commit body (button → submenu → item), when long or
  per-interface, is broken across lines with one `→` transition per line — not
  collapsed into a single line.
