# Primers

Dense reference cards for complex systems I need to orient in before making decisions about direction, design, or interpretation. Each primer compresses a system's *decision-relevant shape* — invariants, tradeoffs, handles, traps — onto one screen. Not for learning; for consulting once I already know the territory exists.

Distinct from [[facts]] (atomic propositions) and [[ops]] (runnable procedures). Distinct from [[notes]] (narrative treatment). A primer is the shape you carry in your head so you can decide under pressure.

Format per entry:

- `## <System name>`
- *one-line compressor in italics*
- **Shape** — 3–6 dense bullets on invariants and tradeoffs
- **Handles** — concrete numbers or thresholds worth remembering
- **Traps** — known failure modes and common misreadings
- **Deeper** — link to the full note(s)

Rules:

- One screen per entry. If it grows past that, split or promote to a note.
- Write to the version of yourself *consulting during a decision*, not the version *learning*.
- Link out, don't explain. A primer that wants to argue wants to be a note.
- Update in place. Don't keep old versions.

---

## Vault note conventions

*What a note in this vault looks like, compressed for consultation before starting one.*

**Shape.**
- Title specific, not bucket. A claim for argument notes; a scoped topic for surveys.
- Under title: one-line `>` summary + `[Confidence]` + `[Last verified]`.
- `## TL;DR` first: three sentences, five ceiling. Delivers the point if nothing else is read.
- Body sections named for content, not numbered.
- `## Disagreements and cautions` and `## Questions I'd like answered` are first-class, not footnotes.
- Inline bracket-key sources `[Author Year]`; resolve in `## Sources` at bottom with URLs.
- `## Links` annotated — one line per link explaining the *relationship*, not topic adjacency.

**Handles.**
- Four confidence tiers: `established | mixed | speculative | contested`.
- Inline confidence tags allowed: *(established)*, *(speculative)*, *(contested)*, *(my guess)*.
- TL;DR target ≤ 5 sentences.

**Traps.**
- Don't add YAML frontmatter. Don't add tags. Both discarded deliberately.
- `Last verified` is only valuable if I actually update it. If I never will, it's a creation date in costume.
- "Related" as adjacency list is the failure mode `## Links` was designed to prevent.
- Confidence attaches to a *claim*, not to a topic.

**Deeper.** → [[conventions]], [[ops]] for vault workflow.

---

## Energy-per-operation scale

*Where a computing substrate sits on the spectrum from thermodynamic floor to engineering reality. Use before reasoning about efficiency claims.*

**Shape.**
- Floor is physics: Landauer k_B T ln 2 per erased bit. Set by logical irreversibility + second law.
- Biology sits within small factors of floor at the molecular-machine level (ribosome, kinase, ion channel).
- Biology sits far above the floor at the systems level (brain per-synaptic-op comparable to CMOS).
- Silicon sits ~10⁶ × above the floor, largely because of voltage scaling, interconnect, and reliability headroom against thermal noise — none of which is physics-forced.
- Reversible computing can in principle dissipate arbitrarily little (Bennett 1973). Adoption blocked by practical overheads, not by theory.

**Handles.**
- k_B T at 300 K ≈ 4.1 × 10⁻²¹ J ≈ 0.025 eV.
- Landauer bound ≈ 2.85 × 10⁻²¹ J per erased bit.
- ATP hydrolysis ≈ 20 k_B T ≈ 8 × 10⁻²⁰ J → ~29 Landauer-bits budget per ATP.
- CMOS switch ≈ 10⁻¹⁵ J ≈ 2.5 × 10⁵ k_B T ≈ 10⁶ Landauer bits.
- Ribosome: ~100 k_B T per peptide bond; error rate ~10⁻⁴.
- DNA polymerase III: ~10⁻⁷ error rate.

**Traps.**
- Don't apply ribosome-level efficiency to whole-brain efficiency. The *system* operates far above the floor even when components don't.
- "Silicon is wasteful" is correct but the gap is engineering, not physics. Reversible CMOS and sub-threshold CMOS exist; they haven't won for reasons unrelated to thermodynamics.
- Landauer is a *floor* under *irreversible* operations. Reversible computations have no such floor.
- Popular claims of "quantum violations" of Landauer usually restore the bound under careful accounting.

**Deeper.** → [[landauer-thermodynamics-computation]], [[why-biology-runs-near-the-landauer-bound]], [[kinetic-proofreading]].

---

## Assembly theory — what's established vs contested

*Use before citing or evaluating an AT claim. The empirical pitch and the theoretical extension have very different confidence.*

