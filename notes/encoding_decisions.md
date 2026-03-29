# Encoding Decisions Log — WP 1.1

Every non-trivial encoding decision is recorded here with:
1. Tradition
2. Decision made
3. Alternatives considered
4. Scholarly justification
5. Sensitivity analysis needed? (Y/N)

---

## Entry 1: Plotinus — Nature (Physis) as Separate Node

**Decision:** Nature encoded as a distinct node at level 3 between Soul and Matter.

**Alternatives considered:**
- Option A (ADOPTED): 5-node encoding — One > Nous > Psyche > Nature > Matter. Nature as Soul's lowest productive activity given its own node because III.8 treats it as a distinct contemplative principle.
- Option B: 4-node encoding — One > Nous > Psyche > Matter. Nature treated as a function of Soul, not a separate ontological level. Strict "three hypostases" reading.

**Scholarly justification:** O'Meara (1993) and Emilsson (2007) both treat III.8 as describing Nature as a distinct productive principle with its own mode of contemplation. Armstrong (1940) tends toward the stricter three-hypostases reading. Gerson (1994) acknowledges Nature as functionally distinct but does not call it a fourth hypostasis. The majority position supports treating it as structurally (if not terminologically) distinct.

**Sensitivity analysis needed:** YES. The 4-node alternative encoding (without Nature) is documented in `plotinian.json` under `alternative_encodings.without_nature`. Both encodings should be run through the topology pipeline to test whether including/excluding Nature changes the cross-traditional similarity results.

---

## Entry 2: Plotinus — World Soul vs. Individual Soul

**Decision:** Soul encoded as a single node. World Soul treated as an alias, not a separate level.

**Alternatives considered:**
- Option A (ADOPTED): One node for Soul/Psyche, with World Soul listed as an alias.
- Option B: Two nodes — "Soul (hypostasis)" at level 2 and "World Soul" at level 3, with individual souls as yet another level.

**Scholarly justification:** Plotinus himself is inconsistent about the relationship between Soul as hypostasis, World Soul, and individual souls. Per Granularity Rule: encode at the coarsest level that preserves the tradition's own structural distinctions. Since Plotinus explicitly names only three hypostases (V.1), and treats World Soul as a functional aspect of the one Soul, the single-node encoding is more conservative and better grounded.

**Sensitivity analysis needed:** YES. The 6-node alternative encoding (with World Soul) is documented in `plotinian.json` under `alternative_encodings.with_world_soul`. Lower priority than Entry 1 sensitivity analysis.

---

## Entry 3: Plotinus — Nature-to-Matter Edge Type

**Decision:** The Nature → Matter edge typed as `reflection` rather than `emanation`.

**Alternatives considered:**
- Option A (ADOPTED): `reflection` — Matter receives forms from Nature passively, like a mirror receiving images, without itself being produced in the same active sense as the higher emanations.
- Option B: `emanation` — treating all downward relationships uniformly as emanation, regardless of mechanism.

**Scholarly justification:** Plotinus describes Matter as the endpoint where the emanative power reaches its limit, not as something actively produced by Nature. O'Meara (1993) describes Matter as "the darkness that is the absence of light" rather than a positive product. Coding Rule 7 requires edge labels from the controlled vocabulary; `reflection` best captures this asymmetric, passive relationship.

**Sensitivity analysis needed:** NO. Edge type affects label comparison but not topology. The graph structure is identical regardless of whether this edge is `emanation` or `reflection`.

---

## Entry 4: Plotinus — Matter as Node Despite Privation Status

**Decision:** Matter included as a node despite Plotinus's claim that it is "near non-being."

**Alternatives considered:**
- Option A (ADOPTED): Matter as a node with `functional_role: matter`. Its structural position as the terminus of descent is clear even if its ontological status is minimal.
- Option B: No matter node. The schema ends at Nature or Soul. Matter is treated as a boundary condition, not an ontological level.

**Scholarly justification:** Every major Plotinus scholar treats Matter as a structurally significant component of the Plotinian system, even if its ontological status is debated. Omitting it would make the Plotinian schema structurally incomplete for cross-traditional comparison (other traditions have explicit material-world endpoints).

**Sensitivity analysis needed:** NO. Removing Matter would reduce the graph to 3-4 nodes, making meaningful topological comparison difficult.

---

## Entry 5: Hermetic — God/Light and Nous as Same or Separate Nodes

