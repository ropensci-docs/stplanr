# Spatial polygons of home locations for flow analysis.

These correspond to the `cents_sf` data.

## Details

- geo_code. the official code of the zone

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
[`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md),
[`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md),
[`od_data_lines`](https://docs.ropensci.org/stplanr/reference/od_data_lines.md),
[`od_data_routes`](https://docs.ropensci.org/stplanr/reference/od_data_routes.md),
[`od_data_sample`](https://docs.ropensci.org/stplanr/reference/od_data_sample.md),
[`osm_net_example`](https://docs.ropensci.org/stplanr/reference/osm_net_example.md),
[`read_table_builder()`](https://docs.ropensci.org/stplanr/reference/read_table_builder.md),
[`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md),
[`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md),
[`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md),
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md)

## Examples

``` r
library(sf)
zones_sf
#> Simple feature collection with 8 features and 4 fields
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -1.568904 ymin: 53.79758 xmax: -1.499425 ymax: 53.83613
#> Geodetic CRS:  WGS 84
#>       geo_code geo_label geo_labelw  avslope                       geometry
#> 654  E02002382 Leeds 053       <NA> 2.284782 POLYGON ((-1.513589 53.8157...
#> 1466 E02002367 Leeds 038       <NA> 5.091685 POLYGON ((-1.553587 53.8308...
#> 1803 E02002393 Leeds 064       <NA> 2.361707 POLYGON ((-1.530424 53.8109...
#> 3093 E02002361 Leeds 032       <NA> 3.589363 POLYGON ((-1.533519 53.8338...
#> 4500 E02002371 Leeds 042       <NA> 2.814496 POLYGON ((-1.545994 53.8249...
#> 6251 E02002363 Leeds 034       <NA> 3.076791 POLYGON ((-1.54344 53.83331...
#> 7422 E02002384 Leeds 055       <NA> 2.856563 POLYGON ((-1.546022 53.8170...
#> 7750 E02002377 Leeds 048       <NA> 2.762529 POLYGON ((-1.515997 53.8217...
plot(zones_sf)
```
