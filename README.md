# Air-Quality-Trainings - Module-5: GEOS-FP

The code compares the PM2.5 data from the EPA and GEOS-FP model for several cities.

Here's a breakdown of what the code does:

1. **Defines Cities:** A dictionary `cities` stores the names and coordinates of the cities for comparison.
2. **Sets Date Range:** A date range is defined for fetching and processing data.
3. **Loads Datasets:** It loads the GEOS-FP data (assuming it's already downloaded in the specified directory) and the EPA PM2.5 data from a CSV file.
4. **Iterates through Cities:** The code loops through each city in the `cities` dictionary.
5. **Processes EPA Data:** For each city, it filters the EPA DataFrame to find the closest monitoring station to the city's coordinates using the `find_closest_lat_lon` function (which calculates distances using the Haversine formula). It then cleans the data, converts the time to datetime objects, and resamples it to a 3-hour mean.
6. **Processes GEOS-FP Data:** It extracts the GEOS-FP PM2.5 data for the nearest grid point to the city's coordinates. If the processed GEOS-FP data for a city doesn't exist as a CSV, it creates one; otherwise, it loads the existing CSV.
7. **Merges and Renames DataFrames:** The EPA and GEOS-FP data are merged based on time, and the columns are renamed for clarity.
8. **Plots Comparison:** The `plot_AQI` function is used to generate a time series plot comparing the EPA and GEOS-FP PM2.5 values for the city. The plot includes background colors representing different AQI categories.
9. **Displays Plots:** The generated plots for each city are displayed.

In summary, this code automates the process of comparing ground-based EPA PM2.5 measurements with model-based GEOS-FP PM2.5 forecasts for selected cities, providing a visual assessment of the model's performance against real-world data.
