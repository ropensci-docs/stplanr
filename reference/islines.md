# Do the intersections between two geometries create lines?

This is a function required in
[`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md).
It identifies whether sets of lines overlap (beyond shared points) or
not.

## Usage

``` r
islines(g1, g2)
```

## Arguments

- g1:

  A spatial object

- g2:

  A spatial object

## See also

Other rnet:
[`gsection()`](https://docs.ropensci.org/stplanr/reference/gsection.md),
[`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md),
[`rnet_breakup_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_breakup_vertices.md),
[`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# sf implementation
islines(routes_fast_sf[2, ], routes_fast_sf[3, ])
islines(routes_fast_sf[2, ], routes_fast_sf[22, ])
} # }
```
