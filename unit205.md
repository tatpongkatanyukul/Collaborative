# Unit 2.05

Statistical models depend on having complete data to use for both exposure and outcome variables, and so we must figure out how to deal with missing data: do we remove incomplete entries and (dramatically) shrink our dataset? Do we replace missing values with estimates (imputation)? And how do we evaluate these strategies?

Types of Missingness
  * The value is missing because it is forgotten, lost, or was never entered. For example, we measured some value but it was never entered into the EMR. 
  * The value is missing because it is not applicable to the instance. For example, we don't have ventilator information for a patient that was taken off the ventilator, and so these records are left empty in the database.
  * The value is missing because it is of no interest to the instance. For example, we didn't measure something about a patient because it is not relevant to their current condition. 
  
## Missing Data Definition
  
See [GitHub Unit 2.05](https://github.com/criticaldata/hst953-edx/blob/master/2.05%20Missing%20Data/Missing%20Data.Rmd) for hands-on exercises

## Types of Missingness

> ... the reason why data is missing is critically important to determine how to approach dealing with the missing information.

  * Missing Completely at Random (MCAR): a scenario in which there is no relationship linking the various missing data points together, and they are truly random. In technical terms, the probability that an observation is missing is not dependent on either the data you have or the data that is missing. You might imagine this as a computer glitch causing every other patient's gender to not be recorded: there is no hidden relationship underlying the missingness of the data.
  * Missing at Random (MAR): In this case, the probability that the data is missing is dependent on the observable data, and so the missing data can be computed from the observed data as the two are statistically related. Essentially, some observable variable (or other pieces of data) allows us to infer an answer about the missing data. For example, if elderly people were more likely to forget they previously had pneumonia, and so forget to tell you, you would have lots of missing data for your variable "has previously had pneumonia," but this missing data would be tied to the "age" variable, and so may be inferable.
  This is a bit of a misnomer: the data is not missing at random but is missing because of a known or identifiable factor that is within your observed data.
  * Missing Not at Random (MNAR): this is when neither MCAR nor MAR hold, and so your missing data depends in some way on the data that is missing, and so cannot be trivially derived -- if at all -- from the observed data that you have. For example, imagine that patients with low blood pressure will have their blood pressure measured less frequently, creating missing data for "blood pressure" that is dependent on the low value for blood pressure.
  
## How to Handle Missing Data

So what do we do about missing data?  Should we ignore it, make up random data to fill its place, or delete all the missing data?

### How much data is missing?
This is an important consideration to look at from the start: it is important to calculate the percentage of missing data for each variable you are considering before moving forward. This will start to clarify what your next steps might be. For example, if 1% of height data is missing, then it may be most effective to remove the patients with those missing data sets for your analysis. If 99% of your data is missing, then it may be more helpful to remove that variable from all of your patients. If your data is somewhere in the middle, however, you will have to consider other options.   

### Overview of Handling Missing Data

Whether missing data is MCAR, MAR, or MNAR shapes how you approach processing the missing data. In general, we aim for the simplest approach and one that minimizes the amount of bias introduced into our analysis. 

MCAR and MAR data can be safely ignored, and so any method can be safely applied. This is a terrific advantage, but it is difficult to specifically determine that data is MCAR or MAR. To test this, we can compare multiple methods of processing the data and use the differences in the results to see if your assumptions make sense. 

The key methods for handling data are:

  * Deletion methods
  * Single imputation methods
  * Model-based methods

#### Deletion Methods

The simplest way of handling missing data is to simply delete the cases with missing values. Generally, this leads to valid inferences only for MCAR.

##### Complete-Case Analysis (Listwise Analysis)

All observations with missing data are discarded so that only individuals with complete data are kept. For example, if you have 100 variables and a single variable is missing, then that entry will be deleted.

This assumes that the missing data is truly random, and so the remaining data are representative of the population, and there is no subgroup bias created. Because this assumes an MCAR mechanism, this is fairly restrictive. However, it is distinctly simple and reasonable to use when the number of observations to discard is relatively small. 

However, power is reduced (smaller resulting sample size) which leads to larger standard errors in the analysis, and if the data is not actually MCAR, bias is likely introduced. 

##### Available-Case Analysis

Only the data needed for the specific analysis at hand are deleted, as opposed to all entries. If 10% of your patients are missing a data entry about "height," when only a data entry about "weight" is needed, then you keep all the entries with their weight and only delete those who are missing height. If you need both height and weight for analysis, then any cases missing either height or weight can be removed. This preserves more information, but the populations of each analysis may be different and hence non-comparable.

## Handling Missing Data: Weighting-Case Analysis
  
Weighting models the degree of missingness to reduce bias introduced in deleting missing data, essentially calculating replacements for the missing values. This process is called imputation. Functionally speaking, you are building a model of your data and then using that model -- whatever it looks like -- to estimate what is missing. 

### Single-Value Imputation

Here, we are trying to generate singular replacements for empty cells in our table, and through the various methods, we may generate different kinds of predicted values for the missing data at hand.

  * Mean and Median
    * Median would be the best approach if your data contains a significant amount of outliers, as the mean may be more skewed by these.
    * The downsides, however, are that this reduces natural variability within your data and lowers the accuracy of your error estimates, while also disregarding any natural relationship between variables and reducing intervariable correlation within your data. This introduces its own set of biases.
  * Linear Interpolation
    * This method is great for time series. You interpolate the values of the previous and next measurements of the patient and then fill in the data as needed.
  * Hot Deck and Cold Deck
    * With Hot Deck, you replace missing values with values from an estimated distribution of your current dataset -- this is used in survey research. You first partition the data into clusters, then associate the missing data with each cluster, utilizing each cluster to fill in the missing value (this could involve using the mean, median, or mode within the associated clusters).
    * Cold deck imputation is similar, but the data source is different. A hot deck tries to preserve the distribution of your variable distribution but may underestimate standard error and variability.
  * Last Observation Carried Forward
    * AKA "sample and hold," this method works well with longitudinal designs. You impute the missing value based on the last available observation of an individual (ie. you do not have the patient's weight for today, but you do from a month ago, so you use that value). This method makes the assumption that the individual has not changed since their last observation, which is often untrue.

[Hands-on Unit 2.05](https://github.com/criticaldata/hst953-edx/blob/master/2.05%20Missing%20Data/Missing%20Data.Rmd)
