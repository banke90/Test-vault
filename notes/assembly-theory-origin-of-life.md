# Assembly theory proposes a measure of complexity-from-selection — useful for biosignatures, philosophically overstretched

> Cronin and Walker's assembly index counts the minimum number of step-wise joining operations (with re-use) needed to build an object; the empirical claim that high-assembly molecules in many copies signal life is operationally promising; the broader claims (new theory of evolution, time intrinsic to objects) are weaker than the headline papers suggest.

[Author: agent (prompted by user)]
[Confidence: contested — strong on the empirical pitch, weak on the philosophical extension]
[Last verified: 2026-04-21]

## TL;DR

Assembly Theory (AT), developed by chemist **Lee Cronin** (Glasgow) and theoretical physicist **Sara Walker** (ASU), proposes the **assembly index** — the minimum number of bond-forming steps (with re-use of substructures) needed to build a molecule from elementary parts. They argue (and show empirically with tandem mass spectrometry) that molecules with assembly index above ~15, present in many copies, are reliably found only in biological samples, making this a candidate **agnostic biosignature** for life detection [Marshall et al. 2021]. The 2023 *Nature* paper [Sharma et al. 2023] extended AT into a claimed unifying framework for selection and evolution, with Walker also proposing time as intrinsic to objects rather than a coordinate. Reception of the empirical work is moderately positive; reception of the theoretical extension has been sharp, with critics arguing that AT either reduces to Bennett's logical depth / Gell-Mann-Lloyd effective complexity, or oversells what is essentially a useful but bounded computable measure [critiques by Hazen, Jaeger, Zenil, Abrahão].

## What the assembly index is

For an object built from identifiable units, the **assembly index** *a* is the minimum number of steps along any pathway that constructs it from elementary parts, where each step combines two previously-built subobjects. **Re-use** is counted once per construction, not once per appearance — so repeated motifs reduce the count.

Trivial example: assembling `ABAB` takes 3 steps under re-use — A, B, combine to AB, combine AB with AB. Without re-use it would take 4 steps (build AB, build another AB, combine).

Applied to molecules: units are bonds or fragments; the index is the shortest pathway of bond-forming steps. The **molecular assembly index** (MA) is computable from the molecule's graph structure *(established as a definition; computability is polynomial for small molecules)*.

The full **assembly equation** combines the index with a population measure:

$$A = e^{a} \cdot \frac{N - 1}{N_0}$$

where *a* is the assembly index, *N* the number of detected copies of the object, *N₀* a normalisation. Intuition: many copies of something hard to build is strong evidence of selection. One complicated molecule could be a lucky accident; a billion copies of a specific complicated molecule cannot.

## Key papers

- **Marshall, Murray, Cronin 2017** [Marshall et al. 2017]: "A probabilistic framework for identifying biosignatures using Pathway Complexity." *Phil. Trans. Royal Soc. A*. Conceptual foundation.
- **Marshall, Moore, Murray, Walker, Cronin 2021** [Marshall et al. 2021]: *Nature Communications*. The empirical paper. Tandem MS fragmentation data on biotic and abiotic samples; argues MA > ~15 is a biotic-only signature.
- **Sharma, Czégel, Lachmann, Kempes, Walker, Cronin 2023** [Sharma et al. 2023]: *Nature*. The theoretical extension. Positions AT as a unifying framework for selection and evolution; objects as carriers of intrinsic history.

Walker has also developed (in book chapters and public-facing writing) the claim that **time is a physical property intrinsic to objects** rather than a coordinate. This is the most philosophically audacious extension.

## Why the empirical pitch is attractive

- **Operational measurability.** Unlike Kolmogorov complexity, the assembly index is finitely computable for molecules and can be *estimated from experiment*. Tandem mass spectrometry fragments molecules along bond-breaking pathways that approximately reverse assembly, so MA can be inferred from fragment spectra without knowing the molecule's identity *(established as a method; some modelling assumptions are still being refined)*.
- **Agnostic biosignature.** The MA > 15 + many copies criterion doesn't presuppose anything about Earth chemistry. For Mars sample return, Enceladus plume sampling, Europa Clipper follow-ons, this is operationally useful. NASA's agnostic biosignature programme has taken AT seriously.
- **Bridges physics and biology.** AT tries to give a physics-compatible definition of "complex" tracking a property — *requires-selection-to-exist* — that was previously informal.

