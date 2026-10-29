# Example of OpenStreetMap road network

Example of OpenStreetMap road network

## Format

An sf object

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
[`read_table_builder()`](https://docs.ropensci.org/stplanr/reference/read_table_builder.md),
[`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md),
[`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md),
[`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md),
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md),
[`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)

## Examples

``` r
osm_net_example
#> Simple feature collection with 71 features and 5 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.535904 ymin: 53.79979 xmax: -1.524435 ymax: 53.80682
#> Geodetic CRS:  WGS 84
#> First 10 features:
#>      osm_id      highway                   name lanes maxspeed
#> 1   5082947     tertiary  Cross Stamford Street  <NA>     <NA>
#> 2   6013279        trunk Sheepscar Street South     2   30 mph
#> 3   6018346     tertiary                   <NA>     1     <NA>
#> 4   6018347     tertiary  Cross Stamford Street     2     <NA>
#> 5   6072857 unclassified                Mabgate  <NA>   30 mph
#> 6   6072858  residential            Bell Street  <NA>     <NA>
#> 7   6072859 unclassified           Byron Street  <NA>     <NA>
#> 8   6242167     tertiary           Skinner Lane     1     <NA>
#> 9  23091062     tertiary             Cherry Row     2   30 mph
#> 10 23091370      footway            Hill Street  <NA>     <NA>
#>                          geometry
#> 1  LINESTRING (-1.531854 53.80...
#> 2  LINESTRING (-1.532834 53.80...
#> 3  LINESTRING (-1.532293 53.80...
#> 4  LINESTRING (-1.531854 53.80...
#> 5  LINESTRING (-1.533278 53.79...
#> 6  LINESTRING (-1.532694 53.80...
#> 7  LINESTRING (-1.532978 53.80...
#> 8  LINESTRING (-1.532765 53.80...
#> 9  LINESTRING (-1.529449 53.80...
#> 10 LINESTRING (-1.527111 53.80...
```
