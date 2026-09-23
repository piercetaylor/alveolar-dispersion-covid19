# Alveolar epithelial state dispersion in lethal COVID-19

This project analyzes alveolar epithelial cell states in the Columbia/NYP COVID-19 Lung Atlas, [SCP1219](https://singlecell.broadinstitute.org/single_cell/study/SCP1219) (Melms et al., 2021). It tests whether cells shift together along a single injury axis or spread across heterogeneous states. The analysis was conducted by Pierce Taylor, Chimdi Walter Ndubuisi, and Toni Kazic.

## Findings

The primary analysis includes 22,128 AT1, AT2, and ECM-high epithelial cells from 27 donors: seven healthy controls and 20 COVID-19 cases. COVID-19 cells showed greater within-group dispersion in the analyzed space (variance ratio 2.3; Levene p < 10⁻³⁰). A one-sided test for coherent displacement did not support that model (p = 1.0). The median diffusion-pseudotime difference was +0.048 on a 0–1 scale (permutation p = 0.001).

An independent cellxgene census cohort contained 89,736 alveolar cells from 618 donors across 35 datasets. An injury-score dispersion signal was also present there (variance ratio 1.65; p ≈ 10⁻¹³⁷). The primary atlas showed enrichment of KRT8+/CLDN4+ transitional cells, but the same marker threshold did not transfer across cohorts.

The primary dispersion result is measured across cells. Donor-level analysis did not show that each COVID-19 donor was individually more dispersed; differences between donors contribute to the cell-level pattern. The primary cohort has seven control donors, and the independent replication used an 84-gene panel that cannot reproduce the full trajectory analysis. These limits constrain biological interpretation. The [manuscript](manuscript/paper_v3.tex) reports the methods, donor-level results, ablations, and remaining uncertainties.

## Data and reproduction

SCP1219 data are obtained from the [Broad Single Cell Portal](https://singlecell.broadinstitute.org/single_cell/study/SCP1219). The raw files are not committed. `scripts/download_data.py` prints access instructions; it does not download the data. Follow those instructions, place the specified files in `data/raw/`, and verify them before running the pipeline. Portal access may require authentication.

```sh
pip install -r requirements.txt
python scripts/download_data.py
python scripts/download_data.py --verify
python scripts/run_pipeline.py --step all
```

The pipeline reads `config.yaml` and writes tables and figures under `results/`. The [runbook](RUNBOOK.md) explains column mappings and quality control checks. The independent replication has a separate [fetch script](scripts/replication/fetch_replication.py) and [analysis script](scripts/replication/analyze_replication.py).

## References and license

The primary atlas is Melms, J. C., et al. (2021), “A molecular single-cell lung atlas of lethal COVID-19,” *Nature* 595:114–119. The repository includes an [analysis plan](ANALYSIS_PLAN.md), [literature review](docs/LITERATURE_REVIEW.md), and [original detailed README](docs/legacy-readme.md). The repository code is under the [MIT License](LICENSE). Data access and reuse follow the source portals' terms.
