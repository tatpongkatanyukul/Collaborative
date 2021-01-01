# Unit 2.05

Statistical models depend on having complete data to use for both exposure and outcome variables, and so we must figure out how to deal with missing data: do we remove incomplete entries and (dramatically) shrink our dataset? Do we replace missing values with estimates (imputation)? And how do we evaluate these strategies?

Types of Missingness
  * The value is missing because it is forgotten, lost, or was never entered. For example, we measured some value but it was never entered into the EMR. 
  * The value is missing because it is not applicable to the instance. For example, we don't have ventilator information for a patient that was taken off the ventilator, and so these records are left empty in the database.
  * The value is missing because it is of no interest to the instance. For example, we didn't measure something about a patient because it is not relevant to their current condition. 
  
  
