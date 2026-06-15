# AI CLI Tools Community Digest 2026-06-15

> Generated: 2026-06-15 04:13 UTC | Tools covered: 9

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

# Cross-Tool AI CLI Ecosystem Comparison Report
**Date:** 2026-06-15

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape on June 15, 2026 shows a field in active flux: established players like Claude Code and OpenAI Codex are grappling with **regression-heavy releases and data-loss bugs**, while mid-tier tools (OpenCode, Pi) are shipping UX enhancements and extension APIs at a rapid pace. Gemini CLI and Qwen Code are investing heavily in **subagent reliability and security hardening**, respectively. A notable trend is the emergence of rebranding and consolidation—DeepSeek TUI's migration to **CodeWhale** signals market maturation, while Kimi Code and GitHub Copilot CLI remain quieter but show focused community demand for **transparency and spec compliance**. Across the board, subagent orchestration, cost transparency, and cross-platform stability remain the top unaddressed pain points.

---

## 2. Activity Comparison

| Tool | Open Issues (notable) | PRs in Last 24h | Release Today | Community Signal |
|---|---|---|---|---|
| **Claude Code** | 10 hot issues (3 critical) | 5 PRs (2 open) | None | High anxiety: recursion bugs, data loss |
| **OpenAI Codex** | 10 hot issues (Windows crash cluster) | 10 open PRs | None | Engineering momentum: async hooks, rate-limit UX |
| **Gemini CLI** | 10 hot issues (P1 hangs, false success) | 10 PRs (all Dependabot) | None | Subagent reliability dominates |
| **GitHub Copilot CLI** | 8 issues (low traffic) | 0 | None | Quiet; session poisoning noted |
| **Kimi Code** | 3 issues updated | 4 PRs (3 closed) | None | Low activity; rate-limit complaints simmer |
| **OpenCode** | 10 hot issues (regressions) | 10 PRs (high quality) | **v1.17.7** | High churn: shipped with regressions |
| **Pi** | 10 hot issues (Windows, TUI) | 10 PRs (active) | None | Vibrant: extension API, profiling, OAuth |
| **Qwen Code** | 10 hot issues (security, policy) | 10 PRs (feature-heavy) | None | High: cost visibility, session resume |
| **DeepSeek TUI / CodeWhale** | 10 hot issues (Windows, sub-agents) | 10 PRs (WhaleFlow, voice) | **v0.8.60** (rebrand) | Rebranding; orchestration focus |

**Key Takeaway:** No tool published a *new feature release* today except OpenCode (v1.17.7, bugfix but regressions). CodeWhale shipped a rebranding release. Activity is concentrated in PR pipelines—Gemini CLI's 42 Dependabot PRs and Pi's extension API work are the most voluminous.

---

## 3. Shared Feature Directions

