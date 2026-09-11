# 项目索引 / Routing Registry

状态：ACTIVE

本文件是 AIPM 的轻量项目注册表。只负责**路由**，不复制项目内部详细状态。

## 当前项目

| Project ID | 项目 | 典型触发词 / 别名 | 状态 | 执行仓库 / 位置 | 硬入口 | 项目级状态 |
|---|---|---|---|---|---|---|
| `PRODUCT_ASSET_SYSTEM` | 商品图与产品资产系统 | 商品图、主图、详情图、富内容、关键词、卖点、Listing、Ozon/WB、玩具图、Drive产品资产 | 进行中 | `wuqi7747-png/ozon-WB` | `AGENTS.md` | `PROJECTS/PRODUCT_ASSET_SYSTEM/CURRENT_STATE.md` |
| `VF520` | VF520 完整商品项目 | VF520、投影仪、V53、D3100、D3101、MTK9269 | 暂停 | `PROJECTS/VF520/` | 项目目录内状态/入口 | `PROJECTS/VF520/CURRENT_STATE.md` |
| `2026-09_MONTHLY_OPERATIONS` | 2026-09 月度运营规划 | 月度计划、采购节点、8款测品、中秋前作图、到货计划、运营安排 | 进行中 | `PROJECTS/2026-09_MONTHLY_OPERATIONS/` | 项目目录内状态/入口 | `PROJECTS/2026-09_MONTHLY_OPERATIONS/CURRENT_STATE.md` |

## 路由原则

### 1. 明确任务：Fast Path

如果用户已经明确说出具体产品/项目，且上表能唯一映射：
- 直接进入执行仓库/项目硬入口；
- 不必先读取所有 AIPM 文件。

例如：
- “继续叉车富内容” → `PRODUCT_ASSET_SYSTEM` → `ozon-WB/AGENTS.md`
- “继续 VF520” → `VF520`

### 2. 模糊 / 跨项目：Discovery Path

以下情况先读 AIPM：
- 只说“继续之前那个”；
- 同时涉及商品图、采购、月度计划等多个项目；
- 不知道当前入口；
- 需要做跨项目优先级或依赖判断。

流程：
`PROJECT_INDEX → 项目 CURRENT_STATE → 执行仓库硬入口 → 最小必要上下文`

### 3. 不确定时不要瞎猜

如果多个项目都可能匹配：
- 优先利用用户话语中的具体产品名、仓库名、任务类型判断；
- 仍无法唯一判断时再问一个最小澄清问题；
- 不通过全量扫描所有仓库来“猜”。

## 项目登记字段

新项目至少登记：
- `Project ID`
- 项目名称
- 典型触发词/别名
- 状态
- 执行仓库/位置
- 硬入口
- 项目级状态文件

只有跨项目路由真正需要的字段才进本表。Folder ID、产品 SKU、图片版本等细节留在执行仓库。

## 事实源规则

- AIPM：项目级路由、状态、边界、跨项目依赖。
- 执行仓库：项目内部最新 ACTIVE 状态和规则。
- Drive/API：实际资产和实时数据。

如果本表与执行仓库入口冲突，以执行仓库最新 ACTIVE 状态为准，并在影响路由时修正本表。
