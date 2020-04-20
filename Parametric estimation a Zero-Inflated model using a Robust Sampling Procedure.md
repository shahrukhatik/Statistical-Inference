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
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/theta.png?raw=true" width="200" title="hover text">
  
Given that the mixture distribution in this paper was conducted where the non-zero proportion of the mixture followed a normal distribution with mean u and variance sigma squared,our probability density function is given by:


<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/normalpdfzip.png?raw=true" width="350" title="hover text">

For example, as per the paper being produced - sa histogram of 1000 randomly generated samples presented in Figure 1 gives a visual idea of a zero-inflated normal mixture model. The histogram contains 70% zero values and 30% non-zero values, where non-zero values follow a normal distribution with mean 6 and standard deviation 1.

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/ZIP_Normal_Histogram.png?raw=true" width="350" title="hover text">
  
The Maximum Pseudo-likelihood function and pseudo-likelihood estimates for the zero-inflated normal model are derived as follows:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip1.png?raw=true" width="400" title="hover text">

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/mlezip2.png?raw=true" width="500" title="hover text">
  
The psuedo-likelihood estimate of the mean of the zero-inflated normal model is then:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/theta.png?raw=true" width="200" title="hover text">
  
The complex sampling design used a combination of stratified sampling with bootstrapping. Stratified sampling is a type of sampling method. With stratified sampling, we divide the population into separate groups, called strata. Afterwards a simple random sample is drawn from each group. Bootstrapping is the practice of estimating properties of an estimator by measuring those properties when sampling from an approximating distribution. Bootstrap methods can be either parametric or nonparametric. Parametric bootstrap methods involve sampling from a known probability distribution; in nonparametric boot-
strap, the distribution is not specified. This paper uses the idea of parametric methods where the non-zero component in mixture model has a specified probability distribution. As an application in normal models, we assume that the non-zero component follows a normal distribution with mean mu and standard deviation sigma, and use maximum pseudo-likelihood
estimates accordingly.
  
## Simulation and Results
 
10,000 bootstrap replicates of theta were computed under both parametric and non-parametric procedures. Bootstrap replicates were all computer under different values of alpha. For example, alpha = 0.05 would mean that the population contains 5% observations that have non-zero values and 95% values are zero's. For the simulation a nite population of size N = 10000 was randomly generated and separated into four strata each of which have a size of 2500. A random sample of 135 was
drawn with inclusion and weight probabilities of strata being the following, Strata 1: P1=25/2500,W1=2500/25,Strata 2: P2 = 30/2500 ,w2 = 2500/30,Strata 3: P3 = 35/2500 ,w3 = 2500/35, Strata 4: P4= 45/2500 ,w4 = 2500/45. The sizes of each samples being drawn are n1 =25,n2 =30,n3 =35,n4=45 respectively. Results are presented from three different normal populations where the means and standard deviations differ signifcantly for the non-zero component. Results in Table 1 and Figure 2 assumed the non-zero component follows N(mu = 100, sd = 10), results in Table 2 and Figure 3 assume that the non-zero component follows N(mu = 50, sd = 2), and results in Table 3 and Figure 4 assumed the non-zero component follows N(mu = 20, sd = 1).

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G2.png?raw=true" width="600" title="hover text">

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G3.png?raw=true" width="600" title="hover text">
  
<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/T4Table.png?raw=true" width="600" title="hover text">
  
<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/G4.png?raw=true" width="600" title="hover text">
  
## Conclusion

The pseudo-likelihood ratio statistic developed in H. Chen et al. (2010) has assumptions, and computing confidence intervals of the mean of a zero-inflated population are mathematically and computationally complex. The complexity arises as the method uses the complex probability sampling designs in the two-component model. The use of bootstrapping bypasses many of the assumptions of the asymptotic distribution and construction of confidence intervals is computationally simpler. Use of the pseudo-likelihood function assumes a known probability distribution for the non-zero component, so the parametric bootstrap method is an appropriate approach. However, the non-parametric bootstrap method is employed to make a comparison. Confidence intervals based on the quantiles of the bootstrap distribution of estimated theta under both the parametric and non-parametric bootstrap method have been shown to consistently capture the true value of theta, the mean of the zero-inflated population. Under the assumption of a normally distributed non-zero component, the parametric bootstrap method gives narrower confidence intervals than the nonparametric bootstrap method.

