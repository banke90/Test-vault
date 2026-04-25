# The Voynich manuscript's text statistics look like natural language but every decipherment claim has collapsed

> Voynichese has word-length, entropy, and Zipf properties consistent with a real writing system, yet 110+ years of "solutions" fail under independent checking — the puzzle is that it is *too* language-like to be noise and *too* weird to be any known language.

[Confidence: mixed]
[Last verified: 2026-04-22]

## TL;DR

The Voynich manuscript (Yale Beinecke MS 408) is a ~240-page illustrated codex, vellum carbon-dated to 1404–1438 [Hodgins 2011], written in an unknown script nobody has convincingly decoded. Its text has Zipf-like word-frequency rank curves, entropy in the range of real written languages, and consistent morphology — so it is almost certainly *structured*, not keyboard-mashing. But the word-length distribution is suspiciously tight and binomial, long-range repetition patterns are weird, and a simple procedural "table-and-dice" generator (Timm & Schinner 2019) can reproduce many of its statistics. The honest position in 2026 is *mixed*: it behaves like writing but not like any one known language, and no decipherment has survived peer scrutiny. *(mixed)*

## Why people think it's not gibberish

Several independent statistical fingerprints of "real writing" show up in Voynichese:

- **Zipf's law.** Word-frequency rank plots on the Voynich text follow a Zipf-style power law with a slope in roughly the same range as medieval Latin, English, or Chinese transliterated text [Montemurro & Zanette 2013]. Random monkey-typing does not do this naturally; you have to work to fake it.
- **Entropy within language range.** Character-level and word-level Shannon entropy put Voynichese roughly between English and the heavily-inflected Semitic and Uralic languages [Landini 2001]. It is not below — which would indicate very short alphabets like DNA — and not above random, which would indicate noise.
- **Heaps' law.** Vocabulary growth with text length follows the sublinear curve typical of real corpora, not the square-root-like curve of random symbol streams [Montemurro & Zanette 2013]. *(established as of the 2013 analysis; contested whether this *forces* a linguistic interpretation)*
- **Topical word clustering.** Frequent Voynich words are not spread uniformly; they cluster into the "herbal," "balneological," and "astronomical" sections in a way that mirrors how content words behave in real texts [Montemurro & Zanette 2013]. This is the single strongest argument against pure hoax.
- **Morphology.** Voynich "words" have prefix-root-suffix-like regularities — certain glyph groups appear almost always word-initially, others almost always word-finally — consistent with an agglutinative or inflecting writing system [Reddy & Knight 2011].

Taken together, these are hard to reproduce by accident. A random scribe scribbling would not produce all of them at once.

## Why every "solution" so far has fallen apart

A partial graveyard of high-profile "decoded!" claims:

- **Newbold (1921)** read anagrammed Latin he saw inside individual glyph strokes. Died when other scholars couldn't reproduce any of his readings.
- **Feely, Strong, Levitov (20th c.)** — variously: medieval Latin shorthand, Roger Bacon's cipher, a Cathar abortion manual. None survived replication; each reading only works for the passage the author chose.
- **Stephen Bax (2014)** claimed partial phonetic readings of plant names. More careful than most, but the proposed identifications didn't generalize beyond a handful of words and weren't confirmed by other linguists.
- **Nicholas Gibbs (2017)** — "idiosyncratic abbreviated Latin" medical text. Lisa Fagin Davis (Medieval Academy of America) pointed out his translations don't produce grammatical Latin and that he'd spliced in unrelated scholarship [Davis 2017].
- **Gerard Cheshire (2019)** — "calligraphic proto-Romance." Bristol University pulled the press release within days after linguists noted that "proto-Romance" as Cheshire uses the term is not a recognized stage of any language [Fagin Davis 2019; Language Log 2019].
- **Ahmet Ardıç (2018)** — phonetic Old Turkish. Not published in a peer-reviewed venue; readings inconsistent across folios.

The common failure mode is the **"cherry-picked caption" trap**: Voynich folios have labels next to star diagrams, plants, and nude figures. Any phonetic mapping rich enough to be underdetermined can be tuned to make a few labels look like words in a chosen language. The test that kills every such claim is *applying the same mapping to running text on the same page* — which then reads as nonsense.

