<div align="center">
<h1> Top-neighbourhoods-in-Toronto </h1>
 
 <p align="center">
<img src="https://github.com/raofida75/Best-neighbourhoods-to-settle-in-Toronto-/blob/main/Dashboard.png" width="1000"/>
</p>

<i>In 2019, Canada had the eighth largest immigrant population, with 35 percent settling in Toronto. Toronto is divided into 140 distinct districts. In this project, I will analyse and classify Toronto neighbourhoods based on their desirability using Machine Learning and Data Visualization.

[Link to the notebook](https://nbviewer.org/github/raofida75/Top-neighbourhoods-in-Toronto/blob/main/Top%20neighbourhoods%20in%20Toronto.ipynb)
</i></div>

## Table of Contents

1. [Datasets](#datasets)     
2. [Metric for a desirable neighbourhood](#metric-for-a-desirable-neighbourhood)  
3. [Methodology](#methodology) 
4. [Results](#results)
5. [Summary](#summary)


## Datasets

- <b> neighbourhood-profiles-2016-140-model.csv </b>: It contains various characteristics such as neighbourhood ID, total population, and so on for 140 neighbourhoods in Toronto.
- <b> Neighbourhood.geojson</b>: It contains the longitude and latitude of each neighbourhood.
- <b> neighbourhood-crime-rates - 4326.csv </b>: It contains the crime rate for different offences in each neighbourhood. 
- <b> housing.xlsx</b>: This dataset contains the median housing rent for 1 bedroom in each neighbourhood.

## Metrics for a desirable neighbourhood

Metrics to be considered when grouping neighbourhoods include: 
- The total number of important venues in each neighbourhood. 
- Additional metrics: The crime rate, total population, unemployment rate in each neighbourhood are the primary metrics. Meanwhile, housing rents will be considered as a secondary metric.

## Methodology

### <i> Part - I : CLustering wrt to the number of venues</i>
- Use Foursquare API to get top 100 venues in each neighbourhood of Toronto. 
- Clean the venue categories by grouping the relevant categories together using this <a href="https://developer.foursquare.com/docs/categories" target="_blank"><b>link: </b></a>
- Extract the essential venues such as Cafe, Restaurant, Park etc. 
- Apply clustering to group each neighbourhood into meaningful, homogeneous clusters based on the number of venues. 

### <i>Part - II : Clustering wrt to the primary and secondary metrics</i>
- Load and clean the data for the primary metrics from the neighbourhood profile dataset.
- Transform all of the features to a similar range (between 0 and 1) using min max scaler
- Apply KMeans clustering algorithms to the normalized data.
- Classify the clusters high, low and medium according to the mean of each metric.
- Now apply kMeans clustering using the housing data. (only neighbourhoods with low primary metrics will be considered.)

## Results

[Link to the interactive dashboard](https://public.tableau.com/app/profile/fida.hussain.abbas.rao/viz/TopNeighbourhoodsinToronto/Dashboard1?publish=yes)

After apply kmeans clustering on the housing data, cluster 2 had the lowest housing rent hence it contains the most desirable neighbourhoods. While cluster 0 has comparatively higher rents hence it is not as desirable; however, still better than the neighbourhoods in cluster 1. Cluster 1 has the highest housing rents, as a result it is semi desirable.

| label | neighbourhood_count | median_rent |
| --- | --- | --- |
| 0 | 49 | 1710.612 |
| 1 | 14 | 2118.571 |
| 2 | 6 | 1064.1667 |


## Summary

- <b>Most Desirable Neighbourhoods:</b> These neighbourhoods should be considered if you are looking for `less expensive` apartments as well as a `low crime `and `unemployment rate`. Some of the most desirable neighbourhoods in Toronto are: **Banbury-Don Mills**, **Etobicoke West Mall**, **Runnymede-Bloor West Village** etc.

- Desirable Neighbourhoods with large number of venues : **Greenwood-Coxell** is the only neighbourhood with a `large number of venues` while also having a `low crime` and `unemployment rate`. Furthermore, the rent in this area is also under <i>$1700</i>.

- Neighbourhoods with a large amount of venues: Only <i>5%</i> of Toronto neighbourhoods have high venue, with the majority of them having either a high crime rate or a high unemployment rate with the exception of Greenwood-Coxell. Some of these neighbourhoods are: **Agincourt South-Malvern West, Flemingdon Park, Thistletown-Beaumond Heights** etc.

- Least Desirable Neighbourhoods: Avoid these neighbourhoods if possible because of `high crime rates` and `unemployment`. Almost <i>50%</i> of the neighbourhoods lie in this category. 

