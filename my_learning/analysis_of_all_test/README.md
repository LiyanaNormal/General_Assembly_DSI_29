# Analysis on ACT and SAT for national testing

### Problem Statement
An analysis is conducted to identify the impacts of socio-economic factors to state-level test scores.

### Background
Representing the national education board, we are analysing between two national test ACT and SAT to identified which of test has correlation to socio-economic factors. A comparison between the year on year participation and the composite and total scores for ACT and SAT respectively across the nation.

In an increasingly globalised world, companies seek a skilled and competent workforce to navigate and resolve business problems in the everchanging climate. Unfortunately, USA is not included in the top 5 nations with skilled workforce ([*source*](https://globalpeoservices.com/top-5-countries-with-the-most-skilled-workers-in-2021/)). Thus, a nationl test is pivotal in determining and preparing the nation to meet the global demands.

Standardized tests such as ACT and SAT aids in raising the knowledge competency of the nation in the long-run. In the selection of a national test, socio-econmic factors such as gini, hdi, racial diversity, and population density within the state are considered in relation to the test participation and the scores to evaluate on the fairness of the test. 

A gini coefficient / gini index is used to measure the income distribution within population, (identifying the income gaps within the state) ([*source*](https://worldpopulationreview.com/country-rankings/gini-coefficient-by-country)). Hdi refers to the human-development index which is an amalgamation of the life expectancy, expected and average years of education, and the gross national income per capita (gini-coefficient) to determine the development of a population ([*source*](https://ourworldindata.org/human-development-index#:~:text=The%20Human%20Development%20Index%20(HDI)%20provides%20a%20single%20index%20measure,a%20long%20and%20healthy%20life)). Racial diversity feature is considered in the following study to test for the hypothesis if a more homogenous state participates and scores better ([*source*](https://worldpopulationreview.com/states/states-by-race)). Population density refers to the number of people within a square kilometers within a state which assist in understanding if there may be other factors such as scarcity of resources (education staff / institution) may be contributing factors within the state participation and results ([*source*](https://www.worlddata.info/population-density.php)).

### Datasets
The following dataset has been used for a comparision for the following study:
1. * [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State 
([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
2. * [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State 
([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
3. * [`act_2019.csv`](./data/act_2019.csv): 2019 ACT Scores by State 
([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
4. * [`sat_2017.csv`](./data/sat_2017.csv): 2017 SAT Scores by State 
([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
5. * [`sat_2018.csv`](./data/sat_2018.csv): 2018 SAT Scores by State 
([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
6. * [`sat_2019.csv`](./data/sat_2019.csv): 2019 SAT Scores by State 
([source](https://blog.prepscholar.com/average-sat-scores-by-state-most-recent))


### Data Dictionary 

|Feature|Type|Dataset|Description|
|---|---|---|---|
|State|object|Name of state|Name of state in USA| 
|Participation|float|0-1|State participation for SAT/ ACT| 
|Score|float|ACT composite/SAT total|Average results from ACT score / Cummulative of score for SAT| 
|Year|object|2017/2018/2019|Year for ACT/SAT test| 
|>90% Participation|boolean|True/False|More than 90% participation for SAT/ACT in states| 
|Test|object|ACT/SAT|Type of test| 


### Additional Dataset
The following assumptions were made regarding the following imported datasets. An assumption was made that the 2020 state population density is the same as the 2019 population density for the states. Herfindahl–Hirschman index was used to calculate the race percentage in a given state([source](https://en.wikipedia.org/wiki/Herfindahl%E2%80%93Hirschman_index)).

* [`gini_5y.csv`](./data/gini_5y.csv): 2019 gini coefficient ([source](https://data.census.gov/cedsci/table?q=Gini&g=0100000US_0400000US01,02,04,05,06,08,09,10,11,12,13,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,44,45,46,47,48,49,50,51,53,54,55,56,72&tid=ACSDT5Y2019.B19083&moe=false&tp=true))
* [`hdi_2019.csv`](./data/hdi_2019.csv): 2019 hdi index ([source](https://globaldatalab.org/shdi/shdi/USA/?levels=1%2B4&interpolation=1&extrapolation=0&nearest_real=0&years=2019))
* [`Population_density.csv`](./data/Population_density.csv): 2020 population density ([source](https://en.wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States_by_population_density))
* [`race_perc_2019.csv`](./data/race_perc_2019.csv): 2019 race percentage ([source](https://worldpopulationreview.com/states/states-by-race))

### Combined Data Dictionary 
|Feature|Type|Dataset|Description|
|---|---|---|---|
|State|object|Name of state|Name of state in USA| 
|Participation|float|0-1|State participation for SAT/ ACT| 
|Score|float|ACT composite/SAT total|Average results from ACT score / Cummulative of score for SAT| 
|Year|object|2017/2018/2019|Year for ACT/SAT test| 
|>90% Participation|boolean|True/False|More than 90% participation for SAT/ACT in states| 
|Test|object|ACT/SAT|Type of test| 
|population_density|float|value|Population of state divided by the area of state (square km) in 2020| 
|gini_index|float|0-1|Estimated Gini index value for 2019|
|hdi_index|float|ACT/SAT|Estimated HDI index value for 2019| 
|race_percentage|float|ACT/SAT|Race percentages expressed in Herfindahl–Hirschman index for 2019| 

### Summary of Analysis
There is a moderately positive correlation (0.55) between population density to scores on ACT and a weakly negative correlation between the scores and the population density (-0.33) in SAT. There is a negligible positive correlation (0.078) between gini index to scores on ACT and a weakly negative correlation between the scores and the gini index (-0.28) for SAT. There is a high positive correlation (0.61) between hdi index to scores on ACT and a weakly positive correlation between the scores and the hdi index (0.036) in SAT. There is negligible positive correlation (0.021) between race percentage to scores on ACT and a weakly negative correlation between the scores and the race percentage (-0.11) in SAT.


### Conclusion & Recommendations 
In conclusion both state scores draws correlation to state socio-economic factors which impacts ACT more greatly than SAT. ACT shows a general positive correlation to scores of ACT with a higher correlation on hdi-index and population density compared to race percentage and the gini index. The socio-economic factors in SAT is less significant and tends to a negative correlation. A morderately negative correlation is drawn from population density and the gini index to SAT scores whilst a negligible and moderately positive correlation is observed in hdi index and race precentage correlations are drawn respectively. 

ACT test scores has a overall correlation to socio-economic factors highlighted in the state and should be favoured over SAT in conducting of further research on factors such as institution and teaching manpower including student to teacher ratios. This would assist to understand more significant contributions which may assist in increasing the state average composite scores.


