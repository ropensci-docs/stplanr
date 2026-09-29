# Subset one route network based on overlaps with another

Subset one route network based on overlaps with another

## Usage

``` r
rnet_subset(
  rnet_x,
  rnet_y,
  dist = 10,
  crop = TRUE,
  min_length = 20,
  rm_disconnected = TRUE
)
```

## Arguments

- rnet_x:

  The route network to be subset

- rnet_y:

  The subsetting route network

- dist:

  The buffer width around y in meters. 1 m by default.

- crop:

  Crop `rnet_x`? `TRUE` is the default

- min_length:

  Segments shorter than this multiple of dist *and* which were longer
  before the cropping process will be removed. 3 by default.

- rm_disconnected:

  Remove ways that are

## Examples

``` r
rnet_x <- osm_net_example[1]
rnet_y <- route_network_small["flow"]
plot(rnet_x$geometry, lwd = 5)
plot(rnet_y$geometry, add = TRUE, col = "red", lwd = 3)
rnet_x_subset <- rnet_subset(rnet_x, rnet_y)
#> Warning: attribute variables are assumed to be spatially constant throughout all geometries
#> Warning: repeating attributes for all sub-geometries for which they may not be constant
#> Joining with `by = join_by(osm_id)`
plot(rnet_x_subset, add = TRUE, col = "blue")
#> Warning: ignoring all but the first attribute
```