A second, subtler failure: proposed mappings rarely explain the **statistical anomalies** (tight word-length distribution, near-repetition of adjacent words like `qokedy qokedy qokeedy`, lack of normal function-word behaviour). A real decipherment should both produce sense *and* explain why the text looked weird in the first place.

## What the carbon dating and codicology tell us

Independent physical evidence constrains the suspect list more than people realise:

- **Vellum radiocarbon.** Four samples dated at Arizona in 2009 gave a 95% confidence range of roughly **1404–1438 CE** [Hodgins 2011]. This kills Roger Bacon (d. 1292) authorship and any 16th-century Dee/Kelley forgery theory. A forger would have had to acquire and write on century-old blank vellum — possible but not parsimonious.
- **Ink.** McCrone Associates' analysis found iron gall inks with compositions consistent with early-15th-century European practice; no anachronistic pigments [McCrone 2009]. No Prussian blue, no titanium white, nothing post-medieval.
- **Binding and quire structure.** The gathering structure, foldouts, and wear patterns are consistent with a single-author production in the early 15th c., though rebound later.
- **Hand analysis.** Lisa Fagin Davis (2020) identified at least **five distinct scribal hands** working on the manuscript, all writing the same script system — which is strong evidence against a single eccentric coding it up for fun. Either it was a scriptorium product, or five people were taught the system.

Together these make the "19th-century Voynich-forged-it" theory and the "one lone coder" theory both harder to sustain. Something social was happening around this script.

## The leading non-crazy hypotheses

Grouped roughly from "most linguistic" to "most procedural":

