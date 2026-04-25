# Superposition explains why neurons are polysemantic

> Neural networks pack more distinct features than they have dimensions by encoding them as nearly-orthogonal directions in activation space; this makes individual neurons polysemantic by construction and is why "one neuron, one concept" is the wrong unit of interpretation.

[Confidence: established framing in toy models; the quantitative role at frontier scale is mixed]
[Last verified: 2026-04-25]

## TL;DR

Naïve hope: each neuron corresponds to one human-legible concept. Real networks don't cooperate. Neurons are **polysemantic** — single neurons respond to many unrelated things. Elhage et al. showed in *Toy Models of Superposition* that networks encode more features than they have dimensions by packing them as nearly-orthogonal directions in activation space [Elhage et al. 2022]; the encoding works because real-world feature distributions are sparse, so collisions are rare. The interpretability task is to invert the code and find the feature *directions*, not read neurons one at a time. This is the conceptual foundation for the SAE programme (see [[sparse-autoencoders-extract-monosemantic-features]]).

## The model

Toy setup, following Elhage et al.:

- Train a small autoencoder to compress sparse high-dimensional inputs through a low-dimensional bottleneck.
- The training data has more underlying features than the bottleneck has dimensions, but each input activates only a few features (sparsity).
- Outcome: the network learns to represent each feature as a direction in the bottleneck activation space, with directions chosen to be approximately mutually orthogonal. Many features → few dimensions → polysemantic units.

Why it works: if features are rare per input, two features almost never co-occur, so a direction representing one feature almost never gets falsely activated by the other. Sparsity is the substrate that makes superposition possible.

## Why this matters for interpretability

Superposition predicts:

- **Polysemantic neurons.** Most neurons respond to several apparently unrelated stimuli, because each neuron sits at some shared component of multiple feature directions.
- **Linear feature directions.** The feature is a *direction* in activation space, not a *neuron*. Linear probes pick up features for this reason.
- **The need for tools that work on directions, not units.** SAEs (see [[sparse-autoencoders-extract-monosemantic-features]]) are explicitly designed to recover feature directions from superposed activations.

Superposition reframes the central interpretability question from "what does this neuron mean?" to "what feature directions does this layer encode, and how are they used downstream?"

## Disagreements and cautions

- **Toy-model-to-frontier-scale generalisation.** Superposition is rigorous in toy settings. Whether real frontier models superpose features in the same way, and at what density, is a research question — the toy framing is the working hypothesis, not a theorem about LLMs.
- **Feature granularity.** "Feature" is doing a lot of work; at finer SAE widths a single feature can split into many sub-features. The right level is unclear.
- **Not all directions are features.** Linear probes find directions that classify well; that doesn't prove the model uses them. Superposition predicts feature-as-direction; the converse (every direction is a feature) is wrong.

## Questions I'd like answered

1. Is the per-layer feature density (features per dimension) predictable from architecture and training data, or is it an emergent property?
2. Do features in superposition have a stable *grammar* — do compositions of two features produce a third feature direction, or is composition non-linear?
3. How does superposition interact with circuit-level analysis (see [[induction-heads-are-the-archetypal-circuit]])? Are the intermediate activations of a circuit themselves superposed?

## Sources

- [Elhage et al. 2022] Elhage, N. et al. *Toy Models of Superposition*. Anthropic. https://transformer-circuits.pub/2022/toy_model/

## Links

- [[mechanistic-interpretability]] — survey hub.
- [[sparse-autoencoders-extract-monosemantic-features]] — the dominant tool for un-superposing learned representations.
- [[induction-heads-are-the-archetypal-circuit]] — circuit-level analysis at the head level; superposition explains why the *inputs* to those circuits often need feature-level decoding to be legible.
- [[collective-intelligence]] — superposition as "many overlapping items represented in a shared medium" has a structural cousin in competing-population codes in biological swarms.
