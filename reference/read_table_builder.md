# Import and format Australian Bureau of Statistics (ABS) TableBuilder files

Import and format Australian Bureau of Statistics (ABS) TableBuilder
files

## Usage

``` r
read_table_builder(dataset, filetype = "csv", sheet = 1, removeTotal = TRUE)
```

## Arguments

- dataset:

  Either a dataframe containing the original data from TableBuilder or a
  character string containing the path of the unzipped TableBuilder
  file.

- filetype:

  A character string containing the filetype. Valid values are 'csv',
  'legacycsv' and 'xlsx' (default = 'csv'). Required even when dataset
  is a dataframe. Use 'legacycsv' for csv files derived from earlier
  versions of TableBuilder for which csv outputs were csv versions of
  the xlsx files. Current csv output from TableBuilder follow a more
  standard csv format.

- sheet:

  An integer value containing the index of the sheet in the xlsx file
  (default = 1).

- removeTotal:

  A boolean value. If TRUE removes the rows and columns with totals
  (default = TRUE).

## Details

The Australian Bureau of Statistics (ABS) provides customised tables for
census and other datasets in a format that is difficult to use in R
because it contains rows with additional information. This function
imports the original (unzipped) TableBuilder files in .csv or .xlsx
format before creating an R dataframe with the data.

Note: we recommend using the
[readabs](https://github.com/mattcowgill/readabs) package for this
purpose.

## See also

Other data:
[`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md),
[`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md),
[`flow`](https://docs.ropensci.org/stplanr/reference/flow.md),
[`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md),
[`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md),
[`od_data_lines`](https://docs.ropensci.org/stplanr/reference/od_data_lines.md),
[`od_data_routes`](https://docs.ropensci.org/stplanr/reference/od_data_routes.md),
[`od_data_sample`](https://docs.ropensci.org/stplanr/reference/od_data_sample.md),
[`osm_net_example`](https://docs.ropensci.org/stplanr/reference/osm_net_example.md),
[`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md),
[`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md),
[`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md),
[`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md),
[`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)
