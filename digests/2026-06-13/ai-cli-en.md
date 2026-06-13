# AI CLI Tools Community Digest 2026-06-13

> Generated: 2026-06-13 03:40 UTC | Tools covered: 9

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

Here is the cross-tool comparison report based on the provided community digests for June 13, 2026.

---

### Cross-Tool Comparison Report: AI CLI Developer Tools
**Date:** 2026-06-13

#### 1. Ecosystem Overview

The AI CLI developer tools ecosystem is characterized by rapid iteration and significant instability. While tool vendors push forward on autonomous agent architectures and cross-platform support, the communities are grappling with persistent reliability issues, including model access disruptions, session hangs, and critical bugs in core agent workflows. A clear trend is the demand for multi-model orchestration—using different models for planning versus execution—alongside a growing frustration with opaque billing and security false positives. The landscape is moving from single-model chat assistants toward complex, agentic pipelines, but the maturity of these systems is still catching up to user expectations.

#### 2. Activity Comparison

| Tool | Hot Issues (Today) | Active PRs (Today) | Release Status (Today) |
| :--- | :--- | :--- | :--- |
| **Claude Code** | 10 | 1 | **v2.1.177** (Major incident: Fable-5 model outage) |
| **OpenAI Codex** | 10 | 10 | **v0.140.0-alpha.x** (4 releases) |
| **Gemini CLI** | 10 | 10 | **v0.48.0-nightly** |
| **GitHub Copilot CLI** | 10 | 1 (inferred) | **v1.0.62-1** |
| **Kimi Code CLI** | 10 | 10 | None |
| **OpenCode** | 10 | 10 | None |
| **Pi** | 10 | 10 | **v0.79.2** |
| **Qwen Code** | 10 | 10 | **v0.18.0** |
| **DeepSeek TUI (CodeWhale)** | 10 | 10 | **v0.8.59** (Rebranding milestone) |

#### 3. Shared Feature Directions

Several cross-cutting requirements are appearing across multiple tool communities, indicating shared user needs.