1. **Natural language in an unusual script.** An unknown or poorly-attested language (e.g. a Turkic, Caucasian, or isolate tongue) recorded by someone devising a phonetic alphabet for it. Fits the morphology and entropy. Fails to explain the narrow word-length distribution and the adjacent near-repetitions.
2. **Known language with heavy abbreviation or shorthand.** Medieval Latin and vernacular manuscripts used extensive scribal abbreviation. A sufficiently idiosyncratic shorthand could look alien. Fails the "abjad-like entropy" argument — shorthand of Latin should still produce recognisable function-word patterns, which Voynichese lacks.
3. **Verbose cipher / substitution with nulls.** A one-to-many or many-to-one cipher with inserted meaningless symbols can flatten entropy toward what we see, and some 15th-century cipher traditions (e.g. Trithemius's *Polygraphia*, 1518, though later) did exactly this. A recent paper explicitly argues Voynichese resembles *Polygraphia III* output [Bowern & Lindemann 2021].
4. **Procedurally generated "filler" — Timm–Schinner hoax hypothesis.** Timm & Schinner (2019) showed that a scribe using a small table of root/prefix/suffix tokens and a self-citation rule (copy from a nearby word, mutate one element) can generate text that matches many Voynich statistics, including the topical clustering. This is the strongest "meaningless" hypothesis on offer. It does not yet explain *all* statistical features (notably the section-specific vocabulary) but it puts a real lower bound on how much structure you can get from a simple algorithm. *(contested — compelling but not decisive)*
5. **Glossolalia / channeled / mnemonic text.** Real-human-produced but not encoding propositional content — closer to outsider-art writing systems like the Codex Seraphinianus (explicitly meaningless) or Hildegard of Bingen's *Lingua Ignota*. Underexplored because hard to falsify.

My read *(my guess)*: the truth is probably some mixture of (3) and (4) — a scribe working from a small generative system, possibly with a core of real content labels (plant names, zodiac labels) embedded in procedural padding. That would explain why captions sometimes feel almost decipherable and running text never does.

## Disagreements and cautions

- **Montemurro & Zanette's word-clustering result is sometimes overstated.** Their paper shows Voynich words cluster like content words in real texts; it does *not* show the text has semantic content in the human sense. A procedural generator that locally biases vocabulary by section could also produce this signal. Timm & Schinner argue exactly that.
- **Zipf's law is weak evidence on its own.** Many non-linguistic processes produce Zipfian distributions (random text with a space character, for example). "Voynich obeys Zipf" is necessary but nowhere near sufficient.
- **Word-length distribution is the main anomaly the "natural language" camp under-addresses.** Real languages have long right tails (a few very long words). Voynichese's length distribution is near-binomial and sharply bounded — genuinely odd for a language.
- **Beware the "line as a unit" effects.** Voynichese has clear line-initial and line-final glyph preferences [Currier 1970s, restated by Zandbergen]. Few proposed languages explain why the visual *line* would be a linguistic unit; most writing systems don't work that way. A procedural scribe, on the other hand, might well have line-level rules.
- **"AI decoded the Voynich" headlines (2018+)** generally misrepresent what the models did. Greg Kondrak's 2018 LSTM work identified Hebrew as the best fit *among a set of candidate languages for anagram-based decoding* — it did not produce readable Hebrew, and the result is not a decipherment.

## Questions I'd like answered

1. Does the Timm–Schinner generator reproduce the *line-position* statistics (line-initial/line-final glyph preferences), or only bag-of-words statistics? If the former, the hoax hypothesis is much stronger. If the latter, there's genuine structure left to explain.
2. Among Fagin Davis's five scribal hands, is the statistical profile the *same* across hands? If each scribe has a slightly different Voynichese "dialect," that points toward a learned system; if identical, more toward a shared procedural recipe.
3. Is there any folio where the image-text relationship is tight enough to get leverage? The astrological/zodiac folios with month names in apparent Romance script next to Voynichese labels seem like the best opening.
4. Would a modern large language model, trained on Voynichese as-is, produce continuations that a Voynich expert could not distinguish from the manuscript? If yes, that tells us little; if no, the text has higher-order structure current generators miss.
5. What is the information-per-glyph rate compared to medieval ciphers of known plaintext length? If Voynichese has *less* information per glyph than a one-to-one substitution should, that's evidence for nulls/padding.

## Sources

- [Hodgins 2011] Greg Hodgins, University of Arizona AMS — radiocarbon dating of four vellum samples, 1404–1438 CE 95% CI. Summarised in the Yale facsimile volume and https://en.wikipedia.org/wiki/Voynich_manuscript.
- [McCrone 2009] McCrone Associates pigment/ink analysis commissioned by Beinecke Library; iron gall inks, period-consistent pigments.
- [Montemurro & Zanette 2013] "Keywords and Co-Occurrence Patterns in the Voynich Manuscript: An Information-Theoretic Analysis," PLOS ONE. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0066344
- [Landini 2001] Gabriel Landini, "Evidence of linguistic structure in the Voynich manuscript using spectral analysis," *Cryptologia* 25(4).
- [Reddy & Knight 2011] Sravana Reddy & Kevin Knight, "What We Know About the Voynich Manuscript," Proc. LaTeCH workshop, ACL. https://aclanthology.org/W11-1511/
- [Timm & Schinner 2019] Torsten Timm & Andreas Schinner, "A possible generating algorithm of the Voynich manuscript," *Cryptologia* 44(1). https://www.semanticscholar.org/paper/433faf3e7d2c30941f61cc8625198961a6591665
- [Bowern & Lindemann 2021] "The Linguistics of the Voynich Manuscript," *Annual Review of Linguistics* 7. Useful neutral survey.
- [Davis 2017] Lisa Fagin Davis's public response to Gibbs, via *The Atlantic* and Twitter.
- [Fagin Davis 2019] Response to Cheshire "proto-Romance"; see also Language Log https://languagelog.ldc.upenn.edu/nll/?p=65930
- [Fagin Davis 2020] "How Many Glyphs and How Many Scribes? Digital Paleography and the Voynich Manuscript," *Manuscript Studies* 5(1). Identifies at least five hands.
- Wikipedia overview (good link farm, variable quality): https://en.wikipedia.org/wiki/Voynich_manuscript
- Beinecke Library high-resolution facsimile: https://collections.library.yale.edu/catalog/2002046

## Links

- [[antikythera-mechanism]] — another artifact whose physical properties outran the documentary record; compare how radiocarbon/codicology here plays the role gear-metrology plays there in constraining the suspect list.
- [[mechanistic-interpretability]] — both fields face the same epistemic problem: a system that behaves *as if* it has internal structure, with no ground truth to check candidate readings against. Voynich decipherers and interp researchers both need to beware of cherry-picked "features" that don't generalise.
- [[assembly-theory-origin-of-life]] — related question of distinguishing "generated by a process with memory/structure" from "generated by chance" using compressibility-like measures. Voynich's Zipf/entropy arguments are in the same methodological family as assembly-index arguments.
- [[collective-intelligence]] — tangentially: the Fagin Davis multi-scribe result reframes Voynich from "one weirdo" to "a small group sharing a system," which is a different cognitive and social object.
