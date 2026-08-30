# Segment a single line, using lwgeom or rsgeo

Segment a single line, using lwgeom or rsgeo

## Usage

``` r
line_segment1(l, n_segments = NA, segment_length = NA)
```

## Arguments

- l:

  A spatial lines object

- n_segments:

  The number of segments to divide the line into

- segment_length:

  The approximate length of segments in the output (overrides n_segments
  if set)

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
[`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md),
[`mats2line()`](https://docs.ropensci.org/stplanr/reference/mats2line.md),
[`n_segments()`](https://docs.ropensci.org/stplanr/reference/n_segments.md),
[`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md),
[`onewaygeo()`](https://docs.ropensci.org/stplanr/reference/onewaygeo.md),
[`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md),
[`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)

## Examples

``` r
l <- routes_fast_sf[2, ]
l_seg2 <- line_segment1(l = l, n_segments = 2)
# Test with rsgeo (must be installed):
# l_seg2_rsgeo = line_segment1(l = l, n_segments = 2)
# waldo::compare(l_seg2, l_seg2_rsgeo)
l_seg3 <- line_segment1(l = l, n_segments = 3)
l_seg_100 <- line_segment1(l = l, segment_length = 100)
l_seg_1000 <- line_segment1(l = l, segment_length = 1000)
plot(sf::st_geometry(l_seg2), col = 1:2, lwd = 5)

plot(sf::st_geometry(l_seg3), col = 1:3, lwd = 5)

plot(sf::st_geometry(l_seg_100), col = seq(nrow(l_seg_100)), lwd = 5)

plot(sf::st_geometry(l_seg_1000), col = seq(nrow(l_seg_1000)), lwd = 5)
```
