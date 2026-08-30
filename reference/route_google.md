# Find shortest path using Google services

Find the shortest path using Google's services. See the `mapsapi`
package for details.

## Usage

``` r
route_google(from, to, mode = "walking", key = Sys.getenv("GOOGLE"), ...)
```

## Arguments

- from:

  An object representing origins (if lines are provided as the first
  argument, from is assigned to `l`)

- to:

  An object representing destinations

- mode:

  Mode of transport, walking (default), bicycling, transit, or driving

- key:

  Google key. By default it is `Sys.getenv("GOOGLE")`. Set it with:
  [`usethis::edit_r_environ()`](https://usethis.r-lib.org/reference/edit.html).

- ...:

  Arguments passed to the routing function

## Examples

``` r
if (FALSE) { # \dontrun{
from <- "university of leeds"
to <- "pedallers arms leeds"
r <- route(from, to, route_fun = cyclestreets::journey)
plot(r)
# r_google <- route(from, to, route_fun = mapsapi::mp_directions) # fails
r_google1 <- route_google(from, to)
plot(r_google1)
r_google <- route(from, to, route_fun = route_google)
} # }
```