**Decision:** Encoded as ONE node (God-Mind) at level 0. Poimandres explicitly identifies Light = Nous = God in CH I.6.

**Alternatives considered:**
- Option A (ADOPTED): Single node "God-Mind" combining Light, Nous, and Father. Aliases capture all names.
- Option B: Two nodes — "God/Light/Father" at level 0 and "Nous/Poimandres" at level 1. Logos, Demiurgos, Anthropos shift to level 2.

**Scholarly justification:** The text's own identification ("That Light is I, thy God, Mind") is the strongest evidence. Copenhaver (1992, pp. 98-101) discusses the ambiguity but does not argue for separating them structurally. Bull (2018) treats them as aspects of one principle.

**Sensitivity analysis needed:** YES. The 9-node alternative (with God and Nous separate) is documented in `hermetic.json` under `alternative_encodings.god_and_nous_separate`. This alternative adds depth and reduces branching at level 0 from 3 to 0, which would significantly alter topology.

---

## Entry 6: Hermetic — Nature as Pre-Existing or Emanated

**Decision:** Nature encoded as pre-existing substrate transformed by Logos, NOT as emanated from God. Edge from Logos to Nature typed as `reflection`.

**Alternatives considered:**
- Option A (ADOPTED): Nature appears independently in the vision as "Moist Darkness" (CH I.4) before Light acts upon it. Edge: Logos → Nature (`reflection`).
- Option B: Nature as emanated from God (the Darkness is a shadow cast by the Light). Edge: God-Mind → Nature (`emanation`).

**Scholarly justification:** The Poimandres text presents the Darkness as appearing in the vision independently: "there came forth from the Light a Holy Word (Logos) upon the Moist Nature." This implies Nature was already there for the Logos to act upon. Copenhaver (1992) notes the parallel with Genesis 1 (spirit of God moving over the waters) where the waters pre-exist the divine action. Fowden (1986) argues for a more monist reading but acknowledges the textual ambiguity.

**Sensitivity analysis needed:** YES. The alternative encoding (Nature emanated from God) would change the graph topology by adding an edge from God-Mind to Nature, increasing God-Mind's out-degree from 3 to 4.

---

## Entry 7: Hermetic — Anthropos as Level 1 or Level 2

**Decision:** Anthropos encoded at level 1 (same level as Logos and Demiurgos), directly produced by God-Mind.

**Alternatives considered:**
- Option A (ADOPTED): Anthropos at level 1. The text says God "gave birth to Man, co-equal to Himself" — placing Anthropos at the same ontological rank as the other direct emanations.
- Option B: Anthropos at level 2, produced by Nous (if Nous is separated from God). This would only apply in the 9-node alternative encoding.

**Scholarly justification:** The text is clear: Anthropos is a direct production of God, not mediated through Demiurgos or Logos. Copenhaver (1992) and Bull (2018) both read the Anthropos as a direct divine emanation.

**Sensitivity analysis needed:** NO (within primary encoding). Only relevant if the God/Nous separation (Entry 5) is adopted.

---

## Entry 8: Hermetic — Anthropos-to-Humanity Edge as Fragmentation

**Decision:** Edge from Anthropos → Mortal Humanity typed as `fragmentation`, not `emanation`.

**Alternatives considered:**
- Option A (ADOPTED): `fragmentation` — Anthropos breaks through the Harmony and falls into Nature by choice/desire. This is a rupture event, not a natural overflow.
- Option B: `emanation` — treating all downward movement uniformly as emanation.
- Option C: `reflection` — Anthropos falls because he sees his REFLECTION in Nature's waters and falls in love with the image.

**Scholarly justification:** The narrative describes a volitional act with destructive consequences — Anthropos "desired to dwell" in Nature and "broke through" the cosmic boundary. This is structurally parallel to Sophia's fall in Gnostic systems (desire + boundary-breaking = fragmentation). The `fragmentation` type captures the rupture. The `reflection` type would capture the mechanism (seeing the reflection) but not the structural consequence (breaking through the Harmony).

**Sensitivity analysis needed:** NO. Edge type does not affect topology, only label comparison.

---

## Entry 9: Valentinian Gnostic — Sophia as Separate Node vs. Part of Luminaries

**Decision:** Sophia encoded as a separate node at level 4, below the Four Luminaries.

