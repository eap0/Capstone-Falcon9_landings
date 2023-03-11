# SpaceX Falcon 9 mission landing predictor 

### This is a repository for the capstone project for data science certification 
The goal is to predict if a SpaceX rocket launch with a Falcon 9 booster would be a success or a failure. A successful rocket launch is crucial to keeping costs down, because it can be reused for following missions. Therefore proper identification of scenarios and variables that allow for a succesful launch are important. In this project I built a mission landing predictor using machine learning libraries, and used different visualization packages to get insight of the relevant variables for the missions. 
Main python libraries used include: BeautifulSoup, sklearn, seaborn, matplotlib, folium, plotly dash. SQL was also used in the data exploration section. 

 ![image](https://user-images.githubusercontent.com/100446091/224451233-b7dcc3c9-9338-4316-b0d0-d59a98e7ce11.png)
Picture from IBM lab –Data collection API

### 1. Data collection API
Made a get request to SpaceX API. 
The information for the Booster Falcon 9 was selected, and other boosters (Falcon 1) were filtered out. 
The dataset was cleaned: missing values in the Payload Mass column were changed to the mean value of the column. 
In the end, the data consists of a dataframe of 90 rows with 17 columns. 
![Dataframe1](https://user-images.githubusercontent.com/100446091/212753055-5d1804bb-3035-4371-b371-2cb1fb36a13b.JPG)


### 2. Web scraping 
The data was collected from Falcon 9 historical launch records available in the Wikipedia page: https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches. The library? BeautifulSoup was used to extract records from an HTML table, then parse the table and convert it into a Pandas data frame. 


### 3. Data wrangling 
The analysis of the data at this stage, showed that there were several Space X launch facilities: Cape Canaveral Space Launch Complex 40 **CCAFS LC-40** and **CCAFS SLC-40**, Vandenberg Air Force Base Space Launch Complex 4E (**VAFB SLC-4E**), Kennedy Space Center Launch Complex 39A **KSC LC 39A**.  Launches had distinct launch orbits around the Earth. In the records, the landing outcomes ranged from True + "intended location of landing", indicating a successful landing or False or None indicating failure to land. The landing outcomes were summarize in a new column called **Class**, were 1 means that the landing was a success or 0 if the landing was a failure. This is the variable that we will predict latter on. More info can be followed in the python notebook here.

### 4. EDA with SQL 
In this section, I used IBM's Watson studio to load the table in a Db2 dataset and inspect the dataset executing SQL queries. The table includes records for wach payload carried during a SpaceX mission to outer space. The total payload mass carried by boosters launched by NASA (CRS) is 45,596 kg. The average payload mass carried by a F9 booster v1.1 is 2,928.4 kg. The first succesful landing outcome was achieved in December 12, 2015. 

### 5. EDA with Visualization 
Preliminary insights started to become evident as different variables (were explored Payload mass, launch orbit, flight number, launch site).
The successful rocket launch trend increases between the years  of 2013 to 2020. Also some rocket launches are more succesful than others.
![image](https://user-images.githubusercontent.com/100446091/224441646-11dd70ce-ab02-4208-96a8-508ffe165793.png)
![image](https://user-images.githubusercontent.com/100446091/224441822-6b4954b7-0aa0-4a41-831c-f919a9a7cc5c.png)



### 6. Plotting with Folium 
In this section, I used Folium to explore the location of the launch sites as a factor in the launch success rate. The four launch sites are located in two states, either California or Florida. Markers were put in each location to show the number of launches, and color was added to show success (green) or failure (red), like in the following image:  ![image](https://user-images.githubusercontent.com/100446091/214718652-b27fa197-aa41-46c5-b39f-57c79026c8ae.png)


All of the locations were close to the coastline, most launch sites were located at a distance of 1 km or less from the coast. The most succesful site is **KSC LC-39A** located in Florida, with a 79% success rate. KSC LC-39A is located more than 4 km from the coast. It is about 1 km away from a railway or highway. The closest city/town is Titusville, which is less than 20 km away.  

### 7. Interactive Plotly dash that helps visualize the impact of the variables on the outcome 
The location with the largest success launches is site **CCAFS LC-40** in Florida. 
The site: KSC LC-39A has the highest launch success rate, 79% of the total launches were successful. 
Missions where the payload range is between 2500 kg and 5000 kg have the highest success rate (55%) than any other range. 
In contrast, missions where the payload is 5000 kg to 7500 kg have the lowest success rate, under 23%. 
The F9 booster version with the highest success rate is FT.  
Examples:
![image](https://user-images.githubusercontent.com/100446091/224448823-2921441d-177c-4223-b41d-6a9035ec395c.png)
![image](https://user-images.githubusercontent.com/100446091/224451814-5affb919-8175-4e5b-84dd-6cf89af542db.png)



### 8. Application of machine learning to predict a successful landing  
Finally a machine learning (ML) pipeline was used to predict if the first stage will have a successful landing using the data from the preceding labs. 

The following classification methods were implemented: logistic regression, support vector machine (svm), decision tree classifier and k-nearest neighbors. 
In the logistic regression, the following parameters were optimized using the GridSearchCV to find the best parameters of each classification algorithm. 

The ML predictor showed high accuracy. The best accuracy on the test data was 83.3%, which was achieved by all four classification method after tuning the parameters.

A confusion matrix was used to illustrate the errors in the predictions; the most common error was false positive, e.g, the method predicted there was a landing but the fact was that the mission did not land.
![image](https://user-images.githubusercontent.com/100446091/212206170-da121c0a-8b66-4193-9a8e-4c38e12f23ac.png)

### 9. Conclusions 
Several variables were identified to have an impact on the landing outcome. These variables are: payload mass (in kg), launch orbit, launch flight number, and launch site. ​

Launches with payload mass in the range of  2500-5000 kg have the most successful rate launches. Launch orbits GEO, SSS and  had the most successful rates. ​

The success rate of landing increased from 2013 to 2020, which could indicate that latter launches benefitted from the information from previous launches. ​

Launch location impacted the landing outcome. Ideally the location would have to be 6 km from the coastline. Site KSC LC-39A in Florida had the highest launch rates, it is ~6 km from the coastline. The biggest city/town is several tenths of kilometers away. ​

As expected, the machine learning models trained on the data that contained these variables had an accuracy of 83.3% in successfully predicting the outcome of the landing. ​

Following the recommendations can reduce the cost of launches from ~165 millions to ~62 millions (est. cost numbers from Space X model)

### 10. References 





