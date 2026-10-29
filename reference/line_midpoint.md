# Find the mid-point of lines

Find the mid-point of lines

## Usage

``` r
line_midpoint(l, tolerance = NULL)
```

## Arguments

- l:

  A spatial lines object

- tolerance:

  The tolerance used to break lines at verteces. See
  [`lwgeom::st_linesubstring()`](https://r-spatial.github.io/lwgeom/reference/st_linesubstring.html).

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
[`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md),
[`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md),
[`line_breakup()`](https://docs.ropensci.org/stplanr/reference/line_breakup.md),
[`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md),
[`line_segment1()`](https://docs.ropensci.org/stplanr/reference/line_segment1.md),
[`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md),
[`mats2line()`](https://docs.ropensci.org/stplanr/reference/mats2line.md),
[`n_segments()`](https://docs.ropensci.org/stplanr/reference/n_segments.md),
[`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md),
[`onewaygeo()`](https://docs.ropensci.org/stplanr/reference/onewaygeo.md),
[`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md),
[`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)

## Examples

``` r
l <- routes_fast_sf[2:5, ]
plot(l$geometry, col = 2:5)
midpoints <- line_midpoint(l)
#> Warning: st_linesubstring does not follow a geodesic; you may want to use st_geod_segmentize first
#> Warning: st_linesubstring does not follow a geodesic; you may want to use st_geod_segmentize first
plot(midpoints, add = TRUE)
# compare with sf::st_point_on_surface:
midpoints2 <- sf::st_point_on_surface(l)
#> Warning: st_point_on_surface assumes attributes are constant over geometries
#> Warning: st_point_on_surface may not give correct results for longitude/latitude data
plot(midpoints2, add = TRUE, col = "red")
#> Warning: ignoring all but the first attribute
```
