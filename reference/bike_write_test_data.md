# Writes test data bundled with package to zip files

Writes very small test files to disk that can be used to test the
package. The entire package works by reading zip-compressed data files
provided by the various hire bicycle systems. This function generates
some equivalent data that can be read into an `SQLite` database by the
[`store_bikedata()`](https://docs.ropensci.org/bikedata/reference/store_bikedata.md)
function, so that all other package functionality can then be tested
from the resultant database. This function is also used in the examples
of all other functions.

## Usage

``` r
bike_write_test_data(data_dir = tempdir())
```

## Arguments

- data_dir:

  Directory in which data are to be extracted. Defaults to
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html). If any other
  directory is specified, files ought to be removed with
  [`bike_rm_test_data()`](https://docs.ropensci.org/bikedata/reference/bike_rm_test_data.md).

## Examples

``` r
if (FALSE) { # \dontrun{
bike_write_test_data ()
list.files (tempdir ())
bike_rm_test_data ()

bike_write_test_data (data_dir = '.')
list.files ()
bike_rm_test_data (data_dir = '.')
} # }
```
