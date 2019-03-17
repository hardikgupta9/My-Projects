# Homework 1

### Question 1
The question talks about a picture that produces a better apples-to-apples comparison. There are several variables that might affect the rent of a building namely: cluster, age, renovated, class, amenities, net, employment growth in area.
To further group this data we can conjecture that:
1) For a particular building accounting for the cluster, we can account for amenities, average rent and employment growth in that area. And since there are quite a lot of values of cluster we’ll take it on x-axis.
2) For a particular building accounting for the class, we can account for age and renovation criteria since overall quality of the building is evaluated by class variable. Thus we will prepare graph for every class. 
3) Also we know that the rent might become biased based on whether the rent includes utility cost or not thus we will take the net=1 buildings separately and net=0 in another graph. 

And we have the following output

![]("My-Projects/Qs_1_graph_HG.png")
![]("My-Projects/1_A1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")

#### Conclusion: 

Based on the 12 graphs above, We can see there are significant points in ggplots that represent the green building receiving rent less than normal buildings and also close to the mean rent of the cluster. Although in some cases such as class B cases there is more possibility of higher rent recovery from green buildings. Thus we cannot confidently conclude that the expectation of rent covered from a green building would be more than that of a normal building without any further information about the proposed building. Hence its uncertain whether investing in a green building will be worth it or not. 

### Question 2

#### Part (a) 

Since radiologists did not see the same set of patients, We will first benchmark our risk factors associated with the patients. For this we 
run logit regression model for each of the subset ( based on individual radiologists) to find out their propoensity to recall a patient 
given various factors ( history, age, density etc.). And we run logit regression of recall over those. Now we will have 5 different regression
results based on each radiologist's perception of risk. Now we calculate the propensity to recall for all patients for each radiologist's 
risk perception. And the recall probability by each radiologist for all the patients have been plotted in the box-plot below. 


![]("My-Projects/test1.PNG")

The above image clearly indicates that Radiologist89 is more conservative in recalling same set of patients.

#### Part (b)

We have taken the null model (from part (a))  where the radiologist percieves variables history , density, symptoms, menopause and age as
important factor and attach weight as given below. 

![]("My-Projects/test1.PNG")


However, we see from the model confusion matrix (explained below) that the above model is not efficient in fetching the information about the risk

![]("My-Projects/test1.PNG")

Error is 8.1%.& TPR is 0% & FPR is 2.6% & FDR is 100%. 

![]("My-Projects/test1.PNG")

Error is 5.1% & TPR is 11.53% & FPR is 2.3% & FDR is 85.7%

This model might look accurate However looking at the TPR, FPR and FDR, we can conclude that the model compromises a lot on sensitivity,
specificity and precision.

Now we propose a new model where the radiologist percieves recall(previous mammograms), history, density and symptoms as
important factor and attach weight as given below.

![]("My-Projects/test1.PNG")

However, we see from the model confusion matrix (explained below) that the above model looks more efficient in fetching the information about the risk

![]("My-Projects/test1.PNG")

Error is 16.24%.& TPR is 55.55% & FPR is 14.5% & FDR is 81%

![]("My-Projects/test1.PNG")

Error is 13.8%. & TPR is 61.5% & FPR is 12.9% & FDR is 86%

This model might look slightly inaccurate when compared to the null model. However looking at the TPR, FPR and FDR, we can conclude that the model compensates on sensitivity,
specificity and precision.

#### Conclusion

Thus

### Question 3

Started with segregating the data into two datasets with two different trims (trim = 350 and trim = 65 AMG). Have run K-nearest-neighbours, made predictions and calculated out of sample RMSE for many different values of K and plotted the required results. 

![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")

##### Optimal k = 68 for trim 350

![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")

#### Conclusion: 
The dataset with trim = 350 yields a larger optimal value of k because it has more observations than the dataset with trim = 65 AMG. The former has 416 observations while the latter has 292 observations. The optimal value of k is 68 for trim = 350 while the optimal value of k for trim = 65 AMG is 11, at least for the random sample that was drawn for this case.

#### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
