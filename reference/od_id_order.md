# Generate ordered ids of OD pairs so lowest is always first This function is slow on large datasets, see szudzik_pairing for faster alternative

Generate ordered ids of OD pairs so lowest is always first This function
is slow on large datasets, see szudzik_pairing for faster alternative

## Usage

``` r
od_id_order(x, id1 = names(x)[1], id2 = names(x)[2])
```

## Arguments

- x:

  A data frame or SpatialLinesDataFrame, representing an OD matrix

- id1:

  Optional (it is assumed to be the first column) text string referring
  to the name of the variable containing the unique id of the origin

- id2:

  Optional (it is assumed to be the second column) text string referring
  to the name of the variable containing the unique id of the
  destination

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
[`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md),
[`od_id`](https://docs.ropensci.org/stplanr/reference/od_id.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
x <- data.frame(id1 = c(1, 1, 2, 2, 3), id2 = c(1, 2, 3, 1, 4))
od_id_order(x) # 4th line switches id1 and id2 so stplanr.key is in order
#>   stplanr.id1 stplanr.id1.1 stplanr.key
#> 1           1             1         1 1
#> 2           1             2         1 2
#> 3           2             3         2 3
#> 4           2             1         1 2
#> 5           3             4         3 4
```