## Source Code

This segment of code simulates data and applies the sampling methodlogy proposed above.

```{r}
rm(list=ls())

library(VGAM)
library(stratifyR)]
library(rsample)
library(boot)
library(sampling)
library(plyr)
library(dplyr)
library(gridExtra)
library(purrr)
library(ggplot2)
library(minDiff)

 ###Initial Sample(As shown in first histogram above###
  prob = 1-0.30
  isZero = rbinom(n = 1000, size = 1, prob = prob)
  y = ifelse(isZero==1, 0, rnorm(sum(isZero==0),6,1))
  hist(y)
  
 ###### STRATA SAMPLE Function###### 
##Simulates data and conducts stratafied sampling methodlogy as conducted in paper##
  Stratafunction <- function(N,alpha,mu,sigma){
  set.seed(1)
  prob = 1-alpha
  isZero = rbinom(n = N, size = 1, prob = prob)
  yi = ifelse(isZero==1, 0, rnorm(sum(isZero==0),mu,sigma))
  id <- c(1:10000)
  dataframe <- data.frame(cbind(id,yi))
  assigment <- create_groups(dataframe, 
                             criteria_scale = c("yi"), sets_n = 4, repetitions = 2000,talk=F)
  
  dataframe_s1_1 <- assigment %>% filter(newSet ==1)
  dataframe_s2_2 <- assigment %>% filter(newSet ==2)
  dataframe_s3_3 <- assigment %>% filter(newSet ==3)
  dataframe_s4_4 <- assigment %>% filter(newSet ==4)
  
  dataframe_s1_1$strata <- 1
  dataframe_s1_1$pi <- 25/2500
  dataframe_s1_1$wi <- 2500/25
  
  dataframe_s2_2$strata <- 2
  dataframe_s2_2$pi <- 30/2500
  dataframe_s2_2$wi <- 2500/30
  
  dataframe_s3_3$strata <- 3
  dataframe_s3_3$pi <- 35/2500
  dataframe_s3_3$wi <- 2500/35
  
  dataframe_s4_4$strata <- 4
  dataframe_s4_4$pi <- 45/2500
  dataframe_s4_4$wi <- 2500/45
  stratafied_frame <- rbind(dataframe_s1_1,dataframe_s2_2,dataframe_s3_3,dataframe_s4_4)
  
  x <- sampling::strata(stratafied_frame, "strata", size = c(25, 30, 35,45), method = "srswor")
  data <- getdata(stratafied_frame, x)
  data
  }
```

This segment of code simulates data and applies the sampling methodlogy proposed above.

