# 🌊 National River Toxin Analysis — Longitudinal EDA & Inferential Statistics

An exploratory data analysis (EDA) and statistical modeling project analyzing chemical properties and heavy metal pollutant levels across five major world river systems (Amazon, Danube, Mississippi, Nile, and Yangtze) between 2018 and 2023.

## 📌 Executive SummaryThis project assesses longitudinal water quality indicators ($N = 1,305$ weekly observations) to identify pollution hot spots, trace temporal toxin trends, and evaluate environmental correlations among heavy metals and chemical indicators ($\text{pH}$, Dissolved Oxygen, Nitrates, Phosphates).

## Key Insights
- Pollution Hierarchy: The Yangtze River exhibits the highest concentration across all primary heavy metals analyzed (Lead: $4.01\text{ mg/L}$, Mercury: $0.78\text{ mg/L}$, Arsenic: $4.97\text{ mg/L}$).
- Temporal Stability: Across 5 years of tracking, heavy metal concentrations show high short-term volatility (jagged seasonal spikes) but remain stationary overall, with no statistically significant upward or downward multi-year trend.
- Significant Separation: A two-sample Welch's $t$-test confirms a statistically significant difference in Lead levels between the Amazon and Nile rivers ($p = 1.34 \times 10^{-67}$).
- Chemical Correlations: $\text{pH}$ exhibits a mild positive correlation with Lead concentrations ($r = 0.32$), indicating that alkalinization slightly aligns with higher dissolved Lead levels.

## 🛠️ Data Stack & Tools

- Language: Python 3.x
- Data Processing: pandas, numpyData Visualization: matplotlib, seabornStatistical
- Modeling & ML: scipy.stats (Independent $t$-test), sklearn.linear_model (Linear Regression)

## 🔬 Data Pipeline & Methodology

1. Data Cleaning & Mean ImputationIdentified missing values across continuous chemical columns ($\text{pH}$, Lead, Mercury, Arsenic, Nitrates).Applied mean imputation across numerical columns (select_dtypes(include=[np.number])) to preserve dataset size without dropping longitudinal timepoints.Converted raw date strings into standard Pandas datetime objects for time-series aggregation.

2. Analytical Findings & Statistical Models

  A. Two-Sample Independent T-Test (Amazon vs. Nile Lead Levels)
  - Hypothesis: Compare mean Lead levels between the Amazon ($2.03\text{ mg/L}$) and Nile ($2.99\text{ mg/L}$).
  - Test Result: $t = -20.238$, $p = 1.338 \times 10^{-67}$
  - Conclusion: Reject $H_0$. The Nile has a significantly higher baseline Lead concentration than the Amazon River.

  B. Simple Linear Regression ($\text{Lead} \sim \text{pH\_Level}$)To evaluate how water acidity influences Lead solubility, a simple linear model was fitted:$$\text{Lead} = \beta_0 + \beta_1 (\text{pH\_Level})$$
  - Slope ($\beta_1$): $0.8029$
  - Intercept ($\beta_0$): $-2.8932$
  - Interpretation: Every $1.0$ unit increase in $\text{pH}$ correlates with an estimated $0.803\text{ mg/L}$ increase in Lead concentration.

## 📊 Visualizations Included
- Bar Charts: Categorical ranking of mean Lead, Mercury, and Arsenic levels across all five river systems.
-Longitudinal Line Plots: Multi-line time series (hue='River_System') showing temporal fluctuations and stationary long-term baselines.
-Correlation Heatmap: Annotated correlation matrix showcasing relationships across all numerical water quality metrics.

## 🎯 Policy & Practical Recommendations

1. Targeted Conservation Allocation: Priority remediation efforts should target the Yangtze River, followed by the Nile and Mississippi, as these systems consistently lead in heavy metal contamination.
2. Industrial & Agricultural Monitoring: Because $\text{pH}$ alone explains only a fraction of the variance in Lead levels ($r = 0.32$), future data collection should incorporate external metrics such as proximity to manufacturing hubs and seasonal rainfall volume.
