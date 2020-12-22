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

## Cohort Definition Rationale

## Building the Study Cohort

## Hidden Exposures

## Case Study: Arterial Line Study Cohort Definition

## Data Visualization

## Study Cohort Fidelity

## Case Study: Cohort Selection

## Conclusion
