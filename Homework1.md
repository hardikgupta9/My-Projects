# Homework 1

### Question 1
The question talks about a picture that produces a better apples-to-apples comparison. There are several variables that might affect the rent of a building namely: cluster, age, renovated, class, amenities, net, employment growth in area.
To further group this data we can conjecture that:
1) For a particular building accounting for the cluster, we can account for amenities, average rent and employment growth in that area. And since there are quite a lot of values of cluster we’ll take it on x-axis.
2) For a particular building accounting for the class, we can account for age and renovation criteria since overall quality of the building is evaluated by class variable. Thus we will prepare graph for every class. 
3) Also we know that the rent might become biased based on whether the rent includes utility cost or not thus we will take the net=1 buildings separately and net=0 in another graph. 

And we have the following output

![](My-Projects/2_HG2.png)
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
![]("My-Projects/test1.PNG")

#### Conclusion: 

Based on the 12 graphs above, We can see there are significant points in ggplots that represent the green building receiving rent less than normal buildings and also close to the mean rent of the cluster. Although in some cases such as class B cases there is more possibility of higher rent recovery from green buildings. Thus we cannot confidently conclude that the expectation of rent covered from a green building would be more than that of a normal building without any further information about the proposed building. Hence its uncertain whether investing in a green building will be worth it or not. 

### Question 2

The mean delay is calculated for each airport and is graphed as under:

![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")
![]("My-Projects/test1.PNG")

Mapping the airports with delay time in minutes greater than the overall average delay time. 

![]("My-Projects/test1.PNG")

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

