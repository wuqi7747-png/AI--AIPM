# 商品图与产品资产系统｜CURRENT_STATE

状态：进行中
最后核对：2026-09-12

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
- 产品内部 owner：`PRODUCT.md / STATE.json` 为基础；`ASSETS.json / EVIDENCE.json / CONTENT.md` 按实际需要存在

## V2.1 当前能力

已经具备：
- Fast Path / Discovery Path；
- 系统级、产品根、产品内部资产分层唯一 owner；
- 动态分析数据按 task purpose 自动发现并读取当前结构/最新内容；
- 稳定视觉证据按 File ID + 版本指纹增量审阅，避免多窗口重复全量看图；
- `EVIDENCE.json` 按需记录审阅 scope、证据资格、锚点角色、冲突与 STALE 状态；
- Generation Gate 可先按 Evidence 筛出少量有效锚点，再实际打开原图进入 Sandbox；
- 已有索引时不重复扫描无关 Drive；
- 外部 Drive 变化定向对账；
- 多窗口写前刷新、写后确认、冲突不覆盖；
- 复杂跨系统操作的可恢复 operation ledger；
- 商品图、Listing、关键词、富内容共享稳定产品事实与最终策略；
- 产品/SKU 真实性隔离；
- 不为结构完整强制制造空白 owner 文件。

核心边界：

> **动态数据重新读取；稳定证据增量审阅。**

`EVIDENCE.json` 不替代真实原图。正式生图遇到高风险结构时，仍必须打开当前图所需真实锚点。

## 当前迁移/试点状态

- `MINI_RC_FORKLIFT_YELLOW`：V2.1 Evidence Layer 首个试点已启用。已创建 `EVIDENCE.json`，补齐原 `ASSETS.json` 中关键 `file_id:null` 证据的稳定 Drive File ID；当前审阅 scope 明确标为 PARTIAL，不把未审源资料冒充已审。
- `MAXSCIE_ROBOT_CAT_PINK / BLUE`：V2 ACTIVE；暂不为形式批量创建 Evidence owner。
- `AMPHIBIOUS_BG008_PINK / BLUE`：V2 ACTIVE。
- `AMPHIBIOUS_CV_B500_CYAN`：V2 ACTIVE，详细事实继续按 SKU 独立确认。
- `GECKO_GREEN`：V2 ACTIVE。
- `RC_CHAMELEON` 及近期补建产品：保持已有 V2 owner；Evidence 迁移待叉车试点验证后按实际工作需要推进，不批量造空文件。
- pre-V2 完整恢复点：两个 GitHub 仓库均有 `backup/pre-v2-2026-09-11`；Drive 有对应架构备份目录。

## 新窗口进入方式

### 已明确属于商品图/产品资产
直接走 Fast Path：
1. `ozon-WB/AGENTS.md`
2. `products/PRODUCTS.json`
3. 有本地产品目录则先读 `STATE.json`
4. 识别 task purpose：
   - 动态分析 → `ASSETS.json` 找数据源 → 读当前结构和相关最新内容；
   - 视觉真实性/商品图 → `PRODUCT.md + ASSETS.json + EVIDENCE.json(若存在)` → 只补审新增/变化/未审/冲突稳定证据；
5. 实际生图时再打开本图真正需要的真实锚点原图；
6. 索引/证据状态不足才扩大 Drive 读取范围。

### 项目归属不明确 / 跨项目
由 AIPM `PROJECT_INDEX.md` 路由，再进入执行仓库。

## AIPM 只维护
- 项目状态；
- 执行仓库与硬入口；
- 最大目标/边界；
- 跨项目依赖；
- 重大架构决策。

不维护具体 Folder/File ID、单张图片审阅记录、SKU 卖点/关键词或产品内部执行细节。

详细状态以 `ozon-WB` 最新 ACTIVE 文件为准。
