# Project - ECO 395M

### Abstract

We try to determine the relationship between a measure of air pollution and different measures of economic activity. We collect data for the period 2010-2016 for 176 different countries. We analyse the data using fixed-effects estimator and infer that that pollution increases with economic growth in the early stages of development. However, beyond a certain level of development, the trend reverses, and economic growth improves environmental conditions by creating the resources to do so.


### Introduction

Our aim is to study the relationship that exists between air pollution and economic activity of a country. 
As an economy grows, so does pollution. With the rapid development of industrialization in the last two decades in developing countries, 
especially in Beijing, the air pollution has progressed to an astonishing level. In absence of additional and more stringent
policies, increasing economic activity and energy demand may lead to a significant increase in global emissions of air 
pollutants. We try to study the trade-off between attaining a level of economic growth and controlling air pollution. 
Increasing economic activity leads to increasing pollution. However, increase in GDP means increase in resources to tackle air 
pollution. Studying the relationship between economic activity and the costs related to air pollution is crucial from the 
policy making perspective. A government may not want to focus only on achieving a certain level of development but may also 
want to take into account the pressure being put on the resources. By focusing only on the economic development, it may hamper
the social and economic development of its country by incurring large economic costs associated with different types of 
pollution and fewer resources in the long run. We try to ascertain the relationship between an air pollution index and a
few economic variables such as GDP, GDP per capita, contribution of the manufacturing sector to a country’s GDP, extent of the
agricultural land while controlling for area under forest, and a few characteristics of each country such as total area, 
population density, length of coastline, number of smokers, etc. 

#### Data Collection

For calculating API, we considered different variables that might have a significant impact on the API which are listed as follows:
1. Share of people who smoke daily
2. Percentage of population living in slum
3. Population density
4. Percentage of people living below poverty
5. Rural population 
6. GDP per capita
7. Fossil fuel consumption
8. Renewable energy consumption
9. Manufacturing Value added
10. R&D
11. Length of Coastline
12. Area of Country
13. Population density
14. Forest Area
15. Area under agriculture
16. Average precipitation by country
17. Average altitude by country
18. Total GDP (in USD)

The data source for each variable has been indicated in the table below

| Variable name     | Link         |
| ------------- |:-------------:|
|Share of people who smoke daily (country wise and year     | https://ourworldindata.org/smoking|
| Population% living in slums    | https://data.worldbank.org/indicator/EN.POP.SLUM.UR.ZS?view=chart | 
| Population density | https://data.worldbank.org/indicator/EN.POP.DNST?year_high_desc=false     |
| BPL | https://data.worldbank.org/topic/poverty?locations=US |
| Rural Population | https://data.worldbank.org/indicator/sp.rur.totl.zs |
|GDP per capita | https://data.worldbank.org/indicator/NY.GDP.PCAP.CD?view=chart| 
| Fossil fuel consumption | https://ourworldindata.org/fossil-fuels |
| Renewable energy consumption | https://data.worldbank.org/indicator/eg.fec.rnew.zs |
| Manufacturing Value added | https://data.worldbank.org/indicator/nv.ind.manf.zs |
| R&D | https://data.worldbank.org/topic/science-and-technology |
| Length of Coastline | http://chartsbin.com/view/ofv |
| Area of Country | https://data.worldbank.org/indicator/ag.lnd.totl.k2 |
| Population density | https://data.worldbank.org/indicator/EN.POP.DNST?year_high_desc=false|
| Forest Area | https://data.worldbank.org/indicator/ag.lnd.frst.zs |
| Area under agriculture | https://data.worldbank.org/indicator/ag.lnd.agri.zs |
| Average precipitation by country | https://data.worldbank.org/indicator/AG.LND.PRCP.MM?year_high_desc=true |
| Average altitude by country | https://www.atlasbig.com/en/countries-average-elevation |
| Total GDP (in USD) | https://data.worldbank.org/indicator/ny.gdp.mktp.cd |

The data in the above table, extracted from world bank website includes different related data. We identify a row which contains the relevant data and the columns which contain the data for the years 2001-2016. 
Regarding other datasets for other variables and indicators (not taken from worldbank website), there are two subtypes in it:

a) Time-invariant variables such as coastal length

b) Time-varying variables such as precipitation

We resorted to R in order to extract country-wise and year-wise data for each of the variables from the raw CSV files that were downloaded from different websites. We generated a CSV file through R which extracted a list of countries and the value of the variable of interest for each year. 

We repeated this process for each variable. We later on, compiled these CSV files into one and used VLookup for assigning the values of different variables as per each country and for each year. 

