# Data Directory Guide

This folder holds all the raw SEM micrographs and any manual annotations used for validation.

## Folder Layout
```text
data/
├── data/          # Unprocessed SEM images (.png, .tif)
├── annotated/     # Manual cell masks & annotation files (.png, .json, .xml)
└── README.md
```

## Guidelines

- **Placement**: Drop all new SEM files into `data/raw/`.  
- **Naming Convention**: Use descriptive names, e.g. `PC_CO2_80kX_500nm.png`.  
- **Exclusion from Git**: `.gitignore` ensures `data/raw/` and `data/annotated/` aren’t versioned (large files).  
- **Manual Annotations**: If you outline cells (in Fiji, CVAT, etc.), save mask files in `data/annotated/` with matching base filenames.

## Calibration Information

1. Each SEM must include a visible scale bar (e.g. “500 nm” or “1 µm”).
2. The I/O module (`src/io.py`) will parse the scale bar automatically when possible.
3. For images missing a bar or with non‑standard labeling, create or edit `data/calibration.yaml` to map filenames → `pixels_per_nm` values.
