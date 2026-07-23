# AI-ML Assignment 3 – Salary Prediction using Polynomial Regression

## Objective

Build a **Polynomial Regression** model (degree = 3) to predict employee salaries based on their position level, using the Position Salaries dataset. The goal is to capture the non-linear growth relationship between job level and salary.

---

## Dataset

**Name:** Position Salaries Dataset  
**Source:** [Kaggle – Position Salaries](https://www.kaggle.com/datasets/akram24/position-salaries)  
**Records:** 10 rows × 3 columns  
**Columns:**
| Column   | Type   | Description                          |
|----------|--------|--------------------------------------|
| Position | object | Job title / role name                |
| Level    | int    | Numeric position level (1–10)        |
| Salary   | int    | Annual salary in USD                 |

> **Note:** The dataset file is NOT included in this repository. Download it from the Kaggle link above.

---

## Libraries Used

| Library      | Purpose                                      |
|--------------|----------------------------------------------|
| pandas       | Data loading and manipulation                |
| numpy        | Numerical operations                         |
| matplotlib   | Data visualization                           |
| scikit-learn | PolynomialFeatures, LinearRegression, metrics|

Install dependencies:
```bash
pip install pandas numpy matplotlib scikit-learn
```

---

## Methodology

1. **Data Understanding**
   - Loaded the CSV using Pandas
   - Inspected the first 5 rows, data types, and summary statistics
   - Identified `Level` as the input feature and `Salary` as the target variable

2. **Data Preprocessing**
   - Verified no missing values exist in the dataset
   - Selected `Level` (X) and `Salary` (y)
   - Split data into **80% training** and **20% testing** (`random_state=42`)

3. **Model Development**
   - Applied `PolynomialFeatures(degree=3)` to transform the input feature into [1, x, x², x³]
   - Fitted a `LinearRegression` model on the polynomial-transformed training data
   - Predicted salaries on the test set

4. **Model Evaluation**
   - Computed MAE, MSE, RMSE, and R² Score
   - Plotted the original data scatter plot with the polynomial regression curve
   - Plotted Actual vs Predicted salaries for the test set

5. **Conclusion**
   - Summarized key findings and contrasted Linear vs Polynomial Regression

---

## Results

| Metric                  | Value (Test Set)     |
|-------------------------|----------------------|
| Mean Absolute Error     | ~varies (2 test pts) |
| Mean Squared Error      | ~varies (2 test pts) |
| R² Score (Full Dataset) | ~0.99+               |

> Because the dataset has only 10 samples, the 80/20 split produces 2 test points. The R² score on the full dataset provides a more reliable measure of fit.

### Visualizations

Generated plots (saved as `polynomial_regression_results.png`):
- **Left:** Scatter plot of actual salary data with the fitted polynomial regression curve
- **Right:** Actual vs Predicted salary for the test set

---

## Conclusion

The Polynomial Regression model (degree = 3) successfully captured the non-linear salary growth across position levels. Salary increases modestly at junior levels but accelerates sharply at executive levels — a pattern no straight-line model can represent accurately.

**Linear Regression** fits `y = b0 + b1*x` — a flat line that cannot follow curves. **Polynomial Regression** adds higher-order terms (x², x³), allowing it to model curvature while still using the same linear coefficient-fitting machinery under the hood.

The key advantage of Polynomial Regression for this dataset is its ability to model the steep, exponential-like salary jump at the highest position levels (Partner → CEO), which would be severely misrepresented by a linear model.

---

## File Structure

```
Assignment-3/
├── Assignment-3.ipynb                  # Main notebook with all 5 tasks
├── Position_Salaries.csv               # Dataset (download from Kaggle)
├── polynomial_regression_results.png   # Generated plots
└── README.md                           # This file
```

---

## Submission Details

- **Assignment:** Assignment-3  
- **Topic:** Salary Prediction using Polynomial Regression  
- **Deadline:** 23 July 2026, 11:59 PM IST  
- **Submission Form:** https://forms.gle/fFL2CFooc5Vb2MXq8
