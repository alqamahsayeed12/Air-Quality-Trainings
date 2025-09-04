# Air-Quality-Trainings - Module 01

# Ground Monitors by EPA

## Summary

This notebook provides code to visualize ground monitor data obtained from the EPA using the AirNow API. It allows users to display the locations of ground monitors on a map and visualize pollutant levels, likely related to air quality.

## Features

*   **Data Acquisition:** Downloads ground monitor data from the EPA AirNow API based on user-defined parameters (pollutants, time range, and geographic boundaries).
*   **Data Processing:** Processes the downloaded data to extract relevant information such as latitude, longitude, and pollutant values. It also calculates daily and average pollutant concentrations and categorizes data based on the Air Quality Index (AQI).
*   **Visualization:** Creates various map visualizations using `matplotlib` and `cartopy` to display monitor locations and pollutant levels. It also generates time series plots for individual locations.
*   **Data Handling:** Supports saving and loading data from Google Drive for persistent storage and analysis.

## Prerequisites

1.  **EPA AirNow API Account:** You need an API key from the EPA AirNow API to access the data. You can register for an account [here](https://docs.airnowapi.org/).
2.  **Google Colab:** This notebook is designed to be run in Google Colab.
3.  **Google Drive (Optional):** If you choose to save or load data from Google Drive, you will need to mount your Google Drive in Colab.

## Setup and Usage

1.  **Open the notebook in Google Colab.**
2.  **Install necessary libraries:** The notebook includes a cell to install `cartopy` using `pip`. Run this cell.
3.  **Mount Google Drive (Optional):** If you plan to use Google Drive for data storage, run the cell that mounts your Google Drive.
4.  **Configure Settings:**
    *   Set `PRE_FILL_SETTINGS` to `True` to use the predefined settings for geographic boundaries, time range, and API key.
    *   Set `PRE_FILL_SETTINGS` to `False` to be prompted to enter these settings manually.
    *   Configure data access options (`PREDOWNLOAD`, `SAVEDATA`, `GDRIVE`, `data_path`) based on your preferences for handling downloaded data.
5.  **Run the code cells sequentially.** The notebook will guide you through the steps of downloading data, processing it, and generating visualizations.
6.  **Provide input when prompted:** If `PRE_FILL_SETTINGS` is set to `False`, you will be asked to enter the required information for the analysis domain and API key. You will also be prompted to select the pollutant you want to analyze and the number of days to look back for time series plots.

## Code Overview

*   **Imports:** Imports necessary libraries including `pandas`, `matplotlib`, `cartopy`, `seaborn`, and `geopy`.
*   **`download_airnow_df` function:** Downloads air quality data from the AirNow API based on the provided parameters.
*   **`get_nearest_city_df` function:** (Requires geopy) Fetches the nearest city and country for given latitude and longitude coordinates.
*   **`plot_map` function:** Generates a scatter plot on a map to visualize data points with a continuous color scale.
*   **`plot_map_aqi` function:** Generates a scatter plot on a map to visualize data points using color-coded AQI categories.
*   **Data Processing and Plotting:** The main part of the notebook handles pollutant selection, data downloading (if not pre-downloaded), data cleaning, calculation of averages, and generation of various map and time series plots.

## Output

The notebook generates and displays various plots, including:

*   Average pollutant concentration map.
*   Average pollutant concentration map categorized by AQI.
*   Daily average pollutant concentration maps for the last 'n' days.
*   Daily or hourly time series plots of pollutant concentration for individual locations.

The generated map plots are also saved as PNG files in the specified `data_path`.

## Notes

*   Ensure you have a valid EPA AirNow API key before running the notebook.
*   Adjust the geographic boundaries and time range in the settings or when prompted to focus on your area and period of interest.
*   The `get_nearest_city_df` function relies on the Nominatim geocoding service, which has usage limits. Be mindful of this if you are processing a very large number of locations.
*   The AQI bins used in the `plot_map_aqi` function are based on standard EPA AQI breakpoints for the specified pollutants.
