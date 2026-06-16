# AI 日报观看说明

你的日报现在按“飞书先看，网页补看”的方式使用。每天 GitHub Actions 会在北京时间 08:00 左右开始运行，生成完成后自动把当天日报入口推送到飞书机器人；实际收到时间通常会比 08:00 晚几分钟。

网页总入口：

https://bcc2802.github.io/agents-radar

GitHub 仓库：

https://github.com/bcc2802/agents-radar

## 每天收集哪些来源

日报主要来自这些地方：

1. AI 编程工具 GitHub 仓库
   - Claude Code：`anthropics/claude-code`
   - OpenAI Codex：`openai/codex`
   - Gemini CLI：`google-gemini/gemini-cli`
   - GitHub Copilot CLI：`github/copilot-cli`
   - Kimi Code CLI：`MoonshotAI/kimi-cli`
   - OpenCode：`anomalyco/opencode`
   - Pi：`badlogic/pi-mono`
   - Qwen Code：`QwenLM/qwen-code`
   - DeepSeek TUI：`Hmbown/DeepSeek-TUI`

2. Claude Skills
   - `anthropics/skills`

3. AI Agent 相关 GitHub 仓库
   - OpenClaw：`openclaw/openclaw`
   - NanoBot、Hermes Agent、PicoClaw、NanoClaw、NullClaw、IronClaw、LobsterAI、TinyClaw、Moltis、CoPaw、ZeptoClaw、ZeroClaw 等同类项目

4. 开源趋势
   - GitHub Trending
   - GitHub Search，关键词包括 `llm`、`ai-agent`、`rag`、`vector-database`、`large-language-model`、`machine-learning`

5. 官方动态
   - OpenAI 官网内容
   - Anthropic 官网内容

6. 社区和产品动态
   - Hacker News
   - Hugging Face 热门模型
   - Dev.to AI 相关文章
   - Lobste.rs AI/ML 内容
   - Product Hunt AI 产品，只有配置 Product Hunt token 时才会稳定出现

7. 论文动态
   - ArXiv：`cs.AI`、`cs.CL`、`cs.LG`

## 每天怎么看

只花 5 分钟时，先看飞书消息里的摘要小点。重点看有没有新模型、新工具、新产品、新开源项目、明显变热的话题。

花 15 分钟时，建议按这个顺序打开：

1. `AI CLI 工具`
   这是最适合你持续看的核心板块。重点看 Claude Code、Codex、Gemini CLI、Qwen Code、Kimi、OpenCode 有什么更新，因为它们会直接影响你以后怎么用 AI 写代码、做自动化、做工作流。

2. `GitHub 趋势`
   适合找新工具、新项目、新选题。看到重复出现的仓库、快速涨星的项目、围绕 Agent/RAG/CLI 的工具，值得点进去看。

3. `官网动态`
   主要看 OpenAI 和 Anthropic 的正式发布。这里信号更强，适合判断大方向，比如模型能力、产品入口、安全规则、API 变化。

4. `AI Agents 生态`
   这个板块更偏技术生态和项目对比。你不需要每天逐条看完，但如果你正在研究 Agent、自动化、MCP、工作流，就值得看。

5. `Hugging Face 模型`
   如果你暂时不做本地模型、开源模型部署，可以只看标题。看到模型名字反复出现，或者和图像、视频、Agent、代码相关，再点进去。

6. `HN 社区动态` 和 `技术社区 AI 动态`
   这里更像市场和开发者情绪。适合看大家在讨论什么、抱怨什么、真正卡在哪里，不需要逐条精读。

7. `ArXiv 研究`
   这是最低频阅读板块。建议一周集中看一次，除非当天标题明显和你正在做的事相关。

## 值得长期关注的信号

持续关注这些变化：

1. AI 编程工具是否在加强：命令行、代码理解、自动修改、多文件操作、浏览器/终端协作、MCP、权限控制。

2. Agent 工具是否从“演示”走向“可用”：是否开始支持记忆、工具调用、工作流编排、多人协作、稳定运行。

3. GitHub Trending 里反复出现的方向：如果同类项目连续几天出现，说明开发者需求在变热。

4. OpenAI / Anthropic 官方发布：这类内容优先级最高，比社区传言更值得信。

5. 社区里反复出现的痛点：安装复杂、成本高、幻觉、权限安全、上下文管理、自动化失败，这些都可能变成产品机会或内容选题。

## 哪些可以跳过

1. 英文版日报
   已经关闭后续生成和推送，历史英文日报文件也已清理。

2. 周报、月报
   对你现在“每天在飞书看日报”的需求来说，它们容易和日报重复。现在已经改成手动运行，不会再自动推送。

3. 每个 GitHub Issue / PR 的细节
   不需要逐条看。你只看总结里反复出现的关键词和大变化即可。

4. 低相关论文
   如果论文标题和你的业务、内容、工具使用没有明显关系，可以跳过。

## 推荐阅读节奏

每天早上收到飞书后，先用 3 到 5 分钟扫摘要。

如果当天有明显重要变化，再打开网页看 `AI CLI 工具`、`GitHub 趋势`、`官网动态` 三个板块。

每周找一次 20 分钟，回看过去几天的 `GitHub 趋势` 和 `HN 社区动态`，专门找可以写内容、做产品验证、优化工作流的线索。
