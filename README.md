# Ss_Dynamics
# Repository for code used in data analysis for Fig.4D. Huge thanks to Scott Rifkins in helping us out on this!


test.CV
# This tests whether the data is overdispersed (or underdispersed or either) relative to an exponential distribution
# The test compares the coefficient of variation (CV=stdev/mean) of your data to that of simulated exponential distributions with the same exponential (rate) parameter

test.skewness.diff
# This compares two distributions and asks whether one has more positive skew than the other
# The test statistic is the difference in skewness
# The null hypothesis is that the distributions the same and so the difference in skewness is 0
# So the null distribution is constructed by randomizing which datapoint belongs to which distribution.  Then taking the test statistic for this randomized dataset.  Then do this 10000 (resolution) times to get a null distribution 