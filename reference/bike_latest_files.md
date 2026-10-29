# Check whether files in database are the latest published files

Check whether files in database are the latest published files

## Usage

``` r
bike_latest_files(bikedb)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database. If no directory
  specified, it is presumed to be in
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

## Value

A named vector of binary values: TRUE is files in `bikedb` are the
latest versions; otherwise FALSE, in which case `store_bikedata` could
be run to update the database.

## Examples

``` r
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
# or download some real data!
# dl_bikedata (city = 'la', data_dir = data_dir)
# Remove one London file that triggers an API call which may fail tests:
file.remove (file.path (tempdir(),
             "01aJourneyDataExtract10Jan16-23Jan16.csv"))
bikedb <- file.path (data_dir, 'testdb')
store_bikedata (data_dir = data_dir, bikedb = bikedb)
# bike_latest_files (bikedb)
# All false because test data are not current, but would pass with real data

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files (data_dir, pattern = '.zip'))
} # }
```
