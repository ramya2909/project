Golf Ball
================
Author
25/06/2019

Introduction

Par Inc., is a major manufacturer of golf equipment. Management believes
that Par’s market share could be increased with the introduction of a
cutresistant, longer-lasting golf ball. Therefore, the research group at
Par has been investigating a new golf ball coating designed to resist
cuts and provide a more durable ball. The tests with the coating have
been promising. One of the researchers voiced concern about the effect
of the new coating on driving distances. Par would like the new
cut-resistant ball to offer driving distances comparable to those of the
current-model golf ball. To compare the driving distances for the two
balls, 40 balls of both the new and current models were subjected to
distance tests. The testing was performed with a mechanical hitting
machine so that any difference between the mean distances for the two
models could be attributed to a difference in the design. The results of
the tests, with distances measured to the nearest yard, are contained in
the data set “Golf”. Prepare a Managerial Report

Project objective

1.  Formulate and present the rationale for a hypothesis test that par
    could use to compare the driving distances of the current and new
    golf balls
2.  Analyze the data to provide the hypothesis testing conclusion. What
    is the p-value for your test? What is your recommendation for Par
    Inc.?
3.  Provide descriptive statistical summaries of the data for each model
4.  What is the 95% confidence interval for the population mean of each
    model, and what is the 95% confidence interval for the difference
    between the means of the two population?
5.  Do you see a need for larger sample sizes and more testing with the
    golf balls? Discuss.

<!-- end list -->

``` r
mydata=read.csv("Golf.csv")
dim(mydata)
```

    ## [1] 40  2

\#Inference -There are 40 rows and 2 columns in the given dataset

``` r
#Exploratory data analysis
str(mydata)
```

    ## 'data.frame':    40 obs. of  2 variables:
    ##  $ Current: int  264 261 267 272 258 283 258 266 259 270 ...
    ##  $ New    : int  277 269 263 266 262 251 262 289 286 264 ...

``` r
#checking for missing values
anyNA(mydata)
```

    ## [1] FALSE

\#Inference -there no missing values in the given dataset

``` r
summary(mydata)
```

    ##     Current           New       
    ##  Min.   :255.0   Min.   :250.0  
    ##  1st Qu.:263.0   1st Qu.:262.0  
    ##  Median :270.0   Median :265.0  
    ##  Mean   :270.3   Mean   :267.5  
    ##  3rd Qu.:275.2   3rd Qu.:274.5  
    ##  Max.   :289.0   Max.   :289.0

The summary helps us to get an idea about the minimum and maximum value
of the data. there are no much difference in the values so this
indicates that there might not be any outliers present.

``` r
par(mfrow=c(2,2))
hist(mydata$Current,main='Current ball',xlab = "Driving distance",ylab = "Frequency",col="red")
hist(mydata$New,main='Current ball',xlab = "Driving distance",ylab = "Frequency",col="red")
boxplot(mydata$Current,main='Current ball',xlab = "Driving distance",ylab = "Frequency",col="blue",horizontal = TRUE)
boxplot(mydata$New,main='Current ball',xlab = "Driving distance",ylab = "Frequency",col="blue",horizontal = TRUE)
```

![](GOLF_BALL_copy_files/figure-gfm/unnamed-chunk-5-1.png)<!-- --> \#Key
Observations

\-The average distance covered by ‘New’ golf ball (Mean = 267.5) is
lower as compared to ‘Current’ golf ball (Mean = 270.3) -New golf ball
observed to have relatively higher variation in the data distribution in
comparison to Current golf ball -No outliers were observed in the data
range for Current & New data sets.

# Hypothesis formation

we need to define the null and the alternative hypothesis

In Par Inc. case, the management would like to produce the new golf
balls once it is comparable to the current golf balls. A sample of 40
balls of both the current and new models were tested with a mechanical
hitting machine so that any difference between the mean distances for
the two models could be attributed to a difference in the two models.
Therefore, a hypothesis test that Par Inc. could use to compare the
driving distance of the current and new golf balls. The Null Hypothesis
& Alternative Hypothesis is formulated as follow:

Null Hypothesis (H0): µ1 - µ2 = 0 (i.e. they are the same) Alternative
Hypothesis (Ha): µ1 - µ2 ≠ 0 (i.e. they are not the same) Where,

``` 
    • µ1: Mean driving distance of current model golf ball
    • µ2: Mean driving distance of new golf ball
```

By formulation of above hypotheses, we assume that the current and new
golf balls show no significant difference to each
other.

``` r
#the given Par Inc.,we can assume that it seems to be an independent sample case,the two tailed test will be pplicable to proceed with this project.

#Let us calculate the p-value using the R function ‘t.test’.

t.test(mydata$Current,mydata$New)
```

    ## 
    ##  Welch Two Sample t-test
    ## 
    ## data:  mydata$Current and mydata$New
    ## t = 1.3284, df = 76.852, p-value = 0.188
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  -1.384937  6.934937
    ## sample estimates:
    ## mean of x mean of y 
    ##   270.275   267.500

