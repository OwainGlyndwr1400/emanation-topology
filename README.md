# Emanation Topology

**Encode nine creation cosmologies from unrelated cultures as directed graphs,
strip out every word, and measure whether what remains has the same shape.**

Two pairs come back **structurally identical** — graph edit distance exactly zero:

- **Plotinus** (3rd-century Roman Egypt) and the **Daodejing** (4th-century BCE China)
- **Lurianic Kabbalah** (16th-century Safed) and **Samkhya** (4th-century India)

Six centuries and a continent apart in the first case; twelve centuries and the
Mediterranean-to-Indian-subcontinent gap in the second.

This repository holds the full pipeline that produces that result: DAG schemas,
topological invariants, 7,000 null-model controls, six statistical tests, four
similarity measures, and six publication-ready figures. One command runs all of it.

[![Python](https://img.shields.io/badge/Python-3.10+-3776ab)](https://www.python.org/)
[![Licence](https://img.shields.io/badge/Licence-MIT-green)](#licence)

*Work Package 1.1 of the Awen Grid Empirical Programme. Submitted to* Digital
Scholarship in the Humanities *(Oxford University Press).*

---

## Run it

```bash
git clone https://github.com/OwainGlyndwr1400/emanation-topology.git
cd emanation-topology
pip install -r requirements.txt
python scripts/run_pipeline.py
```

Python 3.10+. Resume with `--from N`, or run a single step with `--only N`.
Every figure and statistic in the paper regenerates from that one command.

---

## What it measures

Each cosmology is encoded as a **labelled directed acyclic graph** under a
seven-rule contract: single root, 4–20 nodes, five edge types (`emanation`,
`creation`, `fragmentation`, `contraction`, `reflection`) and nine functional
roles (`source`, `first_emanation`, `intellect`, `soul`, `intermediary`,
`fallen`, `demiurge`, `matter`, `process`). Where an encoding decision is
genuinely contested, the alternative is documented rather than quietly chosen.

The pipeline then applies:

| Step | What it does |
|---|---|
| `encode_schemas.py` | Load and validate all 9 schemas against the DAG contract |
| `compute_invariants.py` | 15+ topological metrics per schema |
| `generate_controls.py` | 7,000 null-model random rooted trees |
| `statistical_comparison.py` | 6 formal tests against the null distribution |
| `isomorphism_tests.py` | VF2 isomorphism, Weisfeiler-Leman kernel, graph edit distance, Levenshtein — all 36 pairs |
| `visualize.py` | 6 figures at 300 dpi |

The null models are the load-bearing part. Without a baseline distribution of
random rooted trees, "these structures look similar" is an impression. With one,
it becomes a p-value.

---

## Results

- **6 of 9 schemas are linear chains** — against a null baseline of 6.4%. p < 0.001.
- **Real schemas are significantly deeper than null** — Mann-Whitney U = 6105, p = 0.028.
- **Two exact structural isomorphisms** (GED = 0), listed above.
- **The negative control behaves.** Genesis 1:1–2:3 was encoded specifically as a
  creation-not-emanation cosmology, and it lands maximally distant from every
  emanation schema (GED range 8–12). If the method were finding structure in
  noise, Genesis would not separate.
- **Family separation ratio: 2.46x** — linear-chain intra-family GED versus
  inter-family GED.

---

## The nine traditions

| Tradition | Nodes | Depth | Linear chain? |
|---|---|---|---|
| Plotinian Neoplatonism | 5 | 4 | Yes |
| Sethian Gnosticism | 8 | 7 | Yes |
| Valentinian Gnosticism | 9 | 7 | No |
| Hermetic (*Poimandres*, CH I) | 8 | 3 | No |
| Chaldean Oracles | 6 | 5 | Yes |
| Lurianic Kabbalah | 7 | 6 | Yes |
| Samkhya (*Samkhya Karika*) | 7 | 6 | Yes |
| Taoist (*Daodejing* ch. 42) | 5 | 4 | Yes |
| Genesis 1:1–2:3 *(negative control)* | 8 | 2 | No |

Primary source excerpts used for each encoding are in `data/raw_texts/`;
per-tradition encoding rationale is in `notes/`.

---

## The series

This is where the method starts. Each later work package adds traditions and
re-runs the whole pipeline, so the finding is continuously re-tested rather than
asserted once.

| WP | Traditions | Repository | DOI | Headline |
|---|---|---|---|---|
| **1.1** | **9** | **this repo** | **pending** | **Method established; 2 exact isomorphisms** |
| 1.2 | 11 | [corpus-expansion-emanation](https://github.com/OwainGlyndwr1400/corpus-expansion-emanation) | [zenodo.19305988](https://doi.org/10.5281/zenodo.19305988) | Proclus + Suhrawardi; isomorphisms rise to 5 |
| 1.3 | 14 | [structural-attractors (wp1-3)](https://github.com/OwainGlyndwr1400/structural-attractors-emanation-cosmologies-wp1-3) | [zenodo.19324327](https://doi.org/10.5281/zenodo.19324327) | Zoroastrian, Manichaean, Orphic; separation peaks at 2.87x |
| 1.4 | 17 | [geographic-generality (wp1-4)](https://github.com/OwainGlyndwr1400/geographic-generality-emanation-cosmologies-wp1-4) | [zenodo.19340999](https://doi.org/10.5281/zenodo.19340999) | Popol Vuh - zero Old World contact, same families |
| 1.5 | 22 | [tier2-expansion (wp1-5)](https://github.com/OwainGlyndwr1400/tier2-expansion-emanation-cosmologies-wp1-5) | [zenodo.19362550](https://doi.org/10.5281/zenodo.19362550) | The Rig Veda splits across *both* families |
| 1.6 | 25 | [geographic-role-expansion (wp1-6)](https://github.com/OwainGlyndwr1400/geographic-role-expansion-emanation-cosmologies-wp1-6) | [zenodo.19368287](https://doi.org/10.5281/zenodo.19368287) | Five-way zero-contact convergence |

## Citation

> Ceisiwr, E. (2026). *Convergent Cosmological Architecture: A Computational
> Graph-Theoretic Analysis of Emanation Hierarchies Across Nine Sacred and
> Philosophical Traditions.* Digital Scholarship in the Humanities [submitted].

## Licence

MIT — code and data freely reusable with attribution.

## Author

Erydir Ceisiwr — Independent Researcher, Awen Grid Programme, Swansea, Wales.
ORCID [0009-0004-4577-5253](https://orcid.org/0009-0004-4577-5253)
