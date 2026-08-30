# Extract station-to-station trip matrix or data.frame from SQLite3 database

Extract station-to-station trip matrix or data.frame from SQLite3
database

## Usage

``` r
bike_tripmat(
  bikedb,
  city,
  start_date,
  end_date,
  start_time,
  end_time,
  weekday,
  member,
  birth_year,
  gender,
  standardise = FALSE,
  long = FALSE,
  quiet = FALSE
)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database. If no directory
  specified, it is presumed to be in
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

- city:

  City for which tripmat is to be aggregated

- start_date:

  If given (as year, month, day) , extract only those records from and
  including this date

- end_date:

  If given (as year, month, day), extract only those records to and
  including this date

- start_time:

  If given, extract only those records starting from and including this
  time of each day

- end_time:

  If given, extract only those records ending at and including this time
  of each day

- weekday:

  If given, extract only those records including the nominated weekdays.
  This can be a vector of numeric, starting with Sunday=1, or
  unambiguous characters, so "sa" and "tu" for Saturday and Tuesday.

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

  If TRUE, numbers of trips are standardised to the operating durations
  of each stations, so trip numbers are increased for stations that have
  only operated a short time, and vice versa.

- long:

  If FALSE, a square tripmat of (num-stations, num_stations) is
  returned; if TRUE, a long-format matrix of (stn-from, stn-to, ntrips)
  is returned.

- quiet:

  If FALSE, progress is displayed on screen

## Value

If `long = FALSE`, a square matrix of numbers of trips between each
station, otherwise a long-form tibble with three columns of of
(`start_station_id, end_station_id, numtrips`).

## Note

The `city` parameter should be given for databases containing data from
multiple cities, otherwise most of the resultant trip matrix is likely
to be empty. Both dates and times may be given either in numeric or
character format, with arbitrary (or no) delimiters between fields.
Single numeric times are interpreted as hours, with 24 interpreted as
day's end at 23:59:59.

If `standardise = TRUE`, the trip matrix will have the same number of
trips, but they will be re-distributed as described, with more recent
stations having more trips than older stations. Trip number are also
non-integer in this case, whereas they are always integer-valued for
`standardise = FALSE`.

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


tm <- bike_tripmat (bikedb = bikedb, city = "ny") # full trip matrix
tm <- bike_tripmat (bikedb = bikedb, city = "ny",
                    start_date = 20161201, end_date = 20161201)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", start_time = 1)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", start_time = "01:00")
tm <- bike_tripmat (bikedb = bikedb, city = "ny", end_time = "01:00")
tm <- bike_tripmat (bikedb = bikedb, city = "ny",
                    start_date = 20161201, start_time = 1)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", start_date = 20161201,
                    end_date = 20161201, start_time = 1, end_time = 2)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", weekday = 5)
tm <- bike_tripmat (bikedb = bikedb, city = "ny",
                    weekday = c("f", "sa", "th"))
tm <- bike_tripmat (bikedb = bikedb, city = "ny",
                    weekday = c("f", "th", "sa"))
tm <- bike_tripmat (bikedb = bikedb, city = "ny", member = 1)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", birth_year = 1976)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", birth_year = 1976:1990)
tm <- bike_tripmat (bikedb = bikedb, city = "ny", gender = "f")
tm <- bike_tripmat (bikedb = bikedb, city = "ny",
                    gender = "m", birth_year = 1976:1990)

bike_rm_test_data (data_dir = data_dir)
bike_rm_db (bikedb)
# don't forget to remove real data!
# file.remove (list.files (data_dir, pattern = ".zip"))
} # }
```
