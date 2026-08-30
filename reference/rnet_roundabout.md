# Example of roundabout data showing problems for SpatialLinesNetwork objects

See `data-raw/rnet_roundabout.R` for details on how this was created.

## Format

A sf object

## Examples

``` r
rnet_roundabout
#> Simple feature collection with 9 features and 27 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.473083 ymin: 53.83656 xmax: -1.471986 ymax: 53.83739
#> Geodetic CRS:  WGS 84
#> # A tibble: 9 × 28
#>   osm_id   name      highway waterway aerialway barrier man_made maxspeed oneway
#> * <chr>    <chr>     <chr>   <chr>    <chr>     <chr>   <chr>    <chr>    <chr> 
#> 1 2954219  NA        trunk   NA       NA        NA      NA       40 mph   NA    
#> 2 4802965  Ring Road trunk   NA       NA        NA      NA       40 mph   yes   
#> 3 5098650  NA        trunk   NA       NA        NA      NA       40 mph   yes   
#> 4 90994242 Ring Road trunk   NA       NA        NA      NA       40 mph   yes   
#> 5 90994243 Ring Road trunk   NA       NA        NA      NA       40 mph   yes   
#> 6 90994244 NA        trunk   NA       NA        NA      NA       40 mph   yes   
#> 7 90994245 NA        trunk   NA       NA        NA      NA       40 mph   yes   
#> 8 90994247 Ring Road trunk   NA       NA        NA      NA       40 mph   yes   
#> 9 90994249 Wetherby… trunk   NA       NA        NA      NA       40 mph   yes   
#> # ℹ 19 more variables: building <chr>, surface <chr>, landuse <chr>,
#> #   natural <chr>, start_date <chr>, wall <chr>, service <chr>, lanes <chr>,
#> #   layer <chr>, tracktype <chr>, bridge <chr>, foot <chr>, bicycle <chr>,
#> #   lit <chr>, railway <chr>, footway <chr>, z_order <int>, other_tags <chr>,
#> #   geometry <LINESTRING [°]>
```
