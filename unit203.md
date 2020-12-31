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
   
---

# Unit 2.04
