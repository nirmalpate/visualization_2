# visualization_2

---
title: "MA304_GroupAssignment"
author: "Arsenal"
date: "15/03/2021"
output:
  pdf_document: default
  html_document:
    df_print: paged
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE,warning = FALSE, message = FALSE)
```

Introduction:

The World Bank is an international financial institution that provides loans and grants to the governments of low- and middle-income countries for the purpose of pursuing capital projects.The dataset contains essential information from world wide countries on female literacy,internet users, life expectancy, exports,GDP and population,from which analysis can be drawn on how major factors of the particular country and the region is being effected or influenced.



Data Analysis:

1)Analysis on the features -

It is evident that  female literacy,internet users, life expectancy, exports,GDP and population plays a major role in country and region's economy.

2)Finding any relations while considering multiple features -

a.When population is taken as major factor (range 1,000,888,081 - 1,744,161,298)life expectancy is not highest which may also signify poor health conditions, even though population is high internet users are low.

b.It is also seen that when highest internet users (range 90-98%) are from lowest populated country and region.

c.when GDP is higher,life expectancy is not equally higher this also have clear meaning that highest GDP is not equal to good heath conditions.

d.When literacy rate is higher than 90% life expectancy is also higher than 80 years,this also states education makes differences.

e.EU region has bagged the highest Exports of goods and services percentage of GDP this also lead to good amount of GDP and PPP.



Feature Engineering and Data Cleaning:


1)Removing redundant features -

White spaces or extra spaces in the data set are removed using strip.white=TRUE as a part of data preprocessing.

2)Converting features into suitable form for modeling-

Column names of data set are modified and data sets are divided according to the suitability of R for the best visualization.

Visualization on key points:

1. AF and EU have the highest records of data on the essentials factors of female literacy,internet users, life expectancy, exports,GDP and population in the world bank data. 

```{r loaddata,echo=FALSE, include=TRUE}
df <- read.csv("/Users/nirmalpatel/Desktop/dv/2015 World Bank data by nation and region.csv",header=TRUE,strip.white=TRUE)
df1 <- read.csv("/Users/nirmalpatel/Desktop/dv/2015 World Bank data by region EU.csv",header=TRUE)
df2 <- read.csv("/Users/nirmalpatel/Desktop/dv/2015 World Bank data by region PA.csv",header=TRUE)
df3 <- read.csv("/Users/nirmalpatel/Desktop/dv/2015 World Bank data by exports validation.csv",header=TRUE)
library(ggplot2)
library(ggcorrplot)
e <- ggplot(df,aes(Region, width=1))
e <- e + geom_bar(fill = "#C42126")
e

```

2. Even if the literacy is low for some countries in EU, GDP and PPP are not interlinked.

```{r, echo=FALSE}
ggplot(df1, aes(x=`Literacy_rate_percentage_15years_above`, y=GDP_PPP, label=Country)) + 
  geom_bar(stat='identity', aes(fill=Country), width=.5)
```

3.In the region of PA,even though population and life expectancy is low, literacy is high.This also symbolizes that when less population is present for the particular region resources would be adequate to have a successful education.

```{r, echo=FALSE}
ggplot(df2, aes(x =Population_total, y =Life_expectancy_at_birth_total_years)) +
    geom_point(aes(color = factor(Literacy_rate_percentage_15years_above),size=1))

```

4.when Exports of goods and services percentage of GDP is highest there is a observation on Population Largest City percentage of Urban_Pop is 100%

```{r, echo=FALSE}
ggplot(df3, aes(Country, Exports_of_goods_and_services_percentage_of_GDP)) +
geom_histogram(stat='identity', aes(fill=Popltn_Largest_City_percentage_of_Urban_Pop))
```

5. when consider on dense plotting of points,EU has the highest internet users from 50 to 100 range and AF has the lowest 0 to 50 range internet users compared to other regions.

```{r, echo=FALSE}
ggplot(df, aes(Internet_users_per_100_people, Region) ) +
  geom_point()
```

6.  AF and EU have the highest records of data on the essentials factors of female literacy,internet users, life expectancy, exports,GDP and population in the world bank data. 
 
```{r loaddata,echo=FALSE, include=TRUE}
data2 <- read.csv("/Users/nirmalpatel/Desktop/Book1.csv",header=TRUE)
data3 <- read.csv("/Users/nirmalpatel/Desktop/Training/2015 World Bank data by region EU.csv",header=TRUE)
library(ggplot2)
library(ggcorrplot)
e <- ggplot(data2,aes(Population_total, width=1))
e <- e + geom_bar(fill = "#C42126")
e

```

7. Relation between literacy rate and life expectancy in EU.

```{r, echo=FALSE}
ggplot(data3, aes(x='Literacy_rate_percentage_15years_above', y='Life_expectancy_at_birth_total_years', label=Region)) + 
  geom_bar(stat='identity', aes(fill=Country), width=.5)
```

8.This histogram shows country and their internet users per 100 people in the region of middle east when we considered internet users. Conclusion we can derive from this is, urban popultion in arab countries use internet variely.Bahrain and Oman are rankig first and second.  

```{r, echo=FALSE}
ggplot(data2, aes(Country, Internet_users_per_100_people)) +
geom_histogram(stat='identity', aes(fill=Popltn_Largest_City_percentage_of_Urban_Pop))
```

9. This histogram shows countrywise total population in arab world.

```{r, echo=FALSE}
ggplot(data2, aes(Country, Population_total)) +
geom_histogram(stat='identity', aes(fill=Popltn_Largest_City_percentage_of_Urban_Pop))
```

10.Population of country in arab world.

```{r, echo=FALSE}
ggplot(data2, aes(Country, Population_total) ) +
  geom_point()
```
Questions which need further investigation:

Based on the research on the dataset,following are the questions which need further investigation to understand the adverse effect of the factors leading to country and region downfall on GDP and also which factors are influencing the county and region to have better economy
