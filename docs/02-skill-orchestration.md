# Skills 编排与交接

> 本文概括写作任务中的工具职责、组合方式与交接流程；第三方 Skill 仅列公开来源，不复制其提示词正文。

## 编排原则

Skill 按职责分工，不是需要逐个启用的功能清单。先判断任务类型，再选择需要的环节。串接时明确每个环节的输入、输出和交接关系；多个工具对同一问题意见不同时，由负责整合的人依据事实、文体和任务要求作判断，不以简单投票掩盖分歧。

## 工具分工示例

### 写作与编辑

- **长文缺少素材**：先访谈和收集材料，再收敛结构并逐段成稿。可参考 [writing-fragments](https://github.com/yzsp-studio/writing-fragments)、[writing-shape](https://github.com/yuncang123/writing-shape)；需要逐步探索叙事方向时，可参考 [writing-beats](https://github.com/mattpocock/skills/tree/main/skills/in-progress/writing-beats)。
- **修改现有文章**：按标题和信息依赖拆分，逐节修改，不必整篇推倒重写。
- **结构化文档**：按背景收集、分节打磨和读者测试分阶段协作，可参考 [doc-coauthoring](https://github.com/anthropics/skills/tree/main/skills/doc-coauthoring)。
- **内部沟通**：先判定沟通类型，再按对应格式指南起草；可参考 [Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/internal-comms) 或 [MextAI/internal-comms](https://github.com/MextAI/internal-comms)。
- **需求与工程任务**：先整理需求，再拆成可执行的独立 issue；可参考 [mattpocock/skills](https://github.com/mattpocock/skills)。

### 成稿后的风格处理

- **AI 文风检查**：先报告候选问题和依据，再确认是否修改，改后复测。可参考 [lieflat-less-ai-tone](https://github.com/Xiangson/lieflat-less-ai-tone)。
- **第二遍语言检查**：可参考 [Humanizer-zh](https://github.com/op7418/Humanizer-zh)，不覆盖前一步的审阅结论或作者明确要求保留的内容。
- **局部润色或压缩**：按任务需要选择合适工具，不默认将全文改成同一种句式或长度。

### 文件格式与专门任务

- **Word**：精细编辑可参考 [docx](https://github.com/anthropics/skills/tree/main/skills/docx)；批量格式化可参考 [Word-Skill](https://github.com/ni1o1/claude-skill-docx-batch)。
- **PPT**：修改现有演示文稿可参考 [pptx](https://github.com/anthropics/skills/tree/main/skills/pptx)；新建或大幅重构可参考 [ppt-master](https://github.com/hugohe3/ppt-master)。
- **品牌视觉**：需要时参考 [brand-guidelines](https://github.com/anthropics/skills/tree/main/skills/brand-guidelines)。
- **PDF 与表格**：按文件类型选择相应工具；若工具会将文件发送到第三方服务，使用前确认数据处理方式符合任务要求。

## 不可用时的替代路径

如果适用工具不可调用或无法完成目标，不声称已经调用；按其负责的环节手动完成，或与用户确认是否暂停。涉及第三方服务、用户资料或外部写入时，先确认权限与数据边界。
