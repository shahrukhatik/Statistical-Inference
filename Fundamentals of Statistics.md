Fundamentals of Statistics
================
Shahrukh Khan
April 13th, 2020
Problems adapted and answered from - "All of Statistics, a concise course in Statistical Inference - Larry Wasserman"

1. Let's suppose a coin has probability P of falling heads up. If we flip the coin many times, we would expect the proportion of
heads to be near p. Let's Take P = .3 and P=0.03 and n = 5,000 and simulate n coin flips. 
Plotting the proportion of heads as a function of n, we have:

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/Coinflip.png?raw=true" width="350" title="hover text">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/Coinflip003.png?raw=true" width="350" alt="accessibility text">
</p>

From both these plots we can indeed see that this holds true!

Source Code:

    library(ggplot2)
    n<-1:5000
    events<-sample(c(0,1),5000,prob=c(0.7,0.3),replace=TRUE)
     probability_head<-cumsum(events)/n
     dataset <- cbind(seq(1:5000),probability_head)
     dataset <- as.data.frame(dataset)
     sp <-ggplot(dataset) + geom_line(aes(x=V1, y=probability_head)) + theme_minimal() + labs(title="Probability of heads",     x="# Coinflip", y="Probability")  
     sp +  geom_hline(yintercept=0.3)
     n<-1:5000
     events<-sample(c(0,1),5000,prob=c(0.97,0.03),replace=TRUE)
    probability_head<-cumsum(events)/n
     dataset <- cbind(seq(1:5000),probability_head)
     dataset <- as.data.frame(dataset)
     sp <-ggplot(dataset) + geom_line(aes(x=V1, y=probability_head)) + theme_minimal() + labs(title="Probability of heads",     x="# Coinflip", y="Probability")  
     sp +  geom_hline(yintercept=0.03)

2. Suppose we flip a coin n times and let P denote the probability of heads. Let X be the number of heads. We call X
a binomial random variable. Intuition suggests that X will be close to np. To see if this is true, we
can repeat this experiment many times and average the X values. Let's build a simulation and compare the average of the X's to np . Assuming p =.3 and n = 10, n = 100, and n = 1,000.

Source Code:

```{r}
p = probability of heads 
x = number of heads 
n = number of times coin is flipped
p<- 0.3
n1<- 10
n2<- 100
n3<- 1000

*Case 1: When n is 10:

events <-sample(c(0,1),n1,prob=c(0.7,p),replace=TRUE)
x<- sum(events)
x

probability_head_n1<-x/n1
probability_head_n1

*Comparing X to NP:

n1p<- n1*probability_head_n1
n1p

*We can see that the value of X (3) and NP (3) came out to be the same. 

*Case 2: When n is 100:

events<-sample(c(0,1),n2,prob=c(0.7,p),replace=TRUE)
x<- sum(events)
x
probability_head_n2<-x/n2
probability_head_n2

*Comparing X to NP:

n2p<- n2*probability_head_n2
n2p

*When n is 100, we can see that x and np is the same. Both the values came out to be the same as well. They were 32.
Case 3: When n is 1000

events<-sample(c(0,1),n3,prob=c(0.7,p),replace=TRUE)

x<- sum(events)
x
probability_head_n3<-x/n3
probability_head_n3

*Comparing X to NP: 

n3p<- n3*probability_head_n3
n3p

*When n is 1000, we can see that they are same as well. X and np were both 271.

```

3. Let X have a continuous, strictly increasing cdf F. Let Y = F (X). The density of Y is called the probability integral transform. Now let U ∼ Uniform(0, 1) and let X = F−1(U). We can show that X ∼ F. Let's write a program that takes Uniform (0,1) random variables and generates random variables from an Exponential (β) distribution.

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/betabarplot.png?raw=true" width="350" title="hover text">

```{r}
library(ggplot2)
xbeta<- function(n,beta){
  u<-runif(n,min=0,max=1)
  x <- -beta*log(1-u)
  return(x)
}

df <- as.data.frame(xbeta(1000,2))
colnames(df)[1] <- "value"

p<-ggplot(df, aes(x=value)) + 
  geom_histogram(color="black", fill="white",binwidth=1) + theme_minimal()
p
```