```{r}
set.seed(180)
 resample2 <- rsample::bootstraps(Stratafunction(10000,0.05,100,10), times = 10000)
  Theta_Hat <- map_dbl(resample2$splits,
                function(x) {
                  dat <- as.data.frame(x)$yi
                  mean(dat)
                })
  me2 = ceiling(10 * 2 * sd(Theta_Hat))/10
  ci2 <- round(mean(Theta_Hat), 1) + c(-1, 1) * me2
  lbci2 <- ci2[1]
  hbci2 <- ci2[2]
  m1np05 <- mean(Theta_Hat)
 set.seed(131)
 resample3 <- rsample::bootstraps(Stratafunction(10000,0.10,100,10), times = 10000)
 Theta_Hat_010 <- map_dbl(resample3$splits,
                function(x) {
                  dat <- as.data.frame(x)$yi
                  mean(dat)
                })
  me3 = ceiling(10 * 2 * sd(Theta_Hat_010))/10
  ci3 <- round(mean(Theta_Hat_010), 1) + c(-1, 1) * me3
  lbci3 <- ci3[1]
  hbci3 <- ci3[2]
  m1np10 <- mean(Theta_Hat_010)
 
 set.seed(1)
 resample4 <- rsample::bootstraps(Stratafunction(10000,0.20,100,10), times = 10000)
  Theta_Hat_020 <- map_dbl(resample4$splits,
                function(x) {
                  dat <- as.data.frame(x)$yi
                  mean(dat)
                })
  me4 = ceiling(10 * 2 * sd(Theta_Hat_020))/10
  ci4 <- round(mean(Theta_Hat_020), 1) + c(-1, 1) * me4
  lbci4 <- ci4[1]
  hbci4 <- ci4[2]
  m1np20 <- mean(Theta_Hat_020)
 
 set.seed(31)
 resample5 <- rsample::bootstraps(Stratafunction(10000,0.50,100,10), times = 10000)
Theta_Hat_050 <- map_dbl(resample5$splits,
                function(x) {
                  dat <- as.data.frame(x)$yi
                  mean(dat)
                })
  me5 = ceiling(10 * 2 * sd(Theta_Hat_050))/10
  ci5 <- round(mean(Theta_Hat_050), 1) + c(-1, 1) * me5
  lbci5 <- ci5[1]
  hbci5 <- ci5[2]
 m1np50 <- mean(Theta_Hat_050)
# 6/10/20/50
 # par(mfrow=c(4,2))
p = ggplot(data.frame(Theta_Hat), aes(x=Theta_Hat))+
   geom_histogram(color="black", fill="lightblue", bins = 30, boundary = 0) +
   geom_vline(aes(xintercept=ci2[1]),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=ci2[2]),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_y_continuous(limits = c(0, 1500),breaks = c(0,500,1000,1500)) + scale_x_continuous(limits = c(0, 20),breaks = c(0, 5, 10,15)) + xlab("Theta Hat")
p2 = ggplot(data.frame(Theta_Hat_010), aes(x=Theta_Hat_010))+
   geom_histogram(color="black", fill="lightblue", bins = 30, boundary = 0) +
   geom_vline(aes(xintercept=ci3[1]),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=ci3[2]),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_y_continuous(limits = c(0, 1500),breaks = c(0,500,1000,1500)) + scale_x_continuous(limits = c(0, 20),breaks = c(0, 5, 10,15))+ xlab("Theta Hat")
 p3 = ggplot(data.frame(Theta_Hat_020), aes(x=Theta_Hat_020))+
   geom_histogram(color="black", fill="lightblue", bins = 40, boundary = 0) +
   geom_vline(aes(xintercept=ci4[1]),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=ci4[2]),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_x_continuous(limits = c(7.5, 37),breaks = c(10,15,20,25,30)) + scale_y_continuous(limits = c(0, 1250),breaks = c(0, 250, 500,750,1000))+ xlab("Theta Hat")
  p4 =  ggplot(data.frame(Theta_Hat_050), aes(x=Theta_Hat_050))+
   geom_histogram(color="black", fill="lightblue", binwidth = 1, boundary = 0) +
   geom_vline(aes(xintercept=ci5[1]),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=ci5[2]),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_x_continuous(limits = c(30, 70),breaks = c(40, 50, 60)) + scale_y_continuous(limits = c(0, 1750),breaks = c(0, 500, 1000,1500))+ xlab("Theta Hat")
```

This segment of code is the proposed parametric psuedo-likelihood estimation of mean for a zero-inflated normal mixture.

