# PPS State School Fund grant, FY 2021-22 to FY 2025-26: three factors

Change in the Portland Public Schools (PPS) State School Fund grant between FY 2021-22 and FY 2025-26, split into three factors: the real (above-inflation) increase in the statewide per-ADMw rate, the increase in PPS local revenue `L` deducted by the formula, and the decline in PPS extended ADMw. All dollar amounts are in FY 2025-26 dollars unless stated.

## 1. Result

| Factor | Variable | Effect on PPS grant<br>($M) |
|---|---|---|
| Real per-ADMw rate increase (rate above West CPI-U) | `E_rate` | +35.3 |
| Increase in local revenue `L` | `E_L` | −54.3 |
| Decline in extended ADMw | `E_adm` | −39.3 |
| Net | `E_net` | **−58.2** |

*Table 1-1: Three-factor decomposition, FY 2021-22 to FY 2025-26, West Region CPI-U deflator.*

The net is the gap between the actual FY 2025-26 grant and a counterfactual grant in which the per-ADMw rate grew only with inflation, extended ADMw stayed at its FY 2021-22 value and `L` stayed at its FY 2021-22 nominal value. Local-revenue growth is the largest single factor; the real rate gain offsets about 38% of the two drags combined.

## 2. Inputs

| Description | Variable | Value | Status | Source |
|---|---|---|---|---|
| PPS extended ADMw, FY 2021-22 | `A_21` | 55,688.2 | ODE/LRO estimate as of Apr 2023 | [1] |
| PPS formula revenue, FY 2021-22 | `F_21` | $549,440,740 | ODE/LRO estimate as of Apr 2023 | [1] |
| PPS extended ADMw, FY 2025-26 | `A_25` | 52,441 | LRO projection | [2] |
| PPS formula revenue, FY 2025-26 | `F_25` | $634,000,000 | LRO projection | [2] |
| `PORTLAND PUBLIC SCHOOLS` tax line, tax year 2021 | `T_21` | $300,000,000 | actual | [3] |
| `PORTLAND PUBLIC SCHOOLS` tax line, tax year 2025 | `T_25` | $360,000,000 | approved budget | [4] |
| PPS permanent rate ($ per $1,000 AV) | `r_perm` | 4.7743 | statute/certified | [5] |
| Full `PORTLAND PUBLIC SCHOOLS` line rate ($ per $1,000 AV) | `r_line` | 5.2781 | certified | [5] |
| West Region CPI-U, Dec 2021 | `CPI_21` | 296.102 | BLS, via FRED | [6] |
| West Region CPI-U, Dec 2025 | `CPI_25` | 343.789 | BLS, via FRED | [6] |

*Table 2-1: Inputs. Tax year N funds FY N/N+1.*

Formula revenue is the general purpose grant plus the transportation grant (ORS 327.013), before the high cost disabilities grant and before subtraction of local revenue.

## 3. Derivation

The State School Fund grant to a district is formula revenue minus local revenue (ORS 327.008(2)). Local revenue is taken here as the permanent-rate share of the `PORTLAND PUBLIC SCHOOLS` line, following ORS 327.011(2)(b), which excludes the 2009 gap-rate portion; Common School Fund, county school fund and in-lieu amounts (about $7M per year) are omitted in both years and cancel in the differences.

```
k      = r_perm / r_line              # permanent-rate share of the PPS line
       = 4.7743 / 5.2781 = 0.9045
L_21   = k * T_21                     # local revenue, FY 2021-22
       = 0.9045 * $300.0M = $271.4M
L_25   = k * T_25                     # local revenue, FY 2025-26
       = 0.9045 * $360.0M = $325.6M
R_21   = F_21 / A_21                  # formula revenue per extended ADMw, FY 2021-22
       = $549,440,740 / 55,688.2 = $9,866.4
R_25   = F_25 / A_25                  # formula revenue per extended ADMw, FY 2025-26
       = $634,000,000 / 52,441 = $12,089.8
G_21   = F_21 - L_21                  # grant, FY 2021-22
       = $549.4M - $271.4M = $278.1M
G_25   = F_25 - L_25                  # grant, FY 2025-26
       = $634.0M - $325.6M = $308.4M
```

