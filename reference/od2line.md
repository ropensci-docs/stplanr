# Convert origin-destination data to spatial lines

Origin-destination ('OD') flow data is often provided in the form of 1
line per flow with zone codes of origin and destination centroids. This
can be tricky to plot and link-up with geographical data. This function
makes the task easier.

## Usage

``` r
od2line(
  flow,
  zones,
  destinations = NULL,
  zone_code = names(zones)[1],
  origin_code = names(flow)[1],
  dest_code = names(flow)[2],
  zone_code_d = NA,
  silent = FALSE
)
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

- destinations:

  A spatial object representing destinations of travel flows.

- zone_code:

  Name of the variable in `zones` containing the ids of the zone. By
  default this is the first column names in the zones.

- origin_code:

  Name of the variable in `flow` containing the ids of the zone of
  origin. By default this is the first column name in the flow input
  dataset.

- dest_code:

  Name of the variable in `flow` containing the ids of the zone of
  destination. By default this is the second column name in the flow
  input dataset or the first column name in the destinations if that is
  set.

- zone_code_d:

  Name of the variable in `destinations` containing the ids of the zone.
  By default this is the first column names in the destinations.

- silent:

  TRUE by default, setting it to TRUE will show you the matching columns

## Details

Origin-destination (OD) data is often provided in the form of 1 line per
OD pair, with zone codes of the trip origin in the first column and the
zone codes of the destination in the second column (see the
[`vignette("stplanr-od")`](https://docs.ropensci.org/stplanr/articles/stplanr-od.html))
for details. `od2line()` creates a spatial (linestring) object
representing movement from the origin to the destination for each OD
pair. It takes data frame containing origin and destination cones
(`flow`) that match the first column in a a spatial (polygon or point)
object (`zones`).

## See also

Other od:
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
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
od_data <- stplanr::flow[1:20, ]
l <- od2line(flow = od_data, zones = cents_sf)
plot(sf::st_geometry(cents_sf))
plot(l, lwd = l$All / mean(l$All), add = TRUE)
#> Warning: ignoring all but the first attribute
```
