# Skills 编排与交接

> 本文只记录实际采用的工具分工与调用流程；第三方 Skill 只做来源引用，不复制其提示词正文。

## 编排原则

Skill 是按职责分工的模块，不是需要逐个打开的功能清单。先判断任务类型，再选真正需要的环节。串接时交代输入、输出和交接关系；多个 Skill 对同一问题意见不同时，由人依据事实、文体和用户要求作判断。这里采用的是**任务路由与分工流水线**，不称为 bagging，也不把结果简单投票。

调用某个 Skill 不代表它的全部提示词属于本项目。本文只写本人的路由方法和用途；第三方 Skill 仅列名称及来源链接，不复刻正文、示例或内部检查清单。

## 已使用的 Skills

### 写作与编辑主线

- **长文没有素材：`writing-fragments` → `writing-shape`。** 前者访谈并收集素材，先不定结构；后者从材料中收敛结构，再逐段成稿。`writing-beats` 是需要逐步选择叙事方向时的替代路线，不与 `writing-shape` 机械叠加。GitHub 上找到 [yzsp-studio/writing-fragments](https://github.com/yzsp-studio/writing-fragments) 与 [yuncang123/writing-shape](https://github.com/yuncang123/writing-shape) 两个同名项目；本机文件与当前上游不同，作为候选来源注明，不声称精确版本。`writing-beats` 的本机文件与 [mattpocock/skills](https://github.com/mattpocock/skills/tree/main/skills/in-progress/writing-beats) 当前文件一致。
- **改现有文章：`edit-article`。** 按标题和信息依赖拆分，再逐节修改。本机 Skill 未记录上游链接；GitHub 搜索没有找到可确认的直接来源，暂标来源未记录。
- **结构化文档：`doc-coauthoring`。** 按背景收集、分节打磨、读者测试的阶段协作。[Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/doc-coauthoring) 有同名项目，但本机文件与当前上游不同。
- **内部沟通：`internal-comms`。** 先判沟通类型，再加载对应格式指南。GitHub 上的 [MextAI/internal-comms](https://github.com/MextAI/internal-comms) 和 [Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/internal-comms) 都有同名版本；本机副本与两边当前文件均不完全相同，具体获取来源未能唯一确定。
- **工程支线：`to-prd` → `to-issues`。** 先整理需求文档，再拆成独立 issue，不混入普通文章写作。[mattpocock/skills](https://github.com/mattpocock/skills) 的历史目录包含这两个名称；本机版本有改动，不是逐字副本。

### 成稿后的风格处理

- **`lieflat-less-ai-tone`：报告 → 人工确认 → 定向修改 → 复测。** 检测结果只提供候选问题，不授权自动改写。本机 Skill 文件与 [Xiangson/lieflat-less-ai-tone](https://github.com/Xiangson/lieflat-less-ai-tone) 当前文件一致。
- **`humanizer-zh`：可选第二遍抽查。** 不覆盖前一步报告和用户否决项。本机 README 指向 [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh)，并说明其内容参考 [blader/humanizer](https://github.com/blader/humanizer) 与 [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)；本机 Skill 文件与当前上游不同。
- **`text-rewrite`：** 用户只要求局部改写或润色时使用；本机文件没有记录上游来源，GitHub 搜索未找到可确认的直接匹配。
- **`caveman`：** 只在明确要求压缩表达时使用，不默认把全文压成短句。本机文件没有来源链接；搜到的同名 GitHub 项目与本机文件不匹配，暂不归属。

### 文件格式与专门任务

这些工具处理特定格式或场景，不是每篇文章都要调用：

- **Word**：`docx` 用于单份 Word 精细处理；`Word-Skill` 用于批量格式化和替换。`docx` 同名 Skill 在 [Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/docx)；`Word-Skill` 与 [ni1o1/claude-skill-docx-batch](https://github.com/ni1o1/claude-skill-docx-batch) 的文件一致。
- **PPT**：`pptx` 用于修改现有演示文稿；`ppt-master` 用于新建或大幅重构演示文稿。对应来源分别见 [Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/pptx) 和 [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master)；本机版本与当前上游文件不同。
- **呈现规范**：需要品牌视觉时才用 `brand-guidelines`，见 [Anthropic Skills](https://github.com/anthropics/skills/tree/main/skills/brand-guidelines)。
- **输入资料**：`pdf`、`PDF-Skill`、`pdf-converter` 和 `xlsx` 按文件类型处理，不作为文章风格工具。`pdf-converter` 的本机 README 指向 [tanis90/pdf-converter-mineru](https://github.com/tanis90/pdf-converter-mineru)，并说明可能调用 MinerU 外部 API；处理私人文件前要确认是否允许发送到该服务。`pdf`、`PDF-Skill` 和 `xlsx` 的本机安装文件没有记录可确认的上游链接，暂标来源未记录。
- **专门领域**：`wechat-digest` 用于公众号采集与分析，本机 README 指向 [Jackychen-12/wechat-digest-skill](https://github.com/Jackychen-12/wechat-digest-skill)；`社团材料整理` 服务于社团报销与材料整理，当前安装目录没有记录公共上游来源。它们属于专项入口，不进入通用写作主线。

文风量化使用本项目的 `style_check.py`，它是本机脚本，不是 Skill。当前脚本含个人目标带，不复制进本仓库；通用测量方法和将来可替换的示例见[文风定量画像](03-style-measurement.md)。

## 不可用时的替代路径

如果路由命中的 Skill 没安装、不可调用或版本行为不符，先明确说明限制，再按它负责的环节手动执行；不能声称已经调用，也不能静默跳过关键检查。涉及第三方服务、用户资料或需要写入外部系统时，另行确认权限和数据边界。

## GitHub 来源与版本核验

核验日期：2026-11-20。下列提交哈希固定这次检查到的上游快照；它们不代表本机 CC Switch 安装的副本一定相同。正文中的简化链接可能指向默认分支；如需复核本次来源，以本节固定的 commit permalink 为准。本机 Skill 目录没有 Git 远端，说明里会明确区分“文件精确匹配”“同名/声明来源但本地不同”和“来源未记录”。版本或许可证未知时标未知，不从相似名称推断；这里只保留引用，不转载第三方 Skill 正文。

### 可精确匹配或明确声明的来源

- `writing-beats`：本机 Skill 文件与 [mattpocock/skills](https://github.com/mattpocock/skills/blob/abeeaf95660ba9e8b7c753eb38f441ca707a8823/skills/in-progress/writing-beats/SKILL.md) 在核验时逐字相同；仓库许可为 MIT。
- `Word-Skill`：本机文件与 [ni1o1/claude-skill-docx-batch](https://github.com/ni1o1/claude-skill-docx-batch/blob/4a0345d27b0cbc466e0c967f3bbe7f60ab0354c2/SKILL.md) 逐字相同；许可为 MIT。
- `lieflat-less-ai-tone`：本机 Skill 文件与 [Xiangson/lieflat-less-ai-tone](https://github.com/Xiangson/lieflat-less-ai-tone/blob/1bd1100061b7e6a7797c1bcab3e8148ffd0271df/SKILL.md) 逐字相同。本机 `LICENSE` 文本是 MIT；GitHub 的机器识别未给出标准 SPDX，以上只记录文件核验结果。
- `humanizer-zh`：本机 README 指向 [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh/tree/f4518a8eab97b8bfebc66a89d34320a89bef6930)，并明确说明核心翻译参考 [blader/humanizer](https://github.com/blader/humanizer/tree/a32f24407364c74c812b43c15926d638bee1e072)，工具部分参考 [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop/tree/8da1f030185bdfe8471220585162991eaeb970e9)。上述仓库的许可信息为 MIT；本机 Skill 文件与 op7418 当前版本不同，README 中的来源说明是现有依据。

### 有上游候选，但本机文件不同

- `writing-fragments`：候选为 [yzsp-studio/writing-fragments](https://github.com/yzsp-studio/writing-fragments/tree/53675de09795ea8150d50befadb4f5c249556f28)（仓库标记 MIT）；本机文件与该快照不同，不能据此认定具体复制版本。
- `writing-shape`：候选为 [yuncang123/writing-shape](https://github.com/yuncang123/writing-shape/tree/41c69804a27a85fe2382dcc459d4edae2609aa71)（仓库标记 MIT）；本机文件与该快照不同。
- `doc-coauthoring`、`docx`、`pptx`、`brand-guidelines`：见 [Anthropic Skills](https://github.com/anthropics/skills/tree/e4bb5d960d87126ff3b3a8af1a104b7db67560ba/skills)。这个仓库的 GitHub 许可字段未识别；本机四份 SKILL.md 均与该快照不同，本机 `docx`、`pptx` Skill 头部写有 proprietary 条款，本项目只链接来源，不复制其内容。
- `internal-comms`：同名项目见 [MextAI/internal-comms](https://github.com/MextAI/internal-comms/tree/eb5c5c5e5d0e7d32aaaa2300c5b79286cea1ecc0)（仓库标记 Apache-2.0），Anthropic Skills 快照中也有同名文件。本机文件与两者都不完全相同，精确来源未能唯一确定；本机 `LICENSE.txt` 是 Apache-2.0。
- `to-prd`、`to-issues`：在 [mattpocock/skills](https://github.com/mattpocock/skills/tree/62f43a18177be6ec82da242e59ffbc490a4c22ea/skills/engineering) 的历史快照中能找到同名文件（仓库标记 MIT）；本机版本不同。该仓库当前版本已调整这组 Skill 的名称和流程。
- `ppt-master`：本机 Skill 自己声明的上游为 [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master/tree/d8f704bc8c1552d53a8769b55d1eecd22c782042)（MIT）；本机文件与当前上游不同。
- `pdf-converter`：本机 README 指向 [tanis90/pdf-converter-mineru](https://github.com/tanis90/pdf-converter-mineru/tree/464314156f604943f8373d7701bbb3a521ed3092)；GitHub 没有识别仓库许可。该 Skill 会把文档发到 MinerU 外部 API；其服务说明还链接 [OpenDataLab/MinerU](https://github.com/opendatalab/MinerU/tree/097de7f63f54722c9b805ee1c9a14a0c5b02e078)。使用前需按文档敏感程度决定是否允许外发。
- `wechat-digest`：本机 README 指向 [Jackychen-12/wechat-digest-skill](https://github.com/Jackychen-12/wechat-digest-skill/tree/4d48c327eab7996f5b23c27e1bc4e67eeac33377)（MIT）；本项目不复制其采集代码或语料。

### 目前没有可靠上游记录的本机项

`edit-article`、`text-rewrite`、`caveman`、`社团材料整理`、`pdf`、`PDF-Skill` 和 `xlsx`：本机文件没有提供可确认的上游链接；同名搜索结果不足以证明来源，故标注“本机安装，来源未记录”。`style_check.py` 是本项目使用的本机脚本，不是外部 Skill；现有个人目标带不会发布。
