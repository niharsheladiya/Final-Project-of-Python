# 🦠 COVID-19 Data Analysis & Visualization

<div align="center">

<img src="covid19_updated_banner.gif" alt="Animated COVID-19 data analysis banner" width="100%"/>

### 📊 Explore the spread • Compare countries • Analyze outcomes • Study interventions

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Visualization-4c78a8)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Rows](https://img.shields.io/badge/Rows-10%2C000-2ea44f)
![Columns](https://img.shields.io/badge/Columns-16-6f42c1)
![Plots](https://img.shields.io/badge/Visualizations-26-ff69b4)

</div>

---

## 🎥 Video Demo

> **Add your project demonstration video link here.**

🔗 **Demo Video:** `YOUR_VIDEO_LINK_HERE`

<!-- Example:
[▶️ Watch the COVID-19 Project Demo](https://your-video-link-here)
-->

---

## 🌟 Project Overview

This project is an updated **COVID-19 Data Analysis and Visualization** notebook created with **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

The notebook follows a complete exploratory data-analysis workflow:

```text
📥 Load Data
    ↓
🔎 Understand Data
    ↓
🧹 Prepare & Engineer Features
    ↓
📈 Visualize Trends
    ↓
🌍 Compare Countries & Regions
    ↓
🔗 Study Relationships
    ↓
🏛️ Analyze Government Intervention
    ↓
📝 Summarize the Dataset
```

The updated project contains:

- **10,000 rows**
- **16 columns**
- **10 countries**
- **5 regions**
- **26 plotted visualizations**

It focuses on daily COVID-19 activity, cumulative outcomes, vaccination progress, population-normalized cases, government intervention scores, distributions, correlations, and month-to-month case changes.

---

# 🎯 Project Objectives

The project is designed to explore questions such as:

- 📈 How do daily new cases, recoveries, and deaths change over time?
- 🦠 How do cumulative cases grow across countries?
- ⚰️ How do cumulative deaths compare?
- 💉 How does cumulative vaccination volume change?
- 🌍 Which countries have the highest total case counts?
- 👥 How do population size and total cases relate?
- 📏 Which countries have the highest cases per million people?
- 🌎 Which region contributes the largest total number of cases?
- 🔵 What relationship appears between daily new cases and daily new deaths?
- 🏛️ How are cases per million distributed across intervention levels?
- 📅 What happens to average cases in the **next month** at different intervention levels?

---

# 🧰 Technologies & Libraries

The notebook uses:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style('whitegrid')
```

### 🐍 Main technologies

| Technology | Use in project |
|---|---|
| 🐼 Pandas | Data loading, cleaning, grouping, aggregation, pivot tables |
| 🔢 NumPy | Numerical operations |
| 📊 Matplotlib | Core charts and plotting |
| 🎨 Seaborn | Statistical and categorical visualizations |
| 📓 Jupyter Notebook | Interactive analysis environment |

---

# 📂 Project Structure

Recommended GitHub structure:

```text
COVID-19-Project/
│
├── 📓 Covid-19(1).ipynb
├── 📄 COVID-19 Dataset.csv
├── 📘 README.md
└── 🎞️ covid19_updated_banner.gif
```

> ⚠️ The notebook expects the dataset file to be named **`COVID-19 Dataset.csv`** and available in the notebook's working directory.

---

# 📊 Dataset Overview

The notebook loads the dataset using:

```python
df = pd.read_csv('COVID-19 Dataset.csv')
```

## 🌍 Countries

The updated notebook contains these 10 countries:

| Region | Countries |
|---|---|
| 🌎 North America | United States, Canada |
| 🌏 Asia | India, Japan |
| 🌎 South America | Brazil |
| 🇪🇺 Europe | United Kingdom, Germany, France, Italy |
| 🌊 Oceania | Australia |

## 🗺️ Regions

The five regions are:

```text
North America
Asia
South America
Europe
Oceania
```

---

# 🧬 Dataset Columns

The notebook works with **16 original columns**:

| Column | Description |
|---|---|
| `Date` | Daily observation date |
| `Country` | Country name |
| `Region` | Geographic region |
| `Population` | Population used for normalization |
| `New_Cases` | Newly reported cases |
| `Cumulative_Cases` | Total accumulated cases |
| `New_Recovered` | Newly reported recoveries |
| `Cumulative_Recovered` | Total accumulated recoveries |
| `New_Deaths` | Newly reported deaths |
| `Cumulative_Deaths` | Total accumulated deaths |
| `Active_Cases` | Active cases |
| `New_Vaccinations` | Newly recorded vaccinations |
| `Cumulative_Vaccinations` | Cumulative vaccination doses |
| `Government_Intervention_Score` | Government intervention score |
| `Case_Fatality_Rate_Percent` | Case fatality rate |
| `Recovery_Rate_Percent` | Recovery rate |

---

# 🔍 Initial Data Understanding

The notebook performs the following checks:

```python
print('Rows and columns:', df.shape)
print(df.columns.tolist())
df.info()
df.describe()
```

### ✅ Data-quality checks

The notebook records:

- **Rows:** 10,000
- **Columns:** 16
- **Missing values:** 0
- **Duplicate rows:** 0

### 📏 Data types

The dataset contains:

- **11 integer columns**
- **2 floating-point columns**
- **3 string columns**

---

# 🧹 Data Preparation & Feature Engineering

The notebook prepares the dataset before analysis.

## 📅 1. Convert the date

```python
df['Date'] = pd.to_datetime(df['Date'], format='%d-%m-%Y')
```

This converts the original date strings into real datetime values.

## ↕️ 2. Sort the data

```python
df = df.sort_values(['Country', 'Date']).reset_index(drop=True)
```

The rows are sorted by country and date.

## 🗓️ 3. Create time features

```python
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Year_Month'] = df['Date'].dt.strftime('%Y-%m')
```

These fields make yearly and monthly analysis easier.

## 👥 4. Calculate cases per million

```python
df['Cases_per_Million'] = (
    df['New_Cases'] / df['Population'] * 1000000
)
```

This normalizes daily cases using population size.

## ⚰️ 5. Calculate deaths per million

```python
df['Deaths_per_Million'] = (
    df['New_Deaths'] / df['Population'] * 1000000
)
```

This creates a population-adjusted daily death measure.

## 🏛️ 6. Create intervention categories

```python
df['Intervention_Level'] = pd.cut(
    df['Government_Intervention_Score'],
    bins=[-1, 30, 60, 100],
    labels=['Low', 'Medium', 'High']
)
```

The fixed score bands are:

| Score | Category |
|---:|---|
| 0–30 | 🟢 Low |
| 31–60 | 🟠 Medium |
| 61–100 | 🔴 High |

## 📌 7. Select the final date

```python
last_day = df[df['Date'] == df['Date'].max()]
```

This creates a final-date snapshot used for country and regional comparisons.

---

# 📈 Visualization 1 — Line Charts

The updated notebook contains **5 line-chart analyses**.

## 1.1 📈 Daily new cases, recoveries and deaths

The notebook groups the dataset by date:

```python
daily = df.groupby('Date')[[
    'New_Cases',
    'New_Recovered',
    'New_Deaths'
]].sum()
```

### What this chart shows

Three time-series panels display:

- 🦠 New cases
- 💚 New recoveries
- ⚰️ New deaths

The values are summed across all 10 countries for each date.

### 🎯 Why it is useful

It provides a high-level view of how the three daily measures change over the complete observation period.

---

## 1.2 📅 Average daily new cases per month

The notebook groups by `Year_Month` and `Country` and calculates the mean of `New_Cases`.

### What this chart shows

Each country gets its own line, allowing month-by-month comparison.

### 🎯 Why it is useful

It reduces daily noise and makes it easier to compare monthly patterns across countries.

---

## 1.3 🦠 Cumulative COVID-19 cases

The notebook uses:

```python
sns.lineplot(
    x='Date',
    y='Cumulative_Cases',
    hue='Country',
    data=df
)
```

### What this chart shows

The accumulated case count for every country over time.

### 🎯 Why it is useful

It highlights the overall growth of cumulative cases rather than day-to-day changes.

---

## 1.4 ⚰️ Cumulative COVID-19 deaths

This visualization tracks:

```text
Date → Cumulative_Deaths
```

with one line per country.

### 🎯 Why it is useful

It helps compare how cumulative deaths evolve over the observation period.

---

## 1.5 💉 Cumulative vaccine doses

The notebook plots:

```text
Date → Cumulative_Vaccinations
```

for every country.

### 🎯 Why it is useful

It provides a visual view of vaccination accumulation over time.

---

# 📊 Visualization 2 — Bar Charts

The updated notebook contains **5 bar-chart comparisons**.

## 2.1 🦠 Total COVID-19 cases by country

Uses the final-date values from:

```python
last_day['Cumulative_Cases']
```

### 🎯 Purpose

Compare final cumulative case totals across the 10 countries.

---

## 2.2 ⚰️ Total deaths by country

Uses:

```python
last_day['Cumulative_Deaths']
```

### 🎯 Purpose

Compare final cumulative deaths across countries.

---

## 2.3 💚 Total recoveries by country

Uses a horizontal bar chart for:

```python
last_day['Cumulative_Recovered']
```

### 🎯 Purpose

The horizontal orientation makes country labels easier to read while comparing cumulative recoveries.

---

## 2.4 📏 Total cases per million people

The notebook calculates:

```python
cases_per_million = (
    last_day['Cumulative_Cases']
    / last_day['Population']
    * 1000000
)
```

### 🎯 Purpose

This gives a population-normalized final case comparison.

### 📌 Final-date values recorded by the notebook data

| Country | Cases per million |
|---|---:|
| 🇦🇺 Australia | 266,904.23 |
| 🇧🇷 Brazil | 221,284.87 |
| 🇨🇦 Canada | 271,268.00 |
| 🇫🇷 France | 350,443.72 |
| 🇩🇪 Germany | 247,398.99 |
| 🇮🇳 India | 38,372.29 |
| 🇮🇹 Italy | 300,750.65 |
| 🇯🇵 Japan | 127,746.31 |
| 🇬🇧 United Kingdom | 370,712.91 |
| 🇺🇸 United States | 226,469.61 |

The notebook summary identifies:

> 🥇 **Highest cases per million: United Kingdom**  
> 🟢 **Lowest cases per million: India**

---

## 2.5 🌍 Total cases by region

The notebook calculates:

```python
region_cases = last_day.groupby('Region')['Cumulative_Cases'].sum()
```

### Final regional totals

| Region | Total cumulative cases |
|---|---:|
| 🇪🇺 Europe | **87,247,093** |
| 🌎 North America | **85,269,626** |
| 🌏 Asia | **68,922,043** |
| 🌎 South America | **47,133,678** |
| 🌊 Oceania | **6,939,510** |

### 🥇 Highest region

The notebook records:

> **Europe** as the region with the most cases.

---

# 🥧 Visualization 3 — Pie Charts

The project contains **3 composition charts**.

## 3.1 🌍 Share of total cases by region

Uses the regional totals from `region_cases`.

### 🎯 Purpose

Shows how the total final-date case count is distributed among the five regions.

---

## 3.2 ⚰️ Share of total deaths by country

Uses:

```python
last_day['Cumulative_Deaths']
```

### 🎯 Purpose

Shows each country's share of the combined final-date deaths.

---

## 3.3 🔄 What happened to all the cases?

The notebook combines:

```python
recovered = last_day['Cumulative_Recovered'].sum()
active = last_day['Active_Cases'].sum()
deaths = last_day['Cumulative_Deaths'].sum()
```

and displays:

- 💚 Recovered
- 🟠 Active
- ❤️ Deaths

### 🎯 Purpose

Provides a composition-style view of the final case outcomes across the 10-country snapshot.

---

# 🔵 Visualization 4 — Scatter Plots

The updated notebook includes **3 scatter plots**.

## 4.1 🔗 Daily new cases vs. daily new deaths

```python
sns.scatterplot(
    x='New_Cases',
    y='New_Deaths',
    hue='Region',
    data=df,
    alpha=0.5
)
```

### 🎯 Purpose

Explore the relationship between daily new cases and daily new deaths, while distinguishing observations by region.

---

## 4.2 👥 Population vs. total cases

This plot uses the final snapshot:

```python
sns.scatterplot(
    x='Population',
    y='Cumulative_Cases',
    hue='Country',
    s=200,
    data=last_day
)
```

### 🎯 Purpose

Explore how final population size relates to cumulative case totals.

---

## 4.3 🏛️ Government intervention score vs. cases per million

The notebook takes a reproducible sample:

```python
sample = df.sample(2000, random_state=1)
```

and compares:

```text
Government_Intervention_Score
vs.
Cases_per_Million
```

### 🎯 Purpose

Explore whether visible patterns exist between intervention scores and population-normalized daily cases.

---

# 📦 Visualization 5 — Histograms

The project includes **2 histograms**.

## 5.1 📊 Distribution of daily new cases

Uses 40 bins for `New_Cases`.

### 🎯 Purpose

Understand the spread and frequency of daily case values across the dataset.

---

## 5.2 ⚖️ Distribution of case fatality rate

Uses:

```python
sns.histplot(
    df['Case_Fatality_Rate_Percent'],
    bins=30,
    kde=True
)
```

### 🎯 Purpose

Show the distribution of case fatality rates and its density shape.

---

# 📦 Visualization 6 — Box Plots

The project uses **3 box plots**.

## 6.1 🌍 Daily new cases by country

### 🎯 Purpose

Compare:

- Median
- Spread
- Variability
- Potential outliers

of `New_Cases` across countries.

---

## 6.2 ⚖️ Case fatality rate by country

Compares the distribution of:

```text
Case_Fatality_Rate_Percent
```

for each country.

---

## 6.3 🏛️ Cases per million by intervention level

Compares `Cases_per_Million` across:

- 🟢 Low
- 🟠 Medium
- 🔴 High

intervention categories.

---

# 🔥 Visualization 7 — Heatmaps

The updated notebook contains **3 heatmaps**.

## 7.1 🔥 Correlation heatmap

The notebook examines correlations among:

```python
[
    'New_Cases',
    'New_Recovered',
    'New_Deaths',
    'Active_Cases',
    'New_Vaccinations',
    'Government_Intervention_Score',
    'Case_Fatality_Rate_Percent',
    'Recovery_Rate_Percent'
]
```

### 🎯 Purpose

Quickly inspect pairwise linear relationships among the major numerical variables.

---

## 7.2 📅 Average daily cases per million — Country vs Year

A pivot table is created using:

```python
df.pivot_table(
    index='Country',
    columns='Year',
    values='Cases_per_Million',
    aggfunc='mean'
)
```

### 🎯 Purpose

Compare average population-normalized daily cases across countries and years.

---

## 7.3 🏛️ Average government intervention score — Country vs Year

The notebook creates a country-by-year pivot table of average intervention scores.

### 🎯 Purpose

Compare intervention intensity across countries and years in one compact matrix.

---

# 📅 Special Analysis — What Happened to Cases in the Next Month?

One of the most interesting parts of the updated notebook is its **next-month analysis**.

## 1️⃣ Monthly aggregation

The notebook calculates country-level monthly averages for:

- `New_Cases`
- `Government_Intervention_Score`

```python
monthly = df.groupby(
    ['Country', 'Year_Month']
)[
    ['New_Cases', 'Government_Intervention_Score']
].mean().reset_index()
```

## 2️⃣ Find the next month's cases

```python
monthly['Cases_Next_Month'] = (
    monthly.groupby('Country')['New_Cases'].shift(-1)
)
```

This compares each country-month with its following month.

## 3️⃣ Calculate percentage change

```python
monthly['Change_Percent'] = (
    (monthly['Cases_Next_Month'] - monthly['New_Cases'])
    / monthly['New_Cases']
    * 100
)
```

## 4️⃣ Create three equal-frequency intervention groups

```python
monthly['Level'] = pd.qcut(
    monthly['Government_Intervention_Score'],
    3,
    labels=['Low', 'Medium', 'High']
)
```

> ⚠️ These **Low / Medium / High groups are quantile-based** for this analysis. They are different from the earlier fixed score bins of 0–30, 31–60, and 61–100.

## 5️⃣ Remove months with no next month

The final month of each country cannot have a next-month comparison, so the notebook removes those rows:

```python
monthly = monthly.dropna()
```

---

# 📊 Next-Month Results

The notebook records the following group statistics:

| Intervention level | Mean change next month | Median change next month |
|---|---:|---:|
| 🟢 Low | **+28.73%** | **+32.64%** |
| 🟠 Medium | **+5.56%** | **+4.93%** |
| 🔴 High | **−13.18%** | **−21.03%** |

### 📌 How to read this result

In this notebook's dataset:

- Low-intervention months are associated with a **positive average change** into the next month.
- Medium-intervention months show a **smaller positive average change**.
- High-intervention months show a **negative average change**.

### ⚠️ Important

This is an **exploratory observational analysis**. It does not by itself establish that intervention scores caused the subsequent change in cases.

---

# 📋 Summary Numbers from the Notebook

The final summary cell records:

| Metric | Result |
|---|---:|
| 🦠 Total cumulative cases | **295,511,950** |
| 💚 Total recoveries | **249,533,663** |
| ⚰️ Total deaths | **3,403,611** |
| ✅ Recoveries as share of cases | **84.4%** |
| ⚠️ Deaths as share of cases | **1.15%** |
| 🥇 Most total cases | **United States** |
| 📏 Most cases per million | **United Kingdom** |
| 📏 Fewest cases per million | **India** |
| 🌍 Region with most cases | **Europe** |

---

# 📅 Observation Period

The notebook starts with observations dated:

**01-01-2020**

With 1,000 daily observations per country in the 10,000-row dataset, the displayed dataset spans through:

**26-09-2022**

The final country snapshot in the notebook is therefore based on that maximum date.

---

# 🧪 Exploratory Analysis Techniques Used

This updated project demonstrates a broad range of practical EDA techniques:

| Technique | Used for |
|---|---|
| 🧹 Data cleaning | Preparing reliable analysis columns |
| 🗓️ Date feature engineering | Year, month, monthly periods |
| 👥 Population normalization | Cases per million, deaths per million |
| 🏛️ Categorization | Intervention-level grouping |
| 📈 Time-series analysis | Daily, monthly and cumulative trends |
| 📊 Aggregation | Country and regional summaries |
| 🔵 Relationship analysis | Scatter plots |
| 📦 Distribution analysis | Histograms and box plots |
| 🔥 Correlation analysis | Heatmap |
| 📅 Lag analysis | Next-month case change |
| 📐 Pivot tables | Country/year comparisons |

---

# 🧠 Main Project Takeaways

### 🌍 Country comparison

The notebook's final snapshot shows that the **United States** has the highest total cumulative cases among the 10 countries analyzed.

### 📏 Population-normalized comparison

When cumulative cases are divided by population and scaled per million people, the **United Kingdom** ranks highest while **India** ranks lowest in this dataset's final snapshot.

### 🌎 Regional comparison

**Europe** records the largest final cumulative case total among the five regions.

### 🏛️ Intervention analysis

The next-month analysis shows a decreasing average case-change pattern from the Low group to the High group:

```text
Low       +28.73%  📈
Medium     +5.56%  ↗️
High      -13.18%  📉
```

Again, these are associations observed in the notebook's data and should not be treated as causal proof.

---

# ⚠️ Important Limitations

This is an exploratory data-analysis project, so results should be interpreted with care.

### 1. 🔎 Observational analysis

The notebook identifies patterns and relationships. It does not establish causal effects.

### 2. 🌍 Country differences

Countries can differ in population structure, reporting practices, testing, healthcare systems, and many other factors.

### 3. 📏 Per-million normalization

Cases per million improves population comparability, but it does not eliminate other sources of cross-country difference.

### 4. 📅 Monthly aggregation

Monthly averages can hide short-term spikes and rapid changes.

### 5. 🏛️ Two intervention definitions

The notebook uses:

- Fixed bins for the main `Intervention_Level`
- Quantile groups using `pd.qcut()` for the next-month analysis

These should not be interpreted as the same classification system.

### 6. 📦 Dataset scope

The README and conclusions describe the exact dataset represented in the updated notebook rather than assuming live or continuously updated external COVID-19 data.

---

# ▶️ How to Run the Project

## 1. Install Python

Use Python 3.x.

## 2. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn jupyter
```

## 3. Keep the files together

```text
Covid-19(1).ipynb
COVID-19 Dataset.csv
README.md
covid19_updated_banner.gif
```

## 4. Start Jupyter Notebook

```bash
jupyter notebook
```

## 5. Open the notebook

Open:

```text
Covid-19(1).ipynb
```

## 6. Run the notebook

Run all cells from top to bottom.

---

# 🗂️ Notebook Roadmap

```text
📌 1. Import libraries
        ↓
📌 2. Load the dataset
        ↓
📌 3. Understand the data
        ↓
📌 4. Prepare the data
        ↓
📌 5. Line charts
        ↓
📌 6. Bar charts
        ↓
📌 Pie charts
        ↓
📌 Scatter plots
        ↓
📌 Histograms
        ↓
📌 Box plots
        ↓
📌 Heatmaps
        ↓
📌 Next-month intervention analysis
        ↓
📌 Summary numbers
```

---

# 🚀 Future Improvements

This notebook can be extended into a larger data-science project with:

- 📊 Interactive Plotly dashboards
- 🌐 Streamlit web application
- 🗺️ Country-level map visualizations
- 💉 Vaccination-rate analysis
- 📅 7-day / 14-day rolling averages
- 🔗 Lagged intervention analysis
- 📐 Statistical regression models
- 📈 Forecasting and time-series models
- 🎛️ Interactive country and date filters

---

# ⭐ Why This Project Is Portfolio-Friendly

This project is more than a collection of charts. It demonstrates a full workflow:

```text
📥 Data Loading
      +
🧹 Data Preparation
      +
🧮 Feature Engineering
      +
📊 Exploratory Visualization
      +
🌍 Country/Region Comparison
      +
🔗 Relationship Analysis
      +
🏛️ Intervention Analysis
      +
📝 Summary & Interpretation
```

That makes it suitable as a **Python / Data Analysis / EDA portfolio project**.

---

# 💡 Quick Project Highlights

<div align="center">

| 📊 Dataset | 🌍 Coverage | 📈 Visualizations | 🏛️ Special Analysis |
|---|---:|---:|---|
| 10,000 rows | 10 countries / 5 regions | 26 plots | Next-month intervention analysis |

</div>

---

# 🎥 Demo Video Placeholder

### ▶️ Project Demonstration

Paste your video URL below:

```text
YOUR_VIDEO_LINK_HERE
```

Example Markdown:

```markdown
[🎥 Watch the COVID-19 Project Demo](YOUR_VIDEO_LINK_HERE)
```

---

# 🙌 Credits

This project was created as a **COVID-19 Data Analysis and Visualization** study using Python's data-analysis and visualization ecosystem.

<div align="center">

### 🐍 Python • 🐼 Pandas • 🔢 NumPy • 📊 Matplotlib • 🎨 Seaborn

### 🚀 Keep Exploring Data. Keep Learning. Keep Visualizing.

# **Nihar Sheladiya** ❤️

</div>

---

<div align="center">

### 🦠📊 COVID-19 DATA ANALYSIS • EXPLORE • VISUALIZE • UNDERSTAND 📊🦠

</div>
