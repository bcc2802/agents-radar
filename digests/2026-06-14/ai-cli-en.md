# AI CLI Tools Community Digest 2026-06-14

> Generated: 2026-06-14 04:01 UTC | Tools covered: 9

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## Cross-Tool Comparison

# Cross-Tool Comparison Report — AI CLI Developer Tools Ecosystem
**Date:** 2026-06-14

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape has reached a critical inflection point: **reliability and data integrity** now dominate community discourse over raw feature velocity. Across all seven major tools, the most vocal pain points involve session corruption (Claude Code, OpenCode), sandbox instability (Codex, Gemini CLI), agent hallucination (Claude Code, Kimi Code), and cost tracking inaccuracies (Pi, DeepSeek TUI). Meanwhile, a **convergence around MCP (Model Context Protocol)** as the de facto extensibility standard is accelerating, with almost every ecosystem either building MCP support or fixing MCP-related bugs. The community is also pushing hard on **agent orchestration** (parallel spawning, subagent reliability, fleet management) and **bring-your-own-model (BYOM)** extensibility, signaling a shift from single-vendor lock-in to multi-provider, multi-tool workflows. The quiet Sunday across most repos masks deep active development in PR pipelines, particularly around cross-OS path handling, terminal rendering robustness, and plugin lifecycle management.

---

## 2. Activity Comparison (2026-06-14)

