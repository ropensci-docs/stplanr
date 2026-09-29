# Spatial points representing home locations

These points represent population-weighted centroids of Medium Super
Output Area (MSOA) zones within a 1 mile radius of of my home when I was
writing this package.

## Format

A spatial dataset with 8 rows and 5 columns

## Details

- geo_code the official code of the zone

- MSOA11NM name zone name

- percent_fem the percent female

- avslope average gradient of the zone

Cents was generated from the data repository pct-data:
https://github.com/npct/pct-data. This data was accessed from within the
pct repo: https://github.com/npct/pct, using the following code:

## See also

Other data:
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
[`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md),
[`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md),
[`od_data_lines`](https://docs.ropensci.org/stplanr/reference/od_data_lines.md),
[`od_data_routes`](https://docs.ropensci.org/stplanr/reference/od_data_routes.md),
[`od_data_sample`](https://docs.ropensci.org/stplanr/reference/od_data_sample.md),
[`osm_net_example`](https://docs.ropensci.org/stplanr/reference/osm_net_example.md),
[`read_table_builder()`](https://docs.ropensci.org/stplanr/reference/read_table_builder.md),
[`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md),
[`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md),
[`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md),
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md),
[`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)

## Examples

``` r
cents_sf
#> Simple feature collection with 8 features and 4 fields
#> Geometry type: POINT
#> Dimension:     XY
#> Bounding box:  xmin: -1.550806 ymin: 53.8041 xmax: -1.511861 ymax: 53.82887
#> Geodetic CRS:  WGS 84
#>       geo_code  MSOA11NM percent_fem  avslope                   geometry
#> 1708 E02002384 Leeds 055    0.458721 2.856563 POINT (-1.546463 53.80952)
#> 1712 E02002382 Leeds 053    0.438144 2.284782 POINT (-1.511861 53.81161)
#> 1805 E02002393 Leeds 064    0.408759 2.361707  POINT (-1.524205 53.8041)
#> 1925 E02002367 Leeds 038    0.591141 5.091685 POINT (-1.550806 53.82442)
#> 1928 E02002363 Leeds 034    0.525161 3.076791 POINT (-1.535617 53.82847)
#> 1930 E02002361 Leeds 032    0.511777 3.589363 POINT (-1.516734 53.82887)
#> 2029 E02002377 Leeds 048    0.408293 2.762529  POINT (-1.519318 53.8158)
#> 2034 E02002371 Leeds 042    0.504460 2.814496 POINT (-1.530712 53.81756)
```
