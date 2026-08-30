# Join route networks

Join function that adds columns to a 'target' route network `sf` object
from a 'source' route network that contains the base geometry, e.g. from
OSM

## Usage

``` r
rnet_join(
  rnet_x,
  rnet_y,
  dist = 5,
  length_y = TRUE,
  key_column = 1,
  subset_x = FALSE,
  dist_subset = NULL,
  segment_length = 0,
  endCapStyle = "FLAT",
  contains = TRUE,
  max_angle_diff = NULL,
  crs = geo_select_aeq(rnet_x),
  ...
)
```

## Arguments

- rnet_x:

  Target route network, the output will have the same geometries as
  features in this object.

- rnet_y:

  Source route network. Columns from this route network object will be
  copied across to the new network.

- dist:

  The buffer width around rnet_y in meters. 1 m by default.

- length_y:

  Add a new column called `length_y`? Useful when joining based on
  length of segments (e.g. weighted mean). `TRUE` by default.

- key_column:

  The index of the key (unique identifier) column in `rnet_x`.

- subset_x:

  Subset the source route network by the target network before creating
  buffers? This can lead to faster and better results. Default: `FALSE`.

- dist_subset:

  The buffer distance in m to apply when breaking up the source object
  `rnet_y`. Default: 5.

- segment_length:

  Should the source route network be split? `0` by default, meaning no
  splitting. Values above 0 split the source into linestrings with a max
  distance. Around 5 (m) may be a sensible default for many use cases,
  the smaller the value the slower the process.

- endCapStyle:

  Type of buffer. See
  [`?sf::st_buffer`](https://r-spatial.github.io/sf/reference/geos_unary.html)
  for details

- contains:

  Should the join be based on
  [`sf::st_contains`](https://r-spatial.github.io/sf/reference/geos_binary_pred.html)
  or
  [`sf::st_intersects`](https://r-spatial.github.io/sf/reference/geos_binary_pred.html)?
  `TRUE` by default. If `FALSE` the centroid of each segment of `rnet_y`
  is used for the join. Note: this can result in incorrectly assigning
  values on sideroads, as documented in
  [\#520](https://github.com/ropensci/stplanr/issues/520).

- max_angle_diff:

  The maximum angle difference between x and y nets for a value to be
  returned

- crs:

  The CRS to use for the buffer operation. See
  [`?geo_projected`](https://docs.ropensci.org/stplanr/reference/geo_projected.md)
  for details.

- ...:

  Additional arguments passed to `rnet_subset`.

## Details

The output is an sf object containing polygons representing buffers
around the route network in `rnet_x`. The examples below demonstrate how
to join attributes from a route network object created with the function
[`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
onto OSM geometries.

Note: The main purpose of this function is to join an ID from `rnet_x`
onto `rnet_y`. Subsequent steps, e.g. with
[`dplyr::inner_join()`](https://dplyr.tidyverse.org/reference/mutate-joins.html)
are needed to join the attributes back onto `rnet_x`. There are rarely
1-to-1 relationships between spatial network geometries so we take care
when using this function.

See [\#505](https://github.com/ropensci/stplanr/issues/505) for details
and a link to an interactive example of inputs and outputs shown below.

## Examples

``` r
library(sf)
library(dplyr)
#> 
#> Attaching package: ‘dplyr’
#> The following objects are masked from ‘package:stats’:
#> 
#>     filter, lag
#> The following objects are masked from ‘package:base’:
#> 
#>     intersect, setdiff, setequal, union
plot(osm_net_example$geometry, lwd = 5, col = "grey", add = TRUE)
#> Error in plot.xy(xy.coords(x, y), type = type, ...): plot.new has not been called yet
plot(route_network_small["flow"], add = TRUE)
#> Error in plot.xy(xy.coords(x, y), type = type, ...): plot.new has not been called yet
rnetj <- rnet_join(osm_net_example, route_network_small, dist = 9)
rnetj2 <- rnet_join(osm_net_example, route_network_small, dist = 9, segment_length = 10)
# library(mapview)
# mapview(rnetj, zcol = "flow") +
#   mapview(rnetj2, zcol = "flow") +
#   mapview(route_network_small, zcol = "flow")
plot(sf::st_geometry(rnetj))
plot(rnetj["flow"], add = TRUE)
#> Warning: no non-missing arguments to min; returning Inf
#> Warning: no non-missing arguments to max; returning -Inf
plot(rnetj2["flow"], add = TRUE)
plot(route_network_small["flow"], add = TRUE)
summary(rnetj2$length_y)
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>   7.628   8.531   9.581   9.802  10.265  13.332      55 
rnetj_summary <- rnetj2 %>%
  filter(!is.na(length_y)) %>%
  sf::st_drop_geometry() %>%
  group_by(osm_id) %>%
  summarise(
    flow = weighted.mean(flow, length_y, na.rm = TRUE),
  )
osm_joined_rnet <- dplyr::left_join(osm_net_example, rnetj_summary)
#> Joining with `by = join_by(osm_id)`
plot(sf::st_geometry(route_network_small))
plot(route_network_small["flow"], lwd = 3, add = TRUE)
plot(sf::st_geometry(osm_joined_rnet), add = TRUE)
# plot(osm_joined_rnet[c("flow")], lwd = 9, add = TRUE)
# Improve fit between geometries and performance by subsetting rnet_x
osm_subset <- rnet_subset(osm_net_example, route_network_small, dist = 5)
#> Warning: attribute variables are assumed to be spatially constant throughout all geometries
#> Warning: repeating attributes for all sub-geometries for which they may not be constant
#> Joining with `by = join_by(osm_id)`
osm_joined_rnet <- dplyr::left_join(osm_subset, rnetj_summary)
#> Joining with `by = join_by(osm_id)`
plot(route_network_small["flow"])
# plot(osm_joined_rnet[c("flow")])
# mapview(joined_network) +
#   mapview(route_network_small)
```
