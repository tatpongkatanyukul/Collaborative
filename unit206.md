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
