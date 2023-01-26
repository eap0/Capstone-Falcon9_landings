# SpaceX Falcon 9 mission landing predictor 

### This is a repository for the capstone project for data science certification 
The goal is to predict if a SpaceX rocket launch with a Falcon 9 booster would be a success or a failure. A succesful rocket launch is crucial to keeping costs down, because it can be reused for following missions. Therefore proper identification of scenarios and variables that allow for a succesful launch are important. In this project I built a mission landing predictor using machine learning libraries, and used different visualization packages to get insight of the relevant variables for the missions. 
Main python libraries used include: BeautifulSoup, sklearn, seaborn, matplotlib, folium, plotly dash. SQL was also used in the exploratory section. 

### 1. Data collection API
Made a get request to SpaceX API. 
The information for the Booster Falcon 9 was selected, and other boosters (Falcon 1) were filtered out. 
The dataset was cleaned: missing values in the Payload Mass column were changed to the mean value of the column. 
In the end, the data consists of a dataframe of 90 rows with 17 columns. 
![Dataframe1](https://user-images.githubusercontent.com/100446091/212753055-5d1804bb-3035-4371-b371-2cb1fb36a13b.JPG)


### 2. Web scraping 
The data was collected from Falcon 9 historical launch records available in the Wikipedia page: https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches. The library? BeautifulSoup was used to extract records from an HTML table, then parse the table and convert it into a Pandas data frame. 

### 3. Data wrangling 
The analysis of the data at this stage, showed that there were several Space X launch facilities: Cape Canaveral Space Launch Complex 40 **VAFB SLC 4E** , Vandenberg Air Force Base Space Launch Complex 4E (**SLC-4E**), Kennedy Space Center Launch Complex 39A **KSC LC 39A**.  Launches had distinct launch orbits around the Earth. In the records, the landing outcomes ranged from True + "intended location of landing", indicating a successful landing or False or None indicating failure to land. The landing outcomes were summarize in a new column called **Class**, were 1 means that the landing was a success or 0 if the landing was a failure. This is the variable that we will predict latter on. More info can be followed in the python notebook here.

### 4. EDA with SQL 
In this section, I used IBM's Watson studio to load the table in a Db2 dataset and inspect the dataset executing SQL queries. The table includes records for wach payload carried during a SpaceX mission to outer space. The total payload mass carried by boosters launched by NASA (CRS) is 45,596 kg. The average payload mass carried by a F9 booster v1.1 is 2,928.4 kg. The first succesful landing outcome was achieved in December 12, 2015. 

### 5. EDA with Visualization 

### 6. Plotting with Folium 
In this section, I used Folium to explore the location of the launch sites as a factor in the launch success rate. The four launch sites are located in two states, either California or Florida. Markers were put in each location to show the number of launches, and color was added to show success (green) or failure (red), like in the following image:  ![image](https://user-images.githubusercontent.com/100446091/214718652-b27fa197-aa41-46c5-b39f-57c79026c8ae.png)


All of the locations were close to the coastline, most launch sites were located at a distance of 1 km or less from the coast. The most succesful site is **KSC LC-39A** located in Florida, with a 79% success rate. KSC LC-39A is located more than 4 km from the coast. It is about 1 km away from a railway or highway. The closest city/town is Titusville, which is less than 20 km away.  

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





