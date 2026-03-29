# Emanation Topology — Computational Pipeline

**Convergent Cosmological Architecture: A Computational Graph-Theoretic Analysis of Emanation Hierarchies Across Nine Sacred and Philosophical Traditions**

*Submitted to Digital Scholarship in the Humanities (DSH), Oxford University Press*

---

## Overview

This repository contains the full computational pipeline, DAG schema files, statistical outputs, and publication-ready figures for the above paper. The study encodes nine cosmological hierarchies as labelled directed acyclic graphs (DAGs) and applies graph-theoretic similarity measures (VF2 isomorphism, Weisfeiler-Leman kernel, graph edit distance) to test for structural convergence across culturally independent traditions.

## Repository Structure

```
emanation-topology/
├── data/
│   ├── schemas/          # 9 JSON-encoded DAG schemas
│   └── raw_texts/        # Primary source excerpts used for encoding
├── scripts/
│   ├── encode_schemas.py        # Load + validate schemas against DAG contract
│   ├── compute_invariants.py    # Compute 15+ topological metrics per schema
│   ├── generate_controls.py     # Generate 7,000 null-model random rooted trees
│   ├── statistical_comparison.py # 6 formal statistical tests vs null distribution
│   ├── isomorphism_tests.py     # VF2 + WL kernel + GED + Levenshtein (36 pairs)
│   ├── visualize.py             # 6 publication-ready figures at 300 dpi
│   └── run_pipeline.py          # Single-command orchestrator
├── outputs/
│   ├── figures/          # 6 publication-ready PNG figures (300 dpi)
│   ├── invariants/       # Topological invariants + statistical results (JSON)
│   │   └── controls/     # Null-model DAG summary files
│   └── similarity_matrix/ # 7 pairwise similarity output files
├── notes/                # Encoding rationale and source notes per tradition
├── requirements.txt
└── LICENSE
```

## Schemas

Nine cosmological hierarchies encoded as labelled DAGs:

| Tradition | Nodes | Depth | Chain? |
|---|---|---|---|
| Plotinian Neoplatonism | 5 | 4 | Yes |
| Sethian Gnosticism | 8 | 7 | Yes |
| Valentinian Gnosticism | 9 | 7 | No |
| Hermetic (*Poimandres*, CH I) | 8 | 3 | No |
| Chaldean Oracles | 6 | 5 | Yes |
| Lurianic Kabbalah | 7 | 6 | Yes |
| Samkhya (*Samkhya Karika*) | 7 | 6 | Yes |
| Taoist (Daodejing Ch. 42) | 5 | 4 | Yes |
| Genesis 1:1–2:3 (negative control) | 8 | 2 | No |

## Key Results

- **6/9 schemas are linear chains** — p < 0.001 vs. null baseline of 6.4%
- **Real schemas significantly deeper than null** — Mann-Whitney U=6105, p=0.028
- **Two exact structural isomorphisms (GED=0):**
  - Plotinian Neoplatonism ↔ Taoist Daodejing (separated by 6 centuries + Eurasian continent)
  - Lurianic Kabbalah ↔ Samkhya (separated by 12 centuries + Mediterranean/Indian subcontinent)
- **Genesis negative control maximally distant** from all emanation schemas (GED range 8–12)
- **Family separation ratio: 2.46x** (linear-chain intra-GED vs. inter-family GED)

## Reproducing the Analysis

**Requirements:** Python 3.10+

```bash
pip install -r requirements.txt
python scripts/run_pipeline.py
```

Run individual steps with `--from N` or `--only N` flags.

## Data Deposit

Full dataset also deposited on Zenodo: [DOI to be added on publication]

## Author

Erydir Ceisiwr — Independent Researcher, Awen Grid Programme
Swansea, Wales, United Kingdom
ORCID: [0009-0004-4577-5253](https://orcid.org/0009-0004-4577-5253)

## Licence

MIT License — see [LICENSE](LICENSE)
