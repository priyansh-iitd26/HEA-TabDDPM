# HEA-TabDDPM

Synthetic High-Entropy Alloy (HEA) dataset generation using the TabDDPM diffusion model.

This repository accompanies our research on data augmentation for High-Entropy Alloy (HEA) property prediction. It provides the complete source code, trained model weights, configuration files, and synthetic datasets required to reproduce the reported results.

---

## Repository Structure

```
HEA-TabDDPM/
│
├── checkpoints/          # Trained TabDDPM model weights
├── configs/              # Training configuration (.toml)
├── data/                 # Original and synthetic datasets
├── lib/                  # Utility modules
├── results/              # Training log and Loss curve during training
├── scripts/              # Training, sampling and evaluation scripts
├── tab_ddpm/             # Core TabDDPM implementation
├── environment.yml
├── requirements.txt
├── README.md
├── LICENSE
```

---

## Dataset

The repository contains:

| File | Description |
|------|-------------|
| HEA_real.csv | Original experimental HEA dataset |
| HEA_synthetic_1300.csv | Synthetic dataset generated using TabDDPM |

---

## Model

Synthetic data were generated using the TabDDPM diffusion model.

Training configuration:

| Parameter | Value |
|----------|------:|
| Model | TabDDPM |
| Backbone | MLP |
| Diffusion Steps | 1000 |
| Noise Schedule | Cosine |
| Training Steps | 30000 |
| Device | CPU |
| EMA Model | Enabled |

---

## Installation

Clone the repository

```bash
git clone https://github.com/<your_username>/HEA-TabDDPM.git

cd HEA-TabDDPM
```

Create the Conda environment

```bash
conda env create -f environment.yml

conda activate tabddpm
```

Alternatively,

```bash
pip install -r requirements.txt
```

---

## Training

Run

```bash
set PYTHONPATH=.

python scripts/pipeline.py --config configs/hea_config.toml --train
```

---

## Sampling

Generate synthetic data using the trained model

```bash
set PYTHONPATH=.

python scripts/pipeline.py --config configs/hea_config.toml --sample
```

The generated synthetic dataset will be written to the output directory specified in the configuration file.

---

## Trained Model

The trained checkpoints are provided in

```
checkpoints/

model.pt
model_ema.pt
```

---

## Reproducibility

This repository includes:

- Source code
- Training configuration
- Trained model weights
- Original dataset (if publicly shareable)
- Synthetic dataset
- Environment specification

allowing complete reproduction of the reported TabDDPM experiments.

---

## Acknowledgements

This work builds upon the official implementation of TabDDPM by Yandex Research.
