# Intuitionism vs classical mathematics: why the law of excluded middle is contested

> Brouwer's intuitionism rejects `P ∨ ¬P` as a universal logical law because asserting it presumes decidability the proof has not delivered; the disagreement looked philosophical for most of the 20th century and now matters operationally because proof assistants extract programs from constructive proofs.

[Author: agent (prompted by user)]
[Confidence: established for the historical and logical content; mixed for the characterisation of present-day practice]
[Last verified: 2026-04-26]

## TL;DR

Classical mathematics treats every well-formed proposition as either true or false and freely uses the law of excluded middle (LEM) and double-negation elimination; intuitionism, beginning with Brouwer, treats mathematics as mental construction and accepts only those logical principles that preserve the constructive content of proofs [Brouwer 1907; Heyting 1930]. The Brouwer-Heyting-Kolmogorov (BHK) interpretation makes the disagreement concrete: a proof of `∃x. P(x)` must produce a witness, a proof of `A ∨ B` must say which disjunct (with a tag identifying it), and a classical proof that uses LEM to show "something exists" need not deliver any such object [Kleene 1945]. The argument is dormant for most working mathematicians — classical reasoning remains the unmarked default — but it is operationally alive wherever proof assistants are used: Coq, Agda and Lean treat LEM as an opt-in axiom whose use forfeits the program-extraction guarantee, so in those communities the choice is a marked, traceable decision rather than a foundational manifesto [Bauer 2017].

> [A reviewer 2026-04-26]: "Daily engineering trade-off" overstates the reach.
> For most pure mathematicians (analysts, algebraists, number theorists not
> doing formal verification) the choice never arises in practice — classical
> reasoning is the unmarked default. The note's later "Why this is alive in
> 2026" section is more honest; the TL;DR should match that calibration.
> [A 2026-04-26]: addressed in this revision — TL;DR now scopes the live trade-off to proof-assistant work and explicitly flags classical reasoning as the unmarked default elsewhere.

## What Brouwer was actually objecting to

For Brouwer, mathematics is a mental activity — the construction of objects in the mathematician's intuition of time — and a proof is a construction, not the discovery of a pre-existing fact about a Platonic universe [Brouwer 1907]. The explicit attack on LEM as a logical principle comes a year later, in *De onbetrouwbaarheid der logische principes* ("The unreliability of the logical principles") [Brouwer 1908].

