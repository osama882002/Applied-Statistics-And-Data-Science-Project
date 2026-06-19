# Applied Statistics & Data Science Project (Assignment 9)

## 📌 Project Description

This project delivers a comprehensive end-to-end applied statistical analysis using Python to solve advanced data science questions.

The project is divided into two main analytical domains:

1. **Chess Games Dataset Analysis**

   * Investigating player behaviors
   * Studying skill tiers and match outcomes
   * Testing independence between variables
   * Calculating confidence intervals for game duration

2. **WHO Dataset Analysis**

   * Studying socioeconomic factors affecting global life expectancy
   * Building correlation matrices
   * Identifying possible hidden confounding variables

---

# 📁 Project Structure

```text
Assignment-9-Applied-Statistics/

├── data/
│   └── raw/
│       └── chess_games.csv
│
├── notebook/
│   └── Assignment_9_Analysis.ipynb
│
├── output/
│   └── charts/
│       ├── distributions_analysis.png
│       ├── correlation_heatmap.png
│       ├── chi_square_outcomes.png
│       └── confidence_intervals.png
│
├── venv/
│
├── .gitignore
│
├── requirements.txt
│
└── README.md
```

---

# 🛠️ Technologies Used

The project was developed using Python 3 and scientific computing libraries:

| Library          | Purpose                          |
| ---------------- | -------------------------------- |
| Pandas           | Data manipulation and analysis   |
| NumPy            | Numerical operations             |
| SciPy            | Statistical hypothesis testing   |
| Matplotlib       | Data visualization               |
| Seaborn          | Statistical charts and heatmaps  |
| Jupyter Notebook | Interactive analysis environment |

---

# 🚀 How to Run

## 1. Create Virtual Environment

```bash
python -m venv venv
```

---

## 2. Activate Environment

### Windows

```bash
.\venv\Scripts\activate
```

### macOS/Linux

```bash
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Run Notebook

Launch Jupyter:

```bash
jupyter notebook
```

Open:

```text
notebook/Assignment_9_Analysis.ipynb
```

Run all cells sequentially.

The notebook will:

* Load datasets
* Perform statistical analysis
* Generate visualizations
* Save charts inside:

```text
output/charts/
```

---

# 📊 Analytical Questions & Results

---

# 📈 AQ1 & AQ2

# Descriptive Statistics & Distribution Analysis

## 🔹 Chess Turns Analysis

| Metric             |     Value |
| ------------------ | --------: |
| Mean               | 60.465999 |
| Median             | 55.000000 |
| Standard Deviation | 33.570585 |
| IQR                | 42.000000 |
| Skewness           |  0.897284 |

### Interpretation

The distribution is:

**Moderately positively skewed**

because:

```text
Mean > Median
```

A small number of extremely long games increase the average duration.

---

## Normality Test

Shapiro-Wilk Test:

```text
p-value = 0.000000
```

Result:

```text
Reject H0
```

The variable is not normally distributed.

---

## Log Transformation

Applying:

```python
np.log1p()
```

changed skewness:

Before:

```text
0.897
```

After:

```text
-1.37
```

The transformation overcorrected the distribution.

Therefore, keeping the original distribution or using non-parametric approaches is more appropriate.

---

# 🔹 Rating Difference Analysis

| Metric             |      Value |
| ------------------ | ---------: |
| Mean               | 173.091435 |
| Median             | 115.000000 |
| Standard Deviation | 179.214854 |
| IQR                | 196.000000 |
| Skewness           |   1.948676 |

---

## Interpretation

The variable shows:

```text
Strong positive skewness
```

because some games contain very large rating differences.

---

## Log Transformation Result

Before:

```text
Skewness = 1.95
```

After:

```text
Skewness = -0.90
```

The extreme right tail was reduced significantly.

---

# 🌍 AQ3

# WHO Correlation Matrix + Confounder Discussion

## Strong Positive Correlations with Life Expectancy

| Feature                         | Correlation |
| ------------------------------- | ----------: |
| schooling                       |       0.752 |
| income_composition_of_resources |       0.725 |
| bmi                             |       0.568 |

---

## Strong Negative Correlations

| Feature             | Correlation |
| ------------------- | ----------: |
| adult_mortality     |      -0.696 |
| hiv/aids            |      -0.557 |
| thinness_1-19_years |      -0.477 |

---

# Confounder Discussion

Correlation does not prove causation.

Example:

Schooling has a strong positive relationship with life expectancy.

However, GDP can act as a confounding variable.

Higher GDP can lead to:

* Better education
* Better healthcare
* Lower mortality rates

Therefore, GDP may partially explain the relationship between education and life expectancy.

---

# 🎲 AQ4

# Chi-Squared Test — Rating Group vs Win Rate

## Hypothesis

### H0

There is no relationship between rating group and match outcome.

### H1

There is a relationship between rating group and match outcome.

---

## Contingency Table

| Rating Tier  | Black Win | Draw | White Win |
| ------------ | --------: | ---: | --------: |
| Beginner     |      5266 |    0 |       587 |
| Intermediate |      4433 |   37 |      4953 |
| Advanced     |      3469 |   39 |      4376 |
| Expert       |       679 |   11 |       969 |

---

# Statistical Results

| Metric               |   Value |
| -------------------- | ------: |
| Chi-Square Statistic |   57.30 |
| Degrees of Freedom   |       6 |
| p-value              | < 0.001 |
| Cramér's V           |   0.038 |

---

# Interpretation

Since:

```text
p < 0.001
```

we reject the null hypothesis.

There is a statistically significant relationship.

However:

```text
Cramér's V = 0.038
```

shows a very small practical effect.

The relationship exists statistically but has limited real-world impact.

---

# 🥾 AQ5

# 95% Confidence Intervals

Comparison:

* Rated games
* Unrated games

---

# Rated Games

Sample size:

```text
n = 16,155
```

Mean:

```text
62.0 turns
```

## Parametric CI

```text
(61.4 , 62.5)
```

## Bootstrap CI

```text
(61.4 , 62.5)
```

---

# Unrated Games

Sample size:

```text
n = 3,903
```

Mean:

```text
54.3 turns
```

## Parametric CI

```text
(53.3 , 55.3)
```

## Bootstrap CI

```text
(53.2 , 55.3)
```

---

# Final Conclusion

Both confidence interval methods produced almost identical results because of the large sample sizes.

The confidence intervals do not overlap.

Therefore:

Rated games are significantly longer than unrated games.

This suggests players behave differently when official ranking points are involved.

---

# 📌 Project Summary

This project demonstrates practical usage of:

* Descriptive statistics
* Distribution analysis
* Normality testing
* Data transformation
* Correlation analysis
* Confounding variables
* Chi-square hypothesis testing
* Effect size measurement
* Confidence intervals
* Bootstrap inference

---

# Author

Osama
