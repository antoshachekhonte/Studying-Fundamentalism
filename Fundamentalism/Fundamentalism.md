Aim
---

What are the factors that explain fundamentalism of an individual's
religious belief? Using the General Social Survey dataset, this project
attempts to identify some of the factors that account for the
fundamentalism of a respondent's religious belief.

Data
----

### The following variable from the General Social Survey dataset was identified as the the dependent variable:

**Fund**. This variable captures the fundamentalism of a respondent's
religious belief on a 3 point scale. This variable was recoded into a
binary variable indicating whether a respondent is a fundamentalist or
not

### The following variables from the General Social Survey dataset were identified as independent variables:

**Pray**. This variable captures how often a respondent prays on a 6
pointscale

**Bible**. This variable captures how a respondent believes the bible
should be viewed on a 4 pointscale

**God**. This variable captures respondents' beliefs in the existence of
god on a 6 point scale

**Attend**. This varliable captures how often a respondent attends
religious services on an 8 point scale

Simple Linear Model
-------------------

    ## 
    ## Call:
    ## lm(formula = fund ~ pray + god + attend + bible, data = gss.sub)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -0.5620 -0.3498 -0.1628  0.4596  1.1218 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) -0.400167   0.039292 -10.184  < 2e-16 ***
    ## pray         0.021484   0.006382   3.367 0.000771 ***
    ## god          0.026191   0.007913   3.310 0.000946 ***
    ## attend       0.021568   0.003417   6.313 3.18e-10 ***
    ## bible        0.125895   0.012794   9.840  < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.4244 on 2803 degrees of freedom
    ##   (1702 observations deleted due to missingness)
    ## Multiple R-squared:  0.1487, Adjusted R-squared:  0.1474 
    ## F-statistic: 122.4 on 4 and 2803 DF,  p-value: < 2.2e-16

The independent variables *pray*, *attend*, *bible* and *god* account
for **14.9%** of the variance in the dependent variable *fund*. All the
independent variables are positively correlated with the dependent
variable.

*Pray* is positively correlated with *fund* and is associated with a
coefficient of 0.0215, which means that a unit increase *pray* is
associated with a 0.021 increase in *fund*, controlling for all other
independent variables.

Similarly, *attend* is associated with a coefficient of 0.0215, *bible*
is associated with a coefficient of 0.126, and *god* is associated with
a coefficient of 0.026.

*Bible* has the strongest correlation with *fund*, meaning that the more
uncritically a respondent accepts the bible as the word of god, the more
likely he is to self report as a fundamentalist.

Binary Logistic Model
---------------------

### Why should this model be used?

The linear probability model assumes that the error terms have the same
variance. However, given that the dependent variable in this study is
dichotomous, i.e., it can only take on two values, the above assumption
is violated and heteroscedasticity is observed. Additionally, the linear
probability model assumes the residuals must have a normal distribution.
This assumption too, is violated, since residuals can only take one of
two possible values.

The logistic model overcomes these shortcomings by incorporating the
logistic function (<https://en.wikipedia.org/wiki/Logistic_function>) in
its definition.

    ## 
    ## Call:
    ## glm(formula = fund ~ pray + attend + bible + god, family = binomial, 
    ##     data = gss.sub)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -1.3835  -0.8762  -0.5042   1.0239   2.8727  
    ## 
    ## Coefficients:
    ##             Estimate Std. Error z value Pr(>|z|)    
    ## (Intercept) -6.03701    0.34637 -17.429  < 2e-16 ***
    ## pray         0.15576    0.03938   3.956 7.63e-05 ***
    ## attend       0.10007    0.01834   5.456 4.87e-08 ***
    ## bible        0.73165    0.07768   9.419  < 2e-16 ***
    ## god          0.30798    0.06004   5.130 2.90e-07 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 3445.1  on 2807  degrees of freedom
    ## Residual deviance: 2951.1  on 2803  degrees of freedom
    ##   (1702 observations deleted due to missingness)
    ## AIC: 2961.1
    ## 
    ## Number of Fisher Scoring iterations: 5

From the above model summary, it can be observed that for every category
increase in *pray*, the variable that measures a respondent's
self-reported prayer frequency, the logit of *fund* increases by 0.16,
net all other independent variables. Similarly, for a category increase
in *attend*, the variable that measures the self reported religious
attendance frequency, the logit of *fund* increases by 0.10. For a
category increase in *bible*, the logit of *fund* increases by 0.73 and
for a category increase in *god*, the logit of *fund* increases by 0.30.

The two independent variables that have an especially strong
relationship with the dependent variable are *bible*, which records the
feelings of respondents about the bible, and *god*, which records the
respondent's beliefs in god.

The independent variables *bible* and *god* have particularly strong
relationships with *fund*. *Bible* takes on the following categorical
values: "Other","Ancient Book", "Inspired Word" and "Actual Word". A
category increase in *bible*, which represents an increase in the level
at which a respondent accepts the precepts of the bible, is associated
with an increase in the logit of self reporting to be a fundamentalist
by 0.73. Similarly, a category increase in *god*, which represents an
increase in the level at which a respondent accepts the existence of
god, is associated with an increase in the logit of self reporting to be
a fundamentalist by 0.31.

### Odds-ratios from logit model

    ## (Intercept)        pray      attend       bible         god 
    ## 0.002388691 1.168540199 1.105243059 2.078512361 1.360678441

The odds of being a fundamentalist increase by 17% with a category
increase in the *pray*, net of all other independent variables.
Similarly, the odds of being a fundamentalist increase by 10.5% with a
category increase in the *attend* (net of all other variables). The odds
of being a fundamentalist increase by 108% with a category increase in
*bible* (net of all other variables), and by 36% with a category
increase in *god* (net of all other variables).  
\#\# Predicted Probabilities

### With pray, attend and god at the highest possible categories, what difference does moving from the lowest category of bible to the highest make?

    ##         1         2 
    ## 0.1515619 0.6159882

A movement from the lowest to the highest category of *bible*, with all
other independent variables set to their highest category, is associated
with an increase in the predicted probability of *fund* by 0.46 - a
rather large increase!

### With bible, attend and god at the highest possible categories, what difference does moving from the lowest category of pray to the highest make?

    ##         1         2 
    ## 0.4240372 0.6159882

A change from the lowest to the highest category of *pray*, with all
other independent variables set at their highest categories, results in
an increase in the predicted probability of *fund* by 0.19.

This is interesting because it gives provides an intuition of the extent
to which prayer frequency is related with self identification as a
fundamentalist. The difference, on average, between the predicted *fund*
scores of two individuals, one who responds to the question of "How
often do you pray" with "Never", and the other who responds to the same
with "Sevaral times a day" is 0.19.

Visual Study of Interaction between *Bible* and *God*
-----------------------------------------------------

![](Fundamentalism_files/figure-markdown_strict/unnamed-chunk-10-1.png)

For different answers to the question "Which statement comes closest to
your view of the bible?", a change in the answer to the question "Do you
believe in god" from "Don't believe", on one end, to "I believe without
any doubt", on the other, results in different increases in the
predicted probability of *fund* - for higher categories of *bible*, the
increases in the predicted probability of *fund* with *god* are greater.
