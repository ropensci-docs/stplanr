# Split route based on the id or coordinates of one of its vertices

Split route based on the id or coordinates of one of its vertices

## Usage

``` r
route_split_id(r, id = NULL, p = NULL)
```

## Arguments

- r:

  An `sf` object with one feature containing a linestring geometry to be
  split

- id:

  The index of the point on the number to be split

- p:

  A point represented by an `sf` object the will split the `route`

## Examples

``` r
sample_routes <- routes_fast_sf[2:6, 3]
r <- sample_routes[2, ]
id <- round(n_vertices(r) / 2)
r_split <- route_split_id(r, id = id)
plot(r$geometry, lwd = 9, col = "grey")
plot(r_split, col = c("red", "blue"), add = TRUE)
```
