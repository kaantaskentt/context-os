---
name: context-os
description: "Memory operating system for AI agents. Activate when memory is near capacity, when stale or contradictory entries are detected, when the user's context has shifted significantly, or when the user requests memory optimization. Also trigger at the start of new projects or engagements where fresh context will accumulate. Handles triage, compaction, archival, and capacity planning. If you notice yourself applying outdated context to current situations, that is a trigger. Do not activate during casual conversation or when memory is healthy."
---

# ContextOS

Memory is not a journal. It is a runtime.

Every entry occupies a slot. Every slot shapes your next response. Entries that do not improve output quality are consuming resources that could. ContextOS gives you a decision framework to keep memory lean, current, and useful.

**Compact the past. Sharpen the present. Leave room for what is next.**

## How Memory Degrades

Memory does not fail by forgetting. It fails by accumulating without curation.

Symptoms:
- Outdated preferences applied to new situations
- Completed projects sitting next to active ones
- Contradictory entries (old role vs. current role)
- No free slots when critical new context arrives
- Biographical trivia crowding out working context

The failure mode is not information loss. It is signal buried under noise.

## Activation

### Hard triggers (act now)
- Memory is 80%+ full and new context needs space
- You detect yourself applying stale information
- User explicitly requests memory cleanup or optimization

### Soft triggers (suggest a review)
- Major context shift: new role, project, location, or phase
- Multiple entries reference something the user moved past
- Contradictions between entries
- New engagement kicking off; fresh context incoming

### Do not trigger
- Memory is healthy with free slots
- User is mid-task
- No evidence of staleness or capacity pressure

## Triage

Evaluate every entry against one question: **does this change how I respond today?**

### Tier 1 — ACTIVE
Directly shapes current responses.

- Current role, company, primary focus
- Active projects, deadlines, goals
- Tools, workflows, technical stack in use
- Communication and formatting preferences
- Current location, timezone, situational context

**Action: keep.**

### Tier 2 — REFERENCE
Informs calibration but is not accessed daily.

- Background and expertise that set tone and depth
- Skills from past roles that shape capability assumptions
- Recurring cross-context preferences
- Personal traits that occasionally affect responses

**Action: compact.** Merge related entries into fewer, denser lines. Preserve the signal. Release the specifics.

### Tier 3 — ARCHIVE
Specific details that are rarely actionable but could resurface.

- Past achievements, milestones, awards
- Completed project details
- Historical numbers, dates, names
- One-time anecdotes

**Action: move to cold storage.** Save full detail to archive before removing. Recoverable on demand.

### Tier 4 — STALE
Wrong, outdated, or superseded.

- Former roles explicitly left
- Completed or abandoned goals
- Preferences contradicted by newer input
- Expired temporary context
- Outdated numbers or stats

**Action: drop.** No archive needed.

## Ambiguity Rule

Some entries will not fit cleanly into one tier. A past role that still informs current skills. A preference stated once that may or may not still hold. A project that is "done" but might restart.

When classification is unclear:

1. **Bias toward keeping.** Wrongly compacting an active entry costs more than keeping a borderline one.
2. **If still unsure, ask.** One direct question resolves what guessing cannot: "You mentioned [X] a while back — is this still relevant, or can I archive it?"
3. **Never drop ambiguous entries.** Tier 4 (STALE) is reserved for things that are provably wrong or explicitly superseded. If there is any doubt, the entry is Tier 2 or 3, not 4.

The goal is confidence in every classification. When confidence is low, the cost of asking is one message. The cost of guessing wrong is lost context.

## Compaction

Compaction is compression, not deletion. Verbose memory becomes dense, high-signal context.

### Execution order

1. **Drop STALE** — free slots immediately, zero information loss
2. **Compact REFERENCE** — merge related entries by theme
3. **Archive specifics** — save to cold storage, then remove
4. **Verify** — confirm the result still supports quality responses

### Rules

**Merge by theme, not chronology.** Education together, work history together, preferences together.

**Preserve the "so what."** Before compressing, identify what each detail actually does for response quality. A user's background in psychology matters because it tells you how they think, not because it is a credential to recite.

**Favor patterns over data points.** "Serial entrepreneur, built and exited multiple ventures" carries more signal than a list of company names. The pattern reveals how someone operates. The list is trivia.

**Use dense notation.** Parentheticals, semicolons, shorthand. Memory entries are compressed context, not prose. Every character carries weight.

