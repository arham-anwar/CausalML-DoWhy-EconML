## Executive Summary

This project extends Assignment 1, predicting revenue generated by each customer based on Google Analytics data. The primary goal is to analyze observational data, featuring our target 'Revenue', list of features 'X', and our experiment 'T'. The experiment T refers to the referral program. Using EconML, CausalML, and DoWhy, we investigate the effects of the referral program on revenue generation to form a business strategy on how much the company should focus on the referral program.

- **H0:** Referral has no impact on revenue generation.
- **H1:** Referral does impact revenue generation.

**Conclusion:** The referral program is highly effective in increasing generated revenue compared to non-referral instances. The Null Hypothesis was rejected, and statistical techniques quantified the degree of impact of the referral program on revenue generation. EconML and CausalML are used to examine these hypotheses.

**Note:** Please skip to Section 4 to bypass EDA and business insights from Assignment 1.

- **Target:** Revenue generated
- **Treatment:** Boolean of referral
- **Feature Matrix:** All final predictors except Target and Treatment

## Section 1 - Libraries, Utils, and Preprocessing

### 1.1 Libraries

The project utilizes several libraries, including:
- pandas
- numpy
- seaborn
- matplotlib
- sklearn
- econml
- causalml
- dowhy

### 1.2 Utils.py / Functions

Several utility functions are defined for data processing and analysis.

### 1.3 Load and Flatten the Dataset

The dataset is loaded from JSON and flattened to a suitable format. To save processing time, a subset of the data is used.

### 1.4 Cleaning Datatypes

Data types of the loaded dataset are cleaned to ensure consistent data handling.

### 1.5 Profiling - PandasProfiling, Dtale, and More

Dtale is used for flexible variable analysis, including distribution, missing values, and categorical variable breakdowns.

## Section 2 - EDA / Business Insights / Prediction Model Primer

### 2.1 Initial Logical Cleansing

Null values are identified and removed along with columns having constant values. Grouped columns by their first characters provide a clearer view of data distribution.

### 2.2 Initial Business Insights

Only 2% of events contribute to revenue generation, suggesting the need for balancing techniques in the model pipeline.

### 2.3 Univariate Analysis

Data is fairly symmetrical and skewed with high kurtosis. Outliers are examined.

### 2.4 Bi-variate Analysis

Analysis of features against the target variable to understand relationships.

### 2.5 Missing Information Visualization

Visualizing missing data to identify patterns.

### 2.6 Extended EDA for Business

Detailed exploratory analysis to derive business insights.

### 2.7 Type of Data Analysis

**Predictive Analysis:** Prediction of revenue generation by customer.

### 2.8 Categorical Encodings

Applying one-hot and label encoding to categorical variables.

### 2.9 Predictors and Target

Defining the predictors and target variable for the model.

### 2.10 Correlation Matrix

Correlation matrix to understand relationships between variables.

## Section 3 - Prediction Model

### 3.1 Train Test Split

Splitting the data into training and testing sets.

### 3.2 Handling Imbalanced Datasets

Using techniques like SMOTETomek and SMOTHEEN to balance datasets.

### 3.3 SOTA Modeling

Applying state-of-the-art models like XGBoost, LightGBM, CatBoost, and deep learning architectures.

### 3.4 Model Evaluations

Evaluating models using metrics like ROC-AUC, RMSE, MAE, and SR^2.

### 3.5 Explainability

Using SHAP or LIME for model explainability.

### 3.6 Hyperparameter Optimization

Optimizing model hyperparameters with Hyperopt or Optuna.

### 3.7 Model Persistence

Saving and loading models for future use.

### 3.8 Model by Pipeline

Summarizing the code into a pipeline for easy execution.

## Section 4 - Causal Inference

### 4.1 Feature Importances

Analyzing feature importances from the predictive model.

### 4.2 A Tale of Referral's Impact on Revenue Using EconML

Testing the causal effect of the referral program on revenue while controlling for other factors.

- **Null Hypothesis (H0):** No causal effect of the referral program on revenue.
- **Alternative Hypothesis (H1):** Causal effect of the referral program on revenue.

### 4.3 CausalML - Analysis of Referral Program Impact on Revenue Generation

#### Hypotheses:

- **Null Hypothesis (H0):** The referral program has no significant impact on revenue generation.
- **Alternate Hypothesis (Ha):** The referral program has a significant impact on revenue generation.

### Overview

Investigating the effectiveness of the referral program on revenue generation using predictive models (Linear Regression, XGBoost) to estimate the average treatment effect (ATE).

### Predictive Performance Metrics

- **RMSE:** Lower RMSE indicates better predictive accuracy.
  - **Control:** 0.8686
  - **Treatment:** 0.8717

- **sMAPE:** Lower sMAPE indicates closer alignment between predicted and actual revenue.
  - **Control:** 0.1764
  - **Treatment:** 0.1678

- **Gini Coefficient:** Higher Gini coefficients indicate better discrimination power.
  - **Control:** 0.7125
  - **Treatment:** 0.5977

### Average Treatment Effect (ATE)

- **Linear Regression:**
  - **ATE:** 0.27
  - **Confidence Interval:** [0.19, 0.34]
  - **Interpretation:** Referred customers generated 0.27 units more revenue.

- **XGBoost:**
  - **ATE:** 0.24
  - **Confidence Interval:** [0.22, 0.27]
  - **Interpretation:** Referred customers generated 0.24 units more revenue.

### Conclusion

Both Linear Regression and XGBoost indicate a positive average treatment effect of the referral program on revenue generation.

### Recommendations

Further investigate the reasons for differences in ATE estimates between models. Conduct sensitivity analyses and validate results with additional datasets.

### Visualizations

Graphs depicting revenue distributions, predictive performance metrics, and ATE estimates enhance understanding.

### 4.4 Meta Learner Comparison

Analyzing results based on estimated Average Treatment Effects (ATE) and distribution of Individual Treatment Effects (ITE).

1. **S-Learner:**
   - **ATE Estimate:** 0.268
   - **Confidence Interval:** [0.193, 0.343]
   - **Business Meaning:** Consistent positive impact of referrals on revenue.

2. **T-Learner:**
   - **ATE Estimate:** 0.201
   - **Confidence Interval:** [0.176, 0.226]
   - **Business Meaning:** Positive impact with higher variability.

3. **X-Learner (with propensity score):**
   - **ATE Estimate:** 0.136
   - **Confidence Interval:** [0.113, 0.158]
   - **Business Meaning:** Positive impact, moderate variability.

4. **X-Learner (without propensity score):**
   - **ATE Estimate:** -0.000
   - **Confidence Interval:** [-0.017, 0.017]
   - **Business Meaning:** No significant treatment effect without propensity scores.

### Conclusion

The S-Learner provides a robust estimate of the treatment effect, suggesting that 'Referral' has a positive impact on revenue. The results should be interpreted cautiously, considering the assumptions and limitations of each learner.

## Future Work

- Experiment with different causal models and compare performance.
- Implement analysis on a larger dataset and optimize for scalability.
- Integrate real-time data streams for continuous monitoring and analysis of referral program impacts.

---

This report provides a comprehensive understanding of the project's structure and methodology, ensuring clarity in the implementation and interpretation of the causal inference analysis.
```
