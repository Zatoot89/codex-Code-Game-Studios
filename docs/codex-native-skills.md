# Using the 78 Game Studios skills in Codex and GitHub Copilot

All canonical workflows remain in .claude/skills/<name>/SKILL.md. No source skills have been modified.

## Codex CLI
Codex discovers project skills in .agents/skills. Each native SKILL.md adapter lists a workflow and tells Codex to read its full original instructions from .claude/skills. Open Codex at the repository root so AGENTS.md is in scope. Request the workflow with a task, for example: $prototype a fishing game, $start, or $code-review src/.

## GitHub Copilot coding agent
GitHub Copilot cloud agent also supports project skills from .claude/skills. Give it a task such as: Use the prototype skill from .claude/skills to plan a browser game. Skill discovery does not override GitHub push restrictions or agent approval rules.

## Maintaining the catalog
Run these commands when canonical skills are added, removed, or renamed:
    python3 tools/codex/sync-skills.py
    python3 tools/codex/sync-skills.py --check

The generator requires only Python 3. It preserves custom non-generated native skills and removes only obsolete auto-generated adapters. Keep the full workflow in .claude/skills to avoid drift.

## Compatibility
Claude-specific hooks, inline shell expansion, @ imports, subagents, model pins, and permission modes do not automatically transfer to Codex. Execute suitable steps using the current tools and report unavailable checks as NOT ASSESSED, not PASS. Do not run GitHub Actions merely to validate these skills.

## Parallel unpublished work
A separate unpublished commit 6352e84 on feat/codex-cli-support may add its own AGENTS.md and legacy .codex/prompts conversion. Preserve that commit and reconcile any file conflicts rather than rewriting or force-pushing it.
