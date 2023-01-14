# SpaceX Falcon 9 mission landing predictor 

### This is a repository for the final capstone project for data science certification 
python libraries used: BeautifulSoup, sklearn, folium, plotly dash,  

### 1. Data collection API



### 2. Web scraping 
The data was collected from Falcon 9 historical launch records available in the Wikipedia page: https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches


### 3. Data wrangling 
The analysis of the data at this stage, showed that there were several Space X launch facilities: Cape Canaveral Space Launch Complex 40 VAFB SLC 4E , Vandenberg Air Force Base Space Launch Complex 4E (SLC-4E), Kennedy Space Center Launch Complex 39A KSC LC 39A.  Launches had distinct launch orbits around the Earth, illustrated in the following image:
![Datawrangling_fig1](https://user-images.githubusercontent.com/100446091/212401695-3e20c91c-1687-49d8-89f0-4aac779e86a9.JPG)
The landing outcomes ranged from True or False + "intended location of landing" or None indicating failure to land. The landing outcomes were summarize in a new column called Class, were 1 means that the landing was a success or 0 if the landing was a failure. This is the variable that we will predict latter on. More info can be followed in the python notebook here.

### 4. EDA with SQL 

### 5. EDA with Visualization 

### 6. Plotting with Folium 
All of the locations were close to the coastline, a distance of xxx km or less. 

### 7. Interactive dashboard  
The location with the largest success launches is site CCAFS LC-40 in Florida. 
The site: KSC LC-39A has the highest launch success rate, 79% of the total launches were sucessful. 
Missions where the payload range is between 2500 kg and 5000 kg have the highest success rate (55%) than any other range. 
In contrast, missions where the payload is 5000 kg to 7500 kg have the lowest success rate, under 23%. 
The F9 booster version with the highest success rate is FT.  
### 8. Machine learning  
Used a machine learning pipeline to predict if the first stage will land given the data from the preceding labs. 

The following classification methods were implemented: logistic regression, support vector machine (svm), decision tree classifier and k-nearest neighbors. 
In the logistic regression, the following parameters were optimized using the GridSearchCV to find the best parameters of each classification algorithm. 
The best accuracy on the test data was 83.3%, which was achieved by all four classification method after tuning the parameters. A confusion matrix was used to illustrate the errors in the predictions; the most common error was false positive, e.g, the method predicted there was a landing but the fact was that the mission did not land.
![image](https://user-images.githubusercontent.com/100446091/212206170-da121c0a-8b66-4193-9a8e-4c38e12f23ac.png)

### 9. Conclusions 

### 10. References 





