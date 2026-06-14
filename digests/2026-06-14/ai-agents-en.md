# OpenClaw Ecosystem Digest 2026-06-14

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-14 04:01 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyagi)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw Deep Dive

Here is the project digest for OpenClaw, generated from the provided GitHub data for 2026-06-14.

---

### OpenClaw Project Digest: 2026-06-14

**Based on data from:** [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)

---

### 1. Today's Overview

Project activity is **extremely high**, with 500 issues and 500 pull requests updated in the last 24 hours. While a significant number of these represent ongoing, high-priority work, a substantial portion (95 issues, 201 PRs) are being resolved, showing a strong push to stabilize the codebase. The two new beta releases focus on delivering richer, more reliable channel integrations for Telegram and WhatsApp. The community is actively debating critical stability and memory leak issues, indicating the project is in a rapid, but sometimes turbulent, development phase.

### 2. Releases

Two new beta releases were published on **2026-06-08** and **2026-06-07**, both focusing heavily on channel delivery improvements.

- **[v2026.6.8-beta.1](https://github.com/openclaw/openclaw/releases/tag/v2026.6.8-beta.1):** Rich text delivery for **Telegram** and **WhatsApp** has been made more robust. Telegram now supports structured content like tables, lists, and blockquotes, while WhatsApp layers have been restructured for safer handling of rich-media elements.
- **[v2026.6.7-beta.1](https://github.com/openclaw/openclaw/releases/tag/v2026.6.7-beta.1):** Channel delivery is "tighter" across **Slack** and **Telegram**, including the ability to send images as file attachments via a message tool, expandable Telegram blockquotes, and improved handling of paged results.

**Note:** These are beta releases and may contain breaking changes for users relying on the previous channel delivery formats.

### 3. Project Progress

In the last 24 hours, **201 pull requests** have been merged or closed, and **95 issues** have been closed. Key areas of progress include:

- **Memory Leak Fixes:** A fix is in progress for the critical gateway memory leak (Issue [#91588](https://github.com/openclaw/openclaw/issues/91588)), with related work on monitoring and recovery appearing in several PRs.
- **Session State Corrections:** The embedded-run session state leak (Issue [#48573](https://github.com/openclaw/openclaw/issues/48573)) has been closed.
- **Platform Support:** A Windows node connection issue (Issue [#84644](https://github.com/openclaw/openclaw/issues/84644)) has been resolved.
- **Operational Stability:** Several fixes were advanced to recover gateway processes after network or timeout failures, including handling isolated cron setups and terminal session statuses (PRs [#89055](https://github.com/openclaw/openclaw/pull/89055), [#89045](https://github.com/openclaw/openclaw/pull/89045)).
- **Developer Experience:** Work has been done to protect agent configurations and plugin tool descriptors from errors, increasing overall system resilience (PRs [#89052](https://github.com/openclaw/openclaw/pull/89052), [#89031](https://github.com/openclaw/openclaw/pull/89031)).

### 4. Community Hot Topics

The community is most engaged around issues related to data integrity and system stability.

- **[Diamond Lobster] Subagent Completion Lost (Issue #44925):** 19 comments, 1 👍. This issue details multiple failure modes where subagent results are "silently lost" with no retry or notification. This is a core trust and reliability concern that strikes at the heart of the multi-agent orchestration feature.
- **[Diamond Lobster] Feishu Monitor Memory Leak (Issue #48183):** 19 comments. The report details a potential leak in the Feishu plugin's monitor state cleanup. The community is actively analyzing the code path to confirm the risk.
- **[Platinum Hermit] Filename Encoding Utility (Issue #48788):** 18 comments. This feature request to centralize multi-encoding filename handling has garnered significant discussion. It reflects the pain of international users dealing with corrupted filenames across various channels (e.g., Chinese characters in Feishu).
- **[Diamond Lobster] Steer Mode Injection (Issue #48003):** 12 comments, 2 👍. A bug report that `steer` mode for message injection is broken, meaning users cannot interrupt the agent's current thinking process. The root cause has been identified, and a fix is highly anticipated.

### 5. Bugs & Stability

Stability is the primary theme of this digest, with several high-impact regressions and memory issues reported.

**Critical (P0/P1):**
- **Gateway Memory Leak (Issue #91588):** A critical memory leak causing RSS to grow from 350MB to 15.5GB, leading to repeated OOM crashes and service outages.
- **Session Hangs & Data Loss (Issues #43661, #47975):** Compaction timeouts cause silent duplicate message loops. Subagent sessions persist after completion, locking the main session. These are major user experience failures.
- **Data Contamination & Security:**
    - **Discord Tool-Call Leak (Issue #44905):** Internal LLM tool calls (including `NO_REPLY` and raw JSON) are leaked to end-users.
    - **Cron Contaminates Runtime (Issue #90991):** A scheduled cron trigger can cause "transient system-wide overload failures."
    - **`gh-issues` Prompt Injection (Issue #45740):** Untrusted GitHub issue bodies are injected directly into the sub-agent prompt.
- **Key Fixes in Motion:** PR [#89039](https://github.com/openclaw/openclaw/pull/89039) addresses silent message loss from session takeover errors, and PR [#92857](https://github.com/openclaw/openclaw/pull/92857) fixes a critical bug in the OpenAI ChatGPT-Responses family where encrypted reasoning would break the next turn.

**Other High-Severity Bugs:**
- **Telegram HTML Parse Truncation (Issue #49104):** Responses with `<think>` tags are silently truncated when sent with HTML parse mode. This is a significant interoperability issue.
- **`openclaw update` fails on Windows (Issue #40540):** A regression causing the update command to fail with `EBUSY`.

### 6. Feature Requests & Roadmap Signals

The user base is calling for more robust control and preventative measures.

- **Proactive Memory Management:** There is a strong desire for memory to be preserved and synthesized across session resets (Issues [#45608](https://github.com/openclaw/openclaw/issues/45608), [#40418](https://github.com/openclaw/openclaw/issues/40418)). This suggests a shift from memory as a stateless log to a stateful, learning system.
- **Cost Controls & Security:** A high number of users are requesting operational safeguards, such as per-agent cost budgets (Issue [#42475](https://github.com/openclaw/openclaw/issues/42475)), path-scoped permissions (Issue [#39979](https://github.com/openclaw/openclaw/issues/39979)), and memory trust tagging (Issue [#7707](https://github.com/openclaw/openclaw/issues/7707)).
- **Platform Expansion:**
    - **WhatsApp Group Management (PR #89033):** A new PR proposes letting the agent create and manage WhatsApp groups programmatically. This is a substantial platform expansion.
    - **YAML Config Support (Issue #45758):** A popular request for YAML configuration support (2 👍), indicating a desire to align with standard DevOps tooling.
- **UI/UX Improvements:**
    - **Whiteboard App Status (PR #88988):** A PR shows work on showing session duration in a status footer.
    - **MathJax/LaTeX Support (Issue #42840):** A high-demand request (6 👍) to render mathematical formulas in the Control UI.

### 7. User Feedback Summary

- **Pain Points:** The most common user complaints revolve around **message loss** and **session instability**. Users report messages being silently dropped, conversations getting stuck, and the system becoming unresponsive ("silent failure loops"). The subagent orchestration feature seems particularly prone to these issues (Issue #44925).
- **Use Cases:** Users are clearly running OpenClaw in production-like environments: managing multiple concurrent sessions, using cron for automated tasks, and integrating with enterprise services like Feishu and Discord. The specific, detailed bug reports show sophisticated usage.
- **Sentiment:** Despite the high number of active bugs, the community is engaged and constructive. Users are providing detailed root cause analyses and are actively participating in discussions to find solutions. The immediate effort to fix the critical memory leak (Issue #91588) demonstrates a strong commitment to stability.

### 8. Backlog Watch

Several high-severity, long-standing issues remain open without a clear path to resolution, requiring maintainer attention.

- **[Feishu Media Loss (Issue #41744] - Diamond Lobster):** Created March 10. A bug where images read by the agent are lost before the final outbound payload. It has a linked PR but is awaiting maintainer review and a product decision.
- **[Memory Management Chaos (Issue #43747] - Diamond Lobster):** Created March 12. A regression where memory behavior is inconsistent across users (different persistence backends, chunking behaviors). Still needs a product decision and live reproduction.
- **[Spam Attack via Cron (Issue #45778] - Diamond Lobster):** Created March 14. A security concern where skills using system `crontab` can be used to send background messages omnipotently, bypassing agent context. Needs security and product decisions.
- **[Config Format Request (Issue #45758]):** Created March 14. A straightforward, popular (2 👍) feature request for YAML support that has been "stale" for 3 months.
- **[Control UI Avatar Broken (Issue #41201] - Diamond Lobster):** Created March 9. A regression that is impacting basic UI customization, still awaiting decisions and a security review.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report for the AI agent and personal AI assistant open-source ecosystem, generated from the June 14, 2026, community digest summaries.

---

### 1. Ecosystem Overview

The personal AI agent open-source ecosystem is experiencing a frenetic, bifurcated phase of growth. On one side, major reference projects like OpenClaw and zeroClaw are processing hundreds of issues and pull requests daily, indicating massive adoption and a corresponding wave of stability challenges. On the other, a cohort of smaller, focused projects (NanoBot, Moltis) is advancing rapidly through targeted feature work and dependency management. A clear tension is evident between deploying rich, multi-platform features (Telegram, Slack, WhatsApp, DingTalk) and maintaining the runtime reliability and memory stability required for production use. The ecosystem is maturing beyond simple chat interfaces toward complex, stateful multi-agent orchestrations, but this evolution is currently outpacing the stability of the underlying infrastructure.

### 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release Status | Health Score | Key Signal |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | 2 Beta releases | **Moderate** | High volume, critical memory leaks, active stabilization |
| **ZeroClaw** | 42 | 50 | Pre-release (v0.8.0-beta) | **Moderate** | High activity, major architecture merge, new regressions |
| **IronClaw** | 2 | 24 | None (Release PR stalled) | **Moderate** | Focused on Slack/attachment features, CI test failing |
| **NanoBot** | 5 | 18 | None | **High** | Fast fix turnaround, new features ready for merge |
| **Hermes Agent** | 50 | 50 | None | **Moderate** | "Mega-bundle" PR signals maintainer bottleneck |
| **PicoClaw** | 2 | 7 | Nightly build | **High** | Healthy churn, responsive to bugs |
| **NanoClaw** | 1 | 6 | None | **High** | Provider extensibility push, stability fixes pending |
| **CoPaw** | 9 | 9 | None (lags behind) | **Low** | Backlogged PRs, unresolved data-loss bugs |
| **NullClaw** | 1 | 1 | None | **Moderate** | Single critical bug with fix awaiting review |
| **LobsterAI** | 4 | 5 | None | **Low** | Stale, 72-day response time on issues |
| **Moltis** | 1 | 3 | None | **High** | Active community fix for OAuth bug |

### 3. OpenClaw's Position

OpenClaw remains the clear reference implementation and the most battle-tested project in the ecosystem, evidenced by its massive issue/PR volume and the sheer sophistication of its user base (reported bugs include detailed root-cause analysis of use-after-free issues in cron jobs and complex memory leak paths). It has a distinct technical advantage in **channel delivery depth**, being the only project to ship structured content (tables, lists, blockquotes) for both Telegram and WhatsApp in its latest betas. Its primary disadvantage is that this complexity is causing significant operational pain—critical memory leaks and silent message loss are eroding user trust. While its community is the largest and most vocal, the sheer volume of activity makes it appear less stable than more narrowly focused projects like NanoBot or PicoClaw. OpenClaw is the ecosystem's proving ground, pushing the boundaries of what a personal AI agent can do, but it is currently paying the price for being first to market with these advanced features.

### 4. Shared Technical Focus Areas

Several core requirements are emerging simultaneously across the ecosystem, indicating industry-wide challenges:

- **Memory & Context Stability**: Projects are grappling with the same fundamental problem.
    - **OpenClaw**: Critical memory leak (RSS 350MB to 15.5GB) and subagent completion loss.
    - **ZeroClaw**: "Dream Mode" for periodic memory consolidation is the most popular open feature.
    - **Hermes Agent**: "Auto Dream" feature request is the top-voted item. Context compression hangs reported.
    - **CoPaw**: Context compression omits profile files, resulting in zero-token context and task interruption.
    - **NanoBot**: Fix for `idleCompact` losing conversation history was just merged.
    - **IronClaw**: Runtime hooks and failure recovery are core themes.
    - **NullClaw**: Use-after-free bug in cron jobs causes silent message loss.

- **Multi-Platform Messaging & Rich Content**: Delivering structured, non-plain-text messages is a cross-cutting need.
    - **Telegram**: OpenClaw, Hermes Agent, and NullClaw all have bugs or features dedicated to rich formatting, blocks, and tables.
    - **WhatsApp**: OpenClaw restructured WhatsApp layers; Hermes Agent has a PR for Cloud Calling.
    - **Slack**: IronClaw is fixing approval loops; Hermes Agent is fixing `NO_REPLY` sentinel bugs.
    - **Chinese Platforms (Feishu, DingTalk, QQ)**: OpenClaw has Feishu memory leak; CoPaw has persistent DingTalk registration bug and slow Tauri startup.

- **Security & Guardrails**: As agents take on more autonomous roles, users demand safety controls.
    - **Prompt Injection**: OpenClaw has a critical bug where untrusted GitHub issue bodies are injected into subagent prompts.
    - **Cost Controls**: OpenClaw users request per-agent cost budgets; Hermes Agent has bugs about tool-call bursts causing credit spikes.
    - **Tool/File System Access**: NanoBot merged a fix for workspace symlink escape; Hermes Agent blocks cron from read-only tools.

### 5. Differentiation Analysis

| Project | Core Differentiator | Target User | Primary Technical Focus |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | Depth of platform integrations | Power users, developers | Channel delivery, multi-agent orchestration |
| **ZeroClaw** | Architecture & plugin system | Developers, tinkerers | Turn-engine unification, WASM/Native plugins |
| **IronClaw** | Slack/Enterprise focus | Team managers, Slack users | Slack workflow stability, document extraction |
| **NanoBot** | WebUI parity & provider diversity | DevOps, backend users | Configuration management, MCP, TUI |
| **Hermes Agent** | Platform breadth | General users | Multi-channel support (Telegram, WhatsApp, Matrix) |
| **PicoClaw** | Vision & TTS routing | Media-heavy users | Image compression, model hallucination fixes |
| **NanoClaw** | Containerized provider framework | System integrators | SDK-based extensibility, container lifecycle |
| **CoPaw** | Chinese platform ecosystem | Chinese-language users | DingTalk, QQ, WeChat; Tauri desktop |
| **NullClaw** | Cron & scheduling reliability | Automation users | Scheduled task delivery, non-interactive channels |
| **LobsterAI** | Artifacts & Cowork UI | Knowledge workers | Browser preview, UI polish |
| **Moltis** | MCP Server OAuth integration | MCP/API consumers | Third-party service authentication |

### 6. Community Momentum & Maturity

- **Tier 1: Rapidly Iterating (High Risk/Reward)**: **OpenClaw** and **ZeroClaw** are the ecosystem engines, processing the most code and feedback. They are unstable but set the agenda. **IronClaw** and **Hermes Agent** are close behind, with heavy feature work creating a quality-of-life gap.

- **Tier 2: Balanced Growth (Stable & Active)**: **NanoBot**, **NanoClaw**, and **PicoClaw** are demonstrating a healthy rhythm of feature addition, bug fixing, and community response. They are in a "stabilization + feature-adding phase," which is the most mature state in this fast-moving environment.

- **Tier 3: Niche Specialists (Low Volume, High Focus)**: **NullClaw** and **Moltis** have low overall activity but are laser-focused on solving a specific, deep problem (cron delivery, MCP OAuth). They are stable for their specific use case.

- **Tier 4: Stalling (Low Momentum)**: **CoPaw** and **LobsterAI** are showing signs of maintainer bottleneck and community frustration. CoPaw has a backlog of fix PRs for critical bugs, while LobsterAI has issues going unanswered for over 70 days.

### 7. Trend Signals

The aggregated community feedback points to several clear trends for the AI agent ecosystem:

- **The "Reliability Wall" has been hit**: The single largest signal is that advanced, multi-step agent capabilities (cron jobs, subagents, memory consolidation, multi-turn corrections) are causing silent data loss (OpenClaw, NullClaw, CoPaw) or unexpected cost spikes (Hermes Agent). The market is moving from "can the agent do X?" to "can the agent do X reliably, and can I trust the output?" This is the next major engineering challenge.

- **Cost Observability is a Feature Requirement**: Users are no longer accepting a "black box" model. They want tool-call burst prevention (Hermes Agent), per-agent budgets (OpenClaw), and configurable image compression (PicoClaw). Cost is a first-class UX concern.

- **The "AI Agent" is Becoming an "AI Platform Operator"**: Features like per-turn model routing (ZeroClaw), subagent model presets (NanoBot), and cross-profile delegation (ZeroClaw) show that users want to build complex pipelines, where different tasks are routed to different models (cheap vs. smart, vision vs. text). The agent is no longer a single brain, but an operating system for AI resources.

- **Local and Private Inference is an Underserved Need**: The strong community interest in Ollama support (NanoBot) and the focus on building local model routers (ZeroClaw) indicate a growing segment of users who are either cost-sensitive or have data privacy requirements that prevent them from using commercial APIs. This is a key area for differentiation.

- **Internationalization is a Business Driver**: The ecosystem is global, with strong demand for Chinese platforms (Feishu, DingTalk, WeChat), Vietnamese localization (CoPaw), and proper handling of multi-byte filenames (OpenClaw). Projects that neglect platform-specific edge cases (e.g., character encoding, locale-specific UI) will lose a significant user base.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-06-14

## 1. Today's Overview

NanoBot is experiencing a period of **very high development activity**, with 18 PRs updated in the last 24 hours (5 merged/closed, 13 open) and 5 issues updated (3 closed, 2 open). The project shows strong momentum across multiple fronts: infrastructure fixes (async cleanup, config resolution), new features (WebUI automation management, TUI client, sub-path support), and provider compatibility (Anthropic models). No new releases were published today, but the volume and diversity of merged PRs suggest a release candidate may be approaching. The community is actively contributing both bug reports and feature implementations, indicating healthy adoption and engaged contributor base.

## 2. Releases

**No new releases published today.** No release artifacts or version bumps are present in the data.

## 3. Project Progress

**Merged/Closed PRs (5 total):**

| PR | Title | Summary |
|----|-------|---------|
| [#4326](https://github.com/HKUDS/nanobot/pull/4326) | fix(memory): summarize full session tail during idle compaction | Addresses #4264 — `idleCompact` now summarizes the full unconsolidated session tail, preserving user corrections and final correct responses |
| [#4327](https://github.com/HKUDS/nanobot/pull/4327) | Fix WebUI startup blocking on slow gateway routes | Moves slow HTTP handlers off gateway event loop; avoids full session JSONL reads for sidebar; fetches only installed CLI apps at startup |
| [#4314](https://github.com/HKUDS/nanobot/pull/4314) | Break tool config schema import cycle | Refactors Pydantic config base into a shared `nanobot.config_base` module to resolve circular imports |
| [#4313](https://github.com/HKUDS/nanobot/pull/4313) | WebUI / config.json settings parity | Closes gap between WebUI settings panels and `config.json`; new API endpoints for temperature, tool limits, dream, channels, memory fields |
| [#4098](https://github.com/HKUDS/nanobot/pull/4098) | Fix exec workspace symlink guard and path precedence | Blocks restricted exec commands from following relative symlinks escaping workspace; prepends `pathAppend` on Unix |

**Key advancements:**
- Memory consolidation now correctly preserves full conversation context during idle compaction (critical for multi-turn correction workflows)
- WebUI startup performance improved by eliminating blocking gateway routes and reducing remote catalog fetches
- Settings parity between WebUI and config.json significantly reduced, enabling more configuration without file editing
- Tool execution security hardened against workspace escape via symlinks

## 4. Community Hot Topics

**Most Active Issues/PRs by Engagement:**

1. **[#193](https://github.com/HKUDS/nanobot/issues/193) — Ollama API support?** (15 comments, CLOSED)
   - *Need:* User asking whether NanoBot supports Ollama API beyond vLLM. The high comment count suggests strong community interest in local/alternative inference backends.
   
2. **[#4333](https://github.com/HKUDS/nanobot/issues/4333) — Anthropic provider sends deprecated temperature to opus-4-8/Fable** (0 comments, but has a fix PR)
   - *Need:* Latest Anthropic models reject `temperature` parameter; only opus-4-7 was exempted. Immediate breakage for all users of new models.
   
3. **[#4322](https://github.com/HKUDS/nanobot/issues/4322) — NameError: 'session_key' is not defined** (1 comment, OPEN)
   - *Need:* Crashes during startup after merging branches, pointing to a subtle regression in prompt-building refactoring.

**Underlying Analysis:**
- The Ollama request (#193) signals demand for **provider diversity and local inference** beyond vLLM. Users want to use widely-adopted local backends without being locked into specific infrastructure.
- The Anthropic temperature issue (#4333) reveals a **testing gap** — the provider's model detection is manually hardcoded rather than dynamically queried from the API. This pattern suggests a need for more robust model capability discovery.

## 5. Bugs & Stability

**Issues Opened Today:**

| Issue | Severity | Summary | Fix Available? |
|-------|----------|---------|----------------|
| [#4333](https://github.com/HKUDS/nanobot/issues/4333) | **Critical** | Anthropic provider sends deprecated `temperature` to opus-4-8 / Fable → 400 error on every request | ✅ [#4334](https://github.com/HKUDS/nanobot/pull/4334) — widen `omit_temperature` check |
| [#4322](https://github.com/HKUDS/nanobot/issues/4322) | **High** | `NameError: 'session_key' is not defined` crashes agent at startup after merge | ❌ No fix PR yet (root cause identified: new `_build_memory_context` method extracted from `build_system_prompt` introduced scope issue) |

**Previously Reported Bugs with Fixes Merged Today:**

- **#4264** (idleCompact losing conversation history) — **FIXED** via [#4326](https://github.com/HKUDS/nanobot/pull/4326)
- **#4083** (pathAppend precedence) — **FIXED** via [#4098](https://github.com/HKUDS/nanobot/pull/4098)
- **#4072** (exec workspace symlink escape) — **FIXED** via [#4098](https://github.com/HKUDS/nanobot/pull/4098)

**Stability Assessment:**
The project is stable for existing workflows but has **two high-severity regressions** affecting new Anthropic model users and users on the `fix/prompt-caching` branch. The Anthropic fix is already submitted as PR #4334. The `session_key` issue (#4322) still lacks a fix.

## 6. Feature Requests & Roadmap Signals

**New Features Proposed in PRs:**

1. **[#4138](https://github.com/HKUDS/nanobot/pull/4138) — `tools.file.enable` toggle for built-in filesystem tools**
   - Allows deployments to restrict NanoBot to MCP-only filesystem access. **High probability for next release** — follows existing `tools.exec.enable` and `tools.web.enable` pattern.

2. **[#4291](https://github.com/HKUDS/nanobot/pull/4291) — Subagent model presets**
   - Subagents can use different models than parent via `spawnPresets` configuration. **Moderate-high probability** — powerful for multi-agent architectures.

3. **[#4330](https://github.com/HKUDS/nanobot/pull/4330) — WebUI automation management view**
   - Full UI for listing, filtering, running automations. **Likely for next release** — already has localization support.

4. **[#4329](https://github.com/HKUDS/nanobot/pull/4329) — Nanobot TUI (text user interface)**
   - Inline interactive TUI for `nanobot agent` with markdown rendering, slash commands, multimodal input. **Significant new capability** — may be deferred for polish.

5. **[#4328](https://github.com/HKUDS/nanobot/pull/4328) — Sub-path / reverse proxy support**
   - Enables serving WebUI under path prefix (e.g., `/nanobot/`). **High probability** — essential for production deployments behind proxies.

**Predictions for Next Version:**
- Anthropic model compatibility fix (PR #4334) — safety-critical
- `tools.file.enable` flag (PR #4138) — follows established patterns
- Sub-path support (PR #4328) — infrastructure essential
- WebUI automation management (PR #4330) — already localized
- TUI likely to be gated behind `--experimental-tui` flag

## 7. User Feedback Summary

**Pain Points Expressed:**
- **Missing Ollama support** (Issue #193): Users want local inference beyond vLLM; 15 comments indicate strong demand
- **Breaking Anthropic model updates** (Issue #4333): Latest models immediately broken — users can't use opus-4-8 or Fable
- **Merge conflicts breaking startup** (Issue #4322): Branch merges causing runtime crashes, indicating CI/test gap for non-trunk branches
- **idleCompact losing corrections** (Issue #4264): FIXED — users reported frustration with their conversation corrections being dropped
- **Missing filesystem tool toggle** (PR #4138): Deployments wanting strict MCP-only access currently can't disable built-in tools

**Use Cases Observed:**
- Multi-turn task completion with user corrections (fixed by #4326)
- Production deployments behind reverse proxies (addressed by #4328)
- Multi-agent workflows needing different model presets (addressed by #4291)
- Internationalization — WebUI automation views include translations

**Satisfaction Signals:**
- High PR contribution rate (18 in 24h) indicates engaged developer community
- Fast bug fix turnaround (Anthropic issue → PR within same day, #4326)
- Config parity improvements (#4313) show attention to user configuration experience

## 8. Backlog Watch

**Items Needing Maintainer Attention:**

1. **[#193](https://github.com/HKUDS/nanobot/issues/193) — Ollama API support?** (15 comments, CLOSED but unresolved)
   - *Concern:* Closed without implementation or documentation of how to use Ollama. If not truly resolved, this is a significant unmet community need. Maintainers should clarify or re-open.

2. **[#4303](https://github.com/HKUDS/nanobot/pull/4303) — Fix MCP generator crash** (OPEN since 2026-06-11, 0 maintainer comments)
   - *Concern:* 3 days without maintainer review for a crash-causing bug in streamable HTTP MCP server session termination. Risk of data loss/corruption.

3. **[#4334](https://github.com/HKUDS/nanobot/pull/4334) — Anthropic fix** (OPEN, submitted same day)
   - *Concern:* Critical severity issue, but PR needs maintainer review and merge. Every user of opus-4-8/Fable is currently blocked.

4. **[#4322](https://github.com/HKUDS/nanobot/issues/4322) — session_key crash** (OPEN since yesterday, 0 maintainer responses)
   - *Concern:* Users merging main into feature branches experience startup crashes. If the `fix/prompt-caching` branch is considered experimental, this may be acceptable, but the pattern suggests a testing gap for branch merges.

**No long-abandoned items** (oldest open item is 5 days). The project maintains active triage cadence.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

Based on the GitHub activity data for **Hermes Agent** on **2026-06-14**, here is the project digest.

---

### 1. Today's Overview

The Hermes Agent project is experiencing **very high activity**, with 50 issues and 50 pull requests updated in the last 24 hours. This indicates a highly engaged development community and a significant maintenance workload. While there are no new formal releases today, the project is processing a massive wave of contributions, including a single "mega bundle" PR containing 86 open PRs. The high volume of open issues (48) and open PRs (48) suggests the team is actively reviewing code and triaging bugs, but the backlog is substantial. Overall, the project is in a state of rapid iteration and scaling, with a clear focus on platform expansion (Telegram, WhatsApp, Matrix) and core stability improvements.

### 2. Releases

**None.** No new versions or releases were published today.

### 3. Project Progress

A total of **2 pull requests** were merged or closed in the last 24 hours. While specific details on these are limited in the top-20 list, the general direction of work is clear from the open PRs.

**Features and Fixes Advanced (via open PRs):**
- **Context & Memory Management:** PR #45941 introduces "knowledge checkpoints" to compaction, aiming to improve the quality of context summarization.
- **Platform Expansions:** Significant work is being done on platform integrations, including WhatsApp Cloud Calling (PR #45863), Feishu markdown tables (PR #45939), and a Linear gateway (PR #40739).
- **User Interface:** The TUI is seeing a major potential upgrade with the proposed `opentui` terminal UI (PR #42922). Other UI fixes include auto-scrolling toggles (PR #44927) and handling macOS desktop startup crashes (PR #45942).
- **Bug Fixes:** A wave of targeted fixes is inbound for Slack's `NO_REPLY` sentinel (PR #30936), Ollama length truncation (PR #45930), desktop model switches (PR #45936), and provider resolution in the model picker (PR #45943).

### 4. Community Hot Topics

The community is most engaged with **platform expansion** and **memory/context stability**.

- **[Issue #10771] Feature Request: Automatic Memory Consolidation (Auto Dream)** (8 comments, 5 👍)
    - **Urgency:** High.
    - **Analysis:** This request for a "Claude Code"-style memory consolidation feature is the most upvoted item. It reflects a core user need for long-term, stable agent memory without manual intervention. The discussion likely highlights deep technical requirements for deduplication and summarization.
    - **Link:** `NousResearch/hermes-agent Issue #10771`

- **[Issue #44428] Support Telegram Bot API 10.1 Rich Messages** (5 comments, 3 👍)
    - **Urgency:** High.
    - **Analysis:** Two duplicate issues for this feature were filed in the last 24 hours (#44428, #45864), indicating strong demand from the Telegram user base. The community wants Hermes to leverage Telegram's latest rich formatting (tables, LaTeX, collapsible blocks).
    - **Link:** `NousResearch/hermes-agent Issue #44428`

- **[Issue #42366] Hermes Desktop chat does not auto-scroll** (2 comments, 3 👍)
    - **Urgency:** High.
    - **Analysis:** A core usability bug in the Desktop app. The reaction count suggests this is a widespread pain point, but the low comment count indicates the root cause is clear and doesn't require extensive debate. A fix is proposed in PR #44927.
    - **Link:** `NousResearch/hermes-agent Issue #42366`

- **[PR #45925] Mega bundle: 86 open PRs** (Created by AIalliAI)
    - **Analysis:** This PR itself is a community hot topic. The author has manually cherry-picked 86 open PRs into a single branch for integrated testing. This indicates a massive backlog and a contributor's attempt to unblock the review process. It signals potential maintainer bottlenecking.
    - **Link:** `NousResearch/hermes-agent PR #45925`

### 5. Bugs & Stability

Several critical and high-severity bugs were reported, particularly around Windows, memory, and specific platforms.

| Severity | Issue | Title | Fix PR |
| :--- | :--- | :--- | :--- |
| **Critical** | #45931 | WeChat gateway polling hangs + encoding issues on Chinese Windows | None |
| **High** | #45921 | TUI: Directory selection button missing if too many directories | None |
| **High** | #45877 | Cron background review blocks read-only tools (read_file, search_files) | None |
| **High** | #45783 | Tool call burst on session resume causes massive credit spikes | None |
| **High** | #45792 | Hermes Agent inside docker doesn't understand its environment | None |
| **Medium** | #45813 | HTTP 400: Bad Request with Github Copilot provider | None |
| **Medium** | #45860 | Three bugs found related to Windows Installation (missing exe, prompt) | None |
| **Medium** | #43586 | `model:` block with bare `provider: custom` ignores the API key | None |
| **Low** | #42366 | Desktop chat does not auto-scroll | #44927 |
| **Low** | #40187 | `hermes desktop` fails to compile on macOS | None |

**Key Stability Risks:**
- **Windows/Locale Issues:** Multiple reports of encoding errors (`gbk` codec) on Chinese Windows are emerging, suggesting a systemic issue with file reading in different locales.
- **Memory/Context Hangs:** Bug #42405 describes a silent hang when memory is at capacity, which is a critical non-responsive state for any agent.

### 6. Feature Requests & Roadmap Signals

The most likely features for the next version are those with high community demand and open PRs.

- **Likely Next (v0.16+):**
    - **Web UI Gateway:** Issue #501 is closed, signaling this high-profile feature is likely in the final stages of testing or already merged.
    - **Telegram Bot API 10.1 Rich Messages:** With two duplicate feature requests and a linked PR (#45854), this is a strong candidate.
    - **Automatic Memory Consolidation ("Auto Dream"):** The high number of 👍 on issue #10771 makes this a priority for the roadmap.
- **Potential Next:**
    - **OpenTUI as the New Default TUI:** PR #42922 is a massive overhaul of the terminal interface. While experimental, it signals a future direction.
    - **WhatsApp Cloud API Message Templates:** Issue #45935 from a "real production use case" for re-engagement pushes this beyond a mere feature request.
    - **Planning Consultant (Model-initiated Frontier Model Review):** Issue #19344 suggests a sophisticated feature for using cheaper models with expensive "consultant" models for complex tasks.

### 7. User Feedback Summary

- **Pain Points:**
    - **Windows/Locale Instability:** Users on Chinese Windows are experiencing severe issues, from encoding crashes to gateway polling hangs (#45931, #45932).
    - **Desktop Usability:** The lack of auto-scrolling in the Desktop app (#42366) and a missing scrollbar for directory selection (#45921) degrade the user experience.
    - **Cost & Credit Spikes:** Users are frustrated by unexpected API credit costs caused by tool-call bursts on session resume (#45783).
    - **Configuration Confusion:** Several bugs related to `api_key_env` and provider configuration (#43586, #44666) are causing authentication failures, indicating documentation or clarity issues.
- **Use Cases:**
    - **Production Deployments:** A user is running an engine-machining business and needs WhatsApp template support for re-engagement (#45935).
    - **Advanced Workflows:** A user built an internal "CPRC Health Engine" on top of Hermes for text evaluation, demonstrating the platform's use as a base for custom AI tools (#22417).
    - **Cost Optimization:** Users are actively trying to use cheaper models (DeepSeek V4, Qwen 3.6) for everyday tasks and want features like the "Planning Consultant" to call more expensive models only when needed (#19344).

### 8. Backlog Watch

Several important items are at risk of being overlooked due to the high volume of recent activity.

- **[Issue #23975] Context compression interrupted by gateway messages** (May 11, 2026)
    - **Why it matters:** This is a core stability bug that can corrupt conversation context, leading to incorrect agent behavior.
    - **Link:** `NousResearch/hermes-agent Issue #23975`

- **[Issue #19245] `session_search` returns empty after crash** (May 3, 2026)
    - **Why it matters:** This is a data loss bug. Orphaned session files are not recovered, potentially losing important agent work.
    - **Link:** `NousResearch/hermes-agent Issue #19245`

- **[Issue #31155] `delegation.model` override ignored** (May 23, 2026)
    - **Why it matters:** This negates a core feature (delegation) and prevents users from optimizing cost and performance effectively.
    - **Link:** `NousResearch/hermes-agent Issue #31155`

- **[PR #22532] feat: add Telegram clarify prompts** (May 9, 2026)
    - **Why it matters:** This is a significant UX improvement for one of the most popular platforms. Its age and lack of update suggest it may need maintainer attention to resolve merge conflicts or code review feedback.
    - **Link:** `NousResearch/hermes-agent PR #22532`

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest
**Date:** 2026-06-14

## Today's Overview
PicoClaw shows moderate activity over the past 24 hours with 7 pull requests and 2 issues updated, including the release of a new nightly build (v0.2.9-nightly.20260614.cf67dd38). The project saw strong code churn on the fix side: 5 PRs were merged or closed, addressing linter warnings, image hallucination bugs, TTS configuration improvements, and media routing logic. However, one notable long-standing bug (#3012) involving continuous token consumption with Evolution enabled remains open with no fix PR attached. Overall, the project appears healthy with steady improvements, though the nightly build carries a stability warning.

## Releases
**Nightly Build: v0.2.9-nightly.20260614.cf67dd38**
- This is an automated nightly build that may be unstable.
- Includes changes merged into `main` since v0.2.9.
- No breaking changes or migration notes documented for this release.
- **Full Changelog:** [v0.2.9...main](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)

## Project Progress
Five PRs were merged or closed in the last 24 hours, advancing several fix areas:

- **#3119 (fix/tts)** — Support OpenRouter voice overrides on a per-model basis using `extra_body`; adds auto-retry fallback when `response_format` causes errors. Improves TTS flexibility and resilience.
- **#3117 (fix/agent)** — Routes media turns and `load_image` follow-ups to the configured image model instead of retrying on a text-only model. Fixes a hallucination bug (#3108) where image descriptions were unrelated to actual content.
- **#3065 (fix/seahorse)** — Explicitly ignores `Close()` errors on PRAGMA/migration failure paths to silence linter warnings.
- **#3066 (fix)** — Explicitly ignores `Close()` errors on temp file write/sync failure paths across normalization, WeChat media, and filesystem tools.
- **#2935 (stale/docs)** — Traditional Chinese (zh-TW) locale and READMEs merged, improving i18n coverage for documentation and frontend.

Two PRs remain open:
- **#2964 (Feat/image input compression)** — Configurable multi-level image compression before building the model payload.
- **#3118 (Feat/remote WebSocket mode)** — Adds `--remote` flag to `picoclaw agent` for connecting to a remote WebSocket endpoint.

## Community Hot Topics
- **#3012 — [BUG] Continuous token consumption every minute when evolution is enabled**
  - *Author:* xpader | *Comments:* 3 | *Status:* Open, updated 2026-06-13
  - This issue has been open since June 5 and has seen regular discussion. The bug causes token drain even with no user interaction when Evolution mode is on (Draft mode, Code Path Trigger). This has been a persistent pain point for users running cost-sensitive deployments.
  - [Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)

- **#3108 — [BUG] Image description hallucinations with non-vision models** (now closed)
  - *Author:* afjcjsbx | *Comments:* 0 | *Status:* Closed
  - While this issue has zero comments, it was the trigger for PR #3117 which was just merged. The community's underlying need is clear: PicoClaw should intelligently route vision tasks to vision-capable models rather than hallucinating responses.
  - [Issue #3108](https://github.com/sipeed/picoclaw/issues/3108)

The most active open PR is **#2964 (image input compression)** which has been open since May 28 and continues to receive updates — it's a significant feature for users with bandwidth or cost constraints.

## Bugs & Stability

**High Severity (Open, No Fix PR Yet)**
- **#3012** — Continuous token consumption every minute when Evolution is enabled (open since 2026-06-05). Likely a logic loop or polling behavior in the Evolution subsystem. No associated fix PR. **High severity** for users running pay-per-token models.
  - [Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)

**Medium Severity (Fixed Today)**
- **#3108** — Image description requests hallucinate when active model lacks vision support. Fixed by PR #3117.

**Low Severity (Fixed Today)**
- Linter warnings for unhandled `Close()` errors in `pkg/seahorse`, `pkg/tools`, and `pkg/channels` — all fixed via PRs #3065 and #3066. Not user-facing but improves code quality.

## Feature Requests & Roadmap Signals

- **Image input compression (PR #2964)** — Configurable multi-level compression for inbound images before model payload construction. Currently open, likely to land in the next nightly build after review. This addresses user needs for controlling vision pipeline costs and latency.
- **Remote WebSocket agent mode (PR #3118)** — A new `--remote` flag for the `picoclaw agent` command to connect to remote WebSocket endpoints. Likely targets team collaboration or server-managed agent scenarios. May appear in v0.3.0 depending on testing.
- **TTS voice overrides (PR #3119, merged)** — The `extra_body` field for per-model voice customization will likely appear in the next stable release, improving PicoClaw's integration with multiple TTS providers.

**Prediction for v0.3.0:** Image compression (PR #2964) and remote agent mode (PR #3118) are strong candidates based on current PR activity and community interest.

## User Feedback Summary
- **Pain point: Token waste with Evolution** — Issue #3012 shows a clear cost-sensitivity among users. Running Evolution (Draft mode) should not silently burn tokens every minute. Users are seeking a fix or a configurable polling interval.
- **Pain point: Vision model routing** — Issue #3108 forced users to manually ensure image tasks go to vision-capable models. The fix in PR #3117 addresses this, which should improve satisfaction among users of OpenRouter and multi-model setups.
- **Satisfaction signals:** The quick turnaround on fixing #3108 (issue filed June 11, fix merged June 13) suggests maintainers are responsive to clarity-related bugs. The i18n PR (#2935) for Traditional Chinese indicates community investment in localization.

## Backlog Watch
- **Issue #3012 (token consumption bug, open since 2026-06-05)** — No associated fix PR. This is the most important open bug by severity and duration. Needs maintainer attention to confirm reproduction and assign a fix.
- **PR #2964 (image compression, open since 2026-05-28)** — Important feature that has been open for over two weeks. Appears ready for final review and merge. Maintainer review is needed to prevent feature drift.
- **PR #3118 (remote WebSocket mode, open since 2026-06-12)** — Brand new feature that may require architectural discussion before merge. No maintainer comments yet as of this digest.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-06-14

## Today's Overview

NanoClaw shows **moderate-to-high** development activity today, driven primarily by a cluster of merged PRs advancing provider extensibility and credential management. The only Issue updated in the last 24 hours was a spam/erroneous deletion request. Six PRs were updated, with **4 merged/closed** and **2 remaining open**. No new releases were published. The project appears to be in a **stabilization + feature-adding phase**, with the core team addressing health audit findings and hardening container lifecycles while simultaneously landing new provider capability seams.

---

## Releases

**No new releases** were published in the last 24 hours. The last available release (not provided) remains the current stable target. Developers should watch for an upcoming release incorporating the merged features below.

---

## Project Progress — Merged/Closed PRs (4 items)

All four merged PRs were authored by **omri‑maya** and closed on 2026‑06‑13, representing a coordinated batch of provider‑side feature work:

1. **#2754 — `onExchangeComplete` provider hook + slash‑command interruption**  
   URL: https://github.com/nanocoai/nanoclaw/pull/2754  
   Adds an optional lifecycle hook for providers and a mechanism to interrupt long‑running agent exchanges via slash commands. This is a core source‑seam change, not a skill.

2. **#2747 — SDK 2.2.1 bump + credential‑stub mounts + machine‑checkable pins**  
   URL: https://github.com/nanocoai/nanoclaw/pull/2747  
   Dependencies upgraded (`@onecli-sh/sdk` 0.5.0 → 2.2.1). Introduces credential‑stub mounts for secure container‑side credential injection and pin‑based verification.

3. **#2746 — Agent‑surfaces capability seam for providers**  
   URL: https://github.com/nanocoai/nanoclaw/pull/2746  
   A host‑side registry where providers declare surface capabilities (e.g., Slack, Discord, WebSocket), enabling dynamic routing of agent outputs to appropriate channels.

4. **#2745 — Opt‑in persistent memory scaffold for providers**  
   URL: https://github.com/nanocoai/nanoclaw/pull/2745  
   Adds a `usesMemoryScaffold` capability and a container‑side persistence contract, allowing providers to request and manage long‑term memory for agents.

**Key theme**: These merges collectively build out a **pluggable provider framework** — lifecycle hooks, memory, surface declarations, and secure credential handling — making NanoClaw more extensible for custom integration.

---

## Community Hot Topics

No Issues or PRs today show significant comment or reaction activity. The single Issue (#2755) was a deletion request with zero engagement.

**Notable PRs with ongoing activity (both open):**

- **#2750 (OPEN)** — Critical container journal recovery fix.  
  URL: https://github.com/nanocoai/nanoclaw/pull/2750  
  *Author: sturdy4days*  
  Addresses two related failure modes (`#2516`, `#2640`) where `outbound.db` journals become stale after container SIGKILLs or host systemd kills. Includes `db-journal-wal-persistent` mount and a `LiteMap`‑backed journal recovery fallback. **Most impactful open PR for stability.**

- **#2732 (OPEN)** — Hardening from health audit.  
  URL: https://github.com/nanocoai/nanoclaw/pull/2732  
  *Author: caburi00*  
  A multi‑agent adversarial audit foundings: bind‑mount realpath fix for Docker Desktop crashes, crash‑on‑spawn circuit breaker, `MAX_CONCURRENT_CONTAINERS` enforcement, daemon‑level `docker kill` fallback, plus agent‑runner fixes for graceful teardown and outbound session timeouts. **Large surface‑area stability patch.**

**Underlying needs**: The community is clearly experiencing **production container‑lifecycle failures** — stale database journals, crash loops on Docker Desktop, and resource exhaustion. The open PRs indicate maintainers are actively responding to these operational pain points.

---

## Bugs & Stability

| Severity | Bug | Issue/PR | Status |
|----------|-----|----------|--------|
| **High** | Stale `outbound.db` journals after container SIGKILL | #2750 (fix PR) | Open — fix drafted |
| **High** | Host systemd‑kill causes hot‑journal poll races | #2750 (fix PR) | Open — included in same fix |
| **High** | Docker Desktop drvfs staging crash‑loop (exit 127) | #2732 (fix PR) | Open — realpath bind‑mount fix |
| **Medium** | Crash‑on‑spawn without circuit breaker | #2732 (fix PR) | Open — circuit breaker added |
| **Medium** | No `MAX_CONCURRENT_CONTAINERS` enforcement | #2732 (fix PR) | Open — enforcement added |
| **Low** | Container‑side agent‑runner teardown failures | #2732 (fix PR) | Open — `tini` → `dumb-init`, `kill -TERM` logic |

**No new bugs were reported today** via Issues. The two open PRs (#2750, #2732) serve as the primary fix vehicles for known production issues. All high‑severity items have **corresponding fix PRs already open**.

---

## Feature Requests & Roadmap Signals

No new feature requests were filed today. However, the merged PRs from omri‑maya strongly signal the roadmap direction:

| Signal | Source | Likely Next‑Version Inclusion |
|--------|--------|-------------------------------|
| Provider‑side exchange hooks (`onExchangeComplete`) | #2754 merged | **Very likely** |
| Persistent memory scaffold for providers | #2745 merged | **Very likely** |
| Agent‑surfaces capability seam (multi‑channel routing) | #2746 merged | **Very likely** |
| SDK 2.2.1 with credential‑stub mounts | #2747 merged | **Very likely** |
| Container journal recovery + staleness hardening | #2750 open | **Likely** in next minor release |
| Health audit hardening (circuit breaker, concurrency, Docker Desktop) | #2732 open | **Likely** in next minor release |

**Prediction**: The next NanoClaw release will be **vX.Y.0** (minor bump) incorporating the four merged provider‑seam PRs, plus possibly one of the open stability PRs, focusing on **extensibility + production reliability**.

---

## User Feedback Summary

- **No new user feedback** recorded in Issues or PR comments today. The only Issue was a deletion request.
- The two open PRs (#2750, #2732) implicitly reflect **real pain points** from production users:
  - Container SIGKILL/stale database journals
  - Docker Desktop incompatibility (drvfs path handling)
  - Resource limit enforcement gaps
  - Graceful shutdown timeouts
- Satisfaction indicators: The four merged provider PRs suggest **positive collaboration** with core contributors (omri‑maya); the health audit (#2732) indicates proactive adversarial testing rather than user‑reported complaints.

---

## Backlog Watch

- **No long‑unanswered Issues or PRs** are currently visible in the 24‑hour window. All items updated today are either recently opened (last 2–3 days) or recently merged.
- The two open PRs (#2750, #2732) are both **actively maintained** — last updated today — and are not stalled. No PRs show reviewer inactivity or maintainer ping‑debt.

**Assessment**: The backlog is clean. No items require urgent maintainer attention beyond the normal review cycle for the two open stability PRs.

---

*Generated from NanoClaw GitHub data snapshot — 2026-06-14.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-06-14

## Today's Overview
NullClaw is currently in a low-activity period with no new releases and only two items updated in the last 24 hours. One critical bug remains open (Issue #941) where agent-type cron jobs fail to deliver messages, and a corresponding fix PR (#954) was submitted yesterday and is awaiting review. Community engagement is focused on a single, well-documented reliability issue rather than broader feature work, suggesting the project is in a stabilization phase. With no merged PRs or closed issues today, maintainer attention appears to be on reviewing the pending fix rather than shipping new functionality.

## Releases
No new releases. The latest release remains unchanged.

## Project Progress
**Merged/Closed PRs today:** None

**Open PR (awaiting review):**
- [#954 [OPEN] Fix: one-shot cron jobs silently fail to deliver messages (use-after-free in OutboundMessage.channel)](https://github.com/nullclaw/nullclaw/pull/954) — Submitted by vernonstinebaker, this PR directly addresses Issue #941. The fix identifies a **use-after-free** bug where the `OutboundMessage.channel` pointer becomes invalid after cron job deletion from `cron.json`, causing the message delivery pipeline to silently drop all outputs. The PR modifies the job execution lifecycle to ensure channel references remain valid until message delivery completes.

## Community Hot Topics
**Most active issue:**
- [#941 [OPEN] Agent-type cron jobs don't spawn a subprocess — Telegram delivery never happens](https://github.com/nullclaw/nullclaw/issues/941) — **7 comments**, created 2026-05-31, updated 2026-06-13
  - **Author:** weissfl
  - **Underlying need:** Users running scheduled agent tasks (e.g., daily reports, alerts) require reliable, async message delivery to Telegram or other channels. The current behavior (job marked complete but no subprocess spawned) breaks trust in the scheduling system and makes NullClaw unusable for automated workflows that depend on agent output.
  - **Analysis:** This issue reveals a fundamental lifecycle bug in the cron/agent integration. The high comment count (7 over two weeks) without maintainer response until the PR appeared suggests community members have been self-debugging and converging on the root cause. The fact that the fix PR (#954) arrived from a different contributor indicates this is a reproducible, clear-cut bug rather than a design debate.

## Bugs & Stability
**Active bugs (ranked by severity):**

| Severity | Issue | Description | Fix PR Exists? |
|----------|-------|-------------|----------------|
| **Critical** | [#941](https://github.com/nullclaw/nullclaw/issues/941) | Agent-type cron jobs silently fail to deliver messages via any channel. Job completes, subprocess never spawned, no output. | ✅ Yes (#954) |
| Medium | None | No new bugs reported today | — |

**Analysis:** The single active bug is rated **Critical** because it involves silent data loss — users have no indication their scheduled agent tasks are failing. The "use-after-free" root cause in PR #954 suggests this could affect all channel types (Telegram, Mattermost, etc.) and not just the reported Telegram case. If merged and released, this fix would restore trust in NullClaw's cron scheduling system.

## Feature Requests & Roadmap Signals
No new feature requests were submitted today. The current community focus is entirely on stability and bug fixing. **Prediction:** The next release will likely focus on the cron/agent delivery fix from PR #954, with no feature additions. This signals that NullClaw's maintainers are prioritizing reliability over new capabilities.

## User Feedback Summary
- **Pain point (repeatable):** Scheduled agent tasks that "complete" silently without delivering results. User weissfl documented step-by-step reproduction steps, indicating this is a production-blocking issue for their workflow.
- **Use case highlighted:** Automated asynchronous delivery of agent outputs to Telegram (and potentially Mattermost) via cron-style scheduling. This is critical for users relying on NullClaw for notification/alerting pipelines.
- **Satisfaction:** Not directly measured, but the 7-comment thread without maintainer response until the PR arrived suggests moderate frustration. The community self-diagnosed the issue, which shows engaged users but also indicates a gap in maintainer responsiveness.

## Backlog Watch
**Items needing maintainer attention:**

1. **[#941 Agent-type cron jobs don't spawn a subprocess](https://github.com/nullclaw/nullclaw/issues/941)** — Created 2026-05-31 (14 days open). The issue has a fix PR (#954) submitted yesterday. **After two weeks with no official response**, this now needs maintainer review, testing, and either merge or feedback on the proposed approach. This is the most actionable item in the backlog.

2. **[#954 Fix: one-shot cron jobs silently fail](https://github.com/nullclaw/nullclaw/pull/954)** — Submitted 2026-06-13. **Awaiting maintainer review.** The PR has been open for less than 24 hours, so this is not yet "long-unanswered," but it is the critical path to resolving Issue #941. Timely review would signal responsiveness to the community.

**No other long-unanswered issues detected** — the project's backlog appears clean outside this single active bug thread.

---

**Project Health Assessment:** NullClaw is in a low-activity but focused state. The single critical bug has a community-sourced fix ready for review. The project would benefit from a maintainer response on both #941 and #954 within the next 2-3 days to demonstrate active maintenance and prevent user churn. No feature regressions or breaking changes are in flight, making this an ideal time for a stabilization release.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-06-14

## Today's Overview

IronClaw shows **moderate-to-high activity** today with 24 PRs updated in the last 24 hours (17 open, 7 merged/closed) and 2 open issues. The project appears in a **heavy development sprint** focused on attachment handling, Slack integration stability, and runtime infrastructure—all core to the Reborn binary. No new releases were cut today, but a long-running release PR (#3708) covering breaking changes in `ironclaw_common` (0.5.0) and `ironclaw` (0.29.1) continues to be updated. Core contributors are processing a backlog of feature work across at least five parallel tracks.

## Releases

No new releases today.

*(The open release PR #3708, which has been active since May 16, continues to accumulate changes; see Project Progress.)*

## Project Progress

**7 PRs merged or closed today**, spanning feature delivery, dependency housekeeping, and refactoring:

- **#4675** (merged) — `refactor(extractors)`: Extracted document text-extraction into a standalone `ironclaw_extractors` crate, decoupling it from attachment-specific code. This unblocks the attachment ingestion pipeline.
- **#4672** (merged) — `feat(reborn)`: End-to-end inbound attachment support for WebChat v2—browser file uploads now land in project storage and persist as transcript attachment references.
- **#4670** (merged) — `feat(attachments)`: The byte-landing bridge connecting storage to `AttachmentRef`s in the transcript contract.
- **#4668** (merged) — `feat(attachments)`: `MountView`-based attachment landing crate providing the storage foundation for attachment bytes.
- **#4655** (merged) — `feat(threads)`: Expanded the Reborn transcript contract to carry attachment references (never bytes) so uploads survive from ingestion to persistence.
- **#4242** (closed) — `chore(deps)`: Security bump of `tar` crate from 0.4.45 → 0.4.46 (PAX header fix).

Collectively, this represents delivery of **Tracks 1-3 and Track 6** of the attachment epic (#4644). The attachment pipeline is now wired end-to-end: file upload → byte storage → extracted text → model-visible context.

## Community Hot Topics

The most active items today center on **Slack stability and runtime-hang fixes**:

- **#4839** — *[SLACK RE-APPROVAL LOOP FIX]* — This large PR (XL, 17 comments) addresses a critical bug where capability invocations requiring both one-shot approval and a credential (e.g., Gmail OAuth) demanded a new human approval on every resume cycle. The core fix extracts shared resume-authority dispatch logic into `CapabilityHost::dispatch_resumed_capability`. Underlying need: **eliminating UX-wrecking approval loops in Slack workflows**.

- **#4838** — *[BUSY THREAD HANDLING]* — Replaces the previous "park-and-drain" approach for messages arriving while a thread is busy with explicit rejection + user-facing notice. This simplifies runtime behavior. Underlying need: **predictable thread concurrency behavior and no silent message loss**.

- **#4841** — *[NO RUN-BORKING FAILURES]* — Seeks to eliminate "run-borking" terminal errors where failures (host unavailable, model failure, protocol error) produce opaque errors with no recovery path. Proposes failure explanations + retryable failed runs. Underlying need: **observable, recoverable runtime failures**.

- **#4777** — *[PERSIST SLACK CONNECTED STATE IN WEBUI]* — Fixes a Slack reconnect loop by making WebUI/channel state reflect an existing Slack delivery connection instead of always showing "disconnected." Underlying need: **correct connection state UI that prevents infinite reconnect loops**.

## Bugs & Stability

**High Severity:**

- **#4108** (open since May 27) — **Nightly E2E tests are failing** on the `v2-engine` workflow. No comments or fix PRs yet. This is the longest-standing test failure on the board and represents a regression risk for every commit. *Severity: High* — blocks CI confidence for all subsequent changes.

- **#4839** (open, fix PR exists) — Slack re-approval loop where capability calls cycle through multiple approval gates. The fix (preserving invocation identity across auth-gate re-dispatch) is in PR review. *Severity: High* — directly impacts Slack UX and user trust.

- **#4844** (open, fix PR exists) — Gate delivery filtering was allocating per-route and using incorrect function signatures (`fn(&GateRef)` instead of `fn(&str)`), causing auth vs. approval misclassification. *Severity: Medium* — caused wrong gate buttons to appear in Slack.

- **#4843** (open, fix PR exists) — Single-flight gate delivery failure: gate-resolution acks carry the same `run_id` as the original user message, causing the original delivery loop to misinterpret the ack. *Severity: Medium* — fanout bug causing duplicate or missed resolution processing.

**Medium Severity:**

- **#4846** (open, fix PR exists) — Bare `workspace/...` file-tool paths were being nested under `/workspace/workspace/...` instead of `/workspace/...`. Fix normalizes tool paths. *Severity: Medium* — produces broken file paths in workspace operations.

- **#4842** (open, fix PR exists) — The QA-trace recorder blocks indefinitely when encountering an interactive auth gate (e.g., "connect to Gmail") because `wait_for_terminal` expects a terminal status. Fix records traces to terminal-or-gate instead of hanging. *Severity: Medium* — blocks QA automation.

## Feature Requests & Roadmap Signals

The dominant roadmap signal is the **attachment epic (#4644)**, which is now substantially delivered across its implementation tracks:

- **Track 1** (Registry, PR #4654): *Merged earlier.*
- **Track 2** (Transcript AttachmentRefs, PR #4655): *Merged today.*
- **Track 3** (Model-Visible Context, PR #4677): *Open, in review.*
- **Track 6** (Byte Storage Foundation, PR #4668): *Merged today.*
- **Inbound Landing** (PR #4676): *Open, in review.*
- **WebChat v2 End-to-End** (PR #4672): *Merged today.*

**Expected next release will include:** Full attachment support (upload → storage → extraction → model-visible), the refactored `ironclaw_extractors` crate, and the Slack stability fixes (#4839, #4844, #4843). The runtime-context feature (#4836) surfacing connected channels and delivery state to the model is also likely to land.

**Routine creation API** (PR #4264 by new contributor wcc945) remains open and could ship in a subsequent release if it receives final review.

## User Feedback Summary

While no direct user comments appear in issue discussions today, the following user pain points can be inferred from bug reports and PR motivations:

- **Slack approval loops** (multiple PRs, #4839): "Every Slack capability call demands 4+ approvals." This is a real usability disaster—users cannot complete Gmail or other OAuth actions without hitting repeated authorization gates.
- **Silent message loss / thread hangs** (#4838): Users were likely experiencing messages vanishing into "parked" state with no feedback. The fix (explicit rejection with notice) is user-friendly by design.
- **Connection state confusion** (#4777): Slack "disconnected" state displayed even when delivery connection was active, causing users to re-initiate connection flows unnecessarily.
- **Opaque failures** (#4841): Terminal errors with no explanation and no recovery path—users hitting "run-borking" would see a dead run with no actionable information.

Overall sentiment appears to be **early-adopter frustration**—the Reborn binary is shipping new features (attachments, Slack integration) faster than stabilization, and users are experiencing the rough edges. The team is responsive, with fix PRs for all major issues landing within 1-2 days of identification.

## Backlog Watch

**Critical:**

- **#4108** ([Nightly E2E Failed](https://github.com/nearai/ironclaw/issues/4108)) — Open since **May 27** (18 days). No maintainer response, no fix PR. This nightly test failure on the `v2-engine` workflow means every commit is running with unknown CI risk. **This should be the team's top priority for triage.**

**Stale—Requesting Maintainer Attention:**

- **#4264** ([feat(gateway): add routine create endpoint](https://github.com/nearai/ironclaw/pull/4264)) — Open since May 31 by new contributor wcc945. Last updated June 13. No reviewer assigned. This is a straightforward feature PR from a new contributor that has been waiting over two weeks for maintainer review. Risk of contributor discouragement.

- **#3708** ([chore: release](https://github.com/nearai/ironclaw/pull/3708)) — Open since **May 16** (29 days). This release PR covers breaking changes in two core crates (`ironclaw_common` 0.5.0, `ironclaw` 0.29.1) and is still accumulating commits. The delay suggests either unresolved API disputes or blocked on feature freeze. The project is shipping code faster than it can release.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **2026-06-14**.

---

# 🦞 LobsterAI Project Digest | 2026-06-14

## 1. Today's Overview
The LobsterAI project shows **low activity** over the last 24 hours, with no new issues, pull requests, or releases created during this window. Four existing issues and five PRs received updates (mostly labeling or stale-bot activity), all of which are over two months old. The project appears to be in a **maintenance phase**, with no recent code merges or critical bug reports surfaced today. The health is stable but momentum has slowed significantly since early April.

## 2. Releases
**No new releases.**

The latest release remains dated prior to the current date. No migration notes or breaking changes to report.

## 3. Project Progress
**No new commits were merged or closed today.**  
However, two PRs recently closed (within the last 24h refresh cycle) are worth noting:

- **#1466** [CLOSED] – *fix(mcp): modal close button unreachable when content grows tall*  
  Author: linlihua | [PR Link](https://github.com/netease-youdao/LobsterAI/pull/1466)  
  Fixes a UI usability bug where the MCP server form modal’s close button scrolled out of view. The fix refines scroll behavior to keep header/footer visible.

- **#1467** [CLOSED] – *fix(shortcuts): display Cmd (⌘) instead of Ctrl on macOS*  
  Author: linlihua | [PR Link](https://github.com/netease-youdao/LobsterAI/pull/1467)  
  Corrects a platform-display bug where macOS users saw "Ctrl" instead of "⌘" in the Settings > Shortcuts panel.

## 4. Community Hot Topics
**No active discussion today.** All four updated issues and five PRs have **zero reactions** and minimal comments (1-2 each). The most notable conversation remains:

- **#1443** – *有计划支持新版本的openclaw吗？ (Will you support the new version of OpenClaw?)*  
  Author: Juzisuan965 | [Issue Link](https://github.com/netease-youdao/LobsterAI/issues/1443)  
  A user reports breakage after upgrading to OpenClaw v2026.3.24, which introduced a breaking change. The underlying need is **compatibility with upstream dependency updates** – low urgency but potentially blocking for users who need the latest OpenClaw features.

## 5. Bugs & Stability
**No new bugs reported today.**  
The bug backlog remains static, with several stale open issues. The highest severity item still unresolved:

- **[High] #1437** – *创建定时任务时，计划选择不重复，清空日历，点击【创建任务】按钮没反应*  
  Link: [Issue #1437](https://github.com/netease-youdao/LobsterAI/issues/1437)  
  ✅ **No fix PR exists.** This is a UI/UX bug where a blank calendar + "No repeat" schedule makes the create button silently fail.

- **[Medium] #1439** – *上传技能已停用，对话中仍然可以调用*  
  Link: [Issue #1439](https://github.com/netease-youdao/LobsterAI/issues/1439)  
  ✅ **No fix PR exists.** Disabled skills still trigger in conversation – a correctness issue affecting agent reliability.

## 6. Feature Requests & Roadmap Signals
Two feature-relevant PRs are **open and stale**, signaling that these enhancements may be candidates for the next release:

- **#1440** [OPEN] – *feat(cowork): 将已选技能标签移至输入框内顶部展示*  
  Link: [PR #1440](https://github.com/netease-youdao/LobsterAI/pull/1440)  
  UI improvement to move selected skill badges above the input area, decluttering the toolbar. Likely to ship if merged.

- **#1441** [OPEN] – *feat(artifacts): add extensible preview pipeline for HTML, React and Mermaid*  
  Link: [PR #1441](https://github.com/netease-youdao/LobsterAI/pull/1441)  
  A substantial feature (conflict-resolved fork of #1011) adding rich artifact previews. This is the strongest roadmap signal – if merged, it would significantly enhance the cowork session experience.

## 7. User Feedback Summary
- **Positive Usability Feedback:** The fix in PR #1467 (Cmd vs Ctrl on macOS) addresses a common platform-polish complaint – users are likely satisfied with the correction.
- **Frustration with Silent Failures:** Issue #1437 (task creation button unresponsive with no error toast) suggests users are encountering silent UI failures, which erode trust in form workflows.
- **Confusion Around Agent Skills:** Issue #1442 describes a scenario where selected skills disappear after a conversation turn – the user explicitly asks *"what is the purpose of selecting skills?"* This indicates **poor UX documentation** or unclear design intent for the agent-skill binding feature.
- **Low Community Engagement:** The lack of comments, reactions, and upvotes on all 9 updated items suggests the user base is either not actively giving feedback or the project has a small audience.

## 8. Backlog Watch
Several important issues and PRs have been **open for over 70 days** with no maintainer response:

| Item | Author | Days Stale | Maintainer Needed? |
|------|--------|------------|---------------------|
| **#1443** – OpenClaw support | Juzisuan965 | ~72 days | ✅ Yes – breaking dependency change |
| **#1439** – Disabled skills still callable | devilszy | ~72 days | ✅ Yes – functional correctness bug |
| **#1442** – Skills disappear after chat | devilszy | ~72 days | ✅ Yes – suggests design flaw or bug |
| **#1441** – Artifacts preview pipeline | febugcoder | ~72 days | ⏳ Needs review/merge decision |

**Priority attention needed:** Issue #1443 (OpenClaw breaking change) could block users attempting to deploy with modern dependencies. PR #1441 is a large feature with resolved conflicts – it should be reviewed or explicitly shelved to avoid indefinite stall.

---

*Data source: GitHub – github.com/netease-youdao/LobsterAI*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-06-14

## Today's Overview
The Moltis project saw low activity over the past 24 hours, with 1 open issue and 3 open pull requests, but no merged changes or new releases. The primary focus is on a critical OAuth integration bug affecting popular MCP servers like Notion and Linear, which has attracted developer attention and an associated fix PR. The team is also addressing a Docker infrastructure issue related to volume shadowing in deployments. Overall, the project is in a stable but reactive state, with maintainers actively working on blocking bugs and dependency upkeep.

## Releases
No new releases were published today. The last release remains unchanged.

## Project Progress
No pull requests were merged or closed today. Open PRs in progress include:
- **PR #1122** — Fix to drop `VOLUME` declarations in the Dockerfile that shadow the home bind mount, which can break deployments mounting the entire home directory.
- **PR #1121** — Automated dependency bump for `esbuild` from 0.25.12 to 0.28.1 in the web UI crate.
- **PR #1120** — Fix for MCP OAuth `invalid_target` error, directly addressing the top open issue.

## Community Hot Topics
- **Issue #1119** (1 comment, 0 👍) — [Bug: MCP OAuth fails with `invalid_target` for servers using `resource_metadata` in WWW-Authenticate](https://github.com/moltis-org/moltis/issues/1119)  
  This is the most active item today, reported by user `xzavrel`. The issue blocks adding remote MCP servers (Notion, Linear) that use OAuth with `resource_metadata`. The underlying need is seamless third-party MCP server integration, which is a core workflow for Moltis users. A fix PR (#1120) from the same author has already been submitted, showing strong community-driven debugging.

## Bugs & Stability
**High Severity**
- **Issue #1119** — MCP OAuth `invalid_target` failure for Notion and Linear servers. This is a live bug preventing users from adding two popular MCP services. A fix PR (#1120) exists and is open, which directly modifies `discover_and_register()` and `fetch_resource_metadata()` to handle the `resource_metadata` URL properly.

**Medium Severity**
- **PR #1122** — Docker volume shadowing issue where bind-mounted home directories can be overwritten by `VOLUME` declarations. This affects deployment reproducibility but is not a runtime crash.

No regressions or crash bugs were reported today.

## Feature Requests & Roadmap Signals
No explicit feature requests were filed today. The strongest signal is the community's need for robust third-party MCP server OAuth support, which is a feature requirement for the current fix PR. If merged, this would unblock integration with Notion and Linear — likely candidates for the next patch release.

## User Feedback Summary
The single user interaction today (Issue #1119 author `xzavrel`) reflects a concrete pain point: attempting to use Moltis with popular SaaS MCP servers fails at the OAuth handshake due to a protocol handling mismatch. The user provided detailed reproduction steps and error output, and also contributed a fix PR — indicating both frustration and a high level of engagement. No satisfaction signals were recorded.

## Backlog Watch
No items in the backlog required maintainer attention today. All open PRs are recent (within 24 hours), and the sole open issue is actively being worked on via PR #1120. No stale or unanswered items were identified.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-06-14

## Today's Overview

CoPaw (QwenPaw) shows **moderate activity** today with 9 open issues and 9 PRs updated within the last 24 hours, but only 1 issue and 1 PR were closed/merged — indicating a **build-up of unresolved work**. A single bug fix PR for DingTalk channel synchronization (#5177) was submitted today, while 7 PRs from prior days remain in "Under Review" status. No new releases were published. The backlog of first-time-contributor PRs awaiting review (4 items, all opened June 9–13) continues to grow, which may slow community contribution momentum.

## Releases

**No new releases** — the last release version referenced in issues is `v1.1.11`. Users on `v1.1.10` and `v1.1.11b1` are reporting unresolved (and potentially worsening) stability issues.

## Project Progress

### Merged/Closed Today (1 item)

- **#5172** [CLOSED] [Bug]: "Chat always hangs and shows no response after idle — serious issue persists" — reported by kfrtiamo, closed without resolution visible. The user describes a scenario where after a period of inactivity, all subsequent questions hang indefinitely until manually stopped, with error `Task has been cancelled!`. **Severity: High** — this was closed but no fix PR was linked.

## Community Hot Topics

### Most Active Issues (by comments)

| Issue | Title | Comments | Status | Link |
|-------|-------|----------|--------|------|
| #5156 | Feature: Add `kimi-for-coding` to `uv` allowlist | 4 | OPEN | [View](https://github.com/agentscope-ai/QwenPaw/issues/5156) |
| #5047 | Windows Tauri desktop startup extremely slow (10+ min) | 3 | OPEN | [View](https://github.com/agentscope-ai/QwenPaw/issues/5047) |

**Key theme:** Two dominant user pain points — **service integration limitations** (#5156: paid Kimi coding subscribers cannot use their existing plan with QwenPaw) and **platform degradation** (#5047: Tauri migration regressed startup time from ~2 minutes to 10+ minutes on Windows 11, with frequent freezes). Both are blocking real-world usage scenarios.

## Bugs & Stability

### High Severity

1. **#5177** — [Bug] DingTalk channel messages not registered in `chats.json` — conversations invisible in Console frontend. **Fresh today (June 14).** Agent replies correctly, but sessions never appear in the Console UI. **Fix PR submitted same day:** #5177 is itself the bug report, no separate fix PR yet. PR #5176 (console text overflow fix) is unrelated but from the same author.

2. **#5172** — [Bug] Chat hangs after idle — "Task has been cancelled" error when stopped. **CLOSED without fix.** This is concerning — the user explicitly noted it breaks non-interactive channels (QQ/WeChat) because there is no "stop" button. The closure without resolution is a red flag.

3. **#5171** — [Bug] Context compression omits profile files — "compressed to 0 tokens, context completely lost, task interrupted." Affects agents whose persona token count exceeds the retention threshold. Version `v1.1.11`. **No fix PR.**

### Medium Severity

4. **#5174** — [Bug] Cron agent runs Python scripts but cannot write files or spawn subagents — "heartbeat mechanism has inherent limitations." Suggests cron/heartbeat agents are effectively read-only.

### Open PRs Targeting Known Bugs (awaiting review)

- **#5035** — Fix `LlamaCppBackend.get_version()` — will break when build numbers reach 5 digits (~8514)
- **#5040** — Fix cron `jobs.json` parsing: single malformed job kills entire scheduler
- **#5037** — Fix IndexError on empty `Exec=` field in Linux browser detection
- **#5041** — Fix backup failure when a single file is unreadable (Windows permission errors)
- **#5038** — Fix `IndexError` in `LightContextManager.pre_reply` on empty message list

All five PRs remain "Under Review" since June 9 — **5 days without maintainer action.**

## Feature Requests & Roadmap Signals

### New Feature Requests (this digest period)

| Issue | Feature | Language/Platform | Likelihood for Next Release |
|-------|---------|-------------------|----------------------------|
| #5156 | Add `kimi-for-coding` to UV allowlist | Kimi/API | Medium – clear commercial demand from paying users |
| #5169 | Add Vietnamese (vi) interface language | Console | **High** – PR #5175 already submitted by nguyenthanhthe |
| #5168 | Add official Zalo Bot channel | Vietnam messaging | Medium-High – strong demand signal, complements vi language |
| #5173 | [Enhancement] (undefined title) | Console | Low – insufficient detail |

**Predictions for `v1.1.12` or `v1.2.0`:**
- Vietnamese language support is nearly certain (#5175 PR ready)
- DingTalk chat registration fix (#5177) is likely given it blocks an official channel
- A Tauri startup performance fix may appear if maintainers prioritize the regression (#5047)
- `kimi-for-coding` integration is plausible but may require API agreement

## User Feedback Summary

### Positive Signals
- **First-time contributors are active:** 5 of 9 open PRs are from first-timers (nguyenthanhthe, ly-wang19), and the project maintains a welcoming environment (e.g., `first-time-contributor` label, issue #5169 responded to with PR #5175 within 24 hours).

### Pain Points (real user reports)

1. **"Tauri migration ruined startup"** (#5047) — Windows user: "startup went from 1-2 minutes to 10+ minutes, frequent unresponsive states, reinstalling doesn't help." **Critical UX regression.**

2. **"Paid subscription can't be used"** (#5156) — Users with Kimi coding subscriptions must either waste their existing plan or abandon QwenPaw. **Commercial friction.**

3. **"Chat hang makes channels unusable"** (#5172) — "If connected to QQ/WeChat, there is no stop button, so it just breaks." **Production blocker for multi-channel users.**

4. **"Context compression destroys conversations"** (#5171) — "Agent context reduced to zero, task completely interrupted." **Data loss bug.**

5. **"Cron agents can't produce knowledge files"** (#5174) — Users expecting cron agents to write summaries, extract knowledge, or spawn subagents find the system effectively constrained. **Feature gap.**

### Dissatisfaction Signals
- Issue #5172 was closed **without a fix** despite the user explicitly rating it as "such a serious issue." This may erode trust in the bug reporting process.

## Backlog Watch

### Long-unanswered Issues (maintainer attention needed)

| Issue | Created | Days Open | Topic | Link |
|-------|---------|-----------|-------|------|
| #5047 | June 9 | **5 days** | Windows Tauri startup 10+ min | [View](https://github.com/agentscope-ai/QwenPaw/issues/5047) |
| #5156 | June 12 | **2 days** | Kimi-for-coding / UV allowlist | [View](https://github.com/agentscope-ai/QwenPaw/issues/5156) |

### Orphaned PRs (maintainer review needed)

| PR | Created | Days Stalled | Topic | Link |
|----|---------|--------------|-------|------|
| #5035 | June 9 | **5 days** | LlamaCpp version parsing (will break soon) | [View](https://github.com/agentscope-ai/QwenPaw/pull/5035) |
| #5040 | June 9 | **5 days** | Cron jobs.json validation (single bad job kills all) | [View](https://github.com/agentscope-ai/QwenPaw/pull/5040) |
| #5037 | June 9 | **5 days** | Linux browser detection IndexError | [View](https://github.com/agentscope-ai/QwenPaw/pull/5037) |
| #5041 | June 9 | **5 days** | Backup failure on unreadable file | [View](https://github.com/agentscope-ai/QwenPaw/pull/5041) |
| #5038 | June 9 | **5 days** | Empty message list IndexError | [View](https://github.com/agentscope-ai/QwenPaw/pull/5038) |

**Critical observation:** Five bug-fix PRs from ly-wang19 are all awaiting maintainer review since June 9. Combined, they fix **five distinct crashing or data-loss bugs**. This backlog suggests maintainer bandwidth is a current bottleneck and may be a risk to project health if not addressed soon.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for June 14, 2026.

---

## ZeroClaw Project Digest — 2026-06-14

### 1. Today's Overview
The ZeroClaw project shows **very high activity** driven by a major merge window and active community contributions. With 42 issues and 50 PRs updated in the last 24 hours, the project is in a **build-up phase** toward a significant release. The closure of the long-running RFC for unifying agent turn engines (Issue #7415) marks a key architectural milestone. A worrying trend is the high number of P1 (workflow-blocking) bugs being reported, particularly around the WebSocket gateway and the Web UI dashboard, suggesting that recent merges (notably #6986) may have introduced regressions in production paths.

### 2. Releases
No new releases were published in the last 24 hours. The project appears to be in a pre-release stabilization phase following the v0.8.0-beta-1 tag.

### 3. Project Progress
The primary progress comes from merged/closed PRs and issue closures. Key highlights include:

- **Closed (merged)**: RFC #7415 ("Unify the three agent turn engines") was closed after being executed as a single consolidation PR (#7540). This is a significant architectural simplification.
- **Closed (merged)**: PR #7540 itself was the main deliverable from the RFC.
- **Closed (Merged/Fixed)**: Several P1 bugs were resolved, including a quickstart infinite redraw loop (PR #7507) and a self-test failure on Windows (PR #7509).
- **Closed**: Issue #5470 ("Multiple issues when running safely") and #6223 ("web_fetch in Whatsapp Web") were closed, indicating fixes for long-standing channel reliability problems.
- **Active PRs with progress**: Major PRs like #7558 (canonical install spec), #7570 (OTel instrumentation), and #7361 (per-turn routing) are advancing through review.

**Progress on Trackers**: The "Zerocode" TUI (Issue #6826) and "Zerocode ACP Bridge" (Issue #6823) trackers continue to show steady updates, indicating parallel development on the terminal UI.

### 4. Community Hot Topics
The most active discussions highlight concerns about architecture, memory, and plugin systems:

- **[OPEN] #5849 — Dream Mode (18 comments)**: This remains the most active open issue. The feature proposes periodic memory consolidation during idle periods. Community interest is high, and a corresponding PR (#6693) exists. *Underlying Need*: Users want the agent to autonomously improve its knowledge base without manual intervention. This is a core "agentic" feature.
- **[CLOSED] #7415 — RFC: Unify Agent Turn Engines (5 comments)**: Closed as merged. This was a high-traffic architecture discussion. *Underlying Need*: Developers and maintainers wanted to eliminate complexity and bugs caused by having three separate code paths for agent execution.
- **[OPEN] #5470 — Multiple issues when running safely (5 comments)**: Closed after a long period of being stale. The high volume of comments reflects a user's significant frustration with the agent's reliability. *Underlying Need*: Users need a dependable, "set-it-and-forget-it" operational mode.
- **[OPEN] #7420 — Native Dynamic-Library Plugin System (3 comments)**: An RFC proposing a major new plugin architecture. *Underlying Need*: Power users and developers want to extend ZeroClaw with compiled code (Rust, C) for performance and to bypass WASM limitations.
- **[OPEN] #7497 — OCI-Compliant Registries for WASM Plugins (2 comments)**: Proposes using container registries for plugin distribution. *Underlying Need*: Security-conscious users need a cryptographically verifiable discovery and distribution mechanism for plugins.

### 5. Bugs & Stability
The project is currently experiencing a **patch of instability**, with several S1 (workflow-blocked) bugs reported or active.

- **S1 — Canvas Regression (Issue #7563)**: A `canvas-store` regression after a recent merge (#6986) breaks the Web UI `/canvas` page. **Status**: No fix PR yet.
- **S1 — ask_user fails in WS Dashboard (Issue #7542)**: The `ask_user` tool fails instantly in the Web UI. **Status**: Fix PRs #7588 and #7589 exist (in Chinese).
- **S1 — macOS App Not Working (Issue #7527)**: The new macOS app cannot detect permissions and displays a blank page. **Status**: Open, no fix PR.
- **S1 — Dashboard Not Available (Issue #7523)**: The web dashboard is not built by default on macOS brew install. **Status**: Open, with a documented workaround (`cargo web build`).
- **S2 — Invalid Agent Alias in Quickstart (Issue #7591)**: Capitalized aliases fail silently, forcing the user to restart the entire setup. **Status**: Open, reported today.
- **S2 — Zerocode Dark Theme Issues (Issue #7377)**: Text is unreadable on dark themes when the terminal profile is light. **Status**: Closed/Fixed.
- **S3 — Cmd-C treated as Quit in Zerocode (Issue #7378)**: A minor but annoying usability bug. **Status**: Closed/Fixed.

### 6. Feature Requests & Roadmap Signals
The community is actively shaping the future of ZeroClaw. Based on the latest issues, the next release (likely v0.8.1) will focus on:

- **Memory & Learning**: "Dream Mode" (#5849) is a strong candidate. The PR (#6693) is well-developed and has significant community interest.
- **Plugin & Tool Ecosystem**: RFCs for native plugins (#7420) and OCI-based WASM distribution (#7497) signal a major push toward a robust plugin ecosystem. A prompt-triggered plugin installer (#6289) is also accepted.
- **User Experience & UI**: Multi-session support in the web UI (#7543) and a llama.cpp model router (#7539) are high-priority quality-of-life features.
- **Enterprise/Compliance**: The cross-profile delegation feature (#7514, PR #7590) is a high-risk, important feature for complex multi-agent scenarios.
- **Integration Depth**: Streaming card messages for Chinese platforms (QQ, DingTalk, WeChat) (#7531) shows a strong focus on Asian markets.

### 7. User Feedback Summary
- **Pain Points**: The most significant user pain points are related to **reliability and onboarding**.
    - **Onboarding Friction**: The "quickstart" process is fragile, with bugs that can force a full restart of setup (Issues #7591, #7507).
    - **Platform Bugs**: The macOS app and Web UI dashboard are broken for new users (Issues #7527, #7523), creating a poor first impression for major platforms.
    - **Regression Anxiety**: Users are reporting regressions in core features (e.g., Canvas, `ask_user` tool) after recent merges (Issue #7563, #7542).
    - **Local Model Complexity**: Power users using llama.cpp find the default model selection restrictive and want a quick-switching router (Issue #7539).
- **Satisfaction**: There is high satisfaction with the **breadth of the project** ("very useful for working on smaller tasks"). The community is actively contributing, and there is strong consensus around the architectural direction (e.g., the turn-engine unification being welcomed).

### 8. Backlog Watch
Several important issues and PRs are at risk of being forgotten or are blocked.

- **[PR #6190] feat(obs): instrument runtime memory ops with OTel GenAI spans**: This is a large, important PR for observability. It has been superseded by a newer PR (#7570) from a different author. The original PR's bot name (needs-author-action) indicates it is blocked.
- **[PR #6693] feat(memory): add dream mode for periodic memory consolidation**: A long-standing PR for the popular "Dream Mode" feature. It carries the `needs-author-action` label, meaning the author needs to address review feedback.
- **[PR #6719] fix(runtime,channels): persist model_switch across turns**: A P1 fix that has been open for a month with the `needs-author-action` label. This is a critical UX bug that causes the model to reset after every turn.
- **[PR #5892] fix(providers,runtime): three production blockers**: This PR has been open since April with the `stale-candidate` label. It fixes critical issues for vLLM and vision models. If this is not valid, it should be closed.
- **[PR #6966] feat(obs): capture prompt/completion content on llm.call spans**: Another observability PR that is blocked by `needs-author-action`. It is essential for debugging agent behavior in production.
- **[Issue #6760] Update Docker Documentation**: A low-risk documentation issue that has been open for nearly a month. This is a common barrier for new users.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*