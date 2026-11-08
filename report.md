# Overview

Change in the Portland Public Schools (PPS) State School Fund grant between FY 2021-22 and FY 2025-26, split into three factors: the real (above-inflation) increase in the statewide per-ADMw rate, the increase in PPS local revenue $L$ deducted by the formula, and the decline in PPS extended ADMw. All dollar amounts are in FY 2025-26 dollars unless stated.

# Result

| **Factor** | **Variable** | **Effect on PPS grant (\$M)** |
|--------------------|:----:|:----:|
| Real per-ADMw rate increase (rate above West CPI-U) | $E_{\text{rate}}$ | +35.21 |
| Increase in local revenue $L$ | $E_L$ | −54.27 |
| Decline in extended ADMw | $E_{\text{adm}}$ | −39.26 |
| **Net** | $E_{\text{net}}$ | **−58.32** |

Table result: Three-factor decomposition, FY 2021-22 to FY 2025-26, West Region CPI-U deflator.

The net is the gap between the actual FY 2025-26 grant and a counterfactual grant in which the per-ADMw rate grew only with inflation, extended ADMw stayed at its FY 2021-22 value and $L$ stayed at its FY 2021-22 nominal value. Local-revenue growth is the largest single factor; the real rate gain offsets about 38% of the two drags combined.

# Inputs

| **Description** | **Variable** | **Value** | **Status** |
|---|:-:|:-:|---|
| PPS extended ADMw, FY 2021-22 | $A_{21}$ | 55,688.2 | ODE/LRO estimate as of Apr 2023 |
| PPS formula revenue, FY 2021-22 | $F_{21}$ | \$549M | ODE/LRO estimate as of Apr 2023 |
| PPS extended ADMw, FY 2025-26 | $A_{25}$ | 52,441 | LRO projection |
| PPS formula revenue, FY 2025-26 | $F_{25}$ | \$634M | LRO projection |
| `PORTLAND PUBLIC SCHOOLS` tax line, tax year 2021 | $T_{21}$ | \$300M | actual |
| `PORTLAND PUBLIC SCHOOLS` tax line, tax year 2025 | $T_{25}$ | \$360M | approved budget |
| PPS permanent rate (\$ per \$1,000 AV) | $r_{\text{perm}}$ | 4.7743 | statute/certified |
| Full `PORTLAND PUBLIC SCHOOLS` line rate (\$ per \$1,000 AV) | $r_{\text{line}}$ | 5.2781 | certified |
| West Region CPI-U, Dec 2021, % of 1982-84 prices | $\text{CPI}_{21}$ | 296% | BLS, via FRED |
| West Region CPI-U, Dec 2025, % of 1982-84 prices | $\text{CPI}_{25}$ | 344% | BLS, via FRED |

Table inputs: Inputs. Tax year N funds FY N/N+1.

$A_{21}$ and $F_{21}$ from LRO 2023;[^1] $A_{25}$ and $F_{25}$ from LRO 2025;[^2] $T_{21}$ from TSCC FY 2023-24;[^3] $T_{25}$ from TSCC FY 2025-26;[^4] $r_{\text{perm}}$ and $r_{\text{line}}$ from ORS 327 annotations;[^5] $\text{CPI}_{21}$ and $\text{CPI}_{25}$ from FRED.[^6]

Formula revenue is the general purpose grant plus the transportation grant (ORS 327.013), before the high cost disabilities grant and before subtraction of local revenue.

# Derivation

The State School Fund grant to a district is formula revenue minus local revenue (ORS 327.008(2)). Local revenue is taken here as the permanent-rate share of the `PORTLAND PUBLIC SCHOOLS` line, following ORS 327.011(2)(b), which excludes the 2009 gap-rate portion; Common School Fund, county school fund and in-lieu amounts (about \$7M per year) are omitted in both years and cancel in the differences.

$$
\begin{aligned}
k &= \text{permanent-rate share of the PPS line} \\
L_{21} &= \text{local revenue, FY 2021-22} \\
L_{25} &= \text{local revenue, FY 2025-26} \\
R_{21} &= \text{formula revenue per extended ADMw, FY 2021-22} \\
R_{25} &= \text{formula revenue per extended ADMw, FY 2025-26} \\
G_{21} &= \text{grant, FY 2021-22} \\
G_{25} &= \text{grant, FY 2025-26} \\[1ex]
k &= \frac{r_{\text{perm}}}{r_{\text{line}}} \\
&= \frac{4.7743}{5.2781} \\
&= 0.9045 \\[1ex]
L_{21} &= k \times T_{21} \\
&= 0.9045 \times \$300.0\text{M} \\
&= \$271.35\text{M} \\[1ex]
L_{25} &= k \times T_{25} \\
&= 0.9045 \times \$360.0\text{M} \\
&= \$325.62\text{M} \\[1ex]
R_{21} &= \frac{F_{21}}{A_{21}} \\
&= \frac{\$549\text{M}}{55{,}688.2} \\
&= \$9{,}858.46 \\[1ex]
R_{25} &= \frac{F_{25}}{A_{25}} \\
&= \frac{\$634\text{M}}{52{,}441} \\
&= \$12{,}089.78 \\[1ex]
G_{21} &= F_{21} - L_{21} \\
&= \$549\text{M} - \$271.35\text{M} \\
&= \$277.65\text{M} \\[1ex]
G_{25} &= F_{25} - L_{25} \\
&= \$634\text{M} - \$325.62\text{M} \\
&= \$308.38\text{M}
\end{aligned}
$$

