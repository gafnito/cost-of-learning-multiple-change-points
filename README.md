# The Cost of Learning under Multiple Change Points

Official implementation and experiment code for the paper **"The Cost of Learning under Multiple Change Points"** (ICML 2026).

The main entry point is [`REPRODUCING_EXPERIMENTS.md`](REPRODUCING_EXPERIMENTS.md), which lists the commands used to reproduce the synthetic, real-data, and appendix experiments.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

For headless machines or macOS sessions without GUI access:

```bash
export MPLBACKEND=Agg
export MPLCONFIGDIR=.mplconfig
mkdir -p .mplconfig
```

## Repository Layout

- `icml/ATC.py`: main synthetic ATC experiments.
- `icml/atc_scaling_scenarios_dense_adver.py`: dense, adversarial, and passive-baseline experiments.
- `icml/atc_vary_S_experiment.py`: regret scaling with the number of changes.
- `icml/atc_nab_run.py`: NAB CPU real-data experiments.
- `icml/consants.py`: stored constant-threshold figure reconstruction.
- `illustrations/`: schematic figures.
- `NAB/data/realAWSCloudwatch/ec2_cpu_utilization_ac20cd.csv`: the NAB CPU series used in the paper.

## Quick Start

Run a cheap smoke test:

```bash
MPLBACKEND=Agg MPLCONFIGDIR=.mplconfig python3 icml/ATC.py \
  --algos exact geom_ends \
  --n-mc 10 \
  --T-list 600 1200 \
  --scenario md \
  --out-dir figures_quick
```

The paper-level commands use much larger Monte Carlo counts and can be slow. See [`REPRODUCING_EXPERIMENTS.md`](REPRODUCING_EXPERIMENTS.md).

## Data Notice

The included NAB CSV file is from the Numenta Anomaly Benchmark. Its license notice is included in [`NAB_LICENSE.txt`](NAB_LICENSE.txt).
