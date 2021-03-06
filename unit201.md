# 2.01 Formulating the Research Question

Learning objectives
  * Unverstand how to turn  a clinical question into a research question
  * Principles of choosing a sample
  * Approaches and potential pitfalls
  * Principles of defining the exposure of interest
  * Principles of defining the outcomes
  * Selecting an appropriate study design
  
FINER mnimonic
  * feasible
  * interesting
  * novel
  * ethical
  * relevant
 
PICO
  * P: The population of subjects defined by the researcher (Patients/study sample)
  * I: The drug, event or characteristic that we are basing our alternative hypothesis on (Intervention/exposure)
  * C: The “unexposed” or control group needed to assess the effectiveness of healthcare interventions (Control)
  * O: The predefined outcome of interest (Outcome)
 
Intervention
  * Example Arterial catheter placement
    * Does timing of placement matter?
     	* It is not just what is your intervention, but when you apply your intervention.
	
Control
  * Example: in the case of the IAC study, the control group is fairly straightforward: patients receiving  mechanical ventilation (MV) who did not have an IAC placed.
  * an alternative control group could be all ICU patients no receiving an IAC.
  * However, the inclusion of patients not receiving MV results in a control group with lower severity of illness and expected mortality than patients receiving MV, which would bias in favor of not using IACs.
  * "counterfactual": --> find the counterfactual group
  
Outcome: several different types of outcomes can be considered.
  * Intermediate or mechanistic (Informs etiological pathways, but may not immediately impact patients)
    * Number of artirial blood draws
    * Ventilator setting changes
    * Vasoactive medication change
  * Patient-centered (Informs outcomes important to patients, but may lack mechanistic insights)
    * Comfort scales
    * Quality of life indices
    * Mortality (e.g. 28-day or 90-day mortality)
    * Adverse event rates
  * Healthcare-system centered (e.g., resource utilization, or costs)
    * Hospitalizaion costs
    * Added clinician workload
    
What is a good outcome to measure
  * Go back to FINER questions
    * Hospital mortality?
    * Opinions of patient? ...
    
Clinical question: "Should I put an arterial catheter in my patient" --> Research Question in PICO: Summary
  * Patients?
    * Mechanically ventilated, no shock
  * Intervention?
    * Arterial catheter within 2 days of ventilator
  * Comparator?
    * No arterial catheter, but blood gas checked
  * Outcome(s)
    * Primary: mortality
    * Secondary: lenght of stay (LOS), # blood gases
> "Among mechanically ventilated adult ICU patients who are not receiving vasoactive medications (**P**), is placement of an AC (**I**) after initiation of MV (as compared with not receiving an AC [**C**]) associated with improved 28-day mortality rates (**O**), length of stay, and the number of blood gas measurements per day (supporting/balancing secondary outcomes, intermediate/mechanistic O)?" 

Formulating a Research Question
  * Like scientific methods, **be systematic in forming your question!**
  * Think about **value and feasibility of question** using **FINER** mnemonic
    * Are people interested? Am I interested? Is it useful to the world?
  * **Construct question using PICO** framework
  * Develop **rejectable hypotheses**

## Study Design
Once the research question has been defined, the next step is to choose the optimal study design given the question and resources available. Broadly, the study design can be classified into Randomized Controlled Trials (RCTs) and observational studies. RCTs exhibit a stronger experimental design, that more easily establishes causality, but they have several practical limitations.

### Observational Studies

#### Types of observational research
Major types of observational research and their purpose
  * Epidemiological: Define incidence, prevalence, and risk factors for disease
  * Predictive modeling: Predict future outcomes
  * Comparative effectiveness: Identify intervention associated with superior outcomes
  * Pharmacovigilance: Detect rare adverse events occuring in the long-term