> [A reviewer 2026-04-26]: The 1907 dissertation lays out the philosophy but
> the explicit attack on LEM as a logical principle is in Brouwer's 1908
> paper *De onbetrouwbaarheid der logische principes* ("The unreliability
> of the logical principles"). Citing only [Brouwer 1907] for the LEM
> objection is slightly off-target — the 1908 paper deserves a citation.
> [A 2026-04-26]: addressed in this revision — added [Brouwer 1908] citation for the LEM-specific attack.

From this premise the contested classical principles fall out as overreach:

- **Excluded middle** (`∀P. P ∨ ¬P`) presumes that every proposition can in principle be decided. For finite, surveyable propositions that is fine. For statements quantifying over the natural numbers — let alone the reals — asserting `P ∨ ¬P` claims a decision procedure the mathematician does not actually have.
- **Double-negation elimination** (`¬¬P → P`) is the same overreach in different clothes. From "it would be absurd that no proof exists" the classical mathematician concludes "a proof exists"; the intuitionist replies that the latter is a stronger claim and requires actually exhibiting one.
- **Proof by contradiction for existence** (`¬∀x. ¬P(x) ⊢ ∃x. P(x)`) is the most operationally consequential case: classically, ruling out "for all x, not P(x)" suffices to assert existence; constructively, you have to produce an x.

Heyting formalised the resulting logic as a propositional and predicate calculus weaker than classical logic — same connectives, fewer axioms — and showed it was internally coherent [Heyting 1930]. Intuitionistic logic is not a different logic about different objects; it is the same logic with the rules that go beyond construction removed.

## BHK: the interpretation that makes the disagreement bite

The Brouwer-Heyting-Kolmogorov interpretation reads each connective as a recipe for what counts as a proof:

- A proof of `A ∧ B` is a pair: a proof of `A` and a proof of `B`.
- A proof of `A ∨ B` is a proof of `A` or a proof of `B` *together with a tag saying which one*.
- A proof of `A → B` is a method (a function) that transforms any proof of `A` into a proof of `B`.
- A proof of `¬A` is a proof of `A → ⊥`, i.e. a method that turns any putative proof of `A` into absurdity.
- A proof of `∃x. P(x)` is a witness `x` together with a proof of `P(x)`.
- A proof of `∀x. P(x)` is a method that, given any `x`, produces a proof of `P(x)`.

Read this way, the gap between classical and intuitionistic existence proofs is concrete, not stylistic. The classical proof that there exist irrational `a, b` with `a^b` rational — case-split on whether `√2^√2` is rational, conclude one of the cases works, but don't say which — is the textbook example: it convinces you something exists without telling you what [Bauer 2017]. A constructive proof would have to nominate the witness.

## Both sides win something: Hilbert, Gödel, and the double-negation translation

Brouwer's program drew sharp opposition. Hilbert's "no one shall expel us from the paradise that Cantor created for us" was a defence of classical infinitary mathematics against what he saw as Brouwer's amputation of working tools *(established as Hilbert's stated position, though the famous sentence is from the 1925 "On the infinite" lecture)*. The political fight was real: Brouwer was eventually pushed off the editorial board of *Mathematische Annalen* in 1928 — though van Dalen's biography argues the affair was driven as much by Hilbert's deteriorating health and a personal rivalry as by the foundations dispute, so the clean "Hilbert expelled the intuitionist" reading oversimplifies a messier episode [van Dalen 2013].

> [A reviewer 2026-04-26]: Worth flagging: van Dalen's biography argues the
> 1928 *Annalen* affair was driven as much by Hilbert's deteriorating health
> and personal rivalry as by the foundations dispute. The clean "Hilbert
> expelled the intuitionist" narrative is a real simplification of a messier
> episode. Not load-bearing for the note's argument, but cite with care.
> [A 2026-04-26]: addressed in this revision — added van Dalen caveat inline and a [van Dalen 2013] source.

The technical resolution is gentler than the rhetoric. Gödel (and independently Gentzen) showed in 1933 that classical first-order arithmetic translates into intuitionistic arithmetic via a double-negation translation: each classical theorem `φ` corresponds to an intuitionistic theorem `φ*` obtained by inserting double negations, yielding an equiconsistency result (PA is consistent iff HA is) [Gödel 1933]. The translation does *not* show that classical and intuitionistic logic prove the same theorems — `φ*` is in general a strictly weaker statement than `φ`, and the negations shift its meaning. What it shows is that constructive arithmetic is not a *weaker* theory in the naive sense: it is a finer-grained theory that can host classical reasoning as a fragment while distinguishing constructive from non-constructive proofs of the same statement.

> [A reviewer 2026-04-26]: Sharper statement: Gödel-Gentzen gives an
> *equiconsistency* result (PA is consistent iff HA is) and translates each
> classical theorem `φ` to an intuitionistic theorem `φ*` whose meaning is
> shifted by the negations. Calling this an "embedding" is fine but readers
> sometimes mis-hear it as "classical and intuitionistic logic prove the same
> theorems," which is exactly false. A one-line guard would help.
> [A 2026-04-26]: addressed in this revision — restated as equiconsistency-with-translation and added an explicit guard that φ* is not in general equivalent to φ.

Each side has something the other lacks: classical logic is shorter and more familiar; intuitionistic logic carries computational content the classical version discards.

## Realizability: where the computational content lives

