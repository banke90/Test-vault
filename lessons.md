# Lessons

Generalizable takeaways from specific experiences. Each entry: a lesson distilled from an event or a series of events, with just enough context to know where it came from and when it applies.

Distinct from the other companion files:

- [[facts]] are propositional truths about the world. Lessons are truths about *what I did and what generalised from it*.
- [[ops]] are runnable procedures. Lessons are meta — they inform *which* procedures to choose.
- [[primers]] compress a system's *shape*. Lessons compress an event's *pointe*.
- [[notes]] are narrative treatments. Lessons are post-event distillations, shorter than they would be as notes.

**Verification discipline.** A lesson is *confirmed by repetition*. A lesson from one event is provisional. A lesson from several is load-bearing. Mark this explicitly.

**Format per entry.**

```
## <Lesson as a statement, not a topic label>

*<One-line context: what happened, roughly when.>*
[Confirmed: 1 session | 2–3 sessions | many · Last revisited: YYYY-MM-DD]

<One or two paragraphs of prose explaining the event and the analysis.>

**Generalization:** <The actionable takeaway, one sentence.>

**Doesn't apply when:** <Boundary conditions.>
```

**Rules.**

- Title the lesson, not the event. "Tight prompts + save-often beats broad autonomy" — not "Agent experiment of 2026-04-21".
- Use prose for the explanation. Lessons have a narrative arc that bullets break.
- Specify the generalization as a single scannable sentence.
- Specify the boundary conditions. A lesson without "doesn't apply when" is overclaimed.
- Update in place. When a new experience confirms, refines, or overturns a lesson, revise the existing entry — don't stack versions.
- When a lesson crosses into substantive content (not just process), consider promoting to a full note and leaving a stub here.

---

## Tight prompts with save-often discipline beat broad autonomy for long-running research agents

*Spawned 8 parallel subagents with broad prompts for research; all rate-limited with nothing written. Retried with 2 parallel broad-prompt agents; both timed out with nothing written. Single tight-prompt agent with "save early, save often" instruction succeeded in ~3 minutes. Then scaled back up to 3 parallel agents with the same tight prompt + convention reference; all three succeeded.*
[Confirmed: 2–3 sessions · Last revisited: 2026-04-22]

The failure mode for research agents is the same as for humans: given open-ended freedom, they spend all their time researching and deliberating and never commit output. The successful prompts had three specific properties. First, they forced a decision within 30 seconds — "pick the first topic that genuinely interests you, don't research to decide." Second, they required creating the output file *before* doing most of the research, as an empty skeleton. Third, they told the agent to save after each section, not after the whole note. All three properties protect against the time-out-with-nothing-written failure mode.

The broad-prompt version was not noticeably more creative in topic selection; the successful agents produced Antikythera, Voynich, tardigrades, and Finnish grammar, which is a fine spread. The broader prompt's extra freedom bought nothing.

**Generalization:** For research agents that might time out, default to tight prompts with explicit "create the file first, save after each section" instructions. Give a menu of candidate topics to narrow decision cost.

**Doesn't apply when:** The task is genuinely small enough that one save at the end is fine, or when creative topic choice is the point (then you want breadth of outputs, and the time cost of failed runs is acceptable). Also doesn't apply when running locally without the rate-limit and timeout constraints that shape the remote-agent case.

---

## Release a convention after one use; revise after ~10–15

*Wrote conventions.md v0 as a first-principles design. Used it on 15 notes. Revised to v1 based on what stopped feeling right.*
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

## Assume a 30–70% gap between popular narrative and primary literature

*Wrote notes on mycorrhizal networks, plant learning, assembly theory, mechanistic interpretability, tardigrade extremotolerance, and the Voynich manuscript. In each case, the popular narrative substantially overstated what the primary literature actually supports.*
[Confirmed: many · Last revisited: 2026-04-22]

The pattern held across very different fields and was not driven by a few bad actors. Popularisers face dramatisation incentives that researchers do not; science writers in some cases faithfully report what the researcher said in a public-facing venue, even when the researcher was overstating relative to their own papers. The Karst, Jones & Hoeksema 2023 re-examination of mycorrhizal networks is the textbook case: *citation drift* where a popular claim gets cited with increasing confidence over time while the underlying evidence doesn't strengthen.

