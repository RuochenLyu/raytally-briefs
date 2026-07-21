# RayTally Build Briefs

RayTally turns source-linked, time-bounded public signals into product ideas and coding-agent-ready build briefs. This repository is a data-and-skill mirror, not a second website and not a separate editorial source.

萤录 RayTally 把带来源、带时间边界的公开信号整理成产品灵感与 coding agent 可直接读取的开发任务书。本仓库是 data + skill 镜像，不是网站副本，也不是第二套内容源。

## Contents

- `briefs/YYYY/MM/DD/<slug>.md`: Chinese briefs.
- `briefs/YYYY/MM/DD/en/<slug>.md`: English briefs when a translation exists.
- `latest.json`: byte-identical to [raytally.com/latest.json](https://raytally.com/latest.json).
- `SKILL.md`: instructions for agents consuming RayTally.

Every brief is copied from the deployed site's static build output. The website copy action, Markdown endpoint, and repository file therefore share one generated source.

## Endpoints

- [Latest Chinese issue](https://raytally.com/latest.json)
- [All Chinese ideas](https://raytally.com/ideas.json)
- [Latest English issue](https://raytally.com/en/latest.json)
- [All English ideas](https://raytally.com/en/ideas.json)
- [Agent instructions](https://raytally.com/llms.txt)

## Evidence boundary / 证据边界

Signals are bounded observations captured at the timestamps in each brief. They are not market validation, user counts, or proof of lasting demand. Preserve the time boundary and strongest case against when summarizing or acting.

信号只是任务书所列时间点的有界观察，不是市场验证、用户数量或持续需求证明。转述或行动时，必须保留时间边界与最强反方。
