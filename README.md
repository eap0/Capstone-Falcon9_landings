# datascience-finalprojects

## This is a repository for the final capstone project for data science certification 

# 1. 
# 2. Exploring the data using SQL 
# 3. Dash and Plotly 
All of the locations were close to the coastline, a distance of xxx km or less. 

The location with the largest success launches is site CCAFS LC-40 in Florida. 
The site: KSC LC-39A has the highest launch success rate, 79% of the total launches were sucessful. 
Missions where the payload range is between 2500 kg and 5000 kg have the highest success rate (55%) than any other range. 
In contrast, missions where the payload is 5000 kg to 7500 kg have the lowest success rate, under 23%. 
The F9 booster version with the highest success rate is FT.  
# 4. ML 
Used a machine learning pipeline to predict if the first stage will land given the data from the preceding labs. 

The following classification methods were implemented: logistic regression, support vector machine (svm), decision tree classifier and k-nearest neighbors. 
In the logistic regression, the following parameters were optimized using the GridSearchCV to find the best parameters of each classification algorithm. 
The best accuracy on the test data was 83.3%, which was achieved by all four classification method after tuning the parameters. A confusion matrix was used to illustrate the errors in the predictions; the most common error was false positive, e.g, the method predicted there was a landing but the fact was that the mission did not land.
![image](https://user-images.githubusercontent.com/100446091/212206170-da121c0a-8b66-4193-9a8e-4c38e12f23ac.png)





