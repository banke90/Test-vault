# The Curry-Howard correspondence: programs are proofs, types are propositions

> An intuitionistic proof and a typed lambda term are the same object viewed from two angles; this is what makes a type-checker into a proof-checker, and it is the engineering substrate of every modern proof assistant.

[Author: agent (prompted by user)]
[Confidence: established for the core correspondence; mixed for the philosophical reach of the homotopy and category-theoretic extensions]
[Last verified: 2026-04-26]

## TL;DR

Curry-Howard is the observation that simply-typed lambda calculus and intuitionistic propositional logic are *the same formal system* under a renaming: types are propositions, terms are proofs, and beta-reduction is proof normalisation [Howard 1980; Wadler 2015]. Extended to dependent types, this correspondence makes constructing a term of a given type *equal* to proving a theorem, which is why Coq, Lean, and Agda are simultaneously programming languages and proof assistants. The correspondence is native to *intuitionistic* logic; classical reasoning requires extra machinery (call/cc, double-negation translation), and that constraint is a real feature of the landscape, not a footnote.

## The core correspondence

The dictionary is small and exact:

| Logic (intuitionistic) | Type theory (lambda calculus) |
|---|---|
| proposition `A` | type `A` |
| proof of `A` | term `t : A` |
| implication `A → B` | function type `A → B` |
| conjunction `A ∧ B` | product type `A × B` |
| disjunction `A ∨ B` | sum type `A + B` |
| `⊥` (falsehood) | empty type `0` |
| `⊤` (truth) | unit type `1` |
| universal `∀x:A. P(x)` | dependent product `Π x:A. P(x)` |
| existential `∃x:A. P(x)` | dependent sum `Σ x:A. P(x)` |
| proof normalisation (cut elimination) | program evaluation (beta-reduction) |

