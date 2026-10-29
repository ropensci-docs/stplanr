# stplanr: A Package for Transport Planning

Abstract

Tools for transport planning should be flexible, scalable and
transparent. The **stplanr** package demonstrates and provides a home
for such tools, with an emphasis on spatial transport data and
non-motorized modes. **stplanr** facilitates common transport planning
tasks including: downloading and cleaning transport datasets; creating
geographic ‘desire lines from origin-destination (OD) data; route
assignment, via the `SpatialLinesNetwork` class and interfaces to
routing services such as CycleStreets.net; calculation of route segment
attributes such as bearing and aggregate flow; and \`travel watershed’
analysis. This paper demonstrates this functionality using reproducible
examples on real transport datasets. More broadly, the experience shows
open source software can form the basis of a reproducible transport
planning workflow. **stplanr**, alongside other packages and open source
projects, could provide a more transparent and democratically
accountable alternative to the current approach which is heavily reliant
on proprietary and technically and financially inaccessible software.

### Note

This paper has now been peer reviewed and published by the R Journal.
Please see the published version at
[journal.r-project.org](https://journal.r-project.org/archive/2018/RJ-2018-053/index.html)
and cite it as Lovelace and Ellison (2018).

The code presented in this paper requires stplanr 0.8.5 or earlier,
which can be installed as follows:

``` r

remotes::install_github("ropensci/stplanr", ref = "v0.8.5")
```

## Introduction

Transport planning can broadly be defined as the process of designing
and evaluating transport interventions (de Dios Ortuzar and Willumsen
2011) usually with the ultimate aim of improving transport systems from
economic, social and environmental perspectives. This inevitably
involves a degree of subjective judgment and intuition. With the
proliferation of new transport datasets — and the increasing
availability of hardware and software to make sense of them — there is
great potential for the discipline to become more evidence-based and
scientific (Balmer et al. 2009). Transport planners have always
undertaken a wide range computational activities (Boyce and Williams
2015), but with the digital revolution the demands have grown beyond the
capabilities of a single, monolithic product. The diversity of tasks ,
and need for democratic accountability in public decision making,
suggests that future-proof transport planning software should be:

- flexible, able to handle a wide range of data formats

- scalable, able to work at multiple geographic levels from single
  streets to large cities and regions

- robust and reliable, tested on a range of datasets and able to work
  ’out of the box’ in a range of real-world projects

- open source and reproducible, ensuring transparency and encouraging
  citizen science

This paper sets out to demonstrate that open source software with a
command-line interface (CLI) can provide a foundation for transport
planning software that meets each of these criteria. R provides a strong
basis for progress in this direction because it already contains
functionality used in common transport planning workflows. , and greatly
improved R’s spatial abilities (Bivand et al. 2013), work that is being
consolidated and extended in the recent package.

Building on these foundations a number of spatial packages have been
developed for applied domains including: disease mapping and modelling,
with packages such as and (Kim and Wakefield 2016; Brown and Zhou 2016);
spatial ecology, with the **adehabitat** family of packages (Calenge
2006); and visualisation, with packages such as **SpatialEpi**,
**diseasemapping** and Brown (2016). However, there has been little
prior work to develop R functionality designed specifically for
transport planning, with the notable exceptions of
[TravelR](https://r-forge.r-project.org/projects/travelr/) (a package on
R-Forge last updated in 2012) and
[tidytransit](https://github.com/r-transit/tidytransit) (a package for
handling General Transit Feed Specification (GTFS) data).

The purpose of **stplanr** is to provide a toolbox rather than a
specific solution for transport planning, with an emphasis on spatial
data and active modes. This emphasis is timely given the recent emphasis
on sustainability (Banister 2008) and ‘Big Data’ (Zheng et al. 2016) in
the wider field of transport planning. A major motivation was the lack
of R packages, and open source software in general, for transport
applications. This may be surprising given the ubiquity of transport
problems;[^1] R’s proficiency at handling spatial, temporal and travel
survey data that describe transport systems; and the growing popularity
of R in applied domains (Jalal et al. 2017; Moore and Hutchinson 2017).
Another motivation is the growth in open access datasets: the main
purpose of early versions of the package was to process open
origin-destination data (Lovelace et al. 2017).

R is already used in transport applications, as illustrated by recent
research that applies packages from other domains to transport problems.
For instance, Efthymiou and Antoniou (2012) use R to analyse the data
collected from an online survey focused on car-sharing, bicycle-sharing
and electric vehicles. Efthymiou and Antoniou (2012) also used R to
collect and analyse transport-related data from Twitter using packages
including , and . These packages were used to download, parse and plot
the Twitter data using a method that can be repeated and the results
reproduced or updated. More general statistical analyses have also been
conducted on transport-related datasets using packages including and
(Diana 2012; Cerin et al. 2013). Despite the rising use of R for
transport research, there has yet been to be a package for transport
planning.

The design of the R language, with its emphasis on flexibility, data
processing and statistical modelling, suggests it can provide a powerful
environment for transport planning research. There are many quantitative
methods in transport planning, many of which fit into the classic ‘four
stage’ transport model which involves the following steps (de Dios
Ortuzar and Willumsen 2011): (1) trip *generation* to estimate trip
freqency from origins; (2) *distribution* of trips to destinations; (3)
*modal split* of trips between walking, cycling, buses etc.; (4)
*assignment* of trips to the transport route network. To this we would
like to add two more stages for the big data age: (0) data processing
and exploration; and (5) validation. This sequence is not the only way
of transport modelling and some have argued that its dominance has
reduced innovation. However it is certainly a common approach and
provides a useful schema for classifying the kinds of task that
**stplanr** can tackle:

- Accessing and processing of data on transport infrastructure and
  behaviour (stage 0)

- Analysis and visualisation of the transport network (0)

- Analysis of origin-destination (OD) data and the visualisation of
  resulting ‘desire lines’

- The allocation of desire lines to roads and other guideways via
  routing services

- The aggregation of routes to estimate total levels of flow on segments
  throughout the transport network

- Development of models to estimate transport behaviour currently and
  under various scenarios of change

- The calculation of ‘catchment areas’ affected by transport
  infrastructure

The automation of such tasks can assist researchers and practitioners to
create evidence for decision making. If the data processing and analysis
stages are fast and painless, more time can be dedicated to
visualisation and decision making. This should allow researchers to
focus on problems, rather than on clunky graphical user interfaces
(GUIs), and ad-hoc scripts that could be generalised. Furthermore, if
the process can be made reproducible and accessible (e.g. via online
visualisation packages such as **shiny**), this could help transport
planning move away from reliance on ‘black boxes’ (Waddell 2002) and
empower citizens to challenge decisions made by transport planning
authorities based on the evidence (Hollander 2016). There are many
advantages of using a scriptable, interactive and open source language
such as R for transport planning. Such an approach enables: reproducible
research; the automation and sharing of code between researchers;
reduced barriers to innovation as anyone can create new features for the
benefit of all planners; easier interaction with non domain experts (who
will lack dedicated software); and integration with other software
systems, as illustrated by the use of to generate JavaScript for sharing
interactive maps for transport planning, as used in the publicly
accessible Propensity to Cycle Tool (Lovelace et al. 2017). Furthermore,
R has a strong user community which can support newcomers (*stplanr* was
peer reviewed thanks to the community surrounding ROpenSci). The
advantages of using R specifically to develop the functionality
described in this paper are that it has excellent geo-statistical
capabilities (Pebesma et al. 2015), visualisation packages
(e.g. **tmap**, **ggplot2**), support for logit models (which are useful
for modelling modal shift), and support for the many formats that
transport datasets are stored in (e.g. via the **haven** and **rio**
packages).

## Package structure and functionality

The package can be installed and loaded in the usual way (see the
package’s [README](https://github.com/ropensci/stplanr) for dependencies
and access to development versions):

``` r

