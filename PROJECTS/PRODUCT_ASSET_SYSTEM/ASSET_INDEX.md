# 商品图与产品资产系统｜ASSET_INDEX

状态：ACTIVE

本文件只保存**权威入口指针**。不重复维护具体 Folder ID、SKU、图片版本或 Drive 结构细节。

## 权威入口

| 入口 | 用途 | 权威级别 |
|---|---|---|
| `wuqi7747-png/ozon-WB/AGENTS.md` | 新窗口 / 新 Agent 硬入口 | PRIMARY ENTRY |
| `ozon-WB/.agents/skills/ecommerce-image-core/references/ASSET_STORAGE_STRUCTURE.md` | 通用资产结构规范 | ACTIVE RULE |
| `ozon-WB/.agents/skills/ecommerce-image-core/references/GOOGLE_DRIVE_ASSET_MAP.md` | 当前 Drive Folder/File ID 实例映射 | ACTIVE MAP |
| `ozon-WB/manifests/ASSET_MANIFEST.json` | 跨产品长期资产语义索引 | ACTIVE MANIFEST |
| `ozon-WB/products/.../CURRENT_STATUS.md` | 具体产品当前状态 | PRODUCT STATE |
| `ozon-WB/products/.../ASSET_INDEX.md` | 具体产品 Drive 实例与轻量语义索引 | PRODUCT MAP |
| Google Drive `AI商品图与内容资产系统` | 图片、PSD、关键词、富内容等实际资产 | DATA / ASSET SOURCE |

## 读取规则

### 明确商品图 / 产品资产任务
直接读取 `ozon-WB/AGENTS.md`，由执行仓库按最小必要上下文继续路由。

### 跨项目 / 项目归属不明确
先由 AIPM `PROJECT_INDEX.md` 确认项目，再进入 `ozon-WB/AGENTS.md`。

## 不在本文件维护

以下内容全部留在执行仓库或 Drive：
- Folder ID / File ID 明细；
- 产品族和颜色/SKU完整映射；
- 具体成品图版本；
- 关键词表内容；
- 已确认卖点全文；
- 单产品内部执行状态。

理由：避免 AIPM 与执行仓库形成双映射源和双事实源。
