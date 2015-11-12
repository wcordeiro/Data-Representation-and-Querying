# Data Representation and Querying Project 2015
#####by Wilson Cordeiro - G00330453
A third year Data Representation and Querying Project 2015. 

## Overview
As required on the Data Representation & Querying, I have created a simple API for a dataset.

This project provides an API for two dataset: Galway City Beaches and Bathing Water Compliance.

Both datasets are available at:

1. [Galway City Beaches](https://data.gov.ie/dataset/galway-city-beaches)

2. [Bathing Water Compliance](https://data.gov.ie/dataset/bathing-water-compliance)

For reference, I have attached the following files:
* ```Galway_City_Beaches.csv```
* ```BWPR00198_2013_01_profile.pdf```
* ```BWPR00217_2013_01_profile.pdf```
* ```BWPR00265_2014_01_profile.pdf```
* ```BWPR00307_2015_01_profile.pdf```

## Information about the datasets
1. Galway Beaches
The data is in CSV format (Comma Separated Values), obtained from [Galway City Beaches](https://data.gov.ie/dataset/galway-city-beaches).

### Size, Fields & Values.
The file cointains 4 unique rows. Each row has 8 fields with associated values.
| Field         | Description     |
|:-----:|:-------------------------------------------------------------:|
| **ObjectID**  | An ID given to each park. |
| **Name**      | Name of the beach    |
| **Lat**       | The latitude coordinate of the park  |
| **Long**      | The longitude coordinate of the park |
| **EastITM**   | Irish Transverse Mercator (ITM) East value. * | 
| **NorthITM**  | Irish Transverse Mercator (ITM) North vaule.  | 
| **EastIG**    | East Irish Grid Reference number. ** |
| **NorthIG**   | North Irish Grid Reference number. |

*
> From Wikipedia - [Irish Transverse Mercator](https://en.wikipedia.org/wiki/Irish_Transverse_Mercator).

> _"**Irish Transverse Mercator (ITM)** is the geographic coordinate system for Ireland."_

**
> From Wikipedia - [Irish grid reference system](https://en.wikipedia.org/wiki/Irish_grid_reference_system).

> _"The **Irish grid reference system** is a system of geographic grid references commonly used in Ireland (both Northern Ireland and the Republic of Ireland)."_
