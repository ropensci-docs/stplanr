# Example destinations data

This dataset represents trip destinations on a different geographic
level than the origins stored in the object `cents_sf`.

## Format

A spatial dataset with 87 features

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
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
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md),
[`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)

## Examples

``` r
destinations_sf
#> Simple feature collection with 87 features and 6 fields
#> Geometry type: POINT
#> Dimension:     XY
#> Bounding box:  xmin: -1.571298 ymin: 53.79647 xmax: -1.492713 ymax: 53.83734
#> Geodetic CRS:  WGS 84
#> First 10 features:
#>         WZ11CD   LAD11CD COWZEW_SG                     COWZEW_SGN COWZEW_G
#> 524  E33012352 E08000035         3                  Metro suburbs       3d
#> 1936 E33010351 E08000035         2                       Top jobs       2c
#> 2006 E33012331 E08000035         5 Manufacturing and distribution       5b
#> 2712 E33012280 E08000035         3                  Metro suburbs       3a
#> 2730 E33010390 E08000035         7            Servants of society       7c
#> 2799 E33012310 E08000035         3                  Metro suburbs       3d
#> 2996 E33012370 E08000035         3                  Metro suburbs       3a
#> 3133 E33009663 E08000035         2                       Top jobs       2b
#> 8057 E33013885 E08000035         3                  Metro suburbs       3d
#> 8648 E33012279 E08000035         3                  Metro suburbs       3b
#>                            COWZEW_GN                   geometry
#> 524    Suburban metro infrastructure POINT (-1.492713 53.81042)
#> 1936                   Big city life  POINT (-1.53781 53.80131)
#> 2006                Industrial units POINT (-1.533468 53.80576)
#> 2712    Metro surburban distribution POINT (-1.540438 53.81724)
#> 2730                 Major hospitals POINT (-1.540901 53.80167)
#> 2799   Suburban metro infrastructure POINT (-1.521311 53.81683)
#> 2996    Metro surburban distribution POINT (-1.530386 53.80194)
#> 3133           Adminstrative centres POINT (-1.532527 53.80963)
#> 8057   Suburban metro infrastructure  POINT (-1.56543 53.81388)
#> 8648 Cosmopolitan metro suburban mix POINT (-1.555112 53.82408)
```
