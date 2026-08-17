---
title: "AI 改稿逐处确认"
date: "2026-08-17"
canonical: "https://raytally.com/ideas/2026-08-17-anthropic-s-watermark-text-adulteration-in-claude-is-a/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing"
  observed_at: "2026-08-17T00:33:16.293Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49324087"
    boundary: "发布于 2026-08-16T21:53:43.000Z。 观测于 2026-08-17T00:33:16.293Z。"
  - url: "https://daringfireball.net/2026/08/anthropics_watermark_text_adulteration_in_claude_is_a_perversion_of_writing"
    boundary: "发布于 2026-08-16T00:00:00.000Z。 观测于 2026-08-17T00:33:16.293Z。"
  - url: "https://developers.google.com/workspace/docs/api/how-tos/suggestions"
    boundary: "发布于 2026-07-21T00:00:00.000Z。"
  - url: "https://support.microsoft.com/en-US/Word/accept-or-reject-tracked-changes-in-word"
    boundary: "来源记录未提供发布时间。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-08-17-anthropic-s-watermark-text-adulteration-in-claude-is-a/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

AI 改稿逐处确认
写作者让 AI 润色定稿时，只接收逐处可批准的文字补丁，避免全文被无声改写或混入隐藏字符。

## 产品概念

写作者把接近定稿的文章交给 AI 润色时，通常只想借几个更好的措辞，却担心整段文字被悄悄换掉。尤其是合同、投稿和公开声明，作者需要知道最后留下的每个改动来自哪里。 编辑器插件只读取用户框选的段落，并要求模型以补丁形式返回建议。原文和建议稿并排显示，删除、替换和新增内容按块标色。作者可以接受一句、拒绝一句，或手动改完再继续请求下一处建议，AI 无法直接覆盖整篇文稿。 每次接受后，插件会扫描不可见 Unicode 字符、异常格式和复制时混入的控制符。修改记录保留原句、接受时间与最终文本，导出时还能生成一份干净版本。编辑或法务复核时，作者能逐处说明哪些文字由自己确认过。 早期版本先做浏览器写作场景与常见文档编辑器的补丁面板，支持润色、压缩和改语气三类请求。它不替作者判断事实，不代替协作审批，只把 AI 改稿收束为一连串可见、可撤销的文字选择。

## 为什么是现在（有事实支撑）

8月16日，一篇文章质疑 Claude 文本水印会介入措辞选择，使润色后的文字归属成为具体担忧。 截至8月17日0时33分，该帖位列第10，记录为121 points和99 comments。

## 方向判断（以下为模型推断，未经独立验证）

目标用户：核心用户是准备提交合同、稿件或公开声明的人。此时文章已接近定稿，事实与立场通常不容重排。他们只想借 AI 调整少量措辞，却必须确认每个字是否仍符合原意。编辑、法务和客户追问改动来源时，还需要拿出逐处批准记录，而不是一份无法解释的整段终稿。

最小切入点：浏览器插件先读取当前选区，并保存原文哈希。模型必须返回结构化补丁，包含定位片段、替换文本和简短理由。前端用文本差分把补丁拆成可独立批准的句块。写入前再次核对选区与哈希，避免文档变化造成错位。控制符扫描独立运行，只报告真实码点与格式异常。首版先覆盖普通网页编辑框，再接入 Word 修订接口。Google Docs 的写入建议接口仍在开发者预览，可作为后续适配。

最强反方：不可见字符扫描很容易被误解为水印检测。Claude 所述方案不加入隐藏字符，而是通过词语选择留下统计信号。 因此清理控制符只能解决复制污染，无法验证或移除这类水印。富文本中的脚注、链接和批注会让补丁定位变得脆弱。选区变化后写错位置，可能直接损坏合同或声明。模型也可能漏报改动，结构化返回并不等于内容可信。保存原句与接受时间还会积累敏感文本，带来加密、留存和删除成本。若无法把“字符卫生”与“水印判断”讲清，用户会迅速失去信任。

以上是模型基于灵感本身与已核验事实的推断，请当作方向假设与真实约束对待：不要默认「最强反方」已被解决，也不要据此在产品里写下确定性结论。

## 以小博大（模型推断）

第一批用户可直接来自此次 Hacker News 讨论中的写作者与开发者。 做一个无需登录的选区差分演示，让用户当场看到整段重写被拆成哪些选择。插件商店页面重点展示合同条款和公开声明的前后对照。再用匿名化的改动样例发布技术文章，解释哪些字符被清理，哪些水印无法检测。

## 竞品与缝隙（模型推断）

- Microsoft Word 修订与文档检查器：Word 已能标出增删内容，并让审阅者逐项接受或拒绝。文档检查器还能发现隐藏文本等信息。 这套能力适合人工协作，也能承接外部生成的改稿。缺口在于 AI 请求发生在另一套交互里。用户仍要复制段落、提示模型，再把结果放回文档。模型若返回整段重写，Word 只能展示结果差异，无法限制改动范围。它也不保存提示、原始选区和模型补丁之间的对应关系。本产品可把生成前的约束与生成后的批准串在一起。每次写入都绑定用户明确接受的文字块。
- Google Docs 建议模式：Google Docs 的建议模式把编辑保留为待批准改动。官方 API 能以内联方式读取建议。创建及接受、拒绝建议的能力仍在开发者预览中。 这给插件提供了可利用的文档原生界面。现成建议模式主要解决协作者如何提交修改。它不会自动要求模型只返回选区内的最小补丁。用户仍可能把一段完整改稿贴回文档，再逐项辨认差异。建议线程也不等于完整的 AI 修改凭据。产品缝隙是保存请求、原句、补丁和最终写入结果。即使平台接口失败，也要阻止未经确认的文本落入正文。

## 怎么赚钱（模型推断）

按席位提供月度订阅。免费版保留基础逐句确认与本地撤销。付费版提供跨文档历史、审计导出和团队策略。模型费用可由用户自带密钥承担，避免订阅被推理成本吞噬。

## 来源背景

主题：Claude 文本水印与写作篡改争议
触发的 Hacker News 原帖（英文原文）：Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing
抓取时热度：约 121 分、99 条评论（观测时点数值）

以上数据是抓取时刻的历史快照，分数与评论数会随时间漂移，只用于理解「为什么是现在」，不要写进产品文案当作精确的市场数字。

## 来源清单

- Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing（https://news.ycombinator.com/item?id=49324087）
- Anthropic’s ‘Watermark’ Text Adulteration in Claude Is a Perversion of Writing（https://daringfireball.net/2026/08/anthropics_watermark_text_adulteration_in_claude_is_a_perversion_of_writing）
- Work with comments and suggestions（https://developers.google.com/workspace/docs/api/how-tos/suggestions）
- Accept or reject tracked changes in Word（https://support.microsoft.com/en-US/Word/accept-or-reject-tracked-changes-in-word）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
