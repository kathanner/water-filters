# Read Me — Water Filters Recommendations based on Contaminants

a classification modeling project that leverages the California Open Data Portal

## Dataset

From the California Department of Water Resources (DWR), lab and field results for drinking water quality are considered. The recorded results are dated from 1903 to 2020. For this project, data recorded before 2010 are not included in the modeling.

The dataset contains information about the water station where the sample was taken and the tested contaminant results. There are over 300 contaminants included in this dataset. The preprocessing objective for this model is to identify the key contaminants that are monitored by the State of California and the type of water filter that is able to help remove these contaminants from drinking water.

This dataset is primarily sourced from the state of California's Open Data website: https://data.ca.gov/dataset/water-quality-data

### California State Water Resources Control Board

Comparison of maximum contaminant levels (MCLs) for Regulated Contaminants in Drinking Water:
* 56 contaminants monitored by the State of California are contained in the dataset
* If the measured test result for a contaminate exceeds the MCL, a water filter may help extract that contaminate and increase the water quality

The dataset includes contaminant measurements from the California maximum contaminant levels (MCLs) published here: https://www.waterboards.ca.gov/drinking_water/certlic/drinkingwater/MCLsandPHGs.html

## CDC Water Filter Recommendations and WHO Water Quality Guidelines 

The Centers for Disease Control and Prevention (CDC) has outlined water filters and treatment devices to help the public understand which type of water filter will help improve the quality of water having specific contaminants or qualities. Aliging with this information, he following water filter treatment devices are used for this project: 

* Activated Carbon Filter
* Ion Exchange Unit
* Reverse Osmosis
* Distillation

To read more, please visit the CDC's website: https://www.cdc.gov/healthywater/drinking/home-water-treatment/water-filters/step3.html

Additionally, the World Health Organization (WHO) states that Turbidity at 4 NTU and above is visibly contaminated. They recommend that large municipal water suppliers achieve a Turbidity sample result of 0.5 NTU before disinfection and ideally average a result of 0.2 NTU or less. 

You can read the latest guidelines for drinking water here: https://www.who.int/water_sanitation_health/publications/drinking-water-quality-guidelines-4-including-1st-addendum/en/

## Primary Regulated Contaminants by California Regions

The California census data shows 10 regions in the state (https://census.ca.gov/regions/). In this dataset considering records from 2010 to 2020 only, Orange County and San Diego did not have any regulated contaminate data. So, this model focuses on the following regions:

* Superior California
* North Coast
* San Francisco
* Northern San Joaquin Valley
* Central Coast
* Southern San Joaquin Valley
* Inland Empire
* Los Angeles

After reviewing the CDC's water filter recommendations, the following contaminants and characteristics are the primary considerations for selecting a type of water filter:

* Turbidity
* Hardness
* Copper
* Lead
* Nitrates and Nitrites 
* Barium
* Fluoride 

**Locations of the Key Contaminants and Characteristics**

![contaminants_bylocation.png](attachment:contaminants_bylocation.png)

### Copper and Lead

While the contaminant levels of copper and lead are below the California MCL, there are still recorded levels in the drinking water. This may affect taste and other water characteristics.

**Contaminant Levels by Region**

![region_copper_lead.png](attachment:region_copper_lead.png)

Year over year, the amount of Lead in drinking water has decreased but there is still room for improvement regarding Copper. According to the CDC water filter recommendations, an Activated Carbon Filter will help improve the quality of water containing Lead and Copper.

**Copper by Region Year Over Year**

![yoy_copper.png](attachment:yoy_copper.png)

**Lead by Region Year Over Year**

![yoy_lead.png](attachment:yoy_lead.png)

### Nitrites and Nitrates

Nitrates are on the rise in most regions and are over the MCL in four regions primarily in the Northern part of the state. Reverse Osmosis can help remove these contaminants.

**Location of Nitrates Exceeding MCL**

![map_nitrates.png](attachment:map_nitrates.png)

**Nitrates Exceed California MCL in these Regions**

![region_nitrate_exceeds_mcl.png](attachment:region_nitrate_exceeds_mcl.png)

Nitrates dropped around 2016 but currently show a steady increase across the regions.

**Nitrates by Region Year Over Year**

![yoy_nitrate.png](attachment:yoy_nitrate.png)

Nitrites are rising again in 2020 in most of the regions except for Superior California and Los Angeles.

**Nitrites by Region Year Over Year**

![yoy_nitrite.png](attachment:yoy_nitrite.png)

## Classification Model

After running multiple variations in the modeling notebook, Random Forest with Smote performed the best. Review the model here: <a href="modeling_keys.ipynb">modeling_keys.ipynb</a>

![model_summary.png](attachment:model_summary.png)

![model_confusionmatrix.png](attachment:model_confusionmatrix.png)

## Water Filter Recommendations and Future Applications

Based on the regulated contaminant levels, the classification model is able to recommend one of the following four water filters by California region and the key contaminant test results:

* Activated Carbon Filter
* Ion Exchange Unit
* Reverse Osmosis
* Distillation

Future iterations: this model could be extended to recommend a water filter at the county or city level. 
