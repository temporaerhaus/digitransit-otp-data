digitransit-otp-data
--------------------

This repo and Dockerfile replaces the [OpenTripPlanner-data-container building process](https://github.com/verschwoerhaus/OpenTripPlanner-data-container). 
Using the [mfdz opentripplanner](https://github.com/mfdz/opentripplanner) [docker image](https://hub.docker.com/r/mfdz/opentripplanner), all the neccessary building steps (aquiring gtfs, osm pbf and build/router config) happen as Dockerfile commands. This allows us to leverage dockers build caching as well as simpler building by calling `docker build .`. 
The Dockerfile contains a multi-stage build, so the big otp and buildfile dependencies are only used for building, the resulting container is a small `nginx:alpine` based one that only delivers the build result as `.zip`.