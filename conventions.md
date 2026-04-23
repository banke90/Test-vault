# Conventions for this vault

This is my personal note format, designed from first principles. It is not Obsidian-compatible, Jekyll-compatible, or Zettelkasten-pure. It is what I actually want from notes when I re-read them.

Revised 2026-04-22 after writing ~15 notes under the original version. Changes from v0: dropped `[Kind]` field, softened filename rule, tightened TL;DR target, added companion file for raw facts, honest note on what `Last verified` requires to earn its place. The spirit unchanged.

## What a note is for

Before structure, purpose. I write notes to:

1. Capture what I've understood in a form future-me can actually use.
2. Mark honestly what I'm sure of vs what I'm guessing.
3. Track what I still don't know.
4. Make it easy to follow a thread from one idea to a genuinely related one.

Everything below follows from those four.

## Decisions, and why

### No YAML frontmatter

Frontmatter is for machines. I'm the reader. If I want metadata, I'll put it somewhere a human sees it — in a visible line near the title — not in a fenced block I have to skip over.

### No tags

Tags promise cross-cutting retrieval. In practice they either sprawl (every note gets ten) or atrophy (nobody tags consistently over time). Full-text search handles most retrieval; explicit links handle the rest. I'll reintroduce tags the day I find myself wanting them — not in advance.

### Filenames should be specific where useful, bucket-names where that serves

My first version of this rule said "always prefer phrases over topic-buckets." In practice I kept some bucket-style filenames (`octopus-cognition.md`, `mechanistic-interpretability.md`) because they're shorter, because they don't pretend to a specificity the note doesn't have, and because renaming breaks links. The honest rule: use a specific phrase when the note really is about one claim or one scoped question; use a short bucket when the note is a survey and a phrase would feel forced. Don't force either direction.

### Metadata lives in a visible header block

Two pieces of metadata earn their keep:

- **Confidence.** How much should the reader trust the contents. One of: `established`, `mixed`, `speculative`, `contested`.
- **Last verified.** When was the content last checked against reality. Not the creation date — the creation date is almost never what I want. *Caveat:* `Last verified` only earns its place if I actually come back and update it. If a note sits for years with the same date, the field degenerates into a creation date with extra steps. The discipline is the point.

These go in square brackets, two lines, right under the title. Human-readable, scannable.

(v0 had a `Kind` field with six values: concept, claim, survey, question, comparison, log. In practice almost every note I wrote was "survey" or "concept". The taxonomy did too little work to earn its place. Dropped.)

### Sources live next to claims

End-of-document bibliographies are print-book inertia. Online, a source is a URL you click. I want to click it *at* the claim it supports, not scroll to the end. I use inline bracket keys like `[Bennett 1982]` at the point of use, and resolve them in a `Sources` section at the end.

This also means claims without a source are visibly bare — which is useful, because it makes me notice when I'm writing from vague memory.

### Confidence marking in the body

For claims that are important and non-obvious, I'll flag confidence inline with a short parenthetical: *(established)*, *(speculative)*, *(contested)*, *(my guess)*. Not for every sentence — that would be noise. For the sentences where a reader might reasonably ask "how sure are you?".

### Open questions are first-class

A researcher's most valuable notes are the questions they haven't answered. I put "Questions I'd like answered" as a top-level section, not buried at the bottom as an afterthought. If the note has no such section, either the topic is closed or I haven't thought hard enough.

### Links are compare/contrast, not adjacency

"Related" sections are usually a list of topic-adjacent pages. That's the wrong motion. A link should say *what* connects the notes — "compare the pin-and-slot mechanism here to the epicyclic gear in X" — not just "this is also about gears." One line per link, annotated with the relationship.

### TL;DR is a hard rule, not a nicety

Every note starts with a one-paragraph summary that can stand alone. If a reader reads nothing else, that paragraph should deliver the point. I write it last, but it sits first.

Target length: **three sentences**. Five is a ceiling, not an aim. Longer TL;DRs are the note spilling into its own summary. I drifted past the target in my first round; tightening matters.

## Template

```
# <Specific, contentful title. A claim for argument notes, a scoped topic for surveys.>

> <One-sentence distilled version. The elevator summary.>

[Confidence: established | mixed | speculative | contested]
[Last verified: YYYY-MM-DD]

## TL;DR

<Three sentences. Five is the ceiling. Readable standalone. Main claim plus
any major caveat.>

## <Substantive section named for its content>

<Body. Inline source keys like [Author Year]. Confidence flags where useful:
*(established)*, *(speculative)*, *(contested)*, *(my guess)*.>

## <More sections as needed>

## Disagreements and cautions

<What is contested. Known failed replications. Positions I think are wrong and why. 
If the field is unified on this, say so and skip.>

## Questions I'd like answered

<Open questions, numbered. Concrete enough that I could recognise an answer.>

## Sources

<Bracket keys resolved to full references with URLs where available. DOI or 
arXiv or publisher URL preferred.>

## Links

<Links to other notes in this vault, each with one line explaining the 
*relationship*, not just the topic adjacency.>
```

## What I'm deliberately not doing

- **Dataview queries, plugins, graph views.** This vault should work in a plain text editor with no tooling. If a convention needs a plugin to be useful, I don't want it.
- **Numbered headers (1., 2., 3.).** They imply an order that usually isn't meaningful. Headers are navigation, not chapters.
- **"Last modified: auto"**. Autostamps drift and lie. A manual `Last verified` is a commitment.
- **Categorical directory structure beyond shallow grouping.** Deep directory trees are a losing battle against how ideas actually cross-pollinate. Flat-ish is better.

## Companion files

Full notes are for narratives I've understood. Three companion files at the vault root carry other kinds of knowledge that don't want to be narratives:

- **[[facts]]** — atomic propositional facts. Numbers, dates, specific claims. One bullet each. Bolded noun phrase, inline `[Author Year]`, optional confidence tag, optional `→ [[notes/name]]` link. Shallow topical sections (≤10). Grep beats taxonomy. *Verified by re-reading the source.*
- **[[ops]]** — operational procedures. Commands, workflows, how-to. `[Last worked: YYYY-MM-DD]` tags, no confidence tags. *Verified by running it.*
- **[[primers]]** — dense reference cards for complex systems. Shape + handles + traps + deeper-link per entry. One screen each. For consultation before making decisions about direction, design, or interpretation. *Not for learning; for consulting when you already know the territory.*

The three have different maintenance disciplines and different failure modes. Keeping them separate is the point.

If something doesn't fit any of the three, it's probably a note. If it fits two, put it in the one whose discipline matches how I'll use it.

## Changed my mind on

- **Kind field.** Dropped. See above.
- **Filename rule.** Softened. See above.
- **TL;DR length.** Tightened from "3–5 sentences" to "three, max five".
- **`Last verified` discipline.** Added an explicit caveat that it only earns its place with ongoing maintenance.

## Still on my watchlist

- **Confidence tiers.** Four feels right so far but I've used `established` and `mixed` much more than the others. May collapse to three.
- **Sources as bottom-of-note vs footnotes.** Bottom works; footnotes would be cleaner but render unevenly across tools. Keeping bottom for now.
- **Whether the `Disagreements and cautions` and `Questions I'd like answered` sections overlap too much.** A contested claim can appear in both. Haven't fully resolved.
- **`facts.md` as one file vs split.** One for now. Split when it crosses ~400 lines.

I'll revisit this document when I've written ~20 more notes under it.
