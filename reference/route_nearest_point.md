# Find nearest route to a given point

This function was written as a drop-in replacement for
[`sf::st_nearest_feature()`](https://r-spatial.github.io/sf/reference/st_nearest_feature.html),
which only works with recent versions of GEOS.

## Usage

``` r
route_nearest_point(r, p, id_out = FALSE)
```

## Arguments

- r:

  The input route object from which the nearest route is to be found

- p:

  The point whose nearest route will be found

- id_out:

  Should the index of the matching feature be returned? `FALSE` by
  default

## Examples

``` r
r <- routes_fast_sf[2:6, NULL]
p <- sf::st_sfc(sf::st_point(c(-1.540, 53.826)), crs = sf::st_crs(r))
route_nearest_point(r, p, id_out = TRUE)
#> L1 
#>  1 
r_nearest <- route_nearest_point(r, p)
plot(r$geometry)
plot(p, add = TRUE)
plot(r_nearest, lwd = 5, add = TRUE)
```
