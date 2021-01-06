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

It is important to identify any differences in subject baseline characteristics. The beneﬁts of this are two-fold: ﬁrst it is useful to ***identify potentially confounding variables*** that contribute to an outcome in addition to the predictor (exposure) variable. For example, if mortality is the outcome variable then differences in severity of illness between cohorts may wholly or partially account for any variance in mortality. Identifying these variables is important as it is possible to attempt to control for these using adjustment methods such as multivariable logistic regression. Secondly, it may allow the ***identiﬁcation of variables that are associated with the predictor variable*** enriching our understanding of the phenomenon we are observing.

The analytical extension of identifying any differences using medians, means and data visualization is to test for statistically signiﬁcant differences in any given subject characteristic using for example Wilcoxon-Rank sum test.

![Identify factors](https://github.com/tatpongkatanyukul/Collaborative/blob/main/IdentifyingConfoundingFactorsB2cohorts.png)

### Covariance & Correlation

A positive covariance means the variables are positively related (they move together in the same direction), while a negative covariance means the variables are inversely related.

A problem with covariance is that its value depends on the scale of the values of the random variables.
Given cov(x,y), the larger the values of x and y, the larger the covariance. 

It makes it impossible for example to compare covariances from data sets with different scales (e.g. pounds and inches). This issue can be ﬁxed by dividing the covariance by the product of the standard deviation of each random variable, which gives ***Pearson’s correlation coefﬁcient.***

cor(x,y) = cov(x,y)/( s_x s_y )
where cov(x,y) is the covariance between x and y
and s_x and s_y are the sample standard deviations of x and y.

The signiﬁcance of the correlation coefﬁcient between two normally distributed variables can be evaluated using Fisher’s z transformation (see the cor.test function in R for more details). Other tests exist for measuring the non-parametric relationship between two variables, such as Spearman’s rho or Kendall’s tau.

## Graphical EDA: Histograms

Histograms are among the most useful EDA techniques, and allow you to gain insight into your data, including distribution, central tendency, spread, modality and outliers.

... Histograms give an immediate impression of the shape of the distribution (symmetrical, uni/multimodal, skewed, outliers…).
The number of bins heavily inﬂuences the ﬁnal aspect of the histogram; ***a good practice is to try different values, generally from 10 to 50.***

Histograms enable the conﬁrmation that an operation on data was successful. For example, if you need to log-transform a data set, it is interesting to plot the histogram of the distribution of the data before and after the operation (Fig. 2.07.4).

![Fig 2.07.4](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Fig2074logTransform.png)

Histograms are interesting for ﬁnding outliers. For example, pulse oximetry can be expressed in fractions (range between 0 and 1) or percentage, in medical records. Figure 2.07.5 is an example of a histogram showing the distribution of pulse oximetry, clearly showing the presence of outliers expressed in a fraction rather than as a percentage.

![Fig 2.07.5](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Fig2075_pulseoximetry.png)


### Stem Plots

Stem and leaf plots (also called stem plots) are a simple substitution for histograms.

My question: how about violin plot?

## Graphical EDA: Boxplots

Boxplots are interesting for representing information about the central tendency, symmetry, skew and outliers, but they can hide some aspects of the data such as multimodality. Boxplots are an excellent EDA technique because they rely on robust statistics like median and IQR.

The central rectangle is limited by Q1 and Q3, with the middle line representing the median of the data. The whiskers are drawn, in each direction, to the most extreme point that is less than 1.5 IQR beyond the corresponding hinge. Values beyond 1.5 IQR are considered outliers.

It is also important to realize that the number of boxplot outliers depends strongly on the size of the sample. In fact, for data that is perfectly normally distributed, we expect 0.70 % (about 1 in 140 cases) to be “boxplot outliers”, with approximately half in either direction.


## Graphical EDA: Probability Plots

The interpretation of a QN plot is visual (Fig. 2.07.7): either the points fall randomly around the line (data set normally distributed) or they follow a curved pattern instead of following the line (non-normality).

![QQ plot](https://github.com/tatpongkatanyukul/Collaborative/blob/main/QQplot.png)

Deviation of the observed distribution from normal makes many powerful statistical tools useless. Note that some data sets can be transformed to a more normal distribution, in particular with log-transformation and square-root transformations. If a data set is severely skewed, another option is to discretize its values into a ﬁnite set.

## Graphical EDA: Scatterplots

For binary variables (e.g. 28-day mortality vs. SOFA score), 2D scatterplots are not very helpful (Fig. 2.07.11, left). By dividing the data set in groups (in our example: one group per SOFA point), and plotting the average value of the outcome in each group, scatterplots become a very powerful tool, capable for example to identify a relationship between a variable and an outcome (Fig. 2.07.11, right).



![Scatter plot](https://github.com/tatpongkatanyukul/Collaborative/blob/main/scatter_plot.png)

## Graphical EDA: Scatterplot Examples

APACHE ~ [APACHE II](https://en.wikipedia.org/wiki/APACHE_II)
---Acute Physiology And Chronic Health Evaluation II--- is a severity-of-disease classification system.
... an integer score from 0 to 71 is computed based on several measurements; higher scores correspond to more severe disease and a higher risk of death.

## Graphical EDA: Curve Fitting

Curve ﬁtting is one way to quantify the relationship between two variables or the change in values over time.

## EDA Tools

### Visualization
  * R's ```ggplot2```, ```lattice```, and ```shiny```
  * Tableau
  * Plotly
  * Python's matplotlib and ggplot clone
  * D3.js
  
  

### Descriptive Statistics
	* R's tableone, dplyr
	* Python's tableone
	* SAS's PROC univariate
	* Any stats package
	* SQL


## Integrating EDA into Confirmatory Analysis

## Conclusion

... cognitive disfluency ~ human learns better when it's harder to learn sometimes. So when you slow things down, make things harder, it often is a good check to makke sure that you're trying to understand the data as best you can.
... goal is trying to figure out what data is saying.

---

## EDA Workshop

These questions must be answered by examining and having hands-on [the workshop](https://github.com/criticaldata/hst953-edx/blob/master/2.07.%20Exploratory%20Data%20Analysis/eda_workshop_student.Rmd).
Questions may sound vague, but it will make more sense when working with the workshop R markdown.

### Question 1a
How many patients in the MICU had an indwelling arterial catheter?

Note: field ```aline_flg``` records use of indwelling arterial catheter.
(1 = use?)

### Question 1b
What was the median age of patients with indwelling arterial catheters who died within 28 days of admission?

Note: field ```day_28_flg``` records whether a patient dies within 28 days of admission.
(1 = die?)

### Question 2a
How many patients with indwelling arterial catheters remained alive 28 days after admission?

### Question 3b
What fraction of patients with a SOFA score less than 5 was alive at hospital discharge?

Note: ```hosp_exp_flg``` records a patient has been discharged.
(1 = discharged?)

Term:
SOFA (sequential organ failure assessment) or [SOFA score](https://en.wikipedia.org/wiki/SOFA_score)
is, previously known as the sepsis-related organ failure assessment score, is used to track a person's status during the stay in an intensive care unit (ICU) to determine the extent of a person's organ function or rate of failure.

### Question 4b
What is the approximate 95% confidence interval for 28-day mortality in patients with a SOFA score of 7?

### Question 4c
In the group with the lowest SOFA scores, approximately what proportion of patients with indwelling arterial catheters die within 28 days of admission?
(My addition: given patients are grouped by their SOFA scores into ???)

### Question 4e
What SOFA score range of patients with indwelling arterial cathethers had the largest 28-day mortality 95% confidence interval?
(My addition: given patients are grouped by their SOFA scores into ???)







