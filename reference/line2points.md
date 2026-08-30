# Convert a spatial (linestring) object to points

The number of points will be double the number of lines with
`line2points`. A closely related function, `line2pointsn` returns all
the points that were line vertices. The points corresponding with a
given line, `i`, will be `(2*i):((2*i)+1)`. The last function,
`line2vertices`, returns all the points that are vertices but not nodes.
If the input `l` object is composed by only 1 LINESTRING with 2 POINTS,
then it returns an empty `sf` object.

## Usage

``` r
line2points(l, ids = rep(1:nrow(l)))

line2pointsn(l)

line2vertices(l)
```

## Arguments

- l:

  An `sf` object or a `SpatialLinesDataFrame` from the older `sp`
  package

- ids:

  Vector of ids (by default `1:nrow(l)`)

## See also

Other lines:
[`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md),
[`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md),
[`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md),
[`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md),
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
l <- routes_fast_sf[2, ]
lpoints <- line2points(l)
plot(l$geometry)
plot(lpoints, add = TRUE)

# test all vertices:
plot(l$geometry)
lpoints2 <- line2pointsn(l)
plot(lpoints2$geometry, add = TRUE)


# extract only internal vertices
l_internal_vertices <- line2vertices(l)
plot(sf::st_geometry(l), reset = FALSE)
plot(l_internal_vertices, add = TRUE)

# The boundary points are missing
```
