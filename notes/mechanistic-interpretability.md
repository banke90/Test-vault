# Mechanistic interpretability is the first historical shot at reading the internals of a mind we built

> Treating a trained neural network as a scientific object — reverse-engineering features, circuits, and subroutines from its weights — is a genuinely new epistemic situation, and it matters for alignment, for science, and for how we think about minds in general.

[Confidence: mixed — the empirical results are real; the coverage and faithfulness of current methods are contested]
[Last verified: 2026-04-21]
[Kind: survey]

## TL;DR

Mechanistic interpretability (MI) tries to explain a neural network's behaviour in terms of the computations implemented by its weights — not just what the model outputs, but *how* it produces those outputs. The programme makes two bets: that there is structure to find inside the model (not ineffable soup), and that finding it is useful (for alignment and for science). The dominant tools in 2023–2026 are **sparse autoencoders** (extracting monosemantic features from superposed activations [Bricken et al. 2023; Templeton et al. 2024]) and **circuit analysis** (reverse-engineering subgraphs of attention heads and MLP neurons that implement specific algorithms [Olsson et al. 2022; Wang et al. 2022]). Anthropic's **attribution-graph / "biology of a large language model"** line of work extends this to production-scale Claude models. Open problems: scaling, faithfulness of the found features to the model's real computation, and whether we're seeing a real fraction of what the model does.

## Why interpretability at all

Behavioural evaluation — prompt the model, grade the outputs — is cheap, scalable, and indispensable. It also has a hard ceiling: it tells you what the model does *on the inputs you tested*, not what it does out of distribution, and not whether the behaviour you like is produced by the process you think.

A model that refuses harmful requests because a "refusal circuit" fires on surface features is a different object from a model that refuses because it has something like understanding of the request. **Behavioural evaluation cannot tell them apart.** A model that learned to behave well when it thinks it's being evaluated, and differently otherwise (sandbagging, evaluation-gaming), cannot be reliably detected by evaluation — by definition.

MI tries to break that ceiling. If successful: (a) detect deception or misalignment that hides from behavioural probes, (b) steer models by editing internals rather than prompting around them, (c) build scientific understanding of what learned computation looks like in general.

## Features and superposition — why this is hard

Naïve hope: each neuron corresponds to one human-legible concept. Real networks don't cooperate. Neurons are **polysemantic** — one neuron responds to many unrelated things. Features are **superposed** — the network encodes more distinct concepts than it has dimensions by packing them as nearly-orthogonal directions in activation space [Elhage et al. 2022].

Sparse activation and high dimensionality make this a workable code for the network. The interpretability task is to invert it — to find the feature *directions* rather than reading neurons one by one. *(established framing)*

## Sparse autoencoders