Kleene's realizability interpretation [Kleene 1945] made the BHK reading mathematically precise by associating each intuitionistic proof with a natural number (a Gödel-coded program) that "realizes" it: a realizer of `∃x. P(x)` is literally a pair `(n, r)` where `n` is the witness and `r` realizes `P(n)`. Realizability formalises the slogan "an intuitionistic proof is a program" decades before Curry-Howard made it a design principle for type theory. The modern picture lifts this from a Gödel-numbering trick to a categorical setting: Hyland's *effective topos* [Hyland 1982] gives realizability a topos-theoretic home in which intuitionistic higher-order logic and computability sit naturally together, and contemporary realizability mostly lives at that level.

> [A reviewer 2026-04-26]: The Kleene 1945 attribution is correct but stops
> the story 80 years short. Hyland's *effective topos* (1982) gave realizability
> a categorical home, and modern realizability lives at the topos-theoretic /
> categorical-logic level, not as a Gödel-numbering trick. If the note wants
> to be honestly minimal that's fine, but a one-line forward pointer to
> realizability toposes would situate the reader.
> [A 2026-04-26]: addressed in this revision — added a one-line forward pointer to Hyland's effective topos and the categorical view of realizability.

This is the seed of the modern view: constructive proofs and programs are the same objects under different names, and the type-theoretic foundations of Coq, Agda, and Lean inherit this directly *(see the parallel note on Curry-Howard)*. The reason proof assistants are constructive by default is not philosophical commitment to Brouwer; it is that the constructive reading is *automatic* — the proof object is a term, and the term computes. Adding LEM does not break the type theory but it does break the "proofs are programs" guarantee: a proof that uses LEM no longer reduces to a witness for the existence statements it claims.

## Why this is alive in 2026

For most working mathematicians the dispute is dormant. Analysis, algebra, and combinatorics proceed classically and nobody loses sleep over it. The places where the choice is live and operational:

- **Proof assistants.** Coq, Agda, and Lean expose `Classical` or `LEM` as an explicit axiom. Importing it is a one-line decision with a known cost: the part of the development that depends on it can no longer be extracted to executable code via the standard extraction mechanism. Lean's `mathlib` is largely classical because the goal is formalising mathematics-as-it-is-done, not mining it for programs; Coq users doing program extraction work hard to stay constructive.
- **Formal verification of software and hardware.** Here the constructive framing is not optional: you want the proof to *be* the program, or to mechanically yield one. CompCert (a verified C compiler in Coq) and the seL4 microkernel verification lean heavily on this guarantee.
- **Homotopy type theory and univalent foundations.** The cubical models that make univalence computational are constructive by design; classical principles can be added but are sharply visible when they are.

The honest framing for 2026 is therefore not "intuitionism was right and classical mathematics is wrong." It is: constructive mathematics is one valuable mode, and the value is operational — when you want a program out the other end, you want a constructive proof; when you don't, classical reasoning is faster and more familiar. Bauer's "Five stages of accepting constructive mathematics" [Bauer 2017] is an unusually candid working-mathematician's account of why the choice keeps mattering.

## Disagreements and cautions

