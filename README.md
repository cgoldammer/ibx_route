# Geojsons for IBX

Last update: 2025-11-12

This is for now just a geojson for the upcoming IBX route.

This is unofficial, based on images of maps, and uses hand-coded locations, and the author assumes no warranty for usage.

There might be errors or information might be outdated, so please create issues as you find them!

# Data used

## Train lines from transpotation.gov

Data from:

https://data-usdot.opendata.arcgis.com/datasets/usdot::north-american-rail-network-lines/explore?location=40.705367%2C-73.887214%2C16.14

## IBX Stops:

Using image of map, e.g. https://www.etany.org/ibx-all-faiths-tunnel 
I hand-coded the stops by finding the relevant street intersections on Google Maps.

# Matching process

## Clean Line data:
- keeping `subdiv` ['BAY RIDGE BRANCH', 'FREMONT SECONDARY']
- removing branch 'MONTAUK BRANCH'
- removing objectids [70764, 70362, 68757] (there are many parallel lines at Fresh Pond junction and I took the one in the middle)

This leaves us with a continuous set of line segments.

## Splitting lines by stops

I loop through the stops to create from-to pairs, and for each pair I find the line segment covering these points (restricted to the from-to location)

# Validation

In the map from https://www.etany.org/ibx-all-faiths-tunnel we see the following 19 stops:

['Brooklyn Army Terminal',
 '4 Avenue',
 '8 Avenue',
 'New Utrecht Avenue',
 'McDonald Avenue',
 'East 16 Street',
 'Flatbush Avenue-Nostrand Avenue',
 'Utica Avenue',
 'Remsen Avenue',
 'Linden Boulevard',
 'Livonia Avenue',
 'Sutter Avenue',
 'Atlantic Avenue',
 'Wilson Avenue',
 'Myrtle Avenue',
 'Metropolitan Avenue',
 'Eliot Avenue',
 'Grand Avenue',
 'Roosevelt Avenue']

 This should result in a dataset with 18 rows (one for each connection), which holds true.