The next step was to omit variables with the most number of missing values. Having done this, we also omitted years for which data was not available for most countries. We narrowed down to the period 2010-2016. We also manually entered values for quite a few countries for variables such as land area, length of coastline, elevation, etc. 

The last step was to ensure that the dataset is a balanced dataset as we intended to run panel data models for balanced panels. A balanced panel is a panel dataset wherein we have observations for each panel/individual for the same period. We eliminated countries like Bermuda, Chad, Eritrea, Somalia, Mongolia that did not have data for all the years from 2010 to 2016. We ended up with a balance panel of N = 176 countries and t = 7 years. The final data file has been provided. We can also provide the raw data files if required. 

#### Methodology:

##### Graphical Analysis

We commence by plotting the time-varying variables in our dataset to try and draw inference about the type of relationship between the air pollution index (our dependent variable) and any of the time-varying regressors. 

The below is a plot of the value added by the manufacturing sector as a percentage of GDP for each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/manu.gif)

Most countries have a contribution of less than 20% from the manufacturing sector. A clear linear relationship is not visible.  Countries with GDP per capita above 35K seem to have the same contribution from their manufacturing sectors as lower income countries but their contribution is associated with a much lower value of the air pollution index as compared to the lower income countries. This could mean that the manufacturing sector of the higher income countries are slightly more efficient and less polluting.

The below is a plot of the area under agriculture for each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/agriland.gif)

This is an extremely scattered plot. Most countries, with income per capita greater than 35K, have land under agriculture below 60%. More or less the same relationship holds as that mentioned for the manufacturing sector. 

Now we consider a plot of the area under forest for each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/forland.gif)

We can sort of see a nonlinear relationship between the area under forest and air pollution. It is like a convex to the origin curve where countries with less land under forest experience higher levels of air pollution and vice versa. 

Now we consider a plot of GDP per capita for each country against the air pollution index for each of the years from 2010 to 2016. We chose to emphasise on GDP per capita in the earlier graphs by classifying it through the colour attribute and population density through the size attribute. We continue classifying GDP per capita through colour (even though it is on the x-axis) to maintain the same trend and theme.  

![](https://github.com/hardikgupta9/My-Projects/blob/master/gdppc.gif)

The trend is difficult to visualize and is extremely scattered. However, we do see quite a few countries with high income associated with lower levels of air pollution. But as we move to lower income countries, we cannot say with certainty that on an average, low income countries are associated with higher levels of pollution. So the negative relationship between GDP per capita and air pollution becomes weak. 

The below is a plot of population density for each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/popden.gif)

It seems to be difficult to identify any pattern here. Most countries have population density below 500 and exhibit varying levels of air pollution. Therefore, difficulty to generalize a pattern here. 

The below is a plot of renewable energy consumed by each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/rencons.gif)

A lot of countries with high reliance on renewable energy display the same levels of air pollution as countries with lower levels of consumption of renewable energy. Therefore, it becomes crucial to consider the total energy produced from all sources (as that may draw a more complete and true picture) rather than just studying the consumption from renewable energy. 

Lastly, we consider rural population of each country against the air pollution index for each of the years from 2010 to 2016.

![](https://github.com/hardikgupta9/My-Projects/blob/master/ruralpop.gif)

If we ignore a few outliers, we could trace a positive relationship between countries with a higher proportion of the rural population and lower incomes to be associated with higher pollution levels on an average. 

#### Panel Data Analysis and Results

Given that our panel dataset is a balanced panel, we begin by deciding between estimating our model using a fixed-effects estimator or a random-effects estimator. Our data was compiled in the long format  and therefore, each row is one time point per subject. So each subject (country) will have data in multiple rows. Any variables that don’t change across time will have the same value in all the rows.
We have plotted the Air Pollution Index over the period in consideration for all the countries.


![](https://github.com/hardikgupta9/My-Projects/blob/master/API.png)

We run a simple model with all the independent variables (both time-varying and time-variant) using the fixed-effects and random-effects. The fixed effects model results in insignificant coefficients for all the time-invariant variables. 

The fixed effects estimator assumes that the variables that are fixed over time (constant for each panel) may be correlated with the time varying variables of the model. Use of the random effects model implies the additional orthogonality conditions—that the time-invariant regressors are not correlated with the time-varying regressors—and yields inference about the underlying population that is not conditional on the fixed effects in our sample.
In order to decide between fixed-effects and random-effects, we use the Hausman test with the null hypothesis that a random-effects model should be preferred against the alternate hypothesis that a fixed-effects model would be more appropriate. 
Results from running the fixed-effects model are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Table1.png)

Results from running the random-effects model are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Table2.png)

