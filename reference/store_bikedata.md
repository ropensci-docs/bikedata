# Store hire bicycle data in SQLite3 database

Store previously downloaded data (via the
[dl_bikedata](https://docs.ropensci.org/bikedata/reference/dl_bikedata.md)
function) in a database for subsequent extraction and analysis.

## Usage

``` r
store_bikedata(
  bikedb,
  city,
  data_dir,
  dates = NULL,
  latest_lo_stns = TRUE,
  quiet = FALSE
)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database to use. If it
  doesn't already exist, it will be created, otherwise data will be
  appended to existing database. If no directory specified, it is
  presumed to be in [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

- city:

  One or more cities for which to download and store bike data, or names
  of corresponding bike systems (see Details below).

- data_dir:

  A character vector giving the directory containing the data files
  downloaded with `dl_bikedata` for one or more cities. Only if this
  parameter is missing will data be downloaded.

- dates:

  If specified and no `data_dir` is given, data are downloaded and
  stored only for these dates specified as vector of YYYYMM values.

- latest_lo_stns:

  If `TRUE` (default), download latest version of London stations;
  otherwise use potentially obsolete internal version. (This parameter
  should not need to be changed, but can be set to `FALSE` to avoid
  external calls; for example when not online.)

- quiet:

  If FALSE, progress is displayed on screen

## Value

Number of trips added to database

## Note

Data for different cities may all be stored in the same database, with
city identifiers automatically established from the names of downloaded
data files. This function can take quite a long time to execute, and may
generate an SQLite3 database file several gigabytes in size.

## Details

City names are not case sensitive, and must only be long enough to
unambiguously designate the desired city. Names of corresponding bike
systems can also be given. Currently possible cities (with minimal
designations in parentheses) and names of bike hire systems are:

|                             |                    |
|-----------------------------|--------------------|
| Boston (bo)                 | Hubway             |
| Chicago (ch)                | Divvy Bikes        |
| Washington, D.C. (dc)       | Capital Bike Share |
| Los Angeles (la)            | Metro Bike Share   |
| London (lo)                 | Santander Cycles   |
| Minnesota (mn)              | NiceRide           |
| New York City (ny)          | Citibike           |
| Philadelphia (ph)           | Indego             |
| San Francisco Bay Area (sf) | Ford GoBike        |

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
