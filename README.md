# Tampa Bay Rental Affordability (2015–2025)

A data visualization project examining the rental affordability gap across the Tampa–St. Petersburg–Clearwater metro area — Hillsborough, Pinellas, and Pasco counties using public federal and market data.

Built in **Tableau** with data prepared in **Python (pandas)**.

---

## Research Questions

1. **Who can afford to rent in Tampa Bay** — and which counties and neighborhoods are furthest from being able to afford a standard two-bedroom apartment?
2. **How does HUD's official Fair Market Rent compare to Zillow's market-observed rent (ZORI)**, and has that gap changed since 2015?

## Why It Matters

Tampa Bay has been one of the fastest-growing metros in the country, and rents have moved faster than incomes for much of the last decade. Federal rent benchmarks like HUD's Fair Market Rent drive how much housing assistance a household receives — so if that benchmark drifts away from what the market is actually charging, the gap becomes a real affordability problem for renters relying on it.

---

## Data Sources

| Dataset | Source | Level | Link |
|---|---|---|---|
| Fair Market Rents (2BR) | U.S. Dept. of Housing and Urban Development | County, annual | https://www.huduser.gov/portal/datasets/fmr.html |
| Median household income | U.S. Census Bureau, American Community Survey | County | https://data.census.gov/ |
| Renter cost burden | HUD Comprehensive Housing Affordability Strategy (CHAS) | Census tract | https://www.huduser.gov/portal/datasets/cp.html |
| Zillow Observed Rent Index (ZORI) | Zillow Research | ZIP code, monthly | https://www.zillow.com/research/data/ |
| Population estimates | U.S. Census Bureau Population Estimates Program | County | https://www.census.gov/programs-surveys/popest.html |
| ZIP ↔ County ↔ Tract crosswalk | HUD USPS Crosswalk Files | — | https://www.huduser.gov/portal/datasets/usps_crosswalk.html |

All data is publicly available and free to download. See `data/` for the cleaned files used in the workbook.

---

## Repository Structure

```
data/          Cleaned CSVs used as Tableau data sources
charts/        Exported visualizations (PNG)
report/        Written report (introduction, methodology, analysis, conclusion)
*.twbx         Tableau packaged workbook
```

## Method

The five tables are joined in Tableau through a ZIP ↔ county ↔ tract crosswalk, which allows county-level rent and income figures to be compared against tract-level cost-burden data and ZIP-level market rents in the same workbook. Affordability is measured as the gap between the income needed to afford the local 2BR Fair Market Rent at the standard 30%-of-income threshold and the actual median household income for that county.

The dashboard includes a parameter control that switches the rent benchmark between **HUD FMR** and **Zillow ZORI**, so the same counties and time period can be viewed under both measures, plus a dashboard action that filters the map and trend charts to a selected county.

## Key Findings

- The direction of the affordability gap depends on which rent benchmark is used — a finding that only becomes visible when HUD FMR and ZORI are charted on the same axes.
- Cost burden is not evenly distributed within counties; tract-level data shows concentrations that county averages hide entirely.
- Using estimated rather than published income figures materially changed the results, which is why all income and FMR values here are pulled from source rather than interpolated where possible.

## Limitations

- FMR values for 2015–2016 are interpolated; 2017–2025 are published HUD figures.
- ACS estimates carry margins of error that are not displayed in the visualizations.
- HUD FMR is set at the metro level for some geographies, so county-level comparisons should be read with that in mind.

## Further Questions

- How does renter cost burden in Tampa Bay compare with other fast-growing Florida metros such as Orlando or Sarasota–Bradenton over the same period?
- Does the FMR-to-market-rent gap correspond to measurable differences in housing voucher utilization rates?

---

## Viewing the Workbook

Open the `.twbx` file in Tableau Desktop or the free Tableau Reader. The packaged workbook includes all data extracts, so no additional downloads are needed.
