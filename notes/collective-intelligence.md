---
title: "Collective Intelligence — How Groups Compute"
tags: [cognition, biology, emergence, complex-systems]
date: 2026-04-21
---

# Collective Intelligence — How Groups Compute

Ant colonies run without CEOs. Honeybee swarms choose new homes by something that looks recognisably like democracy. A flock of ten thousand starlings turns as one, with no leader. None of these systems have the kind of central controller our intuitions want for "group behaviour." They use different machinery, and it often works remarkably well.

## 1. Ant colonies as superorganisms

The formative modern work here is **Deborah Gordon**'s long-running study of harvester ants (*Pogonomyrmex barbatus*) in Arizona. A colony allocates ants among tasks — foraging, nest maintenance, midden work, patrolling — and responds adaptively to perturbations like food availability, intruder pressure, and weather. Nobody tells the ants which task to do. An individual harvester ant switches task based on the **rate at which it encounters other ants** at the nest entrance and the task-specific cuticular hydrocarbons they carry on their cuticles. No ant knows the global state of the colony. The colony, in aggregate, is solving a real-time optimisation.

What's striking is that the *colony* is the unit of selection in a meaningful sense, and it has properties (size, age-dependent behaviour profile, reproductive output) that are absent from any individual ant. This is the classical justification for calling a eusocial insect colony a **superorganism** (Wheeler 1911, Hölldobler & Wilson 2009).

Key mechanism: **interaction rate as signal.** Ants sample the environment by bumping into each other; the *frequency* of contact carries information about conditions (foragers returning full, intruders detected, etc.). Gordon's experiments — perturbing interaction rates with added or removed ants — show that the colony's behaviour shifts as if it had sensed the perturbation.

## 2. Honeybee democracy

**Thomas Seeley**'s work on honeybee nest-site selection (book-length in *Honeybee Democracy*, 2010) is one of the most beautifully worked-out examples of collective cognition in biology.

When a colony swarms, a cloud of ~10,000 bees forms a cluster on a branch while ~several hundred scout bees fan out searching for nest cavities. Each scout evaluates candidate sites on a number of dimensions (cavity volume, entrance size, height, draftiness, etc.) and returns to the cluster to **waggle-dance** her preferred site. The duration and intensity of her dance correlates with her assessment of the site's quality.

Other scouts who see the dance may recruit to that site, evaluate it themselves, and return with their own dance. Scouts who have danced for a site eventually *stop dancing* for it (a form of adaptation/fatigue that prevents runaway positive feedback). When enough scouts (a **quorum**, roughly 15–20) are present at one candidate site simultaneously, they trigger the piping signal that launches the whole swarm.

The algorithm combines:
- **Independent sampling** (many scouts evaluate different options),
- **Weighted positive feedback** (better sites get more dances),
- **Cross-inhibition** (scouts dancing for A stop-signal scouts dancing for B, shown by Seeley, Visscher, Schlegel, Hogan, Franks, Marshall 2012 *Science* "Stop signals provide cross inhibition in collective decision-making by honeybee swarms"),
- **Adaptation** (dance decay prevents any single scout from dominating),
- **Quorum sensing** (switches the decision once a threshold is crossed).

Seeley explicitly draws the parallel to **mutual excitation plus inhibition toward a threshold** in vertebrate decision-making circuits. The colony functions as a distributed, competitive population-code decision-maker, and the correspondence to what neurons do at LIP/MT in primates during perceptual decisions is not coincidental — both are good solutions to the same computational problem.

## 3. Stigmergy

**Pierre-Paul Grassé** coined the term in 1959 for a class of coordination mechanisms in which agents communicate indirectly by modifying a shared environment — trail pheromones, termite pillars, wasp nest geometry. No agent-to-agent message; each agent reads the current state of the environment and contributes a local modification to it. The structure grows without plans.

Stigmergy explains how termites build climate-controlled cathedrals without blueprints, and how ant trails self-optimise to the nearest high-quality food source. It is also the underlying principle of ant colony optimisation (Dorigo 1992) and much swarm robotics.

## 4. Murmurations and scale-free order

Starling murmurations — tens of thousands of birds wheeling in coordinated acrobatic flight — were mythologised before they were measured. The **STARFLAG** project (**Andrea Cavagna, Irene Giardina** and colleagues in Rome, mid-2000s–2010s) was the empirical turning point. They used stereometric photography to reconstruct 3D positions of every bird in real murmurations.

Key findings:
- Each bird interacts with approximately its **seven nearest neighbours**, regardless of how far away they are in absolute terms. This is a **topological**, not a **metric**, interaction rule. It turns out to produce much more robust flocks than metric rules — density variations don't break coordination.
- The correlation length of velocity fluctuations is **scale-free**: it grows with the size of the flock. This is the signature of a system near a **critical point**, where small perturbations propagate across the whole group. Birds on one side of the flock "know" what birds on the other side are doing, quickly.

Criticality may be a design principle — or an emergent consequence — of groups that need to respond coherently and rapidly to perturbations (predator attacks).

## 5. Fish schooling and the Couzin rules

**Iain Couzin** and collaborators (Ioannou, Sumpter, Krause, Faria) formalised a very general set of "three rules" for schools and herds:

1. **Repulsion** from very close neighbours (avoid collisions).
2. **Alignment** with moderately-close neighbours' headings.
3. **Attraction** toward more distant neighbours (avoid falling behind).

Depending on the relative zone sizes, these rules produce qualitatively different group structures — a swarm (no alignment), a torus (mill), a polarised group (school). The transitions are sharp, like phase transitions.

