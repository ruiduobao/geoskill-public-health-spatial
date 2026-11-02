# Public Health Spatial Analysis (geoskill-public-health-spatial)

> Spatial scan statistics, kernel density, environment association and accessibility for public health spatial analysis

---

## 1. Overview

A spatial analysis toolkit for public health, covering disease-cluster detection, environmental association, and healthcare accessibility assessment. Kernel density estimation (KDE) maps case points with a 2D Gaussian kernel to identify hotspots; Kulldorff spatial scan statistics use circular moving windows that maximize the log-likelihood ratio (LLR) to detect the most likely cluster with significantly elevated incidence; Pearson correlation quantifies the association between incidence and environmental factors; distance to the nearest healthcare facility (Euclidean distance transform) assesses service accessibility.

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-public-health-spatial.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `case_density.tif` | GeoTIFF | Case kernel density (method=kde/all) |
| `scan_result.json` | JSON | Most likely cluster (LLR/RR/center, method=scan/all) |
| `accessibility.tif` | GeoTIFF | Distance to nearest facility |
| `health_report.json` | JSON | Environmental correlations and accessibility statistics |
| `output-manifest.json` | JSON | Run manifest |


## 6. Technical Principle

(see SKILL.md for details)

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
