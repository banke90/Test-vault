# Induction heads are the archetypal interpretability circuit

> A pair of attention heads — a "previous-token" head followed by a "match-and-copy" head — implement in-context pattern completion ("if you saw A B earlier and now see A, predict B"); they emerge abruptly during training, are tightly correlated with the onset of in-context learning, and are the cleanest existence proof that learned circuits in transformers can be reverse-engineered.

[Confidence: established and replicated]
[Last verified: 2026-04-25]

## TL;DR

Olsson, Elhage and colleagues showed that small transformers reliably learn a two-head **induction circuit**: a previous-token attention head plus a match-and-copy head that together implement in-context completion of repeated patterns [Olsson et al. 2022]. The circuit emerges sharply during training at the same point in-context learning ability does, suggesting it is the algorithmic substrate of that capability. Together with the GPT-2-small **Indirect Object Identification** circuit [Wang et al. 2022] and the modular-arithmetic / grokking circuits [Nanda et al. 2023], it forms the existence-proof set for "learned circuits can be read off almost like code, at least in small models on narrow tasks."

## What an induction circuit is

The behavioural pattern: if a model has seen the bigram `A B` earlier in context and is now processing a new occurrence of `A`, predict `B`. The mechanism, as reverse-engineered:

- **Head 1: previous-token head.** At each position, attend to the immediately preceding token and copy information about it forward. After this layer, every position carries information about its own *and* its predecessor's identity.
- **Head 2: match-and-copy head.** At the current `A` position, attend back through context for tokens whose *predecessor* was also `A`. The prior token at those positions was `B` — copy its identity into the residual stream.

Two heads, two layers, executing a small algorithm. The circuit is causally testable via activation patching and has been replicated across model families.

## Why it matters

Induction heads emerge **abruptly** during training at the same point in-context learning ability rises. Before that point, models cannot copy patterns. After it, they can. The emergence is sharp enough to look like a phase transition, and the temporal correlation with in-context learning suggests they are the mechanism — not a correlate.

This is the cleanest existence proof for the broader bet of mechanistic interpretability: that meaningful, named computations can be located inside trained networks and understood as small algorithms.

## Companion circuit-level results

- **Indirect Object Identification (IOI)** [Wang et al. 2022]. Reverse-engineered the GPT-2-small circuit that completes "When Mary and John went to the store, John gave a drink to ___" with "Mary". A handful of heads do duplicate-token detection, S-inhibition, and name-moving. The end-to-end behaviour decomposes into nameable subcomputations.
- **Modular addition / greater-than** [Nanda et al. 2023]. Small models trained on arithmetic learn Fourier-style decompositions; the circuit can be read off in closed form.

These results all share a property: they are small models on narrow tasks where the ground-truth algorithm is checkable. Whether the same kind of clean circuit-readout works at frontier scale is a live, open question.

## Disagreements and cautions

- **Cherry-picking.** Successes are real but selected; the field reports clean cases more readily than messy ones.
- **Scaling.** Frontier models are larger, more distributed, and likely harder to interpret in this way. Whether a "grammar of transformers" exists or whether circuits are always ad hoc is unsettled.
- **Causal-mediation tests** are necessary but not sufficient to claim a clean reading; the model may also use other paths.

## Questions I'd like answered

1. Is there a grammar of transformers — predictable ways circuits compose — or are they always task-specific?
2. How does circuit interpretability scale with capability? Are we getting closer or further from full accounts as models scale?
3. Can we systematically discover induction-like circuits via automated tools (ACDC, edge attribution patching) at frontier scale?

## Sources

- [Olsson et al. 2022] Olsson, C., Elhage, N. et al. *In-context Learning and Induction Heads*. Anthropic. https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/
- [Wang et al. 2022] Wang, K., Variengien, A., Conmy, A., Shlegeris, B., Steinhardt, J. *Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 Small*. https://arxiv.org/abs/2211.00593
- [Nanda et al. 2023] Nanda, N., Chan, L., Lieberum, T., Smith, J., Steinhardt, J. *Progress Measures for Grokking via Mechanistic Interpretability*. https://arxiv.org/abs/2301.05217
- [Conmy et al. 2023] Conmy, A. et al. *Towards Automated Circuit Discovery for Mechanistic Interpretability*. https://arxiv.org/abs/2304.14997

## Links

- [[mechanistic-interpretability]] — survey hub.
- [[sparse-autoencoders-extract-monosemantic-features]] — feature-level analysis at the activation-direction level, complementary to head/neuron-level circuits.
- [[superposition-explains-polysemanticity]] — superposition explains why neurons themselves resist clean readouts and why circuit-level analysis often needs feature-level decoding first.
- [[attribution-graphs-explain-specific-prompts-not-models]] — combines feature-level and circuit-level analyses at production-model scale.
