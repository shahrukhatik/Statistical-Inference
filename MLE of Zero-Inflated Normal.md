## Introduction

Weather variables such has precipitation could possibly impact human environment in a significant manner. Understanding the frequency of the occurrence and intensity of rainfall events is essential for much of the planning of important resource management systems such as dam's, hyrdo-power plants and food protection. Moreov er, understanding the nature of these variables could critically help to model agriculture. However modeling variables such as precipitation poses a lot of challenges. Precipitation data often consists of sequences of values which are either zero or some positive numbers
depending on the depth of accumulation over discrete intervals. Rainfall is localized unlike temperature which is highly correlated across regions; therefore a derivative holder based on rainfall may suffer geographical basis risk in case of pricing weather derivatives. The final challenge is the choice of a proper probability distribution function to describe precipitation data. Much similar to precipitation, it is also common to have other underlying populations that contains many zeros. It has a large spike of zero-values with a proportion of non-zero values and is thus a zero-in ated population (ZIP). An example of ZIP is modeling defect counts in a well-established manufacturing process.

## Methodology

For our zero-inflated population, two components exist; one consisting solely of a proportion of zero values and a second component of nonzero values that adheres to some probability distribution. The two-component mixture model for zero-inflated population is defined by:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/indicator.png?raw=true" width="350" title="hover text">

where alpha is the proportion of non-zeros, mu is the mean and sigma is the nuisance parameter of
the non-zero components. I represents an indicator function of values 1 and 0 respectively. The parameter of interest is the mean of our mixture distribution i.e

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/theta.png?raw=true" width="250" title="hover text">
  
Given that the mixture distribution in this paper was conducted where the non-zero proportion of the mixture followed a normal distribution with mean u and variance sigma squared,our probability density function is given by:


<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/normalpdfzip.png?raw=true" width="350" title="hover text">

For example, as per the paper being produced - sa histogram of 1000 randomly generated samples presented in Figure 1 gives a visual idea of a zero-inflated normal mixture model. The histogram contains 70% zero values and 30% non-zero values, where non-zero values follow a normal distribution with mean 6 and standard deviation 1.

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/ZIP_Normal_Histogram.png?raw=true" width="350" title="hover text">
  
The Maximum Pseudo-likelihood function and pseudo-likelihood estimates for the zero-inflated normal model are derived as follows:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip1.png?raw=true" width="500" title="hover text">

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip2.png?raw=true" width="500" title="hover text">
  
## Simulation and Results
 
10,000 bootstrap replicates of theta were computed under both parametric and non-parametric procedures. Bootstrap replicates were all computer under different values of alpha. For example, alpha = 0.05 would mean that the population contains 5% observations that have non-zero values and 95% values are zero's. For the simulation a nite population of size N = 10000 was randomly generated and separated into four strata each of which have a size of 2500. A random sample of 135 was
drawn with inclusion and weight probabilities of strata being the following, Strata 1: P1=25/2500,W1=2500/25,Strata 2: P2 = 30/2500 ,w2 = 2500/30,Strata 3: P3 = 35/2500 ,w3 = 2500/35, Strata 4: P4= 45/2500 ,w4 = 2500/45. The sizes of each samples being drawn are n1 =25,n2 =30,n3 =35,n4=45 respectively. Results are presented from three different normal populations where the means and standard deviations differ signifcantly for the non-zero component. Results in Table 1 and Figure 2 assumed the non-zero component follows N(mu = 100, sd = 10), results in Table 2 and Figure 3 assume that the non-zero component follows N(mu = 50, sd = 2), and results in Table 3 and Figure 4 assumed the non-zero component follows N(mu = 20, sd = 1).

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G2.png?raw=true" width="500" title="hover text">

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G3.png?raw=true" width="500" title="hover text">
  
<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/T4Table.png?raw=true" width="500" title="hover text">
  
<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G4.png?raw=true" width="500" title="hover text">
  
## Conclusion

The pseudo-likelihood ratio statistic developed in H. Chen et al. (2010) has assumptions, and computing confidence intervals of the mean of a zero-inflated population are mathematically and computationally complex. The complexity arises as the method uses the complex probability sampling designs in the two-component model. The use of bootstrapping bypasses many of the assumptions of the asymptotic distribution and construction of confidence intervals is computationally simpler. Use of the pseudo-likelihood function assumes a known probability distribution for the non-zero component, so the parametric bootstrap method is an appropriate approach. However, the non-parametric bootstrap method is employed to make a comparison. Confidence intervals based on the quantiles of the bootstrap distribution of estimated theta under both the parametric and non-parametric bootstrap method have been shown to consistently capture the true value of theta, the mean of the zero-inflated population. Under the assumption of a normally distributed non-zero component, the parametric bootstrap method gives narrower confidence intervals than the nonparametric bootstrap method.
