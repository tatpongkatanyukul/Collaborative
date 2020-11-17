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
    
    
