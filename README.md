# Sydney Liveability Analysis

## Overview

This repository contains an analysis of liveability across Sydney suburbs using a variety of datasets. The aim is to evaluate and compare the liveability scores of different neighborhoods based on factors such as accommodation, schools, retail, health, and crime.

## Dataset Description

The analysis utilizes several datasets:

- **CSV Files**:
  - `Neighbourhood.csv`: Data related to neighborhood attributes.
  - `BusinessStats.csv`: Business statistics relevant to the analysis.

- **Shapefiles**:
  - `school_catchments.shp`: Spatial data representing school catchment areas.
  - `sa2.shp`: Statistical Area Level 2 boundaries.
  - `break_and_enter.shp`: Spatial data for break-and-enter incidents.

- **GeoJSON Files**:
  - `Greenhouse_Gas_Emissions.geojson`: Spatial data on greenhouse gas emissions by suburb.
  - `Library_Locations.geojson`: Locations of libraries across Sydney.

The pre-processing of all datasets involved standardizing the format and attributes, with minor adjustments based on specific dataset requirements.

## Spatial Data Optimization

Given the large size of the spatial datasets (some exceeding 2000 rows), three GiST indexes were created to enhance performance:

- **Catchments**: Index for the school catchments data.
- **Break and Enter**: Index for the break-and-enter incidents.
- **Greenhouse Gas**: Index for the greenhouse gas emissions data.

These indexes significantly reduced query times and improved the efficiency of spatial joins during the analysis.

## Liveability Score Calculation

The Liveability Score for each suburb was calculated using z-scores for various factors:
- Retail
- Accommodation
- School
- Health
- Crime

These factors were combined to produce an overall liveability score for each suburb. The analysis then compared these scores with median income and median rent to assess correlations.

## Results

The analysis revealed the following key findings:

- **Monthly Rent**: There is a positive correlation between the liveability score and average monthly rent. Suburbs with higher liveability scores tend to have higher rents. For neighborhoods with a liveability score above 0.6, monthly rents are generally above $2000. For neighborhoods scoring below 0.6, the average monthly rent ranges from $1000 to $2000.

- **Annual Household Income**: There is also a positive correlation between the liveability score and median annual household income, though this correlation is weaker compared to that with monthly rent. Most families in the dataset earn less than $50,000 annually.

- **Top and Bottom Neighborhoods**: Using the liveability scores, the analysis identified the top 5 most liveable and the 5 least liveable neighborhoods in Sydney. These results are displayed in the Jupyter notebook provided in the repository.

## Files in the Repository

- `Liveability_Analysis.ipynb`: Jupyter notebook containing the analysis and visualizations.
- `Neighbourhood.csv`: CSV file with neighborhood data.
- `BusinessStats.csv`: CSV file with business statistics.
- `school_catchments.shp`, `sa2.shp`, `break_and_enter.shp`: Shapefiles for spatial data.
- `Greenhouse_Gas_Emissions.geojson`, `Library_Locations.geojson`: GeoJSON files for spatial data.


