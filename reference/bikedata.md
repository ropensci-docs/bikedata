# Download and aggregate data from public bicycle hire systems

Download data from all public bicycle hire systems which provide open
data, currently including

- Santander Cycles London, U.K.

- citibike New York City NY, U.S.A.

- Divvy Chicago IL, U.S.A.

- Capital BikeShare Washingon DC, U.S.A.

- Hubway Boston MA, U.S.A.

- Metro Los Angeles CA, U.S.A.

## Download and store data

- `dl_bikedata` Download data for particular cities and dates

- `store_bikedata` Store data in `SQLite3` database

## Sample data for testing package

- `bike_test_data` Description of test data included with package

- `bike_write_test_data` Write test data to disk in form precisely
  reflecting data provided by all systems

- `bike_rm_test_data` Remove data written to disk with
  `bike_write_test_data`

## Functions to aggregate trip data

- `bike_daily_trips` Aggregate daily time series of total trips

- `bike_stations` Extract table detailing locations and names of bicycle
  docking stations

- `bike_tripmat` Extract aggregate counts of trips between all pairs of
  stations within a given city

## Summary Statistics

- `bike_summary_stats` Overall quantitative summary of database
  contents. All of the following functions provide individual aspects of
  this summary.

- `bike_db_totals` Count total numbers of trips or stations, either for
  entire database or a specified city.

- `bike_datelimits` Return dates of first and last trips, either for
  entire database or a specified city.

- `bike_demographic_data` Simple table indicating which cities include
  demographic parameters with their data

- `bike_latest_files` Check whether files contained in database are
  latest published versions

## See also

Useful links:

- <https://docs.ropensci.org/bikedata/>

- <https://github.com/ropensci/bikedata>

- Report bugs at <https://github.com/ropensci/bikedata/issues>

## Author

Mark Padgham
