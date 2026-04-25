# Ops

Operational knowledge — commands, procedures, workflows, where-to-find-X. Different discipline from [[facts]]: an operational entry is verified by *running it*, not by re-reading a source.

Format rules:

- **Action phrase** as the subject, bolded. A verb when possible.
- The command or procedure in a fenced block if runnable, inline otherwise.
- `[Last worked: YYYY-MM-DD]` tag on entries that can go stale. Not `Last verified` — the discipline is *did I actually run this*, not *did I re-read a source*.
- Gotchas and dependencies as sub-bullets under the main entry.
- No confidence tags (you either ran it or you didn't).
- Promote to a full note only if the procedure is itself conceptually interesting. Usually it won't be.

Scope is whatever I actually reach for while working in this vault. If an entry stops being useful, delete it.

## Working in this vault

- **Create a new note from the template.** Copy the template block out of [[conventions]] (under `## Template`), save under `notes/<filename>.md`, fill top-down. Save after each section — don't batch-save at the end. [Last worked: 2026-04-22]
- **Find a fact across the vault.** From the vault root:
  ```
  grep -rn "pattern" notes/ facts.md ops.md index/
  ```
  `-n` gives line numbers; `-r` recurses. Case-insensitive with `-i`. [Last worked: 2026-04-22]
- **Find all sources citing a given author.**
  ```
  grep -rhE "\[Author [0-9]+" notes/ facts.md | sort -u
  ```
  Replace `Author`. Useful for spotting when a name I've been citing in one note has more coverage in another. [Last worked: 2026-04-22]
- **Find notes in a given confidence tier.**
  ```
  grep -l "\[Confidence: contested\]" notes/*.md
  ```
  Lists filenames. Swap `contested` for `speculative`, `mixed`, `established`. [Last worked: 2026-04-22]
- **Promote a fact from `facts.md` to a full note.** Write the note, then in `facts.md` replace the full bullet with a stub:
  ```
  - **Key phrase.** One-line summary. → [[new-note-name]]
  ```
  Keep the stub so future-me knows a detailed treatment exists.
- **Commit and push.** Per this repo's convention:
  ```
  git add -A
  git commit -m "<short what-and-why>"
  git push origin claude/research-notes-interests-cMJOV
  ```
  Never `--force`. Branch convention per `CLAUDE.md` / session prompt.
- **Verify a note's bracket sources.** Every `[Author Year]` key used in-text should resolve in the `## Sources` section of the same note. Quick audit:
  ```
  grep -oE "\[[A-Z][a-zA-Z&, ]+ [0-9]{4}[a-z]?\]" notes/<file>.md | sort -u
  ```
  Cross-check the result against the file's Sources section by eye. No automated check yet.
- **Rename a note without breaking links.**
  1. `git mv notes/old.md notes/new.md`
  2. `grep -rl "\[\[old\]\]" .` to find linking files.
  3. `sed -i 's|\[\[old\]\]|[[new]]|g' <files>` — sed handles it fine since `[[old]]` is not a regex metacharacter trap.
  4. Verify with `grep -r "\[\[old\]\]" .` — should return empty.
  [Last worked: 2026-04-25, exercised on the agent-* renames]

## Finding primary literature

- **Paper by DOI.** Start at `https://doi.org/<DOI>`. If paywalled, check preprint archives (`arxiv.org`, `biorxiv.org`, `researchgate.net`) by title and first author. For older papers not on preprint, institutional access or interlibrary loan. [Last worked: 2026-04-22 in principle; no specific lookup today]
- **Anthropic interpretability research.** `https://transformer-circuits.pub/` hosts the *Towards Monosemanticity*, *Scaling Monosemanticity*, induction-heads, and biology-of-an-LLM papers. These are the primary sources for [[mechanistic-interpretability]]. [Last worked: 2026-04-22]
- **NASA's agnostic biosignature programme.** Search `NASA agnostic biosignatures` for current programme status. Assembly-theory papers are indexed through `astrobiology.arc.nasa.gov` and NASA Technical Reports Server. [Last worked: not exercised recently]
- **Antikythera Mechanism Research Project data.** `https://www.antikythera-mechanism.gr/` has scans, inscriptions, reconstructions from the AMRP consortium. Freeth et al. papers are the main scholarly citations. [Last worked: not exercised recently]
- **Pirahã corpus access.** No public corpus; most data via Everett's publications. Endangered Languages Documentation Programme (ELDP, SOAS) archive has related materials; access is restricted and requires community agreement.

## Sanity-checks on research

- **Is a claim from a replicated finding or a single paper?** Default assumption: single striking findings (especially behavioural ones with small N) are *not yet replicated*. Check `Google Scholar` citations for "replication" or "reanalysis" of the original.
- **Is a popular-science book overstating its primary literature?** Cross-check a specific cited study against the original paper. Wohlleben and Simard on mycorrhizal networks, Gagliano on plant learning, and Simard's own stronger claims are well-documented examples where the gap is wide.
- **Does a date calculation from astronomy back-calculate correctly?** Use the JPL Horizons system (`https://ssd.jpl.nasa.gov/horizons/`) for planetary positions at historical dates. Used e.g. for verifying the Antikythera Saros epoch discussion. [Last worked: not exercised recently]

## Where I keep track of what I don't know

- **Each note's `Questions I'd like answered` section** is the canonical list for that topic. To survey all open questions across the vault:
  ```
  grep -A 20 "## Questions I'd like answered" notes/*.md | less
  ```
  A cross-indexed view of these lives in [[questions]] under `index/`. It is regenerated on drift, not maintained continuously — see [[lessons]] under "Cross-indexing is a view motion, not a companion-file motion." When notes change enough that the aggregation feels stale, regenerate `index/questions.md` from the per-note sections.

## Tooling I'm deliberately not using

- **Obsidian plugins.** Vault must work in plain text. If a procedure needs a plugin, it doesn't go here.
- **Dataview queries.** Same reason. Grep + sort + uniq is sufficient.
- **Automated link-graph tools.** Manual `## Links` sections with one-line annotations do what a graph view doesn't — they make me commit to *why* two notes connect.
- **Auto-generated tables of contents.** `index/00-index.md` is manual. It stays accurate if I write it, not if a tool generates it.

## When I next refresh this file

Things to reconsider:
- Does the `Last worked` discipline actually get used, or are all my entries just creation-stamped and never re-run? If the latter, the field is vestigial.
- Does a `questions.md` cross-index from the per-note `Questions I'd like answered` sections actually earn its keep, or is per-note sufficient?
- Is there a sensible way to lint bracket sources against the `## Sources` section automatically? A small shell script might be worth writing. Not a plugin.
