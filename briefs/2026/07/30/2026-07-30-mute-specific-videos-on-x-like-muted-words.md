---
title: "把同一段视频从 X 隐掉"
date: "2026-07-30"
canonical: "https://raytally.com/ideas/2026-07-30-mute-specific-videos-on-x-like-muted-words/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "The hate he gets stems from misogyny and homophobia The hate he gets is from chewing fucking obnoxiously and then the video popping up everywhere on social media because people keep sharing it. I wish there was a way to mute a video in the same way you can mute words. Johnathan Irwin (@A2ZJIRWINKO) "
  observed_at: "2026-07-30T00:33:40.980Z"
sources:
  - url: "https://x.com/A2ZJIRWINKO/status/2082251375908471212"
    boundary: "发布于 2026-07-28T23:46:29.000Z。 观测于 2026-07-30T00:33:40.980Z。"
  - url: "https://help.x.com/en/using-x/advanced-x-mute-options"
    boundary: "来源记录未提供发布时间。"
  - url: "https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts"
    boundary: "来源记录未提供发布时间。"
  - url: "https://chromewebstore.google.com/detail/ytblock-block-any-content/nedcanggplmbbgmlpcjiafgjcpdimpea"
    boundary: "发布于 2026-07-15T00:00:00.000Z。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-07-30-mute-specific-videos-on-x-like-muted-words/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

把同一段视频从 X 隐掉
在 X 上点一次屏蔽不想再看的视频，之后它的转载、裁切版和轻度改编版都会自动折叠。

## 产品概念

用户在 X 信息流里再次刷到令人不适的原视频时，从帖子菜单点一次“屏蔽这段视频”。扩展先在本机为用户点选的画面和音轨生成指纹，随后把原帖替换为一张可展开的占位卡，说明它命中了哪条个人规则。 以后有人换账号、改标题、裁掉边缘、镜像画面、加字幕或略微变速再发，只要仍包含这段内容，扩展便会在加载信息流时将其折叠。用户可选择只隐藏完整原片，或隐藏含某一片段的所有版本；也能为规则设定七天、一月或永久有效。 设置页会列出被隐藏的帖子，用户可以恢复某一条，或删除整条规则。识别和匹配默认在设备上完成，不上传完整视频和观看记录；占位卡仍保留原帖链接，方便用户在需要时自行查看。 第一版只做桌面端 X 信息流，且必须由用户亲自点选一个视频才能建立规则。它不替用户判断什么内容该看，也不把关键词屏蔽误当成视频识别。

## 为什么是现在（有事实支撑）

7月28日，一名 X 用户抱怨同一段咀嚼视频因反复分享而到处弹出。 该帖发布后累计点赞 144 / 转发 2 / 浏览 8800，用户已把反复撞见原片说成具体痛点。

## 方向判断（以下为模型推断，未经独立验证）

目标用户：经常刷 X 的用户，尤其是会被血腥、羞辱、噪声或强烈感官内容触发的人。最需要它的时刻，是刚关掉一条视频，却又从别的账号看到裁切版。此时关键词和账号屏蔽都失灵，用户也最清楚自己要避开的具体片段。规则由本人点选建立，可减少替用户判断内容的争议。

最小切入点：用 Manifest V3 内容脚本接管 X 帖子菜单，并监听动态加载的视频卡片。内容脚本可以读取和修改页面 DOM，适合完成占位卡替换。 用户点选后，先验证扩展后台能否读取该视频资源；失败时不建立规则。对可读取的视频按固定间隔抽帧，缩放、灰度化后生成感知哈希。匹配时同时比较原图、镜像与多种中心裁切，并用连续帧序列降低单帧误报。音轨先作为辅助信号，不单独触发隐藏。规则和命中记录存于本机，首版只预取低清片段，并限制并发分析数量。

