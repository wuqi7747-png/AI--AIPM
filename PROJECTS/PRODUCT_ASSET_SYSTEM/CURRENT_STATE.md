# 商品图与产品资产系统｜CURRENT_STATE

## 状态

进行中，当前目录规范已统一到 2026-09-11 版本。

## 当前核心规则

1. 单个实际颜色/SKU标准目录：
   - `01_产品锚点`
   - `02_源资料_展开`
   - `03_详情图`（含 `00_已确认卖点`；主图与详情图不再拆分）
   - `04_富内容`
   - `05_待确认图`
   - `06_季节_节日版本`
   - `07_PSD_源文件`
   - `08_关键词`
   - `99_归档压缩包`
2. `08_关键词` 固定两个文件：
   - `01_当前标题_描述_标签词`
   - `02_我方与竞品搜索关键词`
3. 两个关键词文件统一按四店固定槽位组织：
   - `Ozon17`
   - `Ozon24`
   - `WB维里迪安`
   - `WB白俄主体`
4. `01_当前标题_描述_标签词` 固定四个店铺段落；每段保存该店实际使用中的 SKU、链接、标题、描述、标签词/搜索词和更新时间。
5. `02_我方与竞品搜索关键词` 固定四个子表：`01_Ozon17` / `02_Ozon24` / `03_WB维里迪安` / `04_WB白俄主体`；每个子表内部通过“来源类型”区分我方与竞品。
6. 固定四店结构不表示商品必须上架四店。实际未上架的店铺对应段落/子表直接留空，不伪造数据。
7. 多颜色商品建立产品族父目录，各颜色/SKU资产完全分开。
8. 不保留“旧结构归档”作为当前资产层；废弃旧事实直接从当前结构移除。

## 当前多颜色产品族

- MAXSCIE机器人猫：粉色 `YKJQM-DXPK` / 蓝色 `YKJQM-DXBL`
- 两栖遥控车：粉色 BG008 `YKCLW-DXPK` / 蓝色 BG008 `YKCLW-DXBL` / 青色 CV-B500 `YKCLQ-DXCY`

## 跨窗口入口

开始相关任务时优先读取：
1. `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/ASSET_STORAGE_STRUCTURE.md`
2. `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/GOOGLE_DRIVE_ASSET_MAP.md`
3. Google Drive `00_系统入口索引`
4. Google Drive `00_产品资产总索引`

不要从本文件复制具体 Folder ID；当前实际 ID 以 `GOOGLE_DRIVE_ASSET_MAP.md` 为准。
