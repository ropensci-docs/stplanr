# Calculate line length of line with geographic or projected CRS

Takes a line (represented in sf or sp classes) and returns a numeric
value representing distance in meters.

## Usage

``` r
geo_length(shp)
```

## Arguments

- shp:

  A spatial line object

## See also

Other geo:
[`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md),
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md),
[`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md),
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
  geo_length(routes_fast_sf)
}
#>  [1] 1538.8810 2990.7783 2297.5929 1870.2117 2239.1301 3352.8345 1538.8810
#>  [8] 1580.7084 1506.1390 2483.2391 3156.1339 3877.7765 2992.2337 1708.4876
#> [15] 2121.8359 3098.9361 3768.5096 3711.6150 2366.0647 1506.1390 2078.5604
#> [22]  977.1004 1646.6739 2371.6377 1875.7200 2483.2391 3055.6605  977.1004
#> [29]  872.9039 1727.9827 2239.4037 3085.7290 3725.2340 1646.6739  872.9039
#> [36] 1303.2590 3285.0306 3829.5751 3868.1338 2323.4363 1727.9827 1303.2590
```
