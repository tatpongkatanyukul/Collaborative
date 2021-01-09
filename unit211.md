# Unit 2.11: Causal Inference

Causal Inference is a process to determine how the changes in the treatment affect the outcome.

## Introduction to Causal Inference

Correlation does not imply causation.

Assumptions/Exclusions
   * We are talking about the ***average effect***, not individual effect
   * We will assume no ***effect modification*** for the examples
   * We will assume there are ***no longitudinal effects*** (effect caused by time)
   
Types of Studies
  * Observational Studies
    * as it is in the natural worlds
    * presence of confounders and selection bias
    * studying the effect of smoking on cancer
  * Natural Experiments
    * Study in which subjects are exposed to the experimental and control conditions that are determined by nature or by other factors not controlled by the investigators
    * Something seems ***randomized*** even when it is not formally
    * Quarter of birth on income of individuals
  * Randomized Trials
    * Treatment is assigned randomly
    * More expensive
    * Ethical concerns
   
Potential Outcomes and Counterfactuals
  * Potential outcomes (Y0 and Y1), observed outcomes (YA) and counterfactuals (YA')
    * counterfactuals are unsobserved.
  * Fundamental Problem of Causal Inference
  * Conditioning (observed outcome) vs setting (potential outcomes)
  * Generally, E[Y1-Y0] != E[Y|A=1] - E[Y|A=0]
  * Causal effect
    * Average causal effect: E[Y1 - Y0]
    * Average relative risk: E[Y1/Y0]
    * Average causal effect of the treatment on the treated: E[Y1 - Y0|A=1]
    * Average causal effect in the subpopulation with the covariate V=v: E[Y1 - Y0|V=v]
    
Causality as a hypothetical intervention    
  * "No causality without manipulation" - Holland (1986)
  * Causal effects of a variable are well-defined if the variable is manipulable.
  * Immutable variables: their causal effects are difficult to define because manipulation is not possible. Example: age, race, and gender.
    * There is a way around it, e.g., compare an old group to a younger group.

## Identifiability

### Stable Unit Treatment Value Assumption (SUTVA)

(a) No interference: the treatment status of any unit does not affect the potential outcomes of the other units. A subject's counterfactual outcome under treatment value 'a' does not depend on other subjects' treatment values. Violations: spill-over effects, carry-over effects, contagion: individual's outcome is influenced by social interaction with other people.
  
The assumption of no interference involves no interaction between units (defined by Cox, 1958)

(b) One version of treatment: a treatment should not have multiple versions and that there is only one version of treatment value A = a.

Example: Zeus will die if he receives a heart transplant. This statement implicitly assumes that all heart transplants are performed by the same surgeon using the same procedure and equipment. That is, there is only one version of heart transplant treatment. If there were multiple version of treatment (surgeons with different skills) then it is possible that Zeus would have survived.
  
(c) Consistency Assumption (no variation in treatment)

The observed outcome for a given treatment will be potential outcome.
Violation: some patients get extra strenght aspirin

(d) Ignorability / Exchangeability Assumption
  * Outcome should be independent of treatment for the given covariates
  * The risk of death in a white group would have to be the same as the risk of death in grey group if individuals in the white group receive same treatment given to those in the grey group
  * coutnerfactual outcome and the actual treatment are independent
  
(e) Positivity Assumption
  * experimental treatment assumption
  * treatment assignment is not deterministic: P(A = a|X = x) > 0 for all x's (covariates)
  * If people with some covariates are ineligible for a particular treatment, then we should exclude those groups of people from the study.
  
### Stratification and Example
  * stratification helps: subgroups --> strata
    * confounding factor may not vary at all between the exposed and unexposed subgroups
  * Example, mortality vs gender --> add in age --> clarify the causal effect (age is a confounding factor/confounder)
  
  
