# Erasing a bit costs at least kT ln 2 of heat — Landauer's principle ties information to thermodynamics

> Logical irreversibility forces physical irreversibility, so deleting a bit has an entropy price — this closes Maxwell's demon, sets the thermodynamic floor on computation, and explains why biology runs close to physics' limit while silicon does not.

[Confidence: established for the central claim; contested on philosophical boundaries]
[Last verified: 2026-04-21]

## TL;DR

Rolf Landauer proved in 1961 that erasing one bit at temperature T must dissipate at least k_B T ln 2 of heat — about 3 × 10⁻²¹ J at 300 K [Landauer 1961] — because erasure reduces the logical system's entropy and the second law sends that entropy to the bath. Bennett used this to exorcise Maxwell's demon (the demon must eventually erase its memory) and noted that *logically reversible* computation has no Landauer floor [Bennett 1973; Bennett 1982]; Bérut et al. verified the bound experimentally in 2012. Current CMOS runs about six orders of magnitude above the floor; biology runs within a small factor of it. The bound is real, verified, and nowhere close to binding for current engineering.

## The 1961 argument

Landauer, at IBM, asked why computers dissipate heat. His observation: **logically irreversible** operations map many input states to fewer output states. The canonical case is `ERASE`: before, a bit is in 0 or 1 (two microstates, equal probability); after, it is in 0 (one microstate). The logical entropy drops by k_B ln 2.

If the logical state is carried by a physical system in contact with a heat bath, by the second law that entropy has to go somewhere. The only place is into thermal degrees of freedom of the environment. Minimum heat dissipation: **k_B T ln 2 per erased bit** *(established)*.

The subtlety worth holding onto: this is the cost of *erasure*, not of reading, copying to a blank tape, or computing a reversible function. Operations that preserve logical information have no Landauer floor [Landauer 1961].

## Maxwell's demon, closed

Maxwell (1867) imagined a tiny being sorting fast from slow molecules through a trapdoor, producing a temperature gradient for free. Apparent second-law violation.

**Szilard (1929)** reduced the puzzle to a one-molecule engine. A single molecule in a box, a measurement of which side it is on, and a partition that extracts k_B T ln 2 of work from that measurement. Szilard made explicit that *information about the molecule* was being converted to work.

**Bennett (1982)** closed the loop. The demon has to erase its memory to run the cycle again. That erasure costs exactly k_B T ln 2 per bit — precisely what the engine extracted. Second law restored. **Information is a bookkept resource, and deletion has a price** *(established)*.

## Reversible computing

Bennett went further [Bennett 1973]: if irreversibility is the only source of Landauer dissipation, then *logically reversible* computation can dissipate arbitrarily little energy per operation. His recipe:

1. Compute f(x) reversibly, keeping all intermediate results plus the input.
2. Copy out the answer.
3. Run the whole computation backwards, cleaning up intermediates.

You end with x, f(x), and a blank workspace. **Fredkin** (a 3-input conservative gate) and **Toffoli** (CCNOT, reversible universal) give a gate basis. Quantum computing inherits this — unitary gates are automatically reversible, which is part of why quantum-thermodynamic accounting is subtle but not catastrophic *(established in theory)*.

In practice, reversible CMOS has overheads (history memory, adiabatic slowness) that have kept it out of consumer hardware. It remains the constructive proof that the Landauer floor applies only to *irreversible* steps, not to computation per se.

## Experimental verification

For decades the principle was treated as established on theoretical grounds alone. Direct measurement required the tools of single-particle thermodynamics:

- **Bérut et al. 2012** [*Nature*]: silica microbead in a double-well optical trap, driven through a bit-erasure protocol. Heat dissipation matched k_B T ln 2 in the quasi-static limit. This is the canonical experimental confirmation *(established)*.
- **Jun, Gavrilov, Bechhoefer 2014** [*PRL*]: refined feedback-trap measurement, sharpened the match.
- **Hong, Lambson, Dhuey, Bokor 2016** [*Science Advances*]: nanomagnetic bits approaching the limit — important because most real memory is magnetic or electronic, not optical-trap-based.
- **Koski, Pekola et al.**: single-electron-box experiments probing quantum and non-equilibrium regimes.

