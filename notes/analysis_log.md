# Analysis Log — WP 1.1 Emanation-Schema Topology

Running log of all decisions, findings, and observations during the analysis.

---

## 2026-03-28 — Project Initialized

- WP 1.1 directory structure created
- Schema extraction specification written (schema_spec.md)
- Sources manifest compiled for all 6 traditions (sources_manifest.md)
- Coding rules established (coding_rules.md)
- Python module plan defined (scripts/README.md)
- Week 1 checklist created

**Status:** Scaffold complete. Ready to begin text acquisition and schema encoding.

**Next action:** Acquire digital texts for Tradition 3 (Plotinian) first — cleanest schema, best test case for the encoding pipeline.

---

## 2026-03-28 — Plotinus Pilot Encoding Complete (v1.0)

### Source Processing
- Located Plotinus Enneads PDF: `Research/plotinustheenneaMackenna,Stephen.pdf` (702pp, MacKenna translation)
- OCR quality: fair — readable but with Greek character artifacts
- Identified 4 schema-relevant treatises out of 54 total:
  - V.1 (Three Initial Hypostases) — PDF pp. 429-441 — **primary source**
  - V.2 (Origin and Order of Beings) — PDF pp. 440-442
  - III.8 (Nature, Contemplation, and the One) — PDF pp. 299-310
  - VI.9 (On the Good, or the One) — PDF pp. 675-685
- Created `data/raw_texts/plotinus_excerpt.md` with key passages and source references
- Created `notes/plotinus_source_notes.md` explaining selection rationale

### Schema Encoding
- **Primary encoding: 5 nodes, 4 edges** (linear chain)
  - The One (source) → Nous (first_emanation) → Psyche (soul) → Nature (intermediary) → Matter (matter)
- Created `data/schemas/plotinian.json` (machine-readable, fully attributed)
- Created `notes/plotinus_encoding_rationale.md` (human-readable rationale)

### Key Findings
1. The three hypostases (One, Nous, Soul) are completely unambiguous — every scholar agrees
2. Nature (Physis) is the main disputed node — included based on III.8 but documented as alternative
3. Matter's ontological status is debated but its structural position is clear — included as terminus
4. The Plotinian schema is **strictly linear** (no branching) — this may be a distinguishing topological feature
5. The emanation mechanism has a distinctive two-phase structure (overflow + reversion) not shared by all traditions
6. Edge types: 3x `emanation`, 1x `reflection` (Nature → Matter)

### Encoding Decisions Logged
- 4 entries added to `encoding_decisions.md`:
  1. Nature as separate node (sensitivity analysis: YES)
  2. World Soul vs. individual Soul (sensitivity analysis: YES, lower priority)
  3. Nature-to-Matter edge type (no sensitivity needed)
  4. Matter as node despite privation status (no sensitivity needed)

### Alternative Encodings Documented
- 4-node encoding (without Nature): documented in JSON
- 6-node encoding (with World Soul): documented in JSON

### Validation
- DAG property: confirmed
- Single root: confirmed (one)
- All connected: confirmed
- Node count: 5 (within 4-20 bounds)
- All required attributes present: confirmed
- All edges labeled: confirmed
- Scholarly verification: cross-referenced against Gerson (1994), O'Meara (1993), Armstrong (1940)

**Status:** Pilot encoding complete. Ready for pipeline testing once `encode_schemas.py` is built.

**Observations for cross-traditional comparison (DO NOT ACT ON YET):**
- The strict linearity of the Plotinian schema (no branching) will be interesting to compare against Gnostic and Kabbalistic schemas, which typically branch
- The Nature node may or may not have equivalents in other traditions — this is an open question
- The `reflection` edge type at the bottom is distinctive — most other traditions use `emanation` or `fragmentation` for the matter-production step

**Next action:** Encode Tradition 6 (Hermetic/Poimandres) as the second pilot case. This tradition has a slightly more complex schema (includes Logos, Seven Governors, and Anthropos) and will test whether the encoding protocol handles branching.

---

## 2026-03-28 — Hermetic Poimandres Encoding Complete (v1.0)

### Source Processing
- No local Poimandres PDF found. Used G.R.S. Mead translation (1906, public domain) via Internet Archive.
- Cross-referenced against Copenhaver (1992) structural analysis and Bull (2018) for scholarly validation.
- Created `data/raw_texts/poimandres_excerpt.md` — key passages from CH I sections 1-19.
- Created `notes/poimandres_source_notes.md` — selection rationale.

### Schema Encoding
- **Primary encoding: 8 nodes, 7 edges** (branching tree, max branching factor 3)
  - God-Mind (source) → [Logos, Demiurgos, Anthropos] → [Nature, Seven Governors, Mortal Humanity] → Sensible Cosmos