Inflation and the inflation-only rate:

```
i      = CPI_25 / CPI_21 - 1          # West Region CPI-U, Dec 2021 to Dec 2025
       = 343.789 / 296.102 - 1 = 16.10%
R_infl = R_21 * (1 + i)               # FY 2021-22 rate carried forward at inflation only
       = $9,866.4 * 1.1610 = $11,455.3
```

Counterfactual grant and the three factors:

```
G_cf   = R_infl * A_21 - L_21         # rate at inflation only, ADMw and L unchanged
       = $11,455.3 * 55,688.2 - $271.4M = $366.6M
E_rate = (R_25 - R_infl) * A_21       # real rate increase, at FY 2021-22 ADMw
       = ($12,089.8 - $11,455.3) * 55,688.2 = +$35.3M
E_adm  = R_25 * (A_25 - A_21)         # ADMw decline, at FY 2025-26 rate
       = $12,089.8 * (52,441 - 55,688.2) = -$39.3M
E_L    = -(L_25 - L_21)               # local revenue increase
       = -($325.6M - $271.4M) = -$54.3M
E_net  = E_rate + E_adm + E_L
       = +$35.3M - $39.3M - $54.3M = -$58.2M
check  : G_25 - G_cf = $308.4M - $366.6M = -$58.2M
```

The inflation-only part of the rate increase, `(R_infl - R_21) * A_21`, is $88.5M; it is absorbed by the deflator and is not one of the three factors.

## 4. Caveats

- `A_25` and `F_25` are LRO projections (Simulation 2025 #1), not final ODE figures; PPS's FY 2025-26 budget book shows 52,392 extended ADMw.
- `T_25` is the approved budget, not collections.
- `L` omits the non-property-tax items of ORS 327.011(1), so `G_21` and `G_25` are about $7M high; the differences are unaffected.
- The split of the rate change into inflation and real parts depends on the index; US CPI-U gives `E_rate` of +$33.7M (Dec-to-Dec) or +$21.1M (annual average).
- `E_adm` is priced at `R_25` and `E_rate` at `A_21`; pricing the other way gives `E_adm` of −$32.0M and `E_rate` of +$33.3M with the same `E_net`.

## 5. Sources

1. Legislative Revenue Office, *School Finance Distribution (2021-22 through 2024-25), Simulation 2023 #1*, May 10, 2023, Portland SD 1J row. https://olis.oregonlegislature.gov/liz/2023R1/Downloads/CommitteeMeetingDocument/273069
2. Legislative Revenue Office, *School Finance Distribution 2023-24 through 2026-27, Simulation 2025 #1*, as cited in [pps_tax_and_funding_report](https://github.com/astangepdx/pps_tax_and_funding_report) (report.md, footnote 7). https://apps.oregonlegislature.gov/liz/2025R1/Downloads/MeasureAnalysisDocument/92719
3. TSCC, *Budget Review FY 2023-24: Portland Public Schools* (tax year 2021 actual), as tabulated in pps_tax_and_funding_report, Table district_tax. https://www.tsccmultco.com/wp-content/uploads/FY24-Portland-Public-Schools-Budget-Review.pdf
4. TSCC, *Budget Review FY 2025-26: Portland Public Schools* (tax year 2025 approved budget), as tabulated in pps_tax_and_funding_report, Table district_tax. https://www.tsccmultco.com/wp-content/uploads/Portland-Public-School-District-FY-26-Budget-Review.pdf
5. ORS 327.008, 327.011, 327.013 and the PPS rates as annotated in pps_tax_and_funding_report, section Statute Annotations. https://www.oregonlegislature.gov/bills_laws/ors/ors327.html
6. BLS West Region CPI-U, FRED series CUUR0400SA0, as recorded in [sabin_tax_report](https://github.com/astangepdx/sabin_tax_report) data/inflation_indices.csv. https://fred.stlouisfed.org/data/CUUR0400SA0.txt
