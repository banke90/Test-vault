# Finnish's "15 cases" are mostly postpositions fused to the noun, not case in the Latin sense

> Finnish inflection is agglutinative — most of the "cases" are regular suffix-slots that do the work English prepositions do, so the scary count overstates the cognitive load.

[Confidence: mixed]
[Last verified: 2026-04-22]
[Kind: claim]

## TL;DR

Finnish is usually advertised as having 15 noun cases, which makes it sound as inflectionally terrifying as Latin or Russian. It isn't, because Finnish is **agglutinative**: case suffixes are stacked in clean, mostly-regular slots and many of them do the work English prepositions do — several cases are historically fossilised postpositions. The six locative cases in particular form a 2×3 spatial/directional matrix that compresses into a single grid. Where Finnish actually is hard: (i) the partitive, which is really an aspect/telicity marker rather than a case; (ii) consonant gradation (k/p/t alternations), which is morphologically conditioned and full of opaque exceptions; (iii) stem variation across declension classes. The case count is the wrong thing to be scared of.

## What a "case" is doing in Finnish

Case endings in Finnish mark a noun's relationship to the rest of the clause — the role English does with a mix of word order, prepositions, and inflection. Finnish has essentially no prepositions; instead it has **postpositions** and **case suffixes**, and many of the case suffixes are historically fossilised postpositions that were glued to the noun stem and regularised [Wikipedia-cases].

Two properties matter and are worth internalising before counting cases:

1. **Agglutination.** Suffixes stack in predictable slots with minimal fusion. `talo` = house, `talossa` = in a house (inessive, *-ssa*), `talossani` = in my house (+ possessive *-ni*), `talossanikin` = in my house too (+ clitic *-kin*). Each morpheme keeps a recognisable shape (modulo vowel harmony and consonant gradation). This is *not* like Latin, where `domus / domi / domo / domum` fuse number, case, and declension class into an opaque ending.

2. **The count depends on where you draw the line between suffix, clitic, and postposition.** "15 cases" is the consensus number, but some sources count 14 or 16, and a handful of the 15 are essentially dead outside fixed expressions. The impressive number comes from counting slots that other languages happen to spell with a separate word.

The standard taxonomy *(established)*:

- **Grammatical cases (4):** nominative, genitive, partitive, accusative. These mark core syntactic roles — subject, object, possessor — and the partitive in particular carries heavy semantic load (incompleteness, negation, mass-noun objects).
- **Locative cases (6):** inessive, elative, illative, adessive, ablative, allative. Discussed below — this is where the "cases = prepositions" claim lives most cleanly.
- **Essive cases (2):** essive (*-na*, "as a / in the state of"), translative (*-ksi*, "becoming / into a state of").
- **"Marginal" cases (3):** instructive (*-n*, "by means of"), abessive (*-tta*, "without"), comitative (*-ne-* plus possessive suffix, "along with"). These are largely confined to fixed expressions, written/formal registers, and fossilised adverbs. In everyday speech Finns use postpositions (`ilman` + partitive for "without") or other cases instead [Wikipedia-grammar].

## The locative six: a preposition system in disguise

The six locative cases are where the "Finnish has 15 cases!" claim is most misleading. They form a clean 2×3 matrix — a spatial feature crossed with a directional feature. Once you see the matrix, they stop feeling like 6 unrelated inflections and start feeling like a small closed-class preposition system that happens to be spelled as suffixes [venla-locative; Wikipedia-cases].

The matrix (using `talo` = house, `katto` = roof):

|           | at / in (static)      | from (source)           | to / into (goal)        |
|-----------|-----------------------|-------------------------|-------------------------|
| **Inside** (internal, *-s-*) | Inessive `talossa` (in the house) | Elative `talosta` (out of the house) | Illative `taloon` (into the house) |
| **Outside / on** (external, *-l-*) | Adessive `katolla` (on the roof) | Ablative `katolta` (off the roof) | Allative `katolle` (onto the roof) |

The morphology itself encodes the grid:

- The consonant picks **inside vs outside/on**: *-s-* for internal, *-l-* for external.
- The vowel/ending picks **direction**: *-ssa/-lla* static ("in/at"), *-sta/-lta* source ("from"), *-Vn/-lle* goal ("into/onto").

