# Perform a buffer operation on a temporary projected CRS

This function solves the problem that buffers will not be circular when
used on non-projected data.

## Usage

``` r
geo_buffer(shp, dist = NULL, width = NULL, ...)
```

## Arguments

- shp:

  A spatial object with a geographic CRS (e.g. WGS84) around which a
  buffer should be drawn

- dist:

  The distance (in metres) of the buffer (when buffering simple
  features)

- width:

  The distance (in metres) of the buffer (when buffering sp objects)

- ...:

  Arguments passed to the buffer (see
  [`?sf::st_buffer`](https://r-spatial.github.io/sf/reference/geos_unary.html)
  for details)

## Details

Requires recent version of PROJ (\>= 6.3.0). Buffers on `sf` objects
with geographic (lon/lat) coordinates can also be done with the
[`s2`](https://r-spatial.github.io/s2/) package.

## See also

Other geo:
[`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md),
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md),
[`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md),
[`geo_projected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md),
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
if (lib_versions[3] >= "6.3.1") {
  buff_sf <- geo_buffer(routes_fast_sf, dist = 50)
  plot(buff_sf$geometry)
  geo_buffer(routes_fast_sf$geometry, dist = 50)
}

#> Geometry set for 42 features 
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -1.551723 ymin: 53.80203 xmax: -1.510228 ymax: 53.83086
#> Geodetic CRS:  WGS 84
#> First 5 geometries:
#> POLYGON ((-1.535569 53.82873, -1.535517 53.8287...
#> POLYGON ((-1.550723 53.82451, -1.550871 53.8248...
#> POLYGON ((-1.530548 53.81706, -1.530586 53.8170...
#> POLYGON ((-1.518697 53.81731, -1.51892 53.81742...
#> POLYGON ((-1.516744 53.82823, -1.51678 53.82823...
```
