# 小红书可爱图解知识账号

用可爱图解讲懂身体、生活和世界里的小机制。

## 项目负责

- 沉淀“小红书可爱图解知识账号”的产品定位、内容边界、选题策略和生产流程。
- 产出身体、生活、AI / 算法等科普主题的小红书纯图文笔记方案，包括标题、分镜、每页配文、画面描述、GPT-image2 Prompt 草案、正文、标签和复盘口径。
- 维护首批验证计划：以小红书为唯一早期渠道，用 4 周、12 到 20 篇内容验证收藏率、评论率、转发率和完读表现。
- 支持后续基于评论、热点和数据复盘建立半自动选题池，但该能力不进入 MVP。

## 项目不负责

- 不做硬核算法课程、考试型知识内容或系统技术教学。
- 不做公众号、视频号、抖音等多平台同步运营。
- 不做复杂视频动画、真人出镜、直播课或知识付费。
- 不建立高成本原创 IP 世界观或固定主角 IP 设定。
- 不在本仓库保存临时 AI 协作过程材料、历史过程归档或一次性中间产物。

## 核心口径

- 早期渠道：只做小红书。
- 首批主题：身体机制、生活机制、AI / 算法机制。
- 内容形态：纯图文 carousel。
- 默认画幅：小红书 3:4。
- 默认页数：根据机制步骤和难易程度动态决定；简单题可 3 到 4 页，常规题 4 到 6 页，复杂题拆上下篇；机制科普必须包含总结页。
- 视觉风格：软萌治愈 + 贴纸手账。
- 图片生成：由创作者使用 GPT-image2 自行生成，项目文档只负责提示词和画面方案。
- 文案立场：中性解释，少做强观点输出。
- 首篇样稿：CP-SAT。早期曾用“安排座位”做 2 页/4 页节奏对比；当前 CP-SAT 推荐稿改为“排课”5 页步骤版，必须包含总结页。

## 内容生产流程

1. 选题：选择一个生活问题或常见概念。
2. 结构生成：AI 根据选题类型拆出通用图文结构；算法类优先使用 `templates/algorithm-xhs-infographic-generator-template.md`，身体和生活机制类按“生活问题 -> 机制拆解 -> 边界提醒”的结构处理。
3. 提示词：AI 根据选题生成外部 LLM 文案提示词。
4. 粗稿：创作者把提示词交给外部 LLM，得到标题、比喻、分镜、配文、正文、标签和风险提醒。
5. 定稿：AI 对外部 LLM 粗稿做二次加工，检查 PRD 口径、通俗度、准确性边界和小红书翻页节奏。
6. 生图方案：AI 整理每页画面描述和 GPT-image2 Prompt 草案，并保持角色、场景、风格一致。
7. 作图：创作者按提示词生成图片。
8. 发布：创作者配标题、正文、话题标签后发布。
9. 复盘：记录数据和评论反馈，反哺选题池。

## 外部 LLM 协作流程

当前项目默认不接入 LLM API。LLM 作为仓库外创作辅助工具使用，仓库只沉淀提示词模板、内容样稿、审稿标准和复盘口径。

推荐协作方式：

1. 用户确定选题，例如“什么是 CP-SAT？用安排座位解释约束求解”。
2. AI 基于 `templates/external-llm-copy-prompt-template.md` 生成该选题专用的外部 LLM 提示词。
3. 用户把提示词交给外部 LLM，生成第一版粗稿。
4. 用户把粗稿贴回仓库协作上下文。
5. AI 按 PRD 进行定稿，输出可用于生图和发布的样稿。

只有在后续明确要产品化为内容生成工具时，才新增 LLM client、提示词编排、输出格式校验和人工审核链路。

## 内容验收标准

- 每篇只围绕一个核心问题展开，不在同一篇里塞太多概念。
- 每页只讲一个小步骤或关键变化。
- 先用生活场景解释，再轻轻点出技术概念。
- 必须保留一个可被用户带走的一句话总结。
- 机制科普图文必须按机制步骤和难易程度动态定页数，并保留最后总结页或大体了解图；不得退回只有解释图、没有总结页的旧结构。
- 身体健康类内容只做普通科普，不做诊断、治疗建议或个体化医疗判断；涉及明显异常、持续疼痛、长期紊乱、大量出血等情况，必须提醒寻求专业医生帮助。
- 必须包含互动问题，引导评论区分享经历或点题。
- 复杂比喻必须说明是“简化理解”，不得把简化表达说成严格技术定义。
- 画面 Prompt 必须体现软萌治愈、贴纸手账、3:4、小红书图文、多页连续叙事。

