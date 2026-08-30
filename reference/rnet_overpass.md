# Example of overpass data showing problems for SpatialLinesNetwork objects

See `data-raw/rnet_overpass.R` for details on how this was created.

## Format

A sf object

## Examples

``` r
rnet_overpass
#> Simple feature collection with 8 features and 27 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.555557 ymin: 53.79936 xmax: -1.554044 ymax: 53.80006
#> Geodetic CRS:  WGS 84
#> # A tibble: 8 × 28
#>   osm_id    name     highway waterway aerialway barrier man_made maxspeed oneway
#> * <chr>     <chr>    <chr>   <chr>    <chr>     <chr>   <chr>    <chr>    <chr> 
#> 1 5947825   Park La… tertia… NA       NA        NA      NA       30 mph   yes   
#> 2 6192813   Inner R… motorw… NA       NA        NA      NA       40 mph   yes   
#> 3 27440196  Inner R… motorw… NA       NA        NA      NA       40 mph   yes   
#> 4 38888444  Park La… tertia… NA       NA        NA      NA       30 mph   yes   
#> 5 99644807  NA       tertia… NA       NA        NA      NA       NA       yes   
#> 6 172735110 West St… motorw… NA       NA        NA      NA       40 mph   yes   
#> 7 175332052 West St… tertia… NA       NA        NA      NA       NA       yes   
#> 8 175332053 NA       tertia… NA       NA        NA      NA       NA       yes   
#> # ℹ 19 more variables: building <chr>, surface <chr>, landuse <chr>,
#> #   natural <chr>, start_date <chr>, wall <chr>, service <chr>, lanes <chr>,
#> #   layer <chr>, tracktype <chr>, bridge <chr>, foot <chr>, bicycle <chr>,
#> #   lit <chr>, railway <chr>, footway <chr>, z_order <int>, other_tags <chr>,
#> #   geometry <LINESTRING [°]>
```
