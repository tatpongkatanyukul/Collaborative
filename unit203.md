# Unit 2.03-2.04

## 2.03 Introduction

The topics tackled in this section are applicable to all data science but are particularly pertinent when tackling medical data. Topics include:
   * What kind of Medical Data can be usually found in databases and how should it be interpreted and handled?
   * What are sources of bias in Medical Data and how can we account for them?
   * What should we take note of when trying to collaborate with professionals of other fields of science?
   * How can we ensure that our study is reproducible? Why is reproducibility important?
   * Whats is a Relational Database?
   * How can I query medical databases?
   
## Data Types in Medical Datasets

  * Billing Data: Biling data usually consists of the codes that hospitals and caregivers use to file claims with insurance providers. 
     * used mainly for billing and so may not accurately reflect the care the patient received in the issue.
  * Charted Physiological Data: Charted physiological data includes all measurements done at the bedside, such as heart rate, blood pressure and respiratory rate. This type of data often has a high sampling rate and so is automatically introduced into the database
     * ***The sampling rate is variable*** depending on the type of event being measured and the state of the patient, sicker patients usually have a higher frequency of data collection. ***Data is often archived at a lower sampling rate than it is collected using averaging algorithms*** that are proprietary and undisclosed. The way this data is stored and collected can vary widely between medical centers.
  * Notes and Reports: Notes are usually written up by nurses or medical doctors to record patient progress, summarize a patient stay upon discharge, or provide findings from imaging studies. It may also contain images such as X-rays, computerized axial tomography (CAT/CT) scans, echo cardiograms, magnetic resonance imaging and others. These notes may contain a wealth of extra data that can enrich any study due to the more free form nature of the data type.
    * Natural Language Processing (NLP) techniques are used. As these notes were written by a person, they are prone to human error (typos, missing data, bias, etc).
  * Laboratory Data: It contains the results of laboratory tests requested by the physician and is usually quantitative.
    * Laboratory tests are conducted by humans and so they suffer from the same problems as charted physiological data (missing values, errors, different methodologies, etc).
    * since these analysis for the most part must be requested, not all patients will have data on all laboratory tests. The timestamp associated with the result may indicate the time the test was requested or the time the test was reported.
  * Medication Data: Medication data contains information on what medication the doctor ordered for each patient. This will include a dosage and, if the medication is infused, a delivery rate. This data type contains information related to a variety of drugs including IV drugs or tablets and so different units may be used.
   * Although these records mean the medication was ordered, they do not guarantee that the patient took the medication.
   * This data is usually input by hospital staff, so errors and missing data are possible. The timestamp associated with each entry may refer to the time the doctor ordered the medication or to the time when the drug was administered.

## Collaborations and Data Source Bias

> One of the greatest challenges of working with medical data is understanding the context in which the data is collected. Collaboration between hospital staff and research analysts is crucial to success. However, it can be easy for members of either group to misunderstand one another or to have different expectations of how the dataset can be used. 

### Biases

In a hospital setting, these biases may be tied to factors such as the patient populations served, the local practices of caregivers, or to the type of services provided. For example:
  * Academic centers often see more complicated patients, and some hospitals may tend to serve patients of a specific ethnic background or socioeconomic status
  * Follow-up visits may be less common at referral centers, so they may be less likely to detect long-term complications
  * Research centers may be more likely to place patients on experimental drugs not generally used in practice
  
> Although there is very little that can be done to completely eliminate biases from your data, it is important to be aware of the possible sources of bias to mitigate them and to correctly interpret the final results of your study. 

## Reproducibility

> There is currently a reproducibility crisis in the scientific community: some researchers are unable to replicate peer-reviewed papers.

> Several factors can be identified as the origin for this issue including the emphasis on the results of research over the methodology utilized or the 'publish or perish' culture that researchers are subject to.

***It is the responsibility of the researcher to make sure their studies are as reproducible as possible.***

How can we make reproducibility an integral part of our studies?
  * the data source and code should be accessible to anyone trying to reproduce our work, ideally as part of a publication.
  * you should never modify source data. Editing the raw data destroys the chain of reproducibility. Instead all changes should be made through code, this way all steps that the study took to process the data can be reproduced.
    * All code and data should be well documented and the terms of reuse should be clear.
      * Usually researchers provide a plain text "README" file that provides an introduction to the analysis package as well as a "LICENSE" file with the terms of reuse.
      * Another way this can be accomplished that is quickly gaining popularity in the research community are tools like Jupyter Notebook, Sweave and Knitr that allow the interweaving of code and text and so produce clearly documented and reproducible studies.
      * Version control systems, like Git, also help to create more reproducible studies. Git can track the changes made to the code used in the study over time by contributor, this way the development process becomes more transparent and the logs can be used to more easily find and fix bugs in the code.

## Relational Databases

Relational databases can be thought of as a collection of tables which are linked together by shared keys. Organizing data across tables can help to utilize storage more efficiently, maintain data integrity and enable faster analysis.

The model that defines the structure and relationships of the tables is known as a "database schema".

tables will be linked through primary and foreign keys. 

Extracting data from a database is known as “querying” the database.

