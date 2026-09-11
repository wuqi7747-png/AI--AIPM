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
- 系统根/一级入口唯一 owner：执行仓库 `GOOGLE_DRIVE_ASSET_MAP.md`
- 产品根 Folder ID 唯一 owner：执行仓库 `products/PRODUCTS.json`
- 产品内部长期状态：`PRODUCT.md / STATE.json` 为基础 owner；`ASSETS.json / CONTENT.md` 按实际需要存在

## V2 当前能力

已经具备：
- Fast Path / Discovery Path；
- 系统级、产品根、产品内部资产分层唯一 owner；
- 已有索引时不重复扫描 Drive；
- 外部 Drive 变化增量扫描与产品路由；
- 多窗口写前刷新、写后确认、冲突不覆盖；
- 复杂跨系统操作的可恢复 operation ledger；
- 商品图、Listing、关键词、富内容共享稳定产品事实与最终策略；
- 产品/SKU 真实性隔离；
- 不为结构完整强制制造空白 owner 文件。

旧全局人工 `manifests/ASSET_MANIFEST.json` 已从 `main` 删除；历史仍保留在 pre-V2 备份分支。当前 `manifests/` 只承担 Drive 增量变化检测和待处理队列，不再保存长期产品语义。

## 当前迁移状态

- `MINI_RC_FORKLIFT_YELLOW`：V2 ACTIVE，已清除产品根 ID 双记账。
- `MAXSCIE_ROBOT_CAT_PINK / BLUE`：V2 ACTIVE。
- `AMPHIBIOUS_BG008_PINK / BLUE`：V2 ACTIVE。
- `AMPHIBIOUS_CV_B500_CYAN`：V2 ACTIVE，详细事实继续按 SKU 独立确认。
- `GECKO_GREEN`：V2 ACTIVE。
- `RC_CHAMELEON`：仅完成产品根注册；没有长期内部语义时不预建空 owner。
- 其他未解析目录保持 `UNRESOLVED`，不为了迁移而全盘扫描。
- pre-V2 完整恢复点：两个 GitHub 仓库均有 `backup/pre-v2-2026-09-11`；Drive 有对应架构备份目录。

## 新窗口进入方式

### 已明确属于商品图/产品资产
直接走 Fast Path：
1. `ozon-WB/AGENTS.md`
2. `products/PRODUCTS.json`
3. 有本地产品目录则先读 `STATE.json`
4. 根据任务只读需要的 owner
5. 索引不足才打开具体 Drive 原件

### 项目归属不明确 / 跨项目
由 AIPM `PROJECT_INDEX.md` 路由，再进入执行仓库。

## AIPM 只维护
- 项目状态；
- 执行仓库与硬入口；
- 最大目标/边界；
- 跨项目依赖；
- 重大架构决策。

不维护具体 Folder/File ID、图片版本、SKU 卖点/关键词或产品内部执行细节。

详细状态以 `ozon-WB` 最新 ACTIVE 文件为准。
