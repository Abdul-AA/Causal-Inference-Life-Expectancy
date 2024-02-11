# Causal Inference: The Impact of a Country's Development Status on Life Expectancy

## Context

A [regression model](https://github.com/Abdul-AA/Life-Expectancy) using a simple decision tree was developed to predict the life expectancy of countries. Analysis of the model's results revealed that a country's development status is one of the most significant factors influencing its life expectancy. Intuitively, this relationship makes sense because a country's development status can affect various factors that may influence the quality of healthcare. Consequently, a causal machine learning model was developed to determine the average impact of a country's development status on its life expectancy in the form of its Average Treatment Effect (ATE) and to assess the impact of other features on the causal impact (treatment effect) of a country's development status on life expectancy.

## Hypothesis

The development status of a country causally impacts its life expectancy; specifically, being in a developing status has a causally negative impact on life expectancy.

## Model and Evaluation Methodology

- The dataset was segmented into treatment, a set of features, and the target.
- The treatment was identified as "developing status," coded as 1 for developing countries and 0 for developed countries, making the latter the control group.
- All other features were isolated to estimate their impact on the treatment effect on life expectancy.
- Life expectancy was set as the target.
- Linear regression and XGBoost regressor models were employed to determine the ATE of the country's development status on life expectancy.
- LightGBM was chosen as a base learner to estimate the impact of other features on the treatment effect on life expectancy by predicting the tau values (average treatment effect). Consequently, the feature importance reveals the impact of the features on the treatment effect and how they modulate the causal relationship.
- The model was trained on a training set and evaluated on a test set to assess the reliability and generalizability of the model's estimates.
- SHAP values were utilized to determine the direction of the impact on the treatment effect since feature importance reveals magnitude but not direction.

## Results and Lessons Learned

- The models demonstrated acceptable generalizability with similar results on both the training and test sets.
- Both the linear regression and XGBoost models revealed a negative treatment effect for countries with a developing status. Specifically, the ATE was -1.55 (-1.99, -1.12) according to linear regression and -6.90 (-7.19, -6.60) according to XGBoost regressor, at a 95% confidence interval. This implies that, on average, developing countries have a reduced life expectancy of about 1.5 years according to the linear regression and 7 years according to the XGBoost regressor.
- The most significant factors affecting the causal impact of a country's developing status on life expectancy include the income composition of resources, HIV prevalence, and adult mortality. These findings suggest that while the development status of a country is a clear disadvantage regarding life expectancy, the most impactful features modulating this effect are the income composition of resources, HIV prevalence, and adult mortality.
- The SHAP beeswarm plot indicated that, in most cases, a low income composition of resources negatively impacts the treatment effect, meaning the lower the index, the more negative the treatment effect. This pattern was also observed for HIV prevalence and adult mortality.