```{r}
  loglikelihood <- function(df,N,alpha,mu,sigma){
  nonzero <- function(x) sum(x == 0)
  P3 = 1
  C = 1
  Wo = 1
  wP = 1
  P4 = 1
  wiyi = 1
  i=1
  n_135 <- data.frame(df)
  n = nrow(n_135)
  m = as.numeric(numcolwise(nonzero)(n_135))
  m = data.frame(m)
  m <- m %>% filter(m >0)
  m <- m[1,1]
  nm = n-m
  ii = as.integer(nm + 1)
  yi = n_135$yi
  alpha = alpha
  mu = mu
  sigma = sigma
  p = n_135$pi
  wi = n_135$wi
  n_1352 <- n_135 %>% filter(yi > 0)
  wi2 <- n_1352$wi
  yi2 <- n_1352$yi

  i=1
  for (i in i:nm){
   P3[i] <-  wi[i] * (yi[i] - mu)^2
   sumP3 <- sum(P3)
   sumP3
  }
  i = 1
    for (i in i:nm){
   C[i] <-  wi[i] * log(2 * pi)^(-1/2)
   Csum <- sum(C)
   Csum
    }

    sumWo = sum(wi[ii:n])
    
    
    i = 1
     for (i in i:nm){
   wP[i] <-  wi2[i]
   wP[is.na(wP)] <- 0
   wPsum <- sum(wP)
   wPsum
    }
  
logl <- sumWo * log(1-alpha) + wPsum * log(alpha) - wPsum * log(sigma) - (1/(2*(sigma^2))) * sumP3 + Csum
  i = 1
  for (i in i:nm) {
    wiyi[i] <- wi2[i] * yi2[i]
    wiyi[is.na(wiyi)] <- 0
     wiyi <- sum(wiyi)
    wiyisum <- sum(wiyi)
    wiyisum
  }
  
    alpha_hat <- (wPsum)/(wPsum+sumWo)
  mu_hat <- (1/wPsum) * wiyisum

  i = 1
  
    for (i in i:nm){
   P4[i] <-  wi[i] * ((yi[i] - mu_hat)^2)
    sumP4 <- sum(P4)
    sumP4
    }
  
  sigma_hat <- sqrt((1/wPsum) * sumP4)
  theta_hat <- alpha_hat * mu_hat 
return(theta_hat)
   }
```
Similarily, this function carries out parametric bootstrap estimation of the mean.

