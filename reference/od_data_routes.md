# Example segment-level route data

See `data-raw/generate-data.Rmd` for details on how this was created.
The dataset shows routes between origins and destinations represented in
`od_data_lines`

## Format

A data frame (tibble) object

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
[`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md),
[`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md),
[`od_data_lines`](https://docs.ropensci.org/stplanr/reference/od_data_lines.md),
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
od_data_routes
#> Simple feature collection with 750 features and 10 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.55995 ymin: 53.80248 xmax: -1.51099 ymax: 53.83041
#> Geodetic CRS:  WGS 84
#> First 10 features:
#>    route_number               name distances time busynance elevations
#> 1             2       Gledhow Lane       308   88      1252   112.5263
#> 2             2  Gledhow Wood Road        27    4        69   111.0000
#> 3             2       Gledhow Lane       281   52       738   106.5000
#> 4             2       Gledhow Lane       143   31       433    84.0000
#> 5             2       Gledhow Lane       550  315      3455    96.6250
#> 6             2 King George Avenue        19    4        37   110.0000
#> 7             2        Church Lane        98   15       157   107.1429
#> 8             2        Town Street        83   26       368   105.5556
#> 9             3       Gledhow Lane       308   88      1252   112.5263
#> 10            3  Gledhow Wood Road        27    4        69   111.0000
#>    start_longitude start_latitude finish_longitude finish_latitude
#> 1         -1.51667       53.82868         -1.53556        53.82829
#> 2         -1.51667       53.82868         -1.53556        53.82829
#> 3         -1.51667       53.82868         -1.53556        53.82829
#> 4         -1.51667       53.82868         -1.53556        53.82829
#> 5         -1.51667       53.82868         -1.53556        53.82829
#> 6         -1.51667       53.82868         -1.53556        53.82829
#> 7         -1.51667       53.82868         -1.53556        53.82829
#> 8         -1.51667       53.82868         -1.53556        53.82829
#> 9         -1.51667       53.82868         -1.55106        53.82410
#> 10        -1.51667       53.82868         -1.55106        53.82410
#>                          geometry
#> 1  LINESTRING (-1.51667 53.828...
#> 2  LINESTRING (-1.52108 53.829...
#> 3  LINESTRING (-1.52148 53.829...
#> 4  LINESTRING (-1.52482 53.830...
#> 5  LINESTRING (-1.52606 53.829...
#> 6  LINESTRING (-1.53391 53.829...
#> 7  LINESTRING (-1.53379 53.828...
#> 8  LINESTRING (-1.53441 53.828...
#> 9  LINESTRING (-1.51667 53.828...
#> 10 LINESTRING (-1.52108 53.829...
```
