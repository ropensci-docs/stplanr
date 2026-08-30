# Convert origin-destination data from wide to long format

This function takes a matrix representing travel between origins (with
origin codes in the `rownames` of the matrix) and destinations (with
destination codes in the `colnames` of the matrix) and returns a data
frame representing origin-destination pairs.

## Usage

``` r
odmatrix_to_od(odmatrix)
```

## Arguments

- odmatrix:

  A matrix with row and columns representing origin and destination zone
  codes and cells representing the flow between these zones.

## Details

The function returns a data frame with rows ordered by origin and then
destination zone code values and with names `orig`, `dest` and `flow`.

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
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
odmatrix <- od_to_odmatrix(flow)
odmatrix_to_od(odmatrix)
#>         orig      dest flow
#> 1  E02002361 E02002361  109
#> 8  E02002361 E02002363   38
#> 15 E02002361 E02002367   10
#> 22 E02002361 E02002371   44
#> 29 E02002361 E02002377   34
#> 36 E02002361 E02002382    7
#> 43 E02002361 E02002393   94
#> 2  E02002363 E02002361   30
#> 9  E02002363 E02002363  183
#> 16 E02002363 E02002367   11
#> 23 E02002363 E02002371   72
#> 30 E02002363 E02002377   13
#> 37 E02002363 E02002382    8
#> 44 E02002363 E02002393  156
#> 3  E02002367 E02002361    5
#> 10 E02002367 E02002363   84
#> 17 E02002367 E02002367   41
#> 24 E02002367 E02002371   66
#> 31 E02002367 E02002377    9
#> 38 E02002367 E02002382    9
#> 45 E02002367 E02002393   88
#> 4  E02002371 E02002361   20
#> 11 E02002371 E02002363  110
#> 18 E02002371 E02002367   27
#> 25 E02002371 E02002371  220
#> 32 E02002371 E02002377   58
#> 39 E02002371 E02002382   33
#> 46 E02002371 E02002393  165
#> 5  E02002377 E02002361   21
#> 12 E02002377 E02002363   30
#> 19 E02002377 E02002367    7
#> 26 E02002377 E02002371   62
#> 33 E02002377 E02002377  129
#> 40 E02002377 E02002382   53
#> 47 E02002377 E02002393   93
#> 6  E02002382 E02002361    8
#> 13 E02002382 E02002363    8
#> 20 E02002382 E02002367   12
#> 27 E02002382 E02002371   36
#> 34 E02002382 E02002377   46
#> 41 E02002382 E02002382   73
#> 48 E02002382 E02002393   94
#> 7  E02002393 E02002361   14
#> 14 E02002393 E02002363   14
#> 21 E02002393 E02002367    7
#> 28 E02002393 E02002371   39
#> 35 E02002393 E02002377   35
#> 42 E02002393 E02002382   26
#> 49 E02002393 E02002393  265
flow[1:9, 1:3]
#>        Area.of.residence Area.of.workplace All
#> 920573         E02002361         E02002361 109
#> 920575         E02002361         E02002363  38
#> 920578         E02002361         E02002367  10
#> 920582         E02002361         E02002371  44
#> 920587         E02002361         E02002377  34
#> 920591         E02002361         E02002382   7
#> 920601         E02002361         E02002393  94
#> 921220         E02002363         E02002361  30
#> 921222         E02002363         E02002363 183
odmatrix_to_od(od_to_odmatrix(flow[1:9, 1:3]))
#>         orig      dest flow
#> 1  E02002361 E02002361  109
#> 3  E02002361 E02002363   38
#> 5  E02002361 E02002367   10
#> 7  E02002361 E02002371   44
#> 9  E02002361 E02002377   34
#> 11 E02002361 E02002382    7
#> 13 E02002361 E02002393   94
#> 2  E02002363 E02002361   30
#> 4  E02002363 E02002363  183
```
