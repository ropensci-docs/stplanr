# Vectorised function to calculate number of segments given a max segment length

Vectorised function to calculate number of segments given a max segment
length

## Usage

``` r
n_segments(line_length, max_segment_length)
```

## Arguments

- line_length:

  The length of the line

- max_segment_length:

  The maximum length of each segment

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
[`mats2line()`](https://docs.ropensci.org/stplanr/reference/mats2line.md),
[`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md),
[`onewaygeo()`](https://docs.ropensci.org/stplanr/reference/onewaygeo.md),
[`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md),
[`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)

## Examples

``` r
n_segments(50, 10)
#> [1] 5
n_segments(50.1, 10)
#> [1] 6
n_segments(1, 10)
#> [1] 1
n_segments(1:9, 2)
#> [1] 1 1 2 2 3 3 4 4 5
```