since it is a two tailed test , the p-value= 0.188/2=0.094

# Key observation and recommendation

  - the p=value 0.094 is is greater than alpha i.e., 0.05,so null
    hypothesis cannot be rejected.
  - The conclusion is that this data does not provide statistical
    evidence that the new golf balls have either a lower mean driving
    distance or a higher mean driving distance. Par Inc. should take the
    new golf balls in production as the p-value indicate that there is
    no significant difference between estimated population mean of
    current as well as new golf balls.

<!-- end list -->

``` r
# the descriptive statistical summaries for each data
t.test(mydata$Current)
```

    ## 
    ##  One Sample t-test
    ## 
    ## data:  mydata$Current
    ## t = 195.29, df = 39, p-value < 2.2e-16
    ## alternative hypothesis: true mean is not equal to 0
    ## 95 percent confidence interval:
    ##  267.4757 273.0743
    ## sample estimates:
    ## mean of x 
    ##   270.275

\#Key observation

The 95% confidence interval of population mean for Current model is
between 267.4757 & 273.0743. This implies that, with 95% confidence, we
can say that the sample mean driving distance of current balls will be
within this range.

``` r
t.test(mydata$New)
```

    ## 
    ##  One Sample t-test
    ## 
    ## data:  mydata$New
    ## t = 170.94, df = 39, p-value < 2.2e-16
    ## alternative hypothesis: true mean is not equal to 0
    ## 95 percent confidence interval:
    ##  264.3348 270.6652
    ## sample estimates:
    ## mean of x 
    ##     267.5

\#Key observation

The 95% confidence interval of population mean for New model is between
264.3348 & 270.6652. This implies that, with 95% confidence, we can say
that the sample mean driving distance of New balls will be within this
range.

``` r
#95% confidence interval for the difference between the means of the two population 
t.test(mydata$Current,mydata$New)
```

    ## 
    ##  Welch Two Sample t-test
    ## 
    ## data:  mydata$Current and mydata$New
    ## t = 1.3284, df = 76.852, p-value = 0.188
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  -1.384937  6.934937
    ## sample estimates:
    ## mean of x mean of y 
    ##   270.275   267.500

\#Key Observation:

The 95% confidence interval of difference in population mean between
both the models is between –1.38 yards on the lower end 6.93 yards on
the upper end. This implies that, with 95% confidence, we can say that
the difference in sample mean driving distance of both the models will
be within the above range. For the 40 balls we have taken in this
sample, the difference in mean driving distance is -2.775 yards (267.5 –
270.275) which falls in the range.

``` r
delta=mean(mydata$Current)-mean(mydata$New)
pooledSD <- (((40-1)*(8.75^2)+(40-1)*(9.9^2))/(40+40-2))^0.5
pooledSD
```

    ## [1] 9.342711

``` r
delta
```

    ## [1] 2.775

Pooled SD=9.342711
Delta=2.775

``` r
power.t.test(n=40, delta = 2.775, sd=9.342,sig.level = 0.05,type = "two.sample",alternative = "two.sided" )
```

    ## 
    ##      Two-sample t test power calculation 
    ## 
    ##               n = 40
    ##           delta = 2.775
    ##              sd = 9.342
    ##       sig.level = 0.05
    ##           power = 0.258536
    ##     alternative = two.sided
    ## 
    ## NOTE: n is number in *each* group

\#Key Observation

The Power of test is 0.258 or 25.8%, which means there are only 25%
chances that the null hypothesis will not be rejected when it is false.
Hence, we should revisit the number of samples to increase the power of
test.

``` r
#to check the need of a larger size golf ball recalculate the sample using power T test with power as 95% and significance level 0.188.

power.t.test(power=0.95, delta = 2.775,sd=9.342,sig.level = 0.188,type = "two.sample",alternative = "two.sided" )
```

    ## 
    ##      Two-sample t test power calculation 
    ## 
    ##               n = 199.2145
    ##           delta = 2.775
    ##              sd = 9.342
    ##       sig.level = 0.188
    ##           power = 0.95
    ##     alternative = two.sided
    ## 
    ## NOTE: n is number in *each* group

# Key observation and Conclusion

We can see that we need sample size of 200 (rounded up) to get 95% power
of Test. -From the Preliminary Data Analysis, we confirm that the mean
driving distance of New Ball is less than Old Ball. (267.5 yards Vs
270.3 yards). -The Hypothesis Testing concludes that this data does not
provide statistical evidence that the new golf balls have either a lower
or higher mean driving distance. -This implies that Par Inc. should take
the new golf balls in production as the p-value indicate that there is
no significant difference between estimated population mean of current
as well as new golf balls. -The 95% confidence interval of population
mean for Current model is between 267.4757 & 273.0743. -The 95%
confidence interval of population mean for New model is between 264.3348
& 270.6652. -Although the 2 Tail Hypothesis Test recommends to launch
the new ball design into Production, the Power of Test is only 25%. -In
order to have 95% Power of Test, it is recommended to have the number of
samples as 200 for both the designs, and then conclude the Hypothesis
test recommendations.
