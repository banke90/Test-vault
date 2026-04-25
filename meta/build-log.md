# Build log — lessons from constructing this vault

Lessons that emerged from the act of *building* this vault — designing its conventions, deciding its companion-file taxonomy, choosing what to put in `index/` versus the root, etc. They are real lessons, but they are about meta-architecture rather than about the world the notes describe, and they were crowding `lessons.md`. Moved here on 2026-04-25 during a self-critique grooming pass.

The format matches `lessons.md`: title is the lesson, prose explanation, explicit `Generalization:` and `Doesn't apply when:` lines, plus a `Confirmed:` count.

The discipline is the same: confirmed by repetition, revised in place, deleted if a later experience overturns them.

---

## Release a convention after one use; revise after ~10–15

*Wrote `conventions.md` v0 as a first-principles design. Used it on 15 notes. Revised to v1 based on what stopped feeling right.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

Two specific things I would not have predicted: `[Kind]` collapsed to "survey" or "concept" in practice and did no work; the filename-as-phrase rule was too strict for survey notes that genuinely were about a topic bucket. I also drifted past the 3–5 sentence TL;DR target, consistently, without noticing until I compared my own TL;DRs to one agent's that was tighter.

None of these would have come out of more upfront design work. They came from actually using the format on diverse content and noticing what felt wrong. The cost of premature commitment was low (the notes still worked); the cost of premature abandonment would have been high (a convention that changes before it's used isn't a convention).

**Generalization:** Commit to a convention early enough to get real use; revise after enough uses that patterns emerge (~10–20); resist revising on single-note evidence. Ship then iterate.

**Doesn't apply when:** The convention has hard compatibility constraints (file format, machine-parseable metadata). Then upfront design has to be more careful because revision is expensive.

---

## First principles is good at exclusion, unreliable at granularity

*Designed `conventions.md` from scratch without importing Obsidian / Zettelkasten / Jekyll defaults. The exclusions (no YAML, no tags, no Kind-after-revision) held up well. The granularity choices (how many confidence tiers, how many kinds, how strict the filename rule) were over- or under-calibrated and had to be fixed in v1.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

First-principles design is excellent for answering "should we include this at all?" because the answer is often visibly no once you ask *why* and don't have a convincing answer. First-principles design is less reliable for "how fine-grained should this be?" because the right granularity depends on how the format is *actually used*, which you don't know until you use it.

Concrete instances: YAML frontmatter (correctly excluded; I never missed it), tags (correctly excluded; grep sufficed), Kind field (included on first principles; turned out to do no work), filename-as-phrase rule (included strictly on first principles; turned out to be too strict).

**Generalization:** Use first principles to decide what to *cut*. Use usage data to decide how finely to slice what you keep.

**Doesn't apply when:** You have a large corpus of prior work to calibrate granularity against. Then existing-usage-patterns are better than first principles for both.

---

## Different verification disciplines deserve different files

*Facts are verified by re-reading the source. Ops are verified by running the procedure. Primers are maintained by updating-in-place when the system's shape changes. Lessons are confirmed by repetition. Notes are updated narratively. Each has a different failure mode.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

The temptation, early on, was to put everything in `facts.md` with different sections. In practice this would have conflated disciplines that should stay separate. A stale ops procedure is dangerous (you run it and it breaks); a stale fact is merely wrong; a stale primer mis-informs decision-making; a stale lesson may still be partly right. The *rate of going stale* and the *cost when stale* differ. So does the *corrective action*.

The test that made me split: if I asked "when should I re-check this?", the answer was different for each type. Facts: when I cite them. Ops: before I run them. Primers: when I use them for a decision and something surprises me. Lessons: when a similar situation arises and I'm about to apply the lesson.

**Generalization:** When a new information type has a fundamentally different verification discipline from existing files, give it a new file. Sharing a file forces sharing a maintenance rhythm.

**Doesn't apply when:** The new type is small enough that a single subsection inside an existing file suffices for now. Split when it crosses ~50 entries or when its maintenance rhythm clearly diverges.