install.packages("stplanr")
```

``` r

library(stplanr)
```

As illustrated by the message emitted when **stplanr** is loaded, it
depends on . This means that the spatial data classes commonly used in
the package will work with generic R functions such as `summary`,
`aggregate` and, as illustrated in the figures below, `plot` .

### Core functions and classes

The package’s core functions are structured around 3 common types of
spatial transport data:

- Origin-destination (OD) data, which report the number of people
  travelling between origin-destination pairs. This type of data is not
  explicitly spatial (OD datasets are usually represented as data
  frames) but represents movement over space between points in
  geographical space. An example is provided in the `flow` dataset.
- Line data, one dimensional linear features on the surface of the
  Earth. These are typically stored as a `SpatialLinesDataFrame`.
- Route data are special types of lines which have been allocated to the
  transport network. Routes typically result from the allocation of a
  straight ‘desire line’ allocated to the route network with a `route_`
  function. Route network represent many overlapping routes. All are
  typically stored as `SpatialLinesDataFrame`.

For ease of use, functions focussed on each data type have been
developed with names prefixed with `od_`, `line_` and `route_`
respectively. A selection of these is presented in Table 1. Additional
‘core functions’ could be developed, such as those prefixed with `rn_`
(for working with route network data) and `g_` functions for geographic
operations such as buffer creation on lat/lon projected data (this
function is currently named `buff_geo`). We plan to elicit feedback on
such changes before implementing them.

With a tip of the hat to the concept of type stability (e.g. as
implemented in ), we also plan to make the core functions of **stplanr**
more type-stable in future releases. Core functions, which begin with
the prefixes listed above, could follow ’s lead and return only objects
with the same class as that of the input. However there are limitations
to this approach: it will break existing functionality and mean that
output objects have a larger size than necessary (`line_bearing`, for
example, does not need to duplicate the spatial data contained in its
input). Instead, we plan to continue to name functions around the type
of *input* data they take, but are open minded about function
input-output data class conventions, especially in the context of the
new class system implemented in .

A class system has not been developed for each data type (this option is
discussed in the final section). The most common data types used in
**stplanr** are assumed to be data frames and spatial datasets.

Transport datasets are very diverse. There are therefore many other
functions which have more ad-hock names. Rather attempt a systematic
description of each of **stplanr**’s functions (which can be gleaned
from the online manual) it is more illuminating to see how they work
together, as part of a transport planning workflow. As with most
workflows, this begins with data access and ends with visualisation.

### Accessing and processing transport data

Gaining access to data is often the first stage in transport research.
This is often a long and protracted process which is thankfully becoming
easier thanks to the ‘open data’ movement and packages such as
**tigris** for making data access from within R easier .

**stplanr** provides a variety of different functions that facilitate
importing common data formats used for transport analysis into R.
Although transport analysis generally requires some transport-specific
datasets, it also typically relies heavily on common sources of data
including census data. This being the case, **stplanr** also includes
functions that may be useful to those not involved in transport
research. This includes the `read_table_builder` function for importing
data from the Australian Bureau of Statistics (ABS) and the UK’s Stats19
road traffic casualty dataset. A brief example of the latter is
demonstrated below, which begins with downloading the data (warning this
downloads ~100 MB of data):

``` r

