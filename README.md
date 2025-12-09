# Machine-Learning-2025

## Audience Decode

### Group Members:

- Zygimantas Kazlauskas (322271)
- Kottage Don Chiara (315161)
- Elvin Magaia (315431)
- Gabija Baltrunaite (314771)

## Introduction

This project analyzes how users interact with content on a large streaming platform. By looking at data like ratings, timestamps, and viewing habits, the goal is to understand how people watch different genres, how their preferences change over time, and how users group together based on similar behavior. Machine learning techniques like clustering and linear regression are used to find patterns in the data. These insights will help improve content recommendations, audience targeting, and overall platform engagement.

## EDA

Innitionally, we opened up the the data. Then transformed the sql files into csv files for ease of use. Then cleaned up the csv files by removing rows with null or erroneous data like out of range values(eg. ratings above 5 or below 0). After cleaning the data, we chose the information that we found to be more valuable, and plotted a variety of graphs exploring various interactions between the data.

## Models 

Using the cleaned data we started bulding the models required ,the first is a predicitive model -linear regression that predicts a movies average rating . The features are extracted from the movie_statistics  (total_ratings,unique_users,std_rating,min_rating,max_rating,year_of_release) are combined with movie's average rating. 


The dataset is then divided into two part (train-80% and test-20% ) then the test data (80%) was divided into two parts (training -75% and  validation-25%) then this was used to get a better analyisis of the data .
Training data(60% of the total dataset) : to train and fit the model
Validation data(20% of the total dataset) : to tune the dataset before the final check
Test data(20% of the total dataset):to report the final output in a unbiased form

We also standerdized all variables so it affects the regression evenly. The linear regression is trained,validated and retrained before being tested in the test data , and then tested on mean square error-mse, root mean square error-rmse, mean absolute error-mae and r square-r^2 .A scatter plot was used to illustrate this finfings of this regression model, the actual vs predicted test ratings.


Next we prep the data for the next two clustering models ,using five user activity features (total ratings,avrage ratings,rating standrad deviation,number of uniques movies watched and activity days) users are categorized.After standardization of the data.

The optimal number of clusters to be used in the model is calculated using both the Elbow method (inertia) and Silhouette score .A sample of 2000 users are taken from X_users to work on the silhouette score becasue the time and processing power to use the whole dataset is incredbily high.while the whole dataset is used for inetia . Two graphs are plotted to show sihlouette and intertia .


After choosing five as the optimal number of clusters from the dataset , we perform KMeans clusting first:

Since KMeans is more focused on lower variance within clusters, the results of this is based more on behavioural types of the users .

Cluster 0 -31,623 users - Generally has new users or casual users that engage less, rating infrequently

Cluster 1 -32,301 users- High activity and medium consistently raters : users here watch and rate a lot but in a more uniform way

Cluster 2 -98,915 users- Users with high aveage rating but high less frequent: they tend to give a very high evaluvation when they do enagage .

Cluster 3 -211,975 users- modratly active users  : these users rate movies frequently in average and generally is the majority of the consumers here .

Cluster 4 -53,949 users-  inactive users: t users with low ratings but consistent patterns .

Another plot is used to shows the scatter of users across the clusters 

Next we perform Hiracheal Clustering, as Hiracheal clustering uses the distance between groups unlike KMeans , the clusters differ a bit. a sample of 7500 users are taken (either 7500 or lenfht of the user feature - whatever is smaller). the same set of features that we used in KMeans is used again for consisitency and easier for model comparison later .feature scaling is also done using standerd scaler.
Five cluster's mean feacture values are calculated and presented in total ratings, average ratings , standerd deviation of ratings , uniquness of movies , activity , ratings per day , generosity , consistency and engagement  to make it clear what each cluster is based on.


CLuster A-3825 users - Moderate Users with stable habits: these users are active but not in any extreme behaviours

CLuster B -1600 users- Infrequent raters: these users have moderate engagemnt and consistency 

Cluster C -59 users- High activity and frequent raters : generally good ratings anre provided by these users 

Cluster D -360 users- low activity and ratings: these users are likely non engaging users. 

Cluster E -1656 users- Ocassional raters with high ratings :rating a few movies with high ratings

a scatter plot is uded to plot this data for better visualization 


Silhouette score and Davies-Bouldin score was checked in the model to see Hierarchical model's performance

## Results

In Part 3, the goal was to evaluate and compare the three models used in the project: Linear Regression, KMeans clustering, and Hierarchical clustering. Each experiment focuses on a different aspect of model performance and provides insights into how well the models work for predicting movie ratings and grouping users based on their behavior.


The first experiment compares the existing Linear Regression model with a very simple baseline model that always predicts the average training rating. By looking at metrics such as MSE, RMSE, MAE, and R², we can see whether the regression model actually learns useful relationships from the data or if it performs no better than a constant prediction. This comparison helps determine the real value of the Linear Regression model in predicting movie ratings.


The second experiment compares the two clustering models used in the project: KMeans and Hierarchical clustering. Both models create five clusters, but they differ in how they form them and in the amount of data they use. To compare their performance, we calculate the Silhouette Score and Davies–Bouldin Index for each model. These metrics show how compact and well-separated the clusters are. The results help assess which clustering method produces clearer and more meaningful user segments.


The third experiment looks at how interpretable and practically useful the clusters are. For both KMeans and Hierarchical clustering, we compare the size of each cluster and compute the average values of key user-behavior features, such as the number of ratings, average rating, consistency of ratings, number of unique movies watched, and engagement levels. By examining these profiles, we can understand what types of viewer groups each model creates and how distinct those groups are. This helps determine which clustering method provides more informative and actionable insights about user behaviour.


## Visualization

This part finilizes the project by interpreting the behavioural meaning of the viewer clusters and checking whether the segmentation is affected by temporal or ating related biases. It summarizes each cluster using key behavioural metrices such as total ratings, avarage rating, rating variability and the number of unique movies watched, allowing clear identification of distincs user groups. It then evaluates fairness by examining whether clusters differ systematically in the year users first rated a movie, and wether activity or rating patterns create distortions in the grouping. Finally, it exports an enriched dataset containing all user features and cluster labels, fulfilling the project requirement to validate, interpret and prepare the clustering results for reporting. 


## Conclusion