So `-sta` is roughly "out of" (internal + source) and `-lta` is roughly "off of" (external + source). A learner memorising six "cases" is actually memorising a 2-bit spatial distinction plus a 3-way directional one, which is less work than the label suggests *(my guess, but the structure is clearly compositional)*.

The external set does extra duty Finnish doesn't have a separate case for:

- **Possession:** Finnish has no verb "to have". `Minulla on koira` — literally "at-me is dog" — uses the adessive to express possession. "I have a dog" is structurally "a dog is on/at me."
- **Instrument / means:** `junalla` = "by train" (adessive).
- **Recipient / indirect object:** `annan sinulle kirjan` = "I give to-you a book" (allative = dative-like).

This overloading of the external cases for possession, instrument, and recipient is the bit where English speakers trip, not the spatial meanings themselves *(speculative but matches common learner reports)*.

## Where Finnish is actually hard

If the case count overstates difficulty, what *is* actually hard? Three things, roughly in order of how much pain they cause English-speaking learners:

**1. The partitive is an aspect marker pretending to be a case.** The partitive suffix (*-a/-ä*, *-ta/-tä*, *-tta/-ttä*) marks the direct object — but *which* direct objects take it depends on telicity, the completion status of the action [Kiparsky 1998]. Contrast:

- `Luin kirjan` (accusative) — "I read the book" (and finished it).
- `Luin kirjaa` (partitive) — "I was reading the/a book" (progressive / incomplete).
- `Join vettä` (partitive) — "I drank (some) water."
- `Join veden` (accusative) — "I drank the water" (all of it).

Partitive also appears with negation (`en nähnyt lasta` "I didn't see the child"), mass nouns, indefinite quantities, and a closed class of "partitive verbs" (`rakastaa` "to love", `odottaa` "to wait for", `auttaa` "to help") which just demand partitive objects regardless of completion. English marks none of this morphologically; you have to learn to *see* the aspectual distinction before you can mark it *(established, this is the standard account since Kiparsky)*.

**2. Consonant gradation (*astevaihtelu*).** The stops /k, p, t/ alternate between "strong" and "weak" grades depending on the phonological shape of the syllable [Wikipedia-gradation]. Typical patterns:

- `kk → k`: `kukka` (flower, nom.) → `kukan` (gen.)
- `pp → p`: `kauppa` (shop) → `kaupan`
- `tt → t`: `matto` (rug) → `maton`
- `k → ∅`: `jalka` (leg) → `jalan`
- `p → v`: `leipä` (bread) → `leivän`
- `t → d`: `katu` (street) → `kadun`
- `nt → nn`: `ranta` (shore) → `rannan`
- `mp → mm`: `kampa` (comb) → `kamman`

Two things make this hard. First, it interacts with nearly every case and verb form, so you can't avoid it. Second, the original phonological trigger — whether the following syllable was open or closed — has been eroded by later sound changes, so the rule is now **morphologically conditioned**: you memorise which form each suffix selects rather than deriving it from phonology [Wikipedia-gradation]. That's the "irregularities and exceptions" complaint learners have.

**3. Vowel harmony and stem variation.** Every suffix has front (*-ssä, -llä, -ksi* with *ä/ö/y*) and back (*-ssa, -lla, -ksi* with *a/o/u*) variants that must match the stem's vowels. That part is easy. The harder part is that Finnish nouns belong to dozens of **declension classes** with different stem shapes — `vesi` (water) has oblique stem `vede-` (partitive `vettä`, inessive `vedessä`); `käsi` (hand) has oblique stem `käde-`; `mies` (man) has oblique stem `miehe-`. A learner needs both the nominative and at least one oblique form to decline a noun correctly [Wikipedia-grammar].

Put together: the difficulty isn't the *number* of cases. It's that every case form requires you to simultaneously apply (a) the right suffix, (b) the right grade, (c) the right stem variant, and (d) the right aspectual/semantic choice between cases that overlap in meaning. The surface "15 cases" is a red herring; the real friction is the multi-axis bookkeeping.

## Disagreements and cautions