Inflation and the inflation-only rate:

$$
\begin{aligned}
i &= \text{West Region CPI-U, Dec 2021 to Dec 2025} \\
R_{\text{infl}} &= \text{FY 2021-22 rate carried forward at inflation only} \\[1ex]
i &= \frac{\text{CPI}_{25}}{\text{CPI}_{21}} - 1 \\
&= \frac{344\%}{296\%} - 1 \\
&= 16.22\% \\[1ex]
R_{\text{infl}} &= R_{21} \times (1 + i) \\
&= \$9{,}858.46 \times 1.1622 \\
&= \$11{,}457.50
\end{aligned}
$$

Counterfactual grant and the three factors:

$$
\begin{aligned}
G_{\text{cf}} &= \text{counterfactual grant: rate at inflation only, ADMw and } L \text{ unchanged} \\
E_{\text{rate}} &= \text{real rate increase, at FY 2021-22 ADMw} \\
E_{\text{adm}} &= \text{ADMw decline, at FY 2025-26 rate} \\
E_L &= \text{local revenue increase} \\
E_{\text{net}} &= \text{net of the three factors} \\[1ex]
G_{\text{cf}} &= R_{\text{infl}} \times A_{21} - L_{21} \\
&= \$11{,}457.50 \times 55{,}688.2 - \$271.35\text{M} \\
&= \$366.70\text{M} \\[1ex]
E_{\text{rate}} &= (R_{25} - R_{\text{infl}}) \times A_{21} \\
&= (\$12{,}089.78 - \$11{,}457.50) \times 55{,}688.2 \\
&= +\$35.21\text{M} \\[1ex]
E_{\text{adm}} &= R_{25} \times (A_{25} - A_{21}) \\
&= \$12{,}089.78 \times (52{,}441 - 55{,}688.2) \\
&= -\$39.26\text{M} \\[1ex]
E_L &= -(L_{25} - L_{21}) \\
&= -(\$325.62\text{M} - \$271.35\text{M}) \\
&= -\$54.27\text{M} \\[1ex]
E_{\text{net}} &= E_{\text{rate}} + E_{\text{adm}} + E_L \\
&= +\$35.21\text{M} - \$39.26\text{M} - \$54.27\text{M} \\
&= -\$58.32\text{M} \\[1ex]
G_{25} - G_{\text{cf}} &= \$308.38\text{M} - \$366.70\text{M} \qquad \text{check} \\
&= -\$58.32\text{M}
\end{aligned}
$$

The inflation-only part of the rate increase, $(R_{\text{infl}} - R_{21}) \times A_{21}$, is \$89.05M; it is absorbed by the deflator and is not one of the three factors.

# Caveats

- $A_{25}$ and $F_{25}$ are LRO projections (Simulation 2025 #1), not final ODE figures; PPS's FY 2025-26 budget book shows 52,392 extended ADMw.
- $T_{25}$ is the approved budget, not collections.
- $L$ omits the non-property-tax items of ORS 327.011(1), so $G_{21}$ and $G_{25}$ are about \$7M high; the differences are unaffected.
- The split of the rate change into inflation and real parts depends on the index; US CPI-U gives $E_{\text{rate}}$ of +\$34.2M (Dec-to-Dec) or +\$21.6M (annual average).
- $E_{\text{adm}}$ is priced at $R_{25}$ and $E_{\text{rate}}$ at $A_{21}$; pricing the other way gives $E_{\text{adm}}$ of −\$37.2M and $E_{\text{rate}}$ of +\$33.2M with the same $E_{\text{net}}$.

[^1]: Legislative Revenue Office, [School Finance Distribution (2021-22 through 2024-25), Simulation 2023 #1](https://olis.oregonlegislature.gov/liz/2023R1/Downloads/CommitteeMeetingDocument/273069), May 10, 2023, Portland SD 1J row.
[^2]: Legislative Revenue Office, [School Finance Distribution 2023-24 through 2026-27, Simulation 2025 #1](https://apps.oregonlegislature.gov/liz/2025R1/Downloads/MeasureAnalysisDocument/92719), as cited in [pps_tax_and_funding_report](https://github.com/astangepdx/pps_tax_and_funding_report) (report.md, footnote 7).
[^3]: TSCC, [Budget Review FY 2023-24: Portland Public Schools](https://www.tsccmultco.com/wp-content/uploads/FY24-Portland-Public-Schools-Budget-Review.pdf) (tax year 2021 actual), as tabulated in pps_tax_and_funding_report, Table district_tax.
[^4]: TSCC, [Budget Review FY 2025-26: Portland Public Schools](https://www.tsccmultco.com/wp-content/uploads/Portland-Public-School-District-FY-26-Budget-Review.pdf) (tax year 2025 approved budget), as tabulated in pps_tax_and_funding_report, Table district_tax.
[^5]: ORS 327.008, 327.011, 327.013 and the PPS rates as annotated in pps_tax_and_funding_report, section Statute Annotations. [Official ORS 327 text](https://www.oregonlegislature.gov/bills_laws/ors/ors327.html).
[^6]: BLS West Region CPI-U, [FRED series CUUR0400SA0](https://fred.stlouisfed.org/data/CUUR0400SA0.txt), as recorded in [sabin_tax_report](https://github.com/astangepdx/sabin_tax_report) data/inflation_indices.csv.
