# Split a spatial object into quadrants

Returns a character vector of NE, SE, SW, NW corresponding to
north-east, south-east quadrants respectively. If number_out is TRUE,
returns numbers from 1:4, respectively.

## Usage

``` r
quadrant(x, cent = NULL, number_out = FALSE)
```

## Arguments

- x:

  Object of class sf

- cent:

  The centrepoint of the region of interest. Quadrants will be defined
  based on this point. By default this will be the geographic centroid
  of the zones.

- number_out:

  Should the result be returned as a number?

## See also

Other geo:
[`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md),
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md),
[`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md),
[`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md),
[`geo_projected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md),
[`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md)

## Examples

``` r
x = zones_sf
(quads <- quadrant(x))
#> Warning: st_centroid assumes attributes are constant over geometries
#> [1] "SE" "SW" "SE" "NE" "NE" "SW" "NW" "SE"
plot(x$geometry, col = factor(quads))
```
