# Homework 3

### Question 1

#### Part (a)
We first used a null model by using seemingly relevant dependent variables such as: cluster_rent, size, age, renovated, class_a and amenities.

We calculated the Mean squared Error for the OLS regression and Ridge regression and got the following output for null model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/MSE_or_null.PNG)

We further explored the Mean squared Error for the Lasso regression which gave the following value for null model.

![](https://github.com/hardikgupta9/My-Projects/blob/master/mse_las_null.PNG)

To further improvise on the model we experimented with different combinations of variabes to calculate the expected rent per unit size. 
And we land up using variables such as: cluster_rent, size,  empl_gr, leasing_rate,  stories, age, renovated, class_a, class_b,
green_rating, amenities, total_dd_07 and Precipitation.

##### Proposed model
We use cluster_rent to contain the causal effect of locality on Rent. Moreover we use class_a and class_b which introduce us to the quality
of apartments we are calculating the rent for. We just use green_rating because consumers should not care for the type of green rating 
but they may care if the building is green rated or not thus we don't include LEED or EnergyStar. Age might have a good impact on the rent 
as old buildings tend to have lower rent , which also brings to the point of including renovated for this model. Also total_dd_07 includes
the total days where the tenant might save on the utility thus would not care about whether its about heating or cooling. 

We got the following coefficients for OLS regression on the proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/coef_ols.PNG)

We got the following coefficients for Ridge regression on the proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/coef_ridge.PNG)

We got the following coefficients for Lasso regression on the proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/coef_lasso.PNG	)

We calculated the Mean squared Error for the OLS regression and Ridge regression and got the following output for proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/MSE_best_or.PNG)

We further explored the Mean squared Error for the Lasso regression which gave the following value for proposed model.

