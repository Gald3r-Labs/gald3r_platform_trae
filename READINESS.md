# gald3r Readiness Report — TRAE (ByteDance AI-native IDE)

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Strong (one gap).** TRAE is an AI-native IDE with first-class
rules, custom agents, and the Agent Skills (`SKILL.md`) open standard. gald3r's rule, agent,
skill, and MCP layers install natively with little-to-no translation; commands map only
partially, and hooks have no native host.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ⚠️ | Built-in Spec Kit workflow commands (`/specify` → `/plan` → `/tasks` → `/implement`) + `@agent-name` routing to custom agents | No user-defined slash-command file primitive (no `.trae/commands/`) — gald3r's `@g-*` set must surface via rules/skills or custom agents |
| **R** | Rules | ✅ | `.trae/rules/` — `project_rules.md` + `user_rules.md`, loaded at init, invokable with `#rulename` (global `~/.trae/rules/` too) | None — gald3r rules install as TRAE's native persistent-instruction layer |
| **A** | Agents | ✅ | User-created Custom Agents (own system prompt, toolset, attached MCP servers) via `@agent-name`; one-click import; plus SOLO autonomous mode | None — gald3r's `g-agnt-*` roles map cleanly to custom agents |
| **S** | Skills | ✅ | `.trae/skills/<name>/SKILL.md` — the Agent Skills open standard, lazy-discovery; Skills Marketplace + `.md`/`.zip` upload | None — gald3r skills install directly with zero format translation |
| **H** | Hooks | ❌ | — | No lifecycle/event script hooks (session-start / pre-tool / pre-commit); only SOLO time-based scheduled tasks, which is scheduling, not event hooks |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Full Model Context Protocol client support (landed in
v1.3.0). Add servers via stdio or SSE, with a built-in MCP Marketplace and per-agent scoping
(`Builder with MCP`); gald3r's MCP backend attaches natively to custom agents.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Spec Kit spec-driven workflow (`/constitution` → `/implement`, Markdown artifacts) | ⚙️ needs customization | Adoptable as a structured planning pipeline feeding gald3r tasks |
| Skills Marketplace + `agentskills.io` registry (uploadable `.md`/`.zip`) | ✅ present | A real distribution channel for gald3r skill bundles |
| One-click custom-agent import/export (shareable config bundles) | ✅ present | Package gald3r `g-agnt-*` roles as importable agents |
| SOLO Mode (autonomous planning→deployment) + scheduled tasks | ⚙️ needs customization | A standing autonomous surface; scheduled tasks approximate (but aren't) hooks |
| Multi-model (Doubao-Seed-2.0-Code free, Claude, GPT, Gemini; custom) | ✅ present | Maps to gald3r's role-based model orchestration |
| Machine-readable output emit (JSON/structured) | ➖ n.a. | None documented — Spec Kit artifacts are Markdown only |

## The honest ceiling

gald3r adapts to this platform the way any third-party layer must — by mapping our commands, rules, agents, skills, and hooks onto whatever extension points the platform happens to expose. Where those points exist, the fit is clean. Where they don't, adaptation can only *approximate* the real thing — a stand-in that covers the common case but not the edges.

That isn't a knock on the platform. It's the ceiling of bolting *any* framework onto a surface that was never built to host it.

Full functional parity isn't something we can reach from the outside. It lives in the native build — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where commands, rules, agents, skills, and hooks aren't *adapted* to the platform, they *are* the platform.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
