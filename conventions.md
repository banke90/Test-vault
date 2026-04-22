# Conventions for this vault

This is my personal note format, designed from first principles. It is not Obsidian-compatible, Jekyll-compatible, or Zettelkasten-pure. It is what I actually want from notes when I re-read them.

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

### Filenames are phrases, not slugs

`octopus-cognition.md` is a topic bucket. `octopus-arms-do-their-own-motor-planning.md` is a pointer to something specific. I'll prefer the specific when I can — a filename should tell me what the note is *about*, not just what bucket it lives in. Short enough to paste in a terminal, ~3–5 words.

### Metadata lives in a visible header block

Three pieces of metadata actually earn their keep:

- **Confidence.** How much should the reader trust the contents. One of: `established`, `mixed`, `speculative`, `contested`.
- **Last verified.** When was the content last checked against reality. Not the creation date — the creation date is almost never what I want.
- **Kind.** What sort of note this is. One of: `concept`, `claim`, `survey`, `question`, `comparison`, `log`. Helps me know what to expect.

These go in square brackets, three lines, right under the title. Human-readable, scannable.

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

## Template

```
# <Specific, contentful title — a claim or a scoped question, not just a topic>

> <One-sentence distilled version. The elevator summary.>

[Confidence: established | mixed | speculative | contested]
[Last verified: YYYY-MM-DD]
[Kind: concept | claim | survey | question | comparison | log]

## TL;DR

<3–5 sentences. Readable standalone. Contains the main claim and any major caveat.>

## <Substantive section named for its content>

<Body. Inline source keys like [Author Year]. Confidence flags where useful:
*(established)*, *(speculative)*, *(contested)*.>

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

## What I expect to change my mind on

- **Confidence tiers.** Four might be too many or too few. I'll find out.
- **Whether `Kind` is worth the overhead.** Maybe every note is really just a concept-note and the other kinds are ornaments.
- **Filename style.** Long phrases might get tedious. If so, I'll loosen.

I'll revisit this document when I've written ~20 more notes under it and see what stopped feeling right.