**Alternatives considered:**
- Option A (ADOPTED): Sophia as a separate `fallen` node. Her fall is a distinct cosmological event that produces the Demiurge and the entire lower cosmos.
- Option B: Sophia remains within the Four Luminaries collective. The fragmentation edge goes from Luminaries directly to Yaltabaoth.

**Scholarly justification:** King (2006) treats Sophia's fall as the pivotal cosmological event in the Apocryphon. The text devotes extensive narrative to it (II 9,25-10,19). Structurally, collapsing Sophia into the Luminaries would hide the most important structural feature of the Gnostic system: the pivot between ordered emanation and disordered creation. Per schema_spec.md criterion 2 (functional cosmological stage): the fall is a distinct stage.

**Sensitivity analysis needed:** YES. The 8-node alternative (Sophia within Luminaries) changes the depth from 7 to 6 and removes the `fallen` role from the graph. This could affect cross-traditional comparison of the "pivot" structure.

---

## Entry 10: Valentinian Gnostic — Tradition Label

**Decision:** Tradition labeled `valentinian_gnostic` per the WP 1.1 roadmap.

**Note:** The Apocryphon of John is technically a Sethian text (per Turner 2001), not Valentinian. It predates Valentinus. The label is maintained for consistency with the roadmap's Tradition 1 slot. Future refinement could relabel as `sethian_gnostic` and separately encode a Valentinian system. This does not affect topology analysis since each tradition gets its own graph.

**Sensitivity analysis needed:** NO (labeling only, no structural impact).

---

## Entry 11: Valentinian Gnostic — Archon Granularity

**Decision:** All archonic powers (12 authorities + 7 kings + 365 angels) encoded as a single collective node with `sub_count: 12`.

**Alternatives considered:**
- Option A (ADOPTED): One node "Archons" covering the entire governing bureaucracy.
- Option B: Three nodes — "12 Authorities" (level 6), "7 Heavenly Kings" (level 7), "365 Angels" (level 8).

**Scholarly justification:** Per Granularity Rule: encode at the coarsest level that preserves structural distinctions. The text lists these groups but treats them as a single governing tier under Yaltabaoth. They do not function as sequential emanation stages. King (2006) treats the archontic realm as one structural level.

**Sensitivity analysis needed:** NO. Expanding would add depth without meaningful topological insight.

---

## Entry 12: Chaldean — Father and First Mind as One Node or Two

**Decision:** Encoded as ONE node (The Father) at level 0. The First Mind "abode in the Paternal Depth" — it is the Father's immanent self-knowing, not a separate emanation.

**Alternatives considered:**
- Option A (ADOPTED): Single node "Father" at level 0. The First Mind is the Father's intellective aspect, not yet "gone forth." Parallel to the Plotinian interpretation where the One's self-thinking doesn't produce a separate level.
- Option B: Two nodes — "Father/Paternal Depth" at level 0 and "First Mind" at level 1. Hecate shifts to level 2. The 7-node alternative.

**Scholarly justification:** Oracle 12 says the First Mind "had not gone forth, but abode in the Paternal Depth" — the "not gone forth" is the key phrase. Majercik (1989, pp. 5-8) identifies the Paternal Mind with the Father's own intellectual act. Johnston (1990) distinguishes the Father-as-mind from the Second Mind as the active creator. The First Mind is the Father's self-contemplation; the Second Mind is the creative principle that "goes forth."

**Sensitivity analysis needed:** YES. The 7-node alternative (Father + First Mind separate) is documented in `chaldean.json` under `alternative_encodings.with_first_mind_separate`. This adds one level of depth but preserves the linear topology.

---

## Entry 13: Chaldean — Hecate as Separate Node or Father's Power

**Decision:** Hecate encoded as a SEPARATE node at level 1 with `functional_role: soul`.

**Alternatives considered:**
- Option A (ADOPTED): Hecate/Power as a distinct node. Oracle 26-27 present the Dyad as structurally distinct from the Monad. She is named and has distinct functional roles (animating, mediating). Johnston (1990) devotes an entire monograph to her structural position.
- Option B: No Hecate node. Father's Power treated as internal. Schema: Father → Second Mind → Iynges → Hypezokos → Matter. 5-node linear chain.

