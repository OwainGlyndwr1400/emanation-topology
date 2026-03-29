# Sethian Gnostic (Trimorphic Protennoia) Encoding Rationale

## Primary Encoding: 8 Nodes, 7 Edges

```
Invisible Spirit (Father)            [source]          level 0
  |  [emanation]
Protennoia (Barbelo/First Thought)   [first_emanation] level 1  ← triadic: Voice/Speech/Word
  |  [emanation]
Autogenes (Perfect Son / Christ)     [intellect]       level 2
  |  [emanation]
Four Luminaries (Armozel-Eleleth)    [intermediary]    level 3
  |  [fragmentation]
Sophia / Epinoia (Fallen Light)      [fallen]          level 4
  |  [fragmentation]
Yaltabaoth (Saklas / Samael)         [demiurge]        level 5
  |  [creation]
Archons (Powers)                     [intermediary]    level 6
  |  [creation]
Material World / Humanity            [matter]          level 7
```

## Why 8 Nodes (vs. Apocryphon's 9)

The Trimorphic Protennoia and the Apocryphon of John share the same Sethian cosmological framework. The schemas are very similar — 8 vs. 9 nodes, depth 7 for both, same edge-type pattern (emanation → fragmentation → creation). The key difference is the absence of Adamas (Perfect Man) as a separate structural level in the TP.

The reason Adamas is excluded: In the Apocryphon, Autogenes branches to BOTH the Four Luminaries AND Adamas (separate structural levels). In the Trimorphic Protennoia, Autogenes establishes the Four Luminaries, and the text doesn't treat Adamas as a distinct cosmological stage — Protennoia herself plays the roles that Adamas performs in other Sethian texts (template for humanity, divine image in the material world).

## The Triadic Protennoia Problem

The text's central distinctive feature is Protennoia's triple nature: she is the Voice, the Speech, and the Word/Logos. These are not three separate nodes (she is one being) but three modes of the same first-emanation.

**Why this doesn't create branching:** The three modes are sequential aspects of the same entity's activity, not three different levels. She is Voice → then Speech → then Word in her three descents. This is a temporal/sequential aspect, not a structural branching.

**Encoding decision:** Protennoia encoded as one node with `triadic_nature` attribute. See encoding_decisions Entry 18.

**Cross-traditional significance:** The triple identity of the first emanation is unique in the corpus. No other tradition has a first emanation with this structure. Closest analog: the Chaldean Triad (Father/Hecate/Mind) which has three principles at the same cosmic level — but those are three separate beings, not three modes of one.

## The Sophia/Epinoia Difference from Apocryphon

In the Apocryphon: Sophia acts without consent → her unauthorized desire produces a defective thought → Yaltabaoth is born from her defective product.

In the Trimorphic Protennoia: Eleleth (fourth luminary) speaks a word → Yaltabaoth appears → Yaltabaoth "snatches power from the innocent one (Sophia) who had descended."

**The structural position is the same** (Sophia between Luminaries and Yaltabaoth), but the causal story is different:
- Apocryphon: Sophia is the *cause* of the fall (she acts without consent)
- Trimorphic Protennoia: Sophia is the *victim* of the fall (she is overpowered)

Same `fallen` functional role, same edge types, different moral valence. Sophia goes from agent of error to innocent victim. This is important for the paper's discussion of cross-traditional semantic variation.

## Edge Type Pattern

| Edge | Type |
|---|---|
| Invisible Spirit → Protennoia | `emanation` |
| Protennoia → Autogenes | `emanation` |
| Autogenes → Four Luminaries | `emanation` |
| Four Luminaries → Sophia | `fragmentation` |
| Sophia → Yaltabaoth | `fragmentation` |
| Yaltabaoth → Archons | `creation` |
| Archons → Material World | `creation` |

**Pattern:** emanation (3 edges) → fragmentation (2 edges) → creation (2 edges)

This is IDENTICAL to the Apocryphon of John's pattern. Two consecutive fragmentation edges at the Sophia pivot point, followed by demiurgic creation below. This shared pattern will be the most significant finding in the inter-Gnostic comparison.

## Topology Summary (All Six Traditions)

| | Plotinus | Poimandres | Apocryphon | Chaldean | Kabbalah | Sethian (TP) |
|---|---|---|---|---|---|---|
| Shape | Linear | Wide tree | Deep tree | Linear | Linear+events | Deep tree |
| Nodes | 5 | 8 | 9 | 6 | 7 | **8** |
| Depth | 4 | 3 | 7 | 5 | 6 | **7** |
| Max branch | 1 | 3 | 2 | 1 | 1 | **1** |
| Process nodes | 0 | 0 | 0 | 0 | 2 | **0** |
| `contraction` | 0 | 0 | 0 | 0 | 1 | **0** |
| `fragmentation` | 0 | 1 | 2 | 0 | 1 | **2** |
| `fallen` role | no | no | yes | no | no | **yes** |
| Distinctive | Uniform emanation | Triple root | Sophia pivot | Double demiurge | Double process | Triadic Protennoia |

**Most similar traditions:**
- Sethian (TP) and Apocryphon: almost structurally identical — same depth, same branching, same edge-type pattern. They differ in 1 node count, Sophia's role semantics, and Protennoia's triadic nature.
- Plotinus and Chaldean: both linear chains, but different functional roles throughout
- Kabbalah is most structurally isolated (unique process nodes, unique contraction edge)

---

*Written: 2026-03-28*
