# Release v1.3.2

## Visible Traders 1.3.2 — Minecraft 1.21.1 / Fabric（归档）

原版制品的归档发布，**模组代码未做任何修改**。

- **Minecraft**：1.21.1
- **加载器**：Fabric Loader ≥ 0.18.4
- **依赖**：Fabric API ≥ 0.116.7+1.21.1
- **Java**：≥ 21

### 文件

| 文件 | 大小 | SHA-256 |
| --- | --- | --- |
| `VisibleTraders-1.3.2.jar` | 65,742 B | `39D70E06C8C39AF5575431CEDED4A14C662B6E2CCF530B65F4551789066E0F10` |

该哈希与 Modrinth 官方发布物**完全一致**，可确认未经任何改动。

### 功能

在原版村民交易界面中预览**尚未解锁**的交易：

- 已解锁与未解锁交易合并显示
- 无需反复升级试探即可了解后续交易
- 为刷新交易类模组提供兼容钩子

### 与 Trade Cycling 搭配

| 组合 | 结果 |
| --- | --- |
| 本版本 + Trade Cycling 1.21.1-1.0.23 原版 | ⚠️ 刷新后未解锁交易消失 |
| 本版本 + Trade Cycling 修复版 | ✅ 正常 |

> 问题源于 Trade Cycling 的反射桥接调用了已重命名的方法，Visible Traders 本身无需修改。
> 详见 [docs/compatibility.md](../docs/compatibility.md)

### 安装

1. 安装 Minecraft 1.21.1 + Fabric Loader
2. 将 jar 与 Fabric API 放入 `mods/`
3. 多人游戏中建议服务端也安装

### 版权

- **Visible Traders** © 2024 **Ramixin** — MIT License
- 上游仓库：https://github.com/Ramixin/VisibleTraders
- 上架页：https://modrinth.com/mod/visible-traders

本仓库仅作归档，整理与文档由 DeepSeek 辅助完成。
