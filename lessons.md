# Lessons

Generalizable takeaways from specific experiences. Each entry: a lesson distilled from an event or a series of events, with just enough context to know where it came from and when it applies.

Distinct from the other companion files:

- [[facts]] are propositional truths about the world. Lessons are truths about *what I did and what generalised from it*.
- [[ops]] are runnable procedures. Lessons are meta — they inform *which* procedures to choose.
- [[primers]] compress a system's *shape*. Lessons compress an event's *pointe*.
- Notes (under `notes/`) are narrative treatments. Lessons are post-event distillations, shorter than they would be as notes.

**Verification discipline.** A lesson is *confirmed by repetition*. A lesson from one event is provisional. A lesson from several is load-bearing. Mark this explicitly.

Meta-lessons about *building* this vault — convention design, companion-file taxonomy, view-vs-companion distinctions, the atomicity rule — live in `meta/build-log.md`. Keeping them separate stops `lessons.md` from being a vault-construction log dressed as research lessons.

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

## Assume a 30–70% gap between popular narrative and primary literature

*Wrote notes on mycorrhizal networks, plant learning, assembly theory, mechanistic interpretability, tardigrade extremotolerance, and the Voynich manuscript. In each case, the popular narrative substantially overstated what the primary literature actually supports.*
[Confirmed: many · Last revisited: 2026-04-22]

The pattern held across very different fields and was not driven by a few bad actors. Popularisers face dramatisation incentives that researchers do not; science writers in some cases faithfully report what the researcher said in a public-facing venue, even when the researcher was overstating relative to their own papers. The Karst, Jones & Hoeksema 2023 re-examination of mycorrhizal networks is the textbook case: *citation drift* where a popular claim gets cited with increasing confidence over time while the underlying evidence doesn't strengthen.

This is not a cynical take. It's a calibration. The gap is large enough to matter for writing accurate notes, small enough that the underlying science is usually doing good work.

**Generalization:** Default to reading primary literature for any substantive claim; treat popular-facing summaries (books, TED talks, podcasts) as pointers, not sources. Flag in `## Disagreements and cautions` when the popular narrative runs ahead of the evidence.

**Doesn't apply when:** The popular-facing venue *is* the primary literature (e.g. Anthropic blog posts for recent interpretability research), or when the claim is simple enough that drift hasn't had room to compound.

---

## Speculative claims require more argumentation than established ones

*Wrote a compact argument note on Voynich with `[Confidence: speculative]`. Noticed that the work-per-sentence was higher than for `[Confidence: established]` content because I couldn't shortcut to citations.*
[Confirmed: 1 session · Last revisited: 2026-04-22]

Established claims can lean on the field's consensus: "X is the case [Author Year]" carries weight *because* the citation is a shortcut for many people having already argued. Speculative claims have no such shortcut. The reader has no reason to believe me unless I walk through the argument explicitly — which evidence favours the claim, which alternatives are ruled out and how, and what would change my mind.

The Voynich note ran ~1000 words for one speculative claim. A comparable established claim would have been ~400. The extra weight went into ruling out natural-language-cipher, ruling out hoax, ruling out lost-language, and giving the positive case for procedural generation. Each was necessary for the claim to carry.

**Generalization:** Budget 2–3× more words for a speculative claim than an established one of comparable scope. If the argument doesn't fit, the claim probably isn't as well-founded as I think.

**Doesn't apply when:** The speculation is frankly flagged as *(my guess)* or *(speculative)* inline, with no attempt to persuade. Those have the same cost as any other flagged thought. The rule applies to speculative *arguments*, not speculative asides.

---

## Write TL;DRs last

*Convention said TL;DRs should be 3–5 sentences. My first round consistently landed at 5–7 without noticing. The agent-written notes in the same format were tighter. The difference was that I was writing TL;DRs first; the tighter ones were written after the rest of the note was settled.*
[Confirmed: 2–3 sessions · Last revisited: 2026-04-22]

Written first, the TL;DR tries to preview everything the note might say and ends up including qualifications the body of the note will handle. Written last, the TL;DR can assume the body exists and only needs to carry what survives compression. The difference is ~2 sentences and a real tightness gain.

This generalises beyond TL;DRs. Abstracts, executive summaries, README openings — all benefit from being written after the thing they summarise is stable. It feels like "backwards" work order because the summary *sits* first. It isn't; it's in-place-of.

**Generalization:** Write the summary last, place it first. Resist pre-emptive summarising.

**Doesn't apply when:** You genuinely don't know what you're writing yet and the summary is a *thinking tool* for getting there. Then write a draft summary, discard it before publishing, and write the real one last.
