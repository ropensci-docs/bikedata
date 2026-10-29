# Count number of entries in sqlite3 database tables

Count number of entries in sqlite3 database tables

## Usage

``` r
bike_db_totals(bikedb, trips = TRUE, city)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database.

- trips:

  If true, numbers of trips are counted; otherwise numbers of stations

- city:

  Optional city for which numbers of trips are to be counted

## Examples

``` r
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
bikedb <- file.path (data_dir, 'testdb')
# latest_lo_stns is set to FALSE just to avoid download on CRAN; this should
# normally remain at default value of TRUE:
store_bikedata (data_dir = data_dir, bikedb = bikedb, latest_lo_stns = FALSE)
# create database indexes for quicker access:
index_bikedata_db (bikedb = bikedb)

bike_db_totals (bikedb = bikedb, trips = TRUE) # total trips
bike_db_totals (bikedb = bikedb, trips = TRUE, city = 'ch')
bike_db_totals (bikedb = bikedb, trips = TRUE, city = 'ny')
bike_db_totals (bikedb = bikedb, trips = FALSE) # total stations
bike_db_totals (bikedb = bikedb, trips = FALSE, city = 'ch')
bike_db_totals (bikedb = bikedb, trips = FALSE, city = 'ny')
# numbers of stations can also be extracted with
nrow (bike_stations (bikedb = bikedb))
nrow (bike_stations (bikedb = bikedb, city = 'ch'))

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files ('.', pattern = '.zip'))
} # }
```
