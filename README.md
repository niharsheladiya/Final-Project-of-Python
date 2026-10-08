<div align="center">

# **Covid-19 Analyzer**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0ea5e9,50:8b5cf6,100:f43f5e&height=190&section=header&text=Covid-19%20Analyzer&fontSize=50&fontColor=ffffff&animation=twinkling&fontAlignY=42&desc=Data%20Analysis%20%26%20Visualization%20with%20Python&descAlignY=64&descSize=18" alt="Covid-19 Analyzer" width="100%"/>

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=8B5CF6&center=true&vCenter=true&width=720&lines=Exploring+295M%2B+COVID-19+cases+across+10+countries;26+charts+%E2%80%A2+7+visualization+types;Did+government+intervention+slow+the+spread%3F;Built+with+Python%2C+Pandas+%26+Seaborn" alt="Typing animation" />
</a>

<br/>

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Computing-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Plots-11557C?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=for-the-badge)

![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![Charts](https://img.shields.io/badge/Charts-26-blueviolet?style=flat-square)
![Records](https://img.shields.io/badge/Records-10%2C000-informational?style=flat-square)
![Countries](https://img.shields.io/badge/Countries-10-orange?style=flat-square)

<br/>

<img src="assets/covid-pulse.svg" alt="Animated epidemic curve" width="100%"/>

</div>

---

## 📑 Table of Contents

- [About the Project](#-about-the-project)
- [Video Demo](#-video-demo)
- [Key Findings](#-key-findings)
- [What's Inside](#-whats-inside)
- [Visual Gallery](#-visual-gallery)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

## 🦠 About the Project

**Covid-19 Analyzer** is an end-to-end exploratory data analysis (EDA) project that turns raw pandemic data into clear, visual stories. It covers **10 countries across 5 regions** and **1,000 days of daily records per country** (starting 1 January 2020), and answers questions such as:

- 📈 How did daily cases, recoveries and deaths evolve over time?
- 🌍 Which countries and regions were hit hardest, both in total and **per million people**?
- 💉 How did vaccination rollouts progress in each country?
- 🛡️ **Did stronger government intervention lead to fewer cases the following month?**

The whole analysis lives in a single, well-organized Jupyter Notebook, with each step explained in plain language so it is easy to follow and reproduce.

---

## 🎬 Video Demo

<div align="center">


🔗 **Video Link:** `PASTE_YOUR_VIDEO_LINK_HERE`

</div>

---

## 🔍 Key Findings

### 🌐 Overall numbers (final day, all 10 countries)

| Metric | Result |
|---|---|
| 🦠 **Total cases** | **295,511,950** |
| 💚 **Total recoveries** | **249,533,663** (84.4% of cases) |
| 🕯️ **Total deaths** | **3,403,611** (1.15% of cases) |
| 🥇 **Most total cases** | United States (74,961,442) |
| 📊 **Highest cases per million** | United Kingdom |
| 📉 **Lowest cases per million** | India |
| 🗺️ **Region with most cases** | Europe (87,247,093) |

### 🛡️ Does government intervention matter?

Months were split into three equal groups (**Low / Medium / High**) by their average Government Intervention Score, then compared with how cases changed **in the following month**:

| Intervention level | Avg. change in next month's cases | Median change |
|:---:|:---:|:---:|
| 🔴 **Low** | **+28.7%** ⬆️ | +32.6% |
| 🟡 **Medium** | **+5.6%** ↗️ | +4.9% |
| 🟢 **High** | **−13.2%** ⬇️ | −21.0% |

> 💡 In this dataset, cases kept **rising** after low-intervention months and **fell** after high-intervention months.
> ⚠️ This is an observational pattern, not proof of cause and effect.

---

## 🧩 What's Inside

The notebook is organized into clear, numbered sections:

| # | Section | What it does |
|:---:|---|---|
| 1 | **Import Libraries** | NumPy, Pandas, Matplotlib, Seaborn |
| 2 | **Load Dataset** | Reads the CSV and checks its shape and columns |
| 3 | **Understand the Data** | `info()`, `describe()`, missing values, duplicates |
| 4 | **Prepare the Data** | Date parsing, sorting, new features, last-day totals |
| 5 | **Line Charts** | Daily trends, monthly averages, cumulative cases / deaths / vaccinations |
| 6 | **Bar Charts** | Total cases, deaths, recoveries, per-million, regional comparison |
| 7 | **Pie Charts** | Share of cases by region, deaths by country, case outcomes |
| 8 | **Scatter Plots** | Cases vs. deaths, population vs. cases, intervention vs. cases per million |
| 9 | **Histograms** | Distribution of daily cases and case fatality rate |
| 10 | **Box Plots** | Spread by country and by intervention level |
| 11 | **Heatmaps** | Correlation matrix, country × year comparisons |
| 12 | **Next-Month Impact Study** | Intervention level vs. change in cases the following month |
| 13 | **Summary Numbers** | Final headline statistics |

### 🛠️ Feature engineering

| New column | Description |
|---|---|
| `Year`, `Month`, `Year_Month` | Extracted from `Date` for time-based grouping |
| `Cases_per_Million` | `New_Cases / Population × 1,000,000` |
| `Deaths_per_Million` | `New_Deaths / Population × 1,000,000` |
| `Intervention_Level` | Score binned into **Low** (≤ 30), **Medium** (31–60), **High** (61–100) |

---

## 🖼️ Visual Gallery

<table>
  <tr>
    <td align="center" width="50%">
      <img src="assets/01-daily-trends.png" alt="Daily new cases, recoveries and deaths"/>
      <br/><sub><b>Daily new cases, recoveries and deaths</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/02-cumulative-cases.png" alt="Cumulative cases by country"/>
      <br/><sub><b>Cumulative cases by country</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="assets/03-total-cases-by-country.png" alt="Total cases by country"/>
      <br/><sub><b>Total cases by country</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/04-case-outcomes.png" alt="Outcome of all cases"/>
      <br/><sub><b>Outcome of all cases: recovered, active, deaths</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="assets/05-correlation-heatmap.png" alt="Correlation heatmap"/>
      <br/><sub><b>Correlation between the main columns</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/06-cases-per-million-heatmap.png" alt="Cases per million heatmap"/>
      <br/><sub><b>Average daily cases per million, country vs. year</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="assets/07-intervention-impact.png" alt="Intervention impact on next month cases"/>
      <br/><sub><b>Change in next month's cases by intervention level</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/08-intervention-boxplot.png" alt="Intervention box plot"/>
      <br/><sub><b>Same study as a box plot, showing the spread</b></sub>
    </td>
  </tr>
</table>

---

## 📂 Dataset

| Property | Value |
|---|---|
| **File** | `COVID-19 Dataset.csv` |
| **Rows × Columns** | 10,000 × 16 |
| **Missing values** | 0 |
| **Duplicate rows** | 0 |
| **Countries (10)** | United States, India, Brazil, United Kingdom, Germany, France, Italy, Canada, Japan, Australia |
| **Regions (5)** | North America, Asia, South America, Europe, Oceania |

<details>
<summary><b>📋 Click to see all 16 columns</b></summary>

<br/>

| Column | Type | Description |
|---|---|---|
| `Date` | date | Day of the record (`dd-mm-yyyy`) |
| `Country` | text | Country name |
| `Region` | text | Continent / region |
| `Population` | integer | Country population |
| `New_Cases` | integer | New cases that day |
| `Cumulative_Cases` | integer | Total cases so far |
| `New_Recovered` | integer | New recoveries that day |
| `Cumulative_Recovered` | integer | Total recoveries so far |
| `New_Deaths` | integer | New deaths that day |
| `Cumulative_Deaths` | integer | Total deaths so far |
| `Active_Cases` | integer | Currently active cases |
| `New_Vaccinations` | integer | Vaccine doses given that day |
| `Cumulative_Vaccinations` | integer | Total doses given so far |
| `Government_Intervention_Score` | integer | Strength of government response (0–100) |
| `Case_Fatality_Rate_Percent` | float | Deaths as a percentage of cases |
| `Recovery_Rate_Percent` | float | Recoveries as a percentage of cases |

</details>

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| 🐍 **Python 3.9+** | Core language |
| 🐼 **Pandas** | Data cleaning, grouping, pivot tables |
| 🔢 **NumPy** | Numerical operations |
| 📊 **Matplotlib** | Base plotting (line, bar, pie, histogram) |
| 🎨 **Seaborn** | Statistical plots (box, scatter, heatmap) |
| 📓 **Jupyter Notebook** | Interactive analysis environment |

---

## 🚀 Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/<your-username>/covid-19-analyzer.git
cd covid-19-analyzer
```

**2. Install the dependencies**

```bash
pip install numpy pandas matplotlib seaborn jupyter
```

**3. Add the dataset**

Place `COVID-19 Dataset.csv` in the same folder as the notebook.

**4. Launch the notebook**

```bash
jupyter notebook Covid-19.ipynb
```

Then choose **Kernel → Restart & Run All** to reproduce every chart. ✅

---

## 🗂️ Project Structure

```text
covid-19-analyzer/
│
├── 📓 Covid-19.ipynb          # Main analysis notebook
├── 📄 COVID-19 Dataset.csv    # Dataset (10,000 rows × 16 columns)
├── 📖 README.md               # You are here
│
└── 🖼️ assets/
    ├── covid-pulse.svg        # Animated epidemic curve
    └── *.png                  # Chart screenshots used in the gallery
```

---

## 🔮 Future Improvements

- [ ] Build an interactive dashboard with **Plotly** or **Streamlit**
- [ ] Add a forecasting model (ARIMA / Prophet) to predict future waves
- [ ] Test the intervention effect with statistical tests and lag analysis
- [ ] Extend the analysis to more countries and real-time data sources
- [ ] Add a vaccination-vs-mortality impact study

---

## ⭐ Show Your Support

If you found this project helpful or interesting, please give it a **star** ⭐ on GitHub. It means a lot!

---

## 👨‍💻 Author

<div align="center">

### Made with ❤️ and Python by

# **Nihar Sheladiya**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:f43f5e,50:8b5cf6,100:0ea5e9&height=140&section=footer&text=Nihar%20Sheladiya&fontSize=30&fontColor=ffffff&animation=twinkling&fontAlignY=68" alt="Nihar Sheladiya footer" width="100%"/>

</div>
