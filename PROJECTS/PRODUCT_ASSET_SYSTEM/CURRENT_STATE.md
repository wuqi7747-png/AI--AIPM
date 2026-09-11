# 商品图与产品资产系统｜CURRENT_STATE

状态：进行中
最后核对：2026-09-11

## 项目级摘要

该项目是长期商品内容资产系统。AIPM 只负责路由和项目级状态；详细 ACTIVE 状态由执行仓库维护。

### 执行面
- 仓库：`wuqi7747-png/ozon-WB`
- 硬入口：`AGENTS.md`
- 通用核心：`.agents/skills/ecommerce-image-core/`
- 玩具插件：`.agents/skills/ozon-wb-toy-image-sop/`

### 数据/资产面
- Google Drive：`AI商品图与内容资产系统`
- 系统一级入口：执行仓库 `GOOGLE_DRIVE_ASSET_MAP.md`
- 产品注册与产品根入口：执行仓库 `products/PRODUCTS.json`
- V2 产品内部状态：产品 `PRODUCT.md / ASSETS.json / STATE.json / CONTENT.md`

## V2 当前能力

已经具备：
- Fast Path / Discovery Path；
- 产品级单一 owner，减少重复索引；
- 已有索引时不重复扫描 Drive；
- 外部 Drive 变化增量扫描与产品路由；
- 多窗口写前刷新、写后确认、冲突不覆盖；
- 复杂跨系统操作的可恢复 operation ledger；
- 商品图、Listing、关键词、富内容共享同一事实与内容策略；
- 产品/SKU 真实性隔离。

`manifests/ASSET_MANIFEST.json` 已降级为 LEGACY_READONLY，仅给尚未迁移产品兜底；不再作为每次资产变化的共享写热点。

## 当前迁移状态

- `MINI_RC_FORKLIFT_YELLOW` 已完成首个 V2 实际迁移并清除主分支 V1 并行索引。
- 其他已注册玩具保留原 Drive 资产，不要求一次性全盘重建；在实际使用/变化时按需迁移到 V2。
- pre-V2 完整恢复点：两个 GitHub 仓库均有 `backup/pre-v2-2026-09-11`；Drive 有对应架构备份目录。

## 新窗口进入方式

### 已明确属于商品图/产品资产
直接走 Fast Path：
1. `ozon-WB/AGENTS.md`
2. `products/PRODUCTS.json`
3. 当前产品 `STATE.json`
4. 根据任务只读需要的产品 owner

### 项目归属不明确 / 跨项目
由 AIPM `PROJECT_INDEX.md` 路由，再进入执行仓库。

## AIPM 只维护

- 项目状态；
- 执行仓库与硬入口；
- 最大目标/边界；
- 跨项目依赖；
- 重大架构决策。

不维护：
- 具体 Folder/File ID；
- 某张图片当前版本；
- 具体 SKU 卖点/关键词；
- 产品内部文件结构和执行细节。

详细状态以 `ozon-WB` 最新 ACTIVE 文件为准。
