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
