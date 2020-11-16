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
    * https://jamanetwork.com/journals/jama/fullarticle/2588763
    * The architecture of neural networks is transferable between problems
    * Neural networks have the ability to adapt themselves to solve new problems without needing additional rules

Medicine rebuilt as data science
  * Many aspects of modern medicine are often built on circumstantial, outdated, or anecdotal evidence
    * Old study leads to medical conclusion, e.g., pregnancy after 35 is risky, from pre-revolution France.
  * Modern data-driven techniques hanve the potential to improve the evidence basis in medicine.
  * Balancing exploration vs exploitation
  
Quiz
  * A model used in dispensing drug prescriptions on a national level would be an example of [Distributed Operational Model].
  * Which one of the following would NOT be considered a component for successful data analytics?
    * Deployment of a model trained on a highly homogenous sample population (correct!)
    * Other choices:
      * Sufficient amount of clean, unbiased data
      * Advanced articitial intelligence techniques
      * Sound application and deployment in real-world setting
  * Which element is MOST important when developing a predictive model?
    * Availability of data at time of prediction
