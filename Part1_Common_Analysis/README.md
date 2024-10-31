# Part 1: Common Analysis
This is the first part of what will culminate in a final project for DATA 512.
Part 1 gets the ball rolling on an interesting topic regarding wildfires and air quality in cities. This repo analyzes wildfire data acquired from [USGS](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). This data is cleaned, analyzed, and used to make insights into fires that occurred near the city of Gainesville, FL over the course of 60 years from 1961 to 2020.

### License and TOU of source data

[Source](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)) for fire feature data used in all notebooks.

[Source](https://aqs.epa.gov/aqsweb/documents/data_api.html) for daily air quality data used by `aqi.ipynb`.

Use of any code or data products must adhere to citing the proper source: `Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3`.

Any use of the EPA API must follow the [terms of service](https://aqs.epa.gov/aqsweb/documents/data_api.html#terms).

### Creating Virtual Environment and Installing Python Packages
Python version 3.8 or greater is required.

The following instructions create a virtual environment (isolated region for Python packages), activates the environment for use, and installs required python packages:

> virtualenv -p python3 part1

> source part1/bin/activate

> pip install -r requirements.txt

### Credentials for EPA API

In order to leverage the [EPA API](https://aqs.epa.gov/aqsweb/documents/data_api.html#terms) in the jupyter notebooks of this package, follow the instructions found in `aqi.ipynb`. This notebook will help setup an EPA account, obtain an API token, and provides helper functions to leverage the API. 

### Data Products

The `datasets` directory contains a sample bit of data to use as a replacement to the full dataset. The full dataset is too large to include in this repo, please refer to links of full data above.

Associated data products can be produced from `data_clean.ipynb`.

### Special Data Considerations and Assumptions
The raw data contains measurements from as early as the late 1800s -- however, for the sake of the analysis done in this repo, the data is cleaned to focus on data in the timeframe of 1961-2020.

See `data_clean.ipynb` for how the full raw data is cleaned up to produce a subset of data that is then used for analysis.

### Notebook Descriptions

* `data_clean.ipynb`: This notebook takes data downloaded from [USGS](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) and cleans the data to produce a data product that consists of the largest fire features for each fire for every year in the span of 1961-2020.

* `visualization.ipynb`: This notebook leverages the data product produced from `data_clean.ipynb` to create visualization for analysis.

*`aqi.ipynb`: This notebook uses the EPA API to get daily measurements of air quality devices for Gainesville, FL. The AQI for each daily measurement is collect and visualized annually for analysis purposes. This notebook also attempts to develop a custom `smoke metric` which is a proxy for how impactful the smoke from fires near Gainesville have affected the city.
