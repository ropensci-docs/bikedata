# Static summary of which systems provide demographic data

Static summary of which systems provide demographic data

## Usage

``` r
bike_demographic_data()
```

## Value

A `data.frame` detailing the kinds of demographic data provided by the
different systems

## Examples

``` r
bike_demographic_data ()
#>    city     city_name      bike_system demographic_data
#> 1    bo        Boston           Hubway             TRUE
#> 2    ch       Chicago            Divvy             TRUE
#> 3    dc Washington DC CapitalBikeShare            FALSE
#> 4    gu   Guadalajara           mibici             TRUE
#> 5    la   Los Angeles            Metro            FALSE
#> 6    lo        London        Santander            FALSE
#> 7    mo      Montreal             Bixi            FALSE
#> 8    mn   Minneapolis         NiceRide             TRUE
#> 9    ny      New York         Citibike             TRUE
#> 10   ph  Philadelphia           Indego            FALSE
#> 11   sf      Bay Area       FordGoBike             TRUE
# Examples of filtering data by demographic parameters:
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
bikedb <- file.path (data_dir, "testdb")
store_bikedata (data_dir = data_dir, bikedb = bikedb)
# create database indexes for quicker access:
index_bikedata_db (bikedb = bikedb)

sum (bike_tripmat (bikedb = bikedb, city = "bo")) # 200 trips
sum (bike_tripmat (bikedb = bikedb, city = "bo", birth_year = 1990)) # 9
sum (bike_tripmat (bikedb = bikedb, city = "bo", gender = "f")) # 22
sum (bike_tripmat (bikedb = bikedb, city = "bo", gender = 2)) # 22
sum (bike_tripmat (bikedb = bikedb, city = "bo", gender = 1)) # = m; 68
sum (bike_tripmat (bikedb = bikedb, city = "bo", gender = 0)) # = n; 9
# Sum of gender-filtered trips is less than total because \code{gender = 0}
# extracts all registered users with unspecified genders, while without
# gender filtering extracts all trips for registered and non-registered
# users.

# The following generates an error because Washinton DC's DivvyBike system
# does not provide demographic data
sum (bike_tripmat (bikedb = bikedb, city = "dc", birth_year = 1990))
bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
} # }
```
