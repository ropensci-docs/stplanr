# Plan routes on the transport network using the OSRM server

This function is a simplified and (because it uses GeoJSON not binary
polyline format) slower R interface to OSRM routing services compared
with the excellent
[`osrm::osrmRoute()`](https://rdrr.io/pkg/osrm/man/osrmRoute.html)
function (which can be used via the
[`route()`](https://docs.ropensci.org/stplanr/reference/route.md))
function.

## Usage

``` r
route_osrm(
  from,
  to,
  osrm.server = "https://routing.openstreetmap.de/",
  osrm.profile = "foot"
)
```

## Arguments

- from:

  An object representing origins (if lines are provided as the first
  argument, from is assigned to `l`)

- to:

  An object representing destinations

- osrm.server:

  The base URL of the routing server. getOption("osrm.server") by
  default.

- osrm.profile:

  The routing profile to use, e.g. "car", "bike" or "foot" (when using
  the routing.openstreetmap.de test server). getOption("osrm.profile")
  by default.

- profile:

  Which routing profile to use? One of "foot" (default) "bike" or "car"
  for the default open server.

## See also

Other routes:
[`route()`](https://docs.ropensci.org/stplanr/reference/route.md),
[`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)

## Examples

``` r
# \donttest{
# Examples no longer working due to API being down
# l1 = od_data_lines[49, ]
# l1m = od_coords(l1)
# from = l1m[, 1:2]
# to = l1m[, 3:4]
# if(curl::has_internet()) {
# r_foot = route_osrm(from, to)
# r_bike = route_osrm(from, to, osrm.profile = "bike")
# r_car = route_osrm(from, to, osrm.profile = "car")
# plot(r_foot$geometry, lwd = 9, col = "grey")
# plot(r_bike, col = "blue", add = TRUE)
# plot(r_car, col = "red", add = TRUE)
# }
# }
```
