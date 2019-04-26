# Homework 4

### Question 1

We need to run both PCA and a clustering algorithm or any transformation thereof.

We plot the correlation between the 11 chemical components.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_1.png)

We see high positive correlation between free sulphur dioxide and total sulphur dioxide as expected; high positive correlation between residual sugar and density and also between residual sugar and total sulphur dioxide; high negative correlation between density and alcohol.

##### Principal Component Analysis (PCA)

We start with PCA. We use scaled data. 

PC1 explains 27.5% of the variation and PC2 explains 22.7% while PC3 explains another 14% of the total proportion of the variance. It is more informative to plot the PVE of each principal component (i.e. a scree plot) and the cumulative PVE of each principal component. As per the elbow plot on the left hand side, it seems optimal to consider the first four principal components. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_2.png)

We graph the scores corresponding to each of the observation on to the axes with PC1 and PC2. Similarly, we graph the scores corresponding to each of the observation on to different combinations of the first four PCs.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_3.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_4.png)

On the whole, observations belonging to the same colour (red and white) tend to lie near each other in this low-dimensional space and tend to have similar values on the first few principal component score vectors. This indicates that wines with the same colour do have similar chemical compositions. However, when we consider PCs explaining lesser proportion of the variance, the difference between red and white wines becomes slightly indistinct.

We know consider the quality of the wine.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_5.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_6.png)

We could now consider the case where we define the low quality wines to be wines with a rating of 6 to 10 and the high quality wines to be those with a rating of 1 to 5. The difference is slightly more visible.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_7.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_8.png)

On the whole, as can be seen, it is difficult to separate the observations based on the quality of wine that is scaled from 1 to 10. Clear and natural clusters fail to emerge as observed from the graphs. The different quality wines simply overlap each other when plotted against the first few principal components. It is hard to distinguish the lower quality from the high quality (after we defined low quality as being wines rated from 6 to 10 and high with ratings of 1 to 5).

##### K-means (without PCA and with PCA)

We commence with the elbow plot in order to determine the optimal number of clusters to be considered. We also consider the gap statistic and the average silhouette method in order to determine the optimal number of clusters.

We consider the entire dataset and scale it.

The optimal number of clusters as per the elbow plot seems to be k = 4 or k = 5.
The optimal number of clusters as per the gap statistic method is k = 5.
The optimal number of clusters as per the average silhouette method is k = 2.

The graphs are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_9.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_10.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_11.png)

We run the k-means algorithm with k = 4 and k = 2 which are the optimal number of clusters as per the elbow plot and the average silhouette method.

The graphs look as shown below:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_12.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_13.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_14.png)

When k = 4 is considered:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_15.png)

0.2 percent of the red wines are in cluster 1; 40 percent of red wines in cluster 2; 57 percent of red wines are in cluster 3; and 2.5% in cluster 4. 

38% of the white wines are in cluster 1; 1 percent of white wines in cluster 2; another 2% in cluster 3 and 59% of the total wines in cluster 4

Proportion of red and white wines in each cluster:

Cluster 1 comprises 99.7% of white wines and a mere 0.3% of red wines
CLuster 2 consists of 7.1% of white wines and 92.9% of red wines
CLuster 3 consists of 8.9% of white wines and 91.9% of red wines
Cluster 4 comprises 98.6% of white wines and a mere 1.4% of red wines

When k = 2 is considered:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_16.png)

1.5 percent of the red wines are in cluster 1 and the remaining 98.5% percent of red wines in cluster 2.

98.6% of the white wines are in cluster 1 and the remaining 1.4% percent of red wines in cluster 2.

Proportion of red and white wines in each cluster:

Cluster 1 comprises 99.5% of white wines and a mere 0.5% of red wines
Cluster 2 consists of 4.1% of white wines and 95.9% of red wines

##### Splitting the data into train and test sets in a way to ensure that the distribution of wines according to colour are approximately equivalent in the train and test data sets and we scale the data as well.

We repeat the same procedure as above in order to determine the optimal number of clusters.

The optimal number of clusters as per the elbow plot seems to be k = 4 or k = 5.
The optimal number of clusters as per the gap statistic method is k = 5.
The optimal number of clusters as per the average silhouette method is k = 3.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_17.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_18.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_19.png)

We consider the case with k = 4:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_20.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_21.png)

We then use the established k-means loadings and project it on to the test data. 

We get the following results:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_22.png)

97.4% of the red wines are in cluster 1 and cluster 2 for the testing data and approximately the same proportion of the red wines are contained in cluster 1 and cluster 2 for the training data.

##### PCA and K-means

We first use PCA and determine the optimal number of principal components to be considered for k-means.

It is more informative to plot the PVE of each principal component (i.e. a scree plot) and the cumulative PVE of each principal component. As per the elbow plot on the left hand side, it seems optimal to consider the first five principal components. After computing this, we run k-means on the first five principal components and learn that the optimal number of clusters seems to be either k = 4 or k = 5.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_23.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_24.png)