The p-value of the test is 0.02 (<0.05) and therefore we reject the alternative hypothesis and use fixed-effects. This is rather intuitional as we would not expect area under forest or agriculture to be uncorrelated with the total land area or length of the coastline. 

We proceed at evaluating different combinations of regressors under the fixed-effects model. 

We run several models (codes of which are listed in the RMD file). However, we choose a model that comprises time-varying regressors with significant coefficients and that has an overall significant F-statistic. We also take into account performance measures such as root mean squared error and R2. 

Note: R squared is not very informative in this case. In panel data analysis, reliance should be placed more on individual significance and overall significance of the model instead of R squared or adjusted R squared. Generally, R squared is low in cross sectional data as compared to time series data. In panel data due to heterogeneity of cross sections, it is not too high. Given that our data is more cross section dominant, R squared will be lower as compared to the case when panel data is more time dominant. 

The first few models considered displayed insignificant coefficients and a very low R-squared. The last model listed in the code exhibited all significant coefficients, and RMSE slightly lower than the multitude of models considered earlier (all models are not explained in the code but quite a few are listed). The final model took into account three regressors that varied with time i.e. Value added by the manufacturing sector (as a percentage of GDP), GDP per capita, and area under agriculture as a percentage of the total land area. The squared terms of the two variables except land under agriculture were considered. We were able to draw this inference based on the graphs shown earlier and the not so clear patterns that were identified. 

The model is as under: 

**fixedap8 = plm(api ~  poly(manu, 2) + poly(gdppc,2) + agriland, data = panelap, index = c("country", "year"), model = "within")**

We compute the cluster robust standard errors for this model and the results are as under: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/Table3.png)

This model had a fairly low RMSE combined with coefficients that were significant after taking into account the cluster robust standard errors. A few other variables had a high R squared but not all statistically significant coefficients. Model 7 considered in the codes had an RMSE of 2.29 compared to RMSE of 2.30 of this model but it did not have statistically significant coefficients. Hence, we decided to consider this model in order to draw inferences. 

#### Conclusion

* As seen through graphical analysis, variables like population density and renewable energy consumption levels fail to display any significant (linear or non-linear) relationship with the level of air pollution. Ideally or theoretically, we would expect air population to exhibit a positive relationship with population density assuming that higher density leads to more pressure on the resources. Similarly, a country relying more on wind or solar energy should have lower levels of air pollution. However, it may be the case that such countries may be producing and consuming lots of energy through conventional sources as well. Therefore, we could consider total energy consumption to identify better patterns. 
* From our model, we can see that increase in contribution by the manufacturing sector leads to higher levels of air pollution on an average but this positive relationship is weakened as the contribution increases. Overall, an increase in the manufacturing activity leads to higher levels of pollution on an average (holding all else fixed). This is in line with the EKC variation that posits that pollution increases with economic growth in the early stages of development. However, beyond a certain level of development, however, the trend reverses, and economic growth improves environmental conditions by creating the resources to do so.
* Due to a non-linear relationship with GDP per capita, same inference could be drawn as above. As GDP per capita increases initially, we see a decline in the levels of air pollution. However, as GDP per capita gets larger and larger, this decline falls. It could be due to the fact that as per capita income increases, we see a rise in private vehicles and an upgrade in lifestyle, more people smoking etc. 
* If the land under agriculture increases, the levels of air pollution may go down on an average (holding all else fixed). We did test for a two-way effect through agriculture. One being directly on air pollution and the other could be rise in GDP as land under cultivation increases and thereby air pollution would decrease. However, none of the interaction terms turned out to be significant. 

#### Limitations:

* We ended up evaluating a panel data as we wanted to study trends across countries. Also, focusing on one country did not seem to be feasible as we would have a smaller data set and increasing the frequency did not make sense as most of these variables change over a quarter or over a year. 
* We could have extracted the fixed effects for each country or created a dummy variable varying across panels and constant over time so as to be able to study the effects of land area, length of coastline etc but we would end up with 176 coefficients. 
* To overcome this, we can implement models like Hausman Taylor model that would explain and estimate the slope coefficients for time-invariant variables. However, due to paucity of time and knowledge, we were not able to successfully classify our variables into time-variant exogenous,  time-variant endogenous,  time-invariant exogenous and  time-invariant endogenous. 
* We get the same outcome when we consider countries with income per capita less than or equal to USD 50K. We could deep dive further by collecting more data and by running models for countries in different income groups. 



