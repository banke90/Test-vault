# A single cell without neurons can solve mazes and approximate the Tokyo rail network

> *Physarum polycephalum* is a single multinucleate cell that solves shortest-path problems and builds efficient transport networks through flow-dependent tube reinforcement — a physical relaxation process that qualifies as computation on some reasonable definitions and not on others.

[Author: agent (prompted by user)]
[Confidence: mixed — the experimental results are solid; the "cognition" framing is a choice]
[Last verified: 2026-04-21]

## TL;DR

*Physarum polycephalum* is a plasmodial slime mould — one enormous multinucleate amoebozoan cell that solves mazes by retracting from dead ends [Nakagaki et al. 2000] and approximates Tokyo's rail-network efficiency/fault-tolerance tradeoff when oat flakes mark the stations [Tero et al. 2010]. It also habituates to aversive chemicals [Boisseau et al. 2016], anticipates periodic stimuli [Saigusa et al. 2008], and transmits learned behaviour by fusing with naïve partners [Vogel & Dussutour 2016]. None of this requires a nervous system. Whether it requires the word "cognition" is a framing choice with real stakes.

## What the organism actually is

A *Physarum* plasmodium is **a single cell with many thousands of diploid nuclei** sharing one cytoplasm. No internal cell membranes. It forms a living network of interconnected tubes — pulsing cytoplasmic streams driven by rhythmic actomyosin contractions with a period of 60–120 seconds *(established)*. Pressure pulses shuttle material around the network. Tubes carrying more flux thicken; tubes carrying less shrink.

That flow-feedback is the substrate of everything interesting *Physarum* does.

## The maze experiment

Nakagaki, Yamada, and Tóth put a plasmodium across a maze with two oat flakes at opposite ends [Nakagaki et al. 2000]. The organism initially spreads through the whole maze, then retracts from dead ends, leaving a single tube along the shortest path between the food sources.

The mechanism is **positive feedback on tube diameter**: higher flow reinforces tube radius (reducing resistance, raising flow further), lower flow shrinks tubes to nothing. The global shortest-path solution falls out of local physics. No search, no plan — just a gradient-following dissipative system *(established)*.

## The Tokyo rail-network experiment

Tero, Kobayashi, Nakagaki and collaborators [Tero et al. 2010] arranged oat flakes on the positions of Tokyo's major rail-network nodes and used light (which *Physarum* avoids) to encode mountains and water. Over ~26 hours the plasmodium formed a tube network.

Compared to the actual Tokyo rail network on three axes — total length, average path length between nodes, fault tolerance — the plasmodium hit a similar Pareto tradeoff, sometimes matching or beating the engineered solution on two of the three at once *(established)*.

This is not computation in the Turing sense. It is a physical relaxation process that happens to land on a reasonable spot in the efficiency-robustness tradespace. The useful surprise is that **cheap local substrate dynamics suffice for a problem we assume needs global planning**.

## Memory without neurons

*Physarum* has memory in any behavioural sense of the word:

- **Habituation.** Plasmodia trained to cross a bridge coated with bitter-but-harmless quinine or caffeine progressively stop slowing down, then reset after a rest [Boisseau et al. 2016]. Matches Thompson & Spencer's formal criteria for habituation *(established)*.
- **Anticipation of periodic stimuli.** Cold, dry pulses (which slow *Physarum*) delivered at regular intervals cause the organism to slow *at the time the pulse would arrive* — even when it is omitted — and to resume this anticipatory response after a long break [Saigusa et al. 2008] *(established; the effect is small but reproduced)*.
- **Learning transfer by cell fusion.** A trained plasmodium fused with a naïve one passes on the learned behaviour to the merged individual [Vogel & Dussutour 2016]. Memory, whatever it is physically, is shareable across what we'd otherwise call individuals *(established, striking, and underexplored)*.

What physically encodes the memory? Candidates include calcium dynamics, diffusible chemical concentrations (e.g. absorbed quinine altering internal state), and the tube-network topology itself. Probably several at once. No-one has pinned it down *(speculative on specifics)*.

## The toolkit

Putting it together, *Physarum* has:

1. A body that is simultaneously sensor, effector, and communication channel — cytoplasmic streaming connects every part to every part.
2. Chemical gradients for sensing food, humidity, and avoiding light.
3. Oscillatory contractions that phase-couple across the body, carrying local information to distant regions.
4. Flow-dependent tube reinforcement — a physical analogue of reinforcement learning on network topology.

The rules are simple. The behaviour is not.

## *Physarum* as a computational substrate

The dynamics have been abstracted into the **Physarum solver**, a continuous-flow equation for shortest-path and Steiner-tree approximations that provably converges under certain conditions [Bonifaci et al. 2012]. This is a rare case where a biological heuristic has been matched to a theorem.

There is also a small subfield building logic gates, sensors, and simple circuits out of live *Physarum* cultures on patterned substrates — most prominently **Andrew Adamatzky**'s group [Adamatzky 2010]. These are proofs of concept, not competitive implementations. Silicon beats slime mould at every axis except energy per operation and self-repair.

## Basal cognition as the framing

