# Apocryphon of John Source Notes

## Source
Apocryphon of John (long version, NHC II,1), trans. Frederik Wisse, in *The Nag Hammadi Library in English*, ed. James M. Robinson (HarperCollins, 1990)
PDF: `Research/the nag hammadi library.pdf` — pages 120-136 (of 566)

## Text Classification Note

The Apocryphon of John is technically a **Sethian** Gnostic text, not Valentinian. It predates Valentinus (2nd century CE) and belongs to the "Barbeloite" or "Sethian" tradition identified by John D. Turner. However, it shares key structural features with Valentinian systems (Sophia's fall, the Demiurge's ignorance, the Pleroma structure), and the WP 1.1 sources_manifest originally listed it under "Valentinian Gnostic" as Tradition 1.

**For encoding purposes:** The tradition label in the JSON is `valentinian_gnostic` for consistency with the roadmap. A future refinement could relabel this as `sethian_gnostic` and encode a separate Valentinian system from Irenaeus' report or the Gospel of Truth. This is noted but not acted upon for the pilot.

## Pages Used

| PDF Pages | NHC Reference | Content | Schema Relevance |
|---|---|---|---|
| 122-123 | II 2,26-4,26 | Negative theology of the Invisible Spirit | Source node (Monad) |
| 123-124 | II 4,26-6,10 | Barbelo's emergence + pentad of aeons | First emanation node |
| 124-125 | II 6,10-8,28 | Autogenes/Christ, Mind, Word | Intellect node |
| 125 | II 7,30-8,28 | Four Luminaries + 12 aeons | Collective intermediary |
| 125-126 | II 8,28-9,14 | Adamas (Perfect Man), Seth, Seed of Seth | Parallel intermediary |
| 126 | II 9,25-10,19 | Sophia's error and Yaltabaoth's birth | Fragmentation event |
| 126-127 | II 10,19-12,25 | Yaltabaoth creates archons + cosmos | Demiurge + Archons |
| 128-133 | II 13-20 | Material humanity created | Matter/endpoint |

## Pages NOT Used

| PDF Pages | Content | Why Excluded |
|---|---|---|
| 120-121 | Introduction (Wisse) | Scholarly apparatus, not primary text |
| 130-131 | Body-part catalogue (365 angels create the body) | Granularity Rule: detail below the schema level |
| 133-136 | Salvation narrative, counter-spirit, paradise | Soteriological, not cosmogonic |

## Key Observations

1. **Deepest schema so far:** 8 levels (0-7), compared to Plotinus (5 levels, 0-4) and Poimandres (4 levels, 0-3). The Gnostic system adds depth through the Sophia-fall and Demiurge layers.

2. **The fragmentation cascade:** Two consecutive `fragmentation` edges (Luminaries → Sophia → Yaltabaoth) create a structural "break" in the middle of the schema. This is unlike Plotinus (all emanation) and unlike Poimandres (fragmentation only at one point, Anthropos's fall).

3. **The demiurge is ignorant and arrogant:** Structurally parallel to the Hermetic Demiurgos but functionally opposite — the Gnostic demiurge is malicious/ignorant, the Hermetic one is positive. Same `demiurge` role tag but different edge type (`fragmentation` from Sophia vs. `creation` from God-Mind).

4. **Sophia as pivot node:** She is the structural hinge between the upper Pleroma (light, order, consent) and the lower cosmos (darkness, ignorance, theft). No other tradition has this specific pivot structure.

---

*Written: 2026-03-28*
