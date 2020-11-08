# Collaborative

Learning Collaborative Data Science for Healthcare on EdX (MITx - HST.953x, started Nov 3rd, 2020)

## Free course e-books
* kku.world/2b887

# My Learning Log

## Nov 3

> "Data science is an inter-disciplinary field that uses scientific techniques from statistics and computer science to systematically extract knowledge from data."

Suggested readings:
  * Donoho D. 50 years of data science. Journal of COmputational and Graphical Statistics. 2017 Oct 2; 26(4): 745-66.
  * Blei DM, Smyth P. Science and data science. Proceedings of the National Academy of Sciences. 2017 Aug 15; 114(33):8689-92.
  
"commucable to people"
  * develop a shared language
    * Same word, different meanings, e.g., planetary features vs ML features.
    * Connotations, e.g., Novelty vs Outlier vs Anomaly.
    * key points: 
      * Same words can have different meanings, depending on the context.
      * Define terms/jargon when working in multidiscilinary teams to avoid confusion and errors.
    * The machine needs a language too
      * Representation (relates to questions we want to ask)
      * Explanations/justifications (so that human can understand)
    * key points: 
      * There is not one single correct way to represent your data - it depends on the nature of the data and the aims of your project.
      * The way the data are represented may limit what conclusions you can draw from your data.
      * Knowing why a model behaves the way it does is also important beyond just performance metrics.
    * Understand your data: key points: 
      * Know what the valid ranges for your data are.
      * Inspect your data to see if there are values that don't make sense.
      * If there are unusual values, check with those who collected the data or handled the instruments that collected the data.
    * Deal with missing data: key points: 
      * Inspect your data to determine if there is missing data. Sometimes, missing data is coded as "99999"
      * Why is the data missing? This requires you to know how the data was collected?
      * Sometimes, missing data arises because a value is unmeasurable (e.g., eccentricity cannot be calculated for a point such as a star)
      * Don't just blindly fill ("impute") the missing values without first understanding why the value is missing
    * Valid range of features: BREAK HERE      
   
# Nov 4, 2020

"Meaningful evaluation"
  * V-FASTR classifier
    * Instead of ROC, which is risky, since ML is based on an assumption that the training and deploying data have the same distribution
    * They test the system in the way it will be deployed, i.e., taking previous data and let it predicts known pulsar, candidate, none as the project goes.
    * successively held out evaluation, replicating what they will be used in real life.
    * Also, show how much human effort the ML system can save.

Key ingredients for successful collaboration in data science:
  * Expertise
  * Shared language
  * Knowing your data's characteristics
  * Meaningful evaluation

1.02 A Data Science Revolution in Healthcare

Successful data analytics
  * Sufficient clean, unbiased feature data
  * Advanced analytics/AI techniques
  * Right outputs in the right place / sound application and deployment in the real-world setting
    * how to deploy it in the effective way
    
Four key technologies
  * Large-scale data warehousing and analytics
    * get data into the same place
  * Sensor networks and personal computing
  * Machine intelligence
    * challenge: better use of the limited data
  * Public cloud computing
    * provide uniformity access/treat to data collecting from or storing in different locations.
 
# Nov 8th, 2020
1.02 Utilizing Healthcare Data
  * In healthcare data science, there are clinical and operational use cases of data analytics
  * Analytics can serve on a local or distributed basis, both of which have their advantages and disadvantages
  
Machine Intelligence
  * Machine intelligence (a term used in data science) describes a computer's ability to predict an outcome using a given set of variables
    * For example, predicting mortality in a given patient using clinical observations, vital signs, and laboratory results as variables
  * Machine learning - computer's ability to learn without being explicitly programmed - can be thougth of as a method of accomplishing "machine intelligence"
  * Deep learning is a tool used in machine learning
  * When developing machine learning models, it is important to consider the availibility of data at the time of making the prediction

Predictive models
  * Rule-based systems: input -> hand-designed features -> output
  * classical machine learning: input -> hand-designed features -> mapping from features (learned) -> output
  * representation learning: input -> features (learned) -> mapping from features (learned) -> output
  * deep learning: input -> simple features (learned) -> additional layers of more abstract features (learned) -> mapping from features (learned) -> output
  
Challeges for AI approaches
  * 2018 FDA approved AI-based method on diabetic retinopathy
  * Appropriate regulatory bodies, statutory quality control and legislation for medical AI algorithms are yet to be developed
  * In healthcare, high-quality datasets are scarce as there is much variation in the way observations are recorded

Key points
  * It is endeavored to build an environment for structured, seamless inpatient and outpatient data collection, producing high-quality, complete medical records for patients and research purposes.
  * Accumulation and integration of all types of data (genomic data, physical data, etc.) will allow for more powerful models of disease progression and therapy
  
Automatic diagnosis of diabetic retinopathy
  * Gulshan and Peng et al. JAMA 2016: Inception model: --> No DR, Mild DR, Moderate DR, Severe DR, Proliferative DR; Image quality, L/R eye, Field of view

Next: 




# Final Exam (Due Jan 25, 2020)
