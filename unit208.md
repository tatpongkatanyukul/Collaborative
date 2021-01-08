# Unit 2.08 Linear Regression

## Defining Study Objectives

Identifying a study objective is an important aspect of planning data analysis for health data. The study objective should clearly identify the study population, the outcome of interest, the covariate(s) of interest, the relevant time points for the study, and what you would like to do with these items.

An example of a clearly stated study objective would be:

"To estimate the reduction in 28-day mortality associated with vasopressor use during the first three days from admission to the ICU in MIMIC-III".

An example of a vague and difficult to execute study objective may be:

"To predict mortality in ICU patients”

The former provides a much clearer path for the data scientist to perform the necessary analysis because it identifies the target population (patients admitted to the ICU in MIMIC III), outcome (28 day mortality), covariate of interest (vasopressor used in the first three days of an ICU admission) and the time span (28 days for the outcome, within the first three days for the covariate). Remember, the less complex, the better.

To reinforce what has been discussed in previous units, it is important to first differentiate between ***outcomes*** and ***covariates***. Outcomes, also referred to as response or dependent variables, are what the study aims to investigate or predict. In the previous example, the outcome is 28-day mortality. Covariates are the variables whose effect on the outcome you would like to study or that you believe may have some effect on the target outcome.

## Introduction to Data Analysis: Linear Regression

Download dataset
```{r}
url <- "https://archive.physionet.org/physiobank/database/mimic2-iaccd/full_cohort_data.csv"
dat <- read.csv(url)
```

## Introduction to Regression Analysis: Part I

Check out residuals is important.

## Introduction to Regression Analysis: Part II

Linear regression ~ orinary least square

Logistic regression
  * binary outcome
  * ordinary outcome: proportional odds model, conditional logistic regression
  
Survival analysis --> Cox proportional hazards model

## Linear Regression: Initial Analysis

```
co2.lm <- lm(tco2_first~pco2_first,data=dat)
```

The basic lm command has two parts. The first is the formula which has the general syntax "outcome ~ covariates".
The second argument is separated by a comma and is specifying the data frame to use. 
In our case, the data frame is called dat , so we pass data = dat , noting that both tco2_first and pco2_first are columns in the dataframe dat.

```
summary(co2.lm)
```

The first part recalls the model we fit, which is useful when we have fit many models, and are trying to compare them. The second part lists some summary information about what are called residuals. Next, listed are the coefficient estimates; these are the  β^0 , (Intercept), and  β^1 , pco2_first, the parameters in the best fit line that we are trying to estimate. This output is telling us that the best fit equation for the data is:

tco2_first = 16.21 + 0.189×pco2_first

My note:
[TCO2](https://harvardapparatus.com/media/harvard/pdf/OT20.pdf) (total carbon dioxide) is either measured on plasma by automated chemistry analyzers or is calculated from pH and PCO2 measured on whole blood gas analyzers.
... Measurement of TCO2 as part of an electrolyte profile is useful chiefly
to evaluate HCO3 concentration. TCO2 and HCO3 are useful in the assessment of acid-base im bal ance
(along with pH and PCO2) and electrolyte imbalance.

[PCO2](https://harvardapparatus.com/media/harvard/pdf/OT20.pdf) (partial pressure of carbon dioxide) is a measure of the tension or pressure of carbon
di ox ide dissolved in the blood. PCO2 represents the balance between cellular production of CO2 and
ven ti la to ry removal of CO2 and a change in PCO2 indicates an alteration in this balance. Causes of
primary respiratory acidosis (increase in PCO2) are airway obstruction, sedatives and an es thet ics,
res pi ra to ry distress syndrome, and chronic obstructive pulmonary disease. Causes of pri ma ry
res pi ra to ry alkalosis (decreased PCO2) are hypoxia (resulting in hyperventilation) due to chronic heart
failure, edema and neurologic disorders, and mechanical hyperventilation.

## Linear Regression: Selecting a Model


## Linear Regression: Hypothesis Testing

Hypothesis testing in statistics is fundamentally about evaluating two competing hypotheses. The null hypothesis is set up as a strawman (a sham argument set up to be defeated) and is the hypothesis you would like to provide evidence against.

This is almost always  βk , and it is often written as  H0:βk=0 . The alternative hypothesis is commonly assumed to be  βk≠0  and will often be written as  HA:βk≠0 . A statistical significance level,  α , should be established before any analysis is performed. This value is known as the Type I error and is the probability that we falsely conclude that the coefficient is non-zero when the coefficient is actually zero. It is commonly set at 0.05.

P-values are the probability of observing data as or more extreme than what was seen, assuming the null hypothesis is true.

We reject the null hypothesis when the p-value is smaller than the significance level,  α .

## Linear Regression: Statistical Interactions and Testing Nest Models - Part I

We can set the gender_num variable to the class factor by using the as.factor function:

```dat$gender_num <-as.factor(dat$gender_num)```

## Linear Regression: Statistical Interactions and Testing Nest Models - Part II

## Linear Regression: Reporting and Interpreting

Often, it’s a good idea to also discuss how well the overall model fit. There are several ways to accomplish this, but reporting a unit-less quantity known as  R^2  (pronounced r-squared) is often done.

This quantity is a proportion (a number between 0 and 1) and describes how much of the total variability in the data is explained by the model. An  R^2  of 1 indicates a perfect fit, while 0 explains no variability in the data. What exactly constitutes a ‘good’  R^2  depends on the subject matter and how it will be used.

## Linear Regression: Confidence and Prediction Intervals - Part I

## Linear Regression: Confidence and Prediction Intervals - Part II

## Take home messages

Linear regression is an extremely powerful tool for conducting data analysis on continuous outcomes. Despite this, there are several aspects to be aware of when performing this type of analysis:

  * Hypothesis testing and the interval generation are reliant on modeling assumptions.
  * Outliers can be problematic when fitting models.
  * Be concerned about missing data.
  * Assess potential multi-colinearity. Co-linearity can occur when two or more covariates are highly correlated, for instance if blood pressure on the left and right arms were simultaneously measured, and both were used as covariates in the model.
  * Check to see if outcomes are dependent.
These concerns should not discourage you from using linear regression. It is extremely powerful, simple and reasonably robust to some of the problems discussed above, depending on the situation.
