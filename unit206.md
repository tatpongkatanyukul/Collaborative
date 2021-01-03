# Unit 2.06

## Introduction

An outlier is a data point which is different from the remaining data. Outliers are also referred to as abnormalities, discordants, deviants, and anomalies. Whereas noise can be defined as mislabeled examples (class noise) or errors in the values of attributes (attribute noise), outlier is a broader concept that includes not only errors but also discordant data that may arise from the natural variation within the population or process. As such, outliers often contain interesting and useful information about the underlying system. These particularities have been exploited in fraud control, intrusion detection systems, web robot detection, weather forecasting, law enforcement and medical diagnosis, generally using methods of supervised outlier detection (see below).

Within the medical domain in general, the main sources of outliers are equipment malfunctions, human errors, anomalies arising from patient-specific behaviors and natural variation within patients. Consider for instance an anomalous blood test result. Several reasons can explain the presence of outliers: **severe pathological states**, **intake of drugs, food or alcohol**, **recent physical activity**, **stress**, **menstrual cycle**, **poor blood sample collection and/or handling**. While some reasons may point to **the existence of patient-specific characteristics** discordant with the "average" patient, in which case the observation being an outlier provides useful information, other reasons may point to **human errors**, and hence the observation should be considered for removal or correction. Therefore, it is crucial to consider the causes that may be responsible for outliers in a given dataset before proceeding to any type of action.

Keys: outliers may be from
  * extreme underlying state, which provides useful info
  * human error, should be corrected
  
The negative effects of outliers can be summarized as: 
  * (1) increase in error variance and reduction in statistical power; 
  * (2) decrease in normality for the cases where outliers are non-randomly distributed; 
  * (3) model bias by corrupting the true relationship between exposure and outcome.

A good understanding of the data itself is required before choosing a model to detect outliers, and several factors influence the choice of an outlier identification method, including the type of data, its size and distribution, the availability of ground truth about the data, and the need for interpretability in a model. For example, regression-based models are better suited for finding outliers in linearly correlated data, while clustering methods are advisable when the data is not linearly distributed along correlation planes.

... the ground-truth about outliers is often unavailable, as in the case of unsupervised scenarios, hampering the use of quantitative methods to assess the effectiveness of the algorithms in a rigorous way. The analyst is left with the alternative of qualitative and intuitive evaluation of results. To overcome this difficulty in this chapter, we will use logistic regression models to investigate the performance of different outlier identification techniques in the medically relevant case study.

## Theoretical Concepts

### Outlier Detection

Outlier identification methods can be classified into supervised and unsupervised methods, depending on whether prior information about the abnormalities in the data is available or not. The techniques can be further divided into univariable and multivariable methods, conditional on the number of variables considered in the dataset of interest.

The simplest form of outlier detection is extreme value analysis of unidimensional data. In this case, the core principle of discovering outliers is to determine the statistical tails of the underlying distribution and assume that either too large or too small values are outliers. In order to apply this type of technique to a multidimensional dataset, the analysis is performed one dimension at a time. In such a multivariable analysis, outliers are samples which have unusual combinations with other samples in the multidimensional space. It is possible to have outliers with reasonable marginal values (i.e. the value appears normal when confining oneself to one dimension), but due to linear or non-linear combinations of multiple attributes these observations unveil unusual patterns in regards to the rest of the population under study.

![outliers](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Selection_003.jpg)

## Statistical Methods

In the field of statistics, the data is assumed to follow a distribution model (e.g., normal distribution) and an instance is considered an outlier if it deviates significantly from the model. Common statistical methods for outlier detection are listed below:
  * clinical ranges
  * experience
  * Tukey’s Method - Inner "fences" are located at a distance of 1.5 IQR below Q1 and above Q3, and outer fences at a distance of 3 IQR below Q1 and above Q3. A value between the inner and outer fences is a possible outlier, whereas a value falling outside the outer fences is a probable outlier.
    * IQR = Q3 - Q1
  * Z-Score -  The Z-value test computes the number of standard deviations by which the data varies from the mean. ... a good “rule of thumb” is to consider values with |z_i| >= 3 as outliers, where z_i is a z value of the datapoint x_i. 
    * Of note, this method is of limited value for small datasets, since the maximum z-score is at most (n-1)/sqrt(n).
  * Modified Z-Score - The estimators used in the z-score, the sample mean and sample standard deviation, can be affected by the extreme values present in the data. To avoid this problem, the modified z-score uses the median and the median absolute deviation (MAD) instead of the mean and standard deviation of the sample:
  M_i = 0.6745(x_i - x_bar)/MAD
where MAD = median(|x_i - x_bar|).
It is recommended that |M_i| >= 3.5 considered as potential outliers.

  * Interquartile Range with Log-Normal Distribution: If a variable follows a log-normal distribution then the logarithms of the observations follow a normal distribution. A reasonable approach then is to apply the natural log ```ln``` to the original data and then apply the tests intended to the "normalized" distributions. We refer to this method as the log-IQ.

  * Ordinary and Studentized Residuals: Studentized residuals eliminate the units of measurement by dividing the residuals by an estimate of their standard deviation. One limitation of this approach is that it assumes the regression model is correctly specified.
  * Cook's Distance -  In a linear regression model, Cook's distance is used to estimate the influence of a data point on the regression. The principle of Cook’s distance is to measure the effect of deleting a given observation. Data points with a large distance may represent outliers. For the i^th point in the sample, Cook's distance is defined as:
