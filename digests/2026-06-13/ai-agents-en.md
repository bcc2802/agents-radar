# OpenClaw Ecosystem Digest 2026-06-13

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-13 03:40 UTC

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

Based on the GitHub data for OpenClaw (github.com/openclaw/openclaw) as of 2026-06-13, here is the project digest.

---

### OpenClaw Project Digest — 2026-06-13

**1. Today's Overview**
OpenClaw is experiencing a period of intense activity and significant stability challenges. While a new patch release (`v2026.6.6`) landed with substantial security hardening, the project is grappling with a high volume of critical bugs. The 24-hour window shows 500 updated issues and 500 updated pull requests, indicating a very active community and maintainer team. However, the high number of open, unmerged PRs (357) and open issues (411) suggests a bottleneck in review and merging capacity relative to the volume of reported problems. The project's health is robust in terms of community engagement but strained by a growing backlog of high-severity regressions.

**2. Releases**
- **New Release:** `v2026.6.6` (openclaw 2026.6.6)
- **Highlights:** This release is a dedicated security hotfix. It substantially tightens security boundaries across critical surfaces, including transcripts, sandbox binds, host environment inheritance, MCP stdio, Codex HTTP access, native search policies, elevated sender checks, and several platform-specific access controls for Discord and Teams. No breaking changes or migration notes were highlighted.

