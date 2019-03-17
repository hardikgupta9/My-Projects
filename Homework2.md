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


#### Part (a) 

We begin by part A where we need to approach the problem from the standpoint of regression. When all the independent variables were plotted against the number of shares or the natural logarithm of number of shares, no linear relationships were visible. On executing several multiple regression models, an R2 of only 3% was obtained. Therefore, it was justified to try KNN regression or a non-parametric approach for the above. The lowest overall error rate was achieved by taking into account all the independent variables (without any transformations) excluding url. The overall error rate was around 0.41 or 41% with the optimal k value being equal to 5 and averaging it over 10 samples (could not do beyond time since it took unusually long to execute the code). A little higher than what would be expected but this was the rate that we were able to achieve after considering quite a few models with different combinations of the regressors and also different transformations (like squared variables and interaction variables). 

The graph of the average estimate of the out-of-sample overall rate against the different values of k is shown as under: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/1_Confusion_matrix.png)

(Note: k values upto 1000 were considered, however, the model only shows the values starting from k = 5 and going upto k = 100 with increments of 5. The other k values did not display a lower overall error rate than k =  5 and hence only that has been reported.)

The confusion matrix for our model is as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Qs3Graph1.png)

As can be confirmed from the table above, the overall error rate = 0.4116534 and the true positive rate = 0.7896974 and the false positive rate = 0.6165394.

We now average the above quantities by running our model over 50 different subsamples of test and train data. On comparison with the null model, our model performed only slightly better. 

The average overall error rate (final model) = 0.4104275
The average true positive rate (final model) = 0.7993485
The average false positive rate (final model) = 0.6145434

The average overall error rate (null model) = 0.4929928

#### Part (b) 


Now we approach the problem by classifying the target variable and then implement a classification or a regression model.
We resort to using the KNN classification as we achieved slightly better results than the logistic regression. This and the case above might be because the data points are way too many and extremely scattered. This makes it harder to trace out any pattern and thereby fit a parametric model. However, the drawback with this classification would be that it will be extremely sensitive to the value of k. We may obtain a different optimal k every time we run the model.

The lowest overall error rate was achieved by taking into account all the independent variables (without any transformations) excluding url and two other variables (is_weekend and data_channel_is_socmed). The overall error rate was around 0.37 or 37% with the optimal k value being equal to 95 and averaging it over 5 samples (could not do beyond time since it took unusually long to execute the code). 

The graph of the average estimate of the out-of-sample overall rate against the different values of k is shown as under: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/2_Confusion_matrix.png)

The confusion matrix for our model is as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/Qs3Graph2.png)

As can be confirmed from the table above, the overall error rate = 0.3768445 and the true positive rate = 0.7386903 and the false positive rate = 0.4736482. The false positive rate has reduced substantially which is good and overall error rate is lower too. However, the true positive rate has declined.

We now average the above quantities by running our model over 50 different subsamples of test and train data. 

The average overall error rate (final model) = 0. 3746097
The average true positive rate (final model) = 0.5956410
The average false positive rate (final model) = 0.3455147

We even ran a logit model for the second part of the question but the results were more or less similar to the part A estimates. However, the average required quantities are as under and are slightly better than the KNN regression in part A:

The average overall error rate (final model) = 0.4067726
The average true positive rate (final model) = 0.8017085
The average false positive rate (final model) = 0.5964092

As can be seen, we prefer the KNN classification model over the logit model.

#### Conclusion

We expect the threshold first and regress approach to do better as we can classify the target variable into the required classes (using KNN classification) or target it to achieve a value between 0 and 1 (using a logit model). Earlier, due to overall high variable and a very large n, we were trying to predict the average number of shares for a given set of values for the independent variables and thus harder to get a reasonable overall error rate. Also, due to a large number of variables and large number of oobservations, we were unable to find any patterns between the regressand and the regressors and thus, difficult to implement a linear model. However, the true positive rate is higher for the KNN regression in part A as compared to the KNN classification in part B. The overall error rate and the false positive rate are lower for the KNN classification model. The importance of true positive rate over the false positive rate and vice versa depends on the aim of the study.


#### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
