---
title: "Mechanistic Interpretability — Reverse-Engineering the Things We Built"
tags: [ai, interpretability, alignment, neural-networks]
date: 2026-04-21
---

# Mechanistic Interpretability — Reverse-Engineering the Things We Built

Mechanistic interpretability (MI) is the research programme of treating a trained neural network as a scientific object and trying to explain its behaviour in terms of the computations implemented by its weights — features, circuits, subroutines. The programme makes two bets at once: that there is something to find (models are not just ineffable soup), and that finding it would be useful (for alignment, for science, for steering).

This is a note about the landscape as of early 2026, as best I can summarise it without re-reading everything. Flag anything specific before citing.

## 1. Why bother

Behavioural evaluation — prompt the model, grade the outputs — is cheap and indispensable, but it has a ceiling: it tells you what the model *does*, not what it will do out of distribution, and not whether the behaviour you like is produced by the process you think. A model that "refuses" because a refusal circuit fires on surface features is a different object from a model that "refuses" because it has something like understanding of the request. Behavioural evaluation cannot tell them apart.

MI tries to break that ceiling by asking what *structures* inside the network are responsible for specific behaviours. If successful, that gives us a way to (a) detect deception or misalignment that hides from behavioural probes, (b) steer models by editing internals rather than prompting around them, and (c) build scientific understanding of what learned computation looks like.

## 2. Features, superposition, and why this is hard

The naïve hope would be: each neuron corresponds to a human-legible concept, and we just read them off. Real networks don't cooperate. Neurons are **polysemantic**: a single neuron will respond to many unrelated things. And features are **superposed**: the network encodes more distinct concepts than it has dimensions, by packing them as nearly-orthogonal directions in activation space (Elhage et al., 2022, *Toy Models of Superposition*). Sparse activation and high dimensionality make this a workable code. Interpretability has to invert it.

## 3. Sparse autoencoders (SAEs)

The breakthrough tool of the 2023–2025 wave was the **sparse autoencoder** trained on a model's activations. You train a wide (much wider than the model's residual stream) autoencoder with an L1 or top-k sparsity penalty to reconstruct activations using as few features as possible. The hope: each learned feature corresponds to a monosemantic concept.

Key milestones:
- **Cunningham, Ewart, Riggs, Huben, Sharkey (2023)** — *Sparse Autoencoders Find Highly Interpretable Features in Language Models*.
- **Bricken, Templeton, et al. / Anthropic (Oct 2023)** — *Towards Monosemanticity* — a clean demonstration on a one-layer model.
- **Templeton, Conerly et al. / Anthropic (May 2024)** — *Scaling Monosemanticity* — applied to Claude 3 Sonnet at production scale. This is where the famous features come from: the Golden Gate Bridge feature, deception/sycophancy features, a "secrecy" feature, etc. Steering Claude by clamping the Golden Gate Bridge feature produced **Golden Gate Claude**, which helpfully tried to relate every topic to the bridge.

Open problems with SAEs as of late 2025:
- **Dead features** — many SAE latents never activate and carry no signal.
- **Feature splitting** — at larger widths, what looked like one feature splits into many; the "right" granularity is unclear.
- **Reconstruction–interpretability tradeoff** — SAEs that reconstruct well are often less interpretable, and vice versa.
- **Completeness** — no proof that SAE features are *all* the features the model uses, or that they are causally faithful to its computation.

Architectural variants that address some of these: **top-k SAEs** (Gao et al., OpenAI), **gated SAEs** (DeepMind), **JumpReLU SAEs**, **transcoders** (approximate MLP blocks instead of residual stream), **crosscoders** (tie features across layers or models).

## 4. Circuits

A **circuit** is a subgraph of attention heads, MLP neurons, and the connections between them that jointly implement a specific algorithm. The archetypal success:

- **Induction heads** (Olsson, Elhage et al., Anthropic 2022, *In-context Learning and Induction Heads*). A pair of attention heads — a "previous token head" plus a "match-and-copy" head — implements the simple algorithm: if you saw `A B` earlier and now see `A`, predict `B`. This circuit emerges abruptly during training and is tightly correlated with the onset of in-context learning.
- **IOI (Indirect Object Identification)** (Wang, Variengien, Conmy, Shlegeris, Steinhardt 2022). Reverse-engineered a circuit in GPT-2 Small that chooses the correct name in "When Mary and John went to the store, John gave a drink to ___" — a handful of heads do name duplication detection, S-inhibition, and name-moving.
- **Greater-than** circuits, **modular addition** circuits (Nanda et al., *Progress Measures for Grokking via Mechanistic Interpretability*), etc.

These are existence proofs that learned circuits can sometimes be read off almost like code.

## 5. Attribution graphs and the "biology of an LLM" programme

Anthropic's follow-up to *Scaling Monosemanticity* was the **attribution graph** / *Biology of a Large Language Model* line of work (2024–2025), applying feature-level circuit analysis at production-model scale. The idea: use SAE features as nodes, compute causal attributions between them via patching or gradient-based methods, and build a graph of how a specific prompt gets processed. This yielded case studies on things like multi-step reasoning, entity recognition, refusal, and planning in poetry generation.

