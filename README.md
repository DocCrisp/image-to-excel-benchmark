# image-to-excel-benchmark

Public, reproducible **image / scan → Excel table extraction** benchmark focused on **US real-world documents**.

This repository backs the methodology described at [doccrisp.com/benchmark](https://doccrisp.com/benchmark?utm_source=github&utm_medium=readme&utm_campaign=benchmark&utm_content=top).

> **Status:** work in progress. The dataset, `METHOD.md`, and scoring scripts are being prepared; the first dated results will be published here.

> **Accuracy numbers in marketing must match a dated run in `/results`.** Placeholders below are intentional until a run is published.

## Why this exists

Vendors claim high accuracy on "receipts" and "statements" without sharing files or scripts. This repo publishes:

- A **public** document pack (redistributable; no PII)
- **Ground-truth** cell text and structure
- **Scoring scripts** you can run locally
- **Dated result tables** for DocCrisp and third-party tools

A **private holdout** set is reserved for anti-overfit checks and is **not** in this repository.

## Metrics (definitions)

| Metric | Definition | Placeholder |
|--------|------------|-------------|
| Cell text accuracy | Exact / normalized match rate after documented normalization | **[X%]** |
| Structure F1 | Row/column / cell-boundary agreement per METHOD.md | **[X%]** |
| End-to-end usable sheets | Human rubric: share of files needing no manual fix | **[X%]** |

See `METHOD.md` for normalization rules, tooling versions, and free vs paid tier notes.

## Quick start

```bash
git clone https://github.com/DocCrisp/image-to-excel-benchmark.git
cd image-to-excel-benchmark
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python scripts/score_cell_accuracy.py --pred path/to/outputs --gt ground_truth
```

## Dataset

- `datasets/public/` — images + provenance (`provenance.csv`)
- `ground_truth/` — JSON / CSV cell annotations
- License: see `datasets/public/LICENSE` (per-file provenance required)

**Do not** contribute photos of real people\'s financial documents.

## Results

| Date (UTC) | Tool | Tier | Cell text | Structure F1 | Notes |
|------------|------|------|-----------|--------------|-------|
| [YYYY-MM-DD] | DocCrisp | [Free/Paid] | [X%] | [X%] | [build / model note] |
| [YYYY-MM-DD] | [Competitor A] | [Free/Paid] | [X%] | [X%] | |
| [YYYY-MM-DD] | [Competitor B] | [Free/Paid] | [X%] | [X%] | |

Raw outputs: `results/[YYYY-MM-DD]/`

## Contributing vendor results

1. Fork and add outputs under `results/...`
2. Open a PR with tool name, version, tier, and date
3. Or open an issue for corrections

## License

- Code: MIT
- Dataset files: as marked per file (typically CC-BY-4.0 or synthetic internal license)

## Links

- Product: [doccrisp.com](https://doccrisp.com?utm_source=github&utm_medium=readme&utm_campaign=benchmark&utm_content=footer)
- Benchmark page: [doccrisp.com/benchmark](https://doccrisp.com/benchmark?utm_source=github&utm_medium=readme&utm_campaign=benchmark&utm_content=footer)
