# Extract daily trip counts for all stations

Extract daily trip counts for all stations

## Usage

``` r
bike_daily_trips(
  bikedb,
  city,
  station,
  member,
  birth_year,
  gender,
  standardise = FALSE
)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database. If no directory
  specified, it is presumed to be in
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

- city:

  City for which trips are to be counted - mandatory if database
  contains data for more than one city

- station:

  Optional argument specifying bike station for which trips are to be
  counted

- member:

  If given, extract only trips by registered members (`member = 1` or
  `TRUE`) or not (`member = 0` or `FALSE`).

- birth_year:

  If given, extract only trips by registered members whose declared
  birth years equal or lie within the specified value or values.

- gender:

  If given, extract only records for trips by registered users declaring
  the specified genders (`f/m/.` or `2/1/0`).

- standardise:

  If TRUE, daily trip counts are standardised to the relative numbers of
  bike stations in operation for each day, so daily trip counts are
  increased during (generally early) periods with relatively fewer
  stations, and decreased during (generally later) periods with more
  stations.

## Value

A `data.frame` containing daily dates and total numbers of trips

## Examples

``` r
if (FALSE) { # \dontrun{
bike_write_test_data () # by default in tempdir ()
# dl_bikedata (city = "la", data_dir = data_dir) # or some real data!
store_bikedata (data_dir = tempdir (), bikedb = "testdb")
# create database indexes for quicker access:
index_bikedata_db (bikedb = "testdb")

bike_daily_trips (bikedb = "testdb", city = "ny")
bike_daily_trips (bikedb = "testdb", city = "ny", member = TRUE)
bike_daily_trips (bikedb = "testdb", city = "ny", gender = "f")
bike_daily_trips (bikedb = "testdb", city = "ny", station = "173",
                  gender = 1)

bike_rm_test_data ()
bike_rm_db ("testdb")
# don't forget to remove real data!
# file.remove (list.files (".", pattern = ".zip"))
} # }
```
