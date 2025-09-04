# Air-Quality-Trainings - Module 04: VIIRS and AERONET AOD Comparison Summary

This notebook performs a comparison of Aerosol Optical Depth (AOD) data obtained from two different sources: the satellite-based VIIRS instrument and the ground-based AERONET network. The process involves several key steps:

1.  **Setup and Data Download:**
    *   Mounts Google Drive to access and save files.
    *   Installs necessary libraries like `netCDF4` and `xarray`.
    *   Sets up working directories and defines parameters for data download, including the base URL for NASA's LAADS website and an authentication token.
    *   Downloads VIIRS data files based on a provided list of URLs, checking if files already exist to avoid redundant downloads.
    *   Defines parameters for AERONET data download, including data level, averaging type, and geographical boundaries.
    *   Downloads AERONET data for a specific date and saves individual and merged CSV files.

2.  **Data Processing:**
    *   Reads and processes the downloaded VIIRS NetCDF files.
    *   Calculates a 5x5 moving average of the VIIRS AOD data to smooth out spatial variations.
    *   Combines data from multiple VIIRS files into a single pandas DataFrame.
    *   Calculates daily average VIIRS AOD.
    *   Reads and processes the downloaded AERONET data from CSV files.
    *   Replaces missing values (-999) with NaN in the AERONET data.
    *   Combines date and time information into a single datetime column.
    *   Calculates daily average AERONET AOD for each site.

3.  **Data Collocation:**
    *   Filters both VIIRS and AERONET daily average data to remove rows with missing AOD values.
    *   Converts latitude and longitude to radians for distance calculations.
    *   Iterates through each AERONET data point.
    *   Interpolates AERONET AOD to 550nm using cubic spline interpolation for consistency with VIIRS data.
    *   Finds the nearest VIIRS data point to each AERONET point based on date and geographical proximity.
    *   Calculates the distance between collocated points.
    *   Filters collocated data to include only points within a specified distance (100 km).
    *   Saves the collocated data to a CSV file.

4.  **Comparison and Visualization:**
    *   Loads the collocated data from the CSV file.
    *   Cleans the data by removing rows with missing values and filtering out outliers.
    *   Calculates statistical measures to compare the collocated VIIRS and AERONET AOD values (e.g., number of points, slope, correlation, bias, RMSE).
    *   Generates a 2D histogram scatter plot of VIIRS AOD vs. AERONET AOD to visualize the data distribution.
    *   Adds a regression line and a 1:1 line to the plot.
    *   Annotates the plot with the calculated statistical metrics.
    *   Saves the comparison plot as a PNG image file.

In essence, this notebook provides a comprehensive workflow for acquiring, processing, and comparing satellite-based and ground-based aerosol optical depth measurements to assess their agreement and identify potential biases.
