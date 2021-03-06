---
title       : Carbon Dioxide Data from Mauna Loa
subtitle    : Monitoring and Predictions
author      : Dennis Noren
job         : Data Scientist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Dataset

* Source: Scripps Institution of Oceanography, University of California  and NOAA; data are obtained from the 'datasets' package included in Base R, structured as a time series

```r
summary(co2)  # values are in parts per million (ppm)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     313     324     335     337     350     367
```
* The monitoring station is at an elevation of about 11,150 feet on the slopes of Mauna Loa on the island of Hawaii.  This location makes the measurements unaffected by temperature inversions and other effects that might produce local variations (exception: measurements are adjusted to account for local outgassing of CO2 from the volcano)
* The idea is that this dataset is a close approximation to ambient CO2 levels for the entire earth.
* Dataset has monthly averages from the years 1959 through 1997 (more recent data have been collected but are not included in this dataset)

--- .class #id 

## Decomposition of Time Series

* Seasonal period is very obvious, caused by the fact that the great majority of Earth's biomass lies in the Northern Hemisphere
* Function 'stl' from R base stats package is used to decompose the time series into seasonal, trend, and residual components
* The 'forecast' function from the 'forecast' package is used to predict based on the decomposition
* The user controls which year the decomposition starts, always using 1997 as the model end point
* The user controls how many years of forecasting are produced (beyond 1997)
* The user also controls reference lines for the CO2 level and year, but these do not affect the model

--- .class #id

## Observations of Results

* Along with the upward trend, there seems to be a moderate acceleration of CO2 levels
* The stl decomposition model does not include a quadratic form to account for this (other types of models could do this)
* If we restrict the starting year for the model, we get some idea of this acceleration

Model Start  | Forecast to Reach 380 Annual avg | Forecast to Reach 390 Annual avg
------------ | ----------------- | -----------------
1959 | 2009 | 2017
1969 | 2008 | 2015
1979 | 2008 | 2014
1984 | 2008 | 2015
1994 | 2007 | 2013

* More recent data show the acceleration continuing: annual averages of 380 ppm in 2005 and 390 ppm in 2010 have been recorded

--- .class #id

## Extensions that Could be Made

* Include more recent data
* Include quadratic trend effect
* Include a tabular view of dataset
* Include specific numeric data predictions
* Compare predictions with actuals for recent years
* Compare results with monitoring stations from other locations

