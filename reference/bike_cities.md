# List of cities currently included in bikedata

List of cities currently included in bikedata

## Usage

``` r
bike_cities()
```

## Value

A `data.frame` of cities, abbreviations, and names of bike systems
currently able to be accessed.

## Examples

``` r
bike_cities ()
#>    city     city_name      bike_system
#> 1    bo        Boston           Hubway
#> 2    ch       Chicago            Divvy
#> 3    dc Washington DC CapitalBikeShare
#> 4    gu   Guadalajara           mibici
#> 5    la   Los Angeles            Metro
#> 6    lo        London        Santander
#> 7    mo      Montreal             Bixi
#> 8    mn   Minneapolis         NiceRide
#> 9    ny      New York         Citibike
#> 10   ph  Philadelphia           Indego
#> 11   sf      Bay Area       FordGoBike
```