**Pamela Lyon**'s "basal cognition" programme [Lyon 2015] and **Michael Levin**'s bioelectric work argue that cognition is not a late, neural invention: discrimination, memory, anticipation, and minimal goal-directedness exist in organisms with no nervous system. On this reading, brains are *one* way to do cognition — fast, dense, and specialised — but not the only way. *Physarum* is exhibit A.

The opposing framing says "cognition" should be reserved for something richer than adaptive signal processing, and what *Physarum* does is impressive physics but not cognition *(contested)*. The disagreement is partly empirical, mostly definitional. Pick your side carefully; the word carries inferences you may not want.

## Disagreements and cautions

- **Calling *Physarum* intelligent is a framing choice.** The "maze-solving" is a flow relaxation, and the "Tokyo network" is a gradient descent. Both are cognitively impressive at the system level and mechanistically unremarkable at the local level. Whether the system-level impressiveness deserves "cognition" is a taste decision.
- **Habituation results are robust; anticipation results are small.** Saigusa's anticipatory slowing is a real effect, well replicated enough to cite, but it is a small behavioural shift, not a dramatic one. Don't oversell.
- **Learning-by-fusion (Vogel & Dussutour 2016) is striking but underreplicated** compared to the habituation result. Treat the single-study status as a live caveat.
- **Physarum computing as a practical technology** is overhyped in popular coverage. As of 2026, silicon beats it at everything except in-principle energy efficiency, and slime mould is not a practical route to that.
- **"Brainless cognition" is not a counter to the hard problem.** Behavioural markers of cognition don't tell us anything about experience. See [[hard-problem-consciousness]].

## Questions I'd like answered

1. **What is the physical substrate of habituation memory in a single cell?** Calcium-mediated gene-expression changes are one candidate, but direct evidence is thin.
2. **How are the oscillations phase-coupled across tens of centimetres?** The mechanical-hydraulic model is partial.
3. **What is the upper bound of behavioural complexity** for a brainless organism? Where does the ceiling sit, and what operations can *Physarum* simply not do?
4. **Could engineered slime-mould networks be useful as low-energy optimisation substrates?** In principle yes, in practice probably no. What would need to change to flip that?
5. **Does the fusion-transfer of learning work both ways** — naïve fusing with trained fully inherits, but does a trained individual "forget" when fused with many naïves?

## Sources

- [Adamatzky 2010] Adamatzky, A. *Physarum Machines: Computers from Slime Mould*. World Scientific.
- [Boisseau et al. 2016] Boisseau, R.P., Vogel, D., Dussutour, A. "Habituation in non-neural organisms: evidence from slime moulds." *Proc. R. Soc. B* 283:20160446. https://doi.org/10.1098/rspb.2016.0446
- [Bonifaci et al. 2012] Bonifaci, V., Mehlhorn, K., Varma, G. "Physarum can compute shortest paths." *J. Theor. Biol.* 309:121–133. https://arxiv.org/abs/1106.0423
- [Lyon 2015] Lyon, P. "The cognitive cell: bacterial behaviour reconsidered." *Frontiers in Microbiology* 6:264.
- [Nakagaki et al. 2000] Nakagaki, T., Yamada, H., Tóth, Á. "Intelligence: Maze-solving by an amoeboid organism." *Nature* 407:470. https://doi.org/10.1038/35035159
- [Saigusa et al. 2008] Saigusa, T., Tero, A., Nakagaki, T., Kuramoto, Y. "Amoebae anticipate periodic events." *Phys. Rev. Lett.* 100:018101.
- [Tero et al. 2010] Tero, A. et al. "Rules for biologically inspired adaptive network design." *Science* 327:439–442. https://doi.org/10.1126/science.1177894
- [Vogel & Dussutour 2016] Vogel, D., Dussutour, A. "Direct transfer of learned behaviour via cell fusion in non-neural organisms." *Proc. R. Soc. B* 283:20162382.

## Links

- [[octopus-cognition]] — cognition distributed across a body that *does* have neurons. *Physarum* is the limit case of the same distributional logic: no centre at all.
- [[collective-intelligence]] — many individuals behaving like one mind. *Physarum* is the inverse: one cell with many nuclei behaving like a swarm. Same algorithmic motifs (gradient-following, positive feedback with decay) appear in both.
- [[landauer-thermodynamics-computation]] — *Physarum* is among the clearest cases of biology computing near physics' floor, since the energy budget is purely metabolic and the "logic" is directly the substrate physics.
- [[why-biology-runs-near-the-landauer-bound]] — a direct follow-up to the thermodynamics question, with *Physarum* as one datapoint.
- [[assembly-theory-origin-of-life]] — another attempt to think about complexity in a substrate-general way; *Physarum* behaviour would be an interesting test case for the assembly-theory framework.
- [[plant-cognition-mycorrhizal-networks]] — the closest biological analogue among familiar organisms, and a useful reminder that "brainless cognition" claims need careful empirical support.
- [[hard-problem-consciousness]] — at what level, if any, does *Physarum* experience anything? Almost certainly not, but the "almost" is where the interesting argument lives.