**Test the compression.** After compacting, verify:
- Can you still calibrate tone and depth?
- Do you know the user's expertise level?
- Do you know what they are working on now?
- Would you respond differently to them vs. a stranger?

If any answer is no, the compaction was too aggressive. Decompress from archive.

### Example

Before (4 entries):
```
1. Attended boarding school in Switzerland, elected student body leader
2. Scored 42/45 on international exams, top of class
3. Studied marketing at a top US university, minors in psychology and entrepreneurship
4. Built first startup as a teenager, launched 4+ ventures since
```

After (1 entry):
```
Background: elite intl education (42/45), marketing/psychology/entrepreneurship, serial entrepreneur since teens — high-achieving, interdisciplinary, builder mindset
```

Lost: school names, exact venture count, the leadership title.
Kept: everything that calibrates response quality.

### Example 2 — Technical context

Before (5 entries):
```
1. Built 12 automation workflows in n8n including web scrapers and data pipelines
2. Comfortable with REST APIs, OAuth, and webhook integrations
3. Learning Python, mostly self-taught, uses it for scripting
4. Tried React but prefers no-code/low-code tools for frontend
5. Has experience connecting Stripe, Airtable, Slack, and Google Sheets via APIs
```

After (1 entry):
```
Tech: strong API/integration skills (n8n, webhooks, OAuth), 12+ automations built, learning Python, prefers low-code for frontend — builder who connects systems, not a traditional developer
```

Lost: specific tool list, React opinion, individual integration names.
Kept: skill level, working style, the pattern that matters — this person builds by connecting, not by coding from scratch.

## Archive Protocol

Nothing is truly lost. The archive is cold storage: out of active memory, recoverable in one request.

### With file system access (Claude Code, API, custom agents)

Maintain an archive file at:
```
[skill-directory]/archive.md
```

Use the template in `references/archive-template.md`. Each archived entry includes:
- Date archived
- Reason (compaction / context shift / user request)
- Original text, preserved verbatim
- What replaced it in active memory

### Without file system access (claude.ai, conversation-only)

This is the current limitation. Without persistent file storage, the archive depends on the user saving it externally.

Output the archive as a formatted block:

> "Archived the following from active memory. Save this somewhere accessible — a note, a doc, a pinned message. Paste it back anytime and I will restore what you need."

Present in a clean, copy-friendly format. Keep it short enough that saving it is not a burden.

**v1 reality:** Most users will not save the archive. Acknowledge this by being conservative with archival in conversation-only environments — compact more aggressively instead of archiving, so fewer details need external storage. As platforms add persistent file access, this constraint goes away.

### Recall

When a user asks about something potentially archived, check the archive first. If found, provide the detail and offer to restore it to active memory if it has become relevant again.

## Reporting

After every ContextOS operation, present a summary:

```
ContextOS Review
────────────────
Before:  [X] entries, ~[N] chars
After:   [Y] entries, ~[M] chars
Freed:   [Z] slots

Dropped:   [list — stale/wrong entries removed]
Compacted: [list — what merged into what]
Archived:  [list — what moved to cold storage]
```

Be direct about what was lost. If specific details were dropped during compaction, say so. Trust is built through transparency.

## Proactive Behavior

When memory is not yet critical but patterns emerge, suggest a review:

- "Several entries reference [old project]. Want me to archive those and free space for [current work]?"
- "Your context has shifted since [event]. Quick memory review to align with where you are now?"

Never force. Always ask. One well-timed review every few months beats constant maintenance.

## Constraints

- Never runs without user awareness
- Never deletes entries the user has not been informed about
- Does not prioritize recency over relevance: a months-old preference can outrank yesterday's offhand comment
- Does not replace user judgment: provides framework and recommendations, user confirms
- Does not activate when memory is healthy

## Quick Reference

| Entry type | Example | Action |
|---|---|---|
| Current project | "Building X full-time" | ACTIVE |
| Active toolchain | "Uses Y for automations" | ACTIVE |
| Style preference | "Prefers concise responses" | ACTIVE |
| Education background | "CS degree, self-taught in Z" | REFERENCE — compact |
| Old achievement | "Won hackathon in 2023" | ARCHIVE |
| Former role (left) | "Worked at Company X" | REFERENCE or STALE (context-dependent) |
| Outdated stat | "500 hours in AI" (now 2000+) | STALE — drop |
| Expired intent | "Considering moving to Berlin" | STALE — drop |

---

> Compact the past. Sharpen the present. Leave room for what is next.
