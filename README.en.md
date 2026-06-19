<div align="center">

# GK1200 Service Manual Lookup Skill

**A lookup assistant for the Gaojin GK1200 (also called BX500 / BX1200 in the manual) motorcycle service manual**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent-Skill-d97757.svg)](SKILL.md)

**English** ·[简体中文](./README.md)

</div>

Ask about torque values, service intervals, fluid specs or removal/install steps in natural language, and the agent searches the manual to answer; vision-capable agents can also interpret the full-page diagrams — no more digging through a PDF for the right page.

## Features

This skill turns the entire GK1200 service manual into something an agent can query directly. It follows the standard skill format, so it is **not limited to Claude Code** — any agent that supports the skill mechanism can load and use it.

- **Common hard data built into a quick-reference table** — torque, service intervals, fluid specs, vehicle specs, spark plug, tire pressure, cylinder compression, electrical: answered instantly, no full-text search needed.
- **Details located via a topic index** — the full manual text is `grep`-able, and built-in topic keywords jump straight to the relevant section.
- **Diagrams served as full-page images on demand** — for disassembly or wiring diagrams, the matching full-page image (one per page, no fragments) is provided; vision-capable agents can interpret it directly.
- **Safety data listed from multiple sources** — when the manual gives inconsistent torque values for the same part across chapters, all sources are listed side by side with the original book flagged as authoritative.

## Repository layout

```
gk1200-repair/
├─ SKILL.md     # skill entry: trigger description + quick-reference table + topic index + image rules
├─ manual.md    # full manual text, image links point to full-page images
└─ pages/       # 184 full-page images (WebP)
```

## Installation

Clone or copy this repository into your agent's user-level skill directory so it ends up at `<skills>/gk1200-repair/`, then restart the agent (start a new session) to load it and just ask a question to trigger it.

Using Claude Code as an example, the skill directory is:

| Platform | Skill directory |
| --- | --- |
| macOS / Linux | `~/.claude/skills/gk1200-repair/` |
| Windows | `%USERPROFILE%\.claude\skills\gk1200-repair\` |

> [!NOTE]
> The skill always references its own files relative to the skill base directory, so it works no matter where you clone it; for other skill-capable agents, place it in that agent's designated skill directory.

## Usage examples

- What's the rear axle nut torque on the GK1200?
- How often do I change the oil, and how much?
- What spark plug model and gap does it use?
- How do I remove the throttle body?

> [!TIP]
> The last question returns the removal steps plus the matching full-page image; vision-capable agents will interpret the parts, disassembly order and wiring directly.

## Viewing images: works for both kinds of agent

- **Agents without vision / yourself** — the skill gives the full-page image path and the caption text next to it, which you open yourself.
- **Vision-capable agents** — read the full-page image directly and interpret it against your question (parts, disassembly order, wiring, etc.).

> [!WARNING]
> Torque values are safety data. For the same part this manual gives **inconsistent** torque values across chapters; the skill lists all source values side by side and recommends treating the original book as authoritative and choosing the more conservative value. For actual work, always treat the printed / official manual as the final authority.

---

<div align="center">
Released under the <a href="LICENSE">MIT</a> license
</div>
