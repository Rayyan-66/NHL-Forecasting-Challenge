# NHL Forecasting Challenge

## Overview
The **2026 SMITH Competition** ([Students Mastering Intriguing Testable Hypotheses](https://www.wlu.ca/academics/faculties/lazaridis-school-of-business-and-economics/student-experience/case-competitions.html#SMITH)) challenged us to forecast the win percentages of every NHL team in 2024-2025. Our model took **1st place** out of 7 competing teams, giving us the win for our year (3rd).

We were provided a dataset of **145 variables** spanning **10 seasons** of NHL data.

---

## Methodology

### Model Selection
Given the high dimensionality of the dataset, we chose a **linear model with component-wise Gradient Boosting** using the `mboost` package in R. Running `glmboost` produced an initial set of 500 candidate models, each capturing different aspects of the data.

### Preventing Overfitting
To avoid overfitting, we applied **K-Fold Cross Validation** via `cvrisk` to identify the optimal stopping iteration (`best_mstop`). With the optimal folds selected, the final model was re-fit using this optimal `mstop`.

### Results
Our final model achieved an **RMSE of 0.0378** on the out-of-sample test set, the best performance among the third year teams.

---

## Tech Stack
- **Language:** R
- **Key Packages:** `mboost`, `caret`, `dplyr`, `ggplot2`, `Metrics`

---

## Acknowledgements
A huge thank you to **Dr. Justin Smith** for organizing and running the competition — it a fun and challenging competition!

