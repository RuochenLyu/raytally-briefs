---
title: "MV2 扩展迁移对照跑"
date: "2026-09-01"
canonical: "https://raytally.com/ideas/2026-09-01-google-has-removed-mv2-extensions-from-the-chrome-web-store/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "Google Has Removed MV2 Extensions from the Chrome Web Store, Including UBO"
  observed_at: "2026-09-01T00:33:19.377Z"
sources:
  - url: "https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline"
    boundary: "来源记录未提供发布时间。"
  - url: "https://playwright.dev/docs/next/chrome-extensions"
    boundary: "来源记录未提供发布时间。"
  - url: "https://www.browserstack.com/docs/automate/playwright/chrome-extension-testing"
    boundary: "来源记录未提供发布时间。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-09-01-google-has-removed-mv2-extensions-from-the-chrome-web-store/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

MV2 扩展迁移对照跑
扩展迁移到 MV3 时，并排重放真实浏览流程，立刻找出新版从哪一步失去旧有能力。

## 产品概念

Chrome 移除旧版 MV2 扩展的安装渠道后，维护者最怕的不是改不动 API，而是 MV3 版本在某个真实页面上悄悄少拦了一类请求。这里的 MV2 与 MV3 是 Chrome 扩展的两代运行规则。团队上传仍在线上运行的旧包和待发布的新包，再选出最能代表用户习惯的网页、登录状态与点击流程。 产品启动两组隔离浏览器，让旧版与新版影子执行同一段操作：打开标签页、切换账户、访问动态页面、触发网络请求，再改动权限状态。它把两边的页面结果、请求记录、存储变化和控制台输出对齐。只要结果出现分叉，报告就停在第一个不同的动作上，附上触发条件、相关 API 和可直接运行的最小复现脚本。 维护者可以把一次修复后的流程存成回归用例，提交代码时自动重跑。首个版本聚焦广告拦截、脚本管理和隐私类扩展常见的网络请求与后台任务，不试图替团队设计完整迁移方案。它交付的是一份能被工程师马上复现和修掉的行为差异清单。

## 为什么是现在（有事实支撑）

2026年8月31日，Chrome Web Store 移除了所有剩余 MV2 扩展。 已装旧版也无法更新或重装，维护者因此更急于在发布前排查 MV3 的静默行为回退。

## 方向判断（以下为模型推断，未经独立验证）

目标用户：面向仍维护广告拦截、脚本管理或隐私扩展的小团队。最需要它的时候，是 MV3 候选包准备提交商店前，或迁移修复刚合并时。此时单元测试通常已通过，团队更担心登录态、动态页面和权限切换后的行为偏差。值班维护者需要可直接复现的差异，而不是再读一份迁移清单。

最小切入点：用 Playwright 接管两个隔离的持久化浏览器配置，并分别载入解压包。 双跑先固定同一 Chrome 138 基线，并启用官方保留策略。 操作录制只覆盖导航、点击、账户切换和权限变更。采集层通过 Playwright 事件与 CDP 记录 DOM 摘要、请求、控制台和存储快照。对齐器按动作边界比较，不追求整页像素一致。报告先给首个分叉，再生成可重跑的 Playwright 用例。通过对照后，MV3 包再到当前 Chromium 做单包冒烟测试。

最强反方：动态站点会制造大量假差异。广告轮换、A/B 实验、时间戳和接口返回，都可能先于扩展发生分叉。若归一化过强，真实漏拦又会被抹掉。登录流程还涉及验证码、双重验证和会话过期，回放稳定性会直接影响报告可信度。旧版运行器必须固定在 Chrome 138，长期维护过期浏览器和高风险沙箱并不轻松。 扩展包与登录态也很敏感，隔离、密钥销毁和本地部署会抬高交付成本。首个分叉一旦频繁误报，工程师很快会回到手工复测。

以上是模型基于灵感本身与已核验事实的推断，请当作方向假设与真实约束对待：不要默认「最强反方」已被解决，也不要据此在产品里写下确定性结论。

## 以小博大（模型推断）

第一批用户就在 GitHub 上仍保留 MV2 与 MV3 构建的扩展仓库。把运行器做成可复用的 GitHub Action，在迁移 PR 中附上首个行为分叉和复现脚本。可挑公开的广告拦截或脚本管理项目，提交可核验的失败用例。再公开一组脱敏差异报告，让维护者判断它是否比现有 E2E 更省排查时间。

## 竞品与缝隙（模型推断）

- Playwright 自建扩展 E2E：Playwright 已能在持久化 Chromium 上加载扩展，并取得 MV3 服务工作线程。 团队可以自行编排登录、点击、弹窗和页面断言，也能接入现有 CI。它适合已经明确知道要验证什么的工程组。测试作者仍要手写预期结果，并维护旧包与新包的运行环境。它不会自动把两边的请求、存储和控制台记录按动作对齐。动态页面产生差异后，团队还要判断哪一处才是首个因果分叉。服务工作线程休眠和权限切换等场景，也需按扩展结构定制夹具。产品的缝隙是把双版本编排、差异消噪和最小复现生成做成默认流程。
- BrowserStack Automate：BrowserStack Automate 已支持上传 Chrome 扩展包，并在 Playwright 远程会话中运行。 它还能保留网络日志和会话结果。 浏览器基础设施、系统矩阵和团队协作都已成熟。对于跨环境兼容性测试，它比自建浏览器池省事。现有流程仍以测试脚本驱动单个扩展包，再由脚本写断言为主。文档未提供 MV2 与 MV3 同步回放、状态对齐或首个分叉定位。 团队仍需自己处理相同登录态、页面数据和差异消噪。产品可以成为其上的迁移诊断层，也可用本地运行器承接敏感扩展与账户。

## 怎么赚钱（模型推断）

按团队订阅收费，套餐包含固定的并行回放与 CI 运行额度。超出额度后，按浏览器运行时长计费。本地部署和私有运行器作为更高档方案。

## 来源背景

主题：Chrome Web Store 移除 MV2 扩展及 uBlock Origin
触发的 Hacker News 原帖（英文原文）：Google Has Removed MV2 Extensions from the Chrome Web Store, Including UBO
抓取时热度：约 408 分、328 条评论（观测时点数值）

以上数据是抓取时刻的历史快照，分数与评论数会随时间漂移，只用于理解「为什么是现在」，不要写进产品文案当作精确的市场数字。

## 来源清单

- Manifest V2 support timeline（https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline）
- Chrome extensions（https://playwright.dev/docs/next/chrome-extensions）
- Test Chrome Extensions on Playwright tests in BrowserStack Automate（https://www.browserstack.com/docs/automate/playwright/chrome-extension-testing）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
