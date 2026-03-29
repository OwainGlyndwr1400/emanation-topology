# Scripts — Emanation-Schema Topology Pipeline

## Overview

This directory contains the Python analysis pipeline for WP 1.1. The pipeline takes JSON schema files as input and produces topological invariants, isomorphism test results, statistical comparisons against randomized controls, and publication-ready visualizations.

## Dependencies

```
networkx >= 3.0        # Graph construction, VF2 isomorphism, invariants
numpy >= 1.24          # Numerical computation
scipy >= 1.10          # Statistical tests (Mann-Whitney U, permutation tests)
matplotlib >= 3.7      # Visualization
seaborn >= 0.12        # Heatmap visualization
```

Install: `pip install networkx numpy scipy matplotlib seaborn`

## Pipeline Architecture

```
run_pipeline.py          # Master orchestration — runs everything in sequence
  |
  +-- encode_schemas.py   # Load JSON schemas into NetworkX DiGraphs, validate
  |
  +-- compute_invariants.py  # Compute topological invariants for each graph
  |
  +-- isomorphism_tests.py   # VF2 + WL isomorphism, graph edit distance
  |
  +-- generate_controls.py   # Generate 1000 randomized DAGs matching real graph properties
  |
  +-- statistical_comparison.py  # Permutation test, Mann-Whitney U, Cohen's d
  |
  +-- visualize.py           # Graph layouts, similarity heatmaps, invariant plots
```

## Module Specifications

### encode_schemas.py

```python
def load_schema(json_path: str) -> nx.DiGraph:
    """Load a JSON schema file and return a NetworkX DiGraph.
    Nodes get all attributes from the JSON.
    Edges get relationship type as attribute."""

def load_all_schemas(schemas_dir: str) -> dict[str, nx.DiGraph]:
    """Load all JSON schemas from a directory. Returns {tradition_name: graph}."""

def validate_dag(G: nx.DiGraph) -> tuple[bool, list[str]]:
    """Validate that G satisfies the DAG Contract from schema_spec.md.
    Returns (is_valid, list_of_violations)."""

def assign_levels(G: nx.DiGraph) -> nx.DiGraph:
    """Compute and assign level attributes based on shortest path from root."""

def get_root(G: nx.DiGraph) -> str:
    """Return the single root node (in-degree 0). Raises if not exactly one."""
```

### compute_invariants.py

```python
def compute_all_invariants(G: nx.DiGraph) -> dict:
    """Compute all topological invariants for a single graph.
    Returns dict with keys:
      - node_count: int
      - edge_count: int
      - depth: int (longest path from root)
      - diameter: int (longest shortest path, treating as undirected)
      - in_degree_dist: list[int] (sorted)
      - out_degree_dist: list[int] (sorted)
      - branching_factors: list[int] (out-degree at each level)
      - betweenness_centrality: dict[node_id, float]
      - clustering_coefficient: float (treating as undirected)
      - level_widths: list[int] (number of nodes at each level)
    """

def invariant_distance(inv1: dict, inv2: dict) -> float:
    """Compute a normalized distance between two invariant sets.
    Combines differences in depth, branching, level widths, degree distributions.
    Returns float in [0, 1] where 0 = identical topology."""

def invariant_table(graphs: dict[str, nx.DiGraph]) -> pd.DataFrame:
    """Compute invariants for all graphs and return as a comparison table."""
```

### isomorphism_tests.py

```python
def vf2_subgraph_isomorphism(G1: nx.DiGraph, G2: nx.DiGraph) -> tuple[bool, dict | None]:
    """Test for subgraph isomorphism using VF2 algorithm.
    Returns (is_isomorphic, node_mapping_or_None).
    Uses functional_role as node match criterion."""

def wl_hash(G: nx.DiGraph, iterations: int = 5) -> str:
    """Compute Weisfeiler-Leman hash for graph G.
    Uses functional_role as initial node label."""

def wl_similarity(G1: nx.DiGraph, G2: nx.DiGraph, iterations: int = 5) -> float:
    """Compute WL-based similarity between two graphs.
    Returns float in [0, 1] where 1 = identical WL hash."""

def graph_edit_distance(G1: nx.DiGraph, G2: nx.DiGraph) -> int:
    """Compute exact graph edit distance between G1 and G2.
    Uses networkx.graph_edit_distance with custom node/edge match."""

def pairwise_similarity_matrix(graphs: dict[str, nx.DiGraph], metric: str = 'ged') -> np.ndarray:
    """Compute pairwise similarity for all graph pairs.
    metric: 'ged' (graph edit distance), 'wl' (WL similarity), 'invariant' (invariant distance)
    Returns (n x n) numpy array + list of tradition names."""
```

