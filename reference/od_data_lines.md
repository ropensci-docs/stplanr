# Example of desire line representations of origin-destination data from UK Census

Derived from `od_data_sample` showing movement between points
represented in `cents_sf`

## Format

A data frame (tibble) object

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
[`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md),
[`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md),
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
od_data_lines
#> Simple feature collection with 64 features and 18 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.550806 ymin: 53.8041 xmax: -1.511861 ymax: 53.82887
#> Geodetic CRS:  WGS 84
#> First 10 features:
#>    geo_code1 geo_code2 all from_home light_rail train bus taxi motorbike
#> 1  E02002361 E02002361 109         0          0     0   4    2         0
#> 2  E02002361 E02002363  38         0          0     1   4    1         0
#> 3  E02002361 E02002367  10         0          0     0   1    0         0
#> 4  E02002361 E02002371  44         0          0     0   2    2         0
#> 5  E02002361 E02002377  34         0          0     0   0    1         2
#> 6  E02002361 E02002382   7         0          0     0   1    0         0
#> 7  E02002361 E02002384  53         0          0     1  10    1         0
#> 8  E02002361 E02002393  94         0          0     0  17    1         0
#> 9  E02002363 E02002361  30         0          0     0   0    1         1
#> 10 E02002363 E02002363 183         0          0     2  13    3         0
#>    car_driver car_passenger bicycle foot other geo_name1 geo_name2  la_1  la_2
#> 1          39             3       2   59     0 Leeds 032 Leeds 032 Leeds Leeds
#> 2          24             4       0    4     0 Leeds 032 Leeds 034 Leeds Leeds
#> 3           8             0       0    1     0 Leeds 032 Leeds 038 Leeds Leeds
#> 4          28             3       3    6     0 Leeds 032 Leeds 042 Leeds Leeds
#> 5          19             3       0    9     0 Leeds 032 Leeds 048 Leeds Leeds
#> 6           5             1       0    0     0 Leeds 032 Leeds 053 Leeds Leeds
#> 7          30             4       4    3     0 Leeds 032 Leeds 055 Leeds Leeds
#> 8          55            10       0   10     1 Leeds 032 Leeds 064 Leeds Leeds
#> 9          18             3       1    6     0 Leeds 034 Leeds 032 Leeds Leeds
#> 10         58             1       5  101     0 Leeds 034 Leeds 034 Leeds Leeds
#>                          geometry
#> 1  LINESTRING (-1.516734 53.82...
#> 2  LINESTRING (-1.516734 53.82...
#> 3  LINESTRING (-1.516734 53.82...
#> 4  LINESTRING (-1.516734 53.82...
#> 5  LINESTRING (-1.516734 53.82...
#> 6  LINESTRING (-1.516734 53.82...
#> 7  LINESTRING (-1.516734 53.82...
#> 8  LINESTRING (-1.516734 53.82...
#> 9  LINESTRING (-1.535617 53.82...
#> 10 LINESTRING (-1.535617 53.82...
```
