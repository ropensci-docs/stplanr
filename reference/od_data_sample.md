# Example of origin-destination data from UK Census

See `data-raw/generate-data.Rmd` for details on how this was created.

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
[`od_data_routes`](https://docs.ropensci.org/stplanr/reference/od_data_routes.md),
[`osm_net_example`](https://docs.ropensci.org/stplanr/reference/osm_net_example.md),
[`read_table_builder()`](https://docs.ropensci.org/stplanr/reference/read_table_builder.md),
[`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md),
[`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md),
[`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md),
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md),
[`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)

## Examples

``` r
od_data_sample
#> # A tibble: 64 × 18
#>    geo_code1 geo_code2   all from_home light_rail train   bus  taxi motorbike
#>    <chr>     <chr>     <dbl>     <dbl>      <dbl> <dbl> <dbl> <dbl>     <dbl>
#>  1 E02002361 E02002361   109         0          0     0     4     2         0
#>  2 E02002361 E02002363    38         0          0     1     4     1         0
#>  3 E02002361 E02002367    10         0          0     0     1     0         0
#>  4 E02002361 E02002371    44         0          0     0     2     2         0
#>  5 E02002361 E02002377    34         0          0     0     0     1         2
#>  6 E02002361 E02002382     7         0          0     0     1     0         0
#>  7 E02002361 E02002384    53         0          0     1    10     1         0
#>  8 E02002361 E02002393    94         0          0     0    17     1         0
#>  9 E02002363 E02002361    30         0          0     0     0     1         1
#> 10 E02002363 E02002363   183         0          0     2    13     3         0
#> # ℹ 54 more rows
#> # ℹ 9 more variables: car_driver <dbl>, car_passenger <dbl>, bicycle <dbl>,
#> #   foot <dbl>, other <dbl>, geo_name1 <chr>, geo_name2 <chr>, la_1 <chr>,
#> #   la_2 <chr>
```
