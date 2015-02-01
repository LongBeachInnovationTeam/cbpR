# cbpR: Working with the County Business Patterns Data in R
This is an R Package that downloads and prepares panel data sets from the **[Census County Business Patterns (CBP)](http://www.census.gov/econ/cbp/)**.

It downloads the CPB data on the county level and then allows the user to aggregate the data up into larger geographic entities such as Metropolitan Statistical Areas, Micropolitan Statistical Areas, or some user defined collection of counties.

The file [`demo/cardealers.R`](https://github.com/jtilly/cbpR/blob/master/demo/cardealers.R) contains a demonstration. It generates a panel data set for "New Car Dealers" [(NAICS 441110)](http://www.census.gov/cgi-bin/sssd/naics/naicsrch?code=441110&search=2012%20NAICS%20Search). The data set ranges from 2000 to 2009. It aggregates the firm count data from the County Business Patterns into Micropolitan Statistical Areas and returns a dataset with annual data on the firm count, employment (if available), firm count by employment, and population figures for each Micropolitan Statistical Area. The population estimates are taken from the *Annual Estimates of the Population of Metropolitan and Micropolitan Statistical Areas: April 1, 2000 to July 1, 2009* [(CBSA-EST2009-01)](https://www.census.gov/popest/data/metro/totals/2009/). The Micropolitan Statistical Area definitions are taken from the [Census 2003-2009 Delineation Files](https://www.census.gov/population/metro/files/lists/2009/List1.txt) .

Note that the CPB data is also directly available for Micropolitan Statistical Areas. However, since the definitions of Micropolitan Statistical Areas have changed frequently in the past, using county level data (and aggregating it for a particular definition of Micropolitan Statistical Areas) is a more reliable way to get a long and balanced panel.

### Installation and how to use

```
install.packages("devtools")
library("devtools")
install_github("jtilly/cpbR")
library("cpbR")
```
Once the library is loaded, use
```
setCbpPath("~/cbpR/data_source", "~/cbpR")
```
to define where to store the source data that will be downloaded and where to store the generated data sets.

To download the source data, use
```
downloadCbp()
```
To get the firm count data from the County Business Patterns, use
```
firms = getFirmCount(naics = "441110", years=c("07", "08", "09"))
```
More details are in [`demo/cardealers.R`](https://github.com/jtilly/cbpR/blob/master/demo/cardealers.R).
