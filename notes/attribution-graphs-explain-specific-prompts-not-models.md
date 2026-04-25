# Attribution graphs explain specific prompts, not whole models

> Anthropic's attribution-graph / "biology of an LLM" line uses SAE features as nodes and causal patching to draw per-prompt graphs of how a forward pass was processed; the result is the state of the art for detailed internal analysis of frontier LLMs, but it is case-by-case rather than a theory of the model.

[Author: agent (prompted by user)]
[Confidence: established for the empirical pipeline; mixed for whether it scales into a general account]
[Last verified: 2026-04-25]

## TL;DR

The follow-up to *Scaling Monosemanticity* is the **attribution-graph** programme — *On the Biology of a Large Language Model* and successors — which applies feature-level circuit analysis at production-model scale. The method uses SAE features (see [[sparse-autoencoders-extract-monosemantic-features]]) as nodes, computes causal attributions between them via patching or gradient-based methods, and builds a graph showing how a *specific* prompt was processed. Reported case studies include multi-step reasoning, entity recognition, refusal, and planning ahead in poetry generation. The crucial caveat is in the title of this note: an attribution graph explains *how this forward pass worked*, not the model in general.

## What an attribution graph is

The pipeline:

1. **Choose a prompt.** Pick a specific input where the model's behaviour is interesting.
2. **Run the model.** Record activations at every relevant layer.
3. **Decode features.** Use a pre-trained SAE (or transcoder) to convert raw activations into sparse feature codes at each layer.
4. **Compute attributions.** Use activation patching, path patching, or gradient-based methods to estimate how much each upstream feature causally contributed to each downstream feature.
5. **Assemble the graph.** Nodes are active features at each layer; edges are causal contributions; the resulting graph is the "biology" of the forward pass.

What you get: a per-prompt narrative of which features fired, what triggered them, and how they routed information toward the output. Striking case studies have shown multi-hop reasoning paths, entity-attribution circuits, and apparent forward-planning in tasks like poetry generation.

## Methodological toolkit it builds on

- **Activation patching / causal mediation.** Standard for establishing the causal role of a component *(established)*.
- **Path patching.** Variant isolating specific paths through the computation graph.
- **Direct logit attribution.** Decompose a logit as a sum over components via the unembedding direction.
- **Linear probing.** Long-established; ambiguous between "the model uses this" and "this is recoverable" — the probe might find structure without it being computationally load-bearing.
- **Representation engineering / activation steering** [Zou et al. 2023]. Add a concept vector to activations and observe behavioural change. Complementary to feature clamping.

## What an attribution graph does *not* give you

- A general theory of the model. The graph explains a particular forward pass; the next prompt might activate different features and route information differently.
- A coverage guarantee. The features and edges in the graph are those the SAE and the attribution method surfaced. The fraction of the actual computation accounted for is unknown.
- Robustness to off-distribution prompts. Features that look interpretable on typical inputs may misbehave on adversarial or out-of-distribution ones.

The honest framing is: it is the most detailed internal analysis tool we have for production-scale LLMs, and it is genuinely case-based.

## Disagreements and cautions

- **Interpretability illusions.** Plausible-looking explanations of internals can fail causal tests (Friedman, Lal, Wiegreffe et al.). Beautiful stories about features are cheap; rigorous ones are hard *(established caution)*.
- **Faithfulness.** Even with causal patching, the graph reflects the SAE's view of features, not necessarily the model's true latent structure. Coverage and causal-faithfulness questions are open.
- **Generalisation across prompts.** When does a circuit observed on one prompt apply to others? Without a clear answer, "we found a refusal circuit" is weaker than it sounds.

## Questions I'd like answered

1. Can attribution-graph results be aggregated across prompts into model-level structure, or are they intrinsically per-prompt?
2. Is there a metric for *fraction of forward-pass computation explained*? Without one, coverage claims are vague.
3. Can attribution graphs catch deliberate sandbagging — a model representing "I could answer this better but won't"? This is the alignment question MI most needs to answer and hasn't yet.

## Sources

- [Templeton et al. 2024] Templeton, A., Conerly, T. et al. *Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet*. Anthropic. https://transformer-circuits.pub/2024/scaling-monosemanticity/
- [Conmy et al. 2023] Conmy, A. et al. *Towards Automated Circuit Discovery for Mechanistic Interpretability*. https://arxiv.org/abs/2304.14997
- [Zou et al. 2023] Zou, A. et al. *Representation Engineering: A Top-Down Approach to AI Transparency*. https://arxiv.org/abs/2310.01405
- [Räuker et al. 2023] Räuker, T. et al. *Toward Transparent AI: A Survey on Interpreting the Inner Structures of Deep Neural Networks*. https://arxiv.org/abs/2207.13243

## Links

- [[mechanistic-interpretability]] — survey hub for the broader interpretability cluster.
- [[sparse-autoencoders-extract-monosemantic-features]] — the feature-extraction tool that supplies the nodes of the attribution graph.
- [[induction-heads-are-the-archetypal-circuit]] — circuit-level analysis at the head/neuron level; attribution graphs combine head-level and feature-level.
- [[superposition-explains-polysemanticity]] — explains why feature decoding is needed before causal attribution makes sense.
