# Get points at the beginner and end of linestrings

Get points at the beginner and end of linestrings

## Usage

``` r
rnet_boundary_points(rnet)

rnet_boundary_df(rnet)

rnet_boundary_unique(rnet)

rnet_boundary_points_lwgeom(rnet)

rnet_duplicated_vertices(rnet, n = 2)
```

## Arguments

- rnet:

  An sf or sfc object with LINESTRING geometry representing a route
  network.

- n:

  The minimum number of time a vertex must be duplicated to be returned

## Examples

``` r
has_sfheaders <- requireNamespace("sfheaders", quietly = TRUE)
if(has_sfheaders) {
rnet <- rnet_roundabout
bp1 <- rnet_boundary_points(rnet)
bp2 <- line2points(rnet) # slower version with lwgeom
bp3 <- rnet_boundary_points_lwgeom(rnet) # slower version with lwgeom
bp4 <- rnet_boundary_unique(rnet)
nrow(bp1)
nrow(bp3)
identical(sort(sf::st_coordinates(bp1)), sort(sf::st_coordinates(bp2)))
identical(sort(sf::st_coordinates(bp3)), sort(sf::st_coordinates(bp4)))
plot(rnet$geometry)
plot(bp3, add = TRUE)
}
```