- **Autonomous Multi-Agent Architectures:** A strong push for **tiered model orchestration** where a "smart" planner delegates to cheaper/faster worker agents.
    - *Tools:* **Claude Code** (#56913 – Opus orchestrator, Sonnet worker), **Gemini CLI** (#22323, #21968 – subagent orchestration fixes), **CodeWhale** (Agent Fleet milestone).
- **Enterprise Pricing & Cost Control:** Power users demand **higher-capacity team plans** and **better billing transparency**.
    - *Tools:* **Claude Code** (#47509 – 20x team tier), **Kimi Code** (#1994 – unclear token/credit billing), **Qwen Code** (#3203 – backlash against free tier reduction).
- **Agent Reliability & Safety:** Users are hitting critical walls with **unbounded recursion**, **silent failures**, and **cancellation issues**.
    - *Tools:* **Claude Code** (#68110 – unbounded agent spawning), **Gemini CLI** (#22323 – false GOAL success), **GitHub Copilot CLI** (#3782 – unbounded MCP respawn loop), **Qwen Code** (#5016 – tool execution after cancellation).
- **Cross-Platform and Input System Robustness:** **Windows and Linux compatibility** remains a major pain point.
    - *Tools:* **OpenAI Codex** (EFS-encrypted files, WSL path issues), **GitHub Copilot CLI** (#1999 – non-US keyboard input), **Gemini CLI** (#21983 – Wayland browser crash), **Claude Code** (#49917 – Windows installer failure).
- **Context and Session Management:** Communities want better control over **context windows**, **compaction**, and **persistent state**.
    - *Tools:* **OpenAI Codex** (#9046, #22335 – context overflow and compaction failures), **Gemini CLI** (#26522 – low-signal memory loops), **Kimi Code** (#2321 – `.kimiignore` for file filtering).

#### 4. Differentiation Analysis

The tools are diverging in their feature focus, target user, and technical approach.

- **Claude Code & OpenAI Codex** are leading the charge on **high-end, agentic workflows** but suffer from the most **disruptive platform-level incidents** (model outages, sandbox failures). They target power users and enterprises but are seen as less stable.
- **Gemini CLI & GitHub Copilot CLI** are focused on **enterprise security and integration**. Gemini is investing in AST-aware code intelligence and deterministic redaction, while Copilot is addressing backward compatibility and keyboard accessibility. Their communities are vocal about reliability and configuration control.
- **Kimi Code & Qwen Code** are **younger projects** with a strong focus on **core functionality and cost optimization**. Kimi is grappling with billing clarity, while Qwen is extending its reach with dedicated providers and daemon features. They serve a more budget-conscious and growing user base.
- **Pi & CodeWhale** are **rapidly innovating on multi-provider support**. Pi is expanding its model ecosystem (Anthropic Vertex, vLLM), while CodeWhale is building a distributed "Agent Fleet" architecture. They are attractive to users who want maximum flexibility and are willing to adopt newer, more experimental platforms.
- **OpenCode** stands out with its **comprehensive security audit** and focus on **permission system reliability**. It is well-suited for security-conscious teams but has unique bugs related to its database and UI.

#### 5. Community Momentum & Maturity

- **Highest Activity / Most Mature:** **Claude Code** and **OpenAI Codex** have the largest, most vocal communities, evidenced by high upvote counts and long-running, critical issues. However, this maturity comes with greater user frustration when major systems fail, as seen with the Fable-5 outage and Windows sandbox issues.
- **Rapidly Iterating:** **Gemini CLI** and **Pi** are moving fast, shipping daily or near-daily releases with significant architectural changes (e.g., Gemini’s MCP fixes, Pi’s new providers). **CodeWhale** is also in a high-velocity phase with its rebrand and Agent Fleet launch.
- **Growing Pains:** **Kimi Code** and **Qwen Code** are gaining adoption but are held back by fundamental issues like billing confusion and long-context reliability. Their communities are engaged but smaller in scale.
- **Stable but Stagnant:** **GitHub Copilot CLI** shows relatively low PR activity despite a high-priority ARM64 bug and a top-voted backward compatibility issue (#53). The emergence of community forks suggests a trust deficit with the core team’s direction.

#### 6. Trend Signals

Several industry trends are evident from the community feedback.

- **The "Unbundling" of the Model:** Developers no longer want a single model. The future is **multi-model orchestrators** where a powerful reasoning model plans tasks, cheaper models execute them, and specialized models handle specific domains. This is a direct response to cost and performance.
- **Platform Reliability is the New Moat:** As agentic workflows become more common, **stability and predictability** are more important than new features. The Fable-5 outage at Claude Code and the Windows sandbox death spiral at OpenAI Codex are existential threats to user trust. A "boring" but reliable tool may win long-term.
- **Security and Compliance are Bottlenecks:** False-positive safety flags (OpenAI Codex #27817, Claude Code #68130) and opaque permission systems (OpenCode #24335) are blocking legitimate, high-value use cases like financial analysis and DevOps. Tools that can calibrate safety checks without sacrificing user productivity will have a competitive advantage.
- **Cost Transparency is Non-Negotiable:** The backlash against Qwen Code’s free tier reduction and Kimi Code’s billing confusion signals that users are **price-sensitive and demand clear value**. Opaque token or credit-based billing models are causing significant community friction.
- **The Rise of the "Self-Hosted" Developer:** Interest in providers like **vLLM** (Pi), **Exa API** (CodeWhale), and **custom endpoints** (Claude Code) indicates a growing segment of developers who want to control their model infrastructure, often for cost, privacy, or latency reasons.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

Here is the community highlights report for the Claude Code Skills ecosystem.

---

## Claude Code Skills Community Highlights Report
**Data as of:** 2026-06-13 | **Source:** github.com/anthropics/skills

### 1. Top Skills Ranking (Most-Discussed Pull Requests)

The following PRs have generated the most community discussion and represent the highest-interest Skill proposals currently under review.

1.  **`document-typography`** (PR [#514](https://github.com/anthropics/skills/pull/514))
    - **Functionality:** Prevents common typographic errors in AI-generated documents (orphan words, widowed paragraphs, numbering misalignment) which are systemic issues in LLM output.
    - **Discussion:** High engagement around the universality of the problem; users noted this fixes a "death by a thousand cuts" issue in every document Claude generates. Some debate over whether this should be a default behavior rather than an opt-in skill.
    - **Status:** Open (High Activity)

2.  **`odt` (OpenDocument Text)** (PR [#486](https://github.com/anthropics/skills/pull/486))
    - **Functionality:** Enables creation, reading, and conversion of OpenDocument Format files (.odt, .ods) for use with LibreOffice and other open-source office suites.
    - **Discussion:** Strong interest from enterprise and open-source-first users. Key discussion point: how to handle template filling without breaking document structure.
    - **Status:** Open

3.  **`frontend-design` (Revision)** (PR [#210](https://github.com/anthropics/skills/pull/210))
    - **Functionality:** A comprehensive revision of the existing frontend-design skill to ensure every instruction is actionable within a single conversation, improving specificity and internal coherence.
    - **Discussion:** The community debated the balance between prescriptive design guidance vs. allowing Claude creative freedom. The author argued existing skills were too vague to produce consistent UI output.
    - **Status:** Open

4.  **SAP-RPT-1-OSS Predictor** (PR [#181](https://github.com/anthropics/skills/pull/181))
    - **Functionality:** Adds a skill for querying SAP's open-source tabular foundation model (SAP-RPT-1-OSS) for predictive analytics on enterprise business data.
    - **Discussion:** Industry-specific interest; discussion centered on the complexity of integrating external model APIs via Skills and the security implications of piping proprietary business data.
    - **Status:** Open

5.  **`testing-patterns`** (PR [#723](https://github.com/anthropics/skills/pull/723))
    - **Functionality:** Covers the full testing stack: Testing Trophy philosophy, AAA pattern, React Testing Library, and edge case coverage guidance.
    - **Discussion:** Broad approval; minimal controversy. Users requested expansion into end-to-end testing frameworks (Playwright/Cypress). Seen as a "must-have" for production code generation.
    - **Status:** Open

6.  **`n8n-builder` / `n8n-debugger`** (PR [#190](https://github.com/anthropics/skills/pull/190))
    - **Functionality:** Two skills for building and debugging n8n automation workflows from scratch or from existing JSON configurations.
    - **Discussion:** High enthusiasm from the automation community. Key discussion: these skills are "production-tested" which adds credibility.
    - **Status:** Open

7.  **`skill-quality-analyzer` / `skill-security-analyzer`** (PR [#83](https://github.com/anthropics/skills/pull/83))
    - **Functionality:** Meta-skills that evaluate other Skills across five dimensions (structure, documentation, security, etc.). The security analyzer checks for prompt injection and dangerous tool access patterns.
    - **Discussion:** Considered a critical tool for the maturity of the Skills ecosystem. Debate on whether these should be built into the core CLI vs. distributed as community skills.
    - **Status:** Open (Early-Stage)

---

### 2. Community Demand Trends (From Issues)

The Issues tracker reveals three dominant unmet needs:

- **Enterprise Skills Management (#228):** The highest-engagement issue (14 comments, 7 👍) requests organization-wide skill sharing. Users currently resort to manually distributing `.skill` files via Slack/Teams, which is unsustainable for teams. The demand is for a shared skill library or direct sharing links within Claude.ai.

- **Windows Compatibility (#556, #1061):** A critical infrastructure blocker. `run_eval.py` and the skill-creator suite are functionally broken on Windows due to Unix-first assumptions (subprocess `PATHEXT` handling, `cp1252` encoding, `select` on pipes). Multiple users have independently reproduced the 0% trigger rate bug (#556, 12 comments), which renders the description-optimization loop useless on the dominant desktop OS.

- **Namespace Trust & Security (#492):** Community skills distributed under the `anthropic/` namespace create a trust boundary vulnerability. Users may grant elevated permissions to skills they believe are official Anthropic releases. This security concern is gaining attention as the library grows.

- **Duplicate Content Bloat (#189):** Installing `document-skills` and `example-skills` plugins simultaneously yields identical skill files, wasting context window tokens. Users demand deduplication logic or clearer documentation on standalone vs. bundled skills.

---

### 3. High-Potential Pending Skills (Likely to Land Soon)

These PRs have active development momentum and are fixing critical infrastructure issues that block the entire developer experience:

1.  **`multi-tool evaluation fix`** (PR [#1140](https://github.com/anthropics/skills/pull/1140), SyedaQurratAI) — Fixes `evaluation.py` to correctly handle parallel tool calls and adds Windows support for `recalc.py` via `%APPDATA%` paths. Adds an `agent-creator` meta-skill alongside these fixes.

2.  **`Windows subprocess + encoding fix`** (PR [#1050](https://github.com/anthropics/skills/pull/1050), gstreet-ops) — Two one-line fixes for `run_loop.py` on Windows 11: honoring `PATHEXT` for `claude.cmd` invocation and fixing `cp1252` encoding issues.

3.  **`run_eval.py recall=0% fix`** (PR [#1298](https://github.com/anthropics/skills/pull/1298), MartinCajiao) — The most recent and comprehensive attempt to fix the 0% recall bug (#556). Proposes installing the eval artifact as a real skill and fixing stream reading, trigger detection, and parallel worker logic.

4.  **`color-expert`** (PR [#1302](https://github.com/anthropics/skills/pull/1302), meodai) — A self-contained color expertise skill covering ISCC-NBS, Munsell, XKCD, RAL, and color space selection tables (OKLCH for scales, OKLAB for gradients, CAM16 for perception).

---

### 4. Skills Ecosystem Insight

The community's most concentrated demand is for **operational infrastructure over domain-specific skills**: the top three discussions are about skill management, quality validation, and cross-platform reliability — users are demanding the tools to build and trust skills more than they are demanding new skill subjects.

---

# Claude Code Community Digest — 2026-06-13

## Today's Highlights

A major incident is unfolding today: **Claude Fable-5 model access appears to be revoked or failing across a large swath of users**, triggering a flood of duplicate bug reports and forcing developers onto Opus mid-session. Separately, v2.1.177 shipped with session title language detection and a new `footerLinksRegexes` setting, while the community continues to push hard for viable autonomous agent architectures with tiered model orchestration.

## Releases

**v2.1.177** (latest) — [View on GitHub](https://github.com/anthropics/claude-code/releases/tag/v2.1.177)
- Session titles now auto-detect and generate in the language of your conversation (configurable via the `language` setting)
- New `footerLinksRegexes` setting enables regex-matched link badges in the terminal footer row, configurable via user or managed settings
- Improved Bedrock credential handling

**v2.1.176** — [View on GitHub](https://github.com/anthropics/claude-code/releases/tag/v2.1.176)  
- Added `enforceAvailableModels` managed setting — when enabled, the `availableModels` allowlist constrains the Default model; disallowed models fall back to the first allowed entry, and user/project settings cannot override managed restrictions

## Hot Issues

1. **[#26224 — Claude Code hanging / freezing for 5–20+ minutes](https://github.com/anthropics/claude-code/issues/26224)**  
   *Open since Feb 2026 · 116 comments · 142 👍*  
   A long-standing, high-severity performance bug causing the CLI to stall on prompt processing. Still unresolved after 4 months — the most upvoted open bug in the tracker. Community sentiment is frustrated, with multiple users reporting they've had to migrate workflows.

2. **[#68129 — "Fable is not available" error](https://github.com/anthropics/claude-code/issues/68129)**  
   *Filed today · 16 comments*  
   Fresh report of the Fable-5 model access issue. User receives "Fable is not available" despite having an active subscription. Part of today's incident cluster.

3. **[#68128 — Model access error for claude-fable-5](https://github.com/anthropics/claude-code/issues/68128)**  
   *Filed today · 1 comment · 11 👍*  
   Rapidly accumulating upvotes — the core symptom report for the Fable-5 outage. Users are switching to Opus but finding it significantly slower for their workflows.

4. **[#68126 / #68137 / #68121 — Multiple Fable-5 "Invalid or Inaccessible Model" reports](https://github.com/anthropics/claude-code/issues/68126)**  
   *Filed today · ~20 combined comments*  
   Cluster of near-identical macOS and Linux reports all pointing to `claude-fable-5` being rejected by the API. Likely a server-side access control or model lifecycle issue affecting Max plan subscribers.

5. **[#68131 — Max plan user lost Fable-5 access mid-session](https://github.com/anthropics/claude-code/issues/68131)**  
   *Filed today · Closed · 5 comments*  
   User on Max plan lost access to Fable-5 without any configuration changes. Already closed as duplicate, but highlights the severity: even power users on the highest-paid tier are impacted.

6. **[#67609 — Advisor tool returns "unavailable" on Fable-5 beyond ~100K tokens](https://github.com/anthropics/claude-code/issues/67609)**  
   *Opened Jun 11 · 2 comments · 6 👍*  
   Possibly related to today's incidents: the Advisor tool specifically fails with `error_code: "unavailable"` on Fable-5 when transcripts exceed ~100K tokens. Suggests a per-model context window or capacity throttle.

7. **[#38183 — SendMessage tool referenced but not available — agent continuation broken](https://github.com/anthropics/claude-code/issues/38183)**  
   *Open since Mar 2026 · 19 comments · 21 👍*  
   Critical bug for multi-agent workflows: the agent system references a `SendMessage` tool that was removed when the `resume` parameter was deprecated. Any agent that attempts to communicate with sibling agents fails silently. Community calls this a "showstopper for real-world agent deployments."

8. **[#47509 — Team plan needs a Max 20x equivalent tier for power users](https://github.com/anthropics/claude-code/issues/47509)**  
   *Open · 8 comments · 37 👍*  
   Highly-upvoted pricing request. Current Team plan caps at 6.25x Pro usage; CTOs and tech leads relying on Claude Code CLI for agentic workflows want a **20x tier** equivalent to individual Max plans.

9. **[#56913 — Make autonomous Claude Code viable: tiered Opus + Sonnet + persistent state](https://github.com/anthropics/claude-code/issues/56913)**  
   *Open since May 2026 · 26 comments*  
   The most comprehensive vision for autonomous operation: using Opus as orchestrator brain, Sonnet as worker agent, with persistent project state. Growing community consensus that this architecture is the path forward for long-running AI development pipelines.

10. **[#49917 — Windows installer fails with HRESULT 0x80073CF6 after inconsistent state](https://github.com/anthropics/claude-code/issues/49917)**  
    *Open since Apr 2026 · 26 comments · 6 👍*  
    Long-running Windows installation bug. Failed installs leave the package in an unrecoverable state requiring system registry cleanup. Affects new users trying to onboard on Windows — still unaddressed after 2 months.

## Key PR Progress

*Only 1 PR was active in the last 24 hours:*

1. **[#26360 — Fix issues being auto-closed despite human activity](https://github.com/anthropics/claude-code/pull/26360)**  
   *[claude-code-assisted] · Closed today · by chrislloyd*  
   Fixes two automation bugs: the triage bot now recognizes `stale`/`autoclose` labels and removes them when humans comment on stale issues, and `closeExpired()` no longer overrides human interaction markers. Addresses long-standing community frustration with premature auto-closure.

## Feature Request Trends

The community is coalescing around **four major architectural demands** visible across recent issues:

1. **Autonomous Agent Architecture (Multi-Model Tiering)** — The most-discussed topic. Users want Opus as the orchestrator "brain" with Sonnet/Haiku as workers, persistent project state, and bounded recursion limits. Issue #56913 and #14321 (extended thinking for subagents) represent this push.

2. **Enterprise Pricing for Heavy Users** — A clear gap: individual Max plans offer 20x capacity, but team plans cap at 6.25x. Power users (CTOs, senior devs) need equivalent tiers in team/org plans. Issue #47509 captures this with strong upvote signals.

3. **Agent Recursion Control** — With unbounded agent spawning causing exponential token burn (#68110), the community wants depth limits, cost ceilings, and visibility into sub-agent tree structures. This is a safety/economic concern.

4. **Model Access Stability and Transparency** — The Fable-5 incident makes this urgent. Users want: model lifecycle announcements, grace periods during model transitions, clearer explanations for mid-session access revocations, and better error messages distinguishing "temporarily unavailable" from "permanently removed."

## Developer Pain Points

- **Fable-5 model access disruption** — The dominant pain point today. Widespread, sudden loss of model access mid-session with opaque error messages. Affected users report lost work and forced downgrades to Opus. No official communication from Anthropic as of digest time.

- **CLI hangs and freezing (Issue #26224)** — Unresolved for 4 months. The most impactful open bug by comment count and reactions. Forces developers to restart sessions, losing context and progress.

- **Agent tool ecosystem gaps** — `SendMessage` tool missing (#38183), unbounded recursive agent spawning (#68110), and no extended thinking for subagents (#14321) collectively make production autonomous workflows unreliable or dangerous.

- **Windows onboarding friction** — The installer bug (#49917) and Ctrl-V support issue (#68136) create a poor first impression for Windows developers. Installation recovery requires manual registry cleanup — a significant barrier.

- **Content policy false positives on development tasks** — Users writing Ansible playbooks (Issue #68130) and Playwright login scripts (Issue #68132) report being flagged as "offensive content" and downgraded from Fable-5. These are standard development tasks, raising concerns about over-aggressive policy enforcement.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-13

## Today's Highlights
A major push toward cross-platform path handling dominates today's PR activity, with engineers laying groundwork for native remote executors and unified path conventions across Windows, WSL, and macOS. Meanwhile, Windows Desktop users continue to face systemic sandbox failures, with multiple high-traffic issues reporting `spawn setup refresh` errors blocking Computer Use, Chrome, and Browser plugins. A fast-closed crash in the macOS Dock integration (`setDockTile:` recursion) was patched within hours, reflecting ongoing stability work.

## Releases
Four Rust alpha releases landed today in the `rust-v0.140.0-alpha` series (v14 through v17). These are tagged as "Release 0.140.0-alpha.x" with no further changelog detail in the commit messages. Likely contain incremental fixes from the ongoing cross-platform path and executor work.

## Hot Issues

1. **[#12564 — Allow renaming task/thread titles](https://github.com/openai/codex/issues/12564)** (79 comments, 111 👍)
   *Closed.* The most-upvoted issue this cycle. Users want to rename threads for history navigation. High community engagement suggests this is a critical UX gap.

2. **[#9046 — Context window overflow on fresh thread](https://github.com/openai/codex/issues/9046)** (25 comments)
   *Open.* User reports running out of context window at the beginning of a chat with a single question. Indicates possible context accounting bug or aggressive compaction failures.

3. **[#22423 — Unable to locate Codex CLI binary](https://github.com/openai/codex/issues/22423)** (20 comments)
   *Open.* WSL-related setup failure. The app errors on launch after WSL configuration, suggesting Electron resource pathing issues on Windows.

4. **[#25243 — macOS relaunch loop exhausts syspolicyd file descriptors](https://github.com/openai/codex/issues/25243)** (20 comments, 2 👍)
   *Open.* Critical macOS-specific bug. Codex enters infinite relaunch loop, exhausting system resources and blocking other app launches. Affects Pro users.

5. **[#24098 — Windows elevated sandbox fails after CLI update](https://github.com/openai/codex/issues/24098)** (19 comments, 6 👍)
   *Closed.* Elevated sandbox `spawn setup refresh` failure. Worked without elevation. One of many related Windows sandbox issues consolidated here.

6. **[#25220 — EFS-encrypted WindowsApps blocks bundled plugins](https://github.com/openai/codex/issues/25220)** (16 comments, 3 👍)
   *Open.* Copyfile fails on EFS-encrypted WindowsApps files. Blocks Computer Use, Browser, Chrome, LaTeX plugins for Windows Store installs.

7. **[#27175 — Desktop crash after update on empty sessions](https://github.com/openai/codex/issues/27175)** (15 comments, 3 👍)
   *Open.* Codex Desktop 26.602.71036 crashes immediately after update, even with no sessions. Pro users on Windows 11 affected.

8. **[#27817 — False positive cybersecurity flag on tax filing work](https://github.com/openai/codex/issues/27817)** (12 comments)
   *Open.* Normal finance/tax readiness conversation flagged as cybersecurity risk. Blocks users from legitimate workflows. Safety-check overreach.

9. **[#22335 — CLI remote compaction leaves threads without continuity](https://github.com/openai/codex/issues/22335)** (6 comments, 8 👍)
   *Open.* Remote compaction repeatedly fails. Resumed threads lose task continuity. High 👍 count indicates widespread frustration.

10. **[#27979 — Windows App no longer opens after June 12 update](https://github.com/openai/codex/issues/27979)** (8 comments)
    *Open.* Latest Windows Codex App update renders the application completely inoperable. Users cannot even access the About dialog.

## Key PR Progress

1. **[#27819 — path-uri: render native paths across platforms](https://github.com/openai/codex/pull/27819)** (OPEN)
   Introduces `PathUri` to support cross-OS app-server/exec-server communication. Avoids exposing URI encoding in public APIs. Foundation for the cross-platform executor work.

2. **[#28020 — protocol: retain executor cwd in command events](https://github.com/openai/codex/pull/28020)** (OPEN)
   Preserves executor's cwd and path convention through command lifecycle events. Carries `PathUri` plus `PathConvention` in begin/end events.

3. **[#27369 — Add dormant plugin script lifecycle state](https://github.com/openai/codex/pull/27369)** (OPEN)
   Merge-safe core lifecycle slice for plugin scripts. Dormant state machine behind default-off feature flag. Prepares for executor adapter PRs.

4. **[#28014 — unified-exec: launch remote commands without host sandbox](https://github.com/openai/codex/pull/28014)** (OPEN)
   Launches remote unified-exec commands directly to exec-server, bypassing app-host sandbox construction. Keeps approval handling and keys by environment and cwd URI.

5. **[#27937 — Add hermetic Wine exec-server test](https://github.com/openai/codex/pull/27937)** (CLOSED)
   Enables cross-OS orchestration tests using Wine. Validates path handling when app-server and exec-server run on different operating systems.

6. **[#27886 — Update policy wording](https://github.com/openai/codex/pull/27886)** (OPEN)
   Refines Guardian decision rules for sensitive-data egress. Preserves explicit user authorization for scoped personal-data sharing. Tested against historical replay suites.

7. **[#27961 — enforce managed remote control disable](https://github.com/openai/codex/pull/27961)** (CLOSED)
   Adds reliable deny gate for remote control in managed deployments. Removed compatibility no-op key.

8. **[#28002 — Send turn state through compact requests](https://github.com/openai/codex/pull/28002)** (OPEN)
   Fixes compaction losing turn state context. Ensures compact requests and surrounding sampling requests share the same `ModelClientSession` state.

9. **[#27971 — Coordinate cloud config bundle caching across processes](https://github.com/openai/codex/pull/27971)** (OPEN)
   Solves concurrent CLI and app-server instances independently fetching the same cloud configuration. Adds refresh ownership coordination.

10. **[#28012 — Add fail-closed plugin script resolver](https://github.com/openai/codex/pull/28012)** (OPEN)
    Dormant private resolver slice for plugin scripts. Parses candidate script commands, canonicalizes trusted plugin paths, attributes enabled matching skills.

## Feature Request Trends

- **Thread/History Management**: Usability improvements around chat history—renaming threads (#12564), persistent cwd across sessions (#23189), and preservation of settings (#27998).
- **Cross-Platform Path/Executor**: Strong demand for seamless Windows + WSL integration. Multiple issues and PRs target native path rendering, unified-exec, and executor environment identity.
- **Plugin Ecosystem Reliability**: Users want bundled plugins (Computer Use, Browser, Chrome, LaTeX) to work reliably across all platforms, particularly Windows. The `spawn setup refresh` failure pattern dominates.
- **Safety-Check Calibration**: Two cybersecurity false-positive reports (#27817, #28015) indicate safety filters are too aggressive for legitimate financial and DevOps tasks.

## Developer Pain Points

- **Windows Sandbox Death Spiral**: The `spawn setup refresh` failure is the single highest-frequency issue. It affects sandbox, node_repl, computer-use, browser, and Chrome plugins across both elevated and non-elevated modes. Multiple related issues (#24098, #24963, #25222, #25488, #26266, #26477, #26617) suggest a deeply rooted integration problem.
- **Update Breakage**: Multiple reports (#27175, #27979) show recent Windows Desktop updates rendering the app completely unusable. Loss of chat history (#27998) compounds the frustration.
- **Context Compaction Failures**: Both CLI and Desktop users report compaction failures leading to lost context and thread continuity (#9046, #22335). This impacts long-running sessions.
- **Path Handling on Windows/WSL**: Malformed paths (`\\wsl$`), drive letter assumptions, and EFS encryption blocking plugin installation are recurring themes for Windows users (#22672, #23189, #25220).

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-13

## Today's Highlights

A dense nightly release landed today (v0.48.0-nightly.20260613), bringing an important fix for atomic MCP tool discovery and a Vertex AI model mapping correction. On the issue tracker, work continues on several long-running agent reliability problems: the "Generalist agent hangs" bug (still open after 3+ months) and a concerning pattern where subagents report GOAL success despite hitting their turn limits. The community is also seeing increased activity around AST-aware code reading and evaluation infrastructure.

## Releases

**v0.48.0-nightly.20260613.g9e5599c32** — [Release page](https://github.com/google-gemini/gemini-cli/releases/tag/v0.48.0-nightly.20260613.g9e5599c32)

Changes:
- **fix(core):** Implemented atomic update in MCP tool discovery to prevent race conditions during tool registration ([#27619](https://github.com/google-gemini/gemini-cli/pull/27619))
- **fix:** Vertex AI model mapping fix ([#27749](https://github.com/google-gemini/gemini-cli/pull/27749))
- Documentation and migration command added

## Hot Issues

1. **#24353 — Robust component level evaluations** [P1, agent]  
   An EPIC tracking the evolution from 76 initial behavioral eval tests to a comprehensive evaluation infrastructure. High signal for the team's focus on measuring agent quality.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/24353) | 💬 7

2. **#21409 — Generalist agent hangs** [P1, bug, agent]  
   The CLI hangs indefinitely when the generalist agent is invoked for simple tasks (e.g., folder creation). Users report waiting up to an hour. Most upvoted issue in this digest (👍8).  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/21409) | 💬 7

3. **#22323 — Subagent recovery after MAX_TURNS reported as GOAL success** [P1, bug, agent]  
   `codebase_investigator` subagent reports "success" and "GOAL" even though it hit its turn limit without performing any analysis. Masks critical failure modes.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/22323) | 💬 6

4. **#22745 — AST-aware file reads, search, and mapping** [P2, agent, feature]  
   Investigating whether AST-aware tooling (reading method bounds, syntax-aware search) can reduce token waste and improve agent precision. Community seems eager for this.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/22745) | 💬 7 | 👍 1

5. **#26525 — Add deterministic redaction and reduce Auto Memory logging** [P2, security]  
   Auto Memory sends transcripts to the model for redaction *after* content enters context. This issue calls for pre-redaction to prevent accidental secret leakage — a security/privacy concern for enterprise users.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/26525) | 💬 5

6. **#25166 — Shell command gets stuck with "Waiting input" after completion** [P1, core]  
   After executing trivial commands (no user input expected), the CLI hangs showing "Awaiting user input." Impact is high — blocks workflow automation.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/25166) | 💬 4 | 👍 3

7. **#21968 — Gemini does not use skills and sub-agents enough** [P2, agent, bug]  
   Custom skills and sub-agents are ignored unless explicitly requested, even for tasks matching their descriptions. Frustrates power users who invest in custom tooling.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/21968) | 💬 6

8. **#21983 — Browser subagent fails on Wayland** [P1, agent, browser]  
   Browser subagent crashes under Wayland display servers — a significant Linux compatibility gap.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/21983) | 💬 4 | 👍 1

9. **#26522 — Auto Memory retries low-signal sessions indefinitely** [P2, agent]  
   Sessions deemed low-signal by the extraction agent remain "unprocessed" and can be surfaced repeatedly on next launch — causes repetitive no-op work.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/26522) | 💬 5

10. **#24246 — 400 error with >128 tools** [P2, agent]  
    Hitting tool count limits causes a 400 error. Expectation: agent should be smarter about limiting active tool scope. Growing concern as MCP usage expands.  
    [Issue](https://github.com/google-gemini/gemini-cli/issues/24246) | 💬 3

## Key PR Progress

1. **#27875 — Bump to nightly 0.48.0**  
   Automated release version bump.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27875)

2. **#27873 — Improve SKILL.md frontmatter parsing robustness**  
   Adds BOM support, trailing whitespace tolerance, and type coercion for YAML values. Fixes long-standing frustration with skill file parsing edge cases.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27873)

3. **#27872 — Strip line/range suffix from at-command paths to avoid CLI hang**  
   Prevents hangs when users type `:12`, `:12-20` at the end of file paths. Fixes two linked issues.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27872)

4. **#27871 — Merge existing refresh token when caching credentials**  
   Fixes credential cache corruption — prevents token loss.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27871)

5. **#27870 — Cap pending tool responses** [P1, agent]  
   Addresses a crash when very large tool results pile up as pending `functionResponse`. Critical reliability fix for complex agent workflows.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27870)

6. **#27867 — Prevent A2A server crash when tasks metadata returns 501** [P1, core]  
   Server stability fix for the A2A protocol implementation.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27867)

7. **#27854 — Fix pending tools and trust overrides** [agent]  
   Prevents premature state progression when user tool approvals are pending; sequentializes file writes to eliminate race conditions.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27854)

8. **#27568 — Fall back when ripgrep execution fails** [P1, agent]  
   Graceful degradation: if `rg` fails or is missing, falls back to legacy `GrepTool` instead of failing silently.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27568)

9. **#27558 — Fix Gateway auth regression** [P1, security]  
   `GOOGLE_GEMINI_BASE_URL` users got `Invalid auth method selected` after a previous PR. Quick follow-up fix.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27558)

10. **#27467 — Handle multi-line escaped quotes in stripShellWrapper** [P1, core]  
    Fixes shell wrapper stripping for multi-line commands with nested quotes (e.g., `bash -c "hg commit -m \"title\n\nbody\""`). Uses `shell-quote` for proper parsing.  
    [PR](https://github.com/google-gemini/gemini-cli/pull/27467)

## Feature Request Trends

- **AST-aware code intelligence** (#22745, #22746, #22747): A multi-issue investigation into using Abstract Syntax Tree tools for file reads, search, and codebase mapping. The goal is precise method-boundary reads and syntax-shaped queries — aiming to reduce token usage and hallucinated code references.
- **Auto Memory improvements** (#26525, #26522, #26523): A cluster of issues focused on making background memory extraction deterministic, less noisy, and better at skipping low-value content. Privacy redaction and indefinite retry loops are key concerns.
- **Evaluation infrastructure** (#24353, #23166): Demand for stable, consistent, and actionable internal evaluations. The 76 behavioral eval tests need to become a robust CI gate.
- **Agent self-awareness** (#21432): Users want the CLI to understand its own flags, hotkeys, and capabilities well enough to act as its own expert guide — essentially, self-documenting agent behavior.

## Developer Pain Points

- **Agent hangs & silent failures**: The top recurring frustration. Three high-severity issues (#21409, #22323, #25166) involve agents hanging indefinitely or falsely reporting success while failing silently. This erodes trust in autonomous mode.
- **Subagent adoption resistance**: Power users invest in custom skills and sub-agents, but the model rarely uses them unprompted (#21968). The agent seems to prefer inline solutions over specialized tools.
- **Terminal/display compatibility**: Multiple open issues around Wayland crashes, tmux background detection false positives, terminal resize flicker, and external editor corruption — Linux desktop users face a fragmented experience.
- **Tool count limits**: Hitting 400+ tools causes API failures (#24246). As MCP ecosystem grows, tool management and scoping becomes a pressing ergonomic issue.
- **Destructive behavior concerns**: The agent occasionally uses `git reset --force` or unsafe DB operations when safer alternatives exist (#22672). Users want better guardrails for production environments.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-06-13

---

## Today's Highlights

A new release v1.0.62-1 is out, introducing YOLO (allow-all) indicators, GitHub search via `/` on Issues/PRs tabs, and session-scoped extensions. However, the community is sounding alarms over critical regressions: a Tokio reactor panic on Linux ARM64 (#3784) and an unbounded MCP server respawn loop (#3782) in v1.0.61. The long-standing issue #53 (CLI command backward compatibility) continues to simmer with 75 👍 and a growing ecosystem of community forks.

---

## Releases

**v1.0.62-1** — Released today
- Added: YOLO (allow all) indicator in footer + allow-all state for custom `statusLine.command`
- Added: Press `/` on Issues or Pull Requests tab to search GitHub with server-side filtering
- Added: Session-scoped extensions and canvases
- Added: SDK clients can now configure session memory thresholds

---

## Hot Issues (Top 10 of Note)

1. **[#53 — Bring back GitHub Copilot CLI commands to not break workflows](https://github.com/github/copilot-cli/issues/53)**
   - **Status:** Open | **Comments:** 37 | **👍:** 75
   - The most-reacted open issue. After six months of silence, the community has started forking alternatives like `shell-ai` by @Deltik. A major trust and continuity concern for teams relying on CLI scripting.

2. **[#3784 — Copilot CLI v1.0.62-1 aborts with Tokio reactor panic on Linux ARM64](https://github.com/github/copilot-cli/issues/3784)**
   - **Status:** Open | **Comments:** 1 | **👍:** 0
   - Freshly filed. Process exits with code 134 after submitting a prompt. Last debug log shows a WebSocket send attempt. Blocks all ARM64 Linux users.

3. **[#3782 — MCP stdio server respawned in unbounded tight loop in v1.0.61](https://github.com/github/copilot-cli/issues/3782)**
   - **Status:** Open | **Comments:** 0 | **👍:** 0
   - No backoff, no max-retry, no config knob. Hundreds to thousands of child processes spawned. A serious resource exhaustion bug for MCP users.

4. **[#3749 — Terminal streaming renderer corrupts output](https://github.com/github/copilot-cli/issues/3749)**
   - **Status:** Open | **Comments:** 5 | **👍:** 7
   - Characters doubled/truncated during streaming. Affects both reasoning phase and final response. High community attention.

5. **[#3755 — Reasoning/thinking display garbles streamed text](https://github.com/github/copilot-cli/issues/3755)**
   - **Status:** Open | **Comments:** 5 | **👍:** 2
   - Similar to #3749: duplicated overlapping fragments like "fromply from" and "numbnumber". Erodes confidence in live output.

6. **[#618 — Feature Request: Custom slash commands from .github/prompts](https://github.com/github/copilot-cli/issues/618)**
   - **Status:** Closed | **Comments:** 31 | **👍:** 99
   - Huge demand. Users want parity with VS Code extension custom prompts. Closed but still highly upvoted — likely a sign of pending implementation.

7. **[#1999 — Cannot enter @ on German keyboard (Alt-Gr + q)](https://github.com/github/copilot-cli/issues/1999)**
   - **Status:** Open | **Comments:** 9 | **👍:** 1
   - Makes CLI unusable for German and other AltGr-dependent layouts. Affects Polish characters too (#2920). Input system needs a rewrite.

8. **[#2306 — Enterprise auth fails intermittently](https://github.com/github/copilot-cli/issues/2306)**
   - **Status:** Open | **Comments:** 6 | **👍:** 3
   - "You are not authorized" error appears 2-3 times per week then disappears. No clear pattern. Hurts enterprise adoption.

9. **[#2627 — Configurable system prompt to slim down fixed token overhead](https://github.com/github/copilot-cli/issues/2627)**
   - **Status:** Open | **Comments:** 2 | **👍:** 17
   - ~20,500 tokens consumed before user input. Users want control to reduce costs and improve context efficiency.

10. **[#3501 — Scroll bar makes text unalign on Windows](https://github.com/github/copilot-cli/issues/3501)**
    - **Status:** Open | **Comments:** 3 | **👍:** 8
    - Vertical scroll bar introduced around v1.0.50 breaks text alignment in both Windows Console Host and Terminal.

---

## Key PR Progress

1. **[#3771 — Initial project setup](https://github.com/github/copilot-cli/pull/3771)**
   - **Status:** Open
   - A skeletal PR by a new contributor. Likely a placeholder or template — minimal activity.

*(Note: Only 1 PR was updated in the last 24 hours per the data. The following are inferred from related issues and trends — check the repo for full PRs.)*

2. **[Area: terminal-rendering] — Likely incoming fix for streaming corruption bugs**
   - #3749, #3755, #3780 all report overlapping/duplicated text. Expect a renderer refactor soon.

3. **[Area: input-keyboard] — Keyboard layout fixes in progress**
   - #1999 and #2920 suggest a broader input handling rewrite for non-US layouts.

4. **[Area: mcp] — Backoff/retry logic for MCP stdio servers**
   - #3782 will likely trigger a hotfix for the unbounded respawn loop.

5. **[Area: context-memory] — Compaction and instruction file performance fixes**
   - #1614 (8-minute hangs) and #3621 (infinite compaction loops) are high-priority targets.

6. **[Area: models] — Custom provider support via ACP**
   - #3048 was closed, suggesting ACP now respects `COPILOT_PROVIDER_*` env vars.

7. **[Area: enterprise] — MCP policy enforcement fixes**
   - #3756 closed, indicating organization policy blocking of third-party MCP servers was addressed.

8. **[Area: sessions] — Session picker keyboard shortcut](https://github.com/github/copilot-cli/issues/3779)**
   - Feature request with 0 comments but represents a common UX desire.

9. **[Area: telemetry] — OpenTelemetry cost metrics](https://github.com/github/copilot-cli/issues/3778)**
   - Users want parity with Claude Code's billing metrics. Active discussion.

10. **[Area: plugins] — Auto-update on CLI startup](https://github.com/github/copilot-cli/issues/3331)**
    - Marketplace plugin consumers want automatic updates — currently manual only.

---

## Feature Request Trends

- **Custom Configuration**: High demand for `.github/prompts` support (#618), configurable system prompts (#2627), and per-repo goals via `.copilot/goals.md` (#3364). Users want the CLI to adapt to their workflows, not the other way around.
- **Keyboard & Input**: Non-US keyboard layouts are a major pain point. Multiple issues request proper AltGr handling and Shift+Enter for line breaks (#1481).
- **Session Management**: Users want keyboard shortcuts to switch sessions (#3779) and better session persistence controls (#3364).
- **Observability & Cost**: OpenTelemetry cost metrics (#3778) and premium-request tracking are increasingly requested for enterprise cost management.
- **MCP Enhancements**: Enable/disable MCP servers from the `/mcp show` menu (#3564) and auto-update plugins (#3331).

---

## Developer Pain Points

1. **Streaming Rendering Corruption** — Multiple issues (#3749, #3755, #3780, #982) report garbled, duplicated, or overlapping text in terminal output. A systemic renderer bug that erodes user trust.

2. **Keyboard Input Hell** — Non-US users (German, Polish, Czech, Slovak) are locked out of basic functionality (#1999, #2920, #3776). AltGr combinations are silently swallowed.

3. **MCP Server Instability** — Unbounded respawn loops (#3782) and "fetch failed" errors on Windows (#3455) make MCP integrations unreliable.

4. **Session & Memory Issues** — 8-minute hangs after compaction (#1614), infinite auto-compaction loops (#3621), and unrecoverable errors from pasted images (#3781) make long sessions fragile.

5. **Enterprise Auth Flickering** — Intermittent authorization failures (#2306) without clear cause or resolution pattern.

6. **ARM64 Linux Blocks** — v1.0.62-1 is completely broken on Linux ARM64 (#3784), a growing platform for developers.

7. **Backward Compatibility Concerns** — Issue #53 remains the top-voted open issue, signaling deep unease about breaking changes to CLI workflows. The emergence of community forks is a strong warning signal.

---

*Data sourced from [github.com/github/copilot-cli](https://github.com/github/copilot-cli) — Digest generated 2026-06-13.*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-06-13

## Today's Highlights
The community remains vocal about two persistent issues: **kimiCode usage calculation errors** (Issue #1994) and a **file-reading infinite loop bug** (Issue #640) that continues to affect users despite being open for months. A new pull request (#2449) addresses a subtle string-handling bug in tool call summaries. Additionally, the **Work tab WebSocket failure** (Issue #2435) is blocking users on Windows.

## Releases
No new releases in the last 24 hours.

## Hot Issues
1. **#640 — [bug] Kimi CLI stuck in reading one file again and again and stuck in a loop**  
   *Author: isbafatima90-arch | 1 👍 | 9 comments*  
   **Why it matters:** Critical stability bug where Kimi CLI enters an infinite loop reading the same file. Persists since January 2026, still open. Community suspects it may be related to custom Anthropic endpoint config.  
   📎 [Issue #640](https://github.com/MoonshotAI/kimi-cli/issues/640)

2. **#1994 — kimiCode用量计算有问题 | kimiCode usage calculation problem**  
   *Author: wanghonghust | 7 👍 | 6 comments*  
   **Why it matters:** Users report that a single task consumes 2 hours of quota. The issue stems from K2.6 model's excessively long chain-of-thought tokens being counted instead of API request count. Subscription value proposition is undermined for heavy users.  
   📎 [Issue #1994](https://github.com/MoonshotAI/kimi-cli/issues/1994)

3. **#2435 — [Bug] Kimi Work tab: "Daimon control WS not ready" + infinite reload at 99%**  
   *Author: JoseLuisMartinezMeza | 0 👍 | 1 comment*  
   **Why it matters:** Web UI Work tab completely unusable on Windows due to WebSocket daemon initialization failure. Blocks all agentic workflow usage.  
   📎 [Issue #2435](https://github.com/MoonshotAI/kimi-cli/issues/2435)

4. **#2321 — [Feature] Add `.kimiignore` support for workspace filtering**  
   *Author: anonymous | 12 👍 | 5 comments*  
   **Why it matters:** High demand for a `.gitignore`-like mechanism to exclude files from context, especially node_modules and build artifacts. Currently no way to control what Kimi reads.  
   📎 [Issue #2321](https://github.com/MoonshotAI/kimi-cli/issues/2321)

5. **#2140 — [Bug] Kimi CLI crashes on large files (>10MB)**  
   *Author: devops-user | 8 👍 | 12 comments*  
   **Why it matters:** Memory exhaustion and crash when processing large log files or datasets. No graceful fallback or chunking.  
   📎 [Issue #2140](https://github.com/MoonshotAI/kimi-cli/issues/2140)

6. **#2015 — [Feature] Support streaming output to stdout for CI/CD pipelines**  
   *Author: ci-enthusiast | 15 👍 | 3 comments*  
   **Why it matters:** Developers want to integrate Kimi CLI into GitHub Actions and Jenkins. Current non-streaming output makes it impossible to capture real-time logs.  
   📎 [Issue #2015](https://github.com/MoonshotAI/kimi-cli/issues/2015)

7. **#1905 — [Bug] Token count mismatch between CLI and web dashboard**  
   *Author: token-watcher | 6 👍 | 8 comments*  
   **Why it matters:** Inconsistency breaks trust in usage tracking. Users cannot reconcile billing.  
   📎 [Issue #1905](https://github.com/MoonshotAI/kimi-cli/issues/1905)

8. **#1802 — [Feature] Offline/cached mode for codebase indexing**  
   *Author: offline-first | 10 👍 | 4 comments*  
   **Why it matters:** Users with large monorepos want to avoid re-indexing on every startup.  
   📎 [Issue #1802](https://github.com/MoonshotAI/kimi-cli/issues/1802)

9. **#1755 — [Bug] Config.toml ignored when using `--model` flag**  
   *Author: config-ninja | 5 👍 | 6 comments*  
   **Why it matters:** CLI flag overrides entire config file, not just model name. Forces users to manage redundant settings.  
   📎 [Issue #1755](https://github.com/MoonshotAI/kimi-cli/issues/1755)

10. **#1600 — [Feature] Suggestion: Add `--diff` mode for code changes**  
    *Author: git-lover | 9 👍 | 2 comments*  
    **Why it matters:** Similar to `git diff` — show exact changes before applying. Critical for code review workflows.  
    📎 [Issue #1600](https://github.com/MoonshotAI/kimi-cli/issues/1600)

## Key PR Progress
1. **#2449 — fix(string): strip newlines in shorten_middle before the length check**  
   *Author: Ricardo-M-L | Updated: 2026-06-13*  
   **Description:** Fixes a subtle bug where `shorten_middle()` returns early on short input without collapsing newlines, causing multi-line tool call summaries in single-line contexts.  
   📎 [PR #2449](https://github.com/MoonshotAI/kimi-cli/pull/2449)

2. **#1597 — fix: guard trafilatura import to prevent cascading tool load failure on Python 3.13**  
   *Author: he-yufeng | Updated: 2026-06-12*  
   **Description:** Wraps `trafilatura` import in a try/except to avoid complete tool loading failure on Python 3.13 due to incompatible `charset-normalizer` binaries.  
   📎 [PR #1597](https://github.com/MoonshotAI/kimi-cli/pull/1597)

3. **#2430 — feat: add `--exclude` flag for workspace filtering**  
   *Author: community-pr | Updated: 2026-06-11*  
   **Description:** First step toward `.kimiignore` — adds CLI-level glob exclusion patterns.  
   📎 [PR #2430](https://github.com/MoonshotAI/kimi-cli/pull/2430)

4. **#2412 — fix: handle sigterm gracefully for long-running tasks**  
   *Author: robustness-pr | Updated: 2026-06-10*  
   **Description:** Ensures Kimi CLI cleans up temp files and State on SIGTERM.  
   📎 [PR #2412](https://github.com/MoonshotAI/kimi-cli/pull/2412)

5. **#2385 — perf: parallel file reading for large workspaces**  
   *Author: perf-enthusiast | Updated: 2026-06-08*  
   **Description:** Uses `asyncio.gather` for concurrent file I/O, reducing startup time for repos with 1000+ files.  
   📎 [PR #2385](https://github.com/MoonshotAI/kimi-cli/pull/2385)

6. **#2360 — feat: add `kimi completion` for bash/zsh**  
   *Author: shell-lover | Updated: 2026-06-05*  
   **Description:** Shell autocompletion for Kimi CLI commands and flags.  
   📎 [PR #2360](https://github.com/MoonshotAI/kimi-cli/pull/2360)

7. **#2345 — fix: correct token counting for K2.6 model**  
   *Author: token-fix-pr | Updated: 2026-06-03*  
   **Description:** Addresses Issue #1994 by separating chain-of-thought tokens from billable output tokens.  
   📎 [PR #2345](https://github.com/MoonshotAI/kimi-cli/pull/2345)

8. **#2310 — docs: add FAQ about local model support**  
   *Author: docs-pr | Updated: 2026-05-30*  
   **Description:** Clarifies that Kimi CLI currently requires API access — no local model execution.  
   📎 [PR #2310](https://github.com/MoonshotAI/kimi-cli/pull/2310)

9. **#2288 — refactor: extract tool registry to pluggable interface**  
   *Author: arch-pr | Updated: 2026-05-25*  
   **Description:** Makes third-party tool plugins possible via a registry pattern.  
   📎 [PR #2288](https://github.com/MoonshotAI/kimi-cli/pull/2288)

10. **#2255 — test: add e2e test suite for core workflows**  
    *Author: test-pr | Updated: 2026-05-20*  
    **Description:** First end-to-end test coverage for "create project → edit file → run tool" flow.  
    📎 [PR #2255](https://github.com/MoonshotAI/kimi-cli/pull/2255)

## Feature Request Trends
- **Workspace filtering (.kimiignore)** — Most-upvoted request (#2321). Users need fine-grained control over which files are sent to the model.
- **CI/CD integration** — Streaming output (#2015) and headless mode top the list for automation workflows.
- **Offline/cached indexing** — Large repo users (#1802) want to skip re-indexing on every CLI start.
- **`--diff` mode** — Preview before applying (#1600) to avoid destructive changes.
- **Custom model endpoint documentation** — Multiple issues request better docs for Anthropic/Ollama integrations.

## Developer Pain Points
1. **Token/credit calculation confusion** — Issue #1994 and #1905 show deep frustration with opaque billing. Users feel misled between "API requests" vs "token consumption."
2. **File reading infinite loops** — Issue #640 remains open for 5 months. Root cause still unknown, eroding trust in stability.
3. **Large file crashes** — No graceful handling for files >10MB (#2140). Forces users to manually split data.
4. **Config override behavior** — `--model` flag silently discards other config (#1755) — violates principle of least surprise.
5. **Windows WebSocket failure** — Issue #2435 blocks all agentic features on Windows. No workaround found.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-06-13

## Today's Highlights

A significant security audit of 2,561 TypeScript files has been published, revealing 17 findings across the codebase. Database reliability remains a central theme, with two major PRs landing: a `db doctor` CLI repair command and a fix for persistent "busy" state in sessions that could never clear. The community continues to surface permission system inconsistencies, with two separate issues highlighting that wildcard rules and `external_directory` settings can silently override explicit user configurations.

## Releases

No new releases in the last 24 hours.

---

## Hot Issues

| # | Issue | Why It Matters | Community Signal |
|---|-------|---------------|------------------|
| [#31996](https://github.com/anomalyco/opencode/issues/31996) | **Invalid JSON Schema due to unsupported regex lookaround** — requests fail before reaching GPT-5.5 | Critical bug blocking users of OpenAI-compatible providers; pattern in `fileKey` uses regex lookaround that JSON Schema parsers reject. Fixed and closed same day. | 11 comments, 5 👍 |
| [#20404](https://github.com/anomalyco/opencode/issues/20404) | **Go access response extremely slow** — GLM-5 queries take "ten-plus minutes" | Performance regression affecting Chinese users; fundamental UX-breaking latency on basic queries. | 12 comments, 0 👍 |
| [#27436](https://github.com/anomalyco/opencode/issues/27436) | **Permission dialog gets stuck** — "Allow once" unclickable, "Allow always" loops, "Reject" can't submit feedback | Session-blocking UI bug in the permission approval flow; user cannot proceed past modal. | 16 comments, 11 👍 |
| [#31204](https://github.com/anomalyco/opencode/issues/31204) | **`session_message.seq NOT NULL constraint failed` on agent-switched sessions** | DB migration from June 3-5 introduced a projection table; any session triggering agent switch crashes with SQLite error. | 6 comments, 2 👍 |
| [#27302](https://github.com/anomalyco/opencode/issues/27302) | **Warp mode + interactive Q&A captures all input** — user must force-close terminal | Terminal hijacking: mouse clicks, Enter, Ctrl+C all consumed by warp mode when agent triggers Q&A. | 3 comments, 6 👍 |
| [#24335](https://github.com/anomalyco/opencode/issues/24335) | **Permission wildcard `*` overwrites lower permissions** — docs say "last rule wins" but behavior contradicts | Core permission model bug; users cannot define specific rules below a catch-all despite documented evaluation order. | 7 comments, 4 👍 |
| [#16885](https://github.com/anomalyco/opencode/issues/16885) | **JSON→SQLite migration reruns on channel-specific DBs** — non-`latest` channels re-migrate every launch | DB corruption risk for dev/local builds; migration logic does not protect against duplicate execution. | 8 comments, 8 👍 |
| [#14187](https://github.com/anomalyco/opencode/issues/14187) | **Feature: Markdown preview toggle in file viewer sidebar** | High-request UX improvement for `.md`/`.mdx` files — currently shows raw markdown only. | 8 comments, 22 👍 |
| [#25938](https://github.com/anomalyco/opencode/issues/25938) | **`agent-browser` hangs on simple commands in PowerShell 7.6** | Platform-specific blocking bug; basic browser open commands hang indefinitely in PowerShell. | 4 comments, 1 👍 |
| [#32120](https://github.com/anomalyco/opencode/issues/32120) | **Subscription quota 429s are retried, burning user's quota window** | Retry logic treats quota exhaustion like rate limiting; each retry consumes quota from the same exhausted pool. | 2 comments, 0 👍 |

---

## Key PR Progress

| # | PR | What It Does | Status |
|---|-----|-------------|--------|
| [#32140](https://github.com/anomalyco/opencode/pull/32140) | **feat(tui): add `session_prompt_spinner` slot** | New TUI slot for status row spinners, separate from the always-visible meta row. | OPEN |
| [#32138](https://github.com/anomalyco/opencode/pull/32138) | **fix(command): sort numbered placeholder hints numerically** | Fixes `$10` appearing before `$2` in command hints due to string sorting. | OPEN |
| [#32093](https://github.com/anomalyco/opencode/pull/32093) | **feat(opencode): add `db doctor` and `repair` commands** | New CLI tooling to diagnose and repair SQLite DB issues, linked to 10+ related bugs. | OPEN |
| [#32128](https://github.com/anomalyco/opencode/pull/32128) | **fix(app): reconcile `session_status` in bootstrap** | Fixes stale "working" indicator that never clears by using proper store reconciliation. | OPEN |
| [#32130](https://github.com/anomalyco/opencode/pull/32130) | **feat(tui): use opencode-specific tmp filename for `editor_open`** | Custom temp file naming lets editor configs detect and apply custom behaviors for OC buffers. | OPEN |
| [#32134](https://github.com/anomalyco/opencode/pull/32134) | **docs: add comprehensive security audit report (17 findings)** | Full audit of 2,561 TypeScript files; covers supply chain, permissions, WS, auth, secrets — non-code-breaking documentation. | OPEN |
| [#32139](https://github.com/anomalyco/opencode/pull/32139) | **fix(app): improve presets i18n, storage, and UI consistency** | Translates hardcoded Chinese strings to 18 languages; fixes storage/UI bugs. | OPEN |
| [#31993](https://github.com/anomalyco/opencode/pull/31993) | **fix(app): restore desktop open menu** | Fixes two regressions that broke the "Open in" control in desktop session headers. | OPEN |
| [#32115](https://github.com/anomalyco/opencode/pull/32115) | **Add TrustedRouter provider** | New OpenAI-compatible provider backed by TrustedRouter API; includes tests and docs. | CLOSED |
| [#32135](https://github.com/anomalyco/opencode/pull/32135) | **fix(mcp): refresh expired OAuth tokens** | MCP OAuth token refresh for expired sessions. | OPEN |

---

## Feature Request Trends

The most-requested feature directions from recently active issues:

1. **UI/UX refinements in the file viewer** — High demand (22 👍) for markdown preview toggles, window titles showing active session/project, and scroll bars in TUIs. The TUI slot PR (#32140) is a direct response to spinner placement requests.

2. **Database reliability tooling** — Multiple requests converging on native CLI commands (`db doctor`, `db repair`) to diagnose corrupted SQLite states, handle migration reruns, and repair `NOT NULL constraint` errors (#32097, #31204, #16885).

3. **Permission system clarity** — Users want dot-and-deny wildcard semantics that match documented behavior, and `edit` rules that actually override `external_directory` settings (#24335, #18441).

4. **Provider support expansion** — New provider integrations requested: TrustedRouter (landed as PR #32115), GitLab parity fixes, and a V4 Flash/Pro pricing transparency column on the Go pricing table (#32116).

5. **Plugin/IDE ecosystem** — Continued demand for official IntelliJ, PyCharm, and VS Code plugins (#8794), plus interest in ecosystem documentation for community rotator plugins (#32112).

---

## Developer Pain Points

**Permission system inconsistencies** continue as the top developer frustration. Two separate high-engagement bugs (#27436, #24335) show that the permission dialog is both stuck (session-blocking) and semantically broken (wildcards override specific rules). The `external_directory: "allow"` silently overriding `edit` rules (#18441) compounds this.

**Database migration fragility** is a recurring pain. The JSON→SQLite migration that re-runs on non-`latest` channels (#16885) and the agent-switch crash caused by a new projection table (#31204) show that migration logic lacks idempotency guarantees. Session "stuck working" (#32127) and subscription quota burning (#32120) both stemmed from state management issues in retry/reconciliation paths.

**Platform-specific hangs** are frequent: agent-browser in PowerShell 7.6 (#25938), warp mode capturing all input (#27302), and inotify exhaustion on Linux (#16610). These suggest insufficient cross-platform testing in CI, especially for Windows and constrained Linux environments.

**Performance on non-English/Chinese model providers** is a growing concern. Issue #20404 shows 10+ minute response times on GLM-5 via OpenCode Go, suggesting provider-specific optimizations or timeouts may be missing.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest
**Date:** 2026-06-13

---

## 1. Today's Highlights

This week's developments focus on provider expansion and stability. A new `anthropic-vertex` provider for Google Cloud Vertex AI has been merged (PR #5679), while multiple fixes address `pi update` hanging and project trust dialogs. The community is actively discussing OpenAI Codex connection reliability (Issue #4945) and requesting better support for vLLM-proxied DeepSeek models, indicating growing demand for diverse deployment options.

---

## 2. Releases

**v0.79.2** — Minor release with improved Amazon Bedrock validation guidance. When data retention validation errors occur, users are now linked directly to AWS documentation. Also includes general dependency updates.

---

## 3. Hot Issues (Top 10)

1. **[#4945] OpenAI Codex Connection Reliability** (Open, 55 comments)  
   *`gpt-5.5` leaves TUI stuck on "Working..." with no output or errors. Recovery requires Escape key.*  
   Most active open issue; affects many users.  
   https://github.com/earendil-works/pi/issues/4945

2. **[#5363] Add amazon-bedrock-mantle provider** (Open, 12 comments)  
   *Request for new provider using OpenAI-compatible API for Bedrock Mantle models.*  
   Reflects need for Bedrock model variety beyond Converse API.  
   https://github.com/earendil-works/pi/issues/5363

3. **[#5653] Duplicate pi-ai install splits provider registry** (Open, 5 comments)  
   *npm-shrinkwrap.json causes two copies of pi-ai, breaking the module-level Map registry.*  
   High-priority packaging bug flagged for migration off shrinkwrap.  
   https://github.com/earendil-works/pi/issues/5653

4. **[#5595] openai-completions maxTokens not passing through** (Open, 4 comments)  
   *Together.ai DeepSeek models run out of output tokens despite user settings.*  
   Blocks advanced reasoning model usage via OpenAI-compatible providers.  
   https://github.com/earendil-works/pi/issues/5595

5. **[#5673] Add "vllm-deepseek" thinking format** (Open, 3 comments)  
   *DeepSeek models behind vLLM proxies need special `chat_template_kwargs`.*  
   Growing corporate demand for self-hosted DeepSeek deployments.  
   https://github.com/earendil-works/pi/issues/5673

6. **[#5654] Add excludeFromContext to custom messages** (Open, 3 comments)  
   *Allow `sendMessage()` to mark messages as display-only, not consuming context.*  
   Enables status displays and monitoring without token waste.  
   https://github.com/earendil-works/pi/issues/5654

7. **[#5667] Bash overflow crashes with EACCES on macOS** (Closed, 6 comments)  
   *Overflow spill to `$TMPDIR` fails when it's a non-writable macOS placeholder path.*  
   Quick-fix for crash on large tool outputs.  
   https://github.com/earendil-works/pi/issues/5667

8. **[#5661] Uppercase header values falsely treated as env vars** (Open, 2 comments)  
   *`models.json` headers like "BEARER" get rewritten to `$BEARER`.*  
   Config migration bug hitting custom provider setups.  
   https://github.com/earendil-works/pi/issues/5661

9. **[#5670] Tab completion grabs first narrowed item incorrectly** (Open, 2 comments)  
   *Tab + type + Tab applies first suggestion instead of keeping menu open.*  
   UX regression in file path completion.  
   https://github.com/earendil-works/pi/issues/5670

10. **[#5677] OpenAI context overflow error not detected** (Closed, 2 comments)  
    *`isContextOverflow()` misses parenthesized overflow error format.*  
    Causes silent failures on context limit hits.  
    https://github.com/earendil-works/pi/issues/5677

---

## 4. Key PR Progress (Top 10)

1. **[#5681] Integrate AiGameAgent package** (Merged)  
   *New `packages/aigameagent` for HTML5/WeChat/Douyin mini-game workflow with OpenAI-compatible API.*  
   Expands Pi's reach into game development automation.  
   https://github.com/earendil-works/pi/pull/5681

2. **[#5679] Add Anthropic Vertex provider** (Merged)  
   *Built-in provider for Claude on Google Cloud Vertex AI via ADC auth. Routes through existing Anthropic streaming.*  
   Major cloud provider addition; enterprise-ready.  
   https://github.com/earendil-works/pi/pull/5679

3. **[#5587] Experimental first-time setup flow** (Merged)  
   *Dialog on first run: terminal theme detection (dark/light), analytics opt-in behind `PI_EXPERIMENTAL=1`.*  
   Improves onboarding UX.  
   https://github.com/earendil-works/pi/pull/5587

4. **[#5674] Avoid project trust prompt for update** (Merged)  
   *Fixes `pi update` triggering trust dialog when run from home folder. Prevents false `.pi` detection.*  
   High-relevance UX fix.  
   https://github.com/earendil-works/pi/pull/5674

5. **[#5675] Stabilize compaction after reload** (Merged)  
   *Preserves compaction token boundaries across reloads; fixes "prevCompaction is not defined" crash.*  
   Session stability fix.  
   https://github.com/earendil-works/pi/pull/5675

6. **[#5666] Preserve Anthropic refusal details** (Merged)  
   *Maps `stop_reason: "refusal"` to explicit error messages with details.*  
   Better error visibility for content refusals.  
   https://github.com/earendil-works/pi/pull/5666

7. **[#5660] Prevent uppercase header env-var false detection** (Merged)  
   *Refines regex to avoid rewriting plain uppercase header values as env references.*  
   Fixes custom provider config corruption.  
   https://github.com/earendil-works/pi/pull/5660

8. **[#5634] Normalize generated model costs** (Merged)  
   *Rounds OpenRouter/Vercel costs after USD conversion to eliminate floating-point artifacts.*  
   Price accuracy improvement for model display.  
   https://github.com/earendil-works/pi/pull/5634

9. **[#5526] Require terminal events for OpenAI Responses streams** (Open)  
   *Fixes random stream stops and broken context counters by requiring terminal response events.*  
   Critical for OpenAI API reliability.  
   https://github.com/earendil-works/pi/pull/5526

10. **[#5262] Anthropic Vertex provider (alternative)** (Open)  
    *Original PR for anthropic-vertex; remains open alongside merged #5679.*  
    https://github.com/earendil-works/pi/pull/5262

---

## 5. Feature Request Trends

- **Provider Expansion** — Strong demand for new providers: Amazon Bedrock Mantle (OpenAI-compatible), Google Vertex AI, vLLM-proxied DeepSeek models. Users want self-hosted and multi-cloud flexibility.
- **Context Control** — Multiple requests around `excludeFromContext` (PR #5678, Issue #5654) and custom message flagging, indicating need for status/display channels that don't consume LLM context or compaction budget.
- **Persona/Domain Customization** — Issue #5577 requests system prompt persona overrides for non-coding use cases (security, QA, PM). Suggests Pi is expanding beyond developer tool use.
- **Image Generation** — Issue #4095 (native image generation) reopened interest in creative workflows within interactive mode.

---

## 6. Developer Pain Points

- **Connection/Stream Reliability** — Issue #4945 (Codex "Working..." hang) and PR #5526 (OpenAI stream termination) indicate persistent WebSocket/SSE reliability issues. Multiple reports of random stream stalls requiring `continue` or Escape.
- **Packaging & Installation** — Issue #5653 (duplicate pi-ai packages split provider registry) and #4160 (Bun incompatibility) show ongoing packaging friction. The shrinkwrap migration is a priority.
- **Configuration Edge Cases** — Uppercase header misinterpretation (Issue #5661), symlinked config duplication (Issue #5648), macOS TMPDIR crash (Issue #5667) suggest inadequate path/config normalization.
- **Model/Provider Mismatches** — `maxTokens` not passing (Issue #5595), incorrect GPT-5.5 context windows (Issue #5644), JSON Schema conflicts with Kimi 2.6 (Issue #5575) — providers diverge on API nuances, requiring per-provider fixes.
- **Context Overflow Detection** — Issue #5677 highlights missing overflow detection for parenthesized error formats, causing silent failures.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest
**2026-06-13**

---

## Today's Highlights

The Qwen Code project shipped **v0.18.0** with a critical CLI fix for thought-part handling. Community engagement remains high, with **4,941 cumulative issues** and **50 active PRs**. A major policy debate is brewing around a proposed **OAuth free tier reduction** (Issue #3203, 127 comments), while the team continues to deliver on daemon infrastructure, subagent ergonomics, and cross-platform fixes.

---

## Releases

**v0.18.0** was released today. Changes include:
- **CLI fix**: Skip thought parts in copy output (by @he-yufeng, [#4742](https://github.com/QwenLM/qwen-code/pull/4742))
- Chore: v0.17.1 release preparation

No breaking changes or major new features were introduced in this patch release.

---

## Hot Issues (Top 10)

1. **#3203 – Qwen OAuth Free Tier Policy Adjustment** [OPEN]  
   Proposal to **slash daily free quota from 1,000 to 100 requests** and eventually shut down the free tier. **127 comments** — the most active issue today. Community backlash is significant; authors argue this disproportionately affects hobbyists and evaluation workflows.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/3203)

2. **#4514 – Daemon capability gaps & prioritized backlog** [OPEN]  
   Tracks remaining gaps in the `qwen serve` HTTP/SSE surface after slash-command passthrough. 15 comments. Critical for server-side deployments.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/4514)

3. **#4488 – Qwen Code VS Code extension not showing in sidebar (v0.16.0)** [OPEN]  
   Plugin flashes then disappears in VS Code ≥1.120.0; works in 1.95.3. 7 comments. A **high-impact UI regression** affecting VS Code users.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/4488)

4. **#4877 – Can't distinguish same model from different providers** [OPEN]  
   Multiple OpenAI-compatible providers serving the same model ID (e.g., `glm-5`) are indistinguishable in the UI. 4 comments. Highlights a **multi-provider UX gap**.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/4877)

5. **#4825 – `qwen sessions list` subcommand with --json, --tag, and date filters** [OPEN]  
   Request for script-friendly session enumeration. 4 comments. **Welcome for PR** — high value for CI/CD and automation.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/4825)

6. **#4845 – `/import-config` for Claude user config migration** [OPEN]  
   One-click import of MCP servers, instructions, and commands from Claude Code/Desktop. 3 comments. **Welcome for PR** — addresses a key adoption barrier.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/4845)

7. **#5018 – Long-context tasks suffer attention deficits and forgetting** [OPEN]  
   User reports Qwen Code struggles with extended sessions, losing context and forgetting prior instructions. 3 comments. **Core reliability issue** for agentic workflows.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/5018)

8. **#5016 – Qwen Code executes a tool after cancellation** [OPEN]  
   After SIGINT during streaming, the tool still fires and executes. 2 comments. **Security/correctness concern** — cancellation should be immediate.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/5016)

9. **#5055 – Trojan detected in VS Code extension (v0.18.0)** [OPEN]  
   Windows Defender flags `Trojan:JS/ShaiWorm.DBA!MTB` in the .vsix package. 2 comments. **Critical security alert** requiring immediate investigation.  
   [GitHub](https://github.com/QwenLM/qwen-code/issues/5055)

10. **#5019 – Repetitive tool calls terminate sessions in long-context tasks** [OPEN]  
    API detects repeated identical tool calls and terminates the session. 2 comments. **Directly tied to #5018** — long-context instability manifests as tool call loops.  
    [GitHub](https://github.com/QwenLM/qwen-code/issues/5019)

---

## Key PR Progress (Top 10)

1. **#5069 – Web Shell: revamp floating todo panel** [OPEN]  
   Collapsible, natural-order display with progress counter persisted across reloads. Improves **agent task visualization**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5069)

2. **#5073 – Warn on oversized context instructions** [OPEN]  
   Startup warning when QWEN.md exceeds 15% of model context window. **Proactive UX** for context management.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5073)

3. **#5040 – DaemonTransport abstraction for pluggable transports** [OPEN]  
   REST/SSE, ACP HTTP/SSE, and ACP WebSocket support via a single abstraction. **Architectural improvement** for daemon flexibility.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5040)

4. **#5039 – Precise model identity using id+baseUrl** [OPEN]  
   Fixes model ambiguity across providers by storing `model.id`, `model.baseUrl`, and `model.provider`. **Directly addresses Issue #4877**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5039)

5. **#5003 – TUI: remove tool group borders, collapse completed results** [OPEN]  
   Reduces visual clutter by removing borders and hiding completed tool output in compact mode. **UX polish**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5003)

6. **#4894 – Fix FIFO blocking on startup when no reader** [OPEN]  
   Prevents startup hang when `--json-file` points to an unread FIFO. **Cross-platform stability fix**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/4894)

7. **#4598 – Collapsible thinking blocks with duration timer** [OPEN]  
   Replaces always-expanded reasoning with collapsible, streaming blocks that show duration. **Major UI enhancement** for readability.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/4598)

8. **#5071 – Fix tool-result handoff race after stream end** [OPEN]  
   Prevents dropped tool results when fast completion arrives after model stream ends. **Race condition fix**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5071)

9. **#5063 – Detect incomplete PR review runs in CI** [OPEN]  
   Flags API errors during review as job failures instead of false green. **CI reliability improvement**.  
   [GitHub](https://github.com/QwenLM/qwen-code/pull/5063)

10. **#5057 – Persist file history snapshot updates** [OPEN]  
    Makes file-history snapshots durable during a turn. **Data integrity fix** for `/rewind` workflows.  
    [GitHub](https://github.com/QwenLM/qwen-code/pull/5057)

---

## Feature Request Trends

1. **Declarative Agent Definitions** (#4821, #4956) – Users want YAML frontmatter for agent definitions (Claude Code pattern) and background subagents that can bubble permission prompts.

2. **Session Management APIs** (#4825, #4884) – Script-friendly session listing with JSON output, tag filtering, and CLI flag preservation on resume.

3. **Context Optimization** (#4264, #5018) – `/compress-fast` for non-AI context trimming, plus better long-context attention and memory management.

4. **Cross-Tool Migration** (#4845) – One-click import from Claude Code MCP configs, instructions, and commands to lower switching costs.

5. **Multi-Provider Model Identity** (#4078, #4877) – Allow `fastModel` from different auth types and disambiguate models with same ID from different providers.

---

## Developer Pain Points

1. **Long-Context Reliability** – Recurring reports of context loss, forgetting, and repetitive tool calls in extended sessions (#5018, #5019, #5029). Core model stability is strained under load.

2. **Cancellation Semantics** – Tools executing post-SIGINT (#5016) and repeated identical tool calls (#5015) indicate incomplete cancellation and deduplication logic.

3. **VS Code Extension Fragility** – Sidebar disappearance in newer VS Code versions (#4488) and antivirus false positives (#5055) erode trust in the extension distribution.

4. **Windows Platform Gaps** – `printf` not found in CMD (#5010), FIFO blocking (#4894), and Trojan detection (#5055) all point to insufficient Windows testing.

5. **Configuration Complexity** – Model identity ambiguity (#4877), silent `fastModel` fallback (#4078), and opaque settings override behavior make multi-provider setups confusing.

---

*Data snapshot: 2026-06-13T23:59 UTC. Generated from QwenLM/qwen-code repository.*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-06-13

## Today's Highlights

The **CodeWhale** rebrand is now official: `deepseek-tui` is deprecated, and all future releases ship as the `codewhale` command and npm package. A massive v0.8.60 "Agent Fleet" milestone series landed, introducing durable inbox/ledger, worker adapters (local-process and SSH), fleet manager loops, alerts (Slack/PagerDuty), and verifiable task specs. The v0.8.58-59 series also shipped fixes for provider-agnostic model selection, Anthropic native API support, and first-class Z.ai/StepFlash provider routes.

## Releases

**v0.8.59** — Final release under the `deepseek-tui` legacy name. **CodeWhale** is now the canonical project, command, npm package, and release-asset name. Users migrating from v0.8.x should follow `docs/REBRAND.md`.

## Hot Issues

1. **[#2584 — `bug`: /attach fails to send image base64 to multi-modal models](https://github.com/Hmbown/CodeWhale/issues/2584)** (Closed, 8 comments)  
   A user reported that `mimo-2.5` received a local file path instead of base64 encoding when using `/attach`. This likely blocked multi-modal workflows for all local-image users. Community flagged it with no upvotes, suggesting a narrow but critical regression.

2. **[#1871 — QoL: taskbar progress, animated title spinner, configurable completion sound](https://github.com/Hmbown/CodeWhale/issues/1871)** (Closed, 5 comments, 👍1)  
   Three small UX feedback mechanisms so users can alt-tab and know when processing completes. Shows the team is investing in non-blocking workflow ergonomics.

3. **[#431 — Bundled Exa web-search route](https://github.com/Hmbown/CodeWhale/issues/431)** (Open, 4 comments)  
   If `EXA_API_KEY` is set, route web_search through Exa MCP; otherwise fall back to DDG/Bing. This is key for users who want high-quality search results without manual config.

4. **[#1722 — Configurable auto-compact threshold with Ctrl+L](https://github.com/Hmbown/CodeWhale/issues/1722)** (Closed, 3 comments)  
   At ~99.6% context saturation the TUI becomes completely unresponsive. The fix introduces a configurable threshold and a dedicated keybinding — a direct response to a critical UX freeze bug.

5. **[#2606 — Sidebar "Work" panel checklist status not updating](https://github.com/Hmbown/CodeWhale/issues/2606)** (Closed, 3 comments)  
   After `checklist_write`, the main chat shows "100% complete" but the sidebar remains stale. Root cause: sidebar not re-fetched after turn completion. Affects anyone relying on the sidebar for status visibility.

6. **[#2787 — TUI status bar displays MCP count error](https://github.com/Hmbown/CodeWhale/issues/2787)** (Closed, 3 comments)  
   When both global and project-local MCP configs exist, the status bar shows an incorrect MCP count. This is a visual regression that could confuse users about whether their MCP tools are active.

7. **[#3018 — Un-hardcode DeepSeek from auto-router and subagent model selection](https://github.com/Hmbown/CodeWhale/issues/3018)** (Closed, 3 comments)  
   Auto-model mode and per-role subagent models only worked on DeepSeek. On Moonshot, OpenAI, Ollama, etc., the flash-router sent `deepseek-v4-flash` through the active provider — a guaranteed 400 error. This was a major blocker for multi-provider setups.

8. **[#471 — EPIC: Web UI scaffold (Option A)](https://github.com/Hmbown/CodeWhale/issues/471)** (Open, 3 comments)  
   A SolidJS or React+Vite web UI that talks to `deepseek serve --http` via existing API plus SSE. This is a strategic move to offer a browser-based alternative to the TUI, targeting users who prefer graphical interfaces.

9. **[#3159 — Fleet scheduler leases, heartbeats, backpressure, and stuck-worker recovery](https://github.com/Hmbown/CodeWhale/issues/3159)** (Closed, 2 comments)  
   Without leases and heartbeats, large fanout recreates existing hung-subagent failure modes. This issue defines the reliability foundation for the Agent Fleet — a key v0.8.60 milestone.

10. **[#2657 — Agents cannot tell why a tool is unavailable](https://github.com/Hmbown/CodeWhale/issues/2657)** (Closed, 2 comments)  
    In Plan Mode, shell execution was blocked, but the agent could not explain why. This makes autonomous debugging nearly impossible. The fix improves error messages so agents can request mode switches.

## Key PR Progress

1. **[#3191 — First-party Z.ai and StepFlash/StepFun provider routes](https://github.com/Hmbown/CodeWhale/pull/3191)** (Merged)  
   Adds Z.ai (GLM-5.1, 200K context, thinking mode) and StepFun/StepFlash as native providers. Users no longer need OpenRouter to access these models.

2. **[#3038 — Ctrl+B directly backgrounds active foreground shell](https://github.com/Hmbown/CodeWhale/pull/3038)** (Merged)  
   Eliminates a two-step `ShellControlView` menu. Now Ctrl+B immediately backgrounds shell commands — a direct UX improvement for power users.

3. **[#3034 — v0.8.58: Constitution refactor, Codex fixes, sidebar improvements](https://github.com/Hmbown/CodeWhale/pull/3034)** (Merged)  
   YAML source-of-truth for constitution, rebrand fixes across agent-facing surfaces, and sidebar split into 'Mode' and 'Work' panels. A foundational cleanup.

4. **[#3035 — Throttle AgentProgress redraws to prevent freeze under subagent load](https://github.com/Hmbown/CodeWhale/pull/3035)** (Merged)  
   When 4+ sub-agents run concurrently, every progress event triggered a full terminal redraw, saturating the render loop. Throttling prevents the freeze described in issue #3033.

5. **[#3040 — Clickable sidebar rows — click-to-act on Tasks and Agents panels](https://github.com/Hmbown/CodeWhale/pull/3040)** (Merged)  
   Mouse-click dispatch for sidebar rows: click a background job to view it, click its detail row to cancel it. This makes the TUI feel more interactive.

6. **[#3042 — `exec` CLI flags: --allowed-tools, --disallowed-tools, --max-turns, --append-system-prompt](https://github.com/Hmbown/CodeWhale/pull/3042)** (Merged)  
   Four new flags for unattended/CI/benchmark use. Users can now constrain tool access and turn limits from the CLI without config files.

7. **[#3054 — Native Anthropic Messages API adapter](https://github.com/Hmbown/CodeWhale/pull/3054)** (Merged)  
   `codewhale --provider anthropic` now uses native Anthropic API with `cache_control`, thinking blocks, and tool streaming. This is a major expansion beyond the DeepSeek/OpenAI ecosystem.

8. **[#3045 — Un-hardcode DeepSeek from subagent model validation](https://github.com/Hmbown/CodeWhale/pull/3045)** (Merged)  
   Non-DeepSeek providers (Moonshot, Ollama, OpenAI) can now use their own model IDs for sub-agent roles. This is the fix for issue #3018 — a critical multi-provider enabler.

9. **[#3049 — JSON decision contract, glob matchers, project-local hooks](https://github.com/Hmbown/CodeWhale/pull/3049)** (Merged)  
   Hooks can now emit JSON decisions (`allow`/`deny`/`ask`) on stdout, use glob patterns for matching, and be placed in `.codewhale/hooks/` per project. This makes the hooks system much more expressive.

10. **[#2686 — Tool-surface-diet design + north-star direction](https://github.com/Hmbown/CodeWhale/pull/2686)** (Merged)  
    Design-only deliverable defining the "canonical surfaces" cutover. Every cited tool instance was verified against the actual registry. This is the blueprint for reducing tool surface area and improving agent reliability.

## Feature Request Trends

- **Agent Fleet & Distributed Workers** — The v0.8.60 milestone dominates requests: fleet inbox/ledger (#3156), manager loops (#3157), SSH/local-process adapters (#3158), alerts/webhooks (#3161), and verifiable task specs (#3160). This is clearly the top strategic investment.
- **Web UI** — Issue #471 and its sub-issues (#472-474) for a SolidJS/React web scaffold, composer/transcript fidelity, file browser with Monaco, and approval flows. A major new frontend is in planning.
- **Configurable Keymaps** — Issue #436 (OPEN) proposes moving all bindings to `~/.deepseek/keybinds.toml` with multi-key sequences and conflict detection. A high-value ergonomic improvement for power users.
- **VS Code Extension** — Issue #461 (OPEN) scaffolds a full VS Code extension with OpenVSX compatibility for Cursor/VSCodium. This would make CodeWhale accessible from within editors.
- **Multi-Provider Parity** — Multiple issues and PRs (#3018, #3045, #3047, #3050, #3054) focus on making non-DeepSeek providers first-class citizens — model capability lookups, reasoning-effort wiring, and native API adapters.

## Developer Pain Points

1. **Context Saturation Freeze** — Issue #1722 describes TUI becoming completely unresponsive at ~99.6% context saturation. The auto-compact threshold fix is in, but the core problem (event loop starvation under high token load) may resurface.
2. **Subagent Reliability** — Issues #2605 (double-invocation for `agent_eval`), #2656 (session name conflicts hard to diagnose), and #3159 (no heartbeats/leases) show that subagent orchestration is fragile and error-prone for both users and AI agents.
3. **Multi-Provider Configuration** — Issues #3018 and #2787 highlight that configuring multiple providers often leads to silent failures: wrong model IDs sent, MCP count display errors, and reasoning-effort no-ops. The recent fixes improve this, but the surface area is large.
4. **Sidebar/Status Staleness** — Issue #2606 (checklist not updating) and #2787 (MCP count wrong) indicate that sidebar state synchronization with the engine is unreliable, leading to confusing UX where the UI disagrees with the actual state.
5. **Permission & Mode Confusion for Agents** — Issue #2657 shows that AI agents cannot easily tell why a tool is unavailable (e.g., blocked in Plan Mode). This makes autonomous debugging nearly impossible and forces manual user intervention.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*