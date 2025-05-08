# Ss_Dynamics
Repository for code used in data analysis for Fig.4D. Huge thanks to Scott Rifkins for helping us out on this!

---

## test.skewness.diff

#This compares two distributions and asks whether one has more positive skew than the other
#The test statistic is the difference in skewness
#The null hypothesis is that the distributions are the same, and the difference in skewness is 0
#The null distribution is constructed by randomizing which datapoint belongs to which distribution.  Then taking the test statistic for this randomized dataset.  Then do this 10000 (resolution) times to get a null distribution 


---

If spineless transcription is a Poisson process in the cell (memoryless), then the waiting times until a state change are exponentially distributed. We only observe the state at defined discrete intervals (1-minute) so the appropriate distribution for modeling is geometric.

Consider changing state a "success". Then the number of minutes in the same state is the number of "failures" until a success. This is a standard setup for a geometric distribution.

With a single probability (p), prob(T=k)=((1-p)^(k-1))*p = k-1 minutes with no change (at probability 1-p per minute) with the last minute being a change and the first minute setting the state

For example, if a cell is OFF at k=1 and ON at k=2, then prob(T=k)=p. It changed on its 1st opportunity

Estimate the probability of a change from the data p_change = 1/mean_duration_in_a_state

Then the rate (# of changes/min) = -ln(1-p_change)

Approach: 
#1) Assume that the process is Poisson and so the data should be geometrically distributed.

#2) We want to know plausible values for the probability of change /if/ the assumption is true. 

#3) There are an infinite number of these, relatively more or less consistent with the data 

#4) Estimate the posterior distribution of these probabilities 

#5) For a geometric distribution, the coefficient of variation, skew, can be derived directly from p Use a Bayesian approach to estimate the rate and then output the posterior distributions for the skew and CV for the geometric models estimated from the data. Then see whether the actual data is consistent with that.

Since the model is a simple one-parameter geometric model, we can scan through probabilities from 0 to 1 [grid approximation], and get the densities from x=0:29 (note that the r geom functions (dgeom, rgeom, etc) are p(1-p)^x. To match the data collection, we'd want to use duration=x+1.

## plotDataAndGeometricModel
Plot the data with HDI intervals as error bars and the median of the posterior marked with a dot

1) Generate posteriors for the counts at each duration for the 4 groups [up to 30 minutes]
2) Estimate HDI for each of them
3) Estimate Median for each of them
4) Make the base plot and add these in keeping in mind the log transformation

## PostPredCheck
For a geometric distribution, the coefficient of variation, skew, can be derived directly from p Use a Bayesian approach to estimate the rate and then output the posterior distributions for the skew and CV for the geometric models estimated from the data. Then see whether the actual data is consistent with that,using a chi-square test.

## postPredDiscrepancyCheck_bayesian-p-value.Rdata
This is the set of simulated data generated and used for calculating the Bayesian p-values with the datasets.