## The critiques

Reception has been sharp and continues.

### "Nothing new"

Many complexity theorists — **Hector Zenil**, **Felipe Abrahão**, **Artemy Kolchinsky**, others — argue the assembly index is essentially a bounded, computable algorithmic-complexity-like measure, and everything genuinely interesting about AT is captured by **Kolmogorov complexity**, **Bennett's logical depth** [Bennett 1988], or **Gell-Mann–Lloyd effective complexity** [Gell-Mann & Lloyd 1996].

The AT defenders respond that AT is *specifically* grounded in physical realisability rather than abstract computation, and that this grounding matters. Whether this distinction is mathematically substantive or a framing difference is genuinely contested *(I think the answer is "partly substantive, partly framing", but I haven't seen a clean settling)*.

### Biosignature threshold robustness

The MA > 15 cutoff has been challenged. **Hazen et al.** and others argue that some abiotic processes (mineral precipitation under unusual conditions, prebiotic chemistry in specific environments) may produce high-assembly molecules, and that the database of measured abiotic molecules is thin enough that the cut may shift with further sampling. The biosignature claim is empirically defensible but provisional *(mixed)*.

### Philosophical overreach

The claim that AT is a new *theory of selection* or that **time is intrinsic to objects** is, for many readers, less well-argued than the operational parts of the theory. Reviewers including **Thurner**, **Jaeger**, and others have pushed back directly, often arguing that the *Nature* 2023 paper conflates an empirical contribution with a metaphysical one. Popular coverage of the *Nature* paper amplified the strongest possible reading.

### Measurement uncertainty

The translation from tandem MS fragment spectra to estimated assembly index involves modelling assumptions actively being refined. Some early numbers may not be robust under improved analysis pipelines.

## Relation to other complexity measures

| Measure | Defined on | Computable? | Relation to AT |
|---|---|---|---|
| Shannon entropy | Probability distribution | Yes | Measures randomness; largely orthogonal to AT. |
| Kolmogorov complexity | Object via universal Turing machine | Semi-computable only | K counts shortest programs; AT counts physical assembly steps. Related, not identical. |
| Logical depth | Object via shortest near-optimal program runtime | Semi-computable | Closer in spirit to AT — both about how much *work* a thing required. |
| Effective complexity | K of regularities minus randomness (Gell-Mann/Lloyd) | Semi-computable | Tries to separate structure from noise; AT sidesteps by counting concrete steps. |
| Assembly index | Min pathway with re-use | Polynomial-time for small molecules | AT's proposal. |

Whether AT is *equivalent to*, *strictly weaker than*, or *strictly different from* logical depth and friends is debated and depends on mathematical details I haven't seen fully settled. *(My guess: there's a clean reduction at the limit, but AT has practical advantages for chemistry-scale objects that the others lack.)*

## Walker on time as intrinsic

The most philosophically bold extension. The idea, roughly: in a universe with no selection, time flows forward but nothing *records* it. In a universe with selection, certain objects are repositories of selection-time, and that is what makes them alive-or-from-alive. Time becomes a property of an object measured by its assembly index.

This overlaps with Schrödinger's negentropy ("life maintains order by exporting entropy") and with Friston-adjacent ideas about living systems as models of their environment. Whether AT's specific formulation is the right way to formalise the intuition or just an evocative reframing is not clear *(speculative; possibly suggestive)*.

## My read

AT is plausibly two things at once:

1. A **genuinely useful empirical measure** for biosignature detection that is operationally distinct from existing methods, even if reducible-in-the-limit to logical depth or similar measures. The MA-from-MS approach is sensible and worth serious testing in astrobiology contexts.
2. A **philosophically overstretched** framing whose claims about selection, evolution, and time are weaker than the *Nature* 2023 paper suggests, and likely won't survive close mathematical scrutiny without being recast as a variant of existing complexity-from-selection ideas.

I'd watch the next few years of empirical replication of the MA biosignature claim and the formal-theory work that either sharpens AT's distinction from Bennett's logical depth or shows it collapses to it.

