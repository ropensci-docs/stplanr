# Convert a series of points into a dataframe of origins and destinations

Takes a series of geographical points and converts them into a
data.frame representing the potential flows, or 'spatial interaction',
between every combination of points.

## Usage

``` r
points2odf(p)
```

## Arguments

- p:

  A spatial points object

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
[`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md),
[`od_id`](https://docs.ropensci.org/stplanr/reference/od_id.md),
[`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md)

## Examples

``` r
points2odf(cents_sf)
#>            O         D
#> 1  E02002384 E02002384
#> 2  E02002384 E02002382
#> 3  E02002384 E02002393
#> 4  E02002384 E02002367
#> 5  E02002384 E02002363
#> 6  E02002384 E02002361
#> 7  E02002384 E02002377
#> 8  E02002384 E02002371
#> 9  E02002382 E02002384
#> 10 E02002382 E02002382
#> 11 E02002382 E02002393
#> 12 E02002382 E02002367
#> 13 E02002382 E02002363
#> 14 E02002382 E02002361
#> 15 E02002382 E02002377
#> 16 E02002382 E02002371
#> 17 E02002393 E02002384
#> 18 E02002393 E02002382
#> 19 E02002393 E02002393
#> 20 E02002393 E02002367
#> 21 E02002393 E02002363
#> 22 E02002393 E02002361
#> 23 E02002393 E02002377
#> 24 E02002393 E02002371
#> 25 E02002367 E02002384
#> 26 E02002367 E02002382
#> 27 E02002367 E02002393
#> 28 E02002367 E02002367
#> 29 E02002367 E02002363
#> 30 E02002367 E02002361
#> 31 E02002367 E02002377
#> 32 E02002367 E02002371
#> 33 E02002363 E02002384
#> 34 E02002363 E02002382
#> 35 E02002363 E02002393
#> 36 E02002363 E02002367
#> 37 E02002363 E02002363
#> 38 E02002363 E02002361
#> 39 E02002363 E02002377
#> 40 E02002363 E02002371
#> 41 E02002361 E02002384
#> 42 E02002361 E02002382
#> 43 E02002361 E02002393
#> 44 E02002361 E02002367
#> 45 E02002361 E02002363
#> 46 E02002361 E02002361
#> 47 E02002361 E02002377
#> 48 E02002361 E02002371
#> 49 E02002377 E02002384
#> 50 E02002377 E02002382
#> 51 E02002377 E02002393
#> 52 E02002377 E02002367
#> 53 E02002377 E02002363
#> 54 E02002377 E02002361
#> 55 E02002377 E02002377
#> 56 E02002377 E02002371
#> 57 E02002371 E02002384
#> 58 E02002371 E02002382
#> 59 E02002371 E02002393
#> 60 E02002371 E02002367
#> 61 E02002371 E02002363
#> 62 E02002371 E02002361
#> 63 E02002371 E02002377
#> 64 E02002371 E02002371
```
