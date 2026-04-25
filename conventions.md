# Conventions for this vault

[Author: agent (prompted by user); attribution+commentary section co-designed with user]

This is my personal note format, designed from first principles. It is not Obsidian-compatible, Jekyll-compatible, or Zettelkasten-pure. It is what I actually want from notes when I re-read them.

Revised 2026-04-22 after writing ~15 notes under the original version. Changes from v0: dropped `[Kind]` field, softened filename rule, tightened TL;DR target, added companion file for raw facts, honest note on what `Last verified` requires to earn its place. The spirit unchanged.

Revised 2026-04-25 after a self-critique pass and grooming. Changes from v1: widened `Confidence` to permit scoped-tier annotations; explicitly accepted bare `[[wikilinks]]` as the link style, since they work across most modern markdown note tools; added `raw/` as a fifth content type for in-progress thinking; flagged that monolithic survey notes should be split into atomic notes when they cover several distinct claims; moved meta-lessons about building this vault out of `lessons.md` into `meta/build-log.md`.

Revised again 2026-04-25 after user feedback that the vault was hostile to human readers (artifacts written in agent-coded register, no way for a human to participate in or annotate work). Changes: added `[Author:]` field as a third metadata line, added a cross-commentary convention using `> [A YYYY-MM-DD]:` and `> [H YYYY-MM-DD]:` blockquote prefixes, applied a one-time retro-tag pass marking existing files as agent-authored.

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

- **Confidence.** How much should the reader trust the contents. One of `established`, `mixed`, `speculative`, `contested` — or, when a note's claims fall in different tiers, an annotated form like `mixed — the neurobiology is solid, the philosophical implications are open` or `established for the basic facts; specific reconstructions are mixed`. The annotated form is a feature, not a deviation: a single tier often misrepresents a note that surveys both well-replicated and contested material.
- **Last verified.** When was the content last checked against reality. Not the creation date — the creation date is almost never what I want. *Caveat:* `Last verified` only earns its place if I actually come back and update it. If a note sits for years with the same date, the field degenerates into a creation date with extra steps. The discipline is the point. *Initial-drop note:* on first writing, `Last verified` is the creation date and the field is provisional until I revisit.

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

### One claim per note, when it earns it

A monolithic survey can hide several distinct claims under one title. When a note actually covers, say, neural architecture *and* a vision paradox *and* an RNA-editing finding *and* sleep behaviour, the unit of reuse is each of those, not the bundle. The fix is to split the note into atoms — one claim per file, named for the claim — and keep the survey as a thin hub linking to the atoms with one-line annotations of the relationship. I do this when a single note grows past ~1,500 words *and* its sections could be cited independently.

This is not a default. Notes that are genuinely about one tightly-scoped thing should not be artificially broken up. The test: would each section be cited from elsewhere on its own? If yes, atomise.

### TL;DR is a hard rule, not a nicety

Every note starts with a one-paragraph summary that can stand alone. If a reader reads nothing else, that paragraph should deliver the point. I write it last, but it sits first.

Target length: **three sentences**. Five is a ceiling, not an aim. Longer TL;DRs are the note spilling into its own summary. I drifted past the target in my first round; tightening matters.

## Template

```
# <Specific, contentful title. A claim for argument notes, a scoped topic for surveys.>

> <One-sentence distilled version. The elevator summary.>

[Author: agent (prompted by user) | user | mixed: ...]
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

- **Dataview queries, plugins, graph views.** Beyond bare `[[wikilinks]]`, the vault should work in a plain text editor. If a convention needs a plugin or a renderer to be useful, I don't want it. (Wikilinks themselves are widely supported across modern markdown note tools — Obsidian, Logseq, Foam, Dendron, Bear, GitHub previews — and their main practical advantage is rename-tracking and `[[target|alias]]` syntax. They're a low-cost dependency.)
- **Numbered headers (1., 2., 3.).** They imply an order that usually isn't meaningful. Headers are navigation, not chapters.
- **"Last modified: auto"**. Autostamps drift and lie. A manual `Last verified` is a commitment.
- **Categorical directory structure beyond shallow grouping.** Deep directory trees are a losing battle against how ideas actually cross-pollinate. Flat-ish is better.

### Wikilink style

Bare `[[note-name]]` everywhere — no path prefix. This relies on the renderer resolving filenames vault-wide, which all the tools listed above do. The advantages: links survive rename if the tool supports rename-propagation, the syntax stays short, and `[[target|alias]]` lets the displayed text differ from the target. Cost: if two notes share a filename, resolution is ambiguous. I use specific filenames precisely so this doesn't happen.

## Companion files

Full notes are for narratives I've understood. Companion files at the vault root carry other kinds of knowledge that don't want to be narratives. Each has its own maintenance discipline — that's the bordering principle, not content type.

- **[[facts]]** — atomic propositional facts. Numbers, dates, specific claims. One bullet each. Bolded noun phrase, inline `[Author Year]`, optional confidence tag, optional `→ [[name]]` link. Shallow topical sections (≤10). Grep beats taxonomy. *Verified by re-reading the source.*
- **[[ops]]** — operational procedures. Commands, workflows, how-to. `[Last worked: YYYY-MM-DD]` tags, no confidence tags. *Verified by running it.*
- **[[primers]]** — dense reference cards for complex systems. Shape + handles + traps + deeper-link per entry. One screen each. For consultation before making decisions about direction, design, or interpretation. *Maintained by updating-in-place when the system's shape changes.*
- **[[lessons]]** — generalisable takeaways from specific experiences. Title is the lesson, not the event. Prose explanation + explicit `Generalization:` and `Doesn't apply when:` lines. *Confirmed by repetition.*

