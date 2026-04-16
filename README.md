# NHL Forecasting Challenge

## Overview
The **2026 SMITH Competition** ([Students Mastering Intriguing Testable Hypotheses](https://www.wlu.ca/academics/faculties/lazaridis-school-of-business-and-economics/student-experience/case-competitions.html#SMITH)) challenged us to forecast the win percentages of every NHL team in the 2024-2025 season. We were provided a dataset of **145 variables** spanning across **10 seasons**.

> Our model took **1st place** out of 7 competing teams, giving us the win for our year (3rd).

We have posted the code for it here, along side a small explanation.
---

## Methodology

### Model Selection
Given the high dimensionality of the dataset, we chose a **linear model with component-wise Gradient Boosting** using the `mboost` package in R. This technique stacks many different weak models together, each explaining a different aspect of our data. Running the `glmboost`, we selected an initial set of 500 candidate models.

The math behind the model is as follows: the algorithm starts off with a simple model, acting as a component. It then computes the the negative gradient of the loss function, otherwise known as the residuals. One component is taken at the next iteration and updates it along that component. This is done until the model no longer takes on new information and begins overfitting.

### Preventing Overfitting
To avoid overfitting, we applied **K-Fold Cross Validation** via `cvrisk` to identify the optimal stopping iteration (`best_mstop`). With the optimal folds selected, the final model was re-fit using this optimal number of iteraiton. We can then forecast what we believe the next year's win percentages will be.

### Results
Our final model achieved an **RMSE of 0.0378** on the out-of-sample test set, the best performance among the third year teams. 

---

## Tech Stack
- **Language:** R
- **Key Packages:** `mboost`

---

## Acknowledgements
A huge thank you to **Dr. Justin Smith** for organizing and running the competition — it was a fun and challenging competition!
