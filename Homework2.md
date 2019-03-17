# Homework 2

### Question 1

#### Part (a)
Referring to the starter script here "saratoga_lm.R", we have taken the medium2 model as the medium model to benchmark the performance of the hand build model. 

The medium model takes into account lotSize, age, livingArea, pctCollege, bedrooms, fireplaces, bathrooms, rooms, heating, fuel and  centralAir.The coefficients and weightage for the medium model has been described as following:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_m.PNG)

The hand-build model takes into account lotSize, age,landValue, livingArea, pctCollege, bedrooms, fireplaces, bathrooms, rooms, heating, fuel,waterfront, newConstruction,  centralAir and interaction terms between livingArea and bedroom AND livingarea and bathroom .The coefficients of the hand-build model has been described as below:


![](https://github.com/hardikgupta9/My-Projects/blob/master/Coeff_Q1_a_h.PNG)

Comparing the average Root mean square error for both the medium and hand-build model below:

RMSE over one regression: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/RMSE.PNG)

Average RMSE over 100 regressions:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Mean_RMSE.PNG)

We can see that the hand build model is much more efficient than the given medium model in the original script.

#### Part (b)

Referring to part (a) we could see that the hand build model is more efficient than the medium2 model from the original script. Thus we will compare the KNN regression model with the hand build model here.

Comparing the average Root mean square error for both the KNN model and hand-build model below:

RMSE over one regression: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/KNN_RMSE.PNG)

Average RMSE over 100 regressions:

![](https://github.com/hardikgupta9/My-Projects/blob/master/KNN_RMSE_mean.PNG)

Thus we can see that the average RMSE for the KNN model is still more than the hand build model in the part (a). 

![](https://github.com/hardikgupta9/My-Projects/blob/master/Qs_1_graph_HG.png)

Based on the above graph we can see that the mean RMSE is minimum in KNN regression if the value of K is chosen below and around k=10.

#### Conclusion: 


### Question 2

#### Part (a) 

Since radiologists did not see the same set of patients, We will first benchmark our risk factors associated with the patients. For this we 
run logit regression model for each of the subset ( based on individual radiologists) to find out their propoensity to recall a patient 
given various factors ( history, age, density etc.). And we run logit regression of recall over those. Now we will have 5 different regression
results based on each radiologist's perception of risk. Now we calculate the propensity to recall for all patients for each radiologist's 
risk perception. And the recall probability by each radiologist for all the patients have been plotted in the box-plot below. 


![](https://github.com/hardikgupta9/My-Projects/blob/master/Q2_plot.png)

The above image clearly indicates that Radiologist89 is more conservative in recalling same set of patients.

#### Part (b)

We have taken the null model (from part (a))  where the radiologist percieves variables history , density, symptoms, menopause and age as important factor and attach weight as given below. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/Old_coef.PNG)


However, we see from the model confusion matrix (explained below) that the above model is not efficient in fetching the information about the risk

![](https://github.com/hardikgupta9/My-Projects/blob/master/Confusion_out_1.PNG)

Out sample: Error is 8.1%.& TPR is 0% & FPR is 2.6% & FDR is 100%. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/Confusion_in_1.PNG)

In sample: Error is 5.1% & TPR is 11.53% & FPR is 2.3% & FDR is 85.7%

This model might look accurate However looking at the TPR, FPR and FDR, we can conclude that the model compromises a lot on sensitivity,
specificity and precision.

Now we propose a new model where the radiologist percieves recall(previous mammograms), history, density and symptoms as
important factor and attach weight as given below.

![](https://github.com/hardikgupta9/My-Projects/blob/master/Coefficients_part2.PNG)

However, we see from the model confusion matrix (explained below) that the above model looks more efficient in fetching the information about the risk

![](https://github.com/hardikgupta9/My-Projects/blob/master/Confusion_out_2.PNG)

Out sample: Error is 16.24%.& TPR is 55.55% & FPR is 14.5% & FDR is 81%

![](https://github.com/hardikgupta9/My-Projects/blob/master/Confusion_in_2.PNG)

In sample: Error is 13.8%. & TPR is 61.5% & FPR is 12.9% & FDR is 86%

This model might look slightly inaccurate when compared to the null model. However looking at the TPR, FPR and FDR, we can conclude that the model compensates on sensitivity,
specificity and precision.

#### Conclusion

Thus, from the coefficients obtained from logit regression in null model and proposed model, we need to see that the radiologist is attaching a lot of weight to the age factor, which we don't find in the efficient model to add significance. Also we could see that the recalled patient have a very high weighage of developing cancer. Thus the radiologists should weight it higher if someone has been recalled again for the mammography. Also in the proposed model the weightage of density and symptoms has also reduced. However the weightage of history almost similar. Thus we will reason that the coefficient of the proposed model tell us the weights attached to the different factors for a patient.

### Question 3

![](https://github.com/hardikgupta9/My-Projects/blob/master/1_Confusion_matrix.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/Qs3Graph1.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/2_Confusion_matrix.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/Qs3Graph2.png)


#### Conclusion: 
The dataset with trim = 350 yields a larger optimal value of k because it has more observations than the dataset with trim = 65 AMG. The former has 416 observations while the latter has 292 observations. The optimal value of k is 68 for trim = 350 while the optimal value of k for trim = 65 AMG is 11, at least for the random sample that was drawn for this case.

#### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
