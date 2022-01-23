# PyBer with Matplotlib

## Overview

As a new data analyst at PyBer, a ride-sharing company, the curiously-named V. Isualize has tasked us with analyzing company data and then visualizing our findings using Matplotlib.  Doing so would hopefully enable decision makers within the company to understand the data, see trends and correlations, and go on to hopefully make good, informed decisions for the company.  For this project, we were given a CSV file containing information on nearly 2400 rides and their corresponding location, date, and fare.  We were then specifically asked to see how the results break down by city type (urban, suburban, and rural).

## Results

To conduct the analysis, most of the work was done at a dataframe level (working with, combining, and manipulating them) rather than performing complicated mathematical work.  Once the ride and city dataframes were merged using `pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city", "city"])`, all we had to do was extract the data and then perform very basic calculations.  Total rides were found using `total_rides = pyber_data_df.groupby(["type"]).count()["ride_id"]` (which pulled all of the data on ride_id and separated it by city type), and the same was done for both drivers and fares.  Once we had these totals, we could find averages simply by using `avg_ride_fare = total_fares / total_rides` and `avg_driver_fare = total_fares / total_drivers`.

![PyBer City Summary](https://github.com/Jeffstr00/PyBer_Analysis/blob/main/analysis/pyber_city_summary.png)

When looking at the results (total rides/drivers/fares and average fares per ride/driver), a crystal clear pattern can be observed when the data is broken down by city type.  As population density increases (rural > suburban > urban), all of the totals rise accordingly.  However, the averages are inversely proportional to density and subsequently decrease.  This makes sense intuitively: in urban areas, ride sharing is going to be much more common due to people not having their own vehicles, difficulty or expensive parking, and the obviously larger population.  This is going to lead to a larger number of available drivers, which will in turn lower costs.  In rural areas where the need for ride sharing is more seldom and sporadic, there is not going to be a need for as many drivers, so a lower supply will lead to higher average costs.

## Summary

![Fares by City](https://github.com/Jeffstr00/PyBer_Analysis/blob/main/analysis/fares_by_city.png)
![PyBer Ride Sharing Data](https://github.com/Jeffstr00/PyBer_Analysis/blob/main/analysis/Fig1.png)

The observed disparities between city types indicates that quite a bit of potential might exist for making the company more profitable.  However, in order to do this, the company must determine how elastic or inelastic the demand for ride sharing is.  Clearly, people are willing to pay more for rides in rural areas than they are in urban areas.  However, what is the primary cause and what is the effect?  In other words, are fewer rural people using ride sharing because prices are high, or are prices high because of a lack of demand?  If prices were lowered, would an increase in rides compensate for the decrease in average cost?  In order to find this out, the company could experiment with changing the prices in certain markets and seeing how much it affects sales.

Once that is determined, the company has a few potential options for increasing profitability.  The fact that rural people are willing to pay more for rides indicates that urban people might be willing to pay more as well (if prices weren't driven down by increased supply).  After all, urban riders also probably have an overall greater need for ride sharing due to lower personal vehicle ownership, parking issues, etc. (however, to be fair, you also have to compete with public transportation, more cabs, or the option to walk, which all work to drive down prices).  Given how many urban rides there are, even a small increase in prices could lead to a great increase in profits (if, of course, those increase don't cause you to lose marketshare to other the aformentioned competition).

On the other side of the coin, the larger number of urban rides could indicate that potential could exist for increasing the number of rural rides.  If rural ride totals are currently being kept low by high prices and low number of drivers (which could equate to longer wait times), we could increase total rides by increasing our number of drivers and lowering prices.  Depending on how elastic the demand is, this increase might be more than enough to offset average prices going down, so it should definitely be explored.  Given how high rural prices are, even small increases in number of rides would lead to decent gains.

<p float="left">
  <img src="https://github.com/Jeffstr00/PyBer_Analysis/blob/main/analysis/Fig5.png" width="400" />
  <img src="https://github.com/Jeffstr00/PyBer_Analysis/blob/main/analysis/Fig6.png" width="400" />
</p>

Basically, it all boils down to this: do you try to increase profits by making urban areas more like rural by increasing their prices, or do you do try to increase the number of rural rides to make them more like urban areas (or both)?  While totals are much higher in urban areas, rural rides are proportionally more profitable.  The company has two basic options for increasing profitability.  First, they could try to raise the currently low prices in urban areas to make them more in line with the higher rural prices.  On the other hand, they could try to make rural rides more common, which would obviously lead to higher profits (as long as it didn't cause prices to fall too much).