![ER Diagram](https://github.com/tatpongkatanyukul/Collaborative/blob/main/relationalDB.png)

## MIMIC-III Structure

## SQL Basics

[SQL teaching](https://www.sqlteaching.com/)

A few of the simplest and essential commands in SQL are as follows:
  * SELECT [what do you want returned, list columns here separated by commas. writing ```'SELECT *'``` will return all columns available in the table]
  * FROM [what is the name of the table where you want the data to come from]
  * WHERE [are there any restrictions in the data you want returned? e.g. before a certain time or that meet certain criteria]
  * GROUP BY [would you like to aggregate the data? note that if you choose to aggregate the data you will need to make sure that you apply proper statements to variables in your select statement]
  * HAVING [this is essentially the same as where after you've used a GROUP BY statement, one use case could be looking for patients that stayed for multiple visits after you aggregate the number of hospital admissions a patient has recorded in the admissions table]
  * ORDER BY [this is to arrange your data according to a certain column, say from greatest to least or alphabetically. By default the ordering is done in ascending order, so you can add the word DESC after the variable(s) listed]. 
  * join commands
    * INNER JOIN
    * LEFT JOIN
    * RIGHT JOIN
    * FULL OUTER JOIN

## Conclusion

  * Not all medical data found in a database has the same characteristics even if it represents the same concept. Pay close attention to the data you are extracting and it's original purpose. Remember that both the type of data and the place where it comes from introduces its own bias to your study. Take precautions accordingly and analyze your results with that knowledge.
  * Collaborating with professionals of different areas of science than our own can be daunting. The language of both sides may be difficult to understand and the needs and expectations of each may not always align. Take time to understand the nuances of the language of every area involved. You do not need to be an expert in all areas but you do need to know how to understand each other and how to manage expectations.
  * No matter what results you obtain in your study, they are as good as nothing if they cannot be reproduced by other groups. Please take steps so that your studies can always be reproduced. Never directly edit the raw data, all modifications should be made through coding. Provide both the raw data as well as all code needed to achieve your processed data status, this way other groups may arrive at the same state you did and may also analyze your path there and provide constructive criticism when necessary.  
    
---

# Unit 2.04

## Introduction

The general steps taken to pre-process data are:
  * Data "cleaning" - This step deals with missing data, noise, outliers, and duplicate or incorrect records while minimizing the introduction of bias into the database.
  * "Data integration" - Extracted raw data can come from heterogeneous sources or be in separate datasets. This step reorganizes the various raw datasets into a single dataset that contains all the information required for the desired statistical analyses.
  * "Data transformation" - This step translates and/or scales variables stored in a variety of formats or units in the raw data into formats or units that are more useful for the statistical methods that the researcher wants to use.
  * "Data reduction" - After the dataset has been integrated and transformed, this step removes redundant records and variables, as well as reorganizes the data in an efficient and "tidy" manner for analysis.
  
## Real World Data

Real-world data is usually "messy" in the sense that they can be incomplete (e.g. missing data), they can be noisy (e.g. random error or outlier values that deviate from the expected baseline), and they can be inconsistent (e.g. patient age and admission service in neonatal intensive care unit).

## Missing Data

Possible ways to deal with missing data:
  * Ignore the record. This method is effective at removing missing data, but it comes with two problems. Firstly it can lead to low sample sizes if a large proportion of the data has missing values. Secondly, if the missing values are correlated with a feature, then removing entries can bias the dataset.
  * Determine and fill in the missing value manually. This approach is the most accurate but it is also time-consuming and often is not feasible in a large dataset with many missing values.
  * Use an expected value. The missing values can be filled in with predicted values (e.g. using the mean of the available data or some prediction method). It must be underlined that this approach may introduce bias in the data, as the inserted values may be wrong. This method is also useful for comparing and checking the validity of results obtained by ignoring missing records.

## Frequency of Data Acquisition

How often data is collected, e.g., every 5 min, hourly.

Use visualization # samples/frequency of data acquisition to decide how frequent we want to choose.
If we choose too high frequency, we may end up with a lot of missing data.

## Noisy and Inconsistent Data

Noisy data can be due to:
  * Faults or technological limitations of instruments during data gathering
  * Human error in data entry
  
Possible ways to deal with noisy data are to exclude outliers through:
  * Binning methods - Binning methods smooth a sorted data value by considering their "neighborhood", or values around it
  * Clustering - Outliers may be detected by clustering, that is by grouping a set of values in such a way that the ones in the same group (i.e., in the same cluster) are more similar to each other than to those in other groups
  * Machine learning - One of the classical methods of machine learning is regression analysis, where data are fitted to a specified (often linear) function
  * Visualization - Outliers can be assessed directly by plotting the distribution of variables, eg. in a box plot
  
Boxplot edges: upper and lower fences

Example of SpO2 100% is shown of an outlier, because it takes samples from just one patient.
Data scientist should fix this (making it not an outlier), because if we have samples from 100 patients, SpO2 (blood oxygen) is good. It's not an outlier.

> We can observe that pulse oximetry (SpO2) values range from 60% to 100%. The value of 60% is an abnormal value and indicates that the patient is in a critical condition at that time.

Inconsistent data in EHR can be due to:
  * variation in how different staff and clinicians enter data - there may be thousands of staff in a single hospital.
  * multiple automated interfaces with the EHR, everything from telemetry monitors to the hospital laboratory.

## Data Integration and Transformation

Data integration is the process of combining data derived from various data sources (eg. such as databases) into a consistent dataset. There are a number of issues to consider during data integration related mostly to possible different standards among data sources. For example, certain variables can be referred to by means of different IDs in two or more sources.

### Data Transformation

The aim of data normalization is to transform the data values into a format, scale, or unit that is more suitable for subsequent statistical analysis.

A few common possible approaches to normalize the data:
  * Normalization - data for a numerical variable is scaled in order to range between a specified set of values, such as 0-1.
  * Aggregation - two or more values of the same attribute are aggregated into one value.
  * Generalization - similar to aggregation, in this case, low-level attributes are transformed into higher-level ones. For example, in the analysis of chronic kidney disease (CKD) patients, instead of using a continuous numerical variable like the patient's creatinine levels, one could use a variable for CKD stages as defined by accepted guidelines.
  
  
