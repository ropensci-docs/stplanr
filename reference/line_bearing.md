# Find the bearing of straight lines

This function returns the bearing (in degrees relative to north) of
lines.

## Usage

``` r
line_bearing(l, bidirectional = FALSE)
```

## Arguments

- l:

  A spatial lines object

- bidirectional:

  Should the result be returned in a bidirectional format? Default is
  FALSE. If TRUE, the same line in the oposite direction would have the
  same bearing

## Details

Returns a boolean vector. TRUE means that the associated line is in fact
a point (has no distance). This can be useful for removing data that
will not be plotted.

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
[`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md),
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
l <- flowlines_sf[1:5, ]
bearings_sf_1_9 <- line_bearing(l)
bearings_sf_1_9 # lines of 0 length have NaN bearing
#> [1]  -92.04942 -102.44566 -143.83660 -173.33154  170.51696
b <- line_bearing(l, bidirectional = TRUE)
r <- routes_fast_sf[1:5, ]
b2 <- line_bearing(r, bidirectional = TRUE)
plot(b, b2)
```