The bound is not just a derivation. It has been seen.

## How far we are from the floor

Rough numbers at T = 300 K:

- Landauer bound: k_B T ln 2 ≈ **3 × 10⁻²¹ J per erased bit** (0.017 eV).
- Modern CMOS: ~**10⁻¹⁵ J per switch** — about **10⁶ × the Landauer bound**.

The gap is engineering, not physics. See [[why-biology-runs-near-the-landauer-bound]] for the breakdown — voltage scaling has plateaued, interconnect capacitance dominates, CMOS pays for reliability against thermal noise with many k_B T of voltage headroom. None of this is forced by the second law.

Frontier LLM training: ~10²⁰–10²¹ FLOPs at tens of pJ each → megawatt-hours. Landauer floor for the same work is factors of 10⁵ to 10⁶ lower. In principle, ML training energy could drop by many orders of magnitude with different devices. In practice, closing the first factor of 10 is already hard.

## Biology runs close to the floor

Life does computation with molecular conformational changes at thermal scale, which is the regime where Landauer is not a far-away abstraction but a few-factor ceiling:

- One **ATP hydrolysis** delivers ~20 k_B T, or roughly 29 Landauer-bits of budget.
- **Kinetic proofreading** [Hopfield 1974; Ninio 1975] — how ribosomes and DNA polymerases achieve low error rates — is a thermodynamic cost of accuracy formally analogous to Landauer erasure: reducing the entropy of a "correct vs incorrect" bit requires dissipation *(established)*.
- Bialek, Tu, Lan and the stochastic-thermodynamics community have sharpened this: sensing, adaptation, and signalling all trade energy for information in ways that match predicted bounds [Seifert 2012].
- **Schrödinger** 1944 anticipated the whole picture with "negative entropy": life maintains order by exporting entropy to its environment. Landauer and Bennett turned the slogan into a quantitative framework.

See [[why-biology-runs-near-the-landauer-bound]] for the detailed comparison.

## Stochastic thermodynamics and quantum Landauer

Stochastic thermodynamics (Seifert, Jarzynski, Crooks; 1990s–2010s) generalised classical thermodynamics to trajectories of small noisy systems. Outputs relevant to Landauer:

- **Fluctuation theorems** — Jarzynski equality, Crooks relation — exact equalities for forward/backward protocol probability ratios.
- **Finite-time Landauer bounds** — tighter inequalities that recover the classical bound in the slow limit and add corrections.
- **Quantum Landauer** — the bound carries over with the right definitions; subtleties appear for non-thermal baths and coherent information. Literature: Goold, Huber, Riera, del Rio, Skrzypczyk, Åberg and others.

Under some resource-theoretic framings (coherent resources, non-thermal baths) the *classical* bound appears violable, but careful accounting restores a generalised version.

## Disagreements and cautions