## Disagreements and cautions

- **Don't cite AT as an established theory of evolution.** It is a measure plus an associated empirical claim; the evolution-unifying framing is contested.
- **Don't cite the MA > 15 biosignature** as definitive. The threshold is empirical, the abiotic database is thin, and abiotic counterexamples have been hypothesised though not (as of my last reading) demonstrated.
- **Walker's "time as intrinsic" claim** is interesting but has not gone through the kind of philosophical or mathematical scrutiny that would establish it. Treat as suggestive.
- **The popular-coverage gap** is wide. *Nature*'s coverage of Sharma et al. 2023 was favourable; subsequent commentary in places like *Quanta* and *Aeon* was mixed; specialist replies in physics and complexity-theory communities were often critical. Read primary literature.
- **I have not chased the latest 2024–2026 follow-ups closely**. The picture may have shifted.

## Questions I'd like answered

1. **Are there abiotic processes that produce high-assembly molecules in many copies?** A clean counterexample would substantially weaken the biosignature claim.
2. **Can assembly index be efficiently measured from remote or in situ instrumentation**, or is it always a post-hoc laboratory calculation?
3. **Is AT's assembly index provably different from Bennett's logical depth**, or just a practically computable approximation? A clean theorem either way would be valuable.
4. **Does the population term *(N − 1)/N₀*** play a meaningful role in the formalism, or is it a dimensional formality?
5. **How does AT handle polymers and biopolymers** where assembly pathways are many and degenerate? Does the formalism stay coherent?
6. **What is the right comparison sample** for biotic vs abiotic — the meteorite database is small and biased, and prebiotic chemistry experiments are limited in chemical space. Does the threshold survive better sampling?

## Sources

- [Bennett 1988] Bennett, C.H. "Logical depth and physical complexity." In *The Universal Turing Machine: A Half-Century Survey*.
- [Gell-Mann & Lloyd 1996] Gell-Mann, M., Lloyd, S. "Information measures, effective complexity, and total information." *Complexity* 2:44.
- [Marshall et al. 2017] Marshall, S.M., Murray, A.R.G., Cronin, L. "A probabilistic framework for identifying biosignatures using Pathway Complexity." *Phil. Trans. R. Soc. A* 375:20160342.
- [Marshall et al. 2021] Marshall, S.M. et al. "Identifying molecules as biosignatures with assembly theory and mass spectrometry." *Nature Communications* 12:3033. https://doi.org/10.1038/s41467-021-23258-x
- [Sharma et al. 2023] Sharma, A., Czégel, D., Lachmann, M., Kempes, C.P., Walker, S.I., Cronin, L. "Assembly theory explains and unifies selection and evolution." *Nature* 622:321–328. https://doi.org/10.1038/s41586-023-06600-9
- Hazen, R.M., and others — critical commentary on AT and biosignature claims.
- Jaeger, J. (2024). Critical responses to Sharma et al., e.g. via *Beyond Networks*/Medium essays.
- Abrahão, F.S., Zenil, H. (2024). Commentary on AT vs algorithmic information measures.
- Schrödinger, E. (1944). *What Is Life?* CUP.

## Links

- [[landauer-thermodynamics-computation]] — physics of information. Landauer counts the cost of erasing a bit; AT counts the steps of building a molecule. Different angles on a similar intuition: information has physical correlates.
- [[why-biology-runs-near-the-landauer-bound]] — companion physical-floor question. Both AT and the Landauer-biology comparison try to ground informational concepts in physical quantities.
- [[slime-mold-computation]] — minimal complex behaviour from simple components. *Physarum* is the kind of object whose "behaviour assembly index" might be interesting if AT were extended beyond molecules.
- [[mechanistic-interpretability]] — another domain where we try to measure "complexity of a trained object" in a way that's physically grounded. The motivations are similar; the methods are quite different.
- [[plant-cognition-mycorrhizal-networks]] — another field where popular coverage runs ahead of evidence. Useful as a methodological case study, not for content overlap.
- [[hard-problem-consciousness]] — AT makes no consciousness claims, but occupies a similar "physics of meaning" niche where philosophical ambition outpaces formal ground.