This is not a cynical take. It's a calibration. The gap is large enough to matter for writing accurate notes, small enough that the underlying science is usually doing good work.

**Generalization:** Default to reading primary literature for any substantive claim; treat popular-facing summaries (books, TED talks, podcasts) as pointers, not sources. Flag in `## Disagreements and cautions` when the popular narrative runs ahead of the evidence.

**Doesn't apply when:** The popular-facing venue *is* the primary literature (e.g. Anthropic blog posts for recent interpretability research), or when the claim is simple enough that drift hasn't had room to compound.

---

## Different verification disciplines deserve different files

*Facts are verified by re-reading the source. Ops are verified by running the procedure. Primers are maintained by updating-in-place when the system's shape changes. Lessons are confirmed by repetition. Notes are updated narratively. Each has a different failure mode.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

The temptation, early on, was to put everything in `facts.md` with different sections. In practice this would have conflated disciplines that should stay separate. A stale ops procedure is dangerous (you run it and it breaks); a stale fact is merely wrong; a stale primer mis-informs decision-making; a stale lesson may still be partly right. The *rate of going stale* and the *cost when stale* differ. So does the *corrective action*.

The test that made me split: if I asked "when should I re-check this?", the answer was different for each type. Facts: when I cite them. Ops: before I run them. Primers: when I use them for a decision and something surprises me. Lessons: when a similar situation arises and I'm about to apply the lesson.

**Generalization:** When a new information type has a fundamentally different verification discipline from existing files, give it a new file. Sharing a file forces sharing a maintenance rhythm.

**Doesn't apply when:** The new type is small enough that a single subsection inside an existing file suffices for now. Split when it crosses ~50 entries or when its maintenance rhythm clearly diverges.

---

## Write TL;DRs last

*Convention said TL;DRs should be 3–5 sentences. My first round consistently landed at 5–7 without noticing. The agent-written notes in the same format were tighter. The difference was that I was writing TL;DRs first; the tighter ones were written after the rest of the note was settled.*
[Confirmed: 2–3 sessions · Last revisited: 2026-04-22]

Written first, the TL;DR tries to preview everything the note might say and ends up including qualifications the body of the note will handle. Written last, the TL;DR can assume the body exists and only needs to carry what survives compression. The difference is ~2 sentences and a real tightness gain.

This generalises beyond TL;DRs. Abstracts, executive summaries, README openings — all benefit from being written after the thing they summarise is stable. It feels like "backwards" work order because the summary *sits* first. It isn't; it's in-place-of.

**Generalization:** Write the summary last, place it first. Resist pre-emptive summarising.

**Doesn't apply when:** You genuinely don't know what you're writing yet and the summary is a *thinking tool* for getting there. Then write a draft summary, discard it before publishing, and write the real one last.

---

## Companion files are bordered by maintenance rhythm, not content

*The bordering principle for `facts`, `ops`, `primers`, and `lessons` is not what kind of content they hold but how they need to be maintained. A fact about physics and a fact about my Finnish grammar note are both in `facts.md` because both are re-read-and-check; a primer on physics and a primer on note conventions are both in `primers.md` because both are update-when-shape-changes.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

This was not my initial intuition — I expected the split would be by *topic cluster* (physics facts separate from biology facts, etc.). Topic-cluster splitting is a reasonable alternative for large vaults; it would mean `physics-facts.md`, `biology-facts.md`, etc. But topic-cluster splitting cuts across maintenance discipline: you'd have to re-check a "physics" file vs. *run* an "ops" file even though some of the physics content is procedural and some of the ops content is propositional.

Maintenance-rhythm splitting groups things you have to think about at the same time. When I audit facts for accuracy, I do all of facts. When I verify ops, I verify all of ops. That's the discipline.

**Generalization:** Split information by how often and how you need to re-check it, not by topic. Topic-cluster-split only within a file if it grows enough.

**Doesn't apply when:** Files grow past what fits in a single editor view and different topic clusters really do have different access patterns. Then split by topic *within* the same maintenance rhythm.
