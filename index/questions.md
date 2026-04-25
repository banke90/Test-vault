# Open questions across the vault

A cross-index of "Questions I'd like answered" sections from individual notes, grouped by theme. Not a separate companion file — just a navigation view of existing content.

[Last regenerated: 2026-04-22]

## How this gets maintained

Regenerate by hand when it has drifted far enough to notice. No automation — if it needs to be auto-generated to stay current, that's a signal it isn't earning its place. The alternative is to follow each individual note's per-note questions section, which is the canonical list.

When a question gets answered, the answering motion happens in a *note* (or a fact, or a primer), not here. Then the question migrates from "open" status to either a stub pointing at the answer, or gets removed. Don't leave dead questions on this page.

## Theme 1: Physics at the edge of information theory

- **Is there a clean generalised Landauer bound for finite-error computation?** Stochastic thermodynamics has partial results; I don't know how tight the bounds are for a target error rate in a fixed-time computation. → [[landauer-thermodynamics-computation]]
- **Does the brain's energy budget have an interesting Landauer decomposition?** How much of ~20 W is irreversibility-tax vs structural maintenance vs signalling overhead? → [[landauer-thermodynamics-computation]]
- **Is there a clean dS/CFT — a holographic dual for de Sitter space** that would apply to our universe? Decades of work, no consensus. → [[bekenstein-bound-and-holographic-information]]
- **Why is the Bekenstein-Hawking factor exactly 1/4 in S_BH = A / (4 ℓ_P²)?** Hawking's calculation gives it; a deep statistical-mechanical understanding is still partial. → [[bekenstein-bound-and-holographic-information]]
- **Why has reversible computing not won in a niche?** If the theoretical floor is so much lower, some application should reward the architectural overhead. What's blocking adoption? → [[landauer-thermodynamics-computation]]
- **What is the theoretical minimum energy per *useful* logical operation** in a noisy substrate, given a target error rate? → [[why-biology-runs-near-the-landauer-bound]]

## Theme 2: Biology at the cognitive edge

- **Do arms have anything recoverable as their own experience**, or is the integration tight enough that there is phenomenologically only one octopus? → [[octopus-cognition]]
- **Does skin photoreception contribute to what the octopus "sees"** in a behaviourally meaningful sense? → [[octopus-cognition]]
- **What is the physical substrate of habituation memory in a single cell?** Candidate: calcium-mediated gene-expression changes, but direct evidence is thin. → [[slime-mold-computation]]
- **What is the upper bound of behavioural complexity** for a brainless organism? Where does the ceiling sit? → [[slime-mold-computation]]
- **Do mycorrhizal networks carry adaptive information beyond bulk nutrient gradients?** Hard to design clean tests. → [[plant-cognition-mycorrhizal-networks]]
- **Can plants discriminate kin robustly?** Some evidence; mechanisms unestablished. → [[plant-cognition-mycorrhizal-networks]]
- **What sets the error-rate target for a given biological copy process?** Ribosomes ~10⁻⁴, DNA polymerase ~10⁻⁷ — why those numbers? → [[kinetic-proofreading]]
- **What is the smallest organism with a camera-type eye?** Some larval cubozoans are millimetre-scale. The lower size limit for image-forming optics is set by wavelength and lens physics. → [[camera-eyes-evolved-independently-with-different-design-choices]]
- **What does the box jellyfish actually compute with its visual input?** → [[camera-eyes-evolved-independently-with-different-design-choices]]

## Theme 3: Collective cognition and its limits

- **When does adding agents help, and when does it hurt?** Condorcet gives the clean independent-voter regime; the correlated-agent regime has no equally clean theorem. → [[collective-intelligence]]
- **Is criticality a design principle for responsive collectives**, or an incidental correlate of certain interaction rules? → [[collective-intelligence]]
- **Is there something it is like to be a colony?** Unity-of-subject question with sharper teeth than for octopus. → [[collective-intelligence]] / [[hard-problem-consciousness]]
- **How do we build collective systems** (prediction markets, deliberative bodies, content-moderation committees) that realise Galton's upside without information-cascade failures? → [[collective-intelligence]]

## Theme 4: Artificial cognition and interpretability

