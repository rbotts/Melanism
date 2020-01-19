# Melanism
All code used in the analysis of melanistic vs. non-melanistic jaguar and oncilla. 

## Overview
### Two files needed to run:

- Main Melanistic Analysis: includes all the code for cleaning data, analyzes and plots
- Functions Used for Melanistic Analysis: all custom background functions used on Main Melanistic Analysis

### Data not included. 
Data used in this was data obtained from camera trap photos with date and time recorded. 

Columns needed for this analys:
  - Coloring: designation of record as "Melanistic" or "Non-melanistic"
  - Date: date of observation in format %m/%d/%Y
  - Time: time of record in decimal format
  - Independent: with designations  as "Yes" for observations of the same species at the same camera within 30 minutes or "No" for non-independent data
  - Longitude: in decimal degrees
  - Latitude: in decimal degrees

## Main Melanistic Analysis
### Important Note: Set timezone on computer to desired timezone for correct sunTime function calculation. Have not ironed out the designation of the timezone in the POSIXct and sunTime functions. 
- cleans data 
- calculats time in radians based on exact sunrise and sunset using sunTime function from overlap package (Meredith & Linkie, 2018)
- calculates Coefficient of Overlapping and related statistics using overlap package
- builds bar plots of proportion and number of each coloring (melanistic and non-melanistic) and designation as night or day
- builds circadian and lunar activity plots
- calculates Rao test for activity patterns  

## Functions Used for Melanistic Analysis
- overlapCI*: calculates Coefficient of Overlapping and confidence interval using overlap package (Ridout & Meredith, 2018). Follows the two-step method developed by [Ridout & Linkie (2009)](https://zslpublications.onlinelibrary.wiley.com/doi/full/10.1111/j.1469-7998.2011.00801.x) where sample sizes between 20 and 75 are run with a non-negative trigonometric sum distribution and sample sizes greater than 75 are run with a kernel density with a standard bandwidth of 1 and bandwidth adjustment of 0.8. Uses user-set number of replicates (numboot). In ours we ran it with 10000 replicates. 
- watson2*: calculates U-squared statistics, modified to work with "tied" data (See: Zar, J. H. (1999). Biostatistical analysis. Upper Saddle River, NJ: Prentice Hall)
- watson2test*: approximates p-value of Watson's U-Squared, given two vectors (See: 
 [Tiku, M. L. (1965). Chi-Square approximations for the distributions of goodness-of-fit statistics U2N and W2N. Biometrika, 52. 630-633](https://www.jstor.org/stable/2333714?seq=1). 
 - w.stat*: calculates W statistic from 2 or more vectors of data (in Radians)
 - w.prob*: approximates p-value of W statistic if given 2+ vectors of data (in radians)
 - binning*: function used within chisquare function to bin data into desired number of bins
 - chisquare*: calculates fisher test statistic (determined fisher test was better for general activity pattern analysis as the majority of species vectors did not meet assumptions for chi-square. 
 - overall: function that runs all functions above given two vectors of observations to compare
 - theme_mooring: theme for bar plots
 - pvalueRAO: function print.rao.spacing.test altered to save p-value range into data frame (Agostinelli & Lund). From package Circular (2017).
  ### * means written by TJ Weigman
 ## Authors
 - Amy Eppert (Student in Department of Biology, Point Loma Nazarene University)
 - TJ Weigman (Student in Department of Physics and Engineering, Point Loma Nazarene University)
    -Initial functions for Coefficient of Overlapping and related statistics