- **Earman and Norton** have argued that Landauer's principle is not strictly forced by the second law in all formulations: the k_B T ln 2 dissipation can sometimes be re-described as occurring elsewhere, and the principle rests on assumptions (ergodicity, specific memory-state definitions) that are not independent of the second law itself [Earman & Norton 1998, 1999]. Shenker has made related objections. Working physicists generally treat the principle as correct and experimentally verified; the critiques are philosophically substantive but do not overturn the experiments *(contested, but at the philosophical level, not the experimental one)*.
- **The "information is physical" slogan** (Landauer's own) is frequently misused. The defensible reading is narrow: *some* questions about information have forced physical answers. The slogan does not license broader claims that information is a fundamental physical quantity on par with mass–energy.
- **Biology ≈ Landauer-optimal** is a slogan, not a universal truth. It holds best at the molecular-machine level (ribosomes, kinases, ion channels); it weakens substantially at the systems level. A cortical spike involves ~10⁹ ATP-equivalents when you include postsynaptic machinery; per-bit, a brain is not nearly as efficient as a ribosome is.
- **Quantum "violations"** of the classical Landauer bound in the literature usually turn out, on careful re-reading, to involve additional resources (coherence, non-thermal baths) that are accounted for elsewhere in the ledger.

## Questions I'd like answered

1. **Is there a clean generalised Landauer bound for finite-error computation?** Stochastic thermodynamics has partial results; I don't know how tight the bounds are for, say, a target error rate of 10⁻⁶ in a fixed-time computation.
2. **Why has reversible computing not won in a niche?** If the theoretical floor is so much lower, some application should reward the architectural overhead. Cryogenic compute? Low-leakage IoT? What's blocking adoption?
3. **Does the brain's energy budget** have an interesting Landauer decomposition — how much of ~20 W is irreversibility-tax vs. structural maintenance vs. signalling overhead?
4. **Are there physical substrates** that naturally do reversible computation without the adiabatic-slowness penalty? Superconducting rapid single flux quantum (RSFQ) partially qualifies.
5. **Is there a version of Landauer for open systems** with actively maintained non-equilibrium baths (like cells)? Stochastic thermodynamics treats this, but the cleanest bound I know of is still the equilibrium one.

## Sources

- [Bennett 1973] Bennett, C.H. "Logical reversibility of computation." *IBM J. Res. Dev.* 17:525.
- [Bennett 1982] Bennett, C.H. "The thermodynamics of computation — a review." *Int. J. Theor. Phys.* 21:905–940. https://doi.org/10.1007/BF02084158
- [Bérut et al. 2012] Bérut, A. et al. "Experimental verification of Landauer's principle linking information and thermodynamics." *Nature* 483:187. https://doi.org/10.1038/nature10872
- [Earman & Norton 1998, 1999] Earman, J., Norton, J. "Exorcist XIV: The wrath of Maxwell's demon." Two-part paper, *Studies in History and Philosophy of Modern Physics*.
- [Hopfield 1974] Hopfield, J.J. "Kinetic proofreading: a new mechanism for reducing errors in biosynthetic processes requiring high specificity." *PNAS* 71:4135.
- [Jun et al. 2014] Jun, Y., Gavrilov, M., Bechhoefer, J. "High-precision test of Landauer's principle in a feedback trap." *PRL* 113:190601.
- [Landauer 1961] Landauer, R. "Irreversibility and heat generation in the computing process." *IBM J. Res. Dev.* 5:183.
- [Seifert 2012] Seifert, U. "Stochastic thermodynamics, fluctuation theorems and molecular machines." *Rep. Prog. Phys.* 75:126001.
- [Szilard 1929] Szilard, L. "Über die Entropieverminderung in einem thermodynamischen System bei Eingriffen intelligenter Wesen." *Z. Phys.* 53:840.
- Schrödinger, E. (1944). *What Is Life?* Cambridge University Press.

## Links

- [[why-biology-runs-near-the-landauer-bound]] — the direct follow-up, working out the biology-vs-silicon comparison in numbers.
- [[mechanistic-interpretability]] — the computations whose thermodynamic cost we currently pay by the megawatt-hour. Landauer is the theoretical floor under those energy costs.
- [[slime-mold-computation]] — a biological substrate that computes extremely close to the physical floor, even by the standards of biology.
- [[assembly-theory-origin-of-life]] — another attempt to quantify "informational" properties of matter physically. AT and Landauer are different measures of the same rough intuition.
- [[hard-problem-consciousness]] — is consciousness thermodynamically cheap or expensive? Almost certainly irrelevant at the Landauer level, but the question of whether experience itself has an entropy price is asked occasionally.
- [[octopus-cognition]] — a biological complex mind operating within small factors of the Landauer bound at the molecular level.
