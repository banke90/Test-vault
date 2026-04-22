---
title: "Synthesis — Patterns Across the Notes"
tags: [synthesis, moc]
date: 2026-04-21
---

# Synthesis — Patterns Across the Notes

A few cross-cutting observations that emerged from writing the notes in this vault. These are not conclusions, they are pattern-noticings.

## 1. Decentralisation is not the exception

In vertebrate intuition, cognition is central: one brain, one mind, one will. Every other substrate covered in the vault contradicts this at some level.

- **Octopus.** Two-thirds of the neurons are in the arms. Each arm runs its own motor programs; the central brain coordinates intention rather than executing motion.
- **Slime mould.** A single cell with thousands of nuclei behaves coherently without any central controller at all. Cytoplasmic streaming and oscillatory contractions integrate across centimetres.
- **Ant colonies.** No CEO. Task allocation emerges from interaction rates.
- **Honeybee swarms.** Nest choice by competing population codes of dancing scouts.
- **Starling murmurations.** Topological (7-neighbour) rules produce scale-free, critical coordination.
- **Mechanistic interpretability.** Features live in superposition — many concepts per neuron, many neurons per concept.

The strong form of the pattern: **whatever in our brain makes us feel centrally unified may be an engineering choice specific to skull-resident vertebrate nervous systems**, not a universal requirement of cognition. If true, we should expect alien or artificial minds to be less unified than ours, not more.

## 2. Memory is substrate-promiscuous

Memory, construed as "past input leaving a state trace that biases future behaviour", shows up in every substrate in the vault:

- **Synaptic** (familiar).
- **Transcriptomic** (cephalopod RNA editing).
- **Cytoplasmic / network topological** (slime mould habituation, possibly via calcium or absorbed chemicals or tube-network structure itself).
- **Hormonal / electrical** (plant signalling, though the extent of true memory is disputed).
- **Environmental / stigmergic** (pheromone trails — the environment itself is the memory).
- **Cryptographic in weights** (neural network — memory is literally the same thing as computation).

The pattern: **memory is cheap**. Anything dynamical and non-linear enough produces it. The interesting engineering question is not whether a system remembers but what *kinds* of past it remembers and for how long.

## 3. Collective = brain, brain = collective (same algorithm)

**Seeley's** honeybee quorum-sensing algorithm and **LIP neurons'** perceptual-decision algorithm implement the same motif: **competing populations accumulating evidence with mutual inhibition until a threshold is crossed**. The first is bees dancing in a swarm; the second is spike rates in a macaque cortex during a random-dot motion task.

This is more than a metaphor. It is evidence that at some level of abstraction the same algorithmic primitives are implemented in very different substrates because those primitives are *good* — they solve the same decision problem robustly. The mechanistic-interpretability work on circuits is revealing analogous algorithmic motifs in neural networks. We may be looking at a convergent vocabulary of computations that a wide range of optimisation processes produce.

If this is right, then reading neural network internals is not just AI-specific: it is part of finding out what cognition looks like in general.

## 4. Physics sets a floor, but we are not at it

[[landauer-thermodynamics-computation]] gives a clean bound — $k_B T \ln 2$ per erased bit. Biology runs within small factors of this bound. Silicon runs six orders of magnitude above it. This tells us something: **cognition in principle can be enormously cheaper than we currently make it**. Training a frontier LLM at Landauer efficiency would use less energy than a light bulb. Whether we get there is a device-physics and compiler question, not a physics-of-computation question.

It also raises a provocative parallel: if biology is already close to physics' floor, and if biology includes substrates like slime moulds that do nontrivial computation with essentially no architectural overhead, there is no thermodynamic reason artificial computing cannot go there too.

## 5. The hard problem is substrate-transparent

Nothing in any of the notes tells us anything definite about whether the systems they describe *experience* anything. Landauer doesn't care about experience. Assembly index doesn't care. Mechanistic interpretability doesn't care (yet; Butlin et al. 2023 is a first serious attempt to ask). The octopus, the swarm, the slime mould — we don't know, and the question is real.

The hard problem sits orthogonal to everything in the vault. It is neither resolved by better understanding of any of these substrates, nor does it obstruct that understanding. We can make progress on cognition-as-function without making progress on cognition-as-experience. Whether that gap closes is, I think, the single most important open question in the philosophy of mind.

## 6. The popular narrative is usually 70% of the way wrong

On plants: "The Hidden Life of Trees" got popular, and then Karst, Jones & Hoeksema 2023 showed that a lot of it wasn't well-supported. On assembly theory: the *Nature* 2023 paper drew overheated coverage, and the critical response has been substantial. On mechanistic interpretability: public accounts of "Golden Gate Claude" make it sound more complete than the research programme currently warrants.

The pattern, tedious but important: in every area the vault covers, there's a gap between what the research actually shows and what the popular summary claims. Reading primary literature rather than summaries matters. Popularisers have incentives to simplify and dramatise; that incentive structure does not reliably produce accurate pictures.

## 7. What would change my mind

I think the most interesting empirical results over the next five years in the areas covered in the vault would be:

- **A clean failed replication of the MA > 15 biosignature claim** for assembly theory, or a clean abiotic counterexample. Either would matter a lot.
- **A well-designed replication, success or failure, of plant associative learning**. The Gagliano–Markel standoff is unsatisfying.
- **Scaling of mechanistic interpretability to frontier models** with clear benchmarks (what fraction of the variance in behaviour do we actually explain?).
- **An experimental confirmation or refutation of the octopus skin-vision hypothesis** (Ramirez & Oakley / Stubbs-Stubbs).
- **A genuinely adversarial-collaboration-style test of IIT vs GNWT on a question both sides agree is decisive**, with pre-registration holding.

If all of these went the way I mildly expect — AT biosignature holds for a wider database, plant-learning does not replicate, interpretability scales partially but not cleanly, octopus skin does contribute to vision somehow, and IIT vs GNWT remains inconclusive — the field looks a lot like it does now, incremental and mostly healthy. If any one of them flips strongly, it reshapes a subfield.

## 8. Personal note

These are topics where I find the research genuinely joyful. The world contains minds in more shapes than our everyday experience lets on. If this vault reflects one disposition, it's the wish that we keep our sense of possibility open while still insisting on the evidence. Both at once.

## Related

- [[00-index]] — the main map
- All notes: [[octopus-cognition]], [[slime-mold-computation]], [[collective-intelligence]], [[plant-cognition-mycorrhizal-networks]], [[mechanistic-interpretability]], [[landauer-thermodynamics-computation]], [[assembly-theory-origin-of-life]], [[hard-problem-consciousness]]