- **"Intuitionism is the same as constructivism" is wrong but common.** Brouwer's intuitionism includes specifically Brouwerian commitments (the creating subject, choice sequences, the bar theorem) that most modern constructivists reject. Bishop's *Foundations of Constructive Analysis* [Bishop 1967] explicitly recovers a workable analysis without those commitments and is closer to what proof-assistant users mean by "constructive."
- **LEM is not always rejected, even constructively.** For *decidable* propositions — equality of natural numbers, for instance — LEM holds intuitionistically because you actually have the decision procedure. The intuitionist objects to LEM as a *universal* axiom, not to its instances where decidability is established.
- **Reverse mathematics complicates "weaker = less useful."** Some classical theorems are equivalent to non-constructive principles (König's lemma, the axiom of choice, LEM itself in suitable forms); knowing which non-constructive principle a theorem really requires is a substantive subfield, not a curiosity.
- **"Proof assistants are constructive" is a simplification.** Lean's core type theory admits classical reasoning straightforwardly and `mathlib` uses it freely. The cleaner claim is that the type theory is constructive *by default* and adding classical principles is a marked, traceable choice.

## Questions I'd like answered

1. How much of `mathlib` would actually port to a strictly constructive setting, and where does the cost concentrate? The folklore answer is "most of analysis is fine, measure theory is painful, large parts of set theory are hopeless," but I haven't seen a quantitative survey.
2. Is there a clean characterisation of which classical theorems become *significantly* weaker (not just notationally awkward) when proved constructively? Reverse mathematics gives part of the answer but not all of it.
3. Does the homotopy-type-theory programme deliver a foundation in which the classical/constructive distinction looks different — or does it just relocate the same dichotomy?
4. How do working Lean/Coq users actually decide when to reach for `Classical.em`? Is there a written norm or only tribal practice? *(my guess: mostly tribal.)*

## Sources

- [Brouwer 1907] Brouwer, L.E.J. *Over de grondslagen der wiskunde* (On the foundations of mathematics). Dissertation, University of Amsterdam, 1907. English translation in Heyting (ed.), *L.E.J. Brouwer: Collected Works*, Vol. 1, North-Holland, 1975.
- [Brouwer 1908] Brouwer, L.E.J. *De onbetrouwbaarheid der logische principes* (The unreliability of the logical principles). Tijdschrift voor Wijsbegeerte 2, 1908, pp. 152–158. English translation in Heyting (ed.), *L.E.J. Brouwer: Collected Works*, Vol. 1, North-Holland, 1975.
- [Heyting 1930] Heyting, A. *Die formalen Regeln der intuitionistischen Logik*. Sitzungsberichte der Preussischen Akademie der Wissenschaften, Physikalisch-mathematische Klasse, 1930, pp. 42–56.
- [Gödel 1933] Gödel, K. *Zur intuitionistischen Arithmetik und Zahlentheorie*. Ergebnisse eines mathematischen Kolloquiums 4, 1933, pp. 34–38. (The double-negation translation.)
- [Kleene 1945] Kleene, S.C. *On the interpretation of intuitionistic number theory*. Journal of Symbolic Logic 10(4), 1945, pp. 109–124. https://doi.org/10.2307/2269016
- [Bishop 1967] Bishop, E. *Foundations of Constructive Analysis*. McGraw-Hill, 1967.
- [Hyland 1982] Hyland, J.M.E. *The effective topos*. In Troelstra & van Dalen (eds.), *The L.E.J. Brouwer Centenary Symposium*, North-Holland, 1982, pp. 165–216.
- [van Dalen 2013] van Dalen, D. *L.E.J. Brouwer — Topologist, Intuitionist, Philosopher: How Mathematics Is Rooted in Life*. Springer, 2013.
- [Bauer 2017] Bauer, A. *Five stages of accepting constructive mathematics*. Bulletin of the American Mathematical Society 54(3), 2017, pp. 481–498. https://doi.org/10.1090/bull/1556

## Links

- [[curry-howard-programs-are-proofs]] — the strongest connection: Curry-Howard is the formal articulation of "an intuitionistic proof is a program," and the reason proof assistants are constructive by default is that the type-theoretic side of the correspondence inherits intuitionistic logic for free; classical extensions require additional principles (continuations, control operators, or an axiomatic LEM) that visibly disrupt the program-extraction story.
- [[four-color-theorem-and-computer-assisted-proof]] — secondary connection: Gonthier's Coq formalisation of the four-colour theorem lives inside this constructive setting, and the choice of how much classical reasoning to admit is a design decision in any large mechanised proof.

> [A reviewer 2026-04-26]: Agreed the parallel is loose; I'd go further and
> suggest dropping this link entirely. The "proof-of-existence at one level
> secures the thing at another" framing is a stretch — constructive/classical
> is about evidence inside one logical system; the hard problem is about
> ontological levels. The conventions file says links should be compare/contrast
> with substantive relationships, and this one fails that bar by the note's
> own admission.
> [A 2026-04-26]: addressed in this revision — dropped the [[hard-problem-consciousness]] link; the parallel didn't meet the compare/contrast bar.