**Shape.**
- AT defines an **assembly index** *a* = min steps to build an object from parts, with re-use of substructures counted once per build.
- Computable in polynomial time for small molecules; estimable from tandem MS fragmentation patterns.
- Core empirical claim: molecular assembly index > ~15, present in many copies, is reliably only biotic *(mixed — provisional, thin abiotic sample)*.
- Theoretical extension: AT unifies selection and evolution; time is intrinsic to objects *(contested — sharply critiqued, likely overstretched)*.
- Critics argue AT reduces in principle to logical depth / effective complexity. Defenders cite physical realisability grounding.

**Handles.**
- MA threshold for biosignature: ≈ 15 *(provisional)*.
- Key papers: Marshall et al. 2021 (empirical), Sharma et al. 2023 (theoretical).
- Key critics: Hazen, Jaeger, Zenil, Abrahão, Kolchinsky.
- NASA agnostic-biosignature programme treats AT as one tool among several.

**Traps.**
- Don't conflate "AT as biosignature method" (plausible and testable) with "AT as theory of evolution" (overstretched). Different confidence tiers.
- Don't cite MA > 15 as established; it depends on a thin abiotic database that may shift.
- "Time is a physical property intrinsic to objects" is an audacious metaphysical claim, not a result.

**Deeper.** → [[assembly-theory-origin-of-life]].

---

## Consciousness theory landscape

*Use before making a claim about whether X is conscious or before citing a theory. No consensus exists; the landscape is the thing.*

**Shape.**
- **Hard problem** (Chalmers 1995): explaining function doesn't explain experience. This framing is itself *contested* (illusionists deny the framing).
- **IIT** (Tononi, Koch): consciousness *is* integrated causal structure, measured by Φ. Panpsychist-adjacent. Predicts posterior-hot-zone substrate.
- **GNWT** (Dehaene, Changeux): consciousness is broadcast across a prefrontal–parietal workspace. Predicts late prefrontal ignition.
- **HOT** (Rosenthal): a state is conscious iff there's a higher-order state about it. Functionalist.
- **Illusionism** (Frankish, Dennett): phenomenal consciousness is systematic introspective misrepresentation. Meta-problem replaces hard problem.
- **Panpsychism** (Goff, Strawson): proto-experience in fundamental physical entities. Combination problem unresolved.
- **Predictive processing** (Seth, Friston, Clark): better theory of *content* of experience than of *existence* of experience.
- **COGITATE**: adversarial IIT vs GNWT collaboration; 2023–25 results partial, neither decisively confirmed.

**Handles.**
- Butlin et al. 2023 indicator-property report: no current AI clearly satisfies enough indicators for strong candidacy, but nothing in principle rules it out.
- PCI (Casali et al. 2013): empirical discriminator of wakeful vs unresponsive states.
- 2023 IIT-as-pseudoscience letter: 124 signatories; contested episode, not a verdict.

**Traps.**
- Don't take any single theory as established.
- Don't let "the easy problems are easy" mislead you — "easy" means tractable, not solved.
- Don't let behavioural evidence stand in for consciousness evidence. Markers (PCI) are for *presence* of consciousness, not *contents*.
- The "substrate independence" intuition is *orthogonal* to the hard problem. Don't let one answer assume the other.

**Deeper.** → [[hard-problem-consciousness]], [[mechanistic-interpretability]] for AI application.

---

## Popular-narrative-vs-evidence traps

*Before citing a public-facing claim, check whether it survives primary literature. Known cases in this vault.*

**Shape.**
- Popular science consistently overstates primary literature by 30–70 %. This is systemic — not a few bad actors — because popularisers have dramatisation incentives that researchers do not.
- The gap tends to widen in areas with photogenic science (plants, octopus, AI, consciousness, origins of life).
- The correction usually comes years later, quietly, in the specialist literature.

**Handles — known cases.**
- **"Mother trees / wood-wide web"** — Wohlleben, Simard. Critical re-evaluation: Karst, Jones, Hoeksema 2023. CMNs are real; kin-biased communicative function is not well supported.
- **Plant associative learning** — Gagliano 2016. Failed replication: Markel 2020. Treat as *contested*, burden on defenders.
- **Assembly theory "new theory of evolution"** — Sharma et al. 2023 *Nature*. Empirical part promising; theoretical extension overstretched. See AT primer above.
- **"Golden Gate Claude" / mechanistic interpretability** — real and striking; popular coverage implies more completeness than the research warrants.
- **"Tardigrade indestructibility"** — only some species are extremotolerant; solar UV and crushing still kill them.
- **"Voynich decipherment"** — every claimed solution has collapsed in peer review.
- **"Octopus observational learning"** (Fiorito & Scotto 1992) — complicated replication history; don't cite as unambiguous.

**Traps.**
- Simard-style citation drift: a single original finding cited with *increasing* confidence over time while the evidence does not strengthen. Check how many primary papers a popular claim actually rests on.
- Book + TED-talk combo is a strong marker of a gap between message and evidence. Not automatic; a strong one.
- "Science writers misunderstand the study" is *not* always the mechanism. Often the *researcher* is overstating in public-facing venues, and the science writer faithfully reports.

