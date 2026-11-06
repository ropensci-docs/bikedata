# Removes test data written with 'bike_write_test_data()'

The function
[`bike_write_test_data()`](https://docs.ropensci.org/bikedata/reference/bike_write_test_data.md)
writes several small zip-compressed files to disk. The default location
is [`tempdir()`](https://rdrr.io/r/base/tempfile.html), in which case
these files will be automatically removed on termination of current R
session. If, however, any other value for `data_dir` is passed to
[`bike_write_test_data()`](https://docs.ropensci.org/bikedata/reference/bike_write_test_data.md),
then the resultant files ought be deleted by calling this function.

## Usage

``` r
bike_rm_test_data(data_dir = tempdir())
```

## Arguments

- data_dir:

  Directory in which data were extracted.

## Value

Number of files successfully removed, which should equal six.

## Examples

``` r
if (FALSE) { # \dontrun{
bike_write_test_data ()
list.files (tempdir ())
bike_rm_test_data ()

bike_write_test_data (data_dir = getwd ())
list.files ()
bike_rm_test_data (data_dir = getwd ())
} # }
```
