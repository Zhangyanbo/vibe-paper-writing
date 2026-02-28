# Vibe Paper Writing

An Agent Skill that brings the fluid, conversational style of **Vibe Coding** to academic paper writing. Send it a chat log, email thread, or a voice-note dump—and it integrates the ideas into your LaTeX paper with proper scholarly prose, automatically.

Compatible with **Cursor**, **Claude Code**, and **Codex (OpenAI)**.

---

## What It Does

Traditional academic writing is a slow, manual process. Vibe Paper Writing breaks that cycle. You talk; the agent writes. Specifically, it handles:

- **Chat logs & email threads** — Extracts only the ideas you explicitly endorsed, translates conversational language into academic prose, and flags anything ambiguous for your review.
- **Personal documents & notes** — Incorporates your drafts, memos, or bullet-point notes into the appropriate section of the paper.
- **Citations & references** — Integrates a new paper or finding, places it in the right location, and updates the bibliography.
- **Mathematical notation** — Writes or audits LaTeX math expressions against the paper's established symbol conventions.
- **Paper review** — Checks the full paper for internal contradictions, broken references, privacy issues, and consistency of claims.
- **Writing improvement** — Linearizes logic, enforces abbreviation policies, and moves verbose passages to an appendix.

After every substantive edit the skill compiles the LaTeX source and reports the result, so you never ship a broken PDF.

---

## Installation

### Cursor

Skills are loaded automatically from `~/.cursor/skills/` (global) or `.cursor/skills/` (project-level).

```bash
git clone https://github.com/Zhangyanbo/vibe-paper-writing ~/.cursor/skills/vibe-paper-writing
```

Then restart Cursor. The skill is discovered automatically; you can also invoke it explicitly by typing `/vibe-paper-writing` in the Agent chat.

### Claude Code

Skills are loaded from `~/.claude/skills/` (global) or `.claude/skills/` (project-level).

```bash
git clone https://github.com/Zhangyanbo/vibe-paper-writing ~/.claude/skills/vibe-paper-writing
```

### Codex (OpenAI)

Skills are loaded from `~/.agents/skills/` (user-level) or `.agents/skills/` (repo-level).

```bash
git clone https://github.com/Zhangyanbo/vibe-paper-writing ~/.agents/skills/vibe-paper-writing
```

Alternatively, use the built-in skill installer inside Codex:

```
$skill-installer install https://github.com/Zhangyanbo/vibe-paper-writing
```

---

## Usage

Once installed, just describe what you want in natural language:

> "Here's the email thread from my advisor. Incorporate the feedback on Section 3 into the paper."

> "Add the Smith et al. 2024 paper on attention mechanisms as a citation in the related work section."

> "Review the whole paper for contradictions and broken references."

> "This is my rough voice-note from yesterday. Turn it into the conclusion section."

The agent identifies the task type, loads the appropriate guidance, and produces the updated `.tex` section along with a brief explanation of what changed and why.

---

## Skill Structure

```
vibe-paper-writing/
├── SKILL.md                  # Skill entry point (metadata + universal rules)
├── tasks/
│   ├── chat-and-email.md     # Endorsement-aware chat/email integration
│   ├── user-documents.md     # Personal drafts and notes
│   ├── citations.md          # Reference insertion
│   ├── math-notation.md      # LaTeX math
│   ├── paper-review.md       # Full-paper consistency check
│   ├── writing-improvement.md
│   └── latex-compilation.md  # Compile-and-fix workflow
└── resources/
    └── math_commands.tex     # Shared math macro reference
```

---

## Design Philosophy

The core challenge in academic writing assistance is not mechanical insertion—it is *intelligent integration*. This skill is built around three principles:

1. **Endorsement awareness.** Conversations contain many voices and tentative ideas. The skill incorporates only what you have explicitly agreed with or instructed it to use—never hallucinated positions.
2. **Voice preservation.** The paper's established register ("we", epistemic hedges like "suggests" and "indicates", subheading density) is preserved across all edits.
3. **Compilation-gated output.** No edit is reported as complete until the LaTeX compiles cleanly.

---

## License

MIT — see [LICENSE](LICENSE).