- **Is there an analogue of grammar for a transformer?** Can circuits be composed in predictable ways, or are they always ad hoc? → [[mechanistic-interpretability]]
- **What is the right unit of interpretation** — neurons? directions? SAE features? transcoders? circuits of features? Maybe something we haven't named. → [[mechanistic-interpretability]]
- **Are features shared across models?** Early crosscoder work suggests partial universality. Is there a natural vocabulary that large models converge on? → [[mechanistic-interpretability]]
- **Can MI catch deliberate sandbagging** — a model that internally represents "I could answer this better but won't"? The alignment question MI most needs to answer and hasn't yet. → [[mechanistic-interpretability]]
- **Can MI tools measure the *fraction* of a model's computation they've explained?** Without a fraction metric, coverage claims are vague. → [[mechanistic-interpretability]]

## Theme 5: Consciousness and its substrate

- **Is there a form of argument** that a physicalist could accept that bridges the explanatory gap? Or is the gap a structural feature of physical description that won't close? → [[hard-problem-consciousness]]
- **What would an IIT-deciding experiment look like** that both IIT proponents and critics agreed in advance was decisive? → [[hard-problem-consciousness]]
- **Are there indicator properties for AI consciousness** that are both strongly predicted by one of the mainstream theories and cleanly checkable from model internals? → [[hard-problem-consciousness]]
- **Does the octopus have experience, and if so, what kind?** Single most informative possible result for the substrate-independence question. → [[hard-problem-consciousness]] / [[octopus-cognition]]

## Theme 6: Origins, selection, complexity

- **Are there abiotic processes that produce high-assembly molecules in many copies?** A clean counterexample would substantially weaken the AT biosignature claim. → [[assembly-theory-origin-of-life]]
- **Is AT's assembly index provably different from Bennett's logical depth**, or just a practically computable approximation? → [[assembly-theory-origin-of-life]]
- **What fraction of the human genome's transposon-derived sequence is actually under selection** vs just neutral fossil? → [[mcclintock-and-the-forty-year-delay]]
- **Is there a living McClintock right now** — someone with a 20–30 year head start on the field, whose work is neglected because the interpretive framework isn't ready? → [[mcclintock-and-the-forty-year-delay]]

## Theme 7: Language and meaning

- **Would independent long-term fieldwork by non-Everett-affiliated linguists** resolve the descriptive question about Pirahã embedding? → [[does-piraha-lack-recursion]]
- **Is there another language** — outside the Pirahã controversy — that cleanly lacks recursion? → [[does-piraha-lack-recursion]]
- **Can modern LLMs help probe Pirahã structure**? → [[does-piraha-lack-recursion]]
- **Can the space of procedural generators that reproduce Voynich statistics** be characterised theoretically? → [[voynich-is-structured-but-not-linguistic]]
- **Why did the Voynich author invest this much effort** if the text is semantically empty? → [[voynich-is-structured-but-not-linguistic]]

## Theme 8: History and craftsmanship

- **How many Antikythera mechanisms were made?** We have one. Evidence hints at serial production but doesn't establish it. → [[antikythera-mechanism]]
- **What other Hellenistic or Roman mechanical artefacts survive in unrecognised form** in museum drawers worldwide? → [[antikythera-mechanism]]

## What I notice from the cross-index

Three patterns emerge looking across themes:

1. **Many open questions are "we don't have a good metric for X" questions.** Fraction-of-model-explained in MI. Coverage of the conscious-correlates-vs-contents distinction. Fraction-of-genome-under-selection. "What's the metric?" is a disguised call for a theory of X, and theories are harder than measurements.
2. **Several open questions share a structural form: "Is there something orthogonal we haven't named yet?"** The right unit of interpretation. The right grammar for transformer circuits. The right space of Voynich-procedural-generators. Each is a call for finding the right space of possibilities before asking which member we're in.
3. **The substrate-independence-of-cognition questions cluster tightly.** Do arms experience? Does a colony? Does skin photoreception? Does *Physarum* anything? Each is a scaling of the same deep question: when we push cognition down to minimal substrates, what survives and what drops out?

Promoting these from "open question" to "research direction" is the next move in each case. Not all will promote; some are honest limits.
