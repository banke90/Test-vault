# Tardigrades survive desiccation by turning their cytoplasm into glass

> Tardigrades tolerate near-total water loss, radiation, and vacuum mainly because disordered "TDP" proteins vitrify the cell interior into an amorphous solid that locks biomolecules in place until rehydration.

[Confidence: mixed]
[Last verified: 2026-04-22]
[Kind: concept]

## TL;DR

When tardigrades dry out, a family of intrinsically disordered proteins unique to the phylum — the **CAHS, MAHS, and SAHS** families, collectively **TDPs** — concentrate, gel, and vitrify the cytoplasm into a biological glass that arrests molecular motion and locks membranes and proteins in place until rehydration. A separate protein, **Dsup**, wraps nucleosomes and physically shields DNA from hydroxyl radicals, which is the dominant mechanism of their radiation tolerance. The popular "indestructible" story is overstated: tardigrades are crushed easily, solar UV still kills them, and only a minority of species are truly extremotolerant — mostly those that evolved in mosses and lichens that dry out regularly. The interesting translational angle is that CAHS and Dsup work in yeast and human cells, opening a route to cold-chain-free storage of biologics.

## The cryptobiosis problem

Tardigrades ("water bears") are ~0.5 mm eight-legged micro-animals that can enter **cryptobiosis**: a reversible, metabolism-approximately-zero state triggered by desiccation, freezing, osmotic stress, or anoxia. In the desiccation form ("anhydrobiosis"), tardigrades shrivel into a compact "tun" shape, lose up to ~99% of their body water, and can remain viable for years — in extreme laboratory and reported field cases, decades *(mixed)* [Guidetti 2011].

The puzzle is that most cellular machinery assumes water. Lipid bilayers phase-separate, proteins unfold or aggregate irreversibly, DNA shears, and reactive oxygen species from trace metabolism accumulate with no repair running. If you take an ordinary animal cell to 1% hydration and then rehydrate it, you do not get a living cell back. So the question is not "how do tardigrades tolerate dryness?" but "what do they put into the cell that replaces the structural and chemical roles water was playing?"

Two candidate answers are longstanding across anhydrobionts broadly: **trehalose**, a non-reducing disaccharide that nematodes, brine shrimp, and bakers' yeast use to vitrify and/or hydrogen-bond-substitute for water; and **LEA proteins** (Late Embryogenesis Abundant), intrinsically disordered proteins found in desiccation-tolerant plant seeds and rotifers [Hibshman 2020]. Tardigrades have LEA proteins but conspicuously low trehalose — several species make <0.1% dry weight, orders of magnitude less than a nematode like *Aphelenchus* [Hengherr 2008] *(established)*. Something else is doing the job.

## TDPs and the vitrification hypothesis

The something-else is a family of **tardigrade-specific intrinsically disordered proteins (TDPs)**, so named because sequence homologs are not found outside Tardigrada and because, in solution, they lack stable tertiary structure. Three subfamilies are defined by predicted localisation [Boothby 2017, Tanaka 2022]:

- **CAHS** — Cytoplasmic Abundant Heat-Soluble
- **MAHS** — Mitochondrial Abundant Heat-Soluble
- **SAHS** — Secretory Abundant Heat-Soluble

"Heat-soluble" is a working definition: boil a tardigrade lysate, most proteins precipitate, these stay in solution, which is a hallmark of intrinsic disorder. CAHS proteins are the best-studied and the most directly tied to survival: knocking out even one CAHS or SAHS gene in *Hypsibius exemplaris* produces measurable drops in desiccation survival, and expressing CAHS in yeast, *E. coli*, or human cell lines confers partial desiccation tolerance on those hosts [Boothby 2017] *(established for in vitro/heterologous; species-level importance in tardigrades themselves is mixed)*.

The **vitrification hypothesis**, the currently favoured mechanism, says: as water leaves the cell, CAHS proteins concentrate, undergo a disorder-to-order transition (some form gel-like fibrous networks, others adopt alpha-helical bundles), and the cytoplasm crosses a glass transition into an **amorphous solid** — a biological glass. In this state, molecular motion is arrested on experimentally relevant timescales. Lipid bilayers stay pinned in place, proteins cannot diffuse to aggregate, DNA cannot whip around and shear. The cell is a paused, brittle diorama of itself.

