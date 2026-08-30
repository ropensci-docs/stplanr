# Scale a bounding box

Takes a bounding box as an input and outputs a bounding box of a
different size, centred at the same point.

## Usage

``` r
bbox_scale(bb, scale_factor)
```

## Arguments

- bb:

  Bounding box object

- scale_factor:

  Numeric vector determining how much the bounding box will grow or
  shrink. Two numbers refer to extending the bounding box in x and y
  dimensions, respectively. If the value is 1, the output size will be
  the same as the input.

## See also

Other geo:
[`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md),
[`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md),
[`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md),
[`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md),
[`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md),
[`geo_projected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md),
[`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md),
[`quadrant()`](https://docs.ropensci.org/stplanr/reference/quadrant.md)

## Examples

``` r
bb <- matrix(c(-1.55, 53.80, -1.50, 53.83), nrow = 2)
bb1 <- bbox_scale(bb, scale_factor = 1.05)
bb2 <- bbox_scale(bb, scale_factor = c(2, 1.05))
bb3 <- bbox_scale(bb, 0.1)
plot(x = bb2[1, ], y = bb2[2, ])
points(bb1[1, ], bb1[2, ])
points(bb3[1, ], bb3[2, ])
points(bb[1, ], bb[2, ], col = "red")
```
