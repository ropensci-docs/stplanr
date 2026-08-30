# Extract coordinates from OD data

Extract coordinates from OD data

## Usage

``` r
od2odf(flow, zones)
```

## Arguments

- flow:

  A data frame representing origin-destination data. The first two
  columns of this data frame should correspond to the first column of
  the data in the zones. Thus in
  [`cents_sf()`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
  the first column is geo_code. This corresponds to the first two
  columns of
  [`flow()`](https://docs.ropensci.org/stplanr/reference/flow.md).

- zones:

  A spatial object representing origins (and destinations if no separate
  destinations object is provided) of travel.

## Details

Origin-destination (OD) data is often provided in the form of 1 line per
OD pair, with zone codes of the trip origin in the first column and the
zone codes of the destination in the second column (see the
[`vignette("stplanr-od")`](https://docs.ropensci.org/stplanr/articles/stplanr-od.html))
for details. `od2odf()` creates an 'origin-destination data frame', with
columns containing origin and destination codes (`flow`) that match the
first column in a a spatial (polygon or point `sf`) object (`zones`).

The function returns a data frame with coordinates for the origin and
destination.

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
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
od2odf(flow[1:2, ], zones_sf)
#> Converting geometry ID from factor to character
#>             o         d        ox       oy        dx       dy
#> 1   E02002361 E02002361 -1.514962 53.82911 -1.514962 53.82911
#> 1.1 E02002361 E02002363 -1.514962 53.82911 -1.535734 53.82863
```
