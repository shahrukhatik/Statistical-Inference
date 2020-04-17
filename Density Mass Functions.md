Density and Mass Functions
================
Shahrukh Khan
April 15th, 2020

In this section, we're going to take a look at several distributions along with their PDFS/PMF's.

### PMF of Binomial with n = 25 and p ∈ {0.25, 0.5}

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

### PMF of Geometric with p = 1/9

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/PMFGeometric.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x2 <- 1:50
data3 <- dgeom(x2,prob=1/9)
df3 <- as.data.frame.array(cbind(x2,data3))
p3 <- ggplot(df3, aes(x2,data3)) +  geom_bar( stat = "identity") + ggtitle("PMF Geometric,p=1/9") + theme_minimal() + ylab("Probability")
p3
```

### PMF of Negative Binomial with p = 1/9, r = 2

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/PMFNB.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x3 <- 1:20
data4 <- dnbinom(1:20, size=2,prob=1/9)
df4 <- as.data.frame.array(cbind(x3,data4))
p4 <- ggplot(df4, aes(x3,data4)) +  geom_bar( stat = "identity") + ggtitle("PMF Negative Binomial,p=1/9") + theme_minimal() + ylab("Probability")
p4
```

### PMF Binomial with n=100 and p=0.0278 and PMF of Poisson with λ=p∗n=2.78

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/BinomialPois.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x<-0:30
  x4 <- 1:30
  data5 <- dbinom(0:100, size=100,0.0278)
  data6 <- dpois(0:100,2.78)
  df5 <- as.data.frame.array(cbind(x4,data5))
  df6 <- as.dataa.frame.array(cbind(x4,data6))
  p5 <- ggplot(df5, aes(x4,data5)) +  geom_bar( stat = "identity") + ggtitle("Binomial PMF (p=0.25)") + theme_minimal() + ylab("Probability")
  p6 <- ggplot(df6, aes(x4,data6)) +  geom_bar( stat = "identity") + ggtitle("Poisson PMF (lambda=2.78)") + theme_minimal() + ylab("Probability")
  grid.arrange(p5,p6,nrow=1,ncol=2)
  ```

### Exponential density with the following mean parameter λ ∈ {1, 5, 10, 20}

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/Expo.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x <- seq(from=0,to=1,length.out=100)
exp1 <- dexp(x,1)
exp2 <- dexp(x,5)
exp3 <- dexp(x,10)
exp4 <- dexp(x,20)
df7 <- as.data.frame(cbind(x,exp1,exp2,exp3,exp4))
p7 <- ggplot(df7, aes(x,exp1)) +  geom_line( stat = "identity") + ggtitle("Exp(1)") + theme_minimal() + ylab("Density")
p8 <- ggplot(df7, aes(x,exp2)) +  geom_line( stat = "identity") + ggtitle("Exp(5)") + theme_minimal() + ylab("Density")
p9 <- ggplot(df7, aes(x,exp3)) +  geom_line( stat = "identity") + ggtitle("Exp(10)") + theme_minimal() + ylab("Density")
p10 <- ggplot(df7, aes(x,exp4)) +  geom_line( stat = "identity") + ggtitle("Exp(20)") + theme_minimal()+ ylab("Density")
grid.arrange(p7,p8,p9,p10,nrow=2,ncol=2)
```

### Gamma density with the following (α, β) pair: (1, 1), (2, 1), (3, 1), (5, 1)

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/GammaPDF.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x <- seq(from=0,to=1,length.out=100)
dgam1 <- dgamma(x,1,1)
dgam2 <- dgamma(x,2,1)
dgam3 <- dgamma(x,3,1)
dgam4 <- dgamma(x,5,1)
df8 <- as.data.frame(cbind(x,dgam1,dgam2,dgam3,dgam4))
p11 <- ggplot(df8, aes(x,dgam1)) +  geom_line( stat = "identity") + ggtitle("Gamma(1,1)") + theme_minimal() + ylab("Density")
p12 <- ggplot(df8, aes(x,dgam2)) +  geom_line( stat = "identity") + ggtitle("Gamma(2,1)") + theme_minimal() + ylab("Density")
p13 <- ggplot(df8, aes(x,dgam3)) +  geom_line( stat = "identity") + ggtitle("Gamma(3,1)") + theme_minimal() + ylab("Density")
p14 <- ggplot(df8, aes(x,dgam4)) +  geom_line( stat = "identity") + ggtitle("Gamma(5,1)") + theme_minimal() + ylab("Density")
grid.arrange(p11,p12,p13,p14,nrow=2,ncol=2)
```

### Beta density with the following parameters for (α, β): (2, 2), (6, 2),(6, 6), (0.5, 4)

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/BetaPDF.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x <- seq(from=0,to=1,length.out=100)
dbet1 <- dbeta(x,2,2)
dbet2 <- dbeta(x,6,2)
dbet3 <- dbeta(x,6,6)
dbet4 <- dbeta(x,0.5,4)
df9 <- as.data.frame(cbind(x,dbet1,dbet2,dbet3,dbet4))
p15 <- ggplot(df9, aes(x,dbet1)) +  geom_line( stat = "identity") + ggtitle("Beta(2,2)") + theme_minimal() + ylab("Density")
p16 <- ggplot(df9, aes(x,dbet2)) +  geom_line( stat = "identity") + ggtitle("Beta(6,2)") + theme_minimal() + ylab("Density")
p17 <- ggplot(df9, aes(x,dbet3)) +  geom_line( stat = "identity") + ggtitle("Beta(6,6)") + theme_minimal() + ylab("Density")
p18 <- ggplot(df9, aes(x,dbet4)) +  geom_line( stat = "identity") + ggtitle("Beta(0.5,4)") + theme_minimal() + ylab("Density")
grid.arrange(p15,p16,p17,p18,nrow=2,ncol=2) 
```

### Normal density with the following (μ, σ2) pair: (0, 0.1), (0, 1), (0, 2), (0,5)

  <p align="center">
  <img src="https://github.com/shahrukhatik/Statistical-Inference/blob/master/Images/NormPDF.png?raw=true" width="350" alt="accessibility text"> </p>

```{r}
x <- seq(from=-5,to=5,length.out=100)
dnorm1 <- dnorm(x,mean = 0,sd=sqrt(0.1))
dnorm2 <- dnorm(x,mean = 0,sd=sqrt(1))
dnorm3 <- dnorm(x,mean = 0,sd=sqrt(2))
dnorm4 <- dnorm(x,mean = 0,sd=sqrt(5))
df10 <- as.data.frame(cbind(x,dnorm1,dnorm2,dnorm3,dnorm4))
p19 <- ggplot(df10, aes(x,dnorm1)) +  geom_line( stat = "identity") + ggtitle("N(0,0.1)") + theme_minimal() + ylab("Density")
p20 <- ggplot(df10, aes(x,dnorm2)) +  geom_line( stat = "identity") + ggtitle("N(0,1)") + theme_minimal() + ylab("Density")
p21 <- ggplot(df10, aes(x,dnorm3)) +  geom_line( stat = "identity") + ggtitle("N(0,2)") + theme_minimal() + ylab("Density")
p22 <- ggplot(df10, aes(x,dnorm4)) +  geom_line( stat = "identity") + ggtitle("N(0,5)") + theme_minimal() + ylab("Density")
grid.arrange(p19,p20,p21,p22,nrow=2,ncol=2)
```