```{r}
set.seed(1238)
psample2 <- rsample::bootstraps(Stratafunction(10000,0.05,100,10) , times = 10000)
Parametric_Theta <- map_dbl(psample2$splits,
                function(x) {
                  dat <- as.data.frame(x)
                  loglikelihood(dat,10000,0.05,100,10)})
Parametric_Theta <- na.omit(Parametric_Theta)
  me6 = ceiling(10 * 2 * sd(Parametric_Theta))/10
  ci6 <- round(mean(Parametric_Theta), 1) + c(-1, 1) * me6
  lbci6 <- ci6[1]
  hbci6 <- ci6[2]
  p105 <- ggplot(data.frame(Parametric_Theta), aes(x=Parametric_Theta))+
   geom_histogram(color="black", fill="lightgreen", bins = 30, boundary = 0) +
   geom_vline(aes(xintercept=lbci6),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=hbci6),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_y_continuous(limits = c(0, 1500),breaks = c(0, 500, 1000,1500))+ xlab("Theta Hat")
  m1p05 <- mean(Parametric_Theta)
  
set.seed(12990)
psample3 <- rsample::bootstraps(Stratafunction(10000,0.10,100,10) , times = 10000)
Parametric_Theta_10 <- map_dbl(psample3$splits,
                function(x) {
                  dat <- as.data.frame(x)
                  loglikelihood(dat,10000,0.10,100,10)})
Parametric_Theta_10 <- na.omit(Parametric_Theta_10)
  me7 = ceiling(10 * 2 * sd(Parametric_Theta_10))/10
  ci7 <- round(mean(Parametric_Theta_10), 1) + c(-1, 1) * me7
  lbci7 <- ci7[1]
  hbci7 <- ci7[2]
  p110 <- ggplot(data.frame(Parametric_Theta_10), aes(x=Parametric_Theta_10))+
   geom_histogram(color="black", fill="lightgreen", bins = 32, boundary = 0) +
   geom_vline(aes(xintercept=lbci7),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=hbci7),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_y_continuous(limits = c(0, 1250),breaks = c(0, 250, 500,750,1000,1250))+ xlab("Theta Hat")
  
  m1p10 <- Parametric_Theta_10
  
set.seed(1943)
psample4 <- rsample::bootstraps(Stratafunction(10000,0.20,100,10) , times = 10000)
Parametric_Theta_20 <- map_dbl(psample4$splits,
                function(x) {
                  dat <- as.data.frame(x)
                  loglikelihood(dat,10000,0.20,100,10)})
Parametric_Theta_20 <- na.omit(Parametric_Theta_20)
  me8 = ceiling(10 * 2 * sd(Parametric_Theta_20))/10
  ci8 <- round(mean(Parametric_Theta_20), 1) + c(-1, 1) * me8
  lbci8 <- ci8[1]
  hbci8 <- ci8[2]
  p120 <- ggplot(data.frame(Parametric_Theta_20), aes(x=Parametric_Theta_20))+
   geom_histogram(color="black", fill="lightgreen", bins = 40, boundary = 0) +
   geom_vline(aes(xintercept=lbci8),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=hbci8),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_x_continuous(limits = c(2, 35),breaks = c(10, 15, 20,25,30)) + scale_y_continuous(limits = c(0, 1250),breaks = c(0, 250, 500,750,1000))+ xlab("Theta Hat")
   # p120
   m1p20 <- mean(Parametric_Theta_20)
   
   set.seed(1944)
psample5 <- rsample::bootstraps(Stratafunction(10000,0.50,100,10) , times = 10000)
Parametric_Theta_50 <- map_dbl(psample5$splits,
                function(x) {
                  dat <- as.data.frame(x)
                  loglikelihood(dat,10000,0.50,100,10)})
Parametric_Theta_50 <- na.omit(Parametric_Theta_50)
  me9 = ceiling(10 * 2 * sd(Parametric_Theta_50))/10
  ci9 <- round(mean(Parametric_Theta_50), 1) + c(-1, 1) * me9
  lbci9 <- ci9[1]
  hbci9 <- ci9[2]
  p150 <- ggplot(data.frame(Parametric_Theta_50), aes(x=Parametric_Theta_50))+
   geom_histogram(color="black", fill="lightgreen", bins = 30, boundary = 0) +
   geom_vline(aes(xintercept=lbci9),   # Ignore NA values for mean
               color="red", size=0.25) +
    geom_vline(aes(xintercept=hbci9),   # Ignore NA values for mean
               color="red", size=0.25) + theme_bw() + scale_x_continuous(limits = c(30, 75),breaks = c(40, 50, 60)) + scale_y_continuous(limits = c(0, 1750),breaks = c(0, 500, 1000,1500))+ xlab("Theta Hat")
   # p150
   m1p50 <- mean(Parametric_Theta_50)
  
grid1 <- gridExtra::grid.arrange(p,p2,p105,p110,p3,p4,p120,p150,ncol=2,nrow=4)
plot(grid1)
```

## References

Paneru, Khyam, et al. \Estimation of Zero-Inflated Population Mean: A Bootstrapping
Approach." Journal of Modern Applied Statistical Methods, vol. 17, no. 1, 2018, doi:10.22237/jmasm/1525133460. Ahmad, W. M. A. W., Abdullah, S. A., Mokhtar, K.,
Aleng, N. A., Halim, N., Ali, Z. (2015). Applications of zero in
ated models for health sciences data. Journal of Advanced Scientific Research, 6(2), 39-44. Chen, H., Chen, J.,
Chen, S.-Y. (2010). 
Confdence intervals for the mean of a population containing many zero values under unequal-probability sampling. Canadian Journal of Statistics, 38(4), 582-597. doi: 10.1002/cjs.10077 Chen, J., Sitter, R. R. (1999). A pseudo empirical
likelihood approach to the effective use of auxiliary information in complex surveys.

## Disclaimer

This project is a reproduction of a previous paper, which can be found here:
https://digitalcommons.wayne.edu/cgi/viewcontent.cgi?article=2557&context=jmasm
This project is meant to reproduce key findings in the paper and reproduce the methods introduced by Paneru. The goal is to make the methodology code freely available to any user. None of this work is original work, and all credit goes to the respective authors for their methodology design. 
