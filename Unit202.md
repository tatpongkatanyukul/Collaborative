# Unit 2.02: Defining the Patient Cohort

## Introduction

A critical first step in any observational study is the selection of an appropriate patient cohort for analysis.

## Exposure and Outcome of Interest

Data mining in biomedical research utilizes a retrospective approach wherein the exposure and outcome of interest occur prior to patient selection.
... Selecting an overly broad exposure may allow for a large patient cohort, but at the expense of result accuracy. Similarly,, being too specific in the choice of exposure may allow for accuracy but at the expense of sample size and generalizability.

  * Patient-centric exposures focus on traits intrinsic to a group of patients. These can include demographic traits (e.g., gender) or medical comorbidities (e.g., diabetes).
  * Episode-centric exposures are transient conditions requiring a discrete treatment course (e.g., sepsis).
  * Encounter-centric exposures refer to a single intervention (e.g., arterial line placement). Although encounter-specific exposures tend to be simpler to isolate, the choice of exposure should be determined by the specific hypothesis under investigation.
  
### Outcome of Interest  

The outcome of interrest should be identified a priori.
... Care must be taken to avoid identifying spurious correlations ... (http://tylervigen.com)
... Broad outcome measures, such as mortality and length-of-stay, may be superficially attractive but ultimately confounded by too many variables. Surrogate outcome measures (e.g., change in blood pressure, duration of mechanical ventilation) can be particularly helpful as they relate more closely to the exposure of interest and are less obscured by confounding.
... Leveraging unstructured data such as narrative notes and radiology reports can be more difficult and often requires the use of natural language processing (NLP) tools.

## Comparison Group

Ideally, the comparison group should be comprised of patients phenotypically similar to those in the study cohort, but who lack the exposure of interest.
The selected comparison cohort should be at equal risk of developing the study outcome. In observational research, this can be accomplished via propensity score development.

In general, the comparison group ought to be as large as or larger than the study cohort to maximize the power of the study. ... Care must be taken to prevent over-matching.

In select cases, investigators can take advantage of natural experiments in which circumstances external to the EHR readily establish a study cohort and a comparison group.
These so-called 'instrumental variables' can include practice variations between care units, hospitals, and even geographic regions.

Researchers must pay attention to the necessity to exclude some patients on the grounds of their background medical history or pathological status, such as pregnancy for example. Failing to do so could introduce confounders and corrupt the causal relationship of interest.


## Cohort Definition Rationale

Examples of cohorts - SSRI study: Ghassemi et al., Leveraging a Critical Care Database: Selective Serotonin Reuptake Inhibitor Use Prior to ICU Admission Is Associated With Increased Hospital Mortality, Chest 2014 Apr;145(4).
  * presented cohorts by ***CONSORT diagram*** 

## Building the Study Cohort

Isolating specific patient phenotypes for inclusion in the study and comparison cohorts requires a combination of clinical reasoning and data-driven techniques. A close working relationship between clinicians and data scientists is an essential component of cohort selection using EHR data.

According to a 2011 Institute of Medicine Committee Report, only 10–20 % of clinical decisions are evidence-based. **Nearly 50 % of clinical practice guidelines rely on expert opinion rather than experimental data.** In this ‘data desert’ it is the role of the clinician to identify novel research questions important for direct clinical care.

... Phenotype querying of structured and unstructured data can be complex and requires frequent tuning of the search criteria.

... the research team must consider patient 'uniqueness' in that some patients have multiple ICU admissions both during a single hospitalization and over repeat hospital visits. If the same patient is included more than once in a study cohort, the assumption of independent measures is lost.
  * how to deal with this then?

### Example 1

In one example from a published MIMIC-II study, the investigators attempted to determine whether proton pump inhibitor (PPI) use was associated with hypomagnesaemia in critically-ill patients in the ICU. The exposure of interest in this study was ‘PPI use.’ A comparison group of patients who were exposed to an alternative acid-reducing agent (histamine-2 receptor antagonists) and a comparison group not receiving any acid-reducing medications were identified. The outcome of interest was a low magnesium level. In order to isolate the study cohort in this case, queries had to be developed to identify:

  * First ICU admission for each patient
  * PPI use as identified through NLP analysis of the ‘Medication’ section of the admission History and Physical
  * Conditions likely to influence PPI use and/or magnesium levels (e.g. diarrheal illness, end-stage renal disease)
  * Patients who were transferred from other hospitals as medications received at other hospitals could not be accounted for (patients excluded)
  * Patients who did not have a magnesium level within 36-h of ICU admission (patients excluded)
  * Patients missing comorbidity data (patients excluded)
    * what is comorbidity data? example?
    * what symptoms (or conditions) can be comorbid of hypomagnesaemia?
  * Potential confounders including [diuretic use](https://en.wikipedia.org/wiki/Diuretic)

See [the Informatics for Integrating Biology and the Bedside (i2b2)](https://www.i2b2.org) for efficient querying.

Example: [MIMIC demo](https://physionet.org/content/mimiciii-demo/1.4/)

### Example 2

[MIMIC Code](https://github.com/MIT-LCP/mimic-code)

[MIMIC Tutorial](https://github.com/MIT-LCP/mimic-code/tree/master/tutorials)
  * cohort-selection.ipynb

## Hidden Exposures

From what I understand, it says:
sometimes the exposures in that we are intested are not in the database fields that we can easily query.
We may have to perform NLP operation

Excerpt:
> ``Performing an NLP search for the term ‘atrial fibrillation with rapid ventricular response’ in provider notes and discharge summaries is feasible, but would not provide the temporal resolution needed with respect to drug administration.''

## Case Study: Arterial Line Study Cohort Definition

## Data Visualization

## Study Cohort Fidelity

> ``In order to guarantee the fidelity of the study cohort, manually reviewing a random subset of selected patients can be helpful. Based on the size of the study cohort, ***5–10 % of clinical charts should be reviewed to ensure the presence or absence of the exposure of interest***.This task should be accomplished by a clinician. If resources permit, two clinician reviewers can be tasked with this role and ***their independent results compared using a Kappa statistic***.''

> Ultimately, the investigators can use the ‘gold standard’ of manual review to establish a Receiver Operating Characteristic (ROC). ***An area-under the ROC curve of >0.80 indicates ‘good’ accuracy of the algorithm*** and should be used as an absolute minimum of algorithm fidelity. If the area under the ROC curve is <0.80, a combination of data visualization techniques and clinical reasoning should be used to better tune the query algorithm to the exposure of interest.

## Case Study: Cohort Selection

> In the case study presented, the authors analyzed the effect of indwelling arterial catheters (IACs) in hemodynamically stable patients with respiratory failure using multivariate data. They identified the encounter-centric ‘arterial catheter placement’ as their exposure of interest. IACs are used extensively in the intensive care unit for beat-to-beat measuring of blood pressure and are thought to be more accurate and reliable than standard, non-invasive blood pressure monitoring. They also have the added benefit of allowing for simpler arterial blood gas collection which can reduce the need for repeated venous punctures. Given their invasive nature, however, IACs carry risks of bloodstream infection and vascular injury. The primary outcome of interest selected was 28-day mortality with secondary outcomes that included ICU and hospital length-of-stay, duration of mechanical ventilation, and the mean number of blood gas measurements made. 

> The authors elected to focus their study on patients requiring mechanical ventilation that did not require vasopressors and were not admitted for sepsis. In patients requiring mechanical ventilation, the dual role of IACs to allow for beat-to-beat blood pressure monitoring and to simplify arterial blood gas collection is thought to be particularly important. Patients with vasopressor requirements and/or sepsis were excluded as invasive arterial catheters are needed in this population to assist with the rapid titration of vasoactive agents. In addition, it would be difficult to identify enough patients requiring vasopressors or admitted for sepsis, who did not receive an IAC.

:

> there were 984 patients in the group who received an IAC and 792 patients who did not. ***These groups were compared using propensity matching techniques.*** 

## Conclusion
  * Take time to characterize the exposure and outcomes of interest pre-hoc.
  * Utilize both structured and unstructured data to isolate your exposure and outcome of interest. NLP can be particularly helpful in analyzing unstructured data.
  * Data visualization can be very helpful in facilitating communication amongst team members
