# Convert 2 matrices to lines

Convert 2 matrices to lines

## Usage

``` r
mats2line(mat1, mat2, crs = NA)
```

## Arguments

- mat1:

  Matrix representing origins

- mat2:

  Matrix representing destinations

- crs:

  Number representing the coordinate system of the data, e.g. 4326

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
[`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md),
[`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md),
[`line_breakup()`](https://docs.ropensci.org/stplanr/reference/line_breakup.md),
[`line_midpoint()`](https://docs.ropensci.org/stplanr/reference/line_midpoint.md),
[`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md),
[`line_segment1()`](https://docs.ropensci.org/stplanr/reference/line_segment1.md),
[`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md),
[`n_segments()`](https://docs.ropensci.org/stplanr/reference/n_segments.md),
[`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md),
[`onewaygeo()`](https://docs.ropensci.org/stplanr/reference/onewaygeo.md),
[`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md),
[`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)

## Examples

``` r
m1 <- matrix(c(1, 2, 1, 2), ncol = 2)
m2 <- matrix(c(9, 9, 9, 1), ncol = 2)
l <- mats2line(m1, m2)
class(l)
#> [1] "sfc_LINESTRING" "sfc"           
l
#> Geometry set for 2 features 
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: 1 ymin: 1 xmax: 9 ymax: 9
#> CRS:           NA
#> LINESTRING (1 1, 9 9)
#> LINESTRING (2 2, 9 1)
lsf <- sf::st_sf(l, crs = 4326)
class(lsf)
#> [1] "sf"         "data.frame"
plot(lsf)

# mapview::mapview(lsf)
```
