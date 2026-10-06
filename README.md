# 🦠 COVID-19 Data Analysis & Visualization

<div align="center">

<img src="assets/covid19_banner.gif" alt="Animated COVID-19 Data Analysis banner" width="100%"/>

### 📊 Explore the spread • compare countries • study outcomes • inspect intervention patterns

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-data%20analysis-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-numerical%20computing-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-visualization-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-statistical%20plots-4c78a8)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Charts](https://img.shields.io/badge/Visualizations-39-ff69b4)
![Rows](https://img.shields.io/badge/Dataset%20Rows-10%2C000-brightgreen)

</div>

---

## 🌟 Project Overview

This project is a **COVID-19 data analysis and visualization notebook** built with **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

The notebook moves through a complete exploratory workflow:

> 📥 Load data → 🔎 Understand data → 🧹 Prepare data → 📈 Visualize → 🧠 Compare relationships → 🏛️ Study interventions → 📝 Summarize findings

The analysis covers **10 countries across 5 regions** and uses **10,000 records with 16 columns**.

### 🌎 Countries included

| Region | Countries |
|---|---|
| 🌏 Asia | India, Japan |
| 🌍 Europe | United Kingdom, Germany, France, Italy |
| 🌎 North America | United States, Canada |
| 🌎 South America | Brazil |
| 🌊 Oceania | Australia |

### 🧾 Data quality recorded in the notebook

- **Rows:** 10,000
- **Columns:** 16
- **Missing values:** 0
- **Duplicate rows:** 0
- **Data types:** 11 integer columns, 2 floating-point columns, 3 string columns

> ✅ The notebook therefore starts its analysis with a clean tabular dataset according to the checks it performs.

---

## 🎯 Goals of the Project

This notebook is designed to answer practical exploratory questions such as:

- 📈 How do daily cases, recoveries, and deaths change over time?
- 🌍 Which countries and regions have the largest cumulative case totals?
- 👥 How do population size and case burden relate?
- 💉 How does cumulative vaccination volume evolve?
- ⚖️ How different are countries when cases are normalized per million people?
- 🏛️ How are government intervention scores distributed?
- 🔗 What relationships appear between cases, deaths, recoveries, intervention scores, and other numeric variables?
- 🔮 What is the average percentage change in cases in the next month at different intervention levels?

---

## 🧰 Tools & Libraries

The notebook imports:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

The visualization styling is initialized with:

```python
sns.set_style('whitegrid')
```

---

## 📂 Dataset Structure

The notebook loads:

```python
df = pd.read_csv('COVID-19 Dataset.csv')
```

> ⚠️ **Important:** the notebook expects `COVID-19 Dataset.csv` to be available when it is run. The uploaded notebook itself does not include that CSV file.

### 🧬 Original columns

| Column | Purpose |
|---|---|
| `Date` | Observation date |
| `Country` | Country name |
| `Region` | Geographic region |
| `Population` | Population used for normalization |
| `New_Cases` | New cases reported for the observation |
| `Cumulative_Cases` | Cumulative reported cases |
| `New_Recovered` | New recoveries |
| `Cumulative_Recovered` | Cumulative recoveries |
| `New_Deaths` | New deaths |
| `Cumulative_Deaths` | Cumulative deaths |
| `Active_Cases` | Active cases |
| `New_Vaccinations` | New vaccination doses |
| `Cumulative_Vaccinations` | Cumulative vaccination doses |
| `Government_Intervention_Score` | Government intervention score |
| `Case_Fatality_Rate_Percent` | Case fatality rate (%) |
| `Recovery_Rate_Percent` | Recovery rate (%) |

---

## 🧹 Data Preparation

Before visualization, the notebook creates several derived fields.

### 📅 Date conversion

```python
df['Date'] = pd.to_datetime(df['Date'], format='%d-%m-%Y')
```

The source date strings are converted into real datetime values so that time-based grouping and plotting work correctly.

### ↕️ Sorting

```python
df = df.sort_values(['Country', 'Date']).reset_index(drop=True)
```

The observations are ordered by country and date.

### 🗓️ Time features

The notebook creates:

```python
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Year_Month'] = df['Date'].dt.strftime('%Y-%m')
```

These fields support yearly and monthly comparisons.

### 👥 Cases per million

```python
df['Cases_per_Million'] = df['New_Cases'] / df['Population'] * 1000000
```

This converts daily new cases into a population-normalized measure.

### ⚰️ Deaths per million

```python
df['Deaths_per_Million'] = df['New_Deaths'] / df['Population'] * 1000000
```

This creates a population-normalized daily death measure.

### 🏛️ Intervention levels

The government intervention score is transformed into three categorical levels:

```python
df['Intervention_Level'] = pd.cut(
    df['Government_Intervention_Score'],
    bins=[-1, 30, 60, 100],
    labels=['Low', 'Medium', 'High']
)
```

So the notebook uses:

| Score | Level |
|---:|---|
| 0–30 | 🟢 Low |
| 31–60 | 🟠 Medium |
| 61–100 | 🔴 High |

### 🧾 Final snapshot

The notebook defines:

```python
last_day = df[df['Date'] == df['Date'].max()]
```

This `last_day` table is then used for final country and region comparisons.

---

# 📊 Complete Visualization Guide

The notebook contains **39 visualization outputs**. The sections below document every plot and what it is intended to show.


## 📈 Line Charts

### 5.1 — Daily new cases, recoveries and deaths

Groups data by date and sums `New_Cases`, `New_Recovered`, and `New_Deaths` across all 10 countries. The three series are displayed as separate panels to compare daily movement.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 5.2 — Average daily new cases per month

Computes the mean `New_Cases` for each country and `Year_Month`, then plots one line per country. Useful for comparing monthly intensity and seasonal/time-period differences.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 5.3 — Cumulative COVID-19 cases

Uses `Cumulative_Cases` over time with country-specific lines. Shows how the accumulated case burden grows across countries.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 5.4 — Cumulative COVID-19 deaths

Uses `Cumulative_Deaths` over time with country-specific lines. Highlights the growth of the cumulative death count.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 5.5 — Cumulative vaccine doses

Uses `Cumulative_Vaccinations` over time by country, giving a visual view of vaccine-dose accumulation.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 📊 Bar Charts

### 6.1 — Total COVID-19 cases by country

Uses the final-date snapshot (`last_day`) and compares `Cumulative_Cases` across countries.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 6.2 — Total deaths by country

Uses `Cumulative_Deaths` from the final snapshot to compare total recorded deaths.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 6.3 — Total recoveries by country

Horizontal bar chart of `Cumulative_Recovered` from the final snapshot, making country labels easy to read.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 6.4 — Total cases per million people

Normalizes final cumulative cases by population: `Cumulative_Cases / Population × 1,000,000`. This improves cross-country comparability by population size.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 6.5 — Total cases by region

Sums final `Cumulative_Cases` by `Region`. Recorded regional totals: Europe 87,247,093; North America 85,269,626; Asia 68,922,043; South America 47,133,678; Oceania 6,939,510.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 6.6 — Outcome of all cases by country

Stacked bars compare `Cumulative_Recovered`, `Active_Cases`, and `Cumulative_Deaths` for each country.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🥧 Pie Charts

### 7.1 — Share of total cases by region

Shows each region's proportion of the combined final cumulative-case total.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 7.2 — Share of total deaths by country

Shows how the combined final cumulative deaths are distributed among the 10 countries.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 7.3 — What happened to all the cases?

Combines final totals for recovered, active, and deaths into one outcome view. The death slice is emphasized with an explode effect.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🔵 Scatter Plots

### 8.1 — Daily new cases vs. daily new deaths

Plots `New_Cases` against `New_Deaths`, colored by region, to inspect their relationship across daily observations.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 8.2 — Population vs. total cases

Compares final population with final cumulative cases for the 10 countries. Country hue distinguishes individual observations.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 8.3 — Government intervention score vs. cases per million

Uses a random sample of 2,000 rows and compares `Government_Intervention_Score` with daily `Cases_per_Million`. Transparency helps reveal the point cloud.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 8.4 — Intervention score vs. cases per million with trend line

Repeats the sampled comparison with a regression line to make the overall linear trend easier to inspect.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 📦 Histograms

### 9.1 — Distribution of daily new cases

Histogram of `New_Cases` using 40 bins, showing the spread of daily case counts across the dataset.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 9.2 — Distribution of case fatality rate

Histogram of `Case_Fatality_Rate_Percent` with a KDE overlay, showing the shape and concentration of fatality-rate values.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 📦 Box Plots

### 10.1 — Daily new cases by country

Compares the distribution, median, spread, and potential outliers of `New_Cases` for each country.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 10.2 — Case fatality rate by country

Compares `Case_Fatality_Rate_Percent` distributions across countries.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 10.3 — Cases per million by intervention level

Groups daily `Cases_per_Million` by the engineered `Low`, `Medium`, and `High` intervention categories.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🎻 Violin Plots

### 11.1 — Case fatality rate by region

Shows the distribution and density of `Case_Fatality_Rate_Percent` within each region.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 11.2 — Recovery rate by region

Shows the distribution and density of `Recovery_Rate_Percent` within each region.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 11.3 — Government intervention score by country

Compares the distribution of intervention scores for each country.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🔥 Heatmaps

### 12.1 — Correlation between the main columns

Displays a correlation matrix for `New_Cases`, `New_Recovered`, `New_Deaths`, `Active_Cases`, `New_Vaccinations`, `Government_Intervention_Score`, `Case_Fatality_Rate_Percent`, and `Recovery_Rate_Percent`.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 12.2 — Average daily cases per million — Country vs Year

Pivot table of mean `Cases_per_Million` by country and year, rendered as an annotated heatmap.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 12.3 — Average daily cases per million — Country vs Month

Pivot table of mean `Cases_per_Million` by country and `Year_Month`, visualized across the full monthly timeline.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 12.4 — Average government intervention score — Country vs Year

Pivot table of average intervention score by country and year, with annotations to show the numeric averages.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🏛️ Government Intervention Analysis

### 13.1 — Average cases per million at each intervention level

Groups `Cases_per_Million` by the predefined `Low`, `Medium`, and `High` intervention levels. Recorded means: Low = **249.41**, Medium = **243.34**, High = **229.93** cases per million.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 13.2a — Average change in cases next month (%)

Builds monthly country-level averages, shifts `New_Cases` to create `Cases_Next_Month`, and computes percentage change. Intervention score is split into three equal-frequency groups using `pd.qcut`. Notebook output: Low = +28.73%, Medium = +5.56%, High = −13.18% (mean change).

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 13.2b — Change in cases next month (%) — box plot

Shows the spread of next-month percentage changes for the same three intervention groups, including variability and outliers.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 13.2c — Intervention score vs. change in cases next month

Regression plot of monthly intervention score against next-month percentage change. Notebook output reports a correlation of −0.59.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 13.3 — United States: new cases and intervention score together

For the United States, overlays a 7-day rolling average of new cases with a 7-day rolling average of government intervention score using two y-axes.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 13.4 — Cases per million by intervention level — violin plot

Repeats the intervention-level comparison with a violin plot to expose distribution shape and density.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


## 🌍 Extra Charts

### 14.1 — Monthly new cases by region

Area chart of monthly summed `New_Cases` by region, showing how regional contributions change over time.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 14.2 — New cases per year by region

Stacked yearly bars showing how each region contributes to annual new-case totals.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.

### 14.3 — Pair plot — all relationships at once

Uses a 500-row random sample of `New_Cases`, `New_Deaths`, `New_Recovered`, and `Government_Intervention_Score` to inspect pairwise relationships and distributions together.

📌 **Reading guide:** focus on trends, differences, distribution shape, clustering, or relative contribution according to the chart type.


---

# 🧠 Key Results Recorded in the Notebook

## 📌 Final combined totals

The notebook's final snapshot calculations report:

| Metric | Result |
|---|---:|
| 🦠 Total cumulative cases | **295,511,950** |
| 💚 Total cumulative recoveries | **249,533,663** |
| ⚰️ Total cumulative deaths | **3,403,611** |
| ✅ Recovery share of cases | **84.4%** |
| ⚠️ Death share of cases | **1.15%** |

These are the notebook's calculated totals for the final date represented in `last_day`.

## 🥇 Country highlights

The summary cell records:

| Insight | Country |
|---|---|
| 🦠 Most total cases | **United States** |
| 📏 Most cases per million | **United Kingdom** |
| 📏 Fewest cases per million | **India** |

## 🌍 Regional highlights

Final cumulative cases by region:

| Region | Cumulative cases |
|---|---:|
| 🇪🇺 Europe | **87,247,093** |
| 🇺🇸 North America | **85,269,626** |
| 🇮🇳 Asia | **68,922,043** |
| 🇧🇷 South America | **47,133,678** |
| 🇦🇺 Oceania | **6,939,510** |

The notebook's summary identifies **Europe** as the region with the most cumulative cases.

---

# 🏛️ Government Intervention Analysis

This part of the notebook goes beyond simple visualization and creates a small observational analysis pipeline.

## 1️⃣ Intervention-level averages

The notebook computes:

```python
avg_cases = df.groupby('Intervention_Level')['Cases_per_Million'].mean()
```

This is a direct comparison of average daily cases per million across the predefined Low / Medium / High score bands.

## 2️⃣ Next-month analysis

The notebook first creates monthly country-level averages for:

- `New_Cases`
- `Government_Intervention_Score`

Then it shifts the case series so that each month is compared with the **next month** for the same country:

```python
monthly['Cases_Next_Month'] = monthly.groupby('Country')['New_Cases'].shift(-1)
```

The percentage change is:

```python
monthly['Change_Percent'] = (
    (monthly['Cases_Next_Month'] - monthly['New_Cases'])
    / monthly['New_Cases'] * 100
)
```

The intervention score is then split into **three equal-frequency groups** with:

```python
pd.qcut(..., 3, labels=['Low', 'Medium', 'High'])
```

### 📉 Recorded mean next-month changes

| Intervention group | Mean change in next-month cases |
|---|---:|
| 🟢 Low | **+28.73%** |
| 🟠 Medium | **+5.56%** |
| 🔴 High | **−13.18%** |

The same calculation also records these medians:

| Intervention group | Median change |
|---|---:|
| 🟢 Low | **+32.64%** |
| 🟠 Medium | **+4.93%** |
| 🔴 High | **−21.03%** |

### 🔗 Intervention score vs. next-month change

The notebook reports a correlation of:

> **−0.59**

This indicates a **moderately negative linear association in this dataset** between the intervention score and the next-month percentage change in cases.

⚠️ **Important interpretation note:** this notebook is exploratory and observational. A negative correlation or a lower average change at higher intervention levels should **not** be presented as proof of causation. Many other factors can influence case counts.

---

# 🧪 Statistical / Exploratory Techniques Used

This project combines several complementary visualization methods:

| Technique | Main purpose |
|---|---|
| 📈 Line chart | Time trends |
| 📊 Bar chart | Category comparison |
| 🥧 Pie chart | Share / composition |
| 🔵 Scatter plot | Relationship between variables |
| 📦 Histogram | Distribution of a variable |
| 📦 Box plot | Median, spread, outliers |
| 🎻 Violin plot | Distribution + density |
| 🔥 Heatmap | Correlation / matrix comparisons |
| 🟦 Area chart | Stacked/continuous regional contribution |
| 🧩 Pair plot | Multiple pairwise relationships |

Using many chart families is useful because no single plot reveals every aspect of a dataset.

---

# 🔍 What Makes This Project Useful?

### 📚 Learning value

This notebook is a strong practice project for learning:

- Pandas grouping and aggregation
- Date/time feature engineering
- Population normalization
- Categorical binning
- Data visualization with Matplotlib
- Statistical visualization with Seaborn
- Correlation analysis
- Pivot tables and heatmaps
- Rolling averages
- Simple regression/trend-line visualization
- Exploratory analysis across countries and regions

### 💼 Portfolio value

It demonstrates a full exploratory data-analysis workflow instead of a single chart:

**Data → Cleaning → Feature Engineering → Visualization → Comparison → Interpretation**

### 🎨 Visualization variety

The project intentionally uses a broad range of visual encodings so the same COVID-19 dataset can be examined from several angles.

---

# ▶️ How to Run the Project

## 1. Clone or download the project

Place these files in the same project folder:

```text
COVID-19-Project/
├── Covid-19.ipynb
├── COVID-19 Dataset.csv
└── assets/
    └── covid19_banner.gif
```

## 2. Install the required packages

```bash
pip install numpy pandas matplotlib seaborn jupyter
```

## 3. Launch Jupyter

```bash
jupyter notebook
```

## 4. Open the notebook

Open:

```text
Covid-19.ipynb
```

## 5. Run all cells

Make sure `COVID-19 Dataset.csv` is in the notebook's working directory before running the data-loading cell.

---

# 🧭 Notebook Roadmap

```text
01  Import libraries
      ↓
02  Load the dataset
      ↓
03  Understand the data
      ↓
04  Prepare the data
      ↓
05  Line charts
      ↓
06  Bar charts
      ↓
07  Pie charts
      ↓
08  Scatter plots
      ↓
09  Histograms
      ↓
10  Box plots
      ↓
11  Violin plots
      ↓
12  Heatmaps
      ↓
13  Impact of government interventions
      ↓
14  Extra charts
      ↓
15  Summary numbers
```

---

# 📈 Suggested Questions to Explore Further

The notebook creates a strong base for additional analysis. Natural extensions include:

- 🌎 Compare countries after adjusting for population and region.
- 💉 Study the relationship between vaccinations and later case patterns.
- ⚰️ Compare fatality and recovery metrics over time rather than only in distributions.
- 📅 Add rolling 7-day or 14-day comparisons for more stable trend analysis.
- 🏛️ Test lagged intervention effects using more formal time-series methods.
- 📐 Add regression diagnostics and confidence intervals.
- 🌍 Build an interactive dashboard with Plotly, Streamlit, or Power BI.

These are extensions rather than results already established by the notebook.

---

# ⚠️ Interpretation & Limitations

This README documents what the notebook does; it does not add causal claims that are not established by the analysis.

A few important limitations to keep in mind:

1. **Observational data:** relationships between intervention scores and cases are associations, not automatic evidence of cause and effect.
2. **Population normalization:** cases per million are useful for comparison, but they do not remove all differences in testing, reporting, healthcare systems, or demographic structure.
3. **Aggregated monthly analysis:** next-month analysis uses monthly averages, which can hide short-term variation.
4. **Equal-frequency intervention grouping:** the `qcut` analysis creates Low / Medium / High groups based on the distribution of observed scores, so those groups are different from the fixed 0–30 / 31–60 / 61–100 bins used earlier.
5. **Final snapshot dependence:** country ranking summaries are based on the dataset's maximum date selected by `last_day`.
6. **Dataset provenance:** this notebook does not document an external source or live-update mechanism for the CSV, so the numbers should be treated as the values present in the project dataset.

---

# 💡 Project Takeaway

The project turns a 10,000-row COVID-19 dataset into a broad exploratory analysis covering **time trends, country comparisons, regional composition, population-normalized rates, distributions, correlations, intervention patterns, and outcome summaries**.

The strongest portfolio feature is the combination of:

> 🧹 **Data preparation**  
> + 📊 **39 visualizations**  
> + 🧠 **exploratory interpretation**  
> + 🏛️ **government-intervention analysis**  
> + 📝 **summary metrics**

---

# 🎥 Video Demo

🔗 **Video Demo:** [Add your video demo link here](YOUR_VIDEO_LINK_HERE)


---

# 🙌 Credits

Built as a **COVID-19 Data Analysis and Visualization** project using Python's data-analysis and visualization ecosystem.

<div align="center">

### 🚀 Keep Exploring Data. Keep Learning. Keep Visualizing. 🚀

**Made with ❤️, 🐍 Python, 📊 Pandas, 🎨 Matplotlib & 🌈 Seaborn**

### **Nihar Sheladiya**

</div>
