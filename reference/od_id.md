# Combine two ID values to create a single ID number

Combine two ID values to create a single ID number

## Usage

``` r
od_id_szudzik(x, y, ordermatters = FALSE)

od_id_max_min(x, y)

od_id_character(x, y)
```

## Arguments

- x:

  a vector of numeric, character, or factor values

- y:

  a vector of numeric, character, or factor values

- ordermatters:

  logical, does the order of values matter to pairing, default = FALSE

## Details

In OD data it is common to have many 'oneway' flows from "A to B" and "B
to A". It can be useful to group these an have a single ID that
represents pairs of IDs with or without directionality, so they contain
'twoway' or bi-directional values.

`od_id*` functions take two vectors of equal length and return a vector
of IDs, which are unique for each combination but the same for twoway
flows.

- the Szudzik pairing function, on two vectors of equal length. It
  returns a vector of ID numbers.

This function superseeds od_id_order as it is faster on large datasets

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
[`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md),
[`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
(d <- od_data_sample[2:9, 1:2])
#> # A tibble: 8 × 2
#>   geo_code1 geo_code2
#>   <chr>     <chr>    
#> 1 E02002361 E02002363
#> 2 E02002361 E02002367
#> 3 E02002361 E02002371
#> 4 E02002361 E02002377
#> 5 E02002361 E02002382
#> 6 E02002361 E02002384
#> 7 E02002361 E02002393
#> 8 E02002363 E02002361
(id <- od_id_character(d[[1]], d[[2]]))
#> [1] "E02002361 E02002363" "E02002361 E02002367" "E02002361 E02002371"
#> [4] "E02002361 E02002377" "E02002361 E02002382" "E02002361 E02002384"
#> [7] "E02002361 E02002393" "E02002361 E02002363"
duplicated(id)
#> [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
od_id_szudzik(d[[1]], d[[2]])
#> [1]  5 10 17 26 37 50 65  5
od_id_max_min(d[[1]], d[[2]])
#> [1]  4  7 11 16 22 29 37  4
```
