# ContextOS

> Compact the past. Sharpen the present. Leave room for what is next.

A memory operating system for AI agents. Teaches models to manage their memory like a strategist, not a hoarder.

## The Problem

AI memory degrades silently. It does not forget — it accumulates. Old preferences override new ones. Completed projects sit next to active ones. Context from six months ago gets applied to today's problems. The result: your AI remembers everything and understands nothing about where you are right now.

## What This Does

ContextOS is an [Agent Skill](https://www.anthropic.com/news/skills) that gives any AI model a structured framework for memory management:

- **Triage** — classify every memory entry as Active, Reference, Archive, or Stale
- **Compact** — compress verbose biographical/historical entries into dense, high-signal context
- **Archive** — move specific details to cold storage (recoverable anytime)
- **Plan** — maintain free capacity for incoming context

No code. No scripts. Pure decision logic in a `SKILL.md` that any model can follow.

## Install

### Claude Code
```bash
# Clone and copy to your skills directory
git clone https://github.com/kaantaskentt/context-os.git
cp -r context-os ~/.claude/skills/
```

Or install via the plugin marketplace once indexed.

### Claude.ai
Upload the `SKILL.md` as a custom skill in your project settings.

### Other agents (Codex CLI, ChatGPT, custom)
The `SKILL.md` follows the open [Agent Skills standard](https://agentskills.io). Drop it into your agent's skill directory.

## Usage

The skill activates automatically when:
- Memory is near capacity (80%+ slots used)
- Stale or contradictory entries are detected
- A major context shift occurs (new role, project, phase)
- You ask: "clean up my memory" / "optimize what you know about me"

Or trigger it manually at the start of any new project to ensure clean context.

## How It Works

```
TRIGGER → TRIAGE → ACTION → RESULT

[capacity]     [active]      [keep]        fewer entries
[stale data]   [reference]   [compact]     sharper context
[user request] [archive]     [cold store]  nothing truly lost
[context shift][stale]       [drop]        room for what is next
```

See the full decision framework in [`SKILL.md`](./SKILL.md).

## File Structure

```
context-os/
├── SKILL.md                        # The skill — triage, compaction, archival logic
└── references/
    └── archive-template.md         # Template for cold storage format
```

## Known Limitations

- **claude.ai (conversation-only):** No persistent file system means the archive relies on the user saving it externally. The skill compensates by favoring compaction over archival in these environments. This constraint disappears as platforms add persistent storage.
- **Memory slot limits vary by platform.** The 80% trigger threshold assumes ~30 slots. Adjust if your platform differs.

## Philosophy

Memory is not storage. It is context. A colleague who remembers your university grades but forgets your current project is not helpful — they are noisy. ContextOS applies that same logic to AI: keep what matters now, compress what shaped you, archive what might return, drop what is dead.

## License

MIT

---

Built by [Kaan](https://github.com/kaantaskentt) — [1% Session](https://1percentsession.com)