- **"Cases are just prepositions in disguise" is a teaching heuristic, not a rigorous linguistic claim.** Typologists distinguish case (morphological, obligatory, participates in agreement/government) from adpositions (separate phonological words with their own syntax). Finnish locative suffixes pass the morphological case test — they undergo vowel harmony, trigger consonant gradation, fuse with possessive suffixes, etc. Saying they "are postpositions" is a useful way to defuse the 15-case bogeyman for English speakers but it elides real structural facts *(contested — depends on how you weigh diachrony vs synchrony)*.
- **The count itself is a convention.** Some treatments list 14 cases (folding the accusative into nominative/genitive because it has no unique suffix for most nouns), some list 16 or 17 (promoting marginal forms like the prolative *-tse* "by way of" or lative). Claiming a definite number is always claiming a definite taxonomy [Wikipedia-cases].
- **The accusative is a mess.** Finnish grammars disagree on whether there's a distinct accusative case at all. For singular pronouns (`minut`, `sinut`) there's a dedicated *-t* ending. For nouns, the "accusative" is syncretic with either the genitive (*-n*) or the nominative depending on the clause type, which is why Kiparsky [1998] argues against treating it as a separate case and reanalyses the system [Kiparsky 1998].
- **Colloquial Finnish (*puhekieli*) drops and simplifies a lot.** Written standard forms don't all survive in speech. The comitative and instructive are essentially dead in ordinary conversation. Possessive suffixes are often replaced by possessive pronouns. A learner chasing the full paradigm can end up sounding like a 19th-century bureaucrat.

## Questions I'd like answered

1. How much faster do English speakers acquire Finnish locatives once shown the 2×3 matrix vs. taught six cases sequentially? Is there classroom evidence, or just anecdote?
2. Are the "marginal" cases (instructive, abessive, comitative) genuinely dying, or are they stable in specific registers (legal, literary)? A corpus frequency comparison over the last century would settle it.
3. Is consonant gradation productive for new loanwords? If a Finn borrows `blogi` and inflects it, do they apply gradation (`blogin`?) or not? That's the cleanest test of whether the rule is synchronically alive or just inherited paradigms.
4. How close is the Estonian locative system to Finnish's, and where do they diverge? Estonian is said to have lost some locative distinctions — what does that look like mechanically?
5. Does the partitive/accusative distinction correlate with *verbal* aspect distinctions in languages that have them (Russian perfective/imperfective)? Are Finnish learners who speak Slavic languages better at the partitive than English speakers?
6. How much of Finnish "difficulty" for English speakers is actually the Uralic/Indo-European distance, vs. genuine complexity? Hungarian has 18 cases and is also Uralic — comparing learner outcomes would help isolate the cause.

## Sources

- [Wikipedia-cases] "Finnish noun cases", Wikipedia. https://en.wikipedia.org/wiki/Finnish_noun_cases
- [Wikipedia-grammar] "Finnish grammar", Wikipedia. https://en.wikipedia.org/wiki/Finnish_grammar
- [Wikipedia-gradation] "Finnish consonant gradation", Wikipedia. https://en.wikipedia.org/wiki/Finnish_consonant_gradation
- [venla-locative] "Finnish grammar: Location cases", venla.info. https://venla.info/grammar-location-cases.html
- [Kiparsky 1998] Paul Kiparsky, "Partitive Case and Aspect", Stanford. https://web.stanford.edu/~kiparsky/Papers/wuppertal.pdf — the canonical analysis of the Finnish partitive as an aspect/telicity marker rather than a pure case.
- [Kiparsky-structural] Paul Kiparsky, "Structural Case in Finnish", Stanford. https://web.stanford.edu/~kiparsky/Papers/finn.pdf — argues the Finnish "accusative" is not a distinct case and reanalyses grammatical cases.
- [uusikielemme-partitive] "The Partitive Case — Partitiivi", Uusi kielemme. https://uusikielemme.fi/finnish-grammar/finnish-cases/grammatical-cases/the-partitive-case-partitiivi
- [Korpela] Jukka Korpela, "The roles of cases in Finnish", Handbook of Finnish. https://jkorpela.fi/finnish/cases.html (403 on direct fetch during research, cited from search metadata)

## Links

- `octopus-cognition.md` — contrast the "how many X does it have?" framing: counting arms/cases alone is misleading; what matters is the internal structure those units participate in.
- `collective-intelligence.md` — a language's case system is itself a piece of accumulated collective cognition; the 6-locative grid is a compressed schema learned by every speaker.
- `mechanistic-interpretability.md` — agglutinative morphology gives cleaner "circuits" (separable morphemes) than fusional morphology, which is arguably what makes Finnish easier to parse mechanically than its case count suggests; compare to decomposing neural network features.
