## 📌 Graduate Admission Prediction – Jamboree Case Study
### 📝 Project Overview
This project aims to predict a student's chance of admission to a graduate program based on various academic and personal profile factors. The analysis involves data exploration, visualization, and the implementation of two regression models: Linear Regression and Polynomial Regression. The goal is to identify key factors influencing admissions and to build a model that accurately predicts admission chances.

The analysis is performed on the "Jamboree Admission" dataset.

## 📂 dataset - [link](https://d2beiqkhq929f0.cloudfront.net/public_assets/assets/000/001/839/original/Jamboree_Admission.csv)

- Serial No. – Unique ID for each record

- GRE Score (out of 340)

- TOEFL Score (out of 120)

- University Rating (1–5)

- SOP Strength (1–5)

- LOR Strength (1–5)

- CGPA (out of 10)

- Research (0 = No, 1 = Yes)

- Chance of Admit (0–1) – Target variable



**Target Variable**:

- Chance of Admit: The probability of a student getting admitted (ranging from 0 to 1).

**Features (Predictors)**:

- GRE Score: Graduate Record Examination score (out of 340).

- TOEFL Score: Test of English as a Foreign Language score (out of 120).

- University Rating: Rating of the university applied to (on a scale of 1 to 5).

- SOP: Statement of Purpose strength (on a scale of 1 to 5).

- LOR: Letter of Recommendation strength (on a scale of 1 to 5).

- CGPA: Cumulative Grade Point Average (out of 10).

- Research: Research experience (0 for no, 1 for yes).

## Exploratory Data Analysis (EDA)
The EDA revealed strong positive correlations between the features and the Chance of Admit.

Test Scores (GRE, TOEFL) and CGPA: There is a clear positive linear relationship. As scores increase, the chance of admission also increases significantly.

University Rating, SOP, and LOR Strength: Higher ratings for these qualitative factors are associated with a higher chance of admission.

Research Experience: Applicants with research experience have a noticeably higher average chance of admission compared to those without.

## Modeling and Evaluation
The data was split into an 80% training set and a 20% testing set.

### 1. Multicollinearity Check
Before modeling, multicollinearity among the features was assessed using a correlation heatmap and the Variance Inflation Factor (VIF).

Findings: The features CGPA, GRE Score, and TOEFL Score showed moderate to high correlation with each other. The VIF scores were:

- CGPA: 4.78

- GRE Score: 4.47

- TOEFL Score: 3.93

- University Rating: 2.53

- SOP: 2.84

- LOR: 2.02

- Research: 1.50

While some VIF values are approaching the common threshold of 5, they were not high enough to warrant immediate feature removal.

### 2. Linear Regression
A standard multiple linear regression model was trained on the data.

## Performance:

**Training Set**: R2=0.814, RMSE=0.062

**Test Set**: R2=0.833, RMSE=0.058

### Assumption Checks:

- Linearity & Homoscedasticity: The "Residuals vs Fitted" plot showed a relatively random scatter of points around the zero line, indicating these assumptions were reasonably met.

- Normality of Residuals: The Q-Q plot and histogram showed a slight deviation from normality. The Shapiro-Wilk test confirmed this, with a p-value close to zero ($p \< 0.001$), formally rejecting the null hypothesis of normal distribution.

- Independence of Residuals: The Durbin-Watson statistic was 2.04, which is very close to 2, suggesting no significant autocorrelation in the residuals.

### 3. Polynomial Regression
To capture potential non-linear relationships, a Polynomial Regression model (degree=2) was implemented.

## Performance:

**Training Set**: R2=0.888, RMSE=0.048

**Test Set**: R2=0.840, RMSE=0.057

### Assumption Checks:

The residual plots for the polynomial model showed similar patterns to the linear model. The Shapiro-Wilk test for normality also returned a significant result (p=0.001), indicating that the residuals were still not normally distributed, although the violation was slightly less severe than in the linear model.

## Results Summary
<img width="979" height="194" alt="image" src="https://github.com/user-attachments/assets/d9ea7b6e-0022-4ffe-9503-3818ed4a0d42" />


## Conclusion

Both models performed well, explaining a significant portion of the variance in the admission chances.

The Polynomial Regression model (degree=2) provided a slightly better fit to the data, with a higher R2 score (0.840 vs. 0.833) and a slightly lower RMSE on the test set. This suggests that there are some non-linear relationships between the predictors and the chance of admission that the polynomial model was able to capture.

**The key takeaway from the analysis is that academic performance metrics (CGPA, GRE Score, TOEFL Score) are the most dominant factors in predicting graduate school admissions**. However, qualitative aspects like the strength of LOR, SOP, University Rating, and having Research experience also play a crucial role.

While the models are effective, the violation of the normality assumption for residuals suggests that further improvements could be made, perhaps through feature transformations or by exploring more advanced non-linear models.

### ⚙️ Tech Stack

- Python: Data Cleaning, EDA, Modeling

- Libraries: Pandas, NumPy, Scikit-learn, Statsmodels, Seaborn, Matplotlib

- Model: Linear Regression (with diagnostic checks)


- Click here to view the full case study notebook:
📘 [View Notebook]()
- Open it directly in Colab:  [▶️ Open in Colab (right-click to open in new tab)](https://colab.research.google.com/drive/1b4z0bp-M_jZvXYDLXlkFNwONsxZbi8__?usp=sharing)
