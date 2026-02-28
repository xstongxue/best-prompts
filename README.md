# best-prompts🚀

通用高质量 prompt 合集，可直接复制到聊天框使用。

本提示词在 Claude4.6、Gemini3、GPT5.2、Composer1.5 等模型下遵循极好，优先推荐使用

更多模型排名：[https://arena.ai/zh/leaderboard](https://arena.ai/zh/leaderboard)

## 一 项目初衷

在 Vibe Coding 时代，**好的 Prompt 决定 AI 的输出质量**。但市面上很多「万能写作 Prompt」要么太泛、要么太散——真正能贴合具体场景、适配输出格式、兼顾约束细节的，少之又少。

best-prompts 希望做两件事：

> 1. **沉淀可复用的高质量 Prompt**：每个 Prompt 都经过场景细分和约束设计，复制即用，减少反复调试
> 2. **按使用场景组织**：从论文撰写、开发流程到自媒体创作，让用户按需找到对应 Prompt，而非在零散文件中翻找

项目**通用且可扩展**，会持续补充更多领域。欢迎 Star、Fork、提 Issue 和 PR。

## 二 按使用场景分类

### 本科&硕士学位论文撰写

学位论文全流程（大纲审核、结构仿写、润色扩写、参考文献、防 AIGC、中英互译等），配合图表生成完成系统设计章节的图文内容。


| 用途         | Prompt                                                                                                                             |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **正文内容撰写** | [paper-write-prompt.md](prompts/paper-write-prompt.md) — 大纲审核、绪论/摘要/实验章节仿写、润色/扩写/缩写、参考文献、防 AIGC、中英互译、结构化信息提取                       |
| **系统章节生成** | [codegen-paper-chapter-generator-prompt.md](prompts/codegen-paper-chapter-generator-prompt.md) — 根据大纲与项目代码生成系统设计章节正文               |
| **通用图表**   | [drawio-diagram-generator-prompt.md](prompts/drawio-diagram-generator-prompt.md) — 模型架构图、算法流程图、概念示意图                               |
| **技术栈图**   | [codegen-tech-stack-diagram-prompt.md](prompts/codegen-tech-stack-diagram-prompt.md) — 前端/后端/模型服务技术栈结构图                            |
| **系统架构图**  | [codegen-system-arch-diagram-prompt.md](prompts/codegen-system-arch-diagram-prompt.md) — 四层分层架构图                                   |
| **数据结构图**  | [codegen-data-structure-diagram-prompt.md](prompts/codegen-data-structure-diagram-prompt.md) — 表格式实体与字段关系图                         |
| **E-R 图**  | [codegen-er-diagram-prompt.md](prompts/codegen-er-diagram-prompt.md) — Chen 记法实体关系图                                                |
| **图片风格迁移** | [codegen-diagram-style-migration-prompt.md](prompts/codegen-diagram-style-migration-prompt.md) — 按参考图风格生成项目图表                      |
| **答辩 PPT** | [pptgen-drawio-thesis-defense-prompt.md](prompts/pptgen-drawio-thesis-defense-prompt.md) — 多页 Draw.io 生成，配合 drawio2pptx 导出可编辑的 PPT |


### 开发流程四步法

需求理解 → 方案设计 → 代码实现 → 代码审查。


| 步骤   | Prompt                                                               |
| ---- | -------------------------------------------------------------------- |
| 需求理解 | [dev-requirement-prompt.md](prompts/dev-requirement-prompt.md)       |
| 方案设计 | [dev-design-prompt.md](prompts/dev-design-prompt.md)                 |
| 代码实现 | [dev-implementation-prompt.md](prompts/dev-implementation-prompt.md) |
| 代码审查 | [dev-review-prompt.md](prompts/dev-review-prompt.md)                 |


### 自媒体创作


| 用途              | Prompt                                                                                                                                            |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 公众号/技术博客        | [wechat-article-writer-prompt.md](prompts/wechat-article-writer-prompt.md) — 搜索资料、撰写、爆款标题、排版优化                                                    |
| 公众号封面 Draw.io   | [wechat-article-image-generator-prompt.md](prompts/wechat-article-image-generator-prompt.md) — 封面/结尾图 .drawio XML，支持 1:1、16:9、9:16、4:3、3:4、2.35:1 |
| 公众号文章插图 Draw.io | [wechat-article-illustration-prompt.md](prompts/wechat-article-illustration-prompt.md) — 正文插图 .drawio XML，步骤图、演示图、流程示意、前后对比                       |


### 项目文档与简历


| 用途     | Prompt                                                                               |
| ------ | ------------------------------------------------------------------------------------ |
| 项目整体梳理 | [codegen-project-overview-prompt.md](prompts/codegen-project-overview-prompt.md)     |
| 项目重点问题 | [codegen-project-key-issues-prompt.md](prompts/codegen-project-key-issues-prompt.md) |
| 简历项目描述 | [codegen-resume-format-prompt.md](prompts/codegen-resume-format-prompt.md)           |


### 投稿小论文撰写

期刊/会议论文写作，推荐使用外部精选资源：

- [awesome-ai-research-writing](https://github.com/Leey21/awesome-ai-research-writing) — AI 辅助学术写作工具与 Prompt 汇总

### 工具与扩展


| 用途                | Prompt                                                                       |
| ----------------- | ---------------------------------------------------------------------------- |
| 代码审查（多语言）         | [code-review-excellence-prompt.md](prompts/code-review-excellence-prompt.md) |
| Skill 创建          | [skill-create-prompt.md](prompts/skill-create-prompt.md)                     |
| Skill 与 Prompt 互转 | [skill-prompt-convert-prompt.md](prompts/skill-prompt-convert-prompt.md)     |


---

## 三 使用方式

> 1. 打开对应 `.md` 文件
> 2. 复制 `# Role` 到 `# Input` 之间的完整 Prompt（含  代码块）
> 3. 粘贴到与 AI 的对话中
> 4. 在 `[在此处填写]` 或 `[在此处粘贴]` 位置填入你的内容