## 目录说明

- `xiaohongshu-cute-knowledge-prd.md`：项目 V1 需求文档，是账号定位、内容范围和首篇样稿要求的事实来源。
- `README.md`：项目总说明、文件地图、内容生产流程和验证口径。
- `AGENTS.md`：AI 协作约束、工程风格、项目专属红线和收口要求。
- `templates/external-llm-copy-prompt-template.md`：根据选题生成通俗易懂小红书文案粗稿的外部 LLM 提示词模板。
- `templates/algorithm-xhs-infographic-generator-template.md`：根据算法名和生活例子生成小红书算法科普图文结构，固定解释骨架，不固定具体场景。
- `templates/humanize-copy-checklist.md`：去 AI 味文案检查清单，用于把顺滑但像说明书的文本改得更像真人表达。
- `templates/image2-infographic-prompt-guide.md`：Image2 竖版信息图 Prompt 规则，用于控制信息结构、文字量、留白和风格一致性。
- `prompts/`：按具体选题生成的外部 LLM 专用提示词。
- `drafts/`：承接外部 LLM 粗稿、AI 定稿、生图 Prompt 和发布文案的样稿目录。

## 文档索引

- `AGENTS.md`：AI 进入仓库后的第一入口。执行任务前必须读取本文件和 `README.md`。
- `xiaohongshu-cute-knowledge-prd.md`：V1 定版 PRD。账号定位、内容范围、视觉风格、渠道、画幅和页数规则以此为准。
- `templates/algorithm-xhs-infographic-generator-template.md`：当需要把某个算法和生活例子转成步骤化图文结构时使用；生活例子可替换，不能把排课、座位等单一场景写死。
- `templates/external-llm-copy-prompt-template.md`：当用户给出选题时，优先用它生成外部 LLM 提示词。
- `templates/humanize-copy-checklist.md`：每次定稿前必须读取，用来降低 AI 腔和八股感。
- `templates/image2-infographic-prompt-guide.md`：每次生成或改写 Image2 Prompt 前必须读取。
- `prompts/cp-sat-seat-arrangement-external-llm-prompt.md`：首篇 CP-SAT 选题的外部 LLM 专用提示词。
- `prompts/cp-sat-seat-arrangement-image2-prompts.md`：首篇 CP-SAT 的 Image2 生图 Prompt 包。
- `prompts/cp-sat-course-scheduling-image2-prompts.md`：CP-SAT 排课小助手版 Image2 生图 Prompt 包。
- `drafts/cp-sat-seat-arrangement-draft.md`：首篇 CP-SAT 样稿承接文件，等待外部 LLM 粗稿后进入定稿。
- `drafts/cp-sat-course-scheduling-draft.md`：CP-SAT 排课小助手版定稿，当前推荐使用。

## 环境口径

当前仓库是内容策划与文档仓库，暂无应用运行环境、数据库、远端服务或生产发布流程。

- 本地文档编辑：只修改当前任务直接相关的 Markdown 文件。
- 本地验证：优先使用全文搜索、占位符检查、Markdown 结构检查和人工阅读核对。
- 真实联调：如后续接入小红书平台、图像生成 API、热点采集接口或自动化发布工具，必须在执行前单独说明环境、对象、影响范围和验证证据。
- 生产发布：当前不适用。未经用户明确授权，不执行任何账号发布、平台写入、远端服务变更或自动化投放。

## 最小验证命令

检查模板占位符：

```powershell
$pattern = [string][char]123 + [string][char]123
rg --fixed-strings $pattern README.md AGENTS.md xiaohongshu-cute-knowledge-prd.md templates prompts drafts
```

检查项目关键词：

```powershell
rg "CP-SAT|软萌治愈|贴纸手账|小红书|身体机制|生活机制|AI / 算法|外部 LLM|去 AI 味|Image2" README.md AGENTS.md xiaohongshu-cute-knowledge-prd.md templates prompts drafts
```

## 后续优先事项

1. 用身体机制、生活机制和算法机制选题测试账号新定位的点击与收藏表现。
2. 每次生成前先根据机制步骤和难易程度确认页数，最后一页必须是总结图。
3. 对比不同生活例子的理解成本、阅读负担、生图稳定性和健康边界表达。
4. 根据多篇样稿继续沉淀可复用的分镜与 Prompt 检查清单。
