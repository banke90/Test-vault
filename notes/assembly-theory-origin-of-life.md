---
title: "Assembly Theory — Information, Complexity, and the Origin of Life"
tags: [astrobiology, complexity, origin-of-life, information-theory]
date: 2026-04-21
---

# Assembly Theory — Information, Complexity, and the Origin of Life

**Assembly Theory (AT)** is the collaborative project of chemist **Leroy "Lee" Cronin** (University of Glasgow) and theoretical physicist / astrobiologist **Sara Imari Walker** (Arizona State). Its core move is to propose a measure — the **assembly index** — that counts the minimum number of step-wise joining operations, each using only previously-constructed subparts, required to build an object from its basic units. The claim is that this measure distinguishes artefacts of life and evolution from things produced by non-biological chemistry, and that it provides a bridge between physics and biology.

It has drawn striking experimental results, striking philosophical claims, and striking criticism — sometimes all at once. A balanced look is warranted.

## 1. What the assembly index is

Given an object (a molecule, a word, an image) made of identifiable units, the **assembly index** $a$ is the minimum number of steps along any assembly pathway that builds the object from elementary pieces, where at each step you may combine two previously-built subobjects. Crucially, **re-use** of substructures is counted once per construction, not once per appearance — so repeated motifs drop the count.

Trivial example: assembling `ABAB` takes 3 steps under the "re-use substructures" rule — A, B, combine to AB, combine AB with AB to make ABAB. Without the re-use rule, it would take 4 steps (build AB, build another AB, combine).

Applied to molecules, the units are chemical bonds or fragments, and the assembly index is the shortest pathway of bond-forming steps allowed by the rules. The "**molecular assembly index**" (MA) is calculated from the graph structure of a molecule.

Assembly theory's full **assembly equation** combines the index with a population measure:

$$A = e^{a} \cdot \frac{N - 1}{N_0}$$

where $a$ is the assembly index of the object type, $N$ is the number of copies of that object detected, and $N_0$ is a normalisation. The intuition: finding many copies of something that requires many selective steps to build is strong evidence of a selection process. One complicated molecule could be a lucky accident; a billion copies of a specific complicated molecule cannot.

## 2. Key papers and claims

- **Marshall, Murray, Cronin (2017)** "A probabilistic framework for identifying biosignatures using Pathway Complexity." *Phil. Trans. Royal Soc. A*.
- **Marshall, Moore, Murray, Walker, Cronin (2021)** "Identifying molecules as biosignatures with assembly theory and mass spectrometry." *Nature Communications* 12:3033. This is the empirical paper. They use tandem mass spectrometry fragmentation patterns to estimate assembly indices of molecules in samples — biotic (living tissue, cells, fossils), abiotic (meteorites, laboratory chemistry). They argue that a molecular assembly index **above ~15** in mass-spec data is reliably found only in biotic samples, and propose this threshold as a candidate **agnostic biosignature**.
- **Sharma, Czégel, Lachmann, Kempes, Walker, Cronin (2023)** "Assembly theory explains and unifies selection and evolution." *Nature*. This is the more ambitious theoretical paper. It positions AT as a framework in which "objects" are physical entities that carry within themselves a history (encoded in how hard they are to make), and argues that AT can unify selection, evolution, and novelty in a single physical framework. Walker and Cronin in public-facing writing also propose that **time is a physical property intrinsic to objects**, rather than a coordinate.

## 3. Why it is attractive

- **Operational measurability.** Unlike Kolmogorov complexity, the assembly index is finitely computable in principle for molecules and can be estimated from experimental data — tandem MS fragmentation reproduces the bond-breaking in reverse of assembly, giving empirical access to the pathway graph.
- **Agnostic biosignature.** If the ~15 threshold claim holds, AT offers a non-Earth-centric way to detect life: don't look for DNA or specific metabolites, just look for highly assembled molecules present in many copies. For astrobiology missions (Mars sample return, Enceladus/Europa flybys), this is operationally valuable.
- **Bridges physics and biology.** AT tries to give a physics-compatible definition of "complex" that tracks a property (requires-selection-to-exist) which was previously informal.

## 4. The critique

The reception has been sharp.

- **The "nothing new" critique.** Many complexity theorists (including **Hector Zenil**, **Felipe Abrahão**, **Artemy Kolchinsky**, and others) argue that the assembly index is essentially a bounded, computable **algorithmic-complexity-like** measure, and that everything interesting about AT is already captured by Kolmogorov complexity, logical depth (Bennett 1988), or effective complexity (Gell-Mann & Lloyd). The response from Cronin and Walker is that AT is *specifically* grounded in physical realisability, not abstract computation, and that this grounding matters.
- **The biosignature threshold.** The claim that MA > 15 is a sharp biosignature has been challenged: Hazen et al. and others have pointed out that some abiotic processes (mineral precipitation under certain conditions, prebiotic chemistry in specific environments) might produce high-assembly molecules, and that the database of measured abiotic molecules is thin. The cut may shift with further sampling.
- **Philosophical overreach.** The claim that AT is a new *theory of selection* or that it shows **time is intrinsic to objects** is, for many readers, less well-argued than the operational parts of the theory. Reviewers including **Thurner**, **Jaeger**, and others have pushed back, often quite directly. The *Nature* 2023 paper drew both favourable and dismissive popular coverage.
- **Measurement uncertainty.** The step from tandem MS fragment spectra to an estimated assembly index involves modelling assumptions that are actively being refined. Some early numbers may not be robust.