When k = 4 and we consider training data, the results are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_25.png)

When k = 4 and we consider training data, the results are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_26.png)

Clusters 1 and 3 represent 97.2% of the red wines in the training set whereas Clusters 2 and 4 represent 96.9% of the white wines in the training set.

Clusters 1 and 3 represent 89.3% of the red wines in the testing set whereas Clusters 2 and 4 represent 73.3% of the white wines in the test set (assuming that the same pattern should hold for the test data).

Only K-means (without PCA) performed better on the test set compared to the case where we considered K-means along with PCA.

Concern: We have considered only one sample and did not draw different combinations of training and test datasets.

##### Agglomerative Hierarchical Clustering

We will not be able to consider the results of hierarchical clustering on the test dataset. Therefore, we consider the case without PCA and with PCA.

We used agnes instead of hclust since we can compute the agglomerative coefficient and see which method has coefficient closer to 1 and thus has a stronger clustering structure. We learnt that agglomerative coefficients for different methods under agnes were as follows:

Agglomerative coefficient using the method "complete" = 0.9757232
Agglomerative coefficient using the method "single" = 0.9564608
Agglomerative coefficient using the method "average" = 0.9686528
Agglomerative coefficient using the method "ward" = 0.996168 <- we use this and the dendrogram looks as shown under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_27.png)

We certainly can prune the tree and in order to know the optimal number of clusters, we resort to using the elbow plot, the average silhouette method and the graph displaying the gap statistics for different clusters. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_28.png)

The optimal number of clusters as per the elbow plot seems to be k = 4.
The optimal number of clusters as per the gap statistic method is k = 6.
The optimal number of clusters as per the average silhouette method is k = 2.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_29.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_30.png)

We use k = 4 and obtain the following results:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_31.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_32.png)

55% percent of the red wines are in cluster 1; 44 percent of red wines in cluster 2; 1% percent of red wines are in cluster 3; 0.2% in cluster 4.
1% of the white wines are in cluster 1; 2 percent of white wines in cluster 2; another 74% in cluster 3 and 23% of the total wines in cluster 4.

Proportion of red and white wines in each cluster:

Cluster 1 comprises 6.4% of white wines and 93.6% of red wines
Cluster 2 consists of 13% of white wines and 87% of red wines
Cluster 3 consists of 99.5% of white wines and 0.5% of red wines
Cluster 4 comprises 99.7% of white wines and a mere 0.3% of red wines

Clusters 1 and 2 represent 98.7% of the red wines in the training set whereas Clusters 3 and 4 represent 96.7% of the white wines in the training set.

The results are similar to what we obtained using k-means without PCA on the entire dataset with no. of clusters k = 4.

##### Agglomerative Hierarchical Clustering with PCA

We use the same principal components as done in the beginning of this section and consider up to 4 principal components. We now run the hierarchical clustering algorithm on these four principal components rather than considering all 11 chemical components. The optimal number of clusters as per the elbow plot seems to be k = 4 or k = 5.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_29.png)

We consider k = 4. We simply use the method defined earlier when we started off with hierarchical clustering. The results are as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_30.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_1_31.png)

Clusters 1 and 2 represent 96.2% of the red wines in the training set whereas Clusters 3 and 4 represent 98.2% of the white wines in the training set

Only agglomerative hierarchical clustering (without PCA) performed slightly better on the dataset compared to the case where we considered hierarchical along with PCA.

Conclusion: There is not much of a stark difference between using PCA and not using PCA and simply using the clustering methods. Only PCA does not prove to be extremely useful in order to distinguish between the red and white wines. The clustering methods were able to perform the task better. Also there is not much difference between k-means and hierarchical clustering. However, we were able to run k-means on the test data. There is not much of a stark difference between using PCA and not using PCA and simply using the clustering methods

If we divide the wines into low quality and high quality, then clustering methods should be able to distinguish between the low and high quality wines. However, it will be harder to distinguish between each category of wine just by using the unsupervised information contained in the chemical properties. But broad clusters should be possible to obtain.


### Question 2

Our aim is to identify broad market segments in order to provide useful insights into the customer-base and thereby aid in better positioning of the brand

Method 1: We commence with scaling the data and running PCA on all the 36 variables. When we plot the PVE of each principal component (i.e. a scree plot) and the cumulative PVE of each principal component, we can conclude that 12 seems to be the optimal number of principal components to be considered to explain a significant variation.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_1.png)

However, we try to consider the first two principal components that explain 15.2% of the total proportion of the variance. We graph the all observations on a plot with PC1 on the x-axis and PC2 on the y-axis. This is shown as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_2.png)

