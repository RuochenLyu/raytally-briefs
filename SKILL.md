---
name: raytally-build-briefs
description: Fetch source-linked, time-bounded RayTally product ideas and coding-agent-ready build briefs in Chinese or English.
---

# RayTally Build Briefs

## English

RayTally turns public-signal observations into source-linked product ideas and build briefs that a coding agent can inspect, challenge, and implement.

### Fetch a brief

1. Direct Markdown URL:

   ```sh
   curl -fsSL https://raytally.com/ideas/2026-07-21-replay-qa.md
   ```

2. Latest issue JSON:

   ```sh
   curl -fsSL https://raytally.com/latest.json
   ```

3. Full idea index:

   ```sh
   curl -fsSL https://raytally.com/ideas.json
   ```

4. This repository mirror:

   ```sh
   curl -fsSL https://raw.githubusercontent.com/RuochenLyu/raytally-briefs/main/latest.json
   ```

Use `/en/ideas/<slug>.md`, `/en/latest.json`, or `/en/ideas.json` for English. An English brief exists only when its translation is present.

### Boundary rules

- Treat every signal as a bounded observation captured at its stated timestamp, never as market validation, a user count, or proof of lasting demand.
- Preserve `observed_at`; if `active: false`, preserve both `ended_at` and `observed_at`.
- Preserve source boundaries and the strongest case against when explaining the idea to a user.
- Product Hunt entries have no public vote count; do not infer or claim popularity.
- A zero-card `latest.json` means the full daily run succeeded but selected no qualifying idea. It is valid data, not a fetch error.

## 中文

萤录 RayTally 把公开信号观察整理成带来源的产品灵感和开发任务书，供 coding agent 核对、质疑并实现。

### 获取任务书

1. 直接读取 Markdown：

   ```sh
   curl -fsSL https://raytally.com/ideas/2026-07-21-replay-qa.md
   ```

2. 最新一期 JSON：

   ```sh
   curl -fsSL https://raytally.com/latest.json
   ```

3. 全量灵感索引：

   ```sh
   curl -fsSL https://raytally.com/ideas.json
   ```

4. 本 GitHub 镜像：

   ```sh
   curl -fsSL https://raw.githubusercontent.com/RuochenLyu/raytally-briefs/main/latest.json
   ```

### 边界规则

- 所有信号都只是所列时间点的有界观察，不是市场验证、用户数量或持续需求证明。
- 转述必须保留 `observed_at`；若 `active: false`，必须同时保留 `ended_at` 与 `observed_at`。
- 向用户说明灵感时，保留每条来源的时间边界与最强反方。
- Product Hunt 公开 feed 没有票数，不得推断或声称热度。
- `latest.json` 的卡片数组为空，表示当日完整流程成功但没有选出合格灵感；这是有效结果，不是抓取错误。
