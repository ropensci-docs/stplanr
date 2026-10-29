# Aggregate flows so they become non-directional (by geometry - the slow way)

Flow data often contains movement in two directions: from point A to
point B and then from B to A. This can be problematic for transport
planning, because the magnitude of flow along a route can be masked by
flows the other direction. If only the largest flow in either direction
is captured in an analysis, for example, the true extent of travel will
by heavily under-estimated for OD pairs which have similar amounts of
travel in both directions.

## Usage

``` r
onewaygeo(x, attrib)
```

## Arguments

- x:

  A dataset containing linestring geometries

- attrib:

  A text string containing the name of the line's attribute to aggregate
  or a numeric vector of the columns to be aggregated

## Value

`onewaygeo` outputs a SpatialLinesDataFrame with single lines and
user-selected attribute values that have been aggregated. Only lines
with a distance (i.e. not intra-zone flows) are included

## Details

This function aggregates directional flows into non-directional flows,
potentially halving the number of lines objects and reducing the number
of overlapping lines to zero.

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
[`n_segments()`](https://docs.ropensci.org/stplanr/reference/n_segments.md),
[`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md),
[`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md),
[`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)
