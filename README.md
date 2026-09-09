# Rice Supply Chain Analysis

Analysis of rice production-side efficiency across Decision Making Units (DMUs) in West Java, Indonesia.

The dataset are obtained from [Mendeley Data](https://data.mendeley.com/datasets/k7c2sgmsj5/1)

The project evaluates how efficiently each DMU converts land and production input costs into production value. Although the dataset is related to the rice supply chain, the available variables primarily represent production-side inputs and output value.

therefore, this project does not cover downstream logistics, storage, milling, distribution, or market dynamics.

## Objectives

The analysis focuses on:

* Comparing DMU economic and production efficiency.
* Understanding the relationship between input costs and production value.
* Evaluating production and cost efficiency relative to land area.
* Comparing economic performance across regencies.
* Identifying groups of DMUs with similar production characteristics.
* Building predictive models for production value.

## Methodology

### 1. Statistical Testing

Statistical hypothesis testing is used to determine whether production performance differs across regencies.

1. **Kruskal-Wallis Test:** The Kruskal-Wallis H test is used as a non-parametric test for comparing the distribution of the selected performance metric across multiple regency groups.

2. **Welch's ANOVA:** Welch's ANOVA is used as a parametric alternative for testing whether group means differ when equal-variance assumptions may not hold.

3. **Dunn's Post-Hoc Test:** When a significant group-level difference is identified, Dunn's post-hoc test with Holm p-value adjustment is used to determine which groups differ from each other.

Statistical decisions are evaluated using a significance level of α = 0.05.

### 2. OLS Regression Analysis

OLS regression is used to estimate the association between production input costs and production value while controlling for the other cost variables.

The model uses:

* **Target:** Production value.
* **Predictors:** Land lease, labor, seed, fertilizer, pesticide, and equipment rental costs.
* **Inference:** regression coefficients, standard errors, t-statistics, and p-values.

Regional differences are additionally evaluated using non-parametric statistical testing, followed by Dunn's post-hoc test with Holm adjustment where appropriate.

### 3. Machine Learning

Production value prediction is evaluated using multiple regression approaches:

* Linear Regression (Baseline)
* XGBoost Regressor
* Random Forest Regressor

For the tree-based models, Random Forest and XGBoost are statistically compared using a paired t-test. The test compares the fold-level cross-validation RMSE scores of the best-performing hyperparameter configuration from each model.

### 4. DMU Clustering

K-Means clustering is used to segment DMUs based on production scale and economic characteristics.

The appropriate number of clusters is evaluated using the Elbow Method. The elbow point is used to determine a suitable number of clusters for the final segmentation.
