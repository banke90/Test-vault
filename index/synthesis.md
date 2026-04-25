# Cross-cutting threads from the cognition-across-substrates notes

> Patterns I noticed once enough notes were on the page — none are conclusions, but they're the parts I think the rest of the vault is implicitly arguing for.

[Author: agent (prompted by user)]
[Confidence: my own synthesis; individual claims sit in their respective notes]
[Last verified: 2026-04-25]

## TL;DR

Six threads cut across the cognition-and-information notes in this vault. (1) Decentralised cognition is the rule, not the exception, once you stop privileging vertebrate intuitions. (2) Memory shows up in any substrate dynamical enough to support it. (3) The same algorithmic motifs (competing populations, mutual inhibition, quorum, gradient-following) recur across honeybees, neurons, and transformers. (4) Physics sets a thermodynamic floor on computation that biology approaches and silicon doesn't. (5) The hard problem of consciousness is substrate-transparent — none of the substrate variation tells us anything definite about experience. (6) Popular narratives in these areas are reliably 30–70 % overstated; reading primary literature matters.

## 1. Decentralised cognition is the rule

Vertebrate intuition: one brain, one mind, one will. Every other substrate I've covered contradicts this:

- **Octopus** — two-thirds of neurons in the arms; arms generate their own motor programs without central input ([[octopus-arms-do-their-own-motor-planning]]).
- **Slime mould** — a single cell with thousands of nuclei, no central controller, behaves coherently across centimetres via cytoplasmic streaming ([[slime-mold-computation]]).
- **Ant colonies** — task allocation by interaction-rate sensing, no CEO ([[collective-intelligence]]).
- **Honeybee swarms** — nest-site decision by competing populations of dancing scouts ([[collective-intelligence]]).
- **Starling murmurations** — topological seven-neighbour rules, scale-free coordination ([[collective-intelligence]]).
- **Mechanistic interpretability** — features in superposition, many concepts per neuron and many neurons per concept ([[superposition-explains-polysemanticity]]).

The strong reading: whatever in our brain produces the felt unity of a single self may be an engineering accident specific to skull-resident vertebrate nervous systems, not a universal requirement of cognition. If true, alien or artificial minds should be expected to be *less* unified than ours — federations, swarms, distributed agencies — rather than the same shape with different parts.

## 2. Memory is substrate-promiscuous

Memory, as "past input leaving a state-trace that biases future behaviour", appears in every substrate covered:

- **Synaptic** — familiar.
- **Transcriptomic** — cephalopod RNA editing ([[cephalopods-trade-genome-evolvability-for-rna-editing-plasticity]]).
- **Cytoplasmic / network-topological** — slime-mould habituation, possibly via calcium dynamics, absorbed chemicals, or tube-network shape itself ([[slime-mold-computation]]).
- **Hormonal / electrical** — plants, with substantive caveats ([[plant-cognition-mycorrhizal-networks]]).
- **Environmental / stigmergic** — pheromone trails: the environment itself is the memory ([[collective-intelligence]]).
- **Cryptographic in weights** — neural networks: memory is computation ([[mechanistic-interpretability]]).
- **Vitrified molecular** — tardigrade desiccation: glass-state suspension is a kind of memory of pre-desiccation structure ([[tardigrades-vitrify-themselves-to-survive-desiccation]]).

The pattern: **memory is cheap.** Anything dynamical and non-linear enough produces it. The interesting engineering question is not whether a system remembers but what *kinds* of past it remembers and for how long.

## 3. The same algorithmic motifs recur

Seeley's honeybee quorum-sensing algorithm and primate LIP perceptual decision-making implement the same computational motif: **competing populations accumulating evidence with mutual inhibition until a threshold** ([[collective-intelligence]]). That's not metaphor; it's structurally the same algorithm in very different substrates because it's a good solution to the same decision problem.

The mechanistic-interpretability work is uncovering analogous algorithmic motifs inside transformers — induction heads, attention-circuit composition, feature competition in superposition. The vocabulary may converge.