**Deeper.** → [[plant-cognition-mycorrhizal-networks]], [[assembly-theory-origin-of-life]], [[mechanistic-interpretability]], [[tardigrades-vitrify-themselves-to-survive-desiccation]], [[voynich-statistics-look-like-language]].

---

## Convergent evolution — when to claim it

*Use before saying "X evolved independently N times." The claim is usually weaker or stronger than it sounds.*

**Shape.**
- Convergent evolution = independent lineages arriving at similar phenotypes from different ancestral states.
- Distinct from **parallel evolution** (similar lineages, similar starting points) and **homology** (shared trait inherited from common ancestor).
- Strong evidence: similar phenotype + dissimilar developmental route + dissimilar gene-regulatory architecture, or similar gene-regulatory architecture but the trait is absent in the common ancestor and intermediate lineages.
- Weak evidence: just "X has trait Y, and so does Z, and they're distantly related" — doesn't rule out hidden homology or repeated loss.
- **Deep regulatory homology can underlie morphological convergence.** PAX6 in eye development is the canonical example: independent eye morphologies built on a shared ancient genetic toolkit.

**Handles.**
- Camera-type eyes: ≥5 independent origins (vertebrates, cephalopods, box jellyfish, alciopid worms, some snails).
- Photoreception generally: shared molecular toolkit (opsins, retinal) — not a convergence story at the molecular level.
- C4 photosynthesis: independently evolved 60+ times in plants — clean convergence case.
- Echolocation in bats and toothed whales: anatomically convergent + recent work shows convergent molecular evolution in hearing genes.
- Powered flight: 4 times (insects, pterosaurs, birds, bats). All vertebrate cases use forelimbs differently.

**Traps.**
- "Eyes evolved 40 times" conflates *photoreceptors* (ancient and shared), *eye spots* (many origins), and *camera-type eyes* (rare and the genuine convergence story). Be specific.
- A shared regulatory gene (PAX6) does *not* mean the eye is homologous in the morphological sense. It means the toolkit is shared.
- Convergence claims are sometimes inflated for narrative purposes ("convergence proves design X is optimal"). The actual claim should be "convergence is consistent with design X being a strong local optimum given certain constraints."
- **Loss is sometimes mistaken for convergent absence.** A trait absent in two distantly related lineages may have been present in their common ancestor and lost twice — not absence-by-convergence.

**Deeper.** → [[camera-eyes-evolved-independently-with-different-design-choices]], and [[octopus-cognition]] for the cephalopod side.

---

## Kinetic proofreading — when biological fidelity matters

*Consult before reasoning about accuracy in biological copying, signalling, or selection. The Hopfield-Ninio trick is specific and often misremembered.*

**Shape.**
- Equilibrium discrimination between correct (C) and incorrect (I) substrates is bounded by exp(ΔΔG / k_B T). Often only factor 20–150 for near-cognate pairings.
- Real biological error rates are 2–5 orders of magnitude lower. The gap is paid in ATP/GTP.
- The trick: insert an *irreversible* energy-consuming step between initial binding and commitment. Mismatched substrates preferentially dissociate during the delay.
- Selectivity ≈ squared (or cubed with multi-stage): (Boltzmann factor)².
- Cost: one GTP/ATP per rejected incorrect substrate. Fidelity is not free.

**Handles.**
- Hopfield 1974; Ninio 1975. Co-founding papers.
- Ribosome: ~10⁻⁴ error rate via EF-Tu·GTP hydrolysis as the irreversible step.
- DNA Pol III: ~10⁻⁷ via 3'→5' exonuclease editing (editing variant of the same principle).
- aaRS editing domains (IleRS, ValRS, LeuRS).
- Murugan, Huse, Leibler 2012 — modern theoretical treatment, speed-accuracy-dissipation tradeoffs.

**Traps.**
- The proofreading trick requires *irreversibility*, not just energy consumption. A reversible ATP-binding step gives no amplification.
- "Squaring" is schematic. Actual gain depends on rate-constant ratios and can be less or (multi-stage) more.
- Proofreading ≠ editing. Ribosome proofreads via branching; DNA Pol III proofreads via excision. Different mechanisms, same abstract principle.
- Organisms that don't proofread aren't broken — mitochondrial DNA polymerase and viral polymerases run with weaker fidelity for reasons of speed or evolvability.
- Hopfield proofreading is a *special case* of the general thermodynamic-cost-of-accuracy principle. Don't generalise from the special case without care.

**Deeper.** → [[kinetic-proofreading]], [[landauer-thermodynamics-computation]] for the general framework.
