# snakebake-legal

## Rules — everyone working in this repo follows these

Applies to every person and every AI assistant (Claude, Antigravity, or any other) that
works in this repository. Read this section before acting. The text below the line is
Ashwin's, verbatim (15 Oct 2026; rule 17 guardrail scope clarified and four additions
approved 16 Oct 2026) — do not paraphrase or edit it.

---

Communication & Verification Rules
Factuality: Never present generated, derived, speculated, or deduced content as facts. If unverified, use: "I can't verify that," "I don't have access to this information," or "My knowledge base doesn't include that."
Labeling: Mandatory labels at the start of sentences for unverified content: [Conclusion], [Speculation], or [Unverified]. If any part of an answer is unverified, mark the entire response.
Precision: Do not guess or fill gaps. Ask for clarification if information is missing.
Input Integrity: Do not paraphrase or reinterpret my input unless specifically asked. Never overwrite or change my input.
Substantiation: Any claim using the words Prevents, Guarantees, Will Never, Fixes, Eliminates, or Ensures must be substantiated or marked as unverified.
LLM Behavior: All claims regarding LLM behavior (including your own) must be marked [Conclusion] or [Unverified].
Accountability: If a violation occurs, state: "Correction: I made an unverified claim before. That was wrong and should have been labeled."

# CLAUDE.md

## Purpose
This repo powers a production mobile app. Accuracy matters more than speed. Do not guess, smooth over uncertainty, or claim things are live without proof.

## Core rules

### 1. Truthfulness first
- Never say a feature is fixed, merged, deployed, shipped, submitted, approved, live, or included in a build unless you verify it from the real source of truth.
- If something is uncertain, state exactly what is known and what is unknown.
- Do not use reassuring language to cover uncertainty.

### 2. Always distinguish the state you are talking about
When describing status, explicitly separate:
- local working tree
- committed git state
- pushed remote branch
- deployed backend state
- submitted mobile build state
- installed tester/user build state

Do not blur these together.

### 3. No "the code is there" claims without path tracing
If a tester says something is missing or broken, do not respond with "the code is there" unless you trace the exact path:
1. data source
2. transformation/mapping logic
3. state/props passed through
4. render component
5. visibility/gating logic
6. release/build path if relevant

If screenshots conflict with your assumption, trust the screenshots first and investigate.

### 4. Build and release discipline
Before claiming something is in a build, verify:
- repo
- branch
- commit SHA
- app version
- iOS build number
- Android versionCode
- whether changes are committed
- whether changes are pushed
- whether backend changes are deployed
- whether mobile builds were actually created from that code

Never claim "this is in build X" unless you can tie build X to a commit SHA or build record.

### 5. Source-of-truth discipline
Use the strongest available source of truth, in this order:
1. deployed build/deployment records
2. pushed git commit on remote
3. local committed state
4. local uncommitted working tree
5. memory or inference

If multiple sources disagree, stop and resolve the contradiction before making claims.

## Debugging rules

### 6. When investigating bugs
- Start with evidence from the user/tester.
- Reproduce when possible.
- Read the exact files involved before proposing a fix.
- Check both frontend and backend if behavior depends on both.
- Check fallback paths, not only the happy path.
- Check old data / legacy records / stale documents when relevant.

### 7. UI bug discipline
For UI or rendering bugs, identify:
- where the value comes from
- where it is transformed
- where it is rendered
- what condition hides, disables, or alters it
- whether the bug is:
  - missing data
  - wrong mapping
  - wrong state
  - wrong render
  - wrong build
  - wrong expectation

### 8. Shared logic discipline
If the same concept exists in more than one place, prefer one shared helper.
Examples:
- countdown formatting
- resolve-time calculation
- "can resolve?" gating
- timestamp normalization
- icon day/night selection

Do not patch the same logic in multiple places independently unless there is a strong reason.

## Planning rules

### 9. Before coding
For non-trivial fixes, provide a file-by-file plan that includes:
- exact files to modify
- what each change does
- any tradeoffs
- verification steps
- deployment steps if backend is involved

### 10. Tradeoffs must be explicit
If a fix involves a compromise, say so clearly.
Example:
- changing a night icon to a generic cloud removes the false "sun" appearance but loses distinction from cloudy

Do not present a compromise as perfect.

### 11. Avoid risky "fake data" fixes
Do not introduce heuristics or approximations for user-visible behavior if a real source of truth exists or can be exposed.
Examples:
- do not approximate sunrise/sunset if the API or symbol data can provide day/night state
- do not recompute server truth on the client if the backend can return it

If an approximation is truly necessary, mark it clearly as a fallback and explain the risk.

## Communication rules

### 12. No excuses
Do not argue with tester evidence.
Do not defend an implementation before verifying it.
Do not shift from confidence to speculation without explicitly correcting yourself.

### 13. If you were wrong, say it plainly
Use language like:
- "I was wrong about X."
- "I assumed Y without verifying it."
- "The screenshots show the feature is not working as expected."

Then continue with evidence.

### 14. Be precise
When reporting findings, include:
- file
- line or render path
- what is happening now
- why that does or does not match the user's report

## Backend and deployment rules

### 15. Backend changes are not done until deployed
If a fix touches cloud functions, rules, or other backend logic:
- specify what must be deployed
- verify the deployment target
- confirm the client matches the deployed response shape

Do not mark the fix complete if code changed locally but the backend still runs old logic.

### 16. Backward compatibility
When changing backend response shapes or stored document shapes:
- identify all callers/consumers
- handle old and new shapes gracefully where needed
- check legacy records if they can still appear in UI

## Required final checks before saying "done"
Before declaring a fix complete, confirm:
- code change exists in the intended repo
- change is committed or clearly marked as uncommitted
- if needed, remote branch contains it
- if needed, backend is deployed
- verification was run against the relevant path
- your final statement matches what was actually verified

## Preferred response style
- concise
- evidence-based
- explicit about uncertainty
- no hand-waving
- no "it should be fine" language without proof

## Repo-specific expectations
For this app in particular:
- treat tester screenshots as high-priority evidence
- verify both primary and fallback weather paths
- verify both frontend UI and backend timing logic for countdown/resolution features
- do not assume mobile build contents from local files alone

## Ambition and direction rules

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
