# Homework 3

### Question 1

#### Part (a)
We first used a null model by using seemingly relevant dependent variables such as: cluster_rent, size, age, renovated, class_a and amenities.

We calculated the Mean squared Error for the OLS regression and Ridge regression and got the following output for null model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/__.PNG)

We further explored the Mean squared Error for the Lasso regression which gave the following value for null model.

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

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

![](https://github.com/hardikgupta9/My-Projects/blob/master/__.PNG)

We got the following coefficients for Ridge regression on the proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/__.PNG)

We got the following coefficients for Lasso regression on the proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/__.PNG)

We calculated the Mean squared Error for the OLS regression and Ridge regression and got the following output for proposed model:

![](https://github.com/hardikgupta9/My-Projects/blob/master/__.PNG)

We further explored the Mean squared Error for the Lasso regression which gave the following value for proposed model.

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

Thus the proposed model with least MSE will be following (OLS)

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

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

After running the OLS regression we got the following MSE for the regression performed. Thus we can say that this model is equally efficient
to the proposed model in part(a).

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

Also the coefficients for the OLS performed are as following:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

 Looking at the coefficients we can say that

1. Green rating effect on rent is same for different size of buildings

2. Green rating effect on rent is slightly different for different cluster, age and stories of building.

3. Green rating effect on rent is significantly different for different classes of buildings.



### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
