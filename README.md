# PyBer-Analysis
Finished Jupyter Notebook Deliverable: [PyBer Challenge](/PyBer_Challenge.ipynb)
  
## Overview
Using Pandas and Matplotlib in Jupyter Notebook, I completed a ride-sharing analysis by city type.  The summary will help leadership at PyBer make future decisions concerning driver count and fare amount in urban, suburban, and rural cities.
    
## Resources
Here are the csv files containing the datasets:     
[City Data](/Resources/city_data.csv)   
[Ride Data](/Resources/ride_data.csv)

## Results
Right away, it's clear that the number of drivers is really high in urban cities and really low in rural cities.  Suburban cities are in the middle.  Total fares and total rides follow the same pattern: 
* Urban cities see the highest fares at just under $40K
* Rural cities see the lowest fares at just over $4K
* Urban cities see the highest rides rides at 1,625
* Rural cities see the lowest rides at 125  
I used the 'groupby' function in association with aggregate functions like 'sum()' and 'count()' in order to calculate these numbers.  As an example, here's the total fares solution:  
```  
total_fares = pyber_data_df.groupby(["type"]).sum()["fare"]
```  
### Total Fare by City Type between January 1st and April 29th  
![PyBer Fare Summary](/Analysis/PyBer_fare_summary.png "PyBer Fare Summary")  
This weekly view shows a trend by city type for total fare.  During this time, it is evident that the fare trend is fairly similar when comparing city to city.  In total, urban is always the highest, suburban is always in the middle, and rural is always the lowest.  Generally, they move in the same direction.   
After summing fares, summing drivers, and counting total rides, I was able to calculate "average fare per ride" and "average fare per driver."  
```  
average_fare_per_ride = total_fares / total_rides
```  
```  
average_fare_per_driver = total_fares / driver_count
```  
Interestingly, average fare per ride and driver were both higher in rural cities at $34.62 and $55.49 respectively.  In suburban cities, it's $30.97 per ride and $39.50 per driver.  In urban cities, it's $24.53 per ride and $16.57 per driver.  
It is clear that PyBer charges a higher fare in areas where they have less available drivers.  

## Summary 
Because driver counts vary so much between cities, PyBer has decisions to make about where to place them, when to place them where, and how much to charge for rides.  I would recommend implementing the following:
* Station drivers closer to their home towns
  -Less distance traveled between rides will cut down on costs and keep customers happy with lower wait times
  -This may mean employing more drivers who have rurual homes, or keeping existing drivers driving customers in rural areas while their is demand there (route optimization)
* When urban drivers leave the city for rides, have them fulfill the demand outside of the cities before heading back to the city
  -This will help fulfill demand, lower wait times, and decongest the cities with an abundance of drivers
  -As a bonus, allow non-urban riders to schedule rides ahead of time so that PyBer can better plan routes
* Consider changing the way fares are charged in order to push the averages between city types closer together
  -Look at charging per unit of distance, per trip, or even subscription based plans
  -Implement minimuns in cities to avoid cost burdens from short trips, and give suburban and urban riders a discount if they are traveling close to customers in demand
