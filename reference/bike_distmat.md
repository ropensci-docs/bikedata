# Extract station-to-station distance matrix

Extract station-to-station distance matrix

## Usage

``` r
bike_distmat(bikedb, city, expand = 0.5, long = FALSE, quiet = TRUE)
```

## Arguments

- bikedb:

  A string containing the path to the SQLite3 database. If no directory
  specified, it is presumed to be in
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

- city:

  City for which tripmat is to be aggregated

- expand:

  Distances are calculated by routing through the OpenStreetMap street
  network surrounding the bike stations, with the street network
  expanded by this amount to ensure all stations can be connected.

- long:

  If FALSE, a square distance matrix of (num-stations, num_stations) is
  returned; if TRUE, a long-format matrix of (stn-from, stn-to,
  distance) is returned.

- quiet:

  If FALSE, progress is displayed on screen

## Value

If `long = FALSE`, a square matrix of numbers of trips between each
station, otherwise a long-form tibble with three columns of of
(start_station_id, end_station_id, distance)

## Note

Distance matrices returned from `bike_distamat` use all stations listed
for a given system, while trip matrices extracted with
[bike_tripmat](https://docs.ropensci.org/bikedata/reference/bike_tripmat.md)
will often have fewer stations because operational station numbers
commonly vary over time. The two matrices may be reconciled with the
`match_trips2dists` function, enabling then to be directly compared.
