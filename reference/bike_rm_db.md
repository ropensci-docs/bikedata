# Remove SQLite3 database generated with 'store_bikedat()'

If no directory is specified the `bikedb` argument passed to
`store_bikedata`, the database is created in
[`tempdir()`](https://rdrr.io/r/base/tempfile.html). This function
provides a convenient way to remove the database in such cases by simply
passing the name.

## Usage

``` r
bike_rm_db(bikedb)
```

## Arguments

- bikedb:

  The SQLite3 database containing the bikedata.

## Value

TRUE if `bikedb` successfully removed; otherwise FALSE

## Examples

``` r
if (FALSE) { # \dontrun{
data_dir <- tempdir ()
bike_write_test_data (data_dir = data_dir)
# or download some real data!
# dl_bikedata (city = "la", data_dir = data_dir)
bikedb <- file.path (data_dir, "testdb")
store_bikedata (data_dir = data_dir, bikedb = bikedb)

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files (data_dir, pattern = ".zip"))
} # }
```