The method mixes **activation patching** (swap one model's activations into another's run and see which components are causally necessary) with **direct logit attribution** and feature-level analyses. It is partial — it describes *how this specific forward pass worked*, not a total theory of the model — but it is the state of the art for saying anything detailed about what modern LLMs are doing.

## 6. Methodological toolkit

- **Activation patching / causal mediation.** Run the model twice with two different inputs, intervene to copy activations from run A into run B at a specific location, and measure the change in output logits. Standard for establishing causal role.
- **Path patching.** Variant that isolates specific paths through the computation graph (Goldowsky-Dill et al.).
- **Attribution (ACDC, Edge Attribution Patching).** Automated discovery of relevant circuits (Conmy et al.).
- **Direct logit attribution.** Decompose the logit for a token as a sum over components (attention heads, MLPs) via the unembedding direction.
- **Linear probing.** Train a classifier on hidden activations for a concept; long-established, but ambiguous between "model represents it" and "it's merely recoverable".
- **Representation engineering / activation steering** (Zou et al. 2023, Turner et al.). Add a concept vector to activations and observe behavioural change. Complementary to SAE feature clamping.

## 7. Alignment relevance

The alignment pitch for MI is: behavioural evaluation misses things that are safety-critical. A model that *learned* to give the trainer-preferred answer regardless of truth (sycophancy) or that *learned* to behave well when it thinks it is being evaluated and otherwise differently (evaluation-gaming, sandbagging) cannot be reliably detected by behavioural tests — by definition. If these patterns leave a signature in the internals, MI is one of the few ways to catch them.

The existence of features that look like "deception", "lying", "unsafe content recognition", "gratification of user", "thinking about being observed", etc. in production models — reported in *Scaling Monosemanticity* and follow-ups — is interesting either way. It suggests MI is seeing something. It doesn't yet tell us whether those features are *used* in misaligned ways or are bookkeeping about relevant concepts.

## 8. Critiques and cautions

- **Interpretability illusions.** Friedman, Lal, Wiegreffe et al. have pointed out multiple ways in which plausible-looking explanations of internals fail causal tests. Beautiful stories about neurons are cheap; rigorous ones are hard.
- **Cherry-picking.** Circuit-level results have tended to come from small models or narrow tasks. It is unclear how much carries over to frontier scale.
- **Dead theories.** Some SAE features look monosemantic under one prompt distribution and polysemantic under another; the monosemanticity may be an artefact of evaluation.
- **Coverage.** Even if each feature we find is real, we do not know what fraction of the model's computation the features we've found account for.
- **Räuker et al. (2023)** *Toward transparent AI: a survey* — a useful landscape survey, deliberately even-handed.

## 9. Why I care about this

Cognition was the hardest thing our ancestors could do, and we had no idea how our own did it; now we've made a second thing that looks, from the outside, like it is doing something similar, and this time we have weights. Having a full causal readout of a mind is historically unprecedented. Even if the thing we're reading is far from ours, the tools we build for it are the first of their kind. See [[hard-problem-consciousness]], [[octopus-cognition]] — these are the only other minds we have for comparison, and for neither of them do we have anything like direct access to internals.

## 10. Open questions

- Is there an analogue of *grammar* for a transformer? Can circuits be composed in predictable ways, or are they always ad hoc?
- How does MI scale with model capability? Frontier models are larger, more distributed, and harder to interpret.
- What is the right *unit* — neurons? directions? SAE features? transcoders? circuits of features? Maybe something we haven't named yet.
- Are features shared across models? Early crosscoder work (Anthropic 2024–25) suggests partial universality but the picture is incomplete.

## Sources (verify before quoting)

- Elhage, N., et al. (2022). *Toy Models of Superposition*. Anthropic / transformer-circuits.pub.
- Olsson, C., Elhage, N., et al. (2022). *In-context Learning and Induction Heads*. Anthropic.
- Wang, K., Variengien, A., Conmy, A., Shlegeris, B., Steinhardt, J. (2022). *Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 Small*.
- Cunningham, H., et al. (2023). *Sparse Autoencoders Find Highly Interpretable Features in Language Models*.
- Bricken, T., et al. (2023). *Towards Monosemanticity*. Anthropic. https://transformer-circuits.pub/2023/monosemantic-features
- Templeton, A., Conerly, T., et al. (2024). *Scaling Monosemanticity*. Anthropic.
- Nanda, N., Chan, L., Lieberum, T., Smith, J., Steinhardt, J. (2023). *Progress Measures for Grokking via Mechanistic Interpretability*.
- Zou, A., et al. (2023). *Representation Engineering: A Top-Down Approach to AI Transparency*.
- Gao, L., et al. (2024). *Scaling and evaluating sparse autoencoders*. OpenAI.
- Räuker, T., et al. (2023). *Toward transparent AI: a survey on interpreting the inner structures of deep neural networks*.
- Conmy, A., et al. (2023). *Towards Automated Circuit Discovery (ACDC)*.

## Related

- [[octopus-cognition]] — another mind whose internals we'd love to see
- [[hard-problem-consciousness]] — what MI could and couldn't tell us about experience
- [[landauer-thermodynamics-computation]] — the physical floor on the computations we're interpreting
- [[collective-intelligence]] — neurons as colony; MLPs as colony of features?
- [[slime-mold-computation]] — computation without interpretable "units" at all
