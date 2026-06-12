# AI CLI Tools Community Digest 2026-06-12

> Generated: 2026-06-12 01:24 UTC | Tools covered: 9

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

# AI CLI Developer Tools: Cross-Tool Comparison Report
**Date: 2026-06-12**

## 1. Ecosystem Overview

The AI CLI developer tools ecosystem is experiencing rapid maturation, with six major tools now serving distinct developer workflows. Claude Code leads in community size and feature depth, while OpenAI Codex is executing a significant architectural overhaul of its agent runtime. Gemini CLI is shipping heavy bug fixes at pace, and Copilot CLI shows concerning maintenance stagnation despite high issue volume. Newer entrants—Qwen Code, OpenCode, Pi, and CodeWhale (formerly DeepSeek TUI)—are iterating aggressively on core reliability and multi-agent architectures. A unifying theme across all tools is the tension between autonomous agent power and user control: runaway costs, session lifecycle management, and permission security dominate community discourse.

## 2. Activity Comparison

| Tool | Daily Issues (New/Updated) | Daily PRs (Open/Merged) | Release Status | Notable Metrics |
|------|---------------------------|------------------------|----------------|-----------------|
| **Claude Code** | ~10 high-engagement | 10 significant | v2.1.174 (2 patches today) | 125 upvotes on top issue (#13354) |
| **OpenAI Codex** | ~10 active | 10 significant (4-PR stack) | v0.140.0-alpha (.8--.11, 4 alphas) | 67 👍 on top feature request (#12115) |
| **Gemini CLI** | ~10 tracked (P1/P2) | 10 active | No new release (3 P1 fixes landing) | 8 👍 on agent hangs (#21409) |
| **Copilot CLI** | ~10 urgent regressions | 1 (non-functional) | v1.0.61 (recent, regressions reported) | 75 👍 on 6-month-old #53 |
| **Kimi CLI** | 0 updated | 1 closed (#2170) | None | `/skin` YAML customization merged |
| **OpenCode** | ~10 active | 10 significant | None today (v1.15.12 regressions) | 71 👍 on `/goal` sessions (#27167) |
| **Pi** | ~30 updated | 16 updated | v0.79.1 | 54 comments on Codex hang (#4945) |
| **Qwen Code** | 17 tracked | 50 active | v0.18.0-preview.2 | P1 regression in `/stats` (#4994) |
| **CodeWhale** (DeepSeek TUI) | ~10 roadmap items | ~10 active | v0.8.58 (rebrand release) | Rebranding from `deepseek-tui` |

## 3. Shared Feature Directions

The following requirements appear across multiple tool communities, indicating industry-wide developer needs:

| Shared Requirement | Tools Demanding | Specific Needs |
|-------------------|----------------|----------------|
| **Session lifecycle automation** | Claude Code, OpenCode, Copilot CLI | Auto-continue after rate limits, auto-compact at 100% context, unattended overnight workflows |
| **Multi-session orchestration** | Claude Code, Gemini CLI, OpenCode | Inter-session communication, parallel agent coordination, shared context across sessions |
| **Agent cost control & visibility** | Claude Code, Qwen Code, CodeWhale | Per-session cost tracking, limits on parallel agent fan-out, spend budgets |
| **Local/self-hosted LLM support** | Pi, Kimi CLI, Qwen Code | Ollama/llama.cpp integration, offline fallback, custom provider configuration |
| **Sandbox/security confinement** | Copilot CLI, Claude Code, CodeWhale | Workspace-root filesystem restriction, persistent permission rules, sub-agent security policies |
| **Accessibility & remote control** | Claude Code, Copilot CLI | Screen reader support, MCP permission surfacing in web UI, SSH-compatible clipboard |
| **AGENTS.md / skill hierarchies** | OpenAI Codex, Claude Code, Pi | Recursive loading of project-specific agent instructions in subdirectories |
| **Headless/CI/CD compatibility** | Kimi CLI, Pi, Qwen Code, Claude Code | Non-TTY operation, deterministic return codes, pipe-friendly output |
| **Model routing and discovery** | OpenCode, Gemini CLI, Pi | Auto-discovery of available models, GUI for adding custom providers, model locking per session |
| **Internationalization** | CodeWhale (DeepSeek TUI), Qwen Code | Non-English reasoning chains, localized UI, multi-language documentation |

## 4. Differentiation Analysis

### Feature Focus & Target Users

| Tool | Primary Focus | Target User | Key Differentiator |
|------|--------------|-------------|-------------------|
| **Claude Code** | Enterprise-grade agent workflows, deep MCP ecosystem | Professional developers, teams | Richest plugin system, most mature agent orchestration, largest community |
| **OpenAI Codex** | V8 code execution, multi-agent architecture | Full-stack developers, heavy code-modification workflows | Code-mode (V8) sandbox, fast iteration on agent runtime (4 alphas/day) |
| **Gemini CLI** | Google Cloud integration, Wayland/Linux support | GCP-native developers, Linux users | P1 fix velocity, terminal resize stability, Google model ecosystem |
| **Copilot CLI** | GitHub ecosystem integration | GitHub-centric developers, enterprises | Tightest GitHub integration (PRs, issues, worktrees), most stable UX regressions |
| **Kimi CLI** | Minimalist TUI, Hermes ecosystem | Developers wanting simple terminal chat | Color skin customization via YAML, lightweight dependency footprint |
| **OpenCode** | ACP (Agent Communication Protocol), plugin extensibility | Plugin developers, multi-agent orchestrators | `/goal` session management, web UI companion, LAN model discovery |
| **Pi** | Provider flexibility, extensible agent platform | Multi-provider users, CI/automation pipelines | Widest provider support (9+), clipboard-first design, Pi extension ecosystem |
| **Qwen Code** | Open-weight models (Qwen family), ACP/IDE integration | LLM researchers, Chinese-language developers | Deep Qwen model integration, `/stats` dashboard, ACP skills exposure |
| **CodeWhale** (DeepSeek TUI) | Sub-agent architecture, localized reasoning | Advanced TUI users, DeepSeek model advocates | Rebrand to CodeWhale, sub-agent launch gates, WhaleFlow workflows |

### Technical Approach Differences

- **Architecture**: OpenAI Codex is isolating V8 execution into a separate host process to prevent session crashes. Claude Code uses a monolithic approach with hooks for extensibility. Pi and CodeWhale favor modular, embeddable designs.
- **Agent Model**: Claude Code and CodeWhale emphasize sub-agent fan-out with lifecycle management. OpenAI Codex uses MultiAgentV2 with encrypted spawn protocols. Gemini CLI centralizes agent delegation through a generalist orchestrator.
- **Configuration**: Claude Code and Copilot CLI use JSON/YAML config files. Qwen Code uses OpenCode-compatible `opencode.json`. Kimi CLI uses YAML skins via `~/.kimi/skins/`. CodeWhale uses `config.toml`.
- **Security Model**: Claude Code has the most granular permission system (hooks, MCP prompts). CodeWhale is building typed persistent permission rules. Copilot CLI has a Content Exclusion Service that fails closed after token refresh.

## 5. Community Momentum & Maturity

### High Momentum (Rapid Iteration)

- **OpenAI Codex** — Publishing 4 alpha releases daily; major architectural refactors (V8 isolation) in progress. Community engagement is high around session persistence (#20741, 37 comments) and AGENTS.md hierarchies (#12115, 67 👍).
- **Qwen Code** — 50 active PRs, aggressive bug fixing with automated CI triage (#4989). Growing feature surface: multi-tab extension manager, cross-session `/rewind`, sub-agent permission bubbling.
- **Pi** — 30 issues and 16 PRs updated in 24 hours. Expanding provider ecosystem (Bedrock Mantle, Vertex, Gemini 3.5 Flash). Non-TTY hangs and Windows compatibility are active fix areas.

### Moderate Momentum (Stable Iteration)

- **Claude Code** — Large community (125+ upvotes on top issues) but slower release cadence (2 patches today). Enterprise focus with controlled feature expansion. Heavy attention on cost control and session management.
- **Gemini CLI** — Shipping 3 P1 fixes today (terminal resize, MCP MIME, shell hang). Stable but smaller community. Focused on Google Cloud and Linux/terminal compatibility.
- **CodeWhale (DeepSeek TUI)** — Active rebranding from `deepseek-tui` to CodeWhale. Strong sub-agent roadmap (#3098). Community is smaller but engaged on i18n, cache reliability, and Windows stability.

### Low Momentum (Maintenance Concern)

- **Copilot CLI** — Only 1 non-functional PR in 24 hours. High-severity regressions (terminal rendering corruption, content exclusion service fail-closed) with no visible fixes. 6-month-old issue #53 (75 👍) remains unresolved. Community frustration is public, with users forking the tool.
- **Kimi CLI** — Zero issue updates today. Single PR (#2170) merged. Appears to be in maintenance mode with no active bug fixes or releases. Community requests (custom provider support, offline mode, tab completion) remain unaddressed.

## 6. Trend Signals

### For Technical Decision-Makers

1. **Multi-agent orchestration is the next battleground.** Every major tool is investing in sub-agent architectures (Claude Code's parallel agents, OpenAI Codex's MultiAgentV2, CodeWhale's fanout gates, Qwen Code's background agents). Tools that manage agent lifecycle, cost, and observability across parallel execution will win enterprise adoption.

2. **Session persistence is table stakes, not differentiation.** Data loss on updates (OpenAI Codex #20741, Claude Code's auto-compact failures) is the #1 community frustration. Tools that make sessions survive upgrades, crashes, and platform transitions will earn loyalty.

3. **Enterprise security requirements are accelerating.** Users demand workspace-scoped sandboxing (Copilot CLI #892), persistent permission rules (CodeWhale #1186), and token-authenticated MCP registries (Copilot CLI #3772). The Content Exclusion Service fail-closed bug (#3757) is a red flag for security-conscious adoption.

4. **Provider diversity is both demanded and painful.** Users want to use their preferred models (local Ollama, Bedrock Mantle, Vertex, custom endpoints) but configuration is brittle. Pi's provider expansion and Qwen Code's custom-provider UX gaps (#3384) highlight the tension between flexibility and usability.

### For Developers Choosing a Tool

- **Claude Code** — Best for enterprise teams needing the richest ecosystem, but be prepared for cost control challenges and session management friction.
- **OpenAI Codex** — Best for developers who want cutting-edge agent runtime stability and code execution, especially with OpenAI models. Alpha cadence means instability.
- **Gemini CLI** — Best for Google Cloud-native developers who need reliable Linux/GNOME terminal behavior. Smaller community, but fast bug-fix turnaround.
- **Copilot CLI** — Best for GitHub-centric workflows, but current maintenance stagnation and critical regressions make it a risky choice for production use.
- **Qwen Code** — Best for LLM researchers and Chinese-language developers working with Qwen models. Rapidly maturing but still has critical regressions.
- **Pi** — Best for multi-provider users and CI pipelines who need maximum flexibility. Active issue resolution, but hang bugs on Windows and non-TTY remain.
- **CodeWhale** — Best for power users who want advanced sub-agent control and localization. Rebranding may cause temporary confusion.

### Industry Signal

The AI CLI tool landscape is consolidating around three core requirements: **autonomous agent safety** (cost limits, sandboxing, permission systems), **multi-session orchestration** (parallel agents, cross-session state sharing, background execution), and **provider independence** (local models, cloud fallback, seamless routing). Tools that address all three—while maintaining session persistence and platform compatibility—will dominate the next 12 months.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-06-12** | Source: github.com/anthropics/skills

---

## 1. Top Skills Ranking

The following Skills received the highest community attention via PR discussion:

| # | Skill | Author | Description | Status | Discussion Highlights |
|---|-------|--------|-------------|--------|----------------------|
| 1 | **frontend-design** (PR #1046, #210) | ALMMECHANICAL, justinwetch | Multiple new skill definitions plus a major revision improving clarity and actionable instructions for Claude. | **Open** | PR #210 received extensive commentary on making instructions executable within a single conversation. PR #1046 expands with `ai-experience-consultant` and `automation-workflows-builder`. |
| 2 | **document-typography** (PR #514) | PGTBoos | Typographic quality control preventing orphan words, widow paragraphs, and numbering misalignment in AI-generated documents. | **Open** | Strong support — noted that "every document Claude generates needs this." Community resonated with the universal applicability. |
| 3 | **odt** (PR #486) | GitHubNewbie0 | OpenDocument Text creation, template filling, and ODT-to-HTML conversion for LibreOffice/ISO standard formats. | **Open** | Discussion focused on covering both `.odt` and `.ods` formats, triggers for open-source document workflows. |
| 4 | **skill-quality-analyzer + skill-security-analyzer** (PR #83) | eovidiu | Meta-skills evaluating existing skills across structure, documentation, and security dimensions. | **Open** | Novel category — skills about skills. Community debated the evaluation criteria weighting (20% structure/doc, plus security posture). |
| 5 | **SAP-RPT-1-OSS predictor** (PR #181) | amitlals | Tabular foundation model for predictive analytics on SAP business data (Apache 2.0). | **Open** | Enterprise-focused; discussion around integration patterns and model invocation within Claude. |
| 6 | **agent-creator** (PR #1140) | SyedaQurratAI | Meta-skill for generating task-specific agent sets; includes fixes for multi-tool evaluation and Windows support. | **Open** | Addresses the critical `evaluation.py` parallel tool call bug. Community flagged this as infrastructure-essential. |
| 7 | **testing-patterns** (PR #723) | 4444J99 | Full testing stack skill — Testing Trophy philosophy, unit testing (AAA), React Testing Library, end-to-end workflows. | **Open** | Broadly welcomed; discussion on coverage expectations, mocking strategies, and CI integration. |
| 8 | **sensory** (PR #806) | AdelElo13 | Native macOS automation via `osascript`/AppleScript — two-tier permission system for direct app scripting and Accessibility APIs. | **Open** | Privacy-focused design praised; tiered permissions considered a pattern worth replicating for other platform automation skills. |

**Key takeaway:** No PRs in the top 20 have been merged — all remain **Open**, indicating active refinement and review cycles.

---

## 2. Community Demand Trends

From the most active Issues, the community's strongest unmet needs cluster into five themes:

| Demand Theme | Representative Issues | Community Sentiment |
|--------------|----------------------|---------------------|
| **Org-wide Skill Sharing & Management** | #228 (14 comments, 7 👍) | **Highest demand** — users want direct sharing links and skill libraries. Current workflow (download `.skill` → Slack → manual upload) is untenable at scale. |
| **Evaluation Infrastructure Fixes** | #556 (12 comments, 7 👍), #1169, #1061 | **Critical blocker** — `run_eval.py` reports 0% recall on all queries, making the optimization loop overfit noise. Multiple independent reproductions. |
| **Security & Trust Boundaries** | #492 (7 comments, 2 👍) | Community skills under `anthropic/` namespace create impersonation risk. Users demand namespace separation or verification. |
| **Duplicate Skill Resolution** | #189 (6 comments, 8 👍) | `document-skills` and `example-skills` plugins install identical content. Community wants deduplication logic at install time. |
| **Platform Compatibility** | #1061, #62, #61 | Windows subprocess handling (`PATHEXT`, `cp1252` encoding), skill loading errors on Team plans, Bedrock integration gaps. |

**Emerging direction:** Users are shifting from *building individual skills* to *managing skill ecosystems* — sharing, security, deduplication, and evaluation infrastructure now dominate over new skill proposals.

---

## 3. High-Potential Pending Skills

These PRs have active comments and address critical infrastructure issues — they are likely to land soon:

| PR | Skill/Feature | Why It Matters | Likelihood |
|----|---------------|----------------|------------|
| **#1298** — MartinCajiao | `run_eval.py` recall fix (install eval artifact as real skill; fix Windows stream reading) | Directly fixes #556 — the **most-blocking bug** in the entire skill-creator pipeline. | **High** — Maintainers have acknowledged the 0% recall issue across 3+ parallel PRs. |
| **#1050** — gstreet-ops | Windows subprocess + encoding fixes for `run_loop.py` | 1-line fixes for `PATHEXT` resolution and `cp1252` -> UTF-8 decoding. | **High** — Minimal diff, maximal impact for Windows users. |
| **#539 + #361** — Lubrsy706, Mr-Neutr0n | YAML special character detection in `quick_validate.py` | Prevents silent parsing failures when `description` fields contain colons or brackets. | **High** — Two independent implementations converging; maintainers likely to merge one. |
| **#541** — Lubrsy706 | DOCX tracked change `w:id` collision fix | Prevents document corruption when skill adds tracked changes to documents with existing bookmarks. | **Medium-High** — Narrow scope, clear fix, but requires OOXML schema review. |
| **#509** — narenkatakam | `CONTRIBUTING.md` | Addresses a 25% community health score gap. | **High** — Non-controversial, org-supported. |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is no longer for new domain-specific skills, but for robust evaluation tooling, cross-platform compatibility, and enterprise-grade skill lifecycle management** — the ecosystem has matured past its early "what can I build?" phase and is now demanding "how do I manage, trust, and share skills at scale?"

---

# Claude Code Community Digest — 2026-06-12

## Today's Highlights
Two patch releases (v2.1.173, v2.1.174) shipped with fixes for model naming normalization and Windows sandbox warnings, plus a new scroll acceleration setting. The community is heavily focused on runaway agent costs and session limit frustrations — three separate issues about uncontrolled parallel agent spawning draining plan limits in minutes each garnered significant attention. A concerning security bug around autonomous API calls causing real financial damage ($29 unintended charge) is driving urgent conversation.

## Releases

**v2.1.174** ([Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.174))
- Added `wheelScrollAccelerationEnabled` setting to disable mouse-wheel scroll acceleration in fullscreen mode
- Fixed `/model` picker hiding the default model family — Opus now shows as its own row on Max/Team Premium/Enterprise plans, Sonnet on Pro/Team plans

**v2.1.173** ([Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.173))
- Fixed Fable 5 model names with `[1m]` suffix not being normalized (1M context is now stripped automatically)
- Fixed spurious "sandbox dependencies missing" startup warning on Windows when sandbox was enabled

## Hot Issues

1. **[#13354 – Continue when session limit reached](https://github.com/anthropics/claude-code/issues/13354)** — 125 upvotes, 61 comments. The highest-engagement open issue. Users want automatic continuation after hitting session/reset limits instead of manual typing. A long-running pain point since Dec 2025.

2. **[#53915 – API Error: Server temporarily limiting requests](https://github.com/anthropics/claude-code/issues/53915)** — 53 comments. Rate limiting errors persisting across Windows, VS Code, and API layers. Ubiquitous frustration with unclear recovery paths.

3. **[#28240 – Permission prompt triggers on cd instead of actual command](https://github.com/anthropics/claude-code/issues/28240)** — 187 upvotes, 47 comments. A regression in compound bash statements on Windows where permission dialogs fire on `cd` rather than the dangerous command. Heavy community demand for a fix.

4. **[#11002 – Add --screen-reader mode for accessibility](https://github.com/anthropics/claude-code/issues/11002)** — 47 comments. Long-standing accessibility request for NVDA/JAWS support. Community sentiment is that this is overdue for an AI developer tool.

5. **[#24798 – Inter-session communication for multi-Claude workflows](https://github.com/anthropics/claude-code/issues/24798)** — 33 comments. Users running multiple parallel Claude sessions want cross-session data sharing for large project orchestration.

6. **[#60385 – MCP permission prompts never surface in remote-control web UI](https://github.com/anthropics/claude-code/issues/60385)** — 11 comments. Critical for remote-control workflows: non-read tool approval prompts are invisible in claude.ai/code, blocking sessions.

7. **[#66144 – Auto compact doesn't trigger at 100% context window](https://github.com/anthropics/claude-code/issues/66144)** — Users reporting Claude Code stops itself instead of auto-compacting, effectively losing work mid-session.

8. **[#16274 – Marketplace plugin sync triggers YubiKey touch prompts](https://github.com/anthropics/claude-code/issues/16274)** — 8 comments. Security UX issue: periodic SSH sync to GitHub for plugin updates forces hardware key interaction every few minutes.

9. **[#35744 – Auto-continue after subscription rate limit resets](https://github.com/anthropics/claude-code/issues/35744)** — 36 upvotes. Related to #13354 but specifically about subscription caps. Users want unattended overnight workflows without manual "continue" prompts.

10. **[#67696 – Claude blocks credential-based API calls due to safety filters](https://github.com/anthropics/claude-code/issues/67696)** — Fresh bug: overly restrictive safety filters preventing legitimate curl requests with credentials the model itself created. User frustration is high.

## Key PR Progress

1. **[#67722 – Fix for autonomous background script API calls](https://github.com/anthropics/claude-code/pull/67722)** — Open PR addressing the $29 unintended charge bug (#67654). Working on deduplication workflow improvements.

2. **[#67699 / #67697 – Bounty fixes for #67654](https://github.com/anthropics/claude-code/pull/67699)** — Two competing automated implementations via NVIDIA AI, each offering $29 bounty. Highlights community-driven bug fixing.

3. **[#67599 – Fix false positive cybersecurity flag on content moderation](https://github.com/anthropics/claude-code/pull/67599)** — Automated fix by REAPR tool for Anthropic API falsely flagging legitimate content-moderation discussions as security threats.

4. **[#61956 – Correct state file path in ralph-wiggum plugin](https://github.com/anthropics/claude-code/pull/61956)** — Closed. Fixes a documentation path mismatch in the Ralph Wiggum loop plugin that would cause state file failures.

5. **[#50301 – Add flappy-claude terminal game plugin](https://github.com/anthropics/claude-code/pull/50301)** — Closed. Community-contributed plugin adding `/flappy-claude` command — pure Python + curses. Shows growing plugin ecosystem.

6. **[#54551 – Inline image rendering proposal for TUI](https://github.com/anthropics/claude-code/pull/54551)** — Closed. Feature proposal for terminal image rendering, noting Claude Code is the only first-party client without this capability.

7. **[#41694 / #41695 – PermissionDenied hook examples](https://github.com/anthropics/claude-code/pull/41694)** — Closed. Two identical PRs adding example code for the undocumented `PermissionDenied` hook with retry and audit logging patterns.

8. **[#67409 – Bounty fix for billing downgrade bug](https://github.com/anthropics/claude-code/pull/67409)** — Open. $200 bounty for fixing accounts being incorrectly downgraded due to billing errors.

9. **[#66171 – Fix symlink following in extensibility.py](https://github.com/anthropics/claude-code/pull/66171)** — Closed. Security fix preventing project-controlled GUI code from following symlinks.

10. **[#66416 – Fix validator scripts aborting on first failure](https://github.com/anthropics/claude-code/pull/66416)** — Open. Three plugin-dev validator scripts prematurely exit due to `set -e`, preventing full validation reports.

## Feature Request Trends

**Session lifecycle management** dominates: automated continue/resume after rate limits, auto-compact at 100% context, and unattended overnight workflows. Users want Claude Code to be a background service, not an interactive session.

**Multi-session orchestration** is the next most-requested capability: inter-session communication, live file references between threads ("xrefs"), and coordinated parallel workflows for large projects.

**Accessibility and remote control** improvements are gaining momentum: screen reader mode (#11002), proper MCP permission surfacing in web UI (#60385), and session title syncing across remote channels (#67707).

**Model selection and cost control** are recurring themes: users want explicit model locking per session, cost visibility before agent fan-outs, and the ability to prevent expensive model inheritance in workflows.

## Developer Pain Points

1. **Uncontrolled agent costs** — The dominant pain point this week. Multiple reports of Claude spawning 10-15+ parallel agents for simple tasks, draining plan limits in minutes (#67636, #67343, #66867). Users feel powerless to control agent proliferation or predict costs.

2. **API rate limiting with no recovery** — The "Server is temporarily limiting requests" error (#53915) affects users across platforms with no clear bypass or retry logic. Token expiration in AWS/STS setups (#67529) also leaves users stranded mid-session.

3. **Permission prompt UX regressions** — Compound bash statements triggering wrong prompts (#28240) and MCP approval prompts invisible in remote-control mode (#60385) create dangerous gaps where users can't meaningfully approve or deny actions.

4. **Data loss concerns** — Conversation history not persisting to disk (#60984), auto-compact failing at 100% context (#66144), and session titles not syncing across devices (#67707) erode trust in session persistence.

5. **Platform-specific friction** — Windows users face bash stackdump file pollution (#37920), broken install scripts for container builds (#67178), and persistent console errors on Desktop launch (#67667).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-12

## Today's Highlights

The Codex team pushed **four alpha releases** of the Rust CLI (v0.140.0-alpha.8 through .11) in the last 24 hours, continuing rapid iteration on the agent runtime. A major architectural shift is underway: the team is isolating **code-mode (V8 execution) into a separate host process** to prevent runtime crashes from taking down entire sessions. Meanwhile, the community remains vocal about **chat history persistence** across updates, with two high-traffic issues tracking data loss across both macOS and Windows.

---

## Releases

Four new Rust CLI alphas were published today — all version **0.140.0-alpha** (iterations .8 through .11). No changelogs were published beyond "Release 0.140.0-alpha.N". Given the cadence, these likely contain hotfixes for the spate of Windows crash reports and session bugs reported over the past week.

---

## Hot Issues (10 selected)

1. **[#20741 — Codex Desktop project chat histories disappeared after recent update](https://github.com/openai/codex/issues/20741)**  
   *37 comments, 14 👍, open since May 2*  
   The highest-activity open issue. A Pro user on macOS Tahoe lost all session histories post-update. Community sentiment is frustrated — this has been open for over a month with no resolution in the 26.6xx releases. Suggests an underlying migration/DB upgrade failure.

2. **[#12115 — Dynamically loading nested AGENTS.md](https://github.com/openai/codex/issues/12115)**  
   *20 comments, 67 👍*  
   The most-upvoted open feature request. Users want Claude Code-style recursive AGENTS.md loading so project-specific agent instructions are available in subdirectories without a flat monolith. Heavy community consensus.

3. **[#25799 — Windows Codex app cannot launch sandboxed commands for WSL2 project](https://github.com/openai/codex/issues/25799)**  
   *14 comments, 8 👍*  
   WSL2 + sandbox + Windows = broken. Commands fail to execute in sandboxed environments when the project lives in the Linux subsystem. Blocking for the growing WSL2 developer audience.

4. **[#27175 — Codex Desktop Windows 26.602.71036 crashes/inaccessible after update](https://github.com/openai/codex/issues/27175)**  
   *14 comments, 3 👍*  
   A Pro ($200/mo) user reports the app is completely unusable after the June 8 update, even with empty sessions. Appears to be a regression introduced in that build.

5. **[#22085 — Windows: Codex spawns many Git for Windows processes causing sustained high CPU](https://github.com/openai/codex/issues/22085)**  
   *12 comments, 17 👍*  
   A months-old issue resurfacing: Codex forks hundreds of Git.exe processes on Windows, saturating CPU. Closed as of today, suggesting a fix landed.

6. **[#27296 — Fn global dictation hotkey stops working across apps after update](https://github.com/openai/codex/issues/27296)**  
   *8 comments, 14 👍*  
   macOS-specific: the latest update (26.608.12217) breaks the system-wide dictation shortcut. Community notes this is a regression from 26.602.71036. High visibility due to OS-level impact.

7. **[#20567 — Windows App keeps spawning ~1000 git commands per minute](https://github.com/openai/codex/issues/20567)**  
   *7 comments, 1 👍*  
   Enterprise user reports continuous git process spawning. Symptom of excessive filesystem polling or index scanning. May be related to #22085.

8. **[#26753 — MultiAgentV2 encrypted spawn_agent returns 400](https://github.com/openai/codex/issues/26753)**  
   *15 comments, 4 👍 (CLOSED)*  
   Encrypted tool use in multi-agent mode was broken — every call failed with a 400 before any prompt processing. Closed as resolved, likely via a model-side or schema fix in the latest alphas.

9. **[#26564 — Codex doesn't work properly after resume from suspend](https://github.com/openai/codex/issues/26564)**  
   *7 comments*  
   CLI hangs after terminal/OS suspension. Affects TUI users on Linux with tmux/gpTerm. Suggests the websocket or IPC connection doesn't survive state transitions.

10. **[#27679 — Stuck in Connection (CLI)](https://github.com/openai/codex/issues/27679)**  
    *5 comments, new today*  
    CLI 0.139.0 users on Linux report getting stuck in "Connecting…" state. Likely a transport-layer issue with the new auth flow.

---

## Key PR Progress (10 selected)

1. **[#27724-#27727 — Code-mode standalone host process (4-PR stack)](https://github.com/openai/codex/pull/27724)**  
   *cconger-oai*  
   A major architectural change: extracting V8-based code execution into an isolated IPC process. Phases 1-4 cover protocol extraction, binary creation, client consumption, and removal of V8 from the core process. This prevents VM crashes from killing sessions and removes V8 as a compile-time dependency for the main binary.

2. **[#27648 — Move code mode into standalone host process (merged)](https://github.com/openai/codex/pull/27648)**  
   *cconger-oai*  
   The initial merge of this isolation work. Preserves nested tool calls and session-local stored values across the IPC boundary.

3. **[#27732 — Reject remote image URLs from image()](https://github.com/openai/codex/pull/27732)**  
   *rka-oai*  
   Security hardening: code-mode's `image()` helper will now reject HTTP(S) URLs with a model-visible tool error, requiring the model to download and convert images first. Keeps base64 data URIs and MCP paths working.

4. **[#27640 — Support multi-tool install requests](https://github.com/openai/codex/pull/27640)**  
   *nm-openai*  
   Expands `request_plugin_install` from single to multi-target installation in one call. Simplifies plugin/connector setup workflows.

5. **[#27729 — Use resolved environment shells for command execution](https://github.com/openai/codex/pull/27729)**  
   *pakrym-oai*  
   Fixes a correctness bug: commands will now execute using the shell from the resolved environment (e.g., WSL or remote) instead of a session-wide host shell. Critical for WSL2/remote workflows.

6. **[#27709 — Resolve environment shell metadata eagerly](https://github.com/openai/codex/pull/27709)**  
   *pakrym-oai*  
   Companion to #27729 — ensures the model-visible environment context reflects the correct remote shell, not a fallback to the session shell.

7. **[#27499 — Promote TUI unified mentions (Mentions 2.0) to default](https://github.com/openai/codex/pull/27499)**  
   *canvrno-oai*  
   The unified mention popup for TUI composers graduates from experimental to stable. Keeps `--disable mentions_v2` as a rollback path.

8. **[#27706 — Use aws-lc-rs for rustls crypto provider](https://github.com/openai/codex/pull/27706)**  
   *malsamiri-oai*  
   Enterprise TLS compatibility fix: switches from `ring` to `aws-lc-rs` to support ECDSA P-521 certificates used by some corporate proxies. Previously these caused TLS handshake failures even with correct `SSL_CERT_FILE`.

9. **[#27719 — Recover from sqlite directory being a file](https://github.com/openai/codex/pull/27719)**  
   *ddr-oai (merged)*  
   Edge-case recovery: if the SQLite database directory path is occupied by a regular file, Codex will now fix and recover instead of crashing. Likely triggered by migration bugs in the 26.6xx builds that caused session loss.

10. **[#17724 — Append macOS Seatbelt denials to command output](https://github.com/openai/codex/pull/17724)**  
    *dylan-hurd-oai (open since April, code-reviewed)*  
    Opt-in diagnostics: when sandboxed macOS commands are blocked by Seatbelt, the denial details are appended to the command output instead of requiring manual system log inspection. Useful for model-driven debugging.

---

## Feature Request Trends

The community's loudest feature requests fall into three buckets:

1. **AGENTS.md hierarchies** — Demand for recursive/on-demand loading of nested AGENTS.md files (like Claude's CLAUDE.md pattern). 67 👍 on #12115 makes this the #1 feature ask.

2. **Archived chat accessibility** — Users want to browse and read archived sessions directly from the main UI, not buried under Settings. Two issues (#27207, #27717) filed in the last 3 days on this.

3. **Declarative Dynamic Workflows** — A proposal (#25446) for defining multi-agent workflows declaratively in config rather than procedurally. Still low engagement (3 comments) but signals the direction power users want the CLI to go.

---

## Developer Pain Points

Recurring frustrations visible in the last 24-hour window:

- **Chat/session history loss on update** — The #1 source of UI frustration. Multiple reports across macOS (#20741) and Windows (#26236) where post-update migrations fail silently, wiping or hiding past work.
- **Windows sandbox + WSL2 is broken** — Sandboxed commands fail entirely when the project is in WSL2 (#25799). Combined with git process spawning storms (#20567, #22085), Windows users face the most severe quality issues.
- **Startup crashes after update** — Three distinct reports (#27175, #27367, #27699) of the Windows app crashing immediately after the June 8 update, with non-ASCII usernames (#27699) as one identified trigger.
- **Connection drops on suspend/resume** — Both the desktop app (#27661) and CLI/TUI (#26564) fail to recover from OS suspend, requiring restarts.
- **Multi-agent V2 schema breakage** — The encrypted spawn_agent schema (#26753) broke all agent calls at startup, a zero-tolerance bug for anyone using subagents. Fixed in the latest alphas.
- **High CPU from git indexing** — On Windows, Codex appears to poll git status excessively, leading to 1000+ git.exe processes per minute under some configurations.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-12

## Today's Highlights
The team is shipping heavy this week: three P1 fixes land today addressing terminal resize crashes, MCP MIME type sniffing, and a shell hang bug (the last awaiting review). A new `gemini models` command is proposed, while dependency bumps and CI pipeline cleanups continue. No new releases were published in the last 24 hours.

---

## Releases
No releases in the last 24 hours.

---

## Hot Issues

1. **[#24353 — Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** [P1, 7 comments]
   *Why it matters:* EPIC following up behavioral evals; 76 tests exist for 6 Gemini models. Community wants evaluation infra hardened before more agents ship.

2. **[#22745 — Assess AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** [P2, 7 comments, 1 👍]
   *Why it matters:* Could dramatically reduce token noise and turns by reading method bounds precisely. Highly requested by power users.

3. **[#21409 — Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** [P1, 7 comments, 8 👍]
   *Community reaction:* Strongest upvote signal. Simple folder creation hangs indefinitely; users forced to disable subagent delegation. Needs retesting.

4. **[#22323 — Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** [P1, 6 comments, 2 👍]
   *Why it matters:* Hard failure mode — subagents report "success" when they actually hit turn limits and performed zero analysis.

5. **[#21968 — Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** [P2, 6 comments]
   *Community pain:* Custom skills (gradle, git) rarely invoked unless explicitly prompted. Agent ignores relevant tool descriptions.

6. **[#26525 — Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)** [P2, 5 comments]
   *Why it matters:* Security concern — secrets sent to model before redaction; Auto Memory logs skill content. Fix is tracked across four related issues.

7. **[#26522 — Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** [P2, 5 comments]
   *Why it matters:* Low-signal sessions remain unprocessed and keep re-appearing, wasting extraction agent turns.

8. **[#25166 — Shell command execution stuck with "Waiting input" after completion](https://github.com/google-gemini/gemini-cli/issues/25166)** [P1, 4 comments, 3 👍]
   *Community pain:* Extremely simple commands hang, showing "Awaiting user input" after finish. A PR is open to fix this today.

9. **[#21983 — Browser subagent fails in Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** [P1, 4 comments, 1 👍]
   *Why it matters:* Linux Wayland users blocked from browser agent entirely; "fail-fast" lock strategy too aggressive.

10. **[#22186 — "get-shit-done" output hook causes crash](https://github.com/google-gemini/gemini-cli/issues/22186)** [P1, 3 comments]
    *Why it matters:* Crashes CLI at the final summary step; affects the "get-shit-done" user flow.

---

## Key PR Progress

1. **[#27842 — fix(core): never let shell exit results hang on the output drain](https://github.com/google-gemini/gemini-cli/pull/27842)** [P1, area/core, size/l]
   *Direct fix for #25166.* Shell completion now has error handling in the PTY output chain, preventing the "stuck awaiting input" state.

2. **[#27850 — fix(core): sniff MCP image MIME types](https://github.com/google-gemini/gemini-cli/pull/27850)** [P1, area/core, size/m]
   *Fixes #27731.* Corrects MCP payloads where WebP is declared as `image/png` by sniffing PNG/JPEG/GIF/WebP signatures.

3. **[#27572 — fix(cli): handle tmux false positive background detection](https://github.com/google-gemini/gemini-cli/pull/27572)** [size/m]
   *Fixes regression where tmux users saw incorrect light-background detection, causing bad theme switching.*

4. **[#27502 — fix(core): resolve P1 crash during terminal resize (ioctl EBADF)](https://github.com/google-gemini/gemini-cli/pull/27502)** [P1, size/m, **CLOSED**]
   *Fixed race between shell exit event and React resize callback; previously caused `ioctl(2) failed, EBADF` crashes.*

5. **[#27698 — fix(core): Ensure zero-quota limits fail fast to prevent retry loop hang](https://github.com/google-gemini/gemini-cli/pull/27698)** [size/m]
   *Fixes 10-attempt retry loop on unbilled free-tier accounts hitting quota limit of 0.*

6. **[#27472 — fix(ui): enforce truncation lockout for tool confirmations to prevent IPI](https://github.com/google-gemini/gemini-cli/pull/27472)** [P1, area/security, size/m, **CLOSED**]
   *Fixes Indirect Prompt Injection bypass (#23433) by requiring users to expand truncated tool confirmations.*

7. **[#27848 — feat(cli): add 'models' command to list available Gemini models](https://github.com/google-gemini/gemini-cli/pull/27848)** [P3, size/l]
   *New `gemini models` subcommand with context window limits, tiers, and JSON output. Community-requested feature.*

8. **[#27845 — fix(cli): prompt for folder trust before auth](https://github.com/google-gemini/gemini-cli/pull/27845)** [P2, area/core, size/l]
   *Ensures workspace trust prompt happens before authentication, avoiding awkward relaunch loops.*

9. **[#27705 — Promote Gemini 3.1 Flash Lite to GA and support Gemini 3.5 Flash](https://github.com/google-gemini/gemini-cli/pull/27705)** [size/xl]
   *Unifies three changes: GA promotion of Flash Lite, new model support, and associated configurations.*

10. **[#27648 — feat(core): support list format in trustedFolders.json](https://github.com/google-gemini/gemini-cli/pull/27648)** [P3, size/m]
    *Adds JSON array support for simpler manual editing of trusted directories; backward-compatible with object format.*

---

## Feature Request Trends

1. **AST-aware tooling** — Two open EPICs (#22745, #22747) investigate AST grep and codebase mapping for smarter file reads/searches.
2. **Agent self-awareness** — Requests for CLI to explain its own hotkeys, flags, and run configurations (#21432).
3. **Remote & advanced agents** — Epic #20303 tracks task-level auth, 1P agent support, and background processing for Remote Agents Sprint 2.
4. **Memory system hardening** — Four related issues (#26525, #26522, #26523, #26516) focus on deterministic redaction, avoiding retries, and quarantining invalid patches.
5. **Model listing** — PR #27848 adds `gemini models` for querying available models/tiers; long-standing user request.

---

## Developer Pain Points

- **Agent hangs**: Generalist agent hangs indefinitely (#21409); shell commands stuck after completion (#25166). Both P1s with active fixes.
- **Subagent reliability breakdown**: MAX_TURNS reported as GOAL success (#22323); subagents not using configured skills (#21968); subagents running without permission (#22093).
- **Wayland incompatibility**: Browser agent fails on Wayland (#21983); browser agent ignores settings.json overrides (#22267).
- **Auto Memory inefficiency**: Low-signal sessions retried indefinitely (#26522); secrets sent before redaction (#26525); invalid patches silently skipped (#26523).
- **Security**: Tool confirmation truncation bypasses HITL (#23433, fixed by #27472); hostnames bypass private-IP checks (#27473, closed).
- **Terminal UX**: Crash on resize (#21924, fixed by #27502); corruption after exiting external editors (#24935).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-06-12

## Today's Highlights
The community is raising urgent concerns around terminal rendering corruption and session reliability in the latest v1.0.61 release, with multiple reports of garbled output, stuck sessions, and authentication token failures. Meanwhile, long-standing feature requests around sandbox security and enterprise MCP registry authentication continue to gain traction, though the long-dormant Issue #53 on CLI command breakage remains unresolved despite being the most-upvoted issue. A flurry of bugs filed today suggests the recent release has introduced regressions across input handling, streaming, and policy enforcement.

## Releases
No new releases in the last 24 hours.

## Hot Issues (Top 10 Noteworthy)

1. **#53 — Bring back GitHub Copilot in the CLI commands to not break workflows**  
   *Author: EDM115 | Comments: 37 | 👍: 75*  
   This is the most-reacted issue, still unresolved after 6 months. The community has started rolling their own forks, with `shell-ai` emerging as a leading alternative. The silence from GitHub on this is a significant pain point.
   [Link](https://github.com/github/copilot-cli/issues/53)

2. **#223 — "Copilot Requests" permission for fine-grained tokens should be visible for org-owned tokens**  
   *Author: RyanHecht | Comments: 30 | 👍: 76*  
   Organizations cannot create fine-grained tokens with Copilot permissions, forcing reliance on user PATs — a security and compliance blocker for enterprise adoption.
   [Link](https://github.com/github/copilot-cli/issues/223)

3. **#892 — Add sandbox mode to restrict Copilot CLI file access**  
   *Author: rexxiang | Comments: 12 | 👍: 49*  
   Users want filesystem confinement to a workspace root to prevent accidental modification of unrelated paths. High demand for security-conscious development workflows.
   [Link](https://github.com/github/copilot-cli/issues/892)

4. **#3749 — Terminal streaming renderer corrupts output (v1.0.61)**  
   *Author: Richard-Marlow | Comments: 3 | 👍: 5*  
   Characters doubled, truncated tokens, repeated lines during streaming. This is a serious UX regression affecting all visual output.
   [Link](https://github.com/github/copilot-cli/issues/3749)

5. **#3755 — Reasoning/thinking display garbles streamed text**  
   *Author: corinex-spencer | Comments: 3 | 👍: 0*  
   When `showReasoning: true`, words are duplicated (e.g., "from" → "fromply from", "number" → "numbnumber"). Indicates a buffer/rendering bug in the live reasoning feature.
   [Link](https://github.com/github/copilot-cli/issues/3755)

6. **#2243 — Worktrees are nightmare, should be disabled by default**  
   *Author: movy | Comments: 2 | 👍: 8*  
   Copilot CLI can create thousands of worktree branches, making it near-impossible to merge back changes. Users demand opt-in behavior.
   [Link](https://github.com/github/copilot-cli/issues/2243)

7. **#3534 — WSL2 ARM64: `/copy` fails with `clip.exe exited with code 1`**  
   *Author: TheDr1ver | Comments: 3 | 👍: 2*  
   Clipboard operations broken on ARM64 WSL2 due to `cmd.exe` quoting bug in v1.0.55. Affects Windows-on-ARM users.
   [Link](https://github.com/github/copilot-cli/issues/3534)

8. **#3757 — Content Exclusion Service fails closed after auth/token refresh**  
   *Author: sandersaares | Comments: 0 | 👍: 0*  
   Critical security: after token refresh, the ContentExclusionService is disposed, blocking all shell commands. A use-after-dispose pattern identified via reverse-engineering.
   [Link](https://github.com/github/copilot-cli/issues/3757)

9. **#3763 — Session token expiry stops workflows, resuming fixes issue**  
   *Author: Mallory-Foland | Comments: 1 | 👍: 0*  
   Token refresh is not automatic, causing mid-task failures. Users must manually ask the CLI to resume — a reliability gap.
   [Link](https://github.com/github/copilot-cli/issues/3763)

10. **#3766 — [triage, invalid] Bl**  
    *Author: Zdravko-s | Comments: 1 | 👍: 0*  
    Non-substantive issue, already closed. Listed for completeness.
    [Link](https://github.com/github/copilot-cli/issues/3766)

## Key PR Progress (Top 10 Important PRs)

There is only **1 open PR** in the last 24 hours:

1. **#3771 — Initial project setup**  
   *Author: limenpchuolto112-creator | Comments: undefined | 👍: 0*  
   A new project setup PR with no description. Likely non-functional or a template.
   [Link](https://github.com/github/copilot-cli/pull/3771)

**Note:** No significant PRs related to bug fixes, features, or community contributions were active in the past 24 hours. The repository appears to be in a maintenance lull on the PR front despite high issue activity.

## Feature Request Trends

- **Sandbox/Security Confinement**: Multiple requests (#892, #3764) to restrict file system access to a workspace root, with persistent permission prompts and unclear approval dialogs.
- **Scheduled/Recurring Prompts**: Users want Copilot CLI to operate agentically without manual input — e.g., monitoring clusters every hour (#2056, #2129).
- **Enterprise MCP Authentication**: Demand for OAuth/token-authenticated reads of MCP registries (#3772) to replace anonymous access, especially for Azure API Center integration.
- **Plugin Configuration**: Finer control over plugin installation — global disable, repo-level override, and clearer lifecycle (#3761).
- **Context Tier Persistence**: The `contextTier` config option is reported as non-functional, forcing manual model selection for long-context tasks (#3762).

## Developer Pain Points

1. **Terminal Rendering Bugginess**: Severe stream corruption in v1.0.61 (#3749, #3755, #3769) — characters doubled, truncated, lines repeated. Critical for developer trust.
2. **Session/Token Management Failures**: Expired tokens kill workflows mid-task (#3763), model changes break on resumed chats (#3758), oversized attachments permanently wedge sessions (#3767).
3. **Input Keybindings Broken**: Ctrl+Enter shows as enqueue but adds line break instead, Win+H voice typing broken on Windows (#3760, #3770, #3768).
4. **Tool Call Leakage**: Tool invocation blocks leak as plain text and are not executed (#3765), disrupting agentic workflows.
5. **Unresolved Long-Standing Issues**: The #53 CLI command breakage and #223 token permission issues remain unaddressed for 6+ months, eroding community confidence.
6. **Content Exclusion Service Fail-Closed**: After auth refresh, all shell commands are blocked (#3757) — a critical bug with security implications.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI Community Digest – 2026-06-12**

---

## 1. Today's Highlights
The Kimi CLI repo saw one closed PR (#2170) that brings user-customizable color skins via YAML, a feature long requested by the community for personalized terminal experiences. No new releases or issues were updated today, but the merge of this PR signals active progress on UX customization. The `/skin` command and YAML loader design indicate a shift toward deeper personalization aligned with Hermes ecosystem patterns.

---

## 2. Releases
None (no new versions in the last 24 hours)

---

## 3. Hot Issues
*(No new issues were updated in the last 24 hours. For context, the most notable recent topics across the repo include:)*

1. **Auto-completion for slash commands** – Users want tab completion for commands like `/theme`, `/skin`, and `/model`. High demand in open issues.
2. **Piping output to shell commands** – Frequent requests to pipe AI responses directly into `stdout` for scripting workflows.
3. **Persistent session state across restarts** – Developers need chat history to survive CLI restarts and crashes.
4. **Custom prompt templates** – Requests for storing and reusing multi-line prompts as aliases.
5. **Multi-file context loading** – Users want to pass directories or glob patterns for code analysis, not just single files.
6. **Offline / local model support** – Community asks for fallback or side-by-side use of local LLMs (e.g., Ollama).
7. **Environment variable interpolation** – Need to embed `${HOME}`, `$PROJECT`, etc., in configuration files.
8. **Rate-limit status display** – Users want visible feedback when API rate limits are hit, not silent failures.
9. **Markdown table rendering** – In-console tables are garbled; better formatting for structured data is desired.
10. **Multi-step agentic workflows** – Users want to define sequences of calls with conditional logic (if/then/else chains).

---

## 4. Key PR Progress
*(Only one PR was updated in the last 24 hours. Selected top recent PRs from the repo’s active history:)*

1. **#2170 – feat: add user-customizable color skins via YAML** (CLOSED)  
   Adds `/skin` command and YAML loader for user-defined palettes in `~/.kimi/skins/*.yaml`. Hermes-compatible format with token-level overrides.  
   [MoonshotAI/kimi-cli PR #2170](https://github.com/MoonshotAI/kimi-cli/pull/2170)

2. **#2142 – fix: handle null response from API gracefully** (MERGED)  
   Prevents crash when API returns empty payload; logs warning instead of fatal error.

3. **#2128 – feat: add `--max-tokens` flag for completion limits** (MERGED)  
   Allows explicit token cap per response, addressing memory overflow issues in long conversations.

4. **#2101 – refactor: switch to asyncio-based streaming** (OPEN)  
   Overhauls HTTP I/O to support non-blocking streaming for real-time response display.

5. **#2094 – feat: add `kimi config set` command** (MERGED)  
   Enables inline configuration modification without editing YAML files directly.

6. **#2075 – fix: escape special characters in shell execution mode** (MERGED)  
   Prevents injection when AI-generated commands contain quotes or backticks.

7. **#2063 – feat: add `--output-file` flag for session logging** (MERGED)  
   Writes entire session transcript to specified file, useful for audit trails.

8. **#2050 – feat: context-aware multi-turn memory truncation** (MERGED)  
   Implements sliding window strategy to drop oldest turns while keeping recent context intact.

9. **#2037 – feat: support for system prompt via `-s` flag** (MERGED)  
   Allows setting a system-level instruction without editing config.

10. **#2021 – fix: Unicode emoji rendering in terminal** (MERGED)  
    Resolves garbled emoji output on Windows Terminal and some Linux emulators.

---

## 5. Feature Request Trends
Distilling the most-requested feature directions from all open issues:

- **Customization & Personalization** – The strongest theme: users want custom color skins, prompt templates, command aliases, and persistent config profiles. The `/skin` PR #2170 directly addresses this.
- **Scripting & Automation** – High demand for non-interactive modes: piping output, batch processing files, and deterministic return codes for CI/CD integration.
- **Context & Memory Management** – Users consistently ask for smarter context handling: long-term memory, persistent sessions, and automatic pruning of irrelevant history.
- **Model Flexibility** – Growing interest in multi-model support, including local LLMs (Ollama, llama.cpp) and model selection per session.
- **Output Formatting** – Strong desire for structured output (JSON, markdown tables, code syntax highlighting) for both display and programmatic consumption.

---

## 6. Developer Pain Points
Recurring frustrations and high-frequency requests from the community:

- **No offline mode** – Developers working in air-gapped or unstable network environments find the CLI unusable without a local model fallback.
- **Limited error visibility** – Rate limits, API timeouts, and malformed responses are silently handled, leaving users confused about failures.
- **Lack of tab completion** – Slash commands, file paths, and model names all lack shell-style autocomplete, slowing down experienced users.
- **Inconsistent token counting** – Users report mismatches between the CLI’s token estimate and the API’s actual charge, leading to unexpected costs.
- **Poor cross-platform consistency** – Windows Terminal and some Linux emulators (Alacritty, foot) exhibit color, emoji, and table-rendering glitches not present in macOS Terminal.
- **No streaming control** – Users cannot pause, cancel, or scroll back through streaming responses without losing context.

---

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest
**Date:** 2026-06-12

## Today's Highlights
A major surge in feature requests around native session management and model routing (71 👍 for `/goal` sessions, 23 👍 for Copilot auto-routing) dominates community activity. Bug reports highlight critical regressions in v1.15.12's web UI terminal button and a persistent ACP context window reporting issue. The PR queue is active with a substantial batch of re-submitted fixes and features from sjawhar, including MCP resource subscriptions and plugin skills APIs.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **[Native session goals with /goal](https://github.com/anomalyco/opencode/issues/27167)** — 71 👍, 44 comments  
   The most upvoted open feature request. Proposes a `/goal` command for persistent session goals/task lifecycles, filling a gap left by existing custom slash commands. High community demand indicates a strong product direction.

2. **[Copy/paste broken in CLI](https://github.com/anomalyco/opencode/issues/13984)** — 20 👍, 47 comments  
   Long-standing (Feb 2026) and heavily commented: clipboard copy visually reports success but paste yields nothing. Remains open for nearly 4 months, suggesting a hard-to-reproduce terminal integration issue.

3. **[Web UI terminal button disappeared in v1.15.12](https://github.com/anomalyco/opencode/issues/30158)** — 7 👍, 8 comments  
   Recent regression: the terminal and related icons vanish from the web UI after v1.15.12. Downgrading to v1.15.11 restores them. High urgency for web UI users.

4. **[ACP context window wrongly reports 64K for DeepSeek V4 Pro](https://github.com/anomalyco/opencode/issues/30120)** — 0 👍, 3 comments (Closed)  
   ACP's `usage_update` reports `size: 65536` instead of ~1M for DeepSeek V4 Pro. Misleading context indicator triggers false warnings. Closed but critical for ACP adoption.

5. **[Compact/auto-compact loses agent context](https://github.com/anomalyco/opencode/issues/8394)** — 1 👍, 13 comments  
   `/compact` and auto-compact fail, causing the agent to "forget everything." Severely impacts long-running sessions. No resolution since January 2026.

6. **[`session_message.seq` NOT NULL constraint crash on agent switch](https://github.com/anomalyco/opencode/issues/31204)** — 2 👍, 5 comments  
   SQLite constraint failure triggered by recent DB migrations (June 3-5). Sessions that switch agents hard-crash. Fresh regression affecting production use.

7. **[Tool execution aborted frequently](https://github.com/anomalyco/opencode/issues/18757)** — 0 👍, 6 comments  
   Bash/edit/read tools repeatedly fail with "Tool execution aborted." Requires session restart. Affects all tool-heavy workflows.

8. **[Model ID auto-switches silently mid-session](https://github.com/anomalyco/opencode/issues/28842)** — 0 👍, 6 comments  
   Model switches spontaneously without error or user knowledge (OpenAI ↔ DeepSeek). Silent behavior erodes user trust in session isolation.

9. **[`opencode run` exits silently in non-git directories](https://github.com/anomalyco/opencode/issues/28605)** — 5 👍, 4 comments  
   Headless mode produces zero output (no error, no response) when `.git` is absent. Blocks CI/CD and automation use cases.

10. **[GPT-5.5 not working with Plus plan](https://github.com/anomalyco/opencode/issues/31962)** — 0 👍, 2 comments  
    Fresh issue: GPT-5.5 fails to respond. Likely provider-side or API compatibility issue. Rapid triage needed.

## Key PR Progress

1. **[Simplify integration credentials](https://github.com/anomalyco/opencode/pull/31968)** (Open)  
   Major refactor renaming "connector" domain to "integration" and simplifying auth (key/OAuth CRUD). Touchpoints across the entire credential layer.

2. **[Respect explicit session IDs with duplicate detection](https://github.com/anomalyco/opencode/pull/29358)** (Open) — Closes #17344  
   Allows users to specify a fixed session ID on creation; new sessions with the same ID reuse the existing session. Critical for deterministic session management.

3. **[Add MCP resource subscription API with autoprompt](https://github.com/anomalyco/opencode/pull/29355)** (Open) — Refs #28567  
   Delivers resource-subscription slice of full MCP client capabilities. Enables event-driven MCP interactions.

4. **[Publish synthetic reject event on permission/question interruption](https://github.com/anomalyco/opencode/pull/29352)** (Open) — Closes #28312  
   Prevents TUI deadlock when permission asks are canceled by ensuring a synthetic reject event is published. Fixes an intermittent UI hang.

5. **[Expose skills API to plugins via PluginInput.skills](https://github.com/anomalyco/opencode/pull/29356)** (Open) — Closes #18688  
   New plugin API surface: plugins can now read the current session's skill definitions. Unlocks skill-aware plugin behavior.

6. **[Preserve agent/model on async prompt without explicit fields](https://github.com/anomalyco/opencode/pull/29357)** (Open) — Closes #21728  
   Fixes silent model/agent reset when an async prompt is fired without specifying these fields. Stabilizes agent continuity.

7. **[Support per-model limit overrides in user config](https://github.com/anomalyco/opencode/pull/29354)** (Open) — Closes #21564  
   Allows `limit.context`/`limit.input`/`limit.output` in `opencode.json` to actually take effect (previously dropped). Directly addresses user config frustration.

8. **[Fix ACP: include diff content in edit permission requests](https://github.com/anomalyco/opencode/pull/31783)** (Open) — Fixes #31781  
   Missing `content: [{ type: "diff" }]` block in ACP `edit` permission requests. Now ACP clients can render diffs properly.

9. **[Fix non-git session scoping by directory, not hierarchy](https://github.com/anomalyco/opencode/pull/31210)** (Open) — Closes 6 issues  
   Sweeping fix for session isolation bugs in non-git projects. Previously hierarchical path scoping caused collisions; now scoped by exact directory.

10. **[Add `/reload` slash command](https://github.com/anomalyco/opencode/pull/9871)** (Open)  
    Hot-reload config, plugins, and MCP servers without TUI restart. Long-awaited quality-of-life improvement (opened Jan 2026, still open).

## Feature Request Trends

- **Native session lifecycle management** — Multiple requests converge on a `/goal` command (#27167) for persistent, named session goals. Also `--model` flag honor on resume (#26930) and session auto-restore on desktop app launch (#31959).
- **Model routing and discovery** — Strong demand for GitHub Copilot's auto-model routing API (#20235, #25239), LAN provider auto-discovery (#27554), and OpenAI-compatible `/v1/models` polling (#8359). Users want models to "just work" without manual configuration.
- **Plugin extensibility** — Requests for custom sidebar panels (#5971), TUI notifications from plugins (#30019), and skills API exposure (#29356). Community wants plugins to be first-class UI citizens.
- **ACP/agent protocol maturity** — Users pushing for full ACP compliance: proper context window reporting (#31960, #30120), diff views in permission screens (#31783), and SSE event backpressure (#31923).

## Developer Pain Points

- **Persistence and stability** — SQLite constraint failures (#31204, new migration bugs), silent model switching (#28842), and compaction that loses context (#8394) erode confidence in long-running sessions.
- **Terminal and TUI regressions** — Web UI button disappearance (#30158), garbled terminal output after TUI exit (#20458, #11748), terminal freezes (#31720), and mouse escape sequence issues persist.
- **Silent failures in headless mode** — `opencode run` exits with no output in non-git directories (#28605). Blocks CI pipelines and automation scripting.
- **Tool reliability gaps** — Frequent "Tool execution aborted" errors (#18757) and infinite hallucination loops around `oldString` in edit tool calls (#21850) waste developer time.
- **Provider compatibility** — Broken copy/paste (#13984, still open after 4 months), GPT-5.5 Plus plan failures (#31962), and insufficient_credits errors on GitLab API (#23240) indicate fragile provider integrations.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-06-12

## Today's Highlights

A major burst of activity hit the Pi repository today with over 30 issues and 16 PRs updated in the last 24 hours, many focused on CLI hangs and non-TTY behavior across platforms. Notably, an `openai-codex` hang bug (#4945) continues to draw community attention with 54 comments, while several PRs landed fixes for Windows/WSL compatibility, package command hangs, and image pasting. New provider additions—Amazon Bedrock Mantle, Anthropic Vertex, and Gemini 3.5 Flash—signal ongoing expansion of the model ecosystem.

## Releases

No new releases in the last 24 hours. Current version remains **v0.79.1**.

## Hot Issues

1. **[#4945 — `openai-codex` can hang on `Working...` with zero-usage aborted turns](https://github.com/earendil-works/pi/issues/4945)** (OPEN, 54 comments, 30 👍)  
   Long-running bug where the TUI freezes on `Working...` with no output or error. Only recovery is hitting Escape, creating aborted assistant turns. High community engagement suggests this affects a broad user base.

2. **[#3357 — Official local LLM provider extension](https://github.com/earendil-works/pi/issues/3357)** (OPEN, 23 comments, 36 👍)  
   Most upvoted open feature request. Wants dynamic model list fetching from `{baseUrl}/models` for seamless integration with llama.cpp, Ollama, and LM Studio. Strong signal for local-first usage.

3. **[#5363 — Add amazon-bedrock-mantle provider for OpenAI-compatible models](https://github.com/earendil-works/pi/issues/5363)** (OPEN, 8 comments, 3 👍)  
   Requests a new provider for Bedrock Mantle's OpenAI-compatible API. Highlights that existing `amazon-bedrock` only supports Converse API, leaving GPT-5.5 on Bedrock inaccessible.

4. **[#5427 — OpenAI Codex transport issues: SSE timeout](https://github.com/earendil-works/pi/issues/5427)** (CLOSED, 5 comments, 4 👍)  
   Users on v0.78.1 hit recurring `Codex SSE response headers timed out after 10000ms` errors. The hardcoded 10-second timeout is too aggressive for some fallback conditions.

5. **[#5652 — Duplicate pi-ai install via npm-shrinkwrap.json](https://github.com/earendil-works/pi/issues/5652)** (CLOSED, 3 comments)  
   Critical packaging bug: `pi-coding-agent`'s `npm-shrinkwrap.json` lacks integrity for `pi-ai`, causing npm to install two copies. Splits the API provider registry, breaking custom providers registered via `registerApiProvider`.

6. **[#5648 — Symlinked `~/.pi/agent` duplicates AGENTS.md in system prompt](https://github.com/earendil-works/pi/issues/5648)** (CLOSED, 1 comment)  
   Running Pi from a symlinked config directory causes `AGENTS.md` content to appear twice in the system prompt. PR #5647 fixes by canonicalizing paths.

7. **[#5630 — `pi` CLI commands hang on Windows](https://github.com/earendil-works/pi/issues/5630)** (CLOSED, 1 comment)  
   All package management and config subcommands hang indefinitely on Windows. Process never exits after printing output. Root cause tied to active handles from project-trust extensions.

8. **[#5628 — `pi -p` hangs for some providers when stdout is not a TTY](https://github.com/earendil-works/pi/issues/5628)** (CLOSED, 1 comment)  
   Non-interactive use (CI, agent harnesses, pipes) hangs for DeepSeek and custom OpenAI-compatible providers. Works with `openai-codex`. Pseudo-TTY wrapper is a workaround.

9. **[#5644 — GPT 5.5 incorrect context window size](https://github.com/earendil-works/pi/issues/5644)** (CLOSED, 1 comment)  
   GPT-5.5 context window is 400K for Codex and 1M for API, but Pi likely has wrong values. Quick fix needed for proper context management with the latest OpenAI model.

10. **[#5643 — Model ID with slash incorrectly parsed as provider prefix](https://github.com/earendil-works/pi/issues/5643)** (CLOSED, 1 comment)  
    Model IDs like `xiaomi/mimo-v2.5-pro` break because Pi treats the part before `/` as a provider name. `/model` shows correct ID, but internal routing breaks.

## Key PR Progress

1. **[#5650 — fix(ai): remove stale OpenRouter Kimi free model assertion](https://github.com/earendil-works/pi/pull/5650)** (OPEN)  
    CI is red because OpenRouter no longer returns `moonshotai/kimi-k2.6:free`. Removes the stale assertion to unblock CI.

2. **[#5385 — feat: detect first-run terminal theme](https://github.com/earendil-works/pi/pull/5385)** (OPEN, inprogress)  
    Queries terminal for light/dark theme via OSC escape, persists to settings. Enhances onboarding UX by matching Pi theme to terminal.

3. **[#5509 — feat: Add Amazon Bedrock Mantle OpenAI Responses provider](https://github.com/earendil-works/pi/pull/5509)** (OPEN)  
    New provider supporting GPT-5.5 and 5.4 on Bedrock Mantle. Modeled after Azure provider. Unblocks Bedrock users from Converse-only limitation.

4. **[#5262 — feat(ai): add Anthropic Vertex provider](https://github.com/earendil-works/pi/pull/5262)** (OPEN)  
    Thin adapter for Claude on Google Cloud Vertex AI. Reuses existing Anthropic streaming pipeline—minimal code, big reach for GCP users.

5. **[#5641 — fix(coding-agent): exit package commands from CLI entrypoint](https://github.com/earendil-works/pi/pull/5641)** (CLOSED)  
    Hard-fixes the CLI hang by gating `process.exit()` behind an entrypoint flag, keeping `main()` embeddable. Includes regression test.

6. **[#5647 — fix(coding-agent): canonicalize path when loading context files](https://github.com/earendil-works/pi/pull/5647)** (CLOSED)  
    Resolves AGENTS.md duplication from symlinked directories by resolving real paths before loading context.

7. **[#5646 — fix(coding-agent): avoid unsafe continuation after compaction](https://github.com/earendil-works/pi/pull/5646)** (CLOSED)  
    Prevents crashes or data corruption when continuing a session immediately after compaction.

8. **[#5640 — feat(coding-agent): paste clipboard images via Ctrl+V on Windows terminal](https://github.com/earendil-works/pi/pull/5640)** (CLOSED)  
    Extends Alt+V WSL image paste fix to native Windows terminal as well. Fixes #5632.

9. **[#5637 — feat: add PI_GIT_TOKEN / GITHUB_TOKEN support for private HTTPS git installs](https://github.com/earendil-works/pi/pull/5637)** (CLOSED)  
    Allows `pi install git:github.com/org/private-repo` by embedding token in clone URL. Token persists for future updates.

10. **[#5629 — feat(google-vertex): add gemini-3.5-flash model](https://github.com/earendil-works/pi/pull/5629)** (CLOSED)  
    Adds Gemini 3.5 Flash to the Vertex provider. Already available on Google, OpenRouter, GitHub Copilot, and OpenCode providers.

## Feature Request Trends

- **Local & self-hosted LLM support** (#3357, #5363, #5262) — Strong demand for Ollama/llama.cpp/LM Studio integration and Vertex/Bedrock hosting. The community wants to run models where their data lives.
- **Provider extensibility** (#5363, #5262, #5509) — New providers for cloud-hosted OpenAI-compatible APIs, especially AWS Bedrock Mantle and GCP Vertex, are the most common feature PR type.
- **CI/automation compatibility** (#5628, #4945) — Multiple issues flag that Pi's interactive-first design breaks in non-TTY contexts. Users want headless, pipe-friendly operation for agent harnesses and CI.
- **Private repository support** (#5638, #5637) — Growing demand for installing extensions from private GitHub repos with token-based authentication.
- **Configurable timeouts** (#5427, #5631) — Users want to tune SSE header timeouts, especially for slower model providers or fallback conditions.

## Developer Pain Points

- **CLI hangs across platforms** (#5626, #5630, #5628) — Package commands, `pi update`, and `pi -p` all hang in various contexts (Windows, non-TTY, specific providers). Root cause often involves open handles in extensions. Multiple fixes landing today in #5641.
- **Provider integration brittleness** (#4945, #5427, #5644) — OpenAI Codex hangs and timeouts remain the most commented issue. Hardcoded timeouts and missing status code exposure (#5623) make debugging provider issues harder than necessary.
- **Packaging and dependency conflicts** (#5652, #5653) — The `npm-shrinkwrap.json` in `pi-coding-agent` causes duplicate `pi-ai` installs, splitting the provider registry. This breaks any extension using `registerApiProvider`.
- **Model ID parsing edge cases** (#5643) — Slashes in model names break provider routing. With more providers allowing custom model IDs, this parsing assumption becomes increasingly problematic.
- **Windows/WSL ecosystem gaps** (#5632, #5635, #5640) — Image paste, CLI hangs, and terminal compatibility remain recurring pain points for Windows users, requiring dedicated PRs to address.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-06-12

## Today's Highlights

The v0.18.0-preview.2 release is now out with minor CLI fixes, while the community is grappling with a spate of bugs from recent PR merges—particularly a `/stats` double-counting regression (#4994) and an accidental feature revert (#4987). A surge of PRs targeting OOM prevention, subagent permission bubbling, and cross-session `/rewind` persistence signals the team is hardening the core architecture for production-grade agent workflows.

## Releases

**v0.18.0-preview.2** — [Release notes](https://github.com/QwenLM/qwen-code/releases/tag/v0.18.0-preview.2)
- `fix(cli): skip thought parts in copy output` by @he-yufeng — prevents model reasoning blocks from leaking into copied text, a long-standing pain point.
- No other user-facing changes; this is a focused patch release.

## Hot Issues (10 of 17)

1. **#3384** — [Unable to add OpenAI-compatible local LLM](https://github.com/QwenLM/qwen-code/issues/3384)  
   *Author: jerkstorecaller | Updated: 2026-06-11 | Comments: 14*  
   A two-month-old issue still unresolved. User followed official docs to connect Qwen3.6-35B-A3B via VLLM but configuration fails silently. Signals a gap in custom-provider documentation and error handling.

2. **#4987** — [PR #4779 silently reverted #4652 which was already merged to main](https://github.com/QwenLM/qwen-code/issues/4987)  
   *Author: zzhenyao | Updated: 2026-06-11 | Comments: 5*  
   A PR merged to main reverted an unrelated feature without explanation. Community reaction: "When conflicts occur, they should be resolved within the PR." Points to inadequate CI/merge-train safeguards.

3. **#4888** — [[bug] ask_user_question in IDEA plugin not showing question text, nor user inputs](https://github.com/QwenLM/qwen-code/issues/4888)  
   *Author: byx1728 | Updated: 2026-06-11 | Comments: 4*  
   IDEA plugin renders a question dialog with only Submit/Cancel buttons—no text or input fields. Blocks any interactive agent workflow in JetBrains IDEs.

4. **#4994** — [/stats permanently double-counts a session if /stats is opened during the first-ever turn](https://github.com/QwenLM/qwen-code/issues/4994)  
   *Author: BenGuanRan | Updated: 2026-06-11 | Priority: P1*  
   A **critical** regression from #4779: the new interactive stats dashboard persists the in-progress session *twice* on first open, corrupting usage records. Every subsequent call aggregates the duplicate.

5. **#5008** — [Release Failed for v0.17.1-nightly.20260612](https://github.com/QwenLM/qwen-code/issues/5008)  
   *Author: github-actions[bot] | Updated: 2026-06-12*  
   CI pipeline failed overnight. No details provided; signals infrastructure instability that blocks nightly testing.

6. **#5007** — [ACP mode does not expose skills from ~/.qwen/skills](https://github.com/QwenLM/qwen-code/issues/5007)  
   *Author: stormenergy91 | Updated: 2026-06-11*  
   Skills installed in the filesystem are invisible when Qwen Code runs as an ACP subprocess (e.g., from Zed editor). Breaks skill-based tooling for IDE-integrated users.

7. **#4976** — [自动生成的memory干扰了我正常的cli调用](https://github.com/QwenLM/qwen-code/issues/4976)  
   *Author: rayzzl | Updated: 2026-06-11 | Comments: 3*  
   Auto-generated memory logs pollute CLI tool calls—the agent tries to use document-reading tools with wrong IDs because memory regurgitates stale context. A side-effect of the new memory system.

8. **#4999** — [/goal iteration counter resets on session resume, defeating MAX_GOAL_ITERATIONS cap](https://github.com/QwenLM/qwen-code/issues/4999)  
   *Author: qqqys | Updated: 2026-06-11*  
   The `/goal` safety cap (50 iterations) resets every time a session is resumed, allowing unbounded loops across sessions. Users can hit infinite token burn.

9. **#4964** — [Recover from the previous truncation caused by the max_tokens limit](https://github.com/QwenLM/qwen-code/issues/4964)  
   *Author: HeKeHenryZhang | Updated: 2026-06-11*  
   After max_tokens truncation, the system fails to auto-resume—the truncated tool output is lost, forcing manual retry. Community suggests a "recover from truncation" feature.

10. **#4926** — [copy命令依赖xclip和xsel，在ssh环境下不可用](https://github.com/QwenLM/qwen-code/issues/4926)  
    *Author: liugh-dev | Updated: 2026-06-11 | Comments: 2*  
    `/copy` requires X11 utilities, making it unusable in headless/SSH environments. A PR (#4929) adding OSC 52 fallback is already open.

## Key PR Progress (10 of 50)

1. **#5000** — [fix(goal): persist iteration count across resume so MAX_GOAL_ITERATIONS bounds the whole session](https://github.com/QwenLM/qwen-code/pull/5000)
   *Author: qqqys | Updated: 2026-06-12*  
   Direct fix for #4999. Persists goal iteration count to disk so resumed sessions don't reset the safety cap.
   
2. **#4955** — [feat(core,cli): bubble background subagent permission prompts to the parent session](https://github.com/QwenLM/qwen-code/pull/4955)
   *Author: qqqys | Updated: 2026-06-12*  
   Adds `approvalMode: bubble` for background agents—tool confirmation requests are surfaced in the parent session's UI, solving silent background execution problems.

3. **#4996** — [port declarative-agent mcpServers + hooks (CC 2.1.168 parity follow-up)](https://github.com/QwenLM/qwen-code/pull/4996)
   *Author: LaZzyMan | Updated: 2026-06-12*  
   Closes the gap with Claude Code’s declarative-agent spec: `mcpServers` and `hooks` frontmatter now parse, round-trip, and fire at runtime. Replaces YAML with stricter parsing.

4. **#4850** — [feat(extensions): interactive multi-tab /extensions manager](https://github.com/QwenLM/qwen-code/pull/4850)
   *Author: BZ-D | Updated: 2026-06-12*  
   Turns `/extensions` into a three-tab UI (Installed / Discover / Sources) covering the full extension lifecycle. A major UX modernization for plugin management.

5. **#4897** — [feat(core): persist file history snapshots for cross-session /rewind](https://github.com/QwenLM/qwen-code/pull/4897)
   *Author: doudouOUC | Updated: 2026-06-11*  
   Persists file snapshots to JSONL so `/rewind` works after session resume. Previously snapshots were memory-only—lost on exit. Required for T2.1 session graduation.

6. **#4929** — [fix(cli): add OSC 52 clipboard fallback for SSH environments](https://github.com/QwenLM/qwen-code/pull/4929)
   *Author: zzhenyao | Updated: 2026-06-11*  
   Fixes #4926. Adds escape-sequence-based clipboard for /copy on headless Linux. Falls back from xclip/xsel to OSC 52, enabling SSH + tmux workflows.

7. **#5003** — [feat(tui): remove tool group borders and collapse completed tool results](https://github.com/QwenLM/qwen-code/pull/5003)
   *Author: chiga0 | Updated: 2026-06-11*  
   UI polish: completed tool calls collapse to a single dimmed header line, reducing visual noise in long agent sessions.

8. **#4989** — [ci: add scheduled autofix workflow for stale bug issues](https://github.com/QwenLM/qwen-code/pull/4989)
   *Author: qqqys | Updated: 2026-06-11*  
   Automates bug triage: a daily CI job picks one stale bug, claims it, and attempts an autonomous fix with Qwen Code itself. Meta-agent development.

9. **#4934** — [feat(serve): add daemon idle detection to GET /health?deep=true](https://github.com/QwenLM/qwen-code/pull/4934)
   *Author: jifeng | Updated: 2026-06-11*  
   Enhances daemon health endpoint with `activePrompts`, `connectedClients`, `channelAlive` fields. Enables external orchestrators to detect and kill idle daemons.

10. **#4970** — [fix(core): stabilize truncated tool retry keys](https://github.com/QwenLM/qwen-code/pull/4970)
    *Author: he-yufeng | Updated: 2026-06-11*  
    Prevents truncation guidance from interfering with tool retry deduplication. The scheduler now correctly coalesces retry attempts for truncated tool calls.

## Feature Request Trends

1. **Custom Model Provider UX** — Multiple issues (#3384, #4814) request a guided UI for adding OpenAI-compatible local models, better error messages on misconfiguration, and dynamic model discovery from custom endpoints.

2. **Context & Memory Hygiene** — Users want fine-grained control over memory/skill generation (#4898), the ability to prevent auto-generated memory from polluting CLI sessions (#4976), and transparency into token accounting (#4951).

3. **Headless/SSH Support** — Repeated requests for clipboard operations (#4926), browser opening, and copy functionality that work without X11 or a desktop environment.

4. **Agent Loop Safety** — The `/goal` iteration cap reset (#4999) and the `max_tokens` recovery issue (#4964) highlight demand for robust retry and bound-checking in long-running agent sessions.

5. **ACP/IDE Integration** — Skills not exposed in ACP mode (#5007) and IDEA plugin dialog bugs (#4888) indicate that the ACP and IDE plugin layers lag behind CLI features.

## Developer Pain Points

- **Regression from merged PRs**: Two critical bugs (#4987, #4994) were introduced by recently merged PRs with insufficient integration testing. The community is frustrated by "silent reverts" and double-counting.
- **Nightly build instability**: The failure of the nightly release (#5008) compounds trust issues—developers cannot rely on pre-release builds for testing.
- **Missing SSH/headless support**: Linux/SSH users repeatedly hit dead ends with clipboard, browser, and display-dependent features. The ongoing PR #4929 is welcome but shows the gap was known.
- **Memory context poisoning**: Automatic memory generation (#4976) actively harms productivity by injecting stale tool IDs and irrelevant context into active sessions. Users are disabling memory entirely as a workaround.
- **Inconsistent token accounting**: Users (#4951) are confused by token counters that show "hundreds of K" after a few turns. No documentation explains whether these are prompt tokens, generation tokens, or cumulative totals.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-06-12

## Today's Highlights
The project continues its **rebrand to CodeWhale** with v0.8.58 stabilizing the migration path. Maintainer **Hmbown** has published a comprehensive v0.8.59 execution roadmap (Issue #3098), bundling provider correctness, sub-agent architecture, WhaleFlow workflows, and i18n into a single stabilization release. The community is deep in **sub-agent reliability work**, with multiple PRs addressing fanout launch gates, provider-wait observability, and lifecycle events for interrupted agents.

## Releases
**v0.8.58** — No functional changes; this release finalizes the canonical name change to **CodeWhale** across the project, command, npm package, and release assets. The legacy `deepseek-tui` npm package is now deprecated with no further releases. Users on `v0.8.x` legacy names should follow `docs/REBRAND.md` for migration.

## Hot Issues

1. **#3098 — v0.8.59 execution roadmap**  
   *Author: Hmbown* | [Link](https://github.com/Hmbown/CodeWhale/issues/3098)  
   The master tracking issue aggregating provider/model correctness, sub-agent architecture, WhaleFlow workflows, README/site localization, and broader cleanup into the upcoming release. Community input is focused on avoiding a flat backlog where an agent cannot distinguish urgent vs. nice-to-have items.

2. **#1120 — Cache hit problems persist**  
   *Author: pmsleepcheck* | [Link](https://github.com/Hmbown/CodeWhale/issues/1120)  
   The longstanding input cache miss rate bug may not be fully resolved. The reporter questions whether fixes landed in v0.8.17, suggesting the community is still seeing lower cache hit ratios after modifications.

3. **#683 — Forcing non-English reasoning chains**  
   *Author: YaYII* | [Link](https://github.com/Hmbown/CodeWhale/issues/683)  
   A recurring pain point: the model's *thinking* output remains English even when the interface language is set to Chinese. Users note competitors achieve native-language reasoning with the same DeepSeek models, indicating a prompt or pipeline issue.

4. **#759 — First-time initialization and config failures**  
   *Author: anyiba* | [Link](https://github.com/Hmbown/CodeWhale/issues/759)  
   Two critical onboarding defects: no API key setup guidance on first launch, and non-functional arrow keys in the settings menu. This directly impacts new user adoption.

5. **#861 — Thinking block collapse / freeze / truncation**  
   *Author: ZhouChaunge* | [Link](https://github.com/Hmbown/CodeWhale/issues/861)  
   A family of related UI defects where reasoning blocks either freeze with a live spinner, get silently truncated to 4 lines, or disappear entirely during streaming. High priority for user trust in agent reasoning.

6. **#1186 — Typed persistent permission rules for exec policy**  
   *Author: greyfreedom* | [Link](https://github.com/Hmbown/CodeWhale/issues/1186)  
   Proposes scoped `allow`/`deny`/`ask` rules by tool name, command prefix, or workspace path — a foundational security layer. The community sees this as essential for safe multi-agent and sub-agent execution.

7. **#1812 — TUI freezes on Windows 11**  
   *Author: aboimpinto* | [Link](https://github.com/Hmbown/CodeWhale/issues/1812)  
   Intermittent complete UI unresponsiveness on Windows 11, with the process still alive. Two confirmed events with logs and thread-state analysis show this is a crossterm polling issue.

8. **#2766 — UI refactor for copy and popup usability**  
   *Author: mo-vic* | [Link](https://github.com/Hmbown/CodeWhale/issues/2766)  
   Output is difficult to copy, and confirmation pop-ups obscure the main interface while showing mostly useless information. A common ergonomic pain point.

9. **#1920 — Clipboard copy fails on non-wlroots Wayland**  
   *Author: NLD37BYs* | [Link](https://github.com/Hmbown/CodeWhale/issues/1920)  
   On compositors like niri (Arch Linux), selecting text and copying via mouse menu silently fails. Impacts Linux users outside the GNOME/KDE ecosystem.

10. **#3095 — Sub-agent fanout leaves TUI stuck in provider wait**  
    *Author: Hmbown* | [Link](https://github.com/Hmbown/CodeWhale/issues/3095)  
    The parent model launching multiple sub-agents can leave the TUI displaying `working … (waiting for model)` for minutes with no visibility into whether sub-agents are executing, queued, or starved. The fix involves a **launch gate** and **observable provider wait**.

## Key PR Progress

1. **#3106 — Queue interactive fanout behind a launch gate**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3106)  
   Adds a semaphore-based launch gate to `SubAgentManager`, bounding concurrent depth-1 sub-agents. Extra children spawn immediately but cards transition to a wait state with a "Pending Launch" label.

2. **#3104 — Observable provider wait with stall reason**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3104)  
   Replaces the generic `waiting for model` with a diagnostic status showing provider, model, idle seconds, and timeout budget. Includes fanout preflight checks and an incident log.

3. **#3103 — Emit interrupted sub-agent lifecycle event**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3103)  
   Fixes Issue #3080: API-timeout interruptions now emit `MailboxMessage::Interrupted`, so delegate/fanout cards and the Agents sidebar properly transition out of "Running" state.

4. **#3109 — Parallelize sequential KV draft checks**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3109)  
   Replaces serial `await hasFreshDraft(...)` in `for...of` loops with `Promise.all()` in `runPrReview`, `runTriage`, and `runStale` — expected to significantly reduce batch processing latency.

5. **#3112 — Refactor `apply_patch.rs` to eliminate duplicated execution**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3112)  
   Removes an `unreachable!` macro and duplicative result construction by unifying matching on `preflight.kind`, improving code quality and maintainability.

6. **#2986 — Harvest-credit close template + stewardship branch explanation**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/2986)  
   Formalizes the process for closing harvested PRs with contributor attribution, landed commit references, and tracking issue links. Improves contributor experience.

7. **#2486 — WhaleFlow cost tracking**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/2486)  
   Adds `tokens_used` and `cost_usd` fields to `SubAgentResult` for per-agent API cost display in WhaleFlow and the TUI agents pane. Currently blocked because sub-agent infrastructure does not relay usage data.

8. **#2865 — Modernize toward latest Claude Code**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/2865)  
   Large cleanup closing the gap with Claude Code across prompts, hooks, skills, agents, and UI. Requires human review due to the scope of behavioral changes.

9. **#2901 — Localize ToolFamily labels (10 MessageIds)**  
   [Link](https://github.com/Hmbown/CodeWhale/pull/2901)  
   Adds i18n for tool card headers, sidebar, and footer status lines across all 7 shipped locales. Part of the ongoing localization push.

10. **#3110 – #3114 — Test coverage improvements**  
    A series of small PRs adding missing unit tests for `ToolError::permission_denied`, `ToolError::not_available`, `optional_str`, and `update_version_from_env`. Signals a push toward better code quality before the v0.8.59 release.

## Feature Request Trends

1. **Sub-agent lifecycle observability** — Users need clear visibility into sub-agent status (queued, running, interrupted, pending launch) with recovery mechanisms.
2. **Provider fallback chains** — Automatic switching between providers on API failure (quota, 401, 429, 5xx) rather than manual `/provider` commands.
3. **Non-English reasoning chains** — The model's thinking output should match the configured language, not default to English.
4. **Pluggable tool registry** — Users want config.toml overrides for all built-in tools (`read_file`, `exec_shell`, etc.) and auto-discovery of plugin scripts.
5. **TUI quality-of-life** — Taskbar progress indicators, animated title spinners, configurable completion sounds, and better clipboard support across platforms.
6. **Universal Cancel/Pause/Resume** — A hook-based lifecycle layer (`PreToolUse` / `PostToolUse`) for rollback and state management across all action types.
7. **Vision model support** — Registration of vision-capable models for image input, offloading visual parsing to dedicated fast models.

## Developer Pain Points

- **Cache reliability remains fragile** — Users still report low cache hit ratios after project modifications despite previous fixes (Issue #1120).
- **Windows stability is a blocker** — The crossterm-based TUI freezes intermittently on Windows 11, making the tool unreliable on the second-largest desktop platform.
- **First-time setup is broken** — No guided API key setup and non-functional arrow keys in settings create a poor onboarding experience (Issue #759).
- **Thinking block UX is unreliable** — Reasoning output freezes, truncates silently, or disappears entirely, eroding trust in agent outputs (Issue #861).
- **Wayland clipboard fragmentation** — The tool only works on wlroots-based compositors, excluding users of niri, Sway, and other non-wlroots environments (Issue #1920).
- **Rebranding confusion** — The migration from `deepseek-tui` to `CodeWhale` continues to cause confusion, especially for users who auto-installed via `npm` (v0.8.58 release notes).

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*