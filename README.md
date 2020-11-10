### TEST


# FALL2020TIDYVERSE
CUNY DATA 607 TIDYVERSE Collaborative project

---
title: "Tidyverse CREATE Assignment"
author: "Shana Green"
date: "10/25/2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Assignment

In this assignment, you’ll practice collaborating around a code project with GitHub.  You could consider our collective work as building out a book of examples on how to use TidyVerse functions.

[GitHub repository](https://github.com/acatlin/FALL2020TIDYVERSE)

[FiveThirtyEight.com](https://data.fivethirtyeight.com/) datasets.

[Kaggle datasets](https://www.kaggle.com/datasets)

Your task here is to Create an Example.  Using one or more TidyVerse packages, and any dataset from fivethirtyeight.com or Kaggle, create a programming sample “vignette” that demonstrates how to use one or more of the capabilities of the selected TidyVerse package with your selected dataset. (25 points)

Later (see next assignment below), you'll be asked to extend an existing vignette.  Using one of your classmate’s examples (as created above), you'll then extend his or her example with additional annotated code. (15 points)

You should clone the provided repository.  Once you have code to submit, you should make a pull request on the shared repository.  You should also update the README.md file with your example.

After you’ve created your vignette, please submit your GitHub handle name in the submission link provided below. 

You should complete your submission on the schedule stated in the course syllabus.

## Data

The dataset I chose came from FiveThirtyEight.com article [We Watched 906 Foul Balls To Find Out Where The Most Dangerous Ones Land](https://fivethirtyeight.com/features/we-watched-906-foul-balls-to-find-out-where-the-most-dangerous-ones-land/). 


```{r}
library(tidyverse)
```

## Reading the Data from Github

```{r}

foul<-read.csv("https://raw.githubusercontent.com/fivethirtyeight/data/master/foul-balls/foul-balls.csv", na.strings=c("NA", "NULL"))

head(foul)
```


## Renaming Data Columns
```{r}
names(foul)<-c("Matchup","Game_Date", "Type_of_Hit","Exit_Velocity", "Predicted_Zone", "Camera_Zone", "Used_Zone")

colnames(foul)
```

In order to have a general visualization of the designated zones, I attached a photo from the article [We Watched 906 Foul Balls To Find Out Where The Most Dangerous Ones Land](https://fivethirtyeight.com/features/we-watched-906-foul-balls-to-find-out-where-the-most-dangerous-ones-land/).

![Generic Stadium Map](stadium map.png)


## Dplyr

I will use dplyr from the Tidyverse package.


### filter()

As a huge baseball fan, I wanted to filter out the outermost predicted zone and compare it to the exit velocity.

```{r}

foul %>%
    filter(Predicted_Zone=="7"|Predicted_Zone=="6")
```

### arrange()

Since this is a large data set, I wanted to take a look at the top 20 highest exit velocities. 

```{r}
foul %>%
    arrange(desc(Exit_Velocity))%>%
    head(20)

```


### summarise()

I used the summarize function from dplyr to generate some statistics for the exit velocity. 

```{r}
foul_info<-na.omit(foul)
```

```{r}
foul_sum <- group_by(foul_info, Type_of_Hit)
```

```{r}
foul_sum <- summarise(foul_sum,Min=min(Exit_Velocity),Max = max(Exit_Velocity),Median=median(Exit_Velocity), Mean=round(mean(Exit_Velocity),1))

```

```{r}
foul_sum<-as.data.frame(foul_sum)
foul_sum

```
