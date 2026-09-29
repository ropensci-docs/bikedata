# Match rows and columns of distance and trip matrices

Match rows and columns of distance and trip matrices

## Usage

``` r
bike_match_matrices(mat1, mat2)
```

## Arguments

- mat1:

  A wide- or long-form trip or distance matrix returned from
  [`bike_tripmat`](https://docs.ropensci.org/bikedata/reference/bike_tripmat.md)
  or
  [`bike_distmat`](https://docs.ropensci.org/bikedata/reference/bike_distmat.md).

- mat2:

  The corresponding distance or trip matrix.

## Value

A list of the same matrices with matching start and end stations, and in
the same order passed to the routine (that is, `mat1` then `mat2`). Each
kind of matrix will be identified and named accordingly as either "trip"
or "dist". Matrices are returned in same format (long or wide) as
submitted.

## Note

Distance matrices returned from `bike_distamat` use all stations listed
for a given system, while trip matrices extracted with
[bike_tripmat](https://docs.ropensci.org/bikedata/reference/bike_tripmat.md)
will often have fewer stations because operational station numbers
commonly vary over time. This function reconciles the two matrices
through matching all row and column names (or just station IDs for
long-form matrices), enabling then to be directly compared.
