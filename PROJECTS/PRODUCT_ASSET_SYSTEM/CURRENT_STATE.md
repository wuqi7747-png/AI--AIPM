# 商品图与产品资产系统｜CURRENT_STATE

状态：进行中
最后核对：2026-09-11

## 项目级摘要

该项目已经从“单次作图流程”升级为长期商品内容资产系统，当前由独立执行仓库维护详细 ACTIVE 状态。

### 执行面
- 仓库：`wuqi7747-png/ozon-WB`
- 硬入口：`AGENTS.md`
- 通用核心：`.agents/skills/ecommerce-image-core/`
- 玩具插件：`.agents/skills/ozon-wb-toy-image-sop/`

### 资产面
- Google Drive：`AI商品图与内容资产系统`
- 当前 Drive 实例位置、Folder/File ID：只认执行仓库 `GOOGLE_DRIVE_ASSET_MAP.md`
- 跨产品语义索引：执行仓库 `manifests/ASSET_MANIFEST.json`

## 当前能力状态

已经具备：
- 商品图通用规则 + 玩具类目插件；
- 产品事实 / 证据 / 输出索引；
- 主图、详情图、富内容、Listing、关键词、卖点联动；
- 内容覆盖治理，避免机械重复；
- Google Drive 标准结构与颜色/SKU拆分；
- Drive 语义 Manifest 与外部变化待索引机制；
- 新窗口/新 Agent 硬入口 `AGENTS.md`；
- Drive 长期变更后的语义回写规则。

## 当前阶段重点

- 用真实产品继续验证“规则 → 内容策略 → 内容覆盖 → 输出”的联动；
- 富内容进入实际项目验证阶段；
- 继续控制 GitHub / Drive 双方不要形成重复事实源；
- 规则和资产变化优先增量维护，不全量重扫。

## 新窗口进入方式

### 已明确属于商品图/产品资产
直接走 Fast Path：
1. `wuqi7747-png/ozon-WB/AGENTS.md`
2. 按任务读取最小必要上下文
3. 再进入对应产品/Drive 实际资产

无需为了流程完整先读取本文件全部历史。

### 项目归属不明确 / 跨项目
先由 AIPM `PROJECT_INDEX.md` 路由，再进入本项目。

## AIPM 只维护的内容

本文件只保留：
- 项目是否进行中；
- 当前最大阶段；
- 执行仓库/硬入口；
- 跨项目层面能力与风险；
- 重大架构变化。

以下内容不在 AIPM 重复维护：
- Folder ID / File ID 明细；
- 具体产品当前图片版本；
- 具体 SKU 卖点/关键词；
- 执行仓库内部目录细节。

详细状态始终以 `ozon-WB` 最新 ACTIVE 文件为准。
