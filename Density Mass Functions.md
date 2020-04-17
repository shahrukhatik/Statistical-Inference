Density and Mass Functions
================
Shahrukh Khan
April 15th, 2020

In this section, we're going to take a look at several distributions along with their PDFS/PMF's.

#Binomial PMF

<p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/PMFBinomial.png?raw=true" width="350" title="hover text">
 
```{r}
library(gridExtra)
library(ggplot2)
#PMF of Binomial with n = 25 and p ∈ {0.25, 0.5}
x<- 0:25
data <- dbinom(x, size=25, 0.25)
df <- as.data.frame.array(cbind(x,data))
p1 <- ggplot(df, aes(x,data)) +  geom_bar( stat = "identity") + ggtitle("PMF Binomial,n=25,p=0.25") + theme_minimal() + ylab("Probability")
data2 <- dbinom(x, size=25, 0.5)
df2 <- as.data.frame.array(cbind(x,data2))
p2 <- ggplot(df2, aes(x,data2)) +  geom_bar( stat = "identity") + ggtitle("PMF Binomial,n=25,p=0.5") + theme_minimal() + ylab("Probability")
grid.arrange(p1,p2,nrow=1,ncol=2)
```

#Geometric
  
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/PMFGeometric.png?raw=true" width="350" alt="accessibility text">
</p>

```{r}
x2 <- 1:50
data3 <- dgeom(x2,prob=1/9)
df3 <- as.data.frame.array(cbind(x2,data3))
p3 <- ggplot(df3, aes(x2,data3)) +  geom_bar( stat = "identity") + ggtitle("PMF Geometric,p=1/9") + theme_minimal() + ylab("Probability")
p3
```
