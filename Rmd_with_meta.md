---
title: "Untitled"
author: "Brigitte Hogan"
date: "3/11/2019"
output: 
  html_document: 
    fig_caption: yes
    toc: yes
    keep_md: yes
---

# Introduction

Here is my first RMarkdown document.

# Let's embed some R code

We'll write an R chunk here that loads the tidyverse library and then reads in the gapminder dataset from our project directory.  


```r
library(tidyverse)
gm <- read_csv("gapminder.csv")
```

# Investigate gm

Let's look at the gm dataset


```r
head(gm)
```

```
## # A tibble: 6 x 12
##    c_id country continent  year pets_per_thou lifeexp population
##   <dbl> <chr>   <chr>     <dbl> <chr>           <dbl>      <dbl>
## 1     1 Albania Europe     1982 14               70.4    2780097
## 2     1 Albania Europe     1987 43               72      3075321
## 3     1 Albania Europe     1992 61               71.6    3326498
## 4     1 Albania Europe     1997 29               72.9    3428038
## 5     1 Albania Europe     2002 16               75.7    3508512
## 6     1 Albania Europe     2007 70               76.4    3600523
## # … with 5 more variables: gdp_per_cap <dbl>, trans_deaths <dbl>,
## #   resp_deaths <dbl>, ext_deaths <chr>, total_perthou <dbl>
```

# Our first plot

Showing the GDP per capita on the x-axis and the life expectancy on the y-axis


```r
gm %>%
  ggplot(aes(gdp_per_cap, lifeexp)) +
  geom_point()
```

![](Rmd_with_meta_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

# A better plot

Adding color by continent and adding a log scale for GDP


```r
gm %>%
  ggplot(aes(gdp_per_cap, lifeexp)) +
  scale_x_log10() +
  geom_point(aes(col=continent))
```

![Life Expectancy by log GDP](Rmd_with_meta_files/figure-html/unnamed-chunk-4-1.png)

# Option 1

Trying chunk option "Echo = False"

![Life Expectancy by log GDP](Rmd_with_meta_files/figure-html/unnamed-chunk-5-1.png)

# Option 2

Trying chunk option "fig.show = hide"


```r
gm %>%
  ggplot(aes(gdp_per_cap, lifeexp)) +
  scale_x_log10() +
  geom_point(aes(col=continent))
```

# Option 3

Trying chunk option "include = FALSE"




# Kable Table

Trying a simple table


```r
head(gm)
```

```
## # A tibble: 6 x 12
##    c_id country continent  year pets_per_thou lifeexp population
##   <dbl> <chr>   <chr>     <dbl> <chr>           <dbl>      <dbl>
## 1     1 Albania Europe     1982 14               70.4    2780097
## 2     1 Albania Europe     1987 43               72      3075321
## 3     1 Albania Europe     1992 61               71.6    3326498
## 4     1 Albania Europe     1997 29               72.9    3428038
## 5     1 Albania Europe     2002 16               75.7    3508512
## 6     1 Albania Europe     2007 70               76.4    3600523
## # … with 5 more variables: gdp_per_cap <dbl>, trans_deaths <dbl>,
## #   resp_deaths <dbl>, ext_deaths <chr>, total_perthou <dbl>
```

head as a table

```r
library(knitr)
kable(head(gm))
```



 c_id  country   continent    year  pets_per_thou    lifeexp   population   gdp_per_cap   trans_deaths   resp_deaths  ext_deaths    total_perthou
-----  --------  ----------  -----  --------------  --------  -----------  ------------  -------------  ------------  -----------  --------------
    1  Albania   Europe       1982  14                70.420      2780097          3631             NA            NA  NA                       NA
    1  Albania   Europe       1987  43                72.000      3075321          3739            305          2688  736                   762.4
    1  Albania   Europe       1992  61                71.581      3326498          2497            423          2522  1065                  690.5
    1  Albania   Europe       1997  29                72.950      3428038          3193            183          1357  2596                  620.6
    1  Albania   Europe       2002  16                75.651      3508512          4604            314           906  1248                  593.4
    1  Albania   Europe       2007  70                76.423      3600523          5937            269           590  964                   457.1

