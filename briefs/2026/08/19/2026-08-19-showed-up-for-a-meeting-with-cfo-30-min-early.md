---
title: "相邻日程导航"
date: "2026-08-19"
canonical: "https://raytally.com/ideas/2026-08-19-showed-up-for-a-meeting-with-cfo-30-min-early/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "Showed up for a meeting with CFO 30 min early"
  observed_at: "2026-08-19T00:38:56.675Z"
sources:
  - url: "https://www.reddit.com/r/ADHD/comments/1vs5voq/showed_up_for_a_meeting_with_cfo_30_min_early/"
    boundary: "发布于 2026-08-18T23:41:23.000Z。 观测于 2026-08-19T00:38:56.675Z。"
  - url: "https://developer.apple.com/documentation/eventkit/accessing-the-event-store"
    boundary: "来源记录未提供发布时间。"
  - url: "https://developer.apple.com/documentation/mapkit/mkdirections"
    boundary: "来源记录未提供发布时间。"
  - url: "https://support.apple.com/en-euro/guide/iphone/iph3d110f84/ios"
    boundary: "来源记录未提供发布时间。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-08-19-showed-up-for-a-meeting-with-cfo-30-min-early/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

相邻日程导航
相邻安排撞在一起时，把时间、路程和提前到场偏好合成当前行动提示，避免早到一场却错过下一场。

## 产品概念

有人为了不迟到，提前半小时赶到与 CFO 的会议室，却因此错过了附近另一项承诺。对 ADHD 用户来说，日历里一排独立提醒很容易把“早到”伪装成“安排妥当”。真正要解决的是：眼前这件事该做到哪一步，才不会挤掉后面两件事。 用户授权工作和个人日历，填入常用通勤方式与提前到场偏好。产品把相隔不远的会议、课程、取件和线上培训串成一段行程。锁屏上不再堆满提醒，只显示当前动作，例如“在大厅等 12 分钟，15:35 离开可赶上下一场线上培训”。下方保留紧接着的两项安排、地点和最晚离开时间。 当用户提前抵达某地，系统依据当前位置、两地路程和下一项的固定开始时间重新计算。若继续等待会导致冲突，它会明确标出会受影响的安排，并给出离开、改线上参加或通知对方晚到的选项。用户点选后，才向相关联系人发送预设消息。 起步可先支持 Google Calendar、Apple 日历和步行、驾车路线。产品保持只读，不会替用户取消会议或编造空档；它的职责是把分散日程压成下一步能照着做的行动提示。

## 为什么是现在（有事实支撑）

一条 8 月 18 日的 r/ADHD 帖抱怨，作者为避免迟到，提前 30 分钟到达会议。 帖子还提到紧接着的培训，且上周曾错过；评论区没有可核实方案，缺口是同时照看相邻承诺。

## 方向判断（以下为模型推断，未经独立验证）

目标用户：主要用户是同时使用工作和个人日历的 ADHD 成年人。他们常在会议、课程、取件和通勤连续发生时失去整体时间感。问题通常出现在已经提前到场，或正专注于当前事项的那一刻。此时普通提醒只重复开始时间，无法回答还能等多久，以及哪项后续安排会被挤掉。

最小切入点：先做 iPhone 原生版，读取设备上已接入的工作和个人日历。EventKit 能读取日历事件，但需要申请完整访问；产品逻辑仍禁止写回和删改。 首版只处理有固定开始时间的相邻事件，地点不明时要求用户确认。MapKit 可计算步行或驾车路线及预计用时，用来倒推最晚离开时间。 规则引擎只看当前项和后续两项，不自动改动原日程。锁屏层显示一条当前动作，并列出时间依据和受影响安排。位置只在活动行程期间参与重算，消息必须由用户确认后发送。

最强反方：日历与位置权限会直接卡住首次使用。iOS 上读取事件需要完整访问，即使产品不写回，授权文案仍会显得很重。 地址缺失、会议室名称含糊或链接混在备注里，都会让路线判断失真。到达检测和后台更新若慢几分钟，锁屏指令就可能引导用户做出错误选择。错误提醒会放大焦虑，误发晚到消息还会伤害职业关系。继续做的前提是默认不自动发信，展示计算依据，并允许用户随时纠正地点与进度。

以上是模型基于灵感本身与已核验事实的推断，请当作方向假设与真实约束对待：不要默认「最强反方」已被解决，也不要据此在产品里写下确定性结论。

## 以小博大（模型推断）

第一批用户可从讨论时间盲区的 ADHD 社区招募，而不是泛投效率工具人群。演示内容应复现“早到一场，却挤掉下一场”的完整过程。用 TestFlight 邀请用户带入真实的一天日程，重点记录地点修正和误报原因。隐私页要直接展示读取范围、位置启用时段，以及产品不会改动日历。

## 竞品与缝隙（模型推断）

- Apple 日历：Apple 日历已支持为事件填写行程时间。添加地址后，它会结合 Apple 地图、交通与公共交通信息，提示用户何时出发。 这解决了前往单项活动时的基础提醒问题。它还占据系统通知入口，无需用户另装工具。公开说明仍围绕单个事件和一次出发提醒，未展示把后续两项安排一起重算。 用户提前抵达后，等待多久才不影响下一场，仍需自己判断。当线下会议紧接线上培训时，也缺少统一的最晚离开指令。它也未明确展示哪项安排将受影响，再让用户选择离开、转线上或通知晚到。产品的缝隙是在日历之上增加实时协调层，而非替代日历。

## 怎么赚钱（模型推断）

采用月度订阅。免费版提供当天行动提示和基础冲突预警，付费版开放多日规划、多个日历、位置重算与消息模板。

## 来源背景

主题：ADHD 用户相邻日程与时间冲突提醒
触发的 Reddit 单帖需求观察：r/ADHD「Showed up for a meeting with CFO 30 min early」
单帖原文与同帖评论记录的未解缺口：A calendar/reminder aid would need to preserve awareness of multiple nearby commitments and explicitly surface timing conflicts while the user is focused on one event.

以上是带发布时间与观测时间的单条网络观察，不代表市场规模或广泛趋势；只用于理解「为什么是现在」。

## 来源清单

- Showed up for a meeting with CFO 30 min early（https://www.reddit.com/r/ADHD/comments/1vs5voq/showed_up_for_a_meeting_with_cfo_30_min_early/）
- Accessing the event store（https://developer.apple.com/documentation/eventkit/accessing-the-event-store）
- MKDirections（https://developer.apple.com/documentation/mapkit/mkdirections）
- Create and edit events in Calendar on iPhone（https://support.apple.com/en-euro/guide/iphone/iph3d110f84/ios）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
