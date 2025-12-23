# The Gender Lens: A World View of Women's Empowerment
An interactive dashboard providing global and regional insights into women's empowerment through exploratory and explanatory features.

**An Interactive Visualization for Global Policy Insight**
![Tableau Dashboard Preview](https://public.tableau.com/static/images/89/89JX3RFW9/1.png)]
(https://public.tableau.com/shared/89JX3RFW9?:display_count=n&:origin=viz_share_link)

*Click the image to explore the interactive dashboard on Tableau Public.*
---
## 1. Project Overview

This project presents **A World View of Women’s Empowerment**, an interactive Tableau-based visualization designed to support evidence-based decision-making in global gender equality policy. Drawing on internationally recognized datasets from the World Bank, UNICEF SOWC, GIWPS, the project consolidates fragmented indicators of women’s social, economic, and health outcomes into a single, interpretable framework.

At the core of the visualization is the **Women’s Empowerment Index (WEI)**, a composite metric constructed to summarize multidimensional aspects of empowerment while preserving transparency and interpretability. The resulting dashboard enables policymakers to rapidly identify regions requiring urgent intervention, compare countries across empowerment dimensions, and diagnose the underlying sources of inequality.

---

## 2. Problem Context

Despite decades of global attention, gender inequality remains persistent and uneven across countries. While international organizations publish hundreds of relevant indicators ranging from literacy rates and labor force participation to maternal mortality and political representation these metrics are often siloed across datasets, reports, and formats.

For policymakers and development organizations, the challenge is not data scarcity but **data overload**. Fragmented indicators make it difficult to answer urgent, policy-relevant questions such as:

* Which countries face the most severe empowerment gaps today?
* Are deficiencies driven primarily by education, economic inclusion, or health and safety?
* Where should limited resources be allocated first?

This project addresses the gap between **data abundance and actionable insight**.

---

## 3. Research Objective

The primary objective of this project is to provide a **unified, visually intuitive system** that allows users to assess women’s empowerment across countries and regions in a comparative and policy-relevant manner.

Specifically, the project seeks to answer:

* Where are women’s empowerment deficits most severe globally?
* How do empowerment outcomes vary across education, economic participation, and safety/health dimensions?
* How can interactive visualization support faster and more informed policy decisions?

---

## 4. Target Audience and Use Case

The visualization is designed for:

* Global policymakers (e.g., World Bank, UN agencies)
* Development economists and policy analysts
* International NGOs and advocacy organizations

The dashboard supports three core policy needs:

1. **Rapid assessment:** Immediate identification of low-performing regions
2. **Comparative insight:** Diagnosis of which empowerment dimensions drive low scores
3. **Actionable intelligence:** Translation of complex data into intervention priorities

---

## 5. Data Sources

The project integrates multiple authoritative international datasets:

* **World Bank – World Development Indicators (WDI)**
  * GDP per capita
  * Labor force participation (male and female)
  * Educational attainment
    
* **World Bank – Women, Business and the Law (WBL)**
  * Legal and institutional gender equality indicators
    
* **UNICEF SOWC**
  * Literacy rates (male and female)
  * Maternal mortality ratio
  * Proportion of seats held by women in national parliaments

All datasets were harmonized at the **country–year level**, covering over 200 countries and territories.

---

## 6. Data Preparation and Integration

Data preprocessing and integration were conducted in R (`DataConjoining.Rmd`) and involved:

1. **Standardization of country identifiers** across all datasets
2. **Reshaping data** into consistent country–year formats
3. **Normalization of indicators** to a common 0–1 scale to ensure comparability
4. **Merging datasets** into a single consolidated file
5. **Handling missing data** by computing dimension scores using available indicators only

The final consolidated dataset is:
* `combined_womens_empowerment_data_with_wei.csv`

---

## 7. Women’s Empowerment Index (WEI) Construction

The WEI is inspired by the **Georgetown Institute for Women, Peace and Security (GIWPS)** framework and follows a hierarchical, two-step construction process.

### Step 1: Dimension Scoring

Eight indicators are grouped into three dimensions:

* **Education & Literacy**
* **Economic Inclusion & Participation**
* **Safety & Health**

Each dimension score is computed as the **mean of its normalized indicators**.

### Step 2: Composite Index

The final WEI score is calculated as the **geometric mean** of the three dimension scores:

* Ensures no single dimension can fully compensate for severe deficits in another
* Produces a bounded score between 0 and 1, where higher values indicate greater empowerment

If a country lacks data for all indicators within a dimension, the dimension score (and hence the WEI) is set to 0.

---

## 8. Visualization Design and Interaction

The dashboard is implemented in **Tableau Public** and emphasizes user-centered design principles.

### Key Features

* **Global choropleth map** for immediate pattern recognition
* **Hierarchical drill-down** from regions to individual countries
* **Dynamic indicator filtering** across empowerment dimensions
* **Rich tooltips** displaying sub-scores and raw indicators

Design decisions were informed by policy workflows, prioritizing clarity, comparability, and interpretability over raw data density.

---

## 9. Key Insights and Use Cases

The dashboard enables users to:

* Identify regions with the most severe empowerment gaps within seconds
* Distinguish whether deficits stem from education, economic inclusion, or health outcomes
* Compare countries within and across regions
* Support evidence-based prioritization of interventions

By transforming a multi-hour analytical task into a short exploratory process, the visualization bridges the gap between data analysis and decision-making.

---

## 10. Limitations

* Indicator selection and aggregation involve normative weighting choices
* Data availability varies across countries and years
* Composite indices may obscure within-dimension variation

These limitations are addressed through transparency: all sub-scores and underlying indicators are accessible via the dashboard.

---

## 11. Repository Structure

```
Womens_Empowerment_Index_Visualization/
├── DataConjoining.Rmd
├── combined_womens_empowerment_data.csv
├── combined_womens_empowerment_data_with_wei.csv
├── UNICEF.xlsx
├── NEW_world_development_indicators.csv
├── NEW_WBL_Indicators.csv
├── Literacy Rate (Adult Male & Female).xlsx
├── Maternal mortality ratio.csv
├── Proportion of seats held by women in national parliament.csv
├── README.md
```

---

## 12. How to Explore and Reproduce

### Interactive Dashboard

The interactive visualization is available on Tableau Public, a preview of which has been provided above

### Reproducing the Data Pipeline

1. Clone the repository
2. Open `DataConjoining.Rmd` in RStudio
3. Install required packages:

```r
install.packages(c("tidyverse", "readxl"))
```

4. Run the script to reproduce the consolidated datasets and WEI scores

---
