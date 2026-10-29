# Package index

## Work with OD data

- [`od2line()`](https://docs.ropensci.org/stplanr/reference/od2line.md)
  : Convert origin-destination data to spatial lines
- [`od2odf()`](https://docs.ropensci.org/stplanr/reference/od2odf.md) :
  Extract coordinates from OD data
- [`od_aggregate_from()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_from.md)
  : Summary statistics of trips originating from zones in OD data
- [`od_aggregate_to()`](https://docs.ropensci.org/stplanr/reference/od_aggregate_to.md)
  : Summary statistics of trips arriving at destination zones in OD data
- [`od_coords()`](https://docs.ropensci.org/stplanr/reference/od_coords.md)
  : Create matrices representing origin-destination coordinates
- [`od_coords2line()`](https://docs.ropensci.org/stplanr/reference/od_coords2line.md)
  : Convert origin-destination coordinates into desire lines
- [`od_id_szudzik()`](https://docs.ropensci.org/stplanr/reference/od_id.md)
  [`od_id_max_min()`](https://docs.ropensci.org/stplanr/reference/od_id.md)
  [`od_id_character()`](https://docs.ropensci.org/stplanr/reference/od_id.md)
  : Combine two ID values to create a single ID number
- [`od_id_order()`](https://docs.ropensci.org/stplanr/reference/od_id_order.md)
  : Generate ordered ids of OD pairs so lowest is always first This
  function is slow on large datasets, see szudzik_pairing for faster
  alternative
- [`od_oneway()`](https://docs.ropensci.org/stplanr/reference/od_oneway.md)
  : Aggregate od pairs they become non-directional
- [`od_to_odmatrix()`](https://docs.ropensci.org/stplanr/reference/od_to_odmatrix.md)
  : Convert origin-destination data from long to wide format
- [`odmatrix_to_od()`](https://docs.ropensci.org/stplanr/reference/odmatrix_to_od.md)
  : Convert origin-destination data from wide to long format
- [`points2flow()`](https://docs.ropensci.org/stplanr/reference/points2flow.md)
  : Convert a series of points into geographical flows
- [`points2odf()`](https://docs.ropensci.org/stplanr/reference/points2odf.md)
  : Convert a series of points into a dataframe of origins and
  destinations

## Work with (desire) lines

- [`angle_diff()`](https://docs.ropensci.org/stplanr/reference/angle_diff.md)
  : Calculate the angular difference between lines and a predefined
  bearing

- [`geo_toptail()`](https://docs.ropensci.org/stplanr/reference/geo_toptail.md)
  : Clip the first and last n metres of SpatialLines

- [`is_linepoint()`](https://docs.ropensci.org/stplanr/reference/is_linepoint.md)
  : Identify lines that are points

- [`line2df()`](https://docs.ropensci.org/stplanr/reference/line2df.md)
  : Convert geographic line objects to a data.frame with from and to
  coords

- [`line2points()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  [`line2pointsn()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  [`line2vertices()`](https://docs.ropensci.org/stplanr/reference/line2points.md)
  : Convert a spatial (linestring) object to points

- [`line_bearing()`](https://docs.ropensci.org/stplanr/reference/line_bearing.md)
  : Find the bearing of straight lines

- [`line_breakup()`](https://docs.ropensci.org/stplanr/reference/line_breakup.md)
  : Break up line objects into shorter segments

- [`line_midpoint()`](https://docs.ropensci.org/stplanr/reference/line_midpoint.md)
  : Find the mid-point of lines

- [`line_segment()`](https://docs.ropensci.org/stplanr/reference/line_segment.md)
  : Divide an sf object with LINESTRING geometry into regular segments

- [`line_segment1()`](https://docs.ropensci.org/stplanr/reference/line_segment1.md)
  : Segment a single line, using lwgeom or rsgeo

- [`line_via()`](https://docs.ropensci.org/stplanr/reference/line_via.md)
  : Add geometry columns representing a route via intermediary points

- [`mats2line()`](https://docs.ropensci.org/stplanr/reference/mats2line.md)
  : Convert 2 matrices to lines

- [`n_segments()`](https://docs.ropensci.org/stplanr/reference/n_segments.md)
  : Vectorised function to calculate number of segments given a max
  segment length

- [`n_vertices()`](https://docs.ropensci.org/stplanr/reference/n_vertices.md)
  : Retrieve the number of vertices in sf objects

- [`onewaygeo()`](https://docs.ropensci.org/stplanr/reference/onewaygeo.md)
  : Aggregate flows so they become non-directional (by geometry - the
  slow way)

- [`points2line()`](https://docs.ropensci.org/stplanr/reference/points2line.md)
  : Convert a series of points, or a matrix of coordinates, into a line

- [`toptail_buff()`](https://docs.ropensci.org/stplanr/reference/toptail_buff.md)
  :

  Clip the beginning and ends of `sf` LINESTRING objects

- [`line_cast()`](https://docs.ropensci.org/stplanr/reference/line_cast.md)
  : Convert multilinestring object into linestrings

## Work with and analyse routes

- [`route_average_gradient()`](https://docs.ropensci.org/stplanr/reference/route_average_gradient.md)
  : Return average gradient across a route
- [`route_rolling_average()`](https://docs.ropensci.org/stplanr/reference/route_rolling_average.md)
  : Return smoothed averages of vector
- [`route_rolling_diff()`](https://docs.ropensci.org/stplanr/reference/route_rolling_diff.md)
  : Return smoothed differences between vector values
- [`route_rolling_gradient()`](https://docs.ropensci.org/stplanr/reference/route_rolling_gradient.md)
  : Calculate rolling average gradient from elevation data at segment
  level
- [`route_sequential_dist()`](https://docs.ropensci.org/stplanr/reference/route_sequential_dist.md)
  : Calculate the sequential distances between sequential coordinate
  pairs
- [`route_slope_matrix()`](https://docs.ropensci.org/stplanr/reference/route_slope_matrix.md)
  : Calculate the gradient of line segments from a matrix of coordinates
- [`route_slope_vector()`](https://docs.ropensci.org/stplanr/reference/route_slope_vector.md)
  : Calculate the gradient of line segments from distance and elevation
  vectors
- [`route()`](https://docs.ropensci.org/stplanr/reference/route.md) :
  Plan routes on the transport network
- [`route_bikecitizens()`](https://docs.ropensci.org/stplanr/reference/route_bikecitizens.md)
  : Get a route from the BikeCitizens web service
- [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  : Route on local data using the dodgr package
- [`route_google()`](https://docs.ropensci.org/stplanr/reference/route_google.md)
  : Find shortest path using Google services
- [`route_nearest_point()`](https://docs.ropensci.org/stplanr/reference/route_nearest_point.md)
  : Find nearest route to a given point
- [`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md)
  : Spatial lines dataset representing a route network
- [`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md)
  : Spatial lines dataset representing a small route network
- [`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)
  : Plan routes on the transport network using the OSRM server
- [`route_split()`](https://docs.ropensci.org/stplanr/reference/route_split.md)
  : Split route in two at point on or near network
- [`route_split_id()`](https://docs.ropensci.org/stplanr/reference/route_split_id.md)
  : Split route based on the id or coordinates of one of its vertices
- [`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md)
  : Spatial lines dataset of commuter flows on the travel network
- [`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md)
  : Spatial lines dataset of commuter flows on the travel network

## Routing

- [`route()`](https://docs.ropensci.org/stplanr/reference/route.md) :
  Plan routes on the transport network
- [`route_dodgr()`](https://docs.ropensci.org/stplanr/reference/route_dodgr.md)
  : Route on local data using the dodgr package
- [`route_osrm()`](https://docs.ropensci.org/stplanr/reference/route_osrm.md)
  : Plan routes on the transport network using the OSRM server

## Work with nodes

- [`geo_code()`](https://docs.ropensci.org/stplanr/reference/geo_code.md)
  : Convert text strings into points on the map

## Route network functions

- [`rnet_add_node()`](https://docs.ropensci.org/stplanr/reference/rnet_add_node.md)
  : Add a node to route network
- [`rnet_boundary_points()`](https://docs.ropensci.org/stplanr/reference/rnet_boundary_points.md)
  [`rnet_boundary_df()`](https://docs.ropensci.org/stplanr/reference/rnet_boundary_points.md)
  [`rnet_boundary_unique()`](https://docs.ropensci.org/stplanr/reference/rnet_boundary_points.md)
  [`rnet_boundary_points_lwgeom()`](https://docs.ropensci.org/stplanr/reference/rnet_boundary_points.md)
  [`rnet_duplicated_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_boundary_points.md)
  : Get points at the beginner and end of linestrings
- [`rnet_breakup_vertices()`](https://docs.ropensci.org/stplanr/reference/rnet_breakup_vertices.md)
  : Break up an sf object with LINESTRING geometry.
- [`rnet_connected()`](https://docs.ropensci.org/stplanr/reference/rnet_connected.md)
  : Keep only segments connected to the largest group in a network
- [`rnet_cycleway_intersection`](https://docs.ropensci.org/stplanr/reference/rnet_cycleway_intersection.md)
  : Example of cycleway intersection data showing problems for
  SpatialLinesNetwork objects
- [`rnet_get_nodes()`](https://docs.ropensci.org/stplanr/reference/rnet_get_nodes.md)
  : Extract nodes from route network
- [`rnet_group()`](https://docs.ropensci.org/stplanr/reference/rnet_group.md)
  : Assign segments in a route network to groups
- [`rnet_join()`](https://docs.ropensci.org/stplanr/reference/rnet_join.md)
  : Join route networks
- [`rnet_merge()`](https://docs.ropensci.org/stplanr/reference/rnet_merge.md)
  : Merge route networks, keeping attributes with aggregating functions
- [`rnet_overpass`](https://docs.ropensci.org/stplanr/reference/rnet_overpass.md)
  : Example of overpass data showing problems for SpatialLinesNetwork
  objects
- [`rnet_roundabout`](https://docs.ropensci.org/stplanr/reference/rnet_roundabout.md)
  : Example of roundabout data showing problems for SpatialLinesNetwork
  objects
- [`rnet_subset()`](https://docs.ropensci.org/stplanr/reference/rnet_subset.md)
  : Subset one route network based on overlaps with another
- [`overline()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  [`overline2()`](https://docs.ropensci.org/stplanr/reference/overline.md)
  : Convert series of overlapping lines into a route network
- [`overline_intersection()`](https://docs.ropensci.org/stplanr/reference/overline_intersection.md)
  : Convert series of overlapping lines into a route network
- [`gsection()`](https://docs.ropensci.org/stplanr/reference/gsection.md)
  : Function to split overlapping SpatialLines into segments
- [`islines()`](https://docs.ropensci.org/stplanr/reference/islines.md)
  : Do the intersections between two geometries create lines?

## Geographic functions

- [`bbox_scale()`](https://docs.ropensci.org/stplanr/reference/bbox_scale.md)
  : Scale a bounding box

- [`bind_sf()`](https://docs.ropensci.org/stplanr/reference/bind_sf.md)
  : Rapid row-binding of sf objects

- [`geo_bb()`](https://docs.ropensci.org/stplanr/reference/geo_bb.md) :
  Flexible function to generate bounding boxes

- [`geo_bb_matrix()`](https://docs.ropensci.org/stplanr/reference/geo_bb_matrix.md)
  : Create matrix representing the spatial bounds of an object

- [`geo_buffer()`](https://docs.ropensci.org/stplanr/reference/geo_buffer.md)
  : Perform a buffer operation on a temporary projected CRS

- [`geo_length()`](https://docs.ropensci.org/stplanr/reference/geo_length.md)
  : Calculate line length of line with geographic or projected CRS

- [`geo_projected()`](https://docs.ropensci.org/stplanr/reference/geo_projected.md)
  : Perform GIS functions on a temporary, projected version of a spatial
  object

- [`geo_select_aeq()`](https://docs.ropensci.org/stplanr/reference/geo_select_aeq.md)
  : Select a custom projected CRS for the area of interest

- [`quadrant()`](https://docs.ropensci.org/stplanr/reference/quadrant.md)
  : Split a spatial object into quadrants

- [`stplanr-deprecated`](https://docs.ropensci.org/stplanr/reference/stplanr-deprecated.md)
  : Deprecated functions in stplanr

- [`stplanr-package`](https://docs.ropensci.org/stplanr/reference/stplanr-package.md)
  [`stplanr`](https://docs.ropensci.org/stplanr/reference/stplanr-package.md)
  :

  **stplanr: Sustainable Transport Planning with R**

## Get transport data

- [`cents_sf`](https://docs.ropensci.org/stplanr/reference/cents_sf.md)
  : Spatial points representing home locations
- [`destinations_sf`](https://docs.ropensci.org/stplanr/reference/destinations_sf.md)
  : Example destinations data
- [`flow`](https://docs.ropensci.org/stplanr/reference/flow.md) : Data
  frame of commuter flows
- [`flow_dests`](https://docs.ropensci.org/stplanr/reference/flow_dests.md)
  : Data frame of invented commuter flows with destinations in a
  different layer than the origins
- [`flowlines_sf`](https://docs.ropensci.org/stplanr/reference/flowlines_sf.md)
  : Spatial lines dataset of commuter flows
- [`od_data_lines`](https://docs.ropensci.org/stplanr/reference/od_data_lines.md)
  : Example of desire line representations of origin-destination data
  from UK Census
- [`od_data_routes`](https://docs.ropensci.org/stplanr/reference/od_data_routes.md)
  : Example segment-level route data
- [`od_data_sample`](https://docs.ropensci.org/stplanr/reference/od_data_sample.md)
  : Example of origin-destination data from UK Census
- [`osm_net_example`](https://docs.ropensci.org/stplanr/reference/osm_net_example.md)
  : Example of OpenStreetMap road network
- [`read_table_builder()`](https://docs.ropensci.org/stplanr/reference/read_table_builder.md)
  : Import and format Australian Bureau of Statistics (ABS) TableBuilder
  files
- [`route_network_sf`](https://docs.ropensci.org/stplanr/reference/route_network_sf.md)
  : Spatial lines dataset representing a route network
- [`route_network_small`](https://docs.ropensci.org/stplanr/reference/route_network_small.md)
  : Spatial lines dataset representing a small route network
- [`routes_fast_sf`](https://docs.ropensci.org/stplanr/reference/routes_fast_sf.md)
  : Spatial lines dataset of commuter flows on the travel network
- [`routes_slow_sf`](https://docs.ropensci.org/stplanr/reference/routes_slow_sf.md)
  : Spatial lines dataset of commuter flows on the travel network
- [`zones_sf`](https://docs.ropensci.org/stplanr/reference/zones_sf.md)
  : Spatial polygons of home locations for flow analysis.

## Example data
