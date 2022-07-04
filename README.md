# Top-neighbourhoods-in-Toronto
[Link to the notebook](https://nbviewer.org/github/raofida75/Top-neighbourhoods-in-Toronto/blob/main/Top%20neighbourhoods%20in%20Toronto.ipynb)

In 2019, Canada had the eighth largest immigrant population, with 35 percent settling in Toronto. Toronto is divided into 140 distinct districts. In this project, I will analyse and classify Toronto neighbourhoods based on their desirability using Machine Learning and Data Visualization.

## Dataset

<b> Toronto neighbourhood profile dataset </b>: It contains various characteristics such as neighbourhood ID, total population, and so on for 140 neighbourhoods in Toronto.

<b> Neighbourhood.geojson dataset</b>: It contains the longitude and latitude of each neighbourhood.

<b> Neighbourhood crime rates </b>: It contains the crime rate for different offences in each neighbourhood. 

<b> Housing rent dataset </b>: This dataset contains the median housing rent for 1 bedroom in each neighbourhood.

## Methodology

Metrics to be considered when grouping neighbourhoods include: 
- The total number of important venues in each neighbourhood. 
- Additional metrics: The crime rate, total population, unemployment rate in each neighbourhood are the primary metrics. Meanwhile, housing rents will be considered as a secondary metric.

### Approach

#### Part - I : Clustering wrt to the total venues.
Use Foursquare API to get top 100 venues in each neighbourhood of Toronto. Venues will be limited to the radius of 500 meters only. Finally, save the obtained dataframe so that we don't have to retrieve the data from the API every time we run this notebook. Thereafter, clean the venue categories by grouping the relevant categories together using the following link:

https://developer.foursquare.com/docs/categories

Then we will extract the essential venues such as Cafe, Restaurant, Park, Grocery / Stores, Hair Salon, Exercise, and Bank and remove the other venues. Furthermore, we will group each neighbourhood into meaningful, homogeneous clusters based on the number of venues. We'll look at the inertia at various k values to identify the ideal k value for k-means. When we plot distortion against k, there will be a k value where we see the bending. This is the ideal number of clusters.<b><i>The optimum number of clusters were found to be 3.</b></i> Based on the number of essential venues, we will now group the neighbourhoods using the k-Means clustering algorithm. We will divide the neighbourhoods into three distinct groups. Lastly, Visualize the clusters wrt to the neighborhoods in order of the increasing venues using the choropleth map.

#### Part - II : Clustering wrt to the primary and secondary metrics 

Load and clean the data for the primary metrics from the neighbourhood profile dataset. The primary metrics are total population, crime rate, and unemployment rate. After loading the data, clean it up and transform the numeric data from object datatype to int or float accordingly. Thereafter, transform all of the features to a similar range (between 0 and 1) using min max scaler. Before applying machine learning models, it is critical to standardise the data because if one feature has very large values, it will dominate over other features. As a result of standardisation, all features will have the same influence. Then, apply KMeans clustering algorithms to the normalized data. Classify the clusters according to the mean of each metric with categories [High, Medium and Low]. Only the neighbourhoods with a 'LOW' crime rate, population, and unemployment rate from the previous section will be used in the next section. We will now group the selected neighbourhoods according to housing rents. There are 69 neighbourhoods with lower primary metrics, while the rest have either a high unemployment rate or a high crime rate, which will be labelled as Least Desirable.

After loading and cleaning the housing rents dataset, extract the data for only those neighbourhoods which had low primary metrics amd apply KMeans clustering on the resulting data. Cluster 2 has the lowest housing rent hence it contains the most desirable neighbourhoods. While cluster 0 has comparatively higher rents hence it is not as desirable; however, still better than the neighbourhoods in cluster 1. Cluster 1 has the highest housing rents, as a result it is semi desirable.

### Results
[Link to the interactive dashboard](https://public.tableau.com/app/profile/fida.hussain.abbas.rao/viz/TopNeighbourhoodsinToronto/Dashboard1?publish=yes)

<p align="center">
<img src="https://github.com/raofida75/Best-neighbourhoods-to-settle-in-Toronto-/blob/main/Dashboard.png" width="1000"/>
</p>

#### Analyzing Results
<b>Most Desirable Neighbourhoods:</b> These neighbourhoods should be considered if you are looking for less expensive apartments as well as a low crime and unemployment rate. Some of the most desirable neighbourhoods in Toronto are: Banbury-Don Mills, Etobicoke West Mall, Runnymede-Bloor West Village etc.

Desirable Neighbourhoods with large number of venues : Greenwood-Coxell is the only neighbourhood with a large number of venues while also having a low crime and unemployment rate. Furthermore, the rent in this area is also under $1700.

Neighbourhoods with a large amount of venues: Only 5% of Toronto neighbourhoods have high venue, with the majority of them having either a high crime rate or a high unemployment rate with the exception of Greenwood-Coxell. Some of these neighbourhoods are: Agincourt South-Malvern West, Flemingdon Park, Thistletown-Beaumond Heights etc.

Least Desirable Neighbourhoods: Avoid these neighbourhoods if possible because of high rates of crime and unemployment. Almost 50% of the neighbourhoods lie in this category. 


label	neighbourhood_id	median_rent		

0	49			1710.612245

1	14			2118.571429

2	6			1064.166667
