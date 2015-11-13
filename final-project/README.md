# Data Representation and Querying Project 2015
#####by Wilson Cordeiro - G00330453
A third year Data Representation and Querying Project 2015. 

## Overview
As required on the Data Representation & Querying, I have created a simple API for a dataset.

This project provides an API for two dataset: Galway City Beaches and Bathing Water Compliance.

The datasets are available at:

1. [Galway City Beaches](https://data.gov.ie/dataset/galway-city-beaches)

2. [Bathing Water Compliance](https://data.gov.ie/dataset/bathing-water-compliance)

For reference, I have attached the following files:
* ```Galway_City_Beaches.csv```
* ```BWPR00198_2013_01_profile.pdf```
* ```BWPR00217_2013_01_profile.pdf```
* ```BWPR00265_2014_01_profile.pdf```
* ```BWPR00307_2015_01_profile.pdf```

## Information about the datasets

### Galway Beaches

The **Galway City Beaches** Dataset contains information about all of the public beaches that can be found in Galway City. This dataset is not particularly useful when used solely but could be integrated with another dataset or as a part of an application.

The data is in CSV format (Comma Separated Values), obtained from [Galway City Beaches](https://data.gov.ie/dataset/galway-city-beaches).

#### Size, Fields & Values.
The file cointains 4 unique rows. Each row has 8 fields with associated values.

| Field         | Description     |
|:-----:|:-------------------------------------------------------------:|
| **ObjectID**  | An ID given to each beach. |
| **Name**      | Name of the beach    |
| **Lat**       | The latitude coordinate of the beach  |
| **Long**      | The longitude coordinate of the beach |
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

### Bathing Water Compliance

The **Bathing Water Compliance** Dataset is divided in four files and each file detailed information about Galway Beaches. This dataset was chosen as a compliment for the Galway City Beaches Dataset.

The data is in four separeted files, each one has information about one of the Galway City main beaches. The files are in PDF format (Portable Document Format), obtained from [Bathing Water Compliance](https://data.gov.ie/dataset/bathing-water-compliance).

#### Size, Fields & Values.
Only a few information of this dataset are going to be used in this API.
Here is a breakdown of each field:

| Field | Description   |
|:--------:|:--------------------------------:|
| **Bathing Water** | Name of the beach. |
| **Bathing Water Code** | An ID given to each beach. |
| **Facilities** | Facilities in the beach eg.: Toilets, Disabled Access, Livesaving, etc. |
| **Water Depth** | The maximum depth of the water. |
| **Number of visitors** | Maximun number of visitors in high season. |
| **Risks** | Risks that may be found on the beach. |
| **Water Quality** | Status of the bathing water. |

## Example Entry

With this API, you can get the information returned in JSON (default) or XML format using the GET method at the following URL:

`` http://galwaycitybeaches.com/beaches/[name] `` where the name section requires the user input.

The response has the following properties:

- **ObjectID** : An ID given to each Beach
- **Name**:	Name of the beach
- **Lat**: The latitude coordinate of the beach
- **Long**: The longitude coordinate of the beach
- **EastITM**: Irish Transverse Mercator (ITM) East value. *
- **NorthITM**: Irish Transverse Mercator (ITM) North vaule.
- **EastIG**: East Irish Grid Reference number. **
- **NorthIG**: North Irish Grid Reference number.
- **Facilities**: List of the facilities in the beach eg.: Toilets,Disabled Access,Livesaving,etc.
- **Water Depth**: The maximun depth of the water.
- **Number of visitors**: Maximun number of visitors in high seanson.
- **Risks**: List of risks that may be found on the beach.
- **Water Quality**: Status of the bathing water.

**Here's an example for the Salthill Beach in JSON format.**

```json
{
    "ObjectID": "IEWEBWC170_0000_0200",
    "Name": "Salthill Beach",
    "Lat": "53.257",
    "Long": "-9.091",
    "EastITM": "527186.209",
    "NorthITM": "723523.15",
    "EastIG": "127219.731",
    "NorthIG": "223493.59",
    "Facilities":[
                    "Toilets",
                    "Car Parking",
                    "Disabled Access",
                    "FirstAid",
                    "Sensitive Area",
                    "Livesaving"
                 ],
    "Water Depth": "5.5m",
    "Number of Visitors": "2500",
    "Risks":[
                "Gentian hill pumping station(Overflow)",
                "The mutton island waste water treatment(Polution)",
                "Recreational boating and charter shipping(Discharge/Polution)",
                "Rainwater discharges"
            ],
    "Water Quality": "Good"
}
```
**And the equivalent in XML format:**

```xml
<Beach>
    <ObjectID>IEWEBWC170_0000_0200</ObjectID>
    <Name>Salthill Beach</Name>
    <Lat>53.257 <\Lat>
    <Long>-9.091</Long>
    <EastITM>527186.209</EastITM>
    <NorthITM>723523.15</NorthITM>
    <EastIG>127219.731</EastIG>
    <NorthIG>223493.59</NorthIG>
    <Facilities>
    	<Facilitie>Toilets</Facility>
       <Facility>Car Parking</Facility>
       <Facility>Disabled Access</Facility>
       <Facility>FirstAid</Facility>
       <Facility>Sensitive Area</Facility>
       <Facility>Livesaving</Facility>
    </Facilities>
    <WaterDepth>5.5m</WaterDepth>
    <NumberofVisitors>2500</NumberofVisitors>
    <Risks>
    	<Risk>Gentian hill pumping station(Overflow)</Risk>
        <Risk>The mutton island waste water treatment(Polution)</Risk>
        <Risk>Recreational boating and charter shipping(Discharge/Polution)</Risk>
        <Risk>Rainwater discharges</Risk>
    </Risks>        
    <WaterQuality>Good</WaterQuality>
</Beach>
```
## Accessing The Dataset

### Receiving A List of All Beaches
You can receive a list of all the beaches in Galway, using the HTTP POST method, at the following URL:

`http://galwaycitybeaches.com/beaches/all`

In this case, using "all" after ".../beaches/" will return an array of all the parks, in JSON format. The XML version can be obtain using `http://galwaycitybeaches.com/beaches/all/xml`

**JSON Example:**

```json
[
    {
        "ObjectID": "IEWEBWC170_0000_0200",
        "Name": "Salthill Beach",
        "Lat": "53.257",
        "Long": "-9.091",
        "EastITM": "527186.209",
        "NorthITM": "723523.15",
        "EastIG": "127219.731",
        "NorthIG": "223493.59",
        "Facilities":[
                        "Toilets",
                        "Car Parking",
                        "Disabled Access",
                        "FirstAid",
                        "Sensitive Area",
                        "Livesaving"
                     ],
        "Water Depth": "5.5m",
        "Number of Visitors": "2500",
        "Risks":[
                    "Gentian hill pumping station(Overflow)",
                    "The mutton island waste water treatment(Polution)",
                    "Recreational boating and charter shipping(Discharge/Polution)",
                    "Rainwater discharges"
                ],
        "Water Quality": "Good"
    },
    { ... },
    { ... }
]
```
**XML Example:**

```xml
<Beaches>
    <Beach>
        <ObjectID>IEWEBWC170_0000_0200</ObjectID>
        <Name>Salthill Beach</Name>
        <Lat>53.257 <\Lat>
        <Long>-9.091</Long>
        <EastITM>527186.209</EastITM>
        <NorthITM>723523.15</NorthITM>
        <EastIG>127219.731</EastIG>
        <NorthIG>223493.59</NorthIG>
        <Facilities>
           <Facility>Toilets</Facility>
           <Facility>Car Parking</Facility>
           <Facility>Disabled Access</Facility>
           <Facility>FirstAid</Facility>
           <Facility>Sensitive Area</Facility>
           <Facility>Livesaving</Facility>
        </Facilities>
        <WaterDepth>5.5m</WaterDepth>
        <NumberofVisitors>2500</NumberofVisitors>
        <Risks>
            <Risk>Gentian hill pumping station(Overflow)</Risk>
            <Risk>The mutton island waste water treatment(Polution)</Risk>
            <Risk>Recreational boating and charter shipping(Discharge/Polution)</Risk>
            <Risk>Rainwater discharges</Risk>
        </Risks>        
        <WaterQuality>Good</WaterQuality>
    </Beach>
    <Beach> ... </Beach>
    <Beach> ... </Beach>
</Beaches>
```

### Accessing Lists of Parks Using Filters
You can request a list of beaches based on a filter, by that I mean, all beaches where that specific filter is true, such as, toilets facilities using the HTTP GET method. The following is a URL example of the format you would use to achieve this.

`http://galwaycitybeaches.com/beaches/?[filter]=[parameter]`

Now, replace [filter] with a field from the dataset, which could be any of the fields including: objectid, name, facility. etc.

Then replace [parameter] with the results you are looking for.

#####Examples

1. `http://galwaycitybeaches.com/beaches/?Name=Ballyloughane+Beach/`

This would return the information about the Ballyloughane Beach in a JSON format.

**Sample:**

```json
{
    "ObjectID": "IEWEBWT170_0700_0200",
    "Name": "Ballyloughane Beach",
    "Lat": "53.27",
    "Long": "-9.018",
    "EastITM": "532120.388",
    "NorthITM": "724841.274",
    "EastIG": "132154.971",
    "NorthIG": "224812.027",
    "Facilities":[
                    "Toilets",
                    "Car Parking",
                    "Disabled Access",
                    "FirstAid",
                    "Livesaving"
                 ],
    "Water Depth": "1.0m",
    "Number of Visitors": "500",
    "Risks":[
                "Waste Water Treatment plant(Polution)",
                "Public Toilets and On site waste water treatment systems(Polution)",
                "Surface Water Outfalls and Storm Overflow"
            ],
    "Water Quality": "Poor"
}
```

2. `http://galwaycitybeaches.com/beaches/?WaterQuality=Good/xml`

This would return an array of all the beaches that have a Water Quality mark as Good, in a XML format. If there isn't any beach with that filter, an empty array is returned.

**Sample:**

```xml
<Beaches>
    <Beach>
        <ObjectID>IEWEBWC170_0000_0200</ObjectID>
        <Name>Salthill Beach</Name>
        <Lat>53.257 \Lat>
        <Long>-9.091</Long>
        <EastITM>527186.209</EastITM>
        <NorthITM>723523.15</NorthITM>
        <EastIG>127219.731</EastIG>
        <NorthIG>223493.59</NorthIG>
        <Facilities>
           <Facility>Toilets</Facility>
           <Facility>Car Parking</Facility>
           <Facility>Disabled Access</Facility>
           <Facility>FirstAid</Facility>
           <Facility>Sensitive Area</Facility>
           <Facility>Livesaving</Facility>
        </Facilities>
        <WaterDepth>5.5m</WaterDepth>
        <NumberofVisitors>2500</NumberofVisitors>
        <Risks>
            <Risk>Gentian hill pumping station(Overflow)</Risk>
            <Risk>The mutton island waste water treatment(Polution)</Risk>
            <Risk>Recreational boating and charter shipping(Discharge/Polution)</Risk>
            <Risk>Rainwater discharges</Risk>
        </Risks>        
        <WaterQuality>Good</WaterQuality>
    </Beach>
    <Beach> ... </Beach>
    <Beach> ... </Beach>
</Beaches>
```

#### Multiple Filters
To search for beachs in a more complet way, one can use more then one filter, is just as easy as using one filter.

`http://galwaycitybeaches.com/beaches/?[filter]=[parameter]&[filter]=[parameter]`

#####Examples

1. `http://galwaycitybeaches.com/beaches/?facility=Toiles&facility=Sensitive+Area/`

This would return an array with the beaches, where both facilities are available. In this particular case the array contains Salthill Beach and Silverstrand beach. 

**Sample:**

```json
[
    {
        "ObjectID": "IEWEBWC170_0000_0200",
        "Name": "Salthill Beach",
        "Lat": "53.257",
        "Long": "-9.091",
        "EastITM": "527186.209",
        "NorthITM": "723523.15",
        "EastIG": "127219.731",
        "NorthIG": "223493.59",
        "Facilities":[
                        "Toilets",
                        "Car Parking",
                        "Disabled Access",
                        "FirstAid",
                        "Sensitive Area",
                        "Livesaving"
                     ],
        "Water Depth": "5.5m",
        "Number of Visitors": "2500",
        "Risks":[
                    "Gentian hill pumping station(Overflow)",
                    "The mutton island waste water treatment(Polution)",
                    "Recreational boating and charter shipping(Discharge/Polution)",
                    "Rainwater discharges"
                ],
        "Water Quality": "Good"
    },
    { 
        "ObjectID": "IEWEBWC170_0000_0100",
        "Name": "Silverstrand Beach",
        "Lat": "53.251",
        "Long": "-9.128",
        "EastITM": "524694.732",
        "NorthITM": "722864.026",
        "EastIG": "12727.719",
        "NorthIG": "222834.31",
        "Facilities":[
                        "Toilets",
                        "Car Parking",
                        "Disabled Access",
                        "FirstAid",
                        "Sensitive Area",
                        "Livesaving"
                     ],
        "Water Depth": "2m",
        "Number of Visitors": "600",
        "Risks":[
                    "Public Toilets - on-site waste water treatment system(Polution)",
                    "Waste Water Treatment plant(Polution)",
                    "Gentian Hill Pumping Station(Overflow/Polution)"
                ],
        "Water Quality": "Good" 
        }
]
```
2. `http://galwaycitybeaches.com/beaches/?WaterDepth=2&NumberofVisitors=600/xml`

**Sample:**

```xml
<Beach>
    <ObjectID>IEWEBWC170_0000_0100</ObjectID>
    <Name>Silverstrand Beach</Name>
    <Lat>53.251<\Lat>
    <Long>-9.128</Long>
    <EastITM>524694.732</EastITM>
    <NorthITM>722864.026</NorthITM>
    <EastIG>12727.719</EastIG>
    <NorthIG>222834.31</NorthIG>
    <Facilities>
       <Facility>Toilets</Facility>
       <Facility>Car Parking</Facility>
       <Facility>Disabled Access</Facility>
       <Facility>FirstAid</Facility>
       <Facility>Sensitive Area</Facility>
       <Facility>Livesaving</Facility>
    </Facilities>
    <WaterDepth>2m</WaterDepth>
    <NumberofVisitors>600</NumberofVisitors>
    <Risks>
        <Risk>Public Toilets - on-site waste water treatment system(Polution)</Risk>
        <Risk>Waste Water Treatment plant(Polution)</Risk>
        <Risk>Gentian Hill Pumping Station(Overflow/Polution)</Risk>
    </Risks>        
    <WaterQuality>Good</WaterQuality>
</Beach>
```




