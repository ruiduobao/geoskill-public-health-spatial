---
name: geoskill-public-health-spatial
description: 'Spatial scan statistics, kernel density, environment association and accessibility for public health spatial analysis'
---

# 公共卫生空间分析 | Public Health Spatial Analysis

A spatial analysis toolbox for public health, covering disease cluster detection, environmental association and healthcare accessibility assessment.

Kernel density estimation (KDE) maps case density with a 2D Gaussian kernel to identify hot spots; Kulldorff spatial scan statistics use a circular moving window to maximize the log-likelihood ratio (LLR) and detect the most likely clusters of significantly elevated incidence; Pearson correlation quantifies the association between incidence and environmental factors; the distance to the nearest healthcare facility (Euclidean distance transform) assesses service accessibility.

## Dependencies / 依赖

```bash
pip install 'numpy' 'rasterio' 'scipy' 'geopandas' 'shapely'
```

## Usage / 使用方法

### Basic usage

```bash
python geoskill-public-health-spatial.py --bbox 116.0 39.0 117.0 40.0 [other options]
```

### Example 1 (all methods on a synthetic scene, offline)

```bash
python geoskill-public-health-spatial.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

### Example 2 (real population/environment rasters)

```bash
python geoskill-public-health-spatial.py --input data.tif --output-dir ./out
```

### Example 3 (KDE only)

```bash
python geoskill-public-health-spatial.py --input data.tif --method kde --bandwidth 4 --output-dir ./out
```

### Example 4 (spatial scan only)

```bash
python geoskill-public-health-spatial.py --input data.tif --method scan --output-dir ./out
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `case_density.tif` | GeoTIFF | Case kernel density (method=kde/all) |
| `scan_result.json` | JSON | Most likely cluster (LLR/RR/center, method=scan/all) |
| `accessibility.tif` | GeoTIFF | Distance to nearest facility |
| `health_report.json` | JSON | Environmental correlation and accessibility statistics |
| `output-manifest.json` | JSON | Run manifest |

## Data Source / 数据源 / Source

Multi-band GeoTIFF with band order population / environmental factors. Alternatively, use `--synthetic` to generate physically consistent simulated data (fully offline).

## Privacy / 隐私声明 / Privacy

- Runs offline by default; `--synthetic` mode requires no network at all.
- All processing is performed locally; user data is never uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