### generate_controls.py

```python
def random_dag(n_nodes: int, n_edges: int, max_depth: int,
               roles: list[str] | None = None) -> nx.DiGraph:
    """Generate a random DAG matching specified structural parameters.
    Assigns random functional_role from the canonical role list."""

def generate_control_set(template_graphs: dict[str, nx.DiGraph],
                         n_controls: int = 1000) -> list[nx.DiGraph]:
    """Generate control graphs that match the structural properties
    (node count, edge count, depth, degree distribution) of the real graphs
    but with randomized topology.

    For each control graph:
    1. Sample n_nodes and n_edges from the real graph distributions
    2. Generate a random DAG with those parameters
    3. Assign random functional_role labels
    """

def control_similarity_distribution(controls: list[nx.DiGraph],
                                     metric: str = 'ged') -> np.ndarray:
    """Compute pairwise similarities within the control set.
    Returns flat array of all pairwise distances."""
```

### statistical_comparison.py

```python
def permutation_test(real_distances: np.ndarray,
                     control_distances: np.ndarray,
                     n_perms: int = 10000) -> tuple[float, float]:
    """Test whether real inter-tradition distances are significantly smaller
    than control distances. Returns (p_value, observed_statistic)."""

def mann_whitney_test(real_distances: np.ndarray,
                      control_distances: np.ndarray) -> tuple[float, float]:
    """Mann-Whitney U test. Returns (U_statistic, p_value)."""

def cohens_d(real_distances: np.ndarray,
             control_distances: np.ndarray) -> float:
    """Effect size: Cohen's d."""

def full_report(real_matrix: np.ndarray,
                control_distribution: np.ndarray,
                tradition_names: list[str]) -> str:
    """Generate a full statistical report as formatted text.
    Includes: descriptive stats, permutation test, Mann-Whitney, Cohen's d,
    per-pair results, and overall conclusion."""
```

### visualize.py

```python
def plot_schema(G: nx.DiGraph, title: str, save_path: str | None = None):
    """Plot a single emanation schema as a top-down hierarchical graph.
    Nodes colored by functional_role. Edges labeled by relationship type."""

def plot_all_schemas(graphs: dict[str, nx.DiGraph], save_dir: str):
    """Plot all schemas side by side for visual comparison."""

def plot_similarity_heatmap(matrix: np.ndarray, labels: list[str],
                            title: str, save_path: str | None = None):
    """Plot a similarity/distance heatmap with tradition labels."""

def plot_invariant_comparison(invariants: dict[str, dict], save_path: str | None = None):
    """Bar charts comparing key invariants across traditions."""

def plot_control_distribution(real_distances: np.ndarray,
                              control_distances: np.ndarray,
                              save_path: str | None = None):
    """Histogram of control distances with real distances marked."""
```

### run_pipeline.py

```python
def main():
    """Master pipeline:
    1. Load all schemas from data/schemas/
    2. Validate each (abort if any fail)
    3. Compute invariants for each
    4. Compute pairwise similarity matrix (GED, WL, invariant-based)
    5. Generate 1000 control graphs
    6. Compute control similarity distribution
    7. Run statistical comparison (permutation, Mann-Whitney, Cohen's d)
    8. Generate all figures
    9. Save all results to outputs/
    10. Print summary report
    """
```

## Output Files

| Output | Location | Description |
|---|---|---|
| Invariant tables | `outputs/invariants/` | CSV tables of all computed invariants |
| Similarity matrices | `outputs/similarity_matrix/` | CSV files for GED, WL, and invariant-based similarity |
| Statistical report | `outputs/statistical_report.txt` | Full test results |
| Schema figures | `outputs/figures/schema_*.png` | Individual schema visualizations |
| Heatmaps | `outputs/figures/heatmap_*.png` | Pairwise similarity heatmaps |
| Control distribution | `outputs/figures/control_distribution.png` | Histogram with real vs. control |

---

*Last updated: 2026-03-28*
