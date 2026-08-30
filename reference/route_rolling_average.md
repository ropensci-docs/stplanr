# Return smoothed averages of vector

This function calculates a simple rolling mean in base R. It is useful
for calculating route characteristics such as mean distances of segments
and changes in gradient.

## Usage

``` r
route_rolling_average(x, n = 3)
```

## Arguments

- x:

  Numeric vector to smooth

- n:

  The window size of the smoothing function. The default, 3, will take
  the mean of values before, after and including each value.

## See also

Other route_funs:
[`route_average_gradient()`](https://docs.ropensci.org/stplanr/reference/route_average_gradient.md),
[`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md),
[`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md),
[`route_sequential_dist()`](https://docs.ropensci.org/stplanr/reference/route_sequential_dist.md),
[`route_slope_matrix()`](https://docs.ropensci.org/stplanr/reference/route_slope_matrix.md),
[`route_slope_vector()`](https://docs.ropensci.org/stplanr/reference/route_slope_vector.md)

## Examples

``` r
y <- od_data_routes$elevations[od_data_routes$route_number == 2]
y
#> [1] 112.5263 111.0000 106.5000  84.0000  96.6250 110.0000 107.1429 105.5556
route_rolling_average(y)
#> [1]        NA 110.00877 100.50000  95.70833  96.87500 104.58929 107.56614
#> [8]        NA
route_rolling_average(y, n = 1)
#> [1] 112.5263 111.0000 106.5000  84.0000  96.6250 110.0000 107.1429 105.5556
route_rolling_average(y, n = 2)
#> [1] 111.7632 108.7500  95.2500  90.3125 103.3125 108.5714 106.3492       NA
route_rolling_average(y, n = 3)
#> [1]        NA 110.00877 100.50000  95.70833  96.87500 104.58929 107.56614
#> [8]        NA
```