- Created `data/schemas/hermetic.json` (machine-readable, fully attributed)
- Created `notes/poimandres_encoding_rationale.md` (node-by-node rationale)

### Key Findings
1. **FIRST BRANCHING SCHEMA:** The Poimandres branches at level 0 with branching factor 3. This is a completely different topology from Plotinus's linear chain.
2. **No Soul hypostasis:** The Poimandres has no `soul` node equivalent to Plotinus's Psyche. God-Mind and Demiurgos perform the cosmic-animating functions that Plotinus assigns to Soul.
3. **Positive Demiurge:** The Hermetic Demiurgos is a positive creative agent (unlike Gnostic Demiurges). Edge type is `creation` (not `fragmentation`).
4. **Anthropos falls by choice:** The Primal Man's descent is a `fragmentation` event driven by desire/love, not by error.
5. **Nature pre-exists:** Unlike Plotinus where Nature is emanated from Soul, Hermetic Nature appears as a primordial substrate transformed by the Logos.

### Encoding Decisions Logged
- 4 new entries added (Entries 5-8):
  5. God/Nous as single vs. separate nodes (sensitivity: YES)
  6. Nature as pre-existing vs. emanated (sensitivity: YES)
  7. Anthropos at level 1 (no sensitivity needed in primary)
  8. Anthropos-to-Humanity edge as fragmentation (no sensitivity needed)

### Pilot Comparison
- Created `notes/pilot_comparison_plotinus_poimandres.md`
- Key contrast: Linear chain (Plotinus, depth 4) vs. Branching tree (Poimandres, depth 3)
- Matching functional roles: 2 clear (source, matter), 1 partial (first_emanation), 1 same-name-different-position (Nature)
- 4 Poimandres nodes have no Plotinian equivalent; 1 Plotinus node (Soul) has no Hermetic equivalent
- The encoding protocol successfully handles branching structures.

### Validation
- All checks pass: DAG, single root, connected, bounds, attributes, edge labels.

**Status:** Two pilot schemas complete. The encoding protocol works for both linear and branching architectures. Ready for the remaining four traditions.

**Next actions:**
1. Encode Tradition 1 (Valentinian Gnostic — Apocryphon of John) — expected to be the most complex schema
2. Begin building `encode_schemas.py` so both pilot schemas can be validated programmatically
3. User has offered to identify source texts from the Research folder — texts needed: Apocryphon of John, Chaldean Oracles, Sefer Yetzirah/Zohar, Corpus Hermeticum (if available locally)

---

## 2026-03-28 — Valentinian Gnostic (Apocryphon of John) Encoding Complete (v1.0)

### Source Processing
- Located Apocryphon of John in `Research/the nag hammadi library.pdf` — pp. 120-136 of 566.
- Wisse translation (long version, NHC II,1). OCR quality: good.
- Cosmogony concentrated in pp. 122-127 (NHC II 2,26-12,25). Body-part catalogue and salvation narrative excluded.
- Note: text is technically Sethian, not Valentinian. Label maintained per roadmap for Tradition 1 slot.

### Schema Encoding
- **Primary encoding: 9 nodes, 8 edges** (deep tree with fragmentation pivot)
- Deepest schema so far: depth 7 (vs. Plotinus 4, Poimandres 3)
- Key structural feature: **Sophia pivot** at level 4 separates ordered emanation (above) from disordered creation (below)
- Edge type pattern: emanation (levels 0-3) → fragmentation (levels 3-5) → creation (levels 5-7)

### Three-Schema Topology Comparison

| | Plotinus | Poimandres | Apocryphon |
|---|---|---|---|
| Shape | Linear chain | Wide shallow tree | Deep tree with pivot |
| Nodes | 5 | 8 | 9 |
| Depth | 4 | 3 | 7 |
| Max branch | 1 | 3 | 2 |
| Has `source` | yes | yes | yes |
| Has `first_emanation` | yes | yes | yes |
| Has `soul` | yes | no | no |
| Has `demiurge` | no | yes (positive) | yes (negative) |
| Has `fallen` | no | no | yes (Sophia) |
| Fragmentation edges | 0 | 1 | 2 |

**Key observation:** Three traditions, three distinct topologies. No two schemas are structurally identical. The formal isomorphism analysis will determine whether the shared features (source → intermediaries → matter) outweigh the structural differences.

### Encoding Decisions Logged
- 3 new entries (Entries 9-11): Sophia as separate node, tradition label, archon granularity

