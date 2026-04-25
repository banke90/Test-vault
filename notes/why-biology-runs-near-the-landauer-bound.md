# Why does biology run so much closer to the Landauer bound than silicon does?

> Roughly because biology computes by shuffling molecules at thermal scale, where the Landauer bound is a non-negligible fraction of available energy per operation, while silicon drives large voltages across large capacitances for reasons of noise margin and manufacturing tolerance — reasons that are contingent, not physical.

[Confidence: mixed]
[Last verified: 2026-04-21]

## TL;DR

A single ATP hydrolysis releases about 20 k_B T of free energy, which is only about 29× the Landauer erasure bound of k_B T ln 2 per bit [Landauer 1961]. Real molecular machines spend single-digit to low-double-digit multiples of Landauer per logical operation *(established)*. Current CMOS, by contrast, dissipates about 10⁻¹⁵ J per switch — six orders of magnitude above the Landauer floor. The gap is not fundamental: it comes from voltage-scaling limits, interconnect capacitance, and the cost of beating thermal noise in a device that was never designed to operate near k_B T. Whether silicon could be redesigned to approach biological efficiency is a live question.

## The numbers

At T = 300 K:

- **k_B T ≈ 4.1 × 10⁻²¹ J** (≈ 0.025 eV).
- **Landauer bound: k_B T ln 2 ≈ 2.85 × 10⁻²¹ J per erased bit.**
- **ATP hydrolysis: ≈ 20 k_B T ≈ 8 × 10⁻²⁰ J per molecule.** So one ATP carries about 29 Landauer-bits of budget.
- **A bacterial ribosome** adds about one amino acid per ~5 ATPs, so roughly 100 k_B T per peptide-bond formation plus ~5–10 k_B T in kinetic proofreading overhead — a few dozen Landauer-bits for something that selects one amino acid from twenty *(established)*.
- **Current CMOS: ≈ 10⁻¹⁵ J per switch.** That's about 2.5 × 10⁵ k_B T, or ~3.5 × 10⁵ Landauer bits.

So biology is within roughly 10× of the Landauer bound per logical operation. Silicon is about 10⁶× above it. The gap between the two is about five orders of magnitude.

## Why silicon is so far above the floor

Several reasons compound, none of them a law of physics:

1. **Voltage scaling has plateaued.** Dynamic switching energy goes as CV². Historically, Dennard scaling let voltage shrink with feature size, keeping energy per operation on a nice curve. Around the 90 nm / 65 nm nodes (~2005), voltage scaling effectively stopped because subthreshold leakage and noise margin became binding. Supply voltages have been stuck around 0.7–1.0 V ever since, and that sets a floor on CV² that is very far above k_B T ≈ 0.025 eV *(established)*.

2. **Interconnect dominates.** A lot of the energy in a real chip isn't in the transistor switching, it's in charging the wires between them. Wires have large capacitances relative to transistors, and shrinking them makes resistance worse. Near-memory and 3D-integrated designs try to shorten wires, but the physics is unfriendly.

3. **Reliability against thermal noise.** A transistor operating near k_B T has thermal fluctuations comparable to its signal. Error rates rise rapidly. CMOS buys its extreme reliability (error rates ~10⁻¹⁵ per op) by operating many k_B T above threshold. Biology accepts much higher per-operation error rates (say 10⁻⁴) and compensates with redundancy and proofreading.

4. **Clocking and signal distribution overhead.** Global clock trees, pipeline registers, and latches all consume energy that isn't doing useful logic work. These are architecture, not physics.

5. **Irreversibility everywhere.** Every standard CMOS gate is logically irreversible. Every operation therefore pays the Landauer tax in principle, but pays vastly more in practice because nothing is tuned to avoid irreversibility *(established)*.

Points 1–4 are the bulk of the factor-of-10⁶ gap. Point 5 is what sets the ultimate floor.

## Why biology is near the floor

Biology's trick is substrate: it does computation with **molecular conformational changes** instead of charge transport through capacitances. The energies involved are naturally a few k_B T because the reaction barriers are a few k_B T — if they were much higher, reactions wouldn't happen on biological timescales; if much lower, thermal noise would dominate *(established)*. This is not an accomplishment; it is the only regime where chemistry works at all.

Key properties:

- **Ballistic reactions.** An enzyme changing conformation doesn't need to drive a capacitive wire. The energy goes into the conformation and nowhere else.
- **Stochastic, not deterministic.** Molecular machines accept per-step error rates that silicon designers would find shocking — and then use kinetic proofreading (Hopfield, Ninio) to reduce error at thermodynamic cost. This *spends* entropy in a controlled way rather than engineering it out with high voltages.
- **Reversibility comes almost for free.** Most enzymatic steps are near-equilibrium and thus near-reversible. Logical-to-physical irreversibility mappings are weaker. Running a ribosome backwards is possible in principle and observable in some contexts *(established)*.
- **Locality.** Neurons, ribosomes, kinases don't wire to everything. They act on their immediate neighbours. No long interconnect.

## A useful comparison

| Metric | ATP hydrolysis | CMOS switch (2024) | Landauer bound (300 K) |
|---|---|---|---|
| Energy | ~8 × 10⁻²⁰ J | ~10⁻¹⁵ J | ~3 × 10⁻²¹ J |
| Bits of Landauer budget | ~29 | ~3.5 × 10⁵ | 1 (definitional) |
| Error rate target | 10⁻³ to 10⁻⁴ | 10⁻¹⁵ | N/A |

Silicon's reliability buy is, crudely, about 11 orders of magnitude in error rate for about 6 orders of magnitude in energy. Whether that tradeoff is optimal depends on what you're computing. Biology's tradeoff is optimal for chemistry-scale computation at 300 K in aqueous medium. Silicon's tradeoff is optimal for committing database writes.

