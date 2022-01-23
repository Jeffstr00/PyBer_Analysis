# PyBer with Matplotlib

## Overview

As a new data analyst at PyBer, a ride-sharing company, the curiously-named V. Isualize has tasked us with analyzing company data and then visualizing our findings using Matplotlib.  Doing so would hopefully enable decision makers within the company to understand the data, see trends and correlations, and go on to hopefully make good, informed decisions for the company.  For this project, we were given a CSV file containing information on nearly 2400 rides and their corresponding location, date, and fare.  We were then specifically asked to see how the results break down by city type (urban, suburban, and rural).

## Results

To conduct the analysis, most of the work was done at a dataframe level (working with, combining, and manipulating them) rather than performing complicated mathematical work.  Once the ride and city dataframes were merged using `pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city", "city"])`, all we had to do was extract the data and then perform very basic calculations.  Total rides were found using `total_rides = pyber_data_df.groupby(["type"]).count()["ride_id"]` (which pulled all of the data on ride_id and seperated it by city type), and the same was done for both drivers and fares.  Once we had these totals, we could find averages simply by using `avg_ride_fare = total_fares / total_rides` and `avg_driver_fare = total_fares / total_drivers`.

![PyBer City Summary](https://github.com/Jeffstr00/PyBer_Analysis/blob/main/Resources/pyber_city_summary.png)

When looking at the results (total rides/drivers/fares and average fares per ride/driver), a crystal clear pattern can be observed when the data broken down by city type.  As population density increases (rural > suburban > urban), all of the totals rise accordingly even though the averages are inversely proportional to density and subsequently decrease.  This makes sense intuitively: in urban areas, ride sharing is going to be much more common due to people not having their own vehicles, difficulty or expensive parking, and the obviously larger population.  This is going to lead to a larger number of available drivers, which will in turn lower costs.  In rural areas where the need for ride sharing is more seldom and sporadic, there is not going to be a need for as many drivers, so a lower supply will lead to higher average costs.

## Summary