dl_stats19() # download and extract stats19 road traffic casualty data
```

    #> [1] "Data saved at: /tmp/RtmpppF3E2/Accidents0514.csv"
    #> [2] "Data saved at: /tmp/RtmpppF3E2/Casualties0514.csv"
    #> [3] "Data saved at: /tmp/RtmpppF3E2/Vehicles0514.csv"  

Once the data has been saved in the default directory, determined by
[`tempdir()`](https://rdrr.io/r/base/tempfile.html), it can be read-in
and cleaned with the `read_stats19_` functions (note these call
`format_stats19_` functions internally to clean the datasets and add
correct labels to the variables):

``` r

ac <- read_stats19_ac()
ca <- read_stats19_ca()
ve <- read_stats19_ve()
```

The resulting datasets (representing accident, casualty and vehicle
level data, respectively) can be merged and made geographic, as
illustrated below:

``` r

library(dplyr)
ca_ac <- inner_join(ca, ac)
ca_cycle <- ca_ac %>%
  filter(Casualty_Severity == "Fatal" & !is.na(Latitude)) %>%
  select(Age = Age_of_Casualty, Mode = Casualty_Type, Longitude, Latitude)
ca_sp <- SpatialPointsDataFrame(coords = ca_cycle[3:4], data = ca_cycle[1:2])
```

Now that this casualty data has been cleaned, subsetted (to only include
serious cycle crashes) and converted into a spatial class system, we can
analyse them using geographical datasets of the type commonly used by
**stplanr**. The following code, for example, geographically subsets the
dataset to include only crashes that occured within the bounding box of
a route network dataset provided by **stplanr** (from version 0.1.7 and
beyond) using the function `bb2poly`, which converts a spatial dataset
into a box, represented as a rectangular `SpatialPolygonsDataFrame`:

``` r

data("route_network") # devtools::install_github("ropensci/splanr")version 0.1.7
proj4string(ca_sp) <- proj4string(route_network)
bb <- bb2poly(route_network)
proj4string(bb) <- proj4string(route_network)
ca_local <- ca_sp[bb, ]
```

The above code chunk shows the importance of understanding geographical
data when working with transport data. It is only by converting the
casualty data into a spatial data class, and adding a coordinate
reference system (CRS), that transport planners and researchers can link
this important dataset back to the route network. We can now perform GIS
operations on the results. The next code chunk, for example, finds all
the fatalities that took place within 100 m of the route network, using
the function `buff_geo`:

``` r

rnet_buff_100 <- geo_buffer(route_network, width = 100)
ca_buff <- ca_local[rnet_buff_100, ]
```

These can be visualised using base R graphics, extended by , as
illustrated in Figure . This provides a good start for analysis but for
publication-quality plots and interactive plots, designed for public
engagement, we recommend using dedicated visualisation packages that
work with spatial data such as .

``` r

plot(bb, lty = 4)
plot(rnet_buff_100, col = "grey", add = TRUE)
points(ca_local, pch = 4)
points(ca_buff, cex = 3)
```

### Creating geographic desire lines

Perhaps the most common type of aggregate-level transport information is
origin-destination (‘OD’) data. This can be presented either as a matrix
or (more commonly) a long table of OD pairs. An example of this type of
raw data is provided below (see
[`?flow`](https://docs.ropensci.org/stplanr/reference/flow.md) to see
how this dataset was created).

``` r

data("flow", package = "stplanr")
head(flow[c(1:3, 12)])
```

Although the flow data displayed above describes movement over
geographical space, it contains no explicitly geographical information.
Instead, the coordinates of the origins and destinations are linked to a
separate geographical dataset which also must be loaded to analyse the
flows. This is a common problem solved by the function `od2line`. The
geographical data is a set of points representing centroids of the
origin and destinations, saved as a `SpatialPointsDataFrame`.
Geographical data in R is best represented as such `Spatial*` objects,
which use the `S4` object engine. This explains the close integration of
**stplanr** with R’s spatial packages, especially **sp**, which defines
the `S4` spatial object system.

``` r

