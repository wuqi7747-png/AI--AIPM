# 商品图与产品资产系统｜DECISION_LOG

## 2026-09-11

### D1｜主图与详情图合并
决定：取消单独主图目录；所有用户确认可用的商品图统一放入 `03_详情图`。

### D2｜新增富内容目录
决定：每个实际颜色/SKU增加 `04_富内容`。

### D3｜关键词资产标准化
决定：每个商品增加 `08_关键词`，其中固定保存当前标题/描述/标签词文档，以及我方与竞品搜索关键词表。

### D4｜确认卖点进入商品目录
决定：`03_详情图/00_已确认卖点` 为产品当前已确认卖点的 Drive 事实文件。用户确认或可靠证据核实后才写入；GitHub不复制具体产品卖点全文。

### D5｜多颜色按颜色/SKU拆分
决定：机器猫按粉/蓝拆分；两栖遥控车统一产品族下按粉 BG008、蓝 BG008、青 CV-B500 三色拆分。父目录只负责分组。

### D6｜不保留旧结构归档
决定：废弃的共用目录/旧事实结构直接从当前资产体系清理，不以“旧结构归档”长期保留，防止其他窗口读取错误事实源。

### D7｜映射同步是变更完成条件
决定：Drive 结构变化必须同任务更新 `ozon-WB` 的 `GOOGLE_DRIVE_ASSET_MAP.md`，并同步 Drive 入口索引/产品总索引；否则变更不算完整。

### D8｜关键词数据源改为 Ozon 主导
决定：`02_我方与竞品搜索关键词` 不再按四店拆分。WB 不单独维护关键词表，关键词研究主要使用 Ozon17 / Ozon24 以及 Ozon 竞品数据，因为 Ozon 数据获取和搜索词表现数据更方便。Ozon 关键词研究结果可用于 WB Listing。

目标五子表：`01_Ozon17` / `02_Ozon24` / `03_竞品1` / `04_竞品2` / `05_竞品3`。所有子表不预设自定义表头，直接粘贴平台原始 Ozon 结构数据；三个竞品表默认空白。

### D9｜Ozon Listing 文档去重
决定：`01_当前标题_描述_标签词` 仍保留 Ozon17、Ozon24、WB维里迪安、WB白俄主体四个店铺槽位；但 Ozon17 / Ozon24 不再重复保存 SKU 和商品链接，因为这些信息已随 Ozon 关键词原始数据保存。WB 两店可继续保留 SKU / 链接。

### D10｜关键词资产作为多下游共享输入
决定：关键词表不是单纯 SEO 数据。它同时作为：
1. Listing 标题/描述优化输入；
2. 商品图卖点排序与文案输入；
3. VK 帖子、视频、选题与市场语言输入。

### D11｜本地脚本与直接 Drive 操作采用动态选择
决定：不固定“所有 Drive 操作都用脚本”或“所有操作都直接用连接器”。

- 日常少量、内容型修改：优先直接用 ChatGPT/Google Drive 连接器；
- 大量、机械、结构性批量修改：优先考虑本地脚本；
- 若脚本的调试、依赖、网络排错成本高于直接修改，则直接操作 Drive；
- 本地脚本执行后依赖日志/自检，只处理异常，避免 ChatGPT 再逐文件全量复查。

### D12｜本地 Google Workspace API 已具备可复用能力
决定：保留当前已联通的本地 Google Drive / Sheets / Docs API 环境，作为后续批处理备用能力。

- OAuth Desktop App 已完成授权；
- 本地 `token.json` 已可复用；
- 当前 Google API 代理为 `http://127.0.0.1:7897`；
- 对 `googleapiclient` / `httplib2`，已验证显式 `ProxyInfo` + `AuthorizedHttp` 可正常连接；
- 认证材料只留用户本地，绝不提交 GitHub。

详细执行规则见 `ozon-WB/.agents/skills/ecommerce-image-core/references/LOCAL_DRIVE_AUTOMATION.md`。

### D13｜任何长期 Drive 变更必须留下语义回写
决定：只要对 Drive 做了会长期保留的新增、修改、替换、移动、重命名或删除，同一任务必须在 GitHub 或 Drive 的合适索引/状态文件中留下语义记录；禁止“只改 Drive，不留记录”。

这条规则的目的不是复制资产本体，而是让新窗口无需重新逐个打开/扫描文件，就能知道：
- 变更了什么；
- 资产在哪里；
- 图片/视频/文件主要讲什么或证明什么；
- 用途和当前状态；
- 必要时的替代关系。

记录位置按类型选择：
- 路径/结构变化 → `GOOGLE_DRIVE_ASSET_MAP.md` + 对应产品 `ASSET_INDEX.md`；
- 正式图片/视频/富内容 → `ASSET_INDEX.md` 或 `OUTPUT_INDEX.md`；
- 锚点/源资料/证据 → `EVIDENCE_INDEX.md` 或 `ASSET_INDEX.md`；
- 关键词/Listing/卖点 → Drive 保留完整内容，同时在 `COPY_ALIGNMENT / CURRENT_STATUS / ASSET_INDEX` 或等价索引中保存轻量摘要与覆盖状态；
- 真正一次性的失败稿/临时过程文件可不进入长期索引。

完成标准改为：**Drive 修改完成 + 语义回写完成，任务才算真正完成。**

### D14｜AIPM 改为 Control Plane，ozon-WB 为 Execution Plane
决定：AIPM 不再复制商品图系统内部详细结构和状态，而只负责项目级路由、状态、边界、跨项目依赖与重大决策。

- AIPM = Control Plane：判断“这是哪个项目、入口在哪里、项目是否进行中”。
- `ozon-WB` = Execution Plane：维护商品图 ACTIVE 规则、产品状态、Manifest、Drive 映射和执行逻辑。
- Google Drive / API = Data Plane：保存实际资产和数据。

启动采用双路径：
- **Fast Path**：用户已明确产品/项目时，直接进入执行仓库 `AGENTS.md`，不强制绕 AIPM。
- **Discovery Path**：任务模糊、跨项目或入口未知时，先由 AIPM `PROJECT_INDEX.md` 路由。

该决策的目的：减少重复上下文、双重记账和跨仓库状态漂移，同时保留新窗口自动找到正确项目的能力。
