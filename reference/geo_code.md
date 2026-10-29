# Convert text strings into points on the map

Generate a lat/long pair from data using Google's geolocation API.

## Usage

``` r
geo_code(
  address,
  service = "nominatim",
  base_url = "https://maps.google.com/maps/api/geocode/json",
  return_all = FALSE,
  pat = NULL
)
```

## Arguments

- address:

  Text string representing the address you want to geocode

- service:

  Which service to use? Nominatim by default

- base_url:

  The base url to query

- return_all:

  Should the request return all information returned by Google Maps? The
  default is `FALSE`: to return only two numbers: the longitude and
  latitude, in that order

- pat:

  Personal access token

## Examples

``` r
if (FALSE) { # \dontrun{
geo_code(address = "Hereford")
geo_code("LS7 3HB")
geo_code("hereford", return_all = TRUE)
# needs api key in .Renviron
geo_code("hereford", service = "google", pat = Sys.getenv("GOOGLE"), return_all = TRUE)
} # }
```