### 3.1 Subagent/Agent Orchestration & Reliability
- **Claude Code**: Unbounded recursion (#68430, #68110) → demand for depth caps, `cwd` params
- **Gemini CLI**: Subagent hangs (#21409), false success reporting (#22323) → need for observability and kill switches
- **CodeWhale**: YOLO mode stalls (#2487), 120s timeouts (#1806) → request for swarm synthesis, fleet ledgers
- **Pi**: Interrupt regression (#5736), local LLM freezes (#5706)
- **OpenCode**: Forward parent attachments to subagents (#32302)

**Common Need:** Depth limits, role-based spawning control, better failure reporting, and configurable timeouts.

### 3.2 Cost Transparency & Rate-Limit Visibility
- **Claude Code**: Overcharging (#32544), excessive token burn (#68430)
- **OpenAI Codex**: `/usage` rate-limit redemption (PR #28154), real-time usage data (#15281)
- **Kimi Code**: Severe rate-limiting on paid plans (#2123), quota transparency demanded
- **OpenCode**: DeepSeek pricing pass-through (#28846, 79 upvotes)
- **Qwen Code**: Per-task token/time detail (PR #5118), cost export (PR #4564)
- **Pi**: Anthropic cache pricing fix (PR #5738)
- **CodeWhale**: Provider fallback to avoid rate-limit failures (#2574)

**Common Need:** Real-time token/cost counters, clear subscription quotas, and provider fallback on 429s.

### 3.3 Cross-Platform Stability (Especially Windows)
- **Claude Code**: Pty leaks on macOS (#65995), kernel zone leak (#66020)
- **OpenAI Codex**: Windows crash loop (#27979, #27367), WSL binary missing (#28103)
- **Kimi Code**: Windows paste fix (PR #2018), log locking (PR #2020)
- **OpenCode**: Linux clipboard support (PR #32370)
- **Pi**: Windows bash detection (#5103), SIGTERM terminal corruption (#5724)
- **Qwen Code**: MCP servers not working on Windows (#4218)
- **CodeWhale**: TUI freeze on Windows (#1812), MSBuild failure (#3147), glibc dependency (#1067)

**Common Need:** Windows-specific testing, native terminal handling, and platform-consistent sandboxing.

### 3.4 Security & Permission Models
- **Claude Code**: Autonomous paid API calls (#67699)
- **Gemini CLI**: Destructive git/DB commands (#22672), secrets in Auto Memory (#26525)
- **GitHub Copilot CLI**: Session poisoning from malformed attachments (#3791)
- **OpenCode**: MCP server env-leakage (#31778)
- **Qwen Code**: Permission-contract bypass (#5102), antivirus false positive (#5055)
- **CodeWhale**: Persistent permission rules (#1186, #3233)

**Common Need:** Sandbox-guaranteed execution, configurable allow/deny lists, and secret redaction before model context.

### 3.5 Session/Project Management
- **OpenAI Codex**: Rename tasks (#12564, closed), sidebar showing "No chats" (#25500)
- **OpenCode**: Session rename (#32375), bookmarks (#24017), compaction undo (#32368)
- **Qwen Code**: Resume without synthetic "continue" (PR #5030)
- **CodeWhale**: Multi-session TUI switching (#5700)
- **Kimi Code**: Auto-load project context files (#850, closed)

**Common Need:** Human-readable session titles, history search, crash recovery, and persistent project context.

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | Kimi Code | OpenCode | Pi | Qwen Code | CodeWhale |
|---|---|---|---|---|---|---|---|---|---|
| **Primary Focus** | Agent depth & cost control | Enterprise sandbox & rate-limit UX | Subagent reliability & eval | Spec compliance & BYOK | Basic coding assist | TUI/Desktop UX & MCP | Extension API & multi-provider | Cost visibility & rule systems | Multi-agent orchestration |
| **Target Users** | Cost-sensitive power users | Enterprise Windows devs | Google Cloud ecosystem | GitHub/Azure ecosystems | Chinese market | Plugin developers | TUI power users | Self-hosters & cost-aware | Agent-heavy devs |
| **Technical Approach** | Node.js, subagent spawning | Electron + WSL sandbox | TypeScript, MCP, GenAI SDK | CAPI integration | Python-based | Rust (TUI) + Go (server) | TypeScript + Rust (extensions) | TypeScript, web-shell | Rust (TUI) |
| **Community Maturity** | Mature, high anxiety | Mature, engineering heavy | Internal-focused | Stagnant | Nascent | Rapidly maturing | Vibrant, extension economy | Feature-rich, policy-driven | Rebranding, orchestration |
| **Key Weakness** | Recursion → cost explosion | Windows crash regressions | Subagent unreliability | Low activity | Rate-limit opacity | Regression-prone releases | TUI edge cases | Free tier instability | Windows stability |

**Key Differentiators:**
- **Claude Code** leads in community engagement volume but suffers from catastrophic bugs (subagent recursion).
- **OpenAI Codex** is shipping the most infrastructure-heavy PRs (async hooks, MITM CA, rate-limit redemption) but has the worst Windows regressions.
- **Pi** has the most vibrant extension economy (vim modal editor, profiling, OAuth providers).
- **OpenCode** ships fastest (v1.17.7 today) but with regressions—high risk/high reward.
- **CodeWhale** is the only tool explicitly building multi-agent orchestration (WhaleFlow).

---

## 5. Community Momentum & Maturity

### Most Active Communities (by issue/PR volume)
1. **OpenAI Codex** — 10 PRs, 10 hot issues, strong engineering team response
2. **Gemini CLI** — 10 PRs (all deps), 10 hot issues, but internal-focused
3. **OpenCode** — 10 PRs (feature-heavy), 10 hot issues, shipped release today
4. **Pi** — 10 PRs (extension API, profiling), 10 hot issues
5. **Qwen Code** — 10 PRs (session resume, cost UI), 10 hot issues

### Most Stable / Slowest Moving
- **GitHub Copilot CLI** — 8 issues, 0 PRs, no release. Appears dormant.
- **Kimi Code** — 3 issues updated, 4 PRs (all closed). Low engagement.
- **Claude Code** — High issue volume but no release today; critical bugs unaddressed.

### Most Rapidly Iterating
- **OpenCode**: Shipped v1.17.7 today, 10+ active PRs, regressions indicate fast cycle.
- **Pi**: 10 PRs in 24h including profiling, OAuth, vim editor—highest feature velocity.
- **CodeWhale**: Rebrand + 28-commit draft for v0.8.61; high churn from rebranding.

### Maturity Assessment
- **Enterprise-ready**: Gemini CLI (Google-backed, eval frameworks). OpenAI Codex (close, but Windows regressions block).
- **Power-user favorite**: Claude Code (best-in-class features, but trust-eroding bugs). Pi (rich extensions).
- **Rising**: OpenCode (fastest feature delivery). Qwen Code (strong cost features).
- **Questionable**: GitHub Copilot CLI (stagnant). Kimi Code (Chinese market, low activity).

---

## 6. Trend Signals

### 6.1 The Subagent Trust Crisis
Across Claude Code, Gemini CLI, and CodeWhale, users are reporting **unbounded recursion, silent failures, and runaway costs** from subagents. The industry has shipped agent-tree architectures without guardrails. Expect **mandatory depth caps, human-in-the-loop approval for agent spawning, and cost budgets** to become table-stakes features within 3 months.

### 6.2 Windows as the Weakest Link
Every tool except Claude Code reports **Windows-specific crashes, terminal freezes, sandbox failures, or packaging defects**. The Windows developer market is large but underserved. Tools that solve Windows stability will capture market share—OpenAI Codex's failure here is notable given their enterprise focus.

### 6.3 Cost Transparency as Competitive Moat
Qwen Code's per-task token/time UI (PR #5118) and OpenAI Codex's rate-limit redemption (PR #28154) signal that **cost visibility is becoming a differentiator**. Tools that hide API consumption behind abstractions (Claude Code's current state) will lose cost-sensitive users to tools that expose granular data.

### 6.4 Extensions Are the New Battleground
Pi's extension API (prompt guidelines, profiling, vim editor) and OpenCode's MCP 2.0 support indicate a shift toward **plugin ecosystems** as the primary growth vector. Tools without extension APIs (Claude Code, GitHub Copilot CLI) risk being out-innovated by community contributions.

### 6.5 Regional Pricing Pressure
Claude Code's #17432 (442 upvotes for India pricing) and Kimi Code's Chinese market focus highlight that **global pricing parity** is a major blocker for adoption in price-sensitive markets. Tools that ignore regional pricing will fail to expand beyond North America/Europe.

### 6.6 Security Is Becoming a First-Class Concern
Qwen Code's permission-contract bypass (#5102) and autonomous paid API calls (#67699 in Claude Code) are early warnings. As agents gain more autonomy, **sandbox enforcement, secret redaction, and permission systems** will shift from nice-to-have to mandatory for enterprise procurement.

### 6.7 TUI/Desktop Convergence
OpenCode's file tree tab, Qwen Code's web-shell, CodeWhale's VS Code extension, and Pi's terminal theme detection all point toward **blended TUI-desktop experiences**. The CLI-only era is ending; tools must offer graphical affordances for file browsing, session management, and settings.

---

## Summary for Decision-Makers

| If you need... | Consider... | But watch out for... |
|---|---|---|
| **Most capable agent** | Claude Code | Cost explosion from recursion bugs |
| **Enterprise Windows stability** | OpenAI Codex (eventually) | Current crash loop on v26.609.4994.0 |
| **Lowest cost / self-hosted** | Qwen Code or OpenCode | Free tier instability; regression risk |
| **Best extension ecosystem** | Pi | TUI edge cases; Windows bash brittle |
| **Multi-agent orchestration** | CodeWhale (early) | Rebranding churn; Windows flaws |
| **Simplest, most stable** | GitHub Copilot CLI (for now) | Low activity; session poisoning bug |
| **Chinese market / Kimi fans** | Kimi Code | Severe rate-limiting on paid plans |

**Bottom Line:** No tool is fully production-ready today. The field is converging on subagent safety, cost transparency, and cross-platform stability as the three pillars that will determine long-term winners. Tools that ship robust permission models and extension APIs first will dominate the next 12 months.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data Snapshot:** github.com/anthropics/skills | **Date:** 2026-06-15

---

## 1. Top Skills Ranking

The following PRs generated the most discussion and community engagement:

### #514 — Document Typography Skill (Open)
**Functionality:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universal pain point—typographic quality in Claude's output.
**Discussion highlights:** The community recognized this as solving a "silent quality crisis" affecting every document Claude generates. Debates centered on whether typographic rules should be language/locale-aware.
**Status:** Open; active since March 2026.
[GitHub: PR #514](https://github.com/anthropics/skills/pull/514)

### #486 — ODT Skill (Open)
**Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods). Bridges Claude with LibreOffice/OpenOffice ecosystems.
**Discussion highlights:** Strong interest from European public-sector and enterprise users who require ODF compliance. Request for LibreOffice macro integration emerged as a sub-thread.
**Status:** Open; last updated April 2026.
[GitHub: PR #486](https://github.com/anthropics/skills/pull/486)

### #210 — Frontend-Design Skill Improvement (Open)
**Functionality:** Revises the frontend-design skill for clarity, actionability, and single-conversation execution. Ensures every instruction is specific enough to steer Claude behavior without ambiguity.
**Discussion highlights:** Positive reception; community members offered concrete examples of ambiguous instructions from the original skill. Consensus that the rewrite should serve as a template for other skill maintainers.
**Status:** Open; ongoing refinement.
[GitHub: PR #210](https://github.com/anthropics/skills/pull/210)

### #83 — Skill-Quality-Analyzer & Skill-Security-Analyzer (Open)
**Functionality:** Two meta-skills that evaluate other skills across five quality dimensions (structure, documentation, examples, resources, security). Addresses skill quality assurance at scale.
**Discussion highlights:** High interest from skill creators. Security dimension sparked debate about false positives in sandboxed vs. non-sandboxed environments.
**Status:** Open; proposed November 2025.
[GitHub: PR #83](https://github.com/anthropics/skills/pull/83)

### #1140 — Agent-Creator Skill (Open)
**Functionality:** Meta-skill for task-specific agent sets; includes multi-tool evaluation fixes and Windows support for recalc.py.
**Discussion highlights:** Tied to Issue #1120 regarding evaluation stability. Community requested explicit agent composition patterns rather than implicit groupings.
**Status:** Open; merged stability fixes into this PR.
[GitHub: PR #1140](https://github.com/anthropics/skills/pull/1140)

### #444 — AURELION Skill Suite (Open)
**Functionality:** Four skills (kernel, advisor, agent, memory) forming a structured cognitive + memory framework for professional knowledge management and AI collaboration. Includes a 5-floor cognitive architecture.
**Discussion highlights:** Most ambitious single-suite submission. Debate centered on overlap with existing memory-related skills (#154 shodh-memory). Maintainers requested deduplication analysis.
**Status:** Open; updated May 2026.
[GitHub: PR #444](https://github.com/anthropics/skills/pull/444)

### #154 — Shodh-Memory Skill (Open)
**Functionality:** Persistent memory system for AI agents that maintains context across conversations. Uses `proactive_context` calls on every user message to surface relevant memories.
**Discussion highlights:** Interest in interoperability with AURELION memory. Technical discussion about memory eviction policies and token budget management.
**Status:** Open; active since December 2025.
[GitHub: PR #154](https://github.com/anthropics/skills/pull/154)

---

## 2. Community Demand Trends

From the most-engaged Issues, five distinct demand directions emerge:

| Demand Direction | Evidence (Key Issues) | Signal Strength |
|---|---|---|
| **Org-wide skill sharing & distribution** | #228 (14 comments, 👍7) — Users want shared skill libraries and direct sharing links instead of manual `.skill` file transfers | **Highest** |
| **Improving the skill-creator toolchain** | #556, #202, #1061, #1169 — `run_eval.py` reports 0% recall on all queries; toolchain is broken across Windows and Linux | **Critical** |
| **Security and trust boundaries** | #492 (7 comments) — Community skills under `anthropic/` namespace impersonate official ones; users request namespace validation | **High** |
| **Windows compatibility** | #1061 (3 comments) — Subprocess PATHEXT issues, cp1252 encoding, `select` on pipes preclude full Windows adoption | **High** |
| **Infrastructure & integration** | #16 (MCP exposure), #29 (Bedrock support), #1220 (multi-file bundling) — Users want Skills to integrate with broader tool ecosystem | **Medium** |

**Key takeaway:** The community is not primarily asking for *new Skill content*—they are demanding **toolchain reliability, secure distribution, and cross-platform support** for the existing ecosystem.

---

## 3. High-Potential Pending Skills

These PRs have active comment threads and are likely to land soon:

- **#538** — *fix(pdf): correct case-sensitive file references* — A targeted bugfix; low risk, high impact. [PR #538](https://github.com/anthropics/skills/pull/538)
- **#539** — *fix(skill-creator): warn on unquoted description with YAML special characters* — Addresses silent YAML parsing failures. [PR #539](https://github.com/anthropics/skills/pull/539)
- **#541** — *fix(docx): prevent tracked change w:id collision* — Prevents DOCX corruption when adding tracked changes. [PR #541](https://github.com/anthropics/skills/pull/541)
- **#1298** — *fix(skill-creator): run_eval.py always reports 0% recall* — The most-reported bug (#556, #1169, #1061); six independent reproductions. Likely the next merged fix. [PR #1298](https://github.com/anthropics/skills/pull/1298)
- **#723** — *testing-patterns skill* — Full-stack testing coverage (unit, React, E2E). Community requested testing skills repeatedly. [PR #723](https://github.com/anthropics/skills/pull/723)
- **#509** — *docs: add CONTRIBUTING.md* — Addresses a community health gap (25% GitHub health score). Low friction for maintainers. [PR #509](https://github.com/anthropics/skills/pull/509)
- **#147** — *codebase-inventory-audit skill* — 10-step orphaned code and documentation gap analysis. Strong interest from enterprise users. [PR #147](https://github.com/anthropics/skills/pull/147)

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is not for any single new Skill domain, but for a reliable, cross-platform, and secure skill toolchain—specifically fixing `run_eval.py`'s universal 0% recall bug and enabling org-wide skill distribution—before the content library can grow sustainably.**

---

# Claude Code Community Digest — 2026-06-15

## Today's Highlights
No new releases shipped in the last 24 hours, but the community is buzzing with a **critical subagent recursion bug** (#68430) that can cause exponential token burn—a top-priority concern. Multiple reports of **pty leaks on macOS** and **silent file truncation on Windows** remain unaddressed, while a long-running **India pricing feature request** (#17432) continues to dominate community engagement with 442 upvotes.

## Releases
No releases published in the last 24 hours.

## Hot Issues

1. **[#68430 — Subagent spawning and subagent pattern bugs trigger infinite recursion, infinite token usage](https://github.com/anthropics/claude-code/issues/68430)** (CRITICAL, 7 comments)
   - Agents spawn child agents 50+ levels deep, ignoring `CLAUDE_CODE_FORK_SUBAGENT=0`. Permission denials trigger *more* agents instead of stopping. This is the most urgent bug in the tracker today—catastrophic for cost.
   
2. **[#68110 — General-purpose sub-agents recursively spawn unbounded child agents](https://github.com/anthropics/claude-code/issues/68110)** (OPEN, 4 comments)
   - Complementary to #68430. The `Agent` tool with `general-purpose` role grants sub-agents the ability to spawn their own children, creating exponential fan-out with no depth limit. Community is calling for an immediate depth cap.

3. **[#53940 — Cowork Edit/Write tools silently truncate files via byte-conservation buffer cap](https://github.com/anthropics/claude-code/issues/53940)** (OPEN, 31 comments)
   - Deterministic bug: files are silently truncated at a fixed buffer size. Affects all file sizes. 12 upvotes, strong community attention—data loss risk is high.

4. **[#17432 — India-Specific Pricing Plans (INR)](https://github.com/anthropics/claude-code/issues/17432)** (OPEN, 194 comments, 442 👍)
   - The most-upvoted open issue. Users want INR pricing similar to OpenAI and Google. No official response yet. Community sentiment: Anthropic is losing the Indian market.

5. **[#41458 — cleanupPeriodDays: 99999 ignored — 490 sessions silently deleted](https://github.com/anthropics/claude-code/issues/41458)** (OPEN, 16 comments)
   - Users explicitly set retention to max; sessions vanished anyway. Tagged as regression and data-loss. A trust-eroding bug.

6. **[#32544 — Extra usage charged despite available plan capacity + false rate limit errors](https://github.com/anthropics/claude-code/issues/32544)** (OPEN, 15 comments, 14 👍)
   - Overbilling and false rate-limit errors on Linux. Affects cost-sensitive teams. No resolution timeline.

7. **[#63870 — Bash tool calls emitted as raw <invoke> text instead of executing](https://github.com/anthropics/claude-code/issues/63870)** (OPEN, 11 comments, 13 👍)
   - Model hallucinates the tool call XML instead of executing it. 23 malformed calls in a single session. Marked duplicate but evidence-rich.

8. **[#66020 — macOS kernel zone leak (data.kalloc.1024) from Claude Code CLI](https://github.com/anthropics/claude-code/issues/66020)** (OPEN, 7 comments)
   - Leak rate scales from 21 → 1027/sec with agent load; kernel panics at ~20GB. Mac-specific but severe: system-level instability.

9. **[#65585 — Auto-compact stopped working for third-party API providers since v2.1.161](https://github.com/anthropics/claude-code/issues/65585)** (OPEN, 4 comments, 3 👍)
   - Regression for users of alternative backends (OpenRouter, etc.). Auto-compact is essential for managing context windows in long sessions.

10. **[#68498 — Feature request: Appshots-style window capture](https://github.com/anthropics/claude-code/issues/68498)** (OPEN, 4 comments)
    - Inspired by OpenAI Codex's Appshots. Wants macOS accessibility-based full-window capture including scrolled-off-screen content. Freshly filed, gathering interest.

## Key PR Progress

1. **[#43598 — Add upstream issue sync workflow](https://github.com/anthropics/claude-code/pull/43598)** (CLOSED)
   - Script to fetch and normalize upstream issues via GitHub CLI. Merged—good for cross-repo visibility.

2. **[#68423 — fix(scripts): don't auto-close assigned issues in sweep](https://github.com/anthropics/claude-code/pull/68423)** (OPEN)
   - Fixes `sweep.ts` which was closing assigned issues despite only intending to close stale unassigned ones. Community-contributed, low risk.

3. **[#67699 — [BUG] Claude autonomously ran background scripts calling a paid external API](https://github.com/anthropics/claude-code/pull/67699)** (OPEN, bounty $29)
   - Agent autonomously called a paid external service without user consent. Fix via NVIDIA AI automation. Raises safety/cost concerns.

4. **[#67409 — [BUG] Account downgraded due to billing error](https://github.com/anthropics/claude-code/pull/67409)** (OPEN, bounty $200)
   - Billing logic bug causing unwarranted downgrades. High-value bounty, still open.

5. **[#67722 — [BUG] Claude autonomously ran background scripts calling a paid external](https://github.com/anthropics/claude-code/pull/67722)** (CLOSED)
   - Similar to #67699. Closed—likely superseded or duplicate.

## Feature Request Trends

- **Regional pricing (INR)**: #17432 dominates with 442 upvotes. Users are explicitly comparing to OpenAI and Google's local pricing. No Anthropic response yet.
- **Per-message model selection**: Multiple requests for switching models mid-session (#68165). Power users want Haiku for simple edits, Opus for complex reasoning—without restarting.
- **Subagent control**: Demand for `cwd` parameter on Task tool (#12748), depth limits, and role-based restrictions on agent spawning. The recursion bugs are accelerating this.
- **Window/UI capture**: #68498 follows OpenAI Codex's Appshots. Users want macOS accessibility-based full-window text capture including scrolled content.
- **Timezone awareness**: #64988 requests Claude default to local timezone for cron/log/deprecation messages instead of UTC.

## Developer Pain Points

- **Subagent recursion / cost explosion**: Two concurrent critical bugs (#68430, #68110) describe unbounded recursive agent spawning leading to "catastrophic token burn." This is the top concern today.
- **Silent data loss**: File truncation (#53940) and session deletion (#41458) erode trust. Both are tagged with `data-loss`.
- **Billing discrepancies**: Overcharging (#32544), false rate limits, and downgrade bugs (#67409) suggest systemic billing logic issues.
- **macOS resource exhaustion**: Pty leak (#65995, #66434) and kernel zone leak (#66020) cause system-wide instability. Two separate but related reports.
- **Third-party provider regressions**: Auto-compact broken since v2.1.161 (#65585). Affects users who rely on non-Anthropic backends.
- **Tool execution failures**: Malformed `<invoke>` text instead of executing bash (#63870), and tool results returning "missing due to internal error" (#68457) degrade core functionality.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-15

## Today's Highlights
The Codex ecosystem is experiencing significant instability on Windows Desktop following the June 12 update (v26.609.4994.0), with multiple reports of app crashes on launch and WSL sandbox failures. Meanwhile, the engineering team is actively shipping infrastructure improvements around async hooks, MITM CA management for sandboxed children, rate-limit reset redemption, and external agent import telemetry. A long-standing enhancement request to allow renaming task/thread titles (filed in February) was finally closed today with substantial community engagement.

## Releases
No new versions were published in the last 24 hours.

## Hot Issues

1. **[#12564 — [CLOSED] Allow renaming task/thread titles to improve history navigation](https://github.com/openai/codex/issues/12564)**
   *Author: dirshaye | 👍 111 | 💬 80*
   After nearly four months and overwhelming community demand, this enhancement request for thread renaming in the IDE extension has been closed. It received the highest engagement of any issue tracked today—111 upvotes and 80 comments—signaling strong user desire for better session management in long-lived workflows.

2. **[#27979 — Windows Codex App 26.609.4994.0 no longer opens after update](https://github.com/openai/codex/issues/27979)**
   *Author: SocialK | 👍 6 | 💬 21*
   A critical regression: the latest Windows MSIX build crashes on launch. Users on Windows 10 and 11 Pro are affected. The "About Codex" dialog is inaccessible, making version verification impossible. This is the top-priority breaking bug for Windows users today.

3. **[#10571 — "Bad request" error (CLI)](https://github.com/openai/codex/issues/10571)**
   *Author: atomical | 👍 7 | 💬 20*
   A long-running, still-open issue affecting Codex CLI v0.94.0 with `gpt-5.2 xhigh`. Users see opaque 400 errors with no actionable diagnostics. Has persisted for over four months without resolution, suggesting a deeper protocol or routing issue.

4. **[#25500 — Desktop Projects sidebar shows "No chats" for projects with older non-archived conversations](https://github.com/openai/codex/issues/25500)**
   *Author: kezh9527 | 👍 2 | 💬 18*
   A data-display bug where the Codex Desktop sidebar fails to list existing conversations in a project. Users report the conversations are accessible via direct links but invisible in the UI, causing confusion and lost productivity.

5. **[#28103 — Codex desktop 26.609.4994.0 missing Linux codex binary — breaks "Run agent in WSL"](https://github.com/openai/codex/issues/28103)**
   *Author: qiyueqiu | 👍 9 | 💬 5*
   A packaging defect in the same Windows v26.609.4994.0 release: the MSIX bundle is missing the Linux `codex` binary from `app/resources`. This completely breaks the "Run agent in WSL" feature, a core workflow for hybrid Windows/Linux developers.

6. **[#27367 — Codex desktop app immediately exits on Windows 10 Pro 22H2 after update](https://github.com/openai/codex/issues/27367)**
   *Author: zms0529 | 👍 0 | 💬 9*
   A second Windows crash report with a similar profile to #27979, specifically on Windows 10 22H2. Notably, the CLI works fine on the same machine, pointing to a desktop-electron sandboxing or packaging issue rather than an authentication problem.

7. **[#27353 — Project chat history disappeared after latest Codex app update](https://github.com/openai/codex/issues/27353)**
   *Author: maksymdonets | 👍 3 | 💬 7*
   After updating to v26.608.12217 (Jun 9, 2026), several Pro users on macOS report that their project-level chat history vanished. This raises concerns about data migration or storage schema changes across updates.

8. **[#15281 — Feature: Expose full usage/limits data in CLI (/status command)](https://github.com/openai/codex/issues/15281)**
   *Author: milord-x | 👍 15 | 💬 6*
   A community feature request with strong support (15 upvotes). Users want the CLI `/status` command to show real-time rate-limit consumption, reset windows, and remaining allowances to avoid surprises mid-session.

9. **[#25431 — Expose spellchecking settings in app settings (Windows Desktop)](https://github.com/openai/codex/issues/25431)**
   *Author: VOOM108 | 👍 14 | 💬 5*
   A user-experience request with 14 upvotes: Windows Desktop users are frustrated by the lack of a toggle to disable spellcheck in the Codex app. Currently it's always on and intrusive.

10. **[#28248 — Windows sandbox fails all read operations with "apply deny-read ACLs" after power outage](https://github.com/openai/codex/issues/28248)**
    *Author: romansydiuk-dev | 👍 0 | 💬 3*
    A sandbox resilience bug: after an unexpected system crash or power loss, the Windows sandbox enters a corrupted state where all file reads are denied due to applied ACLs. This is a data-safety concern for users relying on sandbox persistence.

## Key PR Progress

1. **[#28165 — Use PathUri in filesystem permission paths for exec-server](https://github.com/openai/codex/pull/28165)**
   *Author: anp-oai*
   Refactors filesystem path containment to support heterogeneous app-server and exec-server platforms. Critical groundwork for cross-platform sandbox configuration and the upcoming sandbox-as-a-service model.

2. **[#25888 — Prepare managed child MITM CA env](https://github.com/openai/codex/pull/25888)**
   *Author: winston-openai*
   Parent PR in a multi-stack effort to preserve and materialize CA roots inside managed (child) sandbox environments. Essential for enterprise deployments where MITM TLS inspection is mandatory.

3. **[#28008 — Add external agent import result accounting](https://github.com/openai/codex/pull/28008)**
   *Author: charlesgong-openai*
   Introduces a stable import ID and structured accounting for external-agent imports (plugins, sessions). Enables clients to correlate sync and async import completions with artifact type summaries—key for plugin ecosystem reliability.

4. **[#28143 — feat(app-server): expose rate-limit reset credits](https://github.com/openai/codex/pull/28143)**
   *Author: jayp-oai*
   Adds backend support for reading and redeeming personal rate-limit reset credits via the `account/rateLimits/read` API. This is the server-side foundation for the TUI `/usage` redeem flow.

5. **[#28235 — Add request user input auto-resolution timer](https://github.com/openai/codex/pull/28235)**
   *Author: shijie-oai*
   Adds a 60-second hidden + 60-second visible countdown for `request_user_input` prompts when `autoResolutionMs` is set. Prevents sessions from hanging indefinitely on unattended prompts. Snoozes on user interaction.

6. **[#28154 — feat(tui): add rate-limit reset redemption to /usage](https://github.com/openai/codex/pull/28154)**
   *Author: jayp-oai*
   Restores and extends the `/usage` CLI command with rate-limit reset redemption capabilities. Directly addresses the community request in #15281 for better usage transparency.

7. **[#28232 — Add workspace headline statusline item](https://github.com/openai/codex/pull/28232)**
   *Author: xli-oai*
   Adds backend-client types and an app-server v2 API for workspace messages, with a TUI statusline item that polls every 10 seconds. Gated to Enterprise ChatGPT/Codex accounts. Improves visibility for team-based workflows.

8. **[#27452 — Run async hooks and deliver output on accepted requests](https://github.com/openai/codex/pull/27452)**
   *Author: abhinav-oai*
   Activates asynchronous hook execution (declared but previously disabled). An async hook may finish after its triggering operation; output is delivered only when the next model request accepts it. A major step toward non-blocking agent workflows.

9. **[#27771 — Add a bounded runtime for async hooks](https://github.com/openai/codex/pull/27771)**
   *Author: abhinav-oai*
   Provides session-scoped ownership, deterministic delivery gates, and hard resource limits for async hooks—the runtime substrate for #27452 and #27772. Prevents runaway background tasks.

10. **[#28234 — Increase default MCP tool timeout to 300 seconds](https://github.com/openai/codex/pull/28234)**
    *Author: adaley-openai*
    Doubles the default MCP tool-call timeout from 120 to 300 seconds. Addresses community frustration with timeouts during long-running Computer Use and plugin operations.

## Feature Request Trends

- **Session & project navigation improvements**: The top-voted issue today (#12564) was about renaming task/thread titles. Combined with #25500 (sidebar not showing chats) and #23280 (TUI long-response scrolling), there's a clear demand for better session history organization and visibility in both the desktop app and CLI/TUI.
- **Rate-limit transparency and redemption**: Multiple issues (#15281, #28242, #28251, #28249) request real-time rate-limit visibility and the ability to redeem earned reset credits directly in the CLI. The corresponding PRs #28143 and #28154 show the team is actively delivering on this.
- **Windows Desktop stability**: The volume and severity of Windows-specific crashes (#27979, #27367, #28103) make this the single most urgent feature request by pain level—users are asking not for new features but for the app to simply open.
- **Spellcheck control (#25431)**: A small but highly upvoted UX request: give users a settings toggle to disable intrusive spellcheck in the Codex app text editor.

## Developer Pain Points

- **Windows Desktop app crash loop after update**: The June 12 release (v26.609.4994.0) has caused at least three distinct crash profiles on Windows—app fails to open, immediate exit on launch, and WSL binary missing. Users on Windows 10 and 11, Pro and Plus subscriptions alike are affected. The only known workaround is to revert to a prior version or use the CLI.
- **Data persistence and visibility regressions**: Multiple users report chat history disappearing after updates (#27353) or the sidebar showing "No chats" for projects that contain conversations (#25500). This undermines trust in the app's data layer across version upgrades.
- **Disconnected rate-limit state (#28242)**: Users who upgrade their subscription mid-session find Codex still enforcing their *old* rate limits. The system does not re-check subscription state dynamically, locking users out of their newly purchased capacity until a restart or cache clear.
- **Sandbox fragility on Windows (#28248)**: The sandbox does not gracefully recover from system crashes, leaving files permanently inaccessible via deny-read ACLs. This is a reliability and data-loss concern for developers using Codex sandbox for important work.
- **Opaque "Bad request" errors (#10571)**: A four-month-old CLI issue with gpt-5.2 returning 400 errors with no diagnostic payload. The lack of error details forces developers to guess the cause, wasting debugging time.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-15

## Today's Highlights

No new releases were published in the last 24 hours, but the repository saw a major wave of dependency updates via Dependabot across 42 active pull requests. The community continues to focus heavily on agent reliability, with ongoing investigations into subagent hang behavior, false success reporting, and evaluation infrastructure maturity.

## Releases

No new releases in the last 24 hours.

## Hot Issues

**10 noteworthy open issues, ranked by community traction and engineering impact:**

1. **[Generalist agent hangs indefinitely](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1 bug with 8 reactions. Users report the CLI hangs forever when deferring to the generalist agent for simple tasks (folder creation). Workaround: instructing the model not to use sub-agents. Active `need-retesting` label suggests a pending fix requires validation.

2. **[Agent should stop/discourage destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)** — P2 customer issue with 1 reaction. The model occasionally uses `git reset --force` or destructive DB commands when safer alternatives exist. Community is requesting safety guardrails and prompt-level constraints.

3. **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 bug with 2 reactions. The `codebase_investigator` subagent reports `status: "success"` and termination reason `"GOAL"` despite hitting the maximum turn limit without completing analysis. This masks actual failures and wastes user time.

4. **[Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** — P1 customer epic with 0 reactions (likely high internal priority). Follow-up on the behavioral evals framework; 76 tests generated across 6 Gemini variants. Critical for regression detection.

5. **[Shell command execution gets stuck with "Waiting input"](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1 bug with 3 reactions. Simple CLI commands hang after completion, falsely showing "Awaiting user input." Reproduced with trivial commands — a core stability issue.

6. **[AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — P2 investigation epic with 1 reaction. Tracks whether AST-aware tooling can improve codebase navigation precision and reduce token waste. Split into child issues for file reads and CLI tools.

7. **[Auto Memory retries low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** — P2 bug with 0 reactions. Sessions judged as "low-signal" by the extraction agent remain unprocessed and are repeatedly surfaced, causing infinite retries. Needs a skip-and-mark mechanism.

8. **[Gemini CLI encounters 400 error with >128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** — P2 bug with 0 reactions. When more than 128 tools are configured, the API rejects requests. Community expects smarter tool scoping rather than dropping tools.

9. **[Model frequently creates tmp scripts in random spots](https://github.com/google-gemini/gemini-cli/issues/23571)** — P2 bug with 0 reactions. By restricting shell execution, the model generates edit scripts across various directories, polluting the workspace and complicating commits.

10. **[Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)** — P2 security bug with 0 reactions. Auto Memory sends transcript content to models for redaction *after* content is in context, and logs existing skill content. Requests deterministic pre-redaction and reduced logging.

## Key PR Progress

**10 important pull requests from the last 24 hours:**

1. **[fix: keep array tool results out of structuredContent](https://github.com/google-gemini/gemini-cli/pull/27730)** — P1 fix by he-yufeng. Prevents MCP transport from coercing JSON arrays into `structuredContent`, fixing calendar-style payload issues. Includes regression test.

2. **[fix(core): keep auto visible without preview access](https://github.com/google-gemini/gemini-cli/pull/27718)** — P2 fix by he-yufeng. Prevents the `auto` model alias from being filtered out for users without preview access when dynamic model configuration is enabled.

3. **[Fix issue #27728: truncate telemetry metric attributes](https://github.com/google-gemini/gemini-cli/pull/27729)** — P2 fix by imsrnfo. Truncates telemetry attributes to 1024 characters to prevent GCP export errors that flood the terminal with stack traces.

4. **[chore(deps): bump @google/genai from 1.30.0 to 2.8.0](https://github.com/google-gemini/gemini-cli/pull/27929)** — Major version bump for the core GenAI SDK. Likely introduces breaking changes in model interaction patterns.

5. **[chore(deps): bump puppeteer-core from 24.39.0 to 25.1.0](https://github.com/google-gemini/gemini-cli/pull/27931)** — Major version bump for browser automation dependency. May affect browser subagent behavior on Wayland (see issue #21983).

6. **[chore(deps): bump undici from 7.24.5 to 8.4.0](https://github.com/google-gemini/gemini-cli/pull/27928)** — Major HTTP client dependency update. Impacts all network requests including model API calls and MCP tool communication.

7. **[chore(deps): bump the npm-dependencies group with 53 updates](https://github.com/google-gemini/gemini-cli/pull/27925)** — Massive bulk dependency update. Includes `@agentclientprotocol/sdk` jumping from 0.16.1 to 0.25.0, suggesting protocol-level changes.

8. **[chore(deps): bump yargs from 17.7.2 to 18.0.0](https://github.com/google-gemini/gemini-cli/pull/27933)** — CLI argument parser major update. May affect flag parsing for `gemini-cli` commands.

9. **[chore(deps): bump marked from 15.0.12 to 18.0.5](https://github.com/google-gemini/gemini-cli/pull/27934)** — Markdown renderer major version bump. Could affect how the CLI renders model responses.

10. **[chore(deps-dev): bump @types/node from 20.19.1 to 25.9.2](https://github.com/google-gemini/gemini-cli/pull/27930)** — TypeScript type definitions for Node.js, jumping from Node 20 to 25. Signals potential Node.js engine requirement changes.

## Feature Request Trends

Three dominant feature directions emerge from the issue tracker:

1. **Subagent reliability and observability** — Multiple issues request better visibility into subagent state: why they hang, when they fail silently, and how to configure them. Requests for backgroundable subagents (`Ctrl+B`) and lock recovery for browser sessions indicate productionization pressure.

2. **AST-aware tooling adoption** — A tracked epic (#22745) and its children (#22746, #22747) are investigating whether AST-based file reads, search, and codebase mapping can reduce token waste and improve navigation precision. Suggests the team is considering moving beyond regex-based tooling.

3. **Auto Memory system hardening** — A cluster of issues (#26516, #26522, #26523, #26525) from a single author focuses on making Auto Memory more reliable: skipping low-signal sessions, quarantining invalid patches, and redacting secrets before they reach model context.

## Developer Pain Points

Recurring frustrations from the community (all from maintainer-only issues, indicating internal reporting):

- **Subagent unreliability dominates.** The top-voted bug (#21409, 8 reactions) describes generalist agent hangs. Multiple issues report subagents ignoring `settings.json` overrides (#22267), running without permission (#22093), or masking failures as success (#22323).

- **Terminal UX regressions.** Issues about shell hangs after completion (#25166), flicker on resize (#21924), corruption after external editors (#24935), and stray `\n` escape behavior (#22466) suggest terminal rendering is a persistent pain point.

- **Tool explosion causing API failures.** When users configure many tools (>128), the CLI hits 400 errors (#24246). No automatic tool filtering or scoping exists — the model must handle all tools simultaneously, which it cannot.

- **Workspace pollution.** The model's habit of creating temporary scripts in random directories (#23571) and not using configured skills/sub-agents autonomously (#21968) creates cleanup overhead and reduces trust.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-06-15

## Today's Highlights
A quiet day on the `copilot-cli` repository with no new releases or pull requests in the last 24 hours. However, several triaged issues surfaced around session poisoning from malformed attachments, BYOK model discovery gaps, and Azure DevOps integration requests. The community is still active on two long-running open issues: agent skill execution in wrong folders and duplicate item errors during processing.

## Releases
No new releases in the last 24 hours.

---

## Hot Issues

### 1. Agent skills scripts executed in wrong folder (Issue #956)
**Author:** msundman78 | **👍:** 2 | **Comments:** 6  
A long-standing bug (opened January 2026) where skill scripts referenced via `scripts/myscript.sh` in SKILLS.md execute from the wrong working directory. This contradicts the official agent skills spec. Still active with recent discussion.  
[🔗 github/copilot-cli Issue #956](https://github.com/github/copilot-cli/issues/956)

### 2. Duplicate Item Errors (Issue #3558)
**Author:** psulightning | **👍:** 7 | **Comments:** 4  
A CAPI error (`400 bad_request`) reporting `Duplicate item found with id fc_call_...` during processing. High community interest (7 upvotes). Suggests a session context-memory deduplication bug.  
[🔗 github/copilot-cli Issue #3558](https://github.com/github/copilot-cli/issues/3558)

### 3. Different prompt input box layout in two cmd tabs (Issue #3797)
**Author:** kunalk16 | **👍:** 0 | **Comments:** 1  
A UI inconsistency where the prompt input box renders differently across two terminal tabs in the same window. Newly filed (today).  
[🔗 github/copilot-cli Issue #3797](https://github.com/github/copilot-cli/issues/3797)

### 4. Feature request: opt-in model discovery for BYOK/custom providers (Issue #3795)
**Author:** aosama | **👍:** 0 | **Comments:** 0  
Users of custom providers must manually set `COPILOT_MODEL` or `--model`. The CLI does not query the provider for available models. A discovery endpoint would simplify BYOK workflows.  
[🔗 github/copilot-cli Issue #3795](https://github.com/github/copilot-cli/issues/3795)

### 5. Add Azure DevOps work items to Up next (Issue #3794)
**Author:** OmerMicro | **👍:** 0 | **Comments:** 0  
The global "Up next" panel only surfaces GitHub items, leaving Azure DevOps users with an empty inbox despite the app supporting ADO repos as projects.  
[🔗 github/copilot-cli Issue #3794](https://github.com/github/copilot-cli/issues/3794)

### 6. Malformed attachment poisons session (Issue #3791)
**Author:** jay-tau | **👍:** 0 | **Comments:** 0  
A critical session poisoning bug: attaching a password-protected `.xlsx` causes a CAPI 400, and **all subsequent turns in the same session fail** even without the attachment. No recovery without restarting the session.  
[🔗 github/copilot-cli Issue #3791](https://github.com/github/copilot-cli/issues/3791)

### 7. Unclear error dump (Issue #3793)
**Author:** ja552588 | **👍:** 0 | **Comments:** 0  
Filed with only raw hex addresses and no description. Likely a crash dump or debug output. Needs moderator triage to determine if valid.  
[🔗 github/copilot-cli Issue #3793](https://github.com/github/copilot-cli/issues/3793)

### 8. Spam / invalid issue: "hhhhhhh" (Issue #3796)
**Author:** TAREQ097H | **👍:** 0 | **Comments:** 1  
Already closed as invalid. Low signal — but highlights the need for automated spam filtering in the issue tracker.  
[🔗 github/copilot-cli Issue #3796](https://github.com/github/copilot-cli/issues/3796)

### 9. Duplicate Item Errors (Issue #3558) — *mentioned above*
High community reaction (7 👍) indicates this is blocking multiple users. Likely related to session state management.  
[🔗 github/copilot-cli Issue #3558](https://github.com/github/copilot-cli/issues/3558)

### 10. Agent skills scripts executed in wrong folder (Issue #956) — *mentioned above*
Despite being 5 months old and having community discussion, the working directory issue remains unresolved.  
[🔗 github/copilot-cli Issue #956](https://github.com/github/copilot-cli/issues/956)

---

## Key PR Progress
No pull requests were updated in the last 24 hours. No progress to report.

---

## Feature Request Trends
Trends distilled from the Issues listed above and recent activity:
1. **Custom Provider / BYOK Improvements** — Users want the CLI to auto-discover models from custom providers rather than requiring manual `--model` configuration.
2. **Azure DevOps Integration** — The "Up next" panel should display ADO work items alongside GitHub items, reflecting the multi-platform reality of many development teams.
3. **Agent Skills Spec Compliance** — Script execution working directory behavior must align with the official agent skills specification.
4. **Session Resilience** — Recovery from malformed attachments without killing the entire session is a clear pain point.

---

## Developer Pain Points
1. **Session Poisoning / No Recovery** — A single malformed attachment causes all subsequent turns to fail with the same 400 error (Issue #3791). No graceful recovery mechanism exists.
2. **Duplicate Item Errors Blocking Workflows** — Frequent `Duplicate item found` errors (Issue #3558) with 7 upvotes suggest a systemic issue in context memory deduplication.
3. **Inconsistent UI Rendering** — Prompt input box layout varies across terminal tabs in the same window (Issue #3797), creating confusion.
4. **Missing Model Discovery for BYOK** — Custom provider users must manually set model IDs, adding friction to an otherwise automated workflow.
5. **Cross-Platform Inbox Gaps** — Azure DevOps users find the "Up next" feature useless for their primary workflow.
6. **Skill Script Working Directory** — Long-standing spec deviation (Issue #956) frustrates agent skill developers.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**2026-06-15**

## Today's Highlights
Today's updates reveal a community grappling with both **enhancement momentum** and **service reliability concerns**. A highly-anticipated feature for auto-loading project context files (AGENTS.md, .cursorrules) from Issue #850 was **closed**, suggesting it may have been addressed internally. However, a serious complaint (#2123) about **severe rate limiting** on the paid "Code Plan" persists, with users reporting only ~60 requests per 5-hour window instead of the advertised 300–1200, alongside refund disputes. On the development side, a new PR (#2452) fixes a dangerous bug where `StrReplaceFile` could silently fail on multi-edit hunks.

## Releases
- **No new releases in the last 24 hours.**

## Hot Issues
*(Selected from 3 issues updated in last 24h; top 3 shown due to volume constraints)*

1. **#850 – [CLOSED] Feature Request: Auto-load project context/rules (e.g., AGENTS.md, .cursorrules) at session start**  
   *Author: Al4ric | 👍: 1 | Comments: 3*  
   This feature request, requesting automatic context loading similar to Claude Code's `CLAUDE.md`, has been closed after four months of discussion. The closure may indicate pending implementation or a design decision. Community sentiment was positive, with users wanting seamless onboarding for project-specific conventions.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/850)

2. **#2123 – [OPEN] Bug: 限速，限额严重 (Severe Rate Limiting & Quota Issues)**  
   *Author: littlePoBoy | 👍: 0 | Comments: 2*  
   A critical user complaint about the "Code Plan" subscription. The user reports receiving only ~60 calls per 5-hour window (vs. advertised 300–1200), with frequent rate-limit resets and no clear quota disclosure. The user has cited consumer protection laws and requested a refund, which was denied. This issue touches on **trust and transparency** for paid subscribers.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2123)

3. **#2451 – [OPEN] Bug: System prompt conflicting with my desired workflow**  
   *Author: iaindooley | 👍: 0 | Comments: 0*  
   The user reports that the default system prompt in Kimi Code v0.12.0 (using API key and `k2.7-coding` model) overrides their strict project guidelines. This suggests a need for **more configurable system prompt behavior** or a layered prompt management system.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2451)

## Key PR Progress
*(Selected from 4 PRs updated in last 24h)*

1. **#2452 – [OPEN] fix(tools): fail StrReplaceFile when a multi-edit hunk is unmatched**  
   *Author: Osamaali313*  
   Fixes a dangerous bug where `StrReplaceFile` applied edits with `str.replace` and only errored if the entire result was unchanged. Now fails immediately on unmatched hunks, preventing silent corruption in multi-edit operations.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2452)

2. **#2018 – [CLOSED] feat: add Alt+V paste support for Windows Terminal**  
   *Author: LittleDrinks*  
   Addresses a Windows-specific UX issue where `Ctrl+V` is intercepted by the terminal. `Alt+V` now provides a fallback for media paste, improving Windows parity.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2018)

3. **#2020 – [CLOSED] fix: use per-process log filenames to prevent rotation lock on Windows**  
   *Author: LittleDrinks*  
   Fixes `PermissionError` on Windows when multiple Kimi processes try to rotate the same log file. Now uses `kimi.{pid}.log` naming to eliminate contention.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2020)

4. **#839 – [CLOSED] feat(shell): add configurable shell support for Windows**  
   *Author: HamzaETTH*  
   Adds configurable shell support for Windows users, addressing a long-standing gap in cross-platform shell integration.  
   [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/839)

## Feature Request Trends
- **Auto-loading project context files**: Users want Kimi to automatically read project-specific rules files (AGENTS.md, .cursorrules) at session start, mirroring Claude Code's `CLAUDE.md` behavior. Issue #850 was closed, suggesting possible internal work.
- **Improved rate limiting transparency**: Complaints about unclear quota and aggressive rate limiting on paid plans. Users demand explicit disclosure of limits per subscription tier.
- **Configurable system prompts**: Users working with strict guidelines want more control over the default system prompt to avoid workflow conflicts (see #2451).

## Developer Pain Points
- **Severe rate limiting on paid plans**: The most critical pain point. Users on the "Code Plan" report actual usage (~60 requests/5h) far below advertised ranges (300–1200), leading to refund disputes and loss of trust.
- **Lack of quota transparency**: No clear breakdown of remaining requests per plan, only a vague percentage indicator. Users feel misled when subscribing.
- **Cross-platform inconsistencies**: Windows users face specific issues with paste shortcuts (Ctrl+V intercept, now mitigated by #2018) and log file locking (now mitigated by #2020).
- **Multi-edit w/ silent failure risk**: The bug fixed in #2452 highlights a dangerous pattern where multiple edits could silently fail — a reliability concern for users automating file modifications.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-06-15

## Today's Highlights
v1.17.7 ships today with critical MCP and ACP shell fixes, but users report immediate regressions including terminal freezes and `EditBuffer Destroyed` errors. The DeepSeek V4 Pro pricing adjustment (#28846) remains the most active discussion with 77 comments and 79 upvotes, signaling strong community pressure to pass savings to Go subscribers. A cluster of new features—session rename, file tree tabs, and Linux clipboard—merged or arrived as PRs today, reflecting continued focus on TUI/Desktop UX maturity.

## Releases
**v1.17.7** — Core bugfix release:
- Plugin client requests now reuse the active server instead of defaulting to local port.
- ACP shell tool calls display command and working directory from the start.
- Plugin-provided shell environment variables apply to PTY sessions.
- MCP improvements (details truncated in changelog).

⚠️ **Regressions reported:** Terminal freeze (#32376) and persistent `EditBuffer Destroyed` error (#32348) on upgrade.

---

## Hot Issues (Top 10)

### #28846 — [CLOSED] Adjust Go usage limits after DeepSeek V4 Pro permanent 75% price reduction
**Author:** icocoon | **Comments:** 77 | **👍:** 79  
**Why it matters:** The most upvoted and commented issue this period. DeepSeek slashed API pricing by 75%, and the community demands proportional usage quota increases for Go subscribers. Closed without clear resolution—likely to re-open.  
[GitHub](https://github.com/anomalyco/opencode/issues/28846)

### #13984 — [OPEN] Cannot copy and paste in OpenCode CLI
**Author:** hongyesuifeng | **Comments:** 48 | **👍:** 20  
**Why it matters:** Long-standing (Feb 2026) clipboard issue still unresolved. Affects core terminal UX—users see "copied to clipboard" but paste yields nothing. High engagement suggests widespread pain across platforms.  
[GitHub](https://github.com/anomalyco/opencode/issues/13984)

### #15585 — [CLOSED] "Free usage exceed" on free models
**Author:** Howard-Zhou-77 | **Comments:** 48 | **👍:** 13  
**Why it matters:** Users confused by free-tier limits on free models after extended sessions. Highlights unclear documentation on usage caps. Closed but underlying confusion persists.  
[GitHub](https://github.com/anomalyco/opencode/issues/15585)

### #28567 — [OPEN] Full MCP client capabilities
**Author:** Arcadi4 | **Comments:** 11 | **👍:** 21  
**Why it matters:** OpenCode MCP client lags behind the latest spec (2.0+). Community wants streaming, roots, sampling, and proper transport support. Blocking advanced plugin integrations.  
[GitHub](https://github.com/anomalyco/opencode/issues/28567)

### #32172 — [OPEN] Add GLM-5.2 model support for Z.AI provider
**Author:** phalla-doll | **Comments:** 7 | **👍:** 0  
**Why it matters:** Z.AI released GLM-5.2 reasoning model; users want immediate provider support. Low upvotes but shows demand for latest model integration.  
[GitHub](https://github.com/anomalyco/opencode/issues/32172)

### #28202 — [CLOSED] Plugin async prompts overlap with Web prompt_async
**Author:** ririnto | **Comments:** 6 | **👍:** 4  
**Why it matters:** Session corruption bug where overlapping async prompts create duplicate assistant siblings in Web UI. Fixed, but demonstrates fragility in concurrent prompt handling.  
[GitHub](https://github.com/anomalyco/opencode/issues/28202)

### #26412 — [OPEN] Custom OpenAI provider: "Expected 'function.name' to be a string"
**Author:** mazingerzzz | **Comments:** 6 | **👍:** 0  
**Why it matters:** Blocks all tool calls for vLLM/custom providers. Streaming tool call chunk parsing fails. Affects anyone self-hosting models.  
[GitHub](https://github.com/anomalyco/opencode/issues/26412)

### #32348 — [OPEN] EditBuffer Destroyed consistently after upgrading to 1.17.7
**Author:** maxcroy1 | **Comments:** 3 | **👍:** 0  
**Why it matters:** Critical regression in latest release. Error stack suggests buffer lifecycle mismatch; likely affects all buffer operations.  
[GitHub](https://github.com/anomalyco/opencode/issues/32348)

### #32376 — [OPEN] v1.17.7 terminal completely frozen
**Author:** haisto | **Comments:** 2 | **👍:** 0  
**Why it matters:** Another v1.17.7 regression—terminal unresponsive. Immediate blocker for anyone who upgraded.  
[GitHub](https://github.com/anomalyco/opencode/issues/32376)

### #31778 — [OPEN] MCP server subprocess receives full process.env (API keys leaked)
**Author:** LifetimeVip | **Comments:** 2 | **👍:** 0  
**Why it matters:** Security concern: every local MCP server gets all env vars including API keys. Clear code-level root cause identified.  
[GitHub](https://github.com/anomalyco/opencode/issues/31778)

---

## Key PR Progress (Top 10)

### #32326 — [CLOSED] feat(app): add session file list tab
**Author:** liwanspecial  
**What:** New Files tab in session side panel displaying workspace file tree. Reuses existing file opening flow.  
**Impact:** Directly improves developer workflow by allowing file browsing without leaving the session.  
[GitHub](https://github.com/anomalyco/opencode/pull/32326)

### #32377 — [OPEN] fix(acp): clean up session MCP servers
**Author:** hereswilson  
**What:** MCP servers registered via ACP `mcpServers` were not cleaned up on session close. Now properly torn down.  
**Impact:** Prevents resource leaks and stale server processes in ACP sessions.  
[GitHub](https://github.com/anomalyco/opencode/pull/32377)

### #32373 — [OPEN] feat(opencode): support models.dev reasoning options
**Author:** qwq202  
**What:** Adds `ReasoningVariants` handling for models.dev `reasoning_options`. Generates reasoning variants from provider capabilities.  
**Impact:** Enables nuanced reasoning control (effort levels) for models.dev users.  
[GitHub](https://github.com/anomalyco/opencode/pull/32373)

### #30977 — [OPEN] feat(tui): attach to configured server by default
**Author:** jensenojs  
**What:** New `server.attach` config value to auto-attach TUI to a configured server path instead of spawning a new daemon.  
**Impact:** Solves #17322; enables multi-instance server workflows. 40% of diff is test coverage.  
[GitHub](https://github.com/anomalyco/opencode/pull/30977)

### #32364 — [OPEN] fix: reset terminal modes on TUI shutdown
**Author:** wgu9  
**What:** Ensures `destroyRenderer()` properly resets terminal modes (title, raw mode) during shutdown.  
**Impact:** Fixes #20458; prevents terminal corruption on crash/exit.  
[GitHub](https://github.com/anomalyco/opencode/pull/32364)

### #31867 — [OPEN] feat: improve DeepSeek prompt cache reuse
**Author:** ChangedenCZD  
**What:** Removes current date from system prompt to improve DeepSeek prompt cache hit rate.  
**Impact:** Reduces latency and cost for DeepSeek API users.  
[GitHub](https://github.com/anomalyco/opencode/pull/31867)

### #32245 — [CLOSED] fix(mcp): stop idle OAuth callback server
**Author:** rekram1-node  
**What:** Stops MCP OAuth callback listener when no callbacks remain; releases the port after success/error/timeout.  
**Impact:** Fixes port leak and cross-instance CSRF errors.  
[GitHub](https://github.com/anomalyco/opencode/pull/32245)

### #32302 — [OPEN] fix(opencode): forward parent attachments to subagents
**Author:** 21pounder  
**What:** Fixes attachment handoff for `@mention` subagents in the `task` path.  
**Impact:** Fixes #25553; subagents now correctly inherit parent context attachments.  
[GitHub](https://github.com/anomalyco/opencode/pull/32302)

### #32370 — [OPEN] Linux clipboard selection
**Author:** bornmw  
**What:** Support for Linux PRIMARY clipboard buffer for selection copy.  
**Impact:** Fixes #29963; expected Linux terminal behavior now works correctly.  
[GitHub](https://github.com/anomalyco/opencode/pull/32370)

### #32367 — [OPEN] fix: create worktrees from empty git repos
**Author:** wgu9  
**What:** Handle `git worktree add` failure on repos with no commits.  
**Impact:** Fixes #20910; enables OpenCode worktrees on fresh/empty git repos.  
[GitHub](https://github.com/anomalyco/opencode/pull/32367)

---

## Feature Request Trends

1. **Session Management & UX** — Multiple requests for session rename (#32375), bookmarks (#24017), status flags (#30763), and title display in footer (#32372). Strong desire for better session organization beyond auto-titles.

2. **MCP Ecosystem Expansion** — Full MCP 2.0 client support (#28567), schema warning cleanup (#31002), and environment isolation (#31778). Community wants OpenCode to be a first-class MCP host.

3. **Provider & Model Parity** — GLM-5.2 integration (#32172), xAI/Grok Composer 2.5 model missing (#31475). Users expect rapid support for new model releases.

4. **Remote & Multi-Machine Workflows** — SSH remote directory references (#31901), subagent session directory inheritance (#30355). Growing need for decentralized development setups.

5. **Compaction Reversibility** — #32368 asks for undo capability for session compaction. Users want safety net before irreversible context reduction.

---

## Developer Pain Points

1. **Clipboard Inconsistency** — #13984 remains open since February; copy/paste broken for many users across platforms. New Linux PRIMARY buffer support (#32370, #29967) is overdue but incomplete.

2. **v1.17.7 Regressions** — Terminal freeze (#32376) and `EditBuffer Destroyed` (#32348) are critical blockers. High urgency for hotfix.

3. **MCP Security & Compatibility** — Environment variable leakage (#31778) and non-standard schema formats (#31002) create friction for MCP server developers.

4. **Custom Provider Fragility** — vLLM/OpenAI-compatible provider breaks on streaming tool calls (#26412). Self-hosters face persistent integration issues.

5. **OAuth & Server Lifecycle** — OAuth callback server not cleaned up (#23563), subagent server issues (#30355). Server-mode reliability remains a pain point.

6. **Free Tier Confusion** — #15585 shows users hit invisible usage limits on free models. Documentation and transparency needed around free-tier caps.

---

*Generated from anomalyco/opencode data for 2026-06-15*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-06-15

## Today's Highlights

The Pi ecosystem saw a surge of activity around extension APIs and stability fixes. A major push to decompose the monolithic `generate-models.ts` is underway, prompted by a detailed community contribution (#5702). The team also merged support for `excludeFromContext` on custom messages and introduced a new extension prompt guidelines API, while several concurrency and TUI quirks (SIGTERM handling, CJW alignment) were closed. The `glm-5.2` model was quickly added to the ZAI provider after user demand.

## Releases

No new releases in the last 24 hours.

## Hot Issues

1. **#5103 — Windows bash detector fails when Git Bash is on non-default drive**  
   *18 comments • 0 👍*  
   A long-standing bug where the built-in bash detector only searches `C:\Program Files`, missing Git Bash installations on other drives (e.g., `D:\`). Affects all Windows developers with custom installations. [GitHub](https://github.com/earendil-works/pi/issues/5103)

2. **#5653 — Move off Shrinkwrap: duplicate pi-ai modules on disk**  
   *9 comments • 0 👍*  
   Installing both `pi-ai` and `pi-coding-agent` as direct deps causes two copies of `pi-ai` due to hoisting. The module-level `Map` registry then breaks because each copy is a separate instance. [GitHub](https://github.com/earendil-works/pi/issues/5653)

3. **#5736 — Escape key no longer interrupts interactive tasks**  
   *6 comments • 0 👍*  
   A critical regression: pressing `Escape` / `app.interrupt` during an active run fails to stop the agent, despite being advertised as the cancel key. Co-authored by gpt-5.5. [GitHub](https://github.com/earendil-works/pi/issues/5736)

4. **#5702 — `prompt_cache_retention` sent to providers that reject it (OpenCode/Zen 400)**  
   *6 comments • 0 👍*  
   A deep dive into a model-registry build-system issue. The small bug (sending unsupported `cache_control` TTL to Zen/OpenCode) leads to a larger maintainability concern in `generate-models.ts`. The author contributed a thorough PR (#5743) alongside this report. [GitHub](https://github.com/earendil-works/pi/issues/5702)

5. **#5654 — Add `excludeFromContext` to custom messages via `sendMessage()`**  
   *6 comments • 1 👍*  
   Mirrors the existing bash-execution `!!` flag so that custom messages (e.g., `/status` output) can be rendered to the user without bloating the LLM context. PR already merged by mitsuhiko. [GitHub](https://github.com/earendil-works/pi/issues/5654)

6. **#5687 — `pi list` and `pi update` hang forever when an extension runs an MCP server**  
   *6 comments • 0 👍*  
   Package subcommands never exit if any installed extension starts a long-lived MCP server. The command prints output and then hangs until Ctrl-C. [GitHub](https://github.com/earendil-works/pi/issues/5687)

7. **#5706 — Task hangs at “waiting for summary approval” with local LLM backends**  
   *5 comments • 0 👍*  
   Using a local OpenAI-compatible LLM (e.g., Ollama) causes Pi to freeze at the summary approval step. Cloud providers (DeepSeek, OpenAI) work fine. [GitHub](https://github.com/earendil-works/pi/issues/5706)

8. **#5671 — `~/.pi` and `cwd/.pi` overlap**  
   *5 comments • 3 👍*  
   The `.pi` directory is used for both global settings and project-level config, which collide in `$HOME`. The discussion (from mitsuhiko) asks whether this should be renamed/restructured. Community strongly supportive. [GitHub](https://github.com/earendil-works/pi/issues/5671)

9. **#5303 — Bash tool truncates output when child holds stdout past exit**  
   *3 comments • 0 👍*  
   Every `git commit` with a pre-commit hook that runs lint-staged gets its output truncated. The `waitForChildProcess` uses a 100ms destroy window that misses final output. [GitHub](https://github.com/earendil-works/pi/issues/5303)

10. **#5724 — SIGTERM’d Pi doesn’t reset terminal**  
    *2 comments • 0 👍*  
    Killing Pi with SIGTERM leaves the terminal in raw mode with Kitty keyboard protocol enabled, making the shell unusable. [GitHub](https://github.com/earendil-works/pi/issues/5724)

## Key PR Progress

1. **#5743 — Refactor `generate-models.ts` into data-driven generator**  
   *(CLOSED) — devasur*  
   A community-led decomposition of the huge `generate-models.ts` file into a data-driven approach, following the maintainability concerns raised in #5702. [GitHub](https://github.com/earendil-works/pi/pull/5743)

2. **#5738 — Fix Anthropic 1h cache write pricing**  
   *(OPEN) — theBucky*  
   Corrects undercounting of 1h cache writes by reading `ephemeral_1h_input_tokens` and charging 2x base input instead of the 5m rate. [GitHub](https://github.com/earendil-works/pi/pull/5738)

3. **#5678 — Add `excludeFromContext` for custom messages**  
   *(OPEN) — mitsuhiko*  
   Implements the `excludeFromContext` flag across agent harness and extension APIs, with proper handling in compaction and branch summarization. [GitHub](https://github.com/earendil-works/pi/pull/5678)

4. **#5735 — Defer extension reload requests safely**  
   *(OPEN) — mitsuhiko*  
   Makes `ctx.reload()` safe from all extension contexts via a deferral mechanism, preventing mid-execution reloads. [GitHub](https://github.com/earendil-works/pi/pull/5735)

5. **#5732 — `allowCommands` option in `sendUserMessage`**  
   *(CLOSED) — max-elia*  
   Enables extensions to programmatically trigger slash commands (e.g., session reset) by enabling prompt template expansion in `sendUserMessage`. [GitHub](https://github.com/earendil-works/pi/pull/5732)

6. **#5731 — Tool instrumentation for execution profiling**  
   *(CLOSED) — RHarshith*  
   Adds profiling hooks for tool execution in the coding agent. [GitHub](https://github.com/earendil-works/pi/pull/5731)

7. **#5714 — xAI Grok account OAuth login**  
   *(CLOSED) — hyiiiii*  
   Adds built-in xAI Grok OAuth provider with device-code login, refresh tokens, and subscription models. [GitHub](https://github.com/earendil-works/pi/pull/5714)

8. **#5711 — Extension prompt guideline API**  
   *(OPEN) — xl0*  
   Adds `pi.setPromptGuidelines()` to the ExtensionAPI, allowing extensions to inject global instructions into the system prompt. [GitHub](https://github.com/earendil-works/pi/pull/5711)

9. **#5385 — First-run terminal theme detection**  
   *(CLOSED) — vegarsti*  
   Queries the terminal via OSC to detect light/dark theme on first launch, persisting it to settings. [GitHub](https://github.com/earendil-works/pi/pull/5385)

10. **#2331 — Vim-like modal editor extension**  
    *(CLOSED) — Nokodoko*  
    A fully-featured vim modal editor extension (Normal, Insert, Visual, Command-line modes) with motions, operators, counts, and ex commands. [GitHub](https://github.com/earendil-works/pi/pull/2331)

## Feature Request Trends

- **Multi-session TUI**: Users want concurrent agent sessions with TUI switching (#5700), not the current tear-down/switch model.
- **Extension-level prompt guidelines**: A clean API for extensions to inject global system instructions (#5710, PR #5711).
- **Provider-specific config in `auth.json`**: Beyond API keys, some providers (Cloudflare, xAI) require account IDs, gateway IDs, etc. Users want those configurable in `auth.json` (#5728).
- **Model-specific compaction**: Current compaction options are global; small local models waste tokens on reserve/keep sizes that are too large for them (#5722).
- **Native image generation in interactive mode**: Extend multimodality to creative/visual flows (#4095).
- **Access to raw provider responses in hooks**: `after_provider_response` should expose the full raw payload, not just status/headers (#5730).

## Developer Pain Points

- **Terminal state corruption on crash/kill**: SIGTERM (#5724) and uncaught background process exits (#5208) leave terminals in broken raw mode. This is a high-severity UX issue.
- **Windows bash detection fragility**: Non-standard Git Bash installations (`D:\` drives, PATH-based) are missed entirely (#5103).
- **Output truncation in bash tool**: The 100ms destroy window in `waitForChildProcess` silently loses end-of-command output, especially with pre-commit hooks (#5303).
- **Local LLM backend freezing**: Tasks hang at “waiting for summary approval” with local backends (#5706), making local-first workflows unreliable.
- **TUI rendering edge cases**: CJK characters cause split vertical borders in overlays (#5297); streaming output scrolls to top (#5576); modals block transcript scrolling (#5745).
- **Duplicate module instances**: The shrinkwrap/hoisting issue (#5653) breaks the module-level provider registry when two packages bring different copies of `pi-ai`.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-06-15

## Today's Highlights

The repository is seeing intense activity around **security and reliability** — several critical bugs were reported involving tool-call duplication, permission-contract bypass, and antivirus false positives on the VSIX package. Meanwhile, the community is vocal about **OAuth free tier policy changes** (#3203, 135 comments) and the **unavailability of paid Pro plans** (#3272). On the PR front, a major effort to **support session resume without synthetic "continue" messages** (#5030) and a **per-task token/time detail UI** (#5118) are advancing.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **[#3203 — Qwen OAuth Free Tier Policy Adjustment](https://github.com/QwenLM/qwen-code/issues/3203)** (135 comments, Open)
   **Why it matters:** Proposes reducing daily free requests from 1,000 to 100 and phasing out the free tier entirely by June 20. This is the most commented issue in the repo, signaling strong community backlash or concern about access changes.

2. **[#3267 — Requests limits overview](https://github.com/QwenLM/qwen-code/issues/3267)** (7 comments, Closed)
   **Why it matters:** A user on the free plan hit the 1,000/day limit without completing a single task, suggesting a possible counting bug (e.g., tokenization errors inflating request counts). The issue was closed but the underlying concern remains live.

3. **[#5055 — Trojan:JS/ShaiWorm.DBA!MTB detection in VSIX](https://github.com/QwenLM/qwen-code/issues/5055)** (5 comments, Open)
   **Why it matters:** A Windows user reports that Windows Defender flags the VSIX installer as a trojan. This is a high-priority (P1) security concern that could block enterprise adoption.

4. **[#5102 — Provider-requested side effect executed despite permission-contract probe](https://github.com/QwenLM/qwen-code/issues/5102)** (4 comments, Open)
   **Why it matters:** A critical security bug where a provider-requested shell command writes a side-effect file even though the permission contract should have prevented it. This undermines the sandbox guarantee.

5. **[#4218 — MCP Server "filesystem" shows connected but tools unavailable](https://github.com/QwenLM/qwen-code/issues/4218)** (5 comments, Open)
   **Why it matters:** Windows users cannot use the filesystem MCP server despite UI showing successful connection — the model never receives tool definitions. A persistent integration gap.

6. **[#5101 — Repeated large tool results carried through provider history](https://github.com/QwenLM/qwen-code/issues/5101)** (2 comments, Open)
   **Why it matters:** A performance/context-window bug where large tool outputs are repeatedly sent back, causing request context to balloon. Described as a P1 bug on the context-performance roadmap.

7. **[#4727 — Dual Output mode TUI unresponsive](https://github.com/QwenLM/qwen-code/issues/4727)** (5 comments, Closed)
   **Why it matters:** Using FIFO-based dual-output mode (`--json-file`, `--input-file`) results in a completely unresponsive TUI on version 0.17.0 — a blocking issue for automation pipelines.

8. **[#5119 — No way to allow sudo commands](https://github.com/QwenLM/qwen-code/issues/5119)** (1 comment, Open)
   **Why it matters:** When an agent needs to run a `sudo` command, it fails ungracefully, forcing users to manually copy-paste. A straightforward UX gap for privilege escalation workflows.

9. **[#3979 — Ghostty terminal flickering after plan mode response](https://github.com/QwenLM/qwen-code/issues/3979)** (2 comments, Open)
   **Why it matters:** A terminal-specific rendering bug on macOS Ghostty that causes continuous flickering after plan mode completes — annoying but platform-specific.

10. **[#5099 — Duplicate tool-result history for reused tool-call ID](https://github.com/QwenLM/qwen-code/issues/5099)** (3 comments, Closed)
    **Why it matters:** When a provider reuses a tool-call ID across turns, Qwen Code sends duplicate results, which can corrupt provider state or trigger schema errors — a correctness bug in tool-result handling.

## Key PR Progress

1. **[#5118 — feat(web-shell): per-task token & time detail on completed todos](https://github.com/QwenLM/qwen-code/pull/5118)** (Open)
   **What:** Expanding a completed task in the web-shell now shows start/end times, elapsed duration, token counts (input/output/cached), API time, and cost. A major usability improvement for cost-conscious developers.

2. **[#5030 — feat(core,cli,sdk): resume an interrupted turn without synthetic "continue"](https://github.com/QwenLM/qwen-code/pull/5030)** (Open)
   **What:** Adds a first-class way to resume an unfinished assistant turn after a crash or interruption — no more fake `"continue"` messages in the transcript. Closes the gap raised in issue #4679.

3. **[#5122 — feat(computer-use): configurable screenshot max dimension](https://github.com/QwenLM/qwen-code/pull/5122)** (Open)
   **What:** Adds a user knob (setting + env var) for the screenshot longest-edge cap in the computer-use driver, following the migration from the old `ocu` backend.

4. **[#5120 — fix(core): skip auto-title generation when history has no user message](https://github.com/QwenLM/qwen-code/pull/5120)** (Open)
   **What:** Guards against generating session titles from empty or system-only histories — avoids wasting tokens on title generation when there's no real user input yet.

5. **[#4564 — feat(stats): expose token usage for cost visibility](https://github.com/QwenLM/qwen-code/pull/4564)** (Open)
   **What:** Persists token-usage accounting and extends `/stats` with daily/monthly breakdowns, model/auth-type filters, and CSV/JSON export. Directly addresses the community's demand for cost transparency.

6. **[#5073 — fix: warn on oversized context instructions](https://github.com/QwenLM/qwen-code/pull/5073)** (Open)
   **What:** Warns at startup if the always-loaded QWEN.md / context instructions exceed 15% of the model's context window. A proactive guard against silent context waste.

7. **[#4850 — feat(extensions): interactive multi-tab extensions manager](https://github.com/QwenLM/qwen-code/pull/4850)** (Open)
   **What:** Turns `/extensions` into a three-tab manager (Installed, Discover, Sources) covering the full lifecycle of finding, installing, configuring, and removing extensions and MCP servers.

8. **[#5094 — feat(core): Workflow P4a — meta extraction](https://github.com/QwenLM/qwen-code/pull/5094)** (Open)
   **What:** Implements the first half of phase P4 of the Dynamic Workflows port — extracting and stripping metadata from run outcomes. Builds on three previously merged phases.

9. **[#4943 — feat(cli): add --safe-mode flag for troubleshooting](https://github.com/QwenLM/qwen-code/pull/4943)** (Open)
   **What:** Adds a `--safe-mode` flag that disables all customizations (context files, hooks, extensions, skills, MCP servers, subagents) to provide a clean baseline for debugging issues.

10. **[#5123 — fix(web-shell): remove redundant sanitizeSvg, fix mermaid render failure](https://github.com/QwenLM/qwen-code/pull/5123)** (Open)
    **What:** Removes a custom SVG sanitizer that was breaking mermaid rendering — mermaid already uses DOMPurify internally. A targeted fix for diagram rendering in the web shell.

## Feature Request Trends

- **Token & cost transparency** is the dominant theme — users want visible token usage per session/task (#4564, #5101, #5118) and cost breakdowns to manage API spending.
- **Rule/instruction systems** are increasingly requested — users want persistent rules (like Claude Code's `.rules` or Copilot's instructions) that apply across sessions (#4723), plus proper `sudo` command support (#5119).
- **Context window management** continues to be a high-demand area: warnings when context instructions are too large (#5073), better handling of large tool outputs (#5101), and estimated token counts that include model responses (#4349).
- **MCP server reliability** on Windows is a recurring pain point — servers show as connected but don't pass tools to the model (#4218).
- **UI polish requests** are accumulating: statusline wrapping (#5064), showing the active model in the footer (#5104), and timestamp prefixes on assistant turns (#5001).

## Developer Pain Points

1. **Free tier instability & Pro plan unavailability** — Users report hitting daily limits without completing tasks (#3267), while the Pro plan is perpetually "sold out" (#3272), creating a dead zone for willing paying customers.

2. **Security & trust issues** — Antivirus flagging the VSIX as a trojan (#5055), permission-contract bypass (#5102), and side-effect execution during probe phases undermine confidence in the platform's security model.

3. **Automatic looping & truncation** — The agent enters infinite loops when it can't fix a bug (#3184) and suffers from mid-task truncation that corrupts session state (#4964). Multiple issues report that the model needs to be manually stopped or killed.

4. **Tool-result correctness** — Repeated identical tool calls (#5015), duplicate results for reused tool-call IDs (#5099), and large results flooding provider history (#5101) point to fundamental bookkeeping bugs in the tool execution pipeline.

5. **CI/CD false successes** — The PR review job reports green even when it fails mid-task due to API errors, posting no actual comments (#5052). This erodes trust in automated CI checks for the project itself.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-06-15

## Today's Highlights
The project has fully rebranded from `deepseek-tui` to **CodeWhale**, with v0.8.60 marking the final release under the legacy name. A massive v0.8.61 draft PR is up for review, bundling 28 commits that include a community harvest, a fix for the infamous Windows TUI freeze, and the foundation layer for the upcoming WhaleFlow orchestration system. The community is actively contributing features like voice input, persistent permission rules, and Hugging Face MCP helpers.

## Releases
**v0.8.60** — Final release under the legacy `deepseek-tui` name. All assets, commands, and packages are now published as **CodeWhale**. Users on v0.8.x `deepseek`/`deepseek-tui` should follow `docs/REBRAND.md` for migration instructions. The deprecated npm package `deepseek-tui` will receive no further releases.

## Hot Issues
1. **[#2487 — Turn stalled error in YOLO mode](https://github.com/Hmbown/CodeWhale/issues/2487)** *(12 comments)* — Frequent freeze with "Turn stalled — no completion signal received" in YOLO mode. `continue` command fails to resume. This is the most commented issue, reflecting a critical reliability blocker for agent-heavy users.

2. **[#1186 — Typed persistent permission rules](https://github.com/Hmbown/CodeWhale/issues/1186)** *(8 comments)* — Request to extend execpolicy with rules scoped by tool name, command prefix, and workspace path. Community strongly supports this for safer sub-agent delegation.

3. **[#3147 — MSBuild FileTracker fails on Windows](https://github.com/Hmbown/CodeWhale/issues/3147)** *(7 comments)* — `cmake --build` is completely broken in CodeWhale's managed PowerShell on Windows due to MSBuild FileTracker initialization failure. Blocking C++ developers from using the tool.

4. **[#1812 — TUI freeze on Windows (crossterm poll)](https://github.com/Hmbown/CodeWhale/issues/1812)** *(5 comments)* — Intermittent UI freeze on Windows 11 with process staying alive. Two confirmed events with logs and thread-state analysis. A v0.8.61 fix is in progress.

5. **[#2475 — YOLO mode + Burp MCP interruption](https://github.com/Hmbown/CodeWhale/issues/2475)** *(4 comments)* — When connecting to Burp via MCP in YOLO mode, tasks get interrupted and cannot resume. Security testing workflows are blocked.

6. **[#1806 — Sub-agent 120s API timeout](https://github.com/Hmbown/CodeWhale/issues/1806)** *(4 comments)* — All parallel sub-agents fail with identical 120s timeout when processing multi-file tasks. The advertised parallel offload feature is nearly unusable on Windows.

7. **[#2629 — SiliconFlow / Tencent TokenHub 401 error](https://github.com/Hmbown/CodeWhale/issues/2629)** *(3 comments)* — CodeWhale cannot authenticate with these Chinese OpenAI-compatible providers, always returning `401 invalid api key`. Affecting users in the China market.

8. **[#3102 — First-class clarification questions for agents](https://github.com/Hmbown/CodeWhale/issues/3102)** *(3 comments)* — Feature request by the maintainer for agents to ask clarifying questions through modal UI instead of plain chat messages. Would significantly improve agent UX.

9. **[#2574 — Provider fallback chain](https://github.com/Hmbown/CodeWhale/issues/2574)** *(3 comments)* — Request for automatic fallback when a provider returns 401/429/5xx errors. Currently requires manual `/provider` switch, breaking long-running tasks.

10. **[#1067 — glibc 2.39 dependency on Ubuntu 22.04](https://github.com/Hmbown/CodeWhale/issues/1067)** *(3 comments)* — Binary requires glibc 2.39, breaking on Ubuntu 22.04 (glibc 2.35). Duplicate issue #3207 confirms the same pain. Users want multi-glibc builds.

## Key PR Progress
1. **[#3233 — Persist ask-only permission rules atomically](https://github.com/Hmbown/CodeWhale/pull/3233)** *(new, open)* — Extracts the persistence foundation for typed permission rules. Adds `ConfigStore::append_ask_rules` with atomic writes. Foundation for the broader persistent-permissions effort.

2. **[#3197 — Rename DeepSeek blue to whale accent](https://github.com/Hmbown/CodeWhale/pull/3197)** *(closed)* — Adds `palette::WHALE_ACCENT_PRIMARY` as the semantic color token, keeping `DEEPSEEK_BLUE` as a deprecated alias. Clean rebranding completion.

3. **[#3051 — Voice input via `/voice` command](https://github.com/Hmbown/CodeWhale/pull/3051)** *(closed)* — Adds speech-to-text support inspired by MiMo Code. Three new slash commands for recording, transcription, and composer insertion, reusing the existing provider API.

4. **[#3225 — v0.8.61: community harvest + freeze fix + WhaleFlow foundation](https://github.com/Hmbown/CodeWhale/pull/3225)** *(open, draft)* — The big one: 28 commits assembling the v0.8.61 release. Fixes the Windows TUI freeze, harvests community contributions, and lays groundwork for WhaleFlow orchestration.

5. **[#2811 — VS Code extension scaffold](https://github.com/Hmbown/CodeWhale/pull/2811)** *(closed)* — Adds official VS Code extension with commands to open CodeWhale, start HTTP server, and check runtime status. Activity view, status bar, and VSIX packaging included.

6. **[#2771 — LLM-guided AGENTS.md init](https://github.com/Hmbown/CodeWhale/pull/2771)** *(closed)* — The `/init` command now gathers project context and delegates AGENTS.md generation to the LLM instead of writing a static template. Smarter project onboarding.

7. **[#2802 — Hugging Face MCP helpers](https://github.com/Hmbown/CodeWhale/pull/2802)** *(closed)* — Adds `/hf mcp status`, `/hf mcp setup`, and `/huggingface` alias. Helps users configure Hugging Face MCP integration without manual config editing.

8. **[#2779 — Dormant provider fallback chain config](https://github.com/Hmbown/CodeWhale/pull/2779)** *(closed)* — Implements the config/data-model layer for provider fallback. Adds `fallback_providers = [...]` parsing with dormant `ProviderChain` helper. Runtime switching not yet active.

9. **[#2797 — Sofya web search provider](https://github.com/Hmbown/CodeWhale/pull/2797)** *(closed)* — Adds a new web search backend via Sofya. Community contribution from @yusufgurdogan, expanding search capabilities beyond existing providers.

10. **[#2801 — Project mode prompts per request](https://github.com/Hmbown/CodeWhale/pull/2801)** *(closed)* — Keeps system prompt mode-agnostic; projects mode, approval policy, and tool taxonomy as request-time metadata. Preserves history/prefix cache efficiency.

## Feature Request Trends
- **Persistent permission rules** (multiple issues, #1186, #3233) — Users want granular, persistent permission rules for sub-agents and tool execution with `allow`/`deny`/`ask` decisions per workspace.
- **Provider fallback chains** (#2574, #2779) — Automatic failover between providers when API errors or rate limits occur, without manual intervention.
- **Agent communication improvements** (#3102, #3230) — Agents need first-class clarification questions, synthesis/reduce passes for swarm outputs, and shared fleet ledgers for multi-agent coordination.
- **Voice input** (#3051) — Speech-to-text as a first-class input method, inspired by competing tools like MiMo Code.
- **WhaleFlow orchestration** (#3229, #3230) — A full orchestration system for heterogeneous-model workers with shared task lists and synthesis passes.

## Developer Pain Points
- **Windows instability** (#1812, #3147, #1679) — TUI freezes, MSBuild failures, and 45-second SSE timeouts on Windows remain the top blockers. Windows is the most problematic platform despite high demand.
- **Sub-agent reliability** (#1806, #2487, #2475) — Sub-agents consistently fail with 120s timeouts, stall in YOLO mode, and lose session state on interruption. The core agent orchestration promise is undermined by these failures.
- **GLIBC version dependency** (#1067, #3207) — Requiring glibc 2.39 excludes all Ubuntu 22.04 users and older LTS distributions. Community wants multi-target binaries or static linking.
- **Chinese provider incompatibility** (#2629) — SiliconFlow and Tencent TokenHub, major Chinese OpenAI-compatible providers, return 401 errors. China-market adoption is blocked.
- **Update system fragility** (#2924, #3232) — npm updates fail silently, the native updater breaks behind proxies, and rebranding from `deepseek-tui` to `codewhale` caused PATH confusion for `cargo install` users.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*