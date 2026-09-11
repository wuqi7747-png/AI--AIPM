# 商品图与产品资产系统｜ASSET_INDEX

## 权威入口

| 资产/规则 | 用途 | 位置 | 可信等级 |
|---|---|---|---|
| `ASSET_STORAGE_STRUCTURE.md` | 通用产品资产目录规范 | `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/ASSET_STORAGE_STRUCTURE.md` | ACTIVE规则 |
| `GOOGLE_DRIVE_ASSET_MAP.md` | 当前 Google Drive Folder/File ID 实例映射 | `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/GOOGLE_DRIVE_ASSET_MAP.md` | ACTIVE实例映射 |
| `00_系统入口索引` | Drive 侧跨窗口入口 | Google Drive File ID `1whrfRjFqWkKhkQ5tzrYQ4reDQOlZbahVdfcCtAsebzE` | Drive入口镜像 |
| `00_产品资产总索引` | 当前产品族、颜色/SKU总索引 | Google Drive File ID `1YxmZ4MA_B0gmS3M7HAN85VfgE4z3JFR44eh2JwLciwA` | Drive当前索引 |
| `AI商品图与内容资产系统` | 图片/PSD/关键词/富内容等实际文件 | Google Drive Folder ID `17-kvGSAWPalNTIxew9FUVuRUv34xuTXf` | 实际资产库 |

## 读取顺序

涉及商品图/产品资产的跨窗口任务：
1. 先读 AIPM `CURRENT_STATE.md` 确认项目当前状态；
2. 再读 `ozon-WB` ACTIVE 商品图技能与 `ASSET_STORAGE_STRUCTURE.md`；
3. 用 `GOOGLE_DRIVE_ASSET_MAP.md` 获取真实 Folder ID；
4. 进入对应颜色/SKU的 Drive 目录读取实际资产。

具体 Folder ID 不在 AIPM 重复维护，以 `GOOGLE_DRIVE_ASSET_MAP.md` 为唯一 GitHub 映射源。