data("cents", package = "stplanr")
as.data.frame(cents[1:3, -c(3, 4)])
```

We use `od2line` to combine `flow` and `cents`, to join the former to
the latter. We will visualise the `l` object created below in the next
section.

``` r

l <- od2line(flow = flow, zones = cents)
```

The data is now in a form that is much easier to analyse. We can plot
the data with the command `plot(l)`, which was not possible before.
Because the `SpatialLinesDataFrame` object also contains data per line,
it also helps with visualisation of the flows, as illustrated in Figure
.

### Allocating flows to the transport network

A common problem faced by transport researchers is network allocation:
converting the ‘as the crow flies’ lines illustrated in the figure above
into routes. These are the complex, winding paths that people and
animals make to avoid obstacles such as buildings and to make the
journey faster and more efficient (e.g. by following the route network).

This is difficult (and was until recently near impossible using free
software) because of the size and complexity of transport networks, the
complexity of realistic routing algorithms and need for
context-specificity in the routing engine. Inexperienced cyclists, for
example, would take a very different route than a heavy goods vehicle.
**stplanr** tackles this issue by using 3rd party APIs to provide
route-allocation.

Route allocation is undertaken by functions such as and . These allocate
a single OD pair, represented as a text string to be ‘geo-coded’, a pair
of of coordinates, or two `SpatialPoints` objects, representing origins
and destinations. This is illustrated below with `route_cyclestreet`,
which uses the [CycleStreets.net
API](https://www.cyclestreets.net/api/), a routing service “by cyclists
for cyclists” that offers a range route strategies (primarily ‘fastest’,
‘quietest’ and ‘balanced’) that are based on a detailed analysis of
cyclist wayfinding:[^2]

``` r

route_bl <- route_cyclestreets(from = "Bradford", to = "Leeds")
route_c1_c2 <- route_cyclestreets(cents[1, ], cents[2, ])
```

The raw output from routing APIs is usually provided as a JSON or
GeoJSON text string. By default, `route_cyclestreet` saves a number of
key variables (including length, time, hilliness and busyness variables
generated by CycleStreets.net) from the attribute data provided by the
API. If the user wants to save the raw output, the `save_raw` argument
can be used:

``` r

route_bl_raw <- route_cyclestreets(from = "Bradford", to = "Leeds", save_raw = TRUE)
```

Additional arguments taken by the `route_` functions depend on the
routing function in question. By changing the `plan` argument of
`route_cyclestreet` to `fastest`, `quietest` or `balanced`, for example,
routes favouring speed, quietness or a balance between speed and
quietness will be saved, respectively.

To automate the creation of route-allocated lines over many desire
lines, the `line2route` function loops over each line, wrapping any
`route_` function as an input. The output is a `SpatialLinesDataFrame`
with the same number of dimensions as the input dataset (see the right
panel in Figure ).

    routes_fast <- line2route(l = l, route_fun = route_cyclestreet)

The result of this ‘batch routing’ exercise is illustrated in Figure .
The red lines in the left hand panel are very different from the
hypothetical straight ‘desire lines’ often used in transport research,
highlighting the importance of this route-allocation functionality.

``` r

plot(route_network, lwd = 0)
plot(l, lwd = l$All / 10, add = TRUE)
lines(routes_fast, col = "red")
routes_fast$All <- l$All
rnet <- overline(routes_fast, "All", fun = sum)
rnet$flow <- rnet$All / mean(rnet$All) * 3
plot(rnet, lwd = rnet$flow / mean(rnet$flow))
```

To estimate the amount of capacity needed at each segment on the
transport network, the `overline` function demonstrated above, is used
to divide line geometries into unique segments and aggregate the
overlapping values. The results, illustrated in the right-hand panel of
Figure , can be used to estimate where there is most need to improve the
transport network, for example informing the decision of where to build
new bicycle paths.

Limitations with the `route_cyclestreet` routing API include its
specificity, to one mode (cycling) and a single region (the UK and part
of Europe). To overcome these limitations, additional routing APIs were
added with the functions `route_graphhopper`,
`route_transportapi_public` and `viaroute`. These interface to
Graphhopper, TransportAPI and the Open Source Routing Machine (OSRM)
routing services, respectively. The great advantage of OSRM is that it
allows you to run your own routing services on a local server, greatly
increasing the rate of route generation.

A short example of finding the route by car and bike between New York
and Oaxaca demonstrates how `route_graphhopper` can collect geographical
and other data on routes by various modes, anywhere in the world. The
output, shown in Table , shows that the function also saves time,
distance and (for bike trips) vertical distance climbed for the trips.

``` r

