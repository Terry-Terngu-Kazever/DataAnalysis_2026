Project Description:
This project focuses on cleaning and analyzing a clinical dataset. The main tasks included exploring the data, finding and visualizing missing values, removing variables with too many missing entries, filling in missing data using different imputation methods, and detecting outliers.

Three main assignments were completed:

1. Testing the missing data mechanism using Little’s MCAR Test.

2. Performing imputation with the MICE package (Random Forest and Predictive Mean Matching methods).

3. Detecting outliers using boxplots and the LOF (Local Outlier Factor) algorithm.

___________

Data Description:
The dataset was provided by my lecturer and contains 1,148 records with 41 clinical variables. These variables include:

Hormones: hormone1–hormone14

Lipids: lipids1–lipids5 and lipid_pero1–lipid_pero5

Antioxidants: antioxidant1–antioxidant5

Carbohydrate metabolism variables

Factor/outcome variables: outcome, factor_eth, factor_h, factor_pcos, factor_prl
Some variables had missing data, which were handled during imputation.

_____
R Environment:

IDE: RStudio

R version: 4.5.3

Key Packages Used
dplyr (data manipulation), tidyr (reshaping), ggplot2 (visualization), skimr (summaries), visdat and naniar (missing value visualization), mice (imputation), dbscan (outlier detection).

______

Procedures:

- Data Exploration: Used str() and skim() to check data types and distributions.

- Dataset Preparation: Split into two parts—MD_df for main variables and factor_df for categorical/outcome variables.

- Missing Value Analysis: Calculated missingness percentages. Variables with more than 35% missing values were removed; the rest were kept for imputation.

- Visualizing Missingness: Used vis_miss() and gg_miss_var() to plot missing data patterns.

- Removing High Missingness Variables: Hormone variables 9–14 were dropped, creating the cleaned dataset handle_MD_df.

_____

Task 1 — Little’s MCAR Test:

This test checks whether data is missing completely at random (MCAR).

Result: Statistic = 1809, df = 1102, p-value = 0

Conclusion: The missing data is not MCAR (it’s likely MAR), supporting the use of MICE imputation.

Output: mcar_test.txt


_____

Task 2 — MICE Imputation
Two MICE methods were tested:

Random Forest (rf): Predicts missing values using decision trees.

Predictive Mean Matching (pmm): Matches missing values with similar observed ones to keep data distribution consistent.
Both methods worked well, but PMM produced distributions closer to the original. Therefore, PMM was chosen.

Output Files: Density_PMM_Plot.png, Density_Random_Forest_Plot.png, imputed_rf_dataset.csv, imputed_pmm_dataset.csv

_______

Task 3 — Outlier Detection
Boxplots identified outliers in numeric variables.

Lipids2 and lipids4 showed strong outliers.

Hormone2–5 had extreme values.

Minor outliers appeared in antioxidant4, hormone10_generated, and carb_metabolism.

Output Files: Outlier_Detection_lipid_variables.png

___

Task 3b — LOF Outlier Detection:
Used the LOF algorithm from dbscan to find multivariate outliers.

Observations with LOF scores > 2 were flagged.

Only 3 clear outliers were found across lipids1 and lipids2.

Output Files: Histogram_LOF_scores.png, Bivariate_scatterplot_with_outliers.png

