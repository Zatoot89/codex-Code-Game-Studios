# Game Studios - instructions for Codex and Copilot

CLAUDE.md and .claude/ remain the canonical project instructions. This file adapts their workflows for Codex and other coding agents.

## Read first
- project.yaml for the selected engine and project settings.
- CLAUDE.md and applicable .claude/docs/coordination-rules.md, .claude/docs/coding-standards.md and .claude/docs/directory-structure.md.
- Requested .agents/skills/<name>/SKILL.md, then its full canonical .claude/skills/<name>/SKILL.md.
- production/session-state/active.md if it exists after a session interruption.

## Collaboration protocol and safeguards
- Follow the canonical Question -> Options -> Decision -> Draft -> Approval process.
- Seek approval before writing or changing files unless the user already authorized the specific work.
- Do not commit, push, open PRs, or merge without the user's authorization; do not make direct unreviewed changes to main.
- Protect secrets and private data. Never make changes to upstream vendor/engine repositories without authorization.
- Use existing .claude/scripts/ helpers for project settings as appropriate.
- Run available local checks and report PASS, FAIL or NOT ASSESSED with evidence. Do not claim GitHub Actions ran unless they did.

## Runtime compatibility
- Claude-only hooks, special inline commands, @path imports, model/tool pins and agent spawning do not automatically run in Codex.
- Apply the intended steps with the tools actually available, or report that a step was not assessed.
- .claude/skills remains the complete source of truth. After adding or removing skills, run python3 tools/codex/sync-skills.py and check with --check.
