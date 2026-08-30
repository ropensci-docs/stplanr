# Calculate the gradient of line segments from distance and elevation vectors

Calculate the gradient of line segments from distance and elevation
vectors

## Usage

``` r
route_slope_vector(x, e)
```

## Arguments

- x:

  Vector of locations

- e:

  Elevations in same units as x (assumed to be metres)

## See also

Other route_funs:
[`route_average_gradient()`](https://docs.ropensci.org/stplanr/reference/route_average_gradient.md),
[`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md),
[`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md),
[`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md),
[`route_sequential_dist()`](https://docs.ropensci.org/stplanr/reference/route_sequential_dist.md),
[`route_slope_matrix()`](https://docs.ropensci.org/stplanr/reference/route_slope_matrix.md)

## Examples

``` r
x <- c(0, 2, 3, 4, 5, 9)
e <- c(1, 2, 2, 4, 3, 1) / 10
route_slope_vector(x, e)
#> [1]  0.05  0.00  0.20 -0.10 -0.05
```