**3. Project Progress**
In the last 24 hours, 143 PRs were merged or closed. Key fixes and features that advanced include:
- **Closed Fix for Gateway Event Loop Saturation:** PR #75378 ("[Bug] Gateway event loop saturation during parallel subagent spawn causes 1012 restart") was closed, likely addressing a major crash-loop issue for users running heavy multi-agent workflows.
- **Closed Fix for Kimi/Long Context Regression:** PR #71491 ("Kimi K2.6 reasoning_content 400 regression in long conversations") was closed, resolving a critical compatibility issue with long-running sessions on the Kimi model provider.
- **Mobile UI Progress:** A large PR (#89820) for mobile navigation (hamburger menu) and responsive layout was submitted, showing forward momentum on the web UI.
- **Accessibility Pass:** A multi-part UI polish series is under development, including PRs for keyboard shortcuts (#84827), contrast/focus states (#89822), and skeleton loading states (#89823).
- **End-of-Session Hook Feature:** A new PR (#92422) fixes a bug where isolated cron jobs would crash after using `sessions_yield`.
- **WhatsApp Stability:** A PR (#92095) to fix a bug where WhatsApp login status was reported as successful before authentication credentials were durably saved, preventing forced re-links on Docker container rebuilds, was submitted and is ready for review.

**4. Community Hot Topics**
The most active discussions highlight user frustration with degraded reliability and security concerns.
- **[#25592: Text between tool calls leaks to messaging channels](https://github.com/openclaw/openclaw/issues/25592)** (32 comments, Diamond Lobster rating). A major UX and security issue where internal agent processing text is accidentally sent to user channels. The high commenting volume indicates this is a widespread and critical problem.
- **[#9443: Request: Prebuilt Android APK releases](https://github.com/openclaw/openclaw/issues/9443)** (25 comments). A long-standing feature request with sustained community interest, indicating a strong desire for mobile companion app accessibility.
- **[#91588: Critical: Gateway Memory Leak](https://github.com/openclaw/openclaw/issues/91588)** (9 comments, P0 Silver Shellfish). Despite a lower comment count, this is a newly filed "P0" issue describing a catastrophic memory leak (350MB to 15.5GB), causing repeated OOM crashes. This is a top stability concern.
- **[#6615: Add denylist support for exec-approvals](https://github.com/openclaw/openclaw/issues/6615)** (7 comments, 7 👍). A highly upvoted feature request for a negative security policy ("allow everything except X"), showing a need for more granular control over command execution.

**5. Bugs & Stability**
The project is dealing with a significant number of high-severity regressions and crashes.
- **Severity: P0/CRITICAL**
    - **Gateway Memory Leak** (#91588): RSS grows to >15GB over days, leading to repeated OOM kills. No fix PR yet.
    - **memory_search Metadata Missing** (#91778, P0): Memory search is completely broken since v2026.6.1, rendering all agents "blind" to past context. No fix PR yet.
- **Severity: P1/HIGH**
    - **Session Context Confusion** (#32296): Agent replies to the previous message instead of the current one. A major UX regression.
    - **Parallel Subagent Crash** (#75378 - *Closed*): This was a recent source of crash loops, but the PR has been merged.
    - **Duplicate Message Content** (#88951): User messages are being duplicated 2-4 times, a severe usability bug reported after upgrading to 2026.5.x.
    - **180s Compaction Timeout Lock** (#92043): A legitimate, slow context compaction fails consistently on every turn due to a lowered 180-second timeout. A wall-clock-based timeout creates a deadlock.

**6. Feature Requests & Roadmap Signals**
Feature requests indicate a push toward enterprise-grade security, better data management, and more powerful automation.
- **Exec Policy Upgrades:** The request for a **denylist** (#6615) and **Pre-response enforcement hooks** (#13583) signals a move from "soft" prompt-based instructions to "hard" mechanical security gates for production deployments.
- **Data Resilience:** Multiple requests for **backup/restore utilities** (#13616), **secrets management integration** (#13610), and **tiered bootstrap file loading** (#22438) show a need for better state management and disaster recovery.
- **Automation Enhancements:** The **Direct Exec Mode for Cron Jobs** (#18160, 11 👍) is highly requested, as the current `agentTurn` approach for simple cron jobs is unreliable and costly. The need for a **Post-subagent completion hook** (#22358) also shows users are building complex workflows.
- **Prediction for v2026.7.x:** Based on activity, a fix for the `memory_search` metadata bug (#91778) is an absolute priority and will likely be the headline feature of the next patch. The "Direct Exec Mode" (#18160) and "denylist" (#6615) features have strong community backing and seem like strong candidates for the next minor release.

**7. User Feedback Summary**
User sentiment is mixed: appreciation for the system's power is tempered by frustration over recent regressions and unresolved long-standing issues.
- **Pain Points:**
    - **Regressions are painful:** Comments on bugs like the "Cannot convert undefined or null to object" (#38327) and "Duplicate message content" (#88951) explicitly state that these regressions occurred after updates, impacting trust in the upgrade process.
    - **Complex environment issues:** Users are struggling with complex environments like Docker-only sandboxing (#31331) and CLI deadlocks with gateway pairing scopes (#74484).
    - **Documentation vs. Reality:** Users report that features like multi-turn hook sessions (#11665) and agent directory bootstrap files (#29387) do not work as documented.
- **Satisfaction Signals:**
    - **High engagement:** The volume of feature requests and quality of bug reports indicates a deeply engaged and technically sophisticated user base that sees strong potential in the project.
    - **Enthusiastic adoption demands:** The high number of upvotes for features like Telegram Business Bot support (#20786, 6 👍) and Slack tool-level progress (#33413, 3 👍) shows users are actively integrating OpenClaw into their professional communication stacks.

**8. Backlog Watch**
- **Issue #9443 ([Prebuilt Android APK releases](https://github.com/openclaw/openclaw/issues/9443)):** P2, open since Feb 2026, 25 comments. A significant request for lowering the barrier to mobile use with no assigned milestone or linked PR.
- **Issue #13583 ([Pre-response enforcement hooks](https://github.com/openclaw/openclaw/issues/13583)):** P2, open since Feb 2026, needs product decision. Critical for high-stakes use cases (finance, security) but appears stalled.
- **Issue #10687 ([Models: fully dynamic model discovery](https://github.com/openclaw/openclaw/issues/10687)):** P2, needs product decision. A fundamental architectural improvement for model flexibility that has been open for over four months without resolution.
- **Issue #13616 ([Add backup/restore utility](https://github.com/openclaw/openclaw/issues/13616)):** P2, needs maintainer review. A foundational feature for disaster recovery and environment migration that has not been addressed.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided community digest summaries.

---

## Cross-Project Comparison Report: Personal AI Agent Ecosystem
**Date:** 2026-06-13

### 1. Ecosystem Overview

The personal AI agent open-source landscape is characterized by **frenetic, high-velocity development** across a broad set of projects, with security hardening, memory management, and multi-platform integration emerging as universal priorities. The ecosystem is bifurcating between **heavyweight, full-stack platforms** (like OpenClaw and IronClaw) and **lightweight, specialized agents** (like NullClaw and Moltis), with a middle tier of projects (NanoBot, NanoClaw, PicoClaw) rapidly iterating to gain feature parity with the leaders. A significant pattern is the strain of rapid growth: nearly all projects with high activity are grappling with growing backlogs of open issues and unmerged pull requests, suggesting a **universal bottleneck in maintainer bandwidth** relative to community contribution volume.

### 2. Activity Comparison

| Project | Issues (24h)* | PRs (24h)* | Release Status | Health Score | Key Signal |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | `v2026.6.6` (patch) | 🟡 Strained | High volume, high-criticality bugs. Review bottleneck. |
| **NanoBot** | N/A | 29 | None (in RC prep) | 🟢 Strong | High merge rate, focused on observability & memory. |
| **Hermes Agent** | 50 | 50 | None | 🟡 Overloaded | Massive backlog (49:1 open-to-closed ratio). |
| **PicoClaw** | 6 | 14 | `v0.2.9-nightly` | 🟢 Good | Fast iteration on permissions & protocol. |
| **NanoClaw** | 5 | 18 | ~`v2.0.64` (pre-release) | 🟢 Good | High merge velocity; Signal channel maturity. |
| **NullClaw** | 1 | 3 | None | 🟢 Quiet | Maintenance mode; single contributor. |
| **IronClaw** | 48 | 50 | `rc v0.29.1` (pending) | 🟠 High Velocity | Massive feature push (Reborn V2); CI broken. |
| **LobsterAI** | 1 | 17 | `2026.6.11` (prep) | 🟢 Strong | Rapid merges on core features (Computer Use, Voice). |
| **Moltis** | 3 | 0 | None | 🟡 Low Activity | Planning phase; no code merged. |
| **CoPaw** | 21 | 24 | Beta prep (`1.1.12b1`) | 🟡 Strained | High regressions; preparing major architecture upgrade. |
| **ZeroClaw** | 11 | 37 | `v0.8.x` (prep) | 🟢 Very High | Massive PR volume; critical bugs with fast fix PRs. |

*Note: Data from the 24-hour window of 2026-06-13. High numbers often indicate a release cycle or hackathon.*

### 3. OpenClaw's Position

**Advantages:**
- **Dominant Community Scale:** OpenClaw's metrics (500 issues/PRs in 24h) dwarf every other project by an order of magnitude, indicating the largest user base and contributor pool in the ecosystem.
- **Broadest Surface Area:** It supports the most extensive set of integrations (Discord, Teams, WhatsApp, Codex, MCP) and a highly modular architecture (sandbox binds, gateway scoping).
- **Security as a Feature:** The `v2026.6.6` release is a dedicated security hotfix, demonstrating a proactive stance on security boundaries that most peers are still playing catch-up on.

**Technical Approach Differences:**
- **Architecture:** OpenClaw is a **monolithic core with a wide surface of plugins**, in contrast to the more modular, Rust-focused approach of ZeroClaw or the simpler KISS design of NullClaw.
- **Scheduling:** Uses a complex `gateway` and `subagent` event-loop model (source of current saturation and memory leak issues) vs. the simpler `cron` + `agentTurn` pattern in NanoBot and NanoClaw.

**Community & Weaknesses:**
- **Scale Strain:** The review bottleneck is the worst in the ecosystem (357 open PRs, 411 open issues). The community is generating bugs faster than the core team can stabilize them, leading to a potential trust erosion.
- **Complexity Risk:** Features like `pre-response enforcement hooks` and `sessions_yield` are powerful but have bugs that create confusion. The documentation vs. reality gap (e.g., multi-turn hook sessions) is a sign of a system becoming too complex for its documentation to keep up.

### 4. Shared Technical Focus Areas

Several requirements are emerging across multiple projects simultaneously.

| Emerging Requirement | Related Projects | Specific Needs |
| :--- | :--- | :--- |
| **Memory & Context Stability** | OpenClaw, NanoBot, CoPaw | Memory metadata search broken (`#91778`), short-term "goldfish" problem (`#4044`), long conversation freezes (`#5161`). |
| **Security Hardening & Governance** | OpenClaw, PicoClaw, NanoClaw, ZeroClaw | Denylist for exec-approvals (#6615), channel-level permission scoping (#3109), mTLS (#45052), supply-chain gating (#2749). |
| **Agent Observability & Audit** | NanoBot, IronClaw, Hermes Agent | Audit modules for tool calls (#4319), trajectory observers (#4588), recording/replay for QA (#4773). |
| **Platform/Protocol Expansion** | PicoClaw, Moltis, CoPaw, ZeroClaw | Delta Chat (PicoClaw), Kubernetes sandbox (#1118), Slack (CoPaw #5152), llama.cpp model router (#7539). |
| **Desktop/Mobile App Reliability** | OpenClaw, Hermes Agent, CoPaw | Prebuilt APKs (#9443), Kanban board in desktop (#41222), system tray/auto-start (#5164). |
| **Better Turn/Automation Lifecycle** | OpenClaw, NanoBot, PicoClaw, ZeroClaw | Direct exec for cron jobs (#18160), post-subagent hook (#22358), turn completion signal (#2984). |

### 5. Differentiation Analysis

| Feature / Focus | OpenClaw | NanoBot | Hermes Agent | PicoClaw | NanoClaw | IronClaw | CoPaw | ZeroClaw |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Target User** | Power users / Devs | Devs / Integrators | Devs / Enterprise | Devs / Embedded | Devs / Multi-platform | Enterprise / SaaS | General / Power | General / Devs |
| **Core Language** | Go | Python | Python | Go | Go | Rust | Python | Rust |
| **Architecture** | Monolithic + Plugins | Modular (YAEF) | Hub-based | Lightweight Core | Modular Agents | Reborn Engine V2 | Plugin-based | Modular (WASM) |
| **Unique Strength** | **Scale & Integration** | **Observability** | **UI/Desktop** | **Permission Scoping** | **Signal Maturity** | **Thread Lifecycle** | **Desktop & Memory** | **Plugin System** |
| **Weakness** | **Review Bottleneck** | **Memory Stability** | **Backlog Overload** | **Model Compatibility** | **Silent Failures** | **CI Blocked** | **Regression Rate** | **Cross-Platform Bugs** |
| **Innovation** | - | Agent Audit System | - | - | - | DeferredBusy | AgentScope 2.0 | 3-Engine Unification |

### 6. Community Momentum & Maturity

**Tier 1: Rapidly Iterating / High Risk-High Reward**
- **OpenClaw:** Massive scale, but significant stability challenges. The next patch will be critical for user confidence.
- **IronClaw:** Most intense feature push (Reborn V2), but CI is broken, and a large backlog of breaking changes is pending.
- **ZeroClaw:** Very high velocity on bug fixes and infrastructure (WASM plugins, engine unification). Fast response to S1 bugs is a strong positive signal.

**Tier 2: Strong Growth with Maturity**
- **NanoBot, NanoClaw, PicoClaw:** These projects are merging code rapidly, stabilizing core features (memory, permissions, protocols), and are in a healthy "growth" phase. They represent the best "bang for the buck" for developers looking for a stable, feature-rich agent framework.

**Tier 3: Stabilizing / Maintenance**
- **NullClaw, LobsterAI, CoPaw:** These projects are focused on release engineering and fixing regressions. CoPaw is in a transitional pre-1.1.12 beta phase. LobsterAI is merging a batch of fixes for a pending release.
- **Moltis:** In a planning phase; low activity suggests a potential lull before a major feature push.

### 7. Trend Signals

Several strong industry trends are evident from the community feedback and project roadmaps:

1.  **The "Polyglot Agent" is Standard:** Users expect agents to work across Telegram, WhatsApp, Discord, Slack, Signal, and proprietary channels (e.g., Feishu, DingTalk) simultaneously. Multi-platform routing (agent swarm in Telegram, correct JID routing in WhatsApp) is no longer a "nice-to-have."

2.  **Memory is the #1 UX Bottleneck:** The most frequent complaints across all projects are about agents **forgetting context**. Whether it's the "goldfish problem" in NanoBot or the `memory_search` metadata bug in OpenClaw, the ecosystem is converging on the fact that reliable, long-term memory is the single largest obstacle to building truly useful autonomous agents.

3.  **Security is Moving from "Prompt" to "Code":** Users are rejecting "soft" prompt-based security instructions in favor of "hard" mechanical gates. The demand for denylists (`#6615`), permission scoping (`#3109`), pre-response hooks (`#13583`), and supply-chain verification (`#2749`) signals a shift toward a **zero-trust architecture** for agent execution.

4.  **Observability is Non-Negotiable for Adoption:** The rapid merge of the Agent Audit System in NanoBot and the trajectory observer work in IronClaw show that as agents become more capable, the need for debugging, introspection, and replay becomes critical for both developers and end-users. Silent failures (e.g., NanoClaw's `send_message` dropping responses) are a top source of frustration.

5.  **Desktop App Maturity is a Competitive Differentiator:** Issues like the Windows GPU crash in Hermes Agent, the Kanban board request, and the system tray/auto-start feature for CoPaw show that the desktop app is no longer just a web wrapper; it is expected to be a polished, native, and integrated part of the user's workflow.

6.  **Paid API Integrations Are a Priority:** Requests for `kimi-for-coding` (CoPaw) and the broken Anthropic OAuth flow (Hermes Agent) show that users are eager to leverage their paid subscriptions. Projects that make it easy to authenticate and use premium services (including local models via Ollama) have a clear adoption advantage.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for 2026-06-13.

***

## NanoBot Project Digest — 2026-06-13

### 1. Today's Overview
The project is experiencing **high activity**, dominated by a significant infrastructure effort led by a single contributor (yu-xin-c) focusing on security hardening and memory stability. A major feature wave is also underway, with three separate, progressively refined PRs landed to introduce a new **agent audit/observability** system. While no new releases were cut, the volume of merged code and open PRs (29 updated in 24h) suggests a strong push toward a stable release candidate. The community is actively contributing features (TTS, WebUI parity, WhatsApp mentions), while maintainers are aggressively closing bugs related to memory consistency.

### 2. Releases
**No new releases** were published in the last 24 hours.

### 3. Project Progress (Merged/Closed PRs)
9 PRs were merged or closed. The most significant advancements include:

- **Agent Audit System (Landed):** Three iterative PRs by bjoshuanoah ([#4319](https://github.com/HKUDS/nanobot/pull/4319), [#4318](https://github.com/HKUDS/nanobot/pull/4318), [#4320](https://github.com/HKUDS/nanobot/pull/4320)) were merged to add a fully configurable `tools.audit` module. This provides observability into agent tool calls with four transport backends (loguru, HTTP webhook, JSONL, callback).
- **Cron & Subagent Fix:** PR [#4304](https://github.com/HKUDS/nanobot/pull/4304) (michaelxer) was merged, fixing a critical race condition where cron jobs were marked complete before their spawned subagent tasks finished running.
- **Bug Fixes Closed:** Three long-standing bugs were closed:
    - `find_legal_message_start` logic flaw ([#4203](https://github.com/HKUDS/nanobot/pull/4203))
    - Orphaned tool results ([#4006](https://github.com/HKUDS/nanobot/pull/4006))
    - Multiple custom provider request ([#4305](https://github.com/HKUDS/nanobot/pull/4305))

### 4. Community Hot Topics
- **Short-Term Memory Loss (Issue #4044 - Open):** This is the most debated open issue (5 comments). The user reports a fundamental "goldfish" problem where the agent forgets the user's immediate answer to its own question. The community analysis points to context window pressure from system prompts (SOUL.md, USER.md, MEMORY.md). This is likely a top priority for the next release. [Link](https://github.com/HKUDS/nanobot/issues/4044)
- **Large Feature PRs:** The highest-impact open PRs are the TTS configuration system ([#4316](https://github.com/HKUDS/nanobot/pull/4316)) by tobrien and the WebUI/config.json parity overhaul ([#4313](https://github.com/HKUDS/nanobot/pull/4313)) by La-Volpe. These represent strong community contributions that solve missing feature parity.
- **API Usage Zero Bug (Issue #4309 - Open):** A user reported that the OpenAI-compatible `/v1/chat/completions` endpoint always returns zero token usage. This is a high-visibility bug for anyone integrating with the serve API. [Link](https://github.com/HKUDS/nanobot/issues/4309)

### 5. Bugs & Stability
| Severity | Bug | Status | Fix PR Exists? |
| :--- | :--- | :--- | :--- |
| **Critical** | **Post-turn consolidation wipes agent's own delivery message** ([#4307](https://github.com/HKUDS/nanobot/issues/4307)) | Open | No |
| **High** | **Short term memory loss** ([#4044](https://github.com/HKUDS/nanobot/issues/4044)) | Open | No |
| **Medium** | **`/v1/chat/completions` always returns zero usage tokens** ([#4309](https://github.com/HKUDS/nanobot/issues/4309)) | Open | No |
| **Medium** | **Dream cursor not advancing when `dream.enabled` is off** ([#4321](https://github.com/HKUDS/nanobot/pull/4321)) | Open (PR) | Yes (PR #4321) |

**Key Insight:** The most dangerous reported bug is [#4307](https://github.com/HKUDS/nanobot/issues/4307) (loop consolidation wiping the assistant's own message), which would break user follow-up references. No fix PR is linked yet.

### 6. Feature Requests & Roadmap Signals
- **Voice (TTS) Support:** PR [#4316](https://github.com/HKUDS/nanobot/pull/4316) adds a full TTS configuration system (OpenAI, Groq, ElevenLabs). This is mature code with discoverability docs, signaling it is likely to be merged soon.
- **WebUI/Config Parity:** PR [#4313](https://github.com/HKUDS/nanobot/pull/4313) is closing the gap between WebUI and `config.json`, enabling settings configuration through the UI that previously required manual file edits.
- **Multiple Custom Providers:** Issue [#4305](https://github.com/HKUDS/nanobot/issues/4305) requesting a "template" parameter for providers was closed, suggesting the team either has a different solution in mind or considers this a low priority.
- **SDK Expansion:** PR [#4296](https://github.com/HKUDS/nanobot/pull/4296) is upgrading the Python SDK for developers, adding richer metadata and controls.

### 7. User Feedback Summary
- **Core Pain Point - Context Collapse:** The dominant user complaint is the agent's inability to hold a coherent short-term conversation. The "short-term memory loss" bug reflects real frustration where the agent cannot remember its own previous statement in a single chat turn.
- **Feature Gap - Media/File Handling:** Multiple PRs this week and last (e.g., [#4312](https://github.com/HKUDS/nanobot/pull/4312), [#4311](https://github.com/HKUDS/nanobot/pull/4311)) address user error states in file/media tools. Users are feeding malformed attachments or limits, indicating the UI or documentation isn't preventing these errors.
- **Satisfaction - Observability:** The rapid merge of the audit module suggests internal demand for this feature (flag: `release-TCH-486-audit`) is high, and the community is eager for better debugging tools.

### 8. Backlog Watch
- **Security Sandbox PRs:** Contributor yu-xin-c has a **long tail of critical security and stability PRs** that remain open: blocking symlink escapes ([#4119](https://github.com/HKUDS/nanobot/pull/4119)), keeping read-only roots secure ([#4053](https://github.com/HKUDS/nanobot/pull/4053)), and memory cursor monotonicity ([#4256](https://github.com/HKUDS/nanobot/pull/4256)). These have been open for **12-20 days** without merge. These are high-value, safety-critical changes that require maintainer review.
- **Memory Lifecycle Test Harness:** PR [#4193](https://github.com/HKUDS/nanobot/pull/4193) (also by yu-xin-c) proposes a comprehensive test for the memory system but has been open for **9 days**. The lack of movement here is concerning given the open memory-related bugs reported by users.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

Here is the project digest for **Hermes Agent** on **2026-06-13**.

---

## Hermes Agent Project Digest (2026-06-13)

### 1. Today's Overview
The project is experiencing extremely high activity today, with **50 issues** and **50 PRs** updated in the last 24 hours. This volume is uncharacteristically high, likely due to a release cycle or a hackathon, and indicates a very healthy, engaged contributor base. While the issue count is high, the open-to-closed ratio (49:1) suggests a significant backlog is forming, with maintainers needing to triage aggressively. The focus of contributions is heavily weighted toward bug fixes for gateway integrations, terminal tool behavior, and infrastructure improvements, rather than major new feature work.

### 2. Releases
No new releases were published in the last 24 hours.

### 3. Project Progress
Only **one PR was merged or closed** in the last day, leaving a very large queue of open PRs.
- **#45340** (Closed): A spam/invalid feature request related to hacking was closed.
- **Pending Merges:** A significant number of "fix" PRs are open and awaiting review, including critical fixes for Docker ownership, cron job editing, BlueBubbles webhook issues, and terminal notification behavior (see Section 5).

### 4. Community Hot Topics
The most active discussions highlight major friction points in the user experience:

- **Dependency & Toolchain Management:** Issue **#40666** (3 comments) requests bumping the default toolchain to Python 3.13, Node 24, and Vite 8. This reflects a broad user desire to stay on modern, supported runtimes. This is a lower-priority (P3) housekeeping item that affects all users.
- **Context & Compression:** Issue **#39691** (2 comments, 6 👍) requests integrating `headroom-ai` for tool output compression. This is the most upvoted open issue, indicating strong user interest in more granular, per-tool compression rather than the current session-level full summarization. This is a strong signal for a future feature.
- **Docker Gateway Bug:** Issue **#45129** (2 comments) points out that `docker_extra_args` in config is silently ignored by the gateway. This is a P2 bug that breaks a core configuration feature for Docker users, sparking discussion about the root cause.
- **UX in Desktop App:** Issue **#41222** (2 comments, 2 👍) requests integrating the Kanban board into the desktop app. This highlights a desire for a more unified, less fragmented user interface.

### 5. Bugs & Stability
Today saw a high number of new bug reports. The most severe (P2) items include:

- **Terminal `notify_on_complete` Flooding (#45352, #45357, #45359, #45366):** This is the highest-frequency issue today. When using `terminal(background=true, notify_on_complete=true)`, ALL process exits (including failures and kills) are pushed into the chat. **Four separate PRs (#45357, #45359, #45366, #45380)** have been opened to fix this, indicating a clear consensus and that a fix is imminent. *(Link: #45352)*
- **Docker Gateway Log Crash Loop (#45258, #45274):** The gateway’s log service creates parent directories owned by `root`, causing a fatal `s6-log` loop when new profiles are added. A fix PR (#45274) is already open. *(Link: #45258)*
- **Anthropic OAuth Login Failure (#45250):** The OAuth flow for Claude Pro/Max users is completely broken, returning a HTTP 404 at the token-exchange step. This blocks premium users from authenticating. *(Link: #45250)*
- **WhatsApp Group Routing Bug (#18646):** A long-standing issue (created May 2) where `send_message` ignores the specified WhatsApp group JID and delivers to the user's home channel instead. *(Link: #18646)*
- **macOS Desktop GPU Crash (#45226):** The `hermes desktop` app crashes repeatedly on Windows due to a GPU process error, making the app unusable on that platform. *(Link: #45226)*

A full list of reports is available in the data; notable P3 items include the sidebar moving during fullscreen on macOS (#45264), and a Node shadowing issue on macOS (#45279).

### 6. Feature Requests & Roadmap Signals
- **Home for Code/Compression:** The strong upvote on **#39691** (headroom-ai integration) is a clear signal. This feature fits the "agent efficiency" theme and may be prioritized for the next minor release.
- **Unified Session History (#45275):** A user request to merge Telegram and Desktop app session lists into one view. This is a significant UX enhancement request that would require a major architectural change to the session storage.
- **Multi-Agent Workflow UX (#41222):** Kanban board integration into Desktop. This is a "nice-to-have" but signals that power users want the desktop app to be a central command center.
- **Toolchain Bumps (#40666, #45377, #45374, #45375, #45376):** A torrent of issues regarding outdated Node, Electron, and various npm packages. The maintainers are likely aware of the maintenance debt, and a bulk update PR is probable in the next week.

### 7. User Feedback Summary
- **Pain Points:** The most urgent pain points revolve around **reliability and predictability**. Users are frustrated by failing OAuth flows (Anthropic), broken terminal tool behavior (flooding notifications), and ignored configuration (`docker_extra_args`). The high number of configuration-related bugs (deepseek providers, docker args) suggests the config system is becoming fragile and hard to maintain.
- **Desktop App Dissatisfaction:** The Windows GPU crash (#45226) and macOS fullscreen animation bugs (#45264) indicate the desktop app still has significant polish issues.
- **Positive Signals:** The high volume of PRs from a diverse set of contributors (kyssta-exe, LeonSGP43, liuhao1024, lEWFkRAD) shows a healthy community eager to fix problems. The draft PR for mTLS (#45052) shows attention to enterprise/security use cases.

### 8. Backlog Watch
The project has a massive backlog of issues that are weeks old and still open. The following require urgent maintainer attention:

- **#18646** (P2, May 02): WhatsApp group routing bug. Opened for 6 weeks with no fix PR.
- **#17199** (P2, Apr 29): DeepSeek provider configuration bugs. Opened for 7 weeks.
- **#16484** (P2, Apr 27): Gemini provider routing to `/v1beta` is impossible.
- **#26264** (P2, May 15): Dashboard resume shows "session ended" on non-loopback binds.
- **#44763** (P2, Jun 12): `computer_use` tool returns zero-coordinate element bounds on macOS, breaking the entire tool.

The sheer volume (50 items updated today) suggests the maintainers are overwhelmed. A formal triage session or dedicated "bug smash" week may be necessary to clear the high-priority backlog.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-06-13

## Today's Overview

PicoClaw shows **high development velocity** with 6 issues and 14 pull requests updated in the past 24 hours, including 3 merged/closed PRs and 1 new nightly release. The project's maintainers are actively addressing both bug reports and feature work across channels, protocols, and model providers. Community engagement is moderate, with several serialization safety fixes and protocol enhancements moving through the pipeline. The release of v0.2.9-nightly.20260613 signals ongoing stabilization work, though some critical bugs around token consumption and model compatibility remain under investigation.

## Releases

A new **nightly build (v0.2.9-nightly.20260613.c362114c)** was published on 2026-06-13. This is an automated build that may be unstable; the maintainers recommend caution in production use. Key details:
- **Changelog**: https://github.com/sipeed/picoclaw/compare/v0.2.9...main
- No announced breaking changes or migration notes for this nightly release.

## Project Progress

Three pull requests were **merged or closed** today:

- **[PR #3109](https://github.com/sipeed/picoclaw/pull/3109)** (closed): **Channel-level permission scoping** — adds support for restricting dangerous operations (shell commands, file modification) in group/channel chats vs. private chats. A significant security and governance feature.
- **[PR #3113](https://github.com/sipeed/picoclaw/pull/3113)** (merged): **Fix JSON marshal/unmarshal error handling** in `toChannelHashes` — three previously silent serialization errors in the channel manager are now properly checked.
- **[PR #3112](https://github.com/sipeed/picoclaw/pull/3112)** (merged): **Fix tool call arguments JSON error** — `json.Marshal` errors in the tool loop are now handled instead of silently discarding tool call data.

These PRs improve error resilience in channel configuration, tool execution, and add broader permission controls. The large **[PR #2551](https://github.com/sipeed/picoclaw/pull/2551)** (closed) — a major refactor decoupling channel names from provider types to allow multiple instances of the same provider — also cleared today, a foundational architectural improvement.

## Community Hot Topics

The most active discussions center around **protocol clarity and model compatibility**:

- **[Issue #2984](https://github.com/sipeed/picoclaw/issues/2984)** (👍2, 2 comments): *"Add explicit turn completion signal for Pico WebSocket clients"* — External WebSocket clients lack a deterministic signal for when the agent has finished processing. This has a companion fix PR [#3116](https://github.com/sipeed/picoclaw/pull/3116), indicating maintainers are actively addressing this gap.
- **[Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)** (2 comments): *"Continuous consumption of tokens every minute when evolution is enabled"* — A potentially costly bug for users relying on Evolution mode (Draft with Code Path trigger). This has been open since June 5 and is now marked `[stale]`, suggesting it may be deprioritized.

**Underlying need**: The community is pressing for better **deterministic protocol signals** for clients and safer **permission models** for multi-context deployments (private vs. group vs. channel). Both reflect maturity demands as PicoClaw moves beyond basic chatbot use.

## Bugs & Stability

Three bugs reported today, ranked by severity:

**High severity**:
- **[Issue #3111](https://github.com/sipeed/picoclaw/issues/3111)** — *"Tool execution fails with Gemini 3.5 Flash (Missing thought_signature in schema)"* → 400 error from Google API due to incompatible response schema. **Blocks all Gemini 3.5 Flash tool usage** with no fix PR yet.

**Medium severity**:
- **[Issue #3110](https://github.com/sipeed/picoclaw/issues/3110)** — *"Telegram adapter ignores message_thread_id in Forum topics"* → Replies default to `#General` instead of the correct thread topic. **No fix PR yet.**
- **[Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)** — *"Continuous token consumption every minute with evolution enabled"* — A resource drain bug affecting FreeBSD users with MiniMax models. Marked `[stale]`; no fix PR.

**Lower severity / in-progress fixes**:
- **[PR #3115](https://github.com/sipeed/picoclaw/pull/3115)** (open) — Fixes session-history corruption when data URLs appear in text tool output (e.g., `read_file` / `exec` returning `data:image/...` strings).
- **[PR #3091](https://github.com/sipeed/picoclaw/pull/3091)** (open) — Fixes silent disabling of `native_search` due to unchecked type assertion in OpenAI compat provider.
- **[PR #3053](https://github.com/sipeed/picoclaw/pull/3053)** (open) — Fixes possible panic in Evolution's store lock due to unsafe type assertion on `sync.Map.LoadOrStore`.

## Feature Requests & Roadmap Signals

Two major feature directions are visible:

1. **Granular permission scoping** — [#3109](https://github.com/sipeed/picoclaw/issues/3109) (now closed as implemented) and [#3114](https://github.com/sipeed/picoclaw/issues/3114) (open, for Telegram specifically) demand distinguishability between private/group/channel chat contexts. This will likely ship in the **next minor release (v0.3.0)** given the merged PR.

2. **Turn completion lifecycle** — The protocol-level `turn.done` signal (Issue #2984, PR #3116) is actively in review and likely to land soon, improving WebSocket client reliability.

3. **New integrations** — PRs for a **Delta Chat gateway** ([#3063](https://github.com/sipeed/picoclaw/pull/3063)) and **NEAR AI Cloud provider** ([#2917](https://github.com/sipeed/picoclaw/pull/2917)) indicate expansion plans for both decentralized chat and decentralized AI compute.

**Prediction**: The permission scoping + turn completion + Gemini 3.5 Flash fix will likely compose the **v0.3.0 release** within the next 2-3 weeks.

## User Feedback Summary

- **Pain point**: Users with automated deployments (FreeBSD, MiniMax models, evolution mode) are experiencing significant **uncontrolled token consumption** — a cost and reliability concern.
- **Pain point**: Developers building custom WebSocket clients and Telegram bots face **missing protocol signals** (no turn completion) and **Forum thread misrouting**.
- **Satisfaction**: The permission scoping feature (Issue #3109) was positively received, gaining immediate traction and quick implementation — reflecting maintainers' responsiveness to governance needs.
- **Frustration**: The Gemini 3.5 Flash incompatibility (Issue #3111) is blocking users on the latest Google models with no workaround apparent.

## Backlog Watch

Items needing maintainer attention:

- **[Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)** (open 8 days, 2 comments) — *"Continuous token consumption when evolution enabled"* — Marked `[stale]` but remains unresolved for users on FreeBSD/MiniMax. No fix PR or maintainer response indicating prioritization.
- **[PR #2964](https://github.com/sipeed/picoclaw/pull/2964)** (open 16 days, no maintainer response) — *"Feat/image input compression"* — A substantial feature for configurable inbound image compression; has seen no comment or review since May 28.
- **[PR #2917](https://github.com/sipeed/picoclaw/pull/2917)** (open 23 days) — *"Add NEAR AI Cloud provider"* — A significant provider integration sitting without review since May 21.
- **[Issue #2984](https://github.com/sipeed/picoclaw/issues/2984)** (open 11 days, 👍2) — *"Turn completion signal"* — Active fix PR (#3116) exists but hasn't been merged yet; given the 👎 count and explicit PR, it deserves prompt closure.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-06-13

## Today's Overview
NanoClaw is experiencing a surge of activity, with **18 pull requests** updated and **5 issues** active in the last 24 hours, signaling a healthy, fast-moving open-source project. The majority of PR activity involves closed/merged fixes and features, indicating the maintainers are actively clearing a substantial queue of improvements. Community contributions are particularly high today, with external developers submitting several security hardening PRs alongside the core team's work. The project remains in a high-velocity development phase with no new formal release cut, but the volume of merged PRs suggests one may be imminent.

## Releases
No new releases were published as of this digest. The upstream `main` branch is noted at approximately **v2.0.64**. With 10 PRs merged/closed in the last 24 hours alone, a release bundling these changes (particularly the batch of Signal features and the poison-resume crash fix) appears likely within the week.

## Project Progress
Ten pull requests were merged or closed today, reflecting substantial forward momentum across several areas:

- **Signal channel maturity** — Four PRs advanced Signal as a first-class integration: 
  - [PR #2203](https://github.com/nanocoai/nanoclaw/pull/2203) — Adds bidirectional reaction support
  - [PR #2071](https://github.com/nanocoai/nanoclaw/pull/2071) — Routes all non-audio attachments through the inbox path
  - [PR #2070](https://github.com/nanocoai/nanoclaw/pull/2070) — Accepts host-path attachments in `extractAttachmentFiles`
  - [PR #2040](https://github.com/nanocoai/nanoclaw/pull/2040) — Enables outbound file attachments
  - [PR #2072](https://github.com/nanocoai/nanoclaw/pull/2072) — Adds multimodal image support for Ollama models

- **Agent runner reliability** — Critical fixes merged:
  - [PR #2670](https://github.com/nanocoai/nanoclaw/pull/2670) — Self-healing for the poison-resume crash loop (fixes #2669)
  - [PR #2277](https://github.com/nanocoai/nanoclaw/pull/2277) — Refreshes routing context on follow-up messages mid-query
  - [PR #2267](https://github.com/nanocoai/nanoclaw/pull/2267) — Routes agent-to-agent replies back to the originating session
  - [PR #2692](https://github.com/nanocoai/nanoclaw/pull/2692) — Retries transient 5xx API errors and notifies on exhaustion

- **Backup & disaster recovery** — [PR #2084](https://github.com/nanocoai/nanoclaw/pull/2084) merged: adds daily project backup with S3 support and per-agent restore via CLI

## Community Hot Topics

1. **[Issue #2632](https://github.com/nanocoai/nanoclaw/issues/2632) — Telegram agent-swarm status (1 comment)**  
   Author `arthurkrupa` is trying to plan a v1-to-v2 migration involving the old `/add-telegram-swarm` feature but finds the current state ambiguous. This touches the broader question of how v2 handles multi-bot identity, which remains undocumented. The single comment suggests a maintainer may have responded, but the issue is still open — likely awaiting a clear migration guide.

2. **[Issue #2506](https://github.com/nanocoai/nanoclaw/issues/2506) — send_message dedup drops responses (3 comments)**  
   The most-commented issue today. Two related timing bugs cause agent responses to be silently dropped when turns complete within 60 seconds or when a follow-up arrives mid-stream. This is a high-impact reliability issue that likely frustrates users running real-time conversational agents.

3. **[Issue #2711](https://github.com/nanocoai/nanoclaw/issues/2711) — create_agent MCP tool is ungated (1 comment)**  
   A security concern: the `create_agent` tool is documented as admin-only but has no actual access control, allowing any container to create new agent groups. This has been present since commit e83ffbc and represents a privilege escalation vector.

## Bugs & Stability

| Severity | Issue | Description | Fix PR Exists? |
|----------|-------|-------------|----------------|
| **Critical** | [#2506](https://github.com/nanocoai/nanoclaw/issues/2506) | `send_message` silently drops responses when turns complete within 60 seconds or a follow-up arrives mid-stream. Client times out with no reply. | ❌ No |
| **High** | [#2668](https://github.com/nanocoai/nanoclaw/issues/2668) | No per-tool timeout: a hung MCP tool blocks an agent session for up to 30 minutes before cold-kill. No heartbeats during tool execution. | ❌ No |
| **High** | [#2711](https://github.com/nanocoai/nanoclaw/issues/2711) | `create_agent` MCP tool is ungated — any container can create agent groups despite "admin-only" documentation. | ❌ No |
| **Medium** | [#2751](https://github.com/nanocoai/nanoclaw/issues/2751) | Budget-exhausted LLM turns are silently dropped; user receives no reply. OneCLI cloud returns fabricated HTTP 200 with synthetic message. | ❌ No |

**Today's fix PRs addressing existing bugs:**
- [PR #2750](https://github.com/nanocoai/nanoclaw/pull/2750) — Recover stale `outbound.db` journals after container kills (fixes #2516, #2640)
- [PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752) — Stage inbound attachments that expose only a URL (Discord)

## Feature Requests & Roadmap Signals

Several large capability PRs were opened today, indicating the maintainers' roadmap direction:

- **[PR #2745](https://github.com/nanocoai/nanoclaw/pull/2745) — Opt-in persistent memory scaffold** — A provider capability (`usesMemoryScaffold`) and container interface for long-term agent memory. Likely a foundational piece that providers can opt into.

- **[PR #2746](https://github.com/nanocoai/nanoclaw/pull/2746) — Agent-surfaces capability seam** — A host-side registry where providers declare capabilities. This is a core architectural change that makes the system more pluggable and introspectable.

- **[PR #2747](https://github.com/nanocoai/nanoclaw/pull/2747) — OneCLI SDK 2.2.1 bump** — Credential-stub mounts and machine-checkable pins, indicating continued investment in the OneCLI cloud integration.

- **[PR #2748](https://github.com/nanocoai/nanoclaw/pull/2748) — Harden agent containers** — Defense-in-depth: `--cap-drop=ALL`, `--security-opt no-new-privileges:true`, `--pids-limit 2048`. This suggests security is now a priority (perhaps prompted by Issue #2711).

- **[PR #2749](https://github.com/nanocoai/nanoclaw/pull/2749) — Gate npm installs by package release age** — Prevents agents from installing packages published less than 3 days ago (configurable), adding supply-chain security.

These PRs point toward a **v2.1 release** focused on: security hardening, persistent memory, and a capability-driven provider architecture.

## User Feedback Summary

Real user pain points surfaced today:

1. **Silent failures are a major frustration** — Issue #2506 (dropped responses) and #2751 (budget exhaustion silence) both describe scenarios where the agent simply stops responding with no error feedback. Users are left debugging timeouts.

2. **Migration anxiety** — Issue #2632 reveals that users depending on v1 features (Telegram swarms) are in limbo, unsure whether to migrate. The project would benefit from a clear migration guide for v1→v2.

3. **Security concerns** — Issue #2711's report that `create_agent` is effectively ungated shows users are paying attention to access control boundaries. The community's security focus is validated by today's two security-focused PRs from external contributor `boazdori`.

4. **Timeouts without diagnostics** — Issue #2668 (30-min tool hangs) indicates that even sophisticated users hit operational walls where they can only kill containers. The heartbeat mechanism is correctly identified as insufficient for long-running tool calls.

## Backlog Watch

The following issues are important but not yet addressed:

- **[Issue #2506](https://github.com/nanocoai/nanoclaw/issues/2506) — send_message dedup (3 comments, since May 16)**  
  This is the highest-impact open bug. It has been open for nearly a month with three comments and no fix PR. Given that it causes silent response drops, it should be a priority for maintainers.

- **[Issue #2668](https://github.com/nanocoai/nanoclaw/issues/2668) — No per-tool timeout (since June 1)**  
  A 30-minute session block on a hung tool is a significant operational pain point. No fix PR exists despite being open for 12 days.

- **[Issue #2711](https://github.com/nanocoai/nanoclaw/issues/2711) — create_agent ungated (since June 7)**  
  This security issue has been open for 6 days. Interestingly, [PR #2748](https://github.com/nanocoai/nanoclaw/pull/2748) (container hardening) opened today may be a partial response, but the specific gating issue remains.

- **[Issue #2632](https://github.com/nanocoai/nanoclaw/issues/2632) — Telegram swarm migration (since May 28)**  
  Open for 16 days with one comment. A user is blocked on planning a migration — this needs a clear documented answer or code gesture.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the NullClaw project digest for June 13, 2026.

---

## NullClaw Project Digest
**Date:** 2026-06-13
**Data Source:** GitHub (nullclaw/nullclaw)

### 1. Today's Overview
The NullClaw project is experiencing moderate activity today, with a focus on infrastructure hardening and user-reported bugs. Three pull requests (PRs) remain open for review, primarily addressing configuration flexibility and Discord gateway reliability. A single open issue highlights a potential compatibility problem with local models running via Ollama, where the agent fails to produce complete sentences. There are no new releases, indicating the project is in a maintenance and stabilization phase between version cycles.

### 2. Releases
No new releases have been published in the last 24 hours.

### 3. Project Progress
No pull requests were merged or closed in the last 24 hours. The three open PRs represent the current active development work:
- **PR #949** (fix: make queue_mode configurable from config.json): Adds an `agent.default_queue_mode` field to `config.json`, allowing users to set the initial queue mode without code changes.
- **PR #951** (fix(agent_runner): suppress stderr initialization logs on agent failure): Prevents verbose initialization logs from being posted as agent responses when the agent process fails.
- **PR #953** (fix(discord): recover closed gateway sockets): Implements cleanup logic for Discord gateway sockets, including a grace window for stalled reconnections and regression tests.

### 4. Community Hot Topics
The most active item is **Issue #952** regarding incomplete answers from local models. While it has zero comments, it is the only open issue and represents a core functionality problem that likely resonates with users running local AI models. The three open PRs, all authored by vernonstinebaker, indicate a single contributor driving the current stability effort but receiving no community review or reaction yet.

- **Issue #952** (Bug: Local model using ollama returns incomplete answers) – [Link](nullclaw/nullclaw Issue #952)

### 5. Bugs & Stability
**High Severity:**
- **Issue #952** (Local model incomplete answers): Reported by bloodgroup-cplusplus, this bug indicates that the agent is not generating full sentences when using Ollama’s Gemma model. This is a critical usability issue for users relying on local inference. No fix PR exists yet.

**Low/Medium Severity (Fix PRs Exist):**
- **PR #951** (Suppress stderr logs on agent failure): While not a standard bug, this addresses a "wrong output" bug where diagnostic logs leak into user-facing channels when the agent crashes.
- **PR #953** (Discord gateway socket recovery): Fixes a potential disconnection crash where a closed gateway socket could cause heartbeat thread conflicts.

### 6. Feature Requests & Roadmap Signals
The primary feature signal comes from **PR #949**, which introduces a configuration option (`agent.default_queue_mode`) into the JSON config file. This suggests the maintainers are moving toward more declarative, user-configurable agent behavior. A likely next step would be exposing similar agent parameters (e.g., default model, temperature) to the config file to reduce reliance on CLI flags or hardcoded values.

### 7. User Feedback Summary
The most significant user pain point identified is the **incomplete response bug** with local Ollama models (Issue #952). This suggests that while NullClaw supports local models, the integration with Ollama may lack proper response streaming or truncation handling. Users running local agents expect complete, coherent outputs, and this bug undermines trust in the agent’s reliability. There is no positive or negative feedback visible in the current dataset.

### 8. Backlog Watch
There are no long-unanswered issues or PRs currently requiring maintainer attention. The oldest open items are the three PRs from June 10–12, which are still pending review or merge. The project maintainer should prioritize reviewing **PR #951** and **PR #953** to close out critical stability fixes, and triage **Issue #952** promptly to assess if it is a configuration issue or an underlying bug in the Ollama adapter.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-06-13

## Today's Overview

IronClaw is in a period of **high-intensity development**, with 48 issues and 50 PRs updated in the last 24 hours — nearly double the usual daily volume. The project is actively shipping Reborn (Engine V2) features, with **17 merged/closed PRs today** and a strong focus on thread lifecycle management, Slack integration, and attachment support. The team is iterating rapidly on the DeferredBusy message drain system (now pivoting to a simpler "reject-with-notice" approach), while also clearing a backlog of UX bugs from last week's Reborn WebUI v2 rollout. CI reliability and security advisories are receiving attention. No new releases were cut today.

---

## Releases

**None.** No new releases were published today. The last release candidate (PR #3708, `ironclaw_common` 0.5.0, `ironclaw` 0.29.1) remains open with API-breaking changes and has been pending since May 16.

---

## Project Progress

**17 PRs merged/closed today**, spanning multiple workstreams:

### DeferredBusy / Thread Lifecycle (Closed)
- **#4833** — Filesystem backend: per-thread DeferredBusy index to avoid full transcript scans
- **#4832** — Batch drained DeferredBusy messages into a single run
- **#4831** — Route DeferredBusy drain resubmission through a product_workflow replay entry point
- **#4812** — Drain DeferredBusy messages when the blocking run reaches terminal state *(replaced by #4838 today)*

### Security / Hooks (Closed)
- **#4562** — Record auth continuation dispatch failures
- **#4568** — Bound before-capability dispatch fan-out
- **#4569** — Enforce aggregate tenant predicate key caps

### Testing & CI (Closed)
- **#4773** — Record/replay machinery for QA-phrase traces on the Reborn runtime
- **#4829** — Retire dormant reborn-integration workflow, add Reborn suites to nightly deep CI

### UX Bugfixes (Closed — 10 issues from last week)
- **#4733** — Clicking response links navigates away from active conversation *(fixed)*
- **#4722** — Conversation messages missing user/assistant identity *(fixed)*
- **#4721** — Sidebar "PINNED" section represents active conversation instead of pinned *(fixed)*
- **#4719** — Conversation content area flickers *(fixed)*
- **#4725** — Composer remains interactive while in Working state *(fixed)*
- **#4720** — Attachment warning persists across conversations *(fixed)*
- **#4724** — Unsent draft lost when leaving New Conversation *(fixed)*
- **#4705** — NEAR AI SSO setup fails in local environment *(fixed)*
- **#4706** — Authorization flows do not recover after failed/cancelled sign-in *(fixed)*
- **#4673** — NEAR AI provider configuration cannot be saved *(fixed)*
- **#4703** — NEAR AI model picker saves display name instead of model ID *(fixed)*
- **#4770** — Tool activity may stop updating after refresh (possible SSE reconnect) *(fixed)*

### Open PRs Advancing Today
- **#4738** (attachment web UX) — continues progress on the attachment ecosystem
- **#4777** (Slack connected state persistence) — fixes Slack reconnect loop
- **#4838** (gate-open feedback, replacing #4812) — new simpler approach to busy threads
- **#4836** (runtime-context slice for channels/delivery state) — implements #4828
- **#4835** (persist "always allow" across threads) — fixes #4825

---

## Community Hot Topics

### Most Discussed Issues

| Issue | Title | Comments | Context |
|-------|-------|----------|---------|
| [#4817](https://github.com/nearai/ironclaw/issues/4817) | DeferredBusy drain follow-ups | 3 | Tracks three deferred design decisions after #4812: architecture of drain submission doorway, stale-intent policy (auto-abort vs keep-around), and startup sweep for orphaned intent messages |
| [#4825](https://github.com/nearai/ironclaw/issues/4825) | Persist "always allow" approvals across threads | 3 | High-priority UX need: users answering "always allow" for a capability are re-prompted in every new thread. PR #4835 now fixes this |
| [#4703](https://github.com/nearai/ironclaw/issues/4703) | Model picker saves display name instead of model ID | 3 | Critical data integrity bug — now closed |
| [#4831](https://github.com/nearai/ironclaw/issues/4831) | Route DeferredBusy drain through replay entry point | 2 | Structural review finding: direct TurnCoordinator use bypasses product_workflow entry points — now closed |
| [#4833](https://github.com/nearai/ironclaw/issues/4833) | Per-thread DeferredBusy index | 1 | Performance optimization — closed with implementation |

### Analysis

The most active discussions center on **thread lifecycle and state management** — specifically, what happens when a thread is blocked (busy/gated) and a new message arrives. The community/team is converging on a simpler contract: **reject with explicit notice rather than parking for background resubmission** (PR #4838 replaces #4812). This reflects a design philosophy shift toward immediate, transparent user feedback over complex background machinery.

---

## Bugs & Stability

### Critical
- **#4824** — `cargo-deny` failing repo-wide due to new RUSTSEC advisories against postgres crates (SCRAM iteration DoS, hstore panic, DataRow panic). Blocks all CI. **No fix PR yet — urgent.**

### High Severity (Open)
- **#4762** — Failed tool workflow causes message ordering and activity inconsistencies. Follow-up messages become misattributed. **Open.**
- **#4759** — Workspace path is duplicated when using workspace-relative paths (e.g., `workspace/demo/a.txt` becomes `workspace/workspace/demo/a.txt`). **Open.**
- **#4796** — LLM lacks awareness of current date/time unless explicitly using a time tool. Affects calendar/scheduling workflows. **Open.**
- **#4697** — Active provider status is inconsistent in Inference settings (shows Local Ollama as ACTIVE but actually uses `llama3` from nearai). **Open.**

### High Severity (Closed Today)
- **#4703** — Model picker saves display name instead of model ID (data integrity) — **fixed**
- **#4705, #4706** — SSO and auth flow failures — **fixed**
- **#4673** — NEAR AI provider config cannot be saved — **fixed**
- **#4770** — Tool activity stops updating after refresh (SSE reconnect) — **fixed**

### Medium Severity (Open)
- **#4819** — Attachment warning banner difficult to read in Light theme (low contrast)
- **#4823** — No UI feedback when deleting a running conversation fails
- **#4723** — New conversation composer hover state only highlights top border
- **#4696** — Local Ollama "Test connection" reports success when Ollama is unavailable (false positive)
- **#4822** — Engine V2 LLM usage not tracked in `/api/admin/usage`

---

## Feature Requests & Roadmap Signals

### Advanced/In Progress
- **Attachment ecosystem** (PRs #4738, #4655, #4670, #4668, #4654) — Multi-track effort to land attachment support in Reborn WebChat v2: format registry, byte storage via MountView, transcript AttachmentRefs, web upload UX. Tracks 1-6 of epic #4644 progressing in parallel.
- **Slack as product-adapter extension** (PR #4778) — Moving Slack from hardcoded channel to a host-bundled Reborn extension, enabling lifecycle management and WebUI channel controls.
- **Runtime-context slice for model** (PR #4836) — Telling the model which channels are connected, where delivery points, and run origin — fixing the "model has no ambient knowledge" problem reported by testers.
- **Observability seams** (PR #4588) — Trajectory observer hook + LLM provider injection for external host driving (nearai-bench parity).

### Predicted for Next Release
- **Attachment support in Reborn WebChat v2** — Multiple tracks converging; likely candidate for the next cut
- **Simplified busy-thread UX** — PR #4838 replacing deferred drain with explicit rejection
- **Cross-thread approval persistence** — PR #4835 fixing the "always allow" re-prompt issue
- **Slack channel state persistence** — PR #4777 eliminating reconnect loop
- **CI sharding for faster feedback** — Issue #4813 under discussion

---

## User Feedback Summary

### Pain Points (from last week's UX bug cluster)
- **Conversation identity**: No user/assistant avatars or names in messages
- **Navigation disruption**: Links navigate away from chat (now fixed — target `_blank`)
- **Data loss**: Unsent drafts lost when switching conversations (now fixed)
- **Visual confusion**: "PINNED" section showing active conversation instead of pinned ones (now fixed)
- **Interaction design**: Composer appears interactive during Working state (now fixed)
- **Attachment persistence**: Warning banner carries across conversations (now fixed)
- **SSO/Authorization**: Flows unrecoverable after failure (now fixed)
- **Provider configuration**: NEAR AI setup fails silently (now fixed)

### Emerging Pain Points (reported this week)
- **Thread state transparency**: "Deleting a running conversation gives no feedback" (#4823)
- **Time awareness**: "LLM doesn't know the current date" (#4796)
- **Path handling**: "Workspace path duplicates" (#4759)
- **Tool failure cascade**: "Failed tool breaks message ordering" (#4762)

### Use Case Highlights
- **Multi-thread capability approval**: Users expect "always allow" to be durable across threads (#4825)
- **SSO onboarding flow**: Local environment SSO setup is critical for new developer adoption (#4705)
- **Delivery channel awareness**: Testers need the model to know Slack is connected before asking about delivery (#4828)

---

## Backlog Watch

| Issue | Age | Status | Notes |
|-------|-----|--------|-------|
| [#3708](https://github.com/nearai/ironclaw/pull/3708) | 28 days | **Open PR** | Release cut with breaking changes (`ironclaw_common` 0.4.2→0.5.0). Has 0 comments — appears stalled. |
| [#4561](https://github.com/nearai/ironclaw/pull/4561) | 5 days | **Open PR** | MCP direct-lease denials in SecurityAuditSink. Ready, but not yet merged. |
| [#4588](https://github.com/nearai/ironclaw/pull/4588) | 4 days | **Open PR** | Observability seams (trajectory observer, LLM injection). Important for benchmarking, waiting. |
| [#4654](https://github.com/nearai/ironclaw/pull/4654) | 4 days | **Open PR** | Attachment format registry. First track of the attachment epic, foundational for 5+ other PRs. |
| [#4697](https://github.com/nearai/ironclaw/issues/4697) | 3 days | **Open** | Inconsistent active provider status — no fix PR yet. |
| [#4824](https://github.com/nearai/ironclaw/issues/4824) | 1 day | **Open** | `cargo-deny` failing on all CI — most urgent open item. |

### Attention Required
1. **CI is broken** (#4824) — cargo-deny fails on main and every PR due to new RUSTSEC advisories. This blocks all PR validation and needs immediate resolution (pinning affected crate versions or adding allowlist entries).
2. **Release PR #3708** has been open for 28 days with no activity. The project may benefit from cutting a release with the Reborn WebChat v2 fixes, attachment groundwork, and Slack improvements accumulated over the past month.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **2026-06-13**.

---

## LobsterAI Project Digest — 2026-06-13

### 1. Today’s Overview
The project is in a **high-activity release state**, driven by the merge of the `release/2026.6.11` branch into `main` (PR #2158). **17 pull requests** were updated in the last 24 hours, with **11 closed/merged** and **6 still open**. The primary focus was on stabilizing the **Computer Use MVP**, fixing **cowork voice input** and **media saving bugs**, and defending against data loss in the **cowork UI**. Only **1 issue** was updated (a closed API error from February). No new releases were tagged today, indicating the merge is preparing for a release version `2026.6.12`.

### 2. Releases
**No new releases were published today.**

The latest stable release appears to be `2026.6.11` (per the merge PR #2158). The current activity is preparing the `2026.6.12` release.

### 3. Project Progress (Merged/Closed PRs)
The following key changes were finalized today:

- **Computer Use MVP (PR #2156):** Bumped the managed Computer Use runtime to `1.0.7`, including UIA breadcrumbs for diagnosing helper exits.
- **Release Merge (PR #2158):** Integrated the Computer Use MVP, realtime ASR voice input for cowork prompts, HTML artifact public sharing, and image/SVG artifact sharing support.
- **Media Saving Fix (PR #2157):** Fixed an issue where generated images (PNG) were saved with incorrect file extensions (`.jpg/.jpeg/.webp`). The system now detects the real format from bytes and overrides the server-provided filename.
- **Voice Input Stability (PR #2155):** Fixed a bug that allowed duplicate realtime ASR (speech-to-text) start requests in the cowork flow.
- **Stream Metadata Fix (PR #2154):** Finalized active streaming assistant messages before abort cleanup, preserving model metadata for manually stopped partial replies.
- **Model Selection Fix (PR #2153):** Preserved explicit `lobsterai-server/...` model references during normalization, fixing a bug where same-name package and custom models were not distinguished.

### 4. Community Hot Topics
The most active discussion is a closed issue:

- **Issue #1 (Closed):** [hit API error with OpenAI API Type](https://github.com/netease-youdao/LobsterAI/issues/1)
  - *Author: simson2010* | *Comments: 7* | *Updated: 2026-06-12*
  - **Underlying need:** Users configuring non-OpenAI API keys (e.g., MiniMax) but selecting the "OpenAI message type" encounter a silent `400` error. The key insight is that the API type mismatch is not validated or transformed before sending, leading to a confusing failure where the API test passes but the chat fails. This likely needs a better configuration validation step or automatic protocol detection.

### 5. Bugs & Stability
Two bugs were fixed today, both considered **medium severity**:

1.  **Image Format Extension Mismatch (PR #2157)**
    - **Severity:** High (Data integrity: PNGs saved as .jpg)
    - **Fix:** PR #2157 merged. System now uses byte detection to enforce the correct file extension.

2.  **Duplicate ASR Start on Cowork Voice Input (PR #2155)**
    - **Severity:** Medium (UX: Voice input could start twice, causing overlapping audio capture)
    - **Fix:** PR #2155 merged. Added a guard to prevent duplicate realtime ASR start requests.

**Residual Bugs (Open Stale PRs):**
The following bugs remain unfixed in the backlog (all stale since April 2026):
- **#1446:** OpenClaw gateway infinite restart loop.
- **#1453:** Disabled skills still injected into prompt context.
- **#1454:** "No repeat" scheduled task button unresponsive when date is cleared.

### 6. Feature Requests & Roadmap Signals
- **Computer Use MVP:** The merging of PR #2158 signals that "Computer Use" (likely an agent-controlled desktop automation feature) is graduating from development to general availability in the next release.
- **Artifact Sharing:** Support for HTML public sharing modes and SVG/image artifact sharing is now integrated, suggesting a push towards collaborative artifact delivery.
- **Realtime ASR:** Voice input for cowork prompts is a confirmed feature, likely driven by user requests for faster, hands-free agent interaction.

**Prediction for Next Release (2026.6.12):**
The release will likely include the full **Computer Use** kit, the **new artifact sharing** features, and the **realtime ASR** voice input. Backlog fixes (gateway stability, skill injection) are unlikely to make the cut unless they are blockers.

### 7. User Feedback Summary
- **Pain Point (Configuration):** Issue #1 highlights that API configuration is still fragile. Users are confused when tests pass but actual usage fails due to hidden API type mismatches.
- **Pain Point (Data Loss):** Five PRs (#1473-#1477) were closed today that addressed silent data loss: creating agents, editing agent settings, editing MCP server configs, switching sessions, and re-editing historical messages. This indicates a **long-standing UX regression** where users lose their work due to missing "unsaved changes" warnings.
- **Satisfaction:** The high volume of rapid merges today (11 closed PRs) suggests a maintainer team that is responsive to bugs, which should positively impact user satisfaction once the release reaches users.

### 8. Backlog Watch
The following **stale PRs** have been open since early April 2026 (over 2 months) and require maintainer attention:

| PR # | Title | Stale Since |
| :--- | :--- | :--- |
| [#1446](https://github.com/netease-youdao/LobsterAI/pull/1446) | fix(openclaw): 修复网关反复启动失败导致的无限重启循环 | 2026-04-03 |
| [#1448](https://github.com/netease-youdao/LobsterAI/pull/1448) | fix(i18n): Agent 设置页面删除按钮及技能选择器显示英文 | 2026-04-03 |
| [#1449](https://github.com/netease-youdao/LobsterAI/pull/1449) | feat(cowork): 定时任务多次执行记录折叠分组展示 | 2026-04-03 |
| [#1453](https://github.com/netease-youdao/LobsterAI/pull/1453) | fix(skills): 修复已停用技能仍被注入对话提示词的问题 | 2026-04-03 |
| [#1454](https://github.com/netease-youdao/LobsterAI/pull/1454) | fix(scheduled-tasks): 不重复模式清空日期后点击创建任务按钮无响应 | 2026-04-03 |
| [#1456](https://github.com/netease-youdao/LobsterAI/pull/1456) | fix(shortcuts): 修复快捷键设置缺少重复检测的问题 | 2026-04-03 |

**Risk:** PRs #1453 (skills) and #1446 (gateway restart) represent **high-impact bugs** (functionality broken, app crash) that have been ignored for months. If these affect a significant portion of users, they represent a major risk to user retention.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

Here is the Moltis project digest for **2026-06-13**.

---

## Moltis Project Digest – 2026-06-13

**Project:** Moltis (moltis-org/moltis)  
**Analysis Date:** 2026-06-13  
**Status:** 🟡 Active / Moderate Activity

### 1. Today's Overview
The project saw low but targeted activity over the last 24 hours, with three open issues updated and zero pull request activity or new releases. The level of engagement suggests the maintainers are steady but not currently in a high-velocity push. Two of the three updated issues involve feature requests (Kubernetes sandboxing and local speech-to-text), signaling ongoing expansion into enterprise infrastructure and voice AI. One unclosed bug (Fastmail MCP authorization) remains under discussion. The lack of merged code or new releases today indicates the community is currently in a planning and feedback phase rather than a deployment cycle.

### 2. Releases
**None.**  
No new releases were published. There are no migration notes or breaking changes to report.

### 3. Project Progress
**Merged/Closed PRs today:** **0**  
There were no pull requests updated, merged, or closed in the last 24 hours. Development appears paused or focused on issue triage rather than active code integration.

### 4. Community Hot Topics
The most active issue this period is:

- **[Bug: Fastmail MCP Authorisation (#1115)](https://github.com/moltis-org/moltis/issues/1115)**  
  *Author: kmath313 | 2 comments | Updated 2026-06-12*  
  This bug report details an authorization failure when using the Fastmail MCP (Model Context Protocol). The user has indicated they are on the latest Moltis version and followed the preflight checklist. The discussion likely revolves around OAuth token handling or scope mismatches. This is the only bug currently open, and it remains unresolved.

### 5. Bugs & Stability
**Total open bugs reported/updated today:** **1** (Severity: Medium-High)

- **[#1115: Fastmail MCP Authorisation](https://github.com/moltis-org/moltis/issues/1115)**  
  *Severity: Medium-High*  
  This bug blocks users who rely on Fastmail for email/calendar tool integration within their agent pipelines. No associated fix PR exists yet. The core issue appears to be a frontend-backend auth handshake failure. Maintainer attention is needed to unblock this integration.

**Crashes or regressions:** None reported in the last 24 hours.

### 6. Feature Requests & Roadmap Signals
Two notable feature requests were updated, both with maintainer or community comments:

- **[#1118: Kubernetes-native sandbox backend with runtimeClassName](https://github.com/moltis-org/moltis/issues/1118)**  
  *Author: AzgadAGZ | 1 comment*  
  **Prediction:** High chance of inclusion in next release. This is a major enterprise-grade addition (Kata Containers / gVisor support) that aligns with Moltis’s stated goal of secure agent execution. If the team accepts this, expect a new sandbox backend config option in v0.3 or v0.4.

- **[#1102: Add FunASR/SenseVoice as local STT engine](https://github.com/moltis-org/moltis/issues/1102)**  
  *Author: LauraGPT | 1 comment | Updated 2026-06-12*  
  **Prediction:** Moderate chance. This would dramatically improve voice latency (70ms local recognition). Given Moltis is a voice assistant project, this is a natural fit, but it requires a new backend abstraction for speech engines. Likely a v0.5 target.

### 7. User Feedback Summary
- **Pain Points:** The main friction point is the Fastmail authorization issue (#1115), which breaks a common email automation use case. Frustration is tempered, as the reporter acknowledged the latest version was installed.
- **Use Cases:** The Kubernetes sandbox request (#1118) highlights a real security concern: users want to run untrusted LLM-generated code in isolated environments (Kata/gVisor), not just Docker.
- **Satisfaction:** General satisfaction with the project’s direction is implied by the quality of feature requests (e.g., local STT). No negative sentiment toward the maintainers was observed.

### 8. Backlog Watch
No issues or PRs older than 7 days were updated today other than #1102 (created 2026-06-04). This item is now **9 days old**:

- **[#1102: Add FunASR/SenseVoice as local STT engine](https://github.com/moltis-org/moltis/issues/1102)**  
  *Age: 9 days | Comments: 1 | Maintainer: No response yet*  
  **Watch status: 🟡** This is a high-value feature from a credible contributor. The lack of maintainer response may cause the author to lose momentum. A preliminary acknowledgement or request for design details is recommended soon.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Here is the CoPaw project digest for June 13, 2026.

---

## CoPaw Project Digest: 2026-06-13

### 1. Today's Overview
CoPaw is experiencing high activity, with 24 PRs and 21 issues updated in the last 24 hours, signaling a rapid development cycle as the team prepares for the next release. The project is in a transitional phase, actively addressing a wave of bug reports from the `v1.1.11` and `v1.1.11.post2` releases while simultaneously working on major architectural upgrades. A significant effort is underway to finalize version `1.1.12b1`, with release-related commits merged today. Community engagement is strong, with users reporting regressions and requesting new channel integrations, but the high volume of open issues suggests the team is balancing swift bug fixes with longer-term feature work.

### 2. Releases
No new releases were published today. However, two release preparation PRs were merged:
- **[PR #5159](https://github.com/agentscope-ai/CoPaw/pull/5159) (CLOSED):** Switched the version string to `1.1.12b1`.
- **[PR #5157](https://github.com/agentscope-ai/CoPaw/pull/5157) (CLOSED):** Aligned the package version for the next beta build cycle. These indicate that a `v1.1.12` beta is imminent.

### 3. Project Progress
Today saw 11 PRs merged, indicating progress across several areas:
- **Memory & Configuration:** **[PR #5144](https://github.com/agentscope-ai/CoPaw/pull/5144)** fixed a critical bug where memory and vector model configurations were lost when saving without expanding the relevant UI panels.
- **UI & UX:** **[PR #5147](https://github.com/agentscope-ai/CoPaw/pull/5147)** fixed session redirection bugs in Coding Mode. **[PR #5154](https://github.com/agentscope-ai/CoPaw/pull/5154)** corrected the display of memory search results (fixing Issue #5098).
- **Release Engineering:** A new **Release Verification Gate** was introduced ([PR #5121](https://github.com/agentscope-ai/CoPaw/pull/5121)) to automate end-to-end health checks before publishing to PyPI/DockerHub, improving release stability.
- **Desktop Stability:** **[PR #4144](https://github.com/agentscope-ai/CoPaw/pull/4144)** fixed a readiness check bug when the desktop app binds to the wildcard IP address `0.0.0.0`.
- **Safety & Security:** **[PR #5022](https://github.com/agentscope-ai/CoPaw/pull/5022)** added validation to prevent agent workspaces from being placed within critical QwenPaw-managed directories.

### 4. Community Hot Topics
The most active discussions reveal key user concerns:
- **Backend Architecture Migration (Issue #4727):** The proposal to migrate to AgentScope 2.0 is a high-stakes topic with 10 comments. Users are eager for the upgrade, as seen in Issue #[5149](https://github.com/agentscope-ai/CoPaw/issues/5149): "When can we upgrade to agentscope 2.0?". This is the most significant roadmap signal.
- **Timed Task Reliability (Issue #5064):** A critical bug where Agent-created scheduled tasks fail to trigger has garnered 11 comments. This speaks to core agent autonomy and reliability.
- **File Download Regression (Issue #5140):** A user reports that the fix for plain text downloads in `v1.1.11.post2` introduced a new regression where `docx/pdf` downloads now fail with a 404 error. This highlights the fragility of point fixes.
- **Kimi Integration (Issue #5156):** A user requests support for `kimi-for-coding` API, citing a "pain point" for users who have paid for the Kimi coding subscription but cannot use it within CoPaw. This is a clear demand for a specific vendor's paid service.

### 5. Bugs & Stability
A high number of bugs were reported, with several regressions. Severity levels are estimated:
- **Critical:**
    - **Long Conversation Freeze (Issue #5161):** CoPaw stops responding after long conversations. No fix PR linked, indicating a potential core memory or context window issue.
    - **Automatic Crash/Restart (Issue #5155):** Docker instance crashes and restarts unpredictably on `v1.1.11` (environment: Ubuntu 22.04).
- **High:**
    - **Gemini Tool Calling Regression (Issue #5163):** A confirmed regression between `v1.1.10` and `v1.1.11.post2` where Gemini's tool calling is broken. This is a major regression for a key LLM provider.
    - **Coding Mode Session Loss (Issue #5142):** Session is lost upon page refresh in Coding Mode. A fix was merged in PR #5147.
    - **Memory/Vision Config Loss (Issue #5137):** UI configuration loss when saving without expanding panels. A fix was merged in PR #5144.
- **Medium:**
    - **V1.1.11.post2 File Download Error (Issue #5140):** `docx/pdf` downloads return a 404 error.
    - **Math Formula Rendering (Issues #5148, #5143):** Square root symbols render incorrectly in the web UI.
    - **Python 3.13 Compatibility (Issue #5166):** Plugin installation fails due to a missing deprecated `imghdr` module.

### 6. Feature Requests & Roadmap Signals
Users are requesting several enhancements that signal the project's direction:
- **Multi-Agent Swarm Collaboration (Issue #5139):** A request to add native agent team/swarm capabilities, comparing the feature to that of competitors. This is a complex feature that could be a major milestone for future versions.
- **Desktop System Integration (Issue #5164):** Users want a proper system tray, auto-start, and background service management for the desktop app, indicating a desire for more professional, desktop-native behavior.
- **New Channel Support:**
    - **Slack (Issue #5152):** A request for a native Slack channel.
    - **Kimi for Coding (Issue #5156):** Request to whitelist the `kimi-for-coding` API.
- **Infrastructure:** PR #[4900](https://github.com/agentscope-ai/CoPaw/pull/4900) to decouple plugin loader initialization, and PR #[5067](https://github.com/agentscope-ai/CoPaw/pull/5067) to introduce an "Agent OS Driver" abstraction for MCP/A2A/ACP protocols, suggest the next version (1.1.12) will focus on a more robust and extensible plugin and external capability framework.

### 7. User Feedback Summary
- **Positive:** Users appreciate the team's responsiveness, noting the quick fix for plain text downloads in the previous version. The work on memory and session is visible and being tested.
- **Negative:** The `v1.1.11` series is causing significant frustration due to regressions, particularly with file downloads (Issue #5140) and Gemini tool calling (Issue #5163). Users are experiencing random crashes and freezes, which severely impacts trust.
- **Pain Points:** The "pain point" described in Issue #5156 regarding the inability to use a paid Kimi subscription summarizes a key user desire for value-preserving integrations. The repeated issues with session loss and configuration not saving are creating friction in daily workflows.
- **Demand:** There is clear demand for the AgentScope 2.0 migration, with users explicitly asking about the timeline.

### 8. Backlog Watch
The following items require maintainer attention:
- **High Priority:**
    - **[Issue #4727](https://github.com/agentscope-ai/CoPaw/issues/4727):** The AgentScope 2.0 migration. While an open plan, the community needs a status update or timeline.
    - **[Issue #5064](https://github.com/agentscope-ai/CoPaw/issues/5064):** The timed task bug. This is a core reliability issue with 11 comments and no assigned PR.
- **Medium Priority:**
    - **[Issue #5161](https://github.com/agentscope-ai/CoPaw/issues/5161):** The long-conversation freeze. This is a serious stability bug with no resolution path visible.
    - **[PR #4622](https://github.com/agentscope-ai/CoPaw/pull/4622):** The DataPaw data-analysis plugin. This PR has been open since late May and is a significant feature addition that appears to be stalled under review.
    - **[PR #4900](https://github.com/agentscope-ai/CoPaw/pull/4900):** The plugin loader decoupling fix. This is a critical fix for PyInstaller/Tauri environments that has been open since June 2.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-06-13

## Today's Overview

ZeroClaw is experiencing a significant surge in development activity, with **37 pull requests** updated in the last 24 hours (32 open, 5 merged/closed) and **11 issues** updated (10 open, 1 closed). This represents one of the highest activity days in recent history, suggesting an intensifying push toward the upcoming v0.8.1 release. The project shows strong momentum across bug fixes, infrastructure improvements, and community-driven feature requests, though the high volume of open PRs (32) indicates a growing review bottleneck that maintainers will need to address. No new releases were published today.

## Releases

No new releases were published today. The last release remains v0.8.x (earlier), with the v0.8.1 release cycle actively tracked in issue #6970.

## Project Progress

**5 PRs were merged or closed today:**
- **#7548** — `Chore/01.5 cargo cleanup` (merged): A massive dependency cleanup touching nearly every subsystem (CI, docs, all providers, channels, tools, runtime). This is a significant maintenance win, streamlining the dependency tree across the entire project.
- **#7504** — `fix(openai): honor config timeout_secs instead of hardcoding 120s` (closed): Fixes the long-standing issue #6723 where the native OpenAI provider ignored user-configured timeout settings.
- **#7447** — `fix(providers): wire timeout_secs config into native OpenAI provider (#6723)` (closed): A parallel fix for the same issue, indicating multiple contributors independently addressed this pain point.
- Two other PRs closed without detailed description data.

**Key features that advanced today (still open):**
- **#7429** — WASM plugins infrastructure: Added wasmtime dependency for eventual Extism deprecation (high-risk, large change)
- **#7549** — Plugin path alignment: Fixes mismatch between CLI install paths and runtime scan paths, making CLI-installed WASM plugins actually visible
- **#7424** — Web fetch wildcard fix: `allowed_private_hosts = ["*"]` now correctly covers DNS-resolved private hosts
- **#7351** — MCP auto-reconnect: Remote MCP servers that restart no longer permanently break tool calls
- **#7522** — Binary file rejection in `file_read`: Stops returning mojibake for binary/image files

## Community Hot Topics

**Most Active Discussions:**

| Issue/PR | Comments | Focus |
|----------|----------|-------|
| **#7415** — RFC: Unify the three agent turn engines | 3 comments | Architecture RFC — already implemented as a single consolidation PR (#7540). This is a **major architectural change** merging `run_tool_call_loop`, `turn_streamed`, and `Agent::turn` into one unified engine. |

**Analysis:** The unification of agent turn engines (#7415) is the single most impactful architectural discussion this week. A maintainer has already directed and executed this as a single consolidation PR, suggesting this will land in v0.8.1 or v0.9.0. This fundamentally changes how agents process turns, which will affect every user and downstream tool.

## Bugs & Stability

**S1 - Workflow Blocked (Critical):**

| Issue | Component | Description | Fix PR? |
|-------|-----------|-------------|---------|
| **#7542** | Gateway/API | `ask_user` fails instantly with "Channel closed before receiving a response" in WebSocket sessions | ✅ **#7551** (opened today) |
| **#7537** | Runtime/Daemon | Windows 10 quickstart fails: "no map-keyed/list section at peer-groups" — blocks new user onboarding | ❌ No fix PR yet |
| **#7533** | Docker | Docker build fails during `cargo web build` due to missing `c++` compiler | ✅ **#7534** (opened today) |
| **#7527** | Runtime/Daemon | macOS app unresponsive after install, cannot detect granted permissions, window disappears | ❌ No fix PR yet |

**S2 - Degraded Behavior:**

| Issue | Component | Description | Fix PR? |
|-------|-----------|-------------|---------|
| **#7541** | Gateway/API | V3 legacy paths: gateway WS chat uses `data_dir` as agent workspace_dir instead of proper workspace path | ❌ No fix PR yet |

**Notable:** Two S1 bugs (#7542 and #7533) already have fix PRs opened the same day they were reported, demonstrating responsive maintainer engagement with critical issues. However, the macOS app (#7527) and Windows quickstart (#7537) blockers remain unaddressed, which is concerning for cross-platform adoption.

## Feature Requests & Roadmap Signals

**New Feature Requests (today):**
- **#7543** — Multi-session support in gateway web chat UI (session sidebar: new/switch/rename/delete). Currently single-session per agent. High-impact UX improvement.
- **#7539** — llama.cpp model router for quick model switching. User finds default model initialization blocking flexibility.
- **#7531** — Streaming card messages for QQ/DingTalk/WeChat/Feishu to reduce user wait time. Important for Chinese IM platform users.

**Prediction for v0.8.1/v0.9.0:**
- The **three-agent-engine unification (#7415)** is already implemented and likely to land in the next release
- **Plugin path alignment (#7549)** and **WASM plugin infrastructure (#7429)** suggest the plugin system overhaul is imminent
- Multi-session web chat (#7543) has high community resonance and is architecturally straightforward

## User Feedback Summary

**Pain Points:**
1. **New user onboarding friction**: Windows (#7537) and macOS (#7527) installation failures are blocking first-time users entirely
2. **Config silently ignored**: The `timeout_secs` issue (#6723, now fixed) eroded user trust — users configured timeouts that were silently ignored
3. **SSE/proxy timeout confusion**: Users hitting the 120s hardcoded timeout didn't know their config was being ignored
4. **Docker build failures (#7533)**: Hobbyists and CI users blocked from self-hosting

**Positive Signals:**
- Multiple independent contributors fixing the same issue (#6723, #7504, #7447) shows strong community ownership
- Feature requests for Chinese IM platforms (QQ, DingTalk, Feishu) indicate growing international user base
- Users are actively testing edge cases (binary files in file_read, MCP reconnection) and reporting bugs clearly

## Backlog Watch

**Issues/PRs Needing Maintainer Attention:**

| Item | Age | Status |
|------|-----|--------|
| **#7245** — `fix(read_skill): cannot load plugin-bundled skills` | 8 days | `needs-author-action` — stalled |
| **#7351** — MCP auto-reconnect | 6 days | `needs-author-action` — high-value fix stalled |
| **#6970** — v0.8.1 integration tracker | 17 days | Open, no recent maintainer update on tracker scope |
| **#6723** — OpenAI timeout (now closed via multiple PRs) | 28 days | ✅ Resolved |

**Concerns:**
- Two high-value PRs (#7245, #7351) are stuck on `needs-author-action` with no updates for 8-6 days. These fix real user-facing bugs (plugin skills not loading, MCP connections permanently dying after restart).
- The v0.8.1 tracker (#6970) has no comments since creation 17 days ago, suggesting it may need a refresh or consolidation with the other open PRs.

**Project Health Assessment:**
- **Activity**: 🟢 Very High (37 PRs, 11 issues in 24h)
- **Bug Resolution Speed**: 🟢 Good (S1 bugs getting same-day fix PRs)
- **Cross-Platform Stability**: 🟡 Concerning (Windows & macOS blockers unaddressed)
- **Review Bottleneck**: 🟡 Warning (32 open PRs, growing)
- **Community Growth**: 🟢 Strong (new contributors, diverse feature requests, international users)

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*