Observational study: a generic term for a study where investigators do not assign treatments.
  * Cross Sectional: snapshot in time
  * Case-Control: outcome is known (cases) and retrospective evaluation to identify association with past exposures
  * Cohort: exposures are monitored in subjects for the development of outcomes; propecctive vs retrospective
  * Ecological: exposures and outcomes evaluated on a population level, rather than a patient level; ["Ecological fallacy"](https://en.wikipedia.org/wiki/Ecological_fallacy)--- association true on population level but not on an individual level

#### Problems with observational studies

Observational studies may be more prone to bias (problems with internal validity) than RCTs due to difficulty obtaining the counterfactual control group whereas RCTs create two alternate 'universe' of patients that will be similar except with regard to the exposure of interest.

1. Bias
  * Selection Bias: This occurs during the process of selecting exposed and unexposed participants. Example: Survival bias.
  * Information Bias: Due to mismeasurement or misclassification of certain variables.
    * How accurate is the recorded?
      * Lab value (gluclose, white blood cell count, hemoglobin, etc.)
      * Vital sign (blood pressure, respiratory rate, temperature, heart rate, pain score, etc.)
  * Confounding Bias: This occurs when a third variable is correlated with both the exposure and outcome.
  
2. Missing Data
  * How do you interpret the gaps when HR is documented every 2 hours?
  * How do you interpret the gaps when a continuous infusion is documented every 2 hours?
  * If there's no [blood gas](https://labtestsonline.org/tests/blood-gases) for a patient so I can't get the pH, what does that mean?

### Randomized Controlled Trials (RCTs)

#### Randomizedd controlled trials

RCTs are the gold standard for establishing causal inference under ideal conditions, because they allow for the unobserved confounding to be controlled for through randomization. This means it is relatively simple to establish causality through the use of an RCT. However, they are not always practical, cost-effective, ethical or even possible for some types of questions.

#### Problems in RCTs

  * Logistically complex
  * Risk of harm to participants - if one treatment is less effective than the other, then patients that are assigned to the arm may be harmed.
  * Ethical concerns - some questions involve too much danger to participants, or potential participants may be unable to give full consent, so the study cannot be run.
  * Expensive and may take a long time.
  * Often have a homogeneous population due to stringent inclusion criteria.

### Data Sources
  * Administrative/claims data: tend to provide very large sample sizes but lack granular patient-level data like vital signs, laboratory and microbiology data, timing data or pharmacology data.
  * Secondary use of clinical trial data and large epidemiologic  studies: these types of databases often have detailed, granular information but researchers are often bound by the scope of data collection from the original research study which limits the questions that may be posed.
  * Electronic health record (EHR) systems: contain data from a variety of sources such as patient monitors, laboratory systems, and pharmacy systems which can then be translated into de-identified databases for research purposes that contain detailed patient demographics, billing and procedure information, timing data, hospital outcomes data, as well as patient-level granular data and provider notes which can be searched for using natural language processing tools.

### Conclusion

Fewer than 10% of clinical decisions are supported by high level evidence. Clinical questions arise approximately in every other patient and provide a large cache of research questions. When formulating a research question, investigators must carefully select the appropriate sample of subjects, exposure variable, outcome variable, and confounding variables.

Once the research question is clear, study design becomes the next pivotal step. While RCTs are the gold standard for establishing causal inferene under ideal conditions, they are not always practical, cost-effective, ethical or even possible for some types of questions. Observational research presents an alternative to performing RCTs, but is often limited in casual inference by unmeasured confounding.

Our clinical scenario gave rise to the question of whether IACs improved the outcomes of patients receiving MV. This translated into the research question:
> "Among mechanically ventilated adult ICU patients are not receiving vasoactive medications (study sample), is use of an IAC after initiation of MV (exposure) associated with improved 28-day mortality rates (outcome)?"

While an RCT could answer this question, it would be logistically complex, costly, and difficult. Using comparative effectiveness techniques, one can pose the question using a granular retrospective database comparing patients who received an IAC to measurably similar patients who did not have an IAC placed.

### Key take aways
  * Most research questions arise from clinical scenarios in which the proper course of treatment is unclear or unknown.
  * Defining a research question requires careful consideration of the optimal study, exposure, and outcome in order to answer a clinical question of interest.
  * While observational research studies can overcome many of the limitations of randomized controlled trials, careful consideration of study design and database selection is needed to address bias and confounding.

