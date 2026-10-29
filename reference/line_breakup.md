# Break up line objects into shorter segments

This function breaks up a LINESTRING geometries into smaller pieces.

## Usage

``` r
line_breakup(l, z)
```

## Arguments

- l:

  An sf object with LINESTRING geometry

- z:

  An sf object with `POLYGON` geometry or a number representing the
  resolution of grid cells used to break up the linestring objects

## Value

An sf object with LINESTRING geometry created after breaking up the
input object.

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
[`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md),
[`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md),
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
library(sf)
z <- zones_sf$geometry
l <- routes_fast_sf$geometry[2]
l_split <- line_breakup(l, z)
l
#> Geometry set for 1 feature 
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.550964 ymin: 53.82387 xmax: -1.516748 ymax: 53.83041
#> Geodetic CRS:  WGS 84
#> LINESTRING (-1.516748 53.82868, -1.517513 53.82...
l_split
#> Geometry set for 3 features 
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.550964 ymin: 53.82387 xmax: -1.516748 ymax: 53.83041
#> Geodetic CRS:  WGS 84
#> LINESTRING (-1.516748 53.82868, -1.517513 53.82...
#> LINESTRING (-1.526629 53.82927, -1.526957 53.82...
#> LINESTRING (-1.545996 53.82493, -1.546004 53.82...
sf::st_length(l)
#> 2982.689 [m]
sum(sf::st_length(l_split))
#> 2982.689 [m]
plot(z)
plot(l, add = TRUE, lwd = 9, col = "grey")
plot(l_split, add = TRUE, col = 1:length(l_split))
```
