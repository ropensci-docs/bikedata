# Download hire bicycle data

Download data for subsequent storage via
[store_bikedata](https://docs.ropensci.org/bikedata/reference/store_bikedata.md).

## Usage

``` r
dl_bikedata(city, data_dir = tempdir(), dates = NULL, quiet = FALSE)

download_bikedata(city, data_dir = tempdir(), dates = NULL, quiet = FALSE)
```

## Arguments

- city:

  City for which to download bike data, or name of corresponding bike
  system (see Details below).

- data_dir:

  Directory to which to download the files

- dates:

  Character vector of dates to download data with dates formated as
  YYYYMM.

- quiet:

  If FALSE, progress is displayed on screen

## Note

Only files that don't already exist in `data_dir` will be downloaded,
and this function may thus be used to update a directory of files by
downloading more recent files. If a particular file request fails,
downloading will continue regardless. To ensure all files are
downloaded, this function may need to be run several times until a
message appears declaring that 'All data files already exist'

## Details

This function produces (generally) zip-compressed data in R's temporary
directory. City names are not case sensitive, and must only be long
enough to unambiguously designate the desired city. Names of
corresponding bike systems can also be given. Currently possible cities
(with minimal designations in parentheses) and names of bike hire
systems are:

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

Ensure you have a fast internet connection and at least 100 Mb space

## Examples

``` r
if (FALSE) { # \dontrun{
dl_bikedata (city = 'New York City USA', dates = 201601:201613)
} # }
```
