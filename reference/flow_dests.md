# Data frame of invented commuter flows with destinations in a different layer than the origins

Data frame of invented commuter flows with destinations in a different
layer than the origins

## Usage

``` r
data(flow_dests)
```

## Format

A data frame with 49 rows and 15 columns

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
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
if (FALSE) { # \dontrun{
# This is how the dataset was constructed
flow_dests <- flow
flow_dests$Area.of.workplace <- sample(x = destinations$WZ11CD, size = nrow(flow))
flow_dests <- dplyr::rename(flow_dests, WZ11CD = Area.of.workplace)
devtools::use_data(flow_dests)
} # }
```
