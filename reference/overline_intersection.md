# Convert series of overlapping lines into a route network

This function takes overlapping `LINESTRING`s stored in an `sf` object
and returns a route network composed of non-overlapping geometries and
aggregated values.

## Usage

``` r
overline_intersection(sl, attrib, fun = sum)
```

## Arguments

- sl:

  An `sf` `LINESTRING` object with overlapping elements

- attrib:

  character, column names in sl to be aggregated

- fun:

  Named list of functions to summaries the attributes by? `sum` is the
  default. `list(sum = sum, average = mean)` will summarise all
  `attrib`utes by sum and mean.

## Examples

``` r
routes_fast_sf$value <- 1
sl <- routes_fast_sf[4:6, ]
attrib <- c("value", "length")
rnet <- overline_intersection(sl = sl, attrib)
#> although coordinates are longitude/latitude, st_intersection assumes that they
#> are planar
plot(rnet, lwd = rnet$value)

# A larger example
sl <- routes_fast_sf[4:7, ]
rnet <- overline_intersection(sl = sl, attrib = c("value", "length"))
#> although coordinates are longitude/latitude, st_intersection assumes that they
#> are planar
plot(rnet, lwd = rnet$value)

rnet_sf <- overline(routes_fast_sf[4:7, ], attrib = c("value", "length"))
plot(rnet_sf, lwd = rnet_sf$value)


# An even larger example (not shown, takes time to run)
# rnet = overline_intersection(routes_fast_sf, attrib = c("value", "length"))
# rnet_sf <- overline(routes_fast_sf, attrib = c("value", "length"), buff_dist = 10)
# plot(rnet$geometry, lwd = rnet$value * 2, col = "grey")
# plot(rnet_sf$geometry,  lwd = rnet_sf$value, add = TRUE)
```
