Happiness Presentation
========================================================
author: Jim  Andrade,  Miriam  Amaya,  Giselle  Camacho,  Kevin  Huang (Group 2)
date: April 29th, 2021
autosize: true

Introduction
========================================================


We found our data from Kaggle and is from 2019. The data was collected from the United Nations at an event celebrating International Day of Happiness on March 20th

The reason why we choose this data because: 

- We wanted to see the world's happiness from each country.


- What factors influence the levels of happiness.


- This set of data gave us a lot of variables to compare.


Research Question: What factors in countries are related to happiness?

Packages Used
========================================================
We loaded up the packages tidyverse and skimr, as its seen below:


```r
library(tidyverse)
library(skimr)
```
After using these packages, we are able to upload dataset to R by using read_csv:

```r
happiness <- read_csv("data/2019.csv")
```

Now, looking into the data
========================================================
The Dimensions are: 

```r
dim(happiness)
```

```
[1] 156   9
```

names(happiness)

```r
names(happiness)
```

```
[1] "Overall_rank"                 "Country_or_region"           
[3] "Score"                        "GDP_per_capita"              
[5] "Social_support"               "Healthy_life_expectancy"     
[7] "Freedom_to_make_life_choices" "Generosity"                  
[9] "Perceptions_of_corruption"   
```
Cont. of Data
========================================================
glimpse(happiness)

```r
glimpse(happiness)
```

```
Rows: 156
Columns: 9
$ Overall_rank                 <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 1…
$ Country_or_region            <chr> "Finland", "Denmark", "Norway", "Iceland…
$ Score                        <dbl> 7.769, 7.600, 7.554, 7.494, 7.488, 7.480…
$ GDP_per_capita               <dbl> 1.340, 1.383, 1.488, 1.380, 1.396, 1.452…
$ Social_support               <dbl> 1.587, 1.573, 1.582, 1.624, 1.522, 1.526…
$ Healthy_life_expectancy      <dbl> 0.986, 0.996, 1.028, 1.026, 0.999, 1.052…
$ Freedom_to_make_life_choices <dbl> 0.596, 0.592, 0.603, 0.591, 0.557, 0.572…
$ Generosity                   <dbl> 0.153, 0.252, 0.271, 0.354, 0.322, 0.263…
$ Perceptions_of_corruption    <dbl> 0.393, 0.410, 0.341, 0.118, 0.298, 0.343…
```
Defining Variables
========================================================

# Score

-Sum of the results of all variables

-The Higher the score the happier the country

Diving into the data
========================================================
# Score and Perception of Corruption (Absense of Corruption)
### Hypothesis: The Higher the Score, the Higher the Perceptions of Corruption.
Now, we will look into the relationship of the score variable and the perception of corruption.


```r
ggplot(data = happiness, mapping = aes(x = Score, y = Perceptions_of_corruption)) + 
geom_point() +
  labs(title = "Score and Perception of Corruption",
       subtitle = "Relationship between Score and Perception of Corruption",
       x = "Score", y = "Perception of Corruption")
```

![plot of chunk unnamed-chunk-6](Presentation-figure/unnamed-chunk-6-1.png)

Diving into the data
========================================================
# The Top Five Ranked Countries in Happiness
### Hypothesis: The top 5 coutries will come from the European region.

```r
top_five_rank <- happiness %>%
  filter(Overall_rank < 6)
```

```r
ggplot(data = top_five_rank, mapping = aes(x = Country_or_region, y = Overall_rank)) +
         geom_point() +
  labs(title = "Top Five Ranked Countries",
       x = "Country", y = "Rank")
```

![plot of chunk unnamed-chunk-8](Presentation-figure/unnamed-chunk-8-1.png)
Diving into the data
========================================================
# The Last Five Ranked Countries in Happiness
### Hypothesis: The last five countries will come from third world countries. 

```r
last_five_rank <- happiness %>%
  filter(Overall_rank > 151)
```

```r
ggplot(data = last_five_rank, mapping = aes(x = Country_or_region, y = Overall_rank)) +
         geom_point() +
  labs(title = "Last Five Ranked Countries",
       x = "Country", y = "Rank")
```

![plot of chunk unnamed-chunk-10](Presentation-figure/unnamed-chunk-10-1.png)

Diving into the data
========================================================

# GDP per Capita and Happiness

### Hypothesis: The higher the GDP per Capita the higher the Score (happiness)

- Positive Correlation between both varibles
- Money is often associated with happiness
- Financial Stability and Happiness


```r
ggplot(data = happiness, mapping = aes(x = Score, y = GDP_per_capita)) + 
geom_point() +
  labs(title = "Score and GDP per Capita", subtite = "Relationship between Score and GDP Per Capita",
    x = "Score", y = "GDP per Capita")
```

![plot of chunk unnamed-chunk-11](Presentation-figure/unnamed-chunk-11-1.png)



Summary
========================================================
- The higher the score of happiness on the data of the countries, the higher levels of absence of corruption was seen from the data.
- Based from the data of the ranks of the countries, the top 5 countries were countries from Europe, while the last 5 countries were third world countries.
- Based from the data on GDP per Capita and score, we see that the higher the GDP per Capita, the higher the score of happiness was seen. 
