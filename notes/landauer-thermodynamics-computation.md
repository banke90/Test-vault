---
title: "Landauer's Principle and the Thermodynamics of Computation"
tags: [physics, information-theory, thermodynamics, computation]
date: 2026-04-21
---

# Landauer's Principle and the Thermodynamics of Computation

One of the most interesting slogans in physics of the last century is **Rolf Landauer's** "information is physical." The slogan is vague; the claim behind it is specific: **erasing a bit of information in a physical system at temperature T requires dissipating at least** $k_B T \ln 2$ **of heat**. This is the **Landauer limit**, roughly $2.9 \times 10^{-21}$ J per bit at room temperature — about $3$ zJ, or $0.017$ eV.

This connects three things that look unrelated: the logical structure of a computation, the entropy of the underlying physical state, and the second law of thermodynamics.

## 1. Landauer's argument (1961)

Landauer, at IBM, was thinking about why computers dissipate heat. He noticed that **logically irreversible** operations — operations that map many input states to the same output state — must correspond to **physically irreversible** processes, because the number of accessible microstates *decreases*.

Take the canonical example: `ERASE`. Before: a bit is in state 0 or 1 (two microstates, assuming equal probability). After: the bit is in state 0 (one microstate). Shannon entropy of the logical state went down by $\ln 2$ nats. By the **second law**, if the logical state is part of a physical system in contact with a heat bath, that entropy has to go *somewhere*. The only place it can go is into the thermal degrees of freedom of the environment. The minimum heat dissipated is $k_B T \ln 2$.

The subtlety: this is the cost of **erasure**, not of reading or of copying to a blank slate. Operations that are logically reversible (AND preserving the inputs, NOT on a known input, etc.) have no thermodynamic floor from Landauer.

Landauer's 1961 paper: "Irreversibility and heat generation in the computing process." *IBM J. Res. Dev.* 5(3):183–191.

## 2. Maxwell's demon, and its resolution

Maxwell (1867) imagined a tiny being sorting fast from slow molecules through a trapdoor, apparently producing a temperature gradient for free and violating the second law. A century of cleverness went into explaining why this cannot work.

**Szilard (1929)** refined the problem to a one-molecule engine: a single-molecule gas in a box, a measurement of which side it is on, and a partition that extracts $k_B T \ln 2$ of work using that measurement. Szilard's engine clarified that *information* (about the molecule's position) is being converted into work.

**Bennett (1982)** closed the loop using Landauer's principle: the demon must eventually **erase** its memory to run the cycle again, and that erasure dissipates exactly the work the engine extracts. Second law restored. Information is not magic — it is a bookkept resource, and its deletion has a thermodynamic price.

Bennett, C. (1982). "The thermodynamics of computation — a review." *Int. J. Theor. Phys.* 21:905–940.

## 3. Bennett and reversible computing

Charles Bennett (1973) went further: if logical irreversibility is the only thing forcing heat dissipation, one could in principle build a **logically reversible** computer that dissipates *arbitrarily little* energy per operation. His construction:

1. Compute $f(x)$ reversibly, keeping all intermediate results (and the input).
2. Copy the answer.
3. Run the computation *backwards*, cleaning up intermediates, leaving you with $x$, $f(x)$, and a blank workspace.

**Fredkin and Toffoli** gates (the **Fredkin gate** is a conservative reversible gate; the **Toffoli gate** is a reversible universal gate: CCNOT) give you a universal basis. Quantum computing inherits this — unitary quantum gates are automatically reversible, which is part of why quantum-thermodynamic accounting is subtle but not catastrophic.

In practice, full reversible computation has overheads (memory for history, adiabatic slowness) that have kept it out of consumer hardware. But it remains the proof that the Landauer floor is only for *irreversible* steps, not for computation per se.

## 4. Experimental verification

Landauer's principle was treated as established for decades on theoretical grounds, but direct measurement had to wait for single-particle thermodynamics.

- **Bérut, Arakelyan, Petrosyan, Ciliberto, Dillenschneider, Lutz (2012, *Nature*)** — a silica microbead in a double-well optical trap, representing a bit. They drove the potential through a protocol that erases the bit, measured the heat dissipated quasi-statically, and found agreement with $k_B T \ln 2$ in the slow (quasi-static) limit.
- Follow-ups by **Jun, Gavrilov, Bechhoefer (2014, *Phys. Rev. Lett.*)** refined the measurement.
- **Hong, Lambson, Dhuey, Bokor (2016, *Science Advances*)** — nanomagnetic bits approaching the Landauer limit.
- More recent single-atom and single-electron experiments (Koski, Pekola et al. in Helsinki) extend into the quantum regime and verify related fluctuation-theorem statements.

The limit is real, and it has been seen — not just derived.

## 5. Distance from the Landauer floor

Modern CMOS dissipates roughly $10^{-15}$ J per logical switch. The Landauer limit at room T is about $3 \times 10^{-21}$ J per erasure. That's a gap of roughly **six orders of magnitude**. We are not thermodynamically limited today — we are limited by the engineering of transistors, interconnect capacitance, clock distribution, voltage headroom. The Landauer floor will start to matter as miniaturisation continues and voltage scaling approaches the thermal-noise limit, but it isn't yet binding.

