# Get a route from the BikeCitizens web service

See
[bikecitizens.net](https://map.bikecitizens.net/gb-leeds#/!/1/1/53.8265,-1.576195/53.80025,-1.51577)
for an interactive version of the routing engine used by BikeCitizens.

## Usage

``` r
route_bikecitizens(
  from = NULL,
  to = NULL,
  base_url = "https://map.bikecitizens.net/api/v1/locations/route.json",
  cccode = "gb-leeds",
  routing_profile = "balanced",
  bike_profile = "citybike",
  from_lat = 53.8265,
  from_lon = -1.576195,
  to_lat = 53.80025,
  to_lon = -1.51577
)
```

## Arguments

- from:

  A numeric vector representing the start point

- to:

  A numeric vector representing the end point

- base_url:

  The base URL for the routes

- cccode:

  The city code for the routes

- routing_profile:

  What type of routing to use?

- bike_profile:

  What type of bike?

- from_lat:

  Latitude of origin

- from_lon:

  Longitude of origin

- to_lat:

  Latitude of destination

- to_lon:

  Longitude of destination

## Details

See the bikecitizens.R file in the data-raw directory of the package's
development repository for details on usage and examples.