## 5. Relation to existing complexity measures

| Measure | Defined | Computable? | Relation to AT |
|---|---|---|---|
| Shannon entropy | On a probability distribution | Yes | Measures randomness; largely orthogonal to AT. |
| Kolmogorov complexity | Length of shortest program outputting the object | No (semi-computable) | Related but not identical. K counts programs; AT counts physical assembly steps. |
| Logical depth (Bennett) | Runtime of the shortest near-optimal program | No | Closer in spirit to AT: both are about how much *work* a thing needed. |
| Effective complexity (Gell-Mann/Lloyd) | K of the regularities minus randomness | No | Tries to separate structured from random; AT sidesteps this by counting concrete steps. |
| Assembly index | Min assembly pathway using re-use | Yes (polynomial for small molecules) | AT's proposal. |

Whether AT is *equivalent to* something already known under a different name, *strictly weaker*, or *strictly different*, is genuinely in debate and depends on mathematical details I have not seen fully settled.

## 6. Astrobiology relevance

Mars-sample-return and icy-moon missions (Enceladus plume sampling, Europa Clipper follow-ons) need an operational definition of "life-like" that doesn't prejudge what life looks like. AT's approach — assembly index from mass spec — can be done with instruments small and reliable enough to fly. Even if AT is theoretically contestable, it may be **operationally useful** as one biosignature among several. The NASA agnostic biosignature programme has taken it seriously.

## 7. Walker on time as intrinsic

Walker's conceptual extension — that objects carry their own history inside their structure, and that "**time is a physical property of an object** measured by its assembly index" — is the most philosophically audacious part of AT. The claim, roughly, is that in a universe with no selection, time flows forward but nothing *records* it; in a universe with selection, some objects are repositories of selection-time, and that is what makes them alive-or-from-alive.

This overlaps interestingly with **Schrödinger**'s "negentropy" in *What Is Life?* and with **Karl Friston**-adjacent ideas about living systems as models of their environment. Whether AT's specific formulation is the right way to formalise the intuition, or just an evocative reframing, is not yet clear.

## 8. My read

AT is either:

1. a genuinely new, physical measure of complexity that is practically useful for biosignature detection, partially reducible to old concepts but distinct enough to matter — and philosophically suggestive in ways worth pursuing; or
2. a useful empirical tool with an overinflated theoretical framing that will, on reflection, be seen as a variant of logical depth / effective complexity plus a specific physical-realisability constraint.

These are not mutually exclusive. My suspicion is that something like (1) is close to right on the empirical side (the tandem-MS biosignature approach is sensible and deserves serious testing), and that the philosophical claims around "new theory of evolution / time / matter" are weaker than the authors suggest. I'd keep an eye on the replication of the MA-threshold biosignature claim and on further theoretical work that either sharpens the relation to Kolmogorov/Bennett measures or clearly separates from them.

## 9. Open questions

- Are there **abiotic processes** that produce high-assembly molecules in many copies? (If yes, the biosignature claim is in trouble.)
- Can assembly index be **efficiently measured** from remote or in situ instrumentation, or is it always a post-hoc laboratory calculation?
- Is AT's assembly index **provably different** from Bennett logical depth, or just a practically computable approximation?
- Does the **population term** $(N-1)/N_0$ play a meaningful role or is it a dimensional formality?
- How does AT handle **polymers and biopolymers** where assembly pathways are many and degenerate?

## Sources (verify before quoting)

- Marshall, S.M., Murray, A.R.G., Cronin, L. (2017). "A probabilistic framework for identifying biosignatures using Pathway Complexity." *Phil. Trans. R. Soc. A* 375:20160342.
- Marshall, S.M., Mathis, C., Carrick, E., Keenan, G., Cooper, G.J.T., Graham, H., Craven, M., Gromski, P.S., Moore, D.G., Walker, S.I., Cronin, L. (2021). "Identifying molecules as biosignatures with assembly theory and mass spectrometry." *Nature Communications* 12:3033.
- Sharma, A., Czégel, D., Lachmann, M., Kempes, C.P., Walker, S.I., Cronin, L. (2023). "Assembly theory explains and unifies selection and evolution." *Nature* 622:321–328.
- Jaeger, J. (2024). Response/critique of Sharma et al., various online essays (see *Beyond Networks* / Medium posts).
- Hazen, R.M., and others — critical commentary on AT and biosignature claims.
- Abrahão, F.S., Zenil, H. (2024). Commentary on AT vs algorithmic information measures.
- Gell-Mann, M., Lloyd, S. (1996). "Information measures, effective complexity, and total information." *Complexity* 2:44.
- Bennett, C.H. (1988). "Logical depth and physical complexity." In *The Universal Turing Machine: A Half-Century Survey*.

## Related

- [[landauer-thermodynamics-computation]] — physics of information; the natural companion framework
- [[slime-mold-computation]] — minimal complex behaviour from simple components
- [[mechanistic-interpretability]] — another domain where we measure "complexity of a trained object"
- [[plant-cognition-mycorrhizal-networks]] — another field where popular narrative runs ahead of evidence
- [[hard-problem-consciousness]] — AT makes no consciousness claims, but occupies a similar "physics of meaning" niche
