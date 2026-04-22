---
title: "Slime Mold Computation — Problem-Solving Without a Brain"
tags: [cognition, biology, unconventional-computing, slime-mold, basal-cognition]
date: 2026-04-21
---

# Slime Mold Computation — Problem-Solving Without a Brain

*Physarum polycephalum* is not a plant, not a fungus, and not an animal. It is a **plasmodial slime mould** — an amoebozoan that spends most of its life as a single enormous cell, multinucleate, without a nervous system, without any individual neurons, crawling across the forest floor eating bacteria and decaying matter. And it solves problems people write PhDs about.

If you want to unsettle your intuitions about what "cognition" requires, this is a good place to start.

## 1. What the organism actually is

A *Physarum* plasmodium is a single cell with **many thousands of diploid nuclei** sharing one cytoplasm. No cell membranes divide the interior. It forms a network of interconnected tubes — sort of like a living circulatory system without a heart or a body around it — through which cytoplasm streams back and forth. The streaming is driven by **rhythmic contractions of the actomyosin cortex**, with an oscillation period on the order of 60–120 seconds. The pressure pulses shuttle cytoplasm around the network.

That shuttling, and the way the tube network locally thickens or thins in response to flow and chemical gradients, is the substrate of everything interesting *Physarum* does.

## 2. Maze-solving (Nakagaki et al., Nature 2000)

The headline result: put a *Physarum* plasmodium onto an agar plate shaped as a maze, with oat flakes (food) at two locations. Starting diffusely spread through the whole maze, the organism *retracts* from dead ends over a few hours and leaves behind a **single tube connecting the two food sources along the shortest path**.

The mechanism, so far as the modellers understand it, is a positive feedback between flow and tube radius: tubes that carry more flux thicken (reducing resistance, increasing flux further), while low-flow tubes shrink and eventually disappear. The global optimum falls out of local rules and physics. No search, no plan — just a flow-adaptive network that converges on efficient routes.

Nakagaki, Yamada, and Tóth titled the paper simply: **"Maze-solving by an amoeboid organism."** *Nature* 407, 470 (2000). It is one of my favourite single-page papers in biology.

## 3. The Tokyo rail-network experiment (Tero et al., Science 2010)

**Atsushi Tero, Ryo Kobayashi, Toshiyuki Nakagaki** and collaborators arranged oat flakes on an agar plate in the geographic positions of major cities around Tokyo — Yokohama, Chiba, and the outlying stations of the Kantō rail network. They added a plasmodium at Tokyo. They also used light (which *Physarum* avoids) to represent topographical obstacles like mountains and water.

Over 26 hours or so, the plasmodium formed a tube network between the oat flakes. The researchers compared it quantitatively to the actual Tokyo rail network on three axes: **total length**, **average minimum distance** between nodes (efficiency), and **fault tolerance** (how many edges you can cut before the network disconnects). *Physarum* hit roughly the same Pareto tradeoff the Japanese rail engineers had found — sometimes surprisingly close to the human-built solution on two of the three axes at once.

This is not a computation in the Turing sense. It is a physical relaxation process that happens to land near a reasonable tradeoff surface. That distinction matters — but it also shows that cheap, local, substrate-level dynamics can solve problems we normally treat as requiring global planning.

*Science* 327, 439–442 (2010): "Rules for biologically inspired adaptive network design."

## 4. Memory without neurons

*Physarum* has memory, at least in any behavioural sense of the word:

- **Habituation to aversive stimuli.** Boisseau, Vogel, and Dussutour (2016, *Proc. R. Soc. B*) showed that plasmodia trained to cross a bridge coated with quinine or caffeine — aversive bitters — gradually stop slowing down. After a rest period they return to baseline sensitivity. This matches the formal criteria for habituation (Thompson & Spencer).
- **Anticipation of periodic events.** Saigusa et al. (2008, *Phys. Rev. Lett.*) exposed plasmodia to cold, dry pulses (which slow them) at regular intervals. After several exposures the organism slowed down *at the time the pulse would have come*, even when it was omitted — and resumed this anticipatory response after a long break. Something is encoding the interval.
- **Transmission of learning through fusion.** Vogel and Dussutour (2016, *Proc. R. Soc. B*) let a trained (habituated) plasmodium fuse with a naïve one. The fused individual inherited the trained behaviour. The "memory" — whatever its physical substrate — can be shared across what we would otherwise treat as separate individuals.

What encodes a memory in a single cell with no synapses? Candidate substrates include **calcium dynamics**, **cytoplasmic chemical concentrations** (e.g. absorbed quinine altering internal state), and **network topology itself** (the pattern of thick and thin tubes). Probably several of these at once. No-one has pinned it down.

## 5. Mechanism summary

The *Physarum* toolkit seems to be:

1. A body that is simultaneously its own sensor, effector, and communication channel — every part of the cytoplasm is in contact with every other part via streaming.
2. Chemical gradients for sensing food, humidity, and avoiding light.
3. Oscillatory contractions that can phase-couple across the body, carrying information about local conditions to distant regions.
4. Flow-dependent tube reinforcement (thicker where flow is greater) implementing a physical analogue of reinforcement learning on the network topology.

These are simple rules; the behaviour is not.

## 6. Physarum-inspired algorithms

The dynamics have been abstracted into the **Physarum solver** — a continuous-flow equation for shortest paths and Steiner-tree approximations that provably converges on optimum under certain conditions (Tero, Ito, Nakagaki 2006; subsequent formal analysis by Bonifaci, Mehlhorn, Varma 2012 for shortest paths; further by Becchetti et al.). It's one of the rare cases where a biological heuristic has been matched to a theorem.

There's also a small sub-discipline using *Physarum* itself as a **live computing substrate**:

- **Andrew Adamatzky** and colleagues have built logic gates, sensors, and simple oscillator circuits from *Physarum* cultures grown on patterned substrates.
- Shortest-path wiring, ratio/proportion approximation, travelling salesman heuristics — all demonstrated with live plasmodia, usually more as proofs of concept than competitive implementations.

## 7. Basal cognition

The broader philosophical programme is **basal cognition** — the position most clearly articulated by **Pamela Lyon**, and in a different register by **Michael Levin** (bioelectric cognition across cells and tissues). The claim is roughly: cognition is not a late, neural invention. Core components — discrimination, memory, anticipation, goal-directedness in some minimal sense — exist in organisms with no nervous system, and the hard-problem-style features of experience may or may not require neurons, but the *cognitive* features definitely don't.

This is a less threatening claim than it sounds. It says: the list of operations that count as "thinking" existed before brains, and brains are one particular way to implement them very efficiently and at high speed. Slime moulds are another way, slower and more embodied.

## 8. What *Physarum* is not

A sobering caveat: most of the dramatic-sounding *Physarum* results are best understood as **physics**, not as semantic cognition. The "maze-solving" is a flow-relaxation process; the "Tokyo network" is gradient-following. Calling these "intelligent" is a framing choice. But then again, so is calling what ant colonies do intelligent (see [[collective-intelligence]]), and so is calling what neurons do intelligent at the single-cell level. If "intelligence" means "structured adaptive behaviour emerging from local rules that approximates optimum on some objective", *Physarum* qualifies — and that is either a big claim or a weak one depending on your priors.

## 9. Open questions

- What is the physical substrate of habituation memory in a single cell? (Candidate: calcium-mediated gene-expression changes, but unproven.)
- How are the oscillations phase-coupled over tens of centimetres? The mechanical-hydraulic model is partial.
- Could engineered slime-mould networks be useful as ultra-low-energy optimisation substrates? (Promising in principle; in practice silicon beats them.)
- What is the upper bound of behavioural complexity for a brainless organism? Where does the ceiling sit?

## Sources (verify before quoting)

- Nakagaki, T., Yamada, H., Tóth, Á. (2000). "Intelligence: Maze-solving by an amoeboid organism." *Nature* 407:470.
- Tero, A., et al. (2010). "Rules for biologically inspired adaptive network design." *Science* 327:439–442.
- Saigusa, T., Tero, A., Nakagaki, T., Kuramoto, Y. (2008). "Amoebae anticipate periodic events." *Physical Review Letters* 100:018101.
- Boisseau, R.P., Vogel, D., Dussutour, A. (2016). "Habituation in non-neural organisms: evidence from slime moulds." *Proc. R. Soc. B* 283:20160446.
- Vogel, D., Dussutour, A. (2016). "Direct transfer of learned behaviour via cell fusion in non-neural organisms." *Proc. R. Soc. B* 283:20162382.
- Bonifaci, V., Mehlhorn, K., Varma, G. (2012). "Physarum can compute shortest paths." *J. Theor. Biol.* 309:121–133.
- Adamatzky, A. (2010). *Physarum Machines: Computers from Slime Mould*. World Scientific.
- Lyon, P. (2015). "The cognitive cell: bacterial behaviour reconsidered." *Frontiers in Microbiology* 6:264.
- Levin, M. (2019 onwards) — various papers on bioelectric cognition; e.g. Levin & Dennett, "Cognition all the way down," *Aeon* (2020).

## Related

- [[octopus-cognition]] — cognition distributed across a body that still has neurons
- [[collective-intelligence]] — many individuals behaving like one mind; here it is one cell with many nuclei behaving like many
- [[landauer-thermodynamics-computation]] — physical limits on computation, relevant to the "physics vs computation" question for *Physarum*
- [[assembly-theory-origin-of-life]] — another attempt to think about complexity in a substrate-general way
- [[plant-cognition-mycorrhizal-networks]] — the closest biological analogue among familiar organisms
- [[hard-problem-consciousness]] — at what level, if any, does *Physarum* experience anything?