### Source Texts Confirmed Available
All 6 traditions now have confirmed source texts in the Research folder:
- Plotinus: `plotinustheenneaMackenna,Stephen.pdf` — ENCODED
- Hermetic: `Corpus Hermeticum.txt` — ENCODED
- Gnostic: `the nag hammadi library.pdf` — ENCODED
- Chaldean: `Chaldean Oracles_djvu.txt` — READY
- Kabbalistic: `Sepher Yetzirah_djvu.txt` + `Zohar selections.pdf` — READY
- Sethian: `the nag hammadi library.pdf` (Trimorphic Protennoia) — READY

**Status:** 3 of 6 schemas complete. 3 remaining (Chaldean, Kabbalistic, Sethian). All source texts confirmed available. Ready to continue encoding or switch to pipeline development.

**Next action:** Encode Chaldean Oracles (text file — easiest remaining source). Then Lurianic Kabbalah. Then Sethian Gnostic.

---

## 2026-03-28 — Chaldean Oracles Encoding Complete (v1.0)

### Source Processing
- Full text available: `Research/Chaldean Oracles_djvu.txt` (869 lines, plain text)
- OCR quality: good — text format, minimal artifacts
- Schema extracted from two sources within the text:
  1. Introduction's "CHALDAEAN SCHEME" diagram (lines 139-199) — explicit structural map
  2. Oracle fragments 1-38 (lines 576-862) — textual warrant for node roles and edges
- Cross-referenced against Majercik (1989), Johnston (1990), Lewy (1956), Shaw (1995)
- Created `data/raw_texts/chaldean_excerpt.md` with key oracle fragments and structural commentary
- Created `notes/chaldean_source_notes.md` explaining selection rationale

### Schema Encoding
- **Primary encoding: 6 nodes, 5 edges** (linear chain, depth 5)
  - Father → Hecate (World-Soul) → Second Mind → Iynges/Admins → Hypezokos → Earth-Matter
- Created `data/schemas/chaldean.json` (machine-readable, fully attributed)
- Created `notes/chaldean_encoding_rationale.md` (node-by-node rationale)

### Key Findings
1. **DOUBLE-DEMIURGE STRUCTURE:** The most distinctive Chaldean feature. The Second Mind (level 2) creates the intelligible/empyrean world; Hypezokos / Flower of Fire (level 4) fabricates the material world. No other tradition in the corpus has this two-stage demiurgic architecture.
2. **Second linear chain:** Chaldean schema is linear (depth 5, max branching = 1) — same topology family as Plotinus but deeper and with different functional roles.
3. **Hecate as World-Soul:** The mediating principle at level 1, analogous to Plotinian Psyche but more explicitly mythologized and theurgically active.
4. **Triadic law:** "In every World shineth the Triad, over which the Monad ruleth." The system is explicitly organized around triads — potential relevance to topology analysis.
5. **Fragmentary source:** Unlike systematic treatises, the Chaldean Oracles are preserved fragments. The schema is reconstructed from structural diagrams + oracle texts + secondary scholarship. Higher interpretive uncertainty than Plotinus or Apocryphon.

### Encoding Decisions Logged
- 3 new entries (Entries 12-14):
  12. Father + First Mind as single node (sensitivity: YES)
  13. Hecate as separate node (sensitivity: YES)
  14. Hypezokos as separate demiurge (no sensitivity needed)

### Four-Schema Topology Comparison

| | Plotinus | Poimandres | Apocryphon | Chaldean |
|---|---|---|---|---|
| Shape | Linear chain | Wide shallow tree | Deep tree with pivot | Linear chain |
| Nodes | 5 | 8 | 9 | 6 |
| Depth | 4 | 3 | 7 | 5 |
| Max branch | 1 | 3 | 2 | 1 |
| Has `source` | yes | yes | yes | yes |
| Has `soul` | yes | no | no | yes (Hecate) |
| Has `demiurge` | no | yes (positive) | yes (negative) | yes (double) |
| Has `fallen` | no | no | yes (Sophia) | no |
| Fragmentation edges | 0 | 1 | 2 | 0 |
| Distinctive feature | Uniform emanation | Triple root branch | Fragmentation cascade | Double demiurge |

**Key observation:** Two linear chains (Plotinus, Chaldean) and two branching trees (Poimandres, Apocryphon). Linear chains share topology family but differ completely in functional role distribution. The branching systems differ in both shape and edge type patterns.

### Validation
- DAG property: confirmed
- Single root: confirmed (father)
- All connected: confirmed
- Node count: 6 (within 4-20 bounds)
- All required attributes present: confirmed
- All edges labeled: confirmed
- Scholarly verification: cross-referenced against Majercik (1989), Johnston (1990), Lewy (1956), Shaw (1995)

