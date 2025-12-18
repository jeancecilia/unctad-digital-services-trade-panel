# UNCTAD Digital Services Trade Panel (2010–2023 / 2025 Edition)

## Citation & DOI
For documentation, methodology, and derived analyses, see:
https://devstackph.com/unctad-digital-services-trade-panel/

This dataset is archived on Zenodo with a permanent DOI:
https://doi.org/10.5281/zenodo.17971395

## Overview
This dataset provides a cleaned and structured panel of **country–year digitally-deliverable services trade (exports and imports, USD millions)**, derived from official source data published by **UN Trade and Development (UNCTAD)**.

The dataset was created to support research, policy analysis, journalism, and data-driven content that requires **consistent country naming, comparable time series, and ready-to-use rankings**.

**Canonical dataset page:**  
https://devstackph.com/unctad-digital-services-trade-panel/

---

## Source Data
Primary source:
- **UN Trade and Development (UNCTAD)** – *International trade in digitally deliverable services (UNCTADstat)*  
  Original publication:
  - https://unctadstat.unctad.org/datacentre/reportInfo/US.DigitallyDeliverableServices
  - https://unctadstat.unctad.org/datacentre/dataviewer/US.DigitallyDeliverableServices

The original source data was accessed on **2025-12-18**.

---

## Data Processing & Methodology
The following transformations were applied:

1. Normalized units to **USD millions** using the source unit multiplier.
2. Filtered to annual frequency and total breakdowns to obtain a consistent country-year panel.
3. Removed duplicate observations for the same geography-year-indicator by prioritizing the best observation status.
4. Standardized output schema and column naming for analysis-ready use.
5. Validated derived values against recomputed figures from the raw export.

No imputation was performed.

---

## Dataset Contents
Files included:

- `datasets/unctad_country_year_digital_services_trade_panel.csv` – Main cleaned dataset
- `docs/COLUMN_DICTIONARY.md` – Column descriptions and units
- `docs/KAGGLE_DESCRIPTION.md` – Detailed derivation notes
- `datasets/UNCTAD_DE.csv` – Raw export snapshot used as input

Key fields include:
- `country`
- `iso3`
- `year`
- `dig_services_exports_usd_millions`
- `dig_services_imports_usd_millions`

---

## Intended Use
This dataset is suitable for:
- Academic research and citation
- Policy and trade analysis
- Journalism and reporting
- SEO and content marketing with verifiable data
- Comparative country and regional studies

---

## How to Cite
If you use this dataset, please cite:

> DevStackPH (2025). *UNCTAD Digital Services Trade Panel (2010–2023 / 2025 Edition).* GitHub repository: https://github.com/jeancecilia/unctad-digital-services-trade-panel (accessed YYYY-MM-DD).

DOI: https://doi.org/10.5281/zenodo.17971395

---

## License
This dataset is published under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

You are free to share and adapt the data, provided proper attribution is given.

---

## Related Resources
- Canonical dataset page: https://devstackph.com/unctad-digital-services-trade-panel/
- Derived rankings: https://devstackph.com/top-20-countries-by-digital-services-exports-imports-unctad-yearly-rankings/
- Regional aggregates: https://devstackph.com/regional-digital-services-trade-aggregates-asean-eu27-g7-unctad-derived/

---

## Reproduce
```bash
python scripts/build_unctad_de_panel.py
```

---

## Disclaimer
This dataset is a derived work. The authors are not responsible for interpretations or conclusions drawn from the data.
