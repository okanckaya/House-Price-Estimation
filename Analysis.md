## ANALYSIS

When the analysis of the variables with high correlation with the dependent variable was made with the help of heatmap, it was seen that they were in the following order.
* 2019 m2 selling price, 
* 2020 m2 selling price,
* Number of bathrooms,
* Room
* Total Number of Rooms
* County
* District
* Property Type
* Education (University)
* Education (Middle)
* Socio-Economic Status
* Education (Primary)
* Landscape 1
* Landscape 2
* Master Bathroom
* Floor location
* …

Before the analysis, two separate datasets were created first. In the first dataset, in addition to the existing variables, there is a 54-variable dataset containing all the variables created and added later, while the other is the sub-dataset created by removing the variables with a correlation less than 0.003 with the dependent variable.

These two datasets were tested with three different machine learning algorithms. As a result of the analysis, it was seen that the random forest and XGBoost algorithms gave very good results, but the random forest algorithm was exposed to excessive learning. For this reason, the optimum result was obtained by modeling the first data set, which includes all variables, with the XGBoost algorithm.

![image](https://user-images.githubusercontent.com/71854717/145399755-83c97b9a-5c37-4379-b56c-6f95043ddf2e.png)

![image](https://user-images.githubusercontent.com/71854717/145399838-1a7ce9d5-11f8-4845-b6ab-82910b8fd670.png)

![image](https://user-images.githubusercontent.com/71854717/145399867-1eb2fad3-a685-4548-880e-1d43956335cd.png)

The related project is also a Kaggle competition and the results of the competition can be accessed from the link below.
https://www.kaggle.com/c/dogus-teknoloji-zingat/leaderboard

# RESULTS

The lack of sufficient data on the pandemic process in education data has made modeling the impact of the pandemic on housing sales very difficult and even impossible.

If the date range in the training set regarding the pandemic effect is expanded, the scores of the models during the testing phase will be improved.

Although the data are real sales data, it may have caused quite inconsistent values in prices due to various reasons (such as incorrect data entry, incorrect use of separators such as «.», «,» etc.) (the house sold for 530 million TL in Bağcılar). or a net 70 m2 flat with 1149 rooms).

Levels 1-2-3.. The districts where the flats for the floors are located should be reviewed. A Level 1 flat in Istanbul Beylikdüzü and a Level 1 flat in İzmir Çeşme may not mean the same (the amount of daylight the flat receives, like the facade facing the retaining wall.