ny2oaxaca1 <- route_graphhopper("New York", "Oaxaca", vehicle = "bike")
ny2oaxaca2 <- route_graphhopper("New York", "Oaxaca", vehicle = "car")
rbind(ny2oaxaca1@data, ny2oaxaca2@data)
```

|     time |    dist | change_elev |
|---------:|--------:|------------:|
| 17522.73 | 4885663 |    87388.13 |
|  2759.89 | 4754772 |          NA |

### Modelling travel catchment areas

Accessibility to transport services is a particularly important topic
when considering public transport or active travel because of the
frequent steep reduction in use as distances to access services (or
infrastructure) increase. As a result, the planning for transport
services and infrastructure frequently focuses on several measures of
accessibility including distance, but also travel times and frequencies
and weighted by population. The functions in **stplanr** are intended to
provide a method of estimating these accessibility measures as well as
calculating the population that can access specific services (i.e.,
estimating the catchment area).

Catchment areas in particular are a widely used measure of accessibility
that attempts to both quantify the likely target group for a particular
service, and visualise the geographic area that is covered by the
service. For instance, passengers are often said to be willing to walk
up to 400 metres to a bus stop, or 800 metres to a railway station .
Although these distances may appear relatively arbitrary and have been
found to underestimate the true catchment area of bus stops and railway
stations they nonetheless represent a good, albeit somewhat
conservative, starting point from which catchment areas can be
determined.

In many cases, catchment areas are calculated on the basis of
straight-line (or “as the crow flies”) distances. This is a simplistic,
but relatively appealing approach because it requires little additional
data and is straight-forward to understand. **stplanr** provides
functionality that calculates catchment areas using straight-line
distances with the `calc_catchment` function. This function takes a
`SpatialPolygonsDataFrame` that contains the population (or other) data,
typically from a census, and a `Spatial*` layer that contains the
geometry of the transport facility. These two layers are overlayed to
calculate statistics for the desired catchments including proportioning
polygons to account for the proportion located within the catchment
area.

To illustrate how catchment areas can be calculated, **stplanr**
contains some sample datasets stored in ESRI Shapefile format (a
commonly used format for distributing GIS layers) that can together be
used to calculate sample catchment areas. One of these datasets
(`smallsa1`) contains population data for Statistical Area 1 (SA1) zones
in Sydney, Australia. The second contains hypothetical cycleways aligned
to streets in Sydney. The code below unzips the datasets and reads in
the shapefiles.

``` r

data_dir <- system.file("extdata", package = "stplanr")
unzip(file.path(data_dir, "smallsa1.zip"))
unzip(file.path(data_dir, "testcycleway.zip"))
sa1income <- as(sf::read_sf("smallsa1.shp"), "Spatial")
testcycleway <- as(sf::read_sf("testcycleway.shp"), "Spatial")
# Remove unzipped files
file.remove(list.files(pattern = "^(smallsa1|testcycleway).*"))
```

Calculating the catchment area is straightforward and in addition to
specifying the required datasets, only a vector containing column names
to calculate statistics and a distance is required. Since proportioning
the areas assumes projected data, unprojected data are automatically
projected to either a common projection (if one is already projected) or
a specified projection. It should be emphasised that the choice of
projection is important and has an effect on the results meaning setting
a local projection is recommended to achieve the most accurate results.

``` r

remotes::install_github("ropensci/stplanr")
catch800m <- calc_catchment(
  polygonlayer = sa1income,
  targetlayer = testcycleway,
  calccols = c("Total"),
  distance = 800,
  projection = "austalbers",
  dissolve = TRUE
)
```

By looking at the data.frame associated with the
SpatialPolygonsDataFrame that is returned from the `calc_catchment`
function, the total population within the catchment area can be seen to
be nearly 40,000 people. The catchment area can also be plotted as with
any other `Spatial*` object using the `plot` function using the code
below with the result shown in Figure .

``` r

plot(sa1income, col = "light grey")
plot(catch800m, col = rgb(1, 0, 0, 0.5), add = TRUE)
plot(testcycleway, col = "green", add = TRUE)
```

This simplistic catchment area is useful when the straight-line distance
is a reasonable approximation of the route taken to walk (or cycle) to a
transport facility. However, this is often not the case. The catchment
area in Figure initially appears reasonable but the red-shaded catchment
area includes an area that requires travelling around a bay to access
from the (green-coloured) cycleway. To allow for more realistic
catchment areas for most situations, **stplanr** provides the
`calc_network_catchment` function that uses the same principle as
`calc_catchment` but also takes into account the transport network.

To use `calc_network_catchment`, a transport network needs to be
prepared that can be used in conjunction with the previous datasets.
Preparation of the dataset involves using the `SpatialLinesNetwork`
function to create a network from a `SpatialLinesDataFrame`. This
function combines a `SpatialLinesDataFrame` with a graph network (using
the package) to provide basic routing functionality. The network is used
to calculate the shortest actual paths within the specific catchment
distance. This process involves the following code:

``` r

unzip(file.path(data_dir, "sydroads.zip"))
sydroads <- as(sf::read_sf(".", "roads"), "Spatial")
file.remove(list.files(pattern = "^(roads).*"))
sydnetwork <- SpatialLinesNetwork(sydroads)
```

The network catchment is then calculated using a similar method as with
`calc_catchment` but with a few minor changes. Specifically these are
including the `SpatialLinesNetwork`, and using the `maximpedance`
parameter to define the distance, with distance being the additional
distance from the network. In contrast to the distance parameter that is
based on the straight-line distance in both the `calc_catchment` and
`calc_network_catchment` functions, the `maximpedance` parameter is the
maximum value in the units of the network’s weight attribute. In
practice this is generally distance in metres but can also be travel
times, risk or other measures.

``` r

