# SNMMI AI Certificate – 2-D Patch-Based PET/CT Lesion Segmentation Hands-On

Hands-on PyTorch + Google Colab notebooks for **2-D patch-based lesion segmentation** on PET data (PSMA demo, FDG practice) for the [SNMMI AI Certificate](https://www.snmmi.org/) program.


## Notebooks

| # | Notebook | Description | Open in Colab |
|---|----------|-------------|---------------|
| 1 | `notebooks/01_psma_demo.ipynb` | PSMA demo: train U-Net, eval, task-based comparison | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ZekunLi-Zeke/snmmi-ai-hands-on-segmentation/blob/main/notebooks/01_psma_demo.ipynb) |
| 2 | `notebooks/02_fdg_practice.ipynb` | FDG practice: guided TODOs | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ZekunLi-Zeke/snmmi-ai-hands-on-segmentation/blob/main/notebooks/02_fdg_practice.ipynb) |
| 2★ | `solutions/02_fdg_practice_solution.ipynb` | FDG practice – complete solution | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ZekunLi-Zeke/snmmi-ai-hands-on-segmentation/blob/main/solutions/02_fdg_practice_solution.ipynb) |

## Getting Started

### Option A – Google Colab (recommended)

Click one of the **Open in Colab** badges above. Each notebook:
- installs its own dependencies inline (no `requirements.txt` path needed),
- downloads the dataset from GitHub Releases automatically,
- runs top-to-bottom without any edits.

### Option B – Local setup

```bash
git clone https://github.com/ZekunLi-Zeke/snmmi-ai-hands-on-segmentation.git
cd snmmi-ai-hands-on-segmentation
pip install -r requirements.txt
jupyter notebook
```

## Repository Layout

```
snmmi-ai-hands-on-segmentation/
├── notebooks/
│   ├── 01_psma_demo.ipynb          # PSMA demo (fully worked)
│   └── 02_fdg_practice.ipynb       # FDG practice (learner TODOs)
├── solutions/
│   └── 02_fdg_practice_solution.ipynb  # Complete FDG solution
├── .github/
│   └── instructions/
│       └── notebooks.instructions.md
├── requirements.txt
├── LICENSE
└── README.md
```

> **Note:** `data/` is listed in `.gitignore`. Datasets are downloaded at runtime from GitHub Releases and never committed to the repository.

## Data & Citation

Sample data are **2-D 64×64 lesion-containing PET/CT patches** derived from:

> Gatidis, S., Kuestner, T., Ingrisch, M., Hepp, T., Frueh, M., Nikolaou, K.,
> La Fougere, C., Pfannenberg, C., Fabritius, M., Jeblick, K., Schachtner, B.,
> Dexl, J., Wesp, P., Mittermeier, A., Unterrainer, L., Sheikh, G., Boening, G.,
> Brendel, M., Ricke, J., … Cyran, C. (2025).
> *PSMA-FDG-PET-CT-Lesions*.
> University of Tuebingen, Ludwig-Maximilians-University Munich.
> <https://doi.org/10.57754/FDAT.0zs4c-89f12>

Please cite the original dataset when using or redistributing these patch subsets.

- License: **CC BY-NC 4.0** – non-commercial use only.
- Redistributed patch subsets inherit the original dataset license and must be used for non-commercial purposes only.
- Dataset assets are distributed via [GitHub Releases](https://github.com/ZekunLi-Zeke/snmmi-ai-hands-on-segmentation/releases) (not committed to this repository).

This repository's own code and instructional materials are released under the [LICENSE](LICENSE) found at the repository root.

## Troubleshooting

| Problem | Solution |
|---------|----------|
| **No GPU available** | The notebooks run on CPU too; training 3 epochs on 64×64 patches takes ~2–5 min on CPU. |
| **Slow runtime** | Reduce `BATCH_SIZE` or `EPOCHS` in the Setup cell. |
| **Download fails** | Check that `DATA_URL` in the download cell points to a valid GitHub Release asset URL. |
| **`assert` error on `.npz` files** | Re-run the download cell; the zip may not have extracted correctly. Delete `/tmp/*.zip` and retry. |
| **CUDA out of memory** | Reduce `BATCH_SIZE` (e.g., to 8). |
