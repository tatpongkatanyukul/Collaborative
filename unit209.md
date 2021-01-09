# Unit 2.09

## Logistic Contingency Tables

To understand the intuition behind what is happening, let us start by examining contingency tables.

A contingency table cross-tabulates the outcome across two or more levels of a covariate. When you further stratify your outcome on a variable (feature, factor etc.) you can sometimes observe more dramatic differences within groups that suggest the variable may be important. Let us now consider the example of 28 day mortality distributed among individuals over and under the age of 55. 

contingency table

| Mortality | 0  | 1 |
|-----------|----|---|
|<=55       | 883| 40|
|>55        | 610|243|

From the above table, you can see that 40 patients in the young group (≤55) died within 28 days, while 243 in the older group died. This corresponds to P(die|age≤55) = 40/(883+40) = 0.043 = 4.3 % and P(die|age > 55) = 0.284 or 28.4 %, where the “|” can be interpreted as “given” or “for those who have.” This difference is quite marked, and we know that age is an important factor in mortality, so this is not surprising.

## Logistic Regression: Introduction

![Code Example](https://github.com/tatpongkatanyukul/Collaborative/blob/main/u209codeExample.png)

As you can see, we get a coefficients table that is similar to the lm table we used earlier. Instead of a t-value, we get a z-value, but this can be interpreted similarly. The rightmost column is a p-value, for testing the null hypothesis β=0.

Looking more closely at the coefficients. The intercept is −3.09 and the age.cat coefficient is 2.17. The coefficient for age.cat is the log odds ratio for the 2 x 2 table we previously did the analysis on. When we exponentiate 2.17, we get exp(2.17) = 8.79. This corresponds with the estimate using the 2 x 2 table.

β0  is the log odds of the outcome in the younger group. Exponentiating again, exp(−3.09) = 0.045

(See contingency table along)

Note: odds ratio = 8.79 = odds of old (>55) / odds of young (<=55),
where odds of old = 0.4 and odds of young = 0.045.
That is from: 
  * odds of dying in an old = 0.284/(1 - 0.284).
  * odds of dying in a young = 0.043/(1 - 0.043).
  * odds of old = 243/(243 + 610) = 0.284.
  * odds of young =  40/(40 + 883) = 0.043.

## Logistic Regression: Hypothesis Testing

Just as in the case of linear regression, there is a way to test hypotheses for logistic regression. It follows much of the same framework, with the null hypothesis being β = 0. If you recall, this is the log odds ratio, and testing if it is zero is equivalent to a test for the odds ratio being equal to one.

To examine this concept, the MIT Critical Data textbook Secondary Analysis of Electronic Health Records page 232 walks through an example first fitting two competing models, a larger (alternative model), and a smaller (null model) and then using the ANOVA function to assess the difference. Using a Chi-squared test through the ANOVA function is a common way to test whether a categorical covariate should be retained in the model, as it can be difficult to assess using the z-value in the summary table, particularly when one is very statistically significant, and one is not.

## Logistic Regression: Prediction

After fitting a final model, a common task is to generate subsequent predictions. Such a task may occur when doing a propensity score analysis or creating tools for clinical decision support. In the logistic regression setting, this involves attempting to estimate the probability of the outcome given the characteristics (covariates) of a patient. This quantity is often denoted P(outcome|X). We followed this by adding a pred column to our new data frame by using the predict function.

## Logistic Regression: Model Results

This section explains how results are often presented and how to interpret these models. 

## Logistic Regression: Summary

Logistic regression is an extremely powerful tool for data analysis of health data, especially given the numerous binary and categorical outcomes.

As with linear regression, there are a number of concerns to validate such as outliers, missing data, colinearity, dependent/correlated outcomes, and additional modeling assumptions. 

In cases where the data has been divided into too many subgroups (or the study may be simply too small), you may encounter a level of a discrete variable where none (or very few) of one of the outcomes occurred (i.e. verify that there are a sufficient number of cases in stratified groups as extreme imbalance may cause issues).

## Trees: Introduction

Reference textbooks
  * [Introduction to Statistical Learning](https://github.com/tatpongkatanyukul/Collaborative/blob/main/ISLR%20Seventh%20Printing.pdf)
  * [Elements of Statistical Learning](https://github.com/tatpongkatanyukul/Collaborative/blob/main/ESLII.pdf)
  
## Trees: Prediction vs. Interpretation

## Trees: Decision Trees

[Iris Video](https://github.com/tatpongkatanyukul/Collaborative/blob/main/iris_data.mp4)
  * cool historical comments on Charles Darwin, variance, and IRIS data

## Trees: How to build decision trees

## Boosting and Bagging
  * Bootstrapping
  * Boosting: using weighting mechanism to prioritize datapoints poorly predicted previously to train a new model
  * Bagging: bootstrappin subdatasets to train sub-models and average the sub-predictions
  * Random Forest: similar to bagging, but adding random selection of a subset of attributes
  * Gradient Boosting: Use a child model to correct its parent model. Super creative!!!
  
## Evaluation
  * Holdout (regular way to use a test set for evaluation)
  * Jackknifing: repeat the holdout but with new shuffled sets, the average the measures
  * Bootstraping for Random Forest: since each submodel of RF is trained with only a subset of data, use the left-out to evaluate it and once they are all done, average the measures out. We cannot do this with Gradient Boosting
  * Cross-Validation
    * different from Jackknife that Jackknife is random and it is possible that some datapoints may get used multiple times, while some may never be used.
  * Leave one out = Cross-Validation with a group of only one datapoint
    * It is computationally expensive. It is usually used when there are two few datapoints. E.g., 30 datapoints.
  
## Trees: Summary

Exercise

1. An example using the iris dataset as Alistair demonstrated in his video to best understand the concept. The ensemble methods tutorial provides a more applied exploration of the 506 census tracts of Boston from the 1970 census.
Please follow this tutorial walking through how you build trees on the [iris dataset](https://ademos.people.uic.edu/Chapter24.html) and for an introduction to [ensemble methods](https://daviddalpiaz.github.io/r4sl/ensemble-methods.html) (bagging & boosting).

2. An example from [IBM Watson using XGBoost](https://dataplatform.cloud.ibm.com/data/notebooks/converter/assets/de824290-6811-455b-b2a4-678fd6ae06ee?access_token=cb51caafa25bb0e596867d19fd0e96c77baeffca4b561091e38f0cd4476dc682&project=18a1ec4b-baaa-4cd8-b9c9-28001e5147ee) to classify breast cancer as benign or malignant based on features from 569 diagnostic images from the Wisconsin dataset. Go through steps 2 and 3.