Supporting observations *(established)*:

- Purified CAHS proteins in vitro gelate and vitrify on drying, with glass transition temperatures measurable by differential scanning calorimetry.
- Anhydrobiotic tardigrades show glass-like mechanical properties; warming above the glass transition (~60–70 C in some species) correlates with loss of viability even without rehydration.
- Heterologous expression of CAHS in desiccation-sensitive cells confers tolerance in rough proportion to the vitrifying capacity measured biophysically.

Competing/complementary proposals also on the table: **water replacement** (TDPs hydrogen-bond to membranes and proteins, substituting for water's structural role) and **preferential hydration/molecular shield** (TDPs hold residual water near sensitive surfaces and physically separate aggregation-prone partners). These are not mutually exclusive with vitrification — the consensus as of 2024 is that CAHS likely does all three at different stages of drying [Hesgrove & Boothby 2020].

## Dsup and radiation tolerance

Vitrification explains desiccation. It does not explain why hydrated, active tardigrades also shrug off ionising radiation at doses (1000+ Gy) that sterilise most animals hundreds of times over. The leading molecular answer for one species, *Ramazzottius varieornatus*, is **Dsup** — "Damage Suppressor" — a ~445 aa nuclear protein identified in 2016 [Hashimoto 2016].

Dsup binds nucleosomes. A conserved internal region has sequence similarity to the nucleosome-binding domain of vertebrate HMGN proteins, and binding requires both this HMGN-like motif and C-terminal sequences [Chavez 2019, elife; 2025 Nat Comms]. Mechanistically, Dsup is itself intrinsically disordered and engages the nucleosome at multiple points — the H2A/H2B acidic patch, H3/H4 histone tails, and linker DNA — forming what one paper calls a "diffuse mass" wrapping the chromatin surface. Physically, this cloud of disordered protein appears to **absorb or deflect hydroxyl radicals** (·OH) generated by radiolysis of water before they can reach the DNA backbone. It is, in effect, a chemical umbrella.

The striking practical finding is that Dsup works in non-tardigrade cells. HEK293 human cells transfected with Dsup tolerate roughly 40% more DNA damage from X-rays than controls [Hashimoto 2016] *(established, but the effect size is the low-end bound of what's useful — Dsup is not a magic bullet)*. Yeast expressing Dsup show extended lifespan under oxidative stress [2025 Nat Comms].

Caveats:

- Dsup was found in *R. varieornatus*, which is one of the more extremotolerant tardigrades. *Hypsibius exemplaris*, a common lab species, has a divergent Dsup variant with different and probably weaker activity [Chavez 2019].
- Dsup protects from hydroxyl-radical chemistry specifically. It doesn't do much for direct double-strand breaks caused by high-LET radiation, and one 2023 paper reports Dsup expression paradoxically **increases** DNA damage in neurons under some conditions [Ricci 2023] *(contested; single study).*
- Radiation tolerance in tardigrades is multi-pronged: Dsup is one layer. Others include efficient DNA repair (upregulation of MRE11, Rad51), antioxidant enzymes, and the fact that cryptobiotic tuns are essentially immune to radiation by virtue of having no active metabolism to disrupt.

## What the hype gets wrong

The "tardigrades are indestructible" framing hides the conditional. The feats are:

- **Survived in low Earth orbit vacuum + cosmic radiation** (TARDIS experiment, FOTON-M3, 2007): 68% of animals *protected from solar UV* rehydrated successfully. In the unshielded UV-B + vacuum combination, survival collapsed to near zero [Jönsson 2008].
- **Survived 1.14 GPa shock pressure** in gas-gun impact experiments, but not above. Estimates suggest the 2019 Beresheet lunar lander crash exceeded this — so the tardigrades aboard almost certainly died on impact [Traspas & Burchell 2021] *(established)*.
- **Survived 1000+ Gy ionising radiation in the tun state.** Active, hydrated tardigrades are much less tolerant, by roughly an order of magnitude.

Three recurring misconceptions worth flagging:

1. "Tardigrades don't need water." They emphatically do — when hydrated, they are ordinary micro-animals, and cryptobiosis is not a functional state. They pause biology; they don't exempt themselves from it.
2. "Tardigrades could survive on Mars / colonise space." The tun tolerates vacuum and radiation for days to months, not geological timescales; UV is a hard problem; and tuns do not reproduce, so there's no population dynamic without a habitable rehydration. The honest version is "desiccated tardigrades in shielded capsules are a plausible panspermia analogue for short interplanetary transits."
3. "All tardigrades are extremotolerant." They aren't. Marine tardigrades and many limnic species tolerate little beyond their native conditions. Extreme tolerance is concentrated in terrestrial species adapted to moss/lichen cushions that dry out regularly — *Ramazzottius varieornatus*, *Milnesium tardigradum*, some *Macrobiotus*. The taxon-wide reputation is owed to a minority [Møbjerg 2018].

Useful steel-man: even with these caveats, tardigrades survive environmental insults that no vertebrate comes within three orders of magnitude of. That is genuinely remarkable. The mechanism (disordered proteins that vitrify and radical-scavenge) is also what makes them practically interesting — CAHS and Dsup are under active investigation as **desiccation-protectants for vaccines, blood products, and cell therapies** that currently require cold-chain logistics [Boothby 2023 review].

## Disagreements and cautions

- **How central is vitrification, really?** Boothby et al. 2017 pushed vitrification as *the* mechanism, with dried CAHS behaving glassily. Subsequent work (Hesgrove & Boothby 2020, Tanaka 2022) has walked this back to "one of three complementary modes" — vitrification, water replacement, molecular shielding — with the balance varying by TDP subfamily and drying rate. Reviewers who read the 2017 paper alone overstate the case.
- **CAHS gelation in living cells.** Some in vitro studies find CAHS forms stiff gels at high concentration. Whether the same gelation happens in vivo, and whether it is required for protection, is *(contested)* — live-cell imaging in drying tardigrades is genuinely hard.
- **Dsup universality.** The HMGN-like motif is conserved across tardigrade Dsup homologs, but radiation tolerance differences between species are not well explained by Dsup sequence alone. DNA repair upregulation may matter at least as much.
- **Ricci et al. 2023** reported Dsup promoting DNA damage in neurons — inconsistent with the protective picture. Single study, unusual cell type; treat as a flag for follow-up, not a refutation.
- **Horizontal gene transfer claim (2015).** Boothby et al. initially claimed ~17% of the tardigrade genome was from foreign (bacterial/archaeal) sources. This was rapidly rebutted as a contamination artefact [Koutsovoulos 2016]. The corrected HGT fraction is ~1–2%, similar to other animals. Worth knowing because the original claim still circulates in pop-science pieces.

## Questions I'd like answered

1. In intact drying tardigrades, is the cytoplasm measurably glassy by direct in vivo spectroscopy, or is the glass evidence all on purified CAHS plus bulk mechanical measurements on whole tuns? A definitive FRAP or single-molecule tracking experiment in drying cells would settle it.
2. What sets the **glass transition temperature** of a cryptobiotic tardigrade, and does it predict long-term survival limits better than current empirical curves? If Tg explains longevity, we have a design parameter for engineered desiccation-tolerant cells.
3. Why does *Ramazzottius* have strong Dsup activity while *Hypsibius exemplaris* does not, despite both being extremotolerant? Is Dsup substituted by something else in *Hypsibius*, or is radiation tolerance polygenic and Dsup only important in lineages with a particular ecology?
4. Can CAHS + Dsup plus an antioxidant cocktail confer usable desiccation tolerance on human blood cells or induced pluripotent stem cells for warehouse storage? Early results are encouraging but lossy.
5. What rehydration damage mechanisms dominate, and are they separable from desiccation damage? Losing animals "on the way back up" is a distinct and under-studied failure mode.
6. Are there tardigrade species whose tuns have been revived after genuinely long (decades–centuries) storage under controlled conditions, as opposed to anecdotal herbarium-sample claims? The literature here is thinner than popular accounts suggest.

## Sources

- [Boothby 2017] Boothby T.C. et al. "Tardigrades Use Intrinsically Disordered Proteins to Survive Desiccation." *Molecular Cell* 65(6). https://pmc.ncbi.nlm.nih.gov/articles/PMC5987194/
- [Boothby 2023 review] / [Hesgrove & Boothby 2020] Hesgrove C., Boothby T.C. "The biology of tardigrade disordered proteins in extreme stress tolerance." *Cell Communication and Signaling*. https://biosignaling.biomedcentral.com/articles/10.1186/s12964-020-00670-2
- [Chavez 2019] Chavez C. et al. "The tardigrade damage suppressor protein binds to nucleosomes and protects DNA from hydroxyl radicals." *eLife* 8:e47682. https://elifesciences.org/articles/47682
- [Guidetti 2011] Guidetti R., Altiero T., Rebecchi L. "On dormancy strategies in tardigrades." *Journal of Insect Physiology*.
- [Hashimoto 2016] Hashimoto T. et al. "Extremotolerant tardigrade genome and improved radiotolerance of human cultured cells by tardigrade-unique protein." *Nature Communications* 7:12808.
- [Hengherr 2008] Hengherr S. et al. "Trehalose and anhydrobiosis in tardigrades — evidence for divergence in responses to dehydration." *FEBS Journal*.
- [Hibshman 2020] Hibshman J.D., Clegg J.S., Goldstein B. "Mechanisms of desiccation tolerance: themes and variations in brine shrimp, roundworms, and tardigrades." *Frontiers in Physiology*.
- [Jönsson 2008] Jönsson K.I. et al. "Tardigrades survive exposure to space in low Earth orbit." *Current Biology* 18(17). https://www.sciencedirect.com/science/article/pii/S0960982208008051
- [Koutsovoulos 2016] Koutsovoulos G. et al. "No evidence for extensive horizontal gene transfer in the genome of the tardigrade *Hypsibius dujardini*." *PNAS* 113(18).
- [Møbjerg 2018] Møbjerg N. et al. "Survival in extreme environments — on the current knowledge of adaptations in tardigrades." *Acta Physiologica*.
- [Ricci 2023] Ricci C. et al. "The Tardigrade damage suppressor protein Dsup promotes DNA damage in neurons." *Molecular and Cellular Neuroscience*. https://pmc.ncbi.nlm.nih.gov/articles/PMC10247392/
- [Tanaka 2022] Tanaka A. et al. Review of CAHS/MAHS/SAHS nomenclature and functional divergence. *Communications Biology*.
- [Traspas & Burchell 2021] Traspas A., Burchell M.J. "Tardigrade survival limits in high-speed impacts — implications for panspermia and collection of samples from plumes emitted by ice worlds." *Astrobiology*.
- [2025 Nat Comms] "Multivalent binding of the tardigrade Dsup protein to chromatin promotes yeast survival and longevity upon exposure to oxidative damage." *Nature Communications*. https://www.nature.com/articles/s41467-025-63652-3
- SAHS 2024 paper: https://www.nature.com/articles/s42003-024-06336-w
- Dsup overview: https://en.wikipedia.org/wiki/Dsup

## Links

- `octopus-cognition.md` — different model organism, but similar pattern of a taxon whose biology is genuinely weird enough that mechanisms have no vertebrate analogue. Both cases reward resisting the urge to translate into mammal-terms.
- `plant-cognition-mycorrhizal-networks.md` — compare the LEA-protein route to desiccation tolerance used in plant seeds with the TDP route tardigrades use. Convergent problem (survive dry), different disordered-protein solutions.
- `hard-problem-consciousness.md` — tangential but useful: cryptobiosis is a clean empirical case of a metabolically-halted animal that resumes on rehydration. If "consciousness requires continuity of process", tardigrades are a mild counterexample; if it doesn't, they're not.
- `why-biology-runs-near-the-landauer-bound.md` — Landauer concerns the thermodynamic floor of computation in active cells. Cryptobiosis is the opposite limit: pause the computation, spend no energy, wait. The two notes bracket what "metabolism" is for.
- `assembly-theory-origin-of-life.md` — if vitrified tardigrades pause biology without destroying it, they are an interesting counterpoint to assembly-theory framings that equate "alive" with "ongoing assembly." A tun has no ongoing assembly but clearly is not dead.
