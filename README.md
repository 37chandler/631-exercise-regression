# Exercise: Simple Linear Regression (IMS Chapters 7 & 8)

In-class exercises for the regression week, following *Introduction to Modern Statistics* Chapters 7 and 8. The session has two parts: a translation of the IMS Chapter 7 examples into Python, and a hands-on "Guess the Price" activity using real car listings data.

## Learning Objectives

By completing these exercises, you will practice:
- Fitting a simple linear regression model with `statsmodels`
- Reading and writing a regression equation ($\hat{y} = b_0 + b_1 x$)
- Computing and plotting residuals
- Computing and interpreting the correlation coefficient $r$
- Verifying the slope formula $b_1 = r \cdot s_y / s_x$
- Interpreting $R^2$ as the fraction of variation explained
- Creating and interpreting indicator (dummy) variables for categorical predictors
- Distinguishing high-leverage from influential outliers
- Using data progressively to sharpen a price estimate
- Constructing features (`log_odometer`, `in_minneapolis`) for a real-world model
- Interpreting model coefficients and making predictions

## Data Setup

Place the following CSV files in this folder before running the notebooks. The IMS datasets (`loan50.csv`, `county.csv`, `loans_full_schema.csv`, `email.csv`) are available in the `data.zip` on Canvas. `car_listings.csv` is available separately on Canvas.

Your folder should look like:

```
631-exercise-regression/
├── README.md
├── exercise-ims-ch7.ipynb
├── exercise-ims-ch7-solutions.ipynb
├── exercise-car-regression.ipynb
├── exercise-car-regression-solutions.ipynb
├── IMS Chapter 8 Code.ipynb
├── loan50.csv
├── county.csv
├── car_listings.csv
├── loans_full_schema.csv
└── email.csv
```

## Notebooks

- **`exercise-ims-ch7.ipynb`** — IMS Chapter 7 concepts translated to Python. Work through this during class; finish afterward if needed. Some cells are complete, others have `# YOUR CODE HERE` gaps to fill in.
- **`exercise-ims-ch7-solutions.ipynb`** — Complete solutions for instructor use.
- **`exercise-car-regression.ipynb`** — "Guess the Price" activity: use F-150 listings to refine a price estimate, then formalize the process with a regression model.
- **`exercise-car-regression-solutions.ipynb`** — Complete solutions with instructor notes and visualizations for the reveal.
- **`IMS Chapter 8 Code.ipynb`** — Fully worked Python examples for IMS Chapter 8 (inference for regression). For student reference — no blanks to fill in.

## Topics Covered

### `exercise-ims-ch7.ipynb`

**Part 1: Fitting a Line**
- Scatterplot with a regression line using `smf.ols`
- Interpreting the slope and intercept
- Making predictions with `.predict()`; the danger of extrapolation

**Part 2: Residuals**
- Computing residuals from `.resid`
- Residual plot (residuals vs. fitted values); identifying patterns

**Part 3: Correlation**
- Computing $r$ with `.corr()`
- Verifying $b_1 = r \cdot s_y / s_x$
- Correlation vs. causation

**Part 4: The Regression Equation**
- Extracting coefficients with `.params`
- Interpreting the slope in context
- Verifying the line passes through $(\bar{x}, \bar{y})$

**Part 5: R²**
- Extracting `.rsquared`; verifying $R^2 = r^2$
- Visualizing explained vs. unexplained variation

**Part 6: Categorical Predictors**
- Creating an indicator variable (`.astype(int)`)
- Fitting and interpreting a model with a dummy variable

**Part 7: Outliers**
- Adding an artificial influential point
- High leverage vs. influential points

### `exercise-car-regression.ipynb`

**Part 1: Guess the Price**
- Open exploration with `car_listings.csv` filtered to F-150s
- Progressively narrow in on a specific listing using summary statistics and plots

**Part 2: A Regression Model**
- Feature engineering: `log_odometer`, `in_minneapolis` indicator
- Fitting `price ~ car_age + log_odometer + in_minneapolis`
- Extracting and interpreting each coefficient
- Making a prediction for the specific listing and comparing to the actual price

### `IMS Chapter 8 Code.ipynb` (reference)

- SLR inference: bootstrap CI and t-test for the slope
- L-I-N-E diagnostic plots
- Multiple linear regression inference
- Logistic regression: log-odds, odds ratios, predicted probabilities

## Required Libraries

```bash
pip install pandas numpy matplotlib seaborn statsmodels
```

You can run this from inside a notebook cell by prefixing with `!`:

```bash
!pip install pandas numpy matplotlib seaborn statsmodels
```

## Getting Started

1. Place the data files in this folder (see **Data Setup** above)
2. Open `exercise-ims-ch7.ipynb` and `exercise-car-regression.ipynb` in Jupyter or VS Code
3. Complete the sections marked `# YOUR CODE HERE` and the written answer cells
4. Refer to the solutions notebooks if you get stuck

## Datasets

- **`loan50`** — 50 loans from Lending Club with variables including `loan_amount`, `total_income`, `interest_rate`, and `homeownership`
- **`county`** — 3,142 U.S. counties with demographic and economic variables including `poverty` and `median_hh_income`
- **`car_listings`** — Craigslist used-car listings with `price`, `odometer`, `year`, `make`, `model`, and `location`
- **`loans_full_schema`** — 10,000 Lending Club loans; used in the Chapter 8 MLR example
- **`email`** — 3,921 emails classified as spam or not spam; used in the Chapter 8 logistic regression example
