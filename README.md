# Melanism
All code used in the analysis of melanistic vs. nonmelanistic jaguar and oncilla. 

Two files needed: -Main Melanistic Analysis includes all the code for cleaning data, calculating time in radians based on exact sunrise and sunset, calculating Coefficient of Overlapping and related statistics, builds bar plots and circadian/lunar activity plots, and calculates Rao test for activity patterns -Functions Used for Melanistic Analysis: all custom background functions used on Main Melanistic Analysis
  
  
###Important Note: Set timezone on computer to desired timezone for correct sunTime function calculation. Have not ironed out the designation of the timezone in the POSIXct and sunTime functions. 

Data not included. Data used in this was data obtained from camera trap photos with date and time recorded. 
Columns needed for this analys:
  -Coloring: designation of record as "Melanistic" or "Non-melanistic"
  -Date: date of observation in format %m/%d/%Y
  -Time: time of record in decimal format
  -Independent: with designations  as "Yes" for observations of the same species at the same camera within 30 minutes or "No" for non-independent data
  -Longitude: in decimal degrees
  -Latitude: in decimal degrees
