# Visible Traders × Trade Cycling 兼容性说明

## 背景

在 Minecraft 1.21.1 / Fabric 下同时安装两个模组时出现以下问题：

1. 打开村民交易界面，未解锁交易可以正常预览
2. 点击「刷新交易」后，**未解锁交易全部消失**
3. 必须关闭界面再重新打开，未解锁交易才重新出现

## 结论

**问题不在 Visible Traders，而在 Trade Cycling 一侧。**

Trade Cycling 通过反射调用 Visible Traders 的内部方法，但调用的是**已被重命名的旧方法名**。
`init()` 捕获异常后把反射用的 `Method` 字段置为 `null`，导致：

- 「重新生成锁定交易」变成空操作
- 「带上锁定交易发送」失败，退化为只发送普通交易

于是刷新后客户端只收到普通交易包，而 Visible Traders 的合并列表仍是旧快照，
直到重新打开界面（触发 Visible Traders 的 `openTradingScreen` 钩子）才刷新。

## 方法名对照

| Trade Cycling 期望 | Visible Traders 1.3.2 实际 |
| --- | --- |
| `visibleTraders$forceTradeGeneration()` | `visibleTrades$regenerateTrades()` |
| `visibleTraders$wrapAndSendMerchantOffers(...)` | `visibleTraders$getCombinedOffers()` + `visibleTraders$getShiftedLevel()` |

修复方式是在 Trade Cycling 侧改为调用新的方法名，并保留旧名回退以兼容更早版本。

## 关于本仓库

Visible Traders 1.3.2 **无需任何修改**。
本仓库仅归档该版本制品，便于与修复版 Trade Cycling 配对使用。
