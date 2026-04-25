# Facts

[Author: agent (prompted by user)]

Raw facts, numbers, and specific claims I want to be able to look up later. One bullet = one fact. Bold the key noun or phrase. Cite inline in `[Author Year]` form. Confidence tag where useful. Link to full notes where relevant with `→ [[name]]`.

Format rules in [[conventions]] under "Companion files".

## Cosmology and information

- **Bekenstein bound.** S ≤ 2π k_B R E / (ħc) for any system of radius R and total energy E. [Bekenstein 1973] *(established)*. → [[bekenstein-bound-and-holographic-information]]
- **Bekenstein–Hawking entropy.** A black hole has entropy S_BH = k_B A / (4 ℓ_P²) — proportional to *area*, not volume. ℓ_P ≈ 1.6 × 10⁻³⁵ m.
- **Planck length.** ℓ_P = √(ħG/c³) ≈ 1.6 × 10⁻³⁵ m.
- **Hawking temperature.** T_H = ħc³ / (8π G M k_B) for a Schwarzschild black hole.
- **Holographic principle.** Number of independent degrees of freedom in any region ≤ A / (4 ℓ_P²). ['t Hooft 1993; Susskind 1995] *(established as theoretical-physics consensus; exact scope debated)*.
- **AdS/CFT.** Quantum gravity in 5D AdS₅ × S⁵ ≡ N=4 super-Yang-Mills on the AdS boundary. [Maldacena 1997] *(established as a working duality for the cases studied)*.
- **Page curve resolution.** Black hole information paradox substantially resolved 2019–2020 by gravitational path integral / island formula. [Penington 2020; Almheiri et al. 2020] *(established for the specific models analysed)*.

## Physics and thermodynamics

- **k_B T at 300 K.** ≈ 4.1 × 10⁻²¹ J ≈ 0.025 eV. Standard.
- **Landauer bound at 300 K.** k_B T ln 2 ≈ 2.85 × 10⁻²¹ J per erased bit ≈ 0.017 eV. [Landauer 1961], experimentally verified [Bérut et al. 2012] *(established)*. → [[landauer-thermodynamics-computation]]
- **Modern CMOS energy per switch.** ~10⁻¹⁵ J ≈ 2.5 × 10⁵ k_B T ≈ 10⁶ × the Landauer bound. *(established for ~2024 nodes)*
- **ATP energy budget.** One ATP hydrolysis delivers ~20 k_B T ≈ 8 × 10⁻²⁰ J at 300 K. Enough for ~29 Landauer bits of erasure if Landauer-optimal. [biochemistry standard] *(established)*. → [[why-biology-runs-near-the-landauer-bound]]
- **Bennett closed Maxwell's demon.** The demon must erase its memory to run the cycle again; erasure dissipates exactly the work the engine extracted [Bennett 1982]. *(established)*
- **Bennett's reversible computing trick.** Any computation can in principle be done with arbitrarily small energy dissipation if it is logically reversible [Bennett 1973] *(established in theory; not commercialised)*.
- **Brain power.** Adult human brain ~20 W for ~10¹⁵ synaptic operations per second → ~10⁻¹⁴ J per synaptic op, similar order to CMOS. Brain efficiency per bit is not as good as a ribosome's.

## Biology at the molecular and cellular level

- **Ribosome energetics.** ~5 ATP per amino acid addition → ~100 k_B T per peptide bond plus ~5–10 k_B T proofreading overhead. A few dozen Landauer bits for selecting one amino acid from 20. [Hopfield 1974; biochemistry standard] *(established)*
- **Ribosome error rate.** ~10⁻⁴ per amino acid. Achievable only with kinetic proofreading — equilibrium binding-energy discrimination would give ~10⁻² *(established)*. → [[kinetic-proofreading]]
- **Kinetic proofreading.** Hopfield 1974, Ninio 1975: ribosomes and DNA polymerases spend ATP to reduce error rates beyond the equilibrium Boltzmann bound. Formally analogous to Landauer: reducing entropy of correct-vs-incorrect bit requires dissipation [Hopfield 1974] *(established)*. → [[kinetic-proofreading]]
- **Hopfield squaring.** Proofreading multiplies equilibrium selectivity by roughly itself: a factor-100 equilibrium becomes ~10⁴ at cost of the GTP hydrolysis per rejected substrate *(established as schematic; exact gain depends on rate constants)*.
- **DNA polymerase III error rate.** ~10⁻⁷ per base in *E. coli* — three orders of magnitude better than ribosomal translation because replication can tolerate higher ATP cost per decision.
- **V(D)J recombination.** The RAG1/RAG2 enzymes that diversify antibodies are evolutionarily descended from an ancient transposase — a domesticated transposon. *(established)*.
- **Tardigrade water loss in anhydrobiosis.** Up to ~99% body water loss; reversible. [Guidetti 2011] *(established)*. → [[tardigrades-vitrify-themselves-to-survive-desiccation]]
- **Tardigrade glass state.** CAHS, MAHS, SAHS proteins vitrify the cytoplasm; Dsup protein physically shields DNA from radicals. Unique to phylum Tardigrada. → [[tardigrades-vitrify-themselves-to-survive-desiccation]]
- **Cephalopod RNA editing.** Tens of thousands of A-to-I editing sites in neural transcriptome vs ~dozens in humans [Liscovitch-Brauer et al. 2017] *(established)*. → [[cephalopods-trade-genome-evolvability-for-rna-editing-plasticity]]

## Eyes and vision (comparative)

- **Camera-type eyes evolved independently** at least 5 times: vertebrates, cephalopods, box jellyfish, alciopid annelids, some snails. *(established)*. → [[camera-eyes-evolved-independently-with-different-design-choices]]
- **Vertebrate retina is inverted.** Photoreceptors point away from incoming light; axons exit through the optic disc producing the blind spot. Developmental constraint from evagination of the diencephalon.
- **Cephalopod retina is everted.** Photoreceptors face the light; no blind spot. Developmental route via invagination of surface ectoderm.
- **Box jellyfish eye count.** 24 eyes total in 4 rhopalia of 6 each; 2 of the 6 in each rhopalium are camera-type with a lens. No conventional brain. [Garm et al. 2007] *(established and remarkable)*.
- **PAX6 deep homology.** Master regulator of eye development conserved across vertebrates, cephalopods, insects. Ectopic *eyeless* expression induces eyes in *Drosophila* legs [Halder, Callaerts & Gehring 1995] *(established that the genetic toolkit is shared; "all eyes share an ancestor" reading is more nuanced)*.
- **Müller cells as fibre optics.** Vertebrate retinal Müller glial cells channel light efficiently to photoreceptors despite the inverted layering [Franze et al. 2007] *(established; partial defence of the inverted design)*.
- **Photoreceptor types.** Vertebrate = ciliary (rods, cones); cephalopod = rhabdomeric (microvillar). Deep developmental-evolutionary distinction predating bilaterians.

## Octopus, specifically

- **Neuron count.** ~500 M neurons, roughly 2/3 in the arms, 1/3 in central brain plus very large optic lobes. [Hochner 2012] *(widely cited estimate, not high precision)*. → [[octopus-arms-do-their-own-motor-planning]]
- **Arm motor program.** A surgically isolated arm still produces the "fetch" reach when stimulated; motor program lives in the axial nerve cord [Sumbre et al. 2001] *(established)*.
- **Colour blindness vs skin photoreception.** Retina typically has single rhodopsin; skin expresses opsins and contracts chromatophores in response to light [Ramirez & Oakley 2015] *(established that skin is photosensitive; its role in behaviour is open)*.
- **Chromatic-aberration colour vision hypothesis.** [Stubbs & Stubbs 2016] proposes the U-shaped pupil enables colour discrimination via defocus. *(speculative but not dismissed)*
- **Active sleep in octopus.** ~40-second episodes of skin patterning during sleep in *Octopus insularis* [Medeiros et al. 2021]; similar in cuttlefish [Pophale et al. 2023].

## Slime mould (Physarum polycephalum)

- **Oscillation period.** ~60–120 seconds for actomyosin contractions driving cytoplasmic streaming. *(established)*. → [[slime-mold-computation]]
- **Maze result.** *Physarum* retracts from dead ends leaving a single tube on the shortest path between two food sources [Nakagaki et al. 2000] *(established)*.
- **Tokyo network result.** Approximates real Tokyo rail network's efficiency/fault-tolerance tradeoff with oat flakes at city positions [Tero et al. 2010] *(established, though "matches human engineering" is overstated in popular coverage)*.
- **Physarum solver.** Continuous flow equation proven to converge to shortest path under certain conditions [Bonifaci et al. 2012].
- **Memory.** Habituates to quinine [Boisseau et al. 2016]; anticipates periodic stimuli [Saigusa et al. 2008]; trained plasmodia transfer learning via fusion [Vogel & Dussutour 2016].

## Collective intelligence

- **Honeybee nest-choice quorum.** ~15–20 scouts co-located at a candidate site trigger the piping signal. [Seeley 2010]. → [[collective-intelligence]]
- **Bee stop-signals = cross-inhibition.** Scouts dancing for A send stop-signals to scouts dancing for B [Seeley et al. 2012] *(established)*.
- **Starling neighbour rule.** Each bird attends to ~7 nearest neighbours regardless of absolute distance — topological, not metric [Ballerini et al. 2008] *(established)*.
- **Starling correlation length.** Scale-free: grows with flock size → signature of operation near a critical point [Cavagna et al. 2010].
- **Couzin three rules.** Repulsion, alignment, attraction produce swarm / torus / polarised school depending on zone sizes [Couzin et al. 2005].
- **Uninformed majority improves group decisions.** Adding uninformed individuals increases the informed minority's influence [Couzin et al. 2011] *(established; often overgeneralised in popular coverage)*.
- **Condorcet's jury theorem.** If voters are >50% accurate and independent, majority-vote accuracy → 1 as jury grows. Breaks with correlated voters.

## AI / mechanistic interpretability

- **Superposition in small nets.** Networks pack more features than dimensions by using nearly-orthogonal directions [Elhage et al. 2022] *(established in toy models)*. → [[superposition-explains-polysemanticity]]
- **Induction heads.** Pair of attention heads (previous-token + match-and-copy) implements in-context `A B ... A → B`; emerges abruptly during training [Olsson et al. 2022] *(established and replicated)*.
- **Golden Gate Claude.** Produced by clamping a specific SAE feature in Claude 3 Sonnet [Templeton et al. 2024].
- **IOI circuit in GPT-2 Small.** Reverse-engineered handful of attention heads doing name-duplication detection, S-inhibition, name-moving [Wang et al. 2022].
- **Training compute rough.** Frontier LLM training is ~10²⁰–10²¹ FLOPs, megawatt-hours at tens of pJ per op. Landauer floor is ~10⁵–10⁶ × smaller in principle.

## Astronomy and history

- **Antikythera wreck date.** ~70–60 BCE (coins, amphorae). → [[antikythera-mechanism]]
- **Antikythera construction date.** Between ~205 and ~100 BCE. [Carman & Evans 2014] argued 205 BCE from eclipse-prediction back-calculation. *(contested within that window)*
- **Antikythera gearing.** ≥30 gears identified directly, 37+ in full reconstruction [Freeth et al. 2021]. Teeth ~1 mm hand-cut triangles.
- **Metonic cycle.** 19 tropical years ≈ 235 synodic months; device for reconciling lunar/solar calendars. Used on the Antikythera back face.
- **Saros cycle.** 223 synodic months ≈ 18 years 11 days. Device for predicting eclipse recurrence.
- **Callippic cycle.** 76 years = 4 Metonic − 1 day. Refines Meton.
- **Pin-and-slot lunar anomaly.** Antikythera mechanism's device for modelling the Moon's variable apparent speed (first anomaly); accurate to ~1 part in 200 [Gourtsoyannis 2010].

## Consciousness

- **Hard problem phrase.** Coined by [Chalmers 1995]. → [[hard-problem-consciousness]]
- **PCI (Perturbational Complexity Index).** TMS pulse + EEG response + complexity measure; reliably discriminates wakeful / dreaming / unresponsive states [Casali et al. 2013] *(established)*.
- **COGITATE collaboration.** Templeton-funded adversarial IIT-vs-GNWT collaboration, 2019–2025. Posterior-cortex-sustained signatures favoured IIT; prefrontal ignition weaker than GNWT predicted. *(mixed; neither decisively confirmed)*
- **Butlin et al. 2023 AI-consciousness report.** Indicator-property approach; no current AI clearly satisfies enough indicators [Butlin et al. 2023].
- **IIT "pseudoscience" letter.** 124 researchers signed September 2023. *(contested episode in the field)*.

## Assembly theory

- **MA > 15 biosignature claim.** Molecular assembly index above ~15 in tandem MS data reliably found only in biotic samples [Marshall et al. 2021] *(mixed; provisional)*. → [[assembly-theory-origin-of-life]]
- **Sharma et al. 2023.** *Nature* paper extending AT into a unifying framework for selection and evolution. Reception sharply divided.

## Language and misc

- **Voynich manuscript vellum date.** Radiocarbon 1404–1438 [Hodgins 2011] *(established)*. → [[voynich-statistics-look-like-language]]
- **Voynich Zipf and Heaps.** Word frequencies and vocabulary growth match natural-language curves [Montemurro & Zanette 2013].
- **Finnish "15 cases".** Mostly agglutinative postpositions; six locative cases form a 2×3 spatial/directional matrix. → [[finnish-cases-are-mostly-postpositions]]
- **Pirahã phoneme count.** 10 or 11 phonemes depending on count — one of the smallest inventories known. Two tones. Language survives as whistled and hummed registers. *(established)*. → [[does-piraha-lack-recursion]]
- **Gordon 2004 Pirahã number study.** Speakers fail exact-match tasks above ~3 items; suggests no exact-number cognition without exact-number words. [Gordon 2004] *(established finding; interpretation contested)*.
- **Hauser-Chomsky-Fitch 2002.** Proposed **recursion** as the unique defining feature of the human language faculty (FLN — Faculty of Language in the Narrow Sense). The 2005 Everett Pirahã paper is its most prominent empirical challenge.
- **Mycorrhizal critique.** [Karst et al. 2023] documents citation drift on "mother tree" claims. → [[plant-cognition-mycorrhizal-networks]]

## History of science

- **McClintock Ac/Ds.** Ac (Activator) and Ds (Dissociation) — maize transposon system, discovered 1944–1950 by Barbara McClintock. First identified transposable elements [McClintock 1950] *(established)*. → [[mcclintock-and-the-forty-year-delay]]
- **Transposon fraction of human genome.** ~45% recognisably transposon-derived; higher estimates include more degraded ancient elements [IHGSC 2001] *(established; lower bound)*.
- **Maize genome transposons.** ~85% transposon-derived — the organism where they were first discovered has among the highest fractions known.
- **Active human transposons.** LINE-1 (autonomous), SINE/Alu (non-autonomous, ~1M copies), HERV-K. LINE-1 activity in neuronal progenitors documented [Muotri & Gage 2010] *(established; functional significance mixed)*.
- **McClintock Nobel year.** 1983, unshared, for the maize controlling-elements work done 30+ years earlier.
- **Syncytin.** The protein enabling trophoblast fusion in mammalian placentas is an exapted endogenous retrovirus envelope gene — a transposon contribution to a fundamental biological structure. *(established)*.

## Sources

- [Almheiri et al. 2020] arXiv:1905.08762.
- [Ballerini et al. 2008] *PNAS* 105:1232.
- [Bekenstein 1973] *Phys. Rev. D* 7:2333.
- [Bennett 1973] *IBM J. Res. Dev.* 17:525.
- [Bennett 1982] *Int. J. Theor. Phys.* 21:905.
- [Bérut et al. 2012] *Nature* 483:187.
- [Boisseau et al. 2016] *Proc. R. Soc. B* 283:20160446.
- [Bonifaci et al. 2012] *J. Theor. Biol.* 309:121.
- [Butlin et al. 2023] arXiv:2308.08708.
- [Carman & Evans 2014] *Archive for History of Exact Sciences*.
- [Casali et al. 2013] *Sci. Transl. Med.* 5:198ra105.
- [Cavagna et al. 2010] *PNAS* 107:11865.
- [Chalmers 1995] *J. Consciousness Studies* 2:200.
- [Couzin et al. 2005] *Nature* 433:513.
- [Couzin et al. 2011] *Science* 334:1578.
- [Elhage et al. 2022] *Toy Models of Superposition*, Anthropic.
- [Franze et al. 2007] *PNAS* 104:8287.
- [Freeth et al. 2021] *Scientific Reports*, https://www.nature.com/articles/s41598-021-84310-w
- [Garm et al. 2007] *J. Exp. Biol.* 210:3616.
- [Gourtsoyannis 2010] *Advances in Space Research*.
- [Guidetti 2011] — tardigrade anhydrobiosis review.
- [Halder, Callaerts & Gehring 1995] *Science* 267:1788.
- [Hawking 1975] *Commun. Math. Phys.* 43:199.
- [Hochner 2012] *Current Biology* 22:R887.
- [Hodgins 2011] — Voynich vellum carbon dating.
- [Hopfield 1974] *PNAS* 71:4135.
- [Karst et al. 2023] *Nature Ecology & Evolution* 7:501.
- [Landauer 1961] *IBM J. Res. Dev.* 5:183.
- [Liscovitch-Brauer et al. 2017] *Cell* 169:191.
- [Maldacena 1997] arXiv:hep-th/9711200.
- [Marshall et al. 2021] *Nature Communications* 12:3033.
- [Medeiros et al. 2021] *iScience* 24:102223.
- [Montemurro & Zanette 2013] — Voynich statistical analysis.
- [Nakagaki et al. 2000] *Nature* 407:470.
- [Olsson et al. 2022] *In-context Learning and Induction Heads*, Anthropic.
- [Penington 2020] arXiv:1905.08255.
- [Pophale et al. 2023] *Nature* 619:129.
- [Ramirez & Oakley 2015] *J. Exp. Biol.* 218:1513.
- [Saigusa et al. 2008] *Phys. Rev. Lett.* 100:018101.
- [Seeley 2010] *Honeybee Democracy*, Princeton.
- [Seeley et al. 2012] *Science* 335:108.
- [Stubbs & Stubbs 2016] *PNAS* 113:8206.
- [Sumbre et al. 2001] *Science* 293:1845.
- [Susskind 1995] arXiv:hep-th/9409089.
- [Templeton et al. 2024] *Scaling Monosemanticity*, Anthropic.
- [Tero et al. 2010] *Science* 327:439.
- ['t Hooft 1993] arXiv:gr-qc/9310026.
- [Vogel & Dussutour 2016] *Proc. R. Soc. B* 283:20162382.
- [Wang et al. 2022] *Interpretability in the Wild*, arXiv:2211.00593.