## What could close the gap

- **Sub-threshold CMOS.** Operating transistors below the usual threshold voltage, in the exponential-current regime. Energy per op drops toward k_B T, but delay rises sharply. Used in extremely low-power devices (hearing aids, sensor nodes) but not in frontier compute.
- **Adiabatic / reversible CMOS.** Engineered to approach zero-dissipation switching by varying supply voltage slowly. Exists; has not displaced conventional CMOS, partly because the clock overhead eats the savings at useful speeds.
- **Molecular and DNA-based computing.** Literally running biology in a test tube for computation. Wins on energy per op; loses on operations per second by many orders of magnitude *(established)*.
- **Neuromorphic / spiking chips.** Sparse, event-driven, often low-voltage. IBM TrueNorth, Intel Loihi. Closer to biology in architecture but still far above the Landauer floor in energy per op.
- **Thermodynamic computing / probabilistic computing.** Extropic, Normal Computing, and a few academic groups. Actively tries to do useful work near k_B T by sampling from Boltzmann distributions. Early; unclear if it will scale. *(speculative)*

## Disagreements and cautions

- **The ATP-to-bits conversion isn't clean.** Comparing "one ATP" to "one Landauer bit erasure" requires specifying what operation you mean. A ribosome selects among 20 amino acids, which is ~4.3 bits of information, not 1. A kinase flipping a phosphorylation state is closer to one bit. The per-bit budget for biology is therefore somewhere between ~5 and ~30 k_B T per bit of useful logical work, depending on how you account — all still within about 1.5 orders of magnitude of Landauer, not five or six *(established, but the specific number is definitional)*.
- **Not all biological computation is near the floor.** Brains are substantially less efficient per-bit than individual molecular machines. A cortical spike costs ~10⁹ ATP-equivalents if you include all the downstream postsynaptic activity. The brain as a whole dissipates about 20 W for on the order of 10¹⁵ synaptic operations per second — call it 10⁻¹⁴ J per synaptic op, similar to CMOS. So at the *system* level, biology and silicon are much closer than the ribosome-vs-transistor comparison suggests. The "biology is near the Landauer floor" claim is strongest at the molecular level and weakens as you aggregate *(mixed — I think this is right but the numbers are approximate)*.
- **Earman and Norton** have argued that Landauer's principle is not strictly required by the second law in all formulations [Earman & Norton 1998, 1999]. The experimental verifications (Bérut et al. 2012, Jun et al. 2014) confirm the bound in specific setups; the general-principle status is a philosophical dispute more than a physics one. The practical numbers above don't depend on the outcome of that dispute.

## Questions I'd like answered

1. What is the theoretical minimum energy per **useful** logical operation in a noisy substrate, given a target error rate? Is there a clean generalisation of Landauer for finite-error computation? (Partly addressed by stochastic thermodynamics [Seifert 2012]; I don't know how tight the bounds are.)
2. If we rebuilt CMOS from scratch optimising for k_B T efficiency rather than reliability, at what error rate would a useful general-purpose chip live? 10⁻⁶? 10⁻³? Lower?
3. Is there a way to combine biological-scale energy efficiency with silicon-scale clock speeds, or is that tradeoff fundamental?
4. How much of the brain's efficiency comes from being near Landauer at the molecular level, and how much from architectural choices (sparsity, analog computation, co-located memory and compute)?
5. Does frontier LLM training energy have a Landauer-implied floor that is interestingly far from current energy costs, and what fraction of the ~10⁶× gap could be closed with near-term hardware?

## Sources

- [Bennett 1982] Bennett, C.H. "The thermodynamics of computation — a review." *Int. J. Theor. Phys.* 21:905–940. https://doi.org/10.1007/BF02084158
- [Bérut et al. 2012] Bérut, A. et al. "Experimental verification of Landauer's principle linking information and thermodynamics." *Nature* 483:187. https://doi.org/10.1038/nature10872
- [Earman & Norton 1998, 1999] Earman, J., Norton, J. "Exorcist XIV: The wrath of Maxwell's demon." *Studies in History and Philosophy of Modern Physics* (two parts). https://www.sciencedirect.com/science/article/abs/pii/S1355219898000231
- [Hopfield 1974] Hopfield, J.J. "Kinetic proofreading: a new mechanism for reducing errors in biosynthetic processes requiring high specificity." *PNAS* 71:4135.
- [Jun et al. 2014] Jun, Y., Gavrilov, M., Bechhoefer, J. "High-precision test of Landauer's principle in a feedback trap." *PRL* 113:190601.
- [Landauer 1961] Landauer, R. "Irreversibility and heat generation in the computing process." *IBM J. Res. Dev.* 5:183.
- [Seifert 2012] Seifert, U. "Stochastic thermodynamics, fluctuation theorems and molecular machines." *Rep. Prog. Phys.* 75:126001.
- Brain energetics numbers cross-checked against Lennie, P. "The cost of cortical computation." *Curr. Biol.* 13:493 (2003) and Attwell & Laughlin, "An energy budget for signaling in the grey matter of the brain." *J. Cereb. Blood Flow Metab.* 21:1133 (2001).

## Links

- [[landauer-thermodynamics-computation]] — the standing note on Landauer's principle. This question note is effectively a zoomed-in child of that one: the same framework, applied to a specific comparison.
- [[slime-mold-computation]] — *Physarum* is another datapoint for "biology computes close to the physical floor." The slime mould paper calculates its Tokyo-network at something like a few kJ of metabolic cost — I haven't worked this out per-bit but it would be an interesting exercise.
- [[mechanistic-interpretability]] — the mental backdrop for "what a frontier ML training run would cost at Landauer efficiency." Not a direct link but a reason I care about the question.
