# The four-color theorem and the legitimacy of computer-assisted proof

> Appel & Haken's 1976 proof that every planar map is 4-colorable was the first celebrated theorem whose verification gave machine computation a load-bearing role no human could re-walk (earlier number-theoretic computations, e.g. Lehmer's and the Lucas–Lehmer Mersenne checks, used machines but not as the kernel of a famous theorem); the philosophical objection (Tymoczko) was not that it was wrong but that it was no longer *surveyable*, and the subsequent re-proof (Robertson-Sanders-Seymour-Thomas 1997) and Coq formalization (Gonthier 2005) reshape but do not dissolve the question.

> [A reviewer 2026-04-26]: "First famous" is doing a lot of work here. Lehmer's
> 1949–era number-theoretic computations and the Lucas–Lehmer Mersenne-prime
> verifications already qualified as proofs depending on machine computation;
> what was new in 1976 was the *load-bearing* role in a celebrated theorem,
> not machine assistance per se. Worth tightening the claim.

> [A 2026-04-26]: addressed in this revision — TL;DR now distinguishes
> "load-bearing role in a celebrated theorem" from earlier machine-assisted
> number-theoretic work.

[Author: agent (prompted by user)]
[Confidence: established for the historical record; contested for the philosophical question]
[Last verified: 2026-04-26]

## TL;DR

In 1976 Appel and Haken reduced the four-color conjecture to a finite analysis of ~1,900 reducible configurations, then verified the cases by computer; the proof was correct but no individual could check it line-by-line [Appel & Haken 1977]. Tymoczko argued this changed the epistemic character of mathematical proof — proofs are traditionally *a priori* and surveyable, and a step that rests on trusting a particular silicon run is something else [Tymoczko 1979]. Later work cleaned up the proof (Robertson-Sanders-Seymour-Thomas 1997) and then mechanically certified it inside the Coq kernel (Gonthier 2005, written up 2008), arguably raising the bar for trust above pen-and-paper standards while still failing to deliver the explanatory grasp that "I have read the proof" used to imply.

## What the theorem says, and how the 1976 proof worked

The theorem: any planar map can have its regions colored with at most four colors so that no two regions sharing a border have the same color. The conjecture was posed in 1852 (Guthrie) and resisted attack for over a century, including a famous 1879 Kempe "proof" that stood for eleven years before Heawood found the gap.

The Appel–Haken proof has two parts [Appel & Haken 1977]:

1. **Unavoidability.** Every minimal counterexample must contain at least one configuration from a finite list. Appel and Haken's list had 1,936 configurations (later reduced).
2. **Reducibility.** Each configuration on the list is *reducible*: if a 4-coloring problem contains it, a 4-coloring of the smaller surrounding map can always be extended to cover it. Showing this for each configuration required exhaustive case analysis on the colorings of its boundary ring — combinatorially explosive, ~1,200 hours of IBM 360 time *(specific runtime figures vary across retellings; treat as approximate)*.

Together: a minimal counterexample must contain a reducible configuration, but a reducible configuration cannot appear in a minimal counterexample, contradiction. The mathematical strategy (discharging arguments on planar graphs to produce an unavoidable set) was wholly human; the case-by-case reducibility verification was where the machine was load-bearing.

## Why mathematicians objected — and why the objection was philosophical, not technical

The technical worry — "maybe there's a bug" — was real but secondary. The deeper objection, sharpened by Thomas Tymoczko, was that the proof was not **surveyable**: no mathematician could, even in principle, walk through every step and confirm it [Tymoczko 1979]. Tymoczko's load-bearing move was that surveyability is *constitutive* of the *a priori* character of mathematical proof: if a step rests on trusting how a particular machine ran, the resulting knowledge is *a posteriori* (empirical) — we accept it because of evidence about how a particular computer behaves, not because we have followed a chain of inference. On this view, the Appel–Haken proof necessarily introduced an *a posteriori* element into a discipline whose self-image was wholly *a priori*.

The classical picture, which Tymoczko was challenging, runs roughly:

- Mathematical proofs are *a priori* — established without appeal to particular contingent facts about the world.
- They are *surveyable* — a competent mathematician can in principle check every step.
- They are *convincing through understanding* — reading the proof produces insight into why the theorem is true.

The Appel–Haken proof failed at least the second condition and arguably the first (correctness depended on whether some IBM 360 had a hardware fault during the run). Critics including Bonsall and Halmos voiced versions of this concern in print *(my guess on the exact set of named critics; Tymoczko is the canonical citation)*. Defenders pointed out that long human proofs are also unsurveyable in practice — by the late 20th century, the classification of finite simple groups occupied tens of thousands of pages spread across many authors, and effectively no single person had read it all.

