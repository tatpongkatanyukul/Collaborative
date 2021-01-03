# Unit 2.07 

## Exploratory Data Analysis

Exploratory data analysis (EDA) is an essential step in any research analysis. The primary aim of exploratory analysis is to examine the data for distribution, outliers, and anomalies to direct speciﬁc testing of your hypothesis. 
It also provides tools for hypothesis generation by visualizing and understanding the data usually through graphical representation [1].
...
According to Howard Seltman (Carnegie Mellon University), “loosely speaking, any method of looking at data that does not include formal statistical modeling and inference falls under the term exploratory data analysis” [4].
...
EDA is a fundamental early step after data collection (see subsection 2.03) and pre-processing (see subsection 2.04), where the data is simply visualized, plotted, manipulated, without any assumptions, in order to help assess the quality of the data and building models. “Most EDA techniques are graphical in nature with a few quantitative techniques. The reason for the heavy reliance on graphics is that by its very nature the main role of EDA is to explore, and graphics gives the analysts unparalleled power to do so while being ready to gain insight into the data. There are many ways to categorize the many EDA techniques” [5].
...
The interested reader will ﬁnd further information in the textbooks of Hill and Lewicki [6] or the NIST/SEMATECH e-Handbook [1]. Relevant R packages are available on the CRAN website [7].

References
  * [1] Natrella M (2010) NIST/SEMATECH e-Handbook of Statistical Methods. NIST/SEMATECH
  * [4] Seltman HJ (2012) Experimental design and analysis
  * [5] Kaski, Samuel (1997) “Data exploration using self-organizing maps.” Acta polytechnicascandinavica: Mathematics, computing and management in engineering series no. 82. 1997.
  * [6] Hill T, Lewicki P (2006) Statistics: methods and applications: a comprehensive reference for science, industry, and data mining. StatSoft, Inc., Tulsa
  * [7] CRAN (2016) The Comprehensive R archive network—packages. Contributed Packages, 10 Jan 2016 [Online]. Available: https://cran.r-project.org/web/packages/. Accessed: 10 Jan 2016
  
## What is Exploratory Data Analysis

> "It is important to understand what you CAN DO, before you learn to measure how WELL you seem to have DONE it."
- J. W. Tukey (1977)

> exploratory and comfirmatory (analysis) can and should proceed side by side
- J. W. Tukey (1977)

## Suggested EDA Techniques

EDA Technique by Data Type
  * Categorical: Descriptive statistics
  * Univariate continuous: Line plot, Histograms
  * Bivariate continuous: 2D scatter plots
  * 2D arrays: Heatmap
  * Multivariate, i.e., trivariate: 3D scatter plot or 2D scatter plot with a 3rd variable represented in different color, shape, or size
  * Multiple groups: Side-by-side boxplot
  
EDA Technique by Objective
  * Getting an idea of the distribution of a variable: Histogram
  * Finding outlier: Histogram, scatterplots, box-and-whisker plots
  * Quantify the relationship between two variables (one exposure and one outcome): 2D scatter plot +/- curve ﬁtting, Covariance and correlation
  * Visualize the relationship between two exposure variables and one outcome variable: Heatmap
  * Visualization of high-dimensional data: t-SNE or PCA, 2D/3D scatterplot
  
## Univariate Non-Graphical EDA

  * Categorical Data: Tabulation of the Frequency of Each Category
    * A simple univariate non-graphical EDA method for categorical variables is to build a table containing the count and the fraction (or frequency) of data of each category.
  * Quantitative Data: Characteristics
    * Sample statistics express the characteristics of a sample using a limited set of parameters. They are generally seen as estimates of the corresponding population parameters from which the sample arises. These characteristics can express the central tendency of the data (arithmetic mean, median, mode), its spread (variance, standard deviation, interquartile range, maximum and minimum value) or some features of its distribution (skewness, kurtosis). Many of those characteristics can easily be seen qualitatively on a histogram (see below). Note that these characteristics can only be used for quantitative variables (not categorical).
  
### Central Tendency Parameters
The arithmetic mean, or simply called the mean, is the sum of all data divided by the number of values. The median is the middle value in a list containing all the values sorted. Because the median is affected little by extreme values and outliers, it is said to be more "robust" than the mean
  
### Variance

When calculated on the entirety of the data of a population (which rarely occurs), the variance σ2 is obtained by dividing the sum of squares by n, the size of the population. The sample formula for the variance of observed data conventionally has n-1 in the denominator instead of n to achieve the property of "unbiasedness", which roughly means that when calculated for many different random samples from the same population, the average should match the corresponding population quantity (here σ^2). s^2 is an unbiased estimator of the population variance σ^2.

s^2 = \frac{ \sum_i (x_i -\bar{x})^2}{n-1}

For a theoretical Gaussian distribution, mean plus or minus 1, 2 or 3 standard deviations holds 68.3, 95.4 and 99.7 % of the probability density, respectively.

### Interquartile Range (IQR)

The IQR is calculated using the boundaries of data situated between the 1st and the 3rd quartiles.
...  In the same way that the median is more robust than the mean, the IQR is a more robust measure of spread than variance and standard deviation and should therefore be preferred for small or asymmetrical distributions.

Important Rule (of thumb):
  * Symmetrical distribution (not necessarily normal) and N > 30: State results as mean ± standard deviation.
  * Asymmetrical distribution or N < 30 or evidence for outliers: Use median ± IQR, which is more robust.
  
Non-Graphical Univariate EDA in R
  * summary(x)	General description of a vector
  * max(x)	Maximum value
  * mean(x)	Average or mean value
  * median(x)	Median value
  * min(x)	Smallest value
  * sd(x)	Standard deviation
  * var(x)	Variance, measure the spread or dispersion of the values
  * IQR(x)	Interquartile range
  
## Multivariate Non-Graphical EDA

  * Cross Tabulation
    * Cross-tabulation represents the basic bivariate non-graphical EDA technique. It is an extension of tabulation that works for categorical data and quantitative data with only a few variables. For two variables, build a two-way table with column headings matching the levels of one variable and row headings matching the levels of the other variable, then ﬁll in the counts of all subjects that share a pair of levels. The two variables may be both exposure, both outcome variables, or one of each.
  * Summary Statistics
    * Summary statistics include, frequency, mean, median, mode, range, interquartile range, maximum and minimum values. An extract of summary statistics of patient demographics, vital signs, laboratory results and comorbidities, is shown in Table 2.07.4.
    
Table 2.07.4: Comparison between the two study cohorts (subsample of variables only, n = 1776)
![ComparisonBetween2Cohorts](https://github.com/tatpongkatanyukul/Collaborative/blob/main/ComparisonB2cohorts.png)
  
  
---
