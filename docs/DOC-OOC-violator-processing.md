# DOC Out-of-County Violator Processing Analysis

> **Prepared by:** Kambiz Tavabi
> **Last Updated:** March 2026
> **Audience:** CV, targeted resumes, and cover letters for Data Scientist / AI Engineer roles

---

## Project Summary

Designed and executed an end-to-end data analysis pipeline to support operational intelligence for a **state Department of Corrections (DOC)** out-of-county (OOC) violator management program. The project translated a complex, multi-source administrative dataset spanning **six years (2019–2025)** and **123,291 records** into actionable findings on inter-agency cooperation, geographic capacity distribution, and individual case tracking.

The work was delivered as a self-contained, reproducible **Quarto HTML report** with embedded Python analytics, statistical testing, network graph visualizations, and geospatial mapping of Washington State counties.

---

## Technical Stack

| Category | Tools & Libraries |
|---|---|
| Language | Python 3 |
| Data Wrangling | pandas, NumPy |
| Statistical Analysis | SciPy (`chi2_contingency`, Cramér's V), custom correlation pipelines |
| Visualization | Matplotlib, Seaborn, Missingno |
| Geospatial Analysis | GeoPandas, US Census TIGER/Line shapefiles |
| Network Analysis | NetworkX (directed graph, flow visualization) |
| Reporting | Quarto (`.qmd`), embedded HTML tables, multi-panel figures |
| Data Source | Multi-table relational schema (10 entity tables, SQL/Excel extract) |

---

## Data Architecture

The dataset was assembled from **10 relational source tables** joined across person identifiers, facility assignments, law enforcement arrest records, violation documents, response groups, field violations, hearing records, and sanction records. The resulting flat analytical dataset contains **32 fields** organized across six conceptual domains:

- Person identification and admission/release dates
- Movement type and reason codes
- Geographic origin, destination, and release county/office
- Arrest and booking details (arresting agency, location, county acceptance policy)
- Violation processing (response group, violation type, sanction type)
- Confinement details (sanction days, bucketed confinement category)

---

## Analysis Modules

### 1. Data Profiling and Quality Assessment

Implemented a reusable data profiling framework (`analyze_dtypes_and_sparsity`) that computes per-column missingness metrics, cardinality ratios, memory usage, and missing-value co-occurrence patterns. Applied nullity heatmaps to identify structured (non-random) data gaps.

**Key findings:**
- 17 of 32 fields (53%) had zero missing values, confirming high reliability of core offender tracking.
- Structured co-occurrence of missing values identified systemic workflow gaps: arrest/booking fields were jointly absent in ~10,000+ cases, and sanction fields were absent in ~7,700 cases.
- Perfect null-correlation clusters (Pearson r = 1.0) isolated three distinct data entry failure modes, supporting targeted remediation recommendations.

---

### 2. Agency Reporting Sparsity Analysis

Investigated why the `OTHER_AGENCY_NAME` field—which identifies the arresting agency when DOC did not make the arrest—was missing in 45% of records overall.

**Approach:** Chi-square tests of independence across arrest type (`DOC_ARREST`), county of arrest, booking location, and temporal patterns.

**Key findings:**
- The apparent 45% missingness was entirely explained by DOC-made arrests: when DOC made the arrest, the field is structurally inapplicable (100% null by design). Restricting to non-DOC arrests, field completeness was 99.2%.
- Residual missing data (0.8%) was localized to specific booking facilities (SCCC: 50% missing, AHCC: 25% missing) and a data quality dip in 2021–2022, with full recovery by 2023.
- Chi-square test confirmed the dependency was statistically significant (p < 0.0001), demonstrating that apparent data quality issues can be artifacts of business-process logic rather than true data gaps.

---

### 3. County Cooperation Scoring

Developed a **composite cooperation scoring algorithm** (0–100 scale) to rank Washington's 39 counties on their capacity for inter-agency collaboration in violator management.

**Methodology:**
- Three metrics combined with domain-informed weights: agency name completeness (40%), county violator acceptance policy (30%), and non-DOC arrest rate (30%).
- Counties classified across acceptance policy categories (YES / SOMETIMES / NO) and ranked on the composite.

**Business value:** The score provides an actionable, single-metric ranking to identify counties suitable as cooperation models and counties requiring targeted policy or reporting support.

---

### 4. Arrest-to-Booking Cross-County Transport Analysis

Analyzed the geographic relationship between where violators were arrested and where they were booked, using a combination of cross-tabulations, match-rate statistics, temporal trend analysis, directed network graphs overlaid on a geospatial WA State county map, and off-diagonal pattern heatmaps.

**Key findings:**
- **84.0%** of violators were booked in the same county as arrest; **16.0%** required cross-county transport.
- Match rates were stable across the 2018–2024 period (82–86% range), indicating a structurally consistent system.
- DOC-initiated arrests were ~5x more likely to result in cross-county transport (30.5%) than non-DOC arrests (6.2%).
- **King County** (6,144 cross-county incoming cases) and **Thurston County** (5,555) were identified as primary regional hubs; **Pierce County** was the dominant source of out-of-county transfers (Pierce → Thurston: 3,525 cases; Pierce → King: 3,054 cases).
- County acceptance policies measurably influenced transport rates: counties with restrictive policies had higher cross-county rates (NO: 79.6%, SOMETIMES: 77.0%) versus accepting counties (YES: 84.8%).

---

### 5. Admission-to-Release Cross-County Processing Analysis

Examined geographic continuity of violator processing from admission to release, using Cramér's V (categorical association), cross-county flow matrices, directed network graphs, and year-over-year trend decomposition.

**Key findings:**
- **83.6%** of violators were released in the same county as admission (Cramér's V = 0.859, p < 2×10⁻³²⁴), confirming a highly consistent system.
- Cross-county processing rate (16.4%) closely mirrored the arrest-booking rate (16.0%), validating system coherence across both processing stages.
- **Snohomish → King** emerged as the highest-volume cross-county admission-release route (3,192 total cases, 2018–2024), with an increasing temporal trend (slope: +55.9 cases/year).
- **Spokane → Benton** showed a strong declining trend (slope: −127.1), suggesting a policy or capacity shift warranting investigation.
- Over 20,000 total cross-county transfers were identified across the study period, representing a material ongoing transportation investment.

---

### 6. Individual-Level Dual-Mismatch Identification

Identified **unique individuals (DOCNUM)** who experienced both cross-county booking-arrest and cross-county admission-release, enabling case-level prioritization for follow-up and process improvement.

**Key findings:**
- 9,951 individuals had at least one cross-county booking; 10,083 had at least one cross-county admission-release.
- **4,107 individuals (41.3%)** experienced both disruptions—"dual-affected" cases—with an average of 2.1 cross-county booking events and 2.2 cross-county release events per person (max: 22 and 20, respectively).
- A case-level summary table with most-frequent county-pair patterns per individual supports operational prioritization.

---

## Methodological Highlights

- **Reproducible analytical report:** Delivered as a Quarto `.qmd` file rendering to a self-contained HTML document with table of contents, folded code cells, and embedded figures, enabling non-technical stakeholders to consume findings without running code.
- **Reusable helper functions:** Custom Python functions for dataframe profiling, sparsity analysis, and cooperation scoring are documented with NumPy-style docstrings and structured for reuse across projects.
- **Statistical rigor:** Chi-square independence tests, Cramér's V for categorical association, Pearson correlation for null-pattern co-occurrence, and linear trend estimation (NumPy polyfit) applied throughout.
- **Geospatial integration:** US Census TIGER/Line county shapefiles loaded via GeoPandas and reprojected (WGS84 / EPSG:4326, Web Mercator / EPSG:3857, WA State Plane / EPSG:2285) to underlay network flow visualizations with accurate county geometry.
- **Network graph analysis:** Directed weighted graphs (NetworkX) used to model and visualize county-to-county transport flows, with node sizing reflecting in/out flow volume.
- **Structured missing-data reasoning:** Distinguished between structurally determined missingness (business-process artifacts) and true data quality gaps, preventing misattribution of data issues.

---

## Impact and Business Value

| Finding | Operational Implication |
|---|---|
| 16% cross-county booking rate; King/Thurston as hubs | Supports capacity planning and resource allocation for regional processing centers |
| DOC arrests 5× more likely to cross counties | Informs internal arrest protocols and transport cost projections |
| 4,107 dual-affected individuals identified | Enables targeted case management for highest-complexity violators |
| County cooperation scores ranked across 39 counties | Provides a data-driven basis for inter-agency policy engagement |
| Increasing Snohomish → King trend | Flags emerging capacity pressure in King County for proactive planning |
| 45% apparent agency-name gap resolved to 0.8% true gap | Prevents misallocation of data remediation resources |
| Stable 83–84% same-county processing across 6 years | Confirms system reliability; serves as baseline for future anomaly detection |

---

## CV Bullet Points

The following are condensed, impact-forward bullet points for use in a CV or resume:

- Engineered an end-to-end Python analytics pipeline on 123K+ administrative records spanning 6 years to profile data quality, score inter-agency cooperation, and map geographic transport flows for a state corrections agency.
- Developed a composite county cooperation scoring algorithm combining three weighted metrics (agency reporting completeness, acceptance policy, law enforcement involvement rate) across 39 counties to surface actionable inter-agency collaboration rankings.
- Identified 4,107 high-complexity individuals experiencing dual cross-county processing disruptions using set intersection across two independent geographic mismatch analyses, enabling case-level operational prioritization.
- Applied chi-square independence testing and Cramér's V association analysis to disentangle structural data gaps from true data quality issues, preventing misattribution of ~45,000 records as missing data.
- Built geospatial network visualizations combining US Census TIGER/Line shapefiles (GeoPandas) with directed weighted graphs (NetworkX) to map violator transport patterns across Washington State county boundaries.
- Delivered findings as a reproducible Quarto HTML report with embedded statistical outputs, multi-panel figures, and plain-language summaries accessible to non-technical policy stakeholders.

---

## Cover Letter Talking Points

**For Data Scientist roles:**
> "In a recent corrections analytics project, I analyzed 123,000+ records across a 10-table relational schema to uncover cross-county violator transport patterns and rank county cooperation using a custom scoring algorithm. I applied chi-square testing and Cramér's V to distinguish structurally determined data gaps from true quality issues—resolving an apparent 45% missingness rate to a genuine 0.8% gap—and built geospatial network graphs overlaid on census shapefiles to communicate findings to both technical and policy audiences."

**For AI / ML Engineer roles:**
> "I designed a modular, reproducible Python analytics framework—with documented helper functions, structured profiling utilities, and geospatial visualization pipelines—that processed six years of criminal justice administrative data and produced an HTML business intelligence report requiring zero code execution to consume. The pipeline integrated pandas, GeoPandas, NetworkX, and Quarto in a single reproducible artifact, demonstrating both software engineering discipline and domain-driven analytical thinking."

**For Public Sector / Justice-Adjacent roles:**
> "I partnered with a state Department of Corrections to answer operational questions about inter-county violator management: Which counties function as regional processing hubs? Which individuals face the most complex cross-county routing? Which counties most need support improving compliance reporting? Each question was answered with quantified, evidence-backed findings delivered in a format accessible to non-technical decision-makers."

---

*This document was generated from a structured review of the project's Quarto notebook and supporting assets. Findings represent analysis of administrative data; all results should be validated against operational context before external publication.*
