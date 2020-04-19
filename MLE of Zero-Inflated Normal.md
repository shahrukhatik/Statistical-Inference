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
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/theta.png?raw=true" width="350" title="hover text">
  
Given that the mixture distribution in this paper was conducted where the non-zero proportion of the mixture followed a normal distribution with mean u and variance sigma squared,our probability density function is given by:


<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/normalpdfzip.png?raw=true" width="350" title="hover text">

For example, as per the paper being produced - sa histogram of 1000 randomly generated samples presented in Figure 1 gives a visual idea of a zero-inflated normal mixture model. The histogram contains 70% zero values and 30% non-zero values, where non-zero values follow a normal distribution with mean 6 and standard deviation 1.

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/ZIP_Normal_Histogram.png?raw=true" width="350" title="hover text">
  
The Maximum Pseudo-likelihood function and pseudo-likelihood estimates for the zero-inflated normal model are derived as follows:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip1.png?raw=true" width="350" title="hover text">

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip2.png?raw=true" width="350" title="hover text">
