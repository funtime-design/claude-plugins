# funtimedesign plugin marketplace

Claude Code plugins shared across the funtimedesign org.

## Install

```
/plugin marketplace add https://dev.azure.com/funtimedesign/DevOps/_git/funtimedesign-mp
/plugin install crossverify@funtimedesign
/plugin install gaps@funtimedesign
```

The marketplace clones over your existing git credentials (Git Credential Manager OAuth for Azure DevOps). Nothing prompts.

## Plugins

| Plugin | What it is | After install |
|---|---|---|
| `crossverify` | Stop-hook verifier. Codex (a different vendor, read-only) checks the agent's claims after every turn. Each verdict carries a gap analysis. A second reviewer via Fireworks runs on demand. Pinned to a commit of the public repo `gunwadev/crossverify`, subfolder `plugin/`. | `/crossverify:setup`, then `crossverify on` in a project. Skill: `/crossverify:crossverify`. Needs Node 18+ and the Codex CLI, logged in. |
| `gaps` | Evidence-based gap analysis skill. Findings are CONFIRMED (file:line), RESEARCH GAP (cited), or OPEN QUESTION (names the settling check); everything else is dropped. | `/gaps:gaps`, or say "find gaps", "what are we missing", "poke holes". |

## Updating

- `crossverify`: bump `sha` in `.claude-plugin/marketplace.json` to a CI-green commit of `gunwadev/crossverify` main. Never point at a floating ref alone.
- `gaps`: edit `plugins/gaps/skills/gaps/SKILL.md` and bump `plugins/gaps/.claude-plugin/plugin.json` version.
- Validate before pushing: `claude plugin validate .`

## Backup

Canonical remote is Azure DevOps (`DevOps/funtimedesign-mp`). Mirror to Forgejo per the org rule. Never to GitHub.
