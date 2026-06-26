# Stack Overflow Developer Survey 2024 — Exploratory Data Analysis

An end-to-end exploratory data analysis of the Stack Overflow Developer Survey 2024, covering 65,000+ developer responses across demographics, tech stack adoption, AI sentiment, remote work, compensation, and job satisfaction.

**Author:** Harsh Kadam
**GitHub:** [github.com/harshskadam31](https://github.com/harshskadam31)

---

## 📌 Project Overview

Stack Overflow's annual developer survey is one of the richest publicly available datasets on the global software industry. This project analyzes the **2024 edition** to answer six core questions about the modern developer workforce:

| # | Question | What it covers |
|---|---|---|
| 1 | **Who are developers?** | Geography, age, education |
| 2 | **What do they use?** | Languages, databases, frameworks, cloud platforms |
| 3 | **How do they feel about AI?** | Adoption rate, sentiment, threat perception |
| 4 | **How do they work?** | Remote work patterns by company size, and its effect on satisfaction |
| 5 | **What do they earn?** | Pay distribution, country gaps, drivers of compensation |
| 6 | **What makes them happy?** | The real factors behind job satisfaction |

A dedicated **India-specific deep dive** is also included, comparing Indian developers against global averages on age, AI adoption, and language preferences.

Each section follows the same structure: **ask a specific question → clean the relevant data → visualize it with an appropriate chart type → interpret the result in plain English.**

---

## 📊 Dataset

- **Source:** [Stack Overflow Developer Survey 2024](https://survey.stackoverflow.co/)
- **Size:** ~65,000 respondents, 114 original columns (narrowed to 32 relevant columns for this analysis)
- **Format:** CSV, downloaded programmatically via `urllib.request` directly from Stack Exchange's official GitHub repository — no manual download step required to reproduce this notebook

---

## 🛠️ Tools & Libraries

- **Python 3**
- **pandas** — data loading, cleaning, transformation
- **NumPy** — numerical operations
- **Matplotlib** + **Seaborn** — all visualizations
- **Jupyter Notebook** (built and run in VS Code)

---

## 🧹 Data Cleaning Highlights

- Resolved schema-vs-data column name mismatches (the official schema file groups multi-select questions like *Language* or *Database* under one conceptual name, while the real dataset splits each into `HaveWorkedWith` / `WantToWorkWith` / `Admired` variants)
- Converted text-based numeric fields (`YearsCode`, `YearsCodePro`) to proper numeric types, handling edge-case strings like `"Less than 1 year"` and `"More than 50 years"`
- Removed extreme outliers from `CompTotal` using a 99th-percentile cutoff (raw entries included impossible values in the billions/trillions — clear data-entry artifacts)
- Split semicolon-delimited multi-select fields (e.g. `LanguageHaveWorkedWith`) into individual countable values using `.explode()`
- Bucketed continuous experience values into ordered career-stage brackets (Junior → Senior) to enable fair, controlled comparisons across education and role

---

## 🔍 Key Findings

**Who developers are**
The survey is dominated by 25–34 year-olds (~40% of respondents), with the US and India as the two largest country groups. Most hold Bachelor's degrees, but a meaningful share are self-taught — this industry remains unusually accessible without a formal credential.

**What they use**
Python and JavaScript dominate the language landscape; SQL consistently ranks top 3–4, confirming it's a core developer skill rather than a niche data tool. PostgreSQL has overtaken MySQL among professional developers. AWS leads cloud platform adoption by a wide margin.

**AI has crossed the mainstream threshold**
Over 60% of developers now use AI tools as a regular part of their workflow. Sentiment is broadly favorable across all experience levels — but a notable share of developers who are positive about AI *still* see it as a threat to job security. These two views coexist rather than cancel out, and skepticism rises slightly with seniority.

**Remote work correlates with satisfaction, but only modestly**
Large enterprises (1,000+ employees) offer less remote flexibility than smaller companies. Remote workers report slightly higher satisfaction than in-person workers — but the gap is small; work arrangement alone doesn't explain satisfaction differences.

**Experience matters more than education for pay — but geography matters most**
Compensation rises sharply in the first 0–10 years of experience, then plateaus with high variance. Education adds a small premium early in a career that nearly disappears by the senior level. Country is the single largest predictor of pay: a senior developer in the US earns several times the median compensation of an equivalent developer in India.

**Developers want to learn — more than anything else**
"Learning New Technology" is the top job satisfaction driver globally. Managers additionally place high value on "Driving Strategy." Companies investing in growth opportunities and engineering quality likely retain talent more effectively than those competing on salary alone.

---

## 📁 Project Structure

```
stackoverflow_survey.ipynb   # Main analysis notebook
README.md                    # This file
```

The notebook is organized into the following sections, in order:
1. Setup & Data Loading
2. Data Preparation & Cleansing
3. Exploratory Analysis & Visualization
   - Demographic Baseline
   - State of the Stack
   - AI Adoption & Sentiment
   - Remote Work
   - Compensation
   - India-Specific Analysis
   - Job Satisfaction Drivers
4. Conclusions

---

## ▶️ How to Run

1. Clone this repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open `stackoverflow_survey.ipynb` in Jupyter Notebook or VS Code
4. Run all cells top to bottom — the dataset is downloaded automatically on first run, no manual data download needed

---

## 💡 Possible Future Extensions

- Language co-occurrence analysis (which languages tend to be known together)
- Tech-stack breadth vs. compensation
- Deeper dive into specific AI tool benefits (`AIBen`) rather than overall sentiment alone
- Industry-level breakdowns of compensation and satisfaction

## 📓 View the Notebook
👉 [Open in Google Colab](https://colab.research.google.com/drive/1Ryz-OShVPHecskhwqYfuE41pU1NbcIfQ#scrollTo=557a0309)
---

*This project was built as part of ongoing data analytics skill development, alongside SQL, Power BI, and Excel coursework, in preparation for Data Analyst roles.*