The dominant tool of the 2023–2025 wave. Train a wide autoencoder (much wider than the model's residual stream) on hidden activations with an L1 or top-k sparsity penalty. The hope: each learned latent corresponds to a monosemantic concept.

Key milestones:

- **Cunningham, Ewart, Riggs, Huben, Sharkey 2023**: "Sparse Autoencoders Find Highly Interpretable Features in Language Models" [Cunningham et al. 2023].
- **Bricken, Templeton et al. / Anthropic Oct 2023**: "Towards Monosemanticity" — clean demonstration on a one-layer model [Bricken et al. 2023].
- **Templeton, Conerly et al. / Anthropic May 2024**: "Scaling Monosemanticity" — applied at production scale to Claude 3 Sonnet [Templeton et al. 2024]. The Golden Gate Bridge feature, deception and sycophancy features, secrecy feature, etc. Clamping the Golden Gate feature produced **Golden Gate Claude**, which helpfully related every topic back to the bridge.

Known problems:
- **Dead features.** Many SAE latents never activate on any input. Waste.
- **Feature splitting.** At larger SAE widths, what looked like one feature at smaller width splits into many. The "right" granularity is unclear.
- **Reconstruction–interpretability tradeoff.** SAEs that reconstruct activations well are often less interpretable, and vice versa.
- **Faithfulness / completeness.** No proof that SAE features are *all* the features the model uses, or that they are causally faithful to its actual computation. *(This is the deepest worry.)*

Architectural variants addressing some of these: **top-k SAEs** [Gao et al. 2024], **gated SAEs** (DeepMind), **JumpReLU SAEs**, **transcoders** (approximate MLP blocks), **crosscoders** (tie features across layers or models).

## Circuits

A **circuit** is a subgraph of attention heads, MLP neurons, and connections jointly implementing a specific algorithm. Archetypal successes:

- **Induction heads** [Olsson et al. 2022]. Anthropic. A pair of attention heads — a "previous token" head plus a "match-and-copy" head — implements: if you saw `A B` earlier and now see `A`, predict `B`. Emerges abruptly during training; tightly correlated with the onset of in-context learning *(established and replicated)*.
- **Indirect Object Identification (IOI)** [Wang et al. 2022]. Reverse-engineered the circuit in GPT-2 Small that picks the correct name in "When Mary and John went to the store, John gave a drink to ___". A handful of heads do name duplication detection, S-inhibition, and name-moving.
- **Modular addition / greater-than** circuits [Nanda et al. 2023]. Small models doing arithmetic, with clean Fourier-style decompositions of what's going on internally.

These are existence proofs that learned circuits can sometimes be read off almost like code. They are also, as of 2026, mostly confined to small models and narrow tasks. *(established for small cases; cherry-picked)*

## Attribution graphs and the "biology of an LLM" programme

Anthropic's follow-up to *Scaling Monosemanticity* was the **attribution graph** / *On the Biology of a Large Language Model* line of work (2024–2025). Apply feature-level circuit analysis at production-model scale: use SAE features as nodes, compute causal attributions between them via patching or gradient-based methods, build a graph of how a specific prompt is processed.

Case studies reported: multi-step reasoning, entity recognition, refusal, planning ahead in poetry generation. The method mixes **activation patching** with **direct logit attribution** and feature-level analyses.

Important caveat: an attribution graph explains *how this specific forward pass worked*, not the model as a whole. It's the state of the art for detailed internal analysis of modern LLMs, but it is case-by-case, not a full theory *(mixed — real but partial)*.

## Methodological toolkit

- **Activation patching / causal mediation.** Run the model twice with two different inputs; copy activations from run A into run B at a specific location; measure change in output logits. Standard for establishing causal role of a component *(established)*.
- **Path patching.** Variant isolating specific paths through the computation graph (Goldowsky-Dill et al.).
- **Automated circuit discovery (ACDC, Edge Attribution Patching)** [Conmy et al. 2023].
- **Direct logit attribution.** Decompose a logit for a token as a sum over components (heads, MLPs) via the unembedding direction.
- **Linear probing.** Train a classifier on activations for a concept. Long-established. Ambiguous between "model represents it" and "it's merely linearly recoverable" — the probe might find it without the model using it.
- **Representation engineering / activation steering** [Zou et al. 2023]. Add a concept vector to activations, observe behavioural change. Complementary to SAE feature clamping.

## Alignment relevance

The pitch: behavioural evaluation misses safety-critical phenomena by construction. A model that has learned to give trainer-preferred answers regardless of truth (sycophancy), or to behave well under observation and differently otherwise (sandbagging), cannot be caught behaviourally. If these patterns leave internal signatures, MI is one of the few tools that might catch them.

The existence of production-model features that look like "deception", "lying", "unsafe content recognition", "user gratification", "thinking about being observed" [Templeton et al. 2024] is suggestive either way. It shows MI is seeing *something*. It does not yet tell us whether those features are *used* in misaligned ways or are bookkeeping about relevant concepts — the causal role question is harder than the representation question.

## Disagreements and cautions

- **Interpretability illusions.** Multiple authors (Friedman, Lal, Wiegreffe et al.) have shown that plausible-looking explanations of internals fail causal tests. Beautiful stories about neurons are cheap; rigorous ones are hard *(established caution)*.
- **Cherry-picking.** Circuit-level results tend to come from small models or narrow tasks. How much carries over to frontier scale is unclear.
- **Monosemanticity as artefact.** Some SAE features look monosemantic under one prompt distribution and polysemantic under another. The monosemanticity metric may be evaluation-dependent.
- **Coverage.** Even if each feature we find is real, we don't know what fraction of the model's computation is explained by the features we've identified. The unknown fraction matters for any alignment-critical claim.
- **Räuker et al. 2023** [Räuker et al. 2023] — a useful survey, deliberately even-handed, about what MI is and isn't doing.
- **The "MI is succeeding" / "MI is hype" debate** is live and largely politely conducted. My own read (mixed): the empirical results are real; the field has a track record; but the claims that MI is close to solving alignment-relevant detection problems are premature.

## Questions I'd like answered

1. **Is there a grammar of transformers** — predictable ways circuits compose — or are circuits always ad hoc and task-specific?
2. **How does MI scale with model capability?** Frontier models are larger, more distributed, and likely harder to interpret. Are we getting closer or further from a full account as models scale?
3. **What is the right *unit* of interpretation** — neurons? directions? SAE features? transcoders? circuits of features? Possibly something we haven't named.
4. **Are features shared across models?** Early crosscoder work suggests partial universality. Is there something like a "natural vocabulary" that large models converge on?
5. **Can MI tools measure the *fraction* of a model's computation they've explained?** Without a fraction metric, claims about coverage are vague.
6. **Can MI catch deliberate sandbagging** — a model that internally represents "I could answer this better but won't"? This is the alignment question MI most needs to answer and hasn't yet.

## Sources

- [Bricken et al. 2023] Bricken, T. et al. *Towards Monosemanticity: Decomposing Language Models with Dictionary Learning*. Anthropic. https://transformer-circuits.pub/2023/monosemantic-features
- [Conmy et al. 2023] Conmy, A. et al. *Towards Automated Circuit Discovery for Mechanistic Interpretability*. https://arxiv.org/abs/2304.14997
- [Cunningham et al. 2023] Cunningham, H. et al. *Sparse Autoencoders Find Highly Interpretable Features in Language Models*. https://arxiv.org/abs/2309.08600
- [Elhage et al. 2022] Elhage, N. et al. *Toy Models of Superposition*. Anthropic. https://transformer-circuits.pub/2022/toy_model/
- [Gao et al. 2024] Gao, L. et al. *Scaling and Evaluating Sparse Autoencoders*. OpenAI. https://arxiv.org/abs/2406.04093
- [Nanda et al. 2023] Nanda, N., Chan, L., Lieberum, T., Smith, J., Steinhardt, J. *Progress Measures for Grokking via Mechanistic Interpretability*. https://arxiv.org/abs/2301.05217
- [Olsson et al. 2022] Olsson, C., Elhage, N. et al. *In-context Learning and Induction Heads*. Anthropic. https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/
- [Räuker et al. 2023] Räuker, T. et al. *Toward Transparent AI: A Survey on Interpreting the Inner Structures of Deep Neural Networks*. https://arxiv.org/abs/2207.13243
- [Templeton et al. 2024] Templeton, A., Conerly, T. et al. *Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet*. Anthropic. https://transformer-circuits.pub/2024/scaling-monosemanticity/
- [Wang et al. 2022] Wang, K., Variengien, A., Conmy, A., Shlegeris, B., Steinhardt, J. *Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 Small*. https://arxiv.org/abs/2211.00593
- [Zou et al. 2023] Zou, A. et al. *Representation Engineering: A Top-Down Approach to AI Transparency*. https://arxiv.org/abs/2310.01405

## Links

- [[hard-problem-consciousness]] — MI is the only realistic path to turning AI-consciousness indicator properties into concrete internal tests. The link runs both ways: MI tools care about what concepts are represented; consciousness debates care about whether specific representational structures suffice.
- [[octopus-cognition]] — the only other complex mind we have, and we have essentially no direct access to its internals. That asymmetry is part of why MI matters philosophically, not just technically.
- [[landauer-thermodynamics-computation]] — the physical floor under the computations we're reading. The relationship is indirect but useful: MI tells us the computation, Landauer tells us what it costs physically.
- [[why-biology-runs-near-the-landauer-bound]] — companion note; the energy gap between biology and silicon sits under every MI result about model compute costs.
- [[collective-intelligence]] — features in superposition resemble competing-population codes. There may be a shared abstraction here: "many overlapping items represented in a shared medium" as a motif across biological swarms and transformer residual streams.
- [[slime-mold-computation]] — computation without clearly interpretable "units" at all. A useful limit case: what does MI look like for a system that *has* no discrete features?