**Status:** 4 of 6 schemas complete. 2 remaining (Lurianic Kabbalistic, Sethian Gnostic).

**Next action:** Encode Lurianic Kabbalah from `Sepher Yetzirah_djvu.txt` + `Zohar selections.pdf`. Then Sethian Gnostic (Trimorphic Protennoia) from Nag Hammadi.

---

## 2026-03-28 — Lurianic Kabbalistic Encoding Complete (v1.0)

### Source Processing
- Sepher Yetzirah: `Research/Sepher Yetzirah_djvu.txt` (885 lines) — used for the 10 Sephiroth structural principle
- Zohar selections PDF: `Research/Zohar selections.pdf` (276 pages) — unusable for schema (compiler explicitly excluded Sefirot/emanation doctrine; confirmed by text search)
- Schema reconstructed from Sepher Yetzirah + Scholem (1941, 1974) + Fine (2003)
- Created `data/raw_texts/kabbalistic_excerpt.md` with key passages and scholarly citations
- Created `notes/kabbalistic_source_notes.md` explaining source assessment

### Schema Encoding
- **Primary encoding: 7 nodes, 6 edges** (linear chain with two process nodes)
  - Ain Sof → Tzimtzum → Adam Kadmon → Sefirot → Shevirat HaKelim → Lower Worlds → Malkuth
- Created `data/schemas/lurianic_kabbalistic.json` (machine-readable, fully attributed)
- Created `notes/kabbalistic_encoding_rationale.md` (node-by-node rationale)

### Key Findings
1. **FIRST `contraction` EDGE IN CORPUS:** The Ain Sof → Tzimtzum edge uses the `contraction` edge type, the only use in all six traditions. All other traditions model creation as outward overflow; the Lurianic system uniquely models it as inward withdrawal.
2. **FIRST PROCESS NODES:** Tzimtzum and Shevirat HaKelim are `process` functional role nodes — not ontological levels but cosmological events. No other tradition has process nodes.
3. **SHEVIRAT-SOPHIA PARALLEL:** The Shevirat HaKelim (vessel-shattering) is structurally analogous to Sophia's fall (Apocryphon): both are fragmentation events in the middle of ordered emanation that produce the lower worlds from scattered fragments. Different etiology (structural failure vs. unauthorized volitional act) but same structural position.
4. **ZOHAR PDF LIMITATION:** The local Zohar PDF explicitly excludes Sefirot/emanation doctrine. This is a source gap — documented in source notes. The encoding is grounded in SY + scholarship (standard approach for traditions without directly accessible primary texts).

### Encoding Decisions Logged
- 3 new entries (Entries 15-17):
  15. Tzimtzum as node (no sensitivity needed)
  16. Ten Sefirot as collective (sensitivity: YES — full Tree of Life alternative high-priority)
  17. Shevirat as process node (no sensitivity needed)

### Five-Schema Topology Comparison

| | Plotinus | Poimandres | Apocryphon | Chaldean | Kabbalah |
|---|---|---|---|---|---|
| Shape | Linear | Wide tree | Deep tree | Linear | Linear + events |
| Nodes | 5 | 8 | 9 | 6 | 7 |
| Depth | 4 | 3 | 7 | 5 | 6 |
| Max branch | 1 | 3 | 2 | 1 | 1 |
| Process nodes | 0 | 0 | 0 | 0 | **2** |
| `contraction` edges | 0 | 0 | 0 | 0 | **1** |
| `fragmentation` edges | 0 | 1 | 2 | 0 | 1 |
| Distinctive | Uniform emanation | Triple root | Sophia pivot | Double demiurge | **Double process + contraction** |

**Status:** 5 of 6 schemas complete. 1 remaining: Sethian Gnostic (Trimorphic Protennoia).

**Next action:** Locate Trimorphic Protennoia in `the nag hammadi library.pdf` by page-range search, then encode.

---

## 2026-03-28 — Sethian Gnostic (Trimorphic Protennoia) Encoding Complete (v1.0)

### Source Processing
- Located Trimorphic Protennoia in `Research/the nag hammadi library.pdf` — PDF pages 527-538 (of 566)
- NHC XIII,1 (35,1-50,24), trans. John D. Turner
- OCR quality: good — readable with minor artifacts
- Cosmological content: pages 531-532 (NHC XIII 35,1-37,7). Three salvific descents (pp. 532-538) excluded per schema_spec.md
- Created `data/raw_texts/sethian_excerpt.md` with key passages and structural comparison table
- Created `notes/sethian_source_notes.md` explaining selection rationale

