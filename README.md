# Improved Central Limit Theorem and Bootstrap Approximations for Linear Stochastic Approximation

Code for the numerical experiments accompanying the [paper](https://arxiv.org/abs/2510.12375).

The experiments use synthetic linear regression to study Polyak–Ruppert averaged estimators and multiplier-bootstrap confidence intervals. They compare coverage probabilities, interval lengths, and finite-sample variances across different step-size schedules.

## Notebooks

- **`lsa_experiments.ipynb`** — linear regression experiments comparing percentile bootstrap intervals, normal intervals based on bootstrap standard deviations, and overlapping batch means. Includes coverage, interval-length, and runtime measurements.
- **`lsa_variance_experiments_en.ipynb`** — exact second-moment calculations and Monte Carlo comparisons of the linear approximation, the full estimator, and the conditional bootstrap variance. Includes plots of variance ratios, interval lengths, and coverage.

## Installation

Python 3.12 is recommended. Install the dependencies with:

```bash
pip install jupyterlab numpy scipy pandas matplotlib seaborn tqdm numba ipywidgets
```

Start JupyterLab:

```bash
jupyter lab
```

Open a notebook and run its cells in order from a fresh kernel.

## Run sizes

In `lsa_variance_experiments_en.ipynb`, select a profile in the settings cell:

| Profile | Independent datasets | Bootstrap replicas per dataset |
|---------|---------------------:|-------------------------------:|
| `smoke` | 8 | 64 |
| `standard` | 128 | 256 |
| `large` | 1024 | 256 |

The variance notebook saves tables, figures, simulation arrays, run settings, and package versions in `lsa_results/`.

## Reproducibility

The variance notebook fixes the random seed and uses common data, bootstrap multipliers, and a fixed projection when comparing step-size exponents. The first run also compiles the update functions with Numba.

In `lsa_experiments.ipynb`, data generation and bootstrap sampling use fixed seeds, while some random projections use an unseeded global generator. Exact repetition of those results requires fixing the projection seed as well.
