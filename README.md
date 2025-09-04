# Air-Quality-Trainings - Module 04: CAMS Visualization

**Author: Shima Shams (NCAR)**

**Updates: Alqamah Sayeed (UAH)**

This notebook analyzes and visualizes atmospheric composition data from the Copernicus Atmosphere Monitoring Service (CAMS) ECMWF Atmospheric Composition Reanalysis 4 dataset.

The notebook performs the following steps:

1.  **Setup and Data Download:**
    *   Mounts Google Drive to access and store data.
    *   Installs necessary libraries (cartopy, cdsapi).
    *   Imports required Python libraries for data handling, analysis, and visualization.
    *   Defines file paths for data input, output, and plots.
    *   Specifies the chemical species of interest ('no2', 'pm2p5', or 'go3').
    *   Sets the time range and geographical boundaries for data download.
    *   Downloads atmospheric data using the CDS API, checking if files already exist.

2.  **Data Processing and Unit Conversion:**
    *   Includes functions to calculate air density and specific humidity (although these functions are not explicitly used in the subsequent plotting cells).
    *   Sets a display name for the selected chemical species.
    *   Reads downloaded NetCDF files using xarray, handling potential longitude wrapping.
    *   Combines data from multiple files based on whether they represent different variables or time periods.
    *   Renames time dimensions and sorts data chronologically.
    *   Saves or loads the processed hourly data to/from a NetCDF file.
    *   Displays global metadata from the dataset.
    *   Performs unit conversions for the selected species (PM2.5 to µg/m³, NO2 and O3 to ppbv).
    *   Calculates and saves or loads daily averages from a NetCDF file.

3.  **Data Visualization:**
    *   Plots recent 3-hourly or daily average concentrations for a specified city (Guatemala City in the example) with AQI background coloring.
    *   Estimates and displays monthly average concentrations.
    *   Saves the monthly averaged data to a NetCDF file.
    *   Loads the saved monthly data.
    *   Plots global monthly maps of the selected species for specified time steps, using either a continuous colormap or an AQI-based colormap.
    *   Plots time series of monthly concentrations for multiple cities, with each city on a separate subplot and a trend line for each city.
    *   Calculates and plots annual average concentrations for multiple cities, including a trend line for each city.
