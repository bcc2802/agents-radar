# OpenClaw Ecosystem Digest 2026-06-12

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-12 01:24 UTC

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

# OpenClaw Project Digest — 2026-06-12

## Today's Overview

The OpenClaw project continues at high community velocity, with **500 issues** and **500 PRs** updated in the last 24 hours. Of the issues, 477 remain open/active and 23 were closed; PR activity shows 391 open and 109 merged/closed, indicating a strong but slightly backlogged development pipeline. No new releases were published today, but the maintainer team and community are actively processing a large volume of bug reports, feature requests, and infrastructure improvements. Security, session-state integrity, and auth-provider concerns dominate the high-priority issue landscape, while the PR queue shows steady progress on cron fixes, Docker bundling, and memory reliability. The project's labeling taxonomy (e.g., `clawsweeper`, `impact:security`, `issue-rating`) reflects a mature triage system, though many items still await maintainer review or product decisions.

## Releases

**No new releases today.** The last known version in issue reports is `2026.3.8` for CLI and `2026.3.7` / `2026.3.2` for the gateway; users reference version `2026.6.5` in a catalog-upgrade context. Release cadence appears steady but no formal changelog update was captured for this period.

## Project Progress

**109 PRs were merged or closed today**, indicating active development. Notable merged/closed items from the recent window include:

- **#91330 (CLOSED):** Fix for current-session message-tool replies being replaced by private bookkeeping finals — a critical message-delivery bug.
- **#56263 (CLOSED):** Configurable file permissions for multi-user setups (`chmod 0o640`/`0o750`), addressing Docker/container group-read issues.
- **#92284 (OPEN, recent fix):** Queue race-condition stall fix — `enqueue-followup` now kicks a drain on enqueue to prevent stalls when inbound messages arrive during a terminal run window.
- **#92304 / #92295 (OPEN):** Two independent fixes for cron edit stripping `tz` and `staggerMs` — a clear community-driven quality-of-life improvement.
- **#92300 (OPEN):** OpenAI Responses cumulative message snapshot collapse — reduces token overhead and duplicate outputs.
- **#92298 (OPEN):** Isolates `CODEX_HOME` per `authProfileId` to prevent cross-account state leakage in the Codex extension.

Multiple PRs address the `clawsweeper:fix-shape-clear` and `clawsweeper:queueable-fix` labels, suggesting the project is actively grooming its fix queue.

## Community Hot Topics

### Most Active Issues

