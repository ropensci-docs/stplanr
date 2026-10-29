# Calculate the sequential distances between sequential coordinate pairs

Calculate the sequential distances between sequential coordinate pairs

## Usage

``` r
route_sequential_dist(m, lonlat = TRUE)
```

## Arguments

- m:

  Matrix containing coordinates and elevations

- lonlat:

  Are the coordinates in lon/lat order? `TRUE` by default

## See also

Other route_funs:
[`route_average_gradient()`](https://docs.ropensci.org/stplanr/reference/route_average_gradient.md),
[`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md),
[`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md),
[`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md),
[`route_slope_matrix()`](https://docs.ropensci.org/stplanr/reference/route_slope_matrix.md),
[`route_slope_vector()`](https://docs.ropensci.org/stplanr/reference/route_slope_vector.md)

## Examples

``` r
x <- c(0, 2, 3, 4, 5, 9)
y <- c(0, 0, 0, 0, 0, 1)
m <- cbind(x, y)
route_sequential_dist(m)
#> Maximum distance is > 100km. The 'cheap' measure is inaccurate over such
#> large distances, you'd likely be better using a different 'measure', 
#> one of 'haversine', 'vincenty', or 'geodesic'. 
#> [1] 222257.4 111128.7 111128.7 111128.7 458196.5
```
