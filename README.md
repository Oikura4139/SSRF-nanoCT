# 上海光源纳米 CT 资料包

更新时间：2026-07-23

## 目录结构

- `01_核心论文PDF/`：上海光源主导的硬 X nano-CT 核心论文，以及 BL08U1A 代表性软 X nano-CT 论文。
- `02_支撑文献PDF/`：聚光光学、焦堆栈、软 X PXCT、两角立体成像等支撑/邻接文献。
- `03_专利PDF/`：公开相关专利影像。
- `04_深读笔记/`：13 篇 DeepPaperNote 最终笔记、逐篇图片目录与总索引。
- `05_证据与流水线/`：每篇论文的 metadata、source manifest、raw sections、evidence、figure decisions、synthesis bundle、note plan 与 grounding lint。
- `文献与专利台账.md`：纳入、未取得全文、专利、平台用户成果和排除项。
- `上海光源纳米CT_现状与路线图_2026-07.md`：现状判断、国内外对比、短中长期路线、优先级与验收目标。
- `交付审计_2026-07-23.md`：PDF、笔记、lint、终审、图片和保存路径的总审计。

## 当前完成度

- 论文全文 PDF：13 篇，均已通过 PDF 可读性和全文提取校验。
- 专利 PDF：11 件，均已通过 PDF 文件格式/页数校验。
- 论文证据流水线：13 篇均已建立完整 source manifest、raw sections、evidence、assets、figure decisions 与 synthesis bundle。
- DeepPaperNote：13/13 篇均已完成最终 Markdown，具有规定的 12 个一级章节和机制流程；六项 lint gate 全部通过。
- 终审：13 份 Final Quality Review 与 13 份 Final Readability Review 均通过。
- 图片：48 项 `insert` 决策均经人工视觉核验、物化并被正文引用；污染、截断或身份不完整的候选均降级为具体占位或拒绝。
- 保存：13/13 篇均由 DeepPaperNote writer 写入顶层 `04_深读笔记/<stem>/`，草稿与正式笔记内容一致。

## 笔记与审计入口

- `04_深读笔记/索引.md`：按硬 X 主线、软 X/相干路线和算法/邻接能力组织的逐篇入口。
- `交付审计_2026-07-23.md`：13 篇笔记、48 幅图、26 份终审记录和 24 个 PDF 的核验结果。
- `05_证据与流水线/<stem>/`：逐篇 source manifest、原文分段、证据包、note plan、lint、双终审和 writer 状态。
- 另有 12 篇相关文献因付费墙或 WAF 未能合法取得全文，只列入台账，不伪装为 PDF，也不生成摘要级成品深读笔记。

## 重要口径

- BL18B 官方“20 nm”是二维 TXM 指标，不是已验收的 20 nm 三维 CT。
- 公开的 BL18B 三维实证主要为约 50–100 nm。
- BL08U1A 在 2022 年已有软 X PXCT 实证，但为 22 个有限角投影、小区域数据，三维分辨率约 22.8 nm（横向）/64.6 nm（轴向）。
- 焦堆栈和两角立体成像属于三维邻接能力，不是投影 CT。
- 使用 BL18B 的用户论文证明平台服务能力，但不应全部归为上海光源自主仪器或方法成果。
