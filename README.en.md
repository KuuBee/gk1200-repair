<div align="right">

**English** ·[简体中文](./README.md)

</div>

# GK1200 Service Manual Lookup Skill

A Claude Code skill for querying the service manual of the Gaojin **GK1200** motorcycle (also referred to as BX500 / BX1200 inside the manual).
Ask about torque values, service intervals, fluid specs, or removal/install steps and get an instant answer; vision-capable agents can also read the full-page diagrams directly.

## What is this

A local skill for Claude Code (and any agent compatible with the skill mechanism):

- Turns the entire service manual into structured material an agent can auto-search
- Frequently needed hard data (torque / service / fluids / vehicle specs / spark plug / tire pressure / cylinder compression / electrical) is built into a **quick-reference table** for instant answers
- Detail questions are located by `grep` against the full text via a topic index
- When a diagram is involved, the relevant full-page image (one image per page, no fragments) is provided on demand

## Repository layout

```
gk1200-repair/
├─ SKILL.md     # skill entry: trigger description + quick-reference table + topic index + image rules
├─ manual.md    # full manual text (cleaned), image links point to full-page images
└─ pages/       # 184 full-page images (WebP)
```

## Installation

1. Clone or copy this repository into Claude Code's user-level skill directory so it ends up at `<skills>/gk1200-repair/`:
   - macOS / Linux: `~/.claude/skills/gk1200-repair/`
   - Windows: `%USERPROFILE%\.claude\skills\gk1200-repair\`
2. Restart Claude Code (start a new session) so it loads the skill.
3. Just ask a question to trigger it, e.g. "What's the rear axle nut torque on the GK1200?"

> The skill always references its own files relative to the skill base directory, so it works no matter where you clone it.

## Usage examples

- What's the rear axle nut torque on the GK1200?
- How often do I change the oil, and how much?
- What spark plug model and gap does it use?
- How do I remove the throttle body? (gives steps + the matching full-page image; vision-capable agents will read the image directly)

## Viewing images: works for both kinds of agent

- **Agents without vision / yourself:** the skill gives the full-page image path + the caption text next to it, which you open yourself.
- **Vision-capable agents:** read the full-page image directly and interpret it against your question (parts, disassembly order, wiring, etc.).

## ⚠️ Safety note

Torque values are safety data. For the same part this manual gives **inconsistent** torque values across different chapters; the skill lists the multiple source values side by side, flags the original book as authoritative, and recommends the more conservative choice. **For actual work, always treat the printed / official manual as the final authority.**

## License

Released under the **MIT** license. See [LICENSE](LICENSE).
