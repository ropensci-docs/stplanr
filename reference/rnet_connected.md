# Keep only segments connected to the largest group in a network

This function takes an sf object representing a road network and returns
only the parts of the network that are in the largest group.

## Usage

``` r
rnet_connected(rnet)
```

## Arguments

- rnet:

  An sf object representing a road network

## Value

An sf object representing the largest group in the network

## Examples

``` r
rnet <- rnet_breakup_vertices(stplanr::osm_net_example)
rnet_largest_group <- rnet_connected(rnet)
plot(rnet$geometry)

plot(rnet_largest_group$geometry)
```