最强反方：读取 X 视频资源可能先成为阻断项。若跨域、签名地址或播放器结构变化导致拿不到帧，规则就无法建立。持续抽帧和音频分析会增加 CPU、耗电与流量，滚动信息流还会放大延迟。阈值过松会误折叠相似素材，阈值过严又会漏掉裁切、镜像和变速版。误报会让用户担心错过重要上下文，频繁漏报则会迅速破坏信任。X 的 DOM 与媒体加载方式变化，还会带来持续维护成本。发布前必须用真实改编样本测试性能与准确性，否则应缩小支持的变体范围。

以上是模型基于灵感本身与已核验事实的推断，请当作方向假设与真实约束对待：不要默认「最强反方」已被解决，也不要据此在产品里写下确定性结论。

## 以小博大（模型推断）

第一批用户可从公开抱怨“同一视频总被转发”的 X 讨论中找到。用同一素材制作原片、镜像、裁切、字幕和变速对照，直接展示哪些版本会被折叠。Chrome 商店页面可围绕“mute specific video on X”等原话布局，承接已有明确意图的搜索。再邀请创伤内容、厌恶刺激和信息流整理社群测试，重点收集漏报样本与误折叠截图。

## 竞品与缝隙（模型推断）

- X 原生静音功能：X 原生提供账号静音，以及词语、短语、用户名、表情和话题标签静音。词语规则可作用于主页时间线和通知，还能设置 24 小时、7 天、30 天或永久，并在设置中撤销。 这套能力已覆盖“谁发的”和“文字里写了什么”。官方还说明，含静音词的帖子仍可能出现在搜索结果中。 它没有按画面或音轨建立个人规则的入口。换账号、删标题或改文案后，同一段视频仍可能穿过文字规则。静音整个账号又会连带隐藏该账号的其他内容。这里的缝隙很具体：保留熟悉的静音时长与撤销方式，把匹配对象换成用户亲自点选的视频片段。
- YTBlock：YTBlock 是面向 YouTube 的浏览器扩展。它可按标题、频道、标签、描述、时长、链接和视频 ID 等条件屏蔽内容，也提供白名单和遮罩。 它已经把细粒度规则、可撤销列表和扩展内管理做得较完整。其判断核心仍是页面元数据或可见属性。标题改写、频道更换或同一素材重新上传时，用户需要继续补充规则。它也不服务 X 信息流，无法直接处理转帖与裁切版反复出现。可借鉴的是规则管理和覆盖层交互。真正的差异应放在视听内容匹配、片段级规则和命中原因解释，而不是再做一套关键词黑名单。

## 怎么赚钱（模型推断）

基础版免费，付费版采用一次性买断。付费能力可包括不限规则、批量管理和本地备份。识别不依赖云端，持续订阅的必要性较弱。

## 来源背景

主题：在 X 上按视频内容进行屏蔽
触发的网络趋势观察：X @A2ZJIRWINKO「The hate he gets stems from misogyny and homophobia The hate he gets is from chewing fucking obnoxiously and then the video popping up everywhere on social media because people keep sharing it. I wish there was a way to mute a video in the same way you can mute words. Johnathan Irwin (@A2ZJIRWINKO) 」
有界观察：用户抱怨某段令人讨厌的咀嚼视频因被不断分享而到处弹出，明确许愿能像屏蔽词语一样屏蔽特定视频。；点赞 144 / 转发 2 / 浏览 8800（发布后累计）

以上是带发布时间与观测时间的单条网络观察，不代表市场规模或广泛趋势；只用于理解「为什么是现在」。

## 来源清单

- I wish there was a way to mute a video in the same way you can mute words（https://x.com/A2ZJIRWINKO/status/2082251375908471212）
- How to use advanced muting options（https://help.x.com/en/using-x/advanced-x-mute-options）
- Content scripts（https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts）
- YTBlock - Block any content from YouTube（https://chromewebstore.google.com/detail/ytblock-block-any-content/nedcanggplmbbgmlpcjiafgjcpdimpea）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
