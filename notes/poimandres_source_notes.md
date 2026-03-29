# Poimandres Source Notes — Passage Selection Rationale

## Source
Corpus Hermeticum Book I (Poimandres), G.R.S. Mead translation (1906, public domain)
Cross-reference: Brian P. Copenhaver, *Hermetica* (Cambridge, 1992)
Digital source: Internet Archive (archive.org) — full text

## Text Structure

The Poimandres is a single revelation dialogue, 32 sections long. Unlike the Enneads (54 treatises), the entire cosmogony is contained in ONE text, making passage selection straightforward.

### Sections Used for Schema Encoding

| Sections | Content | Schema Relevance |
|---|---|---|
| 1-3 | Vision opens, Poimandres identified as Nous | Establishes Nous as a distinct level |
| 4 | Primal Light and Darkness/Moist Nature | Source (God/Light) + pre-existing substrate (Nature) |
| 5 | The Holy Word (Logos) descends upon Nature | Logos as distinct emanation from God |
| 6-7 | God-Mind produces Demiurgos + Seven Governors | Branching: Demiurgos → Seven Governors |
| 8-11 | Cosmos takes shape, Nature produces creatures | Sensible cosmos as endpoint of Demiurgic line |
| 12-14 | Anthropos created, falls into Nature | Second branch: Anthropos as direct child of God |
| 15-17 | Union of Anthropos + Nature → mortal humanity | Material humanity as endpoint of Anthropic line |

### Sections NOT Used

| Sections | Content | Why Excluded |
|---|---|---|
| 18-19 | Divine proclamation (self-knowledge → deathlessness) | Ethical teaching, not cosmological structure |
| 20-26 | Ascent through the seven zones, stripping of vices | Return/ascent path — excluded per schema_spec.md (descent only) |
| 27-32 | Hermes becomes a preacher, concluding hymns | Narrative frame, not cosmological architecture |

## Why This Source

The Poimandres is chosen as the primary Hermetic source because:

1. **It contains the only complete Hermetic cosmogony.** Other Corpus Hermeticum texts (CH III, CH XI) touch on creation but none give the full architecture.
2. **It is the most widely studied Hermetic text.** Copenhaver, Fowden, and Bull all treat it as the foundational Hermetic cosmological document.
3. **It has clear structural parallels AND clear structural differences from Plotinus.** This makes it ideal for testing whether the encoding protocol can capture genuine topological variation.

## Translation Choice

**G.R.S. Mead (1906):** Public domain, widely available, established in the field. Known to be somewhat free in translation but structurally accurate for cosmological content.

**Alternative: Brian P. Copenhaver (1992):** More philologically precise but under copyright. Used as cross-reference for structural validation, not for direct quotation.

**Key point:** For graph encoding purposes, the choice of translation does not affect the structural architecture. The cosmological levels and their relationships are the same in every translation. What varies is the philosophical nuance — which matters for interpretation but not for topology.

## Key Source-Level Observations

### 1. Nature's Status Is Anomalous
In Plotinus, Nature is produced by Soul. In Poimandres, "Moist Nature" / Darkness appears *before* the Light acts upon it — it seems to pre-exist as a substrate. This is either:
- **Cosmological dualism** (two co-eternal principles: Light and Darkness)
- **Emanation from a deeper source** (Darkness as the "shadow" cast by Light)
- **Narrative device** (the vision shows stages, not temporal priority)

Copenhaver (1992, p. 101) notes that the Poimandres shares cosmogonic elements with Genesis, Plato's Timaeus, and Egyptian creation myths, and the status of the primordial darkness is debated.

**Encoding decision:** Encode Nature as receiving the action of Logos (edge: Logos → Nature) but NOT as emanated from God. Document the anomaly.

### 2. God/Light and Nous/Poimandres — Same or Different?
In section 6, Poimandres says "That Light is I, thy God, Mind" — identifying himself (Nous) with the Supreme Light. But in the cosmogonic sequence, God-Mind produces the Demiurgos and Anthropos, suggesting Nous is the *active aspect* of the Supreme, not a separate level.

**Encoding decision:** Encode as TWO nodes (God/Light as source, Nous as first_emanation) OR as ONE node (God-Mind as both). See encoding_decisions.md.

### 3. The Poimandres Has No Return Path in the Cosmogony
The ascent through the seven zones (sections 20-26) is a soteriological teaching, not a cosmological structure. It is NOT included in the primary graph.

---

*Written: 2026-03-28*
