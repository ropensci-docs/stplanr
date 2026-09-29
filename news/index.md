# Changelog

## stplanr 1.2.3 (2025-04)

CRAN release: 2025-04-21

- Added `wt_profile` parameter passthrough to `route_dodgr` within the
  main [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function.
- Made examples for
  [`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)
  conditional on the `igraph` package being installed.
- General documentation updates.

## stplanr 1.2.2 (2024-07)

CRAN release: 2024-08-22

- CRAN checks fixed
  ([\#563](https://github.com/ropensci/stplanr/issues/563))

## stplanr 1.2.1

CRAN release: 2024-05-01

- Fixed bug causing errors when `length(n_segments) > 1`
  ([\#560](https://github.com/ropensci/stplanr/issues/560))

## stplanr 1.2.0 (2024-04)

CRAN release: 2024-04-26

- Various fixes for
  [`rnet_join()`](https://docs.ropensci.org/stplanr/reference/rnet_join.md)
  (now recommended over
  [`rnet_merge()`](https://docs.ropensci.org/stplanr/reference/rnet_merge.md))
  and
  [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  ([\#552](https://github.com/ropensci/stplanr/issues/552))
- [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  now will use
  [`rsgeo::line_segmentize()`](https://josiahparry.r-universe.dev/rsgeo/reference/line_segmentize.html)
  if available
- [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  becomes an S3 generic which now has methods for `sf` and `sfc` class
  objects
- [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  now works around [{rsgeo}
  issue](https://github.com/JosiahParry/rsgeo/issues/42) with
  `line_segmentize()` returning fewer segments than requested
  ([\#552](https://github.com/ropensci/stplanr/issues/552))
- Removal of offending URLs with `urlchecker::check_urls()`
- Improvement of documentation of
  [`line_midpoint()`](https://docs.ropensci.org/stplanr/reference/line_midpoint.md):
  comparison of output with
  [`sf::st_point_on_surface()`](https://r-spatial.github.io/sf/reference/geos_unary.html)

## stplanr 1.1.2 (2023-09)

CRAN release: 2023-09-15

- Export S3 methods

## stplanr 1.1.1 (2023-09)

- Fixed URLs and other things for CRAN

## stplanr 1.1.0 (2023-09)

- New function
  [`rnet_merge()`](https://docs.ropensci.org/stplanr/reference/rnet_merge.md)
  and related changes, new contributor Zhao Wang
- [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  is now vectorised
  ([\#518](https://github.com/ropensci/stplanr/issues/518))
- Assorted fixes, see
  <https://github.com/ropensci/stplanr/issues?q=is%3Aissue+is%3Aclosed>
  for details

## stplanr 1.0.2

CRAN release: 2022-11-08

- Update docs, fix missing functions issue
  ([\#499](https://github.com/ropensci/stplanr/issues/499))

## stplanr 1.0.1

CRAN release: 2022-08-19

- Fix for breaking change in `dodgr`
  ([\#494](https://github.com/ropensci/stplanr/issues/494))

## stplanr 1.0.0

CRAN release: 2022-06-10

- Remove dependency on `sp`, `rgeos` and `rgdal`
  ([\#332](https://github.com/ropensci/stplanr/issues/332))
- That involved removal of the following functions:
  - [catchmentArea.R](https://github.com/ropensci/stplanr/releases)
  - Some of the functionality from
    [linefuns.R](https://github.com/ropensci/stplanr/releases)
  - Browse the code base as of stplanr 0.8.5 here:
    <https://github.com/ropensci/stplanr/releases>
- Removal of ‘ABS’ reading functionality in favour of
  <https://github.com/mattcowgill/readabs>

## stplanr 0.9.0 (May 2022)

CRAN release: 2022-05-11

- Message added on loading the package announcing planned changes:
  support for `sp` objects and associated packages will be dropped
  ([\#332](https://github.com/ropensci/stplanr/issues/332))
- New function `line_segment_sf()`
  ([\#482](https://github.com/ropensci/stplanr/issues/482))
- Various changes required by CRAN
  ([\#486](https://github.com/ropensci/stplanr/issues/486))

## stplanr 0.8.7 (February 2022)

CRAN release: 2022-02-01

- [`route()`](https://docs.ropensci.org/stplanr/reference/route.md) now
  runs batch routing when input is a linestring and `opentripplanner` is
  installed ([\#459](https://github.com/ropensci/stplanr/issues/459))

## stplanr 0.8.6 (November 2021)

CRAN release: 2021-11-26

- [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  checks the CRS and gives an appropriate warning if it is projected
- The package now Suggests igraph rather than depending on it making it
  easier to install

## stplanr 0.8.5

CRAN release: 2021-11-01

- No longer Suggests stats19 package

## stplanr 0.8.4

CRAN release: 2021-10-12

- No longer Suggests bench package
- Tests pass when internet unavailable
  ([\#469](https://github.com/ropensci/stplanr/issues/469))

## stplanr 0.8.3

CRAN release: 2021-07-22

- Outputs of
  [`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md)
  now have correct CRS
- `calc_catchment()` have been deprecated because the generate warnings
- Minor fixes and improvements in the package’s documentation

## stplanr 0.8.2

CRAN release: 2021-04-06

- Bug fixed related to the
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function: it silently failed when `pbapply` not installed. The package
  was promoted from Suggests to Imports
  ([\#460](https://github.com/ropensci/stplanr/issues/460))

## stplanr 0.8.1

CRAN release: 2021-01-07

- Thanks to the `styler` package, code in `stplanr` now adheres to a
  consistent style (using arrow `<-` assignment despite the maintainer’s
  default of equals `=` assignment - many `=` had been introduced
  accidentally!)
- New function
  [`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)
  groups route network elements
  ([\#403](https://github.com/ropensci/stplanr/issues/403))
- [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  now converts `MULTILINESTRING` geometries to `LINESTRINGS`
  automatically
- Routing on the network using `sum_network_routes()` now returns a
  linestring for routes that start where they end (i.e. no travel)
  ([\#444](https://github.com/ropensci/stplanr/issues/444))
- Routing using `route_local()` fixed: the `l` argument now works
  ([\#448](https://github.com/ropensci/stplanr/issues/448))
- New
  [`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)
  function ([\#449](https://github.com/ropensci/stplanr/issues/449))
- [`rnet_breakup_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_breakup_vertices.md)
  is now way faster, thanks to Andrea Gilardi and others
  ([\#416](https://github.com/ropensci/stplanr/issues/416))
- [`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)
  is now a generic function that works with `sfNetwork` objects
  ([\#455](https://github.com/ropensci/stplanr/issues/455))
- [`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)
  provides easy access to multi-modal routing
  ([\#449](https://github.com/ropensci/stplanr/issues/449))
- Bug in
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function’s calculation of bbox attributes fixed
  ([\#452](https://github.com/ropensci/stplanr/issues/452))

## stplanr 0.8.0

CRAN release: 2020-10-28

- New function
  [`line_breakup()`](https://docs.ropensci.org/stplanr/reference/line_breakup.md)
  breaks-up lines
  ([\#434](https://github.com/ropensci/stplanr/issues/434))
- Minor documentation fixes, including
  ([\#431](https://github.com/ropensci/stplanr/issues/431))

## stplanr 0.7.2

CRAN release: 2020-09-04

- Support `sf` objects for
  [`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)
- Updated examples for tests and README to enable tests to pass on
  legacy versions of PROJ
  ([\#423](https://github.com/ropensci/stplanr/issues/423))
- Reduce vulnerability to upcoming upstream changes
  ([\#426](https://github.com/ropensci/stplanr/issues/426))

## stplanr 0.7.1

CRAN release: 2020-08-28

- Tweaks to the documentation and examples for CRAN tests

## stplanr 0.7.0

CRAN release: 2020-08-27

- Issue with
  [`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  on some set-ups fixed
  ([\#418](https://github.com/ropensci/stplanr/issues/418))
- Old `mapshape()`, `line_match()` and `gclip()` functions deprecated,
  maintained alternatives can now be found in other packages.
- `sp` objects updated for latest version of `sp`
  ([\#364](https://github.com/ropensci/stplanr/issues/364))
- `sf` objects updated to support more recent CRS encoding
  ([\#393](https://github.com/ropensci/stplanr/issues/393))
- Deprecated functions including `od_aggregate()`, `onewayid()`,
  `gtfs2sldf()`, and `od_radiation()` have been removed

## stplanr 0.6.2

CRAN release: 2020-07-08

### New features

- New interface to Google Directions API via `mapsapi` package
  ([\#410](https://github.com/ropensci/stplanr/issues/410))
- New `quiet` argument in
  [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  makes it less chatty

## stplanr 0.6.1

CRAN release: 2020-06-23

### BUG FIXES

- [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  failed when `data.table` not installed
  ([\#408](https://github.com/ropensci/stplanr/issues/408))

## stplanr 0.6.0

CRAN release: 2020-05-03

### BUG FIXES

- Bug in `SpatialLinesNetwork()` fixed thanks to Andrea Gilardi
  ([\#394](https://github.com/ropensci/stplanr/issues/394))
- Updated documentation for finding shortest paths
- Check `start` and `end` arguments in short path calculations are
  numeric
- `dodgr` removed as Suggests until it’s back on CRAN
  ([\#398](https://github.com/ropensci/stplanr/issues/398))
- Updates to `dplyr` code to prevent warnings when using the dev version
  ([\#395](https://github.com/ropensci/stplanr/issues/395))

### NEW FEATURES

- Improvements to
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  allowing you to save a list of raw outputs and use `data.table` for
  faster performance if available
- A fleet of new `route_rolling_*()` functions have been added:
  - [`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md)
    calculates a rolling gradient from elevation and distance data at
    the segment level
  - [`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md)
    calculates the rolling average of values
  - [`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md)
    calculates the rolling difference between each value and the next
- [`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md)
  function now has `sf` implementation
  ([\#390](https://github.com/ropensci/stplanr/issues/390))
- New `cl` argument in
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md) for
  parallel routing
  ([\#388](https://github.com/ropensci/stplanr/issues/388))
- New and updated datasets representing `od_data_sample` in different
  ways: `od_data_lines` and `od_data_routes`
- `route_graphhopper()` deprecated
  ([\#389](https://github.com/ropensci/stplanr/issues/389))
- Old functions that use legacy `sp` and `dplyr` code, `sp_aggregate`
  and `od_aggregate`, have been deprecated
- New work-in-progress `route_slope*()` functions

## stplanr 0.5.2

CRAN release: 2020-04-06

### BUG FIXES

- Documentation fixes
  ([\#384](https://github.com/ropensci/stplanr/issues/384))
- A bug affecting
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function calls when `pbapply` was not installed has been fixed
  ([\#386](https://github.com/ropensci/stplanr/issues/386))
- `oneway()` has been deprecated in favour of faster and
  easier-to-maintain function
  [`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md)
  (also see the in-development `od` package)
  ([\#387](https://github.com/ropensci/stplanr/issues/387))
- Various other changes have been made to accomodate the dev version of
  `dplyr` ([\#383](https://github.com/ropensci/stplanr/issues/383))

## stplanr 0.5.1

CRAN release: 2020-03-01

- Changes for compatibility with R 4.0.0

## stplanr 0.5.0

CRAN release: 2020-01-26

- `route_graphhopper()` should now work with a local graphhopper
  instance. See <https://github.com/ropensci/stplanr/pull/369>
- The old `line2route()` function now works with routing functions that
  return `sf` objects
- The new
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function is now more resilient, providing a progress bar if you have
  `pbapply` package installed, returning a result even if some routes
  failed, and telling you which routes failed
- The package has fewer dependencies, `readr`, `openxlsx` and
  `lubridate` removed
- Deprecated function `buff_geo()` removed

### BUG FIXES

- `destination` now works again as an argument in `line2route()`
  ([\#368](https://github.com/ropensci/stplanr/issues/368))
- [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  now accepts `sf` objects regardless of the name of the geometry column
- [`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  now works with `sfc` objects
  ([\#361](https://github.com/ropensci/stplanr/issues/361))

## stplanr 0.4.1

CRAN release: 2019-11-23

### NEW FEATURES

- Better error messages if
  [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md)
  fails due to non-matching ids
- Improved documentation of
  [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md)
  in the vignette:
  <https://docs.ropensci.org/stplanr/articles/stplanr-od.html#non-matching-ids>

## stplanr 0.4.0

CRAN release: 2019-10-13

### NEW FEATURES

- A family of new functions, including
  [`route_split()`](https://docs.ropensci.org/stplanr/reference/route_split.md),
  [`rnet_add_node()`](https://docs.ropensci.org/stplanr/reference/rnet_add_node.md)
  and `sln_add_node()` for adding new nodes to routes, route networks
  and `sfNetwork` objects, closing
  [\#342](https://github.com/ropensci/stplanr/issues/342)
- Updated vignette on route networks, solving
  [\#237](https://github.com/ropensci/stplanr/issues/237), which can be
  found here:
  <https://docs.ropensci.org/stplanr/articles/stplanr-route-nets.html>
- [Fix](https://github.com/ropensci/stplanr/commit/592fba2a6d191135d036af73e7c902c3ef4f758c)
  in
  [`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
- `line_to_points()` function removed in favour of `line2point()`.
- New function `sln_clean_graph()` removes unconnected elements of
  `sfNetwork` objects. Credit to Andrea Gilardi. See
  ([\#344](https://github.com/ropensci/stplanr/issues/344)).
- New functions
  [`rnet_breakup_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_breakup_vertices.md)
  and
  [`line2vertices()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  for breaking up linestrings representing route networks into smaller
  segments, in preparation for routing. See
  ([\#282](https://github.com/ropensci/stplanr/issues/282)) (which these
  functions address) and PR
  ([\#347](https://github.com/ropensci/stplanr/issues/347)) for details.

### BUG FIXES

- Bugs in
  [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  and associated examples fixed
  ([\#348](https://github.com/ropensci/stplanr/issues/348))
- Annoying message printed on load removed
  ([\#355](https://github.com/ropensci/stplanr/issues/355))

### OTHER

- Andrea Gilardi added as author.
- Deprecated functions related to road crash (STATS19) data removed

## stplanr 0.3.1

CRAN release: 2019-09-17

- stplanr now has a logo! See
  [\#334](https://github.com/ropensci/stplanr/issues/334)
- `line_to_points()` depreciated in favour of
  [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md),
  the latter function name being more consistent with the package’s
  other functions
- [`line2pointsn()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  now works with `sf` objects
- Documentation fixes - see
  [\#329](https://github.com/ropensci/stplanr/issues/329)

### OTHER

- Various improvements made to the `stplanr-od` vignette, thanks to
  Edward Leigh
- URLs updated to link to stplanr’s new, official website:
  <https://docs.ropensci.org/stplanr/>

## stplanr 0.3.0

CRAN release: 2019-07-30

### NEW FEATURES

- New functions
  [`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md)
  and
  [`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md)
  to convert between matrix forms of origin-destination data
- New function
  [`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md)
  replaces `onewayid()`, works better and is twice as fast
- New `od_id*()` functions provide a range of ways to convert
  origin-destination pair IDs into a single ID. See
  [Stackoverflow](https://stackoverflow.com/questions/57235601/how-to-identify-duplicated-ordered-pairs-efficiently/57236658#57236658)
  and the [issue
  tracker](https://github.com/ropensci/stplanr/issues/321)
- New vignette
  [`stplanr-od`](https://docs.ropensci.org/stplanr/articles/stplanr-od.html)
  provides detailed documentation on the package’s OD data handling
  capabilities

## stplanr 0.2.10

CRAN release: 2019-05-18

- Fix in documentation. See
  [\#311](https://github.com/ropensci/stplanr/issues/311)

## stplanr 0.2.9

CRAN release: 2019-05-10

### NEW FEATURES

- New functions
  [`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md)
  and
  [`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md)
  provide easy ways to aggregate origin-destination pairs. See
  [\#303](https://github.com/ropensci/stplanr/pull/303).
- Updated
  [`overline2()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  is now faster and better documented
  ([\#307](https://github.com/ropensci/stplanr/issues/307))
- Updates to
  [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  function, which provides an interface to the
  [dodgr](https://github.com/UrbanAnalyst/dodgr) package, accepts wider
  range of inputs
- Better website and updated function list. See
  <https://ropensci.github.io/stplanr/index.html>
- The `sf` method for
  [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  has been updated so it calls the much faster
  [`overline2()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  function
- Updated documentation for `route_local()`

### BUG FIXES

- Bug in `sum_network_routes()` fixed. See
  [\#267](https://github.com/ropensci/stplanr/issues/267)

## stplanr 0.2.8

CRAN release: 2019-03-22

### NEW FEATURES

- The stplanr paper has been published! See it here:
  <https://journal.r-project.org/archive/2018/RJ-2018-053/index.html>
- STATS19 functions such as `dl_stats19()` are depreciated. They have
  been split-out into the new package
  [`stats19`](https://github.com/ropensci/stats19)
- [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  has now been implemented
- A new function
  [`overline2()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  has been added, thanks to Malcolm Morgan. This is faster than
  [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md).
- A substantial refactoring operation has begun. This has resulted in
  fewer lines of code in the `od` functions, a new
  [`stplanr::od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md)
  function, and more support of `sf`
- [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  has been added
- A new example dataset, `osm_net_example`, has been added for local
  routing purposes.
- A citation to the package has been added. Try `citation("stplanr")`
- The package has a shiny new website thanks to `@maelle`:
  <https://ropensci.github.io/stplanr/>
- The package looses its Imports dependency on rgdal, which has been
  demoted to a Suggests

### BUG FIXES

- An issue with `route_graphhopper()` has been fixed, see
  <https://github.com/ropensci/stplanr/pull/297>

## stplanr 0.2.7

CRAN release: 2019-01-07

### NEW FEATURES

- Various changes to support `dplyr` \[0.8.0\]:
  <https://github.com/ropensci/stplanr/pull/275>

### BUG FIXES

- Fixed [\#272](https://github.com/ropensci/stplanr/issues/272) by
  removing byvars argument of overline in preparation for overdue
  overhaul of overline function.

### OTHER

- No longer suggests **tmap** to reduce install times:
  [`install.packages()`](https://rdrr.io/r/utils/install.packages.html)
  installs suggested packages by default

## stplanr 0.2.6

CRAN release: 2018-10-20

### NEW FEATURES

- New function `route_local()`
- New argument in `line2route()`: `time_sleep` waits a period between
  each route request

### BUG FIXES

- Issue with `dl_stats19()`, see
  [\#270](https://github.com/ropensci/stplanr/issues/270)
- Make style consistent, see
  [commit](https://github.com/ropensci/stplanr/commit/521598c329c15ff2dfeb159b0da4ba7b1507b060)
- Various small fixes to documentation and style

## stplanr 0.2.5

CRAN release: 2018-06-02

### NEW FEATURES

- New function
  [`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md)
  for identifying intermediary points on a transport network

### BUG FIXES

- Bug associated with `SpatialLinesNetwork()` fixed (see
  [\#249](https://github.com/ropensci/stplanr/issues/249))

## stplanr 0.2.4

CRAN release: 2018-05-19

### NEW FEATURES

- New function
  [`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md)
  returns numeric vector of line lengths from **sp** or **sf** objects.

### DOCUMENTATION

- `?route_graphhopper` no longer mentions the depreciated ‘bike2’
  profile - see [\#246](https://github.com/ropensci/stplanr/issues/246)
- [`?route_osrm`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)
  mentions that the public API only routes for cars - see
  [\#246](https://github.com/ropensci/stplanr/issues/246)
- Updated `introducing-stplanr` vignette to show new function and make
  more robust

## stplanr 0.2.3

CRAN release: 2018-03-06

### NEW FEATURES

- **stplanr** now imports **lwgeom**, needed for
  [`sf::st_length()`](https://r-spatial.github.io/sf/reference/geos_measures.html),
  used in `SpatialLinesNetwork()`.
- Plotting behaviour updated for `sfNetwork` objects: now only plots the
  geometry by default.
- Improved documentation for `SpatialLinesNetwork()` and
  [`plot()`](https://rdrr.io/r/graphics/plot.default.html) for spatial
  networks.

### BUG FIXES

- Bug in `sum_network_routes()` fixed (see
  [\#240](https://github.com/ropensci/stplanr/issues/240)).

## stplanr 0.2.2

CRAN release: 2017-12-19

### NEW FEATURES

- In this release **sp** is demoted from a Depends to an Imports,
  meaning that all its functions will not be attached to your namespace
  (it will not be loaded) when you run
  [`library(stplanr)`](https://docs.ropensci.org/stplanr), making it
  less tied to **sp**. This is a continuation of the work to support
  **sf** and will make it easier for the package to work with
  alternative representations of geographic data.

### BUG FIXES

- Bug in `geo_select_aeq.sf()` was fixed by Jakub Nowosad in pull
  [\#238](https://github.com/ropensci/stplanr/pull/238)
- An issue with `od_aggregate.sf()` was fixed making it much faster

## stplanr 0.2.0

### NEW FEATURES

- This is the largest release since the package was created, with dozens
  of changes to support simple features - see
  <https://github.com/ropensci/stplanr/pull/198> for details.
- Support for **sf**. The package now support the new spatial class
  system for most functions.
- New function
  [`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md)
  supercedes
  [`bb2poly()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md).
  The new function can return polygons, points and matrix objects
  determined by the `output` argument. It also allows bounding boxes to
  be extended in metres, and scaled in x and y dimensions.
- [`geo_code()`](https://docs.ropensci.org/stplanr/reference/geo_code.md)
  now uses nominatim by default to find locations on the maps.
- New function
  [`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md)
  takes a wide range of input data types to return a consistent output
  representing OD data as a data frame of origin and destination
  coordinates. This is used behind the scenes to make other functions
  more modular.

### WORK IN PROGRESS

Plans for the next release

- New generic
  [`route()`](https://docs.ropensci.org/stplanr/reference/route.md)
  function for routing. This is more flexible and user-friendly than the
  existing `line2route()` and `route_*()` functions it enhances.
- Updated function names to make using **stplanr** easier and more
  intuitive.

## stplanr 0.1.9

CRAN release: 2017-07-12

### NEW FEATURES

- Dependency cull: we have removed dependencies on foreach and
  doParallel
- `route_cyclestreet()` now also called (correctly)
  `route_cyclestreets()`
- New
  [`geo_code()`](https://docs.ropensci.org/stplanr/reference/geo_code.md)
  function replaces dependency on RGoogleMaps

### BUG FIXES

- See issues closed after the last release with this search term:
  <https://github.com/ropensci/stplanr/issues?utf8=%E2%9C%93&q=is%3Aissue%20closed%3A%3E2017-06-01%20>
- Bug with `google_dist()` fixed
- Fixed fails due to breaking changes in dplyr

## stplanr 0.1.8

CRAN release: 2017-06-02

### NEW FEATURES

- New argument `combinations` added to `sum_network_routes()` so it runs
  quicker - see
  [pull/177](https://github.com/ropensci/stplanr/pull/177).
- New examples added to `sum_network_routes()`, `weightfield()` and
  `find_network_nodes()` - see e.g. `example(sum_network_routes)` for
  details.
- New dataset `l_poly`
  [added](https://github.com/ropensci/stplanr/commit/7641760fbd6718352ed74142e5c339f6216afea4).
- **stplanr** now has a website! See
  [ropensci.github.io/stplanr/](https://ropensci.github.io/stplanr/).

### BUG FIXES

- Serious bug with `SpatialLinesNetwork()`
  [fixed](https://github.com/ropensci/stplanr/pull/186).
- Depreciated `_each()` **dplyr** functions replaced with equivalent
  `_at` or `_all` functions.

## stplanr 0.1.7

CRAN release: 2016-12-23

### NEW FEATURES

- There is a new vignette! See
  [vignettes/stplanr-paper.Rmd](https://github.com/ropensci/stplanr/blob/master/vignettes/stplanr-paper.Rmd)
  and
  [`vignette("stplanr-paper")`](https://docs.ropensci.org/stplanr/articles/stplanr-paper.md)
  for details.
- The original
  [`introducing-stplanr`](https://github.com/ropensci/stplanr/blob/master/vignettes/stplanr.Rmd)
  vignette has been updated. It now provides a more basic introduction
  for people new to R for spatial and transport data.
- `line2route()` has been refactored to improve error detection and
  allow `n_processes` arguments. Thanks
  [@nikolai-b](https://github.com/nikolai-b). See
  [pull/151](https://github.com/ropensci/stplanr/pull/151) for details.
- `line_match()` function added, a wrapper around `rgeos::gDistance()`,
  to find similar routes.
- **RCurl** and **data.table** dependencies have been
  [removed](https://github.com/ropensci/stplanr/pull/169)
- **leaflet** has been demoted from an import to a suggest. This should
  reduce install times.
- New functions `od_aggregate()` and `sp_aggregate()` have been
  [added](https://github.com/ropensci/stplanr/pull/165), to enable OD
  data to be aggregated to new geographic levels.

### BUG FIXES

- `#141` fixed: `viaroute()` works again.
- [\#153](https://github.com/ropensci/stplanr/issues/153) fixed:
  `bidirectional = TRUE` returns a different result in
  [`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md)
  now.

### FUTURE PLANS

- A new branch that uses **sf** is being
  [tested](https://github.com/ropensci/stplanr/pull/164). We may
  eventually transition to using simple features classes instead of
  **sp** classes.

## stplanr 0.1.6

CRAN release: 2016-11-11

### NEW FEATURES

- `onewayid()` is now a generic function, meaning it can handle spatial
  and non-spatial data
- New arguments provided for `line2route()` allow you to specify
  variables to join-by - also has updated and more sensible defaults
- New function
  [`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md)
  to put origin-destination ids in order, to identify 2 way duplicates
  (split out from `onewayid()`)

### BUG FIXES

- See the [issue
  tracker](https://github.com/ropensci/stplanr/issues?q=is%3Aissue+is%3Aclosed)
- Bug in `route_cyclestreet()` leading `change_elev` and `av_incline`
  being wrong now fixed
- Bug making variable names with spaces in the id columns failed - now
  fixed [\#138](https://github.com/ropensci/stplanr/issues/138)

### stplanr 0.1.5

NEW FEATURES

- New argument destinations added to
  [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md).
  See `example(od2line)` for an example.
- New dataset `destinations` for showing how OD matrix with destinations
  can be converted to spatial data
- New argument `list_output` allows the route information to be saved as
  a list, allowing `save_raw = TRUE` (which does not return a `Spatial`
  object) to be passed to the `route_` function.
- tmap dependency removed for faster installs

BUG FIXES

- Bug with `line2route()`
  ([\#124](https://github.com/ropensci/stplanr/issues/124)) fixed
- Various improvements to documentation

### stplanr 0.1.4

NEW FEATURES

- New function `reproject()` is a simple wrapper around `spTransform()`
  that uses `crs_select_aeq()` to convert a spatial object in geographic
  (lat/lon) coordinates into on with projected coordinates, with units
  of 1 m. This is useful for various spatial operations, such as finding
  the length and area of an object.

- Implement
  [`gprojected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md),
  a function for performing GIS operations on a temporary, projected,
  version of spatial objects.

- Addition of
  [`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md)
  to return the bearing of lines based on start and end points.

- Addition of
  [`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md)
  for finding the angular difference between lines: are they roughly
  parallel or perpendicular?

BUG FIXES

- [`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md)
  now works on lines with multiple vertices and is faster.

- Fixes in the examples used to illustrate how `od_dist()` works.

### stplanr 0.1.3

NEW FEATURES

- Update to OSRM functions to support API v5.

- New parameter `byvars` in the
  [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  function, to allow disaggregation of results by a grouping variable
  (see `example(overline)`).

- Faster implementation of
  [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md):
  `od2line2()`. Plan is to replace the original if no issues are found
  with new implementation.

- New function
  [`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md)
  which converts OD data into a dataframe of origins and destinations
  (feeds `od2line2()` but also useful as self-standing function).

- New argument `new_proj` in `buff_geo()` allows the results to be
  exported to any coordinate reference system (CRS).

- New function
  [`gprojected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md)
  generalises concept of `buff_geo()`, building on `crs_select_aeq()` to
  allow any GIS query to be conducted on a temporary projected version
  of spatial objects with geographical CRSs.

- New function `od_dist()` can quickly calculate Euclidean distances of
  OD pairs without converting to spatial objects.

BUG FIXES

- Bug fix in `onewayid()` so it captures all lines.

- Various improvements to documentation and code.

### stplanr 0.1.2

NEW FEATURES

- Interface to the Google Distance Matrix `API with dist_google`.

- New transport planning API added, with `route_transportapi_public`
  (for testing).

- Update to `line2route`, allowing it to accept different routing
  funtions via the new argument `route_fun` (for testing - tested with
  `route_fun = route_cyclestreet`).

- New functions for creating origin-destination data frames
  (`point2odf`) and SpatialLinesDataFrames (`points2flow`).

- Addition of `n_vertices` and `is_linepoint` for identifying the number
  of vertices in spatial objects and whether the ‘line’ is really a
  point.

BUG FIXES

- `line2route` refactored, with 10 fold speed increases on large (1000+)
  batches of lines.

### stplanr 0.1.0

NEW FEATURES

- Addition of new class definition `SpatialLinesNetwork`, methods for
  `plot` and `summary` and functions `calc_network_routes` and
  `find_network_nodes` allowing fast route calculations via igraph and
  other network analysis functions.

- Functions for removing beginning and end of lines: `toptail` and
  `toptailgs`. Helper functions `buff_geo`, `crs_select_aeq` and
  `line2points` added.

- Functionality for reading in the UK’s stats19 data: `read_stats19_*`
  functions download, unzip and re-categorise the data.

- `read_table` functions added for reading Australian OD data.

- `decode_gl` added to decode Google polylines and other functions for
  querying and reading data from OSRM services.

- `gtfs2sldf` added to import GTFS routes as SpatialLinesDataFrames.

### stplanr 0.0.2

- Published on CRAN
