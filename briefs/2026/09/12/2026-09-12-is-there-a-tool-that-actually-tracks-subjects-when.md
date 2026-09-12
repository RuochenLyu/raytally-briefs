---
title: "会跟拍的竖屏剪辑"
date: "2026-09-12"
canonical: "https://raytally.com/ideas/2026-09-12-is-there-a-tool-that-actually-tracks-subjects-when/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "Is there a tool that actually tracks subjects when reformatting video aspect ratios"
  observed_at: "2026-09-12T00:33:52.886Z"
sources:
  - url: "https://www.reddit.com/r/EntrepreneursGrind/comments/1wdwrzf/is_there_a_tool_that_actually_tracks_subjects/"
    boundary: "发布于 2026-09-11T00:00:00.000Z。 观测于 2026-09-12T00:33:52.886Z。"
  - url: "https://helpx.adobe.com/premiere/desktop/add-video-effects/commonly-used-effects/add-auto-reframe-effect-to-a-sequence.html"
    boundary: "发布于 2026-04-15T00:00:00.000Z。"
  - url: "https://ai.meta.com/research/sam2/"
    boundary: "来源记录未提供发布时间。"
  - url: "https://developer.apple.com/documentation/professional-video-applications/describing-final-cut-pro-items-in-fcpxml"
    boundary: "来源记录未提供发布时间。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-09-12-is-there-a-tool-that-actually-tracks-subjects-when/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

会跟拍的竖屏剪辑
横屏素材改竖屏时，自动跟随真正的说话者或动作生成可编辑运镜，判断不稳的片段交给人确认。

## 产品概念

短视频编辑把横屏采访、比赛或直播素材改成竖屏时，最烦的不是裁切本身，而是画面总在错误的人身上。用户把视频拖进时间线，圈选主讲人、球员或当前动作，产品便生成一条可编辑的虚拟摄像机轨迹。轨迹会在安全区域内保持稳定，避免人物的头顶和字幕被切掉；当系统预测下一位即将接话或接球时，还会提前平滑移动画面。 编辑可以直接在时间线上拖动关键点、调整跟随力度和安全区。每次自动移动都保留为可修改的运镜数据，而不是把裁切结果烘焙成一条无法挽回的视频。多人对话时，编辑可选择“当前说话者优先”或“全员保持可见”，动作素材则可按球、车或手部等主体跟随。 遇到遮挡、多人重叠、快速出画或主体置信度突然下降，产品暂停自动决定，把片段标成待确认，并显示它当时看到的候选主体。第一版先覆盖常见人物和运动物体，输出 Premiere、剪映或 Final Cut 可继续编辑的关键帧轨迹，不负责替编辑完成字幕、调色和最终剪辑。

## 为什么是现在（有事实支撑）

一条2026年9月11日的r/EntrepreneursGrind帖子抱怨，试过3个横屏转竖屏工具后，结果仍只是居中裁切；现有方案没能稳定跟随说话者或动作。 截至9月12日，该帖记录为2分、0条评论，问题出现在创作者正把YouTube横屏内容改成Reels的交付节点。

## 方向判断（以下为模型推断，未经独立验证）

目标用户：核心用户是经常把播客、采访、课程和赛事素材改成竖屏的剪辑师。他们通常在横屏母版已经定剪后，才接到 Reels 或 Shorts 的交付任务。此时字幕、切点和节奏大多不能重做，只能快速补出可靠构图。素材越长、人物切换越多，逐镜打关键帧越难按期完成。

最小切入点：技术核心可拆成主体轨迹、镜头规划和导出三层。用户在首帧圈选后，用 SAM 2 向后传播主体掩码。它支持点、框或掩码提示，也允许在后续帧纠正结果。 采访素材再做离线说话人分段，并与人脸轨迹匹配。镜头规划只生成位置、缩放和贝塞尔关键点，再加入头顶、字幕区和速度约束。首版先支持单主体与双人采访，不做任意球类的接球预测。导出先落在 Final Cut Pro 的 FCPXML；该格式可描述项目时间线，供应用与 Final Cut Pro 交换数据。

最强反方：说话人分段和人脸对应一旦错配，镜头会持续跟错人。提前移动若猜错下一位发言者，成片会出现无缘由的摇镜。比赛素材还会遇到遮挡、镜头切换和高速小物体，单一跟踪模型很难覆盖。为减少误报，系统必须保存置信度、候选主体和人工修改历史，这会增加存储与界面复杂度。FCPXML 导入后的坐标、缩放和插值也要逐版本验证。若编辑仍需通看全部素材，自动化带来的省时价值会明显下降。私密采访和未发布赛事素材还会限制云端处理，迫使产品承担本地推理的性能成本。

以上是模型基于灵感本身与已核验事实的推断，请当作方向假设与真实约束对待：不要默认「最强反方」已被解决，也不要据此在产品里写下确定性结论。

## 以小博大（模型推断）

第一批用户可从专做播客切片、课程分发和赛事集锦的小型剪辑团队中寻找。这些团队有重复素材，也能直接比较人工改竖屏所花的时间。用同一段多人采访展示居中裁切、自动跟拍和人工修正后的差异。再提供少量免费处理额度，换取失败片段和最终关键帧，逐步补齐最常见的遮挡案例。

## 竞品与缝隙（模型推断）

- Adobe Premiere Pro Auto Reframe：Premiere Pro 已能复制序列并转换目标比例，还会给片段应用 Auto Reframe。 它提供慢速、默认和快速三档运动预设。快速模式会跟随动作，并生成更多关键帧。 遇到多处兴趣点或快速运动时，编辑仍需手工微调关键帧。 现有入口主要让用户选择画幅和运动速度。官方说明未提供圈选主角、说话者优先或全员可见等控制。它也没有把判断不稳的片段单独标出，并展示候选主体。采访中的轮流发言，仍可能需要逐段检查。比赛中的传球和快速出画，也缺少面向编辑的歧义处理。缝隙在于把结果做成可审阅的运镜轨迹，让人只处理确实含糊的片段。

## 怎么赚钱（模型推断）

按席位收取月度订阅费，并按可处理的视频时长设置用量档位。基础版提供人物跟随和 FCPXML 导出，高阶版再开放团队审阅、批量处理和自定义安全区。

## 来源背景

主题：Is there a tool that actually tracks subjects when reformatting video aspect ratios
触发的 Reddit 单帖需求观察：r/EntrepreneursGrind「Is there a tool that actually tracks subjects when reformatting video aspect ratios」
单帖原文与同帖评论记录的未解缺口：将横屏视频转为竖屏时，稳定识别并跟随说话者或主要动作，而不是固定居中裁切。

以上是带发布时间与观测时间的单条网络观察，不代表市场规模或广泛趋势；只用于理解「为什么是现在」。

## 来源清单

- Is there a tool that actually tracks subjects when reformatting video aspect ratios（https://www.reddit.com/r/EntrepreneursGrind/comments/1wdwrzf/is_there_a_tool_that_actually_tracks_subjects/）
- Add Auto Reframe effect to sequences in Premiere（https://helpx.adobe.com/premiere/desktop/add-video-effects/commonly-used-effects/add-auto-reframe-effect-to-a-sequence.html）
- Introducing Meta Segment Anything Model 2 (SAM 2)（https://ai.meta.com/research/sam2/）
- Describing Final Cut Pro Items in FCPXML（https://developer.apple.com/documentation/professional-video-applications/describing-final-cut-pro-items-in-fcpxml）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
