# coursera---Applied-Plotting---Assigment4


Please download the Hadex 1961 dataset directly from 
https://www.climdex.org/access/   


# Comments #

This notebook imports data from one of three publicly available sources (ETCCDI, HADEX_ref1961-1990, and HADEX_ref1981-2010) for weather observations, and **is designed 
to show trends**. 
For that purpose weather data are grouped into logical categories ('Warm', 'Cold', 'Wet', 'Dry', and 'Extremes')

The user is then able to zoom into individual states, as well as select one of the categories via radio buttons.

**I have deliberately not displayed any y-values**, because the main purpose is to display trends, not specific values.
Because the different datasets within each category all represent different measurements (i.e. mm of rain, number of days, temperature) they naturally occupy significantly differnt ranges of y-values.

Therefore **I have chosen to normalise each dataset** so it's values range from 0 to 1, and then plot them stacked (non-additive), so they don't overlap. When possible I have plotted a faint 3rd-degree polynomal regression curve to emphasise clear trends if they exist.

The original data contain obviously significant noise, which made it also harder to discern trends. I therefore am plotting a 10 year rolling average, which smoothes out the lines a fair bit. If the purpose of these graphs where to detect outlier and extremes, this would of course not be an acceptable technique.

The original data are provided as directories with thousands of individual csv files, one for each weather-observation category and each weather station.
To import these files takes a significant amount of time. I have therefore provided a csv file which contains my finished DataFrame which is much, much faster to import.
To demonstrate however that I constructed that dataframe from the original data by combining many different datafiles I have also provided a method `importAllAndStore()` to import from the original data (and then save the final DataFrame into a csv file).

This code could be fairly easily adapated to display climate trends from other countries, since the data-format seems to be identical internationally (as far as I checked). Apart from various constants, the main method that would need to be adapted is loadWeatherStations(), which is necessary to group the weatherstations into states.

**To test simply run all cells top to bottom.**

The code as it is imports and uses data from the HADEX_ref1981-2010 dataset, but that can easily be changed as this is fully parameterised.

To do a **quick test** with the prepared and exported dataframe, place the file `Climate-Trends-Australia-HADEX_1961.csv` into the working directory, and run the code as is.

**To test the original import**, expand and create a `Data` folder in the working directory, and place the expanded data into it. Because the datafiles are large, I compressed them separately for each data source - you only need to download the one you chose to use. Execute `importAllAndStore()` once, then run the notebook again top to bottom (exept for `importAllAndStore()` ).

Folder structure for import from original data:

`Data
   ETCCDI Climate Change indices
       Australia
           CDD
           CSDI
           ...
           WSDI
   HADEX_ref1961-1990
       stn-indices
           CDD_6190
           CSDI_6190
           ...
           WSDI_6190
   HADEX_ref1981-2010
       stn-indices
           CSDI_8110
           R95p_8110
           ...
           WSDI_8110
   Stations.csv`

If using this code, please acknowledge original author, **Angelika Sajani**


# URLS #

Explanation of observed indices:  https://www.climdex.org/learn/indices/#index-FD 

Hadex Datasets: https://www.climdex.org/access/   (I found the 1961-1990 dataset to be the most comprehensive) 

ETCCDI Datasets: http://etccdi.pacificclimate.org/data.shtml   

Australian Weather Stations (as part of downloading other data): http://www.bom.gov.au/metadata/catalogue/19115/ANZCW0503900447#dataset-constraints
