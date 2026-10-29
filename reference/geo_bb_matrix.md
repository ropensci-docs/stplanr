# Create matrix representing the spatial bounds of an object

Converts a range of spatial data formats into a matrix representing the
bounding box

## Usage

``` r
geo_bb_matrix(shp)
```

## Arguments

- shp:

  Spatial object

## See also

Other geo:
[`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md),
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md),
[`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md),
[`geo_projected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md),
[`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md),
[`quadrant()`](https://docs.ropensci.org/stplanr/reference/quadrant.md)

## Examples

``` r
geo_bb_matrix(routes_fast_sf)
#>           [,1]      [,2]
#> [1,] -1.550964 -1.510987
#> [2,] 53.802478 53.830414
geo_bb_matrix(cents_sf[1, ])
#>           [,1]      [,2]
#> [1,] -1.546463 -1.546463
#> [2,] 53.809517 53.809517
geo_bb_matrix(c(-2, 54))
#>      [,1] [,2]
#> [1,]   -2   -2
#> [2,]   54   54
geo_bb_matrix(sf::st_coordinates(cents_sf))
#>           [,1]      [,2]
#> [1,] -1.550806 -1.511861
#> [2,] 53.804098 53.828874
```
