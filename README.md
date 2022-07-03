# Best-neighbourhoods-to-settle-in-Toronto
[Link to the notebook]()

In 2019, Canada had the eighth largest immigrant population, with 35 percent settling in Toronto. Toronto is divided into 140 distinct districts. In this project, I will analyse and classify Toronto neighbourhoods based on their desirability using Machine Learning and Data Visualization.

## Methodology

Metrics to be considered when grouping neighbourhoods include: 
- The total number of important venues in each neighbourhood. 
- Additional metrics: The crime rate, total population, unemployment rate in each neighbourhood are the primary metrics. Meanwhile, housing rents will be considered as a secondary metric.

### Approach

Part - I
Get the venues in different neighbourhoods of Toronto using foursquare API, Now clean those venues and then define essential venues to retain only important venues. Now apply KMeans Clustering to the total venues data after determining the optimum cluster number using the elbow method. Visualize the clusters wrt to the neighborhoods in order of the increasing venues.

Part - II
Load and clean data for the primary metrics. Then, apply KMeans clustering algorithms to the data. Classify the clusters according to the mean of each metric with categories [High, Medium and Low]. The best cluster is the cluster that gives the lowest rates for the primary metrics. Use the data for the best cluster only now for the secondary metric. Now load the housing rents for only those neighbourhoods which had low primary metrics. Apply clustering to the resulting data. Give categorical variables to the clusters obtained. Lastly, sisualize the final results.

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
