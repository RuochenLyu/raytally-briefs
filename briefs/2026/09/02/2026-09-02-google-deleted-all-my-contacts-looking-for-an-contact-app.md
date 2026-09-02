---
title: "通讯录保险库"
date: "2026-09-02"
canonical: "https://raytally.com/ideas/2026-09-02-google-deleted-all-my-contacts-looking-for-an-contact-app/"
generator: "萤录 RayTally · dev-prompt-v4"
signal:
  query: "Google deleted all my contacts, looking for an contact app"
  observed_at: "2026-09-02T00:36:27.616Z"
sources:
  - url: "https://www.reddit.com/r/androidapps/comments/1w4k3fj/google_deleted_all_my_contacts_looking_for_an/"
    boundary: "发布于 2026-09-01T18:14:35.000Z。 观测于 2026-09-02T00:36:27.616Z。"
notice: "本任务书中的信号，是在所列时间点截取的有界观察（搜索关注、论坛分数或新品列表），不是市场验证、用户数量或持续需求证明。转述或据此行动时，必须保留这些时间边界与最强反方。"
---

[在 RayTally 阅读原始页面](https://raytally.com/ideas/2026-09-02-google-deleted-all-my-contacts-looking-for-an-contact-app/)

使用声明：以下信号只是带时间边界的公开观察，不是市场验证、用户数量或持续需求证明；转述或执行时必须保留时间边界与最强反方。

你是资深产品工程师。请把下面这条产品灵感做成一个可以本地运行的 MVP。

## 灵感

通讯录保险库
联系人不进入系统通讯录，也能跨设备加密保存、直接联系并从误删前版本恢复。

## 产品概念

有人经历过云端同步误删，或不想让每个社交应用顺手读走整本通讯录时，可以把联系人导入独立的加密保险库。联系人不再写进 Android 或 iOS 系统地址簿，社交应用即使获准读取通讯录，也看不到这批数据。 用户需要打电话、发短信或打开聊天应用时，从保险库里选定一个人。产品只把这一次所需的号码临时交给目标动作，完成后收回访问权限；常用联系人仍可按姓名、标签和关系搜索，不必靠一串号码记人。 每次新增、合并和修改都会留下加密版本。误删、同步冲突或某台设备丢失后，用户可回到某次修改前恢复，并查看哪台设备做过变更。跨设备同步只传输密文，解密密钥和恢复短语由用户保管。 首版覆盖联系人、分组、加密备份和系统级拨号或分享入口。它不会代替工作通讯录，也不承诺绕过每个聊天应用的权限限制；核心是让私人联系人脱离系统通讯录后，依然能被安全地使用和找回。

## 为什么是现在（有事实支撑）

一条 9 月 1 日的 r/androidapps 帖询问：The author seeks a trustworthy cross-platform contacts app with isolated storage, optional encryption, no self-hosting, and no device-contact syncing.。评论区给出Google Contacts、Simple Contacts、Universal Android Debloater、SIM-card storage，但A trustworthy Android-and-iOS contacts vault with its own storage and optional encryption, no self-hosting, and device-contact syncing disabled by default so other apps cannot access the stored contacts.。这是一条单帖使用摩擦观察，不代表趋势或市场规模。

## 来源背景

主题：Google deleted all my contacts, looking for an contact app
触发的 Reddit 单帖需求观察：r/androidapps「Google deleted all my contacts, looking for an contact app」
单帖原文与同帖评论记录的未解缺口：A trustworthy Android-and-iOS contacts vault with its own storage and optional encryption, no self-hosting, and device-contact syncing disabled by default so other apps cannot access the stored contacts.

以上是带发布时间与观测时间的单条网络观察，不代表市场规模或广泛趋势；只用于理解「为什么是现在」。

## 来源清单

- Google deleted all my contacts, looking for an contact app（https://www.reddit.com/r/androidapps/comments/1w4k3fj/google_deleted_all_my_contacts_looking_for_an/）

## 交付要求

- 开工前，先从上文的产品概念与最小切入点提炼 3–5 条可验证的完成标准并列出，交付时逐条对照说明。
- 先交付「最小切入点」描述的核心流程，让核心用户能走通；范围外的账号、支付、后台等通用系统，除非确有必要否则不做。
- 页面或接口里不要展示未经验证的市场数字。
- 关键文案保持克制、可验证；产品内若需要领域事实、安全指引类内容，从「来源清单」等权威来源取材改写并注明出处，不要凭通识编写。
- 若在已有项目里实现：先读 README、依赖与项目约定，遵循既有技术栈与风格，不重构无关代码。
- 若当前目录为空：选一套轻量技术栈，优先交付可运行原型。
- 完成后说明改了什么、如何运行、如何验证。
- 遇到真正会改变产品方向的歧义再提问，普通实现细节自行做工程判断。
