# Create matrices representing origin-destination coordinates

This function takes a wide range of input data types (spatial lines,
points or text strings) and returns a matrix of coordinates representing
origin (fx, fy) and destination (tx, ty) points.

## Usage

``` r
od_coords(from = NULL, to = NULL, l = NULL)
```

## Arguments

- from:

  An object representing origins (if lines are provided as the first
  argument, from is assigned to `l`)

- to:

  An object representing destinations

- l:

  Only needed if from and to are empty, in which case this should be a
  spatial object representing desire lines

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md),
[`od_id`](https://docs.ropensci.org/stplanr/reference/od_id.md),
[`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
od_coords(from = c(0, 52), to = c(1, 53)) # lon/lat coordinates
#>      fx fy tx ty
#> [1,]  0 52  1 53
od_coords(cents_sf[1:3, ], cents_sf[2:4, ]) # sf points
#>             fx       fy        tx       ty
#> [1,] -1.546463 53.80952 -1.511861 53.81161
#> [2,] -1.511861 53.81161 -1.524205 53.80410
#> [3,] -1.524205 53.80410 -1.550806 53.82442
# od_coords("Hereford", "Leeds") # geocode locations
od_coords(flowlines_sf[1:3, ])
#>             fx       fy        tx       ty
#> [1,] -1.516734 53.82887 -1.535617 53.82847
#> [2,] -1.516734 53.82887 -1.550807 53.82442
#> [3,] -1.516734 53.82887 -1.530712 53.81756
```
