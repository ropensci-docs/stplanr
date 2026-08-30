# Perform GIS functions on a temporary, projected version of a spatial object

This function performs operations on projected data.

## Usage

``` r
geo_projected(shp, fun, crs, silent, ...)
```

## Arguments

- shp:

  A spatial object with a geographic (WGS84) coordinate system

- fun:

  A function to perform on the projected object (e.g. from the sf
  package)

- crs:

  An optional coordinate reference system (if not provided it is set
  automatically by
  [`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md))

- silent:

  A binary value for printing the CRS details (default: TRUE)

- ...:

  Arguments to pass to `fun`

## See also

Other geo:
[`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md),
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md),
[`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md),
[`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md),
[`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md),
[`quadrant()`](https://docs.ropensci.org/stplanr/reference/quadrant.md)

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
  shp <- routes_fast_sf[2:4, ]
  geo_projected(shp, sf::st_buffer, dist = 100)
}
#> Simple feature collection with 3 features and 16 fields
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -1.552483 ymin: 53.81487 xmax: -1.511078 ymax: 53.83131
#> Geodetic CRS:  WGS 84
#>   plan start finish length time waypoint cum_hill change_elev dif_max_min
#> 3    1     1      1   2976  829       97      112          -4          39
#> 4    1     1      1   2290  502       37      103         -45          65
#> 5    1     1      1   1866  313       41       89         -61          65
#>   up_tot down_tot av_incline co2_saving calories busyness ID
#> 3     54       58 0.03763441        555       78     7062  3
#> 4     29       74 0.04497817        427       38     3380  4
#> 5     14       75 0.04769561        348       20     2259  5
#>                         geometry
#> 3 POLYGON ((-1.551653 53.8248...
#> 4 POLYGON ((-1.530458 53.8166...
#> 5 POLYGON ((-1.519689 53.8172...
```