**Scholarly justification:** The Chaldean Triad (Father / Power-Hecate / Second Mind) is the scholarly consensus structure. Lewy (1956, pp. 68-104) identifies Hecate as the central mediating principle. Oracle 20: "The Soul, being a brilliant Fire... is Mistress of Life" — this is Hecate's cosmic role. Without her, the Chaldean triadic structure collapses into a dyad that misrepresents the system.

**Sensitivity analysis needed:** YES. The 5-node alternative (without Hecate) is documented in `chaldean.json` under `alternative_encodings.without_hecate`. This would make the Chaldean schema structurally almost identical to a simplified Plotinian chain.

---

## Entry 14: Chaldean — Hypezokos as Separate Demiurge Node

**Decision:** Hypezokos encoded as a SEPARATE demiurge node at level 4, distinct from the Second Mind at level 2.

**Alternatives considered:**
- Option A (ADOPTED): Two demiurgic figures: Second Mind (`intellect`) at level 2 creates the intelligible world; Hypezokos (`demiurge`) at level 4 creates the material world.
- Option B: Collapse them into one demiurge node. "Second Mind / Hypezokos" as one node, removing one level.

**Scholarly justification:** The Introduction's scheme diagram explicitly separates them: "The Second Mind conducts the Empyrean World" (level 2) and "The Demiurgos of the Material Universe / Hypezokos (Flower of Fire)" is listed at the Elementary World (level 4). Oracle 13 says the Father "delivered things over to the Second Mind" — the Second Mind governs but does not materially build. Hypezokos is explicitly called "builder of the world" (lines 136, 374). Shaw (1995, p. 47) distinguishes intellectual creation (Second Mind) from material fabrication (Hypezokos).

**Sensitivity analysis needed:** NO. The double-demiurge is the most explicit Chaldean structural feature, directly stated in the text. Collapsing it would be a significant misrepresentation of the system.

---

## Entry 15: Kabbalistic — Tzimtzum as Node or Edge

**Decision:** Tzimtzum encoded as a SEPARATE NODE at level 1 with `functional_role: process`. The edge from Ain Sof to Tzimtzum is typed `contraction`.

**Alternatives considered:**
- Option A (ADOPTED): Tzimtzum as a node. It is a distinct cosmological event — the withdrawal that creates the Tehiru (vacated space). Scholem (1941, p. 261): "Luria's most crucial and original contribution." Without Tzimtzum as a node, the schema cannot represent what makes Lurianic Kabbalah distinctive.
- Option B: Tzimtzum as an edge. The `contraction` edge type from Ain Sof directly to Adam Kadmon. This encodes the event as a relationship property rather than a level.

**Scholarly justification:** Scholem consistently treats Tzimtzum as a **cosmological event** with its own structure (the Reshimu residue, the Tehiru void). Fine (2003, pp. 120-124) devotes a chapter to it as the first distinct act of the Lurianic cosmology. Its inclusion as a node captures the structural importance that the tradition itself assigns to it.

**Sensitivity analysis needed:** NO. The `contraction` edge type and the Tzimtzum node together constitute the most distinctive Lurianic feature. Removing it would make the schema pre-Lurianic (essentially the simpler Zoharic schema).

---

## Entry 16: Kabbalistic — Ten Sefirot as One Node or Ten Nodes

**Decision:** Encoded as ONE collective node with `sub_count: 10` at level 3. Internal Tree of Life topology documented as alternative encoding.

**Alternatives considered:**
- Option A (ADOPTED): One collective node "Ten Sefirot / Atzilut." The Sepher Yetzirah explicitly treats the 10 as a unified structural principle ("ten and not nine, ten and not eleven"). For the cross-traditional comparison, encoding the Sefirot as a single tier is consistent with how other traditions encode their divine-intellectual tiers (e.g., Four Luminaries in the Apocryphon, Iynges in the Chaldean system).
- Option B: Ten individual nodes forming the Tree of Life (DAG with convergence). This would be the single most complex schema in the corpus (13 nodes with Adam Kadmon + Tzimtzum + Ain Sof) and would introduce the only convergence-node structure in the dataset (Tiphereth with 2 parents, Yesod with 2 parents).

**Scholarly justification:** Per Granularity Rule: encode at the coarsest level that preserves the tradition's own structural distinctions. The SY treats the 10 as a unified set. For primary analysis, the collective encoding allows cleaner comparison. However, the Tree of Life alternative (Option B) is analytically valuable and documented for future sensitivity analysis.

