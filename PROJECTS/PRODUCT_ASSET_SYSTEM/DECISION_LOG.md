# 商品图与产品资产系统｜项目级架构决策

> AIPM 只保留项目级架构决策。产品目录、关键词表、图片索引、具体 Drive 结构等执行细节由 `wuqi7747-png/ozon-WB` 负责。pre-V2 详细历史保留在 `backup/pre-v2-2026-09-11`。

## A1｜Control / Execution / Data 三层分工
状态：ACTIVE
日期：2026-09-11

- AIPM = Control Plane：项目路由、项目状态、边界、跨项目依赖、重大架构决策。
- `ozon-WB` = Execution Plane：ACTIVE 规则、产品事实/状态/内容策略、资产语义、执行逻辑。
- Google Drive / API = Data Plane：真实图片、视频、表格、文档、PSD 和实时数据。

同一详细事实不得在 AIPM 与执行仓库长期双写。

## A2｜Fast Path / Discovery Path
状态：ACTIVE
日期：2026-09-11

- 用户已明确产品/项目 → 直接进入执行仓库硬入口，不强制扫描 AIPM。
- 任务模糊、跨项目、入口未知 → 先由 AIPM `PROJECT_INDEX.md` 路由。

目标：新窗口能找到正确项目，同时不为“流程完整”浪费上下文。

## A3｜产品资产 V2：产品分区单一 owner
状态：ACTIVE
日期：2026-09-11

执行仓库 V2 采用：
- `products/PRODUCTS.json`：低频产品注册表；
- 产品 `PRODUCT.md`：稳定事实/真实性边界；
- 产品 `ASSETS.json`：Drive 位置 + 长期资产语义；
- 产品 `STATE.json`：当前 checkpoint；
- 产品 `CONTENT.md`：最终内容策略/覆盖/输出方向。

普通产品资产变化不再同步多个平行索引，也不再写全局人工 Manifest。

`manifests/ASSET_MANIFEST.json` 降级为 `LEGACY_READONLY`，仅给未迁移旧产品兜底；所有产品完成迁移后删除。

该决策 supersedes 旧的“每次 Drive 变化同步 Drive Map + 产品多索引 + 全局 Manifest”的实现方式，但**不取消变化可传播、语义索引和跨窗口续接能力**。

## A4｜复杂持久化操作使用可恢复 operation ledger
状态：ACTIVE
日期：2026-09-11

跨 Drive + GitHub、多文件批量移动/替换、或中断可能造成状态不一致时，建立独立 operation：

`PLANNED -> DRIVE_DONE -> METADATA_DONE -> COMMITTED`

普通单文件变化不创建 ledger，避免治理本身变成负担。

## A5｜并发与单写原则
状态：ACTIVE
日期：2026-09-11

多窗口允许并发，但持久化必须：
- 写前刷新；
- 写后确认；
- 冲突不覆盖；
- 尽量按产品/文件分区写；
- 禁止把每个产品的高频变化集中进一个共享热点文件。

## A6｜架构验收标准
状态：ACTIVE
日期：2026-09-11

任何后续优化必须保持：
- 高效；
- 已有索引时不重复扫描；
- 多窗口不打架；
- 长期变化能被下一窗口直接知道；
- 单一事实源；
- 中断可恢复；
- 不依赖聊天记忆；
- 普通变化维护成本足够低。

如果新增结构不能明显改善这些指标，默认不新增。
