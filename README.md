# Claude Code Advanced Skills Pack — 7 Skills

This pack contains seven detailed, standalone Claude Code skills.

## Included
1. `rea-reverse-engineering` — Reverse Engineering & Analysis
2. `claude-design` — Product design and design implementation
3. `bug-checker` — Debugging, root-cause analysis, regression verification
4. `android-builder` — Native Android/Kotlin/Java, Gradle, APK/AAB, CI
5. `security-auditor` — Defensive security review and hardening
6. `website-builder` — Production websites, SEO, accessibility, deployment
7. `ui-ux-designer` — User flows, usability, accessibility, design systems

Each folder contains a `SKILL.md` with role, scope, workflow, detailed checklists, quality gates, safety rules, and required output formats.

## Install globally for Claude Code

Extract the ZIP, then copy the seven skill folders into:

`~/.claude/skills/`

Example on Termux (adjust the downloaded ZIP path if needed):

```bash
mkdir -p ~/.claude/skills
unzip ~/storage/downloads/claude-code-advanced-skills.zip -d /tmp/claude-advanced
cp -r /tmp/claude-advanced/claude-code-advanced-skills/* ~/.claude/skills/
```

For one project only, copy the folders into:

`YOUR_PROJECT/.claude/skills/`

## Verify installation

```bash
find ~/.claude/skills -name SKILL.md
```

Start/restart Claude Code if the skills are not immediately listed. Skills provide instructions and workflows; they do not install tools, grant permissions, or guarantee that a build/test can run.

## Important
- Read each skill and tailor it to your repository's actual stack.
- Never put passwords, API secrets, signing keys, or service-account credentials in skill files.
- REA and security instructions are intended for assets the user owns or is authorized to assess.
