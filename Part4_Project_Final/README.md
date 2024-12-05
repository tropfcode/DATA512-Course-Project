# DATA 512 Final Project: The community of Gainesville, Florida as a Case Study for understanding Wildfires, Air Quality, Population Health, and Data Collection

## Project Description
See `Report.pdf` for full description of project, data used, and analysis.

This repo holds the report, notebook, code, and data products for the final project of DATA 512.
This project was tasked with developing a method to understand how the city and general region of Gainesville, FL is affected by wildfire smoke and if a relatively acceptable model could be developed to help inform government officials and legislators to make actionable decisions.

## How to Run Code
### Creating Virtual Environment and Installing Python Packages
Python version 3.8 or greater is required.

The following instructions after cloning this repo to create a virtual environment (isolated region for Python packages), activate the environment for use, and install required python packages:

> cd ./Part4_Project_Final

> python3 -m venv data512

> source data512/bin/activate

> pip install -r requirements.txt


## Data Descriptions
Below are descriptions and associated license for each of the datasets used in this project.

### Wildfire Data
**Title**: Combined wildland fire datasets for the United States and certain territories, 1800s-Present (combined wildland fire polygons)

**Citation**: Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

**Website**: https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81

**Description**: A nested JSON based dataset that includes reported fires dating back to the mid 1800's to Present day.
Features for each fire include the `Fire_Year` and `GIS_Acres`. The primary feature `geometry` is composed of `ring` objects which can be interpreted by the python library `shapely` and used to plot with `folium` or an equivalent package that can interpret that datatype. The `geometry` feature represents the boundary of a fire, with each `ring` object acting as a point that makes up part of the perimeter of a fire.

### Air Quality Index Data
**Title**: EPA Air Quality System (AQS) database

**Citation**: US Environmental Protection Agency. Air Quality System Data Mart Air Quality System (AQS) API available via https://aqs.epa.gov/aqsweb/documents/data_api.html. Accessed November 01, 2024.

**Website**: https://aqs.epa.gov/aqsweb/documents/data_api.html

**Description**: Daily measurements of particulate and gaseous pollutants. Includes `aqi` measurements for a specific measurement site given a FIPS code for county and state. Follow directions to obtain data at website above.

**[EPA Terms of Service](https://aqs.epa.gov/aqsweb/documents/data_api.html#terms)**.

In order to leverage the [EPA API](https://aqs.epa.gov/aqsweb/documents/data_api.html#terms) in the jupyter notebooks of this package, follow the instructions found in `aqi.ipynb`. This notebook will help setup an EPA account, obtain an API token, and provides helper functions to leverage the API.

### Alachua County, Florida Asthma and Heart Attack Data
**Title**: Annual Asthma and Heart Attack Hospitalization Metrics

**Citation**: No explicit citation, see website below.

**Website**: https://www.floridatracking.com/healthtracking/topic.htm?i=10

**Description**: Annual aggregation of various hospitalization metrics for both asthma and heart attack events in Alachua County, FL. Data is in `.csv` format.

### Cartography Boundaries
**Title**: Cartographic Boundary File

**Citation**: U.S. Census Bureau, “Cartography Boundary File,” April 15, 2024, https://www.census.gov/programs-surveys/geography/technical-documentation/naming-convention/cartographic-boundary-file.html, accessed on November 15, 2024.

**Website**: https://www.census.gov/programs-surveys/geography/technical-documentation/naming-convention/cartographic-boundary-file.html

**Description**: Cartography Boundary Files used to plot wildfire ring data onto a map of the United States, specifically of the Southeast United States. See the boundary files under `notebooks/southeast`.

## Notebook Descriptions
*`aqi.ipynb`: This notebook uses the EPA API to get daily measurements of air quality devices for Gainesville, FL. The AQI for each daily measurement is collect and visualized annually for analysis purposes. This notebook also attempts to develop a custom `smoke metric` which is a proxy for how impactful the smoke from fires near Gainesville have affected the city.

*`wildfire.ipynb`: Creates a data product that is a subset of the full Wildfire dataset obtained from the USGS (see above). The subsequent data product is used in `analysis.ipynb` and this must be ran first.

*`analysis.ipynb`: Research grade notebook that uses data products from `aqi.ipynb` and `wildfire.ipynb` to conduct analysis, produce plots, and make conclusions.

## Intermediate Data Products
The `data_products` directory contains intermediate data products produced from the `aqi.ipynb` and `wildfire.ipynb` notebooks as well as manually curated data from the Florida Department of Health. The `wildfire.ipynb` notebook uses the wildfire dataset referenced above in the `Data Descreiption` section. That dataset is too large to include in this GitHub repo, so follow instructions within `wildfire.ipynb` to obtain that dataset.

Both `asthma.csv` and `heart.csv` are manually curated datasets that are raw data from the Florida Department of Health but transformed to be easier to turn into a `Pandas` dataframe.

Finally, `gas_output.csv` and `particulate_output.csv` are outputs from the `aqi.ipynb` notebook. These are intermediate data products of the AQI API for Gainesville, FL which include the daily AQI associated with particulate and gasous pollutants. See `aqi.ipynb` for full description.
