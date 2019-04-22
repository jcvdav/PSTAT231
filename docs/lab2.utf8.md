---
title: "Untitled"
author: "Villaseñor-Derbez J.C."
date: "10/4/2019"
output:
  html_document:
    toc: yes
    toc_float: yes
    code_folding: "hide"
header-includes: \usepackage{mathtools}
---




```r
knitr::opts_chunk$set(echo = T,
                      message = F,
                      warning = F)

suppressPackageStartupMessages({
  library(ISLR)
  library(class)
  library(skimr)
  library(tidyverse)
})
```


# Load and inspect the data


```r
carseats <- ISLR::Carseats

skim(carseats)
```

```
## Skim summary statistics
##  n obs: 400 
##  n variables: 11 
## 
## -- Variable type:factor -------------------------------------------------------------------
##   variable missing complete   n n_unique                        top_counts
##  ShelveLoc       0      400 400        3 Med: 219, Bad: 96, Goo: 85, NA: 0
##      Urban       0      400 400        2          Yes: 282, No: 118, NA: 0
##         US       0      400 400        2          Yes: 258, No: 142, NA: 0
##  ordered
##    FALSE
##    FALSE
##    FALSE
## 
## -- Variable type:numeric ------------------------------------------------------------------
##     variable missing complete   n   mean     sd p0    p25    p50    p75
##  Advertising       0      400 400   6.63   6.65  0   0      5     12   
##          Age       0      400 400  53.32  16.2  25  39.75  54.5   66   
##    CompPrice       0      400 400 124.97  15.33 77 115    125    135   
##    Education       0      400 400  13.9    2.62 10  12     14     16   
##       Income       0      400 400  68.66  27.99 21  42.75  69     91   
##   Population       0      400 400 264.84 147.38 10 139    272    398.5 
##        Price       0      400 400 115.8   23.68 24 100    117    131   
##        Sales       0      400 400   7.5    2.82  0   5.39   7.49   9.32
##    p100     hist
##   29    <U+2587><U+2582><U+2582><U+2583><U+2582><U+2581><U+2581><U+2581>
##   80    <U+2586><U+2586><U+2586><U+2585><U+2586><U+2587><U+2585><U+2586>
##  175    <U+2581><U+2581><U+2583><U+2587><U+2587><U+2583><U+2581><U+2581>
##   18    <U+2587><U+2585><U+2583><U+2583><U+2583><U+2583><U+2585><U+2583>
##  120    <U+2587><U+2586><U+2585><U+2587><U+2587><U+2586><U+2586><U+2585>
##  509    <U+2587><U+2586><U+2586><U+2586><U+2587><U+2587><U+2587><U+2587>
##  191    <U+2581><U+2581><U+2582><U+2586><U+2587><U+2585><U+2582><U+2581>
##   16.27 <U+2581><U+2582><U+2587><U+2587><U+2586><U+2583><U+2582><U+2581>
```


# Feature enginiering

We create a new feature High as the response variable following the rule:

[
High = \begin{dcases}
    \text{No},& \text{if Sales} \leq \text{median(Sales)}\\       
    \text{Yes}, & \text{if Sales}  > \text{median(Sales)}
\end{dcases}
]













