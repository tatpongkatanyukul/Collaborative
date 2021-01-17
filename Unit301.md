# Unit 3.01+

The reproducibility crisis is an issue facing scientific researchers around the world, where the results of studies are not able to be replicated. In recent meta-analyses, experts have found that between 40-80% of studies in psychology, cardiology, hematology, and more were not reproducible.

Reproducibility is generally divided into two major groups:

  * Conceptual Replication: You are asking the same question, but doing so in a different way than originally done. This tests the validity of the underlying theory.
  * Exact Replication: You are asking the exact same question in the same way as was originally done. This tests the validity of theoretical statistical conclusions.

Failing to achieve exact replication is particularly concerning, because it calls into question the validity of studies previously published in the literature.

There are many factors currently contributing to the reproducibility crisis, including:

  * Pressure to publish: Scientists may perform statistical tests which depict their results in the most favorable way for publication.

  * Selective reporting: Oftentimes, only the most positive outcomes or analyses are reported in the literature and all the data is not shared.

  * Insufficient mentoring: In academic settings, students without proper mentorship may interpret or analyze data incorrectly, resulting in results that are not able to be reproduced.

  * Methods - codes not available: Reviewers and scientists are often unable to verify the replicability of a study because the authors do not make the code public.

  * Insufficient peer review: Many peer-reviewed journals do not go through the author's code, which can lead to incorrect analyses being published.
  
  
## Best-Practices to Ensure Reproducibility  

There are many steps we can take as students, researchers, and scientists to perform studies and analyses which are fully-reproducible.

Most notably, we can:
  * Consider the power of statistical tests and their weaknesses.
  * Use prior knowledge to perform 'sanity' checks of your work along the way to avoid reaching incorrect conclusions.
  * Be careful to use statistical inference and hypothesis testing correctly, understand their assumptions, and only employ them when the assumptions are met.
  * Stay current by using modern, field-accepted analysis methodologies.
  * Think carefully about correcting for multiple comparisons in large studies.
  * Write a code that is highly-commented to explain the reasoning behind the analyses done.
  * Release the code for the public when publishing a study so peers can follow all steps of your data analysis. (Few scientific studies today are published with the code freely available for others to use, and hopefully this trend will change in the coming years).
  * There are a plethora of tools available to help you increase the reproducibility of your code and enable others to understand what you have done.



##

# Unit 3.03

[Survival analysis](https://en.wikipedia.org/wiki/Survival_analysis) is a branch of statistics for analyzing the expected duration of time until one or more events happen, such as death in biological organisms and failure in mechanical systems.


Reporting terms
  * p: proportion, from 0 to 1.
    * 2 deaths, 8 survivors
    * p = 0.2
  * odds = p/(1-p)
    * odds grows much faster than p
  * odds ratio: comparing two groups: group 1 and reference group
    * odds ratio (OR) = odds_1/odds_ref
  * OLS (ordinary least square): $y' = sigmoid(\beta_0 + \beta_1 x)$, where $sigmoid(a) = 1/(1 + exp(-a))$
    * $logit(y) = log(y/(1-y))$
    * therefore, logit(p) = log(odds).
    * --> find links between \beta_0, \beta_1 and odds

```{r}
xs = seq(0, 0.8, len=10)
xs
plot(xs, xs, type='l', ylab="f")
lines(xs, xs/(1-xs), col='red')
lines(c(0,1), c(0.5, 0.5), lty=2)

```

## Case Study: Reproducing Studies Using MIMIC-III

  * [Google BigQuery project](https://console.cloud.google.com/bigquery)
  
***Odds ratio*** is more widely used than relative risks.
  
  
# Unit 3.04

Tree-based models: from decision tree to Gradient Boosting
  * [Tutorial](https://github.com/alistairewj/tree-prediction-tutorial)

## Set up the environment

Setting up the environment
If you downloaded the repository to your local machine most requirements should be met with a simple terminal command:

```
pip install pydotplus numpy pandas sklearn matplotlib jupyter
```

If you want the exact version of all the packages installed, you can use the requirements.txt file from the repository:

```
pip install -r requirements.txt
```

### What I have done

```
conda env list

conda create --name py36a2021 --clone py36a

activate py36a2021

pip install -r requirements.txt
# installation was done nicely (trouble free! whew!)
```


## Decision Trees

Properties summary
To wrap up, tree properties to be tuned are:
 
  * Splitting criteria
    * Gini index and entropy
  * Limit the tree size
    * Maximum tree depth and prune the tree
  * Number of samples
    * Minimum in a leaf
    * Minimum to split in a node
  * Software package
    * CART
    * ID3
    * C4.5
    * C5.0 (computationally more expensive)

## Boosting

The premise of boosting is the combination of many weak learners to form a single "strong" learner. In a nutshell, boosting involves building models iteratively, and at each step, focus on the data we performed poorly on.

In our context, we'll use decision trees. The first step would be to build a tree using the data. Next, we'd look at the data that we misclassified and re-weight the data to classify those observations correctly, at a cost of maybe getting some of the other data wrong this time. Let's see how this works in practice.

AdaBoost
  * train a (sub-)model and evaluate training results
  * weight miss classified points higher and train another (sub-)model
  * keep doing it
  * use prediction from (sub-)models by weighing their outputs using weight = 1/error

## Bagging


Bagging is almost the same, except that we don't selectively choose which observations to focus on, but rather we randomly select subsets of data each time or in each iteration.

## Random Forest

The Random Forest takes this one step further (from bagging): instead of just resampling our data, we also select only a fraction of the features to include.

## Gradient Boosting

Gradient boosting (GB) is our last topic - and elegantly combines concepts from the previous methods. As a "boosting" method, GB involves iteratively building trees, aiming to improve upon misclassifications of the previous tree. GB also borrows the concept of subsampling the number of columns (as was done in Random Forests), which tends to prevent overfitting.

... the biggest innovation in GB is that it provides a unifying mathematical framework for boosting models.

GB explicitly casts the problem of building a tree as an optimization problem, defining mathematical functions for how well a tree is performing (which we had before) and how complex a tree is. 

In this light, one can actually treat AdaBoost as a "special case" of GB, where the loss function is chosen to be the exponential loss.

## Dataset: Breast Cancer Wisconsin (Diagnostic)

To make appropriate comparisons, we should calculate 95% confidence intervals on these performance estimates. This can be done a number of ways; ***the easiest is to bootstrap the calculation.***

# Unit 3.04 Workshop: Predictive Models

Let's practice all models checked in this workshop with real-world data. It contains patients admitted to intensive care units at the Beth Israel Deaconness Medical Center in Boston, MA. All patients in the cohort stayed for at least 48 hours, and the goal of the prediction task is to predict in-hospital mortality.

The data is originally provided as a time series of observations for a number of variables, but to simplify the analysis, we've done some preprocessing to get a single row for each patient. The following cell will check if the data is available here. If it's not, it will download it to the subfolder data in the same folder as this notebook.


# Unit 3.05 Workshop: Fairness and Bias

In late 2019, a group of researchers found widespread bias in a broadly deployed algorithm for predicting the medical complexity of patients, with the algorithm assigning lower risk scores to Black patients with a similar level of need as white patients. At the centre of this problem was the developers seemingly innocuous use of healthcare spending as a proxy for medical care needs - despite intentionally excluding race as a factor in the algorithm, the researchers failed to account for the systemic factors which lead Black patients to receive lower cost care.

This case is prototypical of the risks facing machine learning in healthcare. While these technologies have the potential to bring about revolutions in care cost and quality, they also have the potential to exacerbate inequities by improving care to a lesser degree for, or even directly harming, marginalized groups.

