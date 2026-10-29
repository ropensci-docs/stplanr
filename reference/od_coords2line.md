# Convert origin-destination coordinates into desire lines

Convert origin-destination coordinates into desire lines

## Usage

``` r
od_coords2line(odc, crs = 4326, remove_duplicates = TRUE)
```

## Arguments

- odc:

  A data frame or matrix representing the coordinates of
  origin-destination data. The first two columns represent the
  coordinates of the origin (typically longitude and latitude) points;
  the third and fourth columns represent the coordinates of the
  destination (in the same CRS). Each row represents travel from origin
  to destination.

- crs:

  A number representing the coordinate reference system of the result,
  4326 by default.

- remove_duplicates:

  Should rows with duplicated rows be removed? `TRUE` by default.

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
[`od_id`](https://docs.ropensci.org/stplanr/reference/od_id.md),
[`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
odf <- od_coords(l = flowlines_sf)
odlines <- od_coords2line(odf)
odlines <- od_coords2line(odf, crs = 4326)
plot(odlines)

x_coords <- 1:3
n <- 50
d <- data.frame(lapply(1:4, function(x) sample(x_coords, n, replace = TRUE)))
names(d) <- c("fx", "fy", "tx", "ty")
l <- od_coords2line(d)
#> Duplicate OD pairs identified, removing 14 rows
plot(l)

nrow(l)
#> [1] 36
l_with_duplicates <- od_coords2line(d, remove_duplicates = FALSE)
plot(l_with_duplicates)

nrow(l_with_duplicates)
#> [1] 50
```