netcatch800m <- calc_network_catchment(
  sln = sydnetwork,
  polygonlayer = sa1income,
  targetlayer = testcycleway,
  calccols = c("Total"),
  maximpedance = 800,
  distance = 100,
  projection = "austalbers"
)
```

Once calculated, the network catchment area can be used just as the
straight-line network catchment. This includes extracting the catchment
population of 128,000 and plotting the original catchment area together
with the original area with the results shown in Figure :

``` r

plot(sa1income, col = "light grey")
plot(catch800m, col = rgb(1, 0, 0, 0.5), add = TRUE)
plot(netcatch800m, col = rgb(0, 0, 1, 0.5), add = TRUE)
plot(testcycleway, col = "green", add = TRUE)
```

## Modelling and visualisation

### Modelling mode choice

Route-allocated lines allow estimation of *route distance* and
*cirquity* (route distance divided by Euclidean distance). These
variables can help model the rate of flow between origins and
destination, as illustrated in the left-hand panel of Figure . The code
below demonstrates how objects generated by **stplanr** can be used to
undertake such analysis, with the `line_length` function used to find
the distance, in meters, of lat/lon data.

    l$d_euclidean <- line_length(l)
    l$d_rf <- routes_fast@data$length
    plot(l$d_euclidean, l$d_rf,
      xlab = "Euclidean distance", ylab = "Route distance")
    abline(a = 0, b = 1)
    abline(a = 0, b = 1.2, col = "green")
    abline(a = 0, b = 1.5, col = "red")

The left hand panel of Figure shows the expected strong correlation
between Euclidean ($`d_E`$) and fastest route ($`d_{Rf}`$) distance.
However, some OD pairs have a proportionally higher route distance than
others, as illustrated by distance from the black line in the above
plot: this represents : the ratio of network distance to Euclidean
distance :

``` math
 Q = \frac{d_{Rf}}{d_E}
```

An extension to the concept of cirquity is the ‘quietness diversion
factor’ ($`QDF`$) of a desire line , the ratio of the route distance of
a quiet route option ($`d_{Rq}`$) to that of the fastest:

``` math
 QDF = \frac{d_{Rq}}{d_{Rf}}
```

Thanks to the ‘quietest’ route option provided by `route_cyclestreet`,
we can estimate average values for both metrics as follows:

``` r

routes_slow <- line2route(l, route_cyclestreet, plan = "quietest")
```

``` r

l$d_rq <- routes_slow$length # quietest route distance
Q <- mean(l$d_rf / l$d_euclidean, na.rm = TRUE)
QDF <- mean(l$d_rq / l$d_rf, na.rm = TRUE)
Q
QDF
```

The results show that cycle paths are not particularly direct in the
study region by international standards . This is hardly surprisingly
given the small size of the sample and the short distances covered:
$`Q`$ tends to decrease at a decaying rate with distance. What is
surprising is that $`QDF`$ is close to unity, which could imply that the
quiet routes are constructed along direct, and therefore sensible
routes. We should caution against such assumptions, however: It is a
small sample of desire lines and, when time is explored, we find that
the ‘quietness diversion factor with respect to time’ ($`QDF_t`$) is
slightly larger:

``` r

(QDFt <- mean(routes_slow$time / routes_fast$time, na.rm = TRUE))
```

### Models of travel behaviour

There are many ways of estimating flows between origins and
destinations, including spatial interaction models, the four-stage
transport model and gravity models (‘distance decay’). **stplanr** aims
eventually to facilitate creation of many types of flow model.

At present there are no functions for modelling distance decay, but this
is something we would like to add in future versions of **stplanr**.
Distance decay is an especially important concept for sustainable
transport planning due to physical limitations on the ability of people
to walk and cycle large distances .

We can explore the relationship between distance and the proportion of
trips made by walking, using the same object `l` generated by
**stplanr**.

``` r

l$pwalk <- l$On.foot / l$All
plot(l$d_euclidean, l$pwalk,
  cex = l$All / 50,
  xlab = "Euclidean distance (m)", ylab = "Proportion of trips by foot"
)
```

Based on the right-hand panel in Figure , there is a clear negative
relationship between distance of trips and the proportion of those trips
made by walking. This is unsurprising: beyond a certain distance (around
1.5km according the the data presented in the figure above) walking is
usually seen as too slow and other modes are considered. According to
the academic literature, this ‘distance decay’ is non-linear and there
have been a number of functions proposed to fit to distance decay curves
. From the range of options we test below just two forms. We will
compare the ability of linear and log-square-root functions to fit the
data contained in `l` for walking.

``` r

