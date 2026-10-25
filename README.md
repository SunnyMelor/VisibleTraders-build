# Visible Traders — 1.21.1 归档版

**Visible Traders 1.3.2（Minecraft 1.21.1 / Fabric）的归档与说明**

> 本仓库为**原版制品的重新打包归档**，模组代码**未做任何修改**。
> 原作者：**Ramixin** ｜ 许可证：**MIT**

---

## 1. 上游项目

| 项 | 内容 |
| --- | --- |
| 模组名称 | Visible Traders |
| 作者 | **Ramixin** |
| 源仓库 | https://github.com/Ramixin/VisibleTraders |
| 下载页 | https://modrinth.com/mod/visible-traders |
| 许可证 | **MIT**（允许再分发，需保留版权声明） |
| 本仓库版本 | `1.3.2` |
| 适配游戏版本 | Minecraft 1.21.1 |

**本仓库不含任何 Visible Traders 的源代码。**
`dist/VisibleTraders-1.3.2.jar` 与上游 Modrinth 发布物**逐字节一致**（见下方校验值）。

---

## 2. 为什么会有这个仓库

Visible Traders 与 [Trade Cycling](https://github.com/henkelmax/trade-cycling) 同时安装时，曾在 Minecraft 1.21.1 上出现兼容性问题：

- 刷新村民交易后，**未解锁的交易会消失**
- 必须关闭交易界面再重新打开，才能重新预览

根因在于 **Trade Cycling 一侧的反射桥接调用了已在 Visible Traders 中重命名的方法**，Visible Traders 本身工作正常。

修复需要改的是 Trade Cycling，而不是 Visible Traders。因此本仓库**仅归档可正常工作的 1.3.2 原版制品**，方便配对使用与版本追溯。

> 详细根因分析见 [docs/compatibility.md](./docs/compatibility.md)

---

## 3. 文件

| 文件 | 大小 | SHA-256 |
| --- | --- | --- |
| `dist/VisibleTraders-1.3.2.jar` | 65,742 B | `39D70E06C8C39AF5575431CEDED4A14C662B6E2CCF530B65F4551789066E0F10` |

校验方式：

```powershell
Get-FileHash .\dist\VisibleTraders-1.3.2.jar -Algorithm SHA256
```

```bash
sha256sum dist/VisibleTraders-1.3.2.jar
```

> 该哈希与 Modrinth 官方发布物完全一致，可确认未经任何改动。

---

## 4. 安装

1. 安装 Minecraft **1.21.1** 与 **Fabric Loader**
2. 将 `VisibleTraders-1.3.2.jar` 放入 `mods/`
3. 需要 **Fabric API**

依赖（来自 `fabric.mod.json`）：

| 依赖 | 版本要求 |
| --- | --- |
| fabricloader | `>=0.18.4` |
| fabric-api | `>=0.116.7+1.21.1` |
| minecraft | `>=1.21.0` |
| java | `>=21` |

> 单人游戏即可生效；多人游戏中，交易数据由服务端生成，建议**服务端也安装**。

---

## 5. 功能说明

在原版村民交易界面中，额外显示**尚未解锁**的交易条目：

- 可以提前查看后续等级会出现的交易
- 已解锁与未解锁交易合并展示，无需反复升级试探
- 对刷新交易类模组提供兼容钩子

---

## 6. 与 Trade Cycling 搭配

| 组合 | 说明 |
| --- | --- |
| VT 1.3.2 + Trade Cycling 1.21.1-1.0.23 **原版** | ⚠️ 可能出现「刷新后未解锁交易消失」 |
| VT 1.3.2 + Trade Cycling **修复版** | ✅ 正常 |

修复版针对 VT 1.3.2 的 API 做了适配，详见 [docs/compatibility.md](./docs/compatibility.md)。

---

## 7. 版权声明

```
The MIT License (MIT)

Copyright (c) 2024 Ramixin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

- **Visible Traders** © 2024 **Ramixin**，MIT License
- **Minecraft** © Mojang Studios / Microsoft
- **Fabric Loader / Fabric API** © FabricMC

本仓库不包含上述任何专有资源。若原作者希望下架本仓库，请提 Issue，将立即处理。

---

## 8. 说明

本仓库的整理、文档撰写与兼容性分析由 **DeepSeek** 辅助完成。

模组本体未作任何代码修改，仅进行归档与重新打包。