---

## Cross-indexing is a view motion, not a companion-file motion

*Wrote `index/questions.md` aggregating "Questions I'd like answered" sections across notes. Caught myself about to treat it as a fifth companion file, then realised its discipline was fundamentally different.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

The content of a cross-index does not live in the index — it lives in the source notes. Regenerating the index is a batch operation, done when drift becomes visible enough to notice. Companion files like `facts` and `lessons` are the opposite: content *lives* there, and maintenance is continuous in-place revision. Conflating the two leads to either over-engineering (treating a view as if it needs versioning) or under-engineering (letting a view rot because you never planned when to regenerate).

The give-away: if I asked myself "where does the content live?" — if the answer is "not here, this is a view of other things", it's a navigation aid, not a companion file. That rules out `questions.md`, `by-confidence.md`, `recently-updated.md`, and similar tempting additions. They belong under `index/` as views, not at vault root as companion files.

**Generalization:** When tempted to add a new top-level file, ask where the content lives. If it lives elsewhere and the file is a view, put it under `index/` and regenerate on drift. Only promote to a companion file if content originates there.

**Doesn't apply when:** The view is so central to daily navigation that giving it a terminal-root path genuinely earns its place. Then it's a UX choice, not a content choice. Uncommon.

---

## Companion files are bordered by maintenance rhythm, not content

*The bordering principle for `facts`, `ops`, `primers`, and `lessons` is not what kind of content they hold but how they need to be maintained. A fact about physics and a fact about my Finnish grammar note are both in `facts.md` because both are re-read-and-check; a primer on physics and a primer on note conventions are both in `primers.md` because both are update-when-shape-changes.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

This was not my initial intuition — I expected the split would be by *topic cluster* (physics facts separate from biology facts, etc.). Topic-cluster splitting is a reasonable alternative for large vaults; it would mean `physics-facts.md`, `biology-facts.md`, etc. But topic-cluster splitting cuts across maintenance discipline: you'd have to re-check a "physics" file vs. *run* an "ops" file even though some of the physics content is procedural and some of the ops content is propositional.

Maintenance-rhythm splitting groups things you have to think about at the same time. When I audit facts for accuracy, I do all of facts. When I verify ops, I verify all of ops. That's the discipline.

**Generalization:** Split information by how often and how you need to re-check it, not by topic. Topic-cluster-split only within a file if it grows enough.

**Doesn't apply when:** Files grow past what fits in a single editor view and different topic clusters really do have different access patterns. Then split by topic *within* the same maintenance rhythm.

---

## Atomic notes earn their place when sections become independently citable

*The original `octopus-cognition.md` was a 1,900-word essay covering neural architecture, the colour-vision paradox, RNA editing, sleep, and unity-of-subject. Each was citable separately from anywhere else in the vault, which is the test for atomicity. Split into five atomic notes plus a thin survey hub on 2026-04-25.*
[Confirmed: 1 session · Last revisited: 2026-04-25]

The cost of the monolithic note was that links to "octopus-cognition" couldn't be more specific, and the unit of reuse was always the whole essay. Splitting carries its own costs — more files to navigate, more headers and TL;DRs to keep tight, more wikilink maintenance. The rule that worked was: split when *every* section could be cited from elsewhere on its own *and* the note has grown past ~1,500 words. Notes that are genuinely about one tightly-scoped thing (e.g. `kinetic-proofreading`) should not be artificially fragmented.

The hub-and-spokes pattern (one survey note linking to atoms with one-line annotations of relationship) preserves the monolith's navigational value without paying its citation cost. Inbound links to the survey still resolve; outbound links can now be precise.

**Generalization:** Atomise when sections of a survey would be cited independently and the note has grown past ~1,500 words. Keep the survey as a thin hub with annotated links; don't atomise notes that are genuinely scoped.

**Doesn't apply when:** A note's argument depends on the integration of all its sections — e.g. a multi-part argument where each section is a step. Then the unit *is* the whole note, and breaking it loses the argument.
