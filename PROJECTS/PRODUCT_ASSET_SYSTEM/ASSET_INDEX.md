# 商品图与产品资产系统｜ASSET_INDEX

## 权威入口

| 资产/规则 | 用途 | 位置 | 可信等级 |
|---|---|---|---|
| `ASSET_STORAGE_STRUCTURE.md` | 通用产品资产目录规范 | `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/ASSET_STORAGE_STRUCTURE.md` | ACTIVE规则 |
| `GOOGLE_DRIVE_ASSET_MAP.md` | 当前 Google Drive Folder/File ID 实例映射 | `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/GOOGLE_DRIVE_ASSET_MAP.md` | ACTIVE实例映射 |
| `00_系统入口索引` | Drive 侧跨窗口入口 | Google Drive File ID `1whrfRjFqWkKhkQ5tzrYQ4reDQOlZbahVdfcCtAsebzE` | Drive入口镜像 |
| `00_产品资产总索引` | 当前产品族、颜色/SKU总索引 | Google Drive File ID `1YxmZ4MA_B0gmS3M7HAN85VfgE4z3JFR44eh2JwLciwA` | Drive当前索引 |
| `AI商品图与内容资产系统` | 图片/PSD/关键词/富内容等实际文件 | Google Drive Folder ID `17-kvGSAWPalNTIxew9FUVuRUv34xuTXf` | 实际资产库 |

## 本地测品目录同步状态

已根据本地工作目录补建以下产品入口，前置数字编号已忽略：
- 福特车
- 壁虎橙色
- 恐龙
- 机器人
- 英文版GT赛车电商图
- 越野车详情页（源文件）

以上均已按当前标准结构建立，并已同步到 Drive `00_产品资产总索引` 与 `ozon-WB` 的 `GOOGLE_DRIVE_ASSET_MAP.md`。具体 Folder ID 只在 `GOOGLE_DRIVE_ASSET_MAP.md` 维护，避免 AIPM 与技能仓库形成双映射源。

其中 `壁虎橙色` 是否与现有绿壁虎属于同一型号/颜色族、`机器人` 是否与现有 MAXSCIE 机器人猫有关，目前都保持“待确认”，不自动合并。

## 读取顺序

涉及商品图/产品资产的跨窗口任务：
1. 先读 AIPM `CURRENT_STATE.md` 确认项目当前状态；
2. 再读 `ozon-WB` ACTIVE 商品图技能与 `ASSET_STORAGE_STRUCTURE.md`；
3. 用 `GOOGLE_DRIVE_ASSET_MAP.md` 获取真实 Folder ID；
4. 进入对应颜色/SKU的 Drive 目录读取实际资产。

具体 Folder ID 不在 AIPM 重复维护，以 `GOOGLE_DRIVE_ASSET_MAP.md` 为唯一 GitHub 映射源。