### Schema Encoding
- **Primary encoding: 8 nodes, 7 edges** (deep linear chain, depth 7)
  - Invisible Spirit → Protennoia/Barbelo → Autogenes → Four Luminaries → Sophia/Epinoia → Yaltabaoth → Archons → Material World
- Created `data/schemas/sethian_gnostic.json` (machine-readable, fully attributed)
- Created `notes/sethian_encoding_rationale.md` (node-by-node rationale, full six-tradition comparison table)

### Key Findings
1. **SHARED SETHIAN STRUCTURE CONFIRMED:** The Trimorphic Protennoia and Apocryphon of John share the same cosmological framework (same 7 of 8 nodes, same depth, same edge-type pattern). This confirms a consistent Sethian school topology: deep tree with fragmentation pivot at the Sophia level.
2. **PROTENNOIA'S TRIADIC NATURE:** Protennoia = Barbelo = Voice = Speech = Word. The first emanation is triadic in a way not seen in any other tradition. Encoded as one node with attribute, not structural branching.
3. **SOPHIA AS VICTIM:** TP shifts Sophia from agent-of-error (Apocryphon) to innocent victim (usurped by Yaltabaoth). Same structural position, inverted moral valence. Significant for paper discussion of intra-school semantic variation.
4. **ELELETH TRIGGER:** Yaltabaoth appears when Eleleth proclaims "I am King!" — different mechanism but same topology. The Sophia pivot still separates ordered Pleroma from disordered creation.

### Encoding Decisions Logged
- 2 new entries (Entries 18-19):
  18. Protennoia's triadic nature as single node (no sensitivity needed)
  19. Yaltabaoth origin / Sophia's structural position (no sensitivity needed)

---

## 2026-03-28 — ALL SIX SCHEMAS COMPLETE

### Final Topology Summary

| Tradition | Shape | Nodes | Depth | Max Branch | Distinctive Feature |
|---|---|---|---|---|---|
| Plotinus | Linear chain | 5 | 4 | 1 | Uniform emanation, no demiurge |
| Poimandres (Hermetic) | Wide shallow tree | 8 | 3 | 3 | Triple root branch, positive demiurge |
| Apocryphon (Valentinian/Gnostic) | Deep tree + pivot | 9 | 7 | 2 | Sophia pivot (fragmentation cascade) |
| Chaldean | Linear chain | 6 | 5 | 1 | Double demiurge (intelligible + material) |
| Lurianic Kabbalistic | Linear + process events | 7 | 6 | 1 | Tzimtzum (contraction) + Shevirat (shattering) |
| Sethian (Trimorphic Protennoia) | Deep linear | 8 | 7 | 1 | Triadic first emanation, Sophia as victim |

### Topology Families
1. **Linear chains** (depth 4-6, branching = 1): Plotinus, Chaldean, Kabbalah
2. **Branching trees** (depth 3-7, branching > 1): Poimandres, Apocryphon
3. **Deep linear** (depth 7, branching = 1, fragmentation cascade): Sethian TP

Note: Sethian TP has the same edge-type pattern as Apocryphon (eman×3 → frag×2 → create×2) but a linear topology. This creates an interesting case for the isomorphism analysis.

### Cross-Cutting Structural Features
| Feature | Traditions |
|---|---|
| Has `soul` functional role | Plotinus, Chaldean |
| Has `demiurge` functional role | Poimandres, Apocryphon, Chaldean, Kabbalistic, Sethian |
| Has `fallen` functional role | Apocryphon, Sethian |
| Uses `fragmentation` edges | Poimandres (×1), Apocryphon (×2), Kabbalistic (×1), Sethian (×2) |
| Uses `contraction` edges | Kabbalistic only (×1) |
| Has `process` nodes | Kabbalistic only (×2) |
| Has positive demiurge | Poimandres, Chaldean |
| Has negative demiurge | Apocryphon, Sethian |

### Status
All 6 schemas encoded and validated. Ready to build the analysis pipeline:
1. `encode_schemas.py` — load all 6 JSONs into NetworkX DiGraphs
2. `compute_invariants.py` — degree distribution, diameter, betweenness
3. `isomorphism_tests.py` — VF2 / Weisfeiler-Leman across all tradition pairs
4. `generate_controls.py` — 1,000 randomized DAGs for statistical baseline
5. `statistical_comparison.py` — permutation tests, Mann-Whitney U, Cohen's d
6. `visualize.py` — figures for the paper

**Next action:** Build `encode_schemas.py` — the foundation module that loads all 6 schemas and validates against the DAG contract.

---

<!-- Future entries go here -->