1. **#75 — Linux/Windows Clawdbot Apps** (109 comments, 79 👍)
   - *URL: [Issue #75](https://github.com/openclaw/openclaw/issues/75)*
   - Users strongly desire parity with the macOS/iOS/Android apps. This long-standing issue (created Jan 2026) remains the top-voted community request. The need for full-platform coverage is a recurring theme across multiple issues.

2. **#9443 — Prebuilt Android APK releases** (25 comments)
   - *URL: [Issue #9443](https://github.com/openclaw/openclaw/issues/9443)*
   - Submitted via AI assistant QING on behalf of user Lysen. Users want precompiled APKs rather than building from source. Signals frustration with the developer-centric release process.

3. **#32473 — Control UI requires HTTPS/localhost** (17 comments, 5 👍)
   - *URL: [Issue #32473](https://github.com/openclaw/openclaw/issues/32473)*
   - A regression affecting VPS/Docker users — the control UI demands a secure context after a Brave key configuration change.

4. **#22438 — Tiered bootstrap file loading** (17 comments)
   - *URL: [Issue #22438](https://github.com/openclaw/openclaw/issues/22438)*
   - A proposal to reduce LLM token waste by loading only relevant bootstrap files per session. Linked PR #22439 exists but remains open — users want this for cost savings.

5. **#22676 — Signal daemon race condition on SIGUSR1** (17 comments)
   - *URL: [Issue #22676](https://github.com/openclaw/openclaw/issues/22676)*
   - A P1 crash-loop and message-loss bug during gateway restarts — orphaned processes and port conflicts cause cascading failures.

### Underlying Community Needs
- **Cross-platform parity** dominates (#75, #9443) — desktop and mobile users want the same experience.
- **Cost optimization** (#22438, #14785 tool schema overhead) — token-efficiency is a top user concern.
- **Reliability under load** (#22676, #85888 cron failures, #32296 session confusion) — the community is hitting hard stability limits in production-like usage.
- **Security-by-default** (#10659 masked secrets, #32473 HTTPS requirement) — users want both protection and control.

## Bugs & Stability

### Critical / P1 Severity

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| **#22676** | Signal daemon `stop()` race on SIGUSR1 — orphaned processes, send failures, crash-loop | PRs exist but not linked as closers |
| **#32296** | Agent replies to previous message instead of current — session context confusion | No fix PR linked |
| **#29387** | Bootstrap files in `agentDir` silently ignored — only workspace loads | No fix PR; needs maintainer review |
| **#31583** | `exec` tool does not inherit `skills.entries.*.env` env vars — secrets not passed | Linked PR open (#?) |
| **#38327** | "Cannot convert undefined or null to object" with Google Vertex/Gemini 3.1 — regression in 2026.3.2 | No fix PR linked |
| **#69118** | Claude CLI sessions reset every turn in group channels — `extraSystemPromptHash` drift companion to #64386 | No fix PR |
| **#91363** | Isolated cron consistently fails "LLM request failed" — model never reached, regardless of timeout | No fix PR |
| **#40611** | Heartbeat drift fix (PR #39182) causes aggressive retry that blocks Telegram during active conversations | PR #39182 merged, side-effect reported |
| **#40001** | Write tool lacks append mode — isolated cron sessions overwrite shared files, causing data loss | No fix PR |
| **#43367** | Multi-agent orchestration unstable — concurrent `agents add` overwrites, session-lock failures, detached child work | No fix PR; needs maintainer review |
| **#39476** | A2A `sessions_send` target can call back, causing duplicate messages | No fix PR |
| **#29736** | Exec approvals path ignores active state root, writes to `~/.openclaw` | No fix PR |
| **#31331** | Docker Install + Sandbox — `/workspace` can't bind; uses internal Docker paths | No fix PR |
| **#37634** | Sandbox `workspaceAccess: none` gives read-only isolated workspace — tools that need to write fail | No fix PR |
| **#40540** | `openclaw update` fails with `EBUSY` on Windows — process holds the binary | No fix PR |
| **#41165** | Telegram DMs land in `agent:main:main` instead of isolated session after #40519 | Linked PR open |
| **#40440** | Telegram group media loses metadata (only placeholder preserved) | No fix PR |

### Summary of Stability Themes
- **Session state corruption** is the #1 pattern: multiple bugs involve context drift, message misrouting, and agent-to-agent duplication (#32296, #32296, #69118, #39476, #41165).
- **Cron job reliability** is fragile: #85888 (MiniMax overload window), #91363 (LLM request never starts), #40001 (write-tool data loss) all point to insufficient isolation and retry logic.
- **Security boundary issues** persist: #31583 (env vars not passed), #29736 (state root ignored), #31331 (Docker sandbox mount) — these are both stability and security concerns.

## Feature Requests & Roadmap Signals

### Strong Community Demand (Likely Next Version)

| Issue | Feature | Comments | 👍 |
|-------|---------|----------|----|
| **#75** | Linux/Windows Clawdbot Apps | 109 | 79 |
| **#9443** | Prebuilt Android APK releases | 25 | 2 |
| **#10659** | Masked Secrets — prevent agent from accessing raw API keys | 13 | 4 |
| **#39604** | `tools.web.fetch.allowPrivateNetwork` for internal network access | 13 | 9 |
| **#22438** | Tiered bootstrap file loading for progressive context control | 17 | 0 |
| **#14785** | Reduce tool schema token overhead (~3,500 tok/session) | 7 | 0 |
| **#7722** | Filesystem Sandboxing Config (`tools.fileAccess`) | 7 | 4 |
| **#6615** | Denylist support for exec-approvals | 7 | 7 |
| **#20786** | Telegram Business Bot support (business_message/business_connection) | 8 | 6 |
| **#13616** | Backup/restore utility for config, cron, session history | 8 | 0 |
| **#13610** | Native secrets management (AWS Secrets Manager, Vault) | 7 | 1 |
| **#35203** | Multi-Agent Collaboration: Capability Profiling + Shared Blackboard + Layered Memory + Token Cost Governance | 8 | 0 |
| **#40418** | Automated Session Memory Preservation & Synthesis | 7 | 1 |
| **#40786** | `.gitignore`-like exclude patterns for backup CLI | 7 | 1 |
| **#41366** | Durable natural-language rule learning + explicit multi-mention reply semantics | 7 | 1 |

### Prediction for Next Version
- **Tiered bootstrap loading** (PR #22439) and **tool schema token reduction** have working PRs — both likely to land soon.
- **Exec approvals denylist** (#6615) and **filesystem sandboxing** (#7722) are high-value security features with strong community backing.
- **Prebuilt APK** (#9443) may hit a faster track given the volume of mobile-user requests, but requires build-infrastructure investment.
- The **Security Matrix runtime-fact audit model** (PR #92086, size XL) is a major architectural addition that could reshape the security posture in the next release.

### Roadmap Signals from PRs
- **CoreWeave Serverless Inference provider** (PR #92243) — new model provider support.
- **Tool search directory mode** (PR #91632) — reduces prompt overhead.
- **Codex final answer candidates in activity view** (PR #90610) — deeper Codex integration.
- **Revamped command authorization** (PR #84172) — Tree-sitter-backed planning for exec control.

## User Feedback Summary

### Expressed Pain Points

1. **"My cron jobs fail at 5 AM for no reason"** — Multiple users (#85888, #91363) report cron failures that are time-dependent and inconsistent with manual triggers. This suggests a botched scheduling/retry mechanism specific to isolated executors.

2. **"I can't update OpenClaw on Windows"** — #40540: `openclaw update` throws `EBUSY` because the running process holds the binary. This is a fundamental platform gap.

3. **"My agent talks to the wrong message"** — #32296: session context confusion. Users report "the agent responds to content from previous messages," which breaks trust in the conversation.

4. **"I can't run multi-agent workflows without losing state"** — #43367 and #39476: concurrent agent operations lead to config overwrites, detached child processes, and duplicate message delivery.

5. **"Docker users can't use the sandbox properly"** — #31331: workspace bind mounts fail because the gateway sees internal Docker paths instead of host paths.

6. **"I need to block specific dangerous commands, not just allow safe ones"** — #6615: exec-approvals need a denylist to support "allow all except X" policies.

7. **"My Telegram media disappears"** — #40440: images sent without @mention lose their file metadata, only placeholder text remains.

### Positive Signals
- High issue engagement (109 comments on #75) shows a motivated, vocal user base.
- The `clawsweeper` label system and `rating` taxonomy demonstrate mature project governance.
- Multiple users are building orchestration workflows (#43367, #39476) — advanced usage indicates a product that supports real productivity.

### Satisfaction Indicators
- Users are deploying OpenClaw in production-like setups (VPS, Docker, cron, multi-agent) — a strong signal of trust.
- The community submits well-structured bug reports with root cause analysis and PRs attached — suggests a healthy contributor ecosystem.

## Backlog Watch

### Critical Issues Lacking Maintainer Action

| Issue | Created | Last Update | Comments | Impact |
|-------|---------|-------------|----------|--------|
| **#75** — Linux/Windows Clawdbot Apps | 2026-01-01 | 2026-06-11 | 109 | Platform parity — largest blocker for Windows/Linux users |
| **#10659** — Masked Secrets | 2026-02-06 | 2026-06-11 | 13 | Security — prevents API key leaks |
| **#20786** — Telegram Business Bot | 2026-02-19 | 2026-06-11 | 8 | Feature gap for Telegram enterprise users |
| **#22438** — Tiered bootstrap loading | 2026-02-21 | 2026-06-11 | 17 | Cost optimization — has PR #22439 stalled since Feb |
| **#29387** — Bootstrap files in `agentDir` ignored | 2026-02-28 | 2026-06-11 | 14 | P1 regression — per-agent bootstrap broken |
| **#31583** — `exec` tool env var inheritance | 2026-03-02 | 2026-06-11 | 12 | P1 regression — secrets not passed |
| **#32296** — Session context confusion | 2026-03-02 | 2026-06-11 | 15 | P1 usability — agent replies to wrong message |
| **#37634** — Sandbox workspace read-only | 2026-03-06 | 2026-06-11 | 9 | P1 security boundary — `none` workspace not writable |
| **#43367** — Multi-agent orchestration unstable | 2026-03-11 | 2026-06-11 | 10 | P1 reliability — concurrent agent operations broken |
| **#91363** — Isolated cron never reaches provider | 2026-06-08 | 2026-06-11 | 6 | P1 blocking — cron jobs completely fail |

### Stale High-Impact Issues (marked `stale`)

| Issue | Summary | Impact |
|-------|---------|--------|
| **#57901** | Safeguard compaction ignores `compaction.model` config — uses session model instead | Session-state, auth-provider |
| **#57326** | CLI-backed helper paths still bypass CLI dispatch on latest `main` | Session-state, security, auth-provider |
| **#31583** | `exec` tool env var inheritance (also above) | Security, auth-provider |
| **#41165** | Telegram DMs land in wrong session | Session-state, message-loss |
| **#40418** | Automated Session Memory Preservation | Session-state, security |
| **#37966** | `cacheRetention` ignored for LiteLLM-proxied Anthropic models | Auth-provider |

### Notes for Maintainers
- **Issue #75** (109 comments, 79 👍) has not seen maintainer-comment activity in months — this is the single highest-traffic issue and a potential community churn risk.
- **Multiple P1 regression bugs** (#29387, #31583, #38327) from February/March remain open without fix PRs — users may be experiencing these in production.
- **PR #22439** (tiered bootstrap) was created alongside issue #22438 but has not been merged — it addresses a well-understood token-waste problem and could be a quick win.
- The `clawsweeper:needs-maintainer-review` and `clawsweeper:needs-product-decision` labels are applied to a large fraction of high-impact items — these could benefit from batch triage sessions.

---

*Digest generated from OpenClaw GitHub data (openclaw/openclaw) for 2026-06-12. All links refer to openclaw/openclaw Issue/PR numbers.*

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided digest summaries.

## Cross-Project Comparison Report: Personal AI Agent OSS Ecosystem

### 1. Ecosystem Overview

The open-source personal AI agent ecosystem is in a high-velocity expansion phase, characterized by a rapid build-out of core infrastructure (multi-agent orchestration, MCP integration, security boundaries) and significant platform maturation challenges (desktop client stability, cross-platform parity, and credential management). A clear bifurcation is emerging: projects like **OpenClaw** and **ZeroClaw** are prioritizing architectural complexity and production-grade features (custom executors, multi-agent delegation, security matrices), while others like **Hermes Agent** and **CoPaw** are racing to stabilize new desktop clients and user interfaces. Underlying all this is a consistent community demand for token efficiency, local model support, and reliable cross-platform experiences, signaling a shift from "can it work?" to "can it work reliably in my real-world workflow?".

### 2. Activity Comparison

| Project | Issues Updated (Open/Total) | PRs Updated (Open/Total) | Releases (24h) | Health Score (1-5) |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 (477 open) | 500 (391 open) | 0 | 3 (Strong throughput, heavy backlog) |
| **ZeroClaw** | 50 (50 open) | 48 (48 open) | 1 (v0.8.0) | 3 (Major release, high severity bugs) |
| **IronClaw** | 31 (18 open) | 47 (22 open) | 0 | 4 (High velocity, focused on Reborn prod) |
| **CoPaw** | 31 (29 open) | 40 (21 open) | 2 (patches) | 3 (High activity, stabilization phase) |
| **LobsterAI** | 2 (stable) | 19 (1 open) | 0 | 4 (Massive feature merge, clean backlog) |
| **Hermes Agent** | 50 (50 open) | 50 (48 open) | 0 | 3 (Very high activity, many new bugs) |
| **PicoClaw** | 6 (3 open) | 31 (13 open) | 1 (nightly) | 4 (Steady maintenance, security focus) |
| **NanoClaw** | 3 (1 open) | 16 (7 open) | 0 | 4 (Rapid fix cycle, strong contributor) |
| **NanoBot** | 4 (2 open) | 18 (12 open) | 0 | 4 (Active development, moderate backlog) |
| **NullClaw** | 1 | 0 | 0 | 2 (Minimal activity, single reported bug) |
| **Moltis** | 1 | 1 | 0 | 2 (Quiet maintenance, single bug/PR) |
| **TinyClaw** | 0 | 0 | 0 | 1 (No activity) |
| **ZeptoClaw** | 0 | 0 | 0 | 1 (No activity) |

*Note: Health score is an analyst estimate based on throughput, release cadence, bug severity, and backlog management.*

### 3. OpenClaw’s Position

**Advantages:**
- **Scale:** By far the largest community velocity (500 issues/PRs), acting as the ecosystem's core reference implementation.
- **Maturity:** "Clawsweeper" triage system, a `Security Matrix` runtime fact-audit model (PR #92086), and a broadest set of integrations signal production readiness.
- **Feature Depth:** Sessions, cron, multi-agent orchestration, and a rich ecosystem of `claw` extensions (Codex, A2A).

**Technical Approach Differences:**
- **Security by Design:** The `Security Matrix` model is unique—a runtime fact-audit system for managing tool access, not just a config filter.
- **Custom Executors:** Isolated cron executors and `exec` tools are first-class, not just MCP bridges, providing more granular control and isolation.
- **Monorepo + Extensions:** An integrated core (`openclaw/openclaw`) with a large in-house extension ecosystem (Codex, A2A).

**Community Size Comparison:**
- OpenClaw dwarfs all others in raw activity. ZeroClaw and Hermes Agent are the next most active by issue/PR count, each at ~10% of OpenClaw's volume. This signals OpenClaw as the primary community hub for general-purpose agent development.

### 4. Shared Technical Focus Areas

The following needs are emerging *independently* across multiple projects, confirming them as critical for the ecosystem:

| Focus Area | Projects Reporting | Specific Needs |
| :--- | :--- | :--- |
| **Multi-Agent Orchestration** | OpenClaw, ZeroClaw, LobsterAI, PicoClaw, CoPaw | Session/state isolation, agent collaboration buses (PicoClaw PR #2937), delegate orchestration (ZeroClaw #7470). |
| **MCP (Model Context Protocol) Reliability** | Hermes Agent, ZeroClaw, PicoClaw, Moltis | Tool filtering not applied (ZeroClaw #6699, Hermes #38945), reconnection crashes (NanoBot #4302), auth failures (Moltis #1115). |
| **Cross-Platform Desktop Parity** | OpenClaw, Hermes Agent, CoPaw, PicoClaw | Windows/Linux App (OpenClaw #75), Windows updates (Hermes #40540), path separator bugs (PicoClaw #2472), Tauri client bugs (CoPaw #5106). |
| **Local Model & Provider Integration** | NullClaw, CoPaw, OpenClaw, ZeroClaw, IronClaw | Ollama response truncation (NullClaw #952), vLLM regressions (CoPaw #4989), egress lockdown blocking local services (NanoClaw #2731). |
| **Security & Secret Management** | OpenClaw, ZeroClaw, CoPaw, NanoClaw | Masked secrets (OpenClaw #10659), exec approvals denylist (OpenClaw #6615), tool-level security policies (ZeroClaw #6914). |
| **Token & Cost Optimization** | OpenClaw, LobsterAI, CoPaw, ZeroClaw | Tiered bootstrap loading (OpenClaw #22438), duplicate output waste (LobsterAI #2121), context budget mismatches (ZeroClaw #5808). |
| **Cron / Scheduled Jobs** | OpenClaw, ZeroClaw, CoPaw, Hermes Agent | Cron job failures (OpenClaw #91363), repeated execution (ZeroClaw #6037), unscheduled triggers (CoPaw #5064). |

### 5. Differentiation Analysis

| Dimension | OpenClaw | ZeroClaw | Hermes Agent | LobsterAI | CoPaw | NanoClaw |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Core Value Prop** | General-purpose agent OS | Multi-agent daemon | Desktop-first AI assistant | Enterprise agent platform | Developer agent (Qwen ecosystem) | Infrastructure-focused agent framework |
| **Target User** | Power users, developers | Multi-agent workflow architects | Desktop/macOS users | Enterprise teams | Developers (Chinese market focus) | Infrastructure engineers |
| **Architecture** | Monorepo + Extensions | "One daemon, many agents" | Desktop client + remote gateway | Cowork + multi-instance | Tauri Desktop + AgentScope 2.0 | Modular, channel-instance |
| **Key Differentiator** | Largest community, `Security Matrix` | v0.8.0 multi-agent delegation | HEIC transcoding, robust desktop | Computer Use (MVP), Gmail triggers | Rebranding to QwenPaw, UI polish | Rapid infrastructure fixes (gavrielc) |
| **Weakness** | Heavy backlog, many stale P1 bugs | v0.8.0 regressions (delegation, Web UI) | Many new critical bugs | Fewer integrations than OpenClaw | Stabilization churn, Tauri crashes | Small community, niche focus |

### 6. Community Momentum & Maturity

**Tier 1: High Velocity / Core Reference**
- **OpenClaw:** The undisputed leader in community size and feature depth. In a "many bugs, many fixes" cycle—high maturity but significant maintenance burden.
- **ZeroClaw:** Major architectural leap with v0.8.0. Momentum is strong, but the high number of stale PRs and regressions suggests the team is stretched thin.

**Tier 2: Rapid Iteration / Stabilizing**
- **IronClaw:** Very focused on Reborn production readiness. High PR merge rate (25/day) and quick bug turnaround.
- **LobsterAI:** The most impressive single-day feature merge (18 PRs). Focused on enterprise features (Computer Use, Real-time ASR).
- **CoPaw:** High activity but in a "hotfix" phase after a major UI overhaul. The v1.1.11 patches show a responsive team.

**Tier 3: Steady State / Feature Building**
- **NanoBot, NanoClaw, PicoClaw:** Active development with a manageable backlog. Good contributor responsiveness (NanoClaw's gavrielc is a standout).
- **Hermes Agent:** High activity but many *new* bugs being opened, suggesting a less stable release than desired. Momentum is there, but quality is a concern.
- **NullClaw, Moltis, TinyClaw, ZeptoClaw:** Maintains a minimal presence. These projects are either very specialized, single-maintainer efforts, or have stalled.

### 7. Trend Signals

For developers and decision-makers in the AI agent space, the following trends are statistically significant:

1.  **Multi-Agent is the New Baseline:** It is no longer a "nice-to-have." Five of the top eight projects are actively building and debugging multi-agent architectures (delegation, collaboration buses, instance isolation). **Impact:** Any single-agent solution will be seen as legacy within 6 months.

2.  **MCP is the Universal Adapter, but it's Fragile:** MCP is the de facto standard for tool integration, but projects are hitting the same reliability walls (auth, reconnection, security filtering). **Impact:** Investment in robust MCP middleware (retry, auth, filtering) is a high-value area.

3.  **Desktop is a Warzone, Not a Fortress:** The race to ship desktop clients (Tauri, Electron, native) is producing many regressions (crashes, SSL errors, broken updates). **Impact:** Users are in an "early adopter" tolerance zone. Reliability, not features, will be the next competitive moat for desktop agents.

4.  **Local Models are a Non-Negotiable Requirement:** The persistent demand for Ollama, vLLM, and local endpoint support, combined with specific bugs (truncation, egress blocking), shows that privacy and offline capabilities are no longer niche. **Impact:** Cloud-only agents will increasingly lose market share to hybrid/local-first architectures.

5.  **Token Waste is a 2026 Crisis:** Users are actively *measuring* and *complaining* about token efficiency. Duplicate output, untiered context loading, and invisible context bloat are top pain points. **Impact:** The next generation of agents will be defined not by raw capability, but by *cost-aware capability*. Projects that optimize for token budgets (tiered loading, compression, context awareness) will win user trust.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot Project Digest — 2026-06-12**

**1. Today's Overview**
NanoBot is in a high-activity phase with **18 PRs updated** in the last 24 hours (12 open) and **4 issues updated** (2 closed). The core team and community contributors are concurrently addressing bugs, developer experience (SDK/Skills), and infrastructure features (cron, MCP, Slack). No new releases were cut today, but the strong PR merge rate (6 merged/closed) indicates a pending release is likely soon. Overall project health is stable with active triage and multiple in-flight improvements.

**2. Releases**
*No new GitHub releases today.*

**3. Project Progress**
Six PRs were merged or closed today, advancing key areas:

- **🛡️ Security/Sandbox** – PR #4236 (closed): *bwrap sandbox fails on Ubuntu 24.04* was resolved, fixing a namespace restriction issue.
- **💬 Slack Channel** – PR #4289 (merged): Added `groupRequireMention` option to the Slack allowlist, enabling bot responses only in whitelisted channels *and* only when @mentioned.
- **⚡ Streaming & Providers** – PR #4020 (merged): Made stream-idle timeout configurable per-provider, solving local LLM streaming interruptions.
- **🔀 Codex Provider** – PR #4021 (open, updated): Fixes duplicate reasoning IDs causing 400 errors (retry logic).
- **📝 Message Handling** – PR #4257 (merged): `split_message` is now fenced-code-block-aware, preventing broken HTML in long messages.
- **🔌 Transcription Provider** – PR #4281 (merged): Added SiliconFlow as a new transcription provider.

**4. Community Hot Topics**

- **Multiple Custom Providers** – Issue #4305 (open, 0 comments, *very new*): User `smurfix` requests a "template" parameter to support multiple custom/OpenAI providers. This has been a long-standing need (see PR #3239 from Apr 2026). High demand, low maintainer engagement so far. 🏷️ [View Issue](https://github.com/HKUDS/nanobot/issues/4305)
- **MCP Gateway Crash After Reconnect** – Issue #4302 (open, 0 comments): Gateway-level crash during MCP session reconnect. A fix PR (#4303) was opened simultaneously by `michaelxer`, showing rapid community response. 🏷️ [View Issue](https://github.com/HKUDS/nanobot/issues/4302)

**5. Bugs & Stability**
Highest-severity bug reported today:

- **Critical: Crash on MCP Reconnect** – Issue #4302: Gateway crashes with `RuntimeError: Attempted to exit cancel scope in a different task` during MCP session reconnect. A fix PR #4303 is already open, tracking generators during close. 🏷️ [View Issue](https://github.com/HKUDS/nanobot/issues/4302)

Lower severity:
- **Cron + Subagent Completion** – PR #4304 (open): Fix PR for cron jobs that complete before spawned subagents finish (non-crash, functional bug).

**6. Feature Requests & Roadmap Signals**
Strong signals for the next version:

- **Multiple Custom Providers** (Issue #4305, PR #3239) – Likely merge candidate; PR #3239 has been open since April. Could land in v0.9.x.
- **Gateway CLI Commands** (PR #3538) – Adds `start`/`stop`/`restart`/`status` for gateway. Open since April. Maintainer review is overdue.
- **Skill Type Requirements** (PR #4300) – New feature to check skill prerequisites. Fresh addition, likely to merge soon.
- **Python SDK Expansion** (PR #4296) – Major upgrade to `RunResult` and runtime controls. Backward-compatible, high value for developers.

**7. User Feedback Summary**

- ✅ **Positive**: Users appreciate version display in WebUI (Issue #4233, closed) and praise the granular Slack channel controls (PR #4289).
- ❌ **Pain Points**: 
  - *Bubblewrap sandbox* on Ubuntu 24.04 (Issue #4236, closed) – user frustration with silent failures and permission errors.
  - *MCP gateway crash* (Issue #4302) – affects production deployments; urgent fix in review.
- 🔁 **Recurring Request**: Multiple custom provider support (Issue #4305, PR #3239) – users need to connect to multiple OpenAI-compatible endpoints without workarounds.

**8. Backlog Watch**
Long-standing PRs needing maintainer attention:

- **PR #3538** – *feat: add gateway start/stop/restart commands* (open since Apr 29, 2026, 43 days). No maintainer reviews. [View PR](https://github.com/HKUDS/nanobot/pull/3538)
- **PR #3239** – *feat: support multiple custom OpenAI-compatible providers* (open since Apr 17, 2026, 56 days). Stalled despite high community demand. [View PR](https://github.com/HKUDS/nanobot/pull/3239)

These two PRs represent blockers for operations (gateway control) and extensibility (multi-provider). A maintainer triage pass would reduce community friction and unblock downstream deployments.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-06-12

## Today's Overview

Hermes Agent shows very high activity today with 50 open issues and 50 pull requests updated in the last 24 hours, indicating a project under heavy development. The 32 new issues opened today suggest active user adoption and real-world usage is surfacing a wide range of bugs, particularly in the Desktop GUI, remote gateway mode, and CLI workflows. The project merged 9 PRs today, addressing critical bugs including HEIC/HEIF image transcoding failures, terminal environment state persistence, and frontend crash recovery. No new releases were published, but the volume of merged fixes points toward an upcoming patch release.

## Releases

No new releases were published in the last 24 hours. The latest available version remains v0.15.1 (2026.5.29). Given the volume of bugs being fixed, a v0.15.2 patch release appears imminent.

## Project Progress

Nine pull requests were closed/merged today, representing significant stability improvements:

- **[PR #44576](https://github.com/NousResearch/hermes-agent/pull/44576)** — `fix(images): transcode HEIC/HEIF to JPEG at cache and vision boundaries` — Critical fix for iPhone photo handling; HEIC images from iMessage, email, and AirDrop were being silently dropped before reaching the model.
- **[PR #44559](https://github.com/NousResearch/hermes-agent/pull/44559)** — `fix(terminal): advertise persistent env state` — Reduces unnecessary terminal calls by advertising that shell state (e.g., virtualenv activation) persists between commands.
- **[PR #44493](https://github.com/NousResearch/hermes-agent/pull/44493)** — `fix(desktop): recover from transient assistant-ui index-lookup crash` — Fixes the "Something broke in the interface" crash with `tapClientLookup: Index out of bounds` error.
- **[PR #44532](https://github.com/NousResearch/hermes-agent/issues/44532)** — Closed as completed, addressing incomplete `hermes setup` on Linux/WSL.
- **[PR #26670](https://github.com/NousResearch/hermes-agent/issues/26670)** — Closed: Windows `hermes update` quarantine fix for running executables.
- **[PR #14285](https://github.com/NousResearch/hermes-agent/issues/14285)** — Closed: Xiaomi MiMo token plan support added.
- **[PR #44569](https://github.com/NousResearch/hermes-agent/pull/44569)** — Merged: Safe update with dashboard plugin API hardening, macOS verification fixes, and dependency refreshes.
- **[PR #44568](https://github.com/NousResearch/hermes-agent/pull/44568)** — Merged: replaces deprecated `MESSAGING_CWD` with canonical `TERMINAL_CWD` in NixOS module.
- **[PR #44565](https://github.com/NousResearch/hermes-agent/pull/44565)** — Merged: replaces PortPool-based port reservation with OS-assigned ephemeral ports (`--port 0`).

## Community Hot Topics

The most engaged discussions this week reveal three major areas of user concern:

**1. Desktop Approval Flow Blocked** — [Issue #37812](https://github.com/NousResearch/hermes-agent/issues/37812) (7 comments, 4 👍)  
Users on macOS report that `approvals.mode: manual` renders confirmation prompts invisible in the Desktop GUI, making the security feature unusable. This directly impacts trust in the platform's safety guardrails.

**2. Autonomous Model Routing** — [Issue #16525](https://github.com/NousResearch/hermes-agent/issues/16525) (7 comments, 3 👍)  
Feature request asking for `model_switch` as an agent-callable tool for task-complexity-based routing. Users want agents to autonomously select between cheap/fast and expensive/capable models. A new PR [#44577](https://github.com/NousResearch/hermes-agent/pull/44577) adds caching for custom provider model discovery, which may relate.

**3. MCP Tools Unavailable in Desktop/TUI** — [Issue #38945](https://github.com/NousResearch/hermes-agent/issues/38945) (6 comments)  
Configured MCP tools (specifically Todoist) are not reliably exposed in Desktop/TUI sessions, making Hermes "materially worse than Claude Code or Codex" for these workflows. Multiple reports suggest this is a persistent integration gap.

## Bugs & Stability

**Critical/High Severity (P2) — Fixes Available:**
- **[#44562](https://github.com/NousResearch/hermes-agent/issues/44562)** — Frontend crash: `tapClientLookup Index out of bounds` when tools return unexpected data. **Fix PR #44493 merged today**.
- **[#44456](https://github.com/NousResearch/hermes-agent/issues/44456)** — TUI `\compress` returns error instead of compressing. Root cause: TUI command dispatch doesn't redirect built-ins.
- **[#44499](https://github.com/NousResearch/hermes-agent/issues/44499)** — Desktop agent ignores explicitly configured BrowserOS MCP, preferring built-in tools.
- **[#44497](https://github.com/NousResearch/hermes-agent/issues/44497)** — Duplicate responses to same user message via WeChat — context not cleared or thread cross-fire.
- **[#44468](https://github.com/NousResearch/hermes-agent/issues/44468)** — `hermes send` to Discord drops remaining chunks on 429 rate limits; no retry.
- **[#44530](https://github.com/NousResearch/hermes-agent/issues/44530)** — Windows: Desktop GUI cannot start non-default profiles after EXE reinstall; CLI works.
- **[#44523](https://github.com/NousResearch/hermes-agent/issues/44523)** — Desktop remote mode: chat file links are silent dead ends (file:// fallback targets gateway's path on client).
- **[#44121](https://github.com/NousResearch/hermes-agent/issues/44121)** — `npm ci` fails on clean checkout under npm 11 — lockfile version mismatch.
- **[#44242](https://github.com/NousResearch/hermes-agent/issues/44242)** — ACP image content blocks dropped before API call; `persist_user_message` override clobbers multimodal content.
- **[#43657](https://github.com/NousResearch/hermes-agent/issues/43657)** — `aiohttp ClientSession` leak after auxiliary tasks (title_generation).
- **[#40344](https://github.com/NousResearch/hermes-agent/issues/40344)** — WebUI profile `state.db` not created for new profiles; sessions leak to main database.

**Medium Severity (P3):**
- **[#44515](https://github.com/NousResearch/hermes-agent/issues/44515)** — Desktop update stuck at 1/3 unless background processes are stopped.
- **[#44522](https://github.com/NousResearch/hermes-agent/issues/44522)** — Remote folder picker clips long lists with no scrollbar — entries unreachable.
- **[#44574](https://github.com/NousResearch/hermes-agent/pull/44574)** — Fix PR: default 60s timeout for `terminal()` inside `execute_code` prevents hung commands.
- **[#43883](https://github.com/NousResearch/hermes-agent/issues/43883)** — `web.backend=anysearch` silently ignored; falls back to DuckDuckGo, unusable in China.

## Feature Requests & Roadmap Signals

**Likely for Next Release:**
- **Multi-cron schedules** — [PR #44572](https://github.com/NousResearch/hermes-agent/pull/44572) adds support for multiple cron expressions per job (e.g., run at 08:40 AND 19:00). Ready to merge.
- **Mission Control view** — [PR #44566](https://github.com/NousResearch/hermes-agent/pull/44566) adds a Desktop-native operational dashboard for sessions, active runs, automations, and workspace state.
- **Rust-backed install manager** — [PR #44067](https://github.com/NousResearch/hermes-agent/pull/44067) improves update reliability with checksum validation and clean uninstall.
- **Trigger keywords from skills** — [PR #43862](https://github.com/NousResearch/hermes-agent/pull/43862) indexes `trigger_keywords` from SKILL.md frontmatter for better skill discovery.

**Not Yet Addressed:**
- **Autonomous model routing** ([#16525](https://github.com/NousResearch/hermes-agent/issues/16525)) — No implementation PR yet.
- **Kanban skill validation** ([#44072](https://github.com/NousResearch/hermes-agent/issues/44072)) — No fix PR for validating skill names at dispatch time.
- **WebAuthn/Passkey support** ([#42448](https://github.com/NousResearch/hermes-agent/issues/42448)) — Desktop OIDC login window doesn't trigger biometric popups.
- **Local OpenAI endpoints in model picker** ([#44513](https://github.com/NousResearch/hermes-agent/issues/44513)) — Desktop model picker doesn't show local providers as named groups.

## User Feedback Summary

**Pain Points:**
1. **Desktop stability on Windows** — Multiple reports ([#44530](https://github.com/NousResearch/hermes-agent/issues/44530), [#26670](https://github.com/NousResearch/hermes-agent/issues/26670)) of profile startup failures and update failures on Windows.
2. **Remote gateway usability** — File link dead ends ([#44523](https://github.com/NousResearch/hermes-agent/issues/44523)) and clipped folder pickers ([#44522](https://github.com/NousResearch/hermes-agent/issues/44522)) degrade the remote experience significantly.
3. **MCP tool visibility** ([#38945](https://github.com/NousResearch/hermes-agent/issues/38945)) — Users report Hermes Desktop is materially worse than competitors for Todoist/third-party tool workflows.
4. **Image handling gaps** — HEIC/HEIF from iPhones failing ([PR #44576](https://github.com/NousResearch/hermes-agent/pull/44576)) and ACP multimodal content being dropped ([#44242](https://github.com/NousResearch/hermes-agent/issues/44242)).
5. **Rate limit handling** — Discord message drops on 429 ([#44468](https://github.com/NousResearch/hermes-agent/issues/44468)) indicate missing resilience patterns in platform integrations.

**Satisfaction Signals:**
- Active, constructive bug reports with detailed reproduction steps suggest a highly engaged user base.
- Multiple users are extending Hermes for production use cases (WeChat integration, Todoist workflows, cron jobs).
- The Xiaomi MiMo token plan feature ([#14285](https://github.com/NousResearch/hermes-agent/issues/14285)) was completed, showing responsiveness to regional provider support requests.

## Backlog Watch

**Long-unanswered Important Issues:**
- **[#20476](https://github.com/NousResearch/hermes-agent/issues/20476)** — Camofox browser: all operations fail with 403 when `CAMOFOX_API_KEY` is set. Opened May 6, last maintainer activity unknown. Broken authentication flow for a supported browser backend.
- **[#38445](https://github.com/NousResearch/hermes-agent/issues/38445)** — `api_call_count` not refunded when all retries exhausted. Opened June 3, P3, 1 👍. Small but correctness-affecting bug in the conversation loop.
- **[#43240](https://github.com/NousResearch/hermes-agent/issues/43240)** — Error when creating new profile in Desktop; cannot switch to new profile. Opened June 10, no fix PR yet.

**Stale PRs Needing Attention:**
- **[PR #37748](https://github.com/NousResearch/hermes-agent/pull/37748)** — `fix: harden desktop updater handoff` — Opened June 3, still open. Validates staged updater before use; catches async spawn failures. Has unit tests. Appears ready but unmerged.
- **[PR #37471](https://github.com/NousResearch/hermes-agent/pull/37471)** — `fix(desktop): reuse existing source installs` — Opened June 2, still open. Important for CLI-first install compatibility with Desktop.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-06-12

## Today's Overview

PicoClaw remains highly active with 31 pull requests and 6 issues updated in the last 24 hours. The project shipped a new nightly build (v0.2.9-nightly.20260611), while closing 3 issues and merging/merging 18 PRs. Activity is concentrated on dependency updates (10 PRs), channel fixes, and MCP infrastructure improvements, alongside multiple bug triages. The maintainer team appears to be in a maintenance-and-stability phase, with significant attention to security hardening and platform compatibility.

## Releases

**Nightly Build — v0.2.9-nightly.20260611.d955d5bb**  
A fully automated build, marked as potentially unstable. No breaking changes or migration notes provided. This nightly tracks the `main` branch since v0.2.9 and includes all changes merged up to June 11.  
*Changelog:* https://github.com/sipeed/picoclaw/compare/v0.2.9...main

## Project Progress

**18 merged/closed PRs** advanced several areas:

- **Channel fixes:**  
  - PR #2957 — Fixed tool_calls being dropped during streaming in the pico channel  
  - PR #2934 — WhatsApp native mode now correctly detects `use_native: true`  
  - PR #3067 — `dm_scope` setting now persisted to SessionConfig (fixes frontend save bug)  

- **Security & stability:**  
  - PR #2955 — Singleton PID check now verifies process identity (prevents startup collisions with recycled PIDs)  
  - PR #3060 — Improved error wrapping with `%w` and added error handling for `json.MarshalIndent`  

- **Model fixes:**  
  - PR #2947 — Corrected `claude-sonnet-4.6` model ID to `claude-sonnet-4-6` (hyphens, not dots)  

- **MCP improvements:**  
  - PR #2696 — Added per-request dynamic HTTP headers from channel context to MCP servers  

- **Dependency updates:**  
  - 10 PRs updated Go dependencies (AWS SDK, MCP SDK, golang.org/x/sync) and frontend tools (eslint, Vite, shadcn, TypeScript ESLint)

## Community Hot Topics

1. **Issue #2472 — `list_dir` fails on Windows** (5 comments, 1 👍)  
   *https://github.com/sipeed/picoclaw/issues/2472*  
   Persistent Windows compatibility bug — path separators (`\`) conflict with Go's `os.Root` which requires forward slashes. Open since April 10, now 2 months without resolution. Signals cross-platform portability pain for Windows users.

2. **Issue #2954 — No 32-bit Android support** (3 comments)  
   *https://github.com/sipeed/picoclaw/issues/2954*  
   Closed as stale. Community interest in ARM32 Android (Termux) remains unmet, but maintainers appear deprioritizing this.

3. **Issue #3094 — Duplicate messages from async subagent (spawn)** (1 comment)  
   *https://github.com/sipeed/picoclaw/issues/3094*  
   Spawned subagents produce double messages on Telegram/Feishu — raw output plus summarized main-agent version. User reports poor UX.

4. **PR #2937 — Agent Collaboration Bus** (still open, actively updated)  
   *https://github.com/sipeed/picoclaw/pull/2937*  
   Major feature in review: first-class inter-agent communication with mailboxes, collaboration threads, and permission-aware delivery. This signals a shift toward multi-agent architectures.

**Underlying needs:** Cross-platform reliability (Windows/Android), message deduplication in multi-agent flows, and a proper agent collaboration framework are the top community concerns.

## Bugs & Stability

| Severity | Issue | Status | Fix PR? |
|----------|-------|--------|---------|
| **High** | **#3108 — Image description hallucinates** when model lacks vision support (0 comments) | Open, new today | None yet |
| **High** | **#2472 — `list_dir` Windows path separator bug** (5 comments, 2 months old) | Open | None |
| **Medium** | **#3094 — Duplicate subagent spawn messages** (1 comment) | Open | None |
| **Medium** | **#3080 — Security bypass: `allowed_cidrs` can be bypassed via loopback** (0 comments) | Closed | Fix merged |
| **Low** | **#2958 — tool_calls dropped in pico channel streaming** | Closed | PR #2957 merged |

**Critical:** The new image hallucination bug (#3108) is concerning — models without vision support are being tasked to describe images, producing plausible-sounding but irrelevant descriptions. No fix PR exists yet.  
**Security:** #3080 (CIDR bypass) was responsibly disclosed and fixed.  
**Windows:** #2472 remains a long-standing platform gap.

## Feature Requests & Roadmap Signals

- **Agent Collaboration Bus (PR #2937):** The largest feature in review — per-agent mailboxes, structured message envelopes, and collaboration threads. Likely for v0.3.0.
- **Per-request MCP headers (PR #2696, merged):** Enables channel-context-based authentication to MCP servers. Already in main.
- **Dynamic headers from InboundContext:** Gives channel adapters (Telegram, Slack) ability to inject tokens per-request.
- **Session Scope persistence (PR #3067, merged):** Users can now save `dm_scope` setting, improving multi-session isolation.

**Prediction for next version:** The Agent Collaboration Bus and MCP header forwarding are strong candidates for v0.3.0. No stable release since v0.2.9, suggesting a accumulation phase.

## User Feedback Summary

- **Windows users:** Frustrated by unresolved path separator bug (#2472) — `list_dir` effectively broken on the second-largest desktop OS.
- **Multi-agent users:** Double-message problem (#3094) degrades UX on Telegram/Feishu. Users want clean, single-message output.
- **Android Termux users:** 32-bit support requested but stalled (#2954 closed stale). Signals Android users are a minority.
- **Configuration users:** Erroneous model IDs (#2947 fixed) and saving failures (#3067 fixed) caused frustration with first-run experience.
- **Security-conscious users:** Positive reception of `allowed_cidrs` fix (#3080), but the loophole existed for a period.

Overall sentiment: **Active but with platform friction.** Core features stable, but Windows and multi-agent gaps persist.

## Backlog Watch

| Issue/PR | Age | Status | Concern |
|----------|-----|--------|---------|
| **#2472 — Windows `list_dir` bug** | **63 days** | Open | No maintainer response for 2 months. Key platform gap. |
| **#2954 — 32-bit Android** | 16 days | Closed stale | Maintainers closed without resolution. May need re-opening. |
| **#2937 — Agent Collaboration Bus** | 19 days | Open, no merge | Large PR with no reviewer activity in 18 days. Risk of stagnation. |
| **#2956 — Channel enabled state merge fix** | 16 days | Open, no merge | Configuration regression fix — needs review. |

**Most concerning:** Issue #2472 has no maintainer activity since April. If PicoClaw aims for cross-platform adoption, this Windows blocker needs priority.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw Project Digest — 2026-06-12**

Prepared by: AI Agent & OSS Project Analyst
Data source: github.com/nanocoai/nanoclaw

---

### 1. Today's Overview

NanoClaw is in a high-velocity patch and feature cycle today, with **16 PRs updated in the last 24 hours** (9 merged/closed, 7 open) and **3 issues updated**. Today’s activity is dominated by contributor [gavrielc], who authored eight of the nine closed PRs, delivering a rapid succession of fixes and platform features. Two critical issues surfaced: a silent SQLite read-only bug that had been dropping command‑gate denials (now fixed), and a new egress‑lockdown problem blocking host‑local service access for agents. The project overall shows strong maintainer responsiveness and growing community contribution depth.

### 2. Releases

No new releases today.

### 3. Project Progress

**9 PRs were merged or closed today**, representing significant platform hardening and feature addition:

- **fix(session-manager): writeOutboundDirect opens outbound.db read-only — command‑gate denials never deliver** ([PR #2738](https://github.com/nanocoai/nanoclaw/pull/2738)) — CLOSED. Fixes a longstanding bug where denial responses from the command gate were silently discarded because `writeOutboundDirect()` opened the database in read‑only mode.

- **feat(channels): native channel-instance dimension — multi‑bot substrate** ([PR #2733](https://github.com/nanocoai/nanoclaw/pull/2733)) — CLOSED. Adds first‑class support for multiple bot instances per channel.

- **feat(approvals): approval-resolved callback registry** ([PR #2737](https://github.com/nanocoai/nanoclaw/pull/2737)) — CLOSED. Enables additive callback registration when approvals are resolved.

- **feat(delivery): getDeliveryAction read side for the action registry** ([PR #2734](https://github.com/nanocoai/nanoclaw/pull/2734)) — CLOSED.

- **feat(webhook-server): raw-route registry** ([PR #2739](https://github.com/nanocoai/nanoclaw/pull/2739)) — CLOSED. Allows non‑Chat‑SDK webhooks to be appended.

- **feat(container): per-group idle timeout** ([PR #2740](https://github.com/nanocoai/nanoclaw/pull/2740)) — CLOSED. Clean exit for ephemeral sessions.

- **fix(host-sweep): grace period for freshly-woken containers** ([PR #2736](https://github.com/nanocoai/nanoclaw/pull/2736)) — CLOSED. Prevents false‑positive container reaping.

- **fix(chat-sdk-bridge): record the acting user on resolved approval cards** ([PR #2735](https://github.com/nanocoai/nanoclaw/pull/2735)) — CLOSED.

- **fix(setup): auto-submit handoff context as Claude's first prompt** ([PR #2741](https://github.com/nanocoai/nanoclaw/pull/2741)) — CLOSED. Interactive setup now reliably passes context to Claude instead of waiting inertly.

**7 PRs remain open** (see *Bugs & Stability* and *Feature Requests* sections for details).

### 4. Community Hot Topics

- **#1356 — Agent memory system redesign** ([Issue #1356](https://github.com/nanocoai/nanoclaw/issues/1356)) — **OPEN**, 6 👍, 2 comments. This long‑running issue continues to gather interest. The current memory system (Markdown index + satellite files) is showing scaling limits at ~54 files / 83 KB. The community is watching for a proposed redesign, likely to be a priority candidate for the next milestone.

- **#2742 — PR Factory: a published recipe for PR review, triage & testing** ([PR #2742](https://github.com/nanocoai/nanoclaw/pull/2742)) — **OPEN**, created today. This is a skill/recipe that turns every PR into a Slack thread triaged by a dedicated agent. It’s a meta‑feature: a self‑hosted CI‑like workflow built on NanoClaw itself. Signals strong interest in agent‑driven DevOps patterns.

- **#2731 — Egress lockdown hijacks host.docker.internal** ([Issue #2731](https://github.com/nanocoai/nanoclaw/issues/2731)) — **OPEN**, created today, 0 comments yet. Important because it blocks agents from reaching ollama endpoints and any other host‑local proxy services — a fundamental connectivity regression for local development setups.

### 5. Bugs & Stability

| Severity | Bug | Status |
|----------|-----|--------|
| **HIGH** | `writeOutboundDirect()` opens DB read‑only → command‑gate denials silently dropped | FIXED in PR #2738 |
| **HIGH** | Egress lockdown blocks `host.docker.internal` → agents lose host‑local services (ollama, proxies) | OPEN — Issue #2731 |
| **MEDIUM** | `ncl wirings create` skips `agent_destinations` side effect → messages to new chats are dropped | OPEN — PR #2743 (fix proposed) |
| **MEDIUM** | `NANOCLAW_*` env flags set in `.env` never reach `process.env` under launchd/systemd | OPEN — PR #2730 (fix proposed) |
| **MEDIUM** | Signal adapter silently drops `add_reaction` and ignores inbound reaction envelopes | OPEN — PR #2744 (fix proposed) |

**Notable:** The read‑only DB bug had been in the codebase since at least May 15 (issue #2495). Today’s fix closes a month‑old latent data‑loss bug.

### 6. Feature Requests & Roadmap Signals

- **PR Factory (#2742)** — Community‑proposed skill for automated PR review/triage/testing. If accepted, this would become a flagship “eat your own dog food” recipe for NanoClaw.

- **Multi‑bot per channel (#2733, closed)** — Just landed native channel‑instance support. This likely paves the way for conversations that involve multiple agents simultaneously.

- **Approval‑resolved callback registry (#2737, closed)** — A building block for richer multi‑step approval workflows.

- **Raw‑route webhook registry (#2739, closed)** — Enables third‑party webhooks that don’t use the Chat SDK, broadening channel integration.

**Predicted for next version:** The PR Factory skill may become an official recipe. A memory system overhaul (issue #1356) is overdue and has strong community support.

### 7. User Feedback Summary

- **Pain point — Egress lockdown breaks local development**: User `sturdy4days` reports that setting `NANOCLAW_EGRESS_LOCKDOWN=true` cuts agents off from ollama and other host‑local services. This makes the security feature unusable for users who run local AI backends.

- **Pain point — Env variable loading under launchd/systemd**: User `sturdy4days` also reports that `.env` file variables (e.g., `NANOCLAW_EGRESS_LOCKDOWN`) do not propagate to `process.env` under service managers, making operational flags ineffective in production deployments.

- **Pain point — Wired chats silently drop messages**: Multiple users have hit bugs where creating a wiring via the CLI doesn't set up the destination routing properly (PR #2743), causing messages to be sent into a void.

- **Satisfaction — Rapid fix turnaround**: The closing of the month‑old DB read‑only bug (#2495 → #2738) within hours of the fix PR being opened shows strong contributor velocity and maintainer trust.

### 8. Backlog Watch

| Item | Age | Notes |
|------|-----|-------|
| **#1356 — Agent memory system redesign** | 81 days (since Mar 23) | High interest (6 👍), no PR yet. The most upvoted open issue. Maintainer attention warranted — likely a pre‑requisite for scaling beyond alpha. |
| **#2611 — Preserve caller context after approval** | 18 days (since May 25) | **OPEN** PR. Security‑related fix for command approval; hasn’t been merged yet. Risk: approval‑bypass vulnerability if left unmerged. |
| **#2685 — docs(signal): group typing, outbound reactions** | 8 days (since Jun 4) | **OPEN** PR, documentation‑only. Low urgency but adds value for Signal channel users. |

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the NullClaw project digest for **2026-06-12**.

---

## NullClaw Project Digest: 2026-06-12

### 1. Today's Overview
Project activity remains at a minimal baseline today. There is **1 open issue** updated in the last 24 hours, with no new pull requests or releases. The single reported bug indicates a potential **integration stability problem** with the widely-used Ollama local model provider. While no features were merged or released, the emergence of this specific bug is the primary signal for the project’s current state, suggesting a need for maintainer attention on local model handling.

### 2. Releases
There are **no new releases** today. The project has not published a new version or release tag within the reporting period.

### 3. Project Progress
**Merged/Closed PRs:** 0  
No pull requests were merged or closed today. There is no evidence of feature advancement or bug fixes being integrated into the codebase in the last 24 hours.

### 4. Community Hot Topics
- **Issue #952: [bug] Local model using ollama returns incomplete answers**  
  *Author: bloodgroup-cplusplus | Updated: 2026-06-11 | Comments: 0 | 👍: 0*  
  [GitHub Link](https://github.com/nullclaw/nullclaw/issues/952)  
  This is the **only active item** in the project today. The issue reports that when using Gemma pulled via Ollama, the agent fails to output complete sentences. The lack of comments or reactions suggests the issue is very fresh (less than 24 hours old), but the underlying need is clear: **users require reliable, complete response generation from local LLMs**. This is critical for users who prefer or require offline AI assistant capabilities.

### 5. Bugs & Stability
| Issue | Severity | Description | Fix PR Exists? |
|-------|----------|-------------|----------------|
| [#952](https://github.com/nullclaw/nullclaw/issues/952) | **High** | Local model (Gemma via Ollama) returns truncated/incomplete answers | No |

**Analysis:** This is the only bug reported today. It is rated **High** severity because it directly impacts the core functionality (response generation) for users running local models, a key use case for the project. The absence of a linked fix PR indicates no immediate remediation is in progress.

### 6. Feature Requests & Roadmap Signals
No explicit feature requests were filed today. However, the bug report in **Issue #952** acts as a **strong implicit signal** that the community expects robust, complete output from local model integrations. If the root cause is a token streaming issue or a misconfiguration in the Ollama API adapter, a patch to improve output reliability is likely the next necessary update, rather than a new feature. Predictions for the next version: a hotfix addressing streaming truncation or configuration defaults for Ollama models.

### 7. User Feedback Summary
- **Pain Point:** The user reported frustration with an AI agent that "doesn't answer in complete sentences," which undermines trust and utility.  
- **Use Case:** Local, private AI assistant usage via Ollama.  
- **Satisfaction Level:** **Dissatisfied** – the user took the time to provide a screenshot and steps to reproduce, indicating a significant negative impact on their workflow.

### 8. Backlog Watch
There are **no long-standing unanswered issues** in the current 24-hour window. The only open item (#952) is recent and has not yet waited for a reply. No historical stale issues were updated today. Maintainers should prioritize **Issue #952** to prevent it from becoming a stale backlog item, as it touches on a core integration dependency (Ollama).

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-06-12

## Today's Overview

IronClaw continues a high-velocity development cadence with 47 PRs and 31 issues updated in the last 24 hours, reflecting intense focus on the Reborn binary maturation for production readiness. The merge/close rate of 25 PRs and 13 issues demonstrates strong engineering throughput. Activity is concentrated on Reborn WebUI v2 usability fixes, Slack delivery integration, outbound communication routing, and automated QA infrastructure. No new releases were published today, but the project is approaching a major milestone with the Reborn production cutover gate (Issue #4619) now merged and substantial e2e test suites landing.

## Releases

No new releases published today. The last release cycle (PR #3708) is still open and pending, which would bump `ironclaw_common` from 0.4.2 → 0.5.0 and `ironclaw_skills` from 0.3.0 → 0.4.0 with API-breaking changes.

## Project Progress

**25 PRs merged/closed today** advancing the Reborn production track:

- **Automation & Triggers**: PR #4757 fixed triggered-run navigation from the Automations page (blank screen issue when clicking fired runs)
- **Slack Delivery & Outbound Routing**: PR #4782 unified outbound state store so WebUI delivery defaults reach Slack delivery; PR #4753 implemented conversation-keyed routing for Slack approval gating; PR #4781 ported Claude autonomous loop commands for Reborn binary
- **Capability Runtime**: PR #4784 fixed capability runtime unavailability to be handled as tool failure rather than aborting the entire agent loop
- **Extension Activation**: PR #4744 consolidated extension activation/auth-gating and GSuite OAuth reuse
- **Observability**: PR #4588 introduced trajectory observer hooks and LLM provider injection seams for external host (nearai-bench) observability
- **QA Infrastructure**: PR #4769 added 22 new Reborn QA use-case e2e tests on the binary-E2E harness
- **Storage & Config**: PR #4551 (closed) wired Reborn production Postgres storage config; PR #4593 closed effective config API for list/get/set/validate; PR #4615 closed production `build_reborn_runtime` launchability

## Community Hot Topics

1. **[Issue #3036 — Configuration-as-Code Epic](https://github.com/nearai/ironclaw/issues/3036)** (7 comments) — This long-running EPIC for declarative configuration of tenant blueprints and use-case harnesses remains the most commented issue. The community is clearly demanding schema-driven, auditable configuration instead of hand-editing `.env` files and settings JSON.

2. **[Issue #4766 — Chat runtime credential loss](https://github.com/nearai/ironclaw/issues/4766)** (2 comments, CLOSED) — Users reported that UI-saved NEAR AI credentials were lost after restart. This was quickly resolved, demonstrating responsive bug handling.

3. **[Issue #4703 — Model picker saves display name](https://github.com/nearai/ironclaw/issues/4703)** (2 comments) — The NEAR AI model picker saves display names instead of model IDs, causing downstream dispatch failures. PR #4772 includes a fix for this backend issue.

**Underlying needs**: Users are hitting friction in three areas: (1) declarative configuration management, (2) credential persistence across restarts, and (3) model/provider configuration correctness. The project is actively addressing all three.

## Bugs & Stability

**High Severity:**
- **Agent loop abort on capability unavailability** (Issue #4761) — Agent stops entirely after repeated tool failures instead of recovering. **Fix PR #4784 merged today.**
- **Credential loss after restart** (Issue #4766) — UI-saved NEAR AI credentials not persisted across WebUI restarts. **CLOSED.**

**Medium Severity:**
- **Approval UX gaps** (Issue #4764) — Denying shell approval leaves tool pending with no user feedback. **No fix PR yet.**
- **Tool activity update stalls** (Issue #4770) — SSE reconnect issues may cause tool activity to stop updating after page refresh. **No fix PR yet.**
- **Workspace path duplication** (Issue #4759) — Workspace-relative paths are duplicated in file creation. **No fix PR yet.**
- **Large response fails with 16KB limit** (Issue #4751) — Provider tool arguments exceed 16384-byte limit for large responses. **No fix PR yet.**

**Low Severity:**
- Code block wrap toggle ineffective (Issue #4748)
- Workspace files not discoverable from WebUI (Issue #4750)
- NEAR AI MCP search tool name mismatch (Issue #4699, **CLOSED**)
- Nightly E2E failure on extensions (Issue #4108) — Ongoing intermittent CI failure.

## Feature Requests & Roadmap Signals

- **Global "Always Allow" setting for tools** (Issue #4776) — Users want a global setting to auto-approve eligible tools without per-approval clicks. Likely for next patch release.
- **Run/thread-scoped operator log filtering** (Issue #4771) — Follow-up to the Logs page wiring, for granular log filtering per run. Medium-term roadmap.
- **Persistent tenant sandbox & agent-built extension promotion** (PR #4785) — Design document for sandbox backend wiring and persistent agent environments. Indicates hosted deployment ambitions.
- **Automated QA for Reborn binary** (Issue #4775) — Epic for hermetic/fixture/e2e/live testing of the Reborn binary. High priority — PR #4769 already landed 22 tests.

**Prediction for next release**: The pending release (PR #3708) will likely include: Reborn production Postgres support, effective config APIs, trajectory observer hooks, Slack delivery routing, and the automated QA test suites.

## User Feedback Summary

**Pain Points (from Issues #4692, #4701, #4703, #4764, #4766):**

- **Configuration friction**: Users find the current mix of `.env`, `.system/` docs, settings JSON, and runtime flags confusing and error-prone
- **Approval UX lacking**: Approval modals lack sufficient context (e.g., for HTTP tool requests), and denial actions provide no feedback
- **Credential management**: Credentials lost on restart; model picker saves wrong fields
- **Local setup complexity**: SSO setup fails in local environment (GitHub/Google OAuth callbacks); driver errors are opaque
- **Tool workflow inconsistency**: Failed tools lead to message ordering issues and agent confusion

**Satisfaction Signals:**
- High community engagement (31 issues, 47 PRs in 24h)
- Fast turnaround on critical bugs (Issue #4766 closed same day)
- Active Slack integration development shows real use-case focus

## Backlog Watch

- **[Issue #3036 — Configuration-as-Code Epic](https://github.com/nearai/ironclaw/issues/3036)** (7 comments, open since 2026-04-28) — Longest-standing open issue with no closure in sight. Core community pain point without dedicated implementation PR yet.
- **[Issue #4108 — Nightly E2E failed](https://github.com/nearai/ironclaw/issues/4108)** (0 comments, open since 2026-05-27) — Persistent intermittent CI failure with no discussion thread. May indicate flaky test infrastructure that needs maintainer attention.
- **[PR #3708 — Release](https://github.com/nearai/ironclaw/pull/3708)** (open since 2026-05-16) — The pending release PR contains API-breaking changes to `ironclaw_common` and `ironclaw_skills` but has not been merged. May be blocked by Reborn production readiness issues that are now being resolved.

*Note: No issues or PRs older than 30 days remain unanswered; the project maintainers are actively monitoring all threads.*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the LobsterAI project digest for **2026-06-12**.

---

## LobsterAI Project Digest: 2026-06-12

### 1. Today's Overview
LobsterAI saw a massive spike in development activity, with **19 Pull Requests** updated in the last 24 hours—**18 of which were merged or closed**. This represents a significant push toward the next major release. While no new releases were published today, the sheer volume of merged PRs indicates a consolidation phase. The two open issues remain stable, with the community actively discussing feature gaps and potential bugs. Overall, the project health is **very strong**, with high velocity on backend stability, new features (Computer Use, Real-time ASR, HTML Sharing), and critical bug fixes.

### 2. Releases
- **No new releases** were published as of this digest.

*(Note: Given the high volume of merged PRs, a new version may be imminent.)*

### 3. Project Progress (Merged/Closed PRs)
The team closed **18 PRs** today, spanning major feature work and critical fixes:

- **New Features (MVP):**
    - **Computer Use (MVP):** A major addition via digital agency integration, including a runtime resolver, MCP server bridge for app/window control, and Windows x64 support (`#2143`).
    - **Real-time ASR Voice Input:** Added a live speech-to-text mode for the Cowork feature, supporting streaming PCM audio and a new setting toggle (`#2148`).
    - **HTML Share Access Control:** Users can now choose between "share code" or "public access" when creating HTML shares, with support for updating access methods later (`#2146`).
    - **Automatic Model Failover:** The system now automatically retries requests with a fallback model when the primary model fails due to transient errors (`#1483`).
    - **Gmail Email Trigger (Automation):** A new Gmail Watcher module polls for new emails and triggers agent sessions, bringing parity with OpenClaw's integration (`#1484`).

- **Stability & Context Improvements:**
    - **Extended pre-send model sync timeout** from 30s to 90s to prevent message drops on slow gateways (`#2152`).
    - **Improved post-compaction context continuity** to ensure agents maintain task awareness after history compression (`#2145`).
    - **Fixed a startup-stop race condition** where a user stop before a gateway run became active would still send a chat (`#2147`).
    - **Raised gateway heap limit** in OpenClaw to prevent OOM crashes in long-running multi-channel workloads (`#2149`).

- **UI/Frontend Polish:**
    - **Sticky expert suite controls** matching Skills/MCP page behavior (`#2150`).
    - **Skill Tooltip:** Hovering over a skill now shows a full rich-tooltip with name and description (`#1459`).
    - **Fixed scroll-friendly active skill chips** in the prompt bar (`#1481`).
    - **Fixed NSIS destructive init** and redesigned the engine loading page (`#2142`).

### 4. Community Hot Topics
The community activity remains focused on two key areas:

- **Multi-Agent & Model Customization (#1462):** [Link](https://github.com/netease-youdao/LobsterAI/issues/1462)
    - *Context:* User requests per-agent model binding and a "room/manager" pattern for agent orchestration, comparing unfavorably to a competing product.
    - *Analysis:* This is the highest-value feature request currently open. The recent focus on Cowork stability and the new Computer Use kit shows the team is laying the groundwork for complex multi-agent workflows, but dedicated per-agent model binding is not yet on the road map.

- **Token Waste / Duplicate Output (#2121):** [Link](https://github.com/netease-youdao/LobsterAI/issues/2121)
    - *Context:* User suspects the system is wasting tokens on duplicate text output, potentially a bug in the "claw" engine.
    - *Analysis:* This is a high-priority concern for users paying for API tokens. The recent fix on post-compaction context continuity (`#2145`) may partially address this, but the user has not confirmed.

### 5. Bugs & Stability
- **Critical: Possible Token Waste (Duplicate Output):** Issue #2121 reports repetitive text generation, likely consuming excessive API tokens. No fix has been directly linked, but the context compaction improvements in `#2145` may mitigate this. **Severity: High** (cost-related).
- **Memory Leak (Fixed):** PR `#1478` resolved a `setTimeout`-related memory leak in the `CopyButton` component that occurred during rapid session switches.
- **OOM Crash (Fixed):** PR `#2149` explicitly raises heap limits to prevent Out-Of-Memory crashes in the gateway process under heavy load. **Severity: Critical** (stability).
- **Startup-Stop Race (Fixed):** PR `#2147` prevents unwanted chat transmission when a user stops a session before the agent fully starts.

### 6. Feature Requests & Roadmap Signals
| Request | Status | Likely Next Version? |
| :--- | :--- | :--- |
| **Per-agent Model Binding** (#1462) | Open/Wishlist | **Low.** Requires architectural changes to the agent lifecycle. |
| **Multi-Agent Orchestration (Room/Manager)** (#1462) | Open/Wishlist | **Medium.** Recent PRs on Cowork context and the "Computer Use" kit imply a sophisticated agent ecosystem is being built. |
| **Computer Use (Agent that controls the PC)** | **Merged today (#2143)** | **High.** This is a flagship feature likely landing in the next release. |
| **Gmail Trigger for Automation** | **Merged today (#1484)** | **High.** Features a full polling module and session trigger. |
| **Real-time ASR Voice Input** | **Merged today (#2148)** | **High.** A significant UX improvement for voice interactions. |

### 7. User Feedback Summary
- **Satisfaction:** Users are pleased with the multi-instance per-channel functionality introduced in v4.3, calling it "very practical" (#1462).
- **Dissatisfaction:** The leading pain point is the inability to assign different models to different agents. The duplicate text output issue (#2121) is also causing immediate frustration due to perceived cost waste.
- **Competitive Landscape:** Users are actively comparing LobsterAI to other tools (e.g., Hiclaw), noting that LobsterAI has superior interaction experience but is missing specific orchestration features.

### 8. Backlog Watch
The following items lack recent activity and may need maintainer attention:

- **#1459 (Open PR):** "feat(skills): 技能 hover 时展示完整描述 Tooltip" — This was merged today, but was stale for over 2 months. It highlights that feature PRs can linger.
- **#1462 (Open Issue):** "Multi-Agent/Model Wish" — While not stale in content, the project has not formally acknowledged a timeline for these features. As the most upvoted feature request, a maintainer response would be valuable.
- **Open PRs (Total: 1):** Only one PR remains open (`#1459`), which was merged today. The current backlog is remarkably clean.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-06-12

## Today's Overview

Activity in the Moltis project was low today, with only 1 new open issue and 1 open pull request updated in the last 24 hours. No new releases were published. The single open issue reports a bug in Fastmail MCP authorisation, while the open PR addresses a WhatsApp delivery problem for privacy-enabled chat IDs. Overall, the project appears to be in a quiet maintenance phase, with no major feature work or merged changes observed today.

## Releases

None.

## Project Progress

No pull requests were merged or closed today. There are no completed features or fixes to report.

## Community Hot Topics

**Issue #1115 — "Fastmail MCP Authorisation" (1 comment)**  
[GitHub Issue #1115](https://github.com/moltis-org/moltis/issues/1115)  
This is the only open issue with any community discussion. The reporter indicates they have searched existing issues and are using the latest version of Moltis. The brief summary suggests the user encountered a failure in the authorisation flow when connecting to Fastmail via MCP. The single comment may contain additional diagnostic information; given the lack of further reactions or replies, this appears to be an early-stage triage item.

**PR #1116 — "fix(whatsapp): deliver replies to @lid chats via PN JID rewrite" (no comments)**  
[GitHub PR #1116](https://github.com/moltis-org/moltis/pull/1116)  
This PR addresses a silent message delivery failure on WhatsApp: replies sent to privacy-enabled sender chats (tagged `@lid`) were generated by the agent and visible in the web UI, but never delivered to the user. The fix rewrites the phone number/PN JID before sending. No community discussion has occurred yet on this PR.

## Bugs & Stability

One bug was reported today, ranked **Medium** severity:

- **Issue #1115 — Fastmail MCP Authorisation failure**  
  The nature of the authorisation failure is not yet detailed, but it blocks MCP connectivity to Fastmail. No associated fix PR exists. Triage and reproduction steps are pending.

No crashes, regressions, or high-severity bugs were reported.

## Feature Requests & Roadmap Signals

No explicit feature requests were filed today. The only actionable signal is the WhatsApp delivery issue (PR #1116), which is a fix rather than a new feature. There are no indications of planned features or roadmap changes from today's activity.

## User Feedback Summary

The single user report (Issue #1115) reflects a **pain point** with third-party MCP integration authorisation, specifically for Fastmail. The user appears to be following correct setup procedures with the latest version. No other satisfaction or dissatisfaction signals were captured. The WhatsApp delivery fix in PR #1116 indirectly addresses a user-facing silent failure, though the PR author is a contributor rather than an end-user reporter.

## Backlog Watch

None of the open issues or PRs show signs of long-standing inactivity. The oldest item updated today is Issue #1115 (created yesterday). No items require maintainer attention due to age or neglect. The project's backlog is currently clean of stale items.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Based on the GitHub data for **CoPaw (github.com/agentscope-ai/CoPaw)** as of **2026-06-12**, here is the project digest.

---

## CoPaw Project Digest — 2026-06-12

### 1. Today's Overview

The project is experiencing **high activity**, with 31 issues and 40 PRs updated in the last 24 hours, indicating a strong development and community engagement pulse. While bug reports and regressions are surging—particularly around the new Tauri desktop client and recent UI changes—the maintainers are responding rapidly, as evidenced by the release of two patches (`v1.1.11.post1` and `v1.1.11.post2`) and several merged hotfixes. The community is active, submitting feature requests and reporting friction points from the ongoing rebranding from "copaw" to "qwenpaw" and the migration toward AgentScope 2.0. Overall, the project is in a **"hot fix" and stabilization phase** following a major UI overhaul, balancing new features against critical bug fixes.

### 2. Releases

Two patch releases were published today, both focused on **hotfixes and UI polish**:

- **v1.1.11.post2**: A minor patch primarily containing a UI style fix to truncate tool card titles to a single line with an ellipsis (`#5119`). This addresses visual overflow in the conversation log.
- **v1.1.11.post1**: A rollback of a previous fix (`#5092`) and other chores. This release appears to be a response to the OpenSSL 3.5 regression bug (`#5086`) that was breaking the Desktop client startup.

**No breaking changes or migration notes** are associated with these releases.

### 3. Project Progress

**Key Merged/Closed PRs (19 total)** reflect a focus on **stability, CI hardening, and security**:

- **Desktop & Build Stability**:
    - `#5119`: Merged CSS fix for tool card overflow.
    - `#5124`: Bumped version to `1.1.11.post2`.
    - `#5118`: Chore for AgentScope platform news.
- **Governance & Pipeline**:
    - `#5088`: An open discussion PR on initial governance and sandbox interface, signaling a push toward better agent isolation.
    - `#5121`: A new CI feature to add a *release verification gate* between build and publish, aiming to catch installation regressions (like `#5120` and `#5126`) before shipping.
- **Security**:
    - `#5028`: Fix to isolate the OS keychain master key per install, preventing shared credentials across different QwenPaw installations on the same machine.

### 4. Community Hot Topics

The most active discussions reveal **significant friction with the v1.1.11 release** and the new UI:

- **`#5106` [Bug]: New Tauri Desktop SSL + Memory Overflow:** This was the highest-engagement bug today (7 comments). A user reported that the new Tauri client causes SSL certificate errors followed by infinite process spawning, leading to memory exhaustion and system crashes. *Underlying Need: Reliability for the new Desktop build path.*
- **`#5064` [Bug]: Scheduled Tasks Not Triggering:** A critical functional failure (8 comments). Users report that agent-created scheduled tasks appear but never execute, and they cannot be manually edited. *Underlying Need: Core agent autonomy and scheduling reliability.*
- **`#4989` [Bug]: Local vLLM Models Unresponsive:** A regression specifically with the v1.1.9 and v1.1.10 releases. Users running local `Qwen 3.6-27B` via vLLM find the system unresponsive after submitting a question, despite successful connection tests. *Underlying Need: Robust integration with local/self-hosted model backends.*
- **`#5086` [Bug]: OpenSSL 3.5 Regression on Desktop:** This bug caused the Desktop app to fail to launch. It was quickly identified and led to a patch release (v1.1.11.post1). *Underlying Need: Stable Python/OpenSSL bundling for Desktop builds.*

### 5. Bugs & Stability

The following bugs were reported and updated today, ranked by estimated severity:

- **Critical: `#5106` - New Tauri Desktop SSL + Memory Overflow:** This is a **crash/DoS** bug affecting the latest client.
- **Critical: `#5064` - Scheduled Tasks Not Triggering:** A **core functionality** failure in agent autonomy.
- **High: `#5098` - Memory Search UI Display Error:** The `auto_memory_search` tool works functionally but renders garbage data in the UI, causing user confusion.
- **High: `#5137` - Vector Memory Config Loss on Save:** UI bug where settings are lost if specific cards are not expanded before clicking "save".
- **Medium: `#5122` - Context Compression Stats Mismatch:** The displayed token usage after compression does not match the actual input, potentially masking hidden context bloat from skills or MCP services.
- **Medium: `#4989` - Local Model (vLLM) Regression:** A serious regression affecting users with specific (popular) local model setups.
- **Low: `#5102` - File Download Failure in v1.1.11:** New UI prevents downloading certain files.

**Fix PRs:** A PR for the OpenSSL regression (`#5086`) was implicit in the `v1.1.11.post1` revert. A PR addressing the Langfuse trace fragmentation (`#5128`) is currently open.

### 6. Feature Requests & Roadmap Signals

Several feature requests signal where the project is heading:

- **High Probability (Next Release):** Integration with **Headroom** (`#5063`) for optional context compression (60-95% token reduction) to save costs.
- **High Probability (Next Release):** **Langfuse observability improvements** (`#5127`, PR `#5128`) to group traces by agent loop, fixing a major debugging pain point.
- **Medium Probability:** **Agent OS Driver** (PR `#5067`): A unified abstraction for MCP/A2A/ACP capabilities. This is a *major architectural signal* aligning with the Runtime 2.0 discussion (PR `#5078`).
- **Low Probability (Debated):** **Configurable chat interaction modes** (`#5116`), including message queueing (like OpenClaw, per `#5103`).
- **Backlog:** **Quote/Reference** (`#5110`), **Per-turn token stats** (`#5130`), and **Coding mode autocompletion** (`#5131`).

### 7. User Feedback Summary

User sentiment is **mixed, leaning toward frustrated but hopeful**.

- **Pain Points:**
    - **UI/UX Regression:** The new UI in v1.1.11 is causing confusion. Users report it is missing familiar elements (e.g., Ollama model selector `#5108`) and breaking specific functions (file downloads `#5102`).
    - **Stability Issues on Desktop:** The Tauri client is "unusable" for some, with crashes and resource exhaustion (`#5106`).
    - **Rebranding Confusion:** The rename from `copaw` to `qwenpaw` has left residual directory paths (`~/.copaw` vs `~/.qwenpaw`) causing plugin and installation failures (`#5104`).
    - **Lack of Polish:** Users cite "chaotic" timestamps (`#5103`) and non-persistent UI blocks (`#5107`).

- **Satisfaction Signals:**
    - The community is actively contributing, submitting high-quality feature requests and first-time PRs for UI, security, and internationalization (`#5136`).
    - There is appreciation for the feature set (e.g., memory search, scheduled tasks) but frustration with their current reliability.

### 8. Backlog Watch

The following items require maintainer attention due to age or strategic importance:

- **`#4727` [Open] - Migrate backend to AgentScope 2.0:** This is a **critical breaking change** issue, opened on 2026-05-27, with 9 comments. It outlines the plan to migrate the entire backend. While planned, the current wave of stability bugs suggests this migration is stalled or happening behind the scenes. It needs a status update for the community.
- **`#3817` [Closed] - Long-term memory config persistence:** Although closed, this issue (opened 2026-04-24) describes a problem of vector model configs resetting on container restart. The fact that a very similar bug was just reported today (`#5137`) suggests the fix may have been incomplete or re-introduced.
- **`#1533` [Closed] - `install.sh` hanging:** A very old bug (March 2026) resolved, but it indicates a long-standing fragility in the installation script for new users.
- **PR `#4669` [Open] - Tauri Auto Updater:** Opened on 2026-05-25, this is a high-value feature that would directly mitigate the "download-and-reinstall" cycle users are facing with the buggy Tauri client (`#5106`). It has no activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-06-12

## Today's Overview

ZeroClaw is in a period of intense development activity with v0.8.0 freshly released, bringing the landmark "one daemon, many agents" architecture. The project shows 50 open issues and 48 open PRs updated in the last 24 hours, indicating a highly engaged community with significant backlog pressure. Two PRs were merged/closed today, suggesting steady but measured progress toward stabilizing the v0.8.0 release. The project maintains high velocity but faces substantial technical debt, with 26 out of 50 open issues tagged as risk:high and many carrying p1 priority designations.

## Releases

**v0.8.0** — published as "the big one" by the team

Key changes:
- Single daemon now manages multiple named agents, each with independent:
  - Workspace directory
  - Memory store
  - Model provider configuration
  - Security policy (risk profiles)
  - Communication channels
  - Personality/behavior settings
- Rewritten configuration schema with automated migration from previous versions
- New configuration schema supports typed aliased entries referencing each other by `<type>.<alias>` refs

Breaking changes:
- Configuration schema is rewritten; existing setups are automatically migrated
- Agents must now be explicitly named and configured per-agent
- Users should verify their `config.toml` after upgrade, particularly provider, agent, and channel definitions

No migration notes were published with the release, but the schema auto-migration should handle most existing setups.

## Project Progress

Two PRs merged/closed today:

- **#7520** `fix(ci): install cross g++ for ARM glibc release builds` — Critical CI fix that unblocks ARM release builds (aarch64, armv7, arm), which had been failing in the v0.8.0 Release Stable run. This is an infrastructure fix with no user-facing impact.

- **#7519** `fix(config): persist [[mcp.servers]] per-field edits via natural-key dirty-path walker` — Fixes a bug where per-field edits to MCP server configurations (shipped in #7267) were not being written to disk. The on-disk incremental writer was not taught about array-of-table natural keys. Now closed/merged.

No other feature branches advanced to merge today, though 48 open PRs remain in various states, many labeled `needs-author-action`.

## Community Hot Topics

**Most Active Issue:**
- **#5849** `[Feature]: Dream Mode — Periodic Memory Consolidation & Reflective Learning` (17 comments) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/5849)
  - User request for background memory consolidation during idle periods, similar to biological dreaming
  - Would enable reflective learning, long-term knowledge structure updates
  - Status: accepted, p2 priority — likely a future-phase feature

**High-Engagement Bugs:**
- **#6699** `tool_filter_groups is a no-op for real MCP tools` (7 comments) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6699)
  - Two distinct bugs: prefix mismatch in filter gate, no integration with deferred loading
  - p1 priority, status:in-progress
  - Affects all MCP tool users; no fix PR yet

- **#7470** `delegate agentic mode rejects empty risk_profile.allowed_tools` (7 comments) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7470)
  - Filed yesterday (2026-06-11), already 7 comments
  - Blocks practical multi-agent reviewer/research setups
  - Two coupled delegate-path bugs: empty allowed_tools rejection and same-profile gating blocking stricter targets
  - No fix PR yet; this is a critical blocker for v0.8.0's multi-agent feature

**Stale High-Collaboration PRs (no maintainer response):**
- **#5892** `fix(providers,runtime): three production blockers` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/5892)
  - Fixes vLLM tool_choice rejection, orphaned tool_use handling, vision capability detection
  - 3 reviewers' feedback, labeled `needs-author-action` for ~54 days

- **#6143** `feat(skills): universal skill registry support` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/6143)
  - Adds SkillRegistry trait for external skill sources
  - Blocked on author action, XL size PR

## Bugs & Stability

**Critical (S0 - data loss / security risk):**
- **#5542** `consecutive OOM in wsl2` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/5542)
  - Daemon killed by OOM killer with 8.4GB RSS
  - status:in-progress, r:needs-repro
  - No fix PR identified

**High Severity (S1 - workflow blocked):**
- **#7470** `delegate agentic mode rejects empty risk_profile.allowed_tools` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7470) (filed today)
- **#5808** `Default 32k context budget exceeded by system prompt + tool definitions on iteration 1` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/5808)
  - Perpetual preemptive trim from iteration 1; default budget is 3.3x too small
  - status:accepted, p1 priority, no fix PR
- **#6302** `Gemini 400 — assistant tool_call emitted as first non-system turn` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6302)
  - Fix PR #6303 exists but needs author action
- **#6361** `context_compression drops assistant(tool_calls) and tool(result) for OpenAI-compatible providers` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6361)
  - Causes tool loops for MiniMax users; fix PR #6362 exists but needs author action
- **#6434** `Shell tool calls refused at [autonomy] level = "full"` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6434)
- **#6699** `tool_filter_groups is a no-op for real MCP tools` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6699)
- **#6037** `Cron jobs can be launched repeatedly while running` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6037)
  - Fix PR #6038 exists but needs author action
- **#6224** `Cron Job Dispatch to WhatsApp Web` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6224)
  - Fix PR #6230 exists but needs author action
- **#6678** `Skill tools rejected by Anthropic API — tool name format violates `^[a-zA-Z0-9_-]{1,128}$`` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6678)
- **#6891** `Scheduled Jobs edit error API 422` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6891)
  - Web UI incompatibility with v0.8.0 schema

**Medium Severity (S2 - degraded behavior):**
- **#6173** `model_switch tool does not persist across turns` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6173)
- **#6350** `WhatsApp Web — allowed-numbers bypassed for LID-based contacts` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6350)
- **#6548** `Channel runtime command replies bypass Fluent localization` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6548)
- **#5903** `MCP stdio child processes accumulate on daemon with heartbeat.enabled=true` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/5903)
  - One orphan per tick; ~48 orphans per day at default interval

**Notable regressions in v0.8.0:**
- **#6891** — Web gateway Scheduled Jobs edit form incompatible with v0.8.0 schema (API 422 errors)
- **#7470** — Multi-agent delegation broke with strict risk_profile validation

## Feature Requests & Roadmap Signals

**High-priority user requests accepted for development:**
- **#6914** `feat: enforce allowed_tools / denied_tools in main agent loop` (p1, blocked) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6914)
  - Critical security feature; allowed_tools exists on Agent but is not wired to execution

- **#6312** `feat(gateway): per-alias webhook path routing for multi-instance channels` (p2, in-progress) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6312)
  - Follow-up to #7297 which landed `?agent=` per-request dispatch; this asks for path-based routing

**New feature requests with momentum:**
- **#5849** `Dream Mode — Periodic Memory Consolidation` (p2, accepted) — Likely a v0.9.0 candidate
- **#6391** `real heartbeat tracking for daemon nodes` (p2, blocked) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6391)
- **#6390** `zeroclaw node add <url> CLI — register a remote daemon` (p2, blocked)
- **#6823** `TUI ACP Bridge` (p2, accepted) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6823)

**Likely next-release candidates (v0.8.1 or v0.9.0):**
- Fix for #7470 (multi-agent delegation) — critical for v0.8.0's core value proposition
- Fix for #6699 (tool_filter_groups MCP bug) — blocks all MCP tool security policies
- Fix for #5808 (context budget) — affects every conversation
- Fix for #6678 (Anthropic skill tool names) — blocks Anthropic users from using skills

## User Feedback Summary

**Dissatisfaction / Pain Points:**
1. **Multi-agent delegation broken in v0.8.0** (#7470) — Users attempting to set up reviewer/research workflows with multiple agents are blocked. Filed yesterday, already 7 comments. This is the most urgent user-facing issue.

2. **MCP tool filtering non-functional** (#6699) — Users expecting `tool_filter_groups` to control MCP tool access find it has zero effect. Affects all MCP tool deployments.

3. **Context budget insufficient by default** (#5808) — "On iteration 1, already exceeds budget by ~3.3x" — every fresh conversation triggers preemptive trimming.

4. **Cron job reliability** (#6037, #6224) — Jobs run repeatedly (20x bursts) and WhatsApp delivery is broken. Fix PRs exist but have been pending author action for 50+ days.

5. **Web UI incompatibility with v0.8.0** (#6891) — Dashboard's Scheduled Jobs editor still uses v0.7.x schema, producing 422 errors.

**Satisfaction / Positive Signals:**
- v0.8.0 successfully shipped with multi-agent support — a major architectural milestone
- Active community contributions: 48 open PRs from diverse contributors
- Feature requests are being accepted and tracked systematically (p1/p2 priority, accepted/blocked statuses)

## Backlog Watch

**Long-stale issues needing maintainer attention:**
- **#5542** `consecutive OOM in wsl2` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/5542)
  - S0 severity, filed April 9 (64 days open), r:needs-repro, no maintainer response in 63 days
  - Data loss / security risk; WSL2 users may be silently losing work

**Long-stale PRs needing maintainer review or closure:**
- **#5892** `fix(providers,runtime): three production blockers` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/5892)
  - Filed April 19 (54 days), has 3 reviewers' feedback, labeled `needs-author-action`
  - Fixes three distinct provider bugs affecting vLLM, Gemini, and vision models

- **#6038** `fix(cron): add claim/release lock to prevent repeated job execution` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/6038)
  - Filed April 23 (50 days), needs author action, addresses #6037 (S1 bug)

- **#6230** `fix(cron): allow whatsapp as cron delivery channel` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/6230)
  - Filed April 30 (43 days), needs author action, addresses #6224 (S1 bug)

- **#5661** `feat(cron): wire CLI delivery flags, clean envelope, add announce + bounds` — [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/5661)
  - Filed April 12 (61 days), XL size, stale-candidate
  - Blocks cron announce features

**Missing maintainer responses on accepted issues:**
- **#6914** `enforce allowed_tools / denied_tools` — accepted since May 25 (18 days), blocked status
- **#6390** `zeroclaw node add <url> CLI` — accepted since May 5 (38 days), blocked status
- **#6391** `real heartbeat tracking` — accepted since May 5 (38 days), blocked status

The project's v0.8.0 release brought significant architectural improvements but introduced regressions in multi-agent workflows and web UI compatibility. The high ratio of stale PRs (11 of top 20 shown as `needs-author-action`) and the 64-day-old S0 OOM bug suggest the team may be stretched thin between advancing new features and maintaining existing ones.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*