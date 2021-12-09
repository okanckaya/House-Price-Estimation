# VBO_Final_Project

In this project, it is aimed to make housing price estimation modeling in the real estate sector, which has changed with the effect of the Covid-19 pandemic. The project is based on the competition provided by Doğuş Teknoloji on Kaggle, and the project data has been obtained from Doğuş Teknoloji's zingat.com.

Variables in the training dataset:
* Path
* Time
* Property type
* Net area
* Gross area
* Number of rooms
* Number of bathrooms
* Heating type
* Number of floors in the building
* Floor location
* Building Age
* Dressing room
* Children's playground
* Elevator
* Conforms to earthquake regulations
* Car park
* Landscape

![image](https://user-images.githubusercontent.com/71854717/145395283-7f729505-4b91-4319-a6d4-a89725635f2a.png)

## EXPLORATORY DATA ANALYSİS

The training dataset's size is 64573x21 and the test dataset's is 35127x21. 33181 of the data in the training dataset consist of residences in Istanbul, and 31387 of them consist of residences in İzmir.

While the training dataset includes data between 01/01/2019 and 19/04/2020, the test dataset includes data between 20/04/2020 and 31/12/2020.

![image](https://user-images.githubusercontent.com/71854717/145359557-722bdc5c-cfc6-4606-8fe5-edb3f9758230.png)

As can be seen at first glance at the training dataset, the dependent variable "current price (güncel fiyat)" contains outliers.

![image](https://user-images.githubusercontent.com/71854717/145358746-2e69dfa6-ecff-4ef9-a450-471e8e6f8d05.png)

A house sold for 530 million Turkish Liras in Bağcılar and a house sold for 172 Turkish Liras in Torbalı makes no sense. Therefore, outliers in the dataset need to be reexamined. Within the scope of this project, data in the range of 50k-100m were evaluated instead of eliminating outliers with IQR. The reason for this is that data in districts such as Beşiktaş where housing prices are quite high can also be included in the model. After eliminating the outliers in the dataset, the final state of the dataset is as follows:

![image](https://user-images.githubusercontent.com/71854717/145359697-fe232f42-570f-48a6-aaab-b14bcc3090b8.png)

# Landscape
The landscape variable, which is one of the variables in the dataset, encoded with one or more words. Therefore, in order to consider the encoding order of the view in the data with multiple encodings, the view variable is divided into three separate columns (landscape 1, landscape 2 , landscape 3).

When the landscape 1 variable was examined, it was seen that 41454 of the data were not marked with any landscape option, 8688 were marked with the city, 4940 with the street and 3768 with the Bosphorus option.
![image](https://user-images.githubusercontent.com/71854717/145360744-02d6ab2e-1a9e-4970-943c-fb51d09ec58e.png)

Considering the effect of the landscape 1 variable on the dependent variable, it was seen that the average price of the houses marked with the Bosphorus view was higher than the other view types. In the second place is the sea, followed by the nature. The landscape variable with the lowest average is the river.
![image](https://user-images.githubusercontent.com/71854717/145361465-ee22937d-2c6a-4454-976b-d26268174f91.png)

If the same operations are done for the landscape 2 variable, as in the landscape 1 variable, the Bosphorus view is in the first place, the sea in the second place, and the nature variable in the third place.
![image](https://user-images.githubusercontent.com/71854717/145361727-a255a7df-35fb-45fb-9c27-55f0edcaf68b.png)

When the same operations are repeated for the landscape 3 variable, the first place is the nature view, the second is the sea, and the third is the Bosphorus view.
![image](https://user-images.githubusercontent.com/71854717/145361831-19a13749-f436-44dd-9f73-9b07703eb4b9.png)

# Property Type
Considering the propery tope, the majority of the data (56159 units) consists of flats, 4311 of them are villas and 1413 of them are detached houses.
![image](https://user-images.githubusercontent.com/71854717/145361972-dfa2a40b-649b-47a7-8801-cb47698f59d2.png)

It can be seen that the averages on the price variable of the house types, it is seen that the mansion type buildings are sold with the highest average, followed by the waterside apartments and residence type houses.
![image](https://user-images.githubusercontent.com/71854717/145362367-589eb4db-a5fa-4810-8ca9-8dd71312e663.png)

# Building Age
When the building age variable is observed, very interesting results emerge. While the majority of the houses that make up the dataset are newly built, 0-year-old properties, the current price average of these houses is in the lowest rank. The buildings aged 40 and over, which are the lowest in the dataset, have the highest average price. This is because 0-year-old housing datas come from Izmir's relatively low socioeconomic status such as Kınık, Torbalı and Beydağ, and most of the 40-year-old housing data comes from Beşiktaş.

![image](https://user-images.githubusercontent.com/71854717/145389275-7e090ef3-4641-4f73-9313-dc5f7cd932b7.png)

![image](https://user-images.githubusercontent.com/71854717/145389252-6cbccebb-974a-4cc1-b87e-35b135b31e0f.png)

# Number of bathrooms
If the effect of the number of bathrooms on the price is examined, it can be seen that the average prices of the houses with 6 or more bathrooms are the highest, followed by the houses with 5 and 4 bathrooms. It can be seen that the average prices of simple apartments with one bathroom are at the lowest level.
![image](https://user-images.githubusercontent.com/71854717/145389790-7413f559-88ba-4b14-a52f-075728f45100.png)

# Number of rooms
As mentioned before, most of the dataset consists of flats. In this direction, it can be seen that the majority of the these properties are composed of 2+1 and 3+1 apartments. However, it can be seen from the first glance at the chart below that the dataset also includes incorrect datas for various reasons. It is clear that a property with 1149+0 rooms is not possible (when these data are examined, it is seen that there are no complete buildings or factory buildings, but simple flats with an area of 70-120 square meters). Therefore, these data were dropped from the dataset.
![image](https://user-images.githubusercontent.com/71854717/145392894-1af3ed42-f736-45c8-8e09-01275206aff6.png)

# Car park
Istanbul and Izmir are important cities of Turkey in terms of population density. For this reason, it can be thought that the presence of a parking lot in a property can be quite effective in the price of the house. As can be seen from the graphs below, parking information is not available in most of the data that make up the dataset. When the effect of the parking lot on the average price is analyzed, it can be seen that the houses with parking lot can be sold with a higher average price than the houses without.

![image](https://user-images.githubusercontent.com/71854717/145390679-9278c893-fd30-46fa-a0fd-0ec69cae6fae.png)
![image](https://user-images.githubusercontent.com/71854717/145390685-f60b8f15-74ba-4cb1-9eb7-fa632e638a21.png)

# Heating type
The type of heating in the houses is a very effective parameter on the price of the house. A house with a combi boiler working with natural gas and a house with a coal stove can vary considerably in terms of both location and comfort. While most of the data in the dataset consists of houses with natural gas combi boilers, this is followed by air-conditioned houses (especially in Izmir). When we look at the average amount of heating type on the housing price, the houses with solar energy are sold with a very high average price compared to other houses. The reason for this is that most of this data in the dataset comes from regions where housing prices are quite high, such as Beşiktaş and Çeşme.

![image](https://user-images.githubusercontent.com/71854717/145392005-2e18c5f8-06ec-450b-bffa-cac1fbdbe66c.png)
![image](https://user-images.githubusercontent.com/71854717/145392013-a90e44be-6914-4b2e-8da1-7bd136fb0d44.png)

# Number of floors in the building & Floor location
The last two variables to be examined through graphics in the dataset are the floor where the residence is located and the total number of floors in the building. As can be seen from the graphs below, the average sales prices of the residences in buildings with 20 or more floors and the apartments on these floors are higher than those of other residences. The reason for this is that these data come from districts such as Beylikdüzü and Bornova.

![image](https://user-images.githubusercontent.com/71854717/145392923-a5714b05-a838-4c0e-afd4-c0cc8e65a22e.png)
![image](https://user-images.githubusercontent.com/71854717/145392940-806481aa-d672-40d8-9f8c-7337efad6efd.png)

# ADDITIONAL VARIABLES
In addition to these variables that are already present in the dataset, additional variables have been added to the dataset in order to make the modeling of the housing price sales forecast more healthy. Some of them were derived from the existing variables in the dataset (natural gas, stove, coal, free parking, indoor parking, etc.) and some of them were obtained from various data banks (Turkish Statistical Institute, Central Bank of the Republic of Turkey, investing.com and zingat.com).

# investing.com
The dollar exchange rate is a parameter that affects the purchasing power and is very effective on customer consumption reflexes. Especially in countries like Turkey where instant exchange rate fluctuations are experienced, the dollar rate gains even more importance. For this reason, it is obvious that housing prices will fluctuate with the dollar exchange rate. In this context, TL/Dollar exchange rate information, which is not available in the dataset, has been added to the dataset as a monthly average with the help of data obtained from "investin.com".
![image](https://user-images.githubusercontent.com/71854717/145393561-894f79b8-f588-421c-8c43-91eddee879c0.png)

# Central Bank of the Turkish Republic
Housing loan rates and housing price indices are also very effective parameters on housing prices. Especially, periods when housing loan interest rates are low can cause an increase in housing prices. For this reason, the data of these two variables were obtained from the official data of the Central Bank of the Republic of Turkey and added to the dataset.
![image](https://user-images.githubusercontent.com/71854717/145394820-967f1b86-7b65-4cc6-b059-bcbed36ad3b1.png)
![image](https://user-images.githubusercontent.com/71854717/145394834-2ea75bbf-d8bd-439f-98ef-453fccbc45b3.png)
![image](https://user-images.githubusercontent.com/71854717/145394841-8f741e32-ce5d-4995-8fdb-8a61f536eb7d.png)

# Turkish Statistical Institute
The construction cost index (consisting of two variables as material and labor) was taken from the official data of the Turkish Statistical Institute. These data, which are thought to be effective in the modeling of housing price estimation, have been added to the dataset as a monthly average as well as other data added.
![image](https://user-images.githubusercontent.com/71854717/145395079-c1b14ad7-fc4d-40e6-be9a-adb54e2856d1.png)

# zingat.com
The main source of competition data, zingat.com, offers regional report information, which is very important for many provinces/districts. Among these data presented as a real estate index, the average housing prices in the region, their changes over time, demographic information of the population living in the region, etc. It contains many important information. In this context, the socioeconomic status of the districts in the dataset from zingat.com, the education level of the people of the region, the scores given by the people living in the region for the region (security, noise, proximity to markets and cafes, proximity to transportation, etc.) were also collected and added to the dataset. The relevant parameters have been added to the dataset as they are available on zingat.com (educational status as a percentage, score indices scoring in the 5-point system and 2019-2020 square meter sales price in TL).

![image](https://user-images.githubusercontent.com/71854717/145396058-c17f63af-4320-4757-9293-c8231b9da931.png)

All the additional parameters mentioned above can be accessed from the "Additional Datasets" folder.

If the effect of socioeconomic status on the average selling price is examined from these new parameters added, the highest socioeconomic status A+, A and A- have the highest average selling price, and the lowest socioeconomic status C has the lowest average selling price.
![image](https://user-images.githubusercontent.com/71854717/145396243-d85f8a1e-f63b-429d-9806-e6c059938b37.png)

