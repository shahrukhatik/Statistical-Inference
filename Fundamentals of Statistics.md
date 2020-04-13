The Classic Coin Toss Example
================
Shahrukh Khan
April 13th, 2020

Let's suppose a coin has probability P of falling heads up. If we flip the coin many times, we would expect the proportion of
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

Suppose we flip a coin n times and let P denote the probability of heads. Let X be the number of heads. We call X
a binomial random variable. Intuition suggests that X will be close to np. To see if this is true, we
can repeat this experiment many times and average the X values. Let's build a simulation and compare the average of the X's to np . Assuming p =.3 and n = 10, n = 100, and n = 1,000.

