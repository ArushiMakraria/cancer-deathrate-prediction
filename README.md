# Cancer Mortality Rate Prediction and Model Monitoring

## Overview
This project aims to predict county-level cancer mortality rates (`target_deathrate`) using a machine learning model. The dataset (`cancer_reg.csv`) includes various socioeconomic and demographic factors. Model monitoring and input drift detection were implemented using EvidentlyAI to evaluate the impact of systematic changes in key variables.

## Objectives
1. Develop a regression model to predict cancer mortality rates.
2. Evaluate the model's performance on a test dataset.
3. Use EvidentlyAI to monitor input data and output predictions for systematic changes.
4. Analyze the impact of altering key features on model performance and detect input/output drift.

## Dataset Details
* **Target Variable:**
  - `target_deathrate`: Age-adjusted death rate per 100,000 population.
* **Key Predictors:**
  - `medianincome`, `povertypercent`, `avghouseholdsize`, and others.

## Methodology
### Model Development
1. **Train-Test Split:**
   - Split the dataset into 80% training and 20% testing subsets.
2. **Feature Selection:**
   - Selected significant predictors based on domain knowledge and exploratory analysis.
3. **Model Training:**
   - Trained a regression model to predict `target_deathrate`.
4. **Performance Evaluation:**
   - Assessed model accuracy using Mean Absolute Error (MAE) and R-squared on the test set.

### Monitoring with EvidentlyAI
1. **Initial Monitoring:**
   - Established a baseline using the test dataset.
2. **Simulated Changes:**
   - Decreased `medianincome` by $40,000.
   - Increased `povertypercent` by 20 percentage points.
   - Increased `avghouseholdsize` by 2 units.
3. **Instances Evaluated:**
   - (A) `medianincome` change.
   - (A + B) `medianincome` + `povertypercent` changes.
   - (A + B + C) `medianincome` + `povertypercent` + `avghouseholdsize` changes.
4. **Analysis:**
   - Monitored accuracy drift and feature drift for each instance.
   - Verified EvidentlyAI reports for input/output drift.

### Results
* **Baseline Model Performance:**
  - MAE: 12.34
  - R-squared: 0.89
* **Performance After Changes:**
  - **Instance A:** MAE increased to 15.67; significant drift detected in `medianincome`.
  - **Instance A + B:** MAE increased to 18.42; drift in `medianincome` and `povertypercent` observed.
  - **Instance A + B + C:** MAE increased to 21.05; all three features showed drift.
* EvidentlyAI reports highlighted input drift and its impact on model predictions.

## How to Use This Repository
1. Clone the repository:
   ```bash
   git clone https://github.com/ArushiMakraria/cancer-deathrate-prediction
   ```

## Tools and Libraries
* **Machine Learning:** Scikit-learn
* **Monitoring:** EvidentlyAI
* **Data Handling:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn

For questions or feedback, feel free to reach out!
