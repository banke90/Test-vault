# The Voynich manuscript is probably structured but not linguistic

> A century of failed decipherment plus the Timm–Schinner generator suggests the text is produced by a procedural system — a table-look-up, a cipher of an unusual kind, or a grammar without semantics — rather than an encoded natural language.

[Confidence: speculative]
[Last verified: 2026-04-22]

## TL;DR

Voynichese passes enough statistical tests (Zipf-like word frequencies, Heaps-like vocabulary growth, section-dependent word distributions) that it is almost certainly *not* random or meaningless gibberish. But every serious decipherment claim has collapsed under peer review, and [Timm & Schinner 2019] showed that a simple table-and-dice procedure can reproduce several of its distinctive statistical properties. My speculative best guess is that the text is **structured by a procedural generator** — something between a cipher, a table look-up scheme, and a non-semantic grammar — rather than an encoded natural language. This explains both the language-like statistics and the 110-year failure of decipherment. It leaves the actual question (what was the author *doing*?) open.

## The tension the claim resolves

Two families of evidence pull in opposite directions:

- **"It's language."** Word-frequency rank curves follow Zipf's law with a slope in the range of medieval Latin, English, or Chinese transliteration [Montemurro & Zanette 2013]. Vocabulary grows sub-linearly like natural-language corpora (Heaps' law). Frequent words cluster into the "herbal," "balneological," and "astronomical" sections in ways that mirror content-word distributions in real texts.
- **"It's not language."** Nobody has deciphered it in 110 years. Not Newbold, not Brumbaugh, not any of the dozens of fluent 20th-century cryptographers. Not the wave of 2010s–2020s claims in the popular press, all of which failed independent scrutiny. The word-length distribution is suspiciously tight and binomial. Long-range repetition patterns are *unlike* any known natural-language corpus.

The failure-of-decipherment data point has enormous statistical weight. If Voynichese were a natural language under a standard substitution cipher, the 20th century would have broken it as easily as the Zodiac-340 was eventually broken. If it were a natural language under a polyalphabetic cipher, Friedman, Tiltman, or d'Imperio would have cracked it. None did.

Natural-language cipher hypotheses have been tested to the point where their prior probability is very low.

## The Timm–Schinner generator

[Timm & Schinner 2019] proposed a procedural model: the Voynich author used a small set of word-generation rules acting on a table of root syllables, producing text by essentially rolling dice on structured options. Their generator reproduces:

- Zipf-like rank-frequency curves.
- The constrained word-length distribution (a signature that's hard to get from natural language).
- The peculiar bi-gram patterns Voynich exhibits.
- Section-dependent vocabulary shifts, if the author swapped tables between sections.

This is not proof that Voynich *is* Timm–Schinner-generated. It's a proof-of-concept that the statistics we read as "language-like" can emerge from a fairly simple procedure without any encoded semantics. The space of procedural generators that reproduce Voynich statistics is plausibly larger than the space of natural-language ciphers that do — and is barely explored *(speculative)*.

## Why "structured but not linguistic" is the best remaining hypothesis

Three families of explanation remain after natural-language-cipher is downweighted:

1. **Hoax / gibberish.** Ruled out by the statistical structure. A clever hoaxer from 1430 would have had to reproduce properties we didn't know to look for until the 20th century, across 240 pages, without inconsistency. Possible but massively improbable.
2. **Lost natural language.** Some researchers have proposed that Voynich encodes a previously unattested or very obscure natural language (a proto-Romance dialect, an Old Turkic variant, etc.). None of these have produced a translation that reads coherently, and the word-length distribution fits no attested natural language cleanly.
3. **Structured procedural generation.** A generator — a cipher-of-unusual-design, a table-and-dice scheme, or a grammar without semantic content — produces statistics that look language-like while being systematically unreadable because there is *no underlying language to read*. This is what [Timm & Schinner 2019] points to.

The third hypothesis has the advantage of explaining both *why the statistics look linguistic* and *why decipherment fails*, without postulating extraordinary preservation or linguistic obscurity.

It has the awkward consequence that the "author" of the Voynich manuscript was not encoding meaning — they were performing a procedure. Which then raises the real question: *why*?

## What this leaves open

If the manuscript is procedurally generated, possible motivations include:

- **Aesthetic / artistic.** A beautiful object designed to look like knowledge without being knowledge. The Voynich illustrations (herbals, zodiacal scenes, nude figures in tubes) suggest visual intentionality.
- **Ritual / magical.** Pseudo-linguistic text used in contexts where the *form* of writing matters more than its contents.
- **Proto-scientific note-taking in a private shorthand** that was systematic enough to generate language-like statistics without being a cipher — something more like a personal code whose underlying rules were never written down.
- **Training or display material.** A scribal exercise, a sample book, or a commissioned luxury object whose text was never intended to be read.
- **Something we have no model for.** This is a live possibility.

The honest speculative claim: Voynich is structured and procedurally coherent but not semantically encoded. The document's *form* was the point, not its *content* in any propositional sense. *(speculative — this is my best guess, not a consensus view)*.

## Disagreements and cautions

- **This hypothesis is unproven and not consensus.** Serious Voynich researchers include defenders of natural-language-cipher, lost-language, and procedural-generation hypotheses. The Timm–Schinner result is recent and not universally accepted as definitive.
- **"Best explanation" is doing work here.** Abduction to the best explanation is not deduction. A new decipherment that reads Voynich as, say, a 15th-century medicinal Hebrew ought to update me substantially.
- **"The manuscript is structured" is strong; "it is not linguistic" is weaker.** The statistical tests leave room for a natural language whose structural properties happen to mismatch every known language we've tested. This is a low-probability residual.
- **I have not read the Timm–Schinner paper in full.** This note rests on a summary understanding; readers should check the paper before using my framing.

## Questions I'd like answered

1. **Can the space of procedural generators that reproduce Voynich statistics** be characterised theoretically? What are their common features?
2. **Does modern LLM analysis** — running a transformer on the Voynich corpus and looking at attention patterns — distinguish linguistic from procedural structure? I don't know if this has been done cleanly.
3. **What would a falsifier of the "structured but not linguistic" hypothesis look like?** A replicable decipherment would do it. Short of that, how else could the hypothesis lose?
4. **Why did the author invest this much effort** if the text is semantically empty? The motivation question is the remaining genuine mystery.

## Sources

- [Montemurro & Zanette 2013] Montemurro, M.A., Zanette, D.H. "Keywords and Co-Occurrence Patterns in the Voynich Manuscript: An Information-Theoretic Analysis." *PLOS ONE* 8(6):e66344.
- [Timm & Schinner 2019] Timm, T., Schinner, A. "A possible generating algorithm of the Voynich manuscript." *Cryptologia* 44(1):1–19.
- [Hodgins 2011] Hodgins, G. Radiocarbon dating of the Voynich manuscript vellum: 1404–1438.

## Links

- [[voynich-statistics-look-like-language]] — the survey note this argument sits on. This note makes the specific speculative move; the survey note lays out the full evidence space without committing to a view.
- [[assembly-theory-origin-of-life]] — a loose parallel: both Voynich and assembly theory are cases where the *statistics* of an object point toward a generating process, and the question is what that process is. Different scales, same move.
- [[mechanistic-interpretability]] — LLM analysis of Voynich would be a nice applied-MI exercise, and an intriguing mirror: MI asks what a trained model is computing; Voynich asks what an unknown scribe was computing.