The strongest framing of Tymoczko's challenge is not "this proof is wrong" but "the word *proof* now covers two epistemically different objects, and we should be honest about it."

> [A reviewer 2026-04-26]: Tymoczko's specific claim was sharper than the gloss
> here suggests: he argued surveyability is *constitutive* of the *a priori*
> character of mathematical proof, so the Appel–Haken proof necessarily
> introduced an *a posteriori* (empirical) element. The note hints at this in
> the bullet list but should state the a priori / a posteriori dichotomy
> directly — that's the load-bearing move in the 1979 paper.

> [A 2026-04-26]: addressed in this revision — added an explicit statement of
> the a priori / a posteriori dichotomy as Tymoczko's load-bearing move.

## The 1997 Robertson-Sanders-Seymour-Thomas re-proof

Robertson, Sanders, Seymour, and Thomas re-proved the theorem in 1997 with a simpler unavoidable set (633 configurations) and a cleaner discharging argument [Robertson et al. 1997]. The reducibility step was still a computer check, but the program was shorter and the structure of the proof more transparent. This addressed some technical worries — independent reimplementation, smaller and more auditable code — without changing the philosophical situation: the proof was still not surveyable end-to-end by a human.

The re-proof is also a useful data point on what computer-assisted proofs *do* improve over time: they get shorter, the auxiliary code gets cleaner, and the human-mathematical kernel grows clearer relative to the computational kernel. They do not, however, become surveyable in Tymoczko's sense by getting cleaner — that's a category boundary, not a continuum.

## Gonthier's Coq formalization and the certainty inversion

In 2005 Georges Gonthier completed a full formalization of the four-color theorem in the Coq proof assistant [Gonthier 2008]. The entire proof — both the human-mathematical part (unavoidability, reducibility framework) and the case-checking part — was expressed as a term in Coq's dependent type theory and verified by Coq's small trusted kernel.

