# Extract station matrix from SQLite3 database

Extract station matrix from SQLite3 database

## Usage

``` r
bike_stations(bikedb, city)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database. If no directory
  specified, it is presumed to be in
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

- city:

  Optional city (or vector of cities) for which stations are to be
  extracted

## Value

Matrix containing data for each station

## Examples

``` r
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
# or download some real data!
# dl_bikedata (city = 'la', data_dir = data_dir)
bikedb <- file.path (data_dir, 'testdb')
store_bikedata (data_dir = data_dir, bikedb = bikedb)
# create database indexes for quicker access:
index_bikedata_db (bikedb = bikedb)

stations <- bike_stations (bikedb)
head (stations)

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files (data_dir, pattern = '.zip'))
} # }
```
