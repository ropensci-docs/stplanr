# Summary statistics of trips arriving at destination zones in OD data

This function takes a data frame of OD data and returns a data frame
reporting summary statistics for each unique zone of destination.

## Usage

``` r
od_aggregate_to(flow, attrib = NULL, FUN = sum, ..., col = 2)
```

## Arguments

- flow:

  A data frame representing origin-destination data. The first two
  columns of this data frame should correspond to the first column of
  the data in the zones. Thus in
  [`cents_sf()`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
  the first column is geo_code. This corresponds to the first two
  columns of
  [`flow()`](https://docs.ropensci.org/stplanr/reference/flow.md).

- attrib:

  character, column names in sl to be aggregated

- FUN:

  A function to summarise OD data by

- ...:

  Additional arguments passed to `FUN`

- col:

  The column that the OD dataset is grouped by (1 by default, the first
  column usually represents the origin)

## Details

It has some default settings: it assumes the destination ID column is
the 2nd and the default summary statistic is
[`sum()`](https://rdrr.io/r/base/sum.html). By default, if `attrib` is
not set, it summarises all numeric columns.

## See also

Other od:
[`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
[`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md),
[`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md),
[`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md),
[`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md),
[`od_id`](https://docs.ropensci.org/stplanr/reference/od_id.md),
[`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md),
[`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md),
[`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md),
[`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md),
[`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md),
[`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)

## Examples

``` r
od_aggregate_to(flow)
#> # A tibble: 7 × 13
#>   Area.of.workplace   All Work.mainly.at.or.from.…¹ Underground..metro..…² Train
#>   <chr>             <int>                     <int>                  <int> <int>
#> 1 E02002361           207                         0                      0     0
#> 2 E02002363           467                         0                      0     5
#> 3 E02002367           115                         0                      0     1
#> 4 E02002371           539                         0                      0     2
#> 5 E02002377           324                         0                      0     0
#> 6 E02002382           209                         0                      1     0
#> 7 E02002393           955                         0                      0     4
#> # ℹ abbreviated names: ¹​Work.mainly.at.or.from.home,
#> #   ²​Underground..metro..light.rail..tram
#> # ℹ 8 more variables: Bus..minibus.or.coach <int>, Taxi <int>,
#> #   Motorcycle..scooter.or.moped <int>, Driving.a.car.or.van <int>,
#> #   Passenger.in.a.car.or.van <int>, Bicycle <int>, On.foot <int>,
#> #   Other.method.of.travel.to.work <int>
```
