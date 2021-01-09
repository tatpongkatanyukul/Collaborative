# Unit 2.09

## Logistic Contingency Tables

To understand the intuition behind what is happening, let us start by examining contingency tables.

A contingency table cross-tabulates the outcome across two or more levels of a covariate. When you further stratify your outcome on a variable (feature, factor etc.) you can sometimes observe more dramatic differences within groups that suggest the variable may be important. Let us now consider the example of 28 day mortality distributed among individuals over and under the age of 55. 

contingencytable

From the above table, you can see that 40 patients in the young group (≤55) died within 28 days, while 243 in the older group died. This corresponds to P(die|age≤55) = 40/(883+40) = 0.043 = 4.3 % and P(die|age > 55) = 0.284 or 28.4 %, where the “|” can be interpreted as “given” or “for those who have.” This difference is quite marked, and we know that age is an important factor in mortality, so this is not surprising.

## Logistic Regression: Introduction

![Code Example](https://github.com/tatpongkatanyukul/Collaborative/blob/main/u209codeExample.png)

As you can see, we get a coefficients table that is similar to the lm table we used earlier. Instead of a t-value, we get a z-value, but this can be interpreted similarly. The rightmost column is a p-value, for testing the null hypothesis β=0.

Looking more closely at the coefficients. The intercept is −3.09 and the age.cat coefficient is 2.17. The coefficient for age.cat is the log odds ratio for the 2 x 2 table we previously did the analysis on. When we exponentiate 2.17, we get exp(2.17) = 8.79. This corresponds with the estimate using the 2 x 2 table.

Note: odds ratio = 8.79 = odds of old (>55) / odds of young (<=55),
where odds of old = 0.4 and odds of young = 0.045.
That is from: 
  * odds of dying in an old = 0.284/(1 - 0.284).
  * odds of dying in a young = 0.043/(1 - 0.043).
  * odds of old = 243/(243 + 610) = 0.284.
  * odds of young =  40/(40 + 883) = 0.043.



