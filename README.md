# Microcellular Foam SEM Analysis
> SEM‑image analysis pipeline for cell counting and sizing in PC‑CO₂ nanocellular foams.

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Contribution Guidelines](#contribution-guidelines)
- [License](#license)

---

## Features

- **Image I/O & Calibration**: load SEM micrographs, read scale bars, compute pixels‑per‑nm
- **Preprocessing**: denoise with Gaussian blur, normalize contrast
- **Segmentation**: Otsu thresholding, morphological cleanup, connected‑component labeling (with optional watershed)
- **Feature Extraction**: area, equivalent diameter, major/minor axes, circularity
- **Validation**: compare auto results against manual ground truth, compute count‑error% and MAPE
- **(Optional)** Deep‑learning segmentation with a U‑Net model

---

## Getting Started

### Prerequisites

- Python 3.8+  
- Git  
- UNIX‑like shell (bash, zsh, etc.)

### Installation

1. **Clone the repository**
   ```bash
   git clone git@github.com:YourUsername/microcellular-foam-analysis.git
   cd microcellular-foam-analysis
   ```
2. **Create and activate a virtual environment**
    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    ```
3. Install dependencies
    ```bash
    pip install --upgrade pip setuptools wheel packaging
    pip install -r requirements.txt
    ```
4. **Launch Jupyter Lab**
    ```bash
    jupyter lab
    ```

## Project Structure
```text
microcellular-foam-analysis/
├── data/                       # Raw SEM images & annotations (not versioned)
│   └── README.md               # Guidelines for data organization
├── notebooks/                  # Exploratory Jupyter notebooks
├── src/                        # Python modules (I/O, preprocessing, segmentation, analysis)
│   ├── io.py                   # Image loading & calibration functions
│   ├── preprocess.py           # Denoising & normalization routines
│   ├── segment.py              # Thresholding & connected-component labeling
│   └── analyze.py              # Feature extraction & error metrics
├── models/                     # Trained deep-learning models (e.g., U‑Net)
├── results/                    # Generated CSVs, plots, and reports
├── requirements.txt            # Project dependencies
└── README.md                   # Project overview & setup instructions
```

## Usage
1. Add SEM images to `data/raw/` (see `data/README.md`)
2. Preview an image and check calibration:
    ```bash
    python src/io.py data/raw/sample.png
    ```
3. Run full pipeline:
    ```bash
    python run_analysis.py \
    --input data/raw/ \
    --output results/metrics.csv
    ```

## Contribution Guidelines

1. **Branching**

   * `main` = stable releases
   * `develop` = integration
   * `feature/<name>` for new work
2. **Code style**

   * Formatter: `black .`
   * Linter: `flake8`
   * Run `pre-commit install` after cloning
3. **Pull Requests**

   * One feature per PR
   * Link related Issue in the description


## License

This project is licensed under the [MIT License](LICENSE).
