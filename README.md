# Deskmate

办公室里每个人电脑上的 agent 副手：替主人接活、答问，小事自己办，拿不准的回来问主人。

- **没有中心服务器**。每人装同一个 app，彼此对等，靠局域网发现。
- **每个人的电脑就是隔离边界**。开不开放、开放哪些项目，由主人决定。
- **聊天留在 Discord**，每人有自己的 bot；**任务全部落成 GitHub issue**。
- **小内核 + 插件**。内核只管 agent 连接、会话、事件流、存储，其余都是插件。

仅限办公室内部使用。「Deskmate」这个名字与多个公开产品重名，对外发布前必须改名。

## 现状

**设计阶段，还没有代码。** 仓库目前只有文档：

| 文档 | 管什么 |
| --- | --- |
| [docs/product.md](docs/product.md) | 产品设计：已定的决策、核心流程、还没定的问题 |
| [docs/adr-001-无中心对等架构.md](docs/adr-001-无中心对等架构.md) | 为什么不要服务器，三条通道各管什么 |
| [docs/adr-002-技术栈.md](docs/adr-002-技术栈.md) | 为什么全栈 TypeScript，哪些待首个 spike 验证 |
| [AGENTS.md](AGENTS.md) | 工程规范（Claude 与 Codex 共用） |

下一步见 [docs/product.md §待定问题](docs/product.md#待定问题)：插件设计与个人助理还没展开讨论，定了再搭代码骨架。

## 前身

[acpp](../acpp)（同级目录）是前身：单机、单人的 ACP 管理面板，功能全部编译进后端，没有扩展缝，2026-11 决定换架构重做。它的代码不搬，搬的是三样知识：

- 两端 adapter（codex-acp / claude-agent-acp）的协议实测结论与差异收敛思路（acpp `docs/adr-001`、`docs/adr-011`）
- 桌面壳的教训（acpp `docs/adr-015`：WKWebView 拖窗卡顿，必须用 Electron）
- Discord 频道工作区的实测手法（acpp `docs/adr-016` ~ `adr-018`）