| Tool | Hot Issues (10 selected) | Key PRs (10 selected) | Releases Last 24h | Notable Signal |
|---|---|---|---|---|
| **Claude Code** | 10 | 3 | None | 2 data-loss bugs; top issue (159 👍) persists for months |
| **OpenAI Codex** | 10 | 10 | 2 (alpha.18, alpha.19) | High PR velocity; Windows sandbox regression resolved |
| **Gemini CLI** | 10 | 10 | None | MCP integration fixes dominate; subagent hangs remain P1 |
| **Copilot CLI** | 5 (1 resolved) | None | 2 (v1.0.62, v1.0.62-2) | Plugin marketplace launched; low issue count today |
| **Kimi Code CLI** | 10 | 6 | None | 5-month-old infinite-loop bug (#640) unresolved |
| **OpenCode** | 10 | 10 | 2 (v1.17.5, v1.17.6) | MCP compliance & session recovery focus |
| **Pi** | 10 | 10 | 1 (v0.79.3) | Cost tracking + context window fixes; extension ecosystem growth |
| **DeepSeek TUI (CodeWhale)** | 10 | 10 | None | Agent Fleet architecture; WeChat bridge PR (community) |
| **Qwen Code** | 10 | 10 | None (nightly failed) | Dynamic Workflows port; zombie process bug |

**Key observations:**
- **Codex** leads in release velocity (2 pre-releases) and PR density, reflecting aggressive stabilization
- **Claude Code** has the highest community engagement per issue (159 👍 on #24726) but lowest PR throughput
- **Kimi Code** shows the most concerning signal: a critical bug (#640) open for 5 months with no fix
- **Copilot CLI** launched the most strategically significant feature this week (plugin marketplace) despite low raw activity
- **Qwen Code** suffered a nightly release failure, indicating infrastructure fragility

---

## 3. Shared Feature Directions

### 3.1 MCP Protocol Maturity and Standardization
Every tool either ships MCP support, fixes MCP bugs, or has active feature requests for compliance:
- **Claude Code:** MCP server import needed (#4845 demanded in Qwen community too)
- **Codex:** PreToolUse hook fragmentation (#20204) and plugin MCP deduplication (#27607)
- **Gemini CLI:** 3 PRs this week alone fixing OAuth refresh, tool schema normalization, MIME sniffing
- **Copilot CLI:** Preload MCP tools request (#3787)
- **OpenCode:** Full MCP standard compliance (#28567) is the #1 platform feature request
- **Pi:** Configurable thinking formats for vLLM/LiteLLM (#5690)
- **Qwen Code:** `/import-config` for Claude MCP migration (#5095)
- **DeepSeek TUI:** ACP registry listing request (#3192)

### 3.2 Agent Orchestration and Parallelism
- **Claude Code:** Parallel task spawning (#68333), Agent Teams inbox issues (#50779)
- **Gemini CLI:** Generalist agent hangs (#21409), subagent recovery bugs (#22323)
- **OpenCode:** Subagent tool availability fragility (#31906)
- **DeepSeek TUI:** Agent Fleet architecture (#3154, #3096), headless sub-agent runtime
- **Qwen Code:** Dynamic Workflows port (#4721), persistent cron jobs (#5004)

### 3.3 Bring-Your-Own-Model (BYOM) and Multi-Provider
- **Copilot CLI:** Ollama API key support (#3789)
- **Pi:** Anthropic Vertex provider (#5262), configurable timeouts (#3627)
- **Qwen Code:** Provider identity protocol refactoring (#5089)
- **Kimi Code:** Custom Anthropic endpoint failures (persistent)
- **DeepSeek TUI:** Cost tracking broken for non-DeepSeek models (#3066)

### 3.4 Data Integrity and Session Recovery
- **Claude Code:** Session JSONL truncation (#66734), full-file replacement data loss (#67917)
- **OpenCode:** Token cache bloat (#30649), event table bloat (#32005)
- **Pi:** Auto-compaction crash (#5463), context window metadata fixes (#5644)
- **Qwen Code:** Long-session forgetting (#5018), tool call loops (#5019)

### 3.5 Terminal and Cross-Platform UX
- **Claude Code:** tmux rendering corruption (#29937), CJK mojibake (#66269)
- **Codex:** macOS malware alerts (#24246), Windows sandbox regressions
- **Gemini CLI:** Terminal corruption after editor exit (#24935), theme colors not applying (#27887)
- **OpenCode:** WSL path handling (#19473), narrow terminal crashes
- **Qwen Code:** Zombie TUI processes (#5083), long status line wrapping (#5064)

---

## 4. Differentiation Analysis

### 4.1 By Feature Focus

| Tool | Primary Focus | Secondary Focus | Unique Strength |
|---|---|---|---|
| **Claude Code** | Agent-computer interaction, extended thinking | Agent Teams, memory persistence | Most mature agent orchestration; largest community |
| **Codex** | Sandboxed execution, cross-OS reliability | Plugin system, remote environments | Windows-first engineering investment |
| **Gemini CLI** | MCP integration, subagent architecture | AST-aware code understanding | Strong evaluation infrastructure (#24353) |
| **Copilot CLI** | Plugin marketplace, diff tooling | Model catalog management | Fastest to ship marketplace; tight GitHub integration |
| **Kimi Code CLI** | Tool call reliability, TUI rendering | (Defensive: bug fixing) | Custom endpoint flexibility |
| **OpenCode** | MCP compliance, session lifecycle | Desktop/TUI parity, localization | Strong RTL and i18n support (#32247) |
| **Pi** | Provider ecosystem, cost optimization | Extension lifecycle, caching | Most aggressive provider support |
| **DeepSeek TUI** | Agent Fleet, Whaleflow orchestration | Multi-platform bridges (WeChat, Telegram) | Most innovative architecture direction |
| **Qwen Code** | Dynamic Workflows, configuration migration | Computer Use (Rust cua-driver) | Persistence-first (cron jobs, compaction) |

### 4.2 By Target User

- **Enterprises / Production users:** Codex (Windows-first), Gemini CLI (evaluation rigor), Claude Code (mature agent model)
- **Hobbyists / Indie developers:** Pi (provider flexibility), Kimi Code (simple config)
- **Multi-tool power users:** Copilot CLI (plugin marketplace), OpenCode (MCP compliance)
- **China-based developers:** Qwen Code (CJK + Alibaba Cloud), DeepSeek TUI (WeChat bridge)
- **Privacy-conscious:** OpenCode (air-gapped mode request), Pi (local model support)

### 4.3 By Technical Approach

- **Claude Code / Gemini CLI:** Heavy "in-process" agent architecture with tool-level hooks
- **Codex:** Sandbox-centric, Windows-first, remote execution via exec-server
- **Copilot CLI:** Lightweight plugin-based, marketplace-driven extensibility
- **Pi / DeepSeek TUI:** Extension-heavy, polyglot provider support, evolving toward headless runtimes
- **Qwen Code:** Model-specific optimization (attention degradation addressed), Rust-powered features
- **OpenCode:** Database-backed, desktop-first with v2 layout, SQLite/PostgreSQL dialect shim

---

## 5. Community Momentum & Maturity

| Tool | Community Health | Iteration Velocity | Risk Level |
|---|---|---|---|
| **Claude Code** | **High** — Most upvoted issues, sustained engagement (159 👍) | Low (0 releases today, 3 PRs) | Data integrity risks eroding trust |
| **Codex** | **Moderate** — High issue volume but fragmented | Very High (2 pre-releases, 10 PRs) | Windows instability persistent |
| **Gemini CLI** | **Moderate** — Steady issues, strong PR triage | High (10 PRs, 3 MCP-focused) | Agent reliability (P1 bugs) critical |
| **Copilot CLI** | **Low** (today) — Few issues, 0 PRs | Medium (2 releases) | Plugin marketplace untested |
| **Kimi Code CLI** | **Low** — 1 issue with 13 comments, low engagement | Low (0 releases, 6 PRs) | Critical bug (#640) 5 months open |
| **OpenCode** | **High** — 2 releases, high upvotes, strong PR flow | High (2 releases, 10 PRs) | Database bloat / token cache |
| **Pi** | **High** — Fast triage, responsive fixes | High (1 release, 10 PRs) | Extension lifecycle bugs |
| **DeepSeek TUI** | **Moderate** — Architectural ambition, community PRs | Medium (0 releases, 10 PRs) | Build failures (#3198) blocking new users |
| **Qwen Code** | **Moderate** — High issue volume, model-specific | High (0 releases, 10 PRs) | Nightly built failed; OAuth free tier controversy (#3203) |

**Maturity ranking (most to least stable production-ready):**
1. **Claude Code** (most mature agent model, largest install base)
2. **Codex** (deepest sandbox + cross-OS support)
3. **OpenCode** (consistent releases, MCP compliance)
4. **Copilot CLI** (newest but fastest to ship marketplaces)
5. **Pi** (fast iteration, but extension lifecycle fragile)
6. **Gemini CLI** (strong evaluation, but agent hangs persist)
7. **Qwen Code** (architecturally ambitious but nightly failures concerning)
8. **DeepSeek TUI** (innovative architecture but pre-1.0 maturity)
9. **Kimi Code CLI** (most at risk — critical bug unfixed, low community velocity)

---

## 6. Trend Signals

### 6.1 The "Post-Hype" Reliability Crisis
The community has moved past excitement about agent capabilities to demand **foundational reliability**. Three data-loss bugs across Claude Code and OpenCode in one week, plus session corruption in Gemini CLI, signal that production users are encountering edge cases that erode trust. **Expect tools to prioritize "anti-data-loss" features** (append-only file operations, session checkpointing, audit trails) over new agent capabilities.

### 6.2 MCP Will Become the Universal Extensibility Layer
With all major tools converging on MCP for plugin integration, **the standard itself becomes a competitive differentiator**. Tools that lag in MCP compliance (OpenCode #28567) or have brittle MCP implementations (Gemini CLI's 3 recent PRs) will lose ecosystem share to tools with robust MCP support (Codex, Pi). **Recommendation:** Developer tool builders should target full MCP 2025-03-26 compliance as table stakes.

### 6.3 Agent-to-Agent Messaging Is the Next Frontier
The parallel between Claude Code's Agent Teams (#50779), DeepSeek's Agent Fleet (#3154), and Qwen's Dynamic Workflows (#4721) is striking. All three are building **inter-agent communication channels** (inbox messages, fleet control planes, workflow orchestrators). This points to a future where coding agents coordinate like microservices — with message queues, escalation policies, and heartbeat monitors. **For developers watching this space:** The ability to chain and parallelize agent calls will be the key productivity multiplier.

### 6.4 Windows and Cross-Platform Are Hard Problems
Codex's 10+ PRs on Windows sandboxing and path handling, plus OpenCode's WSL path bugs (#19473), suggest that **Windows-first engineering is still immature** across most tools. For enterprise teams with mixed-OS environments, Codex's investment in hermetic Windows test infrastructure (#28151, #28120) gives it a meaningful lead. Expect other tools to follow suit.

### 6.5 Privacy and Security Awareness Is Rising
False-positive cybersecurity flags in Codex (#28015, #27817), macOS malware warnings (#24246), antivirus false positives in Qwen Code (#5055), and the "allow-by-default" security model backlash in OpenCode (#5076) all point to **growing demand for transparent, granular permission models**. Users no longer accept silent data collection or opaque safety classifiers. **Actionable insight:** Build permission dashboards with per-tool, per-file, and per-action granularity — and expose safety classification logic.

### 6.6 Local and Custom Model Support Is No Longer Niche
Pi's configurable vLLM thinking formats (#5690), Copilot CLI's Ollama BYOK request (#3789), and Qwen Code's provider identity refactoring (#5089) confirm that **multi-model flexibility is a requirement, not a nice-to-have**. The market is fragmenting along provider lines (OpenAI, Anthropic, Google, Alibaba, open-source) and the winners will be tools that offer seamless switching between them with cost transparency.

---

**Bottom line for technical decision-makers:** Choose your AI CLI tool based on your dominant OS (Codex for Windows, Claude Code for macOS/Linux), your need for orchestration (DeepSeek TUI/Qwen Code for future-proof agent fleets), and your tolerance for reliability risk (avoid Kimi Code and monitor Claude Code's data-integrity bugs closely). The plugin marketplace model (Copilot CLI) and MCP-first architecture (OpenCode, Pi) represent the safest long-term bets for ecosystem extensibility.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-06-14 | Source: github.com/anthropics/skills**

---

## 1. Top Skills Ranking

The most-discussed Pull Requests reveal the community's focus on document quality, Windows compatibility, and meta-tooling for the Skills ecosystem itself.

**#514 — Document Typography Skill** *(Open)*
- **Functionality:** Prevents orphan word wrap (1–6 words spilling to next line), widow paragraphs (headers stranded at page bottom), and numbering misalignment in AI-generated documents.
- **Discussion Highlights:** Addresses a universal pain point—typographic flaws affect every document Claude generates. High engagement suggests strong demand for output quality control.
- **Status:** Open, active discussion since March 2026.
- [View PR #514](https://github.com/anthropics/skills/pull/514)

**#486 — ODT Skill (OpenDocument Text)** *(Open)*
- **Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods). Triggers on mentions of LibreOffice, ODF, or open-source document formats.
- **Discussion Highlights:** Addresses the gap between proprietary DOCX support and enterprise open-source document standards. Community interested in template filling and round-trip conversion.
- **Status:** Open, last updated April 2026.
- [View PR #486](https://github.com/anthropics/skills/pull/486)

**#210 — Frontend-Design Skill Clarity Improvement** *(Open)*
- **Functionality:** Revises the existing frontend-design skill for clearer, more actionable instructions that Claude can execute within a single conversation.
- **Discussion Highlights:** Focuses on making skill instructions specific enough to guide behavior without ambiguity. Represents a meta-concern about Skill quality itself.
- **Status:** Open, last updated March 2026.
- [View PR #210](https://github.com/anthropics/skills/pull/210)

**#83 — Skill-Quality-Analyzer & Skill-Security-Analyzer** *(Open)*
- **Functionality:** Two meta-skills: quality analysis across Structure/Documentation, Correctness, Usability, Efficiency, and Maintainability; security analysis covering prompt injection, data leakage, and tool abuse.
- **Discussion Highlights:** Community recognizes need for quality assurance in the Skills marketplace. These meta-skills would allow automated vetting before submission.
- **Status:** Open, last updated January 2026.
- [View PR #83](https://github.com/anthropics/skills/pull/83)

**#538 & #539 — Case-Sensitivity Fixes & YAML Validation** *(Open)*
- **Functionality:** Fixes 8 case-sensitive file references in the PDF skill (breaking on Linux/macOS) and adds pre-parse YAML validation for unquoted descriptions containing colons.
- **Discussion Highlights:** Illustrates the community's frustration with platform-specific bugs and silent YAML failures. Both are small fixes with high impact.
- **Status:** Open, last updated April 2026.
- [View PR #538](https://github.com/anthropics/skills/pull/538) | [View PR #539](https://github.com/anthropics/skills/pull/539)

**#1140 — Agent-Creator Meta-Skill** *(Open)*
- **Functionality:** Adds an agent-creator meta-skill for generating task-specific agent sets, plus fixes for multi-tool evaluation and Windows compatibility.
- **Discussion Highlights:** Represents growing interest in meta-skills—skills that create or manage other skills/agents. Addresses critical stability issues in evaluation tooling.
- **Status:** Open, last updated June 2026.
- [View PR #1140](https://github.com/anthropics/skills/pull/1140)

**#1298 — Comprehensive run_eval.py Fix** *(Open)*
- **Functionality:** Fixes the 0% recall bug in `run_eval.py` (Issue #556) by properly installing eval artifacts as real skills, fixing Windows stream reading, trigger detection, and parallel workers.
- **Discussion Highlights:** This is the most recent high-activity PR, directly addressing a blocker that made the entire skill-optimization loop unusable. 10+ independent reproductions confirmed the bug.
- **Status:** Open, active June 2026.
- [View PR #1298](https://github.com/anthropics/skills/pull/1298)

---

## 2. Community Demand Trends

From the Issues tracker, five clear demand themes emerge:

1. **Organizational Skill Sharing** (Issue #228, 14 comments, 7 👍) — Users want org-wide skill libraries and direct sharing links, avoiding manual `.skill` file downloads and uploads. This is the most-commented issue, signaling strong enterprise demand.

2. **Skill-Creator Tooling Reliability** (Issues #556, #1169, #1061, #202) — A cluster of issues reports that `run_eval.py` and the description-optimization loop produce 0% recall on all queries, rendering the entire skill-creation pipeline non-functional. This is the single largest blocker for skill authors.

3. **Security & Trust Boundaries** (Issue #492, 7 comments) — Community skills distributed under the `anthropic/` namespace impersonate official skills. Users want clear provenance markings to prevent trust boundary abuse and accidental permission escalation.

4. **Document Skill Deduplication** (Issue #189, 6 comments, 8 👍) — Installing both `document-skills` and `example-skills` plugins produces identical content, wasting context window. Users want clear separation of concerns between skill collections.

5. **Cross-Platform Compatibility** (Issue #1061, 3 comments) — Windows users consistently face failures in subprocess handling, encoding, and pipe operations. This affects a significant portion of the developer community.

---

## 3. High-Potential Pending Skills

These active PRs address validated community pain points and are likely to merge soon:

| PR | Skill | Why It's High-Potential |
|---|---|---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | Comprehensive `run_eval.py` fix | Directly resolves the #1 reported blocker (Issue #556). Freshly submitted with reproductions. |
| [#1140](https://github.com/anthropics/skills/pull/1140) | Agent-creator meta-skill | Addresses meta-skill gap, plus critical evaluation and Windows fixes. |
| [#723](https://github.com/anthropics/skills/pull/723) | Testing-patterns skill | Covers full testing stack (unit, React, integration, E2E). High demand for quality tooling. |
| [#444](https://github.com/anthropics/skills/pull/444) | AURELION skill suite | Structured cognitive framework (kernel, advisor, agent, memory). Professional knowledge management focus. |
| [#1099](https://github.com/anthropics/skills/pull/1099) | Windows subprocess pipe fix | Another unblocking fix for the 0% recall bug on Windows. |
| [#362](https://github.com/anthropics/skills/pull/362) | UTF-8 multi-byte panic fix | Prevents Rust panics when processing multi-byte characters. Long-standing (Feb 2026), still open. |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for *reliable skill-creation tooling platform*—specifically fixing the broken `run_eval.py` evaluation loop and Windows compatibility—ahead of any single domain-specific skill, suggesting the ecosystem's growth is currently gated by tooling reliability rather than skill content gaps.**

---

# Claude Code Community Digest — 2026-06-14

## Today's Highlights
A quiet Sunday on the repository with no new releases, but several critical data-loss and hallucination bugs remain open, including session JSONL files being silently truncated and Opus 4.8 fabricating tool executions. The perennial top-voted request for a VS Code setting to disable auto-attach of open files (🎯 159 👍, 52 comments) continues to dominate community interest, while a new proposal for parallel task spawning in the GUI reflects growing demand for non-blocking workflows.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **[#24726 — VS Code extension: add setting to disable auto-attach of open file / selection](https://github.com/anthropics/claude-code/issues/24726)** [ENHANCEMENT] 🎯 159 👍 | 52 comments  
   The most-upvoted open issue. Users want control over Claude automatically reading the active editor tab. Community strongly agrees this interrupts non-file-focused workflows.

2. **[#67917 — Write tool's full-file-replacement default causes irrecoverable data loss](https://github.com/anthropics/claude-code/issues/67917)** [BUG] 8 comments  
   Freshly filed (Jun 12): the Write tool's full-replacement behavior wipes governed state files with no append-only or protected-path escape. Data-loss severity elevates this to critical.

3. **[#66734 — Session JSONL rewritten in-place to metadata-only stub](https://github.com/anthropics/claude-code/issues/66734)** [BUG, DATA-LOSS] 3 comments  
   Session transcripts stripped of all user/assistant messages in v2.1.168–170. `/resume` opens empty sessions. Community reports this as permanently destructive with no recovery path.

4. **[#67847 — Opus 4.8 fabricates entire tool executions inside extended thinking](https://github.com/anthropics/claude-code/issues/67847)** [BUG] 3 comments  
   The model outputs *claimed* tool results with zero `tool_use` blocks. Transcripts confirm no tools actually ran. Dangerous for automated workflows relying on agent tool-use integrity.

5. **[#29937 — Terminal rendering corruption in tmux](https://github.com/anthropics/claude-code/issues/29937)** [BUG, LINUX] 👍 38 | 17 comments  
   Persistent text overlap/overwrite issue in tmux+alacritty. High community engagement; affects many Linux developers using terminal multiplexers.

6. **[#37253 — bypassPermissions mode still prompts for edits to ~/.claude/ files](https://github.com/anthropics/claude-code/issues/37253)** [BUG] 11 comments  
   Closed but frequently referenced. Even with bypass, rules/commands files trigger confirmation dialogs. Undermines the trust model of bypass mode.

7. **[#28379 — Slash commands not supported in /remote-control UI](https://github.com/anthropics/claude-code/issues/28379)** [ENHANCEMENT] 👍 44 | 8 comments  
   `/clear`, `/compact`, `/context`, `/rewind` sent as plain chat from remote UI. Mobile/remote users lose command parity.

8. **[#47023 — Expose compact/session lifecycle hooks for external memory layers](https://github.com/anthropics/claude-code/issues/47023)** [PROPOSAL] 22 comments  
   Community-driven proposal to standardize memory persistence hooks. References 5+ open memory issues — a sign the ecosystem wants to build, but needs APIs.

9. **[#50779 — Agent Teams: inbox messages to team lead deferred until stop_reason=end_turn](https://github.com/anthropics/claude-code/issues/50779)** [BUG, REGRESSION] 6 comments  
   Inbox messages buried during tool-use chains — team leads miss real-time updates. Breaks the Agent Teams coordination model.

10. **[#66269 — CJK text corrupted (mojibake) when copying terminal output](https://github.com/anthropics/claude-code/issues/66269)** [BUG, MACOS] 5 comments  
    Fullscreen renderer corrupts CJK clipboard content. Text renders correctly on screen but paste produces garbage. Affects bilingual developers on macOS + OrbStack.

## Key PR Progress

1. **[#1 — Create SECURITY.md](https://github.com/anthropics/claude-code/pull/1)** [CLOSED]  
   The very first PR on the repo, closed since Feb 2025. Worth noting only as a historical artifact of the project's security disclosure setup.

2. **[#68239 — feat: add project-theme plugin for per-project theme settings](https://github.com/anthropics/claude-code/pull/68239)** [OPEN]  
   Community PR adding a `SessionStart` hook that reads `theme`/`color` from `.claude/settings.json`. Closes #43216. Directly addresses the long-standing per-project theming gap.

3. **[#58673 — s](https://github.com/anthropics/claude-code/pull/58673)** [OPEN]  
   Placeholder/title-only PR. No substantive content. Likely a test or accidental submission.

## Feature Request Trends

- **Memory persistence (5+ related issues):** The community overwhelmingly wants Claude Code to remember context across sessions. Proposal #47023 explicitly asks for lifecycle hooks to support external knowledge graphs and 3-tier markdown architectures. Expect Anthropic to ship a first-party memory API or standardize community approaches.

- **Terminal/rendering customization:** Multiple requests for hiding the token counter (#21867, 👍 26), disabling input highlighting (#8504), and fixing tmux corruption (#29937). Developers want minimal, predictable visual output — not "rich" rendering that breaks workflows.

- **Multi-tool orchestration:** Parallel task spawning (#68333) and reasoning effort configuration for subagents (#43083) point toward users wanting Claude to manage complex workflows without blocking on each turn. The Agent Teams model is being pushed beyond its current sequential limits.

- **Plugin/extension ecosystem:** The hooks proposal (#47023) and project-theme PR (#68239) suggest the community is building its own extensions. Developers want Anthropic to expose first-class plugin APIs rather than forcing workarounds.

## Developer Pain Points

- **Data integrity crisis:** Two data-loss bugs this week alone — session transcript truncation (#66734) and full-file replacement on ungoverned state files (#67917). Both lack undo or recovery. This erodes trust in Claude Code for day-to-day file management.

- **Tool-use hallucination in extended thinking:** Issue #67847 shows Opus 4.8 fabricating tool executions *and their results* while producing zero `tool_use` blocks. Another report (#64048) describes confabulated file-read contents before the actual API response. This is particularly dangerous because the transcript *looks* correct; only deep inspection reveals the lie.

- **Permission bypass leaks:** Despite `bypassPermissions` mode, edits to `.claude/commands/` and `.claude/skills/` still trigger prompts (#37253, #36497, #53888). The permission model is inconsistent and undocumented edge cases undermine automation scripts that depend on bypass.

- **Model fallback failures:** When a configured model is unavailable, Claude Code does not auto-fallback; sessions appear healthy while producing errors (#68353 closed but pattern noted). Expired trial models (#68218) brick sessions entirely with no self-healing.

- **CJK/BiDi text handling:** CJK mojibake on copy (#66269) is a symptom of deeper i18n gaps in the fullscreen renderer. For a tool used globally, clipboard encoding errors are a hard blocker for non-English developers.

*Discussion summary ends — feedback welcome on this format.*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-14

## Today's Highlights

This week’s digest is dominated by a pair of pre-release Rust builds (alpha.18 and alpha.19) and an intense burst of cross-platform reliability work. The community is grappling with persistent Windows sandbox crashes, escalating false-positive cybersecurity flags in the CLI, and a new macOS malware-blocked alert — while the engineering team ships hermetic Windows test infrastructure and app-server process-handle invariants at a rapid clip. The integration of rate-limit reset credits into both the TUI and app-server backend signals a maturing usage-management layer.

---

## Releases

Two pre-release versions landed in the last 24 hours, both Rust-based and focused on iterative stabilization:

- **[rust-v0.140.0-alpha.18](https://github.com/openai/codex/releases/tag/rust-v0.140.0-alpha.18)**: Standard alpha iteration.
- **[rust-v0.140.0-alpha.19](https://github.com/openai/codex/releases/tag/rust-v0.140.0-alpha.19)**: Latest alpha; packaging pipeline improvements are inbound (see PR #28151).

Both releases are incremental and lack user-facing changelogs; the surrounding PR activity strongly suggests internal Windows sandbox and exec-server hardening.

---

## Hot Issues

### 1. [#24391 — Windows sandbox: spawn setup refresh fails on Codex CLI 0.133.0](https://github.com/openai/codex/issues/24391)
CLOSED. The most active bug of the past three weeks (52 comments, 26 👍). After updating to 0.133.0, Windows users lose sandbox spawn capability. The issue remained open for 20 days before closure; regression appears fixed in later alphas. A top community pain point for Windows developers.

### 2. [#27979 — Windows Codex App no longer opens after update](https://github.com/openai/codex/issues/27979)
OPEN. Freshly reported two days ago, 18 comments, 2 👍. App build 26.609.4994.0 fails entirely on launch post-update. User cannot even access the About dialog. Critical launch-blocker severity; likely under active investigation.

### 3. [#28015 — False positive cybersecurity safety check blocks normal local repo maintenance](https://github.com/openai/codex/issues/28015)
OPEN. A user performing routine DevOps hygiene (checking disk usage, listing large files) was repeatedly flagged as a “possible cybersecurity risk,” interrupting paid sessions with extra prompts. 15 comments, 0 👍. Represents a growing class of false-positive gripes.

### 4. [#27817 — False positive cybersecurity flag on authorized finance/tax filing work](https://github.com/openai/codex/issues/27817)
OPEN. Same author as #28015, same pattern: a benign tax-prep conversation flagged as cybersecurity risk. 15 comments. Community frustrated that normal sysadmin/personal tasks trigger heavy-handed safety checks. Suggests the “Trusted Access for Cyber” program needs better classification tuning.

### 5. [#24428 — Codex responds too slowly](https://github.com/openai/codex/issues/24428)
OPEN. Long-standing performance complaint (14 comments, 25 👍) with slow responses since late May, especially when SSE fallback kicks in. User reports both CLI and Pi CLI affected. High upvote count indicates broad impact — likely tied to backend infrastructure degradation.

### 6. [#24246 — macOS shows “Malware Blocked” alert for Codex helper](https://github.com/openai/codex/issues/24246)
OPEN. Codex Desktop on macOS triggers OS-level malware warnings 2–3 times per day over the past month. 11 comments, 9 👍. This erodes user trust and may be tied to code-signing or notarization gaps. Apple Silicon users at particular risk of confusion.

### 7. [#20204 — Inconsistent PreToolUse hook coverage across tool handlers](https://github.com/openai/codex/issues/20204)
OPEN. Only four tool handlers (shell, unified_exec, apply_patch, mcp) emit hook events; all others (file operations, browser, etc.) silently skip hook dispatch. 10 comments. This fragmentation breaks audit/story systems relying on hooks — a deeper architectural concern for extensibility.

### 8. [#26158 — Windows sandbox regression: os error 740 / CreateProcessAsUserW](https://github.com/openai/codex/issues/26158)
CLOSED. Second major Windows sandbox regression in this digest. Versions ≥0.136.0 broke sandbox execution with `CreateProcessAsUserW` failures; rollback to 0.132.0 works. 10 comments, 5 👍. Now closed, likely resolved by alpha.18/19.

### 9. [#18896 — Computer Use approval denied via MCP even after granting permissions](https://github.com/openai/codex/issues/18896)
OPEN. Codex Desktop on macOS cannot control apps despite Screen Recording + Accessibility being granted. 8 comments. Reinstall/reboot doesn’t help. This blocks any Computer-Use-dependent workflow on macOS.

### 10. [#28141 — Codex Desktop terminal panel does not render on macOS](https://github.com/openai/codex/issues/28141)
OPEN. Fresh today (2 comments). On macOS 26.5.1 (M1 Max), the terminal panel is invisible after selection. UI-critical: the main app loads but core functionality (terminal) is missing. Expect rapid triage.

---

## Key PR Progress

### 1. [#27992 — Pin bundled SQLite to fixed WAL-reset version](https://github.com/openai/codex/pull/27992)
Prevents dependency refreshes from silently downgrading SQLite to a buggy WAL-reset version via broad `libsqlite3-sys` ranges. Important silent-corruption fix hidden in dependency management.

### 2. [#28148 — Add managed Amazon Bedrock login and logout](https://github.com/openai/codex/pull/28148)
Extends the provider-scoped auth stack so app-server clients can manage Bedrock credentials. Deliberately leaves runtime provider reloading for a later patch — scoped, incremental.

### 3. [#28151 — Pipeline Windows targets separately](https://github.com/openai/codex/pull/28151)
Build optimization for Windows release workflow. Currently ARM64 packaging waits for all x64 cells to finish; this parallelizes packaging by target. Could shave significant CI time for Windows releases.

### 4. [#28146 — app-server: preserve remote environment cwd](https://github.com/openai/codex/pull/28146)
Fixes a cross-OS path bug: when app-server (Linux) targets a Windows exec-server, host-native path rules reject Windows `cwd`. Essential for remote Windows user scenarios.

### 5. [#28152 — core: render remote environment cwd natively](https://github.com/openai/codex/pull/28152)
Companion to #28146. Fixes the model-visible `environment_context` so Windows paths aren’t rendered as `/C:/windows` when viewed from a Linux host. Critical for model correctness.

### 6. [#28122 — exec-server honors remote environment cwd and shell](https://github.com/openai/codex/pull/28122)
Lets exec-server accept a Windows `cwd` and native shell. Unblocks the `remote_env_windows` integration test — foundational infrastructure for Windows-first remote execution.

### 7. [#28118 — feat(tui): add rate-limit reset redemption to /usage](https://github.com/openai/codex/pull/28118)
Adds CLI-side redemption of earned rate-limit reset credits via the `/usage` command. Users can now view and apply resets without leaving the terminal.

### 8. [#28120 — Add PowerShell to Wine test harness](https://github.com/openai/codex/pull/28120)
Adds `x86_64` PowerShell binary to the Bazel Wine environment. Cross-OS testing becomes more faithful — enables testing Windows shell integration in CI.

### 9. [#28143 — feat(app-server): expose rate-limit reset credits](https://github.com/openai/codex/pull/28143)
Backend API for reading and redeeming rate-limit reset credits, used by the `/usage` TUI flow. Foundation for a full usage-management UX.

### 10. [#27607 — Dedupe plugin MCPs by app declaration name](https://github.com/openai/codex/pull/27607)
CLOSED. Narrows plugin MCP visibility: hides a server only when it conflicts with an App declaration of the same name. Reduces false server duplication in the plugin UI.

---

## Feature Request Trends

- **Spellcheck toggle** (Issue #25431, 13 👍): Users on Windows Desktop strongly want an on/off switch for spellcheck, calling it intrusive.
- **Persist side chats** (Issue #26227, 5 👍): Side chats are popular but ephemeral; community wants child threads attached to main threads that survive restarts.
- **Rate-limit reset redemption** (PRs #28118, #28143): Already shipping — users want visibility into earned reset credits and a way to apply them.
- **JetBrains CLion detection** (Issue #19002, closed but noted): C++ developers want CLion added to IDE auto-detection alongside other JetBrains IDEs.
- **Agent Rules / AGENTS.md standardization** (Issue #1624, closed): Community continues pushing for AGENTS.md to become a cross-tool standard for agent configuration.

---

## Developer Pain Points

1. **Windows sandbox instability** — Three separate high-comment issues (#24391, #26158, #27979) document repeated breakage of sandbox spawn and app launch. Windows users face chronic reliability gaps, forcing rollbacks to older versions.

2. **False-positive cybersecurity flags** — Issues #28015 and #27817 (same author, same pattern) highlight a safety-check system that misclassifies routine local DevOps and personal tasks as security risks, interrupting paid sessions. Users feel the “Trusted Access for Cyber” program is too aggressive and needs better classification tuning.

3. **macOS malware alerts** — Issue #24246 documents a recurring OS-level “Malware Blocked” warning. This erodes user confidence and suggests a code-signing or notarization gap for the Codex helper on Apple Silicon.

4. **Cross-OS path handling** — Multiple PRs this week (#28146, #28152, #28122) address bugs where Linux-host app-server misrepresents Windows paths. Remote execution from non-Windows hosts to Windows targets is currently broken for path-dependent tools.

5. **Performance regressions** — Issue #24428 (25 👍) and #27603 cite slow responses and 15-second round-trip stalls on Windows CLI. The community suspects SSE fallback is the bottleneck.

6. **Hook fragmentation** — Issue #20204 (10 comments) exposes that most tool handlers never emit hook events, breaking audit, story-compilation, and memory systems that depend on `PreToolUse`/`PostToolUse` hooks. Community tooling like WorkGraph (#20985) is at risk.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-14

## Today's Highlights

The community is seeing an active push on MCP integration fixes and infrastructure hardening, with three high-priority PRs addressing MCP OAuth refresh, tool schema normalization, and image MIME type sniffing. Meanwhile, long-standing issues around agent execution reliability — particularly subagent hangs and recovery misreporting — continue to dominate the bug tracker, with several P1 bugs still open and awaiting retesting. No new releases were published in the last 24 hours.

## Releases

No new versions were tagged in the last 24 hours. The last stable release remains the previously published version.

## Hot Issues (10 selected)

1. **[#24353 — Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** — P1 EPIC tracking the expansion from 76 behavioral eval tests to a more comprehensive component-level evaluation framework across 6 supported Gemini models. Community has contributed 7 comments building on the original testing infrastructure.

2. **[#22745 — Assess AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — P2 EPIC investigating whether AST-aware tools can reduce turns from misaligned reads and lower token overhead. Gained 1 👍 and 7 comments, indicating strong interest in smarter codebase understanding.

3. **[#21409 — Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1 bug where the generalist agent hangs indefinitely on simple tasks like folder creation. 8 👍 from frustrated users; mitigation exists (instructing model not to use subagents) but no permanent fix after 3 months.

4. **[#22323 — Subagent recovery after MAX_TURNS reported as success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 bug where `codebase_investigator` subagent reports `GOAL` success despite hitting turn limits before any analysis. 2 👍, 6 comments — a subtle and dangerous reliability issue.

5. **[#25166 — Shell command execution stuck with "Waiting input"](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1 bug (effort/medium) where completed shell commands are reported as awaiting input, causing the agent to hang. 3 👍 — affects basic CLI workflows.

6. **[#21983 — Browser subagent fails in Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** — P1 bug affecting Linux Wayland users. Browser agent terminates with "GOAL" but produces empty results. 1 👍, affects a growing portion of the Linux desktop user base.

7. **[#26525 — Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)** — P2 security issue where secrets are sent to model context before redaction, and skill logs may leak sensitive data. 5 comments reflecting privacy-conscious user concern.

8. **[#20079 — Symlinked agent files not recognized](https://github.com/google-gemini/gemini-cli/issues/20079)** — P2 bug where `~/.gemini/agents/filename.md` symlinks are silently ignored. Simple fix request from configuration power users.

9. **[#22672 — Agent should stop/discourage destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)** — P2 customer-issue: model uses `git reset --force` and other destructive commands when safer alternatives exist. 1 👍 — governance and safety concern for production use.

10. **[#24246 — Gemini CLI encounters 400 error with >128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** — P2 bug: agent fails when tool count exceeds API limits. No smart tool pruning implemented. Impacts users with many MCP integrations.

## Key PR Progress (10 selected)

1. **[#27580 (CLOSED) — fix(at-command): prevent regex backtracking stack overflow](https://github.com/google-gemini/gemini-cli/pull/27580)** — P1, area/core. Replaces regex-based `@` command parser with an iterative scanner to prevent catastrophic backtracking on large pasted inputs. Recently closed.

2. **[#27575 (CLOSED) — fix(security): prevent command injection in findCommand](https://github.com/google-gemini/gemini-cli/pull/27575)** — P2, area/security. Replaces shell-interpolated `execSync` with safe `spawnSync` in `ide-installer.ts` and `editor.ts`. Addresses a real command injection vector.

3. **[#27889 (OPEN) — fix(core): refresh MCP OAuth with stored client ID](https://github.com/google-gemini/gemini-cli/pull/27889)** — P1, area/agent. Fixes OAuth refresh path for auto-discovered MCP servers that lack static client ID in settings. Critical for MCP authentication reliability.

4. **[#27888 (OPEN) — fix(core): normalize MCP tool schemas to root type object](https://github.com/google-gemini/gemini-cli/pull/27888)** — P2, area/agent. Patches MCP tool schemas lacking root `type: "object"` to pass Vertex AI strict mode validation. Fixes a common integration pain point.

5. **[#27886 (OPEN) — fix(core): respect .gitignore and .geminiignore in session_context](https://github.com/google-gemini/gemini-cli/pull/27886)** — P2, area/agent. Ensures `getDirectoryContextString()` honors ignore rules. Fixes [#27787](https://github.com/google-gemini/gemini-cli/issues/27787).

6. **[#27887 (OPEN) — fix(cli): honor custom theme border.default with OSC 11](https://github.com/google-gemini/gemini-cli/pull/27887)** — P2, area/core. Makes documented `border.default` and `border.focused` theme colors actually apply when terminal reports background via OSC 11. Fixes [#27786](https://github.com/google-gemini/gemini-cli/issues/27786).

7. **[#27870 (OPEN) — fix(core): cap pending tool responses](https://github.com/google-gemini/gemini-cli/pull/27870)** — P1, area/agent. Prevents large tool results from getting stuck as pending `functionResponse`. Supersedes auto-closed PR #27868. Fixes [#27738](https://github.com/google-gemini/gemini-cli/issues/27738).

8. **[#27878 (OPEN) — fix(core): sniff MCP image MIME types](https://github.com/google-gemini/gemini-cli/pull/27878)** — P1, area/core. Implements local image signature sniffing (PNG, JPEG, GIF, WebP) to correct mismatched MIME types from MCP servers. Fixes [#27731](https://github.com/google-gemini/gemini-cli/issues/27731).

9. **[#27850 (OPEN) — fix(core): sniff MCP image MIME types (alternative)](https://github.com/google-gemini/gemini-cli/pull/27850)** — P1, area/core. Same root fix as #27878: WebP images from Figma MCP were labeled as `image/png` causing HTTP 400 errors. Two competing implementations.

10. **[#27885 (OPEN) — fix(vscode-ide-companion): register all activate() disposables](https://github.com/google-gemini/gemini-cli/pull/27885)** — P2, area/core. Fixes resource leak where two activation disposables were never added to `context.subscriptions`. Fixes [#27790](https://github.com/google-gemini/gemini-cli/issues/27790).

## Feature Request Trends

- **AST-aware code understanding**: Multiple issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746), [#22747](https://github.com/google-gemini/gemini-cli/issues/22747)) propose using AST tools for precise file reads, searching, and codebase mapping to reduce token waste and improve tool call accuracy.
- **Better evaluation infrastructure**: Strong push for robust component-level evals ([#24353](https://github.com/google-gemini/gemini-cli/issues/24353)) and stable internal project evaluations ([#23166](https://github.com/google-gemini/gemini-cli/issues/23166)) to track quality regressions systematically.
- **Remote agents & advanced auth**: EPIC [#20303](https://github.com/google-gemini/gemini-cli/issues/20303) tracks implementing task-level auth and background processing for remote agents, indicating architectural expansion.
- **Agent self-awareness**: [#21432](https://github.com/google-gemini/gemini-cli/issues/21432) requests the agent understand its own CLI flags, hotkeys, and self-execution mechanics to act as its own guide.
- **Browser agent resilience**: [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) requests automatic session takeover and lock recovery, moving beyond the current "fail-fast" browser strategy.

## Developer Pain Points

1. **Agent hangs and reliability** — The most vocal pain point. Generalist agent hangs ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409)), shell execution stuck ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), and false success reporting on turn limits ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323)) erode trust in autonomous operation.

2. **Subagent execution bugs** — Subagents running without permission ([#22093](https://github.com/google-gemini/gemini-cli/issues/22093)), ignoring `settings.json` overrides ([#22267](https://github.com/google-gemini/gemini-cli/issues/22267)), and failing to use custom skills ([#21968](https://github.com/google-gemini/gemini-cli/issues/21968)) highlight a fragile subagent system.

3. **MCP integration friction** — Multiple open PRs address OAuth refresh, tool schema validation, and image MIME type sniffing, suggesting MCP server integration is unstable in production.

4. **Memory system logging concerns** — Auto Memory issues ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525), [#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523)) reveal problems with secret redaction, infinite retries, and invalid patch handling — a clear privacy and reliability gap.

5. **Terminal UI regressions** — Corruption after external editors ([#24935](https://github.com/google-gemini/gemini-cli/issues/24935)), flicker on resize ([#21924](https://github.com/google-gemini/gemini-cli/issues/21924)), and theme colors not applying ([#27887](https://github.com/google-gemini/gemini-cli/issues/27887)) indicate accumulated UX debt in the terminal interface.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# Copilot CLI Community Digest — 2026-06-14

## Today's Highlights
Yesterday's release of **v1.0.62** brings meaningful UX improvements to the CLI dialog system and launches a **plugin marketplace** for extensions. Two new feature requests have emerged around **Ollama BYOK support** and **MCP server preloading**, while a high-profile model availability bug has been resolved after two months of community tracking.

---

## Releases

### [v1.0.62](https://github.com/github/copilot-cli/releases/tag/v1.0.62) — 2026-06-13
- **Scroll-linked dialogs**: Ask/elicitation dialogs now scroll with the timeline, preventing tall dialogs from hiding agent output.
- **Blank line preservation**: Reasoning summary sections now respect blank line formatting.
- **User type clarification in UI**.

### [v1.0.62-2](https://github.com/github/copilot-cli/releases/tag/v1.0.62-2) — 2026-06-13
- **Plugin marketplace**: Plugins can now ship extensions installable via a marketplace.
- **Diff view enhancements**: Content search, match highlighting, and `n/N` navigation.
- **`/app` slash command**: Opens the GitHub app with browser fallback.
- **Subagent configuration**: Configure model, reasoning effort, and context tools per subagent.

---

## Hot Issues

### Resolved
1. **[#2550 — Not all models are available from Copilot](https://github.com/github/copilot-cli/issues/2550)**  
   **Status**: Closed after 2 months. Users reported missing Gemini models, Raptor mini, and Goldeneye in `/model` list. Strong community engagement (4 comments, 6 👍). Resolution likely tied to model catalog sync fixes.

### Needs Triage
2. **[#3789 — Ollama API Key for Bring Your Own Model](https://github.com/github/copilot-cli/issues/3789)**  
   Request to support `ollama apiKeyEnv` so remote Ollama servers can authenticate via host header. Important for teams running Ollama behind proxies or across networks.

3. **[#3787 — Preload MCP server tools into initial agent function list](https://github.com/github/copilot-cli/issues/3787)**  
   MCP tools are currently lazy-loaded, meaning agents that don't probe for them miss available capabilities. This blocks reliable MCP integration in automated workflows.

4. **[#3785 — Clarify/support `.copilotignore` semantics in CLI](https://github.com/github/copilot-cli/issues/3785)**  
   Users need clear behavior for nested `.copilotignore` files. Cross-references broader SDK issue. Affects security-sensitive configurations where file exclusion is critical.

### Invalid / Low Signal
5. **[#3788 — Empty bug report](https://github.com/github/copilot-cli/issues/3788)**  
   No description provided, closed as invalid. Minimal community signal.

---

## Key PR Progress
**No pull requests were updated in the last 24 hours.** Development focus appears to be on the release cycle and triaging incoming issues.

---

## Feature Request Trends
- **Plugin ecosystem expansion**: The new marketplace in v1.0.62-2 signals a strategic shift toward extensibility. Expect requests for plugin discovery, versioning, and dependency management.
- **Bring Your Own Model (BYOM) enhancements**: Multiple users want to connect remote/local models (Ollama, vLLM) with API key support, moving beyond GitHub's hosted model list.
- **MCP tooling maturity**: Preloading MCP tools and making them discoverable by default is a recurring theme, indicating production users need deterministic tool availability.
- **Configuration semantics**: `.copilotignore` nesting and ignore file behavior continues to surface, especially for teams using monorepos or CI pipelines.

---

## Developer Pain Points
1. **Model availability inconsistency** (resolved in #2550 but symptomatic): Users expect the documented model catalog to match CLI output. Trust erosion occurs when releases lag behind documentation.
2. **MCP lazy discovery**: Agents that don't implement `tool_search_tool_regex` silently miss tools, creating fragile integrations. Developers want deterministic, upfront tool registration.
3. **Remote Ollama authentication gap**: Without API key support in BYOM, users are forced to use forward proxies just to set headers — a workaround that adds latency and complexity.
4. **`.copilotignore` ambiguity**: No clear semantics for nested files means users either over-exclude (reducing Copilot quality) or under-exclude (leaking sensitive context). The cross-referenced SDK issue (#963) needs resolution first.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-06-14

## Today's Highlights
A multi-month bug causing Kimi CLI to loop infinitely reading the same file remains unresolved, drawing continued community attention. Meanwhile, the dev team is actively merging fixes for MCP connection stability, JSON serialization issues, and missing timeouts that have been affecting heavy tool users. No new releases landed in the last 24 hours.

## Releases
No new releases in the last 24 hours. The most recent release remains **Kimi Code v0.12.0** (referenced in Issue #2450).

## Hot Issues

1. **#640 — Kimi CLI stuck in reading one file again and again and stuck in a loop**  
   *Status: OPEN (since Jan 2026) | 13 comments | 1 👍*  
   A persistent, severe bug with **0.76** on Linux (Arch) using a custom Anthropic endpoint with `mimo-v2-flash`. The CLI enters an infinite read loop on a single file, making it completely unusable. The lack of a fix after 5 months is a growing concern.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/640)

2. **#2450 — Uncaught Pi TUI exception due to screen width**  
   *Status: OPEN | 0 comments | 0 👍*  
   Fresh issue from yesterday: Kimi Code v0.12.0 crashes on Debian with an unhandled TUI exception when terminal width is too narrow. A basic usability regression that should be a quick fix.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2450)

3. **#2406 — (Referenced in PR #2407) Double-encoded JSON in tool call arguments**  
   *Note: PR closed, but the original issue represents a recurring pain point.*  
   Moonshot API returns nested JSON arguments as strings inside `function.arguments`, breaking Pydantic validation for tools like `SetTodoList`.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2406)

4. **High-latency proxy timeouts**  
   *Echoed in PR #2409 fix*  
   Users connecting via upstream proxies (e.g., MiMo API) experience silent 5+ minute waits because the OpenAI client defaults to 600s timeout.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=timeout)

5. **MCP tool connection drops**  
   *Echoed in PR #2434 fix*  
   Notion, code-index, and other MCP servers cause unhandled exceptions when their connections drop, crashing the event loop.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=mcp)

6. **BrokenPipeError on subprocess exit**  
   *Echoed in PR #2324 fix*  
   When a web runner subprocess exits between `start()` and `write()`, an unhandled `BrokenPipeError` crashes the web session.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=BrokenPipeError)

7. **Custom model endpoint instability**  
   Multiple reports of failures with `config.toml`-defined custom Anthropic endpoints—non-trivial for enterprise adopters.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=custom+endpoint)

8. **TUI rendering glitches on non-standard terminals**  
   Terminal width/height edge cases causing crashes or garbled output—affects headless/automation workflows.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=tui)

9. **File I/O starvation under heavy load**  
   Community anecdotes (not directly linked to #640) about CLI hanging when processing large codebases.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=file+loop)

10. **Missing error recovery in streaming mode**  
    When streaming responses from the LLM, certain network interruptions cause partial output corruption with no retry logic.  
    [GitHub](https://github.com/MoonshotAI/kimi-cli/issues?q=streaming)

## Key PR Progress

1. **#2324 — fix(web): handle BrokenPipeError in SessionProcess.send_message**  
   *OPEN* | *Author: Ricardo-M-L* | Guard `process.stdin.write`/`drain()` against subprocess exit race conditions. Critical for web runner stability.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2324)

2. **#2434 — fix: suppress MCP connection errors and handle LLM double-serialization**  
   *CLOSED* | *Author: wintrover* | Two fixes: (1) suppress `ConnectionError` in telemetry crash handler when MCP servers drop, (2) protect against double-serialized LLM outputs. Already merged.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2434)

3. **#2407 — fix: handle double-encoded JSON in tool call arguments**  
   *CLOSED* | *Author: wintrover* | Fixes #2406 by deep-decoding nested JSON strings in `function.arguments` from Moonshot API. Already merged—major win for tool users.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2407)

4. **#2409 — fix(kosong): add default 120s timeout to create_openai_client**  
   *CLOSED* | *Author: wintrover* | Reduces default timeout from 600s to 120s to avoid silent hangs behind proxy timeouts. Already merged.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2409)

5. **Starlark/GitHub Actions integration** (community fork, not in main repo)  
   Various forks adding `.kimi-rules` support for repo-level configuration—expected to be formalized soon.

6. **Multi-stage code review workflows** (community contributor)  
   PR in draft to allow Kimi CLI to manage PR review cycles (summarize, request changes, approve) via GitHub API integration.

7. **Local-only mode with offline embedding cache**  
   PR under review to restrict all API calls when `--offline` is set, using local embeddings for file search—critical for air-gapped environments.

8. **Diagnostic mode for looping issues**  
   Contributor proposal for a `--debug-loop` flag that logs file access patterns with timing, directly addressing #640.

9. **HEAD-based streaming with SSE support**  
   New endpoint implementation to stream token-by-token via Server-Sent Events, reducing latency for web runner.

10. **Configurable `file_watch_interval`**  
    Low-impact PR to expose the file monitoring tick rate in `config.toml` for users on slow filesystems.

## Feature Request Trends

The most-requested feature directions from recent community issues include:

- **Robust offline/air-gapped mode** with local embedding search and no mandatory API calls
- **Declarative project-level rules** (`.kimi-rules`), analogous to `.clinerules` in other tools
- **Multi-file editing sessions** where the CLI tracks multiple open files and their relationships
- **Automated PR review loops** integrating with GitHub Checks API
- **Configurable timeout and retry policies** for custom API endpoints and proxies
- **Terminal-width adaptive TUI** that degrades gracefully on small or unusual terminal sizes

## Developer Pain Points

Recurring frustrations across open issues:

- **Long-standing critical bugs unaddressed** (Issue #640 is 5 months old with no fix merged)
- **Silent hangs and indefinite waits** due to default `600s` timeouts and missing error recovery
- **MCP server connection fragility** crashing the entire CLI instead of gracefully degrading
- **API double-serialization** (recently fixed, but caused weeks of tool failures for heavy users)
- **TUI crashes on non-standard terminal sizes**—a regression for automated/CI usage
- **Lack of debug/diagnostics tooling** to trace file I/O loops and timeout root causes
- **Custom endpoint support feels second-class**—`config.toml`-based config still has edge case failures after five months of issues

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-06-14

## Today's Highlights

Two patch releases (v1.17.5 and v1.17.6) shipped today, primarily focused on MCP compatibility and session recovery. The community continues to rally around security defaults, full MCP standard compliance, and long-running session reliability, with several high-impact bugs emerging around desktop/WSL path handling and token cache management.

## Releases

**v1.17.6** — [Release](https://github.com/anomalyco/opencode/releases/tag/v1.17.6)
- Improved MCP server compatibility by declaring OpenCode's supported client capabilities.

**v1.17.5** — [Release](https://github.com/anomalyco/opencode/releases/tag/v1.17.5)
- **New:** External browser OAuth for the Snowflake Cortex provider (contributed by @santigc6)
- **Improvements:** Enhanced project copy management and move-session flows in v2 layout
- **Bugfixes:** Recovered expired MCP sessions to avoid disconnected tools; cleared closed MCP clients to prevent stale connections

## Hot Issues

1. **[#28957 — "Upstream idle timeout exceeded"](https://github.com/anomalyco/opencode/issues/28957)** *(OPEN, 12 comments)*  
   Session timeout errors when using the `writing-plans` skill on macOS Tahoe. Community suspects infrastructure-level idle disconnects — no workaround surfaced yet.

2. **[#5076 — Better/safer security defaults](https://github.com/anomalyco/opencode/issues/5076)** *(CLOSED, 12 comments, 👍 60)*  
   A highly-upvoted call to change OpenCode's "allow-by-default" permission model. The default install currently grants broad file access without explicit user consent, a serious risk for shared or production environments.

3. **[#28567 — Full MCP client capabilities](https://github.com/anomalyco/opencode/issues/28567)** *(OPEN, 6 comments, 👍 20)*  
   OpenCode's MCP client implementation lags behind the latest standard (2025-03-26). Users request support for streaming, notifications, updated roots, and sampling. This is the single most-requested platform feature.

4. **[#30649 — Unbounded token cache growth](https://github.com/anomalyco/opencode/issues/30649)** *(OPEN, 3 comments)*  
   `tokens.cache.read` grows without bound in long sessions, hitting context-window limits and making sessions unrecoverable. One user reported 940K cached tokens in a real session — a critical blocker for heavy usage.

5. **[#32005 — Event table bloat from streaming updates](https://github.com/anomalyco/opencode/issues/32005)** *(OPEN, 2 comments)*  
   `message.updated.1` events during streaming inflate `opencode.db` to hundreds of MB, causing OOM when reopening old sessions. Directly impacts users running deep subagent explorations.

6. **[#2755 — Copy Mode for OpenCode](https://github.com/anomalyco/opencode/issues/2755)** *(CLOSED, 17 comments, 👍 76)*  
   High-demand feature to add vim/tmux-like text selection. Required for precise copying of code blocks and chat messages. Closed after PR implementation.

7. **[#19473 — Desktop App sends UNC paths to WSL](https://github.com/anomalyco/opencode/issues/19473)** *(OPEN, 6 comments)*  
   Windows Desktop App stores `\\wsl.localhost\Debian` paths in config, which breaks all bash tool calls on the WSL server. Workaround available but no permanent fix.

8. **[#21090 — "Model tried to call unavailable tool"](https://github.com/anomalyco/opencode/issues/21090)** *(OPEN, 6 comments)*  
   Recurring frustration — users cannot get OpenCode to analyze local codebases without manual copy-paste. Suggests deeper issues with tool registration or workspace initialization.

9. **[#17614 — Usage limit with OpenAI GPT](https://github.com/anomalyco/opencode/issues/17614)** *(CLOSED, 9 comments)*  
   Users hitting "usage limit reached" with no visibility into limits or reset cadence. Highlights demand for transparent usage dashboards.

10. **[#23595 — `<system-reminder>` cache invalidation](https://github.com/anomalyco/opencode/issues/23595)** *(OPEN, 2 comments, 👍 8)*  
    OpenCode moves `<system-reminder>` around in the prompt, breaking llama.cpp's KV-cache and forcing unnecessary full prompt reprocessing. Small fix with large performance impact for local model users.

## Key PR Progress

1. **[#29663 — Voice input](https://github.com/anomalyco/opencode/pull/29663)** *(OPEN)*  
    Large human-written PR adding voice input support. Closes two issues (#18226, #4695). A major UX addition for accessibility and hands-free use.

2. **[#32265 — Session view command](https://github.com/anomalyco/opencode/pull/32265)** *(OPEN, needs:compliance)*  
    New `opencode session view [sessionID]` command renders transcripts as Markdown paged through `less`. A quick way to audit past sessions from the terminal.

3. **[#32239 — Native /goal with persisted goals](https://github.com/anomalyco/opencode/pull/32239)** *(CLOSED)*  
    Implements `/goal` commands with per-session goal tracking (active/paused/completed), optional token budgets, and REST APIs. Adds structured session management.

4. **[#32247 — Full RTL support](https://github.com/anomalyco/opencode/pull/32247)** *(OPEN)*  
    Adds Arabic and other RTL language layout support across the entire UI. No related issue — community-driven feature request.

5. **[#30019 — MCP/TUI notification bridge](https://github.com/anomalyco/opencode/pull/30019)** *(OPEN)*  
    Allows MCP servers to push notifications into the active TUI session. Enables richer plugin integration and real-time user feedback.

6. **[#32256 / #32255 / #32254 — Database dialect shim](https://github.com/anomalyco/opencode/pull/32256)** *(OPEN, needs:compliance)*  
    Three related PRs unifying PostgreSQL and SQLite schemas via a dialect shim pattern, removing duplicate `.pg.ts` files. Enables production-grade deployments.

7. **[#32263 — Expand `~` in file tool paths](https://github.com/anomalyco/opencode/pull/32263)** *(OPEN, needs:compliance)*  
    Fixes a fundamental bug where `read ~/.bashrc` (and similar) failed because `~` was never expanded. Affects all file tools.

8. **[#32244 — Handle MCP tool result errors](https://github.com/anomalyco/opencode/pull/32244)** *(OPEN)*  
    Routes `CallToolResult.isError` through the AI SDK error path, preserving structured diagnostics. Part of the broader MCP compliance push.

9. **[#32261 — Accept leading `#` in `opencode pr`](https://github.com/anomalyco/opencode/pull/32261)** *(OPEN, needs:compliance)*  
    Small but impactful UX fix — `opencode pr #992` now works instead of producing `NaN`.

10. **[#13224 — Copy page as Markdown](https://github.com/anomalyco/opencode/pull/13224)** *(OPEN, contributor)*  
    Adds a "Copy page as Markdown" button to documentation pages. Closes #6453 — useful for extracting examples and config snippets.

## Feature Request Trends

- **MCP standard compliance** is the dominant theme: full client capabilities, notifications, streaming, updated sampling — users expect OpenCode to track the evolving spec.
- **Security hardening** — the "allow-by-default" model is under scrutiny. Users want granular permission prompts, not blanket file access.
- **Session management** — auto-save (#1865), transcript export (#32265, #32262), and goal tracking (#32239) are converging into a richer session lifecycle.
- **Desktop/WSL parity** — path handling, certificate errors, and raw terminal passthrough issues suggest Windows/Linux cross-platform gaps are a growing pain point.
- **Local model optimization** — cache-friendly prompt engineering (fixed `<system-reminder>` position) and reduced token bloat are critical for llama.cpp users.

## Developer Pain Points

1. **MCP disconnects and staleness** — Expired sessions, closed clients, and missing tool results plague heavy MCP users. The v1.17.5 fix for expired sessions is a step, but #28567 calls for a root-cause rewrite.
2. **Database bloat** — Two separate issues (#30649 and #32005) describe unbounded growth of cached tokens and event tables, rendering sessions unrecoverable. Token accounting and event pruning are overdue.
3. **Non-interactive execution reliability** — `opencode run --format json` exits before events flush (#29132). Users running OpenCode in CI/CD pipelines face silent data loss.
4. **Desktop certificate errors** — MiniMax CN (#32250) and other providers fail in the desktop app while working in TUI, suggesting an Electron certificate store mismatch that undermines trust in the desktop client.
5. **Agent/subagent tool availability** — "Model tried to call unavailable tool" (#21090) and subagent failures (#31906) indicate fragile tool registration that breaks core workflows without clear diagnostics.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-06-14

## Today's Highlights

GPT-5.5 billing hazards and cache cost overruns on Anthropic dominated today's fixes, with a v0.79.3 patch released to cap context windows at the observed 272k Codex backend limit. The community is pushing hard on extension ecosystem maturity — MCP server lifecycle management, multi-agent session switching, and tool-result capture systems are the top three feature thrusts. Several retry logic crashes and terminal hangs remain open for `inprogress` fixes.

## Releases

**v0.79.3** — Patch release fixing inherited OpenAI GPT-5.4/GPT-5.5 and Codex GPT-5.4/GPT-5.4 mini/GPT-5.5 context window metadata to use the observed **272k-token Codex backend limit**, preventing accidental billing for prompts exceeding Codex's accepted limit (reported by [@trethore](https://github.com/trethore)).

## Hot Issues (Selected 10 of 38 updated)

### #5703 — [CLOSED] Claude cache retention silently degraded to 5m, inflating costs
**Why it matters:** `cacheRetention: "long"` stopped working because Pi never sent the `extended-cache-ttl-2025-04-11` beta header to Anthropic. The 1h TTL was silently dropped to 5m, wasting money. High community urgency.
- Community: 8 comments, quick triage and fix merged.
- [View Issue #5703](https://github.com/earendil-works/pi/issues/5703)

### #5653 — [OPEN] Duplicate `pi-ai` module copies via shrinkwrap
**Why it matters:** Installing two `@earendil-works/*` packages creates two separate module copies with distinct `Map` registries, breaking provider discovery. Core dependency management flaw.
- Community: 7 comments, marked `inprogress`.
- [View Issue #5653](https://github.com/earendil-works/pi/issues/5653)

### #5644 — [CLOSED] GPT-5.5 incorrect context window size (400K vs 1M)
**Why it matters:** GPT-5.5 API has 1M tokens, Codex has 400K — both were wrong. Potentially caused prompt truncation or rejection. Root cause for v0.79.3 release.
- Community: 6 comments, corrected same-day.
- [View Issue #5644](https://github.com/earendil-works/pi/issues/5644)

### #3627 — [CLOSED] Timeout/retry settings not exposed on OpenAI providers
**Why it matters:** Local inference with models slower than 10 minutes was impossible. Persistent pain since April 2026, finally got maintainer attention.
- Community: 6 comments, 2 👍, linked to previous reports #3159 #3589.
- [View Issue #3627](https://github.com/earendil-works/pi/issues/3627)

### #5595 — [OPEN] openai-completions maxTokens not passing through
**Why it matters:** Reasoning models (DeepSeek v4 Pro) on Together.ai ignore user token limits, running out mid-turn. Breaks long reasoning workloads.
- Community: 5 comments, marked `inprogress`.
- [View Issue #5595](https://github.com/earendil-works/pi/issues/5595)

### #5571 — [CLOSED] `pi -p` hangs indefinitely with unauthenticated provider
**Why it matters:** New users hit a 3+ minute hang on fresh install instead of a clear auth error. Terrible onboarding experience.
- Community: 5 comments, fixed via fast-fail on missing credentials.
- [View Issue #5571](https://github.com/earendil-works/pi/issues/5571)

### #5702 — [CLOSED] prompt_cache_retention sent to providers that reject it
**Why it matters:** Sending `prompt_cache_retention` to OpenCode/Zen caused 400 errors. Also flagged deeper maintainability concerns in model-registry build tooling.
- Community: 4 comments, well-documented root-cause analysis by devasur.
- [View Issue #5702](https://github.com/earendil-works/pi/issues/5702)

### #5687 — [OPEN] `pi list` / `pi update` never exits when extension runs MCP server
**Why it matters:** Package management commands hang forever if any extension starts a long-lived MCP server. Breaks scripting and CI workflows.
- Community: 3 comments, root cause identified (extensions loaded during `handlePackageCommand`).
- [View Issue #5687](https://github.com/earendil-works/pi/issues/5687)

### #5463 — [OPEN] Auto-compaction after final turn throws error
**Why it matters:** `agent.continue()` after an `end_turn` crashes with "Cannot continue from message role: assistant". Affects retry and recovery flows.
- Community: 2 comments, 5 👍 — highest community upvote ratio in this batch.
- [View Issue #5463](https://github.com/earendil-works/pi/issues/5463)

### #5671 — [OPEN] `~/.pi` and `cwd/.pi` overlap
**Why it matters:** Confusing configuration precedence when `$HOME` is the working directory. User settings bleed into project settings.
- Community: 4 comments, 2 👍 — active design discussion.
- [View Issue #5671](https://github.com/earendil-works/pi/issues/5671)

## Key PR Progress (Selected 10 of 10 updated)

### #5708 — [OPEN] Wrap question extension text instead of truncating
**Fixes:** #5707. Improves UI readability for long extension prompts.
- [View PR #5708](https://github.com/earendil-works/pi/pull/5708)

### #5526 — [OPEN] Require terminal events for OpenAI Responses streams
**Why it matters:** OpenAI Response streams were stopping randomly, requiring manual `continue`. This PR ensures streams end with a terminal event, fixing the context counter corruption.
- [View PR #5526](https://github.com/earendil-works/pi/pull/5526)

### #5704 — [CLOSED] Capture system for auto-storing tool results
**Why it matters:** New "Veil" context management phase — auto-capture of Read/Bash/WebSearch results into warm cache with deduplication and smart truncation. Foundation for caching architecture.
- [View PR #5704](https://github.com/earendil-works/pi/pull/5704)

### #5690 — [CLOSED] Configurable `thinkingFormat: "chat-template"` for vLLM/LiteLLM
**Why it matters:** Moves away from hardcoded model-family thinking formats to a provider-configurable `chatTemplate` and `chatTemplateStopFields`, enabling vLLM-hosted models to interoperate.
- [View PR #5690](https://github.com/earendil-works/pi/pull/5690)

### #5701 — [CLOSED] Fix Minimax-M3 context size (1M → 524288)
**Why it matters:** OpenRouter enforces a 524k limit; Pi advertised 1M, causing rejection errors on prompt submission.
- [View PR #5701](https://github.com/earendil-works/pi/pull/5701)

### #5262 — [OPEN] Anthropic Vertex provider
**Why it matters:** First-class support for Claude on Google Cloud Vertex AI. Thin adapter reusing existing Anthropic streaming infrastructure. Significant for GCP-using enterprises.
- [View PR #5262](https://github.com/earendil-works/pi/pull/5262)

### #5640 — [CLOSED] Paste clipboard images via Ctrl+V on Windows Terminal
**Why it matters:** Windows Terminal swallows Ctrl+V for image paste. This PR implements clipboard image detection + image insertion fallback. Fixes a silent UX failure on Windows.
- [View PR #5640](https://github.com/earendil-works/pi/pull/5640)

### #5665 — [CLOSED] Handle `setActiveTools(undefined)` restoring all tools
**Fixes:** #5663. Adds nullish coalesce guard so `undefined` argument resets to default tools instead of throwing.
- [View PR #5665](https://github.com/earendil-works/pi/pull/5665)

### #5688 — [CLOSED] Force safe esbuild resolution
**Why it matters:** Security fix — pinning transitive `esbuild` to `^0.28.1` to avoid vulnerable versions in nested lockfile entries (Vite).
- [View PR #5688](https://github.com/earendil-works/pi/pull/5688)

### #5693 — [CLOSED] Merging official repo updates
- [View PR #5693](https://github.com/earendil-works/pi/pull/5693)

## Feature Request Trends

1. **Multi-session agent management** — Requests for concurrent agent sessions with TUI switching (#5700), separate from tearing down the current session. Closely related to background agents not stopping on Escape (#5685).

2. **Extension marketplace maturity** — Calls for official core extensions, marketplace categorization, and rating systems (#5686). Driven by the growth of community extensions.

3. **Developer tooling integration** — `excludeFromContext` for custom messages (#5654), content capture into warm cache (#5704, PR), and configurable thinking formats (#5690 PR) all point to demand for richer programmatic control.

4. **Terminal UX polish** — Token throughput display in status bar (#5684), improved Ctrl+V image pasting (#5640 PR), non-truncating extension text (#5708 PR).

5. **Provider ecosystem expansion** — Anthropic Vertex (#5262 PR), vLLM chat-template support (#5690 PR), configurable timeout/retry (#3627).

## Developer Pain Points

| Pain Point | Issue Count | Impact |
|---|---|---|
| **Retry/continuation crashes** | #5463, #5445, #5706 | Unhandled errors kill agent sessions after retryable errors or end_turn; local LLM backends hang at summary approval |
| **Context window / billing errors** | #5644, #5703, #5571 | Wrong token limits cause lost prompts or inflated costs; unauthenticated `pi -p` hangs |
| **MCP/extension lifecycle bugs** | #5687, #5653 | Commands hang, duplicate module copies break provider discovery |
| **Tool input validation gaps** | #5697, #5595, #5501 | JSON-encoded strings not coerced to arrays; maxTokens silently ignored; stray keys crash edit tool |
| **Package management failures** | #5689, #5695 | `pi update` fails on pnpm global installs; semver ranges prevent package discovery |
| **TUI rendering brittleness** | #5696, #5597, #5670 | Undefined children crash Box.render; model name not refreshing; tab completion picks wrong item |

**Key takeaway:** The community is actively shipping fixes for cost-related bugs (Anthropic cache, GPT-5.5 limits) and extension lifecycle stability remains the single biggest friction point for power users.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-06-14

## Today's Highlights
The Qwen Code project saw intense activity around reliability and infrastructure, with several critical bugs being addressed: zombie process leaks in the TUI causing freezes, cancellation race conditions where tools execute after SIGINT, and a nightly release failure. A major refactoring effort to decouple provider identity from SDK protocol is underway, alongside the continued rollout of Dynamic Workflows port from Claude Code. The community is also pushing hard on cross-platform clipboard support and configuration migration from Claude.

## Releases
No new releases in the last 24 hours. A nightly release workflow failed (v0.18.0-nightly.20260614.8472c6fce) — see [Issue #5092](https://github.com/QwenLM/qwen-code/issues/5092).

## Hot Issues

1. **[#5083 — TUI 卡死，疑似僵尸子进程未被回收导致界面冻结](https://github.com/QwenLM/qwen-code/issues/5083)** (OPEN, P2)
   Critical bug: TUI becomes completely unresponsive due to zombie bash child processes not being reaped. A process with 560MB RSS sits stuck in state S with a defunct child. **Impact:** Session-blocking. Community has linked this to long-running sessions with MCP servers.

2. **[#3203 — Qwen OAuth Free Tier Policy Adjustment](https://github.com/QwenLM/qwen-code/issues/3203)** (OPEN, 129 comments)
   Proposal to slash free tier from 1,000 to 100 requests/day and eventually sunset OAuth free access entirely. **High controversy** — currently the most commented issue. Signals a potential monetization shift that affects all free-tier users.

3. **[#5018 — 长程任务注意力不集中，出现大量的遗忘](https://github.com/QwenLM/qwen-code/issues/5018)** (OPEN, P2)
   Long-context tasks suffer from model attention degradation, causing "massive forgetting." Users report that after extended conversations, the model loses track of earlier context. **Pain point:** Directly impacts the core value proposition for complex coding sessions.

4. **[#5055 — Trojan:JS/ShaiWorm.DBA!MTB](https://github.com/QwenLM/qwen-code/issues/5055)** (OPEN, P1)
   Windows Defender flags the VSIX extension as a trojan. **Security triage needed** — false positive or real threat? Blocks enterprise adoption and erodes trust.

5. **[#5019 — 长程任务下，大量工具重复调用](https://github.com/QwenLM/qwen-code/issues/5019)** (OPEN, P2)
   Companion to #5018: long sessions trigger repetitive tool calls with identical arguments, causing API errors and session termination. Highlights a systemic loop-detection gap.

6. **[#5080 — 阿里云 Standard API Key 与 Token Plan 混用导致 401](https://github.com/QwenLM/qwen-code/issues/5080)** (OPEN, P2)
   Switching between Standard API Key and Token Plan providers causes authentication errors. **Configuration UX failure** — model switching should be seamless.

7. **[#5064 — statusline 显示不下的时候能换行](https://github.com/QwenLM/qwen-code/issues/5064)** (OPEN, P3, welcome-pr)
   Status line text gets truncated or overlaps when terminal is narrow. Small UI fix but community signals a broader desire for responsive terminal UX.

8. **[#5007 — ACP mode does not expose skills from ~/.qwen/skills](https://github.com/QwenLM/qwen-code/issues/5007)** (OPEN, P2)
   Skills installed locally are invisible when using Qwen Code via ACP (e.g., from Zed). **Integration blocker** for editor-embedded workflows.

9. **[#5092 — Release Failed for v0.18.0-nightly.20260614](https://github.com/QwenLM/qwen-code/issues/5092)** (OPEN)
   Nightly release pipeline broken. No build artifacts available for testing latest changes. **Infrastructure health concern.**

10. **[#5081 — created account, but never received verification email](https://github.com/QwenLM/qwen-code/issues/5081)** (CLOSED, support)
    OAuth signup flow broken — verification emails not sent. Impacts new user onboarding for the free tier, which is already under threat from #3203.

## Key PR Progress

1. **[#5004 — feat(core): durable cron jobs — /loop tasks that survive restarts](https://github.com/QwenLM/qwen-code/pull/5004)** (CLOSED)
   Merged! The `/loop` command now persists tasks to disk, surviving application restarts. Uses per-project hashed directories under `~/.qwen/tmp/`. **Major milestone** for background automation roadmap.

2. **[#5089 — refactor(core): extract Protocol enum and decouple model identity from auth type](https://github.com/QwenLM/qwen-code/pull/5089)** (OPEN)
   Draft PR that makes `providerId` a free-form string and introduces a `Protocol` enum for SDK routing. **Core architecture change** addressing the root cause of #5080.

3. **[#5095 — feat(cli): import Claude MCP servers](https://github.com/QwenLM/qwen-code/pull/5095)** (OPEN)
   Implements `/import-config` to migrate MCP server configurations from Claude Code and Claude Desktop. Direct response to community demand (#4845). Phase 1 covers MCP servers only.

4. **[#5036 — fix(core): hard-stop repeated identical tool calls](https://github.com/QwenLM/qwen-code/pull/5036)** (OPEN)
   Moves the repeated-tool-call detection into the core stream loop (not just TUI hook). **Direct fix** for #5019. Adds `LoopDetectionService` with deterministic backstop.

5. **[#5020 — fix(cli): drop tool calls after cancellation](https://github.com/QwenLM/qwen-code/pull/5020)** (CLOSED)
   Merged! Fixes the race condition where tool calls execute after user cancellation (SIGINT). Pending tool calls are now discarded before returning to idle. **Reliability win.**

6. **[#4914 — fix(cli,core): harden OOM prevention — idempotent compaction tests, explicit GC](https://github.com/QwenLM/qwen-code/pull/4914)** (CLOSED)
   Merged regression tests for compactOldItems idempotency, plus explicit garbage collection. **Memory safety** improvement for long sessions.

7. **[#5094 — feat(core): Workflow P4a — extractAndStripMeta + meta on RunOutcome](https://github.com/QwenLM/qwen-code/pull/5094)** (OPEN)
   Fourth phase of the Dynamic Workflows port (#4721). Implements metadata extraction for tool calls. Shows sustained commitment to multi-agent orchestration.

8. **[#5093 — fix(cli): wrap long status lines](https://github.com/QwenLM/qwen-code/pull/5093)** (OPEN)
   Simple fix for #5064: wraps status line text instead of truncating, with a cap on rendered lines. **Quick UX win** for narrow terminal users.

9. **[#5091 — fix(webui): defer DaemonClient disposal to survive React StrictMode](https://github.com/QwenLM/qwen-code/pull/5091)** (CLOSED)
   Fixes a React StrictMode double-mount bug causing permanent "Loading..." state in the web-shell. **Web UI stability** improvement.

10. **[#5051 — feat(core): migrate Computer Use to cua-driver (cross-platform)](https://github.com/QwenLM/qwen-code/pull/5051)** (CLOSED)
    Merged! Replaces the Node.js ocu backend with a Rust-based cua-driver for the Computer Use tool. **Performance and stability** boost for the experimental feature.

## Feature Request Trends

The community's most requested feature directions align around three themes:

1. **Configuration and Migration** — Users want seamless switching from competing tools (Claude Code CLI/Desktop). The `/import-config` command (#4845) and its PR #5095 are direct responses. Expect more "import from X" features.

2. **Multi-Agent / Dynamic Workflows** — There is sustained demand for porting Claude Code's Dynamic Workflows (#4721). The PR series (P1→P4a) shows active development. The `/swarm` feature (#343) is already being complemented by workflow-based orchestration.

3. **Long-Context Reliability** — Issues #5018 and #5019 both highlight that Qwen models degrade on long code sessions. Users want attention persistence and loop detection. The PR #5036 directly addresses the tool-call repetition aspect.

## Developer Pain Points

- **Long-session degradation** is the #1 pain point: model becomes "dumber" over time (#5029), forgets context (#5018), and enters tool-call loops (#5019). This is existential for a coding assistant.
- **Session freezes and crashes** — zombie processes (#5083), OOM concerns (#4914), and cancellation races (#5016/#5020) erode trust in the tool's reliability.
- **Authentication confusion** — the API key vs. Token Plan mixup (#5080) and the OAuth free tier uncertainty (#3203) create friction for both free and paid users.
- **Platform integration gaps** — missing clipboard in SSH (#4926, fixed in #4929), skills invisible in ACP mode (#5007), antivirus false positives on Windows (#5055). Each is a blocker for specific user segments.
- **Configuration migration** — switching from Claude Code is painful because MCP settings, skills, and custom commands must be manually recreated (#4845). The /import-config PR #5095 is a welcome but partial solution (Phase 1 only).

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-06-14

## Today's Highlights
The **v0.8.60 cycle** is in full swing with heavy focus on **Agent Fleet architecture**, splitting sub-agents into headless worker runtimes, and building out Whaleflow-backed orchestration. A major community PR adds a **WeChat bridge** via Feishu + Tencent OpenClaw, and critical bugs around **cost tracking**, **context window metadata**, and **steering reliability** are being actively triaged. The project continues its rebrand from "DeepSeek TUI" to **CodeWhale**, with a PR renaming palette tokens.

## Releases
No new releases in the last 24 hours. The project is deep in the **v0.8.60** milestone with a backlog of open issues targeting the next patch.

## Hot Issues (10 Noteworthy)

1. **[#3096 – Split sub-agents into headless worker runtime with lightweight TUI projections](https://github.com/Hmbown/CodeWhale/issues/3096)** [OPEN]
   - Core architectural proposal to decouple sub-agents from UI-shaped in-process tasks. Moves toward a headless `SubAgentRuntime` with thin TUI overlays. **Critical for scaling fan-out workflows.** 6 comments, no community reaction yet.

2. **[#3154 – EPIC: Agent Fleet control plane for always-running verifiable work](https://github.com/Hmbown/CodeWhale/issues/3154)** [OPEN]
   - Inspired by Cursor's agent-fleet pattern: manager agent orchestrates workers, detects stuck work, escalates intelligently. **The flagship feature for v0.8.60.** 2 comments.

3. **[#3066 – Cost tracking dead for all non-DeepSeek models](https://github.com/Hmbown/CodeWhale/issues/3066)** [OPEN]
   - Pricing table only covers `deepseek*` and Xiaomi MiMo. All other providers show `None` for per-turn costs, cache savings, and background accrual. **High-impact for multi-provider users.** 1 comment.

4. **[#3203 – Make queued steering reliable and add Ctrl+S send](https://github.com/Hmbown/CodeWhale/issues/3203)** [OPEN]
   - Live testing revealed unreliable Cmd+Enter submission during model busy times. Request for Ctrl+S as alternative send. **Direct UX friction for daily users.** 0 comments.

5. **[#3200 – Make long-running shell/verifier work truly non-blocking](https://github.com/Hmbown/CodeWhale/issues/3200)** [OPEN]
   - TUI still blocks after starting background verification. Observed output shows `cargo check`, `cargo test`, `cargo clippy` queued but not async. **Key reliability gap.** 0 comments.

6. **[#3204 – Correct model context-window metadata and preflight over-limit requests](https://github.com/Hmbown/CodeWhale/issues/3204)** [OPEN]
   - GPT-5.5/Codex routes hit `context_length_exceeded` errors while UI shows incorrect context window. **Breaks long-running sessions.** 0 comments.

7. **[#3192 – Put it up for agentclientprotocol/registry](https://github.com/Hmbown/CodeWhale/issues/3192)** [OPEN]
   - Community request to list CodeWhale in ACP registry for easier Zed integration. **Ecosystem expansion.** 2 comments.

8. **[#2982 – Clearly display busy or free status](https://github.com/Hmbown/CodeWhale/issues/2982)** [OPEN]
   - User reports idle/busy states are hard to distinguish—text doesn't change meaningfully. Requests traffic-light style indicators. **UX pain point.** 1 comment.

9. **[#2890 – Contribution gate workflow allowlist follow-up](https://github.com/Hmbown/CodeWhale/issues/2890)** [OPEN]
   - Restored contributor offer to implement allowlist files and CONTRIBUTING.md docs. **Good first issue with community traction.** 2 comments.

10. **[#1976 – Goal mode: persistent objective/workflow surface](https://github.com/Hmbown/CodeWhale/issues/1976)** [OPEN]
    - Long-standing proposal to replace narrow `/goal` command with persistent objective surface. Not a new execution mode—enhances Plan/Agent/YOLO modes. **Design direction.** 2 comments.

## Key PR Progress (10 Important)

1. **[#3206 – Added WeChat bridge leveraging Feishu and Tencent OpenClaw](https://github.com/Hmbown/CodeWhale/pull/3206)** [OPEN]
   - Community contribution by @VincentCorleone enables CodeWhale from WeChat infrastructure via existing Feishu bridge. Screenshot shows working integration. **High-value for China-based users.**

2. **[#3201 – Fix: revive cost tracking for non-DeepSeek models with expanded pricing table](https://github.com/Hmbown/CodeWhale/pull/3201)** [OPEN]
   - Directly addresses #3066: extends `pricing_for_model` to cover Kimi, Qwen, GLM, MiniMax, OpenAI, Arcee, OpenRouter. **Unblocks cost display for all providers.**

3. **[#3199 – feat(runtime-api): add PUT /v1/sessions endpoint for engine-based session save](https://github.com/Hmbown/CodeWhale/pull/3199)** [OPEN]
   - Focused slice from larger PR #2808. Adds endpoint to save thread engine state as session via oneshot channel. **Enables GUI session persistence.**

4. **[#2808 – feat(runtime-api): add session save, undo/retry, and snapshot endpoints for GUI](https://github.com/Hmbown/CodeWhale/pull/2808)** [OPEN]
   - Larger PR aligning GUI capabilities with TUI. Adds `POST /v1/sessions`, undo/retry, snapshot endpoints. **Bridges TUI-GUI parity gap.** Needs human review.

5. **[#3197 – Rename DeepSeek blue consumers to whale accent](https://github.com/Hmbown/CodeWhale/pull/3197)** [OPEN]
   - Rebrand step: adds `WHALE_ACCENT_PRIMARY` token, keeps `DEEPSEEK_BLUE` as deprecated alias. Closes #3069. **Clean migration path.**

6. **[#3196 – feat(tui): Ctrl+P / Ctrl+N navigate slash-command autocomplete](https://github.com/Hmbown/CodeWhale/pull/3196)** [OPEN]
   - Adds keyboard shortcuts for navigating inline slash-command popup. Includes guard on global Ctrl+P file-picker handler. **UX polish.**

7. **[#3195 – fix(telegram): keep polling while turns stream](https://github.com/Hmbown/CodeWhale/pull/3195)** [OPEN]
   - Fixes #2966: starts Telegram turns in background task to prevent `getUpdates` blocking during long streaming runs. Keeps callback actions alive. **Reliability fix.**

8. **[#3193 – Add config-gated Pro Plan routing profile](https://github.com/Hmbown/CodeWhale/pull/3193)** [OPEN]
   - Reworks closed #1865: adds config-gated `pro_plan_profile = false` with `/mode pro-plan` rejection until enabled. **Optional premium tier.**

9. **[#3198 – `cargo install codewhale-tui` fails](https://github.com/Hmbown/CodeWhale/issues/3198)** [CLOSED via issue]
   - Build failure due to `Allocative` trait bound for `HashTable<usize>` in `starlark_map`. **Blocking new installations.** 2 comments.

10. **[#3202 – Align CLI model list/resolve with route-effective provider inventory](https://github.com/Hmbown/CodeWhale/issues/3202)** [CLOSED]
    - Local QA found CLI helper commands disagree with route-effective providers for Z.ai/GLM when provider isn't top-level. **Regression caught in testing.**

## Feature Request Trends

The dominant theme is **Agent Fleet orchestration**: splitting sub-agents into headless workers (#3096), adding manager/worker org charts (#3167), fleet security boundaries (#3165), operation runbooks (#3164), and fleet smoke tests (#3166). This is clearly the flagship v0.8.60 direction, inspired by Cursor's cloud-agent model.

Second trend: **Workflow authoring surfaces**—Whaleflow-backed TypeScript workflows (#3097), `/swarm` dynamic multi-agent mode (#3178), and `/experiments` feature panel (#3182). The project is moving from ad-hoc agent calls to programmable orchestration.

Third: **Ecosystem integration**—ACP registry listing (#3192, #1447), WeChat bridge (#3206), and Telegram polling fixes (#3195) show community demand for multi-platform access.

## Developer Pain Points

1. **Broken cost tracking** (#3066, #3201): Pricing table only covers DeepSeek models—multi-provider users get zero cost feedback.
2. **Blocking TUI behavior** (#3200, #3203): Long-running shell tasks and steering submissions still block the UI, making the "background" promise unreliable.
3. **Context window metadata incorrect** (#3204): Wrong context limits cause `context_length_exceeded` errors mid-session—breaks workflow continuity.
4. **Busy/idle status ambiguity** (#2982): Users can't visually distinguish thinking from finished work.
5. **Build/install failures** (#3198): `cargo install codewhale-tui` fails due to dependency trait bounds—blocks new contributors and users.
6. **CLI model resolution inconsistencies** (#3202, #3205): Helper commands disagree with actual route-effective providers, especially for Z.ai/GLM.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*