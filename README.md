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

## Releases

Every merge to `main` is released automatically. The workflow `.github/workflows/release.yml` raises the patch number in `.claude-plugin/plugin.json`, tags it and makes a GitHub release. Do not change the version by hand for a fix.

For a minor or major release, set the new version in `plugin.json` in the same pull request. The workflow tags it as it is.

Why: Claude Code gives installed users a change only when the plugin version changes.

The marketplace entry in `act101-ai/act101` has no `version`: the version in `plugin.json` is the only one.

Rule approved by the operator, 2026-11-21.
