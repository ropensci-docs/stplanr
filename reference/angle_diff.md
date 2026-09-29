# Calculate the angular difference between lines and a predefined bearing

This function was designed to find lines that are close to parallel and
perpendicular to some pre-defined route. It can return results that are
absolute (contain information on the direction of turn, i.e. + or -
values for clockwise/anticlockwise), bidirectional (which mean values
greater than +/- 90 are impossible).

## Usage

``` r
angle_diff(l, angle, bidirectional = FALSE, absolute = TRUE)
```

## Arguments

- l:

  A spatial lines object

- angle:

  an angle in degrees relative to North, with 90 being East and -90
  being West. (direction of rotation is ignored).

- bidirectional:

  Should the result be returned in a bidirectional format? Default is
  FALSE. If TRUE, the same line in the oposite direction would have the
  same bearing

- absolute:

  If TRUE (the default) only positive values can be returned

## Details

Building on the convention used in in the `bearing()` function from the
`geosphere` package and in many applications, North is definied as 0,
East as 90 and West as -90.

## See also

Other lines:
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
# fails on some systems (with early versions of PROJ)
if (lib_versions[3] >= "6.3.1") {
  # Find all routes going North-South
  lines_sf <- od2line(od_data_sample, zones = zones_sf)
  angle_diff(lines_sf[2, ], angle = 0)
  angle_diff(lines_sf[2:3, ], angle = 0)
}
#> Creating centroids representing desire line start and end points.
#> Linking to GEOS 3.12.1, GDAL 3.8.4, PROJ 9.4.0; sf_use_s2() is TRUE
#> [1]  92.2313 105.0539
```
