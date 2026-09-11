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
3. `01_当前标题_描述_标签词` 仍按四店固定槽位保存：`Ozon17` / `Ozon24` / `WB维里迪安` / `WB白俄主体`。未上架店铺对应段落留空。
4. Ozon17 / Ozon24 的文档段不再重复保存 SKU 和商品链接；这些信息随 Ozon 关键词原始数据保存。WB 两店仍可保存 SKU / 链接。
5. `02_我方与竞品搜索关键词` 的目标结构改为五个子表：
   - `01_Ozon17`
   - `02_Ozon24`
   - `03_竞品1`
   - `04_竞品2`
   - `05_竞品3`
6. 五个关键词子表不预设自定义表头。用户直接把 Ozon 原始导出/复制的数据整块粘贴进去，保留平台原始表头、SKU、链接和指标。
7. WB 不单独维护关键词子表。关键词研究主要以 Ozon 为数据源，因为数据更方便、可获得性更好；Ozon 关键词可用于 WB Listing。
8. 关键词资产不是单纯 SEO 表：它同时服务于 Listing 标题/描述调整、商品图卖点决策、以及后续 VK 帖子/视频内容选题。
9. 多颜色商品建立产品族父目录，各颜色/SKU资产完全分开。
10. 不保留“旧结构归档”作为当前资产层；废弃旧事实直接从当前结构移除。

## 本地 Google Drive 自动化能力

2026-09-11 已完成本地 Google Workspace API 联通：

- Google Drive API：可用
- Google Sheets API：可用
- Google Docs API：可用
- OAuth Desktop App：已授权
- `token.json`：已生成并可复用，仅保存在用户本地
- 当前访问 Google API 需要代理：`http://127.0.0.1:7897`
- Python / `googleapiclient` 通过显式 `httplib2.ProxyInfo` + `AuthorizedHttp` 已验证可正常连接

认证材料不得提交到 GitHub。详细选择规则见：
`wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/LOCAL_DRIVE_AUTOMATION.md`

执行原则：
- 日常少量、内容型 Drive 修改：优先直接用 ChatGPT/Drive 连接器；
- 大量、机械、结构性批处理：优先考虑本地脚本；
- 但不机械强制使用脚本，如果脚本调试成本高于直接修改，应直接改 Drive；
- 本地脚本执行后应靠日志和自检，不要求 ChatGPT 再逐项全盘复查。

## 当前迁移状态

关键词目标结构已经确定，但 Google Drive 中此前建立的“四店关键词子表”结构尚未确认已全部迁移到新的“五子表 Ozon/竞品结构”。后续执行时先读 `GOOGLE_DRIVE_ASSET_MAP.md` 核对当前实际结构，不要把目标结构当成已经完成的 Drive 事实。

## 当前多颜色产品族

- MAXSCIE机器人猫：粉色 `YKJQM-DXPK` / 蓝色 `YKJQM-DXBL`
- 两栖遥控车：粉色 BG008 `YKCLW-DXPK` / 蓝色 BG008 `YKCLW-DXBL` / 青色 CV-B500 `YKCLQ-DXCY`

## 跨窗口入口

开始相关任务时优先读取：
1. `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/ASSET_STORAGE_STRUCTURE.md`
2. `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/GOOGLE_DRIVE_ASSET_MAP.md`
3. `wuqi7747-png/ozon-WB/.agents/skills/ecommerce-image-core/references/LOCAL_DRIVE_AUTOMATION.md`
4. Google Drive `00_系统入口索引`
5. Google Drive `00_产品资产总索引`

不要从本文件复制具体 Folder ID；当前实际 ID 以 `GOOGLE_DRIVE_ASSET_MAP.md` 为准。