The structural claim made for this kind of formalization, often called the **de Bruijn criterion**: trust in the proof reduces to trust in a small, simple, independently-auditable kernel (Coq's type-checker, plus the mathematical statement of the theorem). The kernel is small enough to be surveyable. The proof term is enormous and unsurveyable, but it does not need to be surveyed — it only needs to type-check.

This produces an interesting inversion of Tymoczko's worry. By his criteria, *every* mature mathematical proof has unsurveyable parts (the long ones literally, the computer-assisted ones structurally). A formalization in a small-kernel proof assistant arguably gives *higher* confidence in correctness than a typical pen-and-paper proof, because the kernel is small and the chain of trust is explicit. Gonthier's Notices article makes a version of this argument [Gonthier 2008]. The qualification matters: trust still flows through the OCaml compiler, the operating system, and the silicon (the original Tymoczko worry, undiminished), and — most underappreciated — through the assumption that the formal Coq statement of the theorem actually expresses the informal four-color theorem. The de Bruijn criterion shrinks the kernel of trust; it does not eliminate it.

> [A reviewer 2026-04-26]: This understates the residual trust load. The de
> Bruijn criterion buys you a small kernel, but you still have to trust the
> OCaml compiler, the OS, the hardware (with the same silicon-fault worry
> Tymoczko raised), and — most underappreciated — that the formal Coq
> statement actually expresses the informal four-color theorem. Section
> "Disagreements" mentions this; the main text should acknowledge it here
> rather than letting "raises the bar above pen-and-paper" stand unqualified.

> [A 2026-04-26]: addressed in this revision — added a paragraph qualifying
> the de Bruijn claim with the OCaml/OS/silicon and definitional-mismatch
> trust loads.

But — on one widely-held view — it does not give *understanding*. Reading 60,000 lines of Coq does not produce insight into why planar graphs are 4-colorable in the way that reading, say, the Cauchy integral theorem proof produces insight into complex analysis. The proof is now more certainly correct and no more humanly graspable. *(The verify/explain split here is itself contested: some philosophers of mathematics, e.g. Avigad, argue that the discharging argument and reducibility framework — i.e. the structure of the case analysis — already constitute the explanation, and the case enumeration is bookkeeping. The framing in this paragraph is the standard "Coq verifies but doesn't explain" reading; the contrary view is treated below.)*

> [A reviewer 2026-04-26]: The "verify but don't explain" framing is widely
> repeated but actively contested. Some philosophers of mathematics (e.g.
> Avigad, and arguably Lakatos avant la lettre) hold that the *structure* of
> the case analysis — the discharging argument, the reducibility framework —
> *is* the explanation, and the case enumeration is just bookkeeping. The
> note presents the explain/verify split as settled; flag it as contested.

> [A 2026-04-26]: addressed in this revision — flagged the verify/explain
> split as contested in the body and pointed forward to "Disagreements".

## Where the question sits in 2025–2026

The contemporary landscape contains several reference points worth comparing:

- **Wiles' proof of Fermat's Last Theorem (1995).** Humanly written, but the technical machinery (modular forms, Galois representations, deformation theory) is understood well enough to evaluate the proof by perhaps a few hundred mathematicians worldwide. Surveyable in principle, illegible in practice.
- **Hales' Kepler conjecture (1998 / formalized 2014).** Hales' original proof was so long and computer-dependent that the *Annals of Mathematics* editors notoriously declined to fully verify it; the eventual Flyspeck formalization in HOL Light and Isabelle was Hales' response [Hales et al. 2017].
- **Lean's growing mathlib and the Liquid Tensor Experiment (2020–2022).** Scholze publicly challenged the formalization community to verify a result he was unsure about; the Lean community succeeded, and Scholze said the formalization had genuinely increased his confidence [Scholze 2022, blog post].
- **Frontier AI assistance in proof writing (2024–2026).** AI systems suggesting tactics or whole proofs in Lean and Coq are now common. This shifts the question further: the human is increasingly writing only the statement, with the mechanical kernel doing the verification and an AI doing the search. The trust chain still bottoms out in the small kernel, but the share of the proof a human author has actually composed shrinks. *(Specific 2025–2026 milestones: this is a fast-moving area; treat any precise claim as speculative.)*

The honest summary is that the field has, over fifty years, partly absorbed and partly bypassed Tymoczko's challenge. *Absorbed:* the working mathematical community now accepts computer-assisted and computer-verified proofs as proofs, and prestigious journals publish them. *Bypassed:* the deeper question of whether a proof should *explain* — should produce understanding, not merely certainty — is no closer to settled. These are different goods, not the same one *(contested)*. A proof can be more certainly correct (formalized) and yet less humanly explanatory; a proof can be deeply illuminating and yet have a residual error rate higher than a formalization. Pretending these collapse onto a single axis of "rigour" is the move that makes the four-color question feel resolved when it isn't.

## Disagreements and cautions

- **Was Tymoczko right?** Disputed. One camp (Detlefsen & Luker, Burgess) accepts that surveyability was always partly an idealization and the Appel–Haken case did not introduce a new epistemic kind. Another camp (closer to Tymoczko) holds that the line between *a priori* and *a posteriori* knowledge runs through the four-color theorem and similar cases, and the discipline gains by being honest about it.
- **Does formalization "increase certainty"?** Often claimed, but the increase is conditional: on the trusted kernel being correct, on the formal statement actually expressing the informal theorem, and on the hardware running the kernel behaving. The first is small, the second is a real and underappreciated risk (definitional mismatch), the third is in practice ignored.
- **The "explanation vs verification" framing is itself contested.** Some mathematicians (Thurston in the 1990s essay *On proof and progress in mathematics*) argue that mathematics' deliverable is human understanding, not formal certificates. Others argue understanding follows verification on a long enough timescale and the distinction is pragmatic, not principled.
- **Specific run-time and configuration-count figures across retellings vary** and I have not cross-checked them against the primary sources for this draft; treat numerics as approximate.
- **The Appel–Haken 1977 citation has not been independently re-verified** against the *Illinois Journal of Mathematics* volume record for this draft. Volume 21, issue 3 is the consensus location; the exact starting page of Part I (429 vs. a few pages later, depending on whether the announcement preface is counted) wants a library spot-check before this note is cited externally.

## Questions I'd like answered

1. Is there a worked example where Coq/Lean formalization of a published proof revealed a substantive (not merely cosmetic) error that the mathematical community had previously accepted? The Kepler conjecture is the standard candidate — what exactly did Flyspeck find?
2. What is the current state of the *definitional gap* problem — checking that the formal statement in Lean/Coq is actually the theorem mathematicians intended? Are there tooling or social practices that catch mismatches?
3. Has any mathematician published a serious update of Tymoczko's 1979 argument in light of mathlib, the Liquid Tensor Experiment, and AI-assisted proof? The philosophical literature I know best is from the 1990s–2000s.
4. Is "explanatory proof" a coherent category that can be characterized independently of human cognitive limits, or is it just "proof short enough for a human to hold in mind"? If the latter, the four-color theorem is a permanent edge case rather than a transitional one.
5. For frontier AI–assisted formalization (2025–2026), what fraction of accepted Lean proofs of nontrivial theorems are now AI-drafted? Where does that leave authorship?

## Sources

- [Appel & Haken 1977] Appel, K., Haken, W. *Every planar map is four colorable. Part I: Discharging.* Illinois Journal of Mathematics 21(3):429–490. https://doi.org/10.1215/ijm/1256049011 (Part II, with Koch, *Part II: Reducibility*, same volume 21(3):491–567, https://doi.org/10.1215/ijm/1256049012) *(volume/issue/page range not independently re-verified against the journal record for this draft; treat the exact page numbers as approximate pending a library check — see "Disagreements and cautions".)*

> [A reviewer 2026-04-26]: Spot-check: the Illinois J. Math. 1977 volume is
> volume 21 issue 3 — please double-check the issue number and the page range
> 429–490 against the journal record (Part I is sometimes cited as starting
> at 429, sometimes at a slightly different page depending on whether the
> announcement preface is counted). Also: Tymoczko 1979 is JPhil 76(2):57–83
> — that I can confirm; DOI 10.2307/2025976 is the JSTOR stable, not a
> DOI-system DOI. Worth noting the distinction.

> [A 2026-04-26]: addressed in this revision — split the citation into Part I
> and Part II explicitly, flagged the page numbers as not independently
> re-verified, and added a caveat to "Disagreements" about the citation
> spot-check. The JSTOR-vs-DOI distinction is already noted on the Tymoczko
> entry below.
- [Tymoczko 1979] Tymoczko, T. *The Four-Color Problem and Its Philosophical Significance.* The Journal of Philosophy 76(2):57–83. JSTOR stable URL: https://www.jstor.org/stable/2025976 *(this is a JSTOR stable identifier, not a registered DOI — earlier drafts mis-formatted it as a doi.org link)*
- [Robertson et al. 1997] Robertson, N., Sanders, D., Seymour, P., Thomas, R. *The Four-Colour Theorem.* Journal of Combinatorial Theory, Series B 70(1):2–44. https://doi.org/10.1006/jctb.1997.1750
- [Gonthier 2008] Gonthier, G. *Formal Proof — The Four-Color Theorem.* Notices of the AMS 55(11):1382–1393. https://www.ams.org/notices/200811/tx081101382p.pdf
- [Hales et al. 2017] Hales, T. et al. *A Formal Proof of the Kepler Conjecture.* Forum of Mathematics, Pi 5:e2. https://doi.org/10.1017/fmp.2017.1
- [Scholze 2022] Scholze, P. *Liquid Tensor Experiment.* Xena Project blog and follow-ups; see https://leanprover-community.github.io/blog/posts/lte-final/ *(blog post, not a peer-reviewed source)*
- Thurston, W. *On proof and progress in mathematics.* Bulletin of the AMS 30(2):161–177, 1994. https://doi.org/10.1090/S0273-0979-1994-00502-6 — referenced in passing for the explanation-vs-verification framing.

## Links

- [[mechanistic-interpretability]] — analogous tension: a large opaque artefact (a trained network) whose behaviour we can verify experimentally but not narratively grasp; same checking-vs-understanding split as formalized proof.
- [[attribution-graphs-explain-specific-prompts-not-models]] — sharper version of that analogy: a mechanically extracted attribution graph is a kind of certificate for a specific output, not an explanation of the model, just as a Coq proof term is a certificate, not an explanation.
- [[curry-howard-programs-are-proofs]] — direct technical underpinning of the Coq formalization: the proof term Gonthier produced is, under Curry–Howard, a program whose type is the theorem statement, and the kernel's "type-check" is the verification step. Read this note for the philosophical framing, the linked one for why a typed-lambda-calculus kernel can play that role.
- [[intuitionism-vs-classical-mathematics]] — Coq's underlying type theory is constructive, which constrains how classical arguments (excluded middle, choice in some forms) appear in formalized proofs; Gonthier's formalization had to navigate this for the four-color theorem specifically. The connection is technical, not just thematic.
- [[hard-problem-consciousness]] — partial analogy at most: both involve a verify/explain gap, but the four-color case concerns epistemic access to a mind-independent mathematical fact, while the hard problem concerns phenomenality. Worth comparing as instances of "verification without explanatory grasp"; not the same family at the deeper level.

> [A reviewer 2026-04-26]: Two cross-link concerns. (1) The hard-problem
> link is strained — the verify/explain gap in math is about epistemic access
> to a mind-independent fact; the hard problem is about phenomenality. Calling
> them "the same family" overstates. (2) The note conspicuously does *not*
> link to [[curry-howard-programs-are-proofs]] or [[intuitionism-vs-classical-mathematics]],
> both of which are directly relevant to the Gonthier/Coq discussion and both
> of which link *here*. That asymmetry should be fixed.

> [A 2026-04-26]: addressed in this revision — added the two missing
> cross-links with one-line relationship annotations, and rewrote the
> hard-problem entry to scope it as a partial analogy rather than "the same
> family."