![](https://github.com/hardikgupta9/My-Projects/blob/master/mse_las_best.PNG)

Thus the proposed model with least MSE will be following (OLS)

![](https://github.com/hardikgupta9/My-Projects/blob/master/coef_ols.PNG)

#### Part (b)
By looking at the coefficients we can say that the Rent per square foot increases by $ 0.635 with green rated building keeping other things constant.

#### Part (c)

We first propose the following interactive terms in our proposed model in part(a):

gr_clsa = gb$green_rating*gb$class_a

gr_clsb = gb$green_rating*gb$class_b

gr_clrent = gb$green_rating*gb$cluster_rent

gr_size = gb$green_rating*gb$size

gr_stories = gb$green_rating*gb$stories

gr_age = gb$green_rating*gb$age

After running the OLS regression we got the following MSE for the regression performed. Thus we can say that this model is equally efficient to the proposed model in part(a).

![](https://github.com/hardikgupta9/My-Projects/blob/master/mse_ols3.PNG)

Also the coefficients for the OLS performed are as following:

![](https://github.com/hardikgupta9/My-Projects/blob/master/coef3.PNG)

 Looking at the coefficients we can say that

1. Since size has a very less impact on Rent per square foot, Green rating effect on rent can be considered negligible for different size of buildings.

2. Green rating effect on rent is slightly different for different cluster, age and stories of building.

3. Green rating effect on rent is significantly different for different classes of buildings.


### Question 2

#### Answer 1
There would mostly be a high positive correlation if we run the variable “Crime” on “Police” as any authority in power would react to an increasing crime rate by hiring more cops. We would learn about correlation and not causation by this experiment as we will not be able to infer what causes what. Does hiring more cops lead to more crimes or does a rising crime rate lead to expanding the police force? We have a solid theoretical reason to believe that putting more police officers on the street will reduce crime, but it is also possible that crime could cause increase in the police force, in the sense that cities experiencing an increase in crime will hire more police officers. 

We could easily find a positive but misleading association between crime and police: the places with the most police officers have the worst crime problems. In order to break this circle of endogeneity, Steven Levitt identified variations in police presence that were not caused by variations in crime but due to elections. He found that police presence increased in mayoral election years but not in off-election years and this increase in the police force would be unrelated to the conventional crime rate. Similarly, the researchers, at the University of Pennsylvania, make use of the terrorism alert system in Washington, D.C. The city responds to high alert days for terrorism by putting more officers in certain areas of the city and we can assume that there is no relationship between street crime and the terrorism threat. Therefore, this boost in the police presence is unrelated to the conventional crime rate and hence, exogenous. In order to consider data from a few different cities, it is essential to identify a valid instrumental variable that has no independent effect on the crime rate, allowing the researcher to uncover the causal effect of the changes in the police force on the crimes in the city.

Alternatively, we could run some sort of a randomized experiment wherein we could randomly place cops in the streets of a city in different days and see what happens to the daily crime rate. But such an experiment is not feasible. 
(Also, different cities mean different places with different demographics and different social and economical and political characteristics and hence, different crime challenges. Ideally, it would also be essential to control for these differences.)


#### Answer 2

The researchers, at the University of Pennsylvania, used the terrorism alert system to break the circle of endogeneity to credibly estimate the causal effect of police on crime. They collected daily data on the crime rate in the city and were able to relate that to days in which there was a higher alert for potential terrorist attacks. During high-alert times, the police increase their presence on the streets of Washington, D.C. This increase is uncorrelated to the conventional crime rate and were thereby able to isolate the causal effect of police on crime. The researchers were able to recognize this natural experiment. (A natural experiment happens when random circumstances somehow create something approximating a randomized, controlled experiment.)

The results in Table 2 display regression results obtained by regressing the daily crime rate in D.C. against the terror alert level [1 = high (orange as mentioned in the podcast) and 0 = elevated (yellow)]. A dummy variable for each day of the week was also included to control for day effects. The alert level never dropped below elevated when the sample was collected but rose to orange on four occasions. The first column in the table does not control for public transportation (Metro) ridership. 

The coefficient on the alert level is statistically significant at the 5 percent level and indicates that on high-alert days, daily crimes decrease by an average of seven crimes per day (holding all else fixed). By including the natural logarithm of the midday ridership of Metro, the coefficient on the alert level is still statistically significant at the 5 percent level and the daily crimes decrease, on an average, by six crimes a day (holding all else fixed). Thus, the level of crime decreases on high alert days in the city because of greater police presence on the streets. Interestingly, an increased Metro ridership is correlated with an increase in crime. The increase, however, is very small—a 10 percent increase in Metro ridership increases the number of crimes by only 1.7 per day on average (holding all else fixed). The R2 increases slightly from 14% to 17% after controlling for the ridership.



#### Answer 3

The researchers were of the opinion that tourism could be reduced on high alert days and therefore, result in fewer crimes. If their hypothesis is true, then lower crime rates on high alert days could not be attributed to the increased police force on the streets. To test whether fewer visitors could explain the results (as seen in the first column of Table 2), daily data on public transportation ridership was obtained assuming that midday Metro ridership would serve as a good proxy for tourism. Thus, in order to investigate the effect of tourism systematically, the natural logarithm of midday Metro ridership was directly included in the regression and this way tourist levels were controlled for.

#### Answer 4

Each district in Washington, D.C. could have its own peculiar crime pattern because of different geographies, demographics, income, spending patterns, etc. Each of these districts might therefore, have very different crime rates. To control for these differences, interactions between locations and high alert days were included in the regression model and the results were displayed in Table 4. Most prominent government agencies and institutions were located in District 1. During periods of high alert, crime in District 1 decreases by 2.62 crimes per day on an average (holding all else fixed). Again, this was justified as most of the potential terrorists’ targets in D.C. are in District 1 and therefore, more cops are most likely to be deployed in this district. The D.C. police had stated to the researchers that regular patrols were not reduced in any other district during high alert days simply due to high concentration of cops in District 1. The police presence was not decreased in other districts. Had this been the case, then levels of crime would have expected to increase in these other districts during high alert days. As expected, crime also decreases in the other districts, by an average of 0.571 crimes per day (holding rest fixed), but this effect is not statistically significant (test statistic of -1.25). 

### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
