# sim1
The exponential distribution can be simulated in R with rexp(n, lambda) where lambda is the rate parameter. The mean of exponential distribution is 1/lambda and the standard deviation is also also 1/lambda. Set lambda = 0.2 for all of the simulations. In this simulation, you will investigate the distribution of averages of 40 exponential(0.2)s. Note that you will need to do a thousand or so simulated averages of 40 exponentials.

Illustrate via simulation and associated explanatory text the properties of the distribution of the mean of 40 exponential(0.2)s.  You should

* 1. Show where the distribution is centered at and compare it to the theoretical center of the distribution.

```r
set.seed(7)
n <- 40
lambda <- .2
nsim <-1000
mns <- colMeans(replicate(nsim, rexp(n,.2)))
```

```r
center <- mean(mns)
center
```

```
## [1] 4.983294
```
we see the distribution is centered at  

```r
center
```

```
## [1] 4.983294
```
is approximatley equal to 

```r
1/lambda
```

```
## [1] 5
```

* 2. Show how variable it is and compare it to the theoretical variance of the distribution.

The theoretical variance is 

```r
(1/lambda^2) / n
```

```
## [1] 0.625
```
The variance of the simulations

```r
var(mns)
```

```
## [1] 0.5792547
```
They are very close.

* 3. Show that the distribution is approximately normal.

As we know when n is large and lambda is small, the exponential distribution can be approxiately regarded as normal distribution. 

```r
simSD <- sd(mns)
simMean <- mean(mns)
mns <- (mns-simMean)/simSD
hist(mns)
```

![](sim1_files/figure-html/unnamed-chunk-7-1.png) 
The quantiles in 1,2,&3 are

```r
sum(abs(mns) <= simSD )/nsim
```

```
## [1] 0.552
```

```r
sum(abs(mns) <= 2*simSD)/nsim
```

```
## [1] 0.882
```

```r
sum(abs(mns) <= 3*simSD)/nsim
```

```
## [1] 0.976
```
is close to 68%, 95%,99%. 

```r
gaussian <- rnorm(1000)
hist(gaussian)
```

![](sim1_files/figure-html/unnamed-chunk-9-1.png) 

```r
hist(mns)
```

![](sim1_files/figure-html/unnamed-chunk-9-2.png) 