lm1 <- lm(pwalk ~ d_euclidean, data = l@data, weights = All)
lm2 <- lm(pwalk ~ d_rf, data = l@data, weights = All)
lm3 <- glm(pwalk ~ d_rf + I(d_rf^0.5),
  data = l@data, weights = All, family = quasipoisson(link = "log")
)
```

The results of these regression models can be seen using
[`summary()`](https://rdrr.io/r/base/summary.html). Surprisingly,
Euclidean distance was a better predictor of walking than route
distance, but no strong conclusions can be drawn from this finding, with
such a small sample of desire lines (n = 42). The results are purely
illustrative, of the kind of the possibilities created by using
**stplanr** in conjuction with R’s modelling capabilities (see Figure ).

``` r

plot(l$d_euclidean, l$pwalk,
  cex = l$All / 50,
  xlab = "Euclidean distance (m)", ylab = "Proportion of trips by foot"
)
l2 <- data.frame(d_euclidean = 1:5000, d_rf = 1:5000)
lm1p <- predict(lm1, l2)
lm2p <- predict(lm2, l2)
lm3p <- predict(lm3, l2)
lines(l2$d_euclidean, lm1p)
lines(l2$d_euclidean, exp(lm2p), col = "green")
lines(l2$d_euclidean, exp(lm3p), col = "red")
```

### Visualisation

Visualisation is an important aspect of any transport study, as it
enables researchers to communicate their findings to other researchers,
policy-makers and, ultimately, the public. It may therefore come as a
surprise that **stplanr** contains no functions for visualisation.
Instead, users are encouraged to make use of existing spatial
visualisation tools in R, such as **tmap**, **leaflet** and **ggmap** .

Furthermore, with the development of online application frameworks such
as **shiny**, it is now easier than ever to make the results of
transport analysis and modelling projects available to the public. An
example is the online interface of the Propensity to Cycle Tool (PCT).
The results of the project, generated using **stplanr**, are presented
at zone, desire line and Route Network levels . There is great potential
to expand on the principle of publicly accessible transport planning
tools via ‘web apps’, perhaps through new R packages dedicated to
visualising transport data.

## Future directions of travel

This paper has demonstrated the great potential for R to be used for
transport planning. R’s flexibility, powerful GIS capabilities and free
accessibility makes it well-suited to the needs of transport planners
and researchers, especially those wanting to avoid the high costs of
market-leading products. Rather than ‘reinvent the wheel’ (e.g. with a
new class system), **stplanr** builds on existing packages and classes
to work with common transport data formats.

It is useful to see **stplanr**, and R for transport planning in
general, as an addition tool in the transport planner’s cabinet. It can
be understood as one part of a wider movement that is making transport
planning a more open and democratic process. Other developments in this
movement include the increasing availability of open data and the rise
of open source products for transport modelling, such as SUMO,
[MATSim](https://www.matsim.org/) and MITSIMLAB . **stplanr**, with its
focus on GIS operations rather than microscopic vehicle-level behaviour,
can complement such software and help make better use of new open data
sources.

Because transport planning is an inherently spatial activity,
**stplanr** occupies an important niche in the transport planning
software landscape, with its focus on spatial transport data. There is
great potential for development of **stplanr** in many directions.
Desirable developments include the additional of functions for modelling
modal split, for examample with functions to create commonly distance
decay curves which are commonly found in active travel research and
improving the computational efficiency of existing functions to make the
methods more scalable for large databases. Our priority for **stplanr**
however, is to keep the focus on geographic functions for transport
planning. There are many opportunities in this direction, including:

- Functions to assess the environment surrounding routes, e.g. via
  integration with the in-development **osmdata** package.
- Functions to match different GIS routes, perhaps building on the
  Hausdorf distance algorithm implemented in the function `gDistance`.
- Additional functions for route-allocation of travel, e.g. via an
  interface to the OpenTripPlanner API.
- Functions for aggregating very large GPS trace datasets (e.g. into
  raster cells) for anonymisation and analysis/visualisation purposes.
- The creation of a class system for spatial transport datasets, such as
  to represent spatial route and a route networks (perhaps with classes
  named and ). This is not a short-term priority and it would be
  beneficial to coincide such developments to a migration to for spatial
  classes.

Such spatial data processing capabilities would increase the range of
transport planning tasks that **stplanr** can facilitate. For all this
planned development activity to be useful, it is vital that new
functionality is intuitive. R has a famously steep learning curve.
Implementing simple concepts such as consistent naming systems and
ensuring ‘type stability’ can greatly improve the usability of the
package. For this reason, much future work in **stplanr** will go into
improving documentation and user-friendliness.

Like much open source software **stplanr** is an open-ended project, a
work-in-progress. We have set out clear motivations for developing
transport planning capabilities in R and believe that the current
version of **stplanr** (0.1.6) provides a major step in that direction
compared with what was available a couple of years ago. But there is
much more to do. We therefore welcome input on where the package’s
priorities should lie, how it should evolve in the future and how to
ensure it is well-developed and sustained.

## References

Balmer, Michael, Marcel Rieser, and Kai Nagel. 2009. “MATSim-T:
Architecture and Simulation Times.” *Multi-Agent Systems for Traffic and
Transportation Engineering*, 57–78.
<https://svn.vsp.tu-berlin.de/repos/public-svn/publications/vspwp/2008/08-03/3aug08.pdf>.

Banister, David. 2008. “The Sustainable Mobility Paradigm.” *Transport
Policy* 15 (2): 73–80. <https://doi.org/10.1016/j.tranpol.2007.10.005>.

Bivand, Roger S, Edzer J Pebesma, and Virgilio G’omez-Rubio. 2013.
*Applied Spatial Data Analysis with R*. Vol. 747248717. Springer.

Boyce, David E., and Huw C. W. L. Williams. 2015. *Forecasting Urban
Travel: Past, Present and Future*. Edward Elgar Publishing.

Brown, Patrick E. 2016. “Maps, Coordinate Reference Systems and
Visualising Geographic Data with Mapmisc.” *The R Journal* 8 (1): 64–91.

Brown, Patrick E., and L. Zhou. 2016. *Diseasemapping: Modelling Spatial
Variation in Disease Risk for Areal Data*.
<https://CRAN.R-project.org/package=diseasemapping>.

Calenge, C. 2006. “The Package Adehabitat for the R Software: Tool for
the Analysis of Space and Habitat Use by Animals.” *Ecological
Modelling* 197: 1035.

Cerin, Ester, Cindy H P Sit, Anthony Barnett, Man Chin Cheung, and Wai
Man Chan. 2013. “Walking for Recreation and Perceptions of the
Neighborhood Environment in Older Chinese Urban Dwellers.” *Journal of
Urban Health* 90 (1): 56–66.
<https://doi.org/10.1007/s11524-012-9704-8>.

de Dios Ortuzar, Juan, and Luis G. Willumsen. 2011. *Modelling
Transport*. John Wiley & Sons.

Diana, Marco. 2012. “Studying Patterns of Use of Transport Modes Through
Data Mining.” *Transportation Research Record: Journal of the
Transportation Research Board* 2308 (December): 1–9.
<https://doi.org/10.3141/2308-01>.

Efthymiou, Dimitrios, and Constantinos Antoniou. 2012. “Use of Social
Media for Transport Data Collection.” *Procedia - Social and Behavioral
Sciences* 48 (August 2016): 775–85.
<https://doi.org/10.1016/j.sbspro.2012.06.1055>.

Hollander, Yaron. 2016. *Transport Modelling for a Complete Beginner*.
CTthink!

Jalal, Hawre, Petros Pechlivanoglou, Eline Krijkamp, Fernando
Alarid-Escudero, Eva Enns, and M. G. Myriam Hunink. 2017. “An Overview
of R in Health Decision Sciences.” *Medical Decision Making*, January 6,
0272989X16686559.

Kim, Albert Y., and Jon Wakefield. 2016. *SpatialEpi: Methods and Data
for Spatial Epidemiology*.
<https://CRAN.R-project.org/package=SpatialEpi>.

Lovelace, Robin, and Richard Ellison. 2018. “Stplanr: A Package for
Transport Planning.” *The R Journal* 10 (2): 7–23.
<https://doi.org/10.32614/RJ-2018-053>.

Lovelace, Robin, Anna Goodman, Rachel Aldred, Nikolai Berkoff, Ali
Abbas, and James Woodcock. 2017. “The Propensity to Cycle Tool: An Open
Source Online System for Sustainable Transport Planning.” *Journal of
Transport and Land Use* 10 (1). <https://doi.org/10.5198/jtlu.2016.862>.

Moore, R. D. (Dan), and David Hutchinson. 2017. “Why Watershed Analysts
Should Use R for Data Processing and Analysis.” *Confluence: Journal of
Watershed Science and Management* 1 (1).
<http://confluence-jwsm.ca/index.php/jwsm/article/view/2>.

Pebesma, Edzer, Roger Bivand, Paulo Justiniano Ribeiro, et al. 2015.
“Software for Spatial Statistics.” *Journal of Statistical Software* 63
(1): 1–8.

Waddell, Paul. 2002. “UrbanSim: Modeling Urban Development for Land Use,
Transportation, and Environmental Planning.” *Journal of the American
Planning Association* 68 (3): 297–314.

Zheng, Xinhu, Wei Chen, Pu Wang, et al. 2016. “Big Data for Social
Transportation.” *IEEE Transactions on Intelligent Transportation
Systems* 17 (3): 620–30.
<https://ieeexplore.ieee.org/abstract/document/7359138/>.

[^1]: Many people can think of things that could be improved on their
    local transport networks, especially for walking, cycling and
    wheel-chairs. But most lack the evidence to communicate the issues,
    and potential solutions, to others.

[^2]: An API key is needed for this function to work. This can be
    requested (or purchased for large scale routing) from
    [cyclestreets.net/api/apply](https://www.cyclestreets.net/api/apply/).
    See `?route_cyclestreet` for details. Thanks to Martin Lucas-Smith
    and Simon Nuttall for making this possible.
