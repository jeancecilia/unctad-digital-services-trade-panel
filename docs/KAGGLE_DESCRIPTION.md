# UNCTAD Country-Year Digital Services Trade Panel Dataset

## Overview
This dataset is a cleaned, analysis-ready country-year panel derived from the UNCTAD Digital Economy and Technology database export (via World Bank Data360 structure `WB.DATA360:DS_DATA360(1.2)`).

Each row represents one `iso3` country (or aggregate region code) in one year, with internationally traded **digitally-deliverable services** values for exports and imports.

## Files
- `datasets/UNCTAD_DE.csv`
  - Raw export used as the source.
- `datasets/unctad_country_year_digital_services_trade_panel.csv`
  - Cleaned country-year panel (this dataset).
- `scripts/build_unctad_de_panel.py`
  - Reproducible build script.

## What is measured
- **Digitally-deliverable services exports**
- **Digitally-deliverable services imports**

The panel is built from these two indicators in the raw file:
- `UNCTAD_DE_DIG_SERVTRADE_ANN_EXP`
- `UNCTAD_DE_DIG_SERVTRADE_ANN_IMP`

## Units
Values are stored as **USD millions**.

The raw export contains a scaling field `UNIT_MULT`. The build script normalizes all values to a consistent multiplier of **6 (Millions)**, so the output columns are directly comparable across all rows.

## Coverage
- **Frequency**: annual
- **Time variable**: `year` (4-digit year)
- **Geography**: ISO3 codes and some aggregate region codes (as provided by the source)

## Data cleaning / filtering rules
To produce a clean country-year panel, the script keeps only observations matching:
- `FREQ = A` (annual)
- `SEX = _T` (total)
- `AGE = _T` (total / no age breakdown)
- `URBANISATION = _T` (total)
- `COMP_BREAKDOWN_1 = _Z` (not applicable)
- `COMP_BREAKDOWN_2 = _Z` (not applicable)
- `COMP_BREAKDOWN_3 = _Z` (not applicable)

If multiple observations exist for the same `(iso3, year, indicator)`, the script selects the best one by observation status priority (`A` preferred over `E`, `P`, then `O`).

## Output columns
- `country`
  - Country or region name.
- `iso3`
  - ISO3 country code or aggregate geography code from the source.
- `year`
  - Calendar year.
- `dig_services_exports_usd_millions`
  - International exports of digitally-deliverable services (USD millions).
- `dig_services_imports_usd_millions`
  - International imports of digitally-deliverable services (USD millions).

## How to reproduce
From the repository root:

```bash
python scripts/build_unctad_de_panel.py
```

This reads `datasets/UNCTAD_DE.csv` and writes `datasets/unctad_country_year_digital_services_trade_panel.csv`.

## Notes and limitations
- Missing values are left blank (NA) when the source reports a missing observation.
- Some `iso3` codes in the source represent **aggregates/regions** (e.g. `WLD` for World).

## Suggested use cases
- Country comparisons of digitally-deliverable services trade
- Time-series charts per country
- Regression / panel models using `iso3` and `year` keys
