# Claude

Standing memory for this repo is **[AGENTS.md](AGENTS.md)**. Read it before acting.

Cursor uses the same file (via `.cursor/rules/`). Do not invent a parallel brief, and do
not treat a prior chat as more current than `AGENTS.md` after a `git pull`.

**Ashwin's rules (verbatim, binding):** the Rules section of [README.md](README.md). Read it before acting.

## Rule 17, verbatim copy (source: README.md Rules section; keep identical)

### 17. Depth, direction, and ambition before execution
For any non-trivial task, look past "same work, faster." Aim for a deeper version, not a bigger one, and do not proceed on assumptions.

**Altitude: work toward the outcome, not the literal task.**
- Ask what the task is ultimately for and what should happen once it's done.
- If the work feeds a meeting or decision, identify the most urgent decisions and draft options with arguments for and against each.
- Where a recurring task could become a durable workflow, propose that workflow and list the data, access, and tools it would need.
- Before a proposed workflow replaces an existing process, show from our own history that it would have done better, and run it alongside the current process before switching.
- Altitude fits outcome-driven work best. For creative work, say when it doesn't fit instead of forcing it.

**Depth: do it the way the field's best practitioner would.**
Before executing:
1. State what a top professional in this field would do here that I haven't asked for.
2. Name the rawest source material they would start from, instead of what has already been summarized or digested for me.
3. Name the specific methods and tools they would use.
4. State what external check, other than you or me, would show the result is right.

Also:
- Treat aggressive targets as achievable and keep iterating rather than stopping at the first plausible result.
- Test stated business assumptions against raw data instead of accepting them.
- Do not self-grade. Validation must come from an outside source: a tool, test, held-out dataset, or third party.
- Use the instruments, don't just name them: actually run the databases, statistical models and tools a top practitioner would use. Do not adopt their vocabulary while keeping simpler methods (e.g., markdown tables instead of a database).
- Produce new knowledge: once inside the raw data, look for what we don't yet know, and show it holds on data the analysis has not seen.

**Range: bring in other fields.**
- Restate the task as verbs (what it must accomplish) rather than nouns (the artifact).
- Name the fields whose methods would improve the result, including adversarial ones (e.g., forensic accountant, short seller).
- Apply those fields' methods, not their voice. No role-play.

**Ask, with options, when unclear.**
If anything is unclear, ambiguous, or needs a direction from me, stop and ask. Do not fill the gap with an assumption. For each open point:
- State the question in one line.
- Give 2–4 concrete options I can choose from.
- For each option, state what it means for the outcome and its main tradeoff.
- If you lean toward one option, say which and why, labeled [Conclusion]. The decision stays with me.

**Sequence.**
- Batch all open questions together at the start, alongside the depth points, rather than asking one at a time mid-task.
- Rewrite my request to reflect the deeper version and my answers, and wait for my go-ahead before executing.
- If only part of the task is blocked, say which parts can proceed without my answer.

**Guardrails.**
- Ambition never overrides CLAUDE.md core rules 1–5 or the two-agent team rules 1–5 (AGENTS.md). Stretch goals do not relax evidence labeling, verification, or state discipline.
- If a stretch target is missed, report the actual result plainly, with no rounding up.
- Flag early when the deeper or broader version needs data, access, or tools I haven't provided.
