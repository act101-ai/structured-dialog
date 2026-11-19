# structured-dialog

A Claude Code output style that makes each agent message cheap to read and cheap to answer.

The style is one file: `output-styles/structured-dialog.md`. The repository has the layout of a Claude Code plugin, so the style can move into another plugin without changes.

## Rules in the style

1. Conclusion first.
2. Playback: what changed in the shared model, and what follows from it.
3. Author's calls are visible, so the operator can veto one.
4. All questions are listed once as short bullets. Then one question at a time is asked in full, with a hypothesis, a recommendation, and the consequence of each answer.
5. Causal order: sequence comes from dependencies, not from dates.

## Install

```sh
claude plugin marketplace add act101-ai/act101
claude plugin install structured-dialog@act101-marketplace
```

Select it with `/output-style structured-dialog`, or set `"outputStyle": "structured-dialog"` in `~/.claude/settings.json`.

## Use it during development

The user-level style file is a symbolic link to this repository:

```sh
ln -s "$PWD/output-styles/structured-dialog.md" ~/.claude/output-styles/structured-dialog.md
```

Select it with `/output-style structured-dialog`, or set `"outputStyle": "structured-dialog"` in `~/.claude/settings.json`.

Claude Code reads style files when it starts. After you edit the style, start a new session.

## Check

```sh
claude plugin validate .
```
