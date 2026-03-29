# Poimandres Encoding Rationale

## Primary Encoding: 8 Nodes, 7 Edges

```
God-Mind (Supreme Light / Life-and-Light)     [source]         level 0
  |              |               |
  | [emanation]  | [creation]    | [emanation]
  v              v               v
Logos          Demiurgos       Anthropos                        level 1
(Holy Word)    (Formative      (Primal Man)
               Mind)
  |              |               |
  | [reflection] | [creation]    | [fragmentation]
  v              v               v
Nature         Seven           Mortal                           level 2
(Moist         Governors       Humanity
 Darkness)     (x7)
                 |
                 | [creation]
                 v
               Sensible                                        level 3
               Cosmos
```

### Why 8 Nodes (Not 5, 6, or 9)

**Not 5 (collapsing to match Plotinus):** The Poimandres genuinely describes more distinct ontological levels than Plotinus. Collapsing Logos + Demiurgos or omitting Anthropos would misrepresent the text's architecture. Per Coding Rule 5: do not force the text.

**Not 6 (omitting Anthropos and Mortal Humanity as "narrative characters"):** Anthropos is NOT merely a character — he is a distinct cosmological principle produced directly by God, "co-equal" with the Father. His fall into Nature is a structural event that creates a new ontological level (mortal humanity). Per schema_spec.md inclusion criterion 1 (named ontological entity) and 2 (functional cosmological stage): both Anthropos and Mortal Humanity qualify.

**Not 9 (separating God and Nous):** Poimandres explicitly identifies Light = Nous = God in CH I.6. Splitting them would contradict the text's own identification. The alternative 9-node encoding is documented.

### Node-by-Node Rationale

#### God-Mind — `source`

**Textual basis:** CH I.2-6

The Supreme is identified as both Light (the visionary form) and Mind (the intellectual principle). Poimandres says: "That Light is I, thy God, Mind." This conflation of Light and Nous is distinctive — in Plotinus they are separate levels (the One is beyond Mind; Mind is the first emanation). In the Poimandres, God IS Mind.

**Why `source` and not `first_emanation` or `intellect`?** Because God-Mind is the absolute origin of the Hermetic cosmos. Nothing precedes it in the text. The Light does not emanate from anything — it simply IS.

**Aliases include "Poimandres" and "Nous"** because the text identifies all of these.

#### Logos — `first_emanation`

**Textual basis:** CH I.5-6, 10-11

The Holy Word proceeds from God-Mind and descends upon Nature. It is called "the Son of God" — a direct emanation, not an aspect of God-Mind.

**Why `first_emanation`?** In the narrative sequence, the Logos is the first thing to emerge from God-Mind and act in the cosmos. However, Demiurgos and Anthropos are also produced by God-Mind. The `first_emanation` role here reflects narrative primacy (Logos appears first), not exclusive emanation.

**Why not merge with God-Mind?** Because the Logos acts independently — it descends onto Nature, causes elemental separation, and then leaps back up. It has its own agency. In Plotinus, Logos is a function of Nous; in Poimandres, it is a distinct entity.

#### Demiurgos — `demiurge`

**Textual basis:** CH I.9-11

The Formative Mind is produced by God-Mind specifically for the purpose of ordering the cosmos. It is "God of Fire and Air" and creates the Seven Governors.

**Why `demiurge` and not `first_emanation`?** The `demiurge` role captures its specific function: world-ordering. It is not the first thing to emerge (Logos precedes it in the narrative) but it is the cosmic craftsman.

**Critical contrast with Gnosticism:** The Hermetic Demiurgos is a POSITIVE figure — created intentionally by God for a good purpose. This is not the ignorant or malicious Gnostic Demiurge. The functional role tag is the same (`demiurge`) but the edge type (`creation` from God, not `fragmentation` from Sophia) captures the difference.

#### Anthropos — `intermediary`

**Textual basis:** CH I.12-14

The Primal Man is produced directly by God "co-equal to Himself." He is beautiful, bears the Father's image, and is given authority over creation. He then FALLS into Nature by choice.

**Why `intermediary` and not `first_emanation`?** Anthropos is not the first thing produced (Logos and Demiurgos precede him), and his primary structural function is to BRIDGE the intelligible and sensible worlds through his fall. The `intermediary` role captures this bridging function.

**Why not `fallen`?** The fall is something that happens to Anthropos, not his defining character. He is originally a god-like being; his fall is an event (modeled as the `fragmentation` edge to Mortal Humanity).

#### Seven Governors — `intermediary`

**Textual basis:** CH I.9, 11, 16

Collective node with `sub_count: 7`. These are the planetary powers who govern the sensible world through Fate. Each one contributes a quality to the creation of mortal humanity.

Per Granularity Rule: encoded as ONE node because the text treats them as a group, not as sequential emanations.

#### Nature — `intermediary`

**Textual basis:** CH I.4-5, 14-15

This is the most anomalous node. In Plotinus, Nature is emanated from Soul. In Poimandres, Nature appears to PRE-EXIST as "Moist Darkness" and is then TRANSFORMED by the Logos.

**Encoding decision:** Nature receives an incoming edge from Logos (`reflection`) but is NOT directly emanated from God-Mind. She is at level 2 — below the primary emanations but above the material world.

**Why `intermediary`?** Nature bridges between the intelligible action (Logos descending upon her) and the material result (the sensible cosmos). She also receives Anthropos in his fall.

#### Sensible Cosmos — `matter`

**Textual basis:** CH I.8-11

The ordered physical universe produced by the Seven Governors governing Nature (after Logos has organized the elements).

#### Mortal Humanity — `matter`

**Textual basis:** CH I.15-17

The endpoint of the Anthropic descent line. Twofold: mortal body from Nature, immortal essence from Anthropos.

### Edge Rationale

| Edge | Type | Rationale |
|---|---|---|
| God-Mind → Logos | `emanation` | Natural overflow — "the Son of God" proceeds from the Father |
| God-Mind → Demiurgos | `creation` | Deliberate production — God "gives birth to" the Formative Mind for a specific purpose |
| God-Mind → Anthropos | `emanation` | Overflow of the Father's image — Man is "co-equal" with God, not made for a purpose |
| Demiurgos → Seven Governors | `creation` | Deliberate formation — the Demiurgos creates the planetary architecture |
| Logos → Nature | `reflection` | The Logos acts UPON Nature (which pre-exists) rather than producing her. The relationship is impression, not generation. |
| Seven Governors → Sensible Cosmos | `creation` | The Governors set the cosmos in motion through their orbits |
| Anthropos → Mortal Humanity | `fragmentation` | Anthropos breaks through the Harmony and falls into Nature by choice — this is a fragmentation event, not a natural emanation |

---

## Topology Summary

| Property | Value | Contrast with Plotinus |
|---|---|---|
| Node count | 8 | vs. 5 (60% more nodes) |
| Edge count | 7 | vs. 4 (75% more edges) |
| Depth | 3 | vs. 4 (shallower despite more nodes) |
| Max branching factor | 3 (at level 0) | vs. 1 (no branching in Plotinus) |
| Graph structure | **Branching tree** | vs. **Linear chain** |
| Distinctive features | Triple branching at root; parallel descent lines; fragmentation edge | vs. Strict linearity; uniform emanation edges |
| Edge type diversity | 3 types (emanation, creation, fragmentation, reflection) | vs. 2 types (emanation, reflection) |

**This is the first genuine topological contrast in the WP 1.1 dataset.**

---

*Written: 2026-03-28*
