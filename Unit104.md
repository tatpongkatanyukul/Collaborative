# Unit 1.04: Challenges in Health Data Science

Key points I:
  * Statistical hypothesis testing includes making a null hypothesis (i.e. there is no difference between two groups) and alternative hypothesis (there is a difference between the groups), either of which shall be rejected through analysis.
  * **P-values assumes the null hypothesis to be correct and serve to determine the likelihood of obtaining a test result by chance**
    * Usually, the significance is chosen at 0.05 or 5% (i.e. in case of significant results, there is a 5% chance the results are significant by chance)
    
Video: Multiple testing and and spurious findings (example: dead salmon study)
  * (This is a poster presentation.) Neural Correlates of Interspecies. Perspective taking in the post-mortem Atlantic Salmon.
    * fMRI study: postmortem salmon --> **detected brain activity in dead salmon.**
    * ! Does this mean that dead fish still has brain activity?
    * Not quite.
    * What was traditionally done in fMRI studies is that they take individual voxels each of those points in that MRI.
    * Then, they run a test to see if there is a difference between the activity at that voxel without the stimulus and at baseline.
    * They do that at every single voxel. In this case, they had about 8000 voxels that they were testing.
    * If we use 5% p value cutoff. (It is a percent to get false positive.)
    * We are going to get 400 significant hits, just by chance.
    * What the authors was really trying to do is to point out the problem in their field.
    * "... random noise in the EPI timeseries may yield spurious results if multiple comparisons are not controlled for ..."
    * The full title of the article is that **an argument for multiple comparisons**
      * [Craig M. Bennett, Michael Miller, and George L Wolford. Neural correlates of interspecies perspective taking in the post-mortem Atlantic Salmon: an argument for multiple comparisons correction, July 2009. Neuro Image 47. DOI: 10.1016/S1053-8119(09)71202-9.](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Bennett-Salmon-2009.pdf)
      
    * **Then what can we do?**
      * we can try to control **a family wise error rate**
        * p-value ~ probability of having a false positive for an individual test.
        * But if we are looking at 8000 tests, instead of controlling the probability of false positive for an individual test, we should control for that across the entire set of tests.
        * I.e. we want to only have maybe one false positive across that entire set of 8000 tests that are really low probability.
        * One way to do it is that taking that 5% threshold (or p-value of your choice) divided by the number of tests you have and then use that as your cutoff for significance.
      * Another way is to use **false discovery rate** (proposed by [Benjamin and Hochberg](https://github.com/tatpongkatanyukul/Collaborative/blob/main/Benjamini%20and%20Y%20FDR.pdf))
        * we are interested in the proportion of our discoveries that are false.
        * I.e. we are willing to live with say 5% of our discoveries being false
        * E[ # false positives/ # total positives ] < alpha
        * FDR (false discovery rate) is good especially for imbalanced data (# positives is much smaller than # negatives)
    
Reproducibility Crisis
  * The lack of reproducibility of research findings has been repeatedly identified as an issue in modern science
  * Approaches to improving on the reproducibility include revising methodologies and giving detailed insight into how studies were conducted.
  * Psychology may need about 10000 subjects to be a reliable data, but experiments typically were conducted on about 50 subjects.
