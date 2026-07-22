# RayTally Build Briefs

Daily product ideas drawn from public signals — each one source-linked, time-bounded, argued against, and shipped as a build brief your coding agent can read directly. This repository mirrors the machine-readable surface of [raytally.com](https://raytally.com/); it is a data-and-skill mirror, not a second website and not a separate editorial source.

萤录 [RayTally](https://raytally.com/) 每天把公开动向整理成产品灵感：带来源、带时间边界、带最强反方，并写成 coding agent 可直接读取的开发任务书。本仓库是站点机器可读面的镜像——data + skill，不是网站副本，也不是第二套内容源。

## Use with your coding agent

- [Use with Claude Code](https://raytally.com/en/product-ideas-for-developers/#use-with-claude-code)
- [Use with Codex](https://raytally.com/en/product-ideas-for-developers/#use-with-codex)
- [Use with Cursor](https://raytally.com/en/product-ideas-for-developers/#use-with-cursor)

Each brief in this repo is also served at a stable URL (`https://raytally.com/en/ideas/<slug>.md`) with identical content.

## Try it with your agent / 直接让 agent 试

Paste one line into Claude Code, Codex, Cursor, or any agent with network access:

```text
Read raytally.com/en/latest.json and pick one idea to break down.
```

```text
读取 raytally.com/latest.json，挑一个方向给我拆解。
```

Or install the skill: copy [`SKILL.md`](./SKILL.md) into your agent's skills directory (for Claude Code: `.claude/skills/raytally-build-briefs/SKILL.md`), and it will know how to fetch briefs and what the data does — and does not — claim.

## What a brief looks like

One real card from 2026-07-21 — [Post-Release Journey Replay](https://raytally.com/en/ideas/2026-07-21-replay-qa/) ([brief.md](https://raytally.com/en/ideas/2026-07-21-replay-qa.md) · [中文](https://raytally.com/ideas/2026-07-21-replay-qa/)):

> After each website release, replay recent successful user journeys and use a short video to pinpoint the first broken step and the changes that may be related.

Every featured brief carries the same skeleton: the signal that raised it (with `observed_at` timestamps), the product concept, the target user and entry point, **the strongest case against it**, checkable sources — and YAML frontmatter with full provenance, so an agent downstream can verify instead of trust.

## Contents

- `briefs/YYYY/MM/DD/<slug>.md`: Chinese briefs.
- `briefs/YYYY/MM/DD/en/<slug>.md`: English briefs when a translation exists.
- `latest.json`: byte-identical to [raytally.com/latest.json](https://raytally.com/latest.json).
- `SKILL.md`: instructions for agents consuming RayTally.

Every brief is copied from the deployed site's static build output. The website copy action, Markdown endpoint, and repository file therefore share one generated source. Synced once a day after the site publishes (before 09:30 UTC+8). A day with zero new briefs means the full pipeline ran and selected nothing worth shipping — that is a designed outcome, not an outage.

## Endpoints

- [Latest Chinese issue](https://raytally.com/latest.json) · [All Chinese ideas](https://raytally.com/ideas.json)
- [Latest English issue](https://raytally.com/en/latest.json) · [All English ideas](https://raytally.com/en/ideas.json)
- [llms.txt](https://raytally.com/llms.txt) · [API catalog](https://raytally.com/.well-known/api-catalog) · [Agent skills index](https://raytally.com/.well-known/agent-skills/index.json)

## Evidence boundary / 证据边界

Signals are bounded observations captured at the timestamps in each brief. They are not market validation, user counts, or proof of lasting demand. Preserve the time boundary and strongest case against when summarizing or acting.

信号只是任务书所列时间点的有界观察，不是市场验证、用户数量或持续需求证明。转述或行动时，必须保留时间边界与最强反方。