The last row is the deepest part. When you simplify a proof by removing detours (Gentzen's cut elimination), you are doing the same *operation* as evaluating a program by reducing redexes [Wadler 2015]. The two communities discovered the same dynamics from opposite sides. The strict bijection is between *normal-form* proofs and *normal-form* terms; calling the whole package an "isomorphism" or "the same formal system" is shorthand for that sharp core plus the dynamics that connect non-normal forms to it, and is mildly looser than the underlying theorem.

> [A reviewer 2026-04-26]: The note uses "isomorphism" (per Sorensen-Urzyczyn's
> title) and "same formal system" interchangeably with "correspondence". Strictly,
> the bijection between proofs-in-normal-form and terms-in-normal-form is what
> is sharp; calling the whole package an isomorphism without that scoping is
> the standard mild overstatement. Worth a single qualifying clause somewhere.
> [A 2026-04-26]: addressed in this revision — added a qualifying clause scoping the bijection to normal forms.

A worked instance: a closed term of type `A → A` is necessarily, up to eta, the identity function `λx.x`, and the corresponding proof of `A → A` is "assume `A`; conclude `A`". A closed term of type `A → B → A` is `λx.λy.x` (the K combinator), corresponding to the proof "assume `A`, assume `B`, return the assumption of `A`" — i.e. the axiom `A → (B → A)`. There is no closed term of type `A` for arbitrary `A`, mirroring the fact that an arbitrary proposition is not provable.

## A short history

- **Curry, 1934** *(my guess on the exact year — Curry's combinator-typing observation predates the full statement and was published in stages; the canonical book reference is Curry & Feys 1958, *Combinatory Logic Vol. I*)*: Curry noticed that the types of combinators in his combinatory logic mirror the axioms of intuitionistic implicational logic. The K combinator's type is the K axiom; the S combinator's type is the S axiom. This is a structural observation about combinator typing, *not* yet the explicit propositions-as-types claim — that is Howard's, three decades later.
- **Howard, 1969 manuscript, formally published 1980**: *The formulae-as-types notion of construction* circulated as a typescript for over a decade before appearing in the Festschrift *To H.B. Curry: Essays on Combinatory Logic, Lambda Calculus and Formalism* [Howard 1980]. Howard extended Curry's combinator observation to the full simply-typed lambda calculus and to first-order intuitionistic logic, and explicitly named the proof-normalisation / program-evaluation correspondence.
- **De Bruijn, late 1960s onward**: independently developed the AUTOMATH system on essentially the same insight — proofs as terms in a typed lambda calculus — and produced the first working machine-checked formalisations.
- **Martin-Löf, 1970s**: built **intuitionistic type theory** with dependent types, making the correspondence carry full first-order logic and providing the design template every modern proof assistant follows.

> [A reviewer 2026-04-26]: The Curry 1934 attribution is for the combinator-typing
> observation only; the explicit propositions-as-types statement is Howard's,
> and the note's own parenthetical already flags the year is a guess. The
> bullet's framing is fine but a reader could come away thinking Curry
> stated the correspondence in 1934, which he did not.
> [A 2026-04-26]: addressed in this revision — added an explicit clause separating Curry's structural observation from Howard's propositions-as-types claim.

## What the correspondence buys

The practical payoff is a single sentence: **proving a theorem is constructing a term of a given type, and a type-checker is a proof-checker**. This is why Coq, Lean, Agda, Idris, and F* are not "programming languages with proof features bolted on" — they are typed lambda calculi rich enough that their type system *is* the logic [Sørensen & Urzyczyn 2006].

Concretely:

- Stating a theorem = writing down a type.
- Proving the theorem = writing a term of that type.
- Checking the proof = the type-checker checks the term.
- Proof tactics (Coq's `Ltac`, Lean's tactic mode) = metaprograms that *build* terms; the kernel still type-checks the resulting term.

The trust story collapses to "do you trust the kernel type-checker?" Kernels are deliberately small (Coq's is a few thousand lines of OCaml; Lean 4 has a similarly small core [de Moura & Ullrich 2021]) so that this trust is achievable in practice.

## Why this is the foundation under modern proof assistants

A non-exhaustive list of formalisations that exist *because* the correspondence is real:

- **Four-color theorem**, Gonthier 2005, in Coq. The first major theorem whose original proof was already computer-assisted to be re-verified end-to-end inside a kernel-checked system. See [[four-color-theorem-and-computer-assisted-proof]].
- **Feit-Thompson odd-order theorem**, Gonthier et al. 2012, in Coq. ~150,000 lines. A landmark of pure mathematics formalised at full depth.
- **CompCert** [Leroy 2009 onward]: a C compiler proved correct in Coq. Used in safety-critical avionics.
- **seL4** [Klein et al. 2009]: an OS microkernel proved correct in Isabelle/HOL — adjacent to Curry-Howard rather than directly built on it (HOL is classical) but shares the "proof-as-checked-term" engineering.
- **Lean's mathlib** [de Moura & Ullrich 2021]: a community-built library of formalised mathematics that has become a working tool for research-level mathematicians; Kevin Buzzard's program of "formalising undergraduate mathematics, then research mathematics" is the active edge.

The shift visible across the 2010s–2020s is that formal verification moved from curiosity to working tool *for those who choose to use it*. mathlib is at the multi-million-line scale and growing, but the published mathematical literature dwarfs it by orders of magnitude, and the majority of working mathematicians still do not use a proof assistant in their day-to-day work. *(established for the engineering systems; mixed for the claim about working mathematicians — adoption is real on the active edge but remains a minority practice.)*

> [A reviewer 2026-04-26]: "Working tool" is fair; "arrived" would be too strong.
> mathlib is a few million lines and growing fast, but the published mathematical
> literature dwarfs it by orders of magnitude, and most working mathematicians
> still do not use a proof assistant. The hedge in the parenthetical is doing
> real work and could be stronger.
> [A 2026-04-26]: addressed in this revision — strengthened the hedge in body and parenthetical to reflect minority-practice adoption.

## Extensions: Curry-Howard-Lambek and homotopy type theory

Two extensions are worth naming, and worth labelling as extensions rather than as the core:

- **Curry-Howard-Lambek**: Lambek showed that **cartesian closed categories** are a third equivalent face of the same structure — types/propositions become objects, terms/proofs become morphisms, function types become exponentials. This is the categorical-logic strand and underwrites a lot of subsequent semantic work.
- **Homotopy Type Theory (HoTT)** [HoTT Book 2013]: Voevodsky and others observed that in Martin-Löf type theory, the identity type `Id_A(x, y)` behaves like a *path space* in a topological sense. Propositions become spaces, proofs become points, proofs of equality become paths between points, and higher equalities become higher paths. Univalence ("equivalent types are equal") is the additional axiom that makes this strict. HoTT is mathematically beautiful and has produced real formalisations, but its status as a *foundational* alternative to ZFC remains a live question rather than a settled win. *(contested at the foundational level; established as a working type theory with implementations in Coq and Agda.)*

## The intuitionistic constraint

Curry-Howard, in its native form, gives you intuitionistic logic. The law of excluded middle (`A ∨ ¬A`) and double-negation elimination (`¬¬A → A`) are *not* inhabited by closed lambda terms in general — there is no constructive program that, given any proposition, returns a proof or a refutation.

Three responses exist, none free:

1. **Stay intuitionistic.** Most of constructive mathematics fits, and the correspondence is clean. See [[intuitionism-vs-classical-mathematics]].
2. **Add classical axioms as opaque constants.** You can postulate excluded middle in Coq or Lean. The resulting "proof" is no longer a closed normalising term — it contains an axiom that does not reduce — but it is still kernel-checked.
3. **Take the classical correspondence on its own terms.** Griffin 1990 showed that Felleisen's `call/cc` (call-with-current-continuation) inhabits Peirce's law `((A → B) → A) → A`, which is classically valid but not intuitionistically — and this was not a one-off trick. Parigot's λμ-calculus [Parigot 1992] turned the same insight into a proper term calculus for classical natural deduction, with confluent reduction, a strong-normalisation theorem, and continuation-passing-style semantics that match the double-negation translation. The result is a *classical* Curry-Howard programme parallel to the intuitionistic one: classical proofs are programs with first-class control, and proof normalisation is the evaluation of those programs. The Gödel-Gentzen double-negation translation sits inside this picture as the static / CPS counterpart to the dynamic control-operator reading. The intuitionistic side remains the cleaner default for proof assistants because computational content stays direct, but "classical Curry-Howard" is a developed area, not a footnote.

> [A reviewer 2026-04-26]: This frames the classical case as a workaround, but
> Griffin 1990 plus Parigot's lambda-mu calculus (1992) launched a full
> classical Curry-Howard programme with its own normalisation theory and
> semantics — not merely a "control-operator trick." Worth naming lambda-mu
> alongside call/cc so the classical side reads as a genuine parallel rather
> than an awkward extension.
> [A 2026-04-26]: addressed in this revision — rewrote the classical bullet to name λμ-calculus and frame classical Curry-Howard as a parallel programme rather than a workaround; added Parigot 1992 to Sources.

The constraint is not a curiosity. It shapes what proof assistants *natively* prove and what they require axioms or tricks for. Lean's mathlib accepts classical logic as standard; Agda communities tend to stay closer to the intuitionistic core. The choice is real.

## Disagreements and cautions

- **"Same system" is precise but easy to overstate.** The correspondence is an isomorphism between specific formal systems (simply-typed lambda calculus ↔ intuitionistic propositional logic, MLTT ↔ predicate logic with constructive interpretation). It is not a general claim that *any* program is a proof of *some* useful proposition — most programs have types so weak (e.g. `Int → Int`) that the corresponding proposition is trivially true. The bite comes from rich types.
- **HoTT's foundational claims are contested.** Whether univalent foundations should replace set-theoretic foundations is a real philosophical dispute, not a settled triumph. Treat HoTT as "a productive type theory with deep geometric content" rather than "the new foundation."
- **Proof assistants are not magic.** A formalisation can encode the wrong theorem, or rely on axioms that quietly weaken the result. `#print axioms` in Lean is the standard hygiene. Gonthier's four-color formalisation is trusted partly because the axioms it invokes are minimal and inspected.
- **Classical mathematicians sometimes dismiss the intuitionistic restriction as pedantry.** This is wrong but understandable. For most working mathematics, classical logic with judicious axioms inside a proof assistant is fine. The intuitionistic constraint becomes load-bearing when you care about *computational content* — when you want the proof to be a program you can run.

## Questions I'd like answered

1. How far can the homotopy interpretation be pushed before it breaks, e.g. for proof assistants that don't natively support higher inductive types?
2. Is there a clean Curry-Howard-style correspondence for *linear* logic and concurrent / resource-aware computation that has reached the same level of practical leverage as the intuitionistic case? (Linear logic ↔ session types is the candidate; how mature is the correspondence in practice?)
3. What is the right way to think about *classical* proofs as programs given the call/cc reading? Is the continuation-passing interpretation the canonical one, or are there competing readings with different practical consequences?
4. As Lean's mathlib grows, does the *shape* of formalised mathematics start to differ from the shape of paper mathematics — and if so, is that a sign of new mathematical structure or of formalisation artefacts?

## Sources

- [Howard 1980] Howard, W. A. *The formulae-as-types notion of construction*. In *To H. B. Curry: Essays on Combinatory Logic, Lambda Calculus and Formalism*, eds. Seldin & Hindley, Academic Press 1980. (Original 1969 manuscript.)
- [Curry & Feys 1958] Curry, H. B., Feys, R. *Combinatory Logic, Volume I*. North-Holland.
- [Wadler 2015] Wadler, P. *Propositions as Types*. Communications of the ACM 58(12), 75–84. https://homepages.inf.ed.ac.uk/wadler/papers/propositions-as-types/propositions-as-types.pdf — the standard accessible introduction; recommended starting point.
- [Sørensen & Urzyczyn 2006] Sørensen, M. H., Urzyczyn, P. *Lectures on the Curry-Howard Isomorphism*. Studies in Logic and the Foundations of Mathematics vol. 149, Elsevier. The standard textbook treatment.
- [HoTT Book 2013] The Univalent Foundations Program. *Homotopy Type Theory: Univalent Foundations of Mathematics*. https://homotopytypetheory.org/book/
- [de Moura & Ullrich 2021] de Moura, L., Ullrich, S. *The Lean 4 Theorem Prover and Programming Language*. CADE 2021. https://leanprover.github.io/papers/lean4.pdf
- [Griffin 1990] Griffin, T. G. *A formulae-as-types notion of control*. POPL 1990. The classical-logic-via-control-operators paper.
- [Parigot 1992] Parigot, M. *λμ-calculus: an algorithmic interpretation of classical natural deduction*. LPAR 1992, LNCS 624, 190–201. The term calculus that established classical Curry-Howard as a programme with its own normalisation theory.
- [Gonthier 2008] Gonthier, G. *Formal proof — the four-color theorem*. Notices of the AMS 55(11), 1382–1393. https://www.ams.org/notices/200811/tx081101382p.pdf
- [Leroy 2009] Leroy, X. *Formal verification of a realistic compiler*. CACM 52(7). The CompCert paper.
- [Klein et al. 2009] Klein, G. et al. *seL4: Formal verification of an OS kernel*. SOSP 2009.

## Links

- [[four-color-theorem-and-computer-assisted-proof]] — the strongest cross-link: Gonthier's Coq formalisation of the four-color theorem is a direct application of Curry-Howard at scale, and is the canonical example of "the kernel is the proof-checker" in mainstream mathematics.
- [[intuitionism-vs-classical-mathematics]] — the philosophical and logical context of the intuitionistic constraint discussed above; Curry-Howard is most natural under intuitionistic logic, and the classical extensions cost something real.
- [[mechanistic-interpretability]] — distant structural parallel only: both are projects of "make a computational artefact legible as a named structure." Curry-Howard makes proofs legible as programs by construction; mechanistic interpretability tries to read programs *out of* learned networks after the fact. Annotate carefully — the parallel is suggestive, not deep.
- [[induction-heads-are-the-archetypal-circuit]] — same structural parallel, narrower: an induction circuit is a small algorithm extracted from a network; a proof term is a small program extracted from a logical derivation. The directions of construction are opposite.

> [A reviewer 2026-04-26]: The mech-interp links are honestly hedged ("distant
> structural parallel only", "annotate carefully — the parallel is suggestive,
> not deep"). Good. This is the right register for this kind of cross-link
> and it should stay this hedged; the temptation to upgrade it later should
> be resisted.
