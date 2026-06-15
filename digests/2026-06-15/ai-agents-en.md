# OpenClaw Ecosystem Digest 2026-06-15

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-15 04:13 UTC

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

# OpenClaw Project Digest — 2026-06-15

## 1. Today's Overview

OpenClaw is experiencing a **sustained high-volume incident period**, with 500 updated issues and 500 updated PRs in the last 24 hours. The project has **434 open/active issues** and **422 open PRs**, indicating an active but potentially strained triage pipeline. A new beta release, **v2026.6.8-beta.1**, was published today, focusing on richer Telegram and WhatsApp delivery, safer rich-media boundaries, and retired native draft migration. However, project health is under pressure: numerous **P1 Platinum Hermit and Diamond Lobster severity bugs** remain open, many with `needs-maintainer-review` and `needs-product-decision` labels, suggesting critical triage bottlenecks. Regression-related issues after the 2026.5.20–5.22 stable releases continue to dominate community reports.

---

## 2. Releases

**v2026.6.8-beta.1** — [View on GitHub](https://github.com/openclaw/openclaw/releases/tag/v2026.6.8-beta.1)

### Highlights
- **Telegram delivery:** Structured rich text with tables, lists, and expandable blockquotes now supported. CLI backend delivery improved with prompt-preserving behavior.
- **WhatsApp delivery:** Richer, more brittle delivery path with retired native draft migration.
- **Safer rich-media boundaries:** Reduced risk of content truncation or malformed messages at platform boundaries.

### Migration Notes
- Users on **native draft-based Telegram or WhatsApp formats** should verify their message formatting still renders correctly. The retired draft migration is one-way; rollback may require manual reconfiguration.
- No breaking changes explicitly called out in the release notes, but users of custom Telegram rich-text formatting should test thoroughly.

---

## 3. Project Progress

**Merged/Closed PRs Today:** 78 PRs merged or closed in the last 24 hours. Notable advances:

| PR | Title | Impact |
|---|---|---|
| [#87298](https://github.com/openclaw/openclaw/pull/87298) (merged) | test: add temp directory helper guidance | Improved test infrastructure; closes #78416's hard cleanup approach |
| [#86184](https://github.com/openclaw/openclaw/issues/86184), [#86090](https://github.com/openclaw/openclaw/issues/86090), [#85692](https://github.com/openclaw/openclaw/issues/85692), [#85192](https://github.com/openclaw/openclaw/issues/85192), [#84137](https://github.com/openclaw/openclaw/issues/84137), [#86231](https://github.com/openclaw/openclaw/issues/86231), [#91016](https://github.com/openclaw/openclaw/issues/91016) | Closed issues with resolved status | Various bug fixes and investigations closed |

**Features Advancing (Open PRs with active work):**
- [#88935](https://github.com/openclaw/openclaw/pull/88935): Shared tools bootstrap instructions (`TOOLS_SHARED.md`) with Codex integration
- [#88968](https://github.com/openclaw/openclaw/pull/88968): Prevent memory flush failure from aborting user replies (#85645)
- [#87478](https://github.com/openclaw/openclaw/pull/87478): Fix Codex project MCP OAuth config projection
- [#70990](https://github.com/openclaw/openclaw/pull/70990): Model failover and terminal failure hooks (XL-sized, maintainer attention needed)
- [#91476](https://github.com/openclaw/openclaw/pull/91476): `ultracode` backend flag for Claude CLI
- [#93157](https://github.com/openclaw/openclaw/pull/93157): Restore Codex usage quota pill in sidebar
- [#93125](https://github.com/openclaw/openclaw/pull/93125): Ordered model fallback chain for compaction (`compaction.fallbacks`)
- [#88750](https://github.com/openclaw/openclaw/pull/88750): Pass typed runtime settings into context-engine lifecycle
- [#87377](https://github.com/openclaw/openclaw/pull/87377): Task flow lifecycle observability (OTel/Prometheus)

---

## 4. Community Hot Topics

**Most Active Issues (by comment count):**

| Issue | Comments | Summary |
|---|---|---|
| [#87307](https://github.com/openclaw/openclaw/issues/87307) | 14 | Matrix thread replies regression: replies sent as normal instead of threaded, `/status` and `/model` silent. **P1 Platinum Hermit** |
| [#85888](https://github.com/openclaw/openclaw/issues/85888) | 12 | Cron jobs fail with MiniMax 503 overload during 05:00-07:30 CST. Manual triggers succeed. **P2 Diamond Lobster** |
| [#84516](https://github.com/openclaw/openclaw/issues/84516) | 11 | Codex agent replies silently truncated at ~1000 chars with `stop=null`. **P1 Platinum Hermit** |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | 9 | Telegram agent repeats replies 2-10x after 5.20 update. **P1 Diamond Lobster** |
| [#86996](https://github.com/openclaw/openclaw/issues/86996) | 9 | Active Memory + Codex app-server causes long latency, hook timeouts, startup aborts. **P1 Platinum Hermit** |
| [#86508](https://github.com/openclaw/openclaw/issues/86508) | 9 | `EmbeddedAttemptSessionTakeoverError` on Discord runs. **P1 Platinum Hermit** |
| [#85103](https://github.com/openclaw/openclaw/issues/85103) | 9 | Model fallback chain not triggered on provider-wide quota exhaustion. **P1 Platinum Hermit** |
| [#86538](https://github.com/openclaw/openclaw/issues/86538) | 8 | Session write-lock timeouts block subagent delivery lanes. **P1 Diamond Lobster** |
| [#86047](https://github.com/openclaw/openclaw/issues/86047) | 8 | Codex app-server/plugin approval stalls in Nextcloud Talk sessions. **P1 Platinum Hermit** |
| [#85251](https://github.com/openclaw/openclaw/issues/85251) | 8 | Codex app-server goes silent after `notification:turn/started`; session wedges for recovery window. **P1 Platinum Hermit** |

**Underlying Community Needs:**
- **Session and message reliability** is the dominant theme — users are experiencing lost messages, duplicate replies, stuck sessions, and silent failures across Matrix, Telegram, Discord, Nextcloud Talk, and WhatsApp.
- **Model fallback and provider resilience** — cron jobs failing on MiniMax overloads, fallback chains not triggering, Anthropic socket failures silently swapping providers.
- **Codex app-server integration** is a major pain point: truncated replies, stalled turns, OAuth refresh failures, event-loop blocking by single stalled sessions.

**Most Reacted Issues:**
- [#91016](https://github.com/openclaw/openclaw/issues/91016) — 5 👍: DeepSeek Prompt Cache completely broken after 2026.6.1 upgrade, costing ~$6/hour
- [#86508](https://github.com/openclaw/openclaw/issues/86508) — 4 👍: Discord `EmbeddedAttemptSessionTakeoverError`
- [#77467](https://github.com/openclaw/openclaw/issues/77467) — 3 👍: MiniMax Portal OAuth cannot auto-refresh

---

## 5. Bugs & Stability

**Critical (P1, Platinum Hermit) — Active:**

| Issue | Description | Fix PR? |
|---|---|---|
| [#87307](https://github.com/openclaw/openclaw/issues/87307) | Matrix thread replies sent as normal replies | No fix PR open; needs maintainer review |
| [#84516](https://github.com/openclaw/openclaw/issues/84516) | Codex agent replies truncated at ~1000 chars | No fix PR open; needs live repro |
| [#86996](https://github.com/openclaw/openclaw/issues/86996) | Active Memory + Codex: long latency, hook timeouts, startup aborts | No fix PR open; needs live repro |
| [#86508](https://github.com/openclaw/openclaw/issues/86508) | Discord `EmbeddedAttemptSessionTakeoverError` | No fix PR open; needs live repro |
| [#85103](https://github.com/openclaw/openclaw/issues/85103) | Model fallback chain not triggered on quota exhaustion | No fix PR open; needs live repro |
| [#86047](https://github.com/openclaw/openclaw/issues/86047) | Codex app-server stalls in Nextcloud Talk | No fix PR open; needs product decision |
| [#85251](https://github.com/openclaw/openclaw/issues/85251) | Codex app-server goes silent mid-turn; session wedges | No fix PR open; needs live repro |
| [#84903](https://github.com/openclaw/openclaw/issues/84903) | Single stalled session blocks entire Gateway event loop | No fix PR open; needs live repro |
| [#86572](https://github.com/openclaw/openclaw/issues/86572) | `withOwnedSessionTranscriptWrites` ALS scope missing pi's listener writes | Fix PR [#86572](https://github.com/openclaw/openclaw/pull/86572) open |

**High Severity (P1, Diamond Lobster) — Active:**

| Issue | Description | Fix PR? |
|---|---|---|
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | Agent repeats replies 2-10x on Telegram after 5.20 | No fix PR open; needs product decision |
| [#86538](https://github.com/openclaw/openclaw/issues/86538) | Session write-lock timeouts block subagent lanes | Fix PR [#86538](https://github.com/openclaw/openclaw/pull/86538) open |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | MCP tools not injected into subagent sessions | No fix PR open; needs security review |
| [#83184](https://github.com/openclaw/openclaw/issues/83184) | Heartbeat-driven replies leave `pendingFinalDelivery` stuck | Fix PR [#83184](https://github.com/openclaw/openclaw/pull/83184) open |
| [#45494](https://github.com/openclaw/openclaw/issues/45494) | Cron jobs silently time out on sustained API errors | No fix PR open; needs product decision |

**Today's New P1 Issues:**
- [#87417](https://github.com/openclaw/openclaw/issues/87417): `EmbeddedAttemptSessionTakeoverError` on all isolated `agentTurn` cron jobs
- [#87407](https://github.com/openclaw/openclaw/issues/87407): Anthropic `UND_ERR_SOCKET` keep-alive failures trigger silent fallback to OpenAI/Codex (regression)

**Regressions (labeled `regression`):**
- [#86519](https://github.com/openclaw/openclaw/issues/86519): Telegram duplicate replies (5.20 → present)
- [#86508](https://github.com/openclaw/openclaw/issues/86508): Discord `EmbeddedAttemptSessionTakeoverError` (after update)
- [#86047](https://github.com/openclaw/openclaw/issues/86047): Nextcloud Talk agent stalls (5.12 → 5.22)
- [#87407](https://github.com/openclaw/openclaw/issues/87407): Anthropic socket failures (regression)
- [#45494](https://github.com/openclaw/openclaw/issues/45494): Cron job timeout behavior (regression, open since March)

**Immediate Safety Concern:**
- [#87407](https://github.com/openclaw/openclaw/issues/87407) — Anthropic `UND_ERR_SOCKET` failures cause **silent mid-turn provider fallback to OpenAI/Codex** without user notification. PR [#87480](https://github.com/openclaw/openclaw/pull/87480) proposes fixing the undici keep-alive configuration.

---

## 6. Feature Requests & Roadmap Signals

**Notable User-Requested Features:**

| Issue | Feature | Community Demand |
|---|---|---|
| [#86881](https://github.com/openclaw/openclaw/issues/86881) | Gateway-lite mode: AI-free deployments for channel gateways, webhooks, cron scheduling | 7 comments, P2 |
| [#85461](https://github.com/openclaw/openclaw/issues/85461) | Capture image-generation provider usage metadata | 6 comments, P2 |
| [#74077](https://github.com/openclaw/openclaw/issues/74077) | Slash command to set preview streaming mode per session | 5 comments, P3 (stale) |
| [#87362](https://github.com/openclaw/openclaw/issues/87362) | Emit task flow lifecycle hook events for plugin observability | 4 comments; **PR #87377 already open** |
| [#44395](https://github.com/openclaw/openclaw/issues/44395) | Heading-aware chunking + entity extraction for memory search | 5 comments, P2 (open since March) |

**Predictions for Next v2026.6.x Stable:**
- **Task flow observability** (#87362) is likely to land soon given the active XL PR (#87377)
- **Compaction fallback chain** (#93125) is a targeted fix for a common production pain point
- **Shared tools bootstrap** (#88935) addresses a documented configuration gap
- **Codex usage quota pill restoration** (#93157) is a small UX fix for Web UI
- **Memory flush failure handling** (#88968) addresses a critical user-facing reliability issue

**Ongoing Roadmap Items:**
- [#86881](https://github.com/openclaw/openclaw/issues/86881) (Gateway-lite) has `needs-product-decision` — significant architectural decision pending
- [#86217](https://github.com/openclaw/openclaw/issues/86217) (iOS background location claims) has `needs-security-review`
- [#84516](https://github.com/openclaw/openclaw/issues/84516) (Codex truncation) has `needs-live-repro` — maintainer cannot reproduce

---

## 7. User Feedback Summary

**Common Pain Points (from issue comments):**
- ❗ **Duplicate replies on Telegram** (#86519, #88951, #83184): Users report 2-10x duplicate agent responses starting after v2026.5.20. Downgrading or upgrading to 5.22 reduces but doesn't eliminate the issue.
- ❗ **Silent session failures**: Multiple reports of sessions entering `failed` state with no user notification (#86827, #84536). Messages are silently dropped.
- ❗ **Codex app-server instability**: Truncated replies (#84516), stalled turns (#85251, #86047), OAuth refresh failures (#86215), event-loop blocking (#84903). Users express frustration at the "silent" nature of failures.
- ❗ **Provider resilience gaps**: MiniMax cron failures (#85888), Anthropic socket failures (#87407), DeepSeek cache invalidation (#86063, #91016). Users spending extra money on failed retries.
- ❗ **EmbeddedAttemptSessionTakeoverError** (#86508, #87417, #85103, #86572): A recurring, poorly understood race condition affecting Discord, cron jobs, and subagents.

**Satisfaction Signals:**
- ✅ Active community engagement with detailed bug reports and reproduction steps (14 comments on #87307, 12 on #85888)
- ✅ Multiple users have tried workarounds (downgrading, pinning models, `doctor --fix`) indicating willingness to troubleshoot
- ✅ Some issues are being actively worked: 6 fix PRs open for high-severity bugs (#86538, #83184, #86572, #88968, #87480, #87471)

**Use Cases Represented:**
- Personal assistants (Telegram, Discord, WhatsApp DMs)
- Group chat agents (Telegram groups, Discord channels, Nextcloud Talk)
- Cron/automation jobs (scheduling, monitoring)
- Enterprise/team deployments (shared agents, MCP tool integration)

---

## 8. Backlog Watch

**Critical Issues Needing Maintainer Attention (stale or unaddressed for weeks):**

| Issue | Created | Status | Why Critical |
|---|---|---|---|
| [#45494](https://github.com/openclaw/openclaw/issues/45494) | 2026-03-13 | Open, P1, needs-maintainer-review, needs-product-decision | **Cron jobs silently time out** on sustained API errors instead of fast-failing. Open for 3 months. |
| [#44395](https://github.com/openclaw/openclaw/issues/44395) | 2026-03-12 | Open, P2, needs-maintainer-review, needs-product-decision | **Memory chunking uses fixed-size characters, ignoring document structure.** Open for 3 months. |
| [#74077](https://github.com/openclaw/openclaw/issues/74077) | 2026-04-29 | Open, P3, stale label | **Slash command for streaming mode** — stale, no engagement in 6 weeks. |
| [#77467](https://github.com/openclaw/openclaw/issues/77467) | 2026-05-04 | Open, P1, needs-maintainer-review, needs-live-repro | **MiniMax Portal OAuth cannot auto-refresh** — 5 comments, 3 👍, open 6 weeks. |
| [#83184](https://github.com/openclaw/openclaw/issues/83184) | 2026-05-17 | Open, P1, fix PR open | **Heartbeat-driven replies leave pendingFinalDelivery stuck** — fix PR exists but not merged. |

**PRs Stuck in Review (Status: "waiting on author" or "needs proof"):**

| PR | Created | Status | Notes |
|---|---|---|---|
| [#70990](https://github.com/openclaw/openclaw/pull/70990) | 2026-04-24 | Waiting on author | **XL-sized feature: model failover hooks** — stale for 52 days |
| [#87478](https://github.com/openclaw/openclaw/pull/87478) | 2026-05-28 | Waiting on author | Codex MCP OAuth config fix |
| [#87414](https://github.com/openclaw/openclaw/pull/87414) | 2026-05-27 | Waiting on author | llama.cpp session keying |
| [#87349](https://github.com/openclaw/openclaw/pull/87349) | 2026-05-27 | Waiting on author | Host-local APK media sends |
| [#73399](https://github.com/openclaw/openclaw/pull/73399) | 2026-04-28 | Automerge armed, human-review needed | Feishu DM fallback — stale for 48 days |

**Issues Blocked on Maintainer Input:**
- **15+ issues** with `needs-product-decision` label (including #86519, #86047, #86538, #85030, #86063, #45494, #86090, #86342, #85692, #86217, #85822, #85246, #91016, #44395)
- **10+ issues** with `needs-live-repro` label where maintainers cannot reproduce the bug

**Recommendation:** The project's triage pipeline is heavily bottlenecked on maintainer review and product decisions. Consider a dedicated triage session or community maintainer delegation to clear the `needs-maintainer-review` and `needs-product-decision` backlog, especially for the 3-month-old P1 cron timeout issue (#45494) and the Codex session-wedging pattern (#85251, #86047).

---

## Cross-Ecosystem Comparison

# Cross-Project Comparison Report: Personal AI Agent Open-Source Ecosystem

## 1. Ecosystem Overview

The personal AI agent open-source ecosystem is experiencing a maturation phase characterized by intense focus on reliability, security, and extensibility. June 15, 2026 saw over 200 issues and 180 PRs updated across 12 monitored projects, with incident-response patterns dominating activity in the largest codebases. The ecosystem is converging on multi-provider resilience, agent delegation frameworks, and approval-security hardening as critical differentiators, while diverging on channel strategy (rich-media vs. lightweight) and deployment model (gateway-lite vs. full-stack). Community engagement remains healthy—users are filing detailed bug reports with reproduction steps—but maintainer bandwidth is emerging as the primary bottleneck for several flagship projects.

## 2. Activity Comparison

| Project | Open Issues | Updated Issues (24h) | Open PRs | Updated PRs (24h) | Releases (24h) | Health Score* |
|---|---|---|---|---|---|---|
| **OpenClaw** | 434 | 500 | 422 | 500 | 1 (beta) | ⚠️ **Strained** |
| **Hermes Agent** | 42 | 50 | 43 | 50 | 0 | ⚠️ **Strained** |
| **IronClaw** | 36 | 43 | 33 | 48 | 0 | ✅ **Healthy** |
| **ZeroClaw** | 42 | 42 | 50 | 50 | 0 | ✅ **Healthy** |
| **NanoBot** | 5 | 5 | 19 | 46 | 0 | ✅ **Healthy** |
| **CoPaw** | 24 | 24 | 17 | 17 | 0 | ⚠️ **Strained** |
| **PicoClaw** | 4 | 5 | 4 | 9 | 1 (nightly) | ✅ **Healthy** |
| **NanoClaw** | 7 | 7 | 10 | 10 | 0 | ⚠️ **Strained** |
| **LobsterAI** | 2 | 2 | 3 | 3 | 0 | ✅ **Healthy** |
| **NullClaw** | 1 | 1 | 0 | 0 | 0 | 🟢 **Quiet** |
| **Moltis** | 1 | 1 | 0 | 0 | 0 | 🟢 **Quiet** |
| **TinyClaw** | 0 | 0 | 0 | 0 | 0 | 🟢 **Inactive** |
| **ZeptoClaw** | 0 | 0 | 0 | 0 | 0 | 🟢 **Inactive** |

*\*Qualitative assessment: issue triage velocity, fix PR availability, maintainer response time*

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Largest community base**: 434 open issues vs. 42 (Hermes) and 36 (IronClaw)—indicates broader adoption but also triage strain
- **Maturity in channel diversity**: Richer Telegram/WhatsApp support (structured tables, expandable blockquotes) than NanoBot or PicoClaw
- **Active incident response**: 78 PRs merged/closed today—outpacing Hermes (7) and IronClaw (15) in raw throughput

**Technical Approach Differences:**
- OpenClaw favors a **monolithic gateway architecture** with deep platform-specific optimization (Telegram, WhatsApp), while peers like Hermes and IronClaw are pivoting to **extension-based channel models** (Slack as product-adapter, out-of-tree channels)
- OpenClaw's **Active Memory + Codex app-server** integration is more tightly coupled than NanoBot's stateless agent loop or ZeroClaw's delegation framework

**Community Size Comparison:**
- 500 updated issues/PRs daily vs. 50 for Hermes and IronClaw—suggests 5-10x more active contributors, but also higher noise
- 3-month-old P1 cron bug (#45494) still open vs. NanoBot closing bugs within 1-2 days → maintainer ratio is a weakness

**Risk**: OpenClaw's triage bottleneck (15+ `needs-product-decision`, 10+ `needs-live-repro`) is the most severe in the ecosystem. The P1 Platinum Hermit bugs with no fix PRs (7 issues) exceed Hermes Agent's total P1 count (2).

## 4. Shared Technical Focus Areas

The following requirements emerged across **3+ projects simultaneously**, indicating ecosystem-wide priorities:

| Requirement | Projects | Specific Needs |
|---|---|---|
| **Multi-provider resilience** | OpenClaw, Hermes, IronClaw, ZeroClaw, NanoClaw | Silent fallback when provider overloaded (OpenClaw #85888, #85103); auto-failover chains (IronClaw #4864); budget exhaustion handling (NanoClaw #2751); provider credential isolation (Hermes #46411) |
| **Approval/security hardening** | IronClaw, Hermes, ZeroClaw, NanoClaw | Shell command bypass via env wrappers (IronClaw #4865, #4864); credential exfiltration across profiles (Hermes #46411, #46413); MCP approval resume failures (NanoClaw #2762); `extra_args` validation (ZeroClaw #5842) |
| **Agent delegation & tool passthrough** | ZeroClaw, IronClaw, OpenClaw, NanoBot | Delegate agents invisible to MCP tools (ZeroClaw #7608, #6136); subagent session contamination (OpenClaw #86572, #84903); tool config refactoring for non-root agents (NanoBot #4344, #4274) |
| **Mobile/Web UI responsiveness** | OpenClaw, IronClaw, CoPaw, PicoClaw | Settings clipping off-screen (IronClaw #4868); Safari iOS <16.4 failure (PicoClaw #3090); slow Tauri startup on Windows (CoPaw #5061); mobile-responsive WebUI (NanoBot #4339) |
| **Channel extensibility** | PicoClaw, IronClaw, NanoClaw, ZeroClaw | RegisterChannelSettings hook (PicoClaw #3120); Slack as extension (IronClaw #4778); out-of-tree channel model (NanoClaw #2756); WeChat Work enterprise integration (CoPaw #5190) |
| **Observability & telemetry** | OpenClaw, IronClaw, NanoBot, LobsterAI | Task flow lifecycle hooks (OpenClaw #87377 → merged); trajectory observer pattern (IronClaw #4588); OTel/Prometheus integration (OpenClaw); runtime context for models (IronClaw #4836 → merged) |

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | ZeroClaw | NanoBot | CoPaw | PicoClaw |
|---|---|---|---|---|---|---|---|
| **Target User** | Power user, enterprise deployer | Developer, plugin author | Internal dogfooder, extension dev | Early adopter, integrator | Developer, API user | Enterprise Chinese market | Hobbyist, self-hoster |
| **Channel Strategy** | Deep native integration (Telegram, WhatsApp) | Broad but shallow (Matrix, Discord, SimpleX) | Extension-based (Slack first, others follow) | SMS channels (Vonage, Sinch, Plivo) | Minimal (WebUI, Telegram) | Enterprise Chinese (WeChat Work, Feishu, DingTalk) | Pragmatic (Matrix, Telegram, web panel) |
| **Architecture** | Monolithic gateway | Profile-based containers | Reborn WebUI v2 with extensions | Delegation + MCP passthrough | Lightweight agent loop | Tauri desktop + plugin system | Minimal core + PRs for features |
| **Differentiator** | Rich-media fidelity | Plugin extensibility | Dogfooding-driven QA | Feature burst velocity | Config/UI parity | Chinese enterprise + i18n | Simplicity |
| **Weakness** | Triage bottleneck | Security gaps | First-run UX | Documentation lag | Low engagement | Windows stability | Small committer base |
| **Release Cadence** | Beta weekly, stable monthly | v0.16.0 (June 5) | Pre-0.29.1 RC | Patch-heavy | No recent release | v1.1.11.post2 | Nightly builds |

## 6. Community Momentum & Maturity

**Tier 1: High Velocity (10+ PRs merged daily)**
- **ZeroClaw**: Strongest momentum—50 updated PRs, feature burst (SMS, smart home, providers), active delegation fixes. Risk: documentation and governance lagging behind code output.
- **OpenClaw**: Highest raw activity but "busy firefighting" pattern. 78 merged PRs vs. 434 open issues—triage cannot keep pace. The beta release cadence suggests maturation, but P1 bugs with no fix PRs (7) erode confidence.
- **NanoBot**: 27 merged PRs with 0 new bugs reported—exemplary maintainer bandwidth ratio (5:1 merged-to-open). Clear candidate for a stable release soon.

**Tier 2: Rapid Iteration (3-10 PRs merged daily)**
- **IronClaw**: 15 merged PRs with strong dogfooding QA. Pre-release mode (0.24.0→0.29.1) indicates major version approaching. Extension model and observability seams are strategic advantages.
- **Hermes Agent**: 7 merged PRs, but open-to-closed ratio (6:1) and 2 new security advisories today suggest maintainer team is stretched. The Unsloth Studio plugin and OAuth hardening are promising.

**Tier 3: Stabilizing (1-3 PRs merged daily)**
- **CoPaw**: 6 merged PRs, but critical Windows regression post v1.1.11.post2. Vietnamese locale contributions indicate untapped community growth. Needs hotfix to restore confidence.
- **PicoClaw**: 5 merged PRs—focused on error handling hygiene. Low engagement but steady. Nightly builds indicate active development toward v0.2.9 stable.
- **NanoClaw**: 5 merged PRs, but 3 critical security advisories today signal a pivot from feature velocity to security hardening. Codex v2 integration is ambitious.

**Tier 4: Low Activity / Maintenance**
- **LobsterAI**: 1 merged PR (artifact sharing). Stale PRs (60+ days) and unanswered i18n bug suggest maintainer attention is elsewhere.
- **NullClaw**: 1 new issue (Azure auth), 0 PRs. Minimal but targeted community contribution.
- **Moltis**: 1 new issue, 0 PRs. Post-v0.7.0 quiet period.
- **TinyClaw, ZeptoClaw**: Inactive. Projects may be abandoned or in hibernation.

## 7. Trend Signals

### Industry Trends Extracted from Community Feedback

1. **"Provider lock-in is dead"** — Every project is investing in multi-provider fallback chains (OpenClaw, ZeroClaw, NanoBot) and provider-switching UX (NanoClaw operator-driven selection). Users are actively mixing Anthropic, OpenAI, Gemini, MiniMax, and local models in single sessions. The ecosystem is converging on provider-agnostic orchestration.

2. **"Security is the new UX frontier"** — The simultaneous discovery of shell approval bypasses (IronClaw), credential exfiltration vectors (Hermes), and MCP tool approval flaws (NanoClaw) signals that agent security is where the next major UX battles will be fought. Users are demanding informed consent (visible command text, OAuth guidance, approval audit trails) before trusting agents with file system or shell access.

3. **"Memory is the killer app—but nobody has solved it"** — Multiple projects are wrestling with memory injection clarity (Hermes #31584), cache invalidation costs (OpenClaw #91016: $6/hour), and context growth performance issues (Hermes #46090). The community is signaling that "dumb" context-window-packing is insufficient—users want heading-aware chunking, entity extraction, and semantic search (OpenClaw #44395).

4. **"Enterprise adoption is happening—messily"** — Enterprise WeChat (CoPaw), Slack as extension (IronClaw), Google Workspace OAuth (Hermes), and Azure identity-based auth (NullClaw) are all being requested simultaneously. The ecosystem lacks a unified enterprise deployment playbook, and each project is implementing custom solutions for compliance (audit logging, approval workflows, credential isolation).

5. **"AI-assisted coding is the primary onboarding path"** — Multiple first-time contributors (CoPaw Vietnamese locale, ZeroClaw feature burst) are filing PRs with AI-generated code (evidenced by coding patterns). The CLAUDE.md documentation fixes (NanoClaw #2764) explicitly target AI coding assistants. Projects that optimize for AI-assisted contribution (clear CONTRIBUTING docs, structured issue templates, predictable API surfaces) are seeing higher contribution velocity.

### Value for AI Agent Developers

- **Adopt extension-based architectures early**: IronClaw and PicoClaw's shift to out-of-tree channel models is the ecosystem's architectural consensus. Monolithic gateways (OpenClaw) create triage debt.
- **Invest in approval UX**: The shell bypass bugs demonstrate that approval dialogs are the last line of defense. Show users the actual command, not "Capability: builtin.shell". Build audit trails.
- **Default to provider-agnostic**: Users are running 3-5 providers in parallel. Design your agent loop to handle silent failover, credential rotation, and latency variance across providers transparently.
- **Prioritize memory performance over features**: DeepSeek cache invalidation costing $6/hour (OpenClaw) and context growth degrading to "hours per task" (Hermes) are real user pain points. Memory systems need cost visibility and structure-aware chunking.
- **Plan for cross-profile isolation**: Active directory-style deployments are emerging where enterprises run shared agent instances across teams. Credential isolation (Hermes #46411) and session scoping are non-negotiable for multi-tenant deployments.
- **Dogfood aggressively**: IronClaw's weekly dogfooding cycles produce the most actionable bug reports (14 issues in one batch). Internal usage before public release catches UX gaps (provider showing "ACTIVE" when unconfigured) before they hit new users.

---

**Bottom Line for Decision-Makers**:
- **Invest in ZeroClaw** if you need rapid feature iteration and channel diversity (SMS, smart home)
- **Invest in NanoBot** if you value stability, maintainer responsiveness, and clean API surfaces
- **Watch IronClaw** for the extension model pattern—it's likely to become the ecosystem reference architecture
- **Contribute to OpenClaw** with caution—high impact potential but triage queues are the bottleneck
- **Avoid TinyClaw and ZeptoClaw** for production deployments until activity resumes

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-06-15

## Today's Overview
NanoBot shows **high development velocity** with 46 PRs updated in the last 24 hours and a strong 27 merged/closed rate, indicating active maintainer response. Community engagement is moderate with 5 issues updated, though two critical bugs were freshly reported today. The project has no new releases, but the sheer volume of merged PRs (27) suggests a substantial release may be forthcoming. Overall project health appears **robust**, with major refactoring work ongoing in configuration architecture and agent loop boundaries.

## Releases
*No new releases today.* The last release date is not available from today's data, though the high volume of merged PRs (27 closed) suggests a release may be imminent.

## Project Progress
**27 PRs merged/closed today**, advancing several key areas:

- **Documentation & Onboarding**: PR #4177 reworked docs entry points for beginners; PR #4245 removed old nightly branch guidance ([PR #4177](https://github.com/HKUDS/nanobot/pull/4177), [PR #4245](https://github.com/HKUDS/nanobot/pull/4245))
- **WebUI Enhancements**: PR #4313 closed the gap between WebUI settings and `config.json`; PR #4248 fixed token usage heatmap rendering; PR #4339 improved mobile responsiveness ([PR #4313](https://github.com/HKUDS/nanobot/pull/4313), [PR #4248](https://github.com/HKUDS/nanobot/pull/4248), [PR #4339](https://github.com/HKUDS/nanobot/pull/4339))
- **Agent Loop Improvements**: PR #4269 added no-tools finalization when max iterations hit; PR #4274 scoped prompt history by session ([PR #4269](https://github.com/HKUDS/nanobot/pull/4269), [PR #4274](https://github.com/HKUDS/nanobot/pull/4274))
- **Configuration & Schema**: PR #4314 broke tool config schema import cycles; PR #4275 added fail-fast on invalid config files ([PR #4314](https://github.com/HKUDS/nanobot/pull/4314), [PR #4275](https://github.com/HKUDS/nanobot/pull/4275))
- **Filesystem Tools**: PR #4138 added `tools.file.enable` toggle for built-in filesystem tools ([PR #4138](https://github.com/HKUDS/nanobot/pull/4138))
- **Channel Fixes**: PR #4277 lazy-loaded lark SDK for Feishu channel startup ([PR #4277](https://github.com/HKUDS/nanobot/pull/4277))
- **Cron & Automation**: PR #4299 bound scheduled automations to sessions ([PR #4299](https://github.com/HKUDS/nanobot/pull/4299))

## Community Hot Topics

1. **WebUI/config.json Parity** (PR #4313, 0 comments, open) — A significant feature PR adding 40+ new WebUI settings endpoints. The underlying need is **configuration consistency** between CLI and UI workflows. [PR #4313](https://github.com/HKUDS/nanobot/pull/4313)

2. **Agent Loop Refactoring** (PR #4344, 0 comments, open) — Moving tool config models into side-effect-free modules. Signals a **long-term architectural cleanup** to decouple agent logic from configuration. [PR #4344](https://github.com/HKUDS/nanobot/pull/4344)

3. **Automation Management View** (PR #4330, 0 comments, open) — New WebUI surface for listing/filtering/running automations. Community interest in **user-facing automation controls** beyond cron configuration. [PR #4330](https://github.com/HKUDS/nanobot/pull/4330)

4. **Subagent Result Injection Fix** (PR #4293, 0 comments, open) — Fixes `process_direct()` to handle subagent results. Critical for **cron jobs that spawn subagents** — a niche but important stability concern. [PR #4293](https://github.com/HKUDS/nanobot/pull/4293)

5. **Image Fallback Leak** (Issue #4345, 0 comments, new today) — Image-strip fallback leaks file paths and hallucinates image content. **High community concern** due to potential data exposure. [Issue #4345](https://github.com/HKUDS/nanobot/issues/4345)

## Bugs & Stability

### High Severity
- **Image path leak** (Issue #4345, [OPEN], reported today) — The `_strip_image_content` fallback leaks the server file path into the model's view and makes the model hallucinate seeing an image. **Fix PR #4346 opened same day** ([Issue #4345](https://github.com/HKUDS/nanobot/issues/4345), [PR #4346](https://github.com/HKUDS/nanobot/pull/4346))
- **Zero token usage in API** (Issue #4309, [OPEN], updated yesterday) — `/v1/chat/completions` always returns zero tokens even though agent loop tracks real usage. **No fix PR yet** ([Issue #4309](https://github.com/HKUDS/nanobot/issues/4309))

### Medium Severity
- **Anthropic `temperature` deprecated for opus-4-8** (Issue #4333, [CLOSED]) — Only opus-4-7 was exempted; fixed and closed within 1 day ([Issue #4333](https://github.com/HKUDS/nanobot/issues/4333))
- **Telegram fenced code blocks broken** (Issue #4250, [CLOSED]) — `split_message` split inside ` ``` ` fences; fixed and closed ([Issue #4250](https://github.com/HKUDS/nanobot/issues/4250))

### Low Severity / Enhancement
- **botIcon not used at startup** (Issue #4262, [CLOSED]) — "puppy" shown instead of configured botIcon on first agent entry; resolved ([Issue #4262](https://github.com/HKUDS/nanobot/issues/4262))
- **Unknown builtin parameters accepted** (PR #4343, [OPEN]) — Tool parameter validation not honoring `additionalProperties`; fix in progress ([PR #4343](https://github.com/HKUDS/nanobot/pull/4343))
- **Empty injected payloads** (PR #4337, [OPEN]) — Blank user messages from empty injection payloads; fix proposed ([PR #4337](https://github.com/HKUDS/nanobot/pull/4337))

## Feature Requests & Roadmap Signals

| Feature | Signal | Likelihood for Next Release |
|---------|--------|---------------------------|
| WebUI/config.json parity (40+ new settings) | PR #4313 merged | ✅ Very High |
| Automation management UI | PR #4330 open | ✅ High — likely follows PR #4313 |
| pathPrepend for exec tool | PR #4273 merged | ✅ Already shipped |
| filesystem tools enable toggle | PR #4138 merged | ✅ Already shipped |
| Session-scoped history | PR #4274 merged | ✅ Already shipped |
| Mobile-responsive WebUI | PR #4339 merged | ✅ Already shipped |
| Subagent injection for `process_direct` | PR #4293 open | ⏳ Medium — critical but niche |
| Fail-fast on bad config | PR #4275 merged | ✅ Already shipped |

**Prediction**: The next release will likely include the massive WebUI settings overhaul (PR #4313), automation management (PR #4330), and the agent loop config refactoring (PR #4344).

## User Feedback Summary

**Pain Points:**
1. **Image handling bugs** (Issue #4345) — Users report models hallucinating images they never received, plus file path disclosure. This is a **data leak concern**.
2. **Zero token tracking** (Issue #4309) — Users relying on API token usage reporting get zero values, breaking cost tracking.
3. **Telegram formatting** (Issue #4250) — Code blocks in long messages render broken HTML (now fixed).
4. **Anthropic model compatibility** (Issue #4333) — Latest Claude models rejected with 400 errors (now fixed).

**Satisfaction Signals:**
- Users requesting enhancements (Issue #4262 for botIcon) had their feature implemented and closed.
- Multiple user-facing fixes (Telegram, Anthropic) were resolved within days.
- The volume of community contributions (27 merged PRs) indicates an **active and engaged contributor base**.

## Backlog Watch

**No long-unanswered items detected in today's snapshot.** All open issues have been updated within the last 3 days, suggesting maintainers are responding promptly. The zero-token usage bug (Issue #4309, since June 12) is the oldest open item without a fix PR, but it's only 3 days old. PRs that may need review attention:

- **PR #4346** (Image fallback fix, opened today) — Should be prioritized due to data leak severity
- **PR #4343** (Reject unknown params, opened June 14) — Important for tool call reliability
- **PR #4337** (Skip empty payloads, opened June 14) — Important for injection stability

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest

**Date:** 2026-06-15  
**Repository:** [NousResearch/hermes-agent](https://github.com/nousresearch/hermes-agent)

---

## Today's Overview

Hermes Agent is experiencing **high activity** with 50 issues and 50 PRs updated in the last 24 hours. The project maintains strong momentum with active community engagement, though the **open-to-closed ratio** (42 open vs. 8 closed issues; 43 open vs. 7 merged/closed PRs) suggests the maintainer team is struggling to keep pace with incoming reports. Two **P1-severity bugs** (Matrix E2EE exhaustion and session cross-contamination) and two newly filed **security vulnerabilities** (credential exfiltration across profiles) indicate critical areas needing immediate attention. No new releases were published today.

---

## Releases

No releases were published today. The last known release is **Hermes Agent v0.16.0 (2026.6.5)** referenced in recent bug reports.

---

## Project Progress

### Merged/Closed Pull Requests Today (7 total)

| PR | Description | Fixes |
|---|---|---|
| [#46289](https://github.com/nousresearch/hermes-agent/pull/46289) | **fix(s6): clear stale log lock before startup** – Prevents virtiofs-backed containers from stuck logger startup loops | Infrastructure stability |
| [#46292](https://github.com/nousresearch/hermes-agent/pull/46292) | **fix(s6): persist profile gateway desired state** – Restores operator intent after container restarts | Docker reliability |
| [#46348](https://github.com/nousresearch/hermes-agent/pull/46348) | **fix(agent): respect disabled_toolsets in memory provider injection** – Prevents memory tools from leaking into disabled tool surfaces | Issue [#46171](https://github.com/nousresearch/hermes-agent/issue/46171) |

### Active Progress (Open PRs with Recent Updates)

- **Systemd PATH fix** ([#46315](https://github.com/nousresearch/hermes-agent/pull/46315)): Makes generated service unit PATH deterministic across profiles
- **Matrix media send fix** ([#46407](https://github.com/nousresearch/hermes-agent/pull/46407)): Reuses single adapter to avoid E2EE key exhaustion (fixes P1 issue [#46310](https://github.com/nousresearch/hermes-agent/issue/46310))
- **Post-update model smoke check** ([#46433](https://github.com/nousresearch/hermes-agent/pull/46433)): Prevents dark chat after failed model updates
- **Unsloth Studio plugin** ([#46451](https://github.com/nousresearch/hermes-agent/pull/46451)): New standalone local fine-tuning plugin (closes [#46450](https://github.com/nousresearch/hermes-agent/issue/46450))
- **Hindsight local timestamps + Discord fixes** ([#46449](https://github.com/nousresearch/hermes-agent/pull/46449)): Three-bug fix batch addressing timezone, deferral, and rename issues
- **Google Workspace OAuth hardening** ([#21774](https://github.com/nousresearch/hermes-agent/pull/21774)): Adds service-scoped setup and JSON format responses

---

## Community Hot Topics

### Most Discussed Issues

1. **[#7237](https://github.com/nousresearch/hermes-agent/issue/7237) – Response truncated due to output length limit** (46 comments, 👍6)  
   **Status:** CLOSED  
   **Analysis:** The highest-comment issue in the project remains a long-standing pain point. The truncation error breaks long-form responses in CLI, Telegram, Discord, and Slack gateways. Though closed, this has been a recurring frustration for users generating substantial content.

2. **[#25267](https://github.com/nousresearch/hermes-agent/issue/25267) – Claude Agent SDK with subscription OAuth** (7 comments, 👍21)  
   **Status:** OPEN  
   **Analysis:** The **most upvoted open feature request** (21 👍). Users with Claude subscriptions resent paying twice (subscription + per-token API). This is a strong monetization signal: integrating Claude's consumer OAuth flow would unlock a large user base.

3. **[#45058](https://github.com/nousresearch/hermes-agent/issue/45058) – Silent web_search routing to Parallel.ai** (7 comments, 👍15)  
   **Status:** CLOSED  
   **Analysis:** A privacy/transparency issue where web search tools silently changed default backend from Firecrawl to Parallel.ai without user opt-in. The community reacted strongly (15 👍), highlighting sensitivity around data routing defaults.

4. **[#38963](https://github.com/nousresearch/hermes-agent/issue/38963) – Desktop install failure "no git???"** (8 comments)  
   **Status:** CLOSED  
   **Analysis:** Windows 11 desktop installer fails with a confusing error on first launch. This suggests installer testing gaps for the Windows platform, a common blocker for new user adoption.

5. **[#31584](https://github.com/nousresearch/hermes-agent/issue/31584) – Memory context as background context** (6 comments)  
   **Status:** OPEN  
   **Analysis:** User-identified that memory injection blurs the line between user-provided context and system-inserted background, creating both confusion and a threat surface for prompt injection.

### Most Active Pull Requests

- **[#46315](https://github.com/nousresearch/hermes-agent/pull/46315)** – Systemd PATH fix for named profiles  
  **Analysis:** The most active PR today, reflecting ongoing Docker/systemd reliability work. This addresses a blocking issue where named profile gateways fail to start due to PATH resolution.

- **[#46407](https://github.com/nousresearchhermes-agent/pull/46407)** – Matrix media send fix  
  **Analysis:** Addressing a P1 bug with high operational impact. The community is watching this closely as Matrix is a primary platform for many deployments.

---

## Bugs & Stability

### Critical (P1)

| Issue | Description | Fix Available? |
|---|---|---|
| [#46310](https://github.com/nousresearch/hermes-agent/issue/46310) | **Matrix send_message media path exhausts E2EE keys** – Each message opens a new connection, consuming recipient one-time keys and dropping messages under burst | ✅ [PR #46407](https://github.com/nousresearch/hermes-agent/pull/46407) open |
| [#46411](https://github.com/nousresearch/hermes-agent/issue/46411) | **Security: read_file can exfiltrate sibling profile credentials** – `file_safety` blocks only active profile's credential stores | ❌ No fix PR |
| [#46413](https://github.com/nousresearch/hermes-agent/issue/46413) | **Security: Desktop file preview reads Hermes credential stores** – Electron IPC guard misses Hermes token files | ❌ No fix PR |
| [#46303](https://github.com/nousresearch/hermes-agent/issue/46303) | **Concurrent sessions cross-contaminate** – Shared memory injection and git worktree without isolation | ❌ No fix PR |

### High (P2)

| Issue | Description |
|---|---|
| [#44560](https://github.com/nousresearch/hermes-agent/issue/44560) | **model.options handler blocks on synchrounous HTTP calls** – Causes WebSocket timeout when providers are slow |
| [#32091](https://github.com/nousresearch/hermes-agent/issue/32091) | **Cron jobs from profile-scoped sessions go to unread jobs.json** – Silent orphan, gateway never triggers them |
| [#45258](https://github.com/nousresearch/hermes-agent/issue/45258) | **Gateway per-profile log/run leaves parent directory root-owned** – Causes s6-log fatal mkdir loop [CLOSED] |
| [#45963](https://github.com/nousresearch/hermes-agent/issue/45963) | **profile create auto-starts doomed resident gateway** – Token-conflict zombies that resurrect [CLOSED] |
| [#46090](https://github.com/nousresearch/hermes-agent/issue/46090) | **Agent extremely slow for basic tasks** – Needs reproduction, possibly context growth issue |

### Medium (P3)

| Issue | Description |
|---|---|
| [#40480](https://github.com/nousresearch/hermes-agent/issue/40480) | **Desktop: Custom provider models not in dropdown** – Works in CLI, missing in Desktop UI |
| [#46265](https://github.com/nousresearch/hermes-agent/issue/46265) | **SimpleX adapter silently drops all DM replies** – `@<contactId>` syntax resolves as display name |
| [#46419](https://github.com/nousresearch/hermes-agent/issue/46419) | **Chat WebSocket error banners hardcoded English** – Bypasses i18n system [CLOSED] |

---

## Feature Requests & Roadmap Signals

### High-Community-Interest Features

1. **Claude Subscription OAuth** ([#25267](https://github.com/nousresearch/hermes-agent/issue/25267), 👍21) – Most upvoted feature. Would allow Claude-subscribed users to avoid double-billing. **Prediction:** Likely in next minor release given the demand and strategic importance for user acquisition.

2. **Configurable TUI status bar** ([#13490](https://github.com/nousresearch/hermes-agent/issue/13490)) – Users want layout customization, field hiding, and theming. This is a quality-of-life improvement that aligns with the recent appearance unification work ([PR #44107](https://github.com/nousresearch/hermes-agent/pull/44107)).

3. **x86_64 macOS Desktop build** ([#42199](https://github.com/nousresearch/hermes-agent/issue/42199)) – Intel Mac users excluded from Desktop App. A straightforward build target addition that opens the app to older Macs.

4. **Remove provider accounts in UI** ([#45865](https://github.com/nousresearch/hermes-agent/issue/45865)) – Desktop UI allows adding but not removing provider accounts. Basic UX gap.

5. **Hide unconfigured providers from model switcher** ([#46304](https://github.com/nousresearch/hermes-agent/issue/46304)) – Local-only users see cluttered UI with "0 models" entries.

6. **GBrain as memory provider plugin** ([#46253](https://github.com/nousresearch/hermes-agent/issue/46253)) – Community member wants deeper integration with shared semantic memory backend.

7. **Make fallback session-stickiness configurable** ([#23094](https://github.com/nousresearch/hermes-agent/issue/23094)) – Users want control over whether fallback provider pins the session.

### Likely Next-Release Candidates

- **Unsloth Studio plugin** ([PR #46451](https://github.com/nousresearch/hermes-agent/pull/46451)) – Complete plugin PR already open, likely to merge soon
- **Appearance unification** ([PR #44107](https://github.com/nousresearch/hermes-agent/pull/44107)) – Dashboard theme + chat skin integration, significant UX improvement
- **Codex native web search** ([PR #16634](https://github.com/nousresearch/hermes-agent/pull/16634)) – Experimental opt-in, may proceed based on testing
- **Minimax China-region OAuth** ([PR #36286](https://github.com/nousresearch/hermes-agent/pull/36286)) – Regional demand for Chinese users

---

## User Feedback Summary

### Common Pain Points

1. **Installation friction** – Windows Desktop installer failing with "no git???" error ([#38963](https://github.com/nousresearch/hermes-agent/issue/38963)) and Intel Mac users unable to run ARM64-only DMG ([#42199](https://github.com/nousresearch/hermes-agent/issue/42199)) represent significant onboarding barriers.

2. **UI/UX gaps** – Users express frustration with basic UI features like removing provider accounts ([#45865](https://github.com/nousresearch/hermes-agent/issue/45865)), custom provider models not appearing in dropdowns ([#40480](https://github.com/nousresearch/hermes-agent/issue/40480)), and cluttered model switchers ([#46304](https://github.com/nousresearch/hermes-agent/issue/46304)).

3. **Privacy/transparency concerns** – The Parallel.ai silent routing issue ([#45058](https://github.com/nousresearch/hermes-agent/issue/45058), 👍15) shows the community is highly sensitive to data routing changes without explicit consent.

4. **Performance degradation** – A user reported hours-long waits for basic tasks ([#46090](https://github.com/nousresearch/hermes-agent/issue/46090)), suggesting context accumulation or memory leaks in long-running sessions.

5. **Double-cost frustration** – Claude subscribers face paying both subscription and per-token API fees ([#25267](https://github.com/nousresearch/hermes-agent/issue/25267), 👍21), a significant financial disincentive for power users.

### What's Working Well

- **Plugin extensibility** is valued – Users are creating plugins (GBrain, Unsloth Studio) and requesting deeper integration
- **Profile system** is powerful but has sharp edges (cron orphans, credential isolation gaps)
- **Tool platform diversity** (Matrix, SimpleX, Feishu, Discord) is appreciated but reveals edge-case bugs under load

---

## Backlog Watch

### Unanswered Issues Needing Maintainer Attention

| Issue | Age | Status |
|---|---|---|
| [#12020](https://github.com/nousresearch/hermes-agent/issue/12020) – **Disable tool progress events in API** (58 days) | Created 2026-04-18 | No maintainer response. OpenAI API compatibility issue breaks frontend parsers. |
| [#13490](https://github.com/nousresearch/hermes-agent/issue/13490) – **Configurable TUI status bar** (55 days) | Created 2026-04-21 | No maintainer response. User-reported with clear use case and implementation direction. |
| [#17480](https://github.com/nousresearch/hermes-agent/pull/17480) – **Fix Codex usage credentials from auth fallbacks** (47 days) | Created 2026-04-29 | Open PR, no recent activity from maintainers. Addresses OAuth credential resolution. |
| [#26051](https://github.com/nousresearch/hermes-agent/pull/26051) – **Preserve context on compression failures** (31 days) | Created 2026-05-15 | Open PR addressing critical data-loss scenario during context compression. |
| [#31584](https://github.com/nousresearch/hermes-agent/issue/31584) – **Memory context as background context** (22 days) | Created 2026-05-24 | User-identified threat surface with detailed analysis, no maintainer acknowledgment. |

### Stale High-Severity Items

- **Security issues filed today** ([#46411](https://github.com/nousresearch/hermes-agent/issue/46411), [#46413](https://github.com/nousresearch/hermes-agent/issue/46413)) – Both are P2 severity credential exfiltration vectors. These should be triaged as a priority, ideally within 24 hours given their security implications.
- **Concurrent session contamination** ([#46303](https://github.com/nousresearch/hermes-agent/issue/46303), P2) – Filed yesterday with detailed reproduction steps. No fix PR exists yet.

---

**Assessment:** Hermes Agent is in a **high-growth phase** with strong community engagement, but **maintainer bandwidth appears constrained** relative to issue volume. The open-to-closed ratio (6:1 for issues, 6:1 for PRs) suggests triage bottlenecks. The two new security vulnerabilities filed today should be prioritized, and the P1 Matrix E2EE exhaustion bug has an open fix PR that should be merged promptly. The highest-ROI feature for user satisfaction would be Claude subscription OAuth integration, which could significantly expand the user base.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-06-15

## 1. Today's Overview

PicoClaw shows a productive day with **9 pull requests** and **5 issues** updated in the last 24 hours, alongside **1 new nightly release**. The project maintains a healthy balance of bug fixes, feature development, and community engagement, with 4 open issues and 4 open PRs remaining active. Merged activity focuses on error handling improvements and code quality, while new feature work explores remote WebSocket agent modes and out-of-tree channel extensibility. The single nightly release (v0.2.9-nightly) signals ongoing development toward a stable v0.2.9 milestone, though users are cautioned about potential instability.

## 2. Releases

**Nightly Build: v0.2.9-nightly.20260615.13a38bd1**

- **Changelog**: [https://github.com/sipeed/picoclaw/compare/v0.2.9...main](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)
- **Status**: Automated build, potentially unstable
- **Breaking Changes**: None documented in this release
- **Migration Notes**: No migration steps required; this is an intermediate nightly snapshot. Users relying on stability should stay on v0.2.9.

## 3. Project Progress

**5 PRs merged/closed today** — primarily focused on error handling hygiene:

| PR | Description | Type |
|---|---|---|
| [#3124](https://github.com/sipeed/picoclaw/pull/3124) | fix(tts): handle io.ReadAll error in error response path | Bug Fix |
| [#3123](https://github.com/sipeed/picoclaw/pull/3123) | fix(filesystem): explicitly ignore Close() error on directory file descriptor | Code Quality |
| [#3122](https://github.com/sipeed/picoclaw/pull/3122) | fix(evolution): capture Close() error on write file in appendJSONLRecords | Bug Fix |
| [#3121](https://github.com/sipeed/picoclaw/pull/3121) | refactor(openai_compat): replace log.Printf with structured logger | Refactor |
| [#2904](https://github.com/sipeed/picoclaw/pull/2904) | Fix agent loop reload and panic cleanup stability | Stability Fix |

**Significant merges**: PR #2904 (by SiYue-ZO) is a substantial stability improvement for the agent loop, fixing goroutine leaks and panic recovery. The three error-handling PRs from chengzhichao-xydt demonstrate a systematic effort to surface previously-silent I/O errors.

## 4. Community Hot Topics

**Most Active Items**:

1. **#2978 — Add omniroute as provider** ([CLOSED](https://github.com/sipeed/picoclaw/issues/2978))  
   *2 comments, community favorite* — User request to integrate OmniRoute as a provider. Despite being closed, it reflects community interest in expanding provider ecosystem.

2. **#3044 — allow_from fails for Matrix user IDs containing colon** ([OPEN](https://github.com/sipeed/picoclaw/issues/3044))  
   *1 comment* — Functional bug impacting Matrix users with standard user ID format. Underlying need: proper handling of special characters in authentication filters.

3. **#3041 — mcp add mis-parses global flags into positionals** ([OPEN](https://github.com/sipeed/picoclaw/issues/3041))  
   *1 comment* — CLI usability issue affecting MCP server configuration. Community member carlosprados provided a detailed reproduction with exact commands and expected behavior.

**Analysis**: Community engagement is moderate, with users contributing detailed bug reports. The closed omniroute request (#2978) suggests the community actively seeks provider integration paths. The MCP flag parsing bug (#3041) from carlosprados shows experienced users investing in thorough testing.

## 5. Bugs & Stability

**High Severity**:
- **#3125 — web_search tool fails silently with Brave API key from .security.yml** ([OPEN](https://github.com/sipeed/picoclaw/issues/3125))  
  *New today* — API key migration to `.security.yml` broke Brave Search integration silently. No fix PR yet. **Severity: High** (core tooling regression, no error feedback to user)

**Medium Severity**:
- **#3044 — allow_from fails for Matrix user IDs containing colon** ([OPEN](https://github.com/sipeed/picoclaw/issues/3044))  
  *Stale (7 days)* — Authentication bypass vulnerability for Matrix users. No fix PR exists.

- **#3041 — mcp add mis-parses global flags into positionals** ([OPEN](https://github.com/sipeed/picoclaw/issues/3041))  
  *Stale (8 days)* — Breaks HTTP/SSE MCP server adds and misnames stdio servers. No fix PR.

- **#3090 — Panel not working on Safari iOS <16.4** ([OPEN](https://github.com/sipeed/picoclaw/issues/3090))  
  *5 days stale* — Web UI compatibility issue affecting older iOS devices.

**Lower Severity**:
- **#3124, #3123, #3122** — All had fix PRs merged today (error handling improvements)
- **#3121** — Refactor merged (structured logging)

## 6. Feature Requests & Roadmap Signals

| Request | Status | Likelihood for v0.2.9 |
|---|---|---|
| **OmniRoute as provider** (#2978, closed) | Closed — likely needs community contribution | Low |
| **Remote WebSocket agent mode** ([PR #3118](https://github.com/sipeed/picoclaw/pull/3118)) | Open PR, no merge yet | Medium — valuable remote management feature |
| **RegisterChannelSettings hook** ([PR #3120](https://github.com/sipeed/picoclaw/pull/3120)) | Open PR, recent (June 14) | Medium-High — enables out-of-tree channels without forking |
| **Launcher allowlist bypass diagnostics** ([PR #3126](https://github.com/sipeed/picoclaw/pull/3126)) | Open PR, new today | Medium — security hardening for launcher |
| **Telegram reply-as-mention** ([PR #2975](https://github.com/sipeed/picoclaw/pull/2975)) | Stale open PR (16 days) | Moderate — community-requested UX improvement |

**Prediction**: The `RegisterChannelSettings` hook (PR #3120) and remote WebSocket agent mode (PR #3118) are the most mature feature additions and could land in the next stable release. The launcher diagnostics PR (#3126) suggests ongoing security improvements.

## 7. User Feedback Summary

**Pain Points**:
- Silent failures: The `web_search` Brave API regression (#3125) exemplifies a recurring theme — tools returning "no results" without surfacing the actual backend error
- Compatibility gaps: Safari on iOS <16.4 (#3090), Matrix user IDs with colons (#3044) show platform/framework edge cases are not fully tested
- CLI usability: MCP flag parsing bug (#3041) undermines confidence in configuration workflows

**Use Cases**:
- **Self-hosted AI agent**: Multiple issues target server-side deployments (Raspberry Pi OS, Linux x86_64)
- **Messaging integration**: Matrix (#3044), Telegram (#2975), web panel (#3090) show diverse channel adoption
- **Provider extensibility**: Omnironte request (#2978), out-of-tree channel hook (#3120) indicate desire for plugin architecture

**Satisfaction Signals**: Community members contribute detailed bug reports with reproduction steps, suggesting engaged and technically proficient users who value the project enough to invest time in diagnostics.

## 8. Backlog Watch

**Critical (needs maintainer attention)**:
- **#3041 — MCP flag parsing bug** (8 days open, no assignee) — Blocks MCP server configuration for HTTP/SSE sources
- **#3044 — Matrix allow_from bug** (8 days open, no assignee) — Core authentication feature broken for standard Matrix IDs

**Stale but Important**:
- **#3090 — Safari iOS compatibility** (5 days open) — Platform regression affecting mobile web users
- **PR #2975 — Telegram reply-as-mention** (16 days stale) — Community contribution awaiting review/merge

**New and Pending**:
- **#3125 — web_search silent failure** (0 days, today) — New regression needing immediate triage; no fix PR yet
- **PR #3126 — Launcher diagnostics** (new today) — Security enhancement, low risk, ready for review
- **PR #3118 — Remote agent mode** (3 days old) — Feature PR with no feedback from maintainers yet

**Summary**: The backlog shows 2 critical open bugs without maintainer response, plus a newly-reported regression today. The open PRs (especially #3118 and #3126) could benefit from maintainer review to prevent further stagnation.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

Here is the NanoClaw project digest for **2026-06-15**, based on GitHub activity in the last 24 hours.

---

### NanoClaw Project Digest — 2026-06-15

**1. Today's Overview**

NanoClaw is currently in a high-velocity phase, with **7 issues** and **10 PRs** updated in the last 24 hours. The project's activity is heavily weighted toward security hardening and architectural expansion. Three critical security advisories were opened today, while a parallel track of major feature work on the Codex and provider systems reached closure. The maintainer team appears to be balancing rapid feature delivery with addressing deep-seated vulnerabilities. The release cadence is currently paused, suggesting a potential stabilization sprint is upcoming.

**2. Releases**

No new releases were published in the last 24 hours. The project is likely between releases, accumulating the significant changes seen in the PR queue.

**3. Project Progress**

Five Pull Requests were merged or closed today, indicating progress on several fronts:
- **Documentation Fixes:** [#2764 (closed)](https://github.com/nanocoai/nanoclaw/pull/2764) fixed broken file paths in the `CLAUDE.md` Key Files table, improving developer onboarding. A follow-up doc fix, [#2769 (closed)](https://github.com/nanocoai/nanoclaw/pull/2769), clarified authentication steps in the `/add-codex` skill guide to prevent agent stalls.
- **Core Architecture & Codex:** Two major feature PRs merged. [#2756 (closed)](https://github.com/nanocoai/nanoclaw/pull/2756) introduces operator-driven provider selection, switching, and memory migration, a foundational change for multi-provider support. [#2757 (closed)](https://github.com/nanocoai/nanoclaw/pull/2757) delivers the **Codex v2 agent-provider payload**, integrating it as a full provider via vault-only authentication.
- **Infrastructure:** [#2758 (closed)](https://github.com/nanocoai/nanoclaw/pull/2758) refactored CLI tool installation to a data-driven manifest, improving maintainability.

**4. Community Hot Topics**

The most active discussion centers around the **budget exhaustion bug** (Issue #2751):
- **[#2751: Budget-exhausted LLM turns are silently dropped](https://github.com/nanocoai/nanoclaw/issues/2751)** — This issue has the longest lifespan (since June 12) and is tied to a fix PR (#2759). While it has zero comments, its pairing with a targeted fix suggests it is the team's current priority. The underlying need is for **reliable user feedback**, ensuring users are not left in the dark when an agent fails due to budget limits, a critical UX concern for production deployments.
- The three **security advisories** (Issues #2760, #2761, #2762) represent the most technically dense and impactful discussions, lacking comments but carrying high implicit urgency.

**5. Bugs & Stability**

Three new security bugs were reported today, all classified as **Critical severity**:
- **[#2762: `add_mcp_server` approval bypass](https://github.com/nanocoai/nanoclaw/issues/2762)** — An attacker-controlled agent can hide malicious `args` and `env` from the approver, bypassing the approval flow.
- **[#2761: Local gateway approval bypass via unauthenticated webhook](https://github.com/nanocoai/nanoclaw/issues/2761)** — An unauthenticated loopback webhook allows a local attacker to forge approval events.
- **[#2760: Arbitrary local file exfiltration via `send_file`](https://github.com/nanocoai/nanoclaw/issues/2760)** — The `send_file` MCP tool can read and exfiltrate any local file via absolute paths.

One stability bug was addressed with a fix PR:
- **[#2751: Silent budget exhaustion](https://github.com/nanocoai/nanoclaw/issues/2751)** (High) — Fixed by **[PR #2759 (open)](https://github.com/nanocoai/nanoclaw/pull/2759)** which ensures budget/billing errors are delivered to the user instead of being silently dropped.

**6. Feature Requests & Roadmap Signals**

The merged PRs clearly signal the immediate roadmap:
- **Multi-Provider Ecosystem:** The core seams for operator-driven provider selection ([PR #2756](https://github.com/nanocoai/nanoclaw/pull/2756)) are in place, setting the stage for third-party providers.
- **Codex as Full Provider:** The Codex integration is moving from a prototype to a first-class citizen with PR [#2757](https://github.com/nanocoai/nanoclaw/pull/2757).
- **Developer Experience:** Several smaller PRs ([#2770](https://github.com/nanocoai/nanoclaw/pull/2770), [#2766](https://github.com/nanocoai/nanoclaw/pull/2766), [#2765](https://github.com/nanocoai/nanoclaw/pull/2765)) focus on delivering file events from agents and improving code formatting, indicating a push for stability in the developer workflow.
- **Speculation:** Given the volume of security findings, the next release (v0.x) will almost certainly include the three critical security fixes and the budget-handling fix. The Codex v2 feature is a candidate for a subsequent, larger release.

**7. User Feedback Summary**

While direct user comments are sparse, the issues themselves reveal clear pain points:
- **Pain Point (Security/Trust):** The three security advisories filed by user `YLChen-007` indicate deep concern about the trust model. Users who deploy agents with MCP or approval flows are at risk of data exfiltration and control bypasses.
- **Pain Point (UX/Failures):** User `assapin` (Issue #2751) highlights a major frustration where agents simply stop responding without explanation, undermining user confidence. The prompt caching issue ([#2768](https://github.com/nanocoai/nanoclaw/issues/2768)) from `galmorduku` also points to cost-sensitive users wanting to optimize their spend.
- **Pain Point (Documentation):** The docs fix in PR #2764 suggests that onboarding developers or AI coding assistants are hitting dead ends due to stale documentation.

**8. Backlog Watch**

- **[PR #2732 (OPEN)](https://github.com/nanocoai/nanoclaw/pull/2732): Harden host + agent-runner from health audit findings** — Created June 11, this large PR (19 files) remains open with no recent comments from maintainers. Given that it addresses findings from a multi-agent health audit, its staleness after 4 days is a concern, especially with new, related security issues coming in.
- There are **no long-standing issues** currently; the oldest open issue (#2751) is just 3 days old and has an active fix PR.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-06-15

## Today's Overview
Project activity remains low today, with no new releases or merged pull requests. A single enhancement issue was opened, suggesting the community is focused on expanding cloud provider integrations rather than fixing bugs. The lack of PR activity indicates a quiet maintenance period. Overall, the project appears stable but with minimal forward momentum in the last 24 hours.

## Releases
No new releases were published in the last 24 hours. The latest available release remains unchanged.

## Project Progress
No pull requests were merged or closed today. No features or fixes advanced through the PR pipeline.

## Community Hot Topics
- **Issue #955 – Identity-based authentication for Azure OpenAI LLM Provider**  
  *[OPEN]* | Created: 2026-06-15 | Comments: 0 | 👍: 0  
  Summary: Suggests supporting `DefaultTokenCredential` to use developer credentials from `az CLI` login, bypassing API key requirements for Azure OpenAI.  
  **Analysis:** This request addresses a common pain point in enterprise Azure environments where security policies restrict API key usage. The zero-comment status suggests early-stage discussion, but the topic is practically significant.  
  [View Issue](https://github.com/nullclaw/nullclaw/issues/955)

## Bugs & Stability
No bugs, crashes, or regressions reported today. The issue tracker remains free of open stability-related items.

## Feature Requests & Roadmap Signals
The sole feature request today is **Issue #955** which proposes identity-based authentication for Azure OpenAI. This aligns with a broader industry trend toward managed identity and token-based access in cloud AI services. Given the explicit request and lack of alternative proposals, this feature is a strong candidate for the next minor release if maintainers prioritize Azure provider improvements.

## User Feedback Summary
The community signal today is very thin. The single issue reflects a user need driven by real enterprise security policies — the inability to use API keys in certain Azure subscriptions. This suggests a user base that includes organizational deployments where compliance and security are top-of-mind. No explicit satisfaction or dissatisfaction was expressed.

## Backlog Watch
No long-unanswered important issues or PRs were identified in today's data. The pipeline is current and maintained.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-06-15

## 1. Today's Overview

The IronClaw project is experiencing **high activity** with 43 issues and 48 PRs updated in the last 24 hours, indicating strong development velocity and community engagement. Seven issues were closed and 15 PRs were merged/closed today, signaling consistent forward progress on the Reborn WebUI v2 architecture. The project remains in an active pre-release cycle (no new tagged releases today), with the team heavily focused on **dogfooding** their own platform — filing bugs discovered by using Reborn locally — and simultaneously shipping **engineering productivity tooling** to accelerate their own workflow. The volume of security-related issues (two shell approval bypass reports) and UX fidelity bugs (WebSocket auth conflicts, mobile layout clipping) suggests the project is maturing through a rigorous internal QA phase before broader public release.

---

## 2. Releases

**No new releases today.** The last release candidate PR (#3708) remains open, bumping `ironclaw` from 0.24.0 → 0.29.1 with breaking changes in `ironclaw_common` (0.4.2 → 0.5.0) and `ironclaw_skills` (0.3.0 → 0.4.0). No migration notes published yet.

---

## 3. Project Progress

**Merged/closed today (15 PRs):**

| PR | Description | Impact |
|---|---|---|
| [#4738](https://github.com/nearai/ironclaw/pull/4738) | Attachment web UX on WebChat v2 SPA (Stacked on #4677) | **Major feature**: image/file uploads now functional in Reborn WebChat |
| [#4836](https://github.com/nearai/ironclaw/pull/4836) | Runtime-context: connected channels, delivery state, run origin (#4828) | **Core infrastructure**: model now sees channel state and delivery targets |
| [#4847](https://github.com/nearai/ironclaw/issues/4847) | Re-homed Slack approval→auth→final-reply e2e test | **Test stability** — previously broken test now passes |
| [#4848](https://github.com/nearai/ironclaw/issues/4848) | Auth-resume matched by per-invocation identity (input_ref) | **Security/Correctness**: fixes slot-reuse vulnerability in auth-resume |
| [#4851](https://github.com/nearai/ironclaw/issues/4851) | Trusted-trigger origin laundered through string — fixed | **Security**: root cause fix for forgeable `ScheduledTrigger` origin |
| [#3515](https://github.com/nearai/ironclaw/issues/3515) | WeChat channel docs | **Documentation** complete |
| [#4751](https://github.com/nearai/ironclaw/issues/4751) | Large response fails with tool args > 16384 bytes | **Bug fix**: provider argument size limit resolved |

**Features that advanced today (open PRs with recent commits):**
- **Image attachments for vision models** ([#4871](https://github.com/nearai/ironclaw/pull/4871)) — closes a gap where attached images were sent as text pointers, now sent as real multimodal content
- **GitHub read-only capabilities** ([#4893](https://github.com/nearai/ironclaw/pull/4893)) — simple repo lookups no longer trigger repeated approval prompts; effectful actions remain at `ask`
- **Tool activity cleanup after cancellation** ([#4889](https://github.com/nearai/ironclaw/pull/4889)) — canceled runs no longer leave stale "running" indicators
- **PR filtering from GitHub issue listings** ([#4888](https://github.com/nearai/ironclaw/pull/4888)) — `github.list_issues` now excludes PR-shaped items
- **System-sentinel ID centralization** ([#4584](https://github.com/nearai/ironclaw/pull/4584)) — authority contract pinned to single sanctioned constructor path

---

## 4. Community Hot Topics

### Most Active Issues (by comments)

1. **[#4857](https://github.com/nearai/ironclaw/issues/4857) — Clean state incorrectly shows NEAR AI provider as Active**
   - *1 comment, 0 reactions.* A fresh local install shows the NEAR AI provider as **ACTIVE** and under the **ACTIVE** section in Settings → Inference, even though no LLM provider is configured. This is a misleading UX bug that could confuse first-time users into thinking setup is complete when it isn't. The header correctly shows "NOT CONFIGURED" but the provider list contradicts it.

2. **[#4887](https://github.com/nearai/ironclaw/issues/4887) — Provider-backed MCP tool approval resume fails with stale capability input_ref**
   - *1 comment, 0 reactions.* After approving a provider-backed MCP capability (e.g., `nearai.web_search`), the resumed invocation fails with "capability input ref is not scoped to this loop run." This breaks the multi-step approval→auth→execution flow for MCP tools, which is critical for the extension ecosystem.

3. **[#4644](https://github.com/nearai/ironclaw/issues/4644) — Universal attachments across all channels**
   - *1 comment, 0 reactions.* Attachments work on v1/v2 but are silently dropped on Reborn. Format-support logic is duplicated across four+ call sites with no single extension point. This is a **foundational UX gap** — users expect attachments to work everywhere, but Reborn's transcript contract is text-only.

### Most Active Pull Requests

1. **[#4588](https://github.com/nearai/ironclaw/pull/4588) — Observability seams: trajectory observer + LLM provider injection**
   - Two small seams that let external hosts (like `nearai-bench`) drive and observe Reborn agent runs with parity to legacy agent path. Critical for benchmarking and testing infrastructure.

2. **[#4778](https://github.com/nearai/ironclaw/pull/4778) — Slack as a product-adapter extension**
   - Moves Slack from hardcoded built-in channel to a host-bundled Reborn extension. Represents the **architectural shift to extension-based channel model** — future communication platforms will follow this pattern.

3. **[#4838](https://github.com/nearai/ironclaw/pull/4838) — Explicit gate-open feedback for busy threads**
   - Replaces the closed defer-and-drain approach with a simple contract: a message arriving while another run holds the thread is **rejected with an explicit notice**, not parked for background resubmission. The user is the retry actor.

### Underlying Needs

The community is signaling **three core needs**:
- **First-run clarity**: New users hit confusing default states (provider shown as active when it's not) and fragmented setup flows (must manually discover "Install → Configure → Authorize")
- **Extension ecosystem stability**: Auth flows between extensions (Google Calendar, GitHub, MCP tools) and the core agent loop are fragile, with approval resumes failing mid-flow
- **Mobile/accessibility parity**: UI components clip offscreen on mobile, and non-operator pages silently swallow 403 errors

---

## 5. Bugs & Stability

### Critical (P0)

1. **Shell approval browser bypass via `env /bin/sh -c` wrapper** ([#4865](https://github.com/nearai/ironclaw/issues/4865))
   - *Severity: CRITICAL.* A destructive command hidden behind `env /bin/sh -c` can avoid the intended per-invocation approval floor. The shell tool's wrapper detection is insufficient.

2. **Shell approval wrapper bypass inherits prior auto-approval** ([#4864](https://github.com/nearai/ironclaw/issues/4864))
   - *Severity: CRITICAL.* A wrapper-prefixed destructive `shell` command can inherit auto-approval from a previous non-destructive command, evading the explicit approval floor.

   *Note: No fix PRs exist for either issue yet. These require immediate maintainer attention.*

### High (P1)

3. **Provider-backed MCP approval resume fails with stale input_ref** ([#4887](https://github.com/nearai/ironclaw/issues/4887))
   - Breaks any MCP tool that requires auth (e.g., `nearai.web_search`). Blocks extension ecosystem.

4. **WebUI v2 WebSocket authenticates with `?token=` while auth contract rejects query-token** ([#4870](https://github.com/nearai/ironclaw/issues/4870))
   - The browser-side `openEventSocket()` helper uses a different auth mechanism than the composed v2 auth contract allows. Not yet confirmed as a real bug, but indicates codebase confusion around auth contracts.

5. **WebChat v2 fails with "Illegal invocation" over plain HTTP from non-localhost** ([#4874](https://github.com/nearai/ironclaw/issues/4874))
   - Blocks deployment to any non-localhost environment without HTTPS. The SPA throws `TypeError: Illegal invocation` on plain HTTP network access.

### Medium (P2)

6. **Logs link visible to non-operators, swallows 403 as empty stream** ([#4892](https://github.com/nearai/ironclaw/issues/4892))
   - UX bug: non-admin users see a Logs link that shows nothing useful, with the error silently cleared.

7. **Google Calendar auth prompt asks for access token instead of guiding OAuth** ([#4884](https://github.com/nearai/ironclaw/issues/4884))
   - Shows a credential input field rather than initiating the proper OAuth flow — confusing for users.

8. **Shell command not visible in approval dialog or Activity history** ([#4852](https://github.com/nearai/ironclaw/issues/4852))
   - Approval dialog shows only "Capability: builtin.shell" with no command preview, making informed approval impossible.

9. **Settings provider actions clip offscreen on mobile** ([#4868](https://github.com/nearai/ironclaw/issues/4868))
   - Fixed-height cards on narrow viewports push action buttons out of visible area.

### Bugs with Fix PRs

| Bug | Fix PR | Status |
|---|---|---|
| Non-wrapped code blocks widen chat timeline ([#4791](https://github.com/nearai/ironclaw/pull/4791)) | [#4791](https://github.com/nearai/ironclaw/pull/4791) | Open |
| Credential gate appears after approval gate ([#4840](https://github.com/nearai/ironclaw/issues/4840)) | [#4840](https://github.com/nearai/ironclaw/pull/4840) | Open |
| "Always allow" scoped per-thread instead of per-user ([#4835](https://github.com/nearai/ironclaw/issues/4835)) | [#4835](https://github.com/nearai/ironclaw/pull/4835) | Open |

---

## 6. Feature Requests & Roadmap Signals

### Likely in Next Version

1. **Image attachments for vision models** ([PR #4871](https://github.com/nearai/ironclaw/pull/4871))
   - Already implemented and in review. Closes a major gap in Reborn's multimodal capabilities. **Prediction:** Ships in next release.

2. **Universal attachment pipeline for Reborn** ([#4644](https://github.com/nearai/ironclaw/issues/4644))
   - Parent issue for #4871. The PR addresses the vision-capable model piece; the full pipeline (extensible format registry, all-channel support) is still open.

3. **Runtime-context for models** ([PR #4836](https://github.com/nearai/ironclaw/pull/4836), merged)
   - Already merged today. Models will now receive connected channels, delivery state, and run origin context at every loop start. **Already in main.**

4. **Engineering productivity platform** ([#4878](https://github.com/nearai/ironclaw/issues/4878))
   - A new initiative to use IronClaw itself to improve the team's engineering workflow. Sub-issues include:
     - [#4882](https://github.com/nearai/ironclaw/issues/4882) — Cloud coding agent workflow
     - [#4881](https://github.com/nearai/ironclaw/issues/4881) — Preview deployments for PRs
     - [#4880](https://github.com/nearai/ironclaw/issues/4880) — Automated code review
     - [#4883](https://github.com/nearai/ironclaw/issues/4883) — Test coverage tracking
   - **Prediction:** These will be internal tools built iteratively over the next 2-4 weeks.

### User-Requested Features

- **Extension setup flow unification** ([#4890](https://github.com/nearai/ironclaw/issues/4890)) — Users want a single guided path from "install" through "configure" to "authorize"
- **Post-install setup guidance** ([#4886](https://github.com/nearai/ironclaw/issues/4886)) — "AUTH NEEDED" on the Installed page is insufficient; users want clear next-step indicators
- **GitHub extension onboarding to classic PAT** ([PR #4891](https://github.com/nearai/ironclaw/pull/4891)) — Documentation fix to send users to correct token creation page
- **Observability seams for external hosts** ([PR #4588](https://github.com/nearai/ironclaw/pull/4588)) — Allows `nearai-bench` and similar tools to drive Reborn agents

### Roadmap Signals from `ironclaw-ci` Release PR

The tagged release candidate ([#3708](https://github.com/nearai/ironclaw/pull/3708)) shows planned breaking changes in `ironclaw_common` and `ironclaw_skills`, suggesting the team is preparing a structured release with API stability guarantees.

---

## 7. User Feedback Summary

### Explicit Pain Points

| Pain Point | Source | Signal Strength |
|---|---|---|
| **"Why does the provider show ACTIVE when I haven't configured anything?"** | [#4857](https://github.com/nearai/ironclaw/issues/4857) — sunglow666 | High — affects every new user's first impression |
| **"I approved a shell command but the dialog showed no command text"** | [#4852](https://github.com/nearai/ironclaw/issues/4852) — sunglow666 | High — security/privacy concern for informed consent |
| **"Google Calendar asked for an access token instead of doing OAuth"** | [#4884](https://github.com/nearai/ironclaw/issues/4884) — sunglow666 | Medium — blocks extension usability |
| **"Extension setup is fragmented between 4 different screens"** | [#4890](https://github.com/nearai/ironclaw/issues/4890) — sunglow666 | Medium — UX friction after installation |
| **"MCP tool approval fails with 'capability input ref is not scoped'"** | [#4887](https://github.com/nearai/ironclaw/issues/4887) — krishna-505 | High — blocks MCP tool functionality |
| **"400 token setting cannot be saved"** | Framework error, not filed as separate issue | Low — single report |

### Implicit Satisfaction Signals

- **Dogfooding engagement**: The same users filing bugs (sunglow666, krishna-505, think-in-universe) are actively using Reborn for daily work and filing detailed, actionable reports — a strong indicator of invested users who believe in the product
- **Engineering productivity initiative**: The team choosing to use IronClaw *to build IronClaw* ([#4878](https://github.com/nearai/ironclaw/issues/4878)) signals confidence in the platform's expandability
- **Weekly dogfooding cycles**: Second weekly batch of findings ([#4692](https://github.com/nearai/ironclaw/issues/4692) → [#4879](https://github.com/nearai/ironclaw/issues/4879)) shows systematic, ongoing quality investment

### Dissatisfaction Indicators

- **Security confidence**: Two shell approval bypass reports ([#4865](https://github.com/nearai/ironclaw/issues/4865), [#4864](https://github.com/nearai/ironclaw/issues/4864)) from a new reporter (YLChen-007) suggest security auditing is revealing real vulnerabilities
- **First-run confusion**: Multiple issues point to a lack of onboarding clarity — users don't know what "ACTIVE" means, don't know where to configure extensions, don't know what "AUTH NEEDED" requires

---

## 8. Backlog Watch

### Long-Unanswered Important Issues

| Issue | Age | Last Updated | Summary | Action Needed |
|---|---|---|---|---|
| [#3511](https://github.com/nearai/ironclaw/pull/3511) — fix(prompt): avoid repeated compact tool schema lookups | 34 days | 2026-06-15 | Optimization for prompt generation — Cached tool schema lookups | **Stale** — last activity is the CI bot re-running; needs maintainer review |
| [#3708](https://github.com/nearai/ironclaw/pull/3708) — chore: release (0.24.0 → 0.29.1) | 30 days | 2026-06-15 | Tagged release with breaking changes | **Blocked** — needs decision on release timing; CI re-runs indicate unresolved conflicts |
| [#4584](https://github.com/nearai/ironclaw/pull/4584) — refactor(host_api): centralize system-sentinel id minting | 6 days | 2026-06-15 | Security/architecture improvement | **Needs review** — code changes ready; linked to critical trust-origin fix (#4851) |
| [#4588](https://github.com/nearai/ironclaw/pull/4588) — feat(reborn): observability seams | 6 days | 2026-06-15 | Trajectory observer + LLM provider injection | **Needs review** — foundation for benchmarking infrastructure |
| [#4778](https://github.com/nearai/ironclaw/pull/4778) — Slack as product-adapter extension | 4 days | 2026-06-14 | Architectural shift to extension-based channel model | **Needs review** — significant architectural PR; risk of merge conflicts with other extension work |

### PRs Needing Maintainer Attention

| PR | Priority | Why It Matters |
|---|---|---|
| [#4575](https://github.com/nearai/ironclaw/pull/4575) — Fix system ResourceScope JSON round-trip | High | Fixes deserialization of system-scoped resources; 7 days open with active commits |
| [#4791](https://github.com/nearai/ironclaw/pull/4791) — Keep code block overflow local | Medium | UX regression fix for chat timeline; 3 days open |
| [#4835](https://github.com/nearai/ironclaw/pull/4835) — Persist "always allow" across threads | High | UX fix for approval persistence; linked to #4825 |

### CI Signal

The release PR [#3708](https://github.com/nearai/ironclaw/pull/3708) and dependency bump PR [#4876](https://github.com/nearai/ironclaw/pull/4876) both show CI re-run activity, suggesting the team is working to keep CI green against moving targets. No CI failures reported in the last 24 hours.

---

**Summary of Project Health**: IronClaw is in a **high-velocity pre-release phase** with strong internal dogfooding, active security auditing, and clear architectural progress (extension model, runtime context, multimodal attachments). The two critical shell bypass bugs and the fragmented extension setup flow are the top risks to user adoption and security confidence. The team's decision to dogfood their own platform is generating high-quality feedback that should accelerate the path to a stable v0.29 release.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the LobsterAI project digest for **2026-06-15**, based on the provided GitHub data.

---

## LobsterAI Project Digest — 2026-06-15

### 1. Today's Overview
Activity is **moderate**, driven primarily by the merge of a significant artifact-sharing feature rather than new releases. One PR was merged, and one old bug fix was closed, indicating progress on both feature development and backlog cleanup. The issue tracker shows no new bugs filed in the last 24 hours, but two older, unresolved UI issues remain open. The core team appears focused on polishing the document collaboration experience and addressing reliability concerns in the Cowork session system.

### 2. Releases
**No new releases** were published in the last 24 hours. The project has no release notes or version bumps to report.

### 3. Project Progress
One major feature was merged, and one long-standing bug was closed:

- **[Merged #2159] feat(artifacts): Document artifact sharing & preview optimization** (by liugang519)
  - Adds support for sharing and previewing DOCX, PPTX, XLSX, PDF, CSV, and TSV files directly in the Artifact panel.
  - Includes file type validation, size limits, DOCX pagination improvements, PDF native fallback preview, and required static resource configuration (pdfjs fonts, cMap).
  - Adjusts CSP headers to allow blob resources needed for previews.
  - **Impact:** Core feature improvement for document-heavy workflows; closes a key gap in artifact functionality.

- **[Closed #1465] fix(scheduled-tasks): Ghost sessions reappearing after restart** (by linlihua)
  - Root cause: Deleting a scheduled task only removed the gateway-side cron record but left the associated local SQLite session record (`cowork_sessions`).
  - **Impact:** Solves a user-reported persistence bug where deleted tasks reappeared as empty “ghost” sessions after application restart. This is a stability fix.

### 4. Community Hot Topics
All discussion this period centers on **UI/UX polish and system reliability**, as evidenced by the two open issues and three stale PRs:

- **#1434 [OPEN] - Mixed-language UI in Chinese mode (Agent skills tab)**
  - User reports that when the UI language is set to Chinese, the skills tab displays English prompts and buttons when search results are empty. This is an i18n gap that breaks the localized experience.
  - **Underlying need:** Complete internationalization consistency; users expect 100% of UI elements to respect the selected language.

- **#1435 [OPEN] - Custom agent name overflow in dialog**
  - Long agent names overflow beyond the modal’s boundaries, creating an unreadable and broken layout.
  - **Underlying need:** Input validation and UI responsiveness; users need to be confident that form inputs will render cleanly without truncation or overflow issues.

### 5. Bugs & Stability
There are **no new bugs** filed in the last 24 hours. Two previously reported, non-critical bugs remain open:

| Issue | Severity | Summary | Fix Status |
|-------|----------|---------|------------|
| #1434 | **Low** | UI language inconsistency (Chinese/English mix) in skills tab | No fix PR open; stale since Apr 3 |
| #1435 | **Low** | Agent name overflows creation dialog | No fix PR open; stale since Apr 3 |

**No crashes, regressions, or security issues** were reported.

### 6. Feature Requests & Roadmap Signals
The three open but stale PRs provide strong signals for upcoming releases:

- **#1429 – In-session message search with `mark.js` highlighting** (Cowork)
  - Adds `Cmd+F` search inside active Cowork sessions with real-time highlights and count navigation. Likely to be merged next as it enhances an existing UX flow without architectural change.

- **#1430 – Prevent system sleep during active sessions** (Cowork)
  - Uses Electron’s `powerSaveBlocker` to prevent hibernation while a session is running. This is a **high-value reliability feature** that directly addresses user pain points with long-running tasks.

- **#1431 – Real-time elapsed timer in StreamingActivityBar** (Cowork)
  - Adds a seconds/minutes elapsed counter during streaming responses. Improves user feedback for longer tasks.

**Prediction:** These three Cowork UX features (#1429, #1430, #1431) are strong candidates for the next minor release (v0.x.1).

### 7. User Feedback Summary
Based on the data, user pain points include:

- **Ghost sessions** (addressed in #1465): Users found it frustrating that deleting a scheduled task did not fully remove it, causing confusion when the app restarted.
- **Incomplete localization** (#1434): Users who prefer Chinese UI are experiencing mixed-language displays, harming trust in the product’s maturity.
- **Poor form UX** (#1435): The agent creation dialog fails to handle long names gracefully, a basic usability gap.

There are no explicit satisfaction signals (e.g., no recently closed issues with positive comments), but the merge of #2159 (document sharing) likely addresses a previously unvoiced need for document artifact support.

### 8. Backlog Watch
**Two issues** and **three PRs** have been stale for over two months without maintainer response or review:

| Item | Type | Last Updated | Reason for Concern |
|------|------|-------------|-------------------|
| #1434 | Issue | 2026-06-14 | i18n bug; no comments from maintainers since creation |
| #1435 | Issue | 2026-06-14 | UI overflow bug; same status |
| #1429 | PR | 2026-06-14 | Feature ready; no review activity |
| #1430 | PR | 2026-06-14 | Reliability feature; no review activity |
| #1431 | PR | 2026-06-14 | UX improvement; no review activity |

**Recommendation:** These items represent a growing backlog of community-submitted value. A maintainer review cycle should be scheduled for #1429, #1430, and #1431 to avoid code drift and maintain contributor morale.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Project Digest: Moltis**
**Date:** 2026-06-15
**Data Snapshot:** Issues (1 open, 0 closed), PRs (0), Releases (0)

---

### 1. Today's Overview
Moltis saw minimal activity in the last 24 hours, with a single new enhancement issue filed and no recent pull requests or releases. The project appears to be in a low-activity or maintenance phase, likely following the recent v0.7.0 release cycle. There are no pending code merges or critical bug fixes in queue, indicating a stable but quiet day for the codebase.

### 2. Releases
*No new releases were published within the last 24 hours.*
The project currently has no tagged releases listed. All dependencies and features remain at their last published state.

### 3. Project Progress
No pull requests were updated or merged in the last 24 hours. There are zero open PRs in the repository. No features advanced or fixes were applied to the codebase today.

### 4. Community Hot Topics
There is only one active item in the repository today, containing no comments or reactions.

- **[#1123 [Feature]: Add pure-Rust turbovec as an alternative memory backend for extreme edge compression](https://github.com/moltis-org/moltis/issues/1123)**
  - *Author:* joeblew999
  - *Analysis:* This is a greenfield feature request proposing the integration of a specific Rust library (`turbovec`) to improve memory efficiency on edge devices. The lack of prior discussion or upvotes suggests this is an early-stage idea from a single contributor. The underlying need is for reduced memory footprint and compression performance on hardware-constrained deployments, but the request has not yet attracted broader community validation or technical debate.

### 5. Bugs & Stability
No bugs, crashes, performance regressions, or stability issues were reported in the last 24 hours. The single open issue is an enhancement request, not a defect. No fix PRs are pending.

### 6. Feature Requests & Roadmap Signals
One feature request was filed today:
- **[#1123] Pure-Rust `turbovec` memory backend:** The proposer explicitly states this is for "extreme edge compression,” targeting deployments where memory is the primary bottleneck and portability (pure Rust) matters.
- *Prediction:* This is unlikely to land in the immediate next minor release unless the core team is already exploring memory backends. It may be deferred until the project’s architecture supports pluggable storage backends, or until additional community interest (reactions, comments) confirms demand.

### 7. User Feedback Summary
With no comments, reactions, or PR discussions in the last 24 hours, there is no direct user feedback to report from this period. The single new issue suggests a user is proactively exploring ways to make Moltis more suitable for constrained environments. No satisfaction/dissatisfaction signals are available from today’s data.

### 8. Backlog Watch
No items currently require maintainer attention. There are no long-unanswered issues or PRs in the repository. The only open item is fresh (< 24 hours old) and has not yet received a maintainer response.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Here is the CoPaw project digest for **2026-06-15**.

---

## CoPaw Project Digest — 2026-06-15

### 1. Today's Overview
CoPaw (formerly QwenPaw) saw elevated activity over the last 24 hours, with **24 issues** and **17 PRs** updated. The team closed **6 issues** and **6 PRs**, including several bug fixes and a key feature revert. However, the project is grappling with a significant stability regression following the v1.1.11.post2 release, with multiple reports of crashes, memory leaks, and UI blocking on Windows. Community engagement is high, particularly around enterprise channel support and AI-assisted coding features, but the spike in bug reports suggests the recent release requires prompt hotfix attention.

### 2. Releases
**No new releases** in the last 24 hours. The latest available version remains **v1.1.11.post2**, which is the subject of several newly filed bug reports.

### 3. Project Progress
The following PRs were merged or closed today, reflecting progress on stability and configuration fixes:

- **[PR #5051 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5051):** Fix(desktop): Persist backend port across restarts to preserve localStorage. This resolves Issue #4733, where the Windows desktop app would reset the selected agent on every restart.
- **[PR #5037 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5037):** Fix(config): Avoid IndexError on empty `Exec=` in Linux browser detection.
- **[PR #5038 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5038):** Fix(context): Guard empty msg list in `LightContextManager.pre_reply` to prevent crashes.
- **[PR #5035 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5035):** Fix(local_models): Parse llama.cpp server version without fixed-width slice, fixing a bug where build numbers exceeding 4 digits would break parsing.
- **[PR #5092 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5092):** Revert of a previous packaging fix that caused a regression in Discord channel compilation.
- **[PR #5188 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/pull/5188):** Added request payload transforms to the chat registry, enabling plugin-based request modification.

### 4. Community Hot Topics
Several issues garnered significant community discussion, highlighting key pain points and desired enhancements:

- **[Issue #5190 [Question]](https://github.com/agentscope-ai/QwenPaw/issues/5190) — WeChat Work (Enterprise WeChat) approval interface invisible.** Users report that when private chat access control is enabled, there is no visible UI for approving requests, creating a dead end for enterprise workflows.
- **[Issue #5138 [Bug]](https://github.com/agentscope-ai/QwenPaw/issues/5138) — Windows client process continuously increasing.** A closed bug that resonated with users, detailing memory exhaustion issues on Windows.
- **[Issue #5156 [Feature]](https://github.com/agentscope-ai/QwenPaw/issues/5156) — Request for `kimi-for-coding` support and `uv` whitelist.** Users subscribed to Kimi's coding plan cannot leverage their paid access within CoPaw, creating a demand for direct API integration.
- **Pull Requests #5175 and #5186 ([PR #5186](https://github.com/agentscope-ai/QwenPaw/pull/5186)):** Two separate first-time-contributor PRs adding full and partial Vietnamese (vi) locale support, indicating strong community interest from the Vietnamese user base.

### 5. Bugs & Stability
Several critical bugs were reported after the v1.1.11.post2 release, indicating a regression in stability.

| Severity | Issue | Description | Fix Status |
| :--- | :--- | :--- | :--- |
| **Critical** | [#5061](https://github.com/agentscope-ai/QwenPaw/issues/5061) | Windows Tauri desktop startup is extremely slow (10+ minutes) and prone to "Not Responding" state since the switch from Python packaging. | No fix PR yet. |
| **Critical** | [#5138](https://github.com/agentscope-ai/QwenPaw/issues/5138) | Windows client process count continuously increases, consuming >90% RAM. | Closed (likely resolved in a recent patch or workaround). |
| **High** | [#5163](https://github.com/agentscope-ai/QwenPaw/issues/5163) | Regression in Gemini tool calling between v1.1.10 and v1.1.11.post2. | No fix PR yet. |
| **High** | [#5181](https://github.com/agentscope-ai/QwenPaw/issues/5181) | `pip install` dependency check in plugin system causes infinite loop and cmd window pop-ups on Windows when network is unstable. | No fix PR yet. |
| **High** | [#5184](https://github.com/agentscope-ai/QwenPaw/issues/5184) | Local model providers not displaying in the UI after upgrade to v1.1.11.post2. | No fix PR yet. |
| **Medium** | [#5192 (PR)](https://github.com/agentscope-ai/QwenPaw/pull/5192) | Fix for Rich console crash on legacy Windows terminals and protection against self-kill commands. | Open PR. |

### 6. Feature Requests & Roadmap Signals
Several feature requests signal strong user demand for improved developer (Coding) experience and deeper enterprise integration.

- **Likely in Next Version:**
    - **Vietnamese (vi) Locale:** Two PRs ([#5175](https://github.com/agentscope-ai/QwenPaw/pull/5175), [#5186](https://github.com/agentscope-ai/QwenPaw/pull/5186)) are under review; a consolidated version is likely to ship soon.
    - **Plugin Command Suggestions:** PR [#5189](https://github.com/agentscope-ai/QwenPaw/pull/5189) adds a framework for plugins to register `/commands` in the chat input, a strong candidate for merging.
- **On the Roadmap (User Requests):**
    - **Code Completion in Coding Mode** ([#5131](https://github.com/agentscope-ai/QwenPaw/issues/5131)) and **Code Highlighting** ([#5191](https://github.com/agentscope-ai/QwenPaw/issues/5191)) are high-demand features for developer users.
    - **Kimi-for-Coding** support with `uv` whitelist ([#5156](https://github.com/agentscope-ai/QwenPaw/issues/5156)) is a request from paying users with no viable solution.
    - **Computer Use for Windows** (PR [#5187](https://github.com/agentscope-ai/QwenPaw/pull/5187)) is a significant new feature adding GUI automation via UIA and Tauri control mode.
    - **Zalo Bot Channel** ([#5168](https://github.com/agentscope-ai/QwenPaw/issues/5168)) has been requested for the Vietnamese market.
    - **Feishu CardKit Streaming Optimization** ([#5167](https://github.com/agentscope-ai/QwenPaw/issues/5167)) reports poor performance on long replies.

### 7. User Feedback Summary
- **Key Pain Points:** The most vocal dissatisfaction centers on **Windows desktop stability**. Users are frustrated by the **slow Tauri startup** (5+ minutes vs 1-2 minutes before), the **memory leak forcing restarts**, and the **regression after the latest patch** (v1.1.11.post2). The **cron/heartbeat agent** limitations are also a point of confusion, with users expecting more autonomous behavior.
- **Satisfaction Signals:** The community actively contributes, with multiple first-time-contributor PRs (new features, bug fixes, i18n). The **Feishu CardKit streaming card** integration is appreciated, though its performance needs work. Users are eager to see **new channel integrations** (e.g., Zalo) and **enhanced coding features**.
- **Use Cases:** The most active use cases appear to be **enterprise chat agents** (WeChat Work, DingTalk, Feishu), **AI-assisted coding**, and **autonomous agents** (cron/heartbeat tasks for data management).

### 8. Backlog Watch
The following items require attention from maintainers due to age or lack of response:

- **[PR #4622 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/4622) — New DataPaw Plugin:** This feature-rich data-analysis plugin has been open for 24 days without merge or feedback. It represents a significant contribution that is languishing under review.
- **[PR #4902 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/4902) — Built-in PRD Management Tool:** Open for 13 days, this is a substantial feature replacing a plugin-based tool with a built-in one, complete with a frontend renderer. It needs a maintainer review.
- **[Issue #5165 [Question]](https://github.com/agentscope-ai/QwenPaw/issues/5165) — White Screen after Packaging:** A packaging script issue causing a completely broken build. This is a blocker for developers trying to create custom distributions and has no response.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for June 15, 2026.

---

## ZeroClaw Project Digest
**Date:** 2026-06-15
**Source Data:** GitHub (zeroclaw-labs/zeroclaw)

### 1. Today's Overview
Project activity is exceptionally high today, signaling a major development push. With **50 Pull Requests** and **42 Issues** updated in the last 24 hours, the community and core team are deeply engaged in addressing critical bugs, merging feature clusters, and refining the developer experience. The most significant themes are a wave of merged SMS and smart-home integrations, aggressive stabilization of the delegation and MCP tool passthrough, and critical fixes for the gateway and runtime configuration. This level of output indicates a project in a highly active and healthy state, likely preparing for a major release candidate.

### 2. Releases
**None.** No new releases were published on this date.

### 3. Project Progress
**Merged/Closed PRs (4 total):** The team focused on merging targeted fixes and a major internal refactor.
- **[CLOSED] [#7664](zeroclaw-labs/zeroclaw/pull/7664) - fix: `ask_user` fails instantly in gateway:** A critical bug was patched where the `ask_user` tool would fail immediately with a "Channel closed" error when used through the web gateway (fixed by xuwei-xy).
- **[CLOSED] [#7594](zeroclaw-labs/zeroclaw/pull/7594) - feat: Type-driven alias pickers & self-declaring enums:** A massive internal refactor (singlerider) that eliminates hardcoded config path special-casing. This is a foundational improvement for configuration UX.
- **[CLOSED] [#7384](zeroclaw-labs/zeroclaw/pull/7384) - feat: Pause/resume toggle for cron tasks:** Adds a pause/resume button to the scheduled tasks dashboard (Nillth), which was previously requested by users to avoid deleting and recreating jobs.

### 4. Community Hot Topics
The most active discussions highlight governance and security concerns.
- **[#6808](zeroclaw-labs/zeroclaw/issues/6808) - RFC: Work Lanes, Board Automation, and Label Cleanup (11 comments):** This is a governance RFC proposing a new system to route work more efficiently across the project. The high engagement suggests the community is eager for a more structured contribution process.
- **[#7470](zeroclaw-labs/zeroclaw/issues/7470) - Bug: Delegate agent mode rejects empty `allowed_tools` (7 comments):** A high-priority bug causing real workflow blocks for multi-agent setups. The depth of discussion indicates this is a critical feature for power users.
- **[#3642](zeroclaw-labs/zeroclaw/issues/3642) - Feature: Provide a "full" Docker image (13 comments, 3 👍):** Even though closed, this remains a top topic. The request for a pre-built Docker image with all features (like WhatsApp) enabled reflects a consistent user desire for easier onboarding.

### 5. Bugs & Stability
Stability was a major focus today, with several high-severity bugs being actively patched.
- **Critical (S0/S1):**
    - **[#7470](zeroclaw-labs/zeroclaw/issues/7470) - Delegate agent tool restrictions:** Blocks multi-agent workflows. **Fix in progress.**
    - **[#7542](zeroclaw-labs/zeroclaw/issues/7542) - `ask_user` channel error:** Blocks gateway-driven interactions. **Merged fix in PR #7664.**
- **High:**
    - **[#7424](zeroclaw-labs/zeroclaw/pull/7424) - `web_fetch` DNS resolution bug:** A security-critical wildcard (`["*"]`) for private hosts was not resolving DNS correctly. **PR is open for review.**
    - **[#7608](zeroclaw-labs/zeroclaw/pull/7608) - MCP tools invisible to delegates:** Delegate agents could not see MCP-provided tools. **PR is open for review.**
    - **[#5892](zeroclaw-labs/zeroclaw/pull/5892) - Empty `tool_choice` and orphaned tool_use:** Two long-standing production blockers for multiple providers (OpenAI, Bedrock, etc.) are finally being addressed in a massive fix PR.

**Summary:** The project is successfully identifying and shipping fixes for the most painful bugs, particularly around delegation and gateway stability.

### 6. Feature Requests & Roadmap Signals
A significant "feature burst" from the user `theonlyhennygod` landed today, signaling a push toward "Environment and Media" integrations.
- **New Integrations (Merged):** A series of SMS channels (Vonage, Sinch, Plivo, Telnyx) and smart-home/media tools (Sonos, Spotify, Shazam, 8Sleep, Philips Hue) were all closed. These likely shipped in a recent build.
- **New Provider Support (Merged):** Support for Inception Labs (Mercury), Lambda AI, Featherless AI, and Upstage Solar were also closed, dramatically expanding the model provider landscape.
- **Next Version Prediction (likely 0.81 or 1.0):** The current hot topics point to **Air-Gapped Execution (RFC #6293)** and the **Zerocode ACP Bridge (Tracker #6823)** as the next major architectural milestones. These are complex, high-risk features being actively discussed.

### 7. User Feedback Summary
- **Pain Point: "Barrier to entry for non-technical users."** This is the core complaint behind **Issue #3642** (Full Docker image), which has high engagement. Users want a "one-click" deploy experience.
- **Pain Point: "Workflow blocks with delegation."** Issues **#7470** (delegate tool restrictions) and **#6136** (MCP tools for delegates) show that the multi-agent ecosystem is still maturing and causing friction for advanced users.
- **Satisfaction: Strong response to "Feature Burst."** The reception to the wave of new integrations (SMS, Smart Home, Providers) seems positive. These are features users have been requesting and are now available.
- **Request: "Better documentation."** Issues like **#6760** (Docker docs) and **#7470** (documenting delegate restrictions) show a clear community need for documentation to keep pace with new features.

### 8. Backlog Watch
Several important issues require maintainer attention to prevent stagnation.
- **[CLOSED but Unresolved] #6074 - Track 153 lost commits:** While closed as a tracking issue, the underlying problem of a mass-revert (losing 153 commits) has no public root-cause analysis or recovery plan. This is a risk to contributor confidence.
- **[OPEN] #5662 - QQ channel voice duplicates (2 comments, last updated 2026-04-12):** This "S1 - workflow blocked" bug for the QQ channel has seen no maintainer response in over two months. The user is experiencing serious data duplication.
- **[OPEN] #5842 - Track: `extra_args` security validation (3 comments):** This open security tracking issue for the Codex CLI flag passthrough is awaiting a maintainer review to evaluate if the current implementation is safe enough.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*