These four have different verification disciplines and different failure modes. Keeping them separate is the point. When I audit facts for accuracy I do all of facts; when I verify ops I verify all of ops; when a system's shape changes I update the primer; when a new experience matches or breaks an existing lesson I revise it in place. Separation supports the rhythm.

A fifth content type sits in `raw/` rather than at the root, because its discipline is the opposite of the others:

- **`raw/`** — scratch notes. In-progress thinking, "haven't read this yet" stubs, fragments I want to capture before they decay. Explicitly **not verified**, explicitly not for understanding. The format is loose: a title, a date, prose. The discipline is *promotion* — when a raw note settles into something I'd stand behind, I rewrite it as a real note under `notes/` and delete the raw original (or leave a one-line stub pointing forward). Raw notes age out: anything older than ~3 months that hasn't been promoted is either deleted or accepted as a permanent fragment. They are the antidote to a vault made entirely of polished essays.

If something doesn't fit any of the five, it's probably a note. If it fits two, put it in the one whose discipline matches how I'll use it.

### Views (not companion files)

The `index/` directory holds views of existing content — `00-index.md` for navigation, `synthesis.md` for cross-cutting threads, `questions.md` for an aggregation of per-note open questions. A view is distinct from a companion file: its *content lives elsewhere* (in the source notes), and it is regenerated-on-drift rather than continuously maintained.

The test: *where does the content live?* If it lives in this file, it's a companion file or a note. If it lives elsewhere and this file is a projection, it's a view and belongs under `index/`. This distinction matters for maintenance rhythm — see [[lessons]] under "Cross-indexing is a view motion, not a companion-file motion."

## Attribution and commentary

The vault is built collaboratively by an agent and a human. Until 2026-04-25, that collaboration was tribal knowledge — every note was produced by an agent on user prompts but nothing in the file said so, and the human had no marked way to disagree with the agent's work without overwriting it. Two conventions make the collaboration legible.

### Author marker

A bracketed `[Author: <value>]` line lives in the metadata header block, alongside `[Confidence:]` and `[Last verified:]`. Free text, not enumerated. Examples:

- `[Author: agent (prompted by user)]` — most existing notes.
- `[Author: user]` — written by the user directly.
- `[Author: mixed: agent-drafted, user-revised]` — substantive joint authorship.
- `[Author: agent (prompted by user); commentary by user]` — agent-drafted, with user `> [H]:` annotations interleaved.

Required for every note, every `index/` view, and every root companion file (`facts.md`, `primers.md`, `ops.md`, `lessons.md`, `conventions.md`). Skipped for `meta/build-log.md` (self-evidently agent-built), for `README.md` (auto-regenerated from `index/00-index.md`), and for `raw/` files (pre-attribution by design — promotion to `notes/` is when attribution attaches).

The marker is at file level only. If a future revision mixes voices within a single file beyond what the file-level marker captures, switch the marker to `mixed: ...` or use commentary blockquotes (below); do not introduce per-section markers.

### Cross-commentary

Either party may comment on the other's work without overwriting it. Comments use a blockquote prefix:

- `> [A YYYY-MM-DD]: ...` for agent comments.
- `> [H YYYY-MM-DD]: ...` for human comments.

Rules:

- Place the comment as close as possible to the text it refers to — adjacent paragraph, or end of section if the comment is about the section as a whole.
- Comments are first-class content. Do not edit or delete them when revising the surrounding text. If a comment sparks a substantive rewrite, leave the comment in place; optionally add a follow-up `> [A/H YYYY-MM-DD]: addressed in this revision` so the trail is preserved.
- Multi-line comments use Markdown blockquote continuation (`> ` on each line). Keep them short — if a comment runs more than ~5 lines, it probably wants to become a note of its own with a wikilink back.
- Silent disagreement on the record is a valid outcome. The convention does not require comments to be answered.

The first worked example of cross-commentary lives in `[[ops]]` under "Retrieval strategy — what to read first," where agent-specific tooling appears as `> [A]:` glosses on the human-readable layer descriptions.

## Changed my mind on

- **Kind field.** Dropped. See above.
- **Filename rule.** Softened. See above.
- **TL;DR length.** Tightened from "3–5 sentences" to "three, max five".
- **`Last verified` discipline.** Added an explicit caveat that it only earns its place with ongoing maintenance.
- **Confidence as single tier.** Widened. Annotated `<tier> for <scope>; <tier> for <scope>` is the working form; the original single-value rule was over-tight for survey notes.
- **Plain-text portability.** Softened. Bare `[[wikilinks]]` are accepted as a low-cost dependency on tooling that nearly every modern markdown note tool provides.
- **Atomicity.** Added a "one claim per note, when it earns it" rule for monolithic surveys that bundle several independently-citable claims.
- **Scratch content.** Added `raw/` as a fifth content type — explicitly unpolished, explicitly not for understanding.
- **Authorship as tribal knowledge.** Made explicit. Added `[Author:]` field plus `> [A]:` / `> [H]:` cross-commentary blockquotes so agent-authored, human-authored, and mixed work are legible at a glance and either party can annotate the other's work without overwriting it.

## Still on my watchlist

- **Confidence tiers.** Four feels right so far but I've used `established` and `mixed` much more than the others. May collapse to three.
- **Sources as bottom-of-note vs footnotes.** Bottom works; footnotes would be cleaner but render unevenly across tools. Keeping bottom for now.
- **Whether the `Disagreements and cautions` and `Questions I'd like answered` sections overlap too much.** A contested claim can appear in both. Haven't fully resolved.
- **`facts.md` as one file vs split.** One for now. Split when it crosses ~400 lines.

I'll revisit this document when I've written ~20 more notes under it.