D_i = sum_{j=1}^n (y_i y_j(i))^2/((k+1) s^2).

  * Mahalanobis Distance - This test is based on Wilks method designed to detect a single outlier from a normal multivariable sample. It approaches the maximum squared Mahalanobis Distance (MD) to an F-distribution function formulation, which is often more appropriate than a chi2 distribution. For a p-dimensional multivariate sample  (i = 1,…,n), the Mahalanobis distance of the i^th case is defined as:
  MD_i = \sqrt{x_i - t}^T C^{-1} (x_i - t)}
where where t is the estimated multivariate location, which is usually the arithmetic mean, and C is the estimated covariance matrix, usually the sample covariance matrix.

Multivariate outliers can be simply defined as observations having a large squared Mahalanobis distance. In this work, the squared Mahalanobis distance is compared with quantiles of the F-distribution with p and p − 1 degrees of freedom. Critical values are calculated using Bonferroni bounds.  
  
  
## Outlier Analysis Using Expert Knowledge

In univariate analyses, expert knowledge can be used to define thresholds of values that are normal, critical (life-threatening) or impossible because they fall outside permissible ranges or have no physical meaning.

## Univariate Analysis (1)

![different outlier detections](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Selection_067.png)

As shown in the picture, overall Tukey’s and log-IQ are the most conservative methods, i.e., they identify the smallest number of points as outliers, whereas IQ identifies more outliers than any other method. With a few exceptions, the modified z-score identifies more outliers than the z-score.

The results in bold highlight the variable with the most outliers in each method, and also the method that removes more patients in total, in each class. Class 0: represents survivors, Class 1: non-survivors

A preliminary investigation of results showed that values falling within reference normal ranges (see Table 2.06.1) are never identified as outliers, whatever the method. On the other hand, critical values are often identified as such. Additional remarks can be made as in general (1) more outliers are identified in the variable BUN than in any other and (2) the ratio of number of outliers and total number of patients is smaller in the class 1 cohorts (non-survivors). As expected, for variables that approximate more to lognormal distribution than to a normal distribution, such as potassium, BUN and PCO2, the IQ method applied to the logarithmic transformation of data (log-IQ method) identifies less outliers than the IQ applied to the real data. Consider for instance the variable BUN, which follows approximately a lognormal distribution. 

## Outliers identified by statistical analysis

Normal values are in the range of 95–105 mmol/L, whereas values <70 or >120 mmol/L are considered critical, and concentrations above 160 mmol/L are physiologically impossible.


## Multivariable Analysis

Using model-based approaches, an unusual combination of values for a number of variables can be identified.

The detection of outliers seems to be more influenced by binary features than by continuous features: red lines are, with some exceptions, fairly close to black lines for the continuous variables (1 to 2 and 15 to 25) and distant in the binary variables. A possible explanation is that clustering was essentially designed for multivariable continuous data; binary variables produce a maximum separation, since only two values exist, 0 and 1, with nothing between them.

## Classification of Mortality in IAC and Non-IAC Patients

The performance of the models is evaluated in terms of area under the receiver operating characteristic curve (AUC), accuracy (ACC, correct classification rate), sensitivity (true positive classification rate), and specificity (true negative classification rate). A specific test suggested by DeLong and DeLong can then test whether the results differ significantly.

Overall, the best AUC is obtained when all the data is used, and when only a few outliers are removed.

## Conclusions & Key Takeaways

The univariable outlier analysis provided in the case study showed that a large number of outliers were identified for each variable within the predefined classes, meaning that the removal of all the identified outliers would cause a large portion of data to be excluded. For this reason, ranking the univariate outliers according to score values and discarding only those with the highest scores provided better classification results.

Overall, none of the outlier removal techniques was able to improve the performance of a classification model. As it had been cleaned these results suggest that the dataset did not contain impossible values, extreme values are probably due to biological variation rather than experimental mistakes. Hence, the “outliers” in this study appear to contain useful information in their extreme values, and automatically excluding resulted in a loss of this information.

Some modeling methods already accommodate for outliers so they have minimal impact in the model, and can be tuned to be more or less sensitive to them. Thus, rather than excluding outliers from the dataset before the modeling step, an alternative strategy would be to use models that are robust to outliers, such as robust regression.

Key Takeaways
  * Distinguishing outliers as useful or uninformative is not clear cut.
  * In certain contexts, outliers may represent extremely valuable information that must not be discarded.
  * Various methods exist and will identify possible or likely outliers, but the expert eye must prevail before deleting or correcting outliers.

code: [Critical Data and Codes](https://github.com/MIT-LCP/critical-data-book)
