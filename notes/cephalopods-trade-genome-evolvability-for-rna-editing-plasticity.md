# Cephalopods trade genome evolvability for RNA-editing plasticity

> Cephalopod neural tissue recodes its transcriptome at tens of thousands of A-to-I editing sites; the genomic regions around heavily-edited sites are evolutionarily conserved because the editing machinery needs specific flanking sequence, so cephalopods may be paying in slowed genome evolution for fast, reversible protein tuning.

[Author: agent (prompted by user)]
[Confidence: established for the editing rate; mixed for the functional consequences]
[Last verified: 2026-04-25]

## TL;DR

Liscovitch-Brauer and colleagues showed that octopus, squid, and cuttlefish neural tissue is **massively A-to-I RNA edited** — tens of thousands of recoding sites, vs. a few dozen in humans — changing amino-acid identities post-transcriptionally [Liscovitch-Brauer et al. 2017]. The DNA flanking these editing sites is unusually conserved, presumably because the editing machinery needs specific flanking sequence to bind. The trade-off, if real: cephalopods reduce **genome-level evolvability** (sequences are fixed in place) in exchange for **transcriptome-level plasticity** (proteins can be tuned on-the-fly, including for temperature compensation across species).

## What was found

Liscovitch-Brauer et al. (2017) sequenced neural transcriptomes from several cephalopod species and identified A-to-I editing sites — adenosine residues post-transcriptionally converted to inosine, which the ribosome reads as guanosine, recoding the amino acid:

- Tens of thousands of recoding editing sites in cephalopod neural tissue, vs. ~dozens in human tissue.
- The editing is enriched in genes encoding ion channels, transporters, and synaptic proteins — exactly where you'd expect functional tuning to matter for nervous-system performance.
- Comparing K⁺ channel sequences from Arctic and tropical octopus species: the edited transcripts (and resulting protein function) differ in temperature-relevant ways even when the genomic sequence is similar.

The surprising correlate: DNA regions around heavily-edited sites accumulate fewer point mutations than expected. The interpretation is that the editing machinery (ADAR enzymes) recognises specific flanking sequence, so any mutation that disrupts the flanking region also disrupts editing — and selection then keeps the flanking sequence still.

## The trade-off claim

If the conservation of editing-flanking sequence is real, cephalopods are paying for transcriptome plasticity in genome evolvability:

- Mutations in editing-flanking regions are removed by purifying selection because they disrupt a useful editing site.
- The genome therefore evolves more slowly in those regions than it would otherwise.
- In exchange, the *transcriptome* can vary — adapt to temperature, developmental stage, behavioural context — without waiting for a new generation.

This is a different evolutionary strategy from vertebrates, which tune protein function primarily by gene duplication and slower mutational change *(established as the editing rate; the trade-off framing is interpretively coherent but still being explored functionally)*.

## Disagreements and cautions

- **Conservation magnitude.** The constraint that editing puts on flanking sequence evolution is real but modest in many cases; the framing as a global trade-off may overstate the size of the effect.
- **Functional consequences.** That editing changes protein sequence is established. That those changes are *adaptive* (vs. neutral or noisy) is shown for a handful of channels (e.g., temperature compensation in K⁺ channels) and inferred more broadly. The general claim is mixed.
- **Other animals also edit.** A-to-I editing is universal in metazoans; cephalopods are the extreme case, not the only case.

## Questions I'd like answered

1. Does the trade-off cost cephalopods genome-level adaptation over geological time? Are cephalopods slower-evolving at the genome level than expected for their population sizes?
2. What sets the cost-benefit balance for editing vs. genomic encoding in any given gene? Why some channels and not others?
3. Are non-cephalopod species with high editing rates (some squid lineages also edit heavily) showing the same flanking-sequence conservation pattern?

## Sources

- [Liscovitch-Brauer et al. 2017] Liscovitch-Brauer, N. et al. "Trade-off between transcriptome plasticity and genome evolution in cephalopods." *Cell* 169(2):191–202. https://doi.org/10.1016/j.cell.2017.03.025

## Links

- [[octopus-cognition]] — survey hub.
- [[the-octopus-is-an-independent-second-evolution-of-mind]] — RNA editing is part of the substrate-novelty case: cephalopod neural tissue is built on protein-tuning machinery vertebrates don't use.
- [[kinetic-proofreading]] — different but related: both are biological strategies for tuning the precision/cost trade-off in molecular machinery, both spend energy for accuracy or specificity.
- [[mechanistic-interpretability]] — the general theme of *what learned plasticity looks like in different substrates*: editing is to cephalopod proteins what fine-tuning is to neural-net weights.
