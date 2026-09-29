# Function to split overlapping SpatialLines into segments

Divides SpatialLinesDataFrame objects into separate Lines. Each new
Lines object is the aggregate of a single number of aggregated lines.

## Usage

``` r
gsection(sl, buff_dist = 0)
```

## Arguments

- sl:

  SpatialLinesDataFrame with overlapping Lines to split by number of
  overlapping features.

- buff_dist:

  A number specifying the distance in meters of the buffer to be used to
  crop lines before running the operation. If the distance is zero (the
  default) touching but non-overlapping lines may be aggregated.

## See also

Other rnet:
[`islines()`](https://docs.ropensci.org/stplanr/reference/islines.md),
[`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md),
[`rnet_breakup_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_breakup_vertices.md),
[`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)

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
  sl <- routes_fast_sf[2:4, ]
  rsec <- gsection(sl)
  length(rsec) # sections
  plot(rsec, col = seq(length(rsec)))
  rsec <- gsection(sl, buff_dist = 50)
  length(rsec) # 4 features: issue
  plot(rsec, col = seq(length(rsec)))
}

```
