# HR-Analytics
<p align="center">
  <img width="460" height="300" src="images/HRAnalytics.jpg">
</p>


## INTRODUCTION
The goal is to predict the promotions of deserving employees using different algorithms like Logistic regression, KNN, Decision Tree etc. 
The dataset consists of the information about employee and related information on trainings, rating, KPI, awards etc. 
The dataset comprises of 54808 observations with 14 columns. Below is a table showing names of all the columns and their description. 
Below is a table showing names of all the columns and their description.

## DATA
| Column Name          | Description                                                                                   |
| -------------        | -------------                                                                                 | 
| employee_id	         | Unique ID for employee                                                                        | 
| department	         | Department of employee                                                                        |  
| region               | Region of employment (unordered)                                                              | 
| education            | Education Level                                                                               |   
| gender               | Gender of employee                                                                            |
| recruitment_channel  | Channel of recruitment for employee                                                           |
| no_of_trainings	     | no of other trainings completed in previous year on soft skills, technical skills etc.        |
| age                  | Age of employee                                                                               |
| previous_year_rating | Employee Rating for the previous year                                                         |
| length_of_service    | Length of service in years                                                                    |
| KPIs_met >80%        | if Percent of KPIs(Key performance Indicators) >80% then 1 else 0                             |
| awards_won?          | if awards won during previous year then 1 else 0                                              |
| avg_training_score   | Average score in current training evaluations                                                 |
| is_promoted          | (Target) Recommended for promotion                                                            |     


## PROJECT ANALYSIS
| Description | Analysis |
| --- | --- |
| Red wine  | ![image.png](images/redwinedataset.png) |
| White wine | ![image.png](images/whitewinedataset.png) |


### CONCLUSION

|     | Models Analysed |
| --- | ---             |
| Model Results                  | ![image.jpg](images/Models.jpg) |
| Model-Cross Validation Results | ![image.jpg](images/CrossValidationResults.png) |
| Model-Grid Search Results      | ![image.jpg](images/GridSearchResults.png) |

#### Observation
##### Based on the data available we try the following approaches to see if the model built on these gives a good accuracy.
- Check a Model which doesnt includes type information, keep the outliers, doesnt scale data nor add any weights (due to imbalance data) and see if the KNN, Logistic Regression or Decision Tree provide good accuracy.
- Check if we add weights but ignore type, keep outliers and use unscaled data.
- Check if accuracy improves if we add type, remove outliers, scale data and add weights for predicting the quality 

After trying all the above it was observed that accuracy could not go beyond 61% even after adding type, removing outliers, standardised data to scale and adding weights. 

The approach is to see if we can bin the class "quality" from 0-10 to 3 major categories 0-2 [poor] ,3-6 [good] and 7-10 [excellent]. and see if the same Model is able to predict the class "quality" now more accurately.

##### For the new class (with 3 category) we found that by adding weights , standardised scale data ,including type the accuracy increased and the best was for KNN  88% for n = 16.

And, The best score for Logistic regression and Decision Tree was model 4 with 82% and Model 8A with 84% respectively.

##### Using cross validation with the new class (with 3 category) we found that accuracy increased to 96% for KNN , Random Forrest and Logistic Regression

![image.jpg](images/CrossValidationResults.png) 

And, Using Grid Search we found that to get the accuracy of 96% for KNN and Logistic Regression, we use KNN with parameters as n_estimator :1 6, p=2, algorithm=auto, metric=minkowski and weights=uniform.

![image.jpg](images/GridSearchFinalResults.png) 
#### Conclusion
##### KNN provides the highest accuracy of 96% with grid search and we use the best parameters as below:
-n_estimator :16
-p=2
-algorithm=auto
-metric=minkowski
-weights=uniform.
.


[Jupyter Notebook](.WineQuality-Classification/EDA_ModelEvaluation_Report/LogisticRegression_WineQuality_V2.ipynb)

