# SKG-dataset

Dataset for the paper **"Skeleton Construction for Scientific Information System with Multi-View Graph Learning"** (submitted to *Expert Systems with Applications*).

## Overview

This repository contains the raw data obtained from the Microsoft Academic Graph (MAG) API, used to construct citation network skeletons in the SKG framework. The dataset comprises 21,688 scientific papers along with their associated metadata, field classifications, authors, journals, and conferences.

## Repository Structure

| File | Entries | Size | Description |
|------|---------|------|-------------|
| `01_data_prepare.json` | 21,688 | ~181 MB | Paper metadata with citation relationships |
| `03_filed_all.json` | 16,080 | ~23 MB | Field-of-study metadata and hierarchy |
| `05_conference_all.json` | 18 | ~2 KB | Conference/series metadata |
| `06_author_all.json` | 130,511 | ~13 MB | Author metadata |
| `07_journal_all.json` | 868 | ~105 KB | Journal metadata |

## Data Description

### `01_data_prepare.json` — Paper Metadata

Each entry is keyed by MAG paper ID. Fields:

| Field | Type | Description |
|-------|------|-------------|
| `Ti` | string | Paper title |
| `D` | string | Publication date (YYYY-MM-DD) |
| `AA` | list[dict] | Author affiliations (`AfId`, `AfN`, `AuId`, `AuN`, `S`) |
| `AW` | list[str] | Abstract words (tokenized) |
| `IA` | string | Inverted abstract text |
| `F` | list[dict] | Fields of study (`FId`, `FN`) |
| `J` | dict | Journal information (`JId`, `JN`) |
| `VFN` | string | Venue full name |
| `CC` | int | Citation count |
| `RId` | list[int] | Reference paper IDs (citation links) |

### `03_filed_all.json` — Field Metadata

Each entry is keyed by field ID. Fields:

| Field | Type | Description |
|-------|------|-------------|
| `FN` | string | Field name |
| `FL` | int | Field level in hierarchy |
| `FP` | string | Parent field name |
| `FC` | list[dict] | Child fields (`FId`, `FN`) |
| `CC` | int | Total citation count of the field |
| `PC` | int | Total publication count of the field |

### `05_conference_all.json` — Conference Metadata

Each entry is keyed by conference series ID. Fields: `CN` (normalized name), `CC` (total citation count), `PC` (total publication count).

### `06_author_all.json` — Author Metadata

Each entry is keyed by author ID. Fields: `AuN` (author name), `CC` (total citation count), `PC` (total publication count).

### `07_journal_all.json` — Journal Metadata

Each entry is keyed by journal ID. Fields: `JN` (journal name), `CC` (total citation count), `PC` (total publication count).

## Data Source

All data were retrieved from the **Microsoft Academic Graph (MAG)** via its public API (retired in December 2021). The data were collected between April and May 2021.

## License

This dataset is made available under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license.

## Citation

If you use this dataset, please cite our paper:

```bibtex
@article{SKG2025,
  title     = {Skeleton Construction for Scientific Information System with Multi-View Graph Learning},
  author    = {<authors>},
  journal   = {Expert Systems with Applications},
  year      = {2025},
  note      = {Under review}
}
```