We see that most of the observations are very closely clustered around the top & top-left indicating large positive loadings on the second component and low to large negative loadings on the first component, while some are clustered near the bottom indicating large negative loadings on the second principal component and others are clustered around the right indication large positive loading on the first principal component. Therefore, we deep dive into how these principal components are related with the original variables.

We learn the following:

Six Categories related most positively with the first component are "religion", "sports_fandom", "parenting", "food", "school", "family".

Six Categories most negatively associated with the first component are "college_uni", "fashion", "cooking", "shopping", "chatter", "photo_sharing".

Six Categories related most positively with the second component are "chatter", "politics", "travel", "shopping", "automotive", "current_events".

Six Categories most negatively associated with the second component are "beauty", "fashion", "cooking", "outdoors", "personal_fitness", "health_nutrition".

These can be identified by closely observing the graph displaying the contribution of each of these variables and is shown as under:

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_3.png)

##### Conclusion: Therefore, two clusters can be identified:

1) One which includes "family", "school", "parenting", "food", "religion", etc. These represent more of familial and core values and could be associated with users in their mid 30s or older.

2) Second which includes "beauty", "fashion", "personal_fitness", "health_nutrition", etc. These are more of self-care related interests, something more popular amongst the younger generation.

Alternative 2: We now try to run k-means on scaled data and consider all the 36 variables. We commence by scaling the data, followed by plotting the elbow curve and graphing the gap statistics against each of the different values of k. We learn that the optimal number of clusters as shown by the elbow is k = 7 or k = 8. Similarly, the optimal number of clusters as per our gap statistics method is k = 10.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_4.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_5.png)

We run k-means with k = 7 and k = 10. Be it k = 7 or k = 10, the clusters are not very distinct. We extract the cluster centers as can be seen from the graphs below.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_6.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_7.png)

Since difficult to locate the different clusters, we compute the cluster center and try to observe any patterns in the clusters, if any. We consider k = 7 since it is optimal as per the elbow plot. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_2_8.png)

A few patterns can be noticed:

Cluster 1: People under cluster 1 tweet about current events, shopping, art, tv, films, dating, business. 

Cluster 2: We fail to notice any categories in particular that interest this group.

Cluster 3: This group tweets frequently about photo sharing, beauty, fashion, cooking, etc indicating that this seems to be a younger lot of all the customers.

Cluster 4: People in this group seem to be interested in travel, politics, news, computers, automotive indicating that it primarily comprises men who could be 30 years or older.

Cluster 5: This group consists of health conscious people tweeting frequently about health and nutrition, personal fitness and outdoors.

Cluster 6: People in this group seem to be inclined towards tweeting about family, religion, food, parenting, schooling, etc. suggesting that it comprises of the older lot of the entire customer base.

Cluster 7: This group may consist of university students that are primarily into tweeting about colleges and universities, online gaming, sports, etc.

### Question 3

We have multiple baskets of grocery items and will find some interesting association rules using the items in these baskets.

After transforming the data into a readable transaction format accepted by arules package, we summarize the data. Below is the graph to briefly summarise 20 most frequently repeated items. 

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_3_1.png)

Few points to note from the summary:
1) Presence of 169 different items in all the transactions combined.
2) Whole milk, other vegetables, rolls/buns are the most frequently bought items.
3) 2159 out of 9835 transactions have only one item in the cart.
4) 75% transactions have less than 6 items in the cart.
5) 25% transactions have less than 2 items in the cart.
6) 50% transactions have less than 3 items in the cart.

We then run the apriori algorithm to get the rules from these transactions. In order to select threshold for support, let us consider itemsets which appear atleast in 10 baskets out of 9835. That converts to a support threshold of (10/9835) ~ 0.001. Threshold for confidence will be fixed at 0.4 to ensure that a min of 4 baskets that contain X also have Y in them(for the rule X -> Y). .
The algorithm created 8967 rules. 
Evidently we can say that rules with high lift have low support.

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_3_2.png)

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_3_3.png)

Now observing the two-key plot for studying the variations in rules with size of itemset: 

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_3_4.png)

All the rules of higher order have low support and itemsets of lower order have low confidence. Lets examine these rules.

Association rules

![](https://github.com/hardikgupta9/My-Projects/blob/master/4_3_5.png)

The inference derived from the graph makes sense:

1)There is a high probability for people to red/blush wine if they buy bottled beer and liquor as people with tend to take liquor for get togethers and these should include a variety of liquor.

2)Buying soda and popcorn has a high association with salty snack since these things will say a lot about consumer’s propensity for a movie or snacking.

3)Processed cheese and white bread has a high association with buying ham since a consumer making a purchase for breakfast will have this basket.

4)Some rules are obvious like buying flour and baking powder has a high association with sugar for a consumer interested in baking cakes etc will have this basket. 
 
### Submitted by: Hardik Gupta (hg8675) and Khushboo R Thakkar (kt24992)