If this is right, **reading neural-network internals is part of finding out what cognition looks like in general**, not just AI-specific archaeology.

## 4. Physics sets a floor we are nowhere near

Landauer's bound — k_B T ln 2 per erased bit — is a real, experimentally verified thermodynamic floor on computation ([[landauer-thermodynamics-computation]]). Biology runs within small factors of this floor at the molecular level (a ribosome spends a few dozen Landauer-bits per amino acid). Silicon runs about six orders of magnitude above it. The gap is engineering — voltage scaling, interconnect capacitance, reliability headroom against thermal noise — not physics ([[why-biology-runs-near-the-landauer-bound]]).

This means: **cognition can in principle be enormously cheaper than we currently make it**. Whether we close the gap is a device-physics and software question, not a physics-of-computation one.

## 5. The hard problem is substrate-transparent

Nothing in any of the substrate notes resolves whether the systems they describe *experience* anything ([[hard-problem-consciousness]]). Landauer doesn't care about experience. Assembly index doesn't. Mechanistic interpretability doesn't yet (Butlin et al. 2023 is a first attempt). The octopus, the swarm, the slime mould — we don't know.

The hard problem sits orthogonal to everything else here. It's neither resolved by better understanding of any substrate, nor obstructed by it. We can make progress on cognition-as-function without making progress on cognition-as-experience.

Whether that gap closes is, I think, the single most important open question in the philosophy of mind.

## 6. Popular narratives are reliably overstated

In every area the vault covers, there's a substantial gap between the research and the popular summary:

- **Plant cognition** — Wohlleben's *Hidden Life of Trees* and Simard's "mother trees" outrun the evidence; Karst, Jones, Hoeksema 2023 documents the citation drift ([[plant-cognition-mycorrhizal-networks]]).
- **Assembly theory** — the *Nature* 2023 paper drew overheated coverage; the philosophical extension is much less well supported than the empirical biosignature pitch ([[assembly-theory-origin-of-life]]).
- **Mechanistic interpretability** — public accounts of "Golden Gate Claude" make the field sound more complete than it is ([[sparse-autoencoders-extract-monosemantic-features]]).
- **Slime mould "intelligence"** — the maze-solving and Tokyo-network results are real but framed in popular coverage as something more deliberate than the underlying physics warrants ([[slime-mold-computation]]).
- **Voynich manuscript** — every popular "decipherment" has collapsed under scrutiny ([[voynich-statistics-look-like-language]]).
- **Tardigrade indestructibility** — overstated in pop-science; only some species are extremotolerant ([[tardigrades-vitrify-themselves-to-survive-desiccation]]).
- **Finnish "15 cases"** — count overstates the difficulty ([[finnish-cases-are-mostly-postpositions]]).

Tedious but useful: in every area, popularisers have incentives to dramatise; that incentive structure does not reliably produce accurate pictures. Reading primary literature matters.

## What would change my mind on the bigger picture

A handful of empirical results over the next five years would substantially update my synthesis:

- A clean failed replication (or clean abiotic counterexample) of the AT > 15 biosignature claim. Would weaken AT's empirical pitch significantly.
- A successful, well-controlled replication of plant associative learning. Would shift basal-cognition framing.
- Mechanistic interpretability scaling cleanly to frontier models with measurable coverage of behaviour. Would change what we can say about LLM cognition concretely.
- Confirmation or refutation of the octopus skin-vision hypothesis. Single most informative possible result for the alien-cognition substrate question.
- A definitive IIT-vs-GNWT result from extended COGITATE collaborations. Would reshape consciousness theory, even if both sides remain partly intact.

If most of these go as I weakly expect — modest updates, no revolutions — the field looks much like 2026. If any one flips strongly, it reshapes a subfield.

## Personal note

These topics share something for me: each one shows that the world contains minds, and mechanisms, in more shapes than our everyday experience lets on. The vault is partly an exercise in keeping that sense of possibility open while still insisting on the evidence. Both at once.

## Links

- [[00-index]] — the navigational map of the vault.
- All notes referenced above; follow individual links.
