# Sparse autoencoders extract monosemantic features from neural-network activations

> A wide autoencoder with a sparsity penalty, trained on a model's hidden activations, learns latent dimensions that often correspond to single human-legible concepts — the dominant tool of the 2023–2025 interpretability wave, with known limits in faithfulness, coverage, and feature-splitting.

[Confidence: established for the empirical results; mixed for whether SAE features faithfully cover the model's real computation]
[Last verified: 2026-04-25]

## TL;DR

A **sparse autoencoder** (SAE) is a wide autoencoder trained on a model's hidden activations with an L1 or top-k sparsity penalty; the hope is that each learned latent corresponds to a monosemantic concept. The clean demonstration came from Bricken, Templeton et al. on a one-layer model in *Towards Monosemanticity* [Bricken et al. 2023]; *Scaling Monosemanticity* [Templeton et al. 2024] applied it at production scale to Claude 3 Sonnet, finding interpretable features for the Golden Gate Bridge, deception, sycophancy, secrecy, and others. SAEs work, ship results, and have known problems — dead features, feature-splitting at larger widths, a reconstruction-vs-interpretability trade-off, and unresolved faithfulness/coverage questions.

## What the technique does

The setup:

- Take a trained model's hidden activations at a layer (the residual stream, or an MLP output).
- Train an autoencoder much wider than the activation dimension — so it has many more latent units than the residual stream has dimensions.
- Add a sparsity penalty (L1 on activations, or a top-k constraint that selects the k strongest activations per input).
- The encoder maps activations to sparse latent codes; the decoder maps latents back to reconstruct activations.

The bet: the model's internal representations are **superposed** — many features packed as nearly-orthogonal directions in fewer dimensions (see [[superposition-explains-polysemanticity]]). A wide-and-sparse autoencoder is a tool for *un*superposing them, finding the feature directions one at a time.

## Key milestones

- **Cunningham, Ewart, Riggs, Huben, Sharkey 2023.** *Sparse Autoencoders Find Highly Interpretable Features in Language Models* [Cunningham et al. 2023] — first wide demonstration on transformer models.
- **Bricken, Templeton et al. (Anthropic, Oct 2023).** *Towards Monosemanticity* [Bricken et al. 2023] — clean demonstration on a one-layer model, with strong evidence for monosemanticity of learned features.
- **Templeton, Conerly et al. (Anthropic, May 2024).** *Scaling Monosemanticity* [Templeton et al. 2024] — production-scale on Claude 3 Sonnet. Surfaces features for the Golden Gate Bridge (clamping it produces "Golden Gate Claude"), deception, sycophancy, secrecy, code categories, language, and safety-relevant concepts.
- **Variant architectures.** Top-k SAEs [Gao et al. 2024], gated SAEs (DeepMind), JumpReLU SAEs, transcoders (approximate MLP blocks), crosscoders (tie features across layers or models).

## Known problems

- **Dead features.** Many SAE latents never activate on any input, wasting capacity.
- **Feature splitting.** At larger SAE widths, what looked like one feature at smaller width splits into many; the "right" granularity is unclear.
- **Reconstruction–interpretability trade-off.** SAEs that reconstruct activations well are often less interpretable, and vice versa.
- **Faithfulness and coverage.** No proof that SAE features are *all* the features the model uses, or that they are causally faithful to its actual computation. This is the deepest worry.

## Disagreements and cautions

- **Monosemanticity as artefact.** Some SAE features look monosemantic under one prompt distribution and polysemantic under another. The metric may be evaluation-dependent.
- **Causal role.** Showing a feature exists in the SAE is weaker than showing the model uses that feature in its computation. Activation patching helps, but coverage is partial.
- **Cherry-picking.** Many published features are striking; the distribution over all features is messier.

## Questions I'd like answered

1. What is the right *unit* of interpretation — neurons, directions, SAE features, transcoders, or something we haven't named? Without a settled unit, claims about coverage are vague.
2. Are SAE features shared across models (universality)? Crosscoder work suggests partial yes.
3. Can SAE-feature analysis be turned into a coverage metric — what fraction of a model's computation is explained?

## Sources

- [Bricken et al. 2023] Bricken, T. et al. *Towards Monosemanticity: Decomposing Language Models with Dictionary Learning*. Anthropic. https://transformer-circuits.pub/2023/monosemantic-features
- [Cunningham et al. 2023] Cunningham, H. et al. *Sparse Autoencoders Find Highly Interpretable Features in Language Models*. https://arxiv.org/abs/2309.08600
- [Gao et al. 2024] Gao, L. et al. *Scaling and Evaluating Sparse Autoencoders*. OpenAI. https://arxiv.org/abs/2406.04093
- [Templeton et al. 2024] Templeton, A., Conerly, T. et al. *Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet*. Anthropic. https://transformer-circuits.pub/2024/scaling-monosemanticity/

## Links

- [[mechanistic-interpretability]] — survey hub for the broader interpretability cluster.
- [[superposition-explains-polysemanticity]] — the underlying coding scheme SAEs are designed to un-pack.
- [[induction-heads-are-the-archetypal-circuit]] — circuit-level analysis at neuron/head granularity, complementary to feature-level SAE analysis.
- [[attribution-graphs-explain-specific-prompts-not-models]] — uses SAE features as nodes in a per-prompt causal graph.
