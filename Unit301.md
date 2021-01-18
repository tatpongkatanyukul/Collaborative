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

[hands-on: tree-based classification](https://colab.research.google.com/github/alistairewj/tree-prediction-tutorial/blob/master/trees-classification.ipynb)


# Unit 3.05 Workshop: Fairness and Bias

In late 2019, a group of researchers found widespread bias in a broadly deployed algorithm for predicting the medical complexity of patients, with the algorithm assigning lower risk scores to Black patients with a similar level of need as white patients. At the centre of this problem was the developers seemingly innocuous use of healthcare spending as a proxy for medical care needs - despite intentionally excluding race as a factor in the algorithm, the researchers failed to account for the systemic factors which lead Black patients to receive lower cost care.

This case is prototypical of the risks facing machine learning in healthcare. While these technologies have the potential to bring about revolutions in care cost and quality, they also have the potential to exacerbate inequities by improving care to a lesser degree for, or even directly harming, marginalized groups.

An excellent approach to fairness in machine learning is formalized in the work of [Gajane and Pechenizkiy (2018)](https://arxiv.org/pdf/1710.03184.pdf)

## Parity or preference?

For example, imagine an algorithm designed to allocate a gender-balanced group of 100 people either pizza or spaghetti for dinner, with only 50 of each dinner option available. If 60% of men prefer spaghetti and 60% of women prefer pizza, what is a fair way of allocating these foods?
  * A parity-preserving approach would strive for a representative division regardless of preference, assigning 25 pizza and 25 spaghetti to each group.
  * A preference-preserving approach would strive to optimize for the preference of users, assigning 30 pizza and 20 spaghetti to the women, and assigning 20 pizza and 30 spaghetti to the men.


Disparate Treatment in the Healthcare System:

Disparate treatment in healthcare arises from a wide range of origins, including direct implicit bias on the part of healthcare practitioners and structural disparities in the construction and delivery of healthcare services. A brief, non-exhaustive list of examples of such disparities follows:

Disparities in Treatment:
African Americans, both children and adults are less likely to receive appropriate pain treatment when in acute distress, even when controlling for age, sex, and time of treatment.
Up to half of medical students in one study hold the physiologically false belief that Black and white patients experience pain differently 
Disparities in Diagnosis:
Women presenting to the emergency department with coronary syndromes are less likely than men with the same symptoms to be admitted to acute care.
Black patients experiencing symptoms of major depression are more likely to receive a potentially inappropriate diagnosis of schizophrenia 
Medical students often only learn to diagnose important and common dermatologic findings on light colored skin, with darker skin being treated as an afterthought.
Structural Disparities:
54% of rural counties do not have a hospital with obstetrics services 
Elderly LGBT individuals experience isolation, and a lack of access to culturally competent healthcare and social service providers 
Understanding these treatment disparities is important to machine learning in that many models implicitly use existing healthcare processes as their "gold standard" for recommendations. A model that attempts to predict diagnostic decisions for patients, for example, will itself be biased if it is generated based on biased physician decisions.

Disparate Outcomes in the Healthcare System:

Healthcare disparities, along with broader disparities in social and government services, contribute to wildly disparate health outcomes for different groups in American society. A similarly non-exhaustive list of these disparities follows:

Life Expectancy Gaps:
The life expectancy at birth for white Americans is 4.4 years longer than for Black Americans.
Life expectancy varies by up to 7 years between states.
Infant Mortality Gaps:
Infant mortality is twice as high for Black Americans as compared to white Americans, at each level of socioeconomic status 
American Indian and Alaska Native infants are 2.7x as likely to die from accidents before one year of age
Chronic Health Problem Gaps:
Puerto Ricans are 72% more likely to develop asthma than non-Hispanic whites 
LGBT youth are more likely to be homeless and 2-3x more likely to attempt suicide.
These vast prior differences in health outcomes between populations cannot be ignored in healthcare data science research, particularly for those models that seek to predict patient outcomes. As recent scholarship has argued, accounting for these disparities is not necessarily so simple as adding a "race factor" to account for and adjust results - as such interventions may act only to set disparities in stone.

Disparities in Medical Knowledge Generation:

Another substantial source of unfairness in healthcare is the biased nature of the medical knowledge generation system, which broadly holds a single (typically white, and typically male) prototype for the presentation and course of disease.

Framingham Scores:
A classic example of disparity in knowledge generation arises from the Framingham risk study, which generated cardiovascular risk scores from long-term examination of the predominantly white, working class town of Framingham Massachusetts. Perhaps unsurprisingly, these scores perform more poorly when applied to Black patients.
Clinical Trials:
Clinical trials for drugs and treatments that go on to influence the care of a diverse range of patients from around the world are often tested on a predominantly white and male population, with women and people of color frequently excluded from or underrepresented in studies.
In the machine learning context, these disparities can represent a classic example of dataset shift, as the training population (predominantly white and male) can vary substantially in its characteristics as compared to the (broadly diverse) testing population. It is always important to interrogate the demographic makeup of data source populations, and where possible to seek to improve the diversity of datasets (as, for example, the "All of Us" researchers are attempting to do).

Trust:

From sordid medical experiments performed on slaves, to the infamous "Tuskegee Syphilis Study" wherein African American men were not given treatment for advanced stage syphilis in order to study the disease's effects, medicine has routinely exploited Black patients in the name of "research". Similarly, the psychiatric pathologization of homosexuality provided a long-standing pretext for anti-gay bigotry. Understandably, it follows that African Americans and LGBT individuals (particularly those with intersectional identities) have high levels of mistrust toward the medical establishment. It is important for those seeking to implement data science in healthcare to understand this history, and to understand the critiques of those who fear that these technologies may act simply to "automate racism" and further disparities. Trust in healthcare data science is something that must be built and earned, rather than assumed.


***Error due to variance*** arises when there is a lack of data for a specific group, leading to a poor estimate. It is solved by gathering additional data.

![Variance](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Variance.png)

***Error due to bias*** arises when there are legitimately different data functions between groups. It may be solved by changing the model class.

![Bias](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Bias_due_to_variance.png)

***Error due to noise*** arises when there is a greater degree of noise for the minority group on a given set of features. It may be solved by adding additional features.

![Noise](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Bias_due_to_noise.png)


One excellent method for assessing the nature of a dataset and whether it is suitable for a specific application arises from the concept of "datasheets for datasets", developed by Timnit Gebru et al. The method involves 50 relevant questions around the motivation, composition, collection process, cleaning process, uses, distribution, and maintenance of a machine learning model.

The machine learning pipeline can be vulnerable to bias at each of its many steps (Harini Suresh et al):
  * Data Collection refers to the initial gathering of the data in the real world
  * Data Preparation refers to the decisions made in structuring and pre-processing the data for deployment, as well as the designation of train, test, and validation sets.
  * Model Development refers to the process of choosing and designing the model, as well as tuning its parameters
  * Model Evaluation refers to the process of evaluating the performance of the model against either a reserved dataset or a benchmark dataset
  * Model Postprocessing refers to the decisions made in better aligning the developed model to its target use cases
  * Model Deployment refers to the real-world steps to deploying the model in its operative environment.
Each of the decisions made at each of these points implicitly embeds certain values and will have certain impacts. A wide range of methods have been proposed for addressing fairness in model construction at each of these levels.

### Unfairness Arising from Socio-Technical Context:

Focusing too directly on "biased data" or "poor model design", however, can be insufficient to describe all relevant socio-technical considerations that play a role in machine learning-driven unfairness or bias. Increasingly, fairness researchers are taking a process-oriented view, and emphasizing that the machine learning pipeline from beginning to end consists of a series of value-driven decisions. We will explore this topic through the framework of Harini Suresh and John V. Guttag (2020).

### Types of Bias:

  * Historical Bias arises when the structure of the world is misaligned with the values or objectives to be encoded or propagated by a model. Importantly, this bias exists in the broader context of the world and is not solved by perfect model design.
  * Representation Bias arises when the training population under-represents a specific portion of the use case population, and thus does not perform well for that portion of the population
  * Measurement Bias arises when the chosen set of features (typically proxy features) does not align well with the actual desired characteristics that the model is attempting to capture.
  * Aggregation Bias arises when distinct populations are inappropriately combined, and a heterogeneous group is reduced to a single model.
  * Evaluation Bias arises when the testing or benchmark population does not accurately represent the use case population (or when the metrics being used to evaluate the model are not aligned with the way the model is supposed to be used)
  * Deployment Bias arises when the model is used or interpreted in inappropriate ways after model deployment.
The diversity of machine learning practitioners is another important component of the sociotechnical context. Women and BIPOC individuals are broadly underrepresented in the machine learning world, and this has implications for the field's "blind spots", and the questions that are and are not asked during the development process.

## Fairness and Bias in Machine Learning for Healthcare

Changes in healthcare practice brought on by the introduction of models may introduce novel inequities into healthcare. One clear example of this was the introduction of melanoma-detection algorithms that are trained predominantly on images of light skin. (JAMA Netw Open. 2019;2(10):e1913436. doi:10.1001/jamanetworkopen.2019.13436)


