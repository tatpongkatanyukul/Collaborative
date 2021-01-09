# Unit 2.10

## 2.10: Sensitivity Analysis and Model Validation

Once you’ve finished your primary analysis, your results and design decisions, such as inclusion criteria and cutoff thresholds still need to be validated. It can be easy to produce misleading conclusions if you forgo examining your analysis. In particular, you should answer these questions:
  * Does the data meet the assumptions of your model? 
  * Would you get the same result with slightly different data? 
How confident should you be in your results? 
  * How much would your results change if your inclusion criteria were slightly different?
  
These steps are especially important if you have a causal interpretation of your results, since causal inference is often limited by the assumptions made in study design and analysis and this is particularly pronounced when working with observational health data.

## What are Sensitivity Analysis and Model Validation?

Sensitivity Analysis and Model Validation are both attempts to assess the appropriateness of a particular model specification and to appreciate the strength of the conclusions being drawn from such a model.

Model validation is the process of assessing how well your model fits within your specific research dataset. It is checking the appropriateness of your model.

Sensitivity analysis is the process of gaining confidence in the generalizability of the result of the primary analysis and is important in situations where a model is likely to be used in a future research investigation or in clinical practice.

## Model Assumptions

The first step to verifying model validity is to check whether your data and analysis meet the model's assumptions.

plot residuals (errors) vs fitted (prediction, y)

## Evaluating Model Performance
We need to know how to evaluate model accuracy. There are many ways to do this, three of the most simple and commonly used methods are:
  * Accuracy, the proportion of records which were correctly labeled (in a classification problem)
  * R^2, the proportion of the variance in the outcome parameter explained by the model (in a regression problem)
  * The area under the Receiver Operating Characteristic Curve (AU-ROC) (in a classification problem)
  
### Sensitivity and Specificity

One issue with accuracy is that it is not a good metric of performance if the dataset is unbalanced.
For instance, imagine you were predicting mortality in a hospital with a 1% mortality rate. A model which predicted everyone to be a 0 would be 99% accurate! To protect against this flaw, we should also always look at the specificity and sensitivity of our model.

Sensitivity (also known as the true positive rate) measures the proportion of positives that are correctly identified (TP)/(TP+FN)
==> Recall

Specificity (also known as the true negative rate) measures the proportion of negatives that are correctly identified (TN)/(TN+FP)

### Receiver Operating Characteristic Curve

## Validation

validation is used to ensure that the model will perform similarly under different conditions - such as similar data from a new source. Several methods can be used to validate model performance:
  * Only training on part of the dataset, keeping some back to validate data
  * K-fold cross-validation, explained below
  * External validation - verification on a data set from another source

Rank these different validation methods in order of least to most robust validation:
  * Validating on training set 
  * Validating on validation set
  * K-fold cross validation
  * Unseen data from the same source - aka a test set
  * Unseen data from a different source

## Sensitivity analysis

The creation of any model requires assumptions and, sometimes arbitrary, decisions on parameter values. The purpose of sensitivity analysis is to assess if the model results are robust to these decisions, or small changes lead to large fluctuations in results. Results that remain consistent throughout sensitivity analysis are more likely to generalize to different datasets.

What sensitivity analysis you perform depends on the assumptions used to construct the model and the structure of your data. Common areas to analyse include:
  * Which features are important to collect? If there are unimportant features could these be removed from the model to reduce computation time and the burden of collection?
  * How robust is the model to noise in the data?
  * How are the results affected when you change parameters in your model, such as the stringency of propensity score matching?
  * How does the cohort affect the results? Are the results replicable with different inclusion criteria? Do your results hold in different subgroups?
  
The best test of your results is to replicate them with many models and using different data sources.

## Conclusion

  * Validation and sensitivity analyses test the robustness of the model assumptions and are a key step in the modeling process.
  * The key principle of both these analyses is to vary the model assumptions and observe how the model responds
  * Failing the validation and sensitivity analyses might require the researcher to start with a new model
  
Validation can be used to check that the model is an appropriate fit for the data and is likely to perform similarly in other cohorts. Sensitivity analysis can be used to interrogate inherent assumptions of the primary analysis. If a model fails these tests, this could indicate that a new approach is required. 
