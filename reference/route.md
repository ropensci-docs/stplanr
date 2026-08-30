# Plan routes on the transport network

Takes origins and destinations, finds the optimal routes between them
and returns the result as a spatial (sf or sp) object. The definition of
optimal depends on the routing function used

## Usage

``` r
route(
  from = NULL,
  to = NULL,
  l = NULL,
  route_fun = cyclestreets::journey,
  wait = 0,
  n_print = 10,
  list_output = FALSE,
  cl = NULL,
  ...
)
```

## Arguments

- from:

  An object representing origins (if lines are provided as the first
  argument, from is assigned to `l`)

- to:

  An object representing destinations

- l:

  A spatial (linestring) object

- route_fun:

  A routing function to be used for converting the lines to routes

- wait:

  How long to wait between routes? 0 seconds by default, can be useful
  when sending requests to rate limited APIs.

- n_print:

  A number specifying how frequently progress updates should be shown

- list_output:

  If FALSE (default) assumes spatial (linestring) object output. Set to
  TRUE to save output as a list.

- cl:

  Cluster

- ...:

  Arguments passed to the routing function

## See also

Other routes:
[`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md),
[`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)

Other routes:
[`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md),
[`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)

## Examples

``` r
# Todo: add examples
```
