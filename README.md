# pupil

A Claude Code skill that flips the default relationship: instead of doing the task, Claude teaches you to do it.

You stay in teaching mode — reading the codebase together, pointed at exact `file:line` locations, with Socratic prompts about *why* — until you explicitly exit. Useful for learning an unfamiliar codebase, leveling up on a pattern, or onboarding without having someone shoulder-surf.

## Install

Drop `SKILL.md` into your skills directory:

```
~/.claude/skills/pupil/SKILL.md
```

Or, if you're using a project-scoped skills folder, place it under `.claude/skills/pupil/SKILL.md` at the project root.

## Usage

```
/pupil [mode] <task>
```

Examples:

```
/pupil add a confirm-on-delete dialog to the dashboard
/pupil guidance refactor the auth middleware to use a middleware chain
/pupil observer wire up Stripe webhooks
/pupil plan migrate auth from JWT to session cookies
```

If `[mode]` is omitted, pupil defaults to **Strict**. The mode is sticky for the whole conversation.

## Modes

| Mode | What pupil does | What you do |
|---|---|---|
| **Strict** (default) | Reads source, points at `file:line`, asks Socratic questions. Never composes code. | Type every line yourself. Report back what happened. |
| **Guidance** | Composes snippets in chat with line-by-line explanation. Does not edit files. | Paste/type snippets into the right places. Verify. |
| **Observer** | Implements end-to-end, but narrates each edit and waits for `ok` before each one. | Approve, push back, or ask questions per step. |

Toggle mid-conversation with phrases like *"switch to guidance"*, *"go observer"*, *"back to strict"*.

## Plan mode

For larger tasks, prefix with `plan` to get a reviewable plan file before walking through it:

```
/pupil plan guidance wire up Stripe webhooks
```

Pupil enters plan mode, drafts the plan, you approve it, then it walks the plan with you in the chosen mode.

## Exit

Say *"exit pupil"*, *"I'm done"*, *"normal mode"*, or start a new conversation.

## Why

Reading a diff teaches less than producing one. Pupil protects the gap between question and answer — that's where the learning happens.
