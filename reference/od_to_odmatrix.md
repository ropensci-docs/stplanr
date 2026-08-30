# Convert origin-destination data from long to wide format

This function takes a data frame representing travel between origins
(with origin codes in `name_orig`, typically the 1st column) and
destinations (with destination codes in `name_dest`, typically the
second column) and returns a matrix with cell values (from `attrib`, the
third column by default) representing travel between origins and
destinations.

## Usage

``` r
od_to_odmatrix(flow, attrib = 3, name_orig = 1, name_dest = 2)
```

## Arguments

- flow:

  A data frame representing flows between origin and destinations

- attrib:

  A number or character string representing the column containing the
  attribute data of interest from the `flow` data frame

- name_orig:

  A number or character string representing the zone of origin

- name_dest:

  A number or character string representing the zone of destination

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
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
od_to_odmatrix(flow)
#>           E02002361 E02002363 E02002367 E02002371 E02002377 E02002382 E02002393
#> E02002361       109        38        10        44        34         7        94
#> E02002363        30       183        11        72        13         8       156
#> E02002367         5        84        41        66         9         9        88
#> E02002371        20       110        27       220        58        33       165
#> E02002377        21        30         7        62       129        53        93
#> E02002382         8         8        12        36        46        73        94
#> E02002393        14        14         7        39        35        26       265
od_to_odmatrix(flow[1:9, ])
#>           E02002361 E02002363 E02002367 E02002371 E02002377 E02002382 E02002393
#> E02002361       109        38        10        44        34         7        94
#> E02002363        30       183        NA        NA        NA        NA        NA
od_to_odmatrix(flow[1:9, ], attrib = "Bicycle")
#>           E02002361 E02002363 E02002367 E02002371 E02002377 E02002382 E02002393
#> E02002361         2         0         0         3         0         0         0
#> E02002363         1         5        NA        NA        NA        NA        NA
```
