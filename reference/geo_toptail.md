# Clip the first and last n metres of SpatialLines

Takes lines and removes the start and end point, to a distance
determined by the user.

## Usage

``` r
geo_toptail(l, toptail_dist, ...)
```

## Arguments

- l:

  An `sf` object representing lines

- toptail_dist:

  The distance (in metres) to top and tail the line by. Can either be a
  single value or a vector of the same length as the SpatialLines
  object.

- ...:

  Arguments passed to
  [`sf::st_buffer()`](https://r-spatial.github.io/sf/reference/geos_unary.html)

## Details

Note: see the function
[`toptailgs()`](https://github.com/ropensci/stplanr/blob/v1.0.0/R/toptail.R)
in stplanr v0.8.5 for an implementation that uses the geosphere package.

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
[`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md),
[`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md),
[`line_breakup()`](https://docs.ropensci.org/stplanr/reference/line_breakup.md),
[`line_midpoint()`](https://docs.ropensci.org/stplanr/reference/line_midpoint.md),
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
lib_versions <- sf::sf_extSoftVersion()
lib_versions
#>           GEOS           GDAL         proj.4 GDAL_with_GEOS     USE_PROJ_H 
#>       "3.12.1"        "3.8.4"        "9.4.0"         "true"         "true" 
#>           PROJ 
#>        "9.4.0" 
# dont test due to issues with sp classes on some set-ups
if (lib_versions[3] >= "6.3.1") {
  l <- routes_fast_sf[2:4, ]
  l_top_tail <- geo_toptail(l, 300)
  l_top_tail
  plot(sf::st_geometry(l_top_tail))
  plot(sf::st_geometry(geo_toptail(l, 600)), lwd = 9, add = TRUE)
}
```
