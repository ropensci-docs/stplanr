# Example of cycleway intersection data showing problems for SpatialLinesNetwork objects

See `data-raw/rnet_cycleway_intersection` for details on how this was
created.

## Format

A sf object

## Examples

``` r
rnet_cycleway_intersection
#> Simple feature collection with 2 features and 27 fields
#> Geometry type: LINESTRING
#> Dimension:     XY
#> Bounding box:  xmin: -1.547457 ymin: 53.81363 xmax: -1.54453 ymax: 53.81545
#> Geodetic CRS:  WGS 84
#> # A tibble: 2 × 28
#>   osm_id    name     highway waterway aerialway barrier man_made maxspeed oneway
#> * <chr>     <chr>    <chr>   <chr>    <chr>     <chr>   <chr>    <chr>    <chr> 
#> 1 145735609 Cross C… tertia… NA       NA        NA      NA       NA       NA    
#> 2 236285574 NA       cyclew… NA       NA        NA      NA       NA       NA    
#> # ℹ 19 more variables: building <chr>, surface <chr>, landuse <chr>,
#> #   natural <chr>, start_date <chr>, wall <chr>, service <chr>, lanes <chr>,
#> #   layer <chr>, tracktype <chr>, bridge <chr>, foot <chr>, bicycle <chr>,
#> #   lit <chr>, railway <chr>, footway <chr>, z_order <int>, other_tags <chr>,
#> #   geometry <LINESTRING [°]>
```