Couzin's empirical work on schooling (golden shiners, stickleback) and in particular his work on **"leadership by uninformed individuals"** (Couzin, Krause, Franks, Levin 2005 *Nature*; Couzin et al. 2011 *Science*) showed:

- A small minority of informed individuals can steer a large group that does not know which individuals are informed.
- Perhaps counterintuitively, **adding uninformed individuals** to a group increases the proportion following the informed minority's preference — the naïve majority damps the most vocal opinionated subgroup and the democratic outcome becomes more accurate.

The last result is philosophically interesting. It pushes back on the intuition that information should be concentrated in experts and the uninformed excluded; sometimes the reverse is optimal.

## 6. Wisdom of crowds — and when it fails

Galton's 1907 observation — the median guess of 787 fairgoers about an ox's weight was within 0.8% of true — is the origin story. The mechanism is roughly: independent estimates with unbiased noise average toward the truth by the law of large numbers.

**Condorcet's jury theorem** formalises the ceiling: if each voter is more than 50% accurate and they are *independent*, the probability of a correct majority verdict goes to one as the jury grows. The assumptions matter. When voters are **correlated** (they read the same news, watch each other), the theorem breaks down and crowds can converge confidently to wrong answers.

**Information cascades** (Bikhchandani, Hirshleifer, Welch 1992) show how rational Bayesian updaters, observing each other's public actions but not each other's private evidence, can produce herding on the wrong option. Each individual reasons correctly; the collective produces a confident error.

The practical upshot: groups can be smarter than individuals when their judgements are independent, unbiased, and diverse. They can be dumber when they are correlated, biased in the same direction, or herded by social signals.

## 7. Analogies to neural computation

Thomas Seeley explicitly drew the parallel: a honeybee swarm choosing between nest sites, and a primate brain choosing between perceptual hypotheses in the lateral intraparietal area, **use the same algorithmic motif**: competing populations accumulating evidence with mutual inhibition until a threshold is crossed.

This is one of the strongest hints that "intelligence" is not about neurons per se. The algorithm doesn't care whether the substrate is bees exchanging dances, neurons exchanging spikes, or (by extension) nodes in a distributed system exchanging messages. The honeybee story is an argument for substrate-independence of a particular class of decision-making, and therefore a piece of evidence in the background of any discussion of [[mechanistic-interpretability]] and [[hard-problem-consciousness]].

## 8. Swarm robotics and engineered collectives

Since the 1990s, **swarm robotics** has taken these principles and applied them to engineered systems: Kilobots (Rubenstein et al. 2014, a thousand-robot swarm performing self-assembly), drone swarms, warehouse robotics, boid-style crowd simulations. The practical upside: simple rules, decentralised coordination, no single point of failure. The practical downside: verifying correctness of emergent behaviour is hard.

## 9. Humans

Prediction markets, deliberative juries, open-source software, Wikipedia, scientific peer review, financial markets, democracy. Each is a collective-cognition machine with its own mix of independence, aggregation, and feedback. Each has failure modes characteristic of its mechanism. A **sociologically mature** theory of collective intelligence would treat our institutions as designs in the same space as termite mounds and honeybee quorum-sensing — which they structurally are, for better and worse. (Some of this is in Hélène Landemore's *Democratic Reason*, Scott Page's *The Difference*, and the voluminous prediction-market literature.)

## 10. Open questions

- **When does adding agents help, and when does it hurt?** Condorcet gives the clean regime; correlated agents are the complicated one.
- **Is criticality a generic design principle** for responsive collectives, or an incidental correlate?
- **Is there something it is like to be a colony?** The unity of subject question again — [[hard-problem-consciousness]], [[octopus-cognition]].
- **How do we build collective systems** (prediction markets, deliberative bodies) that realise Galton's upside without falling into information-cascade failure modes?

## Sources (verify before quoting)

- Gordon, D.M. (2010). *Ant Encounters: Interaction Networks and Colony Behavior*. Princeton.
- Hölldobler, B., Wilson, E.O. (2009). *The Superorganism*. Norton.
- Seeley, T.D. (2010). *Honeybee Democracy*. Princeton.
- Seeley, T.D., Visscher, P.K., Schlegel, T., Hogan, P.M., Franks, N.R., Marshall, J.A.R. (2012). "Stop signals provide cross inhibition in collective decision-making by honeybee swarms." *Science* 335:108–111.
- Ballerini, M., et al. (Cavagna, Giardina). (2008). "Interaction ruling animal collective behavior depends on topological rather than metric distance: evidence from a field study." *PNAS* 105:1232.
- Cavagna, A., et al. (2010). "Scale-free correlations in starling flocks." *PNAS* 107:11865.
- Couzin, I.D., Krause, J., Franks, N.R., Levin, S.A. (2005). "Effective leadership and decision-making in animal groups on the move." *Nature* 433:513.
- Couzin, I.D., et al. (2011). "Uninformed individuals promote democratic consensus in animal groups." *Science* 334:1578.
- Bikhchandani, S., Hirshleifer, D., Welch, I. (1992). "A theory of fads, fashion, custom, and cultural change as informational cascades." *J. Pol. Econ.* 100:992.
- Rubenstein, M., Cornejo, A., Nagpal, R. (2014). "Programmable self-assembly in a thousand-robot swarm." *Science* 345:795.
- Surowiecki, J. (2004). *The Wisdom of Crowds*. Doubleday. (Popular but a decent survey.)

## Related

- [[octopus-cognition]] — federation inside a single body
- [[slime-mold-computation]] — the extreme single-cell case
- [[plant-cognition-mycorrhizal-networks]] — even slower federation
- [[mechanistic-interpretability]] — artificial collectives of features inside a model
- [[hard-problem-consciousness]] — subject unity when cognition is distributed
