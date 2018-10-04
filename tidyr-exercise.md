---
title: "Tidy data and joins"
author: Shreeram Senthivasan
output:
  github_document:
    toc: true
    toc_depth: 2
---



# Intro

For this assignment, we have been tasked with selecting and completing two tasks. The first will be a data reshaping problem, while the second will be a data joining problem.

# Data Reshaping (Prompt #2)

Let's make a table comparing life expectancies between the UK and France over the years sampled in the `gapminder` dataset. Specifically, we want each row to represent a year and have a column for each country that records life expectancy in that year.

## Tabulate Data


```r
FR_UK <- gapminder %>%
  filter(country == "United Kingdom" | country == "France") %>%
  select(year, lifeExp, country) %>%
  spread(country, lifeExp) %T>%   #This is a Tee pipe from the `magrittr` package
                                  #It let's me save the data set here, but still
                                  #pipe it to kable in the next line
  kable(col.names = c("Year",
                      "Life Expectancy\\n in France",  #The double \\n let's me add
                      "Life Expectancy\\n in the UK")) #a linebreak to the title
```

