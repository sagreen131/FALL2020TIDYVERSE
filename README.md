
# TidyVerse Recipe CREATE

Name: Arushi Arora

#### Introduction:
The core tidyverse package includes "readr", "tidyr" and "dplyr"
- `readr` provides a fast and friendly way to read rectangular data
- `tidyr` provides a set of functions that help you get to tidy data. Tidy data is data with a consistent form: in brief, every variable goes in a column, and every column is a variable
- `dplyr` provides a grammar of data manipulation, providing a consistent set of verbs that solve the most common data manipulation

#### Approach:
Read the csv for the article https://fivethirtyeight.com/features/how-americans-like-their-steak/ published on Five Thirty Eight from Github using `readr`. Rename all the variables using `dplyr` package and remove the first row with no real reponses. Mutate the variable type to factor using the function `mutate` for further analysis
 
#### Conclusion:
The dataset was imported and cleaned using packages in TidyVerse

---

#### SYNTAX
- Import CSV from Github
    ```
    urlfile="https://raw.githubusercontent.com/fivethirtyeight/data/master/steak-survey/steak-risk-survey.csv"

    steakdata<- readr::read_csv(url(urlfile))
    ```

- Rename variables

    ```
    steakdata1 = dplyr::rename(steakdata, 
    "lottery" = "Consider the following hypothetical situations: <br>In Lottery A, you have a 50% chance of success, with a payout of $100. <br>In Lottery B, you have a 90% chance of success, with a payout of $20. <br><br>Assuming you have $10 to bet, would you play Lottery A or Lottery B?", 
    "smoke_cigs" = "Do you ever smoke cigarettes?" ,
    "drink_alcohol" = "Do you ever drink alcohol?", 
    "gamble" = "Do you ever gamble?",
    "skydiving" = "Have you ever been skydiving?",
    "overspeeding" = "Do you ever drive above the speed limit?",
    "cheat_patner" = "Have you ever cheated on your significant other?",
    "eat_steak" = "Do you eat steak?",
    "steak_prep" = "How do you like your steak prepared?",
    "hh_income" = "Household Income",
    "location" = "Location (Census Region)")
    ```
- Remove first row

  ```
    steakdata2 <- steakdata1[-c(1), ]
  ```

- Code for populating the tables from .csv file stored locally
    ```
    steakdata3 <- steakdata2 %>% as_tibble() 

    steakdata4 <- steakdata3 %>%
    mutate(lottery = as.factor(lottery)) %>%
    mutate(smoke_cigs = as.factor(smoke_cigs)) %>%
    mutate(drink_alcohol = as.factor(drink_alcohol)) %>%
    mutate(gamble = as.factor(gamble)) %>%
    mutate(skydiving = as.factor(skydiving)) %>%
    mutate(overspeeding = as.factor(overspeeding)) %>%
    mutate(cheat_patner = as.factor(cheat_patner)) %>%
    mutate(eat_steak = as.factor(eat_steak)) %>%
    mutate(steak_prep = as.factor(steak_prep)) %>%
    mutate(Gender = as.factor(Gender)) %>%
    mutate(Age = as.factor(Age)) %>%
    mutate(hh_income = as.factor(hh_income)) %>%
    mutate(Education = as.factor(Education)) %>%
    mutate(location = as.factor(location))

    ```
=======
# FALL2020TIDYVERSE
CUNY DATA 607 TIDYVERSE Collaborative project


* Data Analysis of Grocery items sold using Groceries_dataset.csv
=======
Change Log:
26 October: Added vignette w/ examples for purrr and forcats, Cameron Smith


