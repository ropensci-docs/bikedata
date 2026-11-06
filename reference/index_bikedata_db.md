# Add indexes to database created with store_bikedata

Add indexes to database created with store_bikedata

## Usage

``` r
index_bikedata_db(bikedb)
```

## Arguments

- bikedb:

  The SQLite3 database containing the bikedata.

## Examples

``` r
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
# or download some real data!
# dl_bikedata (city = "la", data_dir = data_dir)
bikedb <- file.path (data_dir, "testdb")
store_bikedata (data_dir = data_dir, bikedb = bikedb)
# create database indexes for quicker access:
index_bikedata_db (bikedb = bikedb)

trips <- bike_tripmat (bikedb = bikedb, city = "LA") # trip matrix
stations <- bike_stations (bikedb = bikedb) # station data

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files (data_dir, pattern = ".zip"))
} # }
```
