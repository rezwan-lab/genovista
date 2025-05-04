
# genovista

**Statistical and Visualization Toolkit for Genomic Mutation Analysis**

---

## Introduction

**Genovista** is a Python-based statistical and visualization toolkit designed to support the analysis of genomic mutation data. It helps researchers explore the relationships between mutation frequency, base substitution rates, and substitution patterns using a range of statistical measures and visualization techniques. The toolkit integrates statistical analysis with clear, publication-quality plots to facilitate meaningful interpretation of mutational data.

---

## Dataset Assumptions

Genovista expects the input data in CSV format with the following columns:

- **`Protein`**: The gene or protein name (optional, non-numeric).
- **`Frequency`**: The occurrence rate of mutations.
- **`Percentage_substitutions`**: Percentage of base substitutions observed.
- **`Substitutions_base`**: Count or index representing substitution types.

The toolkit automatically filters out non-numeric columns during statistical analysis.

---

## Mutational Data Analysis

Genovista supports multiple forms of mutation analysis:

- **Correlation Analysis**: Quantify relationships between mutation frequency and substitution rates.
- **R² Calculations**: Estimate the proportion of variance explained between variables.
- **Genomic Statistical Testing**: Compute statistical significance using p-values and Bayes Factors.
- **Substitution Pattern Exploration**: Understand mutation behavior across base substitutions.

---

## Visualization Tools

Genovista includes multiple visualization modes to complement statistical outputs:

- **Joint Plots**: Visualize bivariate distributions with regression lines and marginal histograms.
- **Correlation Heatmaps**: Display pairwise relationships between numeric variables.
- **Pair Plots**: View all pairwise variable combinations with optional group highlighting.
- **Regression Plots**: Assess linear trends and residual distributions.
- **Clustermaps**: Hierarchically cluster correlation matrices with dendrogram overlays.

---

## Plot Types Covered

| Category              | Features Covered                                                  |
|-----------------------|-------------------------------------------------------------------|
| **Joint Plots**       | Scatterplots, marginal histograms, regression lines, KDE, hexbin |
| **Heatmaps**          | Basic correlation, upper-triangle masking, custom color schemes   |
| **Pair Plots**        | Variable comparisons, hue-based grouping, focused selections      |
| **Regression Plots**  | Simple linear regression, line fitting, variable mapping          |
| **Clustermaps**       | Hierarchical clustering, dendrograms, clustered correlation grids |

---

## Interpretation Guidelines

### Pearson Correlation (`r`)

| `r` Value       | Interpretation           |
|-----------------|--------------------------|
| 0.9 – 1.0       | Very strong positive     |
| 0.7 – 0.9       | Strong positive          |
| 0.5 – 0.7       | Moderate positive        |
| 0.3 – 0.5       | Weak positive            |
| 0.1 – 0.3       | Very weak positive       |
| 0.0             | No correlation           |
| -0.1 – -0.3     | Very weak negative       |
| -0.3 – -0.5     | Weak negative            |
| -0.5 – -0.7     | Moderate negative        |
| -0.7 – -0.9     | Strong negative          |
| -0.9 – -1.0     | Very strong negative     |

### R² Interpretation

- **R² = 0.96** → 96% of the variance in one variable is explained by the other (excellent fit)
- **R² = 0.005** → Less than 1% variance explained (poor fit)

### P-value Significance

- **p < 0.001**: Very strong evidence of association
- **p < 0.05**: Statistically significant
- **p > 0.05**: Not statistically significant

### Bayes Factor (BF10)

- **BF10 > 100**: Extreme evidence for correlation  
- **BF10 > 10**: Strong evidence  
- **BF10 > 3**: Moderate evidence  
- **BF10 < 1**: Evidence against correlation  

---

## Example Results (From Sample Dataset)

- **Frequency vs. Percentage_substitutions**
  - `r = 0.98` → Very strong positive correlation
  - `R² = 0.96` → Excellent model fit
  - `p < 0.001` → Highly significant
  - `BF10` → Strong evidence for correlation

- **Frequency vs. Substitutions_base**
  - `r = 0.07` → Very weak correlation
  - `R² = 0.005` → Negligible variance explained
  - Not statistically significant

---

## Best Practices

- Review multiple correlation metrics (`r`, `R²`, `p-value`) before interpretation.
- Visualize patterns before making statistical claims.
- Always consider biological context alongside statistical findings.
- Identify and inspect outliers; they can heavily influence correlation.
- Choose plots that best match the type of relationship you want to explore.

---

## Key Features Summary

- **Correlation Analysis** using `pingouin`
- **Joint Plots** with regression and KDE overlays
- **Substitution Pattern Analysis**
- **Heatmaps and Clustermaps** for inter-variable exploration
- **Custom Styling**: Color palettes, line styles, and layout adjustments

---

## Dependencies

Genovista requires the following Python packages:

```bash
numpy >= 1.24  
pandas >= 2.0  
seaborn >= 0.12.2  
matplotlib >= 3.7  
pingouin >= 0.5.5  
scipy >= 1.13.0
```

Install them using:

```bash
pip install -r requirements.txt
```

---

## Notes

- The script automatically filters out non-numeric data before computing correlations to prevent errors from string values (e.g., `"3'UTR"`).
- All visualizations are styled for clarity and compatibility with academic publications.

---

## Author

**Dr. Rezwanuzzaman Laskar**
