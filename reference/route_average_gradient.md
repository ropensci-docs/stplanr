# Return average gradient across a route

This function assumes that elevations and distances are in the same
units.

## Usage

``` r
route_average_gradient(elevations, distances)
```

## Arguments

- elevations:

  Elevations, e.g. those provided by the `cyclestreets` package

- distances:

  Distances, e.g. those provided by the `cyclestreets` package

## See also

Other route_funs:
[`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md),
[`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md),
[`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md),
[`route_sequential_dist()`](https://docs.ropensci.org/stplanr/reference/route_sequential_dist.md),
[`route_slope_matrix()`](https://docs.ropensci.org/stplanr/reference/route_slope_matrix.md),
[`route_slope_vector()`](https://docs.ropensci.org/stplanr/reference/route_slope_vector.md)

## Examples

``` r
r1 <- od_data_routes[od_data_routes$route_number == 2, ]
elevations <- r1$elevations
distances <- r1$distances
route_average_gradient(elevations, distances) # an average of a 4% gradient
#> [1] 0.03907936
```
