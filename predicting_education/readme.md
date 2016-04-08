---
title: "Predicting Public Opinion on Education Spending"
author: "Annamaria Prati"
date: "December 2015"
---
In this project, I used the General Social Survey (GSS) data from 2010 and 2008 as our training dataset and testing dataset, respectively, to predict who favors spending more on national education, using sex, age, race, real income, the number of children, marital status, and political views as my predictors.  After exploring four models, I used my best model to predict the outcomes in the GSS 2012 data: given that 2012 was a presidential election year, accurate prediction would have been important to candidates and their campaigns, pollsters, and political analysts.

In the GSS codebook, the variable definitions are as follows:

1. *sex* - the respondent's sex (binary; 1 = male, 2 = female)
2. *age* - the respondent's age (numeric, represents the respondent's self-reported age, from 18 to 89 years)
3. *race* - the respondent's race (numeric, recoded as a factor; 1 = white, 2 = black, 3 = other)
4. *realrinc*  - respondent's income in 1986 USD dollars (numeric: approximately from $245 to $314,700)
5. *childs* - the total number of children respondent ever had (numeric; from 0 to 8 children)
6. *marital* - respondent's marital status (numeric, recoded as a factor; 1 = married, 2 = widowed, 3 = divorced, 4 = separated, 5 = never married)
7. *polviews* - respondent's political views (numeric, recoded as a factor; from 1 = extremely liberal to 7 = extremely conservative)
8. *nateducy* - respondent's view on national education spending (recoded as a binary variable; 1 = spend more on national education, 0 = spend the same or less)

I experimented with adding other demographic variables, such as the respondent's age, region within the US, and education level, as well as other functional forms, such as squaring *age* or taking the log of *realrinc*.  However the smaller and simpler model presented here had more accurate predictions in the training data.

To run the models faster, I subset the datasets to only include the seven variables listed above.  In addition, to avoid any unnecessary errors, I omitted all the observations that had missing data within the subset.  The final subsetted training data has 607 observations, the subsetted testing data has 587 observations, and the subsetted election data has 534 observations.


##Model I: Logit

For my initial model, I started with a simple logit.

Based on the summary of the logit model, only people from "other" race is statistically significant; all other predictors are not.

From the table comparing the predictions and the actual observations in the testing data, there are 133 total errors, and the prediction accuracy rate is 77.34%.

##Model II: glmnet

For my second model, I investigated whether `glmnet` could improve the prediction accuracy of the logit model.

With `glmnet`, there are 128 total errors, with an overall 78.19% accuracy rate, which is slightly better than the original logit model.

##Model III: Random Forest

For my third model, I examined whether a tree based model such as `randomForest` might yield more accurate predictions than `glmnet`.

Using `randomForest`, there are 134 total errors, with an accuracy rate of 77.17%  This result is slightly worse than both the `glmnet` and the original logit model.

##Model IV: bartMachine

For my fourth and final model I used `bartMachine`.

Using `bartmachine`, there are a total of 130 errors, for an accuracy rate of 77.85%. While this is better than `randomForest` and the logit model, it is not as accurate as `glmnet`.

##Testing the Best: GSS 2012

Since I have now concluded that `glmnet` is the best model, I tested its prediction abilities in the GSS 2012. This data is a stronger test for the model: not only is it four years later from the training data (instead of two), those four years were politically turbulent with the controversial introduction of the Common Core education standards as well as the rise of the Tea Party and fiscal conservatives.

With the election year data, `glmnet` made a total of 118 errors, for an accuracy rate of 77.9%.  This is only slightly lower than the `glmnet` prediction accuracy rate for the 2010 testing data.  This leaves me with reinforced confidence in the `glmnet` model.
