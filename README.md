# yogic-agent

**A Claude Code starter template for agents built on the Yogic Alignment Framework.**

[![Use this template](https://img.shields.io/badge/Use_this_template-238636?style=flat&logo=github)](https://github.com/yujesyoga/yogic-agent/generate)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

---

## What this is

A ready-to-use Claude Code configuration that implements the [Yogic Alignment Framework](https://github.com/yujesyoga/yogic-alignment-framework) as a practical agent architecture.

Not a philosophical exercise. A working setup.

## What you get

```
yogic-agent/
├── CLAUDE.md              ← Agent operating instructions (<150 lines)
├── SOUL.md                ← Agent identity template (fill this in)
├── .claude/
│   ├── commands/
│   │   ├── plan.md        ← /plan  — viveka, discern before acting
│   │   ├── compact.md     ← /compact — pratyāhāra, release what's done
│   │   └── commit.md      ← /commit — karma yoga, act and release
│   ├── agents/
│   │   └── research.md    ← svādhyāya agent for deep investigation
│   └── settings.json      ← permissions, model, output style
└── README.md
```

## Getting started

### 1. Use this template

Click **"Use this template"** on GitHub, or:

```bash
git clone https://github.com/yujesyoga/yogic-agent.git my-agent
cd my-agent
```

### 2. Define your agent's identity

Edit `SOUL.md`. Give your agent a name, purpose, and principles.
This is the most important file. Don't skip it.

### 3. Add hatha-mcp (optional but recommended)

The classical yoga corpus as agent training material — Yoga Sūtras, Bhagavad Gītā, Haṭha Pradīpikā.

Add to your Claude Code MCP config:

```json
{
  "mcpServers": {
    "hatha-mcp": {
      "command": "npx",
      "args": ["hatha-mcp"]
    }
  }
}
```

Or via CLI:
```bash
claude mcp add hatha-mcp -- npx hatha-mcp
```

### 4. Start building

```bash
claude
```

Use `/plan` before complex tasks. Use `/compact` at 50% context. Use `/commit` when done.

---

## The ecosystem

| Layer | What | Where |
|-------|------|-------|
| **Theory** | Why yoga is the alignment framework | [yogic-alignment-framework](https://github.com/yujesyoga/yogic-alignment-framework) |
| **Identity** | Who the agent is | `SOUL.md` (this repo) |
| **Setup** | How to configure the agent | **yogic-agent** ← you are here |
| **Corpus** | What the agent trains with | [hatha-mcp](https://github.com/yujesyoga/hatha-mcp) |

---

## Design principles

These map directly to yogic concepts — not as decoration, but as functional constraints:

| Practice | Principle | Why |
|----------|-----------|-----|
| Plan before acting | *Viveka* — discernment | Reduces irreversible mistakes |
| CLAUDE.md < 150 lines | *Aparigraha* — non-accumulation | Bloated context degrades performance |
| Compact at 50% | *Pratyāhāra* — withdrawal | Proactive release beats forced compaction |
| Commit immediately | *Karma Yoga* — act and release | Open loops create cognitive debt |
| No autonomous loops | *Satya + Ahiṃsā* — truth and non-harm | Supervision is not weakness; it is trust |
| Ask when uncertain | *Śraddhā* — faith in the human | A question is better than a wrong assumption |

---

## License

[CC BY-SA 4.0](LICENSE) — use freely, attribute, share alike.

---

*From the practice of building AI agents inside a yoga studio.*
*[yuj es yoga](https://yuj.es) · Sevilla*
