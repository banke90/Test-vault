# Mechanistic interpretability — survey

> Hub for the mechanistic-interpretability cluster. Each substantive technique and result lives in its own atomic note; this file gives the orientation and the index.

[Confidence: this is a navigation aid; see linked atoms for confidence on individual claims]
[Last verified: 2026-04-25]

## TL;DR

Mechanistic interpretability (MI) tries to explain a neural network's behaviour in terms of the computations its weights implement — not just what the model outputs, but *how*. The programme makes two bets: that there is structure to find inside the model, and that finding it is useful for alignment and for science. The dominant tools as of 2026 are **sparse autoencoders** ([[sparse-autoencoders-extract-monosemantic-features]]) and **circuit analysis** ([[induction-heads-are-the-archetypal-circuit]]), grounded conceptually in **superposition** ([[superposition-explains-polysemanticity]]) and combined at production scale in **attribution graphs** ([[attribution-graphs-explain-specific-prompts-not-models]]). Open problems: faithfulness, coverage, scaling, and whether per-prompt analyses generalise.

## Why interpretability at all

Behavioural evaluation is cheap and indispensable, and has a hard ceiling: it tells you what the model does *on the inputs you tested*, not whether the behaviour you like is produced by the process you think. A model that refuses harmful requests because a "refusal feature" fires on surface cues is a different object from one that refuses because it understands the request. **Behavioural evaluation cannot tell them apart.**

MI tries to break that ceiling. If successful: detect deception or misalignment that hides from behavioural probes; steer models by editing internals rather than prompting around them; build scientific understanding of what learned computation looks like in general.

## The cluster

- **[[superposition-explains-polysemanticity]]** — the conceptual foundation: networks pack more features than they have dimensions by encoding them as nearly-orthogonal directions, making single neurons polysemantic by construction.
- **[[sparse-autoencoders-extract-monosemantic-features]]** — the dominant 2023–2025 tool for un-superposing learned representations into single-concept feature directions.
- **[[induction-heads-are-the-archetypal-circuit]]** — the cleanest existence proof that small models implement nameable algorithms (in-context pattern completion via a two-head circuit), with companion results on IOI and modular arithmetic.
- **[[attribution-graphs-explain-specific-prompts-not-models]]** — the production-scale combination: SAE features as nodes, causal patching for edges, per-prompt graphs of how a forward pass was processed.

## Alignment relevance

The pitch: behavioural evaluation misses safety-critical phenomena by construction. Sycophancy (preferring trainer-pleasing answers over true ones) and sandbagging (behaving well under observation, differently otherwise) cannot be caught behaviourally. If these patterns leave internal signatures, MI is one of the few tools that might catch them.

The existence in production models of features that look like "deception", "lying", "unsafe content", "user gratification", and "thinking about being observed" [Templeton et al. 2024] shows MI is seeing *something*. It does not yet tell us whether those features are *used* in misaligned ways or are bookkeeping about relevant concepts. The causal-role question is harder than the representation question.

## Disagreements and cautions

- **Interpretability illusions.** Plausible-looking explanations of internals can fail causal tests. Beautiful stories about features are cheap; rigorous ones are hard *(established caution)*.
- **Cherry-picking.** Many published successes are small models on narrow tasks; how much carries over to frontier scale is unclear.
- **Coverage.** Even if each feature is real, we don't know what fraction of model computation is explained. The unknown fraction matters for alignment-critical claims.
- **The "MI is succeeding" / "MI is hype" debate** is live. My read: empirical results are real and the field has a track record; claims that MI is close to solving alignment-relevant detection problems are premature.

## Questions I'd like answered

1. Is there a grammar of transformers — predictable ways circuits compose — or are they always task-specific?
2. How does MI scale with model capability? Are we getting closer or further from a full account as models scale?
3. What is the right *unit* of interpretation — neurons, directions, SAE features, transcoders, or something we haven't named?
4. Are features shared across models? Crosscoder work suggests partial universality.
5. Can MI tools measure the *fraction* of computation they've explained? Without a fraction metric, coverage claims are vague.
6. Can MI catch deliberate sandbagging? This is the alignment question MI most needs to answer and hasn't yet.

## Sources

- [Templeton et al. 2024] Templeton, A., Conerly, T. et al. *Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet*. Anthropic. https://transformer-circuits.pub/2024/scaling-monosemanticity/
- [Räuker et al. 2023] Räuker, T. et al. *Toward Transparent AI: A Survey on Interpreting the Inner Structures of Deep Neural Networks*. https://arxiv.org/abs/2207.13243

(Per-claim sources live in the atom notes.)

## Links

- [[hard-problem-consciousness]] — MI is the only realistic path to turning AI-consciousness indicator properties into concrete internal tests.
- [[octopus-cognition]] — the only other complex mind we have anything close to internal access to. The asymmetry — octopus internals we can't read, transformer activations we can — is part of why MI matters philosophically, not just technically.
- [[landauer-thermodynamics-computation]] — the physical floor under the computations MI reads.
- [[why-biology-runs-near-the-landauer-bound]] — companion: the energy gap between biology and silicon sits under every MI result about model compute costs.
- [[collective-intelligence]] — features in superposition resemble competing-population codes; "many overlapping items represented in a shared medium" recurs across biological swarms and transformer residual streams.
- [[slime-mold-computation]] — limit case: computation without clearly interpretable units at all. What does MI look like for a system that *has* no discrete features?