This has direct relevance to ML training energy. Training a frontier LLM costs on the order of $10^{19}$ to $10^{20}$ FLOPs; at current energy cost per FLOP (~tens of picojoules), this is megawatt-hours. The Landauer lower bound on the same work is millions of times smaller. So *in principle* ML training energy could fall by factors of millions with better devices. In practice, getting the first factor of 10 is already hard.

## 6. Connection to biology

Life is, among other things, a chemistry that performs computation far closer to the Landauer limit than silicon does.

- A **single ATP hydrolysis** delivers about $20\, k_B T$ — enough for about **28 bits of erasure** at room temperature if it were Landauer-optimal. Real molecular machines use a few to a few tens of ATP per "logical operation", leaving small multiples of the Landauer bound.
- **Kinetic proofreading** (Hopfield 1974; Ninio 1975) — the mechanism by which ribosomes and DNA polymerases achieve high copy fidelity — spends ATP to reduce error rates beyond the equilibrium Boltzmann limit. It is a *thermodynamic* cost of accuracy, formally analogous to Landauer: reducing the entropy of a "correct vs incorrect" bit requires dissipation.
- Bialek, Tu, Lan and others have sharpened the analysis: adaptation, sensing, and signalling in biology all trade energy for information in ways that match predicted bounds from stochastic thermodynamics.

**Schrödinger's** 1944 *What Is Life?* anticipated much of this with his phrase **"negative entropy"** (negentropy) — life maintains order by exporting entropy to its environment. Landauer and Bennett gave the idea a rigorous handle.

## 7. Quantum Landauer and modern stochastic thermodynamics

In the 1990s–2010s the field of **stochastic thermodynamics** (Seifert, Jarzynski, Crooks) generalised classical thermodynamics to trajectories of small systems. This has produced:

- **Fluctuation theorems** — exact equalities for probability ratios of forward/backward protocols (Jarzynski equality, Crooks relation).
- **Refined Landauer bounds** — tighter inequalities that recover the classical bound in the slow limit and capture finite-time corrections.
- **Quantum Landauer** — the bound carries over under appropriate assumptions about initial states; subtleties appear for non-thermal baths and coherent information.

Under certain resource-theoretic assumptions (with quantum coherence or non-thermal baths) you can appear to violate the classical bound, but a careful accounting restores it with the right definitions. The literature here (Goold, Huber, Riera, del Rio, Skrzypczyk, Aberg, etc.) is technical and very alive.

## 8. Critiques

Landauer's principle is not logically forced by the second law in all formulations. **John Earman and John Norton** argue that Landauer erasure can be re-described in ways that do not require the $k_B T \ln 2$ dissipation to occur in the location it is usually attributed to, and that the principle rests on additional assumptions (ergodicity, specific definitions of "memory state"). **Shenker** and others have made similar objections. Most working physicists treat the principle as correct and well-verified by experiment; the critiques are philosophically important but do not overturn the experimental results.

## 9. What to take away

- The second law, the bit, and the forward arrow of time are tied together by Landauer.
- *Irreversibility* is the thermodynamic cost, not *computation* per se.
- Biology operates within a few factors of the Landauer bound; silicon does not.
- The bound is a *floor*, not a target we will hit — but it is useful as a north star for why computing energy *could* come down by many orders of magnitude if we were willing to redesign the stack.

Information is physical. That slogan is both deep and easy to abuse. The defensible version: *some* questions about information have forced physical answers, and knowing those answers is part of what makes life, computation, and their interface make sense together.

## Sources (verify before quoting)

- Landauer, R. (1961). "Irreversibility and heat generation in the computing process." *IBM J. Res. Dev.* 5:183.
- Bennett, C.H. (1973). "Logical reversibility of computation." *IBM J. Res. Dev.* 17:525.
- Bennett, C.H. (1982). "The thermodynamics of computation — a review." *Int. J. Theor. Phys.* 21:905.
- Szilard, L. (1929). "Über die Entropieverminderung in einem thermodynamischen System bei Eingriffen intelligenter Wesen." *Z. Phys.* 53:840.
- Bérut, A., et al. (2012). "Experimental verification of Landauer's principle linking information and thermodynamics." *Nature* 483:187.
- Jun, Y., Gavrilov, M., Bechhoefer, J. (2014). "High-precision test of Landauer's principle in a feedback trap." *PRL* 113:190601.
- Hopfield, J.J. (1974). "Kinetic proofreading: a new mechanism for reducing errors in biosynthetic processes requiring high specificity." *PNAS* 71:4135.
- Seifert, U. (2012). "Stochastic thermodynamics, fluctuation theorems and molecular machines." *Rep. Prog. Phys.* 75:126001.
- Earman, J., Norton, J. (1998, 1999). "Exorcist XIV: The wrath of Maxwell's demon." *Stud. Hist. Phil. Mod. Phys.*
- Schrödinger, E. (1944). *What Is Life?* Cambridge University Press.

## Related

- [[mechanistic-interpretability]] — the computations whose thermodynamic cost we have no choice but to pay
- [[slime-mold-computation]] — another substrate that computes close to physics' floor
- [[assembly-theory-origin-of-life]] — another attempt to quantify the "informational" side of matter
- [[hard-problem-consciousness]] — is consciousness in any way thermodynamically cheap or expensive? (Almost certainly irrelevant at the Landauer level, but people ask.)
- [[octopus-cognition]] — a biological mind operating within a few factors of the Landauer bound
