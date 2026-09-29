# Test data for all 6 cities

A data set containing for each of the six cities a `data.frame` object
of 200 trips.

## Usage

``` r
bike_test_data
```

## Format

A list of one data frame for each of the five cities of (bo, dc, la, lo,
ny), plus two more for chicago stations and trips (ch_st, ch_tr). Each
of these (except "ch_st") contains 200 representative trips.

## Note

These data are only used to convert to `.zip`-compressed files using
[`bike_write_test_data()`](https://docs.ropensci.org/bikedata/reference/bike_write_test_data.md).
These `.zip` files can be subsequently read into an SQLite3 database
using `store_bikedata`.
