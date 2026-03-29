# Apocryphon of John Encoding Rationale

## Primary Encoding: 9 Nodes, 8 Edges

```
Invisible Spirit (Monad)    [source]            level 0
  |  [emanation]
Barbelo (First Thought)     [first_emanation]   level 1
  |  [emanation]
Autogenes (Christ)          [intellect]         level 2
  |          |
  |[emanation] [emanation]
  v          v
Four         Adamas                              level 3
Luminaries   (Perfect Man)
  |
  | [fragmentation]
  v
Sophia (fallen aeon)        [fallen]            level 4
  |  [fragmentation]
  v
Yaltabaoth (Demiurge)       [demiurge]          level 5
  |  [creation]
  v
Archons (12+7+365)          [intermediary]      level 6
  |  [creation]
  v
Material World              [matter]            level 7
```

## Why 9 Nodes

This is the largest schema so far (Plotinus: 5, Poimandres: 8). The depth of the Gnostic system reflects its core narrative: the cosmos is layered with both intentional emanation (upper Pleroma) and accidental/ignorant creation (lower cosmos), separated by the Sophia pivot.

Each node passes the inclusion test from schema_spec.md:
- Named ontological entity or functional cosmological stage? YES for all 9.
- Would a scholar recognize this as a distinct level? YES — King (2006) and Layton (1987) both identify these levels.

## Node-by-Node Rationale

### Invisible Spirit — `source`
Unambiguous. Extended negative theology (over 50 negations in the text). The absolute transcendent origin. Structurally parallel to Plotinus's One and Poimandres's God-Mind.

### Barbelo — `first_emanation`
Unambiguous. The first power to emerge. "His thought performed a deed and she came forth." She is androgynous (Mother-Father), receives the pentad of aeons as attributes (not separate nodes — they are her qualities per Granularity Rule).

### Autogenes/Christ — `intellect`
The only-begotten Son. Given Mind (Nous) as a fellow worker. Creates everything through the Word. Structurally parallel to Plotinus's Nous (contains the Forms/Ideas) but one level deeper due to Barbelo intervening.

**Why `intellect` and not `first_emanation`?** Barbelo is the first emanation. Autogenes is the second generation. His functional role is intellectual ordering — he creates through the Word, organizes the Pleroma, and places beings in the aeons. The `intellect` role captures this.

### Four Luminaries — `intermediary`
Collective node (sub_count: 4, with 12 total aeons). The structural pillars of the Pleroma. Sophia is associated with the fourth luminary (Eleleth) but encoded as a separate node because her fall is a distinct event.

### Adamas — `intermediary`
The Perfect Man, placed in the first aeon. Parallel to the Hermetic Anthropos but WITHOUT the fall — in the Gnostic system, Adamas stays in the Pleroma. It is Sophia, not Adamas, who falls.

### Sophia — `fallen`
**The most structurally significant node in the Gnostic system.** She is an aeon who acts without consent — she "wanted to bring forth a likeness out of herself without the consent of the Spirit." Her unauthorized act produces the Demiurge.

**Why a separate node from Four Luminaries?** Because her fall is the central cosmological event. It creates the entire lower cosmos. Encoding her as part of the Luminaries collective would obscure this structural pivot. Per schema_spec.md criterion 2 (functional cosmological stage): the fall is a distinct stage.

### Yaltabaoth — `demiurge`
Sophia's imperfect offspring. Creates his own realm in ignorance. Three names: Yaltabaoth, Saklas, Samael. Declares "I am God" without knowing the higher realms.

**Contrast with Hermetic Demiurgos:** Same `demiurge` role tag, but:
- Hermetic: positive agent, created by God on purpose, edge = `creation`
- Gnostic: ignorant/arrogant, product of error, edge = `fragmentation`

### Archons — `intermediary`
Collective node (sub_count: 12 authorities + 7 kings + 365 angels). Created by Yaltabaoth to govern the material cosmos.

### Material World — `matter`
The material cosmos and material humanity. Created by the archons in the image of the divine Adamas. The endpoint of descent.

## Edge Type Distribution

| Edge | Type | Note |
|---|---|---|
| Spirit → Barbelo | `emanation` | Natural overflow from self-contemplation |
| Barbelo → Autogenes | `emanation` | Begotten through the Spirit looking at Barbelo |
| Autogenes → Four Luminaries | `emanation` | Natural unfolding of the Pleroma |
| Autogenes → Adamas | `emanation` | The perfect Man appears through divine will |
| Four Luminaries → Sophia | `fragmentation` | Sophia acts WITHOUT consent — a break in the order |
| Sophia → Yaltabaoth | `fragmentation` | Imperfect offspring from unauthorized act |
| Yaltabaoth → Archons | `creation` | Deliberate creation by the ignorant demiurge |
| Archons → Material World | `creation` | Archons fashion the material cosmos and body |

**Key pattern:** The upper half (levels 0-3) is pure emanation. The lower half (levels 4-7) begins with fragmentation and shifts to creation. The Sophia pivot at level 4 is where the edge type changes — above her is ordered emanation, below her is disordered creation. This upper/lower split may be a distinguishing topological feature of Gnostic systems.

## Topology Summary

| Property | Value | vs. Plotinus | vs. Poimandres |
|---|---|---|---|
| Node count | 9 | 5 (+4) | 8 (+1) |
| Edge count | 8 | 4 (+4) | 7 (+1) |
| Depth | 7 | 4 (+3) | 3 (+4) |
| Max branching | 2 (at Autogenes) | 1 | 3 |
| Graph shape | Deep tree with pivot | Linear chain | Wide shallow tree |
| Edge types used | emanation, fragmentation, creation | emanation, reflection | emanation, creation, reflection, fragmentation |
| Distinctive feature | **Fragmentation cascade in the middle** | Uniform emanation | Triple root branching |

**Three distinct topologies from three traditions.** This is exactly the variation the WP 1.1 analysis needs.

---

*Written: 2026-03-28*