**Sensitivity analysis needed:** YES. The full Tree of Life encoding would be the most topologically distinct schema in the corpus, introducing DAG-with-convergence topology not present in any other tradition. This is a high-priority sensitivity analysis for the paper.

---

## Entry 17: Kabbalistic — Include Shevirat HaKelim as Process Node

**Decision:** Shevirat HaKelim encoded as a SEPARATE NODE at level 4 with `functional_role: process`. Edge from Sefirot to Shevirat typed `fragmentation`.

**Alternatives considered:**
- Option A (ADOPTED): Shevirat as a node. It is a discrete cosmological event that structurally separates the ordered world (Sefirot/Atzilut) from the disordered worlds below (Beriah-Yetzirah-Assiah). Without it, the schema cannot capture what makes Lurianic Kabbalah structurally different from pre-Lurianic Kabbalah.
- Option B: No Shevirat node. Lower worlds created directly from Sefirot via `creation` edges. Pre-Lurianic or simplified encoding.

**Scholarly justification:** The Shevirat is as central to Lurianic Kabbalah as Sophia's fall is to Gnostic Kabbalah. Scholem (1941, pp. 265-268): "The most significant mystical event in Lurianic cosmogony." Fine (2003, ch. 5) treats it as the pivot of the entire system. Including it as a process-node captures the structural parallel with the Sophia pivot in the Apocryphon — a discovery that is analytically valuable for the paper.

**Sensitivity analysis needed:** NO. The Shevirat is as well-documented as Sophia's fall. Omitting it would make the Lurianic schema indistinguishable from a generic emanation schema.

---

## Entry 18: Sethian — Protennoia's Triadic Nature as One Node or Three

**Decision:** Protennoia encoded as ONE node at level 1. Her triadic nature (Voice/Speech/Word) is encoded as an attribute (`triadic_nature`), not as three separate nodes or branches.

**Alternatives considered:**
- Option A (ADOPTED): Single node. The three modes are sequential aspects of one being's activity, not three structural levels. The text's own structure confirms this: Protennoia speaks in first person as a unified "I" throughout all three subtractates. The three descents are soteriological (rescue missions), not cosmogonic stages.
- Option B: Three branching nodes — Voice (level 1a), Speech (level 1b), Word (level 1c) — branching from the Invisible Spirit at level 0. This would give branching factor 3 at the source level, analogous to Poimandres.
- Option C: Three sequential nodes — Voice (level 1), Speech (level 2), Word (level 3) — displacing Autogenes, Luminaries, etc. downward.

**Scholarly justification:** Turner (2001, pp. 132-145) treats the three-fold structure as a rhetorical/liturgical device — three aretalogies that express the same divine being's self-presentation. The text does not describe the three modes as separate cosmological levels. Option A preserves Turner's structural reading.

**Sensitivity analysis needed:** NO. The triadic nature is a semantic feature, not a topological one. Encoding as three separate nodes would misrepresent the text's own structure.

---

## Entry 19: Sethian — Origin of Yaltabaoth (Eleleth's Word vs. Sophia's Birth)

**Decision:** Edge from Sophia to Yaltabaoth typed `fragmentation`. Sophia encoded at level 4, Yaltabaoth at level 5 — same as Apocryphon encoding.

**Alternatives considered:**
- Option A (ADOPTED): Sophia → Yaltabaoth (`fragmentation`). Even though in TP Yaltabaoth appears through Eleleth's word and then "snatches power" from Sophia, the structural relationship (Sophia is the proximate origin of Yaltabaoth's power) justifies the same edge.
- Option B: Four Luminaries → Yaltabaoth (`fragmentation`), skipping Sophia as an intermediate. This would reflect the literal text more accurately (Eleleth speaks → Yaltabaoth appears) but would lose Sophia's structural role.

**Scholarly justification:** Keeping Sophia at level 4 (between Luminaries and Yaltabaoth) reflects the scholarly consensus. Turner (2001) treats the Sophia figure as structurally essential in all Sethian texts — she is the pivot between the Pleroma and the material world regardless of the specific narrative mechanism. Logan (1996, pp. 162-168) notes that the TP's "snatching" narrative is an alternative formulation of the same cosmological function as the Apocryphon's "birth" narrative.

**Sensitivity analysis needed:** NO. The structural position is the same even if the mechanism differs.

---
