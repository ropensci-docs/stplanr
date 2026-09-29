# Calculate the gradient of line segments from a matrix of coordinates

Calculate the gradient of line segments from a matrix of coordinates

## Usage

``` r
route_slope_matrix(m, e = m[, 3], lonlat = TRUE)
```

## Arguments

- m:

  Matrix containing coordinates and elevations

- e:

  Elevations in same units as x (assumed to be metres)

- lonlat:

  Are the coordinates in lon/lat order? `TRUE` by default

## See also

Other route_funs:
[`route_average_gradient()`](https://docs.ropensci.org/stplanr/reference/route_average_gradient.md),
[`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md),
[`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md),
[`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md),
[`route_sequential_dist()`](https://docs.ropensci.org/stplanr/reference/route_sequential_dist.md),
[`route_slope_vector()`](https://docs.ropensci.org/stplanr/reference/route_slope_vector.md)

## Examples

``` r
x <- c(0, 2, 3, 4, 5, 9)
y <- c(0, 0, 0, 0, 0, 9)
z <- c(1, 2, 2, 4, 3, 1) / 10
m <- cbind(x, y, z)
plot(x, z, ylim = c(-0.5, 0.5), type = "l")
(gx <- route_slope_vector(x, z))
#> [1]  0.05  0.00  0.20 -0.10 -0.05
(gxy <- route_slope_matrix(m, lonlat = FALSE))
#> [1]  0.05000000  0.00000000  0.20000000 -0.10000000 -0.02030692
abline(h = 0, lty = 2)
points(x[-length(x)], gx, col = "red")
points(x[-length(x)], gxy, col = "blue")
title("Distance (in x coordinates) elevation profile",
  sub = "Points show calculated gradients of subsequent lines"
)
```
