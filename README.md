# The Impact of Health-Adjacent Lifestyle Factors in Global Health

<p align="center">
  <img src="images/f1.jpg" width="80%" height="80%">
</p>

In the study of global health, the measure of life expectancy is one of the most important indicators of the overall health and wellness of the world. In such research, it is important to identify potential factors thatcould contribute to greater longevity. To this end, this report will analyze the extent to which socioeconomic factors such as development status, GDP, population, alcohol consumption, and education have an effect on life expectancy to hopefully elucidate a relationship that can be used to identify methods to prolong life expectancy around the world.

[An article published in the J-Stage Journal of Epidemiology](https://www.jstage.jst.go.jp/article/jea/24/2/24_JE20130059/_article) considered mean years of schooling and gross national income per capita for 91 countries as potential contributors to life expectancy. The results suggested that these factors were correlated to life expectancy, and thus education should be improved in order to increase the overall duration of life. Our analysis will similarly examine potential socioeconomic factors to life expectancy, using data reported in 2019.

## Methods
The goal of this analysis is to develop a model that can explain the relationship between life expectancy
and several socioeconomic factors. This process will involve a series of statistical methods regarding variable
selection, model validation, and assessing potential violations through model diagnostics.

## Variable Selection

In order to select the best set of variables to use in the regression model, we will compare the results of three
different variable selection methods.

1. Forward Selection
This method begins with a model of zero predictors, and builds the model by adding one predictor at a
time in such a way that minimizes the AIC. This continues until the AIC increases, or there are no more
predictors left to add.

2. Backwards Elimination
Similar to the first method but in reverse order, this method begins with a model of all possible predictors,
and removes one predictor at a time whilst trying to minimize the AIC. This continues until the AIC
increases, or there are no more predictors left to remove.

3. Stepwise Selection
This process alternates between forward and backwards selection methods until there are no more variables
to add or delete, or the AIC increases.
From these results, we will select a model that both performs well while still making sense contextually.

## Model Validation

It is important for the model we build to be able to make meaningful predictions on independent data. In
order to validate our model, we will randomly divide our data into two smaller datasets (in 50/50 proportion):

1. A Training Dataset
This dataset will be used to build our model and perform any kind of model-building diagnostics.

2. A Test Dataset
Once the model is built on the training dataset, the test dataset will be used to evaluate the performance of
the model.

In order for the model to be validated, we must not be able to observe significant differences in the estimated
regression coefficients, significant predictors, model violations, and adjusted R-squared between the model
fit on the training dataset versus the test dataset.

## Potential Model Violations and Precautionary Diagnostics

In order to properly interpret the result of our linear regression model, we must ensure that the four assumptions
of linear regression have first been satisfied. We will evaluate each assumption through the use of
residual plots, given that two conditions are met:

**Condition 1: The conditional mean response is a single function of a linear combination of the
predictors.**

This condition is satisfied if the fitted values are randomly distributed around the identity function

**Condition 2. The conditional mean of each predictor is a linear function with another predictor.**

Using pairwise plots between the numerical predictors, if there are no distinct curved, periodic, or anything
other than a linear or random pattern, this condition is satisfied.
Once we verify that these two conditions are met, we will use residual plots to evaluate the assumptions of
linear regression.

**Assumption 1: Linearity of the Relationship**

We must not be able to observe any pattern beyond a linear relationship in the residual plots. If there are
no non-linear trends visible, we can conclude that there exists a linear relationship between the predictors
and the response.

**Assumption 2: Uncorrelated Errors**

The residuals should be randomly scattered, with no odd or separated clusters of residuals in the plots.

**Assumption 3: Common Error Variance (Homoscedasticity)**

The residuals must remain relatively equally spread out for any value of the predictors.

**Assumption 4: Normality of Errors**

A Normal QQ plot can be used to assess this assumption. If the residuals in the QQ plot lie along the
diagonal line, we can conclude that they are Normally distributed.
If any of these four assumptions are not satisfied, the model will not be as effective as we need to properly
explain the relationship between the predictors and the response.

## Data Introduction and Description

The data used in this analysis has primarily been gathered from the WHO and World Bank’s data libraries,
and is compiled into one dataframe. All data is reported for the year 2019.

### Response: Life Expectancy
[Life expectancy data was gathered from the WHO](https://www.who.int/data/gho/data/indicators/indicator-details/GHO/life-expectancy-at-birth-(years)), and reports life expectancy at birth for both sexes for each WHO member state.

### Predictor 1: Population
[Population data was gathered from the World Bank](https://data.worldbank.org/indicator/SP.POP.TOTL?end=2020&start=2018), and reports the total population of each UN member state.

### Predictor 2: Alcohol Consumption
[Alcohol consumption data was gathered from the WHO](https://www.who.int/data/gho/data/themes/topics/topic-details/GHO/levels-of-consumption), and reports levels of total alcohol consumption reported per capita for each WHO member state.

### Predictor 3: GDP
[GDP data was gathered from the World Bank](https://data.worldbank.org/indicator/NY.GDP.PCAP.CD), and reports countries’ GDP per capita in current US dollars.

### Predictor 4: Education
Education is measured in mean years of schooling of a country’s population aged 25 years or older. [This data was gathered from the World Bank.](https://tcdata360.worldbank.org/indicators/h22a4bb2b?country=BRA&indicator=41393&viz=line_chart&years=2017,2019)

### Predictor 5: Development Status
Development status data was retrieved from a 2018 open-source dataset titled [“Life Expectancy (WHO)”](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who), which is a collection of data supplied by the WHO and United Nations.

## Numerical and Visual Summaries

<p align="center">
  <img src="images/f2.jpg" width="80%" height="80%">
</